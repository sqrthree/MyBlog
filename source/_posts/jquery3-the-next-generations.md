title: jQuery 3.0——下一代的jQuery
categories: 技术
date: 2015-11-05 11:42:00
updated: 2015-11-05 11:42:00
tags:
    - jQuery3.0
    - 译文
---

2014年10月29日，jQuery 官方博客上更新了一篇博文，描述了关于下一代 jQuery 的一些信息。实际上这篇博文至今都已经一年时间了，jQuery 官方团队也早在2015年7月13日发布了 `jQuery 3.0.0-alpha1` 版本。我之前也只是匆匆的看过一遍，今日闲着无事，就尝试翻译了一下并发布了这篇迟到了一年的译版，想要了解 `3.0` 中的新特性的话可以关注我后续的更新。

<!-- more -->

### 正文开始

It’s hard to believe it’s been nearly eight years since jQuery was released. Web development has changed a lot over the years, and jQuery has changed along with it. Through all of this time, the team has tried to walk the line between maintaining compatibility with code from the past versus supporting the best web development practices of the present.

很难相信从 `jQuery` 发布以来已经过去八年了，过去的这些年 Web 开发已经改变了很多， `jQuery` 也随之变化着。在这个过程中，团队一直在保持对旧代码的兼容性和支持目前最好的 Web 开发实践之间努力平衡着。

One of those best practices is semantic versioning, or semver for short. In a practical sense, semver gives developers (and build tools) an idea of the risk involved in moving to a new version of software. Version numbers are in the form of MAJOR.MINOR.PATCH with each of the three components being an integer. In semver, if the MAJOR number changes it indicates there are breaking changes in the API and thus developers need to beware.

其中最好的做法就是语义化版本，或者简单的称之为 [semver](http://semver.org/lang/zh-CN/)，从实践的角度看，[semver](http://semver.org/lang/zh-CN/) 给了开发者(以及构建工具) 一个避免由于切换软件版本导致的风险的方法。版本号为 `MAJOR.MINOR.PATCH` 的格式，并且其三个组成部分均为整数。在[semver](http://semver.org/lang/zh-CN/) 中，如果 `MAJOR` 改变了，就意味着在 API 中出现了不兼容的改变，因此开发者们需要当心。

The concept of versioning gets a little more nuanced with jQuery, where browser compatibility can be just as important as API compatibility. In order to create a slimmer jQuery, the team started shipping two versions in 2013. The first version remained numbered in the 1.x line and, currently at 1.11.1, maintains compatibility with a maximal number of browsers. The second version, starting with 2.0.0 and now at 2.1.1, dropped support for browsers like IE8 or lower in order to streamline the code. Both the 1.x and 2.x versions of jQuery have the same public APIs, even though they differ somewhat in their internal implementations.

在 `jQuery` 中版本控制变得更加微妙，(对 jQuery 来说) 浏览器的兼容性和 API 的兼容性同等重要。为了创造一个 “苗条” 的 `jQuery` ，团队在2013年开始放出了两个版本。第一个版本保持着 1.x 的编号，当前(截止到原文发布时)最新版本为 1.11.1，其保持了最大数量的浏览器兼容性。第二个版本从 2.0.0 开始，目前是 2.1.1，为了精简代码，放弃了对 IE8及其以下版本浏览器的支持。1.x 和 2.x 版本的  `jQuery` 都有着相同的公开 API，尽管他们在内部实现上有一些不同。

Our next releases will use a different nomenclature. As before, there will be two different released files. The successor to what is now version 1.11.1 will become jQuery Compat 3.0. The successor to jQuery 2.1.1 will be jQuery 3.0. There are two different packages on npm and Bower, but they share the same version to indicate they have the same API behavior.

我们的下一个版本将会使用一种全新的命名方式。像之前一样，仍然会有两个不同的发布文件。现在的 `1.11.1` 版本的继任者将被称之为 `jQuery Compat 3.0`。`jQuery 2.1.1` 则将由 `jQuery 3.0`来接替。在 `npm` 和 `Bower` 上(译者注: 这是目前非常流行的前端包管理工具)，它们会是两个不同的包，但它们会共享同一个版本号，来说明它们在API层面上的行为是一致的。

We’ll also be re-aligning our policy for browser support starting with these releases. The main jQuery package remains small and tight by supporting the evergreen browsers (the current and previous versions of a specific browser) that are common at the time of its release. We may support additional browsers in this package based on market share. The jQuery Compat package offers much wider browser support, but at the expense of a larger file size and potentially lower performance.

这次版本发布之后，我们也将调整对浏览器的支持策略。主 `jQuery` 包将继续保持短小精悍，并且只支持在发布之时广泛使用的常青浏览器(evergreen browsers 指的是特定浏览器的当前和此前的若干版本)。我们也会根据市场份额在这个包的基础上支持更多的浏览器。而 `jQuery Compat` 包则提供更广泛的浏览器支持，但是付出的代价就是文件变得很大，执行效率也会低一些。

Despite the big version number jump, we don’t anticipate a lot of migration issues for most current jQuery code. We’re just being good semver citizens with this version bump. Changes such as removing deprecated methods will be detected by a new version of the jQuery Migrate plugin to make them easy to find and fix. We’ll have more details on the changes in future blog posts.

尽管这一次版本号跳跃很大，但是对于大多数 `jQuery` 代码来说，我们不期望造成很多的代码迁移问题。我们在这次版本升级中可是符合 `semver` 中的好公民的标准的。诸如像移除已废弃的方法这样的改变会被新版本的 `jQuery Migrate ` 插件检测出来，这样一来，发现并且修复他们就变得容易多了。我们也会在将来的博客文章中讨论这些变化中的更多细节。

So, here’s the TL;DR for version 3.0 of the jQuery API:

下面就是一些 `jQuery API` 3.0 版本要说的内容：

* If you need support for the widest variety of browsers including IE8, Opera 12, Safari 5, and the like, use the jQuery-Compat 3.0.0 package. We recommend this version for most web sites, since it provides the best compatibility for all website visitors.
* 如果你需要支持更多更广泛的浏览器，包括诸如 `IE8, Opera 12, Safari 5` 等，请使用 `jQuery-Compat 3.0.0` 版本。我们建议大多数网站都使用这一版本，因为它为网站的来访者提供了最好的兼容性支持。
* If your web site is built only for evergreen leading-edge browsers, or is an HTML-based app contained in a webview (for example PhoneGap or Cordova) where you know which browser engines are in use, go for the jQuery 3.0.0 package.
* 如果你的网站仅仅是为了那些最先进的浏览器而建，或者仅仅是一个基于 `HTML` 的应用以嵌入一个 `web` 视图(例如: PhoneGap，Cordova)，你预先知道其使用的是哪一个浏览器解析引擎， 那就使用 `jQuery 3.0.0` 吧。
* Until we announce otherwise, both packages will contain the same public APIs in correspondingly-numbered major and minor versions. This should make it easy for developers to switch between the two and be maximally compatible with third-party jQuery plugins.
* 除非我们宣布，否则对应的主、次版本号相同的两个包都会有相同的公开 API。这样开发者就能够很容易的在两个包之间切换，并且在第三方 `jQuery` 插件中拥有最好的兼容性。

With each future release, we’ll be making both packages available on npm and bower. Both packages will also be available as single-file builds on the jQuery CDN. Using them from there is as simple as including either jquery-compat-3.0.0.js or jquery-3.0.0.js depending on your needs. We’ve talked with the folks who run Google’s CDN and they will also be supporting both packages.

未来每一个版本发布的时候，我们都会同时放到 `npm` 和 `bower` 上。两个包也会以单个文件的形式在 `jQuery CDN` 上提供。在那里使用他们和根据你自己的需要去包含 `jquery-compat-3.0.0.js` 或`jquery-3.0.0.js` 一样简便。我们也和 Google’s CDN 的运营人员谈过，他们也会为这两个包提供支持。


As we make further progress on version 3.0, we will update everyone with the details about code changes, supported browsers, and the like. Stay tuned!

随着我们在3.0版本方面工作的推进，我们会向所有人告知代码变更、浏览器支持等一切细节的更新。敬请期待吧！


> 本文根据 [Dave Methvin](http://blog.jquery.com/author/dmethvin/) 的《jQuery 3.0: The Next Generations》所译，整个译文带有自己的理解与思想，如果译得不好或有不对之处还请同行朋友指点。如需转载此译文，需注明英文出处：[http://blog.jquery.com/2014/10/29/jquery-3-0-the-next-generations/](http://blog.jquery.com/2014/10/29/jquery-3-0-the-next-generations/)

## 相关链接

* jQuery 3.0.0-alpha1: [https://code.jquery.com/jquery-3.0.0-alpha1.js](https://code.jquery.com/jquery-3.0.0-alpha1.js)
* jQuery compat 3.0.0-alpha1: [https://code.jquery.com/jquery-3.0.0-alpha1.js](https://code.jquery.com/jquery-3.0.0-alpha1.js)

## 您的鼓励是作者写作最大的动力

如果您认为本网站的文章质量不错，读后觉得收获很大，不妨小额赞助我一下，让我有动力继续写出高质量的文章：我的支付宝账号是 `sqrtthree@foxmail.com`, [点击查看二维码](http://7xl8me.com1.z0.glb.clouddn.com/alipay.JPG)