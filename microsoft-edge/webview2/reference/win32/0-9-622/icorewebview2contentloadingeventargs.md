---
description: '通过 Microsoft Edge WebView2 控件在本机应用程序中嵌入 web 技术 (HTML、CSS 和 JavaScript) '
title: WebView2 Win32 c + + ICoreWebView2ContentLoadingEventArgs
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 09/09/2020
ms.topic: reference
ms.prod: microsoft-edge
ms.technology: webview
keywords: IWebView2、IWebView2WebView、webview2、web 视图、win32 应用、win32、edge、ICoreWebView2、ICoreWebView2Controller、浏览器控件、边缘 html、ICoreWebView2ContentLoadingEventArgs
ms.openlocfilehash: 229389c6859363ef9a7c3fbf7719dbe30a061875
ms.sourcegitcommit: 0faf538d5033508af4320b9b89c4ed99872f0574
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "11011803"
---
# interface ICoreWebView2ContentLoadingEventArgs 

```
interface ICoreWebView2ContentLoadingEventArgs
  : public IUnknown
```

ContentLoading 事件的事件参数。

## 摘要

 成员                        | 描述
--------------------------------|---------------------------------------------
[get_IsErrorPage](#get_iserrorpage) | 如果加载的内容是错误页面，则为 True。
[get_NavigationId](#get_navigationid) | 导航的 ID。

## 成员

#### get_IsErrorPage 

如果加载的内容是错误页面，则为 True。

> 公共 HRESULT [get_IsErrorPage](#get_iserrorpage) (BOOL * IsErrorPage) 

#### get_NavigationId 

导航的 ID。

> 公共 HRESULT [get_NavigationId](#get_navigationid) (UINT64 * NavigationId) 
