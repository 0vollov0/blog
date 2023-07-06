---
title: "MyKaKaoTalk"
excerpt: "MyKaKaoTalk is a program that cloned the PC version of KakaoTalk (as of 2018). The UI/UX was developed using Java's Swing, and TCP/IP communication was used for chatting between users. MySQL database was used for storing chat data."
author_profile: true
header:
  teaser: https://play-lh.googleusercontent.com/Ob9Ys8yKMeyKzZvl3cB9JNSTui1lJwjSKD60IVYnlvU2DsahysGENJE-txiRIW9_72Vd=w240-h480-rw
show_date: true
---

# MyKaKaoTalk

## [Go to Github](https://github.com/0vollov0/MyKaKaoTalk)

Java Swing과 MultiThread Socket, JDBC(MySQL) 을 이용하여 카카오톡(구버전) 을 구현해 보았습니다.

## 기능

* 회원 등록
* 친구 검색
* 친구 추가/삭제
* 프로필 수정
* 채팅방 개설
* 채팅방 참가/나가기
* 채팅방 대화 친구 추가

# 설명

좌측) 로그인 화면  우측) 회원가입 화면

![ImplementationImage](https://github.com/0vollov0/MyKaKaoTalk/blob/master/ReadmeImage/ImplementationImage/imp_01.jpg?raw=true)

메인화면

![ImplementationImage](https://github.com/0vollov0/MyKaKaoTalk/blob/master/ReadmeImage/ImplementationImage/imp_02.jpg?raw=true)

좌측) 채팅방 설정  우측) 채팅방 리스트 

![ImplementationImage](https://github.com/0vollov0/MyKaKaoTalk/blob/master/ReadmeImage/ImplementationImage/imp_03.jpg?raw=true)

친구 추가 좌측) admin1 계정 우측) admin 계정

![ImplementationImage](https://github.com/0vollov0/MyKaKaoTalk/blob/master/ReadmeImage/ImplementationImage/imp_04.jpg?raw=true)

좌측) 본인 계정 프로필 화면 우측) 친구 계정 프로필 화면

![ImplementationImage](https://github.com/0vollov0/MyKaKaoTalk/blob/master/ReadmeImage/ImplementationImage/imp_05.jpg?raw=true)

# DataBase

## MyKaKao DB Table

![DataBase](https://github.com/0vollov0/MyKaKaoTalk/blob/master/ReadmeImage/ImplementationImage/imp_06.jpg?raw=true)

* addfriendlist

| Field | Type | Null | Key | Default | Extra |
|:-------|:-------|:-------|:-------|:-------|:-------|
| senderID | varchar(24) | NO | PRI | NULL |  |
| receiverID | varchar(24) | NO | PRI | NULL |  |

* chatlog

| Field | Type | Null | Key | Default | Extra |
|:-------|:-------|:-------|:-------|:-------|:-------|
| senderID | varchar(24) | NO | PRI | NULL |  |
| roomID | int(11) | NO | PRI | NULL |  |
| chatContent | varchar(100) | YES |  | NULL |  |
| chatTime | datetime | NO | PRI | 0000-00-00 00:00:00 |  |

* chattingroom

| Field | Type | Null | Key | Default | Extra |
|:-------|:-------|:-------|:-------|:-------|:-------|
| roomID | int(11) | NO | PRI | NULL |  |
| roomName | varchar(48) | NO | PRI | NULL |  |
| member | varchar(24) | NO | PRI | NULL |  |

* friend

| Field | Type | Null | Key | Default | Extra |
|:-------|:-------|:-------|:-------|:-------|:-------|
| userID | varchar(24) | NO | PRI | NULL |  |
| friendID | varchar(24) | NO | PRI | NULL |  |

* singlechat

| Field | Type | Null | Key | Default | Extra |
|:-------|:-------|:-------|:-------|:-------|:-------|
| senderID | varchar(24) | NO | PRI | NULL |  |
| roomID | int(11) | NO | PRI | NULL |  |
| chatContent | varchar(100) | YES |  | NULL |  |
| chatTime | datetime | NO | PRI | 0000-00-00 00:00:00 |  |

* user

| Field | Type | Null | Key | Default | Extra |
|:-------|:-------|:-------|:-------|:-------|:-------|
| userID | varchar(24) | NO | PRI | NULL |  |
| userPassword | varchar(24) |  | PRI | NULL |  |
| userName | varchar(16) | NO |  | NULL |  |
| userEmail | varchar(32) | NO |  | NULL |  |
| userTel | varchar(16) | NO |  | NULL |  |
| profile | varchar(32) | YES |  |  |  |

# Class Diagram

## Client

* client

![client_Diagram](https://github.com/0vollov0/MyKaKaoTalk/blob/master/ReadmeImage/ClassDiagram/Client/client.png?raw=true)

* user

![user_Diagram](https://github.com/0vollov0/MyKaKaoTalk/blob/master/ReadmeImage/ClassDiagram/Client/user.png?raw=true)

## Server

* server

![server Diagram](https://github.com/0vollov0/MyKaKaoTalk/blob/master/ReadmeImage/ClassDiagram/Server/server.png?raw=true)

* addfriendlist

![addfriendlist_Diagram](https://github.com/0vollov0/MyKaKaoTalk/blob/master/ReadmeImage/ClassDiagram/Server/addfriendlist.png?raw=true)

* chatlog

![chatlog_Diagram](https://github.com/0vollov0/MyKaKaoTalk/blob/master/ReadmeImage/ClassDiagram/Server/chatlog.png?raw=true)

* chattingroom

![chattingroom_Diagram](https://github.com/0vollov0/MyKaKaoTalk/blob/master/ReadmeImage/ClassDiagram/Server/chattingroom.png?raw=true)

* friend

![friend_Diagram](https://github.com/0vollov0/MyKaKaoTalk/blob/master/ReadmeImage/ClassDiagram/Server/friend.png?raw=true)

* singlechat

![singlechat Diagram](https://github.com/0vollov0/MyKaKaoTalk/blob/master/ReadmeImage/ClassDiagram/Server/singlechat.png?raw=true)

* user

![user_Diagram](https://github.com/0vollov0/MyKaKaoTalk/blob/master/ReadmeImage/ClassDiagram/Server/user.png?raw=true)
