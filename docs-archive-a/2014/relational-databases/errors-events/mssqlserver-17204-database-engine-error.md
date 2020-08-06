---
title: MSSQLSERVER_17204 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 17204 (Database Engine error)
ms.assetid: 40db66f9-dd5e-478c-891e-a06d363a2552
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c63f0b3d2aff8b909e3a7fc841c9038cf95a475e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595080"
---
# <a name="mssqlserver_17204"></a><span data-ttu-id="103b9-102">MSSQLSERVER_17204</span><span class="sxs-lookup"><span data-stu-id="103b9-102">MSSQLSERVER_17204</span></span>
    
## <a name="details"></a><span data-ttu-id="103b9-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="103b9-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="103b9-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="103b9-104">Product Name</span></span>|<span data-ttu-id="103b9-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="103b9-105">SQL Server</span></span>|  
|<span data-ttu-id="103b9-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="103b9-106">Event ID</span></span>|<span data-ttu-id="103b9-107">17204</span><span class="sxs-lookup"><span data-stu-id="103b9-107">17204</span></span>|  
|<span data-ttu-id="103b9-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="103b9-108">Event Source</span></span>|<span data-ttu-id="103b9-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="103b9-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="103b9-110">元件</span><span class="sxs-lookup"><span data-stu-id="103b9-110">Component</span></span>|<span data-ttu-id="103b9-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="103b9-111">SQLEngine</span></span>|  
|<span data-ttu-id="103b9-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="103b9-112">Symbolic Name</span></span>|<span data-ttu-id="103b9-113">DBLKIO_DEVOPENFAILED</span><span class="sxs-lookup"><span data-stu-id="103b9-113">DBLKIO_DEVOPENFAILED</span></span>|  
|<span data-ttu-id="103b9-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="103b9-114">Message Text</span></span>|<span data-ttu-id="103b9-115">%ls:無法開啟檔案 %ls，檔案編號為 %d。</span><span class="sxs-lookup"><span data-stu-id="103b9-115">%ls: Could not open file %ls for file number %d.</span></span>  <span data-ttu-id="103b9-116">作業系統錯誤: %ls。</span><span class="sxs-lookup"><span data-stu-id="103b9-116">OS error: %ls.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="103b9-117">說明</span><span class="sxs-lookup"><span data-stu-id="103b9-117">Explanation</span></span>  
 <span data-ttu-id="103b9-118">SQL Server 無法開啟指定的檔案，因為發生指定的錯誤。</span><span class="sxs-lookup"><span data-stu-id="103b9-118">SQL Server was unable to open the specified file due to the specified error.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="103b9-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="103b9-119">User Action</span></span>  
 <span data-ttu-id="103b9-120">診斷並更正作業系統，然後重試此作業。</span><span class="sxs-lookup"><span data-stu-id="103b9-120">Diagnose and correct the operating system, then retry the operation.</span></span>  
  
  
