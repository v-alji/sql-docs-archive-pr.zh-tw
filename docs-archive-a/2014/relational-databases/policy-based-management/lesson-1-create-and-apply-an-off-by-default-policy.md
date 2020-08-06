---
title: 第 1 課：建立和套用 Off By Default 原則 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
ms.assetid: d31367db-b7db-44c4-8df2-f1240474cf78
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 9a76df1a72b93d09c5c1c199cb0246dbb51c9cbc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591968"
---
# <a name="lesson-1-create-and-apply-an-off-by-default-policy"></a><span data-ttu-id="6fa00-102">第 1 課：建立和套用 Off By Default 原則</span><span class="sxs-lookup"><span data-stu-id="6fa00-102">Lesson 1: Create and Apply an Off By Default Policy</span></span>
  <span data-ttu-id="6fa00-103">您可以使用以原則為基礎的管理原則來管理一個或多個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體、一個或多個執行個體物件、伺服器執行個體、一個或多個資料庫或一個或多個資料庫物件。</span><span class="sxs-lookup"><span data-stu-id="6fa00-103">Using Policy-Based Management policies, you can administer one or more instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], one or more instance objects, server instances, one or more databases, or one or more database objects.</span></span> <span data-ttu-id="6fa00-104">身為資料庫管理員，您想要確保特定伺服器沒有啟用 Database Mail。</span><span class="sxs-lookup"><span data-stu-id="6fa00-104">As the database administrator, you want to ensure that certain servers do not have Database Mail enabled.</span></span> <span data-ttu-id="6fa00-105">在這一課，您將建立一個條件，以及設定這個伺服器選項的原則。</span><span class="sxs-lookup"><span data-stu-id="6fa00-105">In this lesson, you will create a condition and a policy that sets that server option.</span></span> <span data-ttu-id="6fa00-106">您將會測試伺服器，以便查看它是否符合此原則。</span><span class="sxs-lookup"><span data-stu-id="6fa00-106">You will test the server to see whether it complies with the policy.</span></span> <span data-ttu-id="6fa00-107">然後，您將會使用此原則來重新設定伺服器，以便讓伺服器符合。</span><span class="sxs-lookup"><span data-stu-id="6fa00-107">Then, you will use the policy to reconfigure the server to bring the server into compliance.</span></span>  
  
 <span data-ttu-id="6fa00-108">這個課程包含下列主題：</span><span class="sxs-lookup"><span data-stu-id="6fa00-108">This lesson contains the following topics:</span></span>  
  
-   [<span data-ttu-id="6fa00-109">建立依預設為關閉的原則</span><span class="sxs-lookup"><span data-stu-id="6fa00-109">Create the Off By Default Policy</span></span>](lesson-1-1-create-the-off-by-default-policy.md)  
  
-   [<span data-ttu-id="6fa00-110">將伺服器設定為執行 Off By Default 原則</span><span class="sxs-lookup"><span data-stu-id="6fa00-110">Configure a Server to Run the Off By Default Policy</span></span>](lesson-1-2-configure-a-server-to-run-the-off-by-default-policy.md)  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="6fa00-111">本課程的下一項工作</span><span class="sxs-lookup"><span data-stu-id="6fa00-111">Next Task in Lesson</span></span>  
 [<span data-ttu-id="6fa00-112">建立依預設為關閉的原則</span><span class="sxs-lookup"><span data-stu-id="6fa00-112">Create the Off By Default Policy</span></span>](lesson-1-1-create-the-off-by-default-policy.md)  
  
## <a name="next-lesson"></a><span data-ttu-id="6fa00-113">下一課</span><span class="sxs-lookup"><span data-stu-id="6fa00-113">Next Lesson</span></span>  
 [<span data-ttu-id="6fa00-114">第 2 課：建立和套用命名標準原則</span><span class="sxs-lookup"><span data-stu-id="6fa00-114">Lesson 2: Create and Apply a Naming Standards Policy</span></span>](lesson-2-create-and-apply-a-naming-standards-policy.md)  
  
  
