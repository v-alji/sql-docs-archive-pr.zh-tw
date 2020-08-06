---
title: MSSQLSERVER_7901 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 7901 (Database Engine error)
ms.assetid: 2d0d19b9-947b-4474-9ff8-7e03019ab93d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: fae6e55cbe7170f795aff85400da2c5cdaef780a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596013"
---
# <a name="mssqlserver_7901"></a><span data-ttu-id="193aa-102">MSSQLSERVER_7901</span><span class="sxs-lookup"><span data-stu-id="193aa-102">MSSQLSERVER_7901</span></span>
    
## <a name="details"></a><span data-ttu-id="193aa-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="193aa-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="193aa-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="193aa-104">Product Name</span></span>|<span data-ttu-id="193aa-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="193aa-105">SQL Server</span></span>|  
|<span data-ttu-id="193aa-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="193aa-106">Event ID</span></span>|<span data-ttu-id="193aa-107">7901</span><span class="sxs-lookup"><span data-stu-id="193aa-107">7901</span></span>|  
|<span data-ttu-id="193aa-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="193aa-108">Event Source</span></span>|<span data-ttu-id="193aa-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="193aa-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="193aa-110">元件</span><span class="sxs-lookup"><span data-stu-id="193aa-110">Component</span></span>|<span data-ttu-id="193aa-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="193aa-111">SQLEngine</span></span>|  
|<span data-ttu-id="193aa-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="193aa-112">Symbolic Name</span></span>|<span data-ttu-id="193aa-113">DBCC2_DATABASE_IN_EMERGENCY_MODE</span><span class="sxs-lookup"><span data-stu-id="193aa-113">DBCC2_DATABASE_IN_EMERGENCY_MODE</span></span>|  
|<span data-ttu-id="193aa-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="193aa-114">Message Text</span></span>|<span data-ttu-id="193aa-115">未處理修復陳述式。</span><span class="sxs-lookup"><span data-stu-id="193aa-115">The repair statement was not processed.</span></span> <span data-ttu-id="193aa-116">當資料庫處於緊急模式時不支援此修復層級。</span><span class="sxs-lookup"><span data-stu-id="193aa-116">This level of repair is not supported when the database is in emergency mode.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="193aa-117">說明</span><span class="sxs-lookup"><span data-stu-id="193aa-117">Explanation</span></span>  
 <span data-ttu-id="193aa-118">資料庫正處於緊急模式，而且已經指定了 REPAIR_ALLOW_DATA_LOSS 以外的修復層級。</span><span class="sxs-lookup"><span data-stu-id="193aa-118">The database is in emergency mode and a repair level other than REPAIR_ALLOW_DATA_LOSS has been specified.</span></span> <span data-ttu-id="193aa-119">除非指定 REPAIR_ALLOW_DATA_LOSS，否則不能在緊急模式下進行修復。</span><span class="sxs-lookup"><span data-stu-id="193aa-119">Repairs cannot be made in emergency mode unless REPAIR_ALLOW_DATA_LOSS is specified.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="193aa-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="193aa-120">User Action</span></span>  
 <span data-ttu-id="193aa-121">重新執行命令，並指定 REPAIR_ALLOW_DATA_LOSS 選項。</span><span class="sxs-lookup"><span data-stu-id="193aa-121">Rerun the command and specify the REPAIR_ALLOW_DATA_LOSS option.</span></span>  
  
  
