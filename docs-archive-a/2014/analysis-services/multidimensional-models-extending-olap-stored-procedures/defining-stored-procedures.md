---
title: 定義預存程式 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- stored procedures [Analysis Services]
- OLAP [Analysis Services], stored procedures
- external routines [Analysis Services]
- stored procedures [Analysis Services], about stored procedures
ms.assetid: f9c57d91-f60f-4f0e-8f7f-d87f4ba97b7c
author: minewiskan
ms.author: owend
ms.openlocfilehash: cc1f028f822d2289ee79702feb2494487040977c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700426"
---
# <a name="defining-stored-procedures"></a><span data-ttu-id="4d827-102">定義預存程序</span><span class="sxs-lookup"><span data-stu-id="4d827-102">Defining Stored Procedures</span></span>
  <span data-ttu-id="4d827-103">您可以使用預存程式從呼叫外部常式 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="4d827-103">You can use stored procedures to call external routines from [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="4d827-104">您可以用任何 Common Language Runtime (CLR) 語言 (比如：C、C++、C#、Visual Basic，或 Visual Basic .NET)，來撰寫預存程序所呼叫的外部常式。</span><span class="sxs-lookup"><span data-stu-id="4d827-104">You can write an external routines called by a stored procedure in any common language runtime (CLR) language, such as C, C++, C#, Visual Basic, or Visual Basic .NET.</span></span> <span data-ttu-id="4d827-105">預存程序可以只建立一次，再從許多內容中呼叫，比如：其他預存程序、導出量值，或用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="4d827-105">A stored procedure can be created once and called from many contexts, such as other stored procedures, calculated measures, or client applications.</span></span> <span data-ttu-id="4d827-106">預存程序讓通用程式碼只需要開發一次並儲存在單一位置，可簡化 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 資料庫的開發和實作。</span><span class="sxs-lookup"><span data-stu-id="4d827-106">Stored procedures simplify [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database development and implementation by allowing common code to be developed once and stored in a single location.</span></span> <span data-ttu-id="4d827-107">預存程序可用來將 MDX 的原生功能未提供的商務功能，加入您的應用程式中。</span><span class="sxs-lookup"><span data-stu-id="4d827-107">Stored procedures can be used to add business functionality to your applications that is not provided by the native functionality of MDX.</span></span>  
  
 <span data-ttu-id="4d827-108">本節提供了解、設計和實作預存程序所需的資訊。</span><span class="sxs-lookup"><span data-stu-id="4d827-108">This section provides the information necessary to understand, design, and implement stored procedures.</span></span>  
  
|<span data-ttu-id="4d827-109">主題</span><span class="sxs-lookup"><span data-stu-id="4d827-109">Topic</span></span>|<span data-ttu-id="4d827-110">描述</span><span class="sxs-lookup"><span data-stu-id="4d827-110">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="4d827-111">設計預存程序</span><span class="sxs-lookup"><span data-stu-id="4d827-111">Designing Stored Procedures</span></span>](../multidimensional-models-extending-olap-stored-procedures/designing-stored-procedures.md)|<span data-ttu-id="4d827-112">描述如何設計 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 所使用的組件。</span><span class="sxs-lookup"><span data-stu-id="4d827-112">Describes how to design assemblies for use with [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>|  
|[<span data-ttu-id="4d827-113">建立預存程序</span><span class="sxs-lookup"><span data-stu-id="4d827-113">Creating Stored Procedures</span></span>](creating-stored-procedures.md)|<span data-ttu-id="4d827-114">描述如何建立 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 的組件。</span><span class="sxs-lookup"><span data-stu-id="4d827-114">Describes how to create assemblies for [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>|  
|[<span data-ttu-id="4d827-115">呼叫預存程序</span><span class="sxs-lookup"><span data-stu-id="4d827-115">Calling Stored Procedures</span></span>](calling-stored-procedures.md)|<span data-ttu-id="4d827-116">提供有關如何在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 中使用組件的資訊。</span><span class="sxs-lookup"><span data-stu-id="4d827-116">Provides information on how to use assemblies in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>|  
|[<span data-ttu-id="4d827-117">在預存程序中存取查詢內容</span><span class="sxs-lookup"><span data-stu-id="4d827-117">Accessing Query Context in Stored Procedures</span></span>](accessing-query-context-in-stored-procedures.md)|<span data-ttu-id="4d827-118">描述如何用組件來存取範圍及內容資訊。</span><span class="sxs-lookup"><span data-stu-id="4d827-118">Describes how to access scope and context information with assemblies.</span></span>|  
|[<span data-ttu-id="4d827-119">設定預存程序的安全性</span><span class="sxs-lookup"><span data-stu-id="4d827-119">Setting Security for Stored Procedures</span></span>](setting-security-for-stored-procedures.md)|<span data-ttu-id="4d827-120">描述如何在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 中設定組件的安全性。</span><span class="sxs-lookup"><span data-stu-id="4d827-120">Describes how to configure security for assemblies in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>|  
|[<span data-ttu-id="4d827-121">除錯預存程序</span><span class="sxs-lookup"><span data-stu-id="4d827-121">Debugging Stored Procedures</span></span>](debugging-stored-procedures.md)|<span data-ttu-id="4d827-122">描述如何在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 中偵錯組件。</span><span class="sxs-lookup"><span data-stu-id="4d827-122">Describes how to debug assemblies in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4d827-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4d827-123">See Also</span></span>  
 [<span data-ttu-id="4d827-124">多維度模型組件管理</span><span class="sxs-lookup"><span data-stu-id="4d827-124">Multidimensional Model Assemblies Management</span></span>](../multidimensional-models/multidimensional-model-assemblies-management.md)  
  
  
