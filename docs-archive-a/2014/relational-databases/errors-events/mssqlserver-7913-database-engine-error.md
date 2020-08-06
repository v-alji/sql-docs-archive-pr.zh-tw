---
title: MSSQLSERVER_7913 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 7913 (Database Engine error)
ms.assetid: 9d8ad456-b1a2-4f79-a252-657fbec9ad9b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: fb4110ef3aed8697db426ebd80f6764d873944db
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596716"
---
# <a name="mssqlserver_7913"></a><span data-ttu-id="c7306-102">MSSQLSERVER_7913</span><span class="sxs-lookup"><span data-stu-id="c7306-102">MSSQLSERVER_7913</span></span>
    
## <a name="details"></a><span data-ttu-id="c7306-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="c7306-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c7306-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="c7306-104">Product Name</span></span>|<span data-ttu-id="c7306-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="c7306-105">SQL Server</span></span>|  
|<span data-ttu-id="c7306-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="c7306-106">Event ID</span></span>|<span data-ttu-id="c7306-107">7913</span><span class="sxs-lookup"><span data-stu-id="c7306-107">7913</span></span>|  
|<span data-ttu-id="c7306-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="c7306-108">Event Source</span></span>|<span data-ttu-id="c7306-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="c7306-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="c7306-110">元件</span><span class="sxs-lookup"><span data-stu-id="c7306-110">Component</span></span>|<span data-ttu-id="c7306-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="c7306-111">SQLEngine</span></span>|  
|<span data-ttu-id="c7306-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="c7306-112">Symbolic Name</span></span>|<span data-ttu-id="c7306-113">DBCC2_REPAIR_EXTENT_DEALLOCATED</span><span class="sxs-lookup"><span data-stu-id="c7306-113">DBCC2_REPAIR_EXTENT_DEALLOCATED</span></span>|  
|<span data-ttu-id="c7306-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="c7306-114">Message Text</span></span>|<span data-ttu-id="c7306-115">修復:範圍 P_ID 已經從物件識別碼 O_ID，索引識別碼 I_ID，分割區識別碼 PN_ID，配置單位識別碼 A_ID (類型 TYPE) 取消配置。</span><span class="sxs-lookup"><span data-stu-id="c7306-115">Repair: Extent P_ID has been deallocated from object ID O_ID, index ID I_ID, partition ID PN_ID, alloc unit ID A_ID (type TYPE).</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="c7306-116">說明</span><span class="sxs-lookup"><span data-stu-id="c7306-116">Explanation</span></span>  
 <span data-ttu-id="c7306-117">這是來自 REPAIR 的參考用訊息，表示某個範圍已經從指定的物件取消配置。</span><span class="sxs-lookup"><span data-stu-id="c7306-117">This is an informational message from REPAIR that states that an extent has been deallocated from the specified object.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="c7306-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="c7306-118">User Action</span></span>  
 <span data-ttu-id="c7306-119">None</span><span class="sxs-lookup"><span data-stu-id="c7306-119">None</span></span>  
  
  
