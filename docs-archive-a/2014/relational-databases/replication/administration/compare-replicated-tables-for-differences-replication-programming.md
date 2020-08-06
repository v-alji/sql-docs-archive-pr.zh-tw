---
title: 比較複寫資料表的差異 (複寫程式設計) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- tablediff utility
- comparing replicated tables
ms.assetid: cd253a17-0c85-42b4-912c-690169ebe799
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0d804c7d4ac9cc54fa144b7054c6032663b76c0a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709262"
---
# <a name="compare-replicated-tables-for-differences-replication-programming"></a><span data-ttu-id="26be3-102">比較複寫資料表的差異 (複寫程式設計)</span><span class="sxs-lookup"><span data-stu-id="26be3-102">Compare Replicated Tables for Differences (Replication Programming)</span></span>
  <span data-ttu-id="26be3-103">發行項驗證可用來判斷「發行者」和「訂閱者」端資料表發行項的發行資料是否互異，若有則可能代表無法聚合。</span><span class="sxs-lookup"><span data-stu-id="26be3-103">Article validation is used to determine if published data for table articles at the Publisher and Subscriber are not identical, which can indicate non-convergence.</span></span> <span data-ttu-id="26be3-104">如需詳細資訊，請參閱[驗證複寫的資料](../validate-data-at-the-subscriber.md)。</span><span class="sxs-lookup"><span data-stu-id="26be3-104">For more information, see [Validate Replicated Data](../validate-data-at-the-subscriber.md).</span></span> <span data-ttu-id="26be3-105">不過，驗證只會傳回通過或失敗資訊，而不會針對來源及目的地資料表之間的差異提供任何相關資訊。</span><span class="sxs-lookup"><span data-stu-id="26be3-105">However, validation only returns pass or fail information and does not provide any information about what is different between the source and destination tables.</span></span> <span data-ttu-id="26be3-106">**tablediff** 命令提示字元公用程式會傳回兩個資料表之間差異的詳細資訊，甚至可能產生 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 指令碼，將訂閱向發行者端的資料聚合。</span><span class="sxs-lookup"><span data-stu-id="26be3-106">The **tablediff** command prompt utility returns detailed difference information between two tables and can even generate a [!INCLUDE[tsql](../../../includes/tsql-md.md)] script to bring a subscription into convergence with data at the Publisher.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="26be3-107">只有 **伺服器支援** tablediff [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 公用程式。</span><span class="sxs-lookup"><span data-stu-id="26be3-107">The **tablediff** utility is only supported for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] servers.</span></span>  
  
### <a name="to-compare-replicated-tables-for-differences-using-tablediff"></a><span data-ttu-id="26be3-108">若要使用 tablediff 比較複寫資料表的差異</span><span class="sxs-lookup"><span data-stu-id="26be3-108">To compare replicated tables for differences using tablediff</span></span>  
  
1.  <span data-ttu-id="26be3-109">從複寫拓撲中任何伺服器的命令提示字元執行 [tablediff Utility](../../../tools/tablediff-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="26be3-109">From the command prompt at any server in a replication topology, run the [tablediff Utility](../../../tools/tablediff-utility.md).</span></span> <span data-ttu-id="26be3-110">指定下列參數：</span><span class="sxs-lookup"><span data-stu-id="26be3-110">Specify the following parameters:</span></span>  
  
    -   <span data-ttu-id="26be3-111">**-sourceserver** - 已知其上資料正確的伺服器名稱，通常是「發行者」端。</span><span class="sxs-lookup"><span data-stu-id="26be3-111">**-sourceserver** - name of the server on which the data is known to be correct, usually the Publisher.</span></span>  
  
    -   <span data-ttu-id="26be3-112">**-sourcedatabase** - 包含正確資料之資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="26be3-112">**-sourcedatabase** - name of the database containing the correct data.</span></span>  
  
    -   <span data-ttu-id="26be3-113">**-sourcetable** - 所比較發行項之來源資料表的名稱。</span><span class="sxs-lookup"><span data-stu-id="26be3-113">**-sourcetable** - name of the source table for the article being compared.</span></span>  
  
    -   <span data-ttu-id="26be3-114">(選擇性) **-sourceschema** - 來源資料表的結構描述擁有者 (若非預設的結構描述)。</span><span class="sxs-lookup"><span data-stu-id="26be3-114">(Optional) **-sourceschema** - schema owner of the source table, if not the default schema.</span></span>  
  
    -   <span data-ttu-id="26be3-115">(選擇性) 在使用「SQL Server 驗證」連接到「發行者」時，使用 **-sourceuser** 和 **-sourcepassword** 。</span><span class="sxs-lookup"><span data-stu-id="26be3-115">(Optional) **-sourceuser** and **-sourcepassword** when using SQL Server Authentication to connect to the Publisher.</span></span>  
  
        > [!IMPORTANT]  
        >  <span data-ttu-id="26be3-116">盡可能使用 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="26be3-116">When possible, use Windows Authentication.</span></span> <span data-ttu-id="26be3-117">如果必須使用「 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 驗證」，請提示使用者在執行階段輸入安全性認證。</span><span class="sxs-lookup"><span data-stu-id="26be3-117">If you must use [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication, prompt users to enter security credentials at runtime.</span></span> <span data-ttu-id="26be3-118">如果您必須將認證儲存在指令碼檔案中，則必須維護這個檔案的安全性，使他人無法在未獲授權的情況下擅自存取。</span><span class="sxs-lookup"><span data-stu-id="26be3-118">If you must store credentials in a script file, you must secure the file to prevent unauthorized access.</span></span>  
  
    -   <span data-ttu-id="26be3-119">**-destinationserver** - 所比較資料所在伺服器的名稱，通常是「訂閱者」。</span><span class="sxs-lookup"><span data-stu-id="26be3-119">**-destinationserver** - name of the server on which the data is being compared, usually a Subscriber.</span></span>  
  
    -   <span data-ttu-id="26be3-120">**-destinationdatabase** - 所比較資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="26be3-120">**-destinationdatabase** - name of a the database being compared.</span></span>  
  
    -   <span data-ttu-id="26be3-121">**-destinationtable** - 所比較資料表的名稱。</span><span class="sxs-lookup"><span data-stu-id="26be3-121">**-destinationtable** - name of the table being compared.</span></span>  
  
    -   <span data-ttu-id="26be3-122">(選擇性) **-destinationschema** - 目的地資料表的結構描述擁有者 (若非預設的結構描述)。</span><span class="sxs-lookup"><span data-stu-id="26be3-122">(Optional) **-destinationschema** - schema owner of the destination table, if not the default schema.</span></span>  
  
    -   <span data-ttu-id="26be3-123">(選擇性) 在使用「 **驗證」連接到「訂閱者」時，使用** -destinationuser **和** -destinationpassword [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="26be3-123">(Optional) **-destinationuser** and **-destinationpassword** when using [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication to connect to the Subscriber.</span></span>  
  
        > [!IMPORTANT]  
        >  <span data-ttu-id="26be3-124">盡可能使用 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="26be3-124">When possible, use Windows Authentication.</span></span> <span data-ttu-id="26be3-125">如果必須使用「 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 驗證」，請提示使用者在執行階段輸入安全性認證。</span><span class="sxs-lookup"><span data-stu-id="26be3-125">If you must use [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication, prompt users to enter security credentials at runtime.</span></span> <span data-ttu-id="26be3-126">如果您必須將認證儲存在指令碼檔案中，則必須維護這個檔案的安全性，使他人無法在未獲授權的情況下擅自存取。</span><span class="sxs-lookup"><span data-stu-id="26be3-126">If you must store credentials in a script file, you must secure the file to prevent unauthorized access.</span></span>  
  
    -   <span data-ttu-id="26be3-127">(選擇性) 使用 **-c** 可執行資料行層級比較。</span><span class="sxs-lookup"><span data-stu-id="26be3-127">(Optional) Use **-c** to do a column-level comparison.</span></span>  
  
    -   <span data-ttu-id="26be3-128">(選擇性) 使用 **-q** 可執行僅限列數和結構描述的快速比較。</span><span class="sxs-lookup"><span data-stu-id="26be3-128">(Optional) Use **-q** to do a fast, row count- and schema-only comparison.</span></span>  
  
    -   <span data-ttu-id="26be3-129">(選擇性) 針對 **-o** 指定檔案名稱和路徑，以將結果輸出至檔案。</span><span class="sxs-lookup"><span data-stu-id="26be3-129">(Optional) Specify a file name and path for **-o** to output the results to a file.</span></span>  
  
    -   <span data-ttu-id="26be3-130">(選擇性) 指定訂閱資料庫中的資料表，以在其中插入 **-et**的結果。</span><span class="sxs-lookup"><span data-stu-id="26be3-130">(Optional) Specify a table in the subscription database into which to insert results for **-et**.</span></span> <span data-ttu-id="26be3-131">如果該資料表已存在，請指定 **-dt** 先將該資料表卸除。</span><span class="sxs-lookup"><span data-stu-id="26be3-131">If the table already exists, specify **-dt** to first drop the table.</span></span>  
  
    -   <span data-ttu-id="26be3-132">(選擇性) 使用 **-f** 可產生 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 檔案，以修正「訂閱者」端的資料，使其符合「發行者」端的資料。</span><span class="sxs-lookup"><span data-stu-id="26be3-132">(Optional) Use **-f** to generate a [!INCLUDE[tsql](../../../includes/tsql-md.md)] file to fix data at the Subscriber so that it matches data at the Publisher.</span></span> <span data-ttu-id="26be3-133">使用 **-df** 可指定每個檔案中的 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 陳述式數目。</span><span class="sxs-lookup"><span data-stu-id="26be3-133">Use **-df** to specify the number of [!INCLUDE[tsql](../../../includes/tsql-md.md)] statements in each file.</span></span>  
  
    -   <span data-ttu-id="26be3-134">(選擇性) 使用 **-rc** 和 **-ri** 可指定重試作業的次數和重試間隔。</span><span class="sxs-lookup"><span data-stu-id="26be3-134">(Optional) Use **-rc** and **-ri** to specify the number of times to retry an operation and the retry interval.</span></span>  
  
    -   <span data-ttu-id="26be3-135">(選擇性) 使用 **-strict** 可在來源和目的地資料表之間強制執行嚴格的結構描述比較。</span><span class="sxs-lookup"><span data-stu-id="26be3-135">(Optional) Use **-strict** to enforce strict schema comparison between source and destination tables.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26be3-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="26be3-136">See Also</span></span>  
 [<span data-ttu-id="26be3-137">驗證訂閱者端的資料</span><span class="sxs-lookup"><span data-stu-id="26be3-137">Validate Data at the Subscriber</span></span>](../validate-data-at-the-subscriber.md)  
  
  
