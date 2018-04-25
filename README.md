> 部署
# 点击 [![](https://www.herokucdn.com/deploy/button.png)](https://heroku.com/deploy?template=https://github.com/xuiv/gost-heroku)，[一键部署到heroku](https://heroku.com/deploy?template=https://github.com/xuiv/gost-heroku)

本地客户端执行：gost-heroku -L=:1080 -F=ss+wss://aes-128-cfb:1234567890@xxxxx.herokuapp.com:443

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
