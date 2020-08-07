---
title: MSSQLSERVER_2539 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2539 (Database Engine error)
ms.assetid: e638efcc-56f4-40f9-9740-17ef67b47d79
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 9f061d2a827dca641bfc0c348af1328fd71856fd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598912"
---
# <a name="mssqlserver_2539"></a><span data-ttu-id="ab975-102">MSSQLSERVER_2539</span><span class="sxs-lookup"><span data-stu-id="ab975-102">MSSQLSERVER_2539</span></span>
    
## <a name="details"></a><span data-ttu-id="ab975-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="ab975-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ab975-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="ab975-104">Product Name</span></span>|<span data-ttu-id="ab975-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="ab975-105">SQL Server</span></span>|  
|<span data-ttu-id="ab975-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="ab975-106">Event ID</span></span>|<span data-ttu-id="ab975-107">2539</span><span class="sxs-lookup"><span data-stu-id="ab975-107">2539</span></span>|  
|<span data-ttu-id="ab975-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="ab975-108">Event Source</span></span>|<span data-ttu-id="ab975-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="ab975-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="ab975-110">元件</span><span class="sxs-lookup"><span data-stu-id="ab975-110">Component</span></span>|<span data-ttu-id="ab975-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="ab975-111">SQLEngine</span></span>|  
|<span data-ttu-id="ab975-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="ab975-112">Symbolic Name</span></span>|<span data-ttu-id="ab975-113">DBCC_ALLOCATION_SUMMARY_FOR_DATABASE</span><span class="sxs-lookup"><span data-stu-id="ab975-113">DBCC_ALLOCATION_SUMMARY_FOR_DATABASE</span></span>|  
|<span data-ttu-id="ab975-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="ab975-114">Message Text</span></span>|<span data-ttu-id="ab975-115">這個資料庫中的範圍總數目 = EXTENTS，使用的頁面 = USED_PAGES，保留的頁面 = RESERVED_PAGES。</span><span class="sxs-lookup"><span data-stu-id="ab975-115">Total number of extents = EXTENTS, used pages = USED_PAGES, reserved pages = RESERVED_PAGES in this database.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="ab975-116">說明</span><span class="sxs-lookup"><span data-stu-id="ab975-116">Explanation</span></span>  
 <span data-ttu-id="ab975-117">這項資訊是 DBCC CHECKALLOC 命令輸出的一部分，</span><span class="sxs-lookup"><span data-stu-id="ab975-117">This information is part of the output from the DBCC CHECKALLOC command.</span></span> <span data-ttu-id="ab975-118">也是指定資料庫中已配置範圍、已使用頁面和已保留頁面的摘要資訊。</span><span class="sxs-lookup"><span data-stu-id="ab975-118">This information is the summary of allocated extents, used pages, and reserved pages for the specified database.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="ab975-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="ab975-119">User Action</span></span>  
 <span data-ttu-id="ab975-120">None</span><span class="sxs-lookup"><span data-stu-id="ab975-120">None</span></span>  
  
  
