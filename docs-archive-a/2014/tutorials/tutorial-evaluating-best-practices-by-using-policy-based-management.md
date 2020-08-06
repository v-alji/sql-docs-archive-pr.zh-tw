---
title: 教學課程：使用以原則為基礎的管理來評估最佳作法 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- best practices analyzer
- Policy-Based Management, best practices policies
- Best Practices [Database Engine]
- Policy-Based Management, evaluating policies
- BPA
- tutorials [Policy-Based Management]
- Policy-Based Management, tutorials
ms.assetid: c7867f9b-7acc-4fae-bde1-63808c403ebc
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 42e6b505c71abecce7b56b5cb2544b4e9f4e8f71
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702170"
---
# <a name="tutorial-evaluating-best-practices-by-using-policy-based-management"></a><span data-ttu-id="feb1c-102">教學課程：使用原則式管理來評估最佳做法</span><span class="sxs-lookup"><span data-stu-id="feb1c-102">Tutorial: Evaluating Best Practices by Using Policy-Based Management</span></span>
  <span data-ttu-id="feb1c-103">歡迎使用「使用以原則為基礎的管理來評估最佳作法」教學課程。</span><span class="sxs-lookup"><span data-stu-id="feb1c-103">Welcome to the Evaluating Best Practices by Using Policy-Based Management tutorial.</span></span> <span data-ttu-id="feb1c-104">本教學課程的主要對象是熟悉 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 但剛接觸以原則為基礎之管理的使用者。</span><span class="sxs-lookup"><span data-stu-id="feb1c-104">This tutorial is intended for users who are familiar with [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], but new to Policy-Based Management.</span></span> <span data-ttu-id="feb1c-105">原則式管理，這個系統定義可用來強制執行網站管理標準的原則。</span><span class="sxs-lookup"><span data-stu-id="feb1c-105">Policy-Based Management is a system for defining policies that can be used enforce site administration standards.</span></span> <span data-ttu-id="feb1c-106">原則式管理所包含的一組最佳作法原則可用來分析 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的執行個體，以判斷該執行個體是否符合最佳作法指導方針與建議。</span><span class="sxs-lookup"><span data-stu-id="feb1c-106">Policy-Based Management includes a set of best practices policies that you can use to analyze an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] to determine whether the instance meets best practices guidelines and recommendations.</span></span>  
  
## <a name="what-you-will-learn"></a><span data-ttu-id="feb1c-107">學習內容</span><span class="sxs-lookup"><span data-stu-id="feb1c-107">What You Will Learn</span></span>  
 <span data-ttu-id="feb1c-108">在本教學課程中，您將學習如何視需要 (或「特定」) 或根據排程來評估 [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] 的最佳做法原則。</span><span class="sxs-lookup"><span data-stu-id="feb1c-108">In this tutorial, you will learn how to evaluate best practices policies for the [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] on an on-demand (or "ad hoc") basis, or on a scheduled basis.</span></span>  
  
 <span data-ttu-id="feb1c-109">這個教學課程分成兩個課程：</span><span class="sxs-lookup"><span data-stu-id="feb1c-109">This tutorial is divided into two lessons:</span></span>  
  
 [<span data-ttu-id="feb1c-110">第 1 課：視需要評估最佳做法</span><span class="sxs-lookup"><span data-stu-id="feb1c-110">Lesson 1: Evaluate Best Practices on an On-Demand Basis</span></span>](../../2014/tutorials/lesson-1-evaluate-best-practices-on-an-on-demand-basis.md)  
 <span data-ttu-id="feb1c-111">在這一課，您將針對 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的一個或多個執行個體，執行原則的視需要評估。</span><span class="sxs-lookup"><span data-stu-id="feb1c-111">In this lesson, you perform an on-demand evaluation of the policies against one or more instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="feb1c-112">第 2 課：根據排程評估最佳做法原則</span><span class="sxs-lookup"><span data-stu-id="feb1c-112">Lesson 2: Evaluate Best Practices Policies on a Scheduled Basis</span></span>](../../2014/tutorials/lesson-2-evaluate-best-practices-policies-on-a-scheduled-basis.md)  
 <span data-ttu-id="feb1c-113">在這一課，您會設定最佳做法原則根據排程執行。</span><span class="sxs-lookup"><span data-stu-id="feb1c-113">In this lesson, you configure best practices policies to run on a scheduled basis.</span></span> <span data-ttu-id="feb1c-114">此課程會顯示如何針對單一執行個體設定排程的原則，以及如何將排程的原則從中央位置部署至 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的多個執行個體。</span><span class="sxs-lookup"><span data-stu-id="feb1c-114">The lesson shows how to configure scheduled policies on a single instance, and how to deploy scheduled policies from a central location to multiple instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="feb1c-115">需求</span><span class="sxs-lookup"><span data-stu-id="feb1c-115">Requirements</span></span>  
 <span data-ttu-id="feb1c-116">這個課程需要基本資料庫知識以及 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]的基本了解。</span><span class="sxs-lookup"><span data-stu-id="feb1c-116">This lesson requires basic database knowledge and a basic understanding of [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="feb1c-117">若要使用這個教學課程，伺服器上必須已安裝 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="feb1c-117">To use this tutorial, the server must have [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] installed.</span></span>  
  
## <a name="start-the-tutorial"></a><span data-ttu-id="feb1c-118">開始教學課程</span><span class="sxs-lookup"><span data-stu-id="feb1c-118">Start the Tutorial</span></span>  
 [<span data-ttu-id="feb1c-119">第 1 課：視需要評估最佳做法</span><span class="sxs-lookup"><span data-stu-id="feb1c-119">Lesson 1: Evaluate Best Practices on an On-Demand Basis</span></span>](../../2014/tutorials/lesson-1-evaluate-best-practices-on-an-on-demand-basis.md)  
  
## <a name="see-also"></a><span data-ttu-id="feb1c-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="feb1c-120">See Also</span></span>  
 [<span data-ttu-id="feb1c-121">使用原則式管理來管理伺服器</span><span class="sxs-lookup"><span data-stu-id="feb1c-121">Administer Servers by Using Policy-Based Management</span></span>](../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)  
  
  
