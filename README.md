> 部署
# 点击 [![](https://www.herokucdn.com/deploy/button.png)](https://heroku.com/deploy?template=https://github.com/yuyangzxw/gost-heroku)，[一键部署到heroku](https://heroku.com/deploy?template=https://github.com/yuyangzxw/gost-heroku)

本地客户端执行：gost -L=:1080 -F=ss+wss://aes-128-cfb:1234567890@xxxxx.herokuapp.com:443

挂ngrok的方法如下：
```sh
sudo apt-get install heroku
git clone https://github.com/xuiv/gost-heroku.git
cd gost-heroku
```
在app.json中添加如下内容：
```
  "env": {
    "AUX_PORT": {
      "description": "gost socket5 port",
      "value": "9090"
    },    
    "NGROK_API_TOKEN": {
      "description": "ngrok authtoken",
      "value": "4bzM2n2AJwEH3jD2mTxWP_6Vmy6iihkUa2HaDmCmv80" <-- 此处换成你的ngrok认证字符串
    },    
    "NGROK_COMMAND": {
      "description": "ngrok protocol",
      "value": "tcp"
    },
    "NGROK_OPTS": {
      "description": "other ngrok command options",
      "value": ""
    }
  },
```
修改Procfile为：
```
web: with_ngrok gost-heroku -L=ss+ws://aes-128-cfb:1234567890@:$PORT -L=socks5://:9090
```
接下来执行：
```sh
heroku login
heroku create yourappid
heroku config:set NGROK_API_TOKEN=4bzM2n2AJwEH3jD2mTxWP_6Vmy6iihkUa2HaDmCmv80 -a yourappid
heroku config:set AUX_PORT=9090 -a yourappid
heroku config:set NGROK_COMMAND=tcp  -a yourappid
heroku buildpacks:add https://github.com/xuiv/heroku-buildpack-ngrok.git -a yourappid
heroku buildpacks:add https://github.com/heroku/heroku-buildpack-go.git -a yourappid
git push heroku master
```
去ngrok查看转发的域名和端口，这个是直接的soket5代理。

# go-getting-started

A barebones Go app, which can easily be deployed to Heroku.

This application supports the [Getting Started with Go on Heroku](https://devcenter.heroku.com/articles/getting-started-with-go) article - check it out.

## Running Locally

Make sure you have [Go](http://golang.org/doc/install) and the [Heroku Toolbelt](https://toolbelt.heroku.com/) installed.

```sh
$ go get -u github.com/heroku/go-getting-started
$ cd $GOPATH/src/github.com/heroku/go-getting-started
$ heroku local
```

Your app should now be running on [localhost:5000](http://localhost:5000/).

You should also install [govendor](https://github.com/kardianos/govendor) if you are going to add any dependencies to the sample app.

## Deploying to Heroku

```sh
$ heroku create
$ git push heroku master
$ heroku open
```

or

[![Deploy](https://www.herokucdn.com/deploy/button.png)](https://heroku.com/deploy)


## Documentation

For more information about using Go on Heroku, see these Dev Center articles:

- [Go on Heroku](https://devcenter.heroku.com/categories/go)
