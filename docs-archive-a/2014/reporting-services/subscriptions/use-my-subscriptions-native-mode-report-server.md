---
title: 使用我的訂閱 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- subscriptions [Reporting Services], My Subscriptions page
- My Subscriptions page [Reporting Services]
ms.assetid: e96623ba-677e-4748-8787-f32bed3b5c12
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f3378a65637ad04151cc517fd9047363af954c31
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706973"
---
# <a name="use-my-subscriptions"></a><span data-ttu-id="137bc-102">使用我的訂閱</span><span class="sxs-lookup"><span data-stu-id="137bc-102">Use My Subscriptions</span></span>
  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]<span data-ttu-id="137bc-103">報表管理員包含 [**我的訂閱**] 頁面，可將您的所有訂用帳戶組織成一個位置。</span><span class="sxs-lookup"><span data-stu-id="137bc-103">Report Manager includes a **My Subscriptions** page that organizes all of your subscriptions into one place.</span></span> <span data-ttu-id="137bc-104">您可以使用 [我的訂閱] 來檢視、修改和刪除現有的訂閱。</span><span class="sxs-lookup"><span data-stu-id="137bc-104">You can use My Subscriptions to view, modify, and delete existing subscriptions.</span></span> <span data-ttu-id="137bc-105">然而，無法用它來建立訂閱。</span><span class="sxs-lookup"><span data-stu-id="137bc-105">However, you cannot use it to create subscriptions.</span></span>  
  
||  
|-|  
|<span data-ttu-id="137bc-106">**[!INCLUDE[applies](../../includes/applies-md.md)]** [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 原生模式</span><span class="sxs-lookup"><span data-stu-id="137bc-106">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] Native mode</span></span>|  
  
 <span data-ttu-id="137bc-107">在 [我的訂閱] 中，您可以依資料夾、報表、描述、觸發程序、上次執行或狀態來排序訂閱。</span><span class="sxs-lookup"><span data-stu-id="137bc-107">Within My Subscriptions, you can sort subscriptions by folder, report, description, trigger, last run, or status.</span></span> <span data-ttu-id="137bc-108">除了 [上次執行] 依時間順序以外，所有值都依字母順序排序。</span><span class="sxs-lookup"><span data-stu-id="137bc-108">All values are sorted alphabetically except for Last Run, which is in chronological order.</span></span>  
  
 <span data-ttu-id="137bc-109">[我的訂閱] 僅顯示您所建立的訂閱。</span><span class="sxs-lookup"><span data-stu-id="137bc-109">My Subscriptions shows only the subscriptions that you create.</span></span> <span data-ttu-id="137bc-110">即使您已經加入成為其他使用者擁有之訂閱的訂閱者，它一樣不會列出其他使用者擁有的訂閱，也不會顯示資料驅動訂閱。</span><span class="sxs-lookup"><span data-stu-id="137bc-110">It does not list subscriptions that are owned by other users, even if you are added as a subscriber to those subscriptions, nor does it show data-driven subscriptions.</span></span>  
  
 <span data-ttu-id="137bc-111">您無法依名稱搜尋訂閱，也無法根據觸發程序資訊、狀態資訊等等來搜尋訂閱。</span><span class="sxs-lookup"><span data-stu-id="137bc-111">You cannot search for subscriptions by name, nor can you search for subscriptions based on trigger information, status information, and so forth.</span></span> <span data-ttu-id="137bc-112">如需詳細資訊，請參閱[在原生模式中建立、修改和刪除標準訂閱 &#40;Reporting Services&#41;](create-and-manage-subscriptions-for-native-mode-report-servers.md)。</span><span class="sxs-lookup"><span data-stu-id="137bc-112">For more information, see [Create, Modify, and Delete Standard Subscriptions &#40;Reporting Services in Native Mode&#41;](create-and-manage-subscriptions-for-native-mode-report-servers.md).</span></span>  
  
## <a name="how-to-use-my-subscriptions"></a><span data-ttu-id="137bc-113">如何使用我的訂閱</span><span class="sxs-lookup"><span data-stu-id="137bc-113">How to Use My Subscriptions</span></span>  
 <span data-ttu-id="137bc-114">我的訂閱可以透過報表管理員使用。</span><span class="sxs-lookup"><span data-stu-id="137bc-114">My Subscriptions is available through Report Manager.</span></span> <span data-ttu-id="137bc-115">若要存取我的訂閱，請按一下 [報表管理員全域] 工具列上的 [**我的訂閱**]。</span><span class="sxs-lookup"><span data-stu-id="137bc-115">To access My Subscriptions, click **My Subscriptions** on the Report Manager global toolbar.</span></span>  
  
## <a name="use-windows-powershell-to-list-mysubscriptions"></a><span data-ttu-id="137bc-116">使用 Windows PowerShell 來列出 MySubscriptions</span><span class="sxs-lookup"><span data-stu-id="137bc-116">Use Windows PowerShell to list MySubscriptions</span></span>  
 <span data-ttu-id="137bc-117">![PowerShell 相關內容](../media/rs-powershellicon.jpg "PowerShell 相關內容")</span><span class="sxs-lookup"><span data-stu-id="137bc-117">![PowerShell related content](../media/rs-powershellicon.jpg "PowerShell related content")</span></span>  
  
 <span data-ttu-id="137bc-118">下列 PowerShell 指令碼將會傳回目前使用者的訂閱和訂閱屬性清單。</span><span class="sxs-lookup"><span data-stu-id="137bc-118">The following PowerShell script will return the list of subscriptions and subscription properties for the current user.</span></span> <span data-ttu-id="137bc-119">如需詳細資訊，請參閱 [ReportingService2010.ListMySubscriptions 方法](https://technet.microsoft.com/library/reportservice2010.reportingservice2010.listmysubscriptions.aspx)。</span><span class="sxs-lookup"><span data-stu-id="137bc-119">For more information, see [ReportingService2010.ListMySubscriptions Method](https://technet.microsoft.com/library/reportservice2010.reportingservice2010.listmysubscriptions.aspx).</span></span>  
  
```powershell
#server -  all subscriptions of the current user at the given server or site  
$server="[server name]/reportserver"  
$rs2010 = New-WebServiceProxy -Uri "http://$server/ReportService2010.asmx" -Namespace SSRS.ReportingService2010 -UseDefaultCredential ;  
  
$subscriptions=ListMySubscriptions(ItemPathOrSiteURL)  
$subscriptions | select Path, report, Description, Owner, SubscriptionID, lastexecuted,Status  
#uncomment the following to list all the subscription properties  
#$subscriptions
```  
  
## <a name="see-also"></a><span data-ttu-id="137bc-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="137bc-120">See Also</span></span>  
 <span data-ttu-id="137bc-121">[Data-Driven Subscriptions](data-driven-subscriptions.md) </span><span class="sxs-lookup"><span data-stu-id="137bc-121">[Data-Driven Subscriptions](data-driven-subscriptions.md) </span></span>  
 <span data-ttu-id="137bc-122">[訂閱與傳遞 &#40;Reporting Services&#41;](subscriptions-and-delivery-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="137bc-122">[Subscriptions and Delivery &#40;Reporting Services&#41;](subscriptions-and-delivery-reporting-services.md) </span></span>  
 [<span data-ttu-id="137bc-123">建立及管理原生模式報表伺服器的訂閱</span><span class="sxs-lookup"><span data-stu-id="137bc-123">Create and Manage Subscriptions for Native Mode Report Servers</span></span>](../create-manage-subscriptions-native-mode-report-servers.md)  
