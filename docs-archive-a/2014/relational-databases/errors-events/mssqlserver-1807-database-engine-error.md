---
title: MSSQLSERVER_1807 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 1807 (Database Engine error)
ms.assetid: 13c1b240-098b-4d9e-89aa-21599548e074
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 261d352084e490fb7f9216e1a7e352542e85a6f2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595081"
---
# <a name="mssqlserver_1807"></a><span data-ttu-id="23443-102">MSSQLSERVER_1807</span><span class="sxs-lookup"><span data-stu-id="23443-102">MSSQLSERVER_1807</span></span>
    
## <a name="details"></a><span data-ttu-id="23443-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="23443-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="23443-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="23443-104">Product Name</span></span>|<span data-ttu-id="23443-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="23443-105">SQL Server</span></span>|  
|<span data-ttu-id="23443-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="23443-106">Event ID</span></span>|<span data-ttu-id="23443-107">1807</span><span class="sxs-lookup"><span data-stu-id="23443-107">1807</span></span>|  
|<span data-ttu-id="23443-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="23443-108">Event Source</span></span>|<span data-ttu-id="23443-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="23443-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="23443-110">元件</span><span class="sxs-lookup"><span data-stu-id="23443-110">Component</span></span>|<span data-ttu-id="23443-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="23443-111">SQLEngine</span></span>|  
|<span data-ttu-id="23443-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="23443-112">Symbolic Name</span></span>|<span data-ttu-id="23443-113">CANNOT_EX_LOCK</span><span class="sxs-lookup"><span data-stu-id="23443-113">CANNOT_EX_LOCK</span></span>|  
|<span data-ttu-id="23443-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="23443-114">Message Text</span></span>|<span data-ttu-id="23443-115">無法取得資料庫 '%.\*ls' 的獨佔鎖定。</span><span class="sxs-lookup"><span data-stu-id="23443-115">Could not obtain exclusive lock on database '%.\*ls'.</span></span> <span data-ttu-id="23443-116">請稍後再重試作業。</span><span class="sxs-lookup"><span data-stu-id="23443-116">Retry the operation later.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="23443-117">說明</span><span class="sxs-lookup"><span data-stu-id="23443-117">Explanation</span></span>  
 <span data-ttu-id="23443-118">需要獨佔存取資料庫的作業無法取得適當的存取權。</span><span class="sxs-lookup"><span data-stu-id="23443-118">An operation that required exclusive access to the database was unable to obtain it.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="23443-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="23443-119">User Action</span></span>  
 <span data-ttu-id="23443-120">中斷該資料庫的所有連接，或稍後再重試查詢。</span><span class="sxs-lookup"><span data-stu-id="23443-120">Disconnect all the connections to that database or try the query again later.</span></span>  
  
  
