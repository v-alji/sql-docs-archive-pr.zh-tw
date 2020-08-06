---
title: 結束定義域管理活動 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: ab6505ad-3090-453b-bb01-58435e7fa7c0
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: c776674a369bfae8c7da6fa0deabfbd932029570
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700255"
---
# <a name="end-the-domain-management-activity"></a><span data-ttu-id="3044f-102">結束定義域管理活動</span><span class="sxs-lookup"><span data-stu-id="3044f-102">End the Domain Management Activity</span></span>
  <span data-ttu-id="3044f-103">此主題描述如何在 [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) 中完成、關閉或取消定義域管理活動。</span><span class="sxs-lookup"><span data-stu-id="3044f-103">This topic describes how to complete, close, or cancel the domain management activity in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS).</span></span> <span data-ttu-id="3044f-104">定義域管理不是由精靈執行，所以可以從定義域管理活動的任何頁面使用底下所述的控制項。</span><span class="sxs-lookup"><span data-stu-id="3044f-104">Domain management is not performed by a wizard, so the controls described below can used from any of the pages of the domain management activity.</span></span>  
  
## <a name="end-domain-management"></a><span data-ttu-id="3044f-105">結束定義域管理</span><span class="sxs-lookup"><span data-stu-id="3044f-105">End Domain Management</span></span>  
 <span data-ttu-id="3044f-106">**[完成]**</span><span class="sxs-lookup"><span data-stu-id="3044f-106">**Finish**</span></span>  
 <span data-ttu-id="3044f-107">按一下以完成定義域管理。</span><span class="sxs-lookup"><span data-stu-id="3044f-107">Click to complete domain management.</span></span> <span data-ttu-id="3044f-108">隨即顯示快顯視窗，讓您執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="3044f-108">A popup will be displayed enabling you to do the following:</span></span>  
  
-   <span data-ttu-id="3044f-109">**是-發佈知識庫並**結束：將會發行知識庫，供目前使用者或其他人使用。</span><span class="sxs-lookup"><span data-stu-id="3044f-109">**Yes - Publish the knowledge base and exit**: The knowledge base will be published for the current user or others to use.</span></span> <span data-ttu-id="3044f-110">知識庫不會鎖定，知識庫狀態 (在知識庫資料表中) 將會設為空白，而且定義域管理和知識探索活動可供使用。</span><span class="sxs-lookup"><span data-stu-id="3044f-110">The knowledge base will not be locked, the state of the knowledge base (in the knowledge base table) will be set to empty, and both the Domain Management and Knowledge Discovery activities will be available.</span></span> <span data-ttu-id="3044f-111">您會返回 [開啟知識庫] 畫面。</span><span class="sxs-lookup"><span data-stu-id="3044f-111">You will be returned to the Open Knowledge Base screen.</span></span>  
  
-   <span data-ttu-id="3044f-112">**否-儲存知識庫工作並**結束：將會儲存您的工作，知識庫會保持鎖定，而且知識庫的狀態將會設定為 [工作中]。</span><span class="sxs-lookup"><span data-stu-id="3044f-112">**No - Save the work on the knowledge base and exit**: Your work will be saved, the knowledge base will remained locked, and the state of the knowledge base will be set to In work.</span></span> <span data-ttu-id="3044f-113">定義域管理和知識探索活動都可供使用。</span><span class="sxs-lookup"><span data-stu-id="3044f-113">Both the Domain Management and Knowledge Discovery activities will be available.</span></span> <span data-ttu-id="3044f-114">您會返回首頁。</span><span class="sxs-lookup"><span data-stu-id="3044f-114">You will be returned to the home page.</span></span>  
  
-   <span data-ttu-id="3044f-115">**取消 - 留在目前畫面**：快顯視窗將會關閉，而且您會返回 [定義域管理] 畫面。</span><span class="sxs-lookup"><span data-stu-id="3044f-115">**Cancel - Stay on the current screen**: The popup will be closed and you will be returned to the Domain Management screen.</span></span>  
  
 <span data-ttu-id="3044f-116">**取消**</span><span class="sxs-lookup"><span data-stu-id="3044f-116">**Cancel**</span></span>  
 <span data-ttu-id="3044f-117">按一下以結束 [定義域管理] 活動，不儲存工作並返回 DQS 首頁。</span><span class="sxs-lookup"><span data-stu-id="3044f-117">Click to terminate the Domain Management activity, losing your work, and return to the DQS home page.</span></span>  
  
 <span data-ttu-id="3044f-118">**關閉**</span><span class="sxs-lookup"><span data-stu-id="3044f-118">**Close**</span></span>  
 <span data-ttu-id="3044f-119">按一下以儲存工作，並返回 DQS 首頁。</span><span class="sxs-lookup"><span data-stu-id="3044f-119">Click to save your work, and return to the DQS home page.</span></span> <span data-ttu-id="3044f-120">知識庫會鎖定，而且在 **[開啟知識庫]** 畫面中知識庫資料表的知識庫狀態將會是 **[定義域管理]**。</span><span class="sxs-lookup"><span data-stu-id="3044f-120">The knowledge base will be locked, and the state of the knowledge base in the knowledge base table in the **Open Knowledge Base** screen will be **Domain Management**.</span></span> <span data-ttu-id="3044f-121">在按一下 **[關閉]** 之後，若要執行 [知識探索] 活動，您必須返回 **[定義域管理]** 畫面，按一下 **[完成]**，然後按一下 **[是]** 發行知識庫，或按一下 **[否]** 儲存知識庫工作並結束。</span><span class="sxs-lookup"><span data-stu-id="3044f-121">After clicking **Close**, to perform the Knowledge Discovery activity, you would have to return to the **Domain Management** screen, click **Finish**, and then click either **Yes** to publish the knowledge base or **No** to save the work on the knowledge base and exit.</span></span>  <span data-ttu-id="3044f-122">如需開啟鎖定之知識庫的詳細資訊，請參閱＜ [Open a Knowledge Base](../../2014/data-quality-services/open-a-knowledge-base.md)＞。</span><span class="sxs-lookup"><span data-stu-id="3044f-122">For more information on opening a locked knowledge base, see [Open a Knowledge Base](../../2014/data-quality-services/open-a-knowledge-base.md).</span></span>  
  
  
