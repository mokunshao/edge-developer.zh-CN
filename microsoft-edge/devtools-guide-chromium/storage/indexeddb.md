---
description: 如何使用应用程序面板和代码段查看和更改 IndexedDB 数据。
title: 使用 Microsoft Edge DevTools 查看和更改 IndexedDB 数据
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 03/08/2021
ms.topic: article
ms.prod: microsoft-edge
keywords: microsoft edge, web 开发, f12 工具, devtools
ms.openlocfilehash: 719348067b1343ca3d7781737fa6441f92ad7ba1
ms.sourcegitcommit: 4b9fb5c1176fdaa5e3c60af2b84e38d5bb86cd81
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2021
ms.locfileid: "11439708"
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

# <a name="view-and-change-indexeddb-data-with-microsoft-edge-devtools"></a>使用 Microsoft Edge DevTools 查看和更改 IndexedDB 数据  

本指南演示如何使用 [Microsoft Edge DevTools][MicrosoftEdgeDevTools] 查看和更改 [IndexedDB][MDNIndexedDBAPI] 数据。  本文假定你熟悉 DevTools。  本文还假定你熟悉 IndexedDB。  如果没有，导航到“[使用 IndexedDB][MDNUsingIndexedDB]”。  

## <a name="view-indexeddb-data"></a>查看 IndexedDB 数据  

1.  选择“**应用程序**”选项卡以打开**应用程序**工具。  “**清单**”窗格通常默认打开。  
    
    :::image type="complex" source="../media/storage-application-manifest-empty.msft.png" alt-text="“清单”窗格" lightbox="../media/storage-application-manifest-empty.msft.png":::
       “**清单**”窗格  
    :::image-end:::  
    
1.  展开 “**IndexedDB**” 菜单，查看哪些数据库可用。  
    
    :::image type="complex" source="../media/storage-application-storage-indexeddb.msft.png" alt-text="“IndexedDB”菜单" lightbox="../media/storage-application-storage-indexeddb.msft.png":::
       “**IndexedDB**” 菜单  
    :::image-end:::  
    
    *   \(![Database icon](../media/database-icon.msft.png)\) `notes - https://mdn.github.io` 表示一个数据库，其中`notes`是数据库的名称，`https://mdn.github.io`是访问数据库的来源。  
    *   \(![Object Store icon](../media/object-store-icon.msft.png)\) `notes` 是一个对象存储。  
    *   **标题**和 **正文**是[索引][MDNUsingIndexedDBUsingIndex]。  
    
    > [!NOTE]
    > **已知限制**  第三方数据库不可见。  例如，如果使用`<iframe>`在页面上嵌入广告，并且广告网络使用 IndexedDB，则广告网络的 IndexedDB 数据将不可见。  导航到 [issue #943770][ChromiumIssue943770]。  
    
1.  选择一个数据库查看来源和版本号。  
    
    :::image type="complex" source="../media/storage-application-storage-indexeddb-notes_db.msft.png" alt-text="备注数据库" lightbox="../media/storage-application-storage-indexeddb-notes_db.msft.png":::
       **备注**数据库  
    :::image-end:::  
    
1.  选择对象存储查看键值对。  
    
    > [!NOTE]
    > IndexedDB 数据不会实时更新。  导航到“[刷新 IndexedDB 数据](#refresh-indexeddb-data)”。  
    
    :::image type="complex" source="../media/storage-application-storage-indexeddb-notes_db-notes_os.msft.png" alt-text="备注对象存储" lightbox="../media/storage-application-storage-indexeddb-notes_db-notes_os.msft.png":::
       **备注**对象存储  
    :::image-end:::  
    
    *   **总条目数**是对象存储中键值对的总数。  
    *   **密钥生成器值**是下一个可用密钥。  此字段仅在使用[密钥生成器][MDNBasicConceptsKeyGenerator]时显示。  
    
1.  选择“**值**”列的单元格以展开该值。  
    
    :::image type="complex" source="../media/storage-application-storage-indexeddb-notes_db-notes_os-edge-chromium.msft.png" alt-text="查看 IndexedDB 值" lightbox="../media/storage-application-storage-indexeddb-notes_db-notes_os-edge-chromium.msft.png":::
       查看 **IndexedDB** 值  
    :::image-end:::  
    
1.  选择一个索引（如下图的**标题**或**正文**）以根据该索引的值对对象存储排序。  
   
    :::image type="complex" source="../media/storage-application-storage-indexeddb-notes_db-notes_os-title.msft.png" alt-text="按索引对对象存储排序" lightbox="../media/storage-application-storage-indexeddb-notes_db-notes_os-title.msft.png":::
       按索引对对象存储排序  
    :::image-end:::  
    
## <a name="refresh-indexeddb-data"></a>刷新 IndexedDB 数据  

**应用程序**工具中的 IndexedDB 值不会实时更新。  查看对象存储时，选择“**刷新**”\(“![刷新](../media/reload-icon.msft.png)”\)以刷新数据，或在查看数据库时，选择“**刷新数据库**”以刷新全部数据。  

:::image type="complex" source="../media/storage-application-storage-indexeddb-notes_db-notes_os-refresh-database.msft.png" alt-text="查看数据库" lightbox="../media/storage-application-storage-indexeddb-notes_db-notes_os-refresh-database.msft.png":::
   查看数据库  
:::image-end:::  

## <a name="edit-indexeddb-data"></a>编辑 IndexedDB 数据  

无法通过**应用程序**工具编辑 IndexedDB 键和值。  但是，由于 DevTools 可以访问页面上下文，因此你可以在 DevTools 中运行 JavaScript 代码来编辑 IndexedDB 数据。  

### <a name="edit-indexeddb-data-with-snippets"></a>使用代码段编辑 IndexedDB 数据  

[代码段][DevtoolsJavascriptSnippets]是一种在 DevTools 中存储和运行 JavaScript 代码的方法。  运行代码段时，结果将记录到**控制台**。  可以使用代码段运行 JavaScript 代码来编辑 IndexedDB 数据库。  

:::image type="complex" source="../media/storage-sources-snippets-indexeddb-output.msft.png" alt-text="使用代码段与 IndexedDB 交互" lightbox="../media/storage-sources-snippets-indexeddb-output.msft.png":::
   使用代码段与 IndexedDB 交互  
:::image-end:::  

## <a name="delete-indexeddb-data"></a>删除 IndexedDB 数据  

### <a name="delete-an-indexeddb-key-value-pair"></a>删除 IndexedDB 键值对  

1.  [查看 IndexedDB 对象存储](#view-indexeddb-data)。  
1.  选择要删除的键值对。  DevTools 突出显示它以指示已选中。  
    
    :::image type="complex" source="../media/storage-application-storage-indexeddb-notes_db-notes_os2.msft.png" alt-text="选择键值对以将其删除" lightbox="../media/storage-application-storage-indexeddb-notes_db-notes_os2.msft.png":::
       选择键值对以将其删除  
    :::image-end:::  
    
1.  选择`Delete`键或选择“**删除所选**”\(“![删除所选](../media/delete-icon.msft.png)”\)。  
    
    :::image type="complex" source="../media/storage-application-storage-indexeddb-notes_db-notes_os-delete-selected.msft.png" alt-text="删除键值对后对象存储的外观" lightbox="../media/storage-application-storage-indexeddb-notes_db-notes_os-delete-selected.msft.png":::
       删除键值对后对象存储的外观  
    :::image-end:::  
    
### <a name="delete-all-key-value-pairs-in-an-object-store"></a>删除对象存储中所有键值对  

1.  [查看 IndexedDB 对象存储](#view-indexeddb-data)。  
    
    :::image type="complex" source="../media/storage-application-storage-indexeddb-notes_db-notes_os-clear-object-store.msft.png" alt-text="查看对象存储" lightbox="../media/storage-application-storage-indexeddb-notes_db-notes_os-clear-object-store.msft.png":::
       查看对象存储  
    :::image-end:::  
    
1.  选择“**清除对象存储**”\(“![清除对象存储](../media/clear-icon.msft.png)”\)。  
    
### <a name="delete-an-indexeddb-database"></a>删除 IndexedDB 数据库  

1.  [查看要删除的 IndexedDB 数据库](#view-indexeddb-data)。  
1.  选择“**删除数据库**”。  
    
    :::image type="complex" source="../media/storage-application-storage-indexeddb-notes_db-delete-database.msft.png" alt-text="“删除数据库”按钮" lightbox="../media/storage-application-storage-indexeddb-notes_db-delete-database.msft.png":::
       “**删除数据库**”按钮  
    :::image-end:::  
    
### <a name="delete-all-indexeddb-storage"></a>删除所有 IndexedDB 存储  

1.  打开“**清除存储**”窗格。  
1.  确保已启用 **IndexedDB** 复选框。  
1.  选择“**清除网站数据**”。  
    
    :::image type="complex" source="../media/storage-application-clear-storage-indexeddb-clear-site-data.msft.png" alt-text="“清除存储”窗格" lightbox="../media/storage-application-clear-storage-indexeddb-clear-site-data.msft.png":::
       “**清除存储**”窗格  
    :::image-end:::  
    
## <a name="getting-in-touch-with-the-microsoft-edge-devtools-team"></a>联系 Microsoft Edge DevTools 团队  

[!INCLUDE [contact DevTools team note](../includes/contact-devtools-team-note.md)]  

<!-- links -->  

[MicrosoftEdgeDevTools]: ../../devtools-guide-chromium/index.md "Microsoft Edge (Chromium) 开发人员工具 | Microsoft Docs"  
[DevtoolsJavascriptSnippets]: ../javascript/snippets.md "使用 Microsoft Edge DevTools 在任意页面上运行 JavaScript 代码段 | Microsoft Docs"  

[ChromiumIssue943770]: https://crbug.com/943770 "943770 - DevTools:显示 iframe IndexedDB 数据库 - chromium - Monorail"  

[MDNBasicConceptsKeyGenerator]: https://developer.mozilla.org/docs/Web/API/IndexedDB_API/Basic_Concepts_Behind_IndexedDB#gloss_keygenerator "密钥生成器 - 基本概念 | MDN"  
[MDNIndexedDBAPI]: https://developer.mozilla.org/docs/Web/API/IndexedDB_API "IndexedDB API | MDN"  
[MDNUsingIndexedDB]: https://developer.mozilla.org/docs/Web/API/IndexedDB_API/Using_IndexedDB "使用 IndexedDB | MDN"  
[MDNUsingIndexedDBUsingIndex]: https://developer.mozilla.org/docs/Web/API/IndexedDB_API/Using_IndexedDB#Using_an_index "使用索引 - 使用 IndexedDB | MDN"  

> [!NOTE]
> 此页面的某些部分是根据 [Google 创建和共享的][GoogleSitePolicies]作品所做的修改，并根据[ Creative Commons Attribution 4.0 International License ][CCA4IL]中描述的条款使用。  
> 原始页面位于[此处](https://developers.google.com/web/tools/chrome-devtools/storage/indexeddb)，由 [Kayce Basques][KayceBasques]\（Chrome DevTools \& Lighthouse 的技术作家\）撰写。  

[![Creative Commons License][CCby4Image]][CCA4IL]  
本作品根据[ Creative Commons Attribution 4.0 International License ][CCA4IL]获得许可。  

[CCA4IL]: https://creativecommons.org/licenses/by/4.0  
[CCby4Image]: https://i.creativecommons.org/l/by/4.0/88x31.png  
[GoogleSitePolicies]: https://developers.google.com/terms/site-policies  
[KayceBasques]: https://developers.google.com/web/resources/contributors/kaycebasques  
