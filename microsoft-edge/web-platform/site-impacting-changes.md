---
description: 提供可能会影响网站兼容性的高影响更改的摘要
title: Microsoft Edge 中影响网站兼容性的更改
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 02/10/2021
ms.topic: article
ms.prod: microsoft-edge
keywords: microsoft edge， 兼容性， Web 平台
ms.openlocfilehash: 64cdb417e6bd0aa648c7e1225bb6dc522f3873ce
ms.sourcegitcommit: fe7301d0f62493e42e6a1a81cdbda3457f0343b8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/13/2021
ms.locfileid: "11327503"
---
# Microsoft Edge 中影响网站兼容性的更改  

web 正在不断发展，以改善用户体验、安全性和隐私性。  在某些情况下，更改可能足以影响现有页面的功能。  下表汇总了 Microsoft Edge 团队当前跟踪的特别影响大的更改。  经常查看本文;随着思考的不断发展、日程表的强化以及新更改的宣布，Microsoft Edge 团队将更新以下页面。  

| “更改” | 稳定渠道 | 实验 | 其他信息 |  
|:--- |:--- |:--- |:--- |
| Cookie 默认为 `SameSite=Lax` 和 `SameSite=None-requires-Secure` | [Chrome+1](#release-comments) \ (Edge v86\)   | Canary v82，Dev v82 | 此更改发生在 Microsoft Edge 所基于的 Chromium 项目中。  有关详细信息，包括 Google 对此更改的计划日程表，请导航到 [Chrome 平台状态条目][ChromePlatformStatus5088147346030592]。  |  
| 引用者策略：默认为 `strict-origin-when-cross-origin` | [Chrome+1](#release-comments) \ (Edge v86\)   | Canary v79，Dev v79 | 此更改发生在 Microsoft Edge 所基于的 Chromium 项目中。  有关详细信息，包括 Google 对此更改的计划日程表，请导航到 [Chrome 平台状态条目][ChromePlatformStatus6251880185331712]。  |  
| 禁止在页面 `XmlHttpRequest` 解除中同步 | [Chrome+1](#release-comments) \ (Edge v83\)  |  | 此更改发生在 Microsoft Edge 所基于的 Chromium 项目中。  与 Chrome 匹配，Microsoft Edge 提供在 Edge v88 之前关闭此更改的组策略。  有关详细信息，包括 Google 对此更改的计划日程表，请导航到 [Chrome 平台状态条目][ChromePlatformStatus4664843055398912]。  |  
| 显示通知权限请求的细微提示 | Edge v84 |  | 安静通知请求在使用或 API 请求的网站通知权限的地址栏中显示一个细微的请求图标，以替换完整或标准的权限飞 `Notifications` `Push` 出提示 UI。  此功能当前为所有用户启用。  若要选择退出安静通知请求，请导航到 `edge://settings/content/notifications` 。  将来，Microsoft Edge 团队可能会探索在某些情况下重新启用完整的飞出通知提示。  |  
| 默认情况下关闭 TLS/1.0 和 TLS/1.1 | Edge v84 |  | [SSLMinVersion][DeployedgeMicrosoftEdgePoliciesSslversionmin]组策略允许重新启用 TLS/1.0 和 TLS/1.1;策略在 Edge v90 之前仍然可用。  |  
| 阻止混合内容下载 | [Chrome+1](#release-comments) \ (Edge v86\)   |  | 此更改发生在 Microsoft Edge 所基于的 Chromium 项目中。  有关详细信息，包括 Google 对此更改的计划日程表，请导航到 [Google 安全博客条目][GoogleBlogSecurity20200206]。  针对要发出警告或阻止的文件类型的 Microsoft 推出计划计划在 Chrome 发布后发布一次。  |  
| 弃用 AppCache | [Chrome+1](#release-comments) \ (Edge v86\)   |  | 此更改发生在 Microsoft Edge 所基于的 Chromium 项目中。  有关详细信息，请导航到 [WebDev 文档][WebDevAppCacheRemoval]。  Microsoft 推出计划弃用计划在 Chrome 发布后发布一次。  请求 [AppCache OriginTrial 令牌][ChromeDevelopersOrigintrialsAppCacheOriginTrial] 允许站点继续使用已弃用 API，直到 Edge v90。  |  
| 删除 Adobe Flash | Edge v88  |  | 此更改发生在 Microsoft Edge 所基于的 Chromium 项目中。  有关详细信息，请导航到 [Adobe Flash Chromium 路线图][ChromiumFlashRoadmapSupportRemoved]。  | 
| 关闭并删除 FTP | Edge v88  | Edge Beta v87 | 在 Edge Beta v87 中，FTP 支持默认处于关闭状态;在 Edge Stable v87 中，它保持启用状态。  在 Edge v88 中，FTP 支持已完全删除。  此更改发生在 Microsoft Edge 所基于的 Chromium 项目中。  有关详细信息，请导航到 [Chrome 平台状态条目][ChromePlatformStatus6246151319715840]。  具有仍然需要 FTP 支持的网站的企业可以通过将站点配置为使用 [IE][DeployedgeEdgeIeMode]模式来继续使用 FTP。  | 
| 自动升级混合内容图像 | Edge v88  |  | 对图像的非安全 \ (HTTP\) 引用会自动升级到 HTTPS;如果图像无法通过 HTTPS 获得，则图像下载将失败。 组 [策略][DeployedgeMicrosoftEdgePoliciesInsecurecontentallowedforurls] 可用于控制此功能。 此更改发生在 Microsoft Edge 所基于的 Chromium 项目中。 有关详细信息，请导航到 [Chrome 平台状态条目][ChromePlatformStatus4926989725073408]。  | 
| 阻止第三方 Cookie 时不允许 HTTP 身份验证  | Edge v87  |  | 从 Edge v87 开始，当使用 [BlockThirdPartyCookies][DeployedgeMicrosoftEdgePoliciesBlockthirdpartycookies] 策略或通过"边缘设置"页阻止第三方请求的 Cookie 时，也会禁止 HTTP 身份验证。 如果托管列表的终结点需要使用 HTTP 身份验证， [此更改可能会影响][DeployedgeEdgeIeModePoliciesConfigureUsingUseEnterpriseModeIeWebsiteListPolicy] Internet Explorer模式的企业模式站点列表下载。  若要允许将 Cookie 和 HTTP 身份验证用于企业模式站点列表下载，请向 [CookiesAllowedForURLs][DeployedgeMicrosoftEdgePoliciesCookiesallowedforurls] 策略添加匹配的 URL 模式。  |   

##### 发布注释  

:::row:::
   :::column span="1":::
      Chrome+1  
   :::column-end:::
   :::column span="2":::
      根据用户和开发人员的反馈，指示的功能或更改在 Chrome 发布后发布一次。  
   :::column-end:::
:::row-end:::
:::row:::
   :::column span="1":::
      Chrome 或 Chrome+1  
   :::column-end:::
   :::column span="2":::
      根据用户和开发人员的反馈，指示的功能或更改会同时提供，或在 Chrome 发布后发布。  
   :::column-end:::
:::row-end:::

<!-- links -->  

[DeployedgeEdgeIeMode]: /deployedge/edge-ie-mode "关于 IE 模式|Microsoft Docs"  
[DeployedgeEdgeIeModePoliciesConfigureUsingUseEnterpriseModeIeWebsiteListPolicy]: /deployedge/edge-ie-mode-policies#configure-using-the-use-the-enterprise-mode-ie-website-list-policy "使用"使用企业模式 IE 网站列表策略 - 配置 IE 模式策略"|Microsoft Docs"  
[DeployedgeMicrosoftEdgePoliciesBlockthirdpartycookies]: /deployedge/microsoft-edge-policies#blockthirdpartycookies "BlockThirdPartyCookies - Microsoft Edge - 策略|Microsoft Docs"  
[DeployedgeMicrosoftEdgePoliciesCookiesallowedforurls]: /deployedge/microsoft-edge-policies#cookiesallowedforurls "CookiesAllowedForUrls - Microsoft Edge - 策略|Microsoft Docs"  
[DeployedgeMicrosoftEdgePoliciesInsecurecontentallowedforurls]:  /deployedge/microsoft-edge-policies#insecurecontentallowedforurls "InsecureContentAllowedForUrls - Microsoft Edge - 策略|Microsoft Docs"  
[DeployedgeMicrosoftEdgePoliciesSslversionmin]: /deployedge/microsoft-edge-policies#sslversionmin "SSLVersionMin - Microsoft Edge - 策略|Microsoft Docs"  

[ChromePlatformStatus4664843055398912]: https://chromestatus.com/feature/4664843055398912 "禁止在页面解除 JavaScript 中同步 XHR |Chrome 平台状态"  
[ChromePlatformStatus4926989725073408]: https://chromestatus.com/feature/4926989725073408 "自动升级图像混合内容|Chrome 平台状态"  
[ChromePlatformStatus5088147346030592]: https://chromestatus.com/feature/5088147346030592 "Cookie 默认为 SameSite=Lax |Chrome 平台状态"  
[ChromePlatformStatus6246151319715840]: https://chromestatus.com/feature/6246151319715840 "弃用 FTP 支持|Chrome 平台状态"  
[ChromePlatformStatus6251880185331712]: https://chromestatus.com/feature/6251880185331712 "引用器策略：默认为 strict-origin-when-cross-origin |Chrome 平台状态"  

[ChromiumFlashRoadmapSupportRemoved]: https://www.chromium.org/flash-roadmap#TOC-Flash-Support-Removed-from-Chromium-Target:-Chrome-88---Jan-2021- "从 Chromium (目标中删除的 Flash 支持：Chrome 88+ - 2021 年 1 月) - Flash 路线图|Chromium 项目"  

[ChromeDevelopersOrigintrialsAppCacheOriginTrial]: https://developers.chrome.com/origintrials/#/view_trial/1776670052997660673 "AppCache OriginTrial 令牌|Chrome 开发人员"  

[GoogleBlogSecurity20200206]: https://security.googleblog.com/2020/02/protecting-users-from-insecure_6.html "在 Google Chrome 中保护用户免受不安全下载 - Google Online 安全博客" 

[WebDevAppCacheRemoval]: https://web.dev/appcache-removal "准备 AppCache 删除|web.dev"  

<!--todo:  cleanup links  -->  
