---
title: MSSQLSERVER_360 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 360 (Database Engine error)
ms.assetid: e2b7c1b2-3679-4206-9b25-6bd55ef96a2c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b30311d7f55231c1e7a6d5969d49c5d1bc07a848
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594578"
---
# <a name="mssqlserver_360"></a><span data-ttu-id="f1088-102">MSSQLSERVER_360</span><span class="sxs-lookup"><span data-stu-id="f1088-102">MSSQLSERVER_360</span></span>
    
## <a name="details"></a><span data-ttu-id="f1088-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="f1088-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f1088-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="f1088-104">Product Name</span></span>|<span data-ttu-id="f1088-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="f1088-105">SQL Server</span></span>|  
|<span data-ttu-id="f1088-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="f1088-106">Event ID</span></span>|<span data-ttu-id="f1088-107">360</span><span class="sxs-lookup"><span data-stu-id="f1088-107">360</span></span>|  
|<span data-ttu-id="f1088-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="f1088-108">Event Source</span></span>|<span data-ttu-id="f1088-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="f1088-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="f1088-110">元件</span><span class="sxs-lookup"><span data-stu-id="f1088-110">Component</span></span>|<span data-ttu-id="f1088-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="f1088-111">SQLEngine</span></span>|  
|<span data-ttu-id="f1088-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="f1088-112">Symbolic Name</span></span>|<span data-ttu-id="f1088-113">DML_UPDATE_SPARSE_AND_COLSET</span><span class="sxs-lookup"><span data-stu-id="f1088-113">DML_UPDATE_SPARSE_AND_COLSET</span></span>|  
|<span data-ttu-id="f1088-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="f1088-114">Message Text</span></span>|<span data-ttu-id="f1088-115">INSERT、UPDATE 或 MERGE 陳述式的目標資料行清單中不可以同時包含疏鬆資料行和內含疏鬆資料行的資料行集。</span><span class="sxs-lookup"><span data-stu-id="f1088-115">The target column list of an INSERT, UPDATE, or MERGE statement cannot contain both a sparse column and the column set that contains the sparse column.</span></span> <span data-ttu-id="f1088-116">請重寫陳述式，以包含疏鬆資料行或資料行集，而非同時包含兩者。</span><span class="sxs-lookup"><span data-stu-id="f1088-116">Rewrite the statement to include either the sparse column or the column set, but not both.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="f1088-117">說明</span><span class="sxs-lookup"><span data-stu-id="f1088-117">Explanation</span></span>  
 <span data-ttu-id="f1088-118">資料行集是不具類型的 XML 表示，可將資料表的某些資料行結合到結構化輸出中。</span><span class="sxs-lookup"><span data-stu-id="f1088-118">A column set is an untyped XML representation that combines some columns of a table into a structured output.</span></span> <span data-ttu-id="f1088-119">嘗試修改此資料行集以及此資料行集中所含的資料行，造成兩個項目參考相同的資料行。</span><span class="sxs-lookup"><span data-stu-id="f1088-119">An attempt was made to modify both the column set and a column that is included in the column set, causing two references to the same column.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="f1088-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="f1088-120">User Action</span></span>  
 <span data-ttu-id="f1088-121">請重寫陳述式，以包含對此資料行或資料行集的參考，但不要將這兩個參考同時包含在陳述式內。</span><span class="sxs-lookup"><span data-stu-id="f1088-121">Rewrite the statement to include references to either the column or the column set, but do not include both in the statement.</span></span>  
  
  
