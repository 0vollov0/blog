---
title: "VIM-Android version"
excerpt: "VIM(Voice Indoor Maps) Application for Android has been developed for visually impaired persons to support indoor navigation."
author_profile: true
header:
  teaser: https://cdn.vox-cdn.com/thumbor/11JegsiLPrW7pbf-BQCDcb0qiNQ=/0x0:6000x4000/1400x1050/filters:focal(2520x1520:3480x2480):format(jpeg)/cdn.vox-cdn.com/uploads/chorus_image/image/49276747/shutterstock_154744394.0.jpg
show_date: true
---

## [Go to Github](https://github.com/STEMLab/VIM){:target="_blank"}

### What is VIM

VIM(Voice Indoor Maps) Application for Android has been developed for visually impaired persons to support indoor navigation.

Actually two versions of VIM were developped for

1. indoor space with braille blocks
2. indoor space without braille blocks

VIM has been developed for visually impaired, but it will also be useful for non-impaired users in finding indoor routes.

### Demonstration


|location|departure|destination|video
|:--|:--|:--|:--|
|Ease Daegu Station|Information Center|RestRoom Near By Number 2 Entrance|[YouTube](https://youtu.be/KjH6fsr74Jc "VIM Demonstration at 동대구역(1)"){:target="_blank"}|
|Ease Daegu Station|RestRoom Near By Number 2 Entrance|Number 6 Entrance|[YouTube](https://youtu.be/EPm08nGf39k "VIM Demonstration at 동대구역(2)"){:target="_blank"}|


### Form for expressing indoor space information

VIM follows the OGC international standard IndoorGML format to express indoor spatial information. if you want to add or modify indoor space information, you must follow the schema format of the IndoorGML 1.0 core version.

> [What is IndoorGML?](http://www.indoorgml.net/ "OGC Standard for Indoor Spatial Information"){:target="_blank"}

> [indoorgmlcore.xsd](http://schemas.opengis.net/indoorgml/1.0/indoorgmlcore.xsd "indoorgmlcore.xsd"){:target="_blank"}

### IndoorGML For VIM

In order to run VIM smoothly, a total of 4 ```<core:SpaceLayer/>```s which has attribute ```gml:id``` as below table must exist in IndoorGML.

|gml:id|require|description|
|:--|--|--|
|base|optional|This layer expresses only general indoor spatial information like a room, door, stair, elevator...|
|network|essential|This layer expresses route which user can use. It only consists of state and transition.|
|landmark|optional|This layer has poi which you want to recognize for user. It only consists of state.|
|safety|optional|This layer has dangerous or relative safety poi when user face it. It only consists of state.|

In order to express VIM object where exist in network layer you need to add value at IndoorGML element.

|layer|VIM object|indoorGML|element|value|description|
|:--|:--|:--:|:--:|:--:|:--|
|base|stair|```<core:CellSpace/>```|```<name/>```|contain 'stair' |It represent the space of interLayerConnected state which has description value as `type="stair"`  and exist in network layer|
|base|elevator|```<core:CellSpace/>```|```<name/>```|contain 'elevator' |It represent the space of interLayerConnected state which has description value as `type="elevator"` and exist in network layer|
|base|escalator|```<core:CellSpace/>```|```<name/>```|contain 'escalator' |It represent the space of interLayerConnected state which has description value as `type="escalator"`  and exist in network layer|
|network|stair|```<core:State/>```|```<description/>```|type="stair" |It must be connected to other floor state as transition and |
|network|elevator|```<core:State/>```|```<description/>```|type="elevator" |It must be connected to other floor state as transition|
|network|escalator|```<core:State/>```|```<description/>```|type="escalator" |It must be connected to other floor state as transition|
|network|dotted block|```<core:State/>```|```<description/>```|dot="true" |It will work when turn on the visually impaired version|
|network|linear block|```<core:State/>```|```<description/>```|null|It will work when turn on the visually impaired version|

#### More information

In order to make the space that can move floor, you need to make cellSpace in base layer and state which has been interconnected as contains based on base layer in network layer.

#### Location.json

Using the [location.json](./app/src/assets/../main/assets/location.json) you can modify or add destination information. basically, destinations are  ```<core:State/>``` which exist in network layer. the format of [location.json](./app/src/assets/../main/assets/location.json) is as bellow.

```
{
  "service_no" : {
    "209" : { // the number which is positioning system service number
      "name": "pnu_abc.gml", // indoorGML file name
      "floors": {
        "2": { // floor number
          "states": {
            "S71": { // <core:State/> gml:id in network layer
              "name": {
                "en": "2F north man's restroom",
                "ko": "2층 북쪽 남자 화장실"
              }
            },
            ...
            ...
          }
        },
        ...
        ...
      }
    },
    "braille_blocks": false // if the place has been include braille blocks for visually impaired you can put true value
  }
}
```
### Tree
```
└─app
    └─src
        ├─main
        ├─assets
        │  └─indoorgml
        ├─java
        │  └─lab
        │      └─stem
        │          └─vim
        │              ├─core
        │              ├─guideFactory
        │              ├─indoorGML
        │              ├─log
        │              └─observer
        ├─raw
        └─res
```
