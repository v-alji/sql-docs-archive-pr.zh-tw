---
title: MSSQLSERVER_3452 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 3452 (Database Engine error)
ms.assetid: bf838f02-7186-4b33-b01e-361b0c02de1f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 662d342064e8094400a6b672e21704877b4d0448
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584546"
---
# <a name="mssqlserver_3452"></a><span data-ttu-id="f07b7-102">MSSQLSERVER_3452</span><span class="sxs-lookup"><span data-stu-id="f07b7-102">MSSQLSERVER_3452</span></span>
    
## <a name="details"></a><span data-ttu-id="f07b7-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="f07b7-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f07b7-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="f07b7-104">Product Name</span></span>|<span data-ttu-id="f07b7-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="f07b7-105">SQL Server</span></span>|  
|<span data-ttu-id="f07b7-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="f07b7-106">Event ID</span></span>|<span data-ttu-id="f07b7-107">3452</span><span class="sxs-lookup"><span data-stu-id="f07b7-107">3452</span></span>|  
|<span data-ttu-id="f07b7-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="f07b7-108">Event Source</span></span>|<span data-ttu-id="f07b7-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="f07b7-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="f07b7-110">元件</span><span class="sxs-lookup"><span data-stu-id="f07b7-110">Component</span></span>|<span data-ttu-id="f07b7-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="f07b7-111">SQLEngine</span></span>|  
|<span data-ttu-id="f07b7-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="f07b7-112">Symbolic Name</span></span>|<span data-ttu-id="f07b7-113">REC_CHECKIDENTITY</span><span class="sxs-lookup"><span data-stu-id="f07b7-113">REC_CHECKIDENTITY</span></span>|  
|<span data-ttu-id="f07b7-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="f07b7-114">Message Text</span></span>|<span data-ttu-id="f07b7-115">資料庫 '%.\*ls' (%d) 的復原偵測到資料表識別碼 %d 中的識別值可能不一致。</span><span class="sxs-lookup"><span data-stu-id="f07b7-115">Recovery of database '%.\*ls' (%d) detected possible identity value inconsistency in table ID %d.</span></span> <span data-ttu-id="f07b7-116">請執行 DBCC CHECKIDENT ('%.\*ls')。</span><span class="sxs-lookup"><span data-stu-id="f07b7-116">Run DBCC CHECKIDENT ('%.\*ls').</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="f07b7-117">說明</span><span class="sxs-lookup"><span data-stu-id="f07b7-117">Explanation</span></span>  
 <span data-ttu-id="f07b7-118">升級至 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 時，復原資料庫中識別值的處理序在中繼資料中發現不一致的問題。</span><span class="sxs-lookup"><span data-stu-id="f07b7-118">During the upgrade to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], the process to recover the identity values in the database found an inconsistency in the metadata.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="f07b7-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="f07b7-119">User Action</span></span>  
 <span data-ttu-id="f07b7-120">執行 DBCC CHECKIDENT。</span><span class="sxs-lookup"><span data-stu-id="f07b7-120">Run DBCC CHECKIDENT.</span></span>  
  
  
