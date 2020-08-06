---
title: MSSQLSERVER_2570 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2570 (Database Engine error)
ms.assetid: 29800aa9-81aa-4371-992c-487dbb617f46
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 79137d0f70c05c6aa7b758f7e073d152681a14b4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687910"
---
# <a name="mssqlserver_2570"></a><span data-ttu-id="27ff5-102">MSSQLSERVER_2570</span><span class="sxs-lookup"><span data-stu-id="27ff5-102">MSSQLSERVER_2570</span></span>
    
## <a name="details"></a><span data-ttu-id="27ff5-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="27ff5-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="27ff5-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="27ff5-104">Product Name</span></span>|<span data-ttu-id="27ff5-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="27ff5-105">SQL Server</span></span>|  
|<span data-ttu-id="27ff5-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="27ff5-106">Event ID</span></span>|<span data-ttu-id="27ff5-107">2570</span><span class="sxs-lookup"><span data-stu-id="27ff5-107">2570</span></span>|  
|<span data-ttu-id="27ff5-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="27ff5-108">Event Source</span></span>|<span data-ttu-id="27ff5-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="27ff5-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="27ff5-110">元件</span><span class="sxs-lookup"><span data-stu-id="27ff5-110">Component</span></span>|<span data-ttu-id="27ff5-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="27ff5-111">SQLEngine</span></span>|  
|<span data-ttu-id="27ff5-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="27ff5-112">Symbolic Name</span></span>|<span data-ttu-id="27ff5-113">DBCC_COLUMN_VALUE_OUT_OF_RANGE</span><span class="sxs-lookup"><span data-stu-id="27ff5-113">DBCC_COLUMN_VALUE_OUT_OF_RANGE</span></span>|  
|<span data-ttu-id="27ff5-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="27ff5-114">Message Text</span></span>|<span data-ttu-id="27ff5-115">頁面 P_ID，物件識別碼 O_ID 中的位置 S_ID，索引識別碼 I_ID，分割區識別碼 PN_ID，配置單位識別碼 A_ID (類型 TYPE)。</span><span class="sxs-lookup"><span data-stu-id="27ff5-115">Page P_ID, slot S_ID in object ID O_ID, index ID I_ID, partition ID PN_ID, alloc unit ID A_ID (type TYPE).</span></span> <span data-ttu-id="27ff5-116">資料行 COLUMN_NAME 值超出資料類型 "DATATYPE" 的範圍。</span><span class="sxs-lookup"><span data-stu-id="27ff5-116">Column COLUMN_NAME value is out of range for data type "DATATYPE".</span></span> <span data-ttu-id="27ff5-117">請將資料行更新為合法的值。</span><span class="sxs-lookup"><span data-stu-id="27ff5-117">Update column to a legal value.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="27ff5-118">說明</span><span class="sxs-lookup"><span data-stu-id="27ff5-118">Explanation</span></span>  
 <span data-ttu-id="27ff5-119">包含在指定之資料行中的資料行值超出資料行資料類型可能值的範圍。</span><span class="sxs-lookup"><span data-stu-id="27ff5-119">The column value that is contained in the specified column is outside the range of possible values for the column data type.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="27ff5-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="27ff5-120">User Action</span></span>  
 <span data-ttu-id="27ff5-121">這是無法修復的錯誤。</span><span class="sxs-lookup"><span data-stu-id="27ff5-121">The error is not repairable.</span></span> <span data-ttu-id="27ff5-122">請將資料行更新為資料行之資料類型範圍內的值，並重新執行命令。</span><span class="sxs-lookup"><span data-stu-id="27ff5-122">Update the column to a value within the range for the data type of the column and run the command again.</span></span>  <span data-ttu-id="27ff5-123">如需詳細資訊，請參閱這篇知識庫文章：[923247](https://support.microsoft.com/kb/923247)。</span><span class="sxs-lookup"><span data-stu-id="27ff5-123">For more information, see this KB article [923247](https://support.microsoft.com/kb/923247).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27ff5-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="27ff5-124">See Also</span></span>  
 <span data-ttu-id="27ff5-125">[UPDATE &#40;Transact-SQL&#41;](/sql/t-sql/queries/update-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="27ff5-125">[UPDATE &#40;Transact-SQL&#41;](/sql/t-sql/queries/update-transact-sql) </span></span>  
 [<span data-ttu-id="27ff5-126">資料類型 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="27ff5-126">Data Types &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/data-types-transact-sql)  
  
  
