---
description: 使用媒体工具查看信息，并按浏览器选项卡调试媒体播放器。
title: 查看和调试媒体播放器信息
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 02/12/2021
ms.topic: article
ms.prod: microsoft-edge
keywords: microsoft edge、web 开发、f12 工具、开发工具
ms.openlocfilehash: 7680faa13f65a2ea6f0a8b085316b5ed67bfdaba
ms.sourcegitcommit: 6cf12643e9959873f8b5d785fd6158eeab74f424
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2021
ms.locfileid: "11398404"
---
<!-- Copyright Jecelyn Yeen

   Licensed under the Apache License, Version 2.0 (the "License");
   you may not use this file except in compliance with the License.
   You may obtain a copy of the License at

       https://www.apache.org/licenses/LICENSE-2.0

   Unless required by applicable law or agreed to in writing, software
   distributed under the License is distributed on an "AS IS" BASIS,
   WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
   See the License for the specific language governing permissions and
   limitations under the License.  -->  

# <a name="view-and-debug-media-players-information"></a>查看和调试媒体播放器信息  

使用**** Microsoft Edge DevTools 中的媒体工具查看信息，并按浏览器选项卡调试媒体播放器。  

## <a name="open-the-media-tool"></a>打开媒体工具  

**媒体**工具是 DevTools 中用于检查网页的媒体播放器的主要位置。

1.  [打开 DevTools][DevtoolsGuideChromiumOpen]。  
1.  若要打开**媒体面板**，请选择 **"自定义和控制 DevTools** `...`  >  **更多工具**  >  **媒体"。**  
    
    :::image type="complex" source="../media/media-panel-empty.msft.png" alt-text="媒体面板" lightbox="../media/media-panel-empty.msft.png":::
       **媒体** 面板  
    :::image-end:::  
    
## <a name="view-media-players-information"></a>查看媒体播放器信息  

1.  使用媒体播放器导航到网页，如以下网页。  
    
    [使用边缘开发人员工具最大程度地提高工作效率][BingVideosSearchViewDetailMidE0BA14EC0E0D18C06C8DE0BA14EC0E0D18C06C8]  
    
1.  在 **"玩家** "菜单下，将显示媒体播放器。  
1.  选择玩家。  " **属性** "面板显示媒体播放器的属性。  
    
    :::image type="complex" source="../media/media-panel-view.msft.png" alt-text="媒体属性" lightbox="../media/media-panel-view.msft.png":::
       媒体属性  
    :::image-end:::  
    
1.  若要查看所有媒体播放器事件，请选择 **"事件"** 面板。  
    
    :::image type="complex" source="../media/media-panel-events.msft.png" alt-text="媒体事件" lightbox="../media/media-panel-events.msft.png":::
       媒体事件  
    :::image-end:::  
    
1.  若要查看媒体播放器消息日志，请选择"消息 **"** 面板。  您可以按日志级别或字符串筛选邮件。  
    
    :::image type="complex" source="../media/media-panel-messages.msft.png" alt-text="媒体消息" lightbox="../media/media-panel-messages.msft.png":::
       媒体消息  
    :::image-end:::  
    
1.  在 **"时间线** "面板上，媒体播放和缓冲区状态实时显示。  
    
    :::image type="complex" source="../media/media-panel-timeline.msft.png" alt-text="媒体时间线" lightbox="../media/media-panel-timeline.msft.png":::
       媒体时间线  
    :::image-end:::  
    
### <a name="remote-debugging"></a>远程调试  

从 Windows 或 macOS 计算机查看 Android 设备上的媒体播放器信息。  

1.  若要设置远程调试，请导航到远程 [调试 Android 设备入门][DevtoolsGuideChromiumRemoteDebuggingIndex]。  
1.  远程查看媒体播放器信息。  
    
    <!-- TODO: recreate image using an Android device -->  
    <!--  
    :::image type="complex" source="../media/media-panel-remote-debug.msft.png" alt-text="Remote debugging" lightbox="../media/media-panel-remote-debug.msft.png":::
       Remote debugging  
    :::image-end:::  
    -->  
    
## <a name="hide-and-show-media-players"></a>隐藏和显示媒体播放器  

有时，您可以在网页上运行多个媒体播放器，或者使用相同的浏览器选项卡浏览不同的网页，每个网页都有媒体播放器。

你可以选择隐藏 \ (或显示\) 每个媒体播放器，以简化调试体验。  

1.  使用同一浏览器选项卡浏览到多个不同的视频网页。  
1.  若要隐藏媒体播放器，请完成以下操作之一。  
    *   若要隐藏一个媒体播放器，请将鼠标悬停在媒体播放器上，打开上下文菜单 \ (右键单击\) ，然后选择"隐藏**播放器"。**  
    *   若要隐藏所有其他媒体播放器，请将鼠标悬停在媒体播放器上，打开上下文菜单 \ (右键单击\) ，然后选择"隐藏所有其他 **"。**  
    
    :::image type="complex" source="../media/media-panel-hide-show.msft.png" alt-text="隐藏媒体播放器" lightbox="../media/media-panel-hide-show.msft.png":::
       隐藏媒体播放器  
    :::image-end:::  
    
## <a name="export-media-player-information"></a>导出媒体播放器信息  

1.  若要将媒体播放器信息下载为 JSON 文件，请将鼠标悬停在媒体播放器上，打开上下文菜单 \ (右键单击\) ，然后选择"保存播放器 **信息**"。  
    
    :::image type="complex" source="../media/media-panel-save.msft.png" alt-text="导出媒体信息" lightbox="../media/media-panel-save.msft.png":::
       导出媒体信息  
    :::image-end:::  
    
## <a name="getting-in-touch-with-the-microsoft-edge-devtools-team"></a>联系 Microsoft Edge 开发工具团队  

[!INCLUDE [contact DevTools team note](../includes/contact-devtools-team-note.md)]  

<!-- links -->  

[DevtoolsGuideChromiumOpen]: ../open/index.md "在 DevTools (中打开 Microsoft Edge) Chromium |Microsoft Docs"  

[DevtoolsGuideChromiumRemoteDebuggingIndex]: ../remote-debugging/index.md "开始远程调试 Android 设备|Microsoft Docs"  

[BingVideosSearchViewDetailMidE0BA14EC0E0D18C06C8DE0BA14EC0E0D18C06C8]: https://www.bing.com/videos/search?view=detail&mid=DE0BA14EC0E0D18C06C8DE0BA14EC0E0D18C06C8 "使用边缘开发人员工具最大程度地提高工作效率|必应视频"  

> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的][GoogleSitePolicies]作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ][CCA4IL]中描述的条款使用。  
> 原始页面位于 [此处](https://developers.google.com/web/tools/chrome-devtools/media-panel/index)，并由 [Jecelyn Yeen][JecelynYeen] \（开发人员支持者，Chrome DevTools\）制作。  

[![Creative Commons License][CCby4Image]][CCA4IL]  
本作品根据[ Creative Commons Attribution 4.0 International License ][CCA4IL]获得许可。  

[CCA4IL]: https://creativecommons.org/licenses/by/4.0  
[CCby4Image]: https://i.creativecommons.org/l/by/4.0/88x31.png  
[GoogleSitePolicies]: https://developers.google.com/terms/site-policies  
[JecelynYeen]: https://developers.google.com/web/resources/contributors/jecelynyeen  

