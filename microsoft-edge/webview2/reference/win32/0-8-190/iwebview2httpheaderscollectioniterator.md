---
description: 通过 Microsoft Edge WebView2 控件在 Win32 应用中托管 web 内容
title: 适用于 Win32 应用的 Microsoft Edge WebView2
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 12/09/2019
ms.topic: reference
ms.prod: microsoft-edge
ms.technology: webview
keywords: IWebView2、IWebView2WebView、webview2、web 视图、win32 应用、win32、edge
ms.openlocfilehash: 4b9ad48d9b09343bad04d4acbe7c49750e76427d
ms.sourcegitcommit: 07cda56425e5fdf90eeb3972e17041261bf720cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/14/2020
ms.locfileid: "10653163"
---
# interface IWebView2HttpHeadersCollectionIterator 

> [!NOTE]
> 此接口可能会在 SDK 版本0.8.355 后更改或不可用。 请参阅[参考](../../../webview2-api-reference.md)了解最新的 API 参考。

```
interface IWebView2HttpHeadersCollectionIterator
  : public IUnknown
```

HTTP 标头集合的迭代器。

## 摘要

 成员                        | 描述
--------------------------------|---------------------------------------------
[GetCurrentHeader](#getcurrentheader) | 获取迭代器的当前 HTTP 标头的名称和值。
[MoveNext](#movenext) | 将迭代器移动到集合中的下一个 HTTP 标头。

请参阅[IWebView2HttpRequestHeaders](IWebView2HttpRequestHeaders.md)和[IWebView2HttpResponseHeaders](IWebView2HttpResponseHeaders.md)。

## 成员

#### GetCurrentHeader 

获取迭代器的当前 HTTP 标头的名称和值。

> 公共 HRESULT [GetCurrentHeader](#getcurrentheader)（LPWSTR * NAME，LPWSTR * value）

如果对 MoveNext 的最后一次调用设置 has_next 为 FALSE，此方法将失败。

#### MoveNext 

将迭代器移动到集合中的下一个 HTTP 标头。

> 公共 HRESULT [MoveNext](#movenext)（BOOL * has_next）

如果没有更多的 HTTP 标头，则 has_next 参数将设置为 FALSE。 在此情况下，如果调用 GetCurrentHeader 方法，则该方法将失败。
