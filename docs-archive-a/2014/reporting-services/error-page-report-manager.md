---
title: 錯誤頁面 (報表管理員) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 8311ed32-00f3-451d-8279-946429f5fee1
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: fc50a5b0516bcbf8221ce3ee130090f66a929c3e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703885"
---
# <a name="error-page-report-manager"></a><span data-ttu-id="09a16-102">錯誤頁面 (報表管理員)</span><span class="sxs-lookup"><span data-stu-id="09a16-102">Error Page (Report Manager)</span></span>
  <span data-ttu-id="09a16-103">使用 [錯誤] 頁面即可檢視錯誤狀況的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="09a16-103">Use the Error page to view details about an error condition.</span></span> <span data-ttu-id="09a16-104">以伺服器為基礎或以會話為基礎的錯誤會出現在此頁面上。</span><span class="sxs-lookup"><span data-stu-id="09a16-104">Server-based or session-based errors appear on this page.</span></span> <span data-ttu-id="09a16-105">有關特定頁面控制項的驗證錯誤，則會內嵌顯示於該控制項旁。</span><span class="sxs-lookup"><span data-stu-id="09a16-105">Validation errors that relate to specific page controls display inline next to the control.</span></span>  
  
-   <span data-ttu-id="09a16-106">如果您要流覽至本機報表伺服器，而且看到類似下面的錯誤，請參閱：[設定原生模式報表伺服器進行本機管理 &#40;SSRS&#41;](report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md)</span><span class="sxs-lookup"><span data-stu-id="09a16-106">If you are browsing to a local report server and you see errors similar to the following, see: [Configure a Native Mode Report Server for Local Administration &#40;SSRS&#41;](report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md)</span></span>  
  
     <span data-ttu-id="09a16-107">使用者 ' Domain \\ [user name] ' 沒有必要的許可權。</span><span class="sxs-lookup"><span data-stu-id="09a16-107">User 'Domain\\[user name]' does not have required permissions.</span></span> <span data-ttu-id="09a16-108">請確認已授與足夠的權限，而且滿足 Windows 使用者帳戶控制 (UAC) 的限制。</span><span class="sxs-lookup"><span data-stu-id="09a16-108">Verify that sufficient permissions have been granted and Windows User Account Control (UAC) restrictions have been addressed.</span></span>  
  
-   <span data-ttu-id="09a16-109">如果您看見類似下面的錯誤訊息，請參閱＜ [Configure a Report Server for Remote Administration](report-server/configure-a-report-server-for-remote-administration.md)＞。</span><span class="sxs-lookup"><span data-stu-id="09a16-109">If you see error messages similar to the following, see [Configure a Report Server for Remote Administration](report-server/configure-a-report-server-for-remote-administration.md).</span></span>  
  
     <span data-ttu-id="09a16-110">找不到電腦。</span><span class="sxs-lookup"><span data-stu-id="09a16-110">The machine could not be found.</span></span> <span data-ttu-id="09a16-111">\*RPC 伺服器無法使用。</span><span class="sxs-lookup"><span data-stu-id="09a16-111">"The RPC server is unavailable.</span></span> <span data-ttu-id="09a16-112">(來自 HRESULT 的例外狀況: 0x800706BA)」。</span><span class="sxs-lookup"><span data-stu-id="09a16-112">(Exception from HRESULT: 0x800706BA)".</span></span>  
  
-   <span data-ttu-id="09a16-113">您可以在 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 報表伺服器上設定伺服器屬性，以便傳回有關遠端伺服器上發生之錯誤狀況的其他資訊。</span><span class="sxs-lookup"><span data-stu-id="09a16-113">You can set server properties on a [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] report server to return additional information about error conditions that occur on remote servers.</span></span> <span data-ttu-id="09a16-114">如果錯誤訊息包含「如需有關此錯誤的詳細資訊，請流覽至本機伺服器電腦上的報表伺服器，或啟用遠端錯誤」文字，請參閱[&#40;Reporting Services&#41;啟用遠端錯誤](report-server/enable-remote-errors-reporting-services.md)。</span><span class="sxs-lookup"><span data-stu-id="09a16-114">If an error message contains the text "For more information about this error, navigate to the report server on the local server machine, or enable remote errors", see [Enable Remote Errors &#40;Reporting Services&#41;](report-server/enable-remote-errors-reporting-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09a16-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="09a16-115">See Also</span></span>  
 <span data-ttu-id="09a16-116">[設定報表管理員 &#40;原生模式&#41;](report-server/configure-web-portal.md) </span><span class="sxs-lookup"><span data-stu-id="09a16-116">[Configure Report Manager &#40;Native Mode&#41;](report-server/configure-web-portal.md) </span></span>  
 <span data-ttu-id="09a16-117">[錯誤和事件參考 &#40;Reporting Services&#41;](troubleshooting/errors-and-events-reference-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="09a16-117">[Errors and Events Reference &#40;Reporting Services&#41;](troubleshooting/errors-and-events-reference-reporting-services.md) </span></span>  
 [<span data-ttu-id="09a16-118">報表管理員 F1 說明</span><span class="sxs-lookup"><span data-stu-id="09a16-118">Report Manager F1 Help</span></span>](../../2014/reporting-services/report-manager-f1-help.md)  
  
  
