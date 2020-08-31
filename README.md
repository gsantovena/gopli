我是光年实验室高级招聘经理。
我在github上访问了你的开源项目，你的代码超赞。你最近有没有在看工作机会，我们在招软件开发工程师，拉钩和BOSS等招聘网站也发布了相关岗位，有公司和职位的详细信息。
我们公司在杭州，业务主要做流量增长，是很多大型互联网公司的流量顾问。公司弹性工作制，福利齐全，发展潜力大，良好的办公环境和学习氛围。
公司官网是http://www.gnlab.com,公司地址是杭州市西湖区古墩路紫金广场B座，若你感兴趣，欢迎与我联系，
电话是0571-88839161，手机号：18668131388，微信号：echo 'bGhsaGxoMTEyNAo='|base64 -D ,静待佳音。如有打扰，还请见谅，祝生活愉快工作顺利。

gopli
========
Database backup between remote hosts (or local) written in Golang.

## Feature

- High-speed parallel data fetching with goroutine concurrency
- Reuse options of connection with TOML configuration
- Gopli will release you from an annoying replication setting

# TODO
- [ ] Currently MySQL only. so adopt to other management systems
- [ ] Data mask for password, credit-card number, etc...
- [ ] Response packet regulation and compression for fetched data

## Install
```
go get github.com/timakin/gopli
```

## Usage
Write down setting file in toml.
```
[database]
  [database.local]
  host = "localhost"
  management_system = "mysql"
  name = "app_development"
  user = "root"
  password = ""

  [database.staging]
  host = "xxx.xxx.xxx.xxx"
  management_system = "mysql"
  name = "app_staging"
  user = "root"
  password = ""

  [database.production]
  host = "yyy.yyy.yyy.yyy"
  management_system = "mysql"
  name = "app_production"
  user = "root"
  password = ""

[ssh]
  [ssh.local]
  host = "localhost" # or "127.0.0.1"

  [ssh.staging]
  host = "xxx.xxx.xxx.xxx"
  port = "22"
  user = "timakin"
  key = "~/.ssh/id_rsa_staging"

  [ssh.production]
  host = "yyy.yyy.yyy.yyy"
  port = "22"
  user = "remoteuser"
  key = "~/.ssh/id_rsa_prod"

```

```
gopli sync -from production -to staging -c config/gopli.toml
```
