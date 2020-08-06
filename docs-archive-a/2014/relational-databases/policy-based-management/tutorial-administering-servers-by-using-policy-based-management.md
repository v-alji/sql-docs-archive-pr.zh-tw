---
title: 教學課程：使用以原則為基礎的管理來管理伺服器 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- tutorials [Policy-Based Management]
- Policy-Based Management, tutorials
ms.assetid: 7de96e7b-9fb8-4cc8-8d85-61345d68a1e8
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 9b707a5ecd362c6b3b54e853f89d79e25a9e1428
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593996"
---
# <a name="tutorial-administering-servers-by-using-policy-based-management"></a><span data-ttu-id="66d7f-102">教學課程：使用原則式管理來管理伺服器</span><span class="sxs-lookup"><span data-stu-id="66d7f-102">Tutorial: Administering Servers by Using Policy-Based Management</span></span>
  <span data-ttu-id="66d7f-103">歡迎使用「使用以原則為基礎的管理原則來管理伺服器」教學課程。</span><span class="sxs-lookup"><span data-stu-id="66d7f-103">Welcome to the Administering Servers by Using Policy-Based Management Policies tutorial.</span></span> <span data-ttu-id="66d7f-104">本教學課程的主要對象是熟悉 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 但剛接觸以原則為基礎之管理的使用者。</span><span class="sxs-lookup"><span data-stu-id="66d7f-104">This tutorial is intended for users who are familiar with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] but new to the Policy-Based Management.</span></span>  
  
## <a name="what-you-will-learn"></a><span data-ttu-id="66d7f-105">學習內容</span><span class="sxs-lookup"><span data-stu-id="66d7f-105">What You Will Learn</span></span>  
 <span data-ttu-id="66d7f-106">這個教學課程會建立管理伺服器的原則以及套用至單一資料庫的原則。</span><span class="sxs-lookup"><span data-stu-id="66d7f-106">This tutorial creates a policy to administer your server and a policy that applies to a single database.</span></span> <span data-ttu-id="66d7f-107">其中一項原則會視需要執行，以便測試是否符合。</span><span class="sxs-lookup"><span data-stu-id="66d7f-107">One policy is run on demand to test for compliance.</span></span> <span data-ttu-id="66d7f-108">另一項原則會強制執行未來的符合。</span><span class="sxs-lookup"><span data-stu-id="66d7f-108">The other policy enforces future compliance.</span></span>  
  
 <span data-ttu-id="66d7f-109">這個教學課程分成兩個課程：</span><span class="sxs-lookup"><span data-stu-id="66d7f-109">This tutorial is divided into two lessons:</span></span>  
  
 [<span data-ttu-id="66d7f-110">第 1 課：建立和套用 Off By Default 原則</span><span class="sxs-lookup"><span data-stu-id="66d7f-110">Lesson 1: Create and Apply an Off By Default Policy</span></span>](lesson-1-create-and-apply-an-off-by-default-policy.md)  
 <span data-ttu-id="66d7f-111">這個課程會建立指定不要在伺服器上啟用 Database Mail 的原則。</span><span class="sxs-lookup"><span data-stu-id="66d7f-111">This lesson creates a policy that specifies that Database Mail is not enabled on the server.</span></span> <span data-ttu-id="66d7f-112">然後，它會檢查伺服器是否符合此原則，並且透過停用 Database Mail，設定伺服器。</span><span class="sxs-lookup"><span data-stu-id="66d7f-112">Then, it checks to see whether your server complies with the policy, and configures the server by disabling Database Mail.</span></span>  
  
 [<span data-ttu-id="66d7f-113">第 2 課：建立和套用命名標準原則</span><span class="sxs-lookup"><span data-stu-id="66d7f-113">Lesson 2: Create and Apply a Naming Standards Policy</span></span>](lesson-2-create-and-apply-a-naming-standards-policy.md)  
 <span data-ttu-id="66d7f-114">這個課程會建立針對資料表定義並強制執行命名標準的原則。</span><span class="sxs-lookup"><span data-stu-id="66d7f-114">This lesson creates a policy that defines and enforces a naming standard for tables.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="66d7f-115">需求</span><span class="sxs-lookup"><span data-stu-id="66d7f-115">Requirements</span></span>  
 <span data-ttu-id="66d7f-116">這個課程需要基本資料庫知識以及 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]的基本了解。</span><span class="sxs-lookup"><span data-stu-id="66d7f-116">This lesson requires basic database knowledge and a basic understanding of [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="66d7f-117">若要使用這個教學課程，您的系統必須已安裝 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="66d7f-117">To use this tutorial, your system must have [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] installed.</span></span>  
  
## <a name="start-the-tutorial"></a><span data-ttu-id="66d7f-118">開始教學課程</span><span class="sxs-lookup"><span data-stu-id="66d7f-118">Start the Tutorial</span></span>  
 [<span data-ttu-id="66d7f-119">第 1 課：建立和套用 Off By Default 原則</span><span class="sxs-lookup"><span data-stu-id="66d7f-119">Lesson 1: Create and Apply an Off By Default Policy</span></span>](lesson-1-create-and-apply-an-off-by-default-policy.md)  
  
## <a name="see-also"></a><span data-ttu-id="66d7f-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="66d7f-120">See Also</span></span>  
 [<span data-ttu-id="66d7f-121">使用原則式管理來管理伺服器</span><span class="sxs-lookup"><span data-stu-id="66d7f-121">Administer Servers by Using Policy-Based Management</span></span>](administer-servers-by-using-policy-based-management.md)  
  
  
