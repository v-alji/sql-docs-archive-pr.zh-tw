---
title: MSSQLSERVER_11409 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 11409 (Database Engine error)
ms.assetid: 99b71a1c-a72d-4ca9-9d00-4230c9042ba5
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e4249e13a3530f69978c78f2e2ca6e4583eed46a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585483"
---
# <a name="mssqlserver_11409"></a><span data-ttu-id="20400-102">MSSQLSERVER_11409</span><span class="sxs-lookup"><span data-stu-id="20400-102">MSSQLSERVER_11409</span></span>
    
## <a name="details"></a><span data-ttu-id="20400-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="20400-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="20400-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="20400-104">Product Name</span></span>|<span data-ttu-id="20400-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="20400-105">SQL Server</span></span>|  
|<span data-ttu-id="20400-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="20400-106">Event ID</span></span>|<span data-ttu-id="20400-107">11409</span><span class="sxs-lookup"><span data-stu-id="20400-107">11409</span></span>|  
|<span data-ttu-id="20400-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="20400-108">Event Source</span></span>|<span data-ttu-id="20400-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="20400-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="20400-110">元件</span><span class="sxs-lookup"><span data-stu-id="20400-110">Component</span></span>|<span data-ttu-id="20400-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="20400-111">SQLEngine</span></span>|  
|<span data-ttu-id="20400-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="20400-112">Symbolic Name</span></span>|<span data-ttu-id="20400-113">ALTERCOL_COLSET_DROP</span><span class="sxs-lookup"><span data-stu-id="20400-113">ALTERCOL_COLSET_DROP</span></span>|  
|<span data-ttu-id="20400-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="20400-114">Message Text</span></span>|<span data-ttu-id="20400-115">無法卸除資料表 '%.\*ls' 中的資料行集 '%.\*ls'，因為資料表包含超過 1025 個資料行。</span><span class="sxs-lookup"><span data-stu-id="20400-115">Cannot drop column set '%.\*ls' in table '%.\*ls' because the table contains more than 1025 columns.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="20400-116">說明</span><span class="sxs-lookup"><span data-stu-id="20400-116">Explanation</span></span>  
 <span data-ttu-id="20400-117">資料表最多可以包含 1024 個並未指定為疏鬆或計算資料行的資料行。</span><span class="sxs-lookup"><span data-stu-id="20400-117">Tables can contain a maximum of 1024 columns that are not designated as sparse, or computed.</span></span> <span data-ttu-id="20400-118">當疏鬆資料行導致資料表超過 1024 個資料行時，您就必須針對資料表定義資料行集。</span><span class="sxs-lookup"><span data-stu-id="20400-118">When sparse columns cause the table to exceed 1024 columns, a column set must be defined for the table.</span></span> <span data-ttu-id="20400-119">參考的資料表具有超過 1024 個資料行，而且您已嘗試移除資料行集。</span><span class="sxs-lookup"><span data-stu-id="20400-119">The table referenced has more than 1024 columns and you have attempted to remove the column set.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="20400-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="20400-120">User Action</span></span>  
 <span data-ttu-id="20400-121">由於目前的資料行位於資料表中，因此您必須保留資料行集。</span><span class="sxs-lookup"><span data-stu-id="20400-121">With the current columns in the table, you must retain the column set.</span></span>  
  
 <span data-ttu-id="20400-122">若要移除資料行集，請先從資料表中移除資料行，直到沒有超過 1024 個資料行為止。</span><span class="sxs-lookup"><span data-stu-id="20400-122">To remove the column set, first remove columns from the table, until you have no more than 1024 columns.</span></span> <span data-ttu-id="20400-123">然後，您就可以移除資料行集。</span><span class="sxs-lookup"><span data-stu-id="20400-123">Then, you can remove the column set.</span></span>  
  
  
