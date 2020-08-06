---
title: 將方案和專案加入至原始檔控制 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- projects [SQL Server Management Studio], source controls
- solutions [SQL Server Management Studio], source controls
- source controls [SQL Server Management Studio], solutions
- source controls [SQL Server Management Studio], projects
ms.assetid: 3eaed80e-6f55-42ea-a964-aca31c09d055
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 5256795677f4e8ce4249737d25d3ded1c4cd69c8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698554"
---
# <a name="add-solutions-and-projects-to-source-control"></a><span data-ttu-id="225d6-102">將方案與專案加入原始檔控制</span><span class="sxs-lookup"><span data-stu-id="225d6-102">Add Solutions and Projects to Source Control</span></span>
  <span data-ttu-id="225d6-103">當您將方案加入原始檔控制中，方案會成為原始檔控制提供者所建立和維護之動態版本控制保存檔的一部份。</span><span class="sxs-lookup"><span data-stu-id="225d6-103">When you add a solution to source control, the solution becomes part of a dynamic versioning archive created and maintained by the source control provider.</span></span> <span data-ttu-id="225d6-104">每次有人簽入方案的新版本時，這個版本都會成為保存檔的一部份，其他原始檔控制使用者可以使用它。</span><span class="sxs-lookup"><span data-stu-id="225d6-104">Each time someone checks in a new version of the solution, that version becomes part of the archive and is available to other source control users.</span></span>  
  
 <span data-ttu-id="225d6-105">將方案加入原始檔控制中，也會啟動集中式檔案管理的系統。</span><span class="sxs-lookup"><span data-stu-id="225d6-105">Adding a solution to source control also starts a system of centralized file management.</span></span> <span data-ttu-id="225d6-106">原始檔控制提供者 (如 [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe) 會控制原始檔控制項目的存取；如果原始檔控制檔案尚未簽出，原始檔控制用戶端便無法寫入它們的本機副本。</span><span class="sxs-lookup"><span data-stu-id="225d6-106">Source control providers, such as [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe, control access to source-controlled items; source control clients cannot write to local copies of source-controlled files without checking them out.</span></span>  
  
 <span data-ttu-id="225d6-107">下表描述此章節的主題。</span><span class="sxs-lookup"><span data-stu-id="225d6-107">The following table describes the topics in this section.</span></span>  
  
|<span data-ttu-id="225d6-108">主題</span><span class="sxs-lookup"><span data-stu-id="225d6-108">Topic</span></span>|<span data-ttu-id="225d6-109">描述</span><span class="sxs-lookup"><span data-stu-id="225d6-109">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="225d6-110">將方案加入原始檔控制</span><span class="sxs-lookup"><span data-stu-id="225d6-110">Add Solutions to Source Control</span></span>](../../2014/database-engine/add-solutions-to-source-control.md)|<span data-ttu-id="225d6-111">描述您可以加入的專案類型，以及提供如何將方案加入原始檔控制的指示。</span><span class="sxs-lookup"><span data-stu-id="225d6-111">Describes the project types you can add, and provides instructions on how to add a solution to source control.</span></span>|  
|[<span data-ttu-id="225d6-112">將專案加入原始檔控制中</span><span class="sxs-lookup"><span data-stu-id="225d6-112">Add Projects to Source Control</span></span>](../../2014/database-engine/add-projects-to-source-control.md)|<span data-ttu-id="225d6-113">提供如何將專案加入方案的指示。</span><span class="sxs-lookup"><span data-stu-id="225d6-113">Provides instructions on how to add a project to a solution.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="225d6-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="225d6-114">See Also</span></span>  
 [<span data-ttu-id="225d6-115">從原始檔控制中開啟方案和專案</span><span class="sxs-lookup"><span data-stu-id="225d6-115">Open Solutions and Projects from Source Control</span></span>](../../2014/database-engine/open-solutions-and-projects-from-source-control.md)  
  
  
