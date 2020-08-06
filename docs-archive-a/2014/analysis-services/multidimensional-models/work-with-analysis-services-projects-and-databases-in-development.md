---
title: 在開發階段使用 Analysis Services 專案和資料庫 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Analysis Services, projects
ms.assetid: 39cf9166-fa92-40fe-9962-210a52461257
author: minewiskan
ms.author: owend
ms.openlocfilehash: 762ea6f33a94f65e7dd6895cd038d4a52d40d43e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596351"
---
# <a name="working-with-analysis-services-projects-and-databases-during-the-development-phase"></a><span data-ttu-id="a3bc3-102">在開發階段使用 Analysis Services 專案和資料庫</span><span class="sxs-lookup"><span data-stu-id="a3bc3-102">Working with Analysis Services Projects and Databases During the Development Phase</span></span>
  <span data-ttu-id="a3bc3-103">您可以在專案模式或線上模式中使用 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 來開發 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 資料庫。</span><span class="sxs-lookup"><span data-stu-id="a3bc3-103">You can develop an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database by using [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] in either project mode or online mode.</span></span>  
  
## <a name="single-developer"></a><span data-ttu-id="a3bc3-104">單一開發人員</span><span class="sxs-lookup"><span data-stu-id="a3bc3-104">Single Developer</span></span>  
 <span data-ttu-id="a3bc3-105">只有一位開發人員獨自開發整個 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 資料庫及其所有構成物件時，此開發人員在商業智慧方案生命週期期間，隨時都可以在專案模式或線上模式中使用 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="a3bc3-105">When only a single developer is developing the entire [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database and all of its constituent objects, the developer can use [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] in either project mode or online mode at any time during the lifecycle of the business intelligence solution.</span></span> <span data-ttu-id="a3bc3-106">在單一開發人員的情況下，選擇模式並不是特別重要。</span><span class="sxs-lookup"><span data-stu-id="a3bc3-106">In the case of a single developer, the choice of modes is not particularly critical.</span></span> <span data-ttu-id="a3bc3-107">將離線專案檔案的維護整合到原始檔控制系統會有許多好處，例如封存和回復；</span><span class="sxs-lookup"><span data-stu-id="a3bc3-107">The maintenance of an offline project file integrated with a source control system has many benefits, such as archiving and rollback.</span></span> <span data-ttu-id="a3bc3-108">但是，在單一開發人員的作業模式下，將不會與其他開發人員之間有程式碼變更的溝通問題。</span><span class="sxs-lookup"><span data-stu-id="a3bc3-108">However, with a single developer you will not have the problem of communicating changes with another developer.</span></span>  
  
## <a name="multiple-developers"></a><span data-ttu-id="a3bc3-109">多位開發人員</span><span class="sxs-lookup"><span data-stu-id="a3bc3-109">Multiple Developers</span></span>  
 <span data-ttu-id="a3bc3-110">當有多位開發人員同時處理某個商業智慧方案時，如果開發人員不是在具有原始檔控制的專案模式下工作 (如果不是所有情況下，則為大多數情況下)，會發生問題；</span><span class="sxs-lookup"><span data-stu-id="a3bc3-110">When multiple developers are working on a business intelligence solution, problems will arise if the developers do not work in project mode with source control under most, if not all circumstances.</span></span> <span data-ttu-id="a3bc3-111">原始檔控制可確保兩位開發人員不會同時對相同的物件進行變更。</span><span class="sxs-lookup"><span data-stu-id="a3bc3-111">Source control ensures that two developers are not making changes to the same object at the same time.</span></span>  
  
 <span data-ttu-id="a3bc3-112">例如，假設有一位開發人員正在專案模式下工作，並對選定物件進行變更；</span><span class="sxs-lookup"><span data-stu-id="a3bc3-112">For example, suppose a developer is working in project mode and making changes to selected objects.</span></span> <span data-ttu-id="a3bc3-113">當這位開發人員正在進行這些變更時，假設有另一位開發人員要在線上模式中對已部署的資料庫進行變更，</span><span class="sxs-lookup"><span data-stu-id="a3bc3-113">While the developer is making these changes, suppose that another developer makes a change to the deployed database in online mode.</span></span> <span data-ttu-id="a3bc3-114">則當第一位開發人員嘗試部署已經過他修改的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 專案時，將會發生問題；</span><span class="sxs-lookup"><span data-stu-id="a3bc3-114">A problem will arise when the first developer attempts to deploy his or her modified [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project.</span></span> <span data-ttu-id="a3bc3-115">也就是說， [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 將會偵測到部署之資料庫內已經有變更的物件，並提示第一位開發人員覆寫整個資料庫，如此會覆寫第二位開發人員所做的變更。</span><span class="sxs-lookup"><span data-stu-id="a3bc3-115">Namely, [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] will detect that objects have changed within the deployed database and prompt the developer to overwrite the entire database, overwriting the changes of the second developer.</span></span> <span data-ttu-id="a3bc3-116">由於 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 沒有方法可以解決 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 資料庫執行個體以及即將要被覆寫之專案物件之間的變更問題，所以第一位開發人員所擁有的唯一實際選擇就是捨棄他所做的所有變更，並根據目前的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 資料庫版本從新的專案重新開始。</span><span class="sxs-lookup"><span data-stu-id="a3bc3-116">Since [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] has no means of resolving the changes between the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database instance and the objects in the project about to be overwritten, the only real choice the first developer has is to discard all of his or her changes and starting anew from a new project based on the current version of the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database.</span></span>  
  
  
