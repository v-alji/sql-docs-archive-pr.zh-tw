---
title: 新增系統角色 (Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.newsystemrole.f1
ms.assetid: 7b4a0b98-975b-478a-8359-7db39ccbb347
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a744fc78bdd5ae6ef3a37f96ff5ae8cd10f71a80
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700693"
---
# <a name="new-system-role-management-studio"></a><span data-ttu-id="5e6d3-102">新增系統角色 (Management Studio)</span><span class="sxs-lookup"><span data-stu-id="5e6d3-102">New System Role (Management Studio)</span></span>
  <span data-ttu-id="5e6d3-103">使用此頁面，即可建立系統層級角色定義。</span><span class="sxs-lookup"><span data-stu-id="5e6d3-103">Use this page to create a system-level role definition.</span></span> <span data-ttu-id="5e6d3-104">系統角色定義會指定一組整個套用至報表伺服器的系統層級工作。</span><span class="sxs-lookup"><span data-stu-id="5e6d3-104">A system role definition specifies a set of system-level tasks that apply to a report server as whole.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5e6d3-105">角色定義只會用於以原生模式執行的報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="5e6d3-105">Role definitions are used only on a report server that runs in native mode.</span></span> <span data-ttu-id="5e6d3-106">如果報表伺服器是針對 SharePoint 整合所設定，這個頁面就無法使用。</span><span class="sxs-lookup"><span data-stu-id="5e6d3-106">If the report server is configured for SharePoint integration, this page is not available.</span></span>  
  
## <a name="options"></a><span data-ttu-id="5e6d3-107">選項。</span><span class="sxs-lookup"><span data-stu-id="5e6d3-107">Options</span></span>  
 <span data-ttu-id="5e6d3-108">**名稱**</span><span class="sxs-lookup"><span data-stu-id="5e6d3-108">**Name**</span></span>  
 <span data-ttu-id="5e6d3-109">鍵入角色定義的名稱。</span><span class="sxs-lookup"><span data-stu-id="5e6d3-109">Type the name of the role definition.</span></span> <span data-ttu-id="5e6d3-110">角色定義名稱在報表伺服器命名空間內必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="5e6d3-110">A role definition name must be unique within the report server namespace.</span></span> <span data-ttu-id="5e6d3-111">名稱必須至少包含一個英數字元。</span><span class="sxs-lookup"><span data-stu-id="5e6d3-111">A name must contain at least one alphanumeric character.</span></span> <span data-ttu-id="5e6d3-112">它也可以包含空格和某些符號。</span><span class="sxs-lookup"><span data-stu-id="5e6d3-112">It can also include spaces and some symbols.</span></span> <span data-ttu-id="5e6d3-113">指定名稱時，請勿使用下列字元：</span><span class="sxs-lookup"><span data-stu-id="5e6d3-113">Do not use the following characters when specifying a name:</span></span>  
  
 <span data-ttu-id="5e6d3-114">; ?</span><span class="sxs-lookup"><span data-stu-id="5e6d3-114">; ?</span></span> <span data-ttu-id="5e6d3-115">： \@ & = +，$/\*\< ></span><span class="sxs-lookup"><span data-stu-id="5e6d3-115">: \@ & = + , $ / \* \< ></span></span>  
  
 <span data-ttu-id="5e6d3-116">" /</span><span class="sxs-lookup"><span data-stu-id="5e6d3-116">" /</span></span>  
  
 <span data-ttu-id="5e6d3-117">**說明**</span><span class="sxs-lookup"><span data-stu-id="5e6d3-117">**Description**</span></span>  
 <span data-ttu-id="5e6d3-118">提供如何使用角色的描述，並列舉該角色支援的項目。</span><span class="sxs-lookup"><span data-stu-id="5e6d3-118">Provide a description that explains how to use the role and enumerates what the role supports.</span></span>  
  
 <span data-ttu-id="5e6d3-119">**Task**</span><span class="sxs-lookup"><span data-stu-id="5e6d3-119">**Task**</span></span>  
 <span data-ttu-id="5e6d3-120">選取可以透過此角色所執行的系統層級工作。</span><span class="sxs-lookup"><span data-stu-id="5e6d3-120">Select the system-level tasks that can be performed through this role.</span></span> <span data-ttu-id="5e6d3-121">您無法建立新工作，或修改 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]支援的現有工作。</span><span class="sxs-lookup"><span data-stu-id="5e6d3-121">You cannot create new tasks or modify the existing tasks that are supported by [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="5e6d3-122">您無法為系統角色定義選擇項目層級工作。</span><span class="sxs-lookup"><span data-stu-id="5e6d3-122">You cannot choose item-level tasks for a system role definition.</span></span>  
  
 <span data-ttu-id="5e6d3-123">**工作描述**</span><span class="sxs-lookup"><span data-stu-id="5e6d3-123">**Task Description**</span></span>  
 <span data-ttu-id="5e6d3-124">顯示工作的描述，其中列舉出工作能夠支援的作業或權限。</span><span class="sxs-lookup"><span data-stu-id="5e6d3-124">Shows a description of the task that enumerates the operations or permissions that the task supports.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e6d3-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5e6d3-125">See Also</span></span>  
 <span data-ttu-id="5e6d3-126">[Management Studio F1 說明中的報表伺服器](report-server-in-management-studio-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="5e6d3-126">[Report Server in Management Studio F1 Help](report-server-in-management-studio-f1-help.md) </span></span>  
 [<span data-ttu-id="5e6d3-127">角色定義</span><span class="sxs-lookup"><span data-stu-id="5e6d3-127">Role Definitions</span></span>](../security/role-definitions.md)  
  
  
