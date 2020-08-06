---
title: 搜尋報表和其他項目 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 6a586659-5c2b-453b-8f40-a3a469277b17
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a964cbdbc674fb3d29e18b5e5075695f0033801e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585093"
---
# <a name="searching-for-reports-and-other-items-report-builder--and-ssrs"></a><span data-ttu-id="f9a46-102">搜尋報表和其他項目 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="f9a46-102">Searching for Reports and Other Items (Report Builder  and SSRS)</span></span>
  <span data-ttu-id="f9a46-103">您可以使用報表管理員，依名稱或描述在報表伺服器上搜尋特定項目。</span><span class="sxs-lookup"><span data-stu-id="f9a46-103">You can use Report Manager to search a report server for specific items by name or description.</span></span> <span data-ttu-id="f9a46-104">您可以搜尋已發行的報表、報表模型、資料夾、共用資料來源和資源。</span><span class="sxs-lookup"><span data-stu-id="f9a46-104">You can search for published reports, report models, folders, shared data sources, and resources.</span></span> <span data-ttu-id="f9a46-105">您不可以搜尋排程、擁有者、角色指派、報表記錄中的特定快照集或訂閱。</span><span class="sxs-lookup"><span data-stu-id="f9a46-105">You cannot search for schedules, owners, role assignments, specific snapshots in report history, or subscriptions.</span></span> <span data-ttu-id="f9a46-106">此搜尋會在儲存項目的報表伺服器資料庫上執行。</span><span class="sxs-lookup"><span data-stu-id="f9a46-106">The search is performed on the report server database where the items are stored.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f9a46-107">執行檔案系統的搜尋，不會傳回報表伺服器所管理項目的搜尋結果。</span><span class="sxs-lookup"><span data-stu-id="f9a46-107">Performing a file system search will not return search results for items managed by a report server.</span></span>  
  
-   <span data-ttu-id="f9a46-108">若要在報表管理員中搜尋項目，請在頁首的 [搜尋]\*\*\*\* 文字方塊中鍵入搜尋字串。</span><span class="sxs-lookup"><span data-stu-id="f9a46-108">To search for items in Report Manager, type a search string in the **Search for** text box at the top of the page.</span></span> <span data-ttu-id="f9a46-109">搜尋會由資料夾階層的最上層節點開始，然後沿著每一個分支繼續搜尋。</span><span class="sxs-lookup"><span data-stu-id="f9a46-109">Searches begin at the top node in the folder hierarchy and then proceed through every branch.</span></span> <span data-ttu-id="f9a46-110">如果您沒有存取特定分支的權限，則會略過該分支。</span><span class="sxs-lookup"><span data-stu-id="f9a46-110">If you do not have permission to access a specific branch, that branch is skipped.</span></span> <span data-ttu-id="f9a46-111">這適用於其他使用者專屬的 [我的報表] 資料夾，以及通常無法使用的其他資料夾。</span><span class="sxs-lookup"><span data-stu-id="f9a46-111">This applies to My Reports folders that belong to other users, and to other folders that are not generally available.</span></span> <span data-ttu-id="f9a46-112">只有您有權檢視的報表和項目，才會包含在搜尋結果中。</span><span class="sxs-lookup"><span data-stu-id="f9a46-112">Only reports and items that you have permission to view are included in the search results.</span></span>  
  
-   <span data-ttu-id="f9a46-113">若要依名稱或描述來搜尋項目，請指定想要符合的完整或部分文字。</span><span class="sxs-lookup"><span data-stu-id="f9a46-113">To search for an item by name or description, specify all or part of the text that you want to match.</span></span> <span data-ttu-id="f9a46-114">搜尋字串不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="f9a46-114">The search string is not case-sensitive.</span></span> <span data-ttu-id="f9a46-115">您不可以使用搜尋運算子，例如加號 (+) 或減號 (-)，來要求或排除搜尋準則。</span><span class="sxs-lookup"><span data-stu-id="f9a46-115">You cannot use search operators such as plus (+) or minus (-) symbols to require or exclude search criteria.</span></span>  
  
-   <span data-ttu-id="f9a46-116">若要搜尋報表中的特定文字，請使用報表上方的工具列。</span><span class="sxs-lookup"><span data-stu-id="f9a46-116">To search for specific text within a report, use the toolbar at the top of the report.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f9a46-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f9a46-117">See Also</span></span>  
 <span data-ttu-id="f9a46-118">[在報表管理員 &#40;報表產生器和 SSRS 中尋找及查看報表&#41;](finding-and-viewing-reports-in-the-web-portal-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f9a46-118">[Finding and Viewing Reports in Report Manager &#40;Report Builder and SSRS&#41;](finding-and-viewing-reports-in-the-web-portal-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="f9a46-119">[使用我的報表 &#40;報表產生器和 SSRS&#41;](using-my-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f9a46-119">[Using My Reports &#40;Report Builder and SSRS&#41;](using-my-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="f9a46-120">[尋找、查看和管理報表 &#40;報表產生器和 SSRS &#41;](finding-viewing-and-managing-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f9a46-120">[Finding, Viewing, and Managing Reports &#40;Report Builder and SSRS &#41;](finding-viewing-and-managing-reports-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="f9a46-121">開啟及關閉報表 &#40;報表管理員&#41;</span><span class="sxs-lookup"><span data-stu-id="f9a46-121">Open and Close a Report &#40;Report Manager&#41;</span></span>](../reports/open-and-close-a-report-report-manager.md)  
  
  
