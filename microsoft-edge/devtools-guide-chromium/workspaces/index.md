---
title: 编辑具有工作区的文件
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 04/27/2020
ms.topic: article
ms.prod: microsoft-edge
keywords: microsoft edge、web 开发、f12 工具、devtools
ms.openlocfilehash: 612e85b8b00a78a40e53ac5c33d187fdae174024
ms.sourcegitcommit: 5cdc1626d5581b79c0f2ac4ea62e7f1974ebfa57
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/27/2020
ms.locfileid: "10601848"
---
<!-- Copyright Kayce Basques 

   Licensed under the Apache License, Version 2.0 (the "License");
   you may not use this file except in compliance with the License.
   You may obtain a copy of the License at

       https://www.apache.org/licenses/LICENSE-2.0

   Unless required by applicable law or agreed to in writing, software
   distributed under the License is distributed on an "AS IS" BASIS,
   WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
   See the License for the specific language governing permissions and
   limitations under the License.  -->  







# 编辑具有工作区的文件   



> [!NOTE]
> 本教程的目标是提供有关设置和使用工作区的动手练习，以便你可以在自己的项目中使用工作区。  你可以在启用工作区后将对源代码所做的更改保存在你的本地计算机上 DevTools 中。  

> [!CAUTION]
> **先决条件**：在开始本教程之前，你应该知道如何：  
> *   [使用 HTML、CSS 和 JavaScript 构建网页][MDNWebGettingStarted]  
> *   [使用 DevTools 对 CSS 进行基本更改][DevToolsCssIndex]  
> *   [运行本地 HTTP web 服务器][MDNSimpleLocalHTTPServer]  

## 概述   

工作区使你能够将在 Devtools 中所做的更改保存到计算机上同一文件的本地副本。  例如，假设：  

*   您的桌面网站上有您的网站的源代码。  
*   您从源代码目录运行本地 web 服务器，以便可以在该网站上访问 `localhost:8080` 。  
*   您 `localhost:8080` 在 Microsoft Edge 中打开，并且您使用 DevTools 更改网站的 CSS。  

启用了工作区后，在 DevTools 内所做的 CSS 更改将保存到桌面上的源代码中。  

## 限制   

如果你使用的是新式框架，则可能会将你的源代码从易于维护的格式转换为尽可能快地运行的格式。  
工作区通常能够将经过优化的代码映射回原始源代码以及[源映射][TreehouseBlogSourceMaps]的帮助。  但是，在如何使用源映射的框架之间存在许多变化。  Devtools 只支持所有变体。  

已知工作区不能与这些框架配合使用：  

*   创建反应应用  

<!-- If you run into issues while using Workspaces with your framework of choice, or you get it working after some custom configuration, please [start a thread in the mailing list][AlphabetGroupsAlphabetBrowserDevTools] or [ask a question on Stack Overflow][StackOverflowAlphabetBrowserDevTools] to share your knowledge with the rest of the DevTools community.  -->  

## 相关功能：本地覆盖   

**本地重写**是另一个类似于工作区的 DevTools 功能。  如果想要试验对页面所做的更改，并且需要在页面加载期间查看这些更改，但又不介意将更改映射到页面的源代码，请使用本地替代。  

<!--Todo: add section when content is ready  -->  

## 步骤1：设置   

完成本教程，获取有关工作区的实际体验。  

### 设置演示   

1.  [打开演示][GlitchWorkspacesDemo]。  <!--In the top-left of the editor, a randomly-generated project name is displayed.  -->  
    
    > ##### 图 1  
    > ![故障项目][ImageGlitchProject]  
    
    <!--1.  Click the project name.  -->
    <!--1.  Select **Advanced Options** > **Download Project**.  
    
    > ##### Figure 2  
    > The Download Project button  
    > ![The Download Project button][ImageDownloadProjectButton]  
    -->
    <!--1.  Close the tab.  -->
    <!--1.  Unzip the source code and move the unzipped `app` directory to your desktop.  For the rest of this tutorial this directory is referred to as `~/Desktop/app`.  -->  
    
1.  `app`在桌面上创建目录。  在目录中保存文件的副本 `workspaces-demo` 。  对于本教程的其余部分，此目录称为 `~/Desktop/app` 。  
1.  在中启动本地 web 服务器 `~/Desktop/app` 。  下面是用于启动的一些示例代码 `SimpleHTTPServer` ，但你可能会使用所需的任何服务器。  
    
    ```bash
    cd ~/Desktop/app
    python -m SimpleHTTPServer # Python 2
    ```  
    
    ```bash
    cd ~/Desktop/app
    python -m http.server # Python 3
    ```  
    
1.  在 Microsoft Edge 中打开一个选项卡，然后转到本地托管的网站版本。  你应该能够使用诸如或之类的 URL 访问它 `localhost:8080` `http://0.0.0.0:8080` 。  确切的[端口号][WikiPortURLs]可能不同。  
    
    > ##### 图 2  
    > 演示  
    > ![演示][ImageDemo]  

### 设置 DevTools   

1.  按 `Control` + `Shift` + `J` \ （Windows \）或 `Command` + `Option` + `J` \ （macOS \）打开 DevTools 的**控制台**面板。  
    
    > ##### 图 3  
    > **控制台**面板  
    > ![控制台面板][ImageConsolePanel]  

1.  单击 "**源**" 选项卡。  
1.  单击 "**文件系统**" 选项卡。  
    
    > ##### 图 4  
    > "**文件系统**" 选项卡  
    > ![文件系统选项卡][ImageFilesystem]  

1.  单击 "**将文件夹添加到工作区**"。  
1.  选择 `~/Desktop/app` 。  
1.  单击 "**允许**" 以授予 DevTools 读取和写入目录的权限。  
    在 "**文件系统**" 选项卡中，"，" 旁边有一个绿点 `index.html` `script.js` `styles.css` 。  这些绿色圆点意味着 DevTools 已建立了页面的网络资源与中的文件之间的映射 `~/Desktop/app` 。  
    
    > ##### 图 5  
    > "**文件系统**" 选项卡现在显示本地文件和网络文件之间的映射  
    > ![文件系统选项卡现在显示本地文件和网络文件之间的映射][ImageMapping]  

## 步骤2：将 CSS 更改保存到磁盘   

1.  打开 `styles.css`。  
    
    > [!NOTE]
    >`color`元素的属性 `h1` 设置为 `fuchsia` 。
    
    > ##### 图 6  
    > `styles.css`在文本编辑器中查看  
    > ![在文本编辑器中查看样式 .css][ImageStylesFuchsia]  


1.  单击 "**元素**" 选项卡。  
1.  将元素的属性值更改 `color` `<h1>` 为你的常用颜色。  
    请记住，你需要单击 `<h1>` **DOM 树**中的元素，才能在 "**样式**" 窗格中查看应用到它的 CSS 规则。  旁边的绿色圆点 `styles.css:1` 表示你所做的任何更改都将映射到 `~/Desktop/app/styles.css` 。  
    
    > ##### 图 7  
    > 文件链接的绿色指示器  
    > ![文件链接的绿色指示器][ImageStylesGreen]  

1.  `styles.css`再次在文本编辑器中打开。  该 `color` 属性现在设置为你的常用颜色。  
1.  重新加载页面。  元素的颜色 `<h1>` 仍设置为你的常用颜色。  这是因为当你进行更改时，DevTools 将更改保存到了磁盘。  然后，当你重新加载页面时，你的本地服务器从磁盘向修改的文件副本提供服务。  

## 步骤3：将 HTML 更改保存到磁盘   

### 更改 "元素" 面板中的 HTML  

你可以更改 "元素" 面板中的 HTML，但对 DOM 树所做的更改不会保存到磁盘，并且只会影响当前浏览器会话。  
DOM 树不是 HTML。  

<!--### Try changing HTML from the Elements panel   

> [!WARNING]
> The workflow that you are about to try does not work.  You are trying it now so that you do not waste time later trying to figure out why it is not working.  

1.  Click the **Elements** tab.  
1.  Double click the text content of the `h1` element, which says `Workspaces Demo`, and replace it with `I ❤️  Cake`.  
    
    > ##### Old Figure 9  
    > Attempting to change HTML from the **DOM Tree** of the **Elements** panel  
    > ![Attempting to change HTML from the DOM Tree of the Elements panel][ImageElementsCake]  

1.  Open `~/Desktop/app/index.html` in a text editor.  The change that you just made does not appear.  
1.  Reload the page.  The page reverts to its original title.  

#### Optional: Why it is not working   

> [!NOTE]
> This section describes why the workflow from [Try changing HTML from the Elements panel](#try-changing-html-from-the-elements-panel) does not work.  You should skip this section if you do not care why.  

*   The tree of nodes that you see on the **Elements** panel represents the [DOM][MDNWebAPIsDOM] of the page.  
*   To display a page, a browser fetches HTML over the network, parses the HTML, and then converts it into a tree of DOM nodes.  
*   If the page has any JavaScript, that JavaScript may add, delete, or change DOM nodes.  CSS may change the DOM, too, using the [`content`][MDNCSSContent] property.  
*   The browser eventually uses the DOM to determine what content it should present to browser users.  
*   Therefore, the final state of the page that users see may be very different from the HTML that the browser fetched.  
*   This makes it difficult for DevTools to resolve where a change made in the **Elements** panel should be saved, because the DOM is affected by HTML, JavaScript, and CSS.  

In short, the **DOM Tree** `!==` HTML.  
-->
### 从 "源" 面板更改 HTML   

如果要保存对页面的 HTML 所做的更改，请使用 "**源**" 面板执行此操作。  

1.  单击 "**源**" 选项卡。  
1.  单击 "**页面**" 选项卡。  
1.  单击 " **（索引）**"。  将打开页面的 HTML。  
1.  用 `<h1>I ❤️  Cake</h1>` 取代 `<h1>Workspaces Demo</h1>`。  请参阅[图 8](#figure-8)。  
1.  按 `Control` + `S` \ （Windows \）或 `Command` + `S` \ （macOS \）保存所做的更改。  
1.  重新加载页面。  该 `<h1>` 元素仍显示新文本。  
    
    > ##### 图 8  
    > 第12行已设置为 `I ❤️  Cake`  
    > ![从 "源" 面板更改 HTML][ImageSourcesCakeHTML]  

1.  打开 `~/Desktop/app/index.html`。  `<h1>`元素包含新文本。  

## 步骤4：将 JavaScript 更改保存到磁盘   

"**源**" 面板也是对 JavaScript 进行更改的位置。  但有时你需要在对网站进行更改时访问其他面板，如 "**元素**" 面板或 "**控制台**" 面板。  有一种方法可使 "**源**" 面板与其他面板一起打开。  

1.  单击 "**元素**" 选项卡。  
1.  按 `Control` + `Shift` + `P` \ （Windows \）或 `Command` + `Shift` + `P` \ （macOS \）。  此时将打开 "**命令" 菜单**。  
1.  键入 `QS` ，然后选择 "**显示快速源**"。  在 DevTools 窗口的底部，现在有一个 "**快速源**" 选项卡。 该选项卡显示的内容 `index.html` ，这是您在 "**源**" 面板中编辑的最后一个文件。  "**快速源**" 选项卡从 "**源**" 面板提供编辑器，以便您可以在打开其他面板时编辑文件。  
    
    > ##### 图 9  
    > 使用 "**命令" 菜单**打开 "**快速源**" 选项卡  
    > ![使用命令菜单打开 "快速源" 选项卡][ImageCommandMenuQuickSource]  

1.  按 `Control` + `P` \ （Windows \）或 `Command` + `P` \ （macOS \）打开 "**打开文件**" 对话框。  请参阅[图 10](#figure-10)。  
1.  键入 `script` ，然后选择 "**应用/脚本 .js**"。  
    
    > ##### 图 10  
    > `script.js`使用 "**打开文件**" 对话框打开  
    > ![打开 script 使用 "打开文件" 对话框][ImageOpenFileDialog]  
    
    > [!NOTE]
    > `Save Changes To Disk With Workspaces`演示中的链接会定期设置样式。  
    
1.  使用 "**快速源**" 选项卡将以下代码添加到**script**的底部。  
    
    ```javascript
    console.log('greetings from script.js');
    document.querySelector('a').style = 'font-style:italic';
    ```  
    
1.  按 `Control` + `S` \ （Windows \）或 `Command` + `S` \ （macOS \）保存所做的更改。  
1.  重新加载页面。  
    
    > [!NOTE]
    > 页面上的链接现在为斜体。
    
    > ##### 图 11  
    > 页面上的链接现在为斜体  
    > ![页面上的链接现在为斜体][ImageScriptItalic]  

## 后续步骤   

使用在本教程中了解到的功能在您自己的项目中设置工作区。  <!-- If you run into any issues or are able to get it working after some custom configuration, please [start a thread in the mailing list][AlphabetGroupsAlphabetBrowserDevTools] or [ask a question on Stack Overflow][StackOverflowAlphabetBrowserDevTools] to share your knowledge with the rest of the DevTools community.  -->

 <!--  -->



<!-- 
If you have more feedback on these topics or anything else, please use any of the channels below:
*   [Mailing List][AlphabetGroupsAlphabetBrowserDevTools]  
*   [Twitter][TwitterAlphabetBrowserDevTools]  
-->

<!-- image links -->  

[ImageGlitchProject]: /microsoft-edge/devtools-guide-chromium/media/workspaces-glitch-workspaces-demo-source.msft.png "图1：具有随机生成的名称的故障项目"  
<!--[ImageDownloadProjectButton]: /microsoft-edge/devtools-guide-chromium/media/workspaces-glitch-advanced-options-download-project.msft.png "old Figure 2: The Download Project button"  -->  
[ImageDemo]：/microsoft-edge/devtools-guide-chromium/media/workspaces-workspaces-demo.msft.png "图2：" 演示 "  
[ImageConsolePanel]：/microsoft-edge/devtools-guide-chromium/media/workspaces-workspaces-demo-console.msft.png "图3：控制台面板"  
[ImageFilesystem]：/microsoft-edge/devtools-guide-chromium/media/workspaces-workspaces-demo-sources-filesystem.msft.png "图4： Filesystem 选项卡"  
[ImageMapping]：/microsoft-edge/devtools-guide-chromium/media/workspaces-workspaces-demo-sources-filesystem-folder.msft.png "图5： Filesystem 选项卡现在显示本地文件和网络文件之间的映射"  
[ImageStylesFuchsia]：/microsoft-edge/devtools-guide-chromium/media/workspaces-workspaces-demo-sources-filesystem-css.msft.png "图6：在文本编辑器中查看样式 .css"  
[ImageStylesGreen]：/microsoft-edge/devtools-guide-chromium/media/workspaces-workspaces-demo-elements-styles-css.msft.png "图7：文件链接的绿色指示器"  
[ImageSourcesCakeHTML]：/microsoft-edge/devtools-guide-chromium/media/workspaces-workspaces-demo-sources-page-h1.msft.png "图8：从" 源 "面板更改 HTML"  
<!--[ImageElementsCake]: /microsoft-edge/devtools-guide-chromium/media/workspaces-workspaces-demo-change-h1.msft.png "Old Figure 9: Attempting to change HTML from the DOM Tree of the Elements panel"  -->  
[ImageCommandMenuQuickSource]：/microsoft-edge/devtools-guide-chromium/media/workspaces-workspaces-demo-search-show-quick-source.msft.png "图9：使用命令菜单打开" 快速源 "选项卡  
[ImageOpenFileDialog]：/microsoft-edge/devtools-guide-chromium/media/workspaces-workspaces-demo-search-script.msft.png "图10：使用" 打开文件 "对话框打开 script  
[ImageScriptItalic]：/microsoft-edge/devtools-guide-chromium/media/workspaces-workspaces-demo-elements-styles-quick-source-script.msft.png "图11：页面上的链接现在为斜体"  

<!-- links -->  

[DevToolsCssIndex]: /microsoft-edge/devtools-guide-chromium/css/index "查看和更改 CSS 入门"  

<!--[LocalOverrides]: ../whats-new/2018/01/devtools#overrides -->  

<!--[AlphabetGroupsAlphabetBrowserDevTools]: https://groups.alphabet.com/forum/#!forum/alphabet-browser-developer-tools "Alphabet Browser DevTools - Alphabet Groups"  -->  

[GlitchWorkspacesDemo]: https://glitch.com/edit/#!/microsoft-edge-chromium-devtools?path=workspaces-demo/index.html:1:0 "工作区演示文件 |故障"  

[MDNCSSContent]: https://developer.mozilla.org/docs/Web/CSS/content "内容-CSS：级联样式表 |MDN"  
[MDNWebGettingStarted]: https://developer.mozilla.org/docs/Learn/Getting_started_with_the_web "Web 入门 |MDN"  
[MDNSimpleLocalHTTPServer]: https://developer.mozilla.org/docs/Learn/Common_questions/set_up_a_local_testing_server#Running_a_simple_local_HTTP_server "运行一个简单的本地 HTTP 服务器 |MDN"  
[MDNWebAPIsDOM]: https://developer.mozilla.org/docs/Web/API/Document_Object_Model/Introduction "DOM-Web Api 简介 |MDN"  

<!--[StackOverflowAlphabetBrowserDevTools]: https://stackoverflow.com/questions/ask?tags=alphabet-browser-devtools "Alphabet Browser DevTools - Stack Overflow"  -->

[TreehouseBlogSourceMaps]: https://blog.teamtreehouse.com/introduction-source-maps "源地图简介 |Treehouse 博客"  

<!-- [TwitterAlphabetBrowserDevTools]: https://twitter.com/alphabetbrowserdevtools "Alphabet Browser DevTools \(@AlphabetBrowserDevTools\) | Twitter"  -->

[WikiPortURLs]: https://en.wikipedia.org/wiki/Port_(computer_networking)#Use_in_URLs "端口 \ （计算机网络 \）-维基百科"  

> [!NOTE]
> 此页面的某些部分是基于[由 Google][GoogleSitePolicies]创建和共享的工作的修改，并根据 "[创造性 Commons 归属4.0 国际许可证][CCA4IL]" 中所述的条款使用。  
> 原始页面位于[此处](https://developers.google.com/web/tools/chrome-devtools/workspaces/index)，由[Kayce Basques][KayceBasques] \ （技术作者、Chrome DevTools \ & Lighthouse \）创作。  

[![创造性 Commons 许可证][CCby4Image]][CCA4IL]  
此作品通过 [Creative Commons Attribution 4.0 国际许可证][CCA4IL]获得许可。  

[CCA4IL]: https://creativecommons.org/licenses/by/4.0  
[CCby4Image]: https://i.creativecommons.org/l/by/4.0/88x31.png  
[GoogleSitePolicies]: https://developers.google.com/terms/site-policies  
[KayceBasques]: https://developers.google.com/web/resources/contributors/kaycebasques  