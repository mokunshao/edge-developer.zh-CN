---
description: '通过 Microsoft Edge WebView2 控件在本机应用程序中嵌入 web 技术 (HTML、CSS 和 JavaScript) '
title: CoreWebView2Environment 中的 WebView2
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 09/11/2020
ms.topic: reference
ms.prod: microsoft-edge
ms.technology: webview
keywords: WebView2、Core、WebView2、web 视图、新、wpf、winforms、app、edge、CoreWebView2、CoreWebView2Controller、浏览器控件、边缘 html、、浏览器控件、边缘 html、WebView2
ms.openlocfilehash: 05b8a10c723ae57b2c95551f4d5043f3336eba3b
ms.sourcegitcommit: 65db518273b3cd69f1b3c528809600719b9b70aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/16/2020
ms.locfileid: "11016324"
---
# CoreWebView2Environment 类的 WebView2 

命名空间： Microsoft WebView2 \
程序集： Microsoft.Web.WebView2.Core.dll

这表示 WebView2 环境。

## 摘要

 成员                        | 描述
--------------------------------|---------------------------------------------
[BrowserVersionString](#browserversionstring) | 当前 CoreWebView2Environment 的浏览器版本信息，包括频道名称（如果不是稳定频道）。
[NewBrowserVersionAvailable](#newbrowserversionavailable) | 当已安装较新版本的 Edge 浏览器并可通过 WebView2 使用时，将触发 NewBrowserVersionAvailable。
[CompareBrowserVersions](#comparebrowserversions) | 比较浏览器版本以确定它们是否匹配或不同。
[CreateAsync](#createasync) | 使用已安装的 Microsoft Edge 版本创建长绿 WebView2 环境。
[CreateCoreWebView2CompositionControllerAsync](#createcorewebview2compositioncontrollerasync) | 异步创建用于可视化托管的新 Web 视图。
[CreateCoreWebView2ControllerAsync](#createcorewebview2controllerasync) | 异步创建新的 Web 视图。
[CreateCoreWebView2PointerInfo](#createcorewebview2pointerinfo) | 创建一个空 CoreWebView2PointerInfo。
[CreateWebResourceResponse](#createwebresourceresponse) | 创建新的 web 资源响应对象。
[GetAvailableBrowserVersionString](#getavailablebrowserversionstring) | 获取浏览器版本信息。
[GetProviderForHwnd](#getproviderforhwnd) | 返回与给定 HWND 对应的 CoreWebView2CompositionController 的 UI 自动化提供程序。

在使用环境参数指定的浏览器进程中运行的环境中创建的 WebViews，应在同一环境中使用。 在不同的环境中使用它不保证兼容，并且可能会失败。 

## 成员

#### BrowserVersionString 

当前 CoreWebView2Environment 的浏览器版本信息，包括频道名称（如果不是稳定频道）。

> 公共字符串 [BrowserVersionString](#browserversionstring)

这与 GetAvailableCoreWebView2BrowserVersionString API 的格式相匹配。 信道名称为 "beta"、"dev" 和 "未设备"。

#### NewBrowserVersionAvailable 

当已安装较新版本的 Edge 浏览器并可通过 WebView2 使用时，将触发 NewBrowserVersionAvailable。

> 公共事件 EventHandler< 对象 > [NewBrowserVersionAvailable](#newbrowserversionavailable)

若要使用较新版本的浏览器，必须创建新的环境和 Web 视图。 将仅针对从其运行代码的同一边缘通道中的新版本引发此事件。 当不运行安装的边缘时，将不会触发任何事件。

由于用户数据文件夹一次只能由一个浏览器进程使用，如果要在 WebViews 中使用新版本的浏览器使用同一用户数据文件夹，则必须先关闭使用早期版本的浏览器的环境和 WebViews。 或者只提示用户重新启动应用。

#### CompareBrowserVersions 

比较浏览器版本以确定它们是否匹配或不同。

> 公共静态 int [CompareBrowserVersions](#comparebrowserversions) (string version1，string version2) 

返回-1、0或1，具体取决于第一个版本是否小于、等于或大于要比较的第二个版本。

输入可以直接使用从 GetAvailableCoreWebView2BrowserVersionString 获取的 versionInfo，信道信息将被忽略。

##### 参数
* `version1` 要比较的第一个版本。 

* `version2` 要比较的第二个版本。

#### CreateAsync 

使用已安装的 Microsoft Edge 版本创建长绿 WebView2 环境。

> 公共静态异步任务< [CoreWebView2Environment](microsoft-web-webview2-core-corewebview2environment.md)  >  [CreateAsync](#createasync) (string browserExecutableFolder、string userDataFolder、CoreWebView2EnvironmentOptions 选项) 

##### 参数
* `browserExecutableFolder` 包含 WebView2 运行时的固定版本的文件夹的相对路径。 

* `userDataFolder` 可以指定 userDataFolder 以更改 WebView2 的默认用户数据文件夹位置。 

* `options` 用于创建 WebView2 环境的选项。

#### CreateCoreWebView2CompositionControllerAsync 

[!INCLUDE [prerelease-note](../../includes/prerelease-note.md)]

异步创建用于可视化托管的新 Web 视图。

> 公共异步任务< [CoreWebView2CompositionController](microsoft-web-webview2-core-corewebview2compositioncontroller.md)  >  [CreateCoreWebView2CompositionControllerAsync](#createcorewebview2compositioncontrollerasync) (IntPtr ParentWindow) 

parentWindow 是应用将连接 Web 视图的可视化树的 HWND。 这将是应用将接收指向 Web 视图的指针/鼠标输入的 HWND (并且需要使用 SendMouseInput/SendPointerInput 转发) 。 如果应用将 Web 视图可视化树移动到另一个窗口下方，则需要设置 CoreWebView2CompositionController 以更新可视化树的新父 HWND。

在创建的 CoreWebView2CompositionController 上设置 RootVisualTarget 属性，以提供视觉对象以托管浏览器的可视化树。

建议为进程或应用程序窗口设置应用程序用户模型 ID。 如果未设置，则在创建 Web 视图期间生成的应用程序用户模型 ID 将设置为 parentWindow 的根窗口。

#### CreateCoreWebView2ControllerAsync 

异步创建新的 Web 视图。

> 公共异步任务< [CoreWebView2Controller](microsoft-web-webview2-core-corewebview2controller.md)  >  [CreateCoreWebView2ControllerAsync](#createcorewebview2controllerasync) (IntPtr ParentWindow) 

parentWindow 是应在其中显示 Web 视图和接收输入的 HWND。 在创建 Web 视图期间，Web 视图会将子窗口添加到提供的窗口中。 由同辈窗口顺序影响的 Z 顺序和其他项目将相应受到影响。

建议为进程或应用程序窗口设置应用程序用户模型 ID。 如果未设置，则在创建 Web 视图期间生成的应用程序用户模型 ID 将设置为 parentWindow 的根窗口。

#### CreateCoreWebView2PointerInfo 

[!INCLUDE [prerelease-note](../../includes/prerelease-note.md)]

创建一个空 CoreWebView2PointerInfo。

> 公共 [CoreWebView2PointerInfo](microsoft-web-webview2-core-corewebview2pointerinfo.md) [CreateCoreWebView2PointerInfo](#createcorewebview2pointerinfo) ( # A1

在调用 SendPointerInput 之前，需要用所有相关信息填充返回的 CoreWebView2PointerInfo。

#### CreateWebResourceResponse 

创建新的 web 资源响应对象。

> 公共 [CoreWebView2WebResourceResponse](microsoft-web-webview2-core-corewebview2webresourceresponse.md) [CreateWebResourceResponse](#createwebresourceresponse) (流内容、Int StatusCode、String ReasonPhrase、string 标题) 

标头是由换行符分隔的原始响应标题字符串。 也可以使用空的标头字符串创建此对象，然后使用 CoreWebView2HttpResponseHeaders 来逐行构造标题。 有关其他参数的信息，请参阅 CoreWebView2WebResourceResponse。

#### GetAvailableBrowserVersionString 

获取浏览器版本信息。

> 公共静态字符串 [GetAvailableBrowserVersionString](#getavailablebrowserversionstring) (字符串 browserExecutableFolder) 

如果信道不是稳定通道，也可以获取信道名称。 如果使用 WebView2 运行时，则不会返回任何信道名称。

##### 参数
* `browserExecutableFolder` 包含 WebView2 运行时的固定版本的文件夹的相对路径。

#### GetProviderForHwnd 

[!INCLUDE [prerelease-note](../../includes/prerelease-note.md)]

返回与给定 HWND 对应的 CoreWebView2CompositionController 的 UI 自动化提供程序。

> 公共对象 [GetProviderForHwnd](#getproviderforhwnd) (IntPtr hwnd) 