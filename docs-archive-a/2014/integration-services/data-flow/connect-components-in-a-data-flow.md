---
title: 連接資料流程中的元件 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- components [Integration Services], connections
- connections [Integration Services], data flow components
ms.assetid: 70616a58-8921-4218-85bf-f3e90c5a9dbf
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8fc4a2fa81e9b110c27ea63b16d835d069bf12cf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687093"
---
# <a name="connect-components-in-a-data-flow"></a><span data-ttu-id="1a9f9-102">連接資料流程中的元件</span><span class="sxs-lookup"><span data-stu-id="1a9f9-102">Connect Components in a Data Flow</span></span>
  <span data-ttu-id="1a9f9-103">此程序描述如何將資料流程中的元件輸出，連接到同一資料流程中的其他元件。</span><span class="sxs-lookup"><span data-stu-id="1a9f9-103">This procedure describes how to connect the output of components in a data flow to other components within the same data flow.</span></span>  
  
### <a name="to-connect-components-in-a-data-flow"></a><span data-ttu-id="1a9f9-104">連接資料流程中的元件</span><span class="sxs-lookup"><span data-stu-id="1a9f9-104">To connect components in a data flow</span></span>  
  
1.  <span data-ttu-id="1a9f9-105">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，開啟包含所需封裝的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="1a9f9-105">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="1a9f9-106">在 [方案總管] 中，按兩下封裝將其開啟。</span><span class="sxs-lookup"><span data-stu-id="1a9f9-106">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="1a9f9-107">按一下 [控制流程]  索引標籤，然後按兩下包含您要在其中連接元件之資料流程的「資料流程」工作。</span><span class="sxs-lookup"><span data-stu-id="1a9f9-107">Click the **Control Flow** tab, and then double-click the Data Flow task that contains the data flow in which you want to connect components.</span></span>  
  
4.  <span data-ttu-id="1a9f9-108">在 [資料流程]  索引標籤的設計介面上，選取您要連接的轉換或來源。</span><span class="sxs-lookup"><span data-stu-id="1a9f9-108">On the design surface of the **Data Flow** tab, select the transformation or source that you want to connect.</span></span>  
  
5.  <span data-ttu-id="1a9f9-109">將轉換或來源的綠色輸出箭頭拖曳至另一轉換或目的地。</span><span class="sxs-lookup"><span data-stu-id="1a9f9-109">Drag the green output arrow of a transformation or a source to a transformation or to a destination.</span></span> <span data-ttu-id="1a9f9-110">某些資料流程元件有錯誤輸出，您可以使用相同方式加以連接。</span><span class="sxs-lookup"><span data-stu-id="1a9f9-110">Some data flow components have error outputs that you can connect in the same way.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="1a9f9-111">某些資料流程元件具有多個輸出，您可以將每個輸出連接到另一個轉換或目的地。</span><span class="sxs-lookup"><span data-stu-id="1a9f9-111">Some data flow components can have multiple outputs and you can connect each output to a different transformation or destination.</span></span>  
  
6.  <span data-ttu-id="1a9f9-112">若要儲存已更新的封裝，請在 **[檔案]** 功能表上，按一下 **[儲存選取項目]** 。</span><span class="sxs-lookup"><span data-stu-id="1a9f9-112">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a9f9-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1a9f9-113">See Also</span></span>  
 <span data-ttu-id="1a9f9-114">[在資料流程中加入或刪除元件](data-flow.md) </span><span class="sxs-lookup"><span data-stu-id="1a9f9-114">[Add or Delete a Component in a Data Flow](data-flow.md) </span></span>  
 <span data-ttu-id="1a9f9-115">[在資料流程元件中設定錯誤輸出](../configure-an-error-output-in-a-data-flow-component.md) </span><span class="sxs-lookup"><span data-stu-id="1a9f9-115">[Configure an Error Output in a Data Flow Component](../configure-an-error-output-in-a-data-flow-component.md) </span></span>  
 [<span data-ttu-id="1a9f9-116">資料流程</span><span class="sxs-lookup"><span data-stu-id="1a9f9-116">Data Flow</span></span>](data-flow.md)  
  
  
