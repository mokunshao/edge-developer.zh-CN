---
description: 打开命令菜单并运行"禁用 JavaScript"命令。
title: 使用 Microsoft Edge DevTools 禁用 JavaScript
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 02/12/2021
ms.topic: article
ms.prod: microsoft-edge
keywords: microsoft edge、web 开发、f12 工具、开发工具
ms.openlocfilehash: 2067944fa17c332dd15ffb3ef97afe02d35685ed
ms.sourcegitcommit: 6cf12643e9959873f8b5d785fd6158eeab74f424
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2021
ms.locfileid: "11398558"
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

# <a name="disable-javascript-with-microsoft-edge-devtools"></a>使用 Microsoft Edge DevTools 禁用 JavaScript  

完成以下操作以显示禁用 JavaScript 时网页的外观和行为。  

1.  [打开 Microsoft Edge DevTools。][DevToolsOpen]  
1.  选择 `Control`+`Shift`+`P` \(Windows、Linux\) 或 `Command`+`Shift`+`P` \(macOS\) 打开**命令菜单**。  
    
    :::image type="complex" source="../media/javascript-console-command.msft.png" alt-text="命令菜单" lightbox="../media/javascript-console-command.msft.png":::
       **命令菜单**  
    :::image-end:::  
    
1.  开始键入， `javascript` 选择 **"禁用 JavaScript"，** 然后选择 `Enter` 运行命令。  JavaScript 现已禁用。  
    
    :::image type="complex" source="../media/javascript-console-command-javascript.msft.png" alt-text="在命令菜单中选择"禁用 JavaScript"" lightbox="../media/javascript-console-command-javascript.msft.png":::
       在**命令菜单中选择"禁用 JavaScript"** ****  
    :::image-end:::  
    
    源旁边的黄色警告 **图标** 提醒你 JavaScript 已禁用。  
    
    :::image type="complex" source="../media/javascript-console-javascript-disabled-warning.msft.png" alt-text="源旁边的警告图标" lightbox="../media/javascript-console-javascript-disabled-warning.msft.png":::
       源旁边的警告 **图标**  
    :::image-end:::  
    
只要打开 DevTools，JavaScript 在选项卡中就保持禁用状态。  

您可能需要刷新页面，查看网页在加载时是否以及如何依赖 JavaScript。  

若要重新启用 JavaScript，请完成以下操作。  

*   再次 **打开命令菜单** 并运行 `Enable JavaScript` 命令。  
*   关闭 DevTools。  

## <a name="getting-in-touch-with-the-microsoft-edge-devtools-team"></a>联系 Microsoft Edge 开发工具团队  

[!INCLUDE [contact DevTools team note](../includes/contact-devtools-team-note.md)]  

<!-- links -->  

[DevToolsOpen]: ../open/index.md "打开 Microsoft Edge DevTools | Microsoft Docs"  

> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的][GoogleSitePolicies]作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ][CCA4IL]中描述的条款使用。  
> 原始页面位于[此处](https://developers.google.com/web/tools/chrome-devtools/javascript/disable)，由 [Kayce Basques][KayceBasques]\（Chrome DevTools \& Lighthouse 的技术作家\）撰写。  

[![Creative Commons License][CCby4Image]][CCA4IL]  
本作品根据[ Creative Commons Attribution 4.0 International License ][CCA4IL]获得许可。  

[CCA4IL]: https://creativecommons.org/licenses/by/4.0  
[CCby4Image]: https://i.creativecommons.org/l/by/4.0/88x31.png  
[GoogleSitePolicies]: https://developers.google.com/terms/site-policies  
[KayceBasques]: https://developers.google.com/web/resources/contributors/kaycebasques  
