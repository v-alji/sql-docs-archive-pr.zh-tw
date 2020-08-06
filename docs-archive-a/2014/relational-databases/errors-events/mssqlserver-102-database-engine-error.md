---
title: MSSQLSERVER_102 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 102 (Database Engine error)
ms.assetid: 264dc1a2-c8a0-4c89-b5f6-951baf950299
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 18c330b8d6a534ca11e2ad2c03f89793f8c832e1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585489"
---
# <a name="mssqlserver_102"></a><span data-ttu-id="45b8a-102">MSSQLSERVER_102</span><span class="sxs-lookup"><span data-stu-id="45b8a-102">MSSQLSERVER_102</span></span>
    
## <a name="details"></a><span data-ttu-id="45b8a-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="45b8a-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="45b8a-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="45b8a-104">Product Name</span></span>|<span data-ttu-id="45b8a-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="45b8a-105">SQL Server</span></span>|  
|<span data-ttu-id="45b8a-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="45b8a-106">Event ID</span></span>|<span data-ttu-id="45b8a-107">102</span><span class="sxs-lookup"><span data-stu-id="45b8a-107">102</span></span>|  
|<span data-ttu-id="45b8a-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="45b8a-108">Event Source</span></span>|<span data-ttu-id="45b8a-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="45b8a-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="45b8a-110">元件</span><span class="sxs-lookup"><span data-stu-id="45b8a-110">Component</span></span>|<span data-ttu-id="45b8a-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="45b8a-111">SQLEngine</span></span>|  
|<span data-ttu-id="45b8a-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="45b8a-112">Symbolic Name</span></span>|<span data-ttu-id="45b8a-113">P_SYNTAXERR2</span><span class="sxs-lookup"><span data-stu-id="45b8a-113">P_SYNTAXERR2</span></span>|  
|<span data-ttu-id="45b8a-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="45b8a-114">Message Text</span></span>|<span data-ttu-id="45b8a-115">接近 '%.\*ls' 的語法不正確。</span><span class="sxs-lookup"><span data-stu-id="45b8a-115">Incorrect syntax near '%.\*ls'.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="45b8a-116">說明</span><span class="sxs-lookup"><span data-stu-id="45b8a-116">Explanation</span></span>  
 <span data-ttu-id="45b8a-117">表示語法錯誤。</span><span class="sxs-lookup"><span data-stu-id="45b8a-117">Indicates a syntax error.</span></span> <span data-ttu-id="45b8a-118">因為錯誤讓 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 無法處理陳述式，所以無法取得其他資訊。</span><span class="sxs-lookup"><span data-stu-id="45b8a-118">Additional information is not available because the error prevents the [!INCLUDE[ssDE](../../includes/ssde-md.md)] from processing the statement.</span></span>  
  
 <span data-ttu-id="45b8a-119">可能導因於嘗試使用已被取代的 RC4 或 RC4_128 加密建立一組對稱金鑰，但不是在相容性模式 90 或 100 之中。</span><span class="sxs-lookup"><span data-stu-id="45b8a-119">Can be caused by attempting to create a symmetric key using the deprecated RC4 or RC4_128 encryption, when not in 90 or 100 compatibility mode.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="45b8a-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="45b8a-120">User Action</span></span>  
 <span data-ttu-id="45b8a-121">在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式中搜尋語法錯誤。</span><span class="sxs-lookup"><span data-stu-id="45b8a-121">Search the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement for syntax errors.</span></span>  
  
 <span data-ttu-id="45b8a-122">若使用 RC4 或 RC4_128 建立對稱金鑰，請選取較新的加密方式，例如其中一種 AES 演算法</span><span class="sxs-lookup"><span data-stu-id="45b8a-122">If creating a symmetric key using the RC4 or RC4_128, select a newer encryption such as one of the AES algorithms.</span></span> <span data-ttu-id="45b8a-123">(建議使用)。若必須使用 RC4，請使用 ALTER DATABASE SET COMPATIBILITY_LEVEL 將資料庫相容性層級設為 90 或 100</span><span class="sxs-lookup"><span data-stu-id="45b8a-123">(Recommended.) If you must use RC4, use ALTER DATABASE SET COMPATIBILITY_LEVEL to set the database to compatibility level 90 or 100.</span></span> <span data-ttu-id="45b8a-124">(不建議使用)。</span><span class="sxs-lookup"><span data-stu-id="45b8a-124">(Not recommended.)</span></span>  
  
  
