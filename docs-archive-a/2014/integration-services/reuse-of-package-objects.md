---
title: 重複使用套件物件 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- GUID regenerating [Integration Services]
- reusing packages
- templates [Integration Services]
- copying packages
- regenerating package GUID
ms.assetid: 08f723bf-15b5-44bd-9a46-04e8781bfbfb
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b7612cb2684bb842108068b062e54fbe9dee4327
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687989"
---
# <a name="reuse-of-package-objects"></a><span data-ttu-id="b795f-102">重複使用封裝物件</span><span class="sxs-lookup"><span data-stu-id="b795f-102">Reuse of Package Objects</span></span>
  <span data-ttu-id="b795f-103">您要重複使用的常用封裝功能。</span><span class="sxs-lookup"><span data-stu-id="b795f-103">Frequently packages functionality that you want to reuse.</span></span> <span data-ttu-id="b795f-104">例如，如果建立了一組工作，您可能想要以群組方式重複使用這些項目，您也可能想重複使用單一項目，例如您在不同的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案中建立的連接管理員。</span><span class="sxs-lookup"><span data-stu-id="b795f-104">For example, if you created a set of tasks, you might want to reuse the items together as a group, or you might want to reuse a single item such as a connection manager that you created in a different [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project.</span></span>  
  
## <a name="copy-and-paste"></a><span data-ttu-id="b795f-105">複製與貼上</span><span class="sxs-lookup"><span data-stu-id="b795f-105">Copy and Paste</span></span>  
 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] <span data-ttu-id="b795f-106">和「 [!INCLUDE[ssIS](../includes/ssis-md.md)] 設計師」支援複製及貼上封裝物件的功能，這些物件可以包括控制流程項目、資料流程項目和連接管理員。</span><span class="sxs-lookup"><span data-stu-id="b795f-106">and [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer support copying and pasting package objects, which can include control flow items, data flow items, and connection managers.</span></span> <span data-ttu-id="b795f-107">您可以在專案之間和封裝之間執行複製和貼上功能。</span><span class="sxs-lookup"><span data-stu-id="b795f-107">You can copy and paste between projects and between packages.</span></span> <span data-ttu-id="b795f-108">如果方案包含多個專案，您可以在專案之間進行複製，而且專案可以屬於不同類型。</span><span class="sxs-lookup"><span data-stu-id="b795f-108">If the solution contains multiple projects you can copy between projects, and the projects can be of different types.</span></span>  
  
 <span data-ttu-id="b795f-109">如果方案包含多個封裝，您可以在這些封裝之間進行複製和貼上。</span><span class="sxs-lookup"><span data-stu-id="b795f-109">If a solution contains multiple packages, you can copy and paste between them.</span></span> <span data-ttu-id="b795f-110">這些封裝可以位於相同或不同的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案中。</span><span class="sxs-lookup"><span data-stu-id="b795f-110">The packages can be in the same or different [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] projects.</span></span> <span data-ttu-id="b795f-111">不過，封裝物件可能具有其他物件的相依性，如果缺少這些相依性，物件便無效。</span><span class="sxs-lookup"><span data-stu-id="b795f-111">However, package objects may have dependencies on other objects, without which they are not valid.</span></span> <span data-ttu-id="b795f-112">例如，您必須複製「執行 SQL」工作所使用的連接管理員，才能讓工作發揮作用。</span><span class="sxs-lookup"><span data-stu-id="b795f-112">For example, an Execute SQL task uses a connection manager, which you must copy as well to make the task work.</span></span> <span data-ttu-id="b795f-113">此外，某些封裝物件要求封裝必須已經包含某一特定物件，如果沒有這個物件，您就不能成功地將複製的物件貼到封裝中。</span><span class="sxs-lookup"><span data-stu-id="b795f-113">Also, some package objects require that the package already contain a certain object, and without this object you cannot successfully paste the copied objects into a package.</span></span> <span data-ttu-id="b795f-114">例如，您不能將資料流程貼到沒有任何「資料流程」工作的封裝中。</span><span class="sxs-lookup"><span data-stu-id="b795f-114">For example, you cannot paste a data flow into a package that does not have at least one Data Flow task.</span></span>  
  
 <span data-ttu-id="b795f-115">您可能會發現自己重複複製了相同的封裝。</span><span class="sxs-lookup"><span data-stu-id="b795f-115">You may find that you copy the same packages repeatedly.</span></span> <span data-ttu-id="b795f-116">若要避免複製處理，您可以將這些封裝指定成範本，並在建立新封裝時使用這些範本。</span><span class="sxs-lookup"><span data-stu-id="b795f-116">To avoid the copy process, you can designate these packages as templates and use them when you create new packages.</span></span>  
  
 <span data-ttu-id="b795f-117">複製封裝物件時，[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 會自動指定新的 GUID 給新物件的 `ID` 屬性，並更新 `Name` 屬性。</span><span class="sxs-lookup"><span data-stu-id="b795f-117">When you copy a package object, [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] automatically assigns a new GUID to the `ID` property of the new object and updates the `Name` property.</span></span>  
  
 <span data-ttu-id="b795f-118">您無法複製變數。</span><span class="sxs-lookup"><span data-stu-id="b795f-118">You cannot copy variables.</span></span> <span data-ttu-id="b795f-119">如果工作之類的物件使用了變數，則您必須在目的地封裝中重新建立變數。</span><span class="sxs-lookup"><span data-stu-id="b795f-119">If an object such as a task uses variables, then you must re-create the variables in the destination package.</span></span> <span data-ttu-id="b795f-120">相反地，如果您複製整個封裝，也會一併複製封裝中的變數。</span><span class="sxs-lookup"><span data-stu-id="b795f-120">In contrast, if you copy the entire package, then the variables in the package are also copied.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="b795f-121">相關工作</span><span class="sxs-lookup"><span data-stu-id="b795f-121">Related Tasks</span></span>  
  
-   [<span data-ttu-id="b795f-122">複製套件物件</span><span class="sxs-lookup"><span data-stu-id="b795f-122">Copy Package Objects</span></span>](../../2014/integration-services/copy-package-objects.md)  
  
-   [<span data-ttu-id="b795f-123">複製專案項目</span><span class="sxs-lookup"><span data-stu-id="b795f-123">Copy Project Items</span></span>](../../2014/integration-services/copy-project-items.md)  
  
-   [<span data-ttu-id="b795f-124">將套件儲存為套件範本</span><span class="sxs-lookup"><span data-stu-id="b795f-124">Save a Package as a Package Template</span></span>](../../2014/integration-services/save-a-package-as-a-package-template.md)  
  
  
