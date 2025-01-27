---
description: 使用问题工具查找并修复网站问题。
title: 查找并修复 Microsoft Edge DevTools 问题工具的问题
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 02/12/2021
ms.topic: article
ms.prod: microsoft-edge
keywords: microsoft edge、web 开发、f12 工具、开发工具
ms.openlocfilehash: e16bd926ea5bae35ad82f54ac5d1ae2028e3c59d
ms.sourcegitcommit: 6cf12643e9959873f8b5d785fd6158eeab74f424
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2021
ms.locfileid: "11398971"
---
<!-- Copyright Sam Dutton 

   Licensed under the Apache License, Version 2.0 (the "License");
   you may not use this file except in compliance with the License.
   You may obtain a copy of the License at

       https://www.apache.org/licenses/LICENSE-2.0

   Unless required by applicable law or agreed to in writing, software
   distributed under the License is distributed on an "AS IS" BASIS,
   WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
   See the License for the specific language governing permissions and
   limitations under the License.  -->  

# <a name="find-and-fix-problems-with-the-microsoft-edge-devtools-issues-tool"></a>查找并修复 Microsoft Edge DevTools 问题工具的问题  

Microsoft **Edge** DevTools 中的"问题"工具可以减少控制台的通知疲劳和**混乱。**  使用它查找浏览器检测到的问题（如 Cookie 问题和混合内容）的解决方案。  

> [!NOTE]
> 在 Microsoft Edge 84 中， **问题** 工具支持三种类型的问题：  
> *   [Cookie 问题][MDNSameSiteCookies]  
> *   [混合内容][MDNMixedContent]  
> *   [COEP 问题][W3CCOEPSpec]
> 
> Microsoft Edge DevTools 团队计划在未来版本的 Microsoft Edge 中支持更多问题类型。  

## <a name="open-the-issues-tool-in-the-devtools-drawer"></a>在 DevTools 箱中打开"问题"工具  

1.  导航到包含要修复samesite-sandbox.glitch.me的网页[][GlitchSamesiteSandbox]，例如 samesite-sandbox.glitch.me。  
1.  [打开 DevTools][DevtoolsOpen]。  
1.  :::row:::
       :::column span="":::
          选择黄色 **警告栏中** 的"转到问题"按钮。  
          
          :::image type="complex" source="../media/issues-open-issues-tab.msft.png" alt-text="在检测到问题时，转到黄色警告栏中的"问题"按钮" lightbox="../media/issues-open-issues-tab.msft.png":::
             检测到 **问题时** ，黄色警告栏中的"转到问题"按钮。  
          :::image-end:::  
       :::column-end:::
       :::column span="":::
          或者，从"**更多**工具"**菜单中选择"问题"。**  
          
          :::image type="complex" source="../media//issues-more-tools-menu.msft.png" alt-text=""更多工具"菜单中的"问题"工具" lightbox="../media//issues-more-tools-menu.msft.png":::
             **"** 更多工具 **"菜单中的"问题"** 工具  
          :::image-end:::  
       :::column-end:::
    :::row-end:::
    
1.  如有必要 **，选择"重新加载** "页面按钮。  
    
    :::image type="complex" source="../media/issues-tab-before-refresh.msft.png" alt-text="DevTools Drawer 中"重新加载"页面按钮中的"问题"工具" lightbox="../media/issues-tab-before-refresh.msft.png":::
       **DevTools** Drawer 中"重新加载"页面 **按钮中的"问题"** 工具  
    :::image-end:::  

    控制台中报告 **的问题很难** 理解，如下图中的 Cookie 警告。  根据报告的问题，可能不明确您必须执行哪些工作。  
    
    :::image type="complex" source="../media/issues-tab-after-refresh.msft.png" alt-text="具有三个 Cookie 问题的 DevTools Drawer 中的"问题"工具" lightbox="../media/issues-tab-after-refresh.msft.png":::
       **具有** 三个 Cookie 问题的 DevTools Drawer 中的问题工具  
    :::image-end:::  
    
## <a name="view-items-in-the-issues-tool"></a>查看问题工具中的项目  

DevTools Drawer 中的"问题"工具以结构化、聚合且可操作的方式显示警告。 ****  

1.  在"问题"工具 **中选择** 一个项目，获取有关如何解决问题和查找受影响资源的指南。  
    
    :::image type="complex" source="../media/issues-tab-issue-open.msft.png" alt-text="将跨站点 Cookie 标记为"问题"工具中打开的安全问题" lightbox="../media/issues-tab-issue-open.msft.png":::
       **将跨站点 Cookie 标记为**"问题"工具中打开**的安全问题**  
    :::image-end:::  
    
    每个项目都有四个组件：  
    
    *   描述问题的标题。  
    *   提供上下文和解决方案的说明。  
    *   链接到 **相应** DevTools 上下文（如网络面板）中的资源的"受影响资源"部分。  
    *   指向进一步指南的链接。  
    
1.  选择受影响 **资源中的项目** 以查看详细信息。  在下面的示例中，将 **跨站点 Cookie** 标记为安全问题会影响一个 Cookie 和两个请求。  
    
    :::image type="complex" source="../media/issues-tab-affected-resources.msft.png" alt-text="受影响的资源在"问题"工具中打开" lightbox="../media/issues-tab-affected-resources.msft.png":::
       受影响的资源在 DevTools **的"** 问题"工具中打开  
    :::image-end:::  
    
## <a name="view-issues-in-context"></a>查看上下文中的问题  

1.  选择资源链接以查看 DevTools 中相应上下文中的项目。  在下面的示例中，选择 `samesite-sandbox.glitch.me` "请求 **"** 下以显示附加到该请求的 Cookie。  
    
    :::image type="complex" source="../media/issues-tab-view-request.msft.png" alt-text="在 DevTools 网络工具中查看受影响的 Cookie" lightbox="../media/issues-tab-view-request.msft.png":::
       在 DevTools 网络工具中 **查看受影响的** Cookie  
    :::image-end:::  

1.  滚动以查看存在问题的项目：对于以下示例 `ck02` ，Cookie。  将鼠标 **悬停在 SameSite** 列上，查看 `None` 检测到问题的值。  
    
    :::image type="complex" source="../media/issues-tab-view-issue.msft.png" alt-text="DevTools 网络工具中 ck02 Cookie 的 SameSite 列中没有值" lightbox="../media/issues-tab-view-issue.msft.png":::
       `None` DevTools **网络** 工具中 Cookie 的 `ck02` SameSite **列中** 的值  
    :::image-end:::  

## <a name="getting-in-touch-with-the-microsoft-edge-devtools-team"></a>联系 Microsoft Edge 开发工具团队  

[!INCLUDE [contact DevTools team note](../includes/contact-devtools-team-note.md)]  

<!-- links -->  

[DevtoolsOpen]: ../open/index.md "打开 Microsoft Edge DevTools | Microsoft Docs"  

[GlitchSamesiteSandbox]: https://samesite-sandbox.glitch.me "SameSite cookie 测试|小故障"  

[MDNSameSiteCookies]: https://developer.mozilla.org/docs/Web/HTTP/Headers/Set-Cookie/SameSite "SameSite cookie |MDN"  
[MDNMixedContent]: https://developer.mozilla.org/docs/Web/Security/Mixed_content "混合内容|MDN"  

[W3CCOEPSpec]: https://wicg.github.io/cross-origin-embedder-policy "跨源嵌入者策略|Web Incubator 社区组"  

> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的][GoogleSitePolicies]作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ][CCA4IL]中描述的条款使用。  
> 原始页面位于 [此处，](https://developers.google.com/web/tools/chrome-devtools/issues/index) 由 [Sam.T. (\) ][SamDutton] 创作。  
[![Creative Commons License][CCby4Image]][CCA4IL]  
本作品根据[ Creative Commons Attribution 4.0 International License ][CCA4IL]获得许可。  

[CCA4IL]: https://creativecommons.org/licenses/by/4.0  
[CCby4Image]: https://i.creativecommons.org/l/by/4.0/88x31.png  
[GoogleSitePolicies]: https://developers.google.com/terms/site-policies  
[KayceBasques]: https://developers.google.com/web/resources/contributors/kaycebasques  
[SamDutton]: https://developers.google.com/web/resources/contributors/samdutton  
