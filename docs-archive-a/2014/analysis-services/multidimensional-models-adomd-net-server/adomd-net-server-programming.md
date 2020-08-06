---
title: ADOMD.NET 伺服器程式設計 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- programming [ADOMD.NET]
- ADOMD.NET, programming
ms.assetid: 7f7ff5be-3826-43a5-b94d-ddeec5ddb2eb
author: minewiskan
ms.author: owend
ms.openlocfilehash: 522478af0b19f1745d80f167e40345d4751136b7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686525"
---
# <a name="adomdnet-server-programming"></a><span data-ttu-id="aecda-102">ADOMD.NET 伺服器程式設計</span><span class="sxs-lookup"><span data-stu-id="aecda-102">ADOMD.NET Server Programming</span></span>
  <span data-ttu-id="aecda-103">ADOMD.NET 的 ADOMD.NET 伺服器元件是位在 `Microsoft.AnalysisServices.AdomdServer` 命名空間中 (在 msmgdsrv.dll 中)。</span><span class="sxs-lookup"><span data-stu-id="aecda-103">The ADOMD.NET server components of ADOMD.NET reside within the `Microsoft.AnalysisServices.AdomdServer` namespace (in msmgdsrv.dll).</span></span> <span data-ttu-id="aecda-104">您可以使用這些伺服器元件， (MDX) 函數和在實例上執行的預存程式，建立自訂多維度運算式 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="aecda-104">You use these server components to create custom Multidimensional Expressions (MDX) functions and stored procedures that are run on an instance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="aecda-105">伺服器物件提供查詢 Cube 與採礦模型的功能，以及在指定內容中評估運算式的功能。</span><span class="sxs-lookup"><span data-stu-id="aecda-105">The server objects provide the capabilities for querying cubes and mining models, and for evaluating expressions in a given context.</span></span> <span data-ttu-id="aecda-106">建立自訂函數與預存程序的優點包括快速的執行、集中的部署以及改善的可維護性。</span><span class="sxs-lookup"><span data-stu-id="aecda-106">The benefits for creating custom functions and stored procedures include fast execution, centralized deployment, and improved maintainability.</span></span>  
  
 <span data-ttu-id="aecda-107">下表中的主題將協助您開發 ADOMD.NET 伺服器應用程式。</span><span class="sxs-lookup"><span data-stu-id="aecda-107">The topics in the following table will help you develop ADOMD.NET server applications.</span></span>  
  
|<span data-ttu-id="aecda-108">主題</span><span class="sxs-lookup"><span data-stu-id="aecda-108">Topic</span></span>|<span data-ttu-id="aecda-109">描述</span><span class="sxs-lookup"><span data-stu-id="aecda-109">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="aecda-110">ADOMD.NET 伺服器功能</span><span class="sxs-lookup"><span data-stu-id="aecda-110">ADOMD.NET Server Functionality</span></span>](https://docs.microsoft.com/bi-reference/adomd/multidimensional-models-adomd-net-server/adomd-net-server-functionality)|<span data-ttu-id="aecda-111">描述 ADOMD.NET 伺服器物件的使用。</span><span class="sxs-lookup"><span data-stu-id="aecda-111">Describes the uses for ADOMD.NET server objects.</span></span>|  
|[<span data-ttu-id="aecda-112">ADOMD.NET 伺服器物件架構</span><span class="sxs-lookup"><span data-stu-id="aecda-112">ADOMD.NET Server Object Architecture</span></span>](https://docs.microsoft.com/bi-reference/adomd/multidimensional-models-adomd-net-server/adomd-net-server-object-architecture)|<span data-ttu-id="aecda-113">描述 ADOMD.NET 伺服器物件的物件架構。</span><span class="sxs-lookup"><span data-stu-id="aecda-113">Describes the object architecture for ADOMD.NET server objects.</span></span>|  
|[<span data-ttu-id="aecda-114">使用者定義函數和預存程序</span><span class="sxs-lookup"><span data-stu-id="aecda-114">User Defined Functions and Stored Procedures</span></span>](https://docs.microsoft.com/analysis-services/adomd/multidimensional-models-adomd-net-server/user-defined-functions-and-stored-procedures)|<span data-ttu-id="aecda-115">逐步引導您建立使用者定義函數或預存程序的程序。</span><span class="sxs-lookup"><span data-stu-id="aecda-115">Walks you through the process of creating a user defined function or stored Procedure.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="aecda-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aecda-116">See Also</span></span>  
 <span data-ttu-id="aecda-117">[ADOMD.NET 用戶端程式設計](https://docs.microsoft.com/analysis-services/adomd/multidimensional-models-adomd-net-client/adomd-net-client-programming) </span><span class="sxs-lookup"><span data-stu-id="aecda-117">[ADOMD.NET Client Programming](https://docs.microsoft.com/analysis-services/adomd/multidimensional-models-adomd-net-client/adomd-net-client-programming) </span></span>  
 [<span data-ttu-id="aecda-118">使用 ADOMD.NET 來開發</span><span class="sxs-lookup"><span data-stu-id="aecda-118">Developing with ADOMD.NET</span></span>](https://docs.microsoft.com/bi-reference/adomd/developing-with-adomd-net)  
  
  
