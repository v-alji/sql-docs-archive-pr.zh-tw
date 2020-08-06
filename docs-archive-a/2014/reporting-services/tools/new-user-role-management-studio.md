---
title: 新增使用者角色 (Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.newrole.f1
ms.assetid: 9f76a235-0b58-479c-8e5b-50588091b71c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 78201c5ebedd0cdb7f8108b9e6effcaa7fbe87b6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700690"
---
# <a name="new-user-role-management-studio"></a><span data-ttu-id="7cf1d-102">新增使用者角色 (Management Studio)</span><span class="sxs-lookup"><span data-stu-id="7cf1d-102">New User Role (Management Studio)</span></span>
  <span data-ttu-id="7cf1d-103">使用此頁面，即可建立項目層級角色定義。</span><span class="sxs-lookup"><span data-stu-id="7cf1d-103">Use this page to create an item-level role definition.</span></span> <span data-ttu-id="7cf1d-104">項目層級角色定義是具名的工作集合，其中列舉了與資料夾、報表、模型、資源以及共用資料來源相關，且使用者可以執行的工作。</span><span class="sxs-lookup"><span data-stu-id="7cf1d-104">An item-level role definition is a named collection of tasks that enumerate the tasks a user can perform in relation to folders, reports, models, resources, and shared data sources.</span></span> <span data-ttu-id="7cf1d-105">預先定義的瀏覽者角色，就是項目層級角色定義的範例，這個角色會識別報表使用者在導覽資料夾和檢視報表時，可能需要的動作種類。</span><span class="sxs-lookup"><span data-stu-id="7cf1d-105">An example of an item-level role definition is the predefined Browser role that identifies the kinds of actions a report end user might require for navigating folders and viewing reports.</span></span>  
  
 <span data-ttu-id="7cf1d-106">預期角色定義的數目並不多。</span><span class="sxs-lookup"><span data-stu-id="7cf1d-106">Role definitions are intended to be few in number.</span></span> <span data-ttu-id="7cf1d-107">多數組織都只需要少數的角色定義。</span><span class="sxs-lookup"><span data-stu-id="7cf1d-107">Most organizations only require a few role definitions.</span></span> <span data-ttu-id="7cf1d-108">不過，如果預先定義的角色定義不敷使用，您可以加以改變或建立新的角色定義。</span><span class="sxs-lookup"><span data-stu-id="7cf1d-108">However, if the predefined role definitions are insufficient, you can vary them or create new ones.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7cf1d-109">角色定義只會用於以原生模式執行的報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="7cf1d-109">Role definitions are used only on a report server that runs in native mode.</span></span> <span data-ttu-id="7cf1d-110">如果報表伺服器是針對 SharePoint 整合所設定，這個頁面就無法使用。</span><span class="sxs-lookup"><span data-stu-id="7cf1d-110">If the report server is configured for SharePoint integration, this page is not available.</span></span>  
  
## <a name="options"></a><span data-ttu-id="7cf1d-111">選項。</span><span class="sxs-lookup"><span data-stu-id="7cf1d-111">Options</span></span>  
 <span data-ttu-id="7cf1d-112">**名稱**</span><span class="sxs-lookup"><span data-stu-id="7cf1d-112">**Name**</span></span>  
 <span data-ttu-id="7cf1d-113">鍵入角色定義的名稱。</span><span class="sxs-lookup"><span data-stu-id="7cf1d-113">Type the name of the role definition.</span></span> <span data-ttu-id="7cf1d-114">角色定義名稱在報表伺服器命名空間內必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="7cf1d-114">A role definition name must be unique within the report server namespace.</span></span> <span data-ttu-id="7cf1d-115">名稱必須至少包含一個英數字元。</span><span class="sxs-lookup"><span data-stu-id="7cf1d-115">A name must contain at least one alphanumeric character.</span></span> <span data-ttu-id="7cf1d-116">它也可以包含空格和某些符號。</span><span class="sxs-lookup"><span data-stu-id="7cf1d-116">It can also include spaces and some symbols.</span></span> <span data-ttu-id="7cf1d-117">指定名稱時，請勿使用下列字元：</span><span class="sxs-lookup"><span data-stu-id="7cf1d-117">Do not use the following characters when specifying a name:</span></span>  
  
 <span data-ttu-id="7cf1d-118">; ?</span><span class="sxs-lookup"><span data-stu-id="7cf1d-118">; ?</span></span> <span data-ttu-id="7cf1d-119">： \@ & = +，$/\*\< ></span><span class="sxs-lookup"><span data-stu-id="7cf1d-119">: \@ & = + , $ / \* \< ></span></span>  
  
 <span data-ttu-id="7cf1d-120">" /</span><span class="sxs-lookup"><span data-stu-id="7cf1d-120">" /</span></span>  
  
 <span data-ttu-id="7cf1d-121">**說明**</span><span class="sxs-lookup"><span data-stu-id="7cf1d-121">**Description**</span></span>  
 <span data-ttu-id="7cf1d-122">鍵入說明如何使用角色的描述，並列舉該角色支援的項目。</span><span class="sxs-lookup"><span data-stu-id="7cf1d-122">Type a description that explains how to use the role and enumerates what the role supports.</span></span>  
  
 <span data-ttu-id="7cf1d-123">**Task**</span><span class="sxs-lookup"><span data-stu-id="7cf1d-123">**Task**</span></span>  
 <span data-ttu-id="7cf1d-124">選取可以透過此角色執行的工作。</span><span class="sxs-lookup"><span data-stu-id="7cf1d-124">Select the tasks that can be performed through this role.</span></span> <span data-ttu-id="7cf1d-125">您無法建立新工作，或修改 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]支援的現有工作。</span><span class="sxs-lookup"><span data-stu-id="7cf1d-125">You cannot create new tasks or modify the existing tasks that are supported by [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="7cf1d-126">項目層級角色定義中只能使用項目層級工作。</span><span class="sxs-lookup"><span data-stu-id="7cf1d-126">Only item-level tasks can be used in an item-level role definition.</span></span>  
  
 <span data-ttu-id="7cf1d-127">**工作描述**</span><span class="sxs-lookup"><span data-stu-id="7cf1d-127">**Task Description**</span></span>  
 <span data-ttu-id="7cf1d-128">顯示工作的描述，其中列舉出工作能夠支援的作業或權限。</span><span class="sxs-lookup"><span data-stu-id="7cf1d-128">Shows a description of the task that enumerates the operations or permissions that the task supports.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7cf1d-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7cf1d-129">See Also</span></span>  
 <span data-ttu-id="7cf1d-130">[Management Studio F1 說明中的報表伺服器](report-server-in-management-studio-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="7cf1d-130">[Report Server in Management Studio F1 Help](report-server-in-management-studio-f1-help.md) </span></span>  
 [<span data-ttu-id="7cf1d-131">角色定義</span><span class="sxs-lookup"><span data-stu-id="7cf1d-131">Role Definitions</span></span>](../security/role-definitions.md)  
  
  
