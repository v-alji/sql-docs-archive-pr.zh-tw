---
title: MSSQLSERVER_1803 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 1803 (Database Engine error)
ms.assetid: d4315390-82f1-4c4c-8d1b-1a4989537cca
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 11302f882846c49c6e9998608967e7042ac9860c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597155"
---
# <a name="mssqlserver_1803"></a><span data-ttu-id="fa752-102">MSSQLSERVER_1803</span><span class="sxs-lookup"><span data-stu-id="fa752-102">MSSQLSERVER_1803</span></span>
    
## <a name="details"></a><span data-ttu-id="fa752-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="fa752-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="fa752-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="fa752-104">Product Name</span></span>|<span data-ttu-id="fa752-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="fa752-105">SQL Server</span></span>|  
|<span data-ttu-id="fa752-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="fa752-106">Event ID</span></span>|<span data-ttu-id="fa752-107">1803</span><span class="sxs-lookup"><span data-stu-id="fa752-107">1803</span></span>|  
|<span data-ttu-id="fa752-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="fa752-108">Event Source</span></span>|<span data-ttu-id="fa752-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="fa752-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="fa752-110">元件</span><span class="sxs-lookup"><span data-stu-id="fa752-110">Component</span></span>|<span data-ttu-id="fa752-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="fa752-111">SQLEngine</span></span>|  
|<span data-ttu-id="fa752-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="fa752-112">Symbolic Name</span></span>|<span data-ttu-id="fa752-113">NO_SPACE</span><span class="sxs-lookup"><span data-stu-id="fa752-113">NO_SPACE</span></span>|  
|<span data-ttu-id="fa752-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="fa752-114">Message Text</span></span>|<span data-ttu-id="fa752-115">CREATE DATABASE 失敗。</span><span class="sxs-lookup"><span data-stu-id="fa752-115">CREATE DATABASE failed.</span></span> <span data-ttu-id="fa752-116">主要檔案至少要有 %d MB，才能容納模型資料庫的副本。</span><span class="sxs-lookup"><span data-stu-id="fa752-116">Primary file must be at least %d MB to accommodate a copy of the model database.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="fa752-117">說明</span><span class="sxs-lookup"><span data-stu-id="fa752-117">Explanation</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="fa752-118">會建立模型資料庫的複本來建立資料庫。</span><span class="sxs-lookup"><span data-stu-id="fa752-118">creates a database by making a copy of the model database.</span></span> <span data-ttu-id="fa752-119">然後 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會將此複本重新命名，並將新的資料庫放大為所要求的大小。</span><span class="sxs-lookup"><span data-stu-id="fa752-119">Then [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] renames the copy, and enlarges the new database to the requested size.</span></span> <span data-ttu-id="fa752-120">在此情況下，使用者嘗試建立小於模型資料庫的資料庫。</span><span class="sxs-lookup"><span data-stu-id="fa752-120">In this case, the user tried to create a database smaller than the model database.</span></span> <span data-ttu-id="fa752-121">由於模型資料庫的複本不適合主要資料檔案 (因為檔案小於此模型資料庫)，所以此作業失敗。</span><span class="sxs-lookup"><span data-stu-id="fa752-121">The operation failed because the copy of the model database could not fit on the primary data file, because the file was smaller than the model database.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="fa752-122">使用者動作</span><span class="sxs-lookup"><span data-stu-id="fa752-122">User Action</span></span>  
 <span data-ttu-id="fa752-123">使用較大的資料庫檔案大小建立資料庫。</span><span class="sxs-lookup"><span data-stu-id="fa752-123">Create the database by using a larger database file size.</span></span> <span data-ttu-id="fa752-124">然後如果您想要使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 或 DBCC SHRINKDATABASE 陳述式，請縮小資料庫。</span><span class="sxs-lookup"><span data-stu-id="fa752-124">Then shrink the database if you want by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], or the DBCC SHRINKDATABASE statement.</span></span>  
  
  
