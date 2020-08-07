---
title: 指定資料表複製或查詢 (SQL Server 匯入和匯出精靈) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.impexpwizard.specifytablecopyorquery.f1
ms.assetid: 08aa7158-40e6-4ef3-84d3-1265a8ba194c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a3d1eafb57475ed6a0f9fb20894fcc9718d1f0c2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597917"
---
# <a name="specify-table-copy-or-query-sql-server-import-and-export-wizard"></a><span data-ttu-id="a260a-102">指定資料表複製或查詢 (SQL Server 匯入和匯出精靈)</span><span class="sxs-lookup"><span data-stu-id="a260a-102">Specify Table Copy or Query (SQL Server Import and Export Wizard)</span></span>
  <span data-ttu-id="a260a-103">使用 [**指定資料表複製或查詢**] 頁面，即可指定如何複製資料。</span><span class="sxs-lookup"><span data-stu-id="a260a-103">Use the **Specify Table Copy or Query** page to specify how to copy data.</span></span> <span data-ttu-id="a260a-104">您可以使用圖形介面來選取要複製的現有資料庫物件，或使用 Transact-SQL 來建立更複雜的查詢。</span><span class="sxs-lookup"><span data-stu-id="a260a-104">You can use a graphical interface to select the existing database objects you want to copy, or you can use Transact-SQL to create a more complex query.</span></span>  
  
 <span data-ttu-id="a260a-105">若要深入瞭解此嚮導，請參閱[SQL Server 匯入和匯出嚮導](import-and-export-data-with-the-sql-server-import-and-export-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="a260a-105">To learn more about this wizard, see [SQL Server Import and Export Wizard](import-and-export-data-with-the-sql-server-import-and-export-wizard.md).</span></span> <span data-ttu-id="a260a-106">若要瞭解用來啟動精靈的選項，以及成功執行嚮導所需的許可權，請參閱[執行 SQL Server 匯入和匯出嚮導](start-the-sql-server-import-and-export-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="a260a-106">To learn about the options for starting the wizard, as well as the permissions required to run the wizard successfully, see [Run the SQL Server Import and Export Wizard](start-the-sql-server-import-and-export-wizard.md).</span></span>  
  
 <span data-ttu-id="a260a-107">「SQL Server 匯入和匯出精靈」的用途在於將資料從來源複製到目的地。</span><span class="sxs-lookup"><span data-stu-id="a260a-107">The purpose of the SQL Server Import and Export Wizard is to copy data from a source to a destination.</span></span> <span data-ttu-id="a260a-108">這個精靈也可以為您建立目的地資料庫和目的地資料表。</span><span class="sxs-lookup"><span data-stu-id="a260a-108">The wizard can also create a destination database and destination tables for you.</span></span> <span data-ttu-id="a260a-109">不過，如果您必須複製多個資料庫或資料表，或複製其他種類的資料庫物件，則應該改用「複製資料庫精靈」。</span><span class="sxs-lookup"><span data-stu-id="a260a-109">However, if you have to copy multiple databases or tables, or other kinds of database objects, you should use the Copy Database Wizard instead.</span></span> <span data-ttu-id="a260a-110">如需詳細資訊，請參閱 [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="a260a-110">For more information, see [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="a260a-111">選項。</span><span class="sxs-lookup"><span data-stu-id="a260a-111">Options</span></span>  
 <span data-ttu-id="a260a-112">**從一個或多個資料表或檢視表複製資料**</span><span class="sxs-lookup"><span data-stu-id="a260a-112">**Copy data from one or more tables or views**</span></span>  
 <span data-ttu-id="a260a-113">使用 [**選取來源資料表和流覽**器] 對話方塊，將欄位從選取的來源資料表和視圖複製到指定的目的地或目的地。</span><span class="sxs-lookup"><span data-stu-id="a260a-113">Copy fields from selected source tables and views to the specified destination or destinations by using the **Select Source Tables and Views** dialog box.</span></span> <span data-ttu-id="a260a-114">如果您要複製來源的所有資料，但不要篩選或排序記錄，請使用此選項。</span><span class="sxs-lookup"><span data-stu-id="a260a-114">Use this option if you want to copy all data in the source without filtering or ordering records.</span></span>  
  
 <span data-ttu-id="a260a-115">當您使用 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 資料提供者來連接至資料來源時，可能會無法使用 **[從一或多個資料表或檢視表複製資料]** 選項。</span><span class="sxs-lookup"><span data-stu-id="a260a-115">When you use a [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] data provider to connect to your data source, the **Copy data from one or more tables or views** option might not be available.</span></span> <span data-ttu-id="a260a-116">這個選項僅適用於在 ProviderDescriptors.xml 檔案中具有 ProviderDescription 區段的提供者。</span><span class="sxs-lookup"><span data-stu-id="a260a-116">This option is available only for those providers that have a ProviderDescription section in the ProviderDescriptors.xml file.</span></span> <span data-ttu-id="a260a-117">每個 ProviderDescription 區段會包含從對應提供者擷取中繼資料所需的資訊。</span><span class="sxs-lookup"><span data-stu-id="a260a-117">Each ProviderDescription section contains the information that is required to retrieve metadata from the corresponding provider.</span></span> <span data-ttu-id="a260a-118">根據預設，只有下列提供者的 ProviderDescriptors.xml 檔案包含 ProviderDescription 區段：</span><span class="sxs-lookup"><span data-stu-id="a260a-118">By default, the ProviderDescriptors.xml file contains a ProviderDescription section for only the following providers:</span></span>  
  
-   <span data-ttu-id="a260a-119">System.Data.SqlClient</span><span class="sxs-lookup"><span data-stu-id="a260a-119">System.Data.SqlClient</span></span>  
  
-   <span data-ttu-id="a260a-120">System.Data.OracleClient</span><span class="sxs-lookup"><span data-stu-id="a260a-120">System.Data.OracleClient</span></span>  
  
-   <span data-ttu-id="a260a-121">System.Data.OleDb</span><span class="sxs-lookup"><span data-stu-id="a260a-121">System.Data.OleDb</span></span>  
  
-   <span data-ttu-id="a260a-122">System.Data.Odbc</span><span class="sxs-lookup"><span data-stu-id="a260a-122">System.Data.Odbc</span></span>  
  
 <span data-ttu-id="a260a-123">若要讓其他提供者可以使用 [**從一個或多個資料表或視圖來複製資料]** 選項，協力廠商可將自己的 ProviderDescriptor 區段新增至 ProviderDescriptors.xml 檔案。</span><span class="sxs-lookup"><span data-stu-id="a260a-123">To make the **Copy data from one or more tables or views** option available for additional providers, third parties can add their own ProviderDescriptor sections to the ProviderDescriptors.xml file.</span></span> <span data-ttu-id="a260a-124">根據預設，此檔案位於 \<*drive*> ： \Program FILES\MICROSOFT SQL server\100\dts\providerdescriptors。</span><span class="sxs-lookup"><span data-stu-id="a260a-124">By default, this file is in \<*drive*>:\Program Files\Microsoft SQL Server\100\DTS\ProviderDescriptors.</span></span> <span data-ttu-id="a260a-125">若要檢閱 ProviderDescriptor 區段的需求，請參閱 ProviderDescriptors.xsd 結構描述檔案 (預設與 ProviderDescriptors.xml 檔案位於相同的資料夾中)。</span><span class="sxs-lookup"><span data-stu-id="a260a-125">To review the requirements for the ProviderDescriptor section, see the ProviderDescriptors.xsd schema file that is, by default, in the same folder as the ProviderDescriptors.xml file.</span></span>  
  
 <span data-ttu-id="a260a-126">**撰寫查詢來指定要傳送的資料**</span><span class="sxs-lookup"><span data-stu-id="a260a-126">**Write a query to specify the data to transfer**</span></span>  
 <span data-ttu-id="a260a-127">使用 [**提供來源查詢**] 對話方塊來建立 SQL 語句，以取得資料列。</span><span class="sxs-lookup"><span data-stu-id="a260a-127">Build SQL statements to retrieve rows by using the **Provide a Source Query** dialog box.</span></span> <span data-ttu-id="a260a-128">如果您要在進行複製作業時修改或限制來源資料，請使用此選項。</span><span class="sxs-lookup"><span data-stu-id="a260a-128">Use this option if you want to modify or restrict the source data during the copy operation.</span></span> <span data-ttu-id="a260a-129">只有符合選取準則的資料列可供複製。</span><span class="sxs-lookup"><span data-stu-id="a260a-129">Only the rows matching the selection criteria are available for copying.</span></span>  
  
  
