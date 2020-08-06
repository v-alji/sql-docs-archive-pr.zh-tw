---
title: MSSQLSERVER_5231 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 5231 (Database Engine error)
ms.assetid: 6954ae84-ed0b-4f4c-9d0a-e73f3d71476c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 68f40ac3a566280526757bd8b83c784954ba3dde
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687905"
---
# <a name="mssqlserver_5231"></a><span data-ttu-id="b100a-102">MSSQLSERVER_5231</span><span class="sxs-lookup"><span data-stu-id="b100a-102">MSSQLSERVER_5231</span></span>
    
## <a name="details"></a><span data-ttu-id="b100a-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="b100a-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b100a-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="b100a-104">Product Name</span></span>|<span data-ttu-id="b100a-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="b100a-105">SQL Server</span></span>|  
|<span data-ttu-id="b100a-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="b100a-106">Event ID</span></span>|<span data-ttu-id="b100a-107">5231</span><span class="sxs-lookup"><span data-stu-id="b100a-107">5231</span></span>|  
|<span data-ttu-id="b100a-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="b100a-108">Event Source</span></span>|<span data-ttu-id="b100a-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="b100a-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="b100a-110">元件</span><span class="sxs-lookup"><span data-stu-id="b100a-110">Component</span></span>|<span data-ttu-id="b100a-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="b100a-111">SQLEngine</span></span>|  
|<span data-ttu-id="b100a-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="b100a-112">Symbolic Name</span></span>|<span data-ttu-id="b100a-113">DBCC4_DEADLOCK_SKIPPED_OBJECT</span><span class="sxs-lookup"><span data-stu-id="b100a-113">DBCC4_DEADLOCK_SKIPPED_OBJECT</span></span>|  
|<span data-ttu-id="b100a-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="b100a-114">Message Text</span></span>|<span data-ttu-id="b100a-115">物件識別碼 O_ID (物件 'NAME')：嘗試鎖定此物件進行檢查時發生死結。</span><span class="sxs-lookup"><span data-stu-id="b100a-115">Object ID O_ID (object 'NAME'): A deadlock occurred while trying to lock this object for checking.</span></span> <span data-ttu-id="b100a-116">已經略過這個物件，不會處理。</span><span class="sxs-lookup"><span data-stu-id="b100a-116">This object has been skipped and will not be processed.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="b100a-117">說明</span><span class="sxs-lookup"><span data-stu-id="b100a-117">Explanation</span></span>  
 <span data-ttu-id="b100a-118">DBCC 嘗試鎖定物件時發生死結，並已選擇 DBCC 做為死結犧牲者。</span><span class="sxs-lookup"><span data-stu-id="b100a-118">A deadlock occurred when DBCC was trying to lock the object, and DBCC was chosen as the deadlock victim.</span></span> <span data-ttu-id="b100a-119">將不會處理此物件。</span><span class="sxs-lookup"><span data-stu-id="b100a-119">The object will not be processed.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="b100a-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="b100a-120">User Action</span></span>  
 <span data-ttu-id="b100a-121">None</span><span class="sxs-lookup"><span data-stu-id="b100a-121">None</span></span>  
  
  
