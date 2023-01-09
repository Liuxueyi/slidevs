[toc]

slidev pipiti made by sli.dev :D

# nodejs
（当前）nodejs的版本必须大于14，bullseye默认是12：
- https://packages.debian.org/bullseye/arm64/nodejs

可以给bullseye添加额外的nodejs镜像源，可以使用lts，也可以使用某个特定版本：
- https://www.linuxcapable.com/how-to-install-node-js-14-lts-16-npm-on-debian-11-bullseye/

之后就可以正常安装了。

# slidev
slidev指令未必需要全局安装。文件夹下的就可以用：
```
Codes/slidev [ ./node_modules/@slidev/cli/bin/slidev.js export --with-clicks --timeout 300000
```
不过这个命令是js文件，而不是二进制。

# 导出
必须安装playwright-chromium：
```
npm i -D playwright-chromium
```
但是装的挺慢的，而且没有进度条。

后来用这个先装playwright，有进度条，但是明显装多了，不止装了chromium，还装了firefox……
```
$ npx playwright install                                                                                     [14:26:13]
Need to install the following packages:
  playwright@1.29.2
Ok to proceed? (y)
╔═══════════════════════════════════════════════════════════════════════════════╗
║ WARNING: It looks like you are running 'npx playwright install' without first ║
║ installing your project's dependencies.                                       ║
║                                                                               ║
║ To avoid unexpected behavior, please install your dependencies first, and     ║
║ then run Playwright's install command:                                        ║
║                                                                               ║
║     npm install                                                               ║
║     npx playwright install                                                    ║
║                                                                               ║
║ If your project does not yet depend on Playwright, first install the          ║
║ applicable npm package (most commonly @playwright/test), and                  ║
║ then run Playwright's install command to download the browsers:               ║
║                                                                               ║
║     npm install @playwright/test                                              ║
║     npx playwright install                                                    ║
║                                                                               ║
╚═══════════════════════════════════════════════════════════════════════════════╝
Downloading Chromium 109.0.5414.46 (playwright build v1041) from https://playwright.azureedge.net/builds/chromium/1041/chromium-linux.zip
140.1 Mb [====================] 100% 0.0s
Chromium 109.0.5414.46 (playwright build v1041) downloaded to /home/win-pichu/.cache/ms-playwright/chromium-1041
Downloading FFMPEG playwright build v1008 from https://playwright.azureedge.net/builds/ffmpeg/1008/ffmpeg-linux.zip
2.6 Mb [====================] 100% 0.0s
FFMPEG playwright build v1008 downloaded to /home/win-pichu/.cache/ms-playwright/ffmpeg-1008
Downloading Firefox 107.0 (playwright build v1369) from https://playwright.azureedge.net/builds/firefox/1369/firefox-debian-11.zip
77.8 Mb [====================] 100% 0.0s
Firefox 107.0 (playwright build v1369) downloaded to /home/win-pichu/.cache/ms-playwright/firefox-1369
Downloading Webkit 16.4 (playwright build v1751) from https://playwright.azureedge.net/builds/webkit/1751/webkit-debian-11.zip
89.9 Mb [====================] 100% 0.0s
Webkit 16.4 (playwright build v1751) downloaded to /home/win-pichu/.cache/ms-playwright/webkit-1751
```

之后再正常装：
```
$ npm i -D playwright-chromium

added 2 packages, and audited 481 packages in 10s

96 packages are looking for funding
  run `npm fund` for details

found 0 vulnerabilities
```

## timeout
导出的时候就是用本文件夹下的slidev js就行，但是注意设置timeout，默认30000ms：
```
$ ./node_modules/@slidev/cli/bin/slidev.js export --with-clicks --timeout 300000                     ] 3:16 PM


  ●■▲
  Slidev  v0.38.2

  theme   @slidev/theme-seriph
  entry   /home/win-pichu/Codes/ls/slides.md


  ✓ exported to ./slides-export.pdf
```
因为需要一些外部资源，比如封面图。可能字体之类的也有关系。

## 字体

### WSL字体安装
因为用的是WSL，没有什么字体，所以导出来的中文字体非常奇怪，大大小小……

- https://unix.stackexchange.com/a/149368/283488

装完wqy就正常多了，虽然还不是很好看，但中文至少不是大大小小的了：
```
% sudo apt install fonts-wqy-microhei fonts-wqy-zenhei
```

> 如果不用WSL应该没什么字体的问题……

> render pdf的时候用wqy会快很多，不知道为啥。

的确，在Debian KDE上导出的字体完全没问题，很漂亮，而且导出速度巨快，没有超时的问题（也可能是网络的问题）。WSL：图形界面的事关我什么事。

如果需要emoji，装上这个` fonts-noto-color-emoji`

建议把arphic都装上：
```
% sudo apt-get install "fonts-arphic-*"
```

### 字体选用
建议按照教程说的使用这几个字体：
- https://cn.sli.dev/custom/fonts.html

在frontmatter里：
```
---
fonts:
  # 基础字体
  sans: 'Robot'
  # 与 windicss 的 `font-serif` css 类一同使用
  serif: 'Robot Slab'
  # 用于代码块、内联代码等
  mono: 'Fira Code'
---
```
英文和数字会圆润许多。



