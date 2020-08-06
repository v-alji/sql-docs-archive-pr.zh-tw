---
title: 使用已修改的資料庫協調資料庫關係圖 (Visual Database Tools) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- updating diagram to match database
- reconciling database diagrams
- diagrams [SQL Server], reconciling changes
- updating database to match diagram
- database diagrams [SQL Server], reconciling changes
ms.assetid: eda8dea2-eedd-43a7-85aa-92bd97783b5f
author: stevestein
ms.author: sstein
ms.openlocfilehash: e5e5127ab613a6f791919a98899e40caa2ddac20
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688378"
---
# <a name="reconcile-a-database-diagram-with-a-modified-database-visual-database-tools"></a><span data-ttu-id="39004-102">使用修改的資料庫協調資料庫圖表 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="39004-102">Reconcile a Database Diagram with a Modified Database (Visual Database Tools)</span></span>
  <span data-ttu-id="39004-103">當您準備開始更新資料庫以便與圖表相符時，您可以儲存資料庫圖表。</span><span class="sxs-lookup"><span data-stu-id="39004-103">You save your database diagram when you are ready to update the database to match your diagram.</span></span> <span data-ttu-id="39004-104">但是，在您開啟圖表之後，如果其他使用者更新資料庫，他們所做的變更可能會影響您的圖表，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="39004-104">However, if other users have updated the database since you opened your diagram, their changes might affect your diagram and vice versa.</span></span>  
  
 <span data-ttu-id="39004-105">儲存圖表會覆寫其他使用者的變更，讓資料庫符合您的圖表，以便使資料庫與圖表趨於一致。</span><span class="sxs-lookup"><span data-stu-id="39004-105">Saving your diagram will reconcile the database with your diagram by overwriting other users' changes so that the database will match your diagram.</span></span>  
  
### <a name="to-update-a-database-to-match-your-diagram"></a><span data-ttu-id="39004-106">若要更新資料庫以便與圖表相符</span><span class="sxs-lookup"><span data-stu-id="39004-106">To update a database to match your diagram</span></span>  
  
1.  <span data-ttu-id="39004-107">儲存您的資料庫圖表。</span><span class="sxs-lookup"><span data-stu-id="39004-107">Save your database diagram.</span></span>  
  
     <span data-ttu-id="39004-108">如果您先前未儲存圖表，請在 [儲存新資料庫圖表]  對話方塊中輸入圖表名稱，再選擇 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="39004-108">If you have not previously saved your diagram, type a name for the diagram in the **Save New Database Diagram** dialog box and choose **OK**.</span></span>  
  
2.  <span data-ttu-id="39004-109">[儲存]  對話方塊會列出儲存圖表時會影響的資料表。</span><span class="sxs-lookup"><span data-stu-id="39004-109">The **Save** dialog box lists the tables that will be affected when you save your diagram.</span></span> <span data-ttu-id="39004-110">選擇 [是]  繼續進行。</span><span class="sxs-lookup"><span data-stu-id="39004-110">Choose **Yes** to continue.</span></span>  
  
3.  <span data-ttu-id="39004-111">[偵測到資料庫變更]  對話方塊會列出修改的物件，這些物件將會變更，以符合您的圖表。</span><span class="sxs-lookup"><span data-stu-id="39004-111">The **Database Changes Detected** dialog box lists the objects that were modified and will be changed to match your diagram.</span></span> <span data-ttu-id="39004-112">選擇 [是]  儲存圖表，並接受變更的清單。</span><span class="sxs-lookup"><span data-stu-id="39004-112">Choose **Yes** to save the diagram and accept the list of changes.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="39004-113">如果您的圖表包含已經在資料庫中刪除的資料表和資料行，儲存圖表時只會在資料庫中重新建立這些物件的定義。</span><span class="sxs-lookup"><span data-stu-id="39004-113">If your diagram contains tables and columns that were deleted in the database, only their definitions are recreated in the database when you save your diagram.</span></span> <span data-ttu-id="39004-114">此程序不會還原刪除這些物件之前就存在於物件中的任何資料。</span><span class="sxs-lookup"><span data-stu-id="39004-114">This process does not restore any data that existed in these objects before their deletion.</span></span>  
  
### <a name="to-update-your-diagram-to-match-a-modified-database"></a><span data-ttu-id="39004-115">若要更新圖表以便與修改的資料庫相符</span><span class="sxs-lookup"><span data-stu-id="39004-115">To update your diagram to match a modified database</span></span>  
  
1.  <span data-ttu-id="39004-116">關閉圖表而不儲存變更。</span><span class="sxs-lookup"><span data-stu-id="39004-116">Close your diagram without saving changes.</span></span>  
  
2.  <span data-ttu-id="39004-117">在 [物件總管] 的圖表上按一下滑鼠右鍵。</span><span class="sxs-lookup"><span data-stu-id="39004-117">Right-click the diagram in Object Explorer.</span></span>  
  
3.  <span data-ttu-id="39004-118">從快速鍵功能表按一下 [重新整理]  。</span><span class="sxs-lookup"><span data-stu-id="39004-118">From the shortcut menu click **Refresh**.</span></span>  
  
4.  <span data-ttu-id="39004-119">重新開啟圖表。</span><span class="sxs-lookup"><span data-stu-id="39004-119">Reopen the diagram.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39004-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="39004-120">See Also</span></span>  
 [<span data-ttu-id="39004-121">使用資料庫圖表 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="39004-121">Work with Database Diagrams &#40;Visual Database Tools&#41;</span></span>](visual-database-tools.md)  
  
  
