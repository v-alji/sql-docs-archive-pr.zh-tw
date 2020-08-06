---
title: 偵測到資料庫變更對話方塊 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.dlgbox.schema.databasechangesdetected
- vdtsql.chm:65543
- vdtsql.chm:65554
ms.assetid: 91f13086-371f-46a2-9f46-804c1415f3ed
author: stevestein
ms.author: sstein
ms.openlocfilehash: 91d58e812b93f207d592d245d094b0fbeddcce72
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699067"
---
# <a name="database-changes-detected-dialog-box-visual-database-tools"></a><span data-ttu-id="e7c7b-102">偵測到資料庫變更對話方塊 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="e7c7b-102">Database Changes Detected Dialog Box (Visual Database Tools)</span></span>
  <span data-ttu-id="e7c7b-103">如果您嘗試儲存資料庫圖表或選取的資料表，但是儲存動作將影響的某些資料庫物件對於資料庫而言已經過期，這個對話方塊便會出現。</span><span class="sxs-lookup"><span data-stu-id="e7c7b-103">This dialog appears if you attempt to save a database diagram or selected tables but some of the database objects that will be affected by the save action are out of date with the database.</span></span> <span data-ttu-id="e7c7b-104">接受此對話方塊中顯示的變更，會更新資料庫，以符合您的圖表，並覆寫其他使用者的變更。</span><span class="sxs-lookup"><span data-stu-id="e7c7b-104">Accepting the changes shown in this dialog box updates the database to match your diagram and overwrites other users' changes.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e7c7b-105">雖然您無法復原對於資料表或資料庫圖表所做的變更，但是，在您儲存資料表或圖表之前，這些變更都不會儲存至資料庫中。</span><span class="sxs-lookup"><span data-stu-id="e7c7b-105">Although you cannot undo changes made to a table or database diagram, the changes are not saved to the database until you save the table or diagram.</span></span> <span data-ttu-id="e7c7b-106">您可以選擇 [否]  以捨棄任何未儲存的變更，並關閉所有開啟的圖表，不予以儲存。</span><span class="sxs-lookup"><span data-stu-id="e7c7b-106">You can discard any unsaved changes by choosing **No** and closing all open diagrams without saving them.</span></span>  
  
## <a name="options"></a><span data-ttu-id="e7c7b-107">選項。</span><span class="sxs-lookup"><span data-stu-id="e7c7b-107">Options</span></span>  
 <span data-ttu-id="e7c7b-108">**警告差異偵測**</span><span class="sxs-lookup"><span data-stu-id="e7c7b-108">**Warn about difference detection**</span></span>  
 <span data-ttu-id="e7c7b-109">指定下次您嘗試儲存資料庫圖表或選取的資料表時，此對話方塊是否出現。</span><span class="sxs-lookup"><span data-stu-id="e7c7b-109">Specify whether this dialog box appears the next time you attempt to save a database diagram or selected tables.</span></span> <span data-ttu-id="e7c7b-110">核取表示每次您儲存對於資料庫而言已過期的圖表或資料表時，此對話方塊都會出現。</span><span class="sxs-lookup"><span data-stu-id="e7c7b-110">Checked means that the dialog box continues to appear each time you save a diagram or table that is out of date with the database.</span></span> <span data-ttu-id="e7c7b-111">未核取表示對話方塊不會出現。</span><span class="sxs-lookup"><span data-stu-id="e7c7b-111">Unchecked means that the dialog box does not appear.</span></span> <span data-ttu-id="e7c7b-112">依照預設，此方塊為核取。</span><span class="sxs-lookup"><span data-stu-id="e7c7b-112">By default, this box is checked.</span></span> <span data-ttu-id="e7c7b-113">如果您取消核取此選項，可以在 [選項]  對話方塊中重新核取。</span><span class="sxs-lookup"><span data-stu-id="e7c7b-113">If you uncheck this option, you can recheck it in the **Options** dialog box.</span></span>  
  
 <span data-ttu-id="e7c7b-114">**是**</span><span class="sxs-lookup"><span data-stu-id="e7c7b-114">**Yes**</span></span>  
 <span data-ttu-id="e7c7b-115">以清單中顯示的所有變更更新資料庫。</span><span class="sxs-lookup"><span data-stu-id="e7c7b-115">Update the database with all the changes shown in the list.</span></span>  
  
 <span data-ttu-id="e7c7b-116">**否**</span><span class="sxs-lookup"><span data-stu-id="e7c7b-116">**No**</span></span>  
 <span data-ttu-id="e7c7b-117">取消儲存動作。</span><span class="sxs-lookup"><span data-stu-id="e7c7b-117">Cancel the save action.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e7c7b-118">若要重新整理圖表以符合資料庫，可關閉圖表而不予以儲存，在 [伺服器總管] 的圖表上按一下滑鼠右鍵，並且按一下 [重新整理]，然後重新開啟圖表。</span><span class="sxs-lookup"><span data-stu-id="e7c7b-118">To refresh your diagram to match the database, close it without saving changes, right-click the diagram in Server Explorer and click Refresh, and then reopen the diagram.</span></span>  
  
 <span data-ttu-id="e7c7b-119">**儲存為文字檔**</span><span class="sxs-lookup"><span data-stu-id="e7c7b-119">**Save Text File**</span></span>  
 <span data-ttu-id="e7c7b-120">顯示 [另存新檔]  對話方塊，讓您指定包含資料庫變更清單的文字檔位置。</span><span class="sxs-lookup"><span data-stu-id="e7c7b-120">Display the **Save As** dialog box, letting you specify a location for a text file containing a list of the database changes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7c7b-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e7c7b-121">See Also</span></span>  
 <span data-ttu-id="e7c7b-122">[使用修改過的資料庫協調資料庫關係圖 &#40;Visual Database Tools&#41;](visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="e7c7b-122">[Reconcile a Database Diagram with a Modified Database &#40;Visual Database Tools&#41;](visual-database-tools.md) </span></span>  
 [<span data-ttu-id="e7c7b-123">多使用者環境 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="e7c7b-123">Multiuser Environments &#40;Visual Database Tools&#41;</span></span>](multiuser-environments-visual-database-tools.md)  
  
  
