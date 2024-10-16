### 常用命令

- `hexo n "title"` 创建新文章。
- `hexo g -d` 生成静态文件（generate），且文件生成后立即部署网站（deploy）。
- `hexo publish "tilte"` 发表草稿。
- `hexo s` 启动服务器。默认访问本地4000端口。
- `hexo clean` 清除缓存文件（`db.json`）和已生成的静态文件（`public`）；在某些情况（尤其是更换主题后），如果发现站点的更改无论如何也不生效，可能需要运行该命令。
- `hexo version` 显示 Hexo 版本。
- `npm list` 查看插件。
- `npm uninstall 插件名称` 卸载插件。

### 备份博客

#### 安装插件

首先通过npm安装hexo的备份插件。

``````javascript
npm install hexo-git-backup --save
``````

#### 插件升级

如果使用 –save 安装，则在更新时必须先删除。

``````javascript
npm remove hexo-git-backup
npm install hexo-git-backup --save
``````

#### 插件配置

在博客目录根的 _config.yml 中增加相应配置。

```yaml
backup:
    type: git
    theme: yilia-plus
    message: backup message
    repository:
       github: git@github.com:xxx/xxx.git,backup
```

#### 插件使用

`hexo b` 备份博客到github上对应的backup分支。

**建议每次发布博客 `hexo d` 的时候都同时 `hexo b` 对博客进行备份更新。**

### 恢复博客

#### 安装 Hexo

在新环境下使用命令配置好 Hexo 环境。

```javascript
npm install hexo-cli -g
```

安装博客部署到 GitHub 所需要的插件。

```javascript
npm install
npm install --save hexo-deployer-git
```

#### 下载备份的博客文件

从之前插件备份到 GitHub 分支中下载博客文件到本地。此时运行如下三连进行测试博客是否迁移成功。

```javascript
hexo clean
hexo g
hexo s
git remote add github git@github.com:cglcl/blog-backup.git
```
