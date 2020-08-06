---
title: MSSQLSERVER_5242 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 5242 (Database Engine error)
ms.assetid: 712b1a10-2f87-41df-a111-1ed9f14102d4
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c979d0a788e80cf5c7e1ab9b9a1ca8eccc0eea19
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595056"
---
# <a name="mssqlserver_5242"></a><span data-ttu-id="8b1c5-102">MSSQLSERVER_5242</span><span class="sxs-lookup"><span data-stu-id="8b1c5-102">MSSQLSERVER_5242</span></span>
    
## <a name="details"></a><span data-ttu-id="8b1c5-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="8b1c5-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8b1c5-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="8b1c5-104">Product Name</span></span>|<span data-ttu-id="8b1c5-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="8b1c5-105">SQL Server</span></span>|  
|<span data-ttu-id="8b1c5-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="8b1c5-106">Event ID</span></span>|<span data-ttu-id="8b1c5-107">5242</span><span class="sxs-lookup"><span data-stu-id="8b1c5-107">5242</span></span>|  
|<span data-ttu-id="8b1c5-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="8b1c5-108">Event Source</span></span>|<span data-ttu-id="8b1c5-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="8b1c5-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="8b1c5-110">元件</span><span class="sxs-lookup"><span data-stu-id="8b1c5-110">Component</span></span>|<span data-ttu-id="8b1c5-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="8b1c5-111">SQLEngine</span></span>|  
|<span data-ttu-id="8b1c5-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="8b1c5-112">Symbolic Name</span></span>||  
|<span data-ttu-id="8b1c5-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="8b1c5-113">Message Text</span></span>|<span data-ttu-id="8b1c5-114">於資料庫 '%.\*ls'(識別碼:%d) 的頁面 %S_PGID 上執行內部作業期間，偵測到不一致性。</span><span class="sxs-lookup"><span data-stu-id="8b1c5-114">An inconsistency was detected during an internal operation in database '%.\*ls'(ID:%d) on page %S_PGID.</span></span> <span data-ttu-id="8b1c5-115">請連絡技術支援部門。</span><span class="sxs-lookup"><span data-stu-id="8b1c5-115">Please contact technical support.</span></span> <span data-ttu-id="8b1c5-116">參考編號 %ld。</span><span class="sxs-lookup"><span data-stu-id="8b1c5-116">Reference number %ld.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="8b1c5-117">說明</span><span class="sxs-lookup"><span data-stu-id="8b1c5-117">Explanation</span></span>  
 <span data-ttu-id="8b1c5-118">錯誤訊息中參照的資料庫頁面上發生結構不一致的問題。</span><span class="sxs-lookup"><span data-stu-id="8b1c5-118">A structural inconsistency occurred on the database page that is referenced in the error message.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b1c5-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8b1c5-119">See Also</span></span>  
 <span data-ttu-id="8b1c5-120">[DBCC CHECKDB &#40;Transact-sql&#41;](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="8b1c5-120">[DBCC CHECKDB &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) </span></span>  
 [<span data-ttu-id="8b1c5-121">資料庫檔案與檔案群組</span><span class="sxs-lookup"><span data-stu-id="8b1c5-121">Database Files and Filegroups</span></span>](../databases/database-files-and-filegroups.md)  
  
  
