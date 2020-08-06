---
title: SQL Server 參數 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Database Engine analysis [Upgrade Advisor]
- SQL Server Upgrade Advisor, Database Engine
- Upgrade Advisor [SQL Server], Database Engine
- analyzing system [Upgrade Advisor], Database Engine
ms.assetid: 44a18bfe-e593-47a5-995f-382c01d3f618
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 2b885e7616506fd08cae99166cc794dbfb5dac7d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704678"
---
# <a name="sql-server-parameters"></a><span data-ttu-id="5b8a3-102">SQL Server 參數</span><span class="sxs-lookup"><span data-stu-id="5b8a3-102">SQL Server Parameters</span></span>
  <span data-ttu-id="5b8a3-103">在這個頁面上，您可以設定分析器將用於 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 分析的參數。</span><span class="sxs-lookup"><span data-stu-id="5b8a3-103">On this page, set parameters that the analyzer will use for [!INCLUDE[ssDE](../../includes/ssde-md.md)] analysis.</span></span> <span data-ttu-id="5b8a3-104">您可以分析一個、許多個或所有資料庫、分析使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 所建立的追蹤檔案，以及分析 SQL 批次檔。</span><span class="sxs-lookup"><span data-stu-id="5b8a3-104">You can analyze one, several, or all databases, analyze trace files that were created by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], and analyze SQL batch files.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5b8a3-105">只有在您提交要分析的追蹤檔案或 SQL 批次檔時，才能偵測出某些升級問題。</span><span class="sxs-lookup"><span data-stu-id="5b8a3-105">Some upgrade issues can be detected only if you submit trace files or SQL batch files to be analyzed.</span></span>  
  
## <a name="options"></a><span data-ttu-id="5b8a3-106">選項</span><span class="sxs-lookup"><span data-stu-id="5b8a3-106">Options</span></span>  
 <span data-ttu-id="5b8a3-107">**要分析的資料庫**</span><span class="sxs-lookup"><span data-stu-id="5b8a3-107">**Database(s) to analyze**</span></span>  
 <span data-ttu-id="5b8a3-108">若要分析所有資料庫，請選取 [**所有資料庫**] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="5b8a3-108">To analyze all databases, select the **All databases** check box.</span></span> <span data-ttu-id="5b8a3-109">若要分析資料庫的選取範圍，請選取要包括在掃描中之每個資料庫旁的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="5b8a3-109">To analyze a selection of databases, select the check box next to each database to include in the scan.</span></span>  
  
 <span data-ttu-id="5b8a3-110">**分析追蹤檔案**</span><span class="sxs-lookup"><span data-stu-id="5b8a3-110">**Analyze trace file(s)**</span></span>  
 <span data-ttu-id="5b8a3-111">選取此核取方塊可以在檔案系統中分析追蹤檔案。</span><span class="sxs-lookup"><span data-stu-id="5b8a3-111">Select this check box to analyze trace files in the file system.</span></span>  
  
 <span data-ttu-id="5b8a3-112">**追蹤檔案的路徑**</span><span class="sxs-lookup"><span data-stu-id="5b8a3-112">**Path to trace file(s)**</span></span>  
 <span data-ttu-id="5b8a3-113">您可以分析一個或多個檔案。</span><span class="sxs-lookup"><span data-stu-id="5b8a3-113">You can analyze one or more files.</span></span> <span data-ttu-id="5b8a3-114">您可以瀏覽至某個位置並選取多個檔案，也可以提供多個檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="5b8a3-114">You can browse to a location and select multiple files, or you can provide multiple file names.</span></span> <span data-ttu-id="5b8a3-115">請使用每個檔案的完整路徑名稱、加入檔案名稱，然後使用縱線字元 (|) 來分隔項目。</span><span class="sxs-lookup"><span data-stu-id="5b8a3-115">Use the full path name to each file, include the file name, and separate entries by using the pipe character (|).</span></span>  
  
 <span data-ttu-id="5b8a3-116">如果您啟用 [\*\*分析追蹤檔案] (s) \*\*，則會停用 **[下一步]** ，直到您輸入路徑名稱和檔案名為止。</span><span class="sxs-lookup"><span data-stu-id="5b8a3-116">If you enable **Analyze trace file(s)**, **Next** is disabled until you enter a path name and a file name.</span></span>  
  
 <span data-ttu-id="5b8a3-117">**分析 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (s) 的批次檔**</span><span class="sxs-lookup"><span data-stu-id="5b8a3-117">**Analyze [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] batch file(s)**</span></span>  
 <span data-ttu-id="5b8a3-118">選取此核取方塊可以在檔案系統中分析 [!INCLUDE[tsql](../../includes/tsql-md.md)] 批次檔。</span><span class="sxs-lookup"><span data-stu-id="5b8a3-118">Select this check box to analyze [!INCLUDE[tsql](../../includes/tsql-md.md)] batch files in the file system.</span></span>  
  
 <span data-ttu-id="5b8a3-119">\*\*[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]批次檔 (s 的路徑) \*\*</span><span class="sxs-lookup"><span data-stu-id="5b8a3-119">**Path to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] batch file(s)**</span></span>  
 <span data-ttu-id="5b8a3-120">您可以分析一個或多個批次檔。</span><span class="sxs-lookup"><span data-stu-id="5b8a3-120">You can analyze one or more batch files.</span></span> <span data-ttu-id="5b8a3-121">您可以瀏覽至某個位置並選取多個檔案，也可以輸入多個檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="5b8a3-121">You can browse to a location and select multiple files, or you can type multiple file names.</span></span> <span data-ttu-id="5b8a3-122">請使用每個檔案的完整路徑名稱、加入檔案名稱，然後使用縱線字元 (|) 來分隔項目。</span><span class="sxs-lookup"><span data-stu-id="5b8a3-122">Use the full path name to each file, include the file name, and separate entries by using the pipe character (|).</span></span>  
  
 <span data-ttu-id="5b8a3-123">如果您啟用 [**分析 SQL 批次檔 (s) **]，則會停用 [**下一步]** 按鈕，直到您輸入路徑名稱和檔案名為止。</span><span class="sxs-lookup"><span data-stu-id="5b8a3-123">If you enable **Analyze SQL batch file(s)**, the **Next** button is disabled until you enter a path name and a file name.</span></span>  
  
 <span data-ttu-id="5b8a3-124">**SQL 批次分隔符號**</span><span class="sxs-lookup"><span data-stu-id="5b8a3-124">**SQL Batch Separator**</span></span>  
 <span data-ttu-id="5b8a3-125">用來分隔 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式批次的文字。</span><span class="sxs-lookup"><span data-stu-id="5b8a3-125">The text that is used to separate batches of [!INCLUDE[tsql](../../includes/tsql-md.md)] statements.</span></span> <span data-ttu-id="5b8a3-126">預設值為**GO**。</span><span class="sxs-lookup"><span data-stu-id="5b8a3-126">The default value is **GO**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b8a3-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5b8a3-127">See Also</span></span>  
 <span data-ttu-id="5b8a3-128">[使用 Upgrade Advisor](../../../2014/sql-server/install/working-with-upgrade-advisor.md) </span><span class="sxs-lookup"><span data-stu-id="5b8a3-128">[Working with Upgrade Advisor](../../../2014/sql-server/install/working-with-upgrade-advisor.md) </span></span>  
 [<span data-ttu-id="5b8a3-129">Upgrade Advisor 使用者介面參考</span><span class="sxs-lookup"><span data-stu-id="5b8a3-129">Upgrade Advisor User Interface Reference</span></span>](../../../2014/sql-server/install/upgrade-advisor-user-interface-reference.md)  
  
  
