---
title: 作業屬性和新作業 (一般頁面) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.job.general.f1
ms.assetid: b6832840-1c18-4db8-94fc-080db880ae9f
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7a5d2ab84ed211a03a3c217bd5f4cd54453a4dc5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699184"
---
# <a name="job-properties-and-new-job-general-page"></a><span data-ttu-id="fdb11-102">作業屬性及新增作業 (一般頁面)</span><span class="sxs-lookup"><span data-stu-id="fdb11-102">Job Properties and New Job (General Page)</span></span>
  <span data-ttu-id="fdb11-103">使用此頁面來查看和修改 Agent 作業的一般屬性 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="fdb11-103">Use this page to view and modify the general properties of a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job.</span></span>  
  
## <a name="options"></a><span data-ttu-id="fdb11-104">選項。</span><span class="sxs-lookup"><span data-stu-id="fdb11-104">Options</span></span>  
 <span data-ttu-id="fdb11-105">**名稱**</span><span class="sxs-lookup"><span data-stu-id="fdb11-105">**Name**</span></span>  
 <span data-ttu-id="fdb11-106">變更作業的名稱。</span><span class="sxs-lookup"><span data-stu-id="fdb11-106">Change the name of the job.</span></span>  
  
 <span data-ttu-id="fdb11-107">**擁有者**</span><span class="sxs-lookup"><span data-stu-id="fdb11-107">**Owner**</span></span>  
 <span data-ttu-id="fdb11-108">選取作業的擁有者。</span><span class="sxs-lookup"><span data-stu-id="fdb11-108">Select the owner for the job.</span></span>  
  
 <span data-ttu-id="fdb11-109">**類別**</span><span class="sxs-lookup"><span data-stu-id="fdb11-109">**Category**</span></span>  
 <span data-ttu-id="fdb11-110">選取作業的作業類別目錄。</span><span class="sxs-lookup"><span data-stu-id="fdb11-110">Select the job category for the job.</span></span>  
  
 <span data-ttu-id="fdb11-111">**...**</span><span class="sxs-lookup"><span data-stu-id="fdb11-111">**...**</span></span>  
 <span data-ttu-id="fdb11-112">檢視選取之類別目錄中的作業。</span><span class="sxs-lookup"><span data-stu-id="fdb11-112">View the jobs in the selected category.</span></span>  
  
 <span data-ttu-id="fdb11-113">**說明**</span><span class="sxs-lookup"><span data-stu-id="fdb11-113">**Description**</span></span>  
 <span data-ttu-id="fdb11-114">變更作業的描述。</span><span class="sxs-lookup"><span data-stu-id="fdb11-114">Change the description of the job.</span></span>  
  
 <span data-ttu-id="fdb11-115">**已啟用**</span><span class="sxs-lookup"><span data-stu-id="fdb11-115">**Enabled**</span></span>  
 <span data-ttu-id="fdb11-116">啟用作業。</span><span class="sxs-lookup"><span data-stu-id="fdb11-116">Enable the job.</span></span> <span data-ttu-id="fdb11-117">未啟用作業時，則不會執行作業以回應排程或警示，但是您仍可以使用 **sp_start_job** 預存程序來啟動作業。</span><span class="sxs-lookup"><span data-stu-id="fdb11-117">When the job is not enabled, the job does not run in response to a schedule or an alert, although you can still start the job using the **sp_start_job** stored procedure.</span></span>  
  
 <span data-ttu-id="fdb11-118">**Source**</span><span class="sxs-lookup"><span data-stu-id="fdb11-118">**Source**</span></span>  
 <span data-ttu-id="fdb11-119">顯示作業的主要伺服器。</span><span class="sxs-lookup"><span data-stu-id="fdb11-119">Displays the master server for the job.</span></span> <span data-ttu-id="fdb11-120">只能在 [作業屬性] 的 [一般]\*\*\*\* 頁面使用。</span><span class="sxs-lookup"><span data-stu-id="fdb11-120">Only available on the **Job PropertiesGeneral** page.</span></span>  
  
 <span data-ttu-id="fdb11-121">**建立日期**</span><span class="sxs-lookup"><span data-stu-id="fdb11-121">**Created**</span></span>  
 <span data-ttu-id="fdb11-122">顯示作業的建立日期和時間。</span><span class="sxs-lookup"><span data-stu-id="fdb11-122">Displays the date and time that the job was created.</span></span> <span data-ttu-id="fdb11-123">只能在 [作業屬性] 的 [一般]\*\*\*\* 頁面使用。</span><span class="sxs-lookup"><span data-stu-id="fdb11-123">Only available on the **Job PropertiesGeneral** page.</span></span>  
  
 <span data-ttu-id="fdb11-124">**上次修改時間**</span><span class="sxs-lookup"><span data-stu-id="fdb11-124">**Last modified**</span></span>  
 <span data-ttu-id="fdb11-125">顯示作業的上次修改日期和時間。</span><span class="sxs-lookup"><span data-stu-id="fdb11-125">Displays the date and time that the job was last modified.</span></span> <span data-ttu-id="fdb11-126">只能在 [作業屬性] 的 [一般]\*\*\*\* 頁面使用。</span><span class="sxs-lookup"><span data-stu-id="fdb11-126">Only available on the **Job PropertiesGeneral** page.</span></span>  
  
 <span data-ttu-id="fdb11-127">**上次執行**</span><span class="sxs-lookup"><span data-stu-id="fdb11-127">**Last executed**</span></span>  
 <span data-ttu-id="fdb11-128">顯示作業上次開始執行的日期和時間。</span><span class="sxs-lookup"><span data-stu-id="fdb11-128">Displays the date and time that the job last started running.</span></span> <span data-ttu-id="fdb11-129">只能在 [作業屬性] 的 [一般]\*\*\*\* 頁面使用。</span><span class="sxs-lookup"><span data-stu-id="fdb11-129">Only available on the **Job PropertiesGeneral** page.</span></span>  
  
 <span data-ttu-id="fdb11-130">**檢視作業記錄**</span><span class="sxs-lookup"><span data-stu-id="fdb11-130">**View Job History**</span></span>  
 <span data-ttu-id="fdb11-131">檢視作業的作業記錄。</span><span class="sxs-lookup"><span data-stu-id="fdb11-131">View the job history for the job.</span></span> <span data-ttu-id="fdb11-132">只能在 [作業屬性] 的 [一般]\*\*\*\* 頁面使用。</span><span class="sxs-lookup"><span data-stu-id="fdb11-132">Only available on the **Job PropertiesGeneral** page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fdb11-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fdb11-133">See Also</span></span>  
 <span data-ttu-id="fdb11-134">[實作作業](implement-jobs.md) </span><span class="sxs-lookup"><span data-stu-id="fdb11-134">[Implement Jobs](implement-jobs.md) </span></span>  
 [<span data-ttu-id="fdb11-135">作業類別目錄：管理作業類別目錄</span><span class="sxs-lookup"><span data-stu-id="fdb11-135">Job Categories: Manage Job Categories</span></span>](job-categories-manage-job-categories.md)  
  
  
