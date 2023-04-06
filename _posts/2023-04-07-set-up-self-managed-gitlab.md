---
title:  "Set up Self-Managed GitLab"
search: true
categories:
  - DevOps
tags: 
  - GitLab
  - Infra
  - Self Managed GitLab
toc: true
last_modified_at: 2023-04-7T00:00:00
show_date: true
---
### Enviroment
- Ubuntu 22.04
- AWS EC 2 t.large instance

### Install
Follow the instruction on the link

link: [Download and install GitLab](https://about.gitlab.com/install/#ubuntu)


### Apply up domain and HTTPS
When you installed gitlab, the gitlab server run as port 80 you can use nginx or something else.
You can set up nginx refer to this link [NGINX settings | GitLab ](https://docs.gitlab.com/omnibus/settings/nginx.html).
But I used aws S5 and cloud flont service to apply domain and HTTPS.

### Modify exteranl Url
```bash
ubuntu@user:~$ sudo vim /etc/gitlab/gitlab.rb
```
Search `external_url` in the above file and change it to your applied domain url like below.
![/etc/gitlab/gitlab.rb](/blog/assets/images/2a7fab6b-5ead-4adc-805d-a1f122bef5d3.png "/etc/gitlab/gitlab.rb")

After modify, you need to run this line.

```bash
sudo gitlab-ctl reconfigure
```

### Change Admin Password
After gitlab server has been installed and ran, you can check root(administer account) account’s password in the /etc/gitlab/initial_root_password.
Login as admin using id(root) and password that you checked in above.

1. Go to Edit profile where is in the right top drop down button.

2. Go to Password tab where is on the left side bar.

3. Chage admin password

### Set up SMTP as Gmail
Ref: [SMTP settings | GitLab](https://docs.gitlab.com/omnibus/settings/smtp.html#gmail)

Add below codes and in the `/etc/gitlab/gitlab.rb`.

![Gmail](/blog/assets/images/c23ab445-c2b3-4eaf-928b-4ef3a497b48b.png "Gmail")

After modify, you need to run this line.

```bash
sudo gitlab-ctl reconfigure
```

### Change Admin Email

1. Go to Edit profile where is in the right top drop down button.
2. On the page, you can see Email filed on the `Main settings` section.
3. Change you want to use email.

### Import project from gitlab.com

1. click the create project.
2. click the import project.
3. click the Repository by URL.
4. put the information into the fileds.

### Mirroring repositories

If you want to sync with origin(gitlab.com), go to settings > Repository in the origin gitlab repo.

Input the git repo url using userid and password likve below.

![Mirroring](/blog/assets/images/75cf948e-59de-4bc2-abee-7670c84ac0b4.png "Mirroring")

The opposite also work if you set up in not origin gitlab.