---
title: 選取來源資料表和檢視 (SQL Server 匯入和匯出精靈) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.impexpwizard.selectsourcetablesandviews.f1
ms.assetid: f60e1a19-2ea6-403c-89ab-3e60ac533ea0
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e18f9f34db7965033d4e1e62964060a26404a45e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597920"
---
# <a name="select-source-tables-and-views-sql-server-import-and-export-wizard"></a><span data-ttu-id="950af-102">選取來源資料表和檢視 (SQL Server 匯入和匯出精靈)</span><span class="sxs-lookup"><span data-stu-id="950af-102">Select Source Tables and Views (SQL Server Import and Export Wizard)</span></span>
  <span data-ttu-id="950af-103">使用 [**選取來源資料表和資料檢視**] 頁面，即可指定要從資料來源複製到目的地的資料表和 views。</span><span class="sxs-lookup"><span data-stu-id="950af-103">Use the **Select Source Tables and Views** page to specify the tables and views to be copied from the data source to the destination.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="950af-104">當您選取 [資料表複製] 選項時，並不必複製資料表中的所有資料行。</span><span class="sxs-lookup"><span data-stu-id="950af-104">You do not have to copy all the columns in a table when you select the Table Copy option.</span></span> <span data-ttu-id="950af-105">選取目的地資料表之後，請按一下 [編輯對應] 以顯示 [資料**行**對應] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="950af-105">After selecting a destination table, click Edit Mappings to display the **Column Mappings** dialog box.</span></span> <span data-ttu-id="950af-106">**\<ignore>** 針對您要略過的資料行，在 [資料**行**對應] 對話方塊的 [**目的地**] 資料行中選取。</span><span class="sxs-lookup"><span data-stu-id="950af-106">Select **\<ignore>** in the **Destination** column of the **Column Mappings** dialog box for columns that you want to skip.</span></span>  
  
 <span data-ttu-id="950af-107">若要深入瞭解此嚮導，請參閱[SQL Server 匯入和匯出嚮導](import-and-export-data-with-the-sql-server-import-and-export-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="950af-107">To learn more about this wizard, see [SQL Server Import and Export Wizard](import-and-export-data-with-the-sql-server-import-and-export-wizard.md).</span></span> <span data-ttu-id="950af-108">若要瞭解啟動精靈的選項，以及成功執行嚮導所需的許可權，請參閱[執行 SQL Server 匯入和匯出嚮導](start-the-sql-server-import-and-export-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="950af-108">To learn about the options for starting the wizard, and about the permissions required to run the wizard successfully, see [Run the SQL Server Import and Export Wizard](start-the-sql-server-import-and-export-wizard.md).</span></span>  
  
 <span data-ttu-id="950af-109">「SQL Server 匯入和匯出精靈」的用途在於將資料從來源複製到目的地。</span><span class="sxs-lookup"><span data-stu-id="950af-109">The purpose of the SQL Server Import and Export Wizard is to copy data from a source to a destination.</span></span> <span data-ttu-id="950af-110">這個精靈也可以為您建立目的地資料庫和目的地資料表。</span><span class="sxs-lookup"><span data-stu-id="950af-110">The wizard can also create a destination database and destination tables for you.</span></span> <span data-ttu-id="950af-111">不過，如果您必須複製多個資料庫或資料表，或複製其他種類的資料庫物件，則應該改用「複製資料庫精靈」。</span><span class="sxs-lookup"><span data-stu-id="950af-111">However, if you have to copy multiple databases or tables, or other kinds of database objects, you should use the Copy Database Wizard instead.</span></span> <span data-ttu-id="950af-112">如需詳細資訊，請參閱 [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="950af-112">For more information, see [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="950af-113">選項。</span><span class="sxs-lookup"><span data-stu-id="950af-113">Options</span></span>  
  
### <a name="tables-and-views-list"></a><span data-ttu-id="950af-114">資料表和檢視表清單</span><span class="sxs-lookup"><span data-stu-id="950af-114">Tables and views List</span></span>  
 <span data-ttu-id="950af-115">**Source**</span><span class="sxs-lookup"><span data-stu-id="950af-115">**Source**</span></span>  
 <span data-ttu-id="950af-116">使用這些核取方塊，從可用的資料表和檢視清單中選取要複製到目的地的項目。</span><span class="sxs-lookup"><span data-stu-id="950af-116">Using the check boxes, select from the list of available tables and views to copy to the destination.</span></span> <span data-ttu-id="950af-117">如果您選取來源資料表或檢視，並且未執行其他任何動作，就會複製來自來源的結構描述和資料，而不會進行變更。</span><span class="sxs-lookup"><span data-stu-id="950af-117">If you select a source table or view and perform no other action, the schema and data from the source are copied without changes.</span></span>  
  
 <span data-ttu-id="950af-118">**目的地**</span><span class="sxs-lookup"><span data-stu-id="950af-118">**Destination**</span></span>  
 <span data-ttu-id="950af-119">從每個來源資料表的清單中選取目的地資料表。</span><span class="sxs-lookup"><span data-stu-id="950af-119">Select a destination table from the list for each source table.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="950af-120">如果此時在精靈中暫停，使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 或其他工具在 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 中建立目的地資料表，並不能立刻在可用的目的地資料表清單中看到新的資料表。</span><span class="sxs-lookup"><span data-stu-id="950af-120">If you pause at this point in the wizard to create a destination table in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by using [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] or another tool, the new table is not immediately visible in the list of available destination tables.</span></span> <span data-ttu-id="950af-121">若要重新整理目的地資料表清單，請將兩個頁面移至 [**選擇目的地**] 頁面上，再次選取目的地資料庫，然後再次前進到 [**選取來源資料表和資料檢視]**。</span><span class="sxs-lookup"><span data-stu-id="950af-121">To refresh the list of destination tables, step back two pages to the **Choose a Destination** page, re-select the destination database, then step forward again to the **Select Source Tables and Views**.</span></span>  
  
### <a name="other-options"></a><span data-ttu-id="950af-122">其他選項</span><span class="sxs-lookup"><span data-stu-id="950af-122">Other Options</span></span>  
 <span data-ttu-id="950af-123">**編輯對應**</span><span class="sxs-lookup"><span data-stu-id="950af-123">**Edit mappings**</span></span>  
 <span data-ttu-id="950af-124">使用 [資料**行**對應] 對話方塊，即可指定要接收來源資料的目的地資料行。</span><span class="sxs-lookup"><span data-stu-id="950af-124">Use the **Column Mappings** dialog box to specify destination columns to receive the source data.</span></span> <span data-ttu-id="950af-125">您可以 \<ignore> 針對想要略過的資料行，在 [資料**行**對應] 對話方塊的 [**目的地**] 資料行中選取，只複製資料行的子集。</span><span class="sxs-lookup"><span data-stu-id="950af-125">You can copy only a subset of columns by selecting \<ignore> in the **Destination** column of the **Column Mappings** dialog box for columns that you want to skip.</span></span>  
  
 <span data-ttu-id="950af-126">**預覽**</span><span class="sxs-lookup"><span data-stu-id="950af-126">**Preview**</span></span>  
 <span data-ttu-id="950af-127">在執行匯入或匯出之前，預覽 [**預覽資料**] 對話方塊中的來源資料以進行驗證。</span><span class="sxs-lookup"><span data-stu-id="950af-127">Preview source data in the **Preview Data** dialog box to verify it before performing the import or export.</span></span> <span data-ttu-id="950af-128">[**預覽資料**] 對話方塊會顯示多達200個數據列。</span><span class="sxs-lookup"><span data-stu-id="950af-128">The **Preview Data** dialog box displays up to 200 rows of data.</span></span>  
  
 <span data-ttu-id="950af-129">預覽資料之後，您可能會想要變更已針對資料來源和目的地選取的選項。</span><span class="sxs-lookup"><span data-stu-id="950af-129">After previewing the data, you might want to change the options that you have selected for the data source and destination.</span></span> <span data-ttu-id="950af-130">若要進行這些變更，請在 [選取來源資料表和檢視]\*\*\*\* 頁面上，按 [上一步]\*\*\*\* 返回先前的頁面，如此您就可以在其中變更選項。</span><span class="sxs-lookup"><span data-stu-id="950af-130">To make these changes, on the **Select Source Tables and Views** page, click **Back** to return to previous pages where you can change your selections.</span></span>  
  
  
