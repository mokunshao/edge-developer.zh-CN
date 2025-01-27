---
description: 如何从 Microsoft Edge DevTools 的应用程序面板查看应用程序缓存数据。
title: 使用 Microsoft Edge DevTools 查看应用程序缓存数据
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 12/11/2020
ms.topic: article
ms.prod: microsoft-edge
keywords: microsoft edge、web 开发、f12 工具、devtools
ms.openlocfilehash: 3d73047a8332e4d6cae5f7411f968a7dfe4c3738
ms.sourcegitcommit: a35a6b5bbc21b7df61d08cbc6b074b5325ad4fef
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/17/2020
ms.locfileid: "11230780"
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

# 使用 Microsoft Edge DevTools 查看应用程序缓存数据  

> [!WARNING]
> 应用程序缓存 API [正在从 Web 平台中删除][HTMLStandardOfflineWebApplications]。  

本指南演示如何使用 [Microsoft Edge DevTools][MicrosoftEdgeDevTools] 检查 [应用程序缓存][MDNWebAPIsWindowApplicationCache] 资源。  

## 查看应用程序缓存数据  

1.  选择 **"源"** 选项卡以打开 **"源"** 面板。  清单 **窗格** 通常默认打开。  
    
    :::image type="complex" source="../media/storage-application-manifest.msft.png" alt-text="清单窗格" lightbox="../media/storage-application-manifest.msft.png":::
       清单**窗格**  
    :::image-end:::  

1.  展开 **"应用程序缓存"** 部分，然后选择一个缓存以查看资源。  
    
    :::image type="complex" source="../media/storage-cache-pane-cache-storage-resources.msft.png" alt-text="应用程序缓存窗格" lightbox="../media/storage-cache-pane-cache-storage-resources.msft.png":::
       应用程序 **缓存** 窗格  
    :::image-end:::  

表格的每一行表示一个缓存的资源。  

" **类型** "列 [表示资源的类别][MDNHTMLResourcesInAnApplicationCache]。  

| 类别 | 详细信息 |  
|:--- |:--- |  
| `Explicit` | 此资源在清单中显式列出。 |  
| `Fallback` | URL 是另一个资源的回退。  另一个资源的 URL 未在 DevTools 中列出。 |  
| `Master` | `manifest`资源上的属性指示缓存是资源的父项。 |  
| `Network` | 清单指定资源必须来自网络。 |  

<!--todo:  replace "Master" phrasing if possible.  -->  

在表的底部有状态图标，指示网络连接和应用程序缓存 **的状态**。  应用程序 **缓存** 可能具有以下状态。  

| State | 详细信息 |  
|:--- |:--- |  
| `CHECKING` | 正在获取清单并检查更新。 |  
| `DOWNLOADING` | 资源将添加到缓存中。 |  
| `IDLE` | 缓存没有新更改。 |  
| `OBSOLETE` | 正在删除缓存。 |  
| `UPDATEREADY` |  提供新版本的缓存。 |  

<!-- links -->  

[MicrosoftEdgeDevTools]: ../../devtools-guide-chromium/index.md "Microsoft Edge (Chromium) 开发人员工具 |Microsoft Docs"  

[HTMLStandardOfflineWebApplications]: https://html.spec.whatwg.org/multipage/offline.html#offline "脱机 Web 应用程序 - HTML Standard"  

[MDNHTMLResourcesInAnApplicationCache]: https://developer.mozilla.org/docs/Web/HTML/Using_the_application_cache#Resources_in_an_application_cache "应用程序缓存中的资源 |MDN"  
[MDNWebAPIsWindowApplicationCache]: https://developer.mozilla.org/docs/Web/API/Window/applicationCache "Window.applicationCache - Web API |MDN"  

> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的][GoogleSitePolicies]作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ][CCA4IL]中描述的条款使用。  
> 原始页面位于[此处](https://developers.google.com/web/tools/chrome-devtools/storage/applicationcache)，由 [Kayce Basques][KayceBasques]\（Chrome DevTools \& Lighthouse 的技术作家\）撰写。  

[![Creative Commons License][CCby4Image]][CCA4IL]  
本作品根据[ Creative Commons Attribution 4.0 International License ][CCA4IL]获得许可。  

[CCA4IL]: https://creativecommons.org/licenses/by/4.0  
[CCby4Image]: https://i.creativecommons.org/l/by/4.0/88x31.png  
[GoogleSitePolicies]: https://developers.google.com/terms/site-policies  
[KayceBasques]: https://developers.google.com/web/resources/contributors/kaycebasques  
