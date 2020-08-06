---
title: 刪除目錄項目 (Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.deleteitems.f1
ms.assetid: b0599e01-6dc3-4484-80d4-022a412e0ebd
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d2a1824f2611165c9ae891fcb702418244f3621e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594936"
---
# <a name="delete-catalog-items-management-studio"></a><span data-ttu-id="b28ea-102">刪除目錄項目 (Management Studio)</span><span class="sxs-lookup"><span data-stu-id="b28ea-102">Delete Catalog Items (Management Studio)</span></span>
  <span data-ttu-id="b28ea-103">您可以使用這個頁面刪除共用排程和角色定義。</span><span class="sxs-lookup"><span data-stu-id="b28ea-103">Use this page to delete shared schedules and role definitions.</span></span>  
  
 <span data-ttu-id="b28ea-104">如果您刪除了多個報表和訂閱所使用的共用排程，報表伺服器將會針對先前使用此共用排程的每個報表和訂閱建立個別的排程。</span><span class="sxs-lookup"><span data-stu-id="b28ea-104">If you delete a shared schedule that is used by multiple reports and subscriptions, the report server will create individual schedules for each report and subscription that previously used the shared schedule.</span></span> <span data-ttu-id="b28ea-105">每個新的個別排程將包含共用排程中原本指定的日期、時間和循環模式。</span><span class="sxs-lookup"><span data-stu-id="b28ea-105">Each new individual schedule will contain the date, time, and recurrence pattern that was specified in the shared schedule.</span></span> <span data-ttu-id="b28ea-106">請注意， [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 不會提供個別排程的集中管理功能。</span><span class="sxs-lookup"><span data-stu-id="b28ea-106">Note that [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] does not provide central management of individual schedules.</span></span> <span data-ttu-id="b28ea-107">如果您刪除了共用排程，現在就必須針對每個個別項目維護排程資訊。</span><span class="sxs-lookup"><span data-stu-id="b28ea-107">If you delete a shared schedule, you will now need to maintain the schedule information for each individual item.</span></span> <span data-ttu-id="b28ea-108">刪除共用排程之前，請使用 [報表頁面](schedule-properties-reports-page.md) 來判斷哪些報表目前正在使用共用排程。</span><span class="sxs-lookup"><span data-stu-id="b28ea-108">Before deleting a shared schedule, use the [Reports page](schedule-properties-reports-page.md) to determine which reports are currently using the shared schedule.</span></span>  
  
 <span data-ttu-id="b28ea-109">若為角色定義，您只能刪除目前並未在角色指派中使用的角色定義。</span><span class="sxs-lookup"><span data-stu-id="b28ea-109">For role definitions, you can only delete those that are not actively used in a role assignment.</span></span> <span data-ttu-id="b28ea-110">如果您嘗試刪除目前使用中的角色，報表伺服器將不會刪除該角色，而且您會看見描述此一情況的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="b28ea-110">If you try to delete a role that is currently in use, the report server will not delete the role and you will see an error message to that effect.</span></span> <span data-ttu-id="b28ea-111">如果這個頁面包含目前未使用中的單一角色定義，當您按一下 **[確定]** 時，系統就會刪除它。</span><span class="sxs-lookup"><span data-stu-id="b28ea-111">If this page contains a single role definition that is not currently in use, it will be deleted when you click **OK**.</span></span> <span data-ttu-id="b28ea-112">如果這個頁面包含多個角色，您無法選取要保留或移除的角色。</span><span class="sxs-lookup"><span data-stu-id="b28ea-112">If this page contains multiple roles, you cannot select which roles to keep or remove.</span></span> <span data-ttu-id="b28ea-113">當您按一下 **[確定]** 時，系統將刪除所有未使用的角色定義。</span><span class="sxs-lookup"><span data-stu-id="b28ea-113">All unused role definitions will be deleted when you click **OK**.</span></span>  
  
 <span data-ttu-id="b28ea-114">您無法恢復刪除作業。</span><span class="sxs-lookup"><span data-stu-id="b28ea-114">You cannot undo a delete operation.</span></span> <span data-ttu-id="b28ea-115">如果想要復原已刪除的項目，您就必須重新建立它，或是用報表伺服器資料庫的備份副本來還原。</span><span class="sxs-lookup"><span data-stu-id="b28ea-115">If you want to recover an item that you deleted, you must either recreate it or restore a backup copy of the report server database.</span></span>  
  
## <a name="options"></a><span data-ttu-id="b28ea-116">選項。</span><span class="sxs-lookup"><span data-stu-id="b28ea-116">Options</span></span>  
 <span data-ttu-id="b28ea-117">**名稱**</span><span class="sxs-lookup"><span data-stu-id="b28ea-117">**Name**</span></span>  
 <span data-ttu-id="b28ea-118">指定您正在刪除之項目的名稱。</span><span class="sxs-lookup"><span data-stu-id="b28ea-118">Specifies the name of the item you are deleting.</span></span>  
  
 <span data-ttu-id="b28ea-119">**型別**</span><span class="sxs-lookup"><span data-stu-id="b28ea-119">**Type**</span></span>  
 <span data-ttu-id="b28ea-120">顯示您正在刪除之項目的類型。</span><span class="sxs-lookup"><span data-stu-id="b28ea-120">Shows the type of item you are deleting.</span></span>  
  
 <span data-ttu-id="b28ea-121">**擁有者**</span><span class="sxs-lookup"><span data-stu-id="b28ea-121">**Owner**</span></span>  
 <span data-ttu-id="b28ea-122">顯示擁有者的名稱。</span><span class="sxs-lookup"><span data-stu-id="b28ea-122">Shows the name of the owner.</span></span> <span data-ttu-id="b28ea-123">在大多數情況下，這就是 System。</span><span class="sxs-lookup"><span data-stu-id="b28ea-123">In most cases, this is System.</span></span>  
  
 <span data-ttu-id="b28ea-124">**狀態**</span><span class="sxs-lookup"><span data-stu-id="b28ea-124">**Status**</span></span>  
 <span data-ttu-id="b28ea-125">顯示刪除作業的進度資訊。</span><span class="sxs-lookup"><span data-stu-id="b28ea-125">Shows progress information for a delete operation.</span></span>  
  
 <span data-ttu-id="b28ea-126">**錯誤**</span><span class="sxs-lookup"><span data-stu-id="b28ea-126">**Error**</span></span>  
 <span data-ttu-id="b28ea-127">如果在刪除項目時發生錯誤，則顯示錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="b28ea-127">Displays an error code if an error occurs while deleting an item.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b28ea-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b28ea-128">See Also</span></span>  
 <span data-ttu-id="b28ea-129">[刪除項目 &#40;Management Studio&#41;](delete-an-item-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="b28ea-129">[Delete an Item &#40;Management Studio&#41;](delete-an-item-management-studio.md) </span></span>  
 <span data-ttu-id="b28ea-130">[Management Studio F1 說明中的報表伺服器](report-server-in-management-studio-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="b28ea-130">[Report Server in Management Studio F1 Help](report-server-in-management-studio-f1-help.md) </span></span>  
 [<span data-ttu-id="b28ea-131">建立、修改和刪除排程</span><span class="sxs-lookup"><span data-stu-id="b28ea-131">Create, Modify, and Delete Schedules</span></span>](../subscriptions/create-modify-and-delete-schedules.md)  
  
  
