---
title: MSSQLSERVER_7915 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 7915 (Database Engine error)
ms.assetid: 63338587-7dd3-40e6-b70e-d8ae18fff47b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e1dc7a69023e49b48a10da9f0388cbd72fbe46be
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596713"
---
# <a name="mssqlserver_7915"></a><span data-ttu-id="e4a53-102">MSSQLSERVER_7915</span><span class="sxs-lookup"><span data-stu-id="e4a53-102">MSSQLSERVER_7915</span></span>
    
## <a name="details"></a><span data-ttu-id="e4a53-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="e4a53-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e4a53-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="e4a53-104">Product Name</span></span>|<span data-ttu-id="e4a53-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="e4a53-105">SQL Server</span></span>|  
|<span data-ttu-id="e4a53-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="e4a53-106">Event ID</span></span>|<span data-ttu-id="e4a53-107">7915</span><span class="sxs-lookup"><span data-stu-id="e4a53-107">7915</span></span>|  
|<span data-ttu-id="e4a53-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="e4a53-108">Event Source</span></span>|<span data-ttu-id="e4a53-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="e4a53-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="e4a53-110">元件</span><span class="sxs-lookup"><span data-stu-id="e4a53-110">Component</span></span>|<span data-ttu-id="e4a53-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="e4a53-111">SQLEngine</span></span>|  
|<span data-ttu-id="e4a53-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="e4a53-112">Symbolic Name</span></span>|<span data-ttu-id="e4a53-113">DBCC2_REPAIR_IAM_CHAIN_REBUILT</span><span class="sxs-lookup"><span data-stu-id="e4a53-113">DBCC2_REPAIR_IAM_CHAIN_REBUILT</span></span>|  
|<span data-ttu-id="e4a53-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="e4a53-114">Message Text</span></span>|<span data-ttu-id="e4a53-115">修復:物件識別碼 O_ID，索引識別碼 I_ID，分割區識別碼 PN_ID，配置單位識別碼 A_ID (類型 TYPE) 的 IAM 鏈結已在頁面 P_ID 之前截斷，且將會重建。</span><span class="sxs-lookup"><span data-stu-id="e4a53-115">Repair: IAM chain for object ID O_ID, index ID I_ID, partition ID PN_ID, alloc unit ID A_ID (type TYPE), has been truncated before page P_ID and will be rebuilt.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="e4a53-116">說明</span><span class="sxs-lookup"><span data-stu-id="e4a53-116">Explanation</span></span>  
 <span data-ttu-id="e4a53-117">這是由 REPAIR 傳送的參考用資訊，指出已經修補指定的索引配置對應 (IAM) 鏈結，因此可以重建該鏈結。</span><span class="sxs-lookup"><span data-stu-id="e4a53-117">This is an information message sent by REPAIR that indicates that the specified Index Allocation Map (IAM) chain was patched so that it could be rebuilt.</span></span> <span data-ttu-id="e4a53-118">這項修補動作可能已經要求配置 IAM 鏈結的新標頭，或是從鏈結中移除錯誤的頁面。</span><span class="sxs-lookup"><span data-stu-id="e4a53-118">This patching may have required the allocation of a new head of the IAM chain or the removal of bad pages from the chain.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="e4a53-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="e4a53-119">User Action</span></span>  
 <span data-ttu-id="e4a53-120">None</span><span class="sxs-lookup"><span data-stu-id="e4a53-120">None</span></span>  
  
  
