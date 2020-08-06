---
title: 將知識新增至知識庫 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: da148a7f-55bc-4990-a157-e61968b831d7
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: d3450f220b7d879e76c112232081dfec22665dae
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592278"
---
# <a name="adding-knowledge-to-a-knowledge-base"></a><span data-ttu-id="a1804-102">將知識加入至知識庫</span><span class="sxs-lookup"><span data-stu-id="a1804-102">Adding Knowledge to a Knowledge Base</span></span>
  <span data-ttu-id="a1804-103">此主題描述您可以在 [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) 中將知識加入至知識庫的方式。</span><span class="sxs-lookup"><span data-stu-id="a1804-103">This topic describes the ways in which you can add knowledge to a knowledge base in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS).</span></span> <span data-ttu-id="a1804-104">在您可以執行資料品質作業之前，您必須擁有資料的相關知識。</span><span class="sxs-lookup"><span data-stu-id="a1804-104">Before you can perform data quality operations, you have to have knowledge about the data.</span></span> <span data-ttu-id="a1804-105">您取得該項知識的方式是建立及維護資料品質知識庫，並將與特定類型之資料來源相關的知識加入至知識庫。</span><span class="sxs-lookup"><span data-stu-id="a1804-105">You acquire that knowledge by building and maintaining a data quality knowledge base, and adding to it knowledge related to a specific type of data source.</span></span> <span data-ttu-id="a1804-106">知識庫是有關資料的知識儲存機制，可讓您了解資料及維護資料的完整性。</span><span class="sxs-lookup"><span data-stu-id="a1804-106">The knowledge base is a repository of knowledge about your data that enables you to understand your data and maintain its integrity.</span></span>  
  
 <span data-ttu-id="a1804-107">知識庫包含與資料來源相關的資料定義域。</span><span class="sxs-lookup"><span data-stu-id="a1804-107">The knowledge base contains data domains that relate to the data source.</span></span> <span data-ttu-id="a1804-108">對於每一個資料定義域而言，DQKB 都會儲存所有識別的詞彙、拼字錯誤、驗證和商務規則，以及可用來針對資料來源執行資料品質動作的參考資料。</span><span class="sxs-lookup"><span data-stu-id="a1804-108">For each data domain, the DQKB stores all identified terms, spelling errors, validation and business rules, and reference data that can be used to perform data quality actions on the data source.</span></span> <span data-ttu-id="a1804-109">DQS 會使用這項知識來識別不正確或無效的資料，或是執行比對。</span><span class="sxs-lookup"><span data-stu-id="a1804-109">DQS uses this knowledge to identify incorrect or invalid data, or perform matching.</span></span>  
  
 <span data-ttu-id="a1804-110">您可以透過以下電腦輔助或互動式方式，將知識加入至知識庫。</span><span class="sxs-lookup"><span data-stu-id="a1804-110">You can add knowledge to a knowledge base in the following computer-assisted or interactive ways.</span></span>  
  
-   [<span data-ttu-id="a1804-111">執行知識探索</span><span class="sxs-lookup"><span data-stu-id="a1804-111">Perform Knowledge Discovery</span></span>](#Discovery)  
  
-   [<span data-ttu-id="a1804-112">管理定義域中的資料值</span><span class="sxs-lookup"><span data-stu-id="a1804-112">Manage Data Values in a Domain</span></span>](#ManageDomain)  
  
-   [<span data-ttu-id="a1804-113">從 .dqs 檔案匯入知識</span><span class="sxs-lookup"><span data-stu-id="a1804-113">Import Knowledge from a .dqs File</span></span>](#DQSFile)  
  
-   [<span data-ttu-id="a1804-114">從 Excel 檔案匯入知識</span><span class="sxs-lookup"><span data-stu-id="a1804-114">Import Knowledge from an Excel File</span></span>](#Excel)  
  
-   [<span data-ttu-id="a1804-115">將專案中的知識匯入回知識庫</span><span class="sxs-lookup"><span data-stu-id="a1804-115">Import Knowledge from a Project Back into the Knowledge Base</span></span>](#Project)  
  
-   [<span data-ttu-id="a1804-116">使用預設 DQS 知識庫</span><span class="sxs-lookup"><span data-stu-id="a1804-116">Use the Default DQS Knowledge Base</span></span>](#Default)  
  
##  <a name="perform-knowledge-discovery"></a><a name="Discovery"></a><span data-ttu-id="a1804-117">執行知識探索</span><span class="sxs-lookup"><span data-stu-id="a1804-117">Perform Knowledge Discovery</span></span>  
 <span data-ttu-id="a1804-118">知識探索會針對資料品質準則分析資料取樣，然後將它取得的知識加入至知識庫。</span><span class="sxs-lookup"><span data-stu-id="a1804-118">Knowledge discovery analyzes a sample of data for data quality criteria, and then adds the knowledge it has gained to the knowledge base.</span></span> <span data-ttu-id="a1804-119">這是電腦輔助的程序，可識別資料不一致和語法錯誤，並向資料建議變更。</span><span class="sxs-lookup"><span data-stu-id="a1804-119">This is a computer-assisted process that identifies data inconsistencies and syntax errors, and proposes changes to the data.</span></span> <span data-ttu-id="a1804-120">知識探索活動是一個精靈，其中包括您可以互動方式在其上管理定義域值的頁面。</span><span class="sxs-lookup"><span data-stu-id="a1804-120">The knowledge discovery activity is a wizard that includes a page that you can interactively manage domain values on.</span></span>  
  
-   <span data-ttu-id="a1804-121">如需文件集中的詳細資訊，請參閱＜ [Perform Knowledge Discovery](../../2014/data-quality-services/perform-knowledge-discovery.md)＞。</span><span class="sxs-lookup"><span data-stu-id="a1804-121">For more information in documentation, see [Perform Knowledge Discovery](../../2014/data-quality-services/perform-knowledge-discovery.md).</span></span>  
  
-   <span data-ttu-id="a1804-122">如需示範如何執行知識探索的影片，請按一下 [這裡](https://msdn.microsoft.com/sqlserver/hh323825.aspx)。</span><span class="sxs-lookup"><span data-stu-id="a1804-122">For a video demonstrating how to perform knowledge discovery, click [here](https://msdn.microsoft.com/sqlserver/hh323825.aspx).</span></span>  
  
##  <a name="manage-data-values-in-a-domain"></a><a name="ManageDomain"></a><span data-ttu-id="a1804-123">管理定義域中的資料值</span><span class="sxs-lookup"><span data-stu-id="a1804-123">Manage Data Values in a Domain</span></span>  
 <span data-ttu-id="a1804-124">DQS 可讓您以互動方式變更及增加電腦輔助的知識探索活動所產生的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="a1804-124">DQS enables you to interactively change and augment the metadata that is generated by the computer-assisted knowledge discovery activity.</span></span> <span data-ttu-id="a1804-125">您會在 [定義域管理] 活動中執行這項作業，您可以在此活動中將變更套用至特定資料值。</span><span class="sxs-lookup"><span data-stu-id="a1804-125">You do so in the Domain Management activity, where you can apply a change to a specific data value.</span></span>  
  
-   <span data-ttu-id="a1804-126">如需文件集中的詳細資訊，請參閱＜ [Change Domain Values](../../2014/data-quality-services/change-domain-values.md)＞。</span><span class="sxs-lookup"><span data-stu-id="a1804-126">For more information in documentation, see [Change Domain Values](../../2014/data-quality-services/change-domain-values.md).</span></span>  
  
-   <span data-ttu-id="a1804-127">如需示範如何執行定義域管理的影片，請按一下 [這裡](https://msdn.microsoft.com/sqlserver/hh323825.aspx)。</span><span class="sxs-lookup"><span data-stu-id="a1804-127">For a video demonstrating how to perform domain management, click [here](https://msdn.microsoft.com/sqlserver/hh323825.aspx).</span></span> <span data-ttu-id="a1804-128">請注意，在此影片中，您會在知識探索精靈的 [管理定義域值] 頁面中變更定義域值。</span><span class="sxs-lookup"><span data-stu-id="a1804-128">Note that in this video, you change domain values in the Managing Domain Values page of the Knowledge Discovery wizard.</span></span> <span data-ttu-id="a1804-129">您也可以在 [定義域管理] 活動的 [定義域值] 頁面中執行這些步驟。</span><span class="sxs-lookup"><span data-stu-id="a1804-129">You can also perform these steps in the Domain Values Page of the Domain Management activity.</span></span>  
  
##  <a name="import-knowledge-from-a-dqs-file"></a><a name="DQSFile"></a><span data-ttu-id="a1804-130">從 dqs 檔案匯入知識</span><span class="sxs-lookup"><span data-stu-id="a1804-130">Import Knowledge from a .dqs File</span></span>  
 <span data-ttu-id="a1804-131">您可以將 .dqs 資料檔中的定義域匯入現有的知識庫，或者將 .dqs 中的整個知識庫匯入新的知識庫。</span><span class="sxs-lookup"><span data-stu-id="a1804-131">You can import a domain from a .dqs data file into an existing knowledge base, or you can import an entire knowledge base from a .dqs into a new knowledge base.</span></span> <span data-ttu-id="a1804-132">若要這樣做，您必須先將現有的定義域或知識庫匯出至 .dqs 檔案。</span><span class="sxs-lookup"><span data-stu-id="a1804-132">To do so, you first need to export an existing domain or knowledge base to a .dqs file.</span></span> <span data-ttu-id="a1804-133">包含定義域的 .dqs 檔案會包含所有定義域資料；包含知識庫的 .dqs 檔案將包含所有知識庫資訊，包括定義域和比對原則。</span><span class="sxs-lookup"><span data-stu-id="a1804-133">A .dqs file containing a domain includes all domain data; a .dqs file containing a knowledge base will contain all knowledge base information, including domains and the matching policy.</span></span>  
  
-   <span data-ttu-id="a1804-134">如需文件中的詳細資訊，請參閱[從 .dqs 檔案匯入定義域](../../2014/data-quality-services/import-a-domain-from-a-dqs-file.md)或[從 .dqs 檔案匯入知識庫](../../2014/data-quality-services/import-a-knowledge-base-from-a-dqs-file.md)。</span><span class="sxs-lookup"><span data-stu-id="a1804-134">For more information in documentation, see [Import a Domain from a .dqs File](../../2014/data-quality-services/import-a-domain-from-a-dqs-file.md) or [Import a Knowledge Base from a .dqs File](../../2014/data-quality-services/import-a-knowledge-base-from-a-dqs-file.md).</span></span>  
  
##  <a name="import-knowledge-from-an-excel-file"></a><a name="Excel"></a><span data-ttu-id="a1804-135">從 Excel 檔案匯入知識</span><span class="sxs-lookup"><span data-stu-id="a1804-135">Import Knowledge from an Excel File</span></span>  
 <span data-ttu-id="a1804-136">您可以將 Excel 試算表檔案中的定義域值匯入現有的定義域或知識庫。</span><span class="sxs-lookup"><span data-stu-id="a1804-136">You can import domain values from an Excel spreadsheet file into an existing domain or knowledge base.</span></span> <span data-ttu-id="a1804-137">若要這樣做，您必須先使用您想要匯入的定義域值建立 Excel 試算表，並確定 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 電腦上已安裝 Excel，好讓您能夠使用 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]匯入值。</span><span class="sxs-lookup"><span data-stu-id="a1804-137">To do so, you must first create an Excel spreadsheet with the domain values that you want to import, and ensure that Excel is installed on the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] computer for you to be able to import values using [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)].</span></span> <span data-ttu-id="a1804-138">您不能將定義域或知識庫中的定義域值匯出到 Excel 檔案。</span><span class="sxs-lookup"><span data-stu-id="a1804-138">You cannot export domain values from a domain or knowledge base to an Excel file.</span></span>  
  
-   <span data-ttu-id="a1804-139">如需文件中的詳細資訊，請參閱[將 Excel 檔案中的值匯入至定義域](../../2014/data-quality-services/import-values-from-an-excel-file-into-a-domain.md)或[在知識探索中匯入 Excel 檔案中的定義域](../../2014/data-quality-services/import-domains-from-an-excel-file-in-knowledge-discovery.md)。</span><span class="sxs-lookup"><span data-stu-id="a1804-139">For more information in documentation, see [Import Values from an Excel File into a Domain](../../2014/data-quality-services/import-values-from-an-excel-file-into-a-domain.md) or [Import Domains from an Excel File in Knowledge Discovery](../../2014/data-quality-services/import-domains-from-an-excel-file-in-knowledge-discovery.md).</span></span>  
  
##  <a name="import-knowledge-from-a-project-back-into-the-knowledge-base"></a><a name="Project"></a><span data-ttu-id="a1804-140">將專案中的知識匯入回知識庫</span><span class="sxs-lookup"><span data-stu-id="a1804-140">Import Knowledge from a Project Back into the Knowledge Base</span></span>  
 <span data-ttu-id="a1804-141">在您使用知識庫執行清理或比對資料品質專案之後，您可以將清理或比對期間建立的知識匯入回該知識庫。</span><span class="sxs-lookup"><span data-stu-id="a1804-141">After you have run a cleansing or matching data quality project using a knowledge base, you can import knowledge created during cleansing or matching back into that knowledge base.</span></span> <span data-ttu-id="a1804-142">這樣可讓您保存專案期間產生的知識，並持續在知識庫中建立知識。</span><span class="sxs-lookup"><span data-stu-id="a1804-142">This enables you to keep knowledge generated during the project, and to continuously build the knowledge in the knowledge base.</span></span>  
  
-   <span data-ttu-id="a1804-143">如需文件中的詳細資訊，請參閱[將清理專案值匯入定義域中](../../2014/data-quality-services/import-cleansing-project-values-into-a-domain.md)。</span><span class="sxs-lookup"><span data-stu-id="a1804-143">For more information in documentation, see [Import Cleansing Project Values into a Domain](../../2014/data-quality-services/import-cleansing-project-values-into-a-domain.md).</span></span>  
  
##  <a name="use-the-default-dqs-knowledge-base"></a><a name="Default"></a><span data-ttu-id="a1804-144">使用預設的 DQS 知識庫</span><span class="sxs-lookup"><span data-stu-id="a1804-144">Use the Default DQS Knowledge Base</span></span>  
 <span data-ttu-id="a1804-145">DQS 隨附在預先建立的知識庫 (稱為 DQS 資料) 中，其中包含美國公司和地址資料。</span><span class="sxs-lookup"><span data-stu-id="a1804-145">DQS ships with a pre-built knowledge base called DQS Data that contains domains for United States company and address data.</span></span> <span data-ttu-id="a1804-146">這個知識庫可用來快速啟動專案，不需要建立新的知識庫。</span><span class="sxs-lookup"><span data-stu-id="a1804-146">This knowledge base can be used to quickly start a project without creating a new knowledge base.</span></span> <span data-ttu-id="a1804-147">「DQS 資料」知識庫是唯讀的，但是資料監管可將它做為基礎建立新的知識庫。</span><span class="sxs-lookup"><span data-stu-id="a1804-147">The DQS Data knowledge base is read-only, but the data steward can create a new knowledge base based on it.</span></span>  
  
-   <span data-ttu-id="a1804-148">如需文件集中的詳細資訊，請參閱＜ [Using the DQS Default Knowledge Base](../../2014/data-quality-services/using-the-dqs-default-knowledge-base.md)＞。</span><span class="sxs-lookup"><span data-stu-id="a1804-148">For more information in documentation, see [Using the DQS Default Knowledge Base](../../2014/data-quality-services/using-the-dqs-default-knowledge-base.md).</span></span>  
  
  
