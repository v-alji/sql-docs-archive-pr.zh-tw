---
title: MSSQLSERVER_7910 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 7910 (Database Engine error)
ms.assetid: 017a0113-2b17-40b3-a419-30bbc43d46b8
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 60e7cca3f6973374ae7aeaa959a0b31207a1258e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596002"
---
# <a name="mssqlserver_7910"></a><span data-ttu-id="a5d62-102">MSSQLSERVER_7910</span><span class="sxs-lookup"><span data-stu-id="a5d62-102">MSSQLSERVER_7910</span></span>
    
## <a name="details"></a><span data-ttu-id="a5d62-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="a5d62-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a5d62-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="a5d62-104">Product Name</span></span>|<span data-ttu-id="a5d62-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="a5d62-105">SQL Server</span></span>|  
|<span data-ttu-id="a5d62-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="a5d62-106">Event ID</span></span>|<span data-ttu-id="a5d62-107">7910</span><span class="sxs-lookup"><span data-stu-id="a5d62-107">7910</span></span>|  
|<span data-ttu-id="a5d62-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="a5d62-108">Event Source</span></span>|<span data-ttu-id="a5d62-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="a5d62-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="a5d62-110">元件</span><span class="sxs-lookup"><span data-stu-id="a5d62-110">Component</span></span>|<span data-ttu-id="a5d62-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="a5d62-111">SQLEngine</span></span>|  
|<span data-ttu-id="a5d62-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="a5d62-112">Symbolic Name</span></span>|<span data-ttu-id="a5d62-113">DBCC2_REPAIR_PAGE_ALLOCATED</span><span class="sxs-lookup"><span data-stu-id="a5d62-113">DBCC2_REPAIR_PAGE_ALLOCATED</span></span>|  
|<span data-ttu-id="a5d62-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="a5d62-114">Message Text</span></span>|<span data-ttu-id="a5d62-115">修復:頁面 P_ID 已經配置給物件識別碼 O_ID，索引識別碼 I_ID，分割區識別碼 PN_ID，配置單位識別碼 A_ID (類型 TYPE)。</span><span class="sxs-lookup"><span data-stu-id="a5d62-115">Repair: The page P_ID has been allocated to object ID O_ID, index ID I_ID, partition ID PN_ID, alloc unit ID A_ID (type TYPE).</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="a5d62-116">說明</span><span class="sxs-lookup"><span data-stu-id="a5d62-116">Explanation</span></span>  
 <span data-ttu-id="a5d62-117">這是 REPAIR 傳回的參考用訊息，說明頁面已經配置給索引配置對應 (IAM) 頁面的單頁位置陣列。</span><span class="sxs-lookup"><span data-stu-id="a5d62-117">This is an informational message from REPAIR that states that a page has been allocated to the single-page slot array of an Index Allocation Map (IAM) page.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="a5d62-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="a5d62-118">User Action</span></span>  
 <span data-ttu-id="a5d62-119">None</span><span class="sxs-lookup"><span data-stu-id="a5d62-119">None</span></span>  
  
  
