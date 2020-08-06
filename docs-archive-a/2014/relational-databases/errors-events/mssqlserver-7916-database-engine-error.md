---
title: MSSQLSERVER_7916 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 7916 (Database Engine error)
ms.assetid: 9bac3536-de14-4e98-84c2-bde9a59ba0d1
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 21b31eedf61369d9c4d1cfdfd5f53eebd3f5341c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596714"
---
# <a name="mssqlserver_7916"></a><span data-ttu-id="d7256-102">MSSQLSERVER_7916</span><span class="sxs-lookup"><span data-stu-id="d7256-102">MSSQLSERVER_7916</span></span>
    
## <a name="details"></a><span data-ttu-id="d7256-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="d7256-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d7256-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="d7256-104">Product Name</span></span>|<span data-ttu-id="d7256-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="d7256-105">SQL Server</span></span>|  
|<span data-ttu-id="d7256-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="d7256-106">Event ID</span></span>|<span data-ttu-id="d7256-107">7916</span><span class="sxs-lookup"><span data-stu-id="d7256-107">7916</span></span>|  
|<span data-ttu-id="d7256-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="d7256-108">Event Source</span></span>|<span data-ttu-id="d7256-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="d7256-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="d7256-110">元件</span><span class="sxs-lookup"><span data-stu-id="d7256-110">Component</span></span>|<span data-ttu-id="d7256-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="d7256-111">SQLEngine</span></span>|  
|<span data-ttu-id="d7256-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="d7256-112">Symbolic Name</span></span>|<span data-ttu-id="d7256-113">DBCC2_REPAIR_RECORD_DELETED</span><span class="sxs-lookup"><span data-stu-id="d7256-113">DBCC2_REPAIR_RECORD_DELETED</span></span>|  
|<span data-ttu-id="d7256-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="d7256-114">Message Text</span></span>|<span data-ttu-id="d7256-115">修復:已刪除頁面 P_ID，位置 S_ID 上的物件識別碼 O_ID，索引識別碼 I_ID，分割區識別碼 PN_ID，配置單位識別碼 A_ID (類型 TYPE) 之記錄。</span><span class="sxs-lookup"><span data-stu-id="d7256-115">Repair: Deleted record for object ID O_ID, index ID I_ID, partition ID PN_ID, alloc unit ID A_ID (type TYPE), on page P_ID, slot S_ID.</span></span> <span data-ttu-id="d7256-116">將會重建索引。</span><span class="sxs-lookup"><span data-stu-id="d7256-116">Indexes will be rebuilt.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="d7256-117">說明</span><span class="sxs-lookup"><span data-stu-id="d7256-117">Explanation</span></span>  
 <span data-ttu-id="d7256-118">這是來自 REPAIR 的參考用訊息，指出已經從頁面中刪除指定的記錄。</span><span class="sxs-lookup"><span data-stu-id="d7256-118">This is an information messages from REPAIR that indicates the specified record was deleted from the page.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="d7256-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="d7256-119">User Action</span></span>  
 <span data-ttu-id="d7256-120">None</span><span class="sxs-lookup"><span data-stu-id="d7256-120">None</span></span>  
  
  
