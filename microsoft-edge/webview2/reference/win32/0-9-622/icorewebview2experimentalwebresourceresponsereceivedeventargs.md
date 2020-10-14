---
description: '通过 Microsoft Edge WebView2 控件在本机应用程序中嵌入 web 技术 (HTML、CSS 和 JavaScript) '
title: WebView2 Win32 c + + ICoreWebView2ExperimentalWebResourceResponseReceivedEventArgs
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 09/10/2020
ms.topic: reference
ms.prod: microsoft-edge
ms.technology: webview
keywords: IWebView2、IWebView2WebView、webview2、web 视图、win32 应用、win32、edge、ICoreWebView2、ICoreWebView2Controller、浏览器控件、边缘 html、ICoreWebView2ExperimentalWebResourceResponseReceivedEventArgs
ms.openlocfilehash: 552421aa003be2ea52493f16ad94ed2b08e8c3a9
ms.sourcegitcommit: 0faf538d5033508af4320b9b89c4ed99872f0574
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "11011733"
---
# interface ICoreWebView2ExperimentalWebResourceResponseReceivedEventArgs 

[!INCLUDE [prerelease-note](../../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalWebResourceResponseReceivedEventArgs
  : public IUnknown
```

WebResourceResponseReceived 事件的事件参数。

## 摘要

 成员                        | 描述
--------------------------------|---------------------------------------------
[get_Request](#get_request) | Web 资源请求对象。 对此对象所做的任何修改都将被忽略。
[get_Response](#get_response) | Web 资源响应对象。
[PopulateResponseContent](#populateresponsecontent) | 请求响应的内容流的异步方法。

将包含发送的请求和收到的响应。 注意：若要获取响应内容流，请先调用 PopulateResponseContent 并等待异步调用完成，否则返回的内容流对象将为 null。

## 成员

#### get_Request 

Web 资源请求对象。 对此对象所做的任何修改都将被忽略。

> 公共 HRESULT [get_Request](#get_request) ([ICoreWebView2WebResourceRequest](icorewebview2webresourcerequest.md) * * 请求) 

#### get_Response 

Web 资源响应对象。

> 公共 HRESULT [get_Response](#get_response) ([ICoreWebView2WebResourceResponse](icorewebview2webresourceresponse.md) * * 响应) 

对此对象所做的任何修改都将被忽略。

#### PopulateResponseContent 

请求响应的内容流的异步方法。

> 公共 HRESULT [PopulateResponseContent](#populateresponsecontent) ([ICoreWebView2ExperimentalWebResourceResponseReceivedEventArgsPopulateResponseContentCompletedHandler](icorewebview2experimentalwebresourceresponsereceivedeventargspopulateresponsecontentcompletedhandler.md) * 处理程序) 

```cpp
                    args->PopulateResponseContent(
                        Callback<
                            ICoreWebView2ExperimentalWebResourceResponseReceivedEventArgsPopulateResponseContentCompletedHandler>(
                            [this, webResourceRequest, webResourceResponse](HRESULT result) {
                                std::wstring message =
                                    L"{ \"kind\": \"event\", \"name\": "
                                    L"\"WebResourceResponseReceived\", \"args\": {"
                                    L"\"request\": " +
                                    RequestToJsonString(webResourceRequest.get()) +
                                    L", "
                                    L"\"response\": " +
                                    ResponseToJsonString(webResourceResponse.get()) + L"}";

                                message +=
                                    WebViewPropertiesToJsonString(m_webviewEventSource.get());
                                message += L"}";
                                PostEventMessage(message);
                                return S_OK;
                            })
                            .Get());
```
