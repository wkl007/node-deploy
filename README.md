# node-deploy

> node自动化部署前端项目至远程服务器指定目录

参考项目 [my-auto-deploy](https://github.com/aotianwinter/my-auto-deploy)

## 功能特性

- 支持多个配置信息，自动化部署时支持选择配置信息运行
- 支持修改服务器连接端口，支持`ssh`私钥及解密密码连接（ps：不使用此方法时，请注释privateKey）
- 支持远程文件备份

## 使用

```javascript
yarn install 
yarn deploy
```

## 配置文件说明

```javascript
/*
  deploy.config.js说明：
  ssh: 连接服务器用户信息
  targetDir: 需要压缩的文件目录（启用本地压缩后生效）
  openCompress: 关闭后，将跳过本地文件压缩，直接上传同级目录下指定文件
  openBackUp: 开启后，若远端存在相同目录，则会修改原始目录名称，不会直接覆盖
  deployDir: 指定远端部署地址
  releaseDir: 指定远端部署地址下的发布目录名称
*/

const config = [
  {
    name: '项目A-dev',
    ssh: {
      host: '192.168.0.110',
      port: 22,
      username: 'root',
      password: 'root',
      // privateKey: 'E:/id_rsa', // ssh私钥(不使用此方法时请勿填写， 注释即可)
      // passphrase: '123456' // ssh私钥对应解密密码(不存在设为''即可)
    },
    targetDir: './dist', // 目标压缩目录(可使用相对地址)
    openCompress: true, // 是否开启本地压缩
    openBackUp: true, // 是否开启远端备份
    deployDir: '/home/node_deploy/test/', // 远端目录
    releaseDir: 'dist' // 发布目录
  }
]

module.exports = config
```

