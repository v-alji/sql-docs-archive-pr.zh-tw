---
title: MSSQLSERVER_2508 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2508 (Database Engine error)
ms.assetid: c37d40e5-c665-4d66-a727-5cb845634fcc
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 11dd1c72c8cae868b7ebcb02e72ef0db81aeafe2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699640"
---
# <a name="mssqlserver_2508"></a><span data-ttu-id="36501-102">MSSQLSERVER_2508</span><span class="sxs-lookup"><span data-stu-id="36501-102">MSSQLSERVER_2508</span></span>
    
## <a name="details"></a><span data-ttu-id="36501-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="36501-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="36501-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="36501-104">Product Name</span></span>|<span data-ttu-id="36501-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="36501-105">SQL Server</span></span>|  
|<span data-ttu-id="36501-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="36501-106">Event ID</span></span>|<span data-ttu-id="36501-107">2508</span><span class="sxs-lookup"><span data-stu-id="36501-107">2508</span></span>|  
|<span data-ttu-id="36501-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="36501-108">Event Source</span></span>|<span data-ttu-id="36501-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="36501-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="36501-110">元件</span><span class="sxs-lookup"><span data-stu-id="36501-110">Component</span></span>|<span data-ttu-id="36501-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="36501-111">SQLEngine</span></span>|  
|<span data-ttu-id="36501-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="36501-112">Symbolic Name</span></span>|<span data-ttu-id="36501-113">DBCC_OUT_OF_DATE_PAGE_OR_ROW_COUNT</span><span class="sxs-lookup"><span data-stu-id="36501-113">DBCC_OUT_OF_DATE_PAGE_OR_ROW_COUNT</span></span>|  
|<span data-ttu-id="36501-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="36501-114">Message Text</span></span>|<span data-ttu-id="36501-115">物件 "%.\*ls"，索引識別碼 %d，分割區識別碼 %I64d，配置單位識別碼 %I64d (類型 %.\*ls) 的 %.\*ls 計數不正確。</span><span class="sxs-lookup"><span data-stu-id="36501-115">The %.\*ls count for object "%.\*ls", index ID %d, partition ID %I64d, alloc unit ID %I64d (type %.\*ls) is incorrect.</span></span> <span data-ttu-id="36501-116">請執行 DBCC UPDATEUSAGE。</span><span class="sxs-lookup"><span data-stu-id="36501-116">Run DBCC UPDATEUSAGE.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="36501-117">說明</span><span class="sxs-lookup"><span data-stu-id="36501-117">Explanation</span></span>  
 <span data-ttu-id="36501-118">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 之前的 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 版本中，資料表和索引資料列計數值與頁數計數值可能會變得不正確。</span><span class="sxs-lookup"><span data-stu-id="36501-118">In versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] before [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], the values for the table and index row counts and page counts can become incorrect.</span></span> <span data-ttu-id="36501-119">在 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 之前的版本中建立的資料庫可能包含不正確的計數。</span><span class="sxs-lookup"><span data-stu-id="36501-119">Databases that were created on versions prior to [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] may contain incorrect counts.</span></span> <span data-ttu-id="36501-120">DBCC CHECKDB 已經增強為可以偵測到這些錯誤，而且會在遇到錯誤時傳回這則警告訊息。</span><span class="sxs-lookup"><span data-stu-id="36501-120">DBCC CHECKDB has been enhanced to detect these errors and returns this warning message when the error encountered.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="36501-121">使用者動作</span><span class="sxs-lookup"><span data-stu-id="36501-121">User Action</span></span>  
 <span data-ttu-id="36501-122">針對指定的物件或索引，或針對包含此物件的資料庫執行 DBCC UPDATEUSAGE，以便更正無效的計數。</span><span class="sxs-lookup"><span data-stu-id="36501-122">Run DBCC UPDATEUSAGE against the specified object or index, or against the database in which the object is contained to correct the invalid counts.</span></span>  
  
  
