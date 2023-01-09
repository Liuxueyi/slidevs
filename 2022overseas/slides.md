---
# try also 'default' to start simple
theme: seriph
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
background: https://source.unsplash.com/collection/94734566/1920x1080
# apply any windi css classes to the current slide
class: 'text-center'
# https://sli.dev/custom/highlighters.html
highlighter: shiki
fonts:
  # basically the text
  sans: 'Robot'
  # use with `font-serif` css class from windicss
  serif: 'Robot Slab'
  # for code blocks, inline code, etc.
  mono: 'Fira Code'
# some information about the slides, markdown enabled
info: |
  ## Youdao ads
  Presentation slides for developers.

  Learn more at [Sli.dev](https://sli.dev)
---

# 2022技术总结

——海外广告后端

<div class="pt-12">
  <span @click="$slidev.nav.next" class="px-2 p-1 rounded cursor-pointer" hover="bg-white bg-opacity-10">
     <carbon:arrow-right class="inline"/>
  </span>
</div>

<!--
The last comment block of each slide will be treated as slide notes. It will be visible and editable in Presenter Mode along with the slide. [Read more in the docs](https://sli.dev/guide/syntax.html#notes)
-->

---

# 从技术的角度

总结一下过去一年海外广告技术上的变化，对整个项目需求实现的影响。

<br>
<br>

- 📤 **基础设施**： 系统中第三方服务的变化
- 💻 **开发流程**： “我变秃了，也变强了”
- 🛠 **部署维护**： 积极探索能够更懒的办法


<br>
<br>

详情参考 [《2022海外广告后端技术总结》](https://confluence.inner.youdao.com/pages/viewpage.action?pageId=237751248)

<!--
You can have `style` tag in markdown to override the style for the current page.
Learn more: https://sli.dev/guide/syntax#embedded-styles
-->

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>

---

# 基础设施

## elasticsearch

数据使用 - 从默默无闻到重度使用

|     |     |
| --- | --- |
| <kbd>分词</kbd> | 可以“主动找”kol了 |
| <kbd>父子索引</kbd> | kol和media数据之间拥有了实质上的“关系” |
| <kbd>pipeline</kbd> | 挖掘每一个media数据背后的意义 |

---

# 基础设施

## elasticsearch

数据存储、性能 - 更快 更大 更强

| | before | after    |
| --- | --- | --- |
| 存储空间 | 存储混用🥺 | 6×4T独占🤪 |
| 查询速度 | 30s+🦽 | ms级🏍 |

---

# 基础设施

## elasticsearch

数据安全

| | before | after    |
| --- | --- | --- |
| 数据备份 | 😵 | 日备份、月备份💃 |
| 权限控制 | 😵 | 😵 |

---

# 基础设施

## canal相关

不仅对业务无感知，现在开发也无感知

| | before | after    |
| --- | --- | --- |
| 增量同步 | 数据积压🤕 | 多多益善😎 |
| 全量同步 | 又慢又繁😵‍💫 | 随意切换😎 |

---

# 基础设施

## AWS

~~你们做海外服务的，服务一定都部署在海外吧🤪~~

- 全球部署
- 实时同步
- 链路加速
- 负载均衡

<!-- https://sli.dev/guide/animations.html#click-animations -->
<img
  v-click
  class="absolute -bottom-9 -left-7 w-80 opacity-50"
  src="https://sli.dev/assets/bottom-left.svg"
/>
<p v-after class="absolute bottom-23 left-45 opacity-30 transform -rotate-10">又（关）快（键）又（是）省钱！</p>

---

# 基础设施

## PlayWright

数据是业务之源

- official API
- PlayWright
- Selenium

| |  |
| --- | --- |
| Http Client | 三天两挂 |
| Selenium | 代理支持不佳 |
| PlayWright | 支持代理验证、稳定轻量 |

---

# 开发流程

## 自动配置

写代码嘛，很简单的：<kbd>Ctrl</kbd> + <kbd>C</kbd>，<kbd>Ctrl</kbd> + <kbd>V</kbd> 🤫🤫🤫

<br>

- 因复制粘贴产生的“平行世界”代码
- 动态自动配置

---

# 开发流程

## 读写elasticsearch

只要我不写代码，就不会产生bug ✔

<br>

- 代码写得少，需要维护的代码就少
- 代码写得少，活干完得早
- 代码写得少，bug真的会减少

---

# 开发流程

## 测试

写代码 + 写测试代码 + 测试 + 修bug ≯ 写代码 + 修bug

<br>

- jupiter
- testcontainers
- gitlab-ci

---

# 部署维护

懒是推进科技进步的第一生产力

| | before | after    |
| --- | --- | --- |
| 部署位置 | 苟😵‍💫 | 😎 |
| 部署方式 | linux操作越来越熟练了~😵‍💫 | 一键式😎 | 
| 多实例 | 苟😵‍💫 | 并行处理😎 |


