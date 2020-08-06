---
title: MSSQLSERVER_17128 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 17128 (Database Engine error)
ms.assetid: 7b15a5e6-fd41-47ce-ba87-54f72acea4bb
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0e08c668acd0a8b2decb14da338b8d1f1e650de5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698269"
---
# <a name="mssqlserver_17128"></a><span data-ttu-id="289fc-102">MSSQLSERVER_17128</span><span class="sxs-lookup"><span data-stu-id="289fc-102">MSSQLSERVER_17128</span></span>
    
## <a name="details"></a><span data-ttu-id="289fc-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="289fc-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="289fc-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="289fc-104">Product Name</span></span>|<span data-ttu-id="289fc-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="289fc-105">SQL Server</span></span>|  
|<span data-ttu-id="289fc-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="289fc-106">Event ID</span></span>|<span data-ttu-id="289fc-107">17128</span><span class="sxs-lookup"><span data-stu-id="289fc-107">17128</span></span>|  
|<span data-ttu-id="289fc-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="289fc-108">Event Source</span></span>|<span data-ttu-id="289fc-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="289fc-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="289fc-110">元件</span><span class="sxs-lookup"><span data-stu-id="289fc-110">Component</span></span>|<span data-ttu-id="289fc-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="289fc-111">SQLEngine</span></span>|  
|<span data-ttu-id="289fc-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="289fc-112">Symbolic Name</span></span>|<span data-ttu-id="289fc-113">INIT_NOBUFSPACE</span><span class="sxs-lookup"><span data-stu-id="289fc-113">INIT_NOBUFSPACE</span></span>|  
|<span data-ttu-id="289fc-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="289fc-114">Message Text</span></span>|<span data-ttu-id="289fc-115">initdata:未提供記憶體給核心緩衝區。</span><span class="sxs-lookup"><span data-stu-id="289fc-115">initdata: No memory for kernel buffers.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="289fc-116">說明</span><span class="sxs-lookup"><span data-stu-id="289fc-116">Explanation</span></span>  
 <span data-ttu-id="289fc-117">緩衝集區的初始記憶體配置或保留已經失敗，而且 SQL Server 結束。</span><span class="sxs-lookup"><span data-stu-id="289fc-117">The buffer pool's initial memory allocations or reservations have failed, and SQL Server exits.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="289fc-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="289fc-118">User Action</span></span>  
 <span data-ttu-id="289fc-119">通常是由於在非常小型的電腦 (遠低於最低系統需求) 上啟動 SQL Server 所造成。</span><span class="sxs-lookup"><span data-stu-id="289fc-119">Usually caused by starting SQL Server on an extremely small machine - far smaller than the minimum system requirements.</span></span>  
  
  
