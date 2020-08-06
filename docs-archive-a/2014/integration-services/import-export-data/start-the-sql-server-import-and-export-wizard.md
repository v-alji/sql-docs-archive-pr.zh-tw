---
title: 執行 SQL Server 匯入和匯出嚮導 |Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Import and Export Wizard
- starting SQL Server Import and Export Wizard
- Import and Export Wizard
- starting Import and Export Wizard
ms.assetid: 5fc4f6d1-1f6f-444e-9aeb-827f85e1c405
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 008c541b1f1a295057b0ee7cc384982627b9689a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597918"
---
# <a name="run-the-sql-server-import-and-export-wizard"></a><span data-ttu-id="e2a1e-102">執行 SQL Server 匯入和匯出精靈</span><span class="sxs-lookup"><span data-stu-id="e2a1e-102">Run the SQL Server Import and Export Wizard</span></span>
  <span data-ttu-id="e2a1e-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 匯入和匯出精靈提供最簡單的方法，讓您在資料來源之間複製資料以及建構基本封裝。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Import and Export Wizard provides the simplest method of copying data between data sources and of constructing basic packages.</span></span> <span data-ttu-id="e2a1e-104">如需有關 wizard 的詳細資訊，請參閱[SQL Server 匯入和匯出 wizard](import-and-export-data-with-the-sql-server-import-and-export-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-104">For more information about the wizard, see [SQL Server Import and Export Wizard](import-and-export-data-with-the-sql-server-import-and-export-wizard.md).</span></span>  
  
 <span data-ttu-id="e2a1e-105">如需示範如何使用 SQL Server 匯入和匯出 Wizard 建立封裝，將資料從 SQL Server 資料庫匯出至 Microsoft Excel 試算表的影片，請參閱[將 SQL Server 資料匯出至 Excel (SQL Server video) ](https://go.microsoft.com/fwlink/?LinkId=131024)。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-105">For a video that demonstrates how to use the SQL Server Import and Export Wizard to create a package that exports data from a SQL Server database to a Microsoft Excel spreadsheet, see [Exporting SQL Server Data to Excel (SQL Server Video)](https://go.microsoft.com/fwlink/?LinkId=131024).</span></span>  
  
### <a name="to-start-the-sql-server-import-and-export-wizard"></a><span data-ttu-id="e2a1e-106">若要啟動 SQL Server 匯入和匯出精靈</span><span class="sxs-lookup"><span data-stu-id="e2a1e-106">To start the SQL Server Import and Export Wizard</span></span>  
  
-   <span data-ttu-id="e2a1e-107">在 [**開始**] 功能表上，依序指向 [**所有程式**]、[**Microsoft SQL Server** ]，然後按一下 [匯**入和匯出資料**]。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-107">On the **Start** menu, point to **All Programs**, point to**Microsoft SQL Server** , and then click **Import and Export Data**.</span></span>  
  
     <span data-ttu-id="e2a1e-108">-或-</span><span class="sxs-lookup"><span data-stu-id="e2a1e-108">-or-</span></span>  
  
     <span data-ttu-id="e2a1e-109">在中 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] ，以滑鼠右鍵按一下 [ **SSIS 封裝**] 資料夾，然後按一下 [ **SSISImport 和匯出嚮導]**。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-109">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], right-click the **SSIS Packages** folder, and then click **SSISImport and Export Wizard**.</span></span>  
  
     <span data-ttu-id="e2a1e-110">-或-</span><span class="sxs-lookup"><span data-stu-id="e2a1e-110">-or-</span></span>  
  
     <span data-ttu-id="e2a1e-111">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 的 [**專案**] 功能表上，按一下 [ **SSISImport 和匯出嚮導]**。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-111">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], on the **Project** menu, click **SSISImport and Export Wizard**.</span></span>  
  
     <span data-ttu-id="e2a1e-112">-或-</span><span class="sxs-lookup"><span data-stu-id="e2a1e-112">-or-</span></span>  
  
     <span data-ttu-id="e2a1e-113">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 伺服器類型，展開 [資料庫]，以滑鼠右鍵按一下資料庫， **Tasks**指向 [工作]，然後按一下 [匯**入資料**] 或 [**匯出資料**]。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-113">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)] server type, expand Databases, right-click a database, point to **Tasks**, and then click **Import Data** or **Export data**.</span></span>  
  
     <span data-ttu-id="e2a1e-114">-或-</span><span class="sxs-lookup"><span data-stu-id="e2a1e-114">-or-</span></span>  
  
     <span data-ttu-id="e2a1e-115">在命令提示字元視窗中，執行 DTSWizard.exe (位於 C:\Program Files\Microsoft SQL Server\100\DTS\Binn)。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-115">In a command prompt window, run DTSWizard.exe, located in C:\Program Files\Microsoft SQL Server\100\DTS\Binn.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e2a1e-116">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 會在 64 位元電腦上安裝 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 匯入和匯出精靈 (DTSWizard.exe) 的 64 位元版本。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-116">On a 64-bit computer, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] installs the 64-bit version of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Import and Export Wizard (DTSWizard.exe).</span></span> <span data-ttu-id="e2a1e-117">不過，有些資料來源 (例如，Access 或 Excel) 只有 32 位元提供者。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-117">However, some data sources, such as Access or Excel, only have a 32-bit provider available.</span></span> <span data-ttu-id="e2a1e-118">若要使用這些資料來源，您可能必須安裝並執行此精靈的 32 位元版本。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-118">To work with these data sources, you might have to install and run the 32-bit version of the wizard.</span></span> <span data-ttu-id="e2a1e-119">若要安裝此精靈的 32 位元版本，您必須在安裝期間選取用戶端工具或 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-119">To install the 32-bit version of the wizard, select either Client Tools or [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] during setup.</span></span>  
  
### <a name="to-import-or-export-data-by-using-the-sql-server-import-and-export-wizard"></a><span data-ttu-id="e2a1e-120">使用 SQL Server 匯入和匯出精靈來匯入或匯出資料</span><span class="sxs-lookup"><span data-stu-id="e2a1e-120">To import or export data by using the SQL Server Import and Export Wizard</span></span>  
  
1.  <span data-ttu-id="e2a1e-121">啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 匯入和匯出精靈。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-121">Start the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Import and Export Wizard.</span></span>  
  
2.  <span data-ttu-id="e2a1e-122">在對應的精靈頁面上，選取資料來源和資料目的地。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-122">On the corresponding wizard pages, select a data source and a data destination.</span></span>  
  
     <span data-ttu-id="e2a1e-123">可用的資料來源包括 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 資料提供者、OLE DB 提供者、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 提供者、[!INCLUDE[vstecado](../../includes/vstecado-md.md)] 提供者、Microsoft Office Excel、Microsoft Office Access 和一般檔案來源。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-123">The available data sources include [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] data providers, OLE DB providers, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client providers, [!INCLUDE[vstecado](../../includes/vstecado-md.md)] providers, Microsoft Office Excel, Microsoft Office Access, and the Flat File source.</span></span> <span data-ttu-id="e2a1e-124">視來源而定，您可以設定驗證模式、伺服器名稱、資料庫名稱和檔案格式等選項。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-124">Depending on the source, you set options such as the authentication mode, server name, database name, and file format.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e2a1e-125">[!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB Provider for Oracle 不支援 Oracle BLOB、CLOB、NCLOB、BFILE 和 UROWID 等資料類型。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-125">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB Provider for Oracle does not support the Oracle BLOB, CLOB, NCLOB, BFILE, and UROWID data types.</span></span> <span data-ttu-id="e2a1e-126">因此，OLE DB 來源不能從包含這些資料類型之資料行的資料表中擷取資料。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-126">Therefore, the OLE DB source cannot extract data from tables that contain columns with these data types.</span></span>  
  
     <span data-ttu-id="e2a1e-127">可用的資料目的地包括 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 資料提供者、OLE DB 提供者、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client、Excel、Access 和一般檔案目的地。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-127">The available data destinations include [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] data providers, OLE DB providers, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client, Excel, Access, and the Flat File destination.</span></span>  
  
3.  <span data-ttu-id="e2a1e-128">設定選取之目的地類型的選項。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-128">Set the options for the type of destination that you selected.</span></span>  
  
     <span data-ttu-id="e2a1e-129">如果目的地為 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫，您可以指定下列項目：</span><span class="sxs-lookup"><span data-stu-id="e2a1e-129">If the destination is a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database you can specify the following:</span></span>  
  
    -   <span data-ttu-id="e2a1e-130">指示是否要新建資料庫並設定資料庫屬性。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-130">Indicate whether to create a new database and set the database properties.</span></span> <span data-ttu-id="e2a1e-131">下列屬性無法進行設定，精靈將使用指定的預設值：</span><span class="sxs-lookup"><span data-stu-id="e2a1e-131">The following properties cannot be configured and the wizard uses the specified default values:</span></span>  
  
        |<span data-ttu-id="e2a1e-132">屬性</span><span class="sxs-lookup"><span data-stu-id="e2a1e-132">Property</span></span>|<span data-ttu-id="e2a1e-133">值</span><span class="sxs-lookup"><span data-stu-id="e2a1e-133">Value</span></span>|  
        |--------------|-----------|  
        |<span data-ttu-id="e2a1e-134">定序</span><span class="sxs-lookup"><span data-stu-id="e2a1e-134">Collation</span></span>|<span data-ttu-id="e2a1e-135">Latin1_General_CS_AS_KS_WS</span><span class="sxs-lookup"><span data-stu-id="e2a1e-135">Latin1_General_CS_AS_KS_WS</span></span>|  
        |<span data-ttu-id="e2a1e-136">復原模式</span><span class="sxs-lookup"><span data-stu-id="e2a1e-136">Recovery model</span></span>|<span data-ttu-id="e2a1e-137">完整</span><span class="sxs-lookup"><span data-stu-id="e2a1e-137">Full</span></span>|  
        |<span data-ttu-id="e2a1e-138">使用全文檢索索引</span><span class="sxs-lookup"><span data-stu-id="e2a1e-138">Use full-text indexing</span></span>|<span data-ttu-id="e2a1e-139">是</span><span class="sxs-lookup"><span data-stu-id="e2a1e-139">True</span></span>|  
  
    -   <span data-ttu-id="e2a1e-140">選擇是要從資料表或檢視表複製資料，還是複製查詢結果。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-140">Select whether to copy data from tables or views, or to copy query results.</span></span>  
  
         <span data-ttu-id="e2a1e-141">若要查詢來源資料並複製結果，可以建構 Transact-SQL 查詢。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-141">If you want to query the source data and copy the results, you can construct a Transact-SQL query.</span></span> <span data-ttu-id="e2a1e-142">您可以手動輸入 Transact-SQL 查詢，或使用儲存到檔案的查詢。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-142">You can enter the Transact-SQL query manually or use a query saved to a file.</span></span> <span data-ttu-id="e2a1e-143">此精靈包含用來尋找檔案的瀏覽功能，還可在您選取檔案時自動開啟檔案，並將其內容貼到精靈頁面。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-143">The wizard includes a browse feature for locating the file, and the wizard automatically opens the file and pastes its content into the wizard page when you select the file.</span></span>  
  
         <span data-ttu-id="e2a1e-144">如果來源為 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 提供者，您還可以使用複製查詢結果的選項，提供 DBCommand 字串當做查詢。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-144">If the source is an [!INCLUDE[vstecado](../../includes/vstecado-md.md)] provider you can also use the option to copy query results, providing the DBCommand string as the query.</span></span>  
  
         <span data-ttu-id="e2a1e-145">如果來源資料為檢視，則「[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 匯入和匯出精靈」會自動將檢視轉換為目的資料表。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-145">If the source data is a view, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Import and Export Wizard automatically converts the view to a table in the destination.</span></span>  
  
    -   <span data-ttu-id="e2a1e-146">指示是否卸除並重新建立目的地資料表，以及是否啟用識別插入。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-146">Indicate whether the destination table is dropped and then re-created, and whether to enable identity inserts.</span></span>  
  
    -   <span data-ttu-id="e2a1e-147">指示是要刪除資料列，還是在現有的目的地資料表內附加資料列。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-147">Indicate whether to delete rows or append rows in an existing destination table.</span></span> <span data-ttu-id="e2a1e-148">如果資料表不存在，「[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 匯入和匯出精靈」會自動予以建立。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-148">If the table does not exist, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Import and Export Wizard automatically creates it.</span></span>  
  
     <span data-ttu-id="e2a1e-149">如果目的地為一般檔案目的地，您可以指定下列項目：</span><span class="sxs-lookup"><span data-stu-id="e2a1e-149">If the destination is a Flat File destination you can specify the following:</span></span>  
  
    -   <span data-ttu-id="e2a1e-150">指定目的地檔案中的資料列分隔符號。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-150">Specify the row delimiter in the destination file.</span></span>  
  
    -   <span data-ttu-id="e2a1e-151">指定目的地檔案中的資料行分隔符號。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-151">Specify the column delimiter in the destination file.</span></span>  
  
4.  <span data-ttu-id="e2a1e-152">(選擇性) 選取一個資料表並變更來源和目的地資料行之間的對應，或變更目的地資料行的中繼資料：</span><span class="sxs-lookup"><span data-stu-id="e2a1e-152">(Optional) Select one table and change the mappings between source and destination columns, or change the metadata of destination columns:</span></span>  
  
    -   <span data-ttu-id="e2a1e-153">將來源資料行對應到不同的目的地資料行。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-153">Map source columns to different destination columns.</span></span>  
  
    -   <span data-ttu-id="e2a1e-154">變更目的地資料行中的資料類型。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-154">Change the data type in the destination column.</span></span>  
  
    -   <span data-ttu-id="e2a1e-155">設定具有字元資料類型之資料行的長度。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-155">Set the length of columns with character data types.</span></span>  
  
    -   <span data-ttu-id="e2a1e-156">設定具有數值資料類型之資料行的有效位數和小數位數。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-156">Set the precision and scale of columns with numeric data types.</span></span>  
  
    -   <span data-ttu-id="e2a1e-157">指定資料行是否可包含 Null 值。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-157">Specify whether the column can contain null values.</span></span>  
  
5.  <span data-ttu-id="e2a1e-158">(選擇性) 選取多個資料表，並更新套用至這些資料表的中繼資料和選項：</span><span class="sxs-lookup"><span data-stu-id="e2a1e-158">(Optional) Select multiple tables, and update the metadata and options to apply to those tables:</span></span>  
  
    -   <span data-ttu-id="e2a1e-159">選取現有的目的地結構描述，或提供要指派資料表的新結構描述。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-159">Select an existing destination schema or provide a new schema to which to assign tables.</span></span>  
  
    -   <span data-ttu-id="e2a1e-160">指定目的地資料表中是否啟用識別插入。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-160">Specify whether to enable identity inserts in destination tables.</span></span>  
  
    -   <span data-ttu-id="e2a1e-161">指定是否要卸除目的地資料表，然後重建。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-161">Specify whether to drop and re-create destination tables.</span></span>  
  
    -   <span data-ttu-id="e2a1e-162">指定是否要截斷現有的目的地資料表。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-162">Specify whether to truncate existing destination tables.</span></span>  
  
6.  <span data-ttu-id="e2a1e-163">儲存並執行封裝。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-163">Save and run a package.</span></span>  
  
     <span data-ttu-id="e2a1e-164">如果從 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 或命令提示字元啟動精靈，此封裝便可立即執行。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-164">If the wizard is started from [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or the command prompt, the package can run immediately.</span></span> <span data-ttu-id="e2a1e-165">您可以選擇性地將封裝儲存到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **msdb**資料庫或檔案系統。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-165">You can optionally save the package to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **msdb** database or to the file system.</span></span> <span data-ttu-id="e2a1e-166">如需**msdb**資料庫的詳細資訊，請參閱[套件管理 &#40;SSIS 服務&#41;](../service/package-management-ssis-service.md)。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-166">For more information about the **msdb** database, see [Package Management &#40;SSIS Service&#41;](../service/package-management-ssis-service.md).</span></span>  
  
     <span data-ttu-id="e2a1e-167">當您儲存封裝時，可以設定封裝保護等級，而如果保護等級使用密碼，請提供密碼。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-167">When you save the package you can set the package protection level, and if the protection level uses a password, provide the password.</span></span> <span data-ttu-id="e2a1e-168">如需封裝保護層級的詳細資訊，請參閱[封裝中的敏感性資料存取控制](../security/access-control-for-sensitive-data-in-packages.md)。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-168">For more information about package protection levels, see [Access Control for Sensitive Data in Packages](../security/access-control-for-sensitive-data-in-packages.md).</span></span>  
  
     <span data-ttu-id="e2a1e-169">如果從 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 中的 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 專案啟動精靈，則無法從精靈執行封裝，</span><span class="sxs-lookup"><span data-stu-id="e2a1e-169">If the wizard is started from an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], you cannot run the package from the wizard.</span></span> <span data-ttu-id="e2a1e-170">而是加入到啟動精靈的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-170">Instead, the package is added to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project from which you started the wizard.</span></span> <span data-ttu-id="e2a1e-171">然後，您可以在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 中執行封裝。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-171">You can then run the package in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e2a1e-172">在 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] 中，無法使用儲存此精靈所建立之封裝的選項。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-172">In [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)], the option to save the package created by the wizard is not available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2a1e-173">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e2a1e-173">See Also</span></span>  
 <span data-ttu-id="e2a1e-174">[SQL Server 匯入和匯出嚮導](import-and-export-data-with-the-sql-server-import-and-export-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="e2a1e-174">[SQL Server Import and Export Wizard](import-and-export-data-with-the-sql-server-import-and-export-wizard.md) </span></span>  
 [<span data-ttu-id="e2a1e-175">在 SQL Server Data Tools 中建立套件</span><span class="sxs-lookup"><span data-stu-id="e2a1e-175">Create Packages in SQL Server Data Tools</span></span>](../create-packages-in-sql-server-data-tools.md)  
  
  
