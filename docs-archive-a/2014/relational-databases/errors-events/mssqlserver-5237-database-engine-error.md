---
title: MSSQLSERVER_5237 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 5237 (Database Engine error)
ms.assetid: 9ff28935-d1eb-47ee-99b3-1a65cb948ce7
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 224317e290ce15aaed979129733b6273b3b663df
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598888"
---
# <a name="mssqlserver_5237"></a><span data-ttu-id="ae380-102">MSSQLSERVER_5237</span><span class="sxs-lookup"><span data-stu-id="ae380-102">MSSQLSERVER_5237</span></span>
    
## <a name="details"></a><span data-ttu-id="ae380-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="ae380-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ae380-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="ae380-104">Product Name</span></span>|<span data-ttu-id="ae380-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="ae380-105">SQL Server</span></span>|  
|<span data-ttu-id="ae380-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="ae380-106">Event ID</span></span>|<span data-ttu-id="ae380-107">5237</span><span class="sxs-lookup"><span data-stu-id="ae380-107">5237</span></span>|  
|<span data-ttu-id="ae380-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="ae380-108">Event Source</span></span>|<span data-ttu-id="ae380-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="ae380-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="ae380-110">元件</span><span class="sxs-lookup"><span data-stu-id="ae380-110">Component</span></span>|<span data-ttu-id="ae380-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="ae380-111">SQLEngine</span></span>|  
|<span data-ttu-id="ae380-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="ae380-112">Symbolic Name</span></span>|<span data-ttu-id="ae380-113">DBCC4_INDEXED_VIEW_CHECK_QUERY_FAILED_NO_ERRORCODE</span><span class="sxs-lookup"><span data-stu-id="ae380-113">DBCC4_INDEXED_VIEW_CHECK_QUERY_FAILED_NO_ERRORCODE</span></span>|  
|<span data-ttu-id="ae380-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="ae380-114">Message Text</span></span>|<span data-ttu-id="ae380-115">物件 'NAME' (物件識別碼 O_ID) 的 DBCC 跨資料列集檢查失敗，因為發生內部查詢錯誤。</span><span class="sxs-lookup"><span data-stu-id="ae380-115">DBCC cross-rowset check failed for object 'NAME' (object ID O_ID) due to an internal query error.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="ae380-116">說明</span><span class="sxs-lookup"><span data-stu-id="ae380-116">Explanation</span></span>  
 <span data-ttu-id="ae380-117">由於發生內部錯誤，導致 DBCC 無法執行查詢來檢查索引檢視表。</span><span class="sxs-lookup"><span data-stu-id="ae380-117">An internal error resulted in DBCC not being able to execute the query to check indexed views.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="ae380-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="ae380-118">User Action</span></span>  
 <span data-ttu-id="ae380-119">重新執行 DBCC 命令。</span><span class="sxs-lookup"><span data-stu-id="ae380-119">Rerun the DBCC command.</span></span>  
  
  
