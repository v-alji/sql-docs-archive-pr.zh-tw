---
title: MSSQLSERVER_8642 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 8642 (Database Engine error)
ms.assetid: fc498059-202f-4d0b-8599-4e784b47c186
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e30296fa569599b91ca74edc7535d330119e1680
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597858"
---
# <a name="mssqlserver_8642"></a><span data-ttu-id="8b579-102">MSSQLSERVER_8642</span><span class="sxs-lookup"><span data-stu-id="8b579-102">MSSQLSERVER_8642</span></span>
    
## <a name="details"></a><span data-ttu-id="8b579-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="8b579-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8b579-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="8b579-104">Product Name</span></span>|<span data-ttu-id="8b579-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="8b579-105">SQL Server</span></span>|  
|<span data-ttu-id="8b579-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="8b579-106">Event ID</span></span>|<span data-ttu-id="8b579-107">8642</span><span class="sxs-lookup"><span data-stu-id="8b579-107">8642</span></span>|  
|<span data-ttu-id="8b579-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="8b579-108">Event Source</span></span>|<span data-ttu-id="8b579-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="8b579-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="8b579-110">元件</span><span class="sxs-lookup"><span data-stu-id="8b579-110">Component</span></span>|<span data-ttu-id="8b579-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="8b579-111">SQLEngine</span></span>|  
|<span data-ttu-id="8b579-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="8b579-112">Symbolic Name</span></span>|<span data-ttu-id="8b579-113">EXCHNGSTART_ERR</span><span class="sxs-lookup"><span data-stu-id="8b579-113">EXCHNGSTART_ERR</span></span>|  
|<span data-ttu-id="8b579-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="8b579-114">Message Text</span></span>|<span data-ttu-id="8b579-115">查詢處理器無法為平行查詢的執行啟動必要的執行緒資源。</span><span class="sxs-lookup"><span data-stu-id="8b579-115">The query processor could not start the necessary thread resources for parallel query execution.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="8b579-116">說明</span><span class="sxs-lookup"><span data-stu-id="8b579-116">Explanation</span></span>  
 <span data-ttu-id="8b579-117">伺服器中的執行緒資源不足。</span><span class="sxs-lookup"><span data-stu-id="8b579-117">Thread resources are low in the server.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="8b579-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="8b579-118">User Action</span></span>  
 <span data-ttu-id="8b579-119">減少伺服器的負載，然後重新執行查詢。</span><span class="sxs-lookup"><span data-stu-id="8b579-119">Reduce load on the server, and run the query again.</span></span>  
  
  
