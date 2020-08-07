---
title: MSSQLSERVER_1101 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 1101 (Database Engine error)
ms.assetid: d63b67d5-59f5-4f77-904e-5ba67f2dd850
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 631b0ab1466815cbacfd71b4f9fd714fabd0f7b4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598969"
---
# <a name="mssqlserver_1101"></a><span data-ttu-id="23ee5-102">MSSQLSERVER_1101</span><span class="sxs-lookup"><span data-stu-id="23ee5-102">MSSQLSERVER_1101</span></span>
    
## <a name="details"></a><span data-ttu-id="23ee5-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="23ee5-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="23ee5-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="23ee5-104">Product Name</span></span>|<span data-ttu-id="23ee5-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="23ee5-105">SQL Server</span></span>|  
|<span data-ttu-id="23ee5-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="23ee5-106">Event ID</span></span>|<span data-ttu-id="23ee5-107">1101</span><span class="sxs-lookup"><span data-stu-id="23ee5-107">1101</span></span>|  
|<span data-ttu-id="23ee5-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="23ee5-108">Event Source</span></span>|<span data-ttu-id="23ee5-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="23ee5-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="23ee5-110">元件</span><span class="sxs-lookup"><span data-stu-id="23ee5-110">Component</span></span>|<span data-ttu-id="23ee5-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="23ee5-111">SQLEngine</span></span>|  
|<span data-ttu-id="23ee5-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="23ee5-112">Symbolic Name</span></span>|<span data-ttu-id="23ee5-113">NOALLOCPG</span><span class="sxs-lookup"><span data-stu-id="23ee5-113">NOALLOCPG</span></span>|  
|<span data-ttu-id="23ee5-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="23ee5-114">Message Text</span></span>|<span data-ttu-id="23ee5-115">檔案群組中的磁碟空間不足，無法為資料庫 '%.\*ls' 配置新的頁面，檔案群組：'%.\*ls'。</span><span class="sxs-lookup"><span data-stu-id="23ee5-115">Could not allocate a new page for database '%.\*ls' because of insufficient disk space in filegroup '%.\*ls'.</span></span> <span data-ttu-id="23ee5-116">請卸除檔案群組中的物件、將其他檔案加入檔案群組，或將檔案群組中現有檔案設定為自動成長，以產生必要的空間。</span><span class="sxs-lookup"><span data-stu-id="23ee5-116">Create the necessary space by dropping objects in the filegroup, adding additional files to the filegroup, or setting autogrowth on for existing files in the filegroup.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="23ee5-117">說明</span><span class="sxs-lookup"><span data-stu-id="23ee5-117">Explanation</span></span>  
 <span data-ttu-id="23ee5-118">檔案群組中沒有可用的磁碟空間。</span><span class="sxs-lookup"><span data-stu-id="23ee5-118">No disk space available in a filegroup.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="23ee5-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="23ee5-119">User Action</span></span>  
 <span data-ttu-id="23ee5-120">下列動作可以在檔案群組中提供可用的空間。</span><span class="sxs-lookup"><span data-stu-id="23ee5-120">The following actions may make space available in the filegroup.</span></span>  
  
-   <span data-ttu-id="23ee5-121">開啟自動成長功能。</span><span class="sxs-lookup"><span data-stu-id="23ee5-121">Turn on AUTOGROW.</span></span>  
  
-   <span data-ttu-id="23ee5-122">加入更多檔案到檔案中。</span><span class="sxs-lookup"><span data-stu-id="23ee5-122">Add more files to the file group.</span></span>  
  
-   <span data-ttu-id="23ee5-123">卸除檔案群組中不需要的索引或資料表，以釋出磁碟空間。</span><span class="sxs-lookup"><span data-stu-id="23ee5-123">Free up disk space by dropping unnecessary indexes or tables in the filegroup.</span></span>  
  
  
