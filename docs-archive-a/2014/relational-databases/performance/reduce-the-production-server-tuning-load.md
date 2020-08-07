---
title: 降低生產伺服器的微調負載 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- overhead [Database Engine Tuning Advisor]
- tuning overhead [SQL Server]
- reducing production server tuning load
- Database Engine Tuning Advisor [SQL Server], test servers
- test servers [Database Engine Tuning Advisor]
- production servers [SQL Server]
- offload tuning overhead [SQL Server]
ms.assetid: bb95ecaf-444a-4771-a625-e0a91c8f0709
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 53a61b17793a50d6b819f7c1684afdc4de4377f4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597783"
---
# <a name="reduce-the-production-server-tuning-load"></a><span data-ttu-id="93ffc-102">降低生產伺服器的微調負載</span><span class="sxs-lookup"><span data-stu-id="93ffc-102">Reduce the Production Server Tuning Load</span></span>
  [!INCLUDE[ssDE](../../../includes/ssde-md.md)] <span data-ttu-id="93ffc-103">Tuning Advisor 會仰賴查詢最佳化工具來分析工作負載以及提出微調建議。</span><span class="sxs-lookup"><span data-stu-id="93ffc-103">Tuning Advisor relies on the query optimizer to analyze a workload and to make tuning recommendations.</span></span> <span data-ttu-id="93ffc-104">針對實際伺服器執行這項分析會增加伺服器負載，而且可能會在微調工作階段期間減損伺服器效能。</span><span class="sxs-lookup"><span data-stu-id="93ffc-104">Performing this analysis on the production server adds to the server load and can hurt server performance during the tuning session.</span></span> <span data-ttu-id="93ffc-105">除了實際伺服器以外，您可以使用測試伺服器來減少微調工作階段期間對伺服器負載造成的影響。</span><span class="sxs-lookup"><span data-stu-id="93ffc-105">You can reduce the impact to the server load during a tuning session by using a test server in addition to the production server.</span></span>

## <a name="how-database-engine-tuning-advisor-uses-a-test-server"></a><span data-ttu-id="93ffc-106">Database Engine Tuning Advisor 使用測試伺服器的方式</span><span class="sxs-lookup"><span data-stu-id="93ffc-106">How Database Engine Tuning Advisor Uses a Test Server</span></span>
 <span data-ttu-id="93ffc-107">測試伺服器的傳統使用方式是，將生產伺服器上所有的資料都複製到測試伺服器上，然後微調測試伺服器，再於生產伺服器上實作建議項目。</span><span class="sxs-lookup"><span data-stu-id="93ffc-107">The traditional way to use a test server is to copy all of the data from your production server to your test server, tune the test server, and then implement the recommendation on your production server.</span></span> <span data-ttu-id="93ffc-108">這項程序可避免對生產伺服器造成效能上的影響，但卻不是最好的解決方案。</span><span class="sxs-lookup"><span data-stu-id="93ffc-108">This process eliminates the performance impact on your production server, but nevertheless is not the optimal solution.</span></span> <span data-ttu-id="93ffc-109">例如，從生產伺服器複製大量資料到測試伺服器，會耗用大量的時間與資源。</span><span class="sxs-lookup"><span data-stu-id="93ffc-109">For example, copying large amounts of data from the production to the test server can consume substantial amounts of time and resources.</span></span> <span data-ttu-id="93ffc-110">此外，測試伺服器硬體不太可能和生產伺服器所部署的硬體一樣強大。</span><span class="sxs-lookup"><span data-stu-id="93ffc-110">In addition, test server hardware is seldom as powerful as the hardware that is deployed for production servers.</span></span> <span data-ttu-id="93ffc-111">微調處理所依賴的是查詢最佳化工具，而它所產生的建議有部份卻是依據基礎硬體。</span><span class="sxs-lookup"><span data-stu-id="93ffc-111">The tuning process relies on the query optimizer, and the recommendations it generates are based in part on the underlying hardware.</span></span> <span data-ttu-id="93ffc-112">如果測試與實際伺服器的硬體不同， [!INCLUDE[ssDE](../../../includes/ssde-md.md)] Tuning Advisor 建議的品質就會受到影響。</span><span class="sxs-lookup"><span data-stu-id="93ffc-112">If the test and production server hardware are not identical, the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] Tuning Advisor recommendation quality is diminished.</span></span>

 <span data-ttu-id="93ffc-113">為避免這些問題， [!INCLUDE[ssDE](../../../includes/ssde-md.md)] Tuning Advisor 在對實際伺服器的資料庫進行微調時，會將大部分的微調負載卸載到測試伺服器上。</span><span class="sxs-lookup"><span data-stu-id="93ffc-113">To avoid these problems, [!INCLUDE[ssDE](../../../includes/ssde-md.md)] Tuning Advisor tunes a database on a production server by offloading most of the tuning load onto a test server.</span></span> <span data-ttu-id="93ffc-114">它的作法是使用生產伺服器硬體組態資訊，而不實際將生產伺服器的資料複製到測試伺服器。</span><span class="sxs-lookup"><span data-stu-id="93ffc-114">It does this by using the production server hardware configuration information and without actually copying the data from the production server to the test server.</span></span> [!INCLUDE[ssDE](../../../includes/ssde-md.md)] <span data-ttu-id="93ffc-115">Tuning Advisor 不會從實際伺服器將實際資料複製到測試伺服器。</span><span class="sxs-lookup"><span data-stu-id="93ffc-115">Tuning Advisor does not copy actual data from the production server to the test server.</span></span> <span data-ttu-id="93ffc-116">它只會複製中繼資料與必要的統計資料。</span><span class="sxs-lookup"><span data-stu-id="93ffc-116">It only copies the metadata and necessary statistics.</span></span>

 <span data-ttu-id="93ffc-117">下列步驟將概略說明在測試伺服器上微調生產資料庫的程序：</span><span class="sxs-lookup"><span data-stu-id="93ffc-117">The following steps outline the process for tuning a production database on a test server:</span></span>

1.  <span data-ttu-id="93ffc-118">確定要使用測試伺服器的使用者，同時存在於兩部伺服器上。</span><span class="sxs-lookup"><span data-stu-id="93ffc-118">Make sure that the user who wants to use the test server exists on both servers.</span></span>

     <span data-ttu-id="93ffc-119">開始之前，請先確定要使用測試伺服器來微調生產伺服器資料庫的使用者，同時存在於兩部伺服器上。</span><span class="sxs-lookup"><span data-stu-id="93ffc-119">Before you start, make sure that the user who wants to use the test server to tune a database on the production server exists on both servers.</span></span> <span data-ttu-id="93ffc-120">為此，您必須建立使用者及其在測試伺服器上的登入。</span><span class="sxs-lookup"><span data-stu-id="93ffc-120">This requires that you create the user and his or her login on the test server.</span></span> <span data-ttu-id="93ffc-121">若您在兩部電腦上都是 **系統管理員** 固定伺服器角色的成員，即可略過此步驟。</span><span class="sxs-lookup"><span data-stu-id="93ffc-121">If you are a member of the **sysadmin** fixed server role on both computers, this step is not necessary.</span></span>

2.  <span data-ttu-id="93ffc-122">在測試伺服器上微調工作負載。</span><span class="sxs-lookup"><span data-stu-id="93ffc-122">Tune the workload on the test server.</span></span>

     <span data-ttu-id="93ffc-123">若要在測試伺服器上微調工作負載，您必須透過 **dta** 命令列公用程式使用 XML 輸入檔。</span><span class="sxs-lookup"><span data-stu-id="93ffc-123">To tune a workload on a test server, you must use an XML input file with the **dta** command-line utility.</span></span> <span data-ttu-id="93ffc-124">在 XML 輸入檔中，使用 **TestServer** 子元素指定測試伺服器的名稱，並指定 **TuningOptions** 父元素底下其他子元素的值。</span><span class="sxs-lookup"><span data-stu-id="93ffc-124">In the XML input file, specify the name of your test server with the **TestServer** subelement in addition to specifying the values for the other subelements under the **TuningOptions** parent element.</span></span>

     <span data-ttu-id="93ffc-125">在微調的過程中，Database Engine Tuning Advisor 會在測試伺服器上建立 Shell 資料庫。</span><span class="sxs-lookup"><span data-stu-id="93ffc-125">During the tuning process, Database Engine Tuning Advisor creates a shell database on the test server.</span></span> <span data-ttu-id="93ffc-126">為建立此 Shell 資料庫並加以微調，Database Engine Tuning Advisor 會針對下列項目，對生產伺服器發出呼叫：</span><span class="sxs-lookup"><span data-stu-id="93ffc-126">To create this shell database and tune it, Database Engine Tuning Advisor makes calls to the production server for the following:</span></span>

    1.  [!INCLUDE[ssDE](../../../includes/ssde-md.md)] <span data-ttu-id="93ffc-127">Tuning Advisor 會將生產環境資料庫的中繼資料匯入測試伺服器的 Shell 資料庫。</span><span class="sxs-lookup"><span data-stu-id="93ffc-127">Tuning Advisor imports metadata from the production database to the test server shell database.</span></span> <span data-ttu-id="93ffc-128">此中繼資料中包含了空白資料表、索引、檢視、預存程序、觸發程序等，</span><span class="sxs-lookup"><span data-stu-id="93ffc-128">This metadata includes empty tables, indexes, views, stored procedures, triggers, and so on.</span></span> <span data-ttu-id="93ffc-129">如此即可對測試伺服器的 Shell 資料庫執行工作負載查詢。</span><span class="sxs-lookup"><span data-stu-id="93ffc-129">This makes it possible for the workload queries to execute against the test server shell database.</span></span>

    2.  [!INCLUDE[ssDE](../../../includes/ssde-md.md)] <span data-ttu-id="93ffc-130">Tuning Advisor 會從實際伺服器匯入統計資料，讓查詢最佳化工具能夠準確地將測試伺服器上的查詢最佳化。</span><span class="sxs-lookup"><span data-stu-id="93ffc-130">Tuning Advisor imports statistics from the production server so the query optimizer can accurately optimize queries on the test server.</span></span>

    3.  [!INCLUDE[ssDE](../../../includes/ssde-md.md)] <span data-ttu-id="93ffc-131">Tuning Advisor 會匯入硬體參數，以指定實際伺服器的處理器與可用記憶體數量，進而為查詢最佳化工具提供在產生查詢計劃時所需的資訊。</span><span class="sxs-lookup"><span data-stu-id="93ffc-131">Tuning Advisor imports hardware parameters specifying the number of processors and available memory from the production server to provide the query optimizer with the information it needs to generate a query plan.</span></span>

3.  <span data-ttu-id="93ffc-132">[!INCLUDE[ssDE](../../../includes/ssde-md.md)] Tuning Advisor 完成測試伺服器 Shell 資料庫的微調之後，它會產生微調建議。</span><span class="sxs-lookup"><span data-stu-id="93ffc-132">After [!INCLUDE[ssDE](../../../includes/ssde-md.md)] Tuning Advisor finishes tuning the test server shell database, it generates a tuning recommendation.</span></span>

4.  <span data-ttu-id="93ffc-133">將微調測試伺服器之後所得到的建議，套用到生產伺服器上。</span><span class="sxs-lookup"><span data-stu-id="93ffc-133">Apply the recommendation received from tuning the test server to the production server.</span></span>

 <span data-ttu-id="93ffc-134">下圖說明測試伺服器與生產伺服器的案例：</span><span class="sxs-lookup"><span data-stu-id="93ffc-134">The following illustration shows the test server and production server scenario:</span></span>

 <span data-ttu-id="93ffc-135">![Database Engine Tuning Advisor 測試伺服器使用方式](../../database-engine/media/testsvr.gif "Database Engine Tuning Advisor 測試伺服器使用方式")</span><span class="sxs-lookup"><span data-stu-id="93ffc-135">![Database Engine Tuning Advisor test server usage](../../database-engine/media/testsvr.gif "Database Engine Tuning Advisor test server usage")</span></span>

> [!NOTE]
>  <span data-ttu-id="93ffc-136">[!INCLUDE[ssDE](../../../includes/ssde-md.md)] Tuning Advisor 圖形化使用者介面 (GUI) 不支援測試伺服器微調功能。</span><span class="sxs-lookup"><span data-stu-id="93ffc-136">The test server tuning feature is not supported in the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] Tuning Advisor graphical user interface (GUI).</span></span>

## <a name="example"></a><span data-ttu-id="93ffc-137">範例</span><span class="sxs-lookup"><span data-stu-id="93ffc-137">Example</span></span>
 <span data-ttu-id="93ffc-138">首先，請確定要執行微調的使用者，同時存在於測試伺服器與生產伺服器上。</span><span class="sxs-lookup"><span data-stu-id="93ffc-138">First, make sure that the user who wants to perform the tuning exists on both the test and production servers.</span></span>

 <span data-ttu-id="93ffc-139">將使用者資訊複製到測試伺服器之後，您可以在 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] Tuning Advisor XML 輸入檔中定義測試伺服器微調工作階段。</span><span class="sxs-lookup"><span data-stu-id="93ffc-139">After the user information is copied over to your test server, you can define your test server tuning session in the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] Tuning Advisor XML input file.</span></span> <span data-ttu-id="93ffc-140">下列 XML 輸入檔範例將示範如何以 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] Tuning Advisor 指定測試伺服器的資料庫微調作業。</span><span class="sxs-lookup"><span data-stu-id="93ffc-140">The following example XML input file illustrates how to specify a test server to tune a database with [!INCLUDE[ssDE](../../../includes/ssde-md.md)] Tuning Advisor.</span></span>

 <span data-ttu-id="93ffc-141">在此範例中， `MyDatabaseName` 資料庫會在 `MyServerName`上進行微調。</span><span class="sxs-lookup"><span data-stu-id="93ffc-141">In this example, the `MyDatabaseName` database is being tuned on `MyServerName`.</span></span> <span data-ttu-id="93ffc-142">並使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] 指令碼 `MyWorkloadScript.sql`做為工作負載。</span><span class="sxs-lookup"><span data-stu-id="93ffc-142">The [!INCLUDE[tsql](../../includes/tsql-md.md)] script, `MyWorkloadScript.sql`, is used as the workload.</span></span> <span data-ttu-id="93ffc-143">此工作負載中包含了針對 `MyDatabaseName`而執行的事件。</span><span class="sxs-lookup"><span data-stu-id="93ffc-143">This workload contains events that execute against `MyDatabaseName`.</span></span> <span data-ttu-id="93ffc-144">在微調過程中，查詢最佳化工具對此資料庫所產生的大多數呼叫，都由位於 `MyTestServerName`中的 Shell 資料庫處理。</span><span class="sxs-lookup"><span data-stu-id="93ffc-144">Most of the query optimizer calls to this database, which occur as part of the tuning process, are handled by the shell database that resides on `MyTestServerName`.</span></span> <span data-ttu-id="93ffc-145">Shell 資料庫中含有中繼資料與統計資料，</span><span class="sxs-lookup"><span data-stu-id="93ffc-145">The shell database is composed of metadata and statistics.</span></span> <span data-ttu-id="93ffc-146">此程序會將微調負擔卸載到測試伺服器上。</span><span class="sxs-lookup"><span data-stu-id="93ffc-146">This process results in the tuning overhead being offloaded to the test server.</span></span> <span data-ttu-id="93ffc-147">當 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] Tuning Advisor 使用此 XML 輸入檔產生微調建議時，它應該只會考量索引 (`<FeatureSet>IDX</FeatureSet>`)，而不考量資料分割，也不需在 `MyDatabaseName`中保存任何現有的實體設計結構。</span><span class="sxs-lookup"><span data-stu-id="93ffc-147">When [!INCLUDE[ssDE](../../../includes/ssde-md.md)] Tuning Advisor generates its tuning recommendation using this XML input file, it should consider indexes only (`<FeatureSet>IDX</FeatureSet>`), no partitioning, and need not keep any of the existing physical design structures in `MyDatabaseName`.</span></span>

```
<?xml version="1.0" encoding="utf-16" ?>
<DTAXML xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="https://schemas.microsoft.com/sqlserver/2004/07/dta">
  <DTAInput>
    <Server>
      <Name>MyServerName</Name>
      <Database>
        <Name>MyDatabaseName</Name>
      </Database>
    </Server>
    <Workload>
      <File>MyWorkloadScript.sql</File>
    </Workload>
    <TuningOptions>
      <TestServer>MyTestServerName</TestServer>
      <FeatureSet>IDX</FeatureSet>
      <Partitioning>NONE</Partitioning>
      <KeepExisting>NONE</KeepExisting>
    </TuningOptions>
  </DTAInput>
</DTAXML>
```

## <a name="see-also"></a><span data-ttu-id="93ffc-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="93ffc-148">See Also</span></span>
 <span data-ttu-id="93ffc-149">[使用測試伺服器](considerations-for-using-test-servers.md) [XML 輸入檔參考 &#40;Database Engine Tuning Advisor&#41;](database-engine-tuning-advisor.md)的考慮</span><span class="sxs-lookup"><span data-stu-id="93ffc-149">[Considerations for Using Test Servers](considerations-for-using-test-servers.md) [XML Input File Reference &#40;Database Engine Tuning Advisor&#41;](database-engine-tuning-advisor.md)</span></span>


