---
description: 渐进式 Web (Chromium) 在 Windows 10 上本地运行。  下面是作为 Web 开发人员需要知道的所有内容。
title: Windows 上的渐进式 Web 应用
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 04/06/2021
ms.topic: article
ms.prod: microsoft-edge
ms.technology: pwa
keywords: 渐进式 Web 应用， PWA， Edge， JavaScript， Windows， UWP， Microsoft Store
ms.openlocfilehash: be832ee5c0ad395dae7b4946c41da157ab5cd9ba
ms.sourcegitcommit: 146072bf606b84e5145a48333abf9c6b892a12d8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/07/2021
ms.locfileid: "11480186"
---
# <a name="progressive-web-apps-on-windows-overview"></a>Windows 上的渐进式 Web 应用概述  

[渐进式 Web 应用][MDNApps] \ (PWA\) 提供对开放 Web 技术的访问权限，实现跨平台互操作性，并为用户提供为设备自定义的本机、类似应用的体验。  PWA 是逐步增强的网站[][AListApartUnderstandingProgressiveEnhancement]，其功能与支持平台上的本机应用类似。  PWA 的特性结合了最好的 Web 和本机应用。  

:::row:::
    :::column:::
        :::image type="icon" source="./media/i_search-small.png":::
        ### <a name="discoverablemdnpwaadvantagesdiscoverable"></a>[可发现][MDNPwaAdvantagesDiscoverable]
        从 Web 搜索结果和支持的应用商店
    :::column-end:::
    :::column:::
        :::image type="icon" source="./media/i_package-small.png":::
        ### <a name="installablemdnpwaadvantagesinstallable"></a>[可安装][MDNPwaAdvantagesInstallable]
        从主屏幕、"开始"菜单、任务栏等固定和启动
    :::column-end:::
    :::column:::
        :::image type="icon" source="./media/i_push-notification-small.png":::
        ### <a name="re-engageablemdnpwaadvantagesreengageable"></a>[重新参与][MDNPwaAdvantagesReEngageable]
        发送推送通知，即使应用不处于活动状态
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        :::image type="icon" source="./media/i_offline-small.png":::
        ### <a name="network-independentmdnpwaadvantagesnetworkindependent"></a>[与网络无关][MDNPwaAdvantagesNetworkIndependent]
        在脱机和低网络条件下工作
    :::column-end:::
    :::column:::
        :::image type="icon" source="./media/i_progressive-small.png":::
        ### <a name="progressivemdnpwaadvantagesprogressive"></a>[渐进][MDNPwaAdvantagesProgressive]
        体验通过 (功能) 向上或向下扩展
    :::column-end:::
    :::column:::
        :::image type="icon" source="./media/i_security-small.png":::
        ### <a name="safemdnpwaadvantagessafe"></a>[安全][MDNPwaAdvantagesSafe]
        提供安全的 HTTPS 终结点和其他用户安全措施
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        :::image type="icon" source="./media/i_responsive-small.png":::
        ### <a name="responsivemdnpwaadvantagesresponsive"></a>[响应][MDNPwaAdvantagesResponsive]
        适应用户的屏幕大小或方向和输入方法
    :::column-end:::
    :::column:::
        :::image type="icon" source="./media/i_link-small.png":::
        ### <a name="linkablemdnpwaadvantageslinkable"></a>[可链接][MDNPwaAdvantagesLinkable]
        从标准超链接共享和启动
    :::column-end:::
    :::column:::
        &nbsp;  
    :::column-end:::
:::row-end:::  


生成 \ (或将) 网站转换为 PWA，以增强用户参与度。  增强功能包括推送通知、类似应用的集成和脱机支持。  继续构建开放 Web 上的受众，以便用户通过搜索和链接共享发现 PWA。  最好使用 Web 服务器代码更新应用。  

## <a name="pwas-on-microsoft-edge-chromium"></a>Microsoft Edge 上的 PWA (Chromium)   

构建面向 Web 标准 API 的渐进式 Web 应用时，应用可能会跨平台和设备进行部署，并尽可能利用特定于设备的功能。  Microsoft Edge \ (Chromium\) 中的 PWA 将以下优势添加到您的网站。  

*   你的应用基于基于标准的 Web 平台构建。  
*   使用户可以直接从浏览器安装应用。  
*   使你的用户无需基于应用商店的部署或注册即可安装你的应用。  
    
桌面 PBA 在任何 Microsoft Edge \ (Chromium\) 都受支持。 Microsoft Edge \ (Chromium\) Windows 7、Windows 10 和 macOS 上可用。  其中包括以下好处。  

*   可以直接在浏览器中使用导航栏中的 **"安装** "图标安装应用。  
    
    :::image type="complex" source="./media/install-progressive-web-app-icon.png" alt-text="安装应用飞出和图标" lightbox="./media/install-progressive-web-app-icon.png":::
       安装应用飞出和图标  
    :::image-end:::  
    
*   也可以从"设置应用"菜单安装、运行**和管理**  >  **** 应用  
    
    :::image type="complex" source="./media/app-menus.png" alt-text="设置下的应用菜单项" lightbox="./media/app-menus.png":::
       设置下的应用菜单项  
    :::image-end:::  
    
*   Web 通知已集成到 Windows 通知系统  
*   具有安装应用程序的浏览器配置文件的共享 Cookie 存储  
*   使用"设置"和 **更多** \ (\) 菜单访问其他浏览器功能，包括证书验证、网站权限、跟踪保护和 `...` 浏览器扩展  
*   完全访问[用于调试应用的 Microsoft Edge DevTools][DevtoolsProgressiveWebApps]  
    
> [!NOTE]
> 有关 PWA 优势、即将推出的功能和简短演示的信息，请导航到 Build [2020 PWA 会话][BuildVideo]。 

## <a name="requirements"></a>要求  

若要作为 PWA 运行，服务器托管的 Web 应用应满足以下最低要求。  

:::row:::
   :::column span="1":::
      [HTTPS][WikiHttps]  
   :::column-end:::
   :::column span="2":::
      通过为服务器或应用通信提供安全连接来保护用户。  服务工作人员和其他 PWA 技术仅适用于通过安全连接 \ (或用于调试 `localhost` 目的\) 的 Web 资源。  
   :::column-end:::
:::row-end:::  
:::row:::
   :::column span="1":::
      [服务工作者][MDNServiceWorkerApi]  
   :::column-end:::
   :::column span="2":::
      使用服务工作线程充当服务器和客户端应用之间的网络代理。  服务工作线程提供脱机支持、资源缓存、推送通知、后台数据同步和页面加载性能优化。    
   :::column-end:::
:::row-end:::  
:::row:::
   :::column span="1":::
      [Web 应用清单][MDNWebAppManifest]  
   :::column-end:::
   :::column span="2":::
      提供一个基于 JSON 的元数据文件，该文件描述有关 Web 应用的关键信息，以便 Windows 10 和其他主机平台为 PWA 用户提供可安装的本机类似应用的体验。  关键信息包括图标、语言和 URL 入口点。 
   :::column-end:::
:::row-end:::  

若要成为出色的 PWA，您的应用程序还必须满足以下要求。  

:::row:::
   :::column span="1":::
      [跨浏览器兼容性][MDNCrossBrowserTesting]  
   :::column-end:::
   :::column span="2":::
      通过在不同的浏览器和环境中 [进行测试，][MicrosoftDeveloperEdgeToolsRemote] 确保 PWA 能够正常工作。  
   :::column-end:::
:::row-end:::  
:::row:::
   :::column span="1":::
      [响应式设计][WikiResponsiveWebDesign]  
   :::column-end:::
   :::column span="2":::
      采用流畅的布局和灵活的图像。  响应式设计包括以下使用户体验适应用户设备的元素。  
      
      *   CSS [网格][MDNCssGridLayout]  
      *   [flexbox][MDNCssFlexibleBoxLayout]  
      *   CSS [网格][MDNCssGridLayout] 和 [弹性框][MDNCssFlexibleBoxLayout]  
      *   [媒体查询][MDNMediaQueries]  
      *   [响应式图像][MDNResponsiveImages]  
      
      使用 [浏览器的设备仿真][DevToolsGuideDeviceModeTestingOtherBrowsers] 工具在本地测试，或在 [Windows][DevtoolsRemoteDebuggingWindows] 或 [Android][DevtoolsRemoteDebuggingIndex] 上创建远程调试会话以直接在目标设备上进行测试。
   :::column-end:::
:::row-end:::  
:::row:::
   :::column span="1":::
      [深度链接][WikiDeepLinking]  
   :::column-end:::
   :::column span="2":::
      将网站的每个页面路由到一个唯一 URL，以便现有用户可以通过社交媒体共享帮助你吸引更广泛的受众。  
   :::column-end:::
:::row-end:::  
:::row:::
   :::column span="1":::
      [验证和测试实践][Webhint]  
   :::column-end:::
   :::column span="2":::
      使用 [Webhint][Webhint] linter 等代码质量工具优化应用的效率、稳定性、安全性和辅助功能。  
   :::column-end:::
:::row-end:::  
:::row:::
   :::column span="1":::
      [Chromium PWA 清单][WebDevGoodPwaChecklist]  
   :::column-end:::
   :::column span="2":::
      根据 Google 基线 PWA 清单验证 PWA。  
   :::column-end:::
:::row-end:::  

> [!NOTE]
> 若要将 PWA 转换为 [Microsoft Store][MicrosoftDeveloperStore] 应用，请导航到 Microsoft Store 中的渐进式 Web [应用][PwaChromiumMicrosoftStore]。  
  
## <a name="see-also"></a>另请参阅  

*   [为 PBA 提供一些支持][Davrous20191018MythBustingPwasNewEdgeEdition]  
*   [渐进式 Web 应用的渐进路线图][CloudfourThinksProgressiveRoadmapYourWebApp]  
*   [使用渐进 Web 应用的脱机 POS][MediumWebEdgeOfflinePostsProgressiveWebApps]  
*   [PWA 问答&A][AaronGustafsonNotebookPwaQa]  
*   [Web 上的百年][JoretegBlogBettingWeb]  
*   [命名渐进式 Web 应用][Fberriman20170626NamingProgressiveWebApps]  
*   [设计和生成不带框架的渐进式 Web (第 1) ][Smashingmagazine201907ProgressiveWebAppFrameworkPart1]  
*   [设计和生成不带框架的渐进式 Web 应用 (第 2) ][Smashingmagazine201907ProgressiveWebAppFrameworkPart2]  
*   [设计和生成不带框架的渐进式 Web (第 3 部分) ][Smashingmagazine201907ProgressiveWebAppFrameworkPart3]  
    
<!-- links -->  

[DevtoolsRemoteDebuggingIndex]: ../devtools-guide-chromium/remote-debugging/index.md "Android 设备远程调试入门 | Microsoft Docs"  
[DevtoolsRemoteDebuggingWindows]: ../devtools-guide-chromium/remote-debugging/windows.md "远程调试 Windows 10 设备|Microsoft Docs"  
[DevToolsGuideDeviceModeTestingOtherBrowsers]: ../devtools-guide-chromium/device-mode/testing-other-browsers.md "模拟和测试其他浏览器|Microsoft Docs"  
[DevtoolsProgressiveWebApps]: ../devtools-guide-chromium/progressive-web-apps/index.md "调试渐进式 Web 应用|Microsoft Docs"  
[PwaChromiumMicrosoftStore]: ./microsoft-store.md "将渐进式 Web 应用发布到 Microsoft Store |Microsoft Docs"



[WindowsUWPControlsPatternTilesNotificationsWns]: /windows/uwp/controls-and-patterns/tiles-and-notifications-windows-push-notification-services--wns--overview.md "Windows 推送通知服务 (WNS) 概述|Microsoft Docs"  
[WindowsUWPDesignDevicesDesigningTv]: /windows/uwp/design/devices/designing-for-tv.md "针对 Xbox 和电视|Microsoft Docs"  
[WindowsUWPDesignDevicesIndex]: /windows/uwp/design/devices/index.md "UWP 设备的 UI 注意事项|Microsoft Docs"  
[WindowsUWPGetStartedGuide]: /windows/uwp/get-started/universal-application-platform-guide.md "什么是通用 Windows 平台 (UWP) 应用？|Microsoft Docs"  
[WindowsUWPLaunchResumeBackgroundTasks]: /windows/uwp/launch-resume/support-your-app-with-background-tasks.md "使用后台任务支持|Microsoft Docs"  
[WindowsUWPPublishIndex]: /windows/uwp/publish/index.md "发布 Windows 应用和游戏|Microsoft Docs"  
[WindowsUWPPublishDeveloperAccount]: /windows/uwp/publish/opening-a-developer-account.md "打开开发者帐户|Microsoft Docs"  

[WindowsBlogsWelcomingPWAsEdgeWindows]: https://blogs.windows.com/msedgedev/2018/02/06/welcoming-progressive-web-apps-edge-windows-10/#56z7mJwKsykfbR4I.97 "将渐进式 Web 应用用于 Microsoft Edge 和 Windows 10 - Windows 博客"  
[MicrosoftDeveloperEdgePlatformStatusBackgroundSync]: https://developer.microsoft.com/microsoft-edge/platform/status/backgroundsyncapi "后台同步 API - Microsoft Edge 平台状态"  
[MicrosoftDeveloperEdgePlatformStatusWebAppManifest]: https://developer.microsoft.com/microsoft-edge/platform/status/webapplicationmanifest "Web 应用清单 - Microsoft Edge 平台状态"  
[MicrosoftDeveloperEdgeToolsRemote]: https://developer.microsoft.com/microsoft-edge/tools/remote "即时测试"  
[MicrosoftDeveloperWindowsMixedReality]: https://developer.microsoft.com/windows/mixed-reality "混合现实（针对开发人员）"  
[MicrosoftDeveloperWindowsSurfaceHub]: https://developer.microsoft.com/windows/surfacehub "Microsoft Surface Hub"  
[MicrosoftDeveloperStore]: https://developer.microsoft.com/store "Microsoft 开发人员应用商店"  
[MicrosoftEdge]: https://www.microsoft.com/edge "下载新的 Microsoft Edge 浏览器"  
[MicrosoftSupportWindowsFocusAssist]: https://support.microsoft.com/help/4026996/windows-10-turn-focus-assist-on-or-off "在 Windows 10 中打开或关闭焦点辅助"  
[MicrosoftSupportWindowsNotificationSettings]: https://support.microsoft.com/help/4028678/windows-10-change-notification-settings "更改 Windows 10 中的通知设置"  

[AaronGustafsonNotebookPwaQa]: https://www.aaron-gustafson.com/notebook/pwa-qa "PWA 问答&A"  

[AListApartUnderstandingProgressiveEnhancement]: https://alistapart.com/article/understandingprogressiveenhancement "了解渐进式增强 - 列表分开"  

[MDNApps]: https://developer.mozilla.org/Apps/Progressive "应用|MDN"  
[MDNCache]: https://developer.mozilla.org/docs/Web/API/Cache "缓存|MDN"  
[MDNCrossBrowserTesting]: https://developer.mozilla.org/docs/Learn/Tools_and_testing/Cross_browser_testing "跨浏览器测试|MDN"  
[MDNCssFlexibleBoxLayout]: https://developer.mozilla.org/docs/Web/CSS/CSS_Flexible_Box_Layout "CSS 弹性框布局|MDN"  
[MDNCssGridLayout]: https://developer.mozilla.org/docs/Web/CSS/CSS_Grid_Layout "CSS 网格布局 | MDN"  
[MDNFetchApi]: https://developer.mozilla.org/docs/Web/API/Fetch_API "提取 API |MDN"  
[MDNMediaQueries]: https://developer.mozilla.org/docs/Web/CSS/Media_Queries "媒体查询|MDN"  
[MDNNotificationsApi]: https://developer.mozilla.org/docs/Web/API/Notifications_API "通知 API | MDN"  
[MDNPushApi]: https://developer.mozilla.org/docs/Web/API/Push_API "推送 API | MDN"  
[MDNPwaAdvantagesDiscoverable]: https://developer.mozilla.org/docs/Web/Apps/Progressive/Advantages#Discoverable "可发现 - 渐进式 Web 应用优势"  
[MDNPwaAdvantagesInstallable]: https://developer.mozilla.org/docs/Web/Apps/Progressive/Advantages#Installable "可安装 - 渐进式 Web 应用优势"  
[MDNPwaAdvantagesLinkable]: https://developer.mozilla.org/Apps/Progressive/Advantages#Linkable "可链接 - 渐进式 Web 应用优势"  
[MDNPwaAdvantagesNetworkIndependent]: https://developer.mozilla.org/docs/Web/Apps/Progressive/Advantages#Network_independent "独立于网络 - 渐进式 Web 应用优势"  
[MDNPwaAdvantagesProgressive]: https://developer.mozilla.org/docs/Web/Apps/Progressive/Advantages#Progressive "渐进 - 渐进式 Web 应用优势"  
[MDNPwaAdvantagesReEngageable]: https://developer.mozilla.org/docs/Web/Apps/Progressive/Advantages#Re-engageable "重新参与 - 渐进式 Web 应用优势"  
[MDNPwaAdvantagesResponsive]: https://developer.mozilla.org/Apps/Progressive/Advantages#Responsive "响应式 - 渐进式 Web 应用优势"  
[MDNPwaAdvantagesSafe]: https://developer.mozilla.org/docs/Web/Apps/Progressive/Advantages#Safe "安全 - 渐进式 Web 应用优势"  
[MDNResponsiveImages]: https://developer.mozilla.org/docs/Learn/HTML/Multimedia_and_embedding/Responsive_images "响应式图像|MDN"  
[MDNServiceWorkerApi]: https://developer.mozilla.org/docs/Web/API/Service_Worker_API "服务工作线程 API |MDN"  
[MDNSyncManager]: https://developer.mozilla.org/docs/Web/API/SyncManager "SyncManager |MDN"  
[MDNWebAppManifest]: https://developer.mozilla.org/docs/Web/Manifest "Web 应用清单|MDN"  

[BuildVideo]: https://www.youtube.com/watch?v=y4p_QHZtMKM "PWA 视频"  

[CloudfourThinksProgressiveRoadmapYourWebApp]: https://cloudfour.com/thinks/a-progressive-roadmap-for-your-progressive-web-app "渐进式 Web 应用的渐进路线图"  

[Davrous20191018MythBustingPwasNewEdgeEdition]: https://www.davrous.com/2019/10/18/myth-busting-pwas-the-new-edge-edition "百年计划 PBA – 新边缘版本"  

[Fberriman20170626NamingProgressiveWebApps]: https://fberriman.com/2017/06/26/naming-progressive-web-apps "命名渐进式 Web 应用"  

[JoretegBlogBettingWeb]: https://joreteg.com/blog/betting-on-the-web "Web 上的百年"  

[MediumWebEdgeOfflinePostsProgressiveWebApps]: https://medium.com/web-on-the-edge/offline-posts-with-progressive-web-apps-fc2dc4ad895 "使用渐进 Web 应用的脱机 POS"  

[PWABuilder]: https://www.pwabuilder.com "PWABuilder"  

[Smashingmagazine201907ProgressiveWebAppFrameworkPart1]: https://www.smashingmagazine.com/2019/07/progressive-web-application-pwa-framework-part-1 "设计和构建不带框架的渐进式 Web (第 1) "  

[Smashingmagazine201907ProgressiveWebAppFrameworkPart2]: https://www.smashingmagazine.com/2019/07/progressive-web-application-pwa-framework-part-2 "设计和生成不带框架的渐进式 Web (第 2) "  

[Smashingmagazine201907ProgressiveWebAppFrameworkPart3]: https://www.smashingmagazine.com/2019/07/progressive-web-application-pwa-framework-part-3 "设计和构建不带框架的渐进式 Web (第 3) "  

[WebDevGoodPwaChecklist]: https://web.dev/pwa-checklist "什么是良好的渐进式 Web 应用？|web.dev"  

[Webhint]: https://webhint.io "webhint"  

[WikiDeepLinking]: https://en.wikipedia.org/wiki/Deep_linking "深层链接 - Wikipedia"  
[WikiHttps]: https://en.wikipedia.org/wiki/HTTPS "HTTPS - Wikipedia"  
[WikiResponsiveWebDesign]: https://en.wikipedia.org/wiki/Responsive_web_design "响应式 Web 设计 - 维基百科"  
