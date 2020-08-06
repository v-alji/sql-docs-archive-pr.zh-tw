---
title: MSSQLSERVER_1793 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
ms.assetid: 808db1d0-acc1-41d0-9287-8a5455001a02
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 54172adb957c3cbc1dbc221d1cae2a583830a1cc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699691"
---
# <a name="mssqlserver_1793"></a><span data-ttu-id="bcd9e-102">MSSQLSERVER_1793</span><span class="sxs-lookup"><span data-stu-id="bcd9e-102">MSSQLSERVER_1793</span></span>
    
## <a name="details"></a><span data-ttu-id="bcd9e-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="bcd9e-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="bcd9e-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="bcd9e-104">Product Name</span></span>|<span data-ttu-id="bcd9e-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="bcd9e-105">SQL Server</span></span>|  
|<span data-ttu-id="bcd9e-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="bcd9e-106">Event ID</span></span>|<span data-ttu-id="bcd9e-107">1793</span><span class="sxs-lookup"><span data-stu-id="bcd9e-107">1793</span></span>|  
|<span data-ttu-id="bcd9e-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="bcd9e-108">Event Source</span></span>|<span data-ttu-id="bcd9e-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="bcd9e-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="bcd9e-110">元件</span><span class="sxs-lookup"><span data-stu-id="bcd9e-110">Component</span></span>|<span data-ttu-id="bcd9e-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="bcd9e-111">SQLEngine</span></span>|  
|<span data-ttu-id="bcd9e-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="bcd9e-112">Symbolic Name</span></span>|<span data-ttu-id="bcd9e-113">FILESTREAM_BASEDATA_NEED_SAME_PARTITION</span><span class="sxs-lookup"><span data-stu-id="bcd9e-113">FILESTREAM_BASEDATA_NEED_SAME_PARTITION</span></span>|  
|<span data-ttu-id="bcd9e-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="bcd9e-114">Message Text</span></span>|<span data-ttu-id="bcd9e-115">無法卸除索引 '%.\*ls'，因為未指定 FILESTREAM 資料的分割區配置。</span><span class="sxs-lookup"><span data-stu-id="bcd9e-115">Cannot drop index '%.\*ls' since a partition scheme is not specified for FILESTREAM data.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="bcd9e-116">說明</span><span class="sxs-lookup"><span data-stu-id="bcd9e-116">Explanation</span></span>  
 <span data-ttu-id="bcd9e-117">當您嘗試在包含 FILESTREAM 資料的資料表上卸除叢集索引，而且對基底資料指定 **MOVE TO** 子句，但未對 FILESTREAM 資料指定 **FILESTREAM_ON** 子句時，就會出現這個訊息。</span><span class="sxs-lookup"><span data-stu-id="bcd9e-117">This message occurs when you try to drop a clustered index on a table that contains FILESTREAM data, and you specify a **MOVE TO** clause for the base data, but you do not specify a **FILESTREAM_ON** clause for the FILESTREAM data.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="bcd9e-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="bcd9e-118">User Action</span></span>  
 <span data-ttu-id="bcd9e-119">在包含 FILESTREAM 資料的資料表上卸除叢集索引時，使用下列其中一個選項：</span><span class="sxs-lookup"><span data-stu-id="bcd9e-119">When dropping a clustered index on a table that contains FILESTREAM data, use one of the following options:</span></span>  
  
-   <span data-ttu-id="bcd9e-120">對基底資料指定 **MOVE TO** 子句，而且對 FILESTREAM 資料指定 **FILESTREAM_ON** 子句。</span><span class="sxs-lookup"><span data-stu-id="bcd9e-120">Specify both a **MOVE TO** clause for the base data and a **FILESTREAM_ON** clause for the FILESTREAM data.</span></span>  
  
-   <span data-ttu-id="bcd9e-121">不對基底資料指定 **MOVE TO** 子句，或對 FILESTREAM 資料指定 **FILESTREAM_ON** 子句。</span><span class="sxs-lookup"><span data-stu-id="bcd9e-121">Do not specify either a **MOVE TO** clause for the base data or a **FILESTREAM_ON** clause for the FILESTREAM data.</span></span>  
  
 <span data-ttu-id="bcd9e-122">下列範例失敗，因為指定基底資料的分割區配置，但未指定 FILESTREAM 資料的分割區配置。</span><span class="sxs-lookup"><span data-stu-id="bcd9e-122">The following example fails because a partition scheme is specified for the base data, but is not specified for the FILESTREAM data.</span></span>  
  
```sql  
DROP INDEX [<clustered_index_name>] ON [<table_name>]   
WITH ( ONLINE = OFF, MOVE TO [PRIMARY] )  
GO  
```  
  
 <span data-ttu-id="bcd9e-123">下列範例成功，因為對基底資料指定 **MOVE TO** 子句，而且對 FILESTREAM 資料指定 **FILESTREAM_ON** 子句。</span><span class="sxs-lookup"><span data-stu-id="bcd9e-123">The following example succeeds because both a **MOVE TO** clause for the base data and a **FILESTREAM_ON** clause for the FILESTREAM data are specified.</span></span>  
  
```sql  
DROP INDEX [<clustered_index_name>] ON [<table_name>]   
WITH ( ONLINE = OFF, MOVE TO [PRIMARY], filestream_on 'default' )  
GO  
```  
  
 <span data-ttu-id="bcd9e-124">下列範例也成功，因為未對基底資料指定 **MOVE TO** 子句，也未對 FILESTREAM 資料指定 **FILESTREAM_ON** 子句。</span><span class="sxs-lookup"><span data-stu-id="bcd9e-124">The following example also succeeds because neither a **MOVE TO** clause for the base data nor a **FILESTREAM_ON** clause for the FILESTREAM data is specified.</span></span>  
  
```sql  
DROP INDEX [<clustered_index_name>] ON [<table_name>]   
WITH ( ONLINE = OFF )  
GO  
```  
  
  
