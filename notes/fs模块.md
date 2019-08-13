# fs模块

### fs模块需要掌握的9个基本方法：
```js
let fs = require('fs')

// 文件
fs.readFile()
fs.writeFile()
fs.appendFile()
fs.unlink()

// 目录
fs.mkdir()
fs.readdir()
fs.rmdir()

// common
fs.rename()
fs.stat()

```

### 读取流
```js
let fs = require('fs')

let rs = fs.createReadStream('demo/index.html')

let str = ''
rs.on('data', function (chunk) {
  str += chunk
})

rs.on('end', function (err) {
  if (err) {
    console.log(err)
    return
  }
  console.log(str)
})

rs.on('error', function (err) {
  console.log(err)
})

```

### 写入流
```js
let fs = require('fs')

let ws = fs.createWriteStream('demo/hello.txt')

ws.write('我是写入的内容1\n')
ws.write('我是写入的内容2\n')

// 标记写入结束,触发finish事件
ws.end()

ws.on('finish', function () {
  console.log('写入完成')
})

ws.on('error', function (err) {
  console.log(err)
})
```

