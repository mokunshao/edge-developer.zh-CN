---
description: 了解如何调试 WebView2 控件。
title: 开始调试 WebView2 应用程序
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 03/08/2021
ms.topic: how-to
ms.prod: microsoft-edge
ms.technology: webview
keywords: IWebView2、IWebView2WebView、webview2、webview、win32 应用、win32、edge、ICoreWebView2、ICoreWebView2Host、浏览器控件、边缘 html
ms.openlocfilehash: f895634d5e005bb07579d9a5f41c6a988cd78a33
ms.sourcegitcommit: 140e09e508fa97f2d124f264d7d2ff77d12d1ffb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/09/2021
ms.locfileid: "11399842"
---
# <a name="get-started-debugging-webview2-apps"></a>开始调试 WebView2 应用  

Microsoft Edge WebView2 控件的目标是将 Web 和本机应用开发功能和工具的最佳组合在一起。  开发 WebView2 应用时，应调试应用。  本文概述了用于调试 Web 和 WebView2 应用中的本机代码的不同工具。  

## [<a name="microsoft-edge-devtools"></a>Microsoft Edge 开发工具](#tab/devtools)  

使用 [Microsoft Edge (Chromium) 开发人员][DevtoolsGuideChromiumMain] 工具调试 WebView2 控件中显示的 Web 内容，方法与调试 Microsoft Edge 中显示的其他网页的方式相同。  若要打开 DevTools，请设置 WebView 控件的焦点，然后使用以下操作之一。  

*   选择 `F12`。  
*   选择 `Ctrl` + `Shift` + `I` 。  
*   打开上下文菜单 \ (右键单击\) 并选择 `Inspect` 。  
    
有关详细信息，请导航到 [DevTools 概述][DevtoolsGuideChromiumMain]。  

:::image type="complex" source="./media/f12.png" alt-text="DevTools 调试" lightbox="./media/f12.png":::
   DevTools 调试  
:::image-end:::  

## [<a name="visual-studio"></a>Visual Studio](#tab/visualstudio)  

Visual Studio WebView2 应用中为 Web 和本机代码提供各种调试工具。  在Visual Studio部分中，主要侧重于调试 WebView 控件，但其他 Visual Studio 方法也照常可用。  使用以下过程仅调试 Win32 应用或 Office 外接程序中的 Web 和本机代码。  

> [!IMPORTANT]
> 在附加了本机调试Visual Studio中调试应用时，选择可能会触发 `F12` 本机调试器，而不是开发人员工具。  选择 `Ctrl` + `Shift` + `I` ，或使用上下文菜单 \ (右键单击\) 以避免这种情况。  

开始之前，请确保满足以下要求。  

*   若要调试脚本，必须从应用程序内启动Visual Studio。  
*   无法将调试器附加到正在运行的 WebView2 进程。  
*   安装 Visual Studio 2019 版本 16.4 Preview 2 或更高版本。  
    
安装并设置脚本调试器工具Visual Studio。  

1.  完成以下操作以使用 C++ 在桌面开发中安装 **JavaScript** **诊断组件**。  
    
    1.  在 Windows 资源管理器栏中，键入 `Visual Studio Installer` 。  
    1.  选择 **Visual Studio安装程序** 打开它。  
    1.  在Visual Studio安装程序中，在已安装的版本上，选择"更多 **"按钮，** 然后选择"**修改"。**  
    1.  In Visual Studio， under **Workloads，** choose the **Desktop Development in C++** setting.  
        
        :::image type="complex" source="./media/workloads.png" alt-text="Visual Studio修改工作负载屏幕" lightbox="./media/workloads.png":::
            Visual Studio修改工作负载屏幕
        :::image-end:::  
        
    1.  选择 **单个组件**。  
    1.  在搜索框中，输入 `JavaScript diagnostics` 。  
    1.  选择 **JavaScript 诊断** 设置。  
    1.  选择 **"修改"。** 
        
        :::image type="complex" source="./media/indivcomp.png" alt-text="Visual Studio"修改单个组件"选项卡" lightbox="./media/indivcomp.png":::
           Visual Studio"修改单个组件"选项卡  
        :::image-end:::  
        
1.  为 WebView2 应用启用脚本调试。  
    1.  在 WebView2 项目中，打开上下文菜单 \ (右键单击\) ，然后选择"**属性"。**  
    1.  在"**配置属性"下**，选择 **"调试"。**  
    1.  在**调试器类型下**，选择**JavaScript (WebView2) 。 **  
        
        :::image type="complex" source="./media/enbjs.png" alt-text="Visual Studio调试配置属性" lightbox="./media/enbjs.png":::
           Visual Studio **调试** 配置属性  
        :::image-end:::  
        
完成以下操作以调试 WebView2 应用。  

1.  若要在源代码中设置断点，请将鼠标悬停在行号左侧，然后选择设置断点。  JS/TS 调试适配器不执行源路径映射。  必须打开与 WebView2 关联的完全相同的路径。  
    
    :::image type="complex" source="./media/breakpoint.png" alt-text="Visual Studio断点" lightbox="./media/breakpoint.png"::: 
       Visual Studio断点  
    :::image-end:::  
    
1.  若要运行调试程序，请选择平台的位大小，然后选择本地 Windows 调试器旁边的绿色播放 **按钮**。  应用运行，调试程序连接到创建的第一个 WebView2 进程。  
    
    :::image type="complex" source="./media/run.png" alt-text=" Visual Studio本地 Windows 调试器" lightbox="./media/run.png"::: 
       Visual Studio **本地 Windows 调试器**  
    :::image-end:::  
    
1.  在 **调试控制台中**，从调试器中查找输出。  
    
    :::image type="complex" source="./media/console.png" alt-text=" Visual Studio调试控制台" lightbox="./media/console.png"::: 
       Visual Studio **调试控制台**  
    :::image-end:::  
    
## [<a name="visual-studio-code"></a>Visual Studio Code](#tab/visualstudiocode)  

使用 Microsoft Visual Studio 代码调试在 WebView2 控件中运行的脚本。  <!--Ensure that you're using Visual Studio Code version [insert build here] or later.  -->  

在Visual Studio中，完成以下操作以调试代码。 

1.  项目需要具有 `launch.json` 文件。  如果项目没有文件，请复制以下 `launch.json` 代码段并创建新 `launch.json` 文件。  
    
    ```json
        "name": "Hello debug world",
        "type": "pwa-msedge",
        "port": 9222, // The port value is optional, and the default value is 9222.
        "request": "launch",
        "runtimeExecutable": "C:/path/to/your/webview2/app.exe",
        "env": {
            // Customize for your app location if needed
            "Path": "%path%;e:/path/to/your/app/location; "
        },
        "useWebView": true,
        // The following two lines setup source path mapping, where `url` is the start page of your app, and `webRoot` is the top level directory with all your code files.
        "url": "file:///${workspaceFolder}/path/to/your/toplevel/foo.html",
        "webRoot": "${workspaceFolder}/path/to/your/assets"
    ```  
    
    > [!NOTE]
    > Visual Studio代码源路径映射现在需要 URL，因此你的应用现在在启动时接收命令行参数。  如果需要，可以 `url` 安全地忽略该参数。  
    
1.  若要在源代码中设置断点，请将鼠标悬停在行上，然后选择 `F9`
    
    :::image type="complex" source="./media/breakpointvs.png" alt-text="断点在代码Visual Studio设置" lightbox="./media/breakpointvs.png":::
       断点在代码Visual Studio设置  
    :::image-end:::
    
1.  运行代码。  
    1.  在 **"运行** "选项卡上，从下拉菜单中选择启动配置。  
    1.  若要开始调试应用，请选择"开始调试"，这是启动配置下拉列表旁边的绿色三角形。  
        
        :::image type="complex" source="./media/runvs.png" alt-text=" Visual Studio"代码运行"选项卡" lightbox="./media/runvs.png":::
           Visual Studio"代码运行"选项卡  
        :::image-end:::  
        
1.  打开 **调试控制台** 以查看调试输出和错误。  
    
    :::image type="complex" source="./media/resultsvs.png" alt-text=" Visual Studio代码调试控制台" lightbox="./media/resultsvs.png":::
       Visual Studio代码调试控制台  
    :::image-end:::  
    
**高级设置**：  

*   目标 Web 视图调试。 
    
    在某些 WebView2 应用中，可以使用多个 WebView2 控件。 若要选取 WebView2 控件以在这种情况下进行调试，可以使用目标 Webview2 调试 
    
    打开 `launch.json` 并完成以下操作以使用目标 Webview 调试。  
    
    1.  确认参数 `useWebview` 设置为 `true` 。  
    1.  添加 `urlFilter` 参数。  当 WebView2 控件导航到 URL 时，参数值用于 `urlFilter` 比较 URL 中出现的字符串。  
    
    ```json
    "useWebview": "true",
    "urlFilter": "*index.ts",
    
    // Other urlFilter options.
    
    urlFilter="*index.ts"    // Match any url that ends with index.ts, and ignore all leading characters. 
    urlFilter="*index*"      // Match any url that contains the string index anywhere in the URL.  
    urlFilter="file://C:/path/to/my/index.ts," // To match explicit file called index.ts.  
    ```  
    
    在调试应用时，你可能需要从呈现过程开始逐步调试代码。 如果您在网站上呈现网页，但无法访问源代码，可以使用该选项，因为网页将忽略无法识别 `?=value`  的参数。   
    
    > [!IMPORTANT]
    > 在 URL 中发现第一个匹配项后，调试器将停止。  不能同时调试两个 WebView2 控件，因为 CDP 端口由所有 WebView2 控件共享，并且使用单个端口号。  
    
*   调试正在运行的进程  
    
    您可能需要将调试器附加到运行 WebView2 进程。 为此，在 `launch.json` 中，将 `request` 参数更新为 `attach` 。
    
    ```json
        "name": "Hello debugging world",
        "type": "pwa-msedge",
        "port": 9222, 
        "request": "attach",
        "runtimeExecutable": "C:/path/to/your/webview2/app.exe",  
        "env": {
            "Path": "%path%;e:/path/to/your/build/location; "  
        },
        "useWebView": true
    ```  
    
    WebView2 控件必须打开 CDP 端口，以允许调试 WebView2 控件。  必须生成代码，以确保在启动调试程序之前，只有一个 WebView2 (CDP) 打开 Chrome 开发人员协议。  
    
*   调试跟踪选项  
    
    将参数 `trace` 添加到launch.js启用调试跟踪。  
    
    1.  添加 `trace` 参数。  
        
        :::row:::
           :::column span="":::
              ```json
                "name": "Hello debugging world",
                "type": "pwa-msedge",
                "port": 9222, 
                "request": "attach",
                "runtimeExecutable": "C:/path/to/your/webview2/app.exe",  
                "env": {
                "Path": "%path%;e:/path/to/your/build/location; "  
                },
                "useWebView": true
                ,"trace": true  // Turn on  debug tracing, and save the output to a log file.
              ```  
              
              :::image type="complex" source="./media/tracelog.png" alt-text=" 将调试输出保存到日志文件。" lightbox="./media/tracelog.png":::
                 将调试输出保存到日志文件  
              :::image-end:::  
           :::column-end:::
           :::column span="":::
              ```json
              ,"trace": "verbose"  // Turn on verbose tracing in the Debug Output pane.
              ```  
              
              :::image type="complex" source="./media/verbose.png" alt-text=" 详细输出" lightbox="./media/verbose.png":::
                 Visual Studio启用详细跟踪功能的代码调试输出  
              :::image-end:::  
           :::column-end:::
        :::row-end:::  
        
*   调试 Office 加载项。  
    
    如果要调试 Office 加载项，请打开外接程序源代码，在代码的单独Visual Studio实例。  打开launch.jsWebView2 应用中的"打开"菜单，并添加以下代码段以将调试器附加到 Office 加载项。
    
    ```json
    ,"debugServer": 4711
    ```  
    
*   调试器疑难解答  
    
    使用调试器时，可能会遇到以下情况。  
    
    *   调试程序不会在断点停止，并且你有调试输出。  若要解决此问题，请确认断点为 WebView2 控件所使用的文件。  调试器不执行源路径映射。  
    *   无法附加到正在运行的进程，并收到超时错误。  若要解决此问题，请确认 WebView2 控件打开了 CDP 端口。  请确保  `additionalBrowserArguments`  注册表中的值正确，或者选项正确。  有关详细信息，请导航到[dotnet 的其他BrowserArguments][Webview2ReferenceDotnetMicrosoftWebWebview2CoreCorewebview2environmentoptionsAdditionalbrowserarguments]和[Win32 的其他BrowserArguments。][Webview2ReferenceWin32Webview2IdlParameters]  
    
* * *  

## <a name="see-also"></a>另请参阅  

*   若要开始使用 WebView2，请导航到 [WebView2 入门指南][Webview2MainGettingStarted]。  
*   有关 WebView2 功能的全面示例，请导航到 GitHub 上的 [WebView2Samples][GithubMicrosoftedgeWebview2samples] 存储库。
*   有关 WebView2 API 的更多详细信息，请导航到 [API 参考][Webview2ApiReference]。
*   有关 WebView2 的信息，请导航到 [WebView2 资源][Webview2MainNextSteps]。
    
## <a name="getting-in-touch-with-the-microsoft-edge-webview-team"></a>与 Microsoft Edge WebView 团队联系  

[!INCLUDE [contact WebView team note](../includes/contact-webview-team-note.md)]  

<!-- links -->  

[DevtoolsGuideChromiumMain]: ../index.md "Microsoft Edge (Chromium) 开发人员工具 | Microsoft 文档"  

[Webview2ReferenceDotnetMicrosoftWebWebview2CoreCorewebview2environmentoptionsAdditionalbrowserarguments]: /dotnet/api/microsoft.web.webview2.core.corewebview2environmentoptions.additionalbrowserarguments "CoreWebView2EnvironmentOptions.AdditionalBrowserArguments (Microsoft.Web.WebView2.Core) |Microsoft Docs"  
[Webview2ReferenceWin32Webview2IdlParameters]: /microsoft-edge/webview2/reference/win32/webview2-idl#createcorewebview2environmentwithoptions  "CreateCoreWebView2Environment - 全局|Microsoft Docs"  
[Webview2ApiReference]: ../webview2-api-reference.md "Microsoft Edge WebView2 API 参考|Microsoft Docs"  
[Webview2MainNextSteps]: ../index.md#next-steps "下一步 - Microsoft Edge WebView2 (预览版) |Microsoft Docs"  
[Webview2MainGettingStarted]: ../index.md#getting-started "入门 - Microsoft Edge WebView2 (预览版) |Microsoft Docs"  

[GithubMicrosoftedgeWebview2samples]: https://github.com/MicrosoftEdge/WebView2Samples "WebView2 示例 - MicrosoftEdge/WebView2Samples |GitHub"  
