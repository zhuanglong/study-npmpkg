# npm 包发布与管理

开始之前先[注册一个 npm 账号](https://www.npmjs.com/)。

## 目录

- <a href="#创建项目">创建项目</a>
- <a href="#发布项目">发布项目</a>
- <a href="#更新项目">更新项目</a>
- <a href="#使用项目">使用项目</a>
- <a href="#关联 github">关联 github</a>

## <a id="创建项目">创建项目</a>

1、为了避免包名已被使用，可以提前在 npm 搜索包名是否存在

2、新建名为 `study-npmpkg` 的文件夹，也是你的包名

`npm init -y`

![](https://gitee.com/zloooong/image_store/raw/master/img/20210126152316.png)

## <a id="发布项目">发布项目</a>

1、先把 npm 源设置为默认的

`npm config set registry=http://registry.npmjs.org`

2、登录 npm 账号

`npm login`

![](https://gitee.com/zloooong/image_store/raw/master/img/20210126152804.png)

3、发布

![](https://gitee.com/zloooong/image_store/raw/master/img/20210126152901.png)

可使用 `npm info` 命令查看包的详细信息。

在 npm 官网搜索。

![](https://gitee.com/zloooong/image_store/raw/master/img/20210126153131.png)

<font color="red">发布 403 报错。</font>

```
npm ERR! code E403
npm ERR! 403 403 Forbidden - PUT http://registry.npmjs.org/study-npmpkg - Forbidden
npm ERR! 403 In most cases, you or one of your dependencies are requesting
npm ERR! 403 a package version that is forbidden by your security policy.
```

解决方案：首次注册，没有验证邮箱，去邮箱按步验证，再次发布即可解决。

## <a id="更新项目">更新项目</a>

package.json 中的 `"main": "index.js"` 是入口文件

新建 index.js，内容如下：

```js
const text = 'study npmpkg';
export default text;
```

每次发包都要更新版本号，

```
npm version [<newversion> | major | minor | patch | premajor | preminor | 
prepatch | prerelease | from-git]
```

其语义为：

```json
major：主版本号（大版本）
minor：次版本号（小更新）
patch：补丁号（补丁）
premajor：预备主版本
preminor: 预备次版本
prepatch：预备补丁版本
prerelease：预发布版本
```

这里执行 `npm version minor`，版本号从 `1.0.0` 变成 `1.1.0`。

最后发布。

## <a id="使用项目">使用项目</a>

1、安装依赖包

`yarn add study-npmpkg`

2、导入使用

```
import studynpmpkg from 'study-npmpkg';

<p>{studynpmpkg}</p>
```

![](https://gitee.com/zloooong/image_store/raw/master/img/20210126162327.png)

## <a id="关联 github">关联 github</a>

1、新建 github 仓库

![](https://gitee.com/zloooong/image_store/raw/master/img/20210126164908.png)

然后复制地址，通过命令 `git clone xx` 拷贝到本地，

把之前的项目复制到这里，

![](https://gitee.com/zloooong/image_store/raw/master/img/20210126165228.png)

2、repository

package.json 新增 `"repository"`，

```
"repository": {
    "type": "git",
    "url": "git@github.com:xxx/study-npmpkg.git"
}
```

3、发布

修改版本号为 `1.2.0`，提交到 github，再执行 `npm publish` 发布。

![](https://gitee.com/zloooong/image_store/raw/master/img/20210126172258.png)

可以看到关联地址了。

==注：其实更规范的流程是，每次发布版本前，先打 tag，再发布。==

参考 ant-design

![](https://gitee.com/zloooong/image_store/raw/master/img/20210126171922.png)

## 参考

- [NPM包（模块）发布、更新、撤销发布](https://juejin.cn/post/6844903769365282829)
- [一文搞定 npm 包发布与管理](https://juejin.cn/post/6920231981834108942)
- [npm包 搭建，打包，调试，发布](https://juejin.cn/post/6871591252417216520)