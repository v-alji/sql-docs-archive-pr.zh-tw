---
title: MSSQLSERVER_9532 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 9532 (Database Engine error)
ms.assetid: ab95cce8-4f97-4aea-a746-a73eea7c9aab
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c34ebc7c682d2ffe8bc0205565f5dfd44fdd5b66
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595037"
---
# <a name="mssqlserver_9532"></a><span data-ttu-id="6033c-102">MSSQLSERVER_9532</span><span class="sxs-lookup"><span data-stu-id="6033c-102">MSSQLSERVER_9532</span></span>
    
## <a name="details"></a><span data-ttu-id="6033c-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="6033c-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6033c-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="6033c-104">Product Name</span></span>|<span data-ttu-id="6033c-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="6033c-105">SQL Server</span></span>|  
|<span data-ttu-id="6033c-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="6033c-106">Event ID</span></span>|<span data-ttu-id="6033c-107">9532</span><span class="sxs-lookup"><span data-stu-id="6033c-107">9532</span></span>|  
|<span data-ttu-id="6033c-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="6033c-108">Event Source</span></span>|<span data-ttu-id="6033c-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="6033c-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="6033c-110">元件</span><span class="sxs-lookup"><span data-stu-id="6033c-110">Component</span></span>|<span data-ttu-id="6033c-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="6033c-111">SQLEngine</span></span>|  
|<span data-ttu-id="6033c-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="6033c-112">Symbolic Name</span></span>|<span data-ttu-id="6033c-113">XMLERR_COLUMNSET_CANNOT_CONVERT_FROM_TO</span><span class="sxs-lookup"><span data-stu-id="6033c-113">XMLERR_COLUMNSET_CANNOT_CONVERT_FROM_TO</span></span>|  
|<span data-ttu-id="6033c-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="6033c-114">Message Text</span></span>|<span data-ttu-id="6033c-115">在包含資料行集 '%.\*ls' 的查詢/DML 作業中，將資料行 '%.\*ls' 從資料類型 '%ls' 轉換成資料類型 '%ls' 時，轉換失敗。</span><span class="sxs-lookup"><span data-stu-id="6033c-115">In the query/DML operation involving  column set '%.\*ls', conversion failed when converting from the data type '%ls' to the data type '%ls' for the column '%.\*ls'.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="6033c-116">說明</span><span class="sxs-lookup"><span data-stu-id="6033c-116">Explanation</span></span>  
 <span data-ttu-id="6033c-117">資料行集是不具類型的 XML 表示，可將資料表的某些資料行結合到結構化輸出中。</span><span class="sxs-lookup"><span data-stu-id="6033c-117">A column set is an untyped XML representation that combines some of the columns of a table into a structured output.</span></span> <span data-ttu-id="6033c-118">當您透過 XML 資料行集來插入或更新疏鬆資料行值時，插入基礎疏鬆資料行內的值會從 `xml` 資料類型隱含地轉換。</span><span class="sxs-lookup"><span data-stu-id="6033c-118">When you are inserting or updating sparse column values through the XML column set, the values that are inserted into the underlying sparse columns are implicitly converted from the `xml` data type.</span></span> <span data-ttu-id="6033c-119">提供了無法轉換成此資料行之資料類型的值。</span><span class="sxs-lookup"><span data-stu-id="6033c-119">A value was provided that cannot be converted to the data type of the column.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="6033c-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="6033c-120">User Action</span></span>  
 <span data-ttu-id="6033c-121">由於提供的值無法隱含地轉換，所以它可能是無效的輸入。</span><span class="sxs-lookup"><span data-stu-id="6033c-121">Because the value provided could not be implicitly converted, it might be an invalid entry.</span></span> <span data-ttu-id="6033c-122">請更正錯誤後重試。</span><span class="sxs-lookup"><span data-stu-id="6033c-122">Correct the error and retry.</span></span> <span data-ttu-id="6033c-123">如果此值正確無誤，請修改陳述式來使用個別資料行，而非資料行集。</span><span class="sxs-lookup"><span data-stu-id="6033c-123">If the value is correct, modify the statement to use the individual columns instead of the column set.</span></span> <span data-ttu-id="6033c-124">如此可讓您明確地將此值轉換成正確的資料類型。</span><span class="sxs-lookup"><span data-stu-id="6033c-124">This will allow you to explicitly cast the value into the correct data type.</span></span>  
  
  
