---
title: 將報表連結至模型做為點選連結報表 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- customizing clickthrough reports
- clickthrough reports, customizing
- clickthrough reports, templates
ms.assetid: 3af42de3-67ef-41c2-bc8a-7045baec6f63
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: cb84f8036dbe5a1694628144f0b948452261ca75
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592503"
---
# <a name="link-a-report-to-a-model-as-a-clickthrough-report"></a><span data-ttu-id="a9cfe-102">將報表連結至模型以做為點選連結報表</span><span class="sxs-lookup"><span data-stu-id="a9cfe-102">Link a Report to a Model as a Clickthrough Report</span></span>
  <span data-ttu-id="a9cfe-103">如果不使用預設點選連結報表範本，您可以建立報表產生器報表，然後將它連結至報表模型中的特定實體。</span><span class="sxs-lookup"><span data-stu-id="a9cfe-103">Instead of using the default clickthrough report templates, you can create a Report Builder report and then link it to a specific entity in the report model.</span></span> <span data-ttu-id="a9cfe-104">當檢視報表的人按一下主報表中的互動式資料時，此報表就會顯示為點選連結報表。</span><span class="sxs-lookup"><span data-stu-id="a9cfe-104">When the person viewing the report clicks the interactive data in the main report, this report is displayed as a clickthrough report.</span></span> <span data-ttu-id="a9cfe-105">若要將報表連結至實體，請使用 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 報表管理員。</span><span class="sxs-lookup"><span data-stu-id="a9cfe-105">To link a report to an entity, use [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Report Manager.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="a9cfe-106">報表中使用的主要實體或基底實體，必須與連結報表的實體相同。</span><span class="sxs-lookup"><span data-stu-id="a9cfe-106">The primary, or base, entity that is used in the report must to be the same entity to which the report is linked.</span></span>  
  
### <a name="to-start-report-manager-from-a-browser"></a><span data-ttu-id="a9cfe-107">若要從瀏覽器啟動報表管理員</span><span class="sxs-lookup"><span data-stu-id="a9cfe-107">To start Report Manager from a browser</span></span>  
  
1.  <span data-ttu-id="a9cfe-108">開啟 [!INCLUDE[msCoName](../includes/msconame-md.md)] Internet Explorer 6.0 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="a9cfe-108">Open [!INCLUDE[msCoName](../includes/msconame-md.md)] Internet Explorer 6.0 or later.</span></span>  
  
2.  <span data-ttu-id="a9cfe-109">在網頁瀏覽器的網址列中，輸入報表管理員 URL。</span><span class="sxs-lookup"><span data-stu-id="a9cfe-109">In the address bar of the Web browser, type the Report Manager URL.</span></span> <span data-ttu-id="a9cfe-110">根據預設，URL 為 HTTP:// \<*ComputerName*> /reports。</span><span class="sxs-lookup"><span data-stu-id="a9cfe-110">By default, the URL is http://\<*ComputerName*>/reports.</span></span>  
  
### <a name="to-create-a-customized-clickthrough-report"></a><span data-ttu-id="a9cfe-111">建立自訂點選連結報表</span><span class="sxs-lookup"><span data-stu-id="a9cfe-111">To create a customized clickthrough report</span></span>  
  
1.  <span data-ttu-id="a9cfe-112">導覽至您要加入自訂點選連結報表的目標報表模型。</span><span class="sxs-lookup"><span data-stu-id="a9cfe-112">Navigate to the report model to which you want to add the customized clickthrough report.</span></span>  
  
2.  <span data-ttu-id="a9cfe-113">按兩下報表模型。</span><span class="sxs-lookup"><span data-stu-id="a9cfe-113">Double-click the report model.</span></span>  
  
3.  <span data-ttu-id="a9cfe-114">按一下 **[Clickthrough]**。</span><span class="sxs-lookup"><span data-stu-id="a9cfe-114">Click **Clickthrough**.</span></span>  
  
4.  <span data-ttu-id="a9cfe-115">選取您要附加自訂點選連結報表的目標實體。</span><span class="sxs-lookup"><span data-stu-id="a9cfe-115">Select the entity to which you want to attach the customized clickthrough report.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a9cfe-116">這個實體必須與自訂點選連結報表的基礎實體相同。</span><span class="sxs-lookup"><span data-stu-id="a9cfe-116">This entity must be the same as the base entity of the customized clickthrough report.</span></span>  
  
5.  <span data-ttu-id="a9cfe-117">若要在按一下所選實體的單一執行個體時顯示自訂報表，按一下單一執行個體報表的 **[瀏覽]** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="a9cfe-117">To display the customized report when a single instance of the selected entity is clicked, click the Single instance report **Browse** button.</span></span>  
  
     <span data-ttu-id="a9cfe-118">-或-</span><span class="sxs-lookup"><span data-stu-id="a9cfe-118">-or-</span></span>  
  
     <span data-ttu-id="a9cfe-119">若要在按一下所選實體的多個執行個體時顯示自訂報表，按一下多個執行個體報表的 **[瀏覽]** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="a9cfe-119">To display the customized report when a multiple instance of the selected entity is clicked, click the Multiple instance report **Browse** button.</span></span>  
  
6.  <span data-ttu-id="a9cfe-120">選取報表，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="a9cfe-120">Select the report and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="a9cfe-121">按一下 [套用]。</span><span class="sxs-lookup"><span data-stu-id="a9cfe-121">Click **Apply**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9cfe-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a9cfe-122">See Also</span></span>  
 [<span data-ttu-id="a9cfe-123">&#40;SSRS&#41;的點選連結報表</span><span class="sxs-lookup"><span data-stu-id="a9cfe-123">Clickthrough Reports &#40;SSRS&#41;</span></span>](reports/clickthrough-reports-ssrs.md)  
  
  
