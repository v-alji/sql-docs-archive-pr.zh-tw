---
title: 設計預存程式 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- stored procedures [Analysis Services], designing
- dependent assemblies [Analysis Services]
- assemblies [Analysis Services]
ms.assetid: af4e7bd5-041b-4a40-9942-0ef6a3af46c6
author: minewiskan
ms.author: owend
ms.openlocfilehash: 42b33873d6bdf28f7f702bcf186d681f57d6024d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700429"
---
# <a name="designing-stored-procedures"></a><span data-ttu-id="63e7d-102">設計預存程序</span><span class="sxs-lookup"><span data-stu-id="63e7d-102">Designing Stored Procedures</span></span>
  <span data-ttu-id="63e7d-103">管理的物件模型分析管理物件 (AMO) 和用戶端導向的物件模型 [!INCLUDE[msCoName](../../includes/msconame-md.md)] ActiveX® Data Objects (多維度) (ADO MD)，二者都可在預存程序中使用。</span><span class="sxs-lookup"><span data-stu-id="63e7d-103">Both the administrative object model Analysis Management Objects (AMO) and the client oriented object model [!INCLUDE[msCoName](../../includes/msconame-md.md)] ActiveX® Data Objects (Multidimensional) (ADO MD) are available in stored procedures.</span></span>  
  
 <span data-ttu-id="63e7d-104">預存程序必須在被呼叫的多維度運算式 (MDX) 層級可以看見的範圍內 (伺服器或資料庫)。</span><span class="sxs-lookup"><span data-stu-id="63e7d-104">Stored procedures must be in scope (either the server or the database) to be visible at the Multidimensional Expressions (MDX) level to be called.</span></span> <span data-ttu-id="63e7d-105">不過，一旦叫用預存程序後，其範圍就不限於其父系下的動作。</span><span class="sxs-lookup"><span data-stu-id="63e7d-105">However, once a stored procedure is invoked, its scope is not limited to actions under its parent.</span></span> <span data-ttu-id="63e7d-106">預存程序可以在伺服器上的任何位置進行變更或修改，只受限於叫用它之使用者處理序的安全性限制，或是它正在執行之交易的限制。</span><span class="sxs-lookup"><span data-stu-id="63e7d-106">A stored procedure may make changes or modifications anywhere on the server, subject only to the security limitations of the user process that invokes it or to the limitations of the transaction in which it is operating.</span></span>  
  
 <span data-ttu-id="63e7d-107">伺服器範圍的程序可以在伺服器的所有內容中使用。</span><span class="sxs-lookup"><span data-stu-id="63e7d-107">Server scope procedures are available in all contexts on the server.</span></span> <span data-ttu-id="63e7d-108">資料庫範圍的預存程序，只有在定義它們之資料庫的資料庫內容中才看得見。</span><span class="sxs-lookup"><span data-stu-id="63e7d-108">Database scope stored procedures are visible only in the database context of the database in which they are defined.</span></span>  
  
 <span data-ttu-id="63e7d-109">如同所有的 MDX 函數，必須先解析預存程序才能繼續 MDX 工作階段；在執行時，預存程序會鎖定 MDX 工作階段。</span><span class="sxs-lookup"><span data-stu-id="63e7d-109">As with any MDX function, stored procedure must be resolved before an MDX session can continue; stored procedures lock MDX sessions while executing.</span></span> <span data-ttu-id="63e7d-110">除非有特定原因需暫止 MDX 工作階段，等候使用者互動，否則不建議使用者互動 (例如對話方塊)。</span><span class="sxs-lookup"><span data-stu-id="63e7d-110">Unless a specific reason exists to halt an MDX session pending user interaction, then user interactions (such as dialog boxes) are discouraged.</span></span>  
  
## <a name="dependent-assemblies"></a><span data-ttu-id="63e7d-111">相依組件</span><span class="sxs-lookup"><span data-stu-id="63e7d-111">Dependent Assemblies</span></span>  
 <span data-ttu-id="63e7d-112">所有相依組件都必須載入 Common Language Runtime (CLR) 所要尋找的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體中。</span><span class="sxs-lookup"><span data-stu-id="63e7d-112">All dependent assemblies must be loaded into an instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] to be found by the common language runtime (CLR).</span></span> [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="63e7d-113">會將相依組件儲存在與主組件相同的資料夾中，所以 CLR 會自動解析組件中函數的所有函數參考。</span><span class="sxs-lookup"><span data-stu-id="63e7d-113">stores the dependent assemblies in the same folder as the main assembly, so the CLR automatically resolves all function references to functions in those assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63e7d-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="63e7d-114">See Also</span></span>  
 <span data-ttu-id="63e7d-115">[多維度模型元件管理](../multidimensional-models/multidimensional-model-assemblies-management.md) </span><span class="sxs-lookup"><span data-stu-id="63e7d-115">[Multidimensional Model Assemblies Management](../multidimensional-models/multidimensional-model-assemblies-management.md) </span></span>  
 [<span data-ttu-id="63e7d-116">定義預存程式</span><span class="sxs-lookup"><span data-stu-id="63e7d-116">Defining Stored Procedures</span></span>](../multidimensional-models-extending-olap-stored-procedures/defining-stored-procedures.md)  
  
  
