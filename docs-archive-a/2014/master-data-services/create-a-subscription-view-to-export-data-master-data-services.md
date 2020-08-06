---
title: " (Master Data Services) 建立訂閱視圖 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- subscription views [Master Data Services], creating
- creating subscription views [Master Data Services]
ms.assetid: a5e28961-af16-414a-9845-d2e06aac5214
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: e5e2b901e56d75e97a444fd2858ef95872f3b766
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597893"
---
# <a name="create-a-subscription-view-master-data-services"></a><span data-ttu-id="2a63c-102">建立訂閱檢視 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="2a63c-102">Create a Subscription View (Master Data Services)</span></span>
  <span data-ttu-id="2a63c-103">當您想要在資料庫中建立資料 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 的視圖以供訂閱系統使用時，請建立訂閱視圖。</span><span class="sxs-lookup"><span data-stu-id="2a63c-103">Create a subscription view when you want to create a view of your data in the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database for use by subscribing systems.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="2a63c-104">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="2a63c-104">Prerequisites</span></span>  
 <span data-ttu-id="2a63c-105">若要執行此程序：</span><span class="sxs-lookup"><span data-stu-id="2a63c-105">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="2a63c-106">您必須擁有存取 **[整合管理]** 功能區域的權限。</span><span class="sxs-lookup"><span data-stu-id="2a63c-106">You must have permission to access the **Integration Management** functional area.</span></span>  
  
-   <span data-ttu-id="2a63c-107">您必須是模型管理員。</span><span class="sxs-lookup"><span data-stu-id="2a63c-107">You must be a model administrator.</span></span> <span data-ttu-id="2a63c-108">如需詳細資訊，請參閱系統[管理員 &#40;Master Data Services&#41;](administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="2a63c-108">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
### <a name="to-create-a-subscription-view"></a><span data-ttu-id="2a63c-109">若要建立訂閱檢視</span><span class="sxs-lookup"><span data-stu-id="2a63c-109">To create a subscription view</span></span>  
  
1.  <span data-ttu-id="2a63c-110">在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]中，按一下 **[整合管理]**。</span><span class="sxs-lookup"><span data-stu-id="2a63c-110">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **Integration Management**.</span></span>  
  
2.  <span data-ttu-id="2a63c-111">按一下功能表列上的 **[建立檢視表]**。</span><span class="sxs-lookup"><span data-stu-id="2a63c-111">From the menu bar, click **Create Views**.</span></span>  
  
3.  <span data-ttu-id="2a63c-112">在 [**訂閱視圖**] 頁面上，按一下 [**加入訂閱視圖**]。</span><span class="sxs-lookup"><span data-stu-id="2a63c-112">On the **Subscription Views** page, click **Add subscription view**.</span></span>  
  
4.  <span data-ttu-id="2a63c-113">在 [**建立訂閱視圖**] 窗格的 [**訂閱視圖名稱**] 方塊中，輸入此視圖的名稱。</span><span class="sxs-lookup"><span data-stu-id="2a63c-113">In the **Create Subscription View** pane, in the **Subscription view name** box, type a name for the view.</span></span>  
  
5.  <span data-ttu-id="2a63c-114">從 **[模型]** 清單中選取模型。</span><span class="sxs-lookup"><span data-stu-id="2a63c-114">From the **Model** list, select a model.</span></span>  
  
6.  <span data-ttu-id="2a63c-115">選取 [**版本**] 或 [**版本旗**標] 選項，然後從對應的清單中選取。</span><span class="sxs-lookup"><span data-stu-id="2a63c-115">Select either the **Version** or **Version Flag** option, and then select from the corresponding list.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="2a63c-116">根據版本旗標建立訂閱檢視。</span><span class="sxs-lookup"><span data-stu-id="2a63c-116">Create a subscription view based on a version flag.</span></span> <span data-ttu-id="2a63c-117">當您鎖定版本時，您可以重新指派旗標給開啟的版本，而不用更新訂閱檢視。</span><span class="sxs-lookup"><span data-stu-id="2a63c-117">When you lock a version, you can reassign the flag to an open version without updating the subscription view.</span></span>  
  
7.  <span data-ttu-id="2a63c-118">選取 [**實體**] 或 [**衍生**階層] 選項，然後從對應的清單中選取。</span><span class="sxs-lookup"><span data-stu-id="2a63c-118">Select either the **Entity** or **Derived hierarchy** option, and then select from the corresponding list.</span></span>  
  
8.  <span data-ttu-id="2a63c-119">從 **[格式]** 清單中選取訂閱檢視格式。</span><span class="sxs-lookup"><span data-stu-id="2a63c-119">From the **Format** list, select a subscription view format.</span></span>  
  
9. <span data-ttu-id="2a63c-120">如果您從 **[格式]** 清單中選擇 **[明確層級]** 或 **[衍生層級]** ，請輸入階層內要加入檢視中的層級數。</span><span class="sxs-lookup"><span data-stu-id="2a63c-120">If you chose **Explicit levels** or **Derived levels** from the **Format** list, type the number of levels in the hierarchy to include in the view.</span></span>  
  
10. <span data-ttu-id="2a63c-121">按一下 [檔案] 。</span><span class="sxs-lookup"><span data-stu-id="2a63c-121">Click **Save**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a63c-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2a63c-122">See Also</span></span>  
 <span data-ttu-id="2a63c-123">[將資料匯出 &#40;Master Data Services&#41;](overview-exporting-data-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="2a63c-123">[Exporting Data &#40;Master Data Services&#41;](overview-exporting-data-master-data-services.md) </span></span>  
 <span data-ttu-id="2a63c-124">[刪除訂閱視圖 &#40;Master Data Services&#41;](delete-a-subscription-view-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="2a63c-124">[Delete a Subscription View &#40;Master Data Services&#41;](delete-a-subscription-view-master-data-services.md) </span></span>  
 [<span data-ttu-id="2a63c-125">建立版本旗標 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="2a63c-125">Create a Version Flag &#40;Master Data Services&#41;</span></span>](create-a-version-flag-master-data-services.md)  
  
  
