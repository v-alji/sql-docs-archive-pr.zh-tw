---
title: 移動或刪除項目或專案 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- deleting project items
- projects [SQL Server Management Studio], item removal
- removing project items
ms.assetid: 3fd92434-70f5-466e-bef0-7e0fd73ddb1c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 679911f15d6c47f4274180602a5376c4ec03c77b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594315"
---
# <a name="remove-or-delete-an-item-or-project"></a><span data-ttu-id="faea9-102">移除或刪除項目或專案</span><span class="sxs-lookup"><span data-stu-id="faea9-102">Remove or Delete an Item or Project</span></span>
  <span data-ttu-id="faea9-103">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 專案中的專案項目有「查詢」、「連接」及「其他」檔案。</span><span class="sxs-lookup"><span data-stu-id="faea9-103">Project items in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] projects are Queries, Connections, and Miscellaneous files.</span></span> <span data-ttu-id="faea9-104">您可以在不從儲存體清除檔案的情況下，從方案中移除專案查詢和其他檔案。</span><span class="sxs-lookup"><span data-stu-id="faea9-104">You can remove project queries and miscellaneous files from your solution without erasing the files from storage.</span></span> <span data-ttu-id="faea9-105">當專案或項目在目前的方案中沒有用，而且您想要將它包含在另一個方案中時，就可移除它。</span><span class="sxs-lookup"><span data-stu-id="faea9-105">Remove a project or item when it is not useful in the current solution but you want to include it in another solution.</span></span>  
  
### <a name="to-remove-a-project-item"></a><span data-ttu-id="faea9-106">移除專案項目</span><span class="sxs-lookup"><span data-stu-id="faea9-106">To remove a project item</span></span>  
  
1.  <span data-ttu-id="faea9-107">在 [方案總管] 中，選取您要移除的專案項目。</span><span class="sxs-lookup"><span data-stu-id="faea9-107">In Solution Explorer, select the project item you want to remove.</span></span>  
  
2.  <span data-ttu-id="faea9-108">在 [編輯]  功能表上，按一下 [移除]  。</span><span class="sxs-lookup"><span data-stu-id="faea9-108">On the **Edit** menu, click **Remove**.</span></span>  
  
3.  <span data-ttu-id="faea9-109">在確認對話方塊中，按一下 [移除]  ，從專案中移除項目。</span><span class="sxs-lookup"><span data-stu-id="faea9-109">On the confirmation dialog, click **Remove** to remove the item from the project.</span></span>  
  
 <span data-ttu-id="faea9-110">移除的項目仍會在檔案系統中。</span><span class="sxs-lookup"><span data-stu-id="faea9-110">A removed item still exists on the file system.</span></span> <span data-ttu-id="faea9-111">因此，您可以將已移除的項目加入原始方案或另一個方案中。</span><span class="sxs-lookup"><span data-stu-id="faea9-111">Therefore, you can add a removed item to its original solution or to another solution.</span></span>  
  
#### <a name="to-remove-a-project"></a><span data-ttu-id="faea9-112">移除專案</span><span class="sxs-lookup"><span data-stu-id="faea9-112">To remove a project</span></span>  
  
1.  <span data-ttu-id="faea9-113">在 [方案總管] 中，選取您要移除的專案。</span><span class="sxs-lookup"><span data-stu-id="faea9-113">In Solution Explorer, select the project you want to remove.</span></span>  
  
2.  <span data-ttu-id="faea9-114">在 [編輯]  功能表上，按一下 [移除]  。</span><span class="sxs-lookup"><span data-stu-id="faea9-114">On the **Edit** menu, click **Remove**.</span></span>  
  
3.  <span data-ttu-id="faea9-115">在確認對話方塊中，按一下 [確定]  ，從方案中移除專案。</span><span class="sxs-lookup"><span data-stu-id="faea9-115">On the confirmation dialog, click **OK**, to remove the project from the solution.</span></span>  
  
 <span data-ttu-id="faea9-116">您可以永久刪除專案，但您必須先從 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 方案中，移除任何指向這個專案的參考，之後，再利用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 檔案總管，從儲存體中，永久刪除相關的檔案。</span><span class="sxs-lookup"><span data-stu-id="faea9-116">You can delete a project permanently, but you first need to remove any references to the project from [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] solutions, and then use [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Explorer to permanently delete the associated files from storage.</span></span>  
  
#### <a name="to-delete-a-project"></a><span data-ttu-id="faea9-117">刪除專案</span><span class="sxs-lookup"><span data-stu-id="faea9-117">To delete a project</span></span>  
  
1.  <span data-ttu-id="faea9-118">在 [方案總管] 中，移除您要從方案中刪除的專案。</span><span class="sxs-lookup"><span data-stu-id="faea9-118">In Solution Explorer, remove the project you want to delete from the solution.</span></span>  
  
2.  <span data-ttu-id="faea9-119">在 Windows 的 [檔案總管] 中，尋找和選取您要刪除的專案或項目的相關檔案。</span><span class="sxs-lookup"><span data-stu-id="faea9-119">In Windows Explorer, locate and select the files associated with the project or item you want to delete.</span></span>  
  
3.  <span data-ttu-id="faea9-120">在 [檔案]  功能表上，按一下 [刪除]  。</span><span class="sxs-lookup"><span data-stu-id="faea9-120">On the **File** menu, click **Delete**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="faea9-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="faea9-121">See Also</span></span>  
 <span data-ttu-id="faea9-122">[方案總管](solution-explorer.md) </span><span class="sxs-lookup"><span data-stu-id="faea9-122">[Solution Explorer](solution-explorer.md) </span></span>  
 <span data-ttu-id="faea9-123">[將新專案新增至專案](add-new-items-to-a-project.md) </span><span class="sxs-lookup"><span data-stu-id="faea9-123">[Add New Items to a Project](add-new-items-to-a-project.md) </span></span>  
 [<span data-ttu-id="faea9-124">將現有的項目加入至專案</span><span class="sxs-lookup"><span data-stu-id="faea9-124">Add Existing Items to a Project</span></span>](add-existing-items-to-a-project.md)  
  
  
