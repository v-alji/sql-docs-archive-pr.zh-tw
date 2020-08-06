---
title: MSSQLSERVER_7911 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 7911 (Database Engine error)
ms.assetid: dd8390f3-0f77-4fb2-ba94-631a56e42bc6
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6d37ce2dc11f231e8a6f8ae6cc8b95d8b2f87c12
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596000"
---
# <a name="mssqlserver_7911"></a><span data-ttu-id="a1928-102">MSSQLSERVER_7911</span><span class="sxs-lookup"><span data-stu-id="a1928-102">MSSQLSERVER_7911</span></span>
    
## <a name="details"></a><span data-ttu-id="a1928-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="a1928-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a1928-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="a1928-104">Product Name</span></span>|<span data-ttu-id="a1928-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="a1928-105">SQL Server</span></span>|  
|<span data-ttu-id="a1928-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="a1928-106">Event ID</span></span>|<span data-ttu-id="a1928-107">7911</span><span class="sxs-lookup"><span data-stu-id="a1928-107">7911</span></span>|  
|<span data-ttu-id="a1928-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="a1928-108">Event Source</span></span>|<span data-ttu-id="a1928-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="a1928-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="a1928-110">元件</span><span class="sxs-lookup"><span data-stu-id="a1928-110">Component</span></span>|<span data-ttu-id="a1928-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="a1928-111">SQLEngine</span></span>|  
|<span data-ttu-id="a1928-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="a1928-112">Symbolic Name</span></span>|<span data-ttu-id="a1928-113">DBCC2_REPAIR_PAGE_DEALLOCATED</span><span class="sxs-lookup"><span data-stu-id="a1928-113">DBCC2_REPAIR_PAGE_DEALLOCATED</span></span>|  
|<span data-ttu-id="a1928-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="a1928-114">Message Text</span></span>|<span data-ttu-id="a1928-115">修復:頁面 P_ID 已經從物件識別碼 O_ID，索引識別碼 I_ID，分割區識別碼 PN_ID，配置單位識別碼 A_ID (類型 TYPE) 解除配置。</span><span class="sxs-lookup"><span data-stu-id="a1928-115">Repair: The page P_ID has been deallocated from object ID O_ID, index ID I_ID, partition ID PN_ID, alloc unit ID A_ID (type TYPE).</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="a1928-116">說明</span><span class="sxs-lookup"><span data-stu-id="a1928-116">Explanation</span></span>  
 <span data-ttu-id="a1928-117">這是 REPAIR 傳回的參考用訊息，說明頁面已經從索引配置對應 (IAM) 頁面的單頁位置陣列取消配置。</span><span class="sxs-lookup"><span data-stu-id="a1928-117">This is an informational message from REPAIR that states that a page has been deallocated from the single-page slot array of an Index Allocation Map (IAM) page.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="a1928-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="a1928-118">User Action</span></span>  
 <span data-ttu-id="a1928-119">None</span><span class="sxs-lookup"><span data-stu-id="a1928-119">None</span></span>  
  
  
