[toc]

### cli

#### 编写指令

命令代码都应该写在 bin 目录下，并在`package.json`中配置启用命令

```json
{
  "bin": {
    "cc": "./bin/index.js"
  }
}
```

#### 安装[commander][1]插件

方便编写命令代码

```bash
yarn add -D commander
```

[1]: https://github.com/tj/commander.js/blob/master/Readme_zh-CN.md

#### 代码

```js
// 这段很重要
#!/usr/bin/env node

const { program } = require("commander");
program
  .option("-v,--version [version]", "版本", require("../package.json").version)
  .option("-d,--dir [dir]", "存放目录,", "")
  .option("-p,--port [port]", "端口号", 8080)
  .option("-b,--base [base]", "默认地址,可以选填主要解决github pages", "")
  .parse(process.argv);

let opts = program.opts();
console.log(opts);
```
