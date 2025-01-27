---
description: 了解如何将 DevTools 中所做的更改保存到磁盘。
title: 使用工作区编辑文件
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 02/12/2021
ms.topic: article
ms.prod: microsoft-edge
keywords: microsoft edge、web 开发、f12 工具、开发工具
ms.openlocfilehash: 17f9ced15dbacd62c9ffe40e4af889925a8155fb
ms.sourcegitcommit: 6cf12643e9959873f8b5d785fd6158eeab74f424
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2021
ms.locfileid: "11399244"
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

# <a name="edit-files-with-workspaces"></a>使用工作区编辑文件  

> [!NOTE]
> 本教程的目标是提供设置和使用工作区的动手实践，以便可以在自己的项目中使用工作区。  在启用工作区后，可以在本地计算机上保存对开发人员Tools 中源代码所做的更改。  

> [!IMPORTANT]
> **先决条件：** 在开始本教程之前，你应该知道如何执行以下操作。  
> 
> *   [使用 html、CSS 和 JavaScript 生成网页][MDNWebGettingStarted]  
> *   [使用 DevTools 对 CSS 进行基本更改][DevToolsCssIndex]  
> *   [运行本地 HTTP Web 服务器][MDNSimpleLocalHTTPServer]  

## <a name="overview"></a>概述  

工作区使您能够将你在 Devtools 中做出更改保存到计算机上同一文件的本地副本。  对于本教程，计算机上应具有以下设置。  

*   桌面上具有网站的源代码。  
*   您从源代码目录运行本地 Web 服务器，以便可从中访问该网站 `localhost:8080` 。  
*   你在 `localhost:8080` Microsoft Edge 中打开，并且正在使用 DevTools 更改网站的 CSS。  

启用 Workspaces 后，你在 DevTools 中所做的更改将保存到桌面上的源代码中。  

## <a name="limitations"></a>限制  

如果你使用的是新式框架，它可能会将源代码从易于维护的格式转换为经过优化以尽快运行的格式。  

工作区通常能够在源映射的帮助下将优化的代码映射回原始 [源代码][TreehouseBlogSourceMaps]。  但是，在框架之间，每个框架使用源映射时存在很大差异。  Devtools 仅支持所有变体。  

工作区已知无法与以下框架一起工作。  

*   创建 React 应用  

    <!-- If you run into issues while using Workspaces with your framework of choice, or you get it working after some custom configuration, please [start a thread in the mailing list][AlphabetGroupsAlphabetBrowserDevTools] or [ask a question on Stack Overflow][StackOverflowAlphabetBrowserDevTools] to share your knowledge with the rest of the DevTools community.  -->  
    
## <a name="related-feature-local-overrides"></a>相关功能：本地替代  

**本地覆盖** 是另一个类似于 Workspaces 的 DevTools 功能。  当您要尝试对网页所做的更改，并且需要跨网页加载显示更改，但您不关心将更改映射到网页的源代码时，请使用本地覆盖。  

<!--Todo: add section when content is ready  -->  

## <a name="step-1-set-up"></a>步骤 1：设置  

完成以下操作，获取工作区的动手体验。  

### <a name="set-up-the-demo"></a>设置演示  

1.  [打开演示][GlitchWorkspacesDemo]。  <!--In the top-left of the editor, a randomly-generated project name is displayed.  -->  
    
    :::image type="complex" source="../media/workspaces-glitch-workspaces-demo-source.msft.png" alt-text="小故障项目" lightbox="../media/workspaces-glitch-workspaces-demo-source.msft.png":::
       小故障项目  
    :::image-end:::  
    
    <!--1.  Choose the project name.  -->  
    <!--1.  Choose **Advanced Options** > **Download Project**.  
    
    :::image type="complex" source="../media/workspaces-glitch-advanced-options-download-project.msft.png" alt-text="The Download Project button" lightbox="../media/workspaces-glitch-advanced-options-download-project.msft.png":::
       The Download Project button  
    :::image-end:::  

    -->  
    <!--1.  Close the tab.  -->  
    <!--1.  Unzip the source code and move the unzipped `app` directory to your desktop.  For the rest of this tutorial the unzipped directory is referred to as `~/Desktop/app`.  -->  
    
1.  在 `app` 桌面上创建目录。  将目录中的文件副本 `workspaces-demo` 保存到 `app` 目录中。  对于本教程的其余部分，目录称为 `~/Desktop/app` 。  
1.  在 中启动本地 Web 服务器 `~/Desktop/app` 。  下面是一些用于启动的示例代码，但 `SimpleHTTPServer` 您可以使用您喜欢的任何服务器。  
    
    :::row:::
       :::column span="":::
          ```bash
          cd ~/Desktop/app
          python -m SimpleHTTPServer # Python 2
          ```  
       :::column-end:::  
       :::column span="":::
          ```bash
          cd ~/Desktop/app
          python -m http.server # Python 3
          ```  
       :::column-end:::
    :::row-end:::  
    
1.  在 Microsoft Edge 中打开一个选项卡，然后导航到本地托管的网站版本。  你应该能够使用 URL（如 或 `localhost:8080` ）来访问 `http://0.0.0.0:8080` 它。  确切的 [端口号][WikiPortURLs] 可能不同。  
    
    :::image type="complex" source="../media/workspaces-workspaces-demo.msft.png" alt-text="演示" lightbox="../media/workspaces-workspaces-demo.msft.png":::
       演示  
    :::image-end:::  
    
### <a name="set-up-devtools"></a>设置 DevTools  

1.  选择 `Control` + `Shift` + `J` \ (Windows、Linux\) 或 `Command` + `Option` + `J` \ (macOS\) 打开 DevTools**** 的控制台面板。  
    
    :::image type="complex" source="../media/workspaces-workspaces-demo-console.msft.png" alt-text="控制台面板" lightbox="../media/workspaces-workspaces-demo-console.msft.png":::
       控制台**面板**  
    :::image-end:::  
    
1.  选择 **"源"** 工具。  
1.  选择 **"文件系统"** 面板。  
    
    :::image type="complex" source="../media/workspaces-workspaces-demo-sources-filesystem.msft.png" alt-text="文件系统面板" lightbox="../media/workspaces-workspaces-demo-sources-filesystem.msft.png":::
       **文件系统**面板  
    :::image-end:::  
    
1.  选择 **"将文件夹添加到工作区"。**  
1.  键入 `~/Desktop/app`。  
1.  Choose **Allow** to give DevTools permission to read and write to the directory.  
    在 **Filesystem** 面板中，现在 ，和 旁边有一个 `index.html` 绿色 `script.js` 点 `styles.css` 。  这些绿色点表示 DevTools 已建立页面的网络资源和中文件之间的映射 `~/Desktop/app` 。  
    
    :::image type="complex" source="../media/workspaces-workspaces-demo-sources-filesystem-folder.msft.png" alt-text="Filesystem 面板现在显示本地文件和网络文件之间的映射" lightbox="../media/workspaces-workspaces-demo-sources-filesystem-folder.msft.png":::
       **Filesystem**面板现在显示本地文件和网络文件之间的映射  
    :::image-end:::  
    
## <a name="step-2-save-a-css-change-to-disk"></a>步骤 2：将 CSS 更改保存到磁盘  

1.  打开 `styles.css`。  
    
    > [!NOTE]
    > 元素 `color` 的属性 `h1` 设置为 `fuchsia` 。  
    
    :::image type="complex" source="../media/workspaces-workspaces-demo-sources-filesystem-css.msft.png" alt-text="在文本编辑器中查看 styles.css" lightbox="../media/workspaces-workspaces-demo-sources-filesystem-css.msft.png":::
       在 `styles.css` 文本编辑器中查看  
    :::image-end:::  
    
1.  选择 **"元素"** 工具。  
1.  将元素的 `color` 属性值 `<h1>` 更改为你最喜爱的颜色。  
    请记住，您需要选择 DOM 树中的元素，才能在"样式"窗格中显示应用于该元素的 `<h1>` CSS**** 规则。 ****  旁边的绿色点表示你进行的任何更改 `styles.css:1` 都映射到 `~/Desktop/app/styles.css` 。  
    
    :::image type="complex" source="../media/workspaces-workspaces-demo-elements-styles-css.msft.png" alt-text="文件链接的绿色指示器" lightbox="../media/workspaces-workspaces-demo-elements-styles-css.msft.png":::
       文件链接的绿色指示器  
    :::image-end:::  
    
1.  在 `styles.css` 文本编辑器中再次打开。  属性 `color` 现在设置为你最喜爱的颜色。  
1.  刷新页面。  元素的颜色 `<h1>` 仍设置为你最喜爱的颜色。  更改将在整个刷新中保留，因为进行更改时 DevTools 将更改保存到磁盘。  然后，刷新页面时，本地服务器从磁盘提供文件的修改副本。  
    
## <a name="step-3-save-an-html-change-to-disk"></a>步骤 3：将 HTML 更改保存到磁盘  

### <a name="change-html-from-the-elements-panel"></a>从元素面板更改 HTML  

你可以从元素面板对 html 进行更改，但是对 DOM 树所做的更改不会保存到磁盘，并且只影响当前浏览器会话。  

DOM 树不是 html。  

<!--### Try changing HTML from the Elements panel  

> [!WARNING]
> The workflow that you are about to try does not work.  You are trying it now so that you do not waste time later trying to figure out why it is not working.  

1.  Choose the **Elements** tool.  
1.  Choose and edit the text content of the `h1` element, which says `Workspaces Demo`, and replace it with `I ❤️  Cake`.  
    
    :::image type="complex" source="../media/workspaces-workspaces-demo-change-h1.msft.png" alt-text="Attempt to change html from the DOM Tree of the Elements panel" lightbox="../media/workspaces-workspaces-demo-change-h1.msft.png":::
       Attempt to change html from the DOM Tree of the **Elements** tool  
    :::image-end:::  
    
1.  Open `~/Desktop/app/index.html` in a text editor.  The change that you just made does not appear.  
1.  Refresh the page.  The page reverts to the original title.  
    
#### Optional: Why it is not working  

> [!NOTE]
> This section describes why the workflow from [Try changing html from the Elements panel](#try-changing-html-from-the-elements-panel) does not work.  You should skip this section if you do not care why.  

*   The tree of nodes that are displayed on the **Elements** tool represents the [DOM][MDNWebAPIsDOM] of the page.  
*   To display a page, a browser fetches html over the network, parses the html, and then converts it into a tree of DOM nodes.  
*   If the page has any JavaScript, that JavaScript may add, delete, or change DOM nodes.  CSS may change the DOM, too, using the [`content`][MDNCSSContent] property.  
*   The browser eventually uses the DOM to determine what content it should present to browser users.  
*   Therefore, the final state of the webpage displayed for users may be very different from the html that the browser fetched.  
*   This makes it difficult for DevTools to resolve where a change made in the **Elements** tool should be saved, because the DOM is affected by HTML, JavaScript, and CSS.  

In short, the **DOM Tree** `!==` HTML.  
-->  

### <a name="change-html-from-the-sources-panel"></a>从"源"面板更改 HTML  

如果要保存对页面 html 的更改，则使用"源"**面板执行。**  

1.  选择 **"源"** 工具。  
1.  选择 **"页面"** 面板。  
1.  选择** (索引) 。 **  将打开页面的 HTML。  
1.  用 `<h1>I ❤️  Cake</h1>` 取代 `<h1>Workspaces Demo</h1>`。  查看下图。  
1.  选择 `Control` + `S` \ (Windows、Linux\) 或 `Command` + `S` \ (macOS\) 保存更改。  
1.  刷新页面。  该 `<h1>` 元素仍在显示新文本。  
    
    :::image type="complex" source="../media/workspaces-workspaces-demo-sources-page-h1.msft.png" alt-text="从"源"面板更改 HTML" lightbox="../media/workspaces-workspaces-demo-sources-page-h1.msft.png":::
       从"源" **面板更改** HTML  
    :::image-end:::  
    
1.  打开 `~/Desktop/app/index.html`。  元素 `<h1>` 包含新文本。  
    
## <a name="step-4-save-a-javascript-change-to-disk"></a>步骤 4：将 JavaScript 更改保存到磁盘  

源 **面板** 也是对 JavaScript 进行更改的位置。  但有时，你需要访问其他面板，如 **元素** 工具或 **控制台** 面板，同时对网站进行更改。  有一种方法可以与其他面板一**** 起打开"源"面板。  

1.  选择 **"元素"** 工具。  
1.  选择 `Control` + `Shift` + `P` \ (Windows、Linux\) `Command` + `Shift` + `P` 或 \ (macOS\) 。  命令 **菜单** 将打开。  
1.  键入 `QS` ，然后选择"**显示快速源"。**  在 DevTools 窗口底部，现在有一个 **快速源** 面板。  面板显示内容，这是你在"源"面板中编辑的最后 `index.html` **一** 个文件。  快速**源**面板提供了"源"面板中的编辑器****，以便您可以在打开其他面板的同时编辑文件。  
    
    :::image type="complex" source="../media/workspaces-workspaces-demo-search-show-quick-source.msft.png" alt-text="使用命令菜单打开快速源面板" lightbox="../media/workspaces-workspaces-demo-search-show-quick-source.msft.png":::
       使用 **命令菜单打开快速** 源 **面板**  
    :::image-end:::  
    
1.  选择 `Control` + `P` \ (Windows、Linux\) 或 `Command` + `P` \ (macOS\) 打开 **"打开文件"** 对话框。  查看下图。  
1.  键入 `script` ，然后选择**应用/script.js。 **  
    
    :::image type="complex" source="../media/workspaces-workspaces-demo-search-script.msft.png" alt-text="使用script.js打开文件对话框打开" lightbox="../media/workspaces-workspaces-demo-search-script.msft.png":::
       使用 `script.js` "打开 **文件"对话框** 打开  
    :::image-end:::  
    
    > [!NOTE]
    > 演示 `Save Changes To Disk With Workspaces` 中的链接会定期设置样式。  
    
1.  使用"快速源"**面板script.js下面的****代码。**  
    
    ```javascript
    console.log('greetings from script.js');
    document.querySelector('a').style = 'font-style:italic';
    ```  
    
1.  选择 `Control` + `S` \ (Windows、Linux\) 或 `Command` + `S` \ (macOS\) 保存更改。  
1.  刷新页面。  
    
    > [!NOTE]
    > 页面上的链接现在为 italicized。  
    
    :::image type="complex" source="../media/workspaces-workspaces-demo-elements-styles-quick-source-script.msft.png" alt-text="页面上的链接现在为 italicized" lightbox="../media/workspaces-workspaces-demo-elements-styles-quick-source-script.msft.png":::
       页面上的链接现在为 italicized  
    :::image-end:::  
    
## <a name="next-steps"></a>后续步骤  

使用本教程中学到的内容在您自己的项目中设置工作区。  <!-- If you run into any issues or are able to get it working after some custom configuration, please [start a thread in the mailing list][AlphabetGroupsAlphabetBrowserDevTools] or [ask a question on Stack Overflow][StackOverflowAlphabetBrowserDevTools] to share your knowledge with the rest of the DevTools community.  -->  

<!--  
If you have more feedback on the topics or anything else, please use any of the channels below:  

*   [Mailing List][AlphabetGroupsAlphabetBrowserDevTools]  
*   [Twitter][TwitterAlphabetBrowserDevTools]  -->  

## <a name="getting-in-touch-with-the-microsoft-edge-devtools-team"></a>联系 Microsoft Edge 开发工具团队  

[!INCLUDE [contact DevTools team note](../includes/contact-devtools-team-note.md)]  

<!-- links -->  

[DevToolsCssIndex]: ../css/index.md "开始查看和更改 CSS |Microsoft Docs"  

<!--[LocalOverrides]: ../whats-new/2018/01/devtools#overrides -->  

<!--[AlphabetGroupsAlphabetBrowserDevTools]: https://groups.alphabet.com/forum/#!forum/alphabet-browser-developer-tools "Alphabet Browser DevTools - Alphabet Groups"  -->  

[GlitchWorkspacesDemo]: https://glitch.com/edit/#!/microsoft-edge-chromium-devtools?path=workspaces-demo/index.html:1:0 "工作区演示文件|小故障"  

[MDNCSSContent]: https://developer.mozilla.org/docs/Web/CSS/content "内容 - CSS：级联样式表|MDN"  
[MDNWebGettingStarted]: https://developer.mozilla.org/docs/Learn/Getting_started_with_the_web "Web 应用程序入门|MDN"  
[MDNSimpleLocalHTTPServer]: https://developer.mozilla.org/docs/Learn/Common_questions/set_up_a_local_testing_server#Running_a_simple_local_HTTP_server "运行简单的本地 HTTP 服务器|MDN"  
[MDNWebAPIsDOM]: https://developer.mozilla.org/docs/Web/API/Document_Object_Model/Introduction "DOM 简介 - Web API |MDN"  

<!--[StackOverflowAlphabetBrowserDevTools]: https://stackoverflow.com/questions/ask?tags=alphabet-browser-devtools "Alphabet Browser DevTools - Stack Overflow"  -->

[TreehouseBlogSourceMaps]: https://blog.teamtreehouse.com/introduction-source-maps "源地图视图|Treehouse 博客"  

<!-- [TwitterAlphabetBrowserDevTools]: https://twitter.com/alphabetbrowserdevtools "Alphabet Browser DevTools \(@AlphabetBrowserDevTools\) | Twitter"  -->

[WikiPortURLs]: https://en.wikipedia.org/wiki/Port_(computer_networking)#Use_in_URLs "Port \ (computer networking\) - Wikipedia"  

> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的][GoogleSitePolicies]作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ][CCA4IL]中描述的条款使用。  
> 原始页面位于[此处](https://developers.google.com/web/tools/chrome-devtools/workspaces/index)，由 [Kayce Basques][KayceBasques]\（Chrome DevTools \& Lighthouse 的技术作家\）撰写。  

[![Creative Commons License][CCby4Image]][CCA4IL]  
本作品根据[ Creative Commons Attribution 4.0 International License ][CCA4IL]获得许可。  

[CCA4IL]: https://creativecommons.org/licenses/by/4.0  
[CCby4Image]: https://i.creativecommons.org/l/by/4.0/88x31.png  
[GoogleSitePolicies]: https://developers.google.com/terms/site-policies  
[KayceBasques]: https://developers.google.com/web/resources/contributors/kaycebasques  
