---
title: 在資料流程中新增或刪除元件 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- adding components
- components [Integration Services], data flow
ms.assetid: d99124f9-0994-4f40-a48e-fdca6a4383e7
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a2f041258d2b66e7b8da540a842848ebf70f4ed5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688077"
---
# <a name="add-or-delete-a-component-in-a-data-flow"></a><span data-ttu-id="b6a16-102">在資料流程中加入或刪除元件</span><span class="sxs-lookup"><span data-stu-id="b6a16-102">Add or Delete a Component in a Data Flow</span></span>
  <span data-ttu-id="b6a16-103">資料流程元件指資料流程中的來源、目的地和轉換。</span><span class="sxs-lookup"><span data-stu-id="b6a16-103">Data flow components are sources, destinations, and transformations in a data flow.</span></span> <span data-ttu-id="b6a16-104">封裝中的控制流程必須包含「資料流程」工作，您才能將元件加入到資料流程中。</span><span class="sxs-lookup"><span data-stu-id="b6a16-104">Before you can add components to a data flow, the control flow in the package must include a Data Flow task.</span></span>  
  
 <span data-ttu-id="b6a16-105">下列程序將描述如何在封裝的資料流程中加入或刪除元件。</span><span class="sxs-lookup"><span data-stu-id="b6a16-105">The following procedures describe how to add or delete a component in the data flow of a package.</span></span>  
  
### <a name="to-add-a-component-to-a-data-flow"></a><span data-ttu-id="b6a16-106">將元件加入資料流程</span><span class="sxs-lookup"><span data-stu-id="b6a16-106">To add a component to a data flow</span></span>  
  
1.  <span data-ttu-id="b6a16-107">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，開啟包含所需封裝的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="b6a16-107">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="b6a16-108">在 [方案總管] 中，按兩下封裝將其開啟。</span><span class="sxs-lookup"><span data-stu-id="b6a16-108">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="b6a16-109">按一下 [控制流程]  索引標籤，然後按兩下包含要加入元件之資料流程的「資料流程」工作。</span><span class="sxs-lookup"><span data-stu-id="b6a16-109">Click the **Control Flow** tab, and then double-click the Data Flow task that contains the data flow to which you want to add a component.</span></span>  
  
4.  <span data-ttu-id="b6a16-110">在 [工具箱] 中，展開 [資料流程來源]  、[資料流程轉換]  或 [資料流程目的地]  ，然後將資料流程項目拖曳到 [資料流程]  索引標籤的設計介面上。</span><span class="sxs-lookup"><span data-stu-id="b6a16-110">In the Toolbox, expand **Data Flow Sources**, **Data Flow Transformations**, or **Data Flow Destinations**, and then drag a data flow item to the design surface of the **Data Flow** tab.</span></span>  
  
5.  <span data-ttu-id="b6a16-111">若要儲存已更新的封裝，請在 **[檔案]** 功能表上，按一下 **[儲存選取項目]** 。</span><span class="sxs-lookup"><span data-stu-id="b6a16-111">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
### <a name="to-delete-a-component-from-a-data-flow"></a><span data-ttu-id="b6a16-112">從資料流程中刪除元件</span><span class="sxs-lookup"><span data-stu-id="b6a16-112">To delete a component from a data flow</span></span>  
  
1.  <span data-ttu-id="b6a16-113">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，開啟包含所需封裝的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="b6a16-113">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="b6a16-114">在 [方案總管] 中，按兩下封裝將其開啟。</span><span class="sxs-lookup"><span data-stu-id="b6a16-114">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="b6a16-115">按一下 [控制流程]  索引標籤，然後按兩下包含您要刪除元件之資料流程的「資料流程」工作。</span><span class="sxs-lookup"><span data-stu-id="b6a16-115">Click the **Control Flow** tab, and then double-click the Data Flow task that contains the data flow from which you want to delete a component.</span></span>  
  
4.  <span data-ttu-id="b6a16-116">以滑鼠右鍵按一下資料流程元件，然後按一下 [刪除]  。</span><span class="sxs-lookup"><span data-stu-id="b6a16-116">Right-click the data flow component, and then click **Delete**.</span></span>  
  
5.  <span data-ttu-id="b6a16-117">確認刪除作業。</span><span class="sxs-lookup"><span data-stu-id="b6a16-117">Confirm the delete operation.</span></span>  
  
6.  <span data-ttu-id="b6a16-118">若要儲存已更新的封裝，請在 **[檔案]** 功能表上，按一下 **[儲存選取項目]** 。</span><span class="sxs-lookup"><span data-stu-id="b6a16-118">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6a16-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b6a16-119">See Also</span></span>  
 <span data-ttu-id="b6a16-120">[連接資料流程中的元件](data-flow.md) </span><span class="sxs-lookup"><span data-stu-id="b6a16-120">[Connect Components in a Data Flow](data-flow.md) </span></span>  
 <span data-ttu-id="b6a16-121">[在資料流程元件中設定錯誤輸出](../configure-an-error-output-in-a-data-flow-component.md) </span><span class="sxs-lookup"><span data-stu-id="b6a16-121">[Configure an Error Output in a Data Flow Component](../configure-an-error-output-in-a-data-flow-component.md) </span></span>  
 [<span data-ttu-id="b6a16-122">資料流程</span><span class="sxs-lookup"><span data-stu-id="b6a16-122">Data Flow</span></span>](data-flow.md)  
  
  
