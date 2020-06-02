# 设置npm的registry

设置国内镜像 三种方式

* 通过config命令

npm config set registry https://registry.npm.taobao.org npm info underscore （如果上面配置正确这个命令会有字符串response）

* 命令行指定

npm --registry https://registry.npm.taobao.org info underscore

* 编辑 ~/.npmrc 加入下面内容

registry = https://registry.npm.taobao.org

由于npm自身的更新频率比Node.js高很多，可以通过下面的命令单独更新npm

```
npm install npm@latest -g
```

查看npm全局配置

```
npm config ls -l
```

module对应prefix，cache对应cache

安装yarn

```
npm install -g yarn
yarn --version
```

Yarn 淘宝源安装

```
yarn config set registry https://registry.npm.taobao.org -g
yarn config set sass_binary_site http://cdn.npm.taobao.org/dist/node-sass -g
```

nodejs升级，用 n 命令升级 

```
sudo npm install -g n
sudo n lts
#如果下载不下来，可以直接将官网下载包解压到目录。例：/usr/local/n/versions/node/12.16.3
```

```
# Using Ubuntu 安装nodejs
curl -sL https://deb.nodesource.com/setup_12.x | sudo -E bash -
sudo apt-get install -y nodejs
```

npm查看本地安装包信息

```
npm ls webpack
```

查看全局安装的webpack

```
npm ls webpack -g
```

查看服务器所有版本信息

```
npm view webpack versions
npm info webpack
```

查看最新

```
npm view webpack version
```

- ~ 会匹配最近的小版本依赖包，比如~1.2.3会匹配所有1.2.x版本，但是不包括1.3.0
- ^ 会匹配最新的大版本依赖包，比如^1.2.3会匹配所有1.x.x的包，包括1.3.0，但是不包括2.0.0
- `* `这意味着安装最新版本的依赖包