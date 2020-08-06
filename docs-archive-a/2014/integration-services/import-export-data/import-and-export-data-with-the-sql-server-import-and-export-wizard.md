---
title: SQL Server 匯入和匯出嚮導 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- exporting data
- mapping files [Integration Services]
- SQL Server Import and Export Wizard
- SSIS packages, creating
- packages [Integration Services], copying
- Integration Services packages, creating
- packages [Integration Services], creating
- SQL Server Integration Services packages, creating
- Import and Export Wizard
- copying data [Integration Services]
- importing data, SSIS packages
- sources [Integration Services], copying data
ms.assetid: c0e4d867-b2a9-4b2a-844b-2fe45be88f81
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1c175bd005a9f3b9d55467abbbb278e13dafc521
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597932"
---
# <a name="sql-server-import-and-export-wizard"></a><span data-ttu-id="80bb1-102">SQL Server 匯入和匯出精靈</span><span class="sxs-lookup"><span data-stu-id="80bb1-102">SQL Server Import and Export Wizard</span></span>
  <span data-ttu-id="80bb1-103">[匯 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 入和匯出嚮導] 提供最簡單的方法，讓您建立可 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 將資料從來源複製到目的地的封裝。</span><span class="sxs-lookup"><span data-stu-id="80bb1-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Import and Export Wizard offers the simplest method to create a [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that copies data from a source to a destination.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="80bb1-104">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 會在 64 位元電腦上安裝 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 匯入和匯出精靈 (DTSWizard.exe) 的 64 位元版本。</span><span class="sxs-lookup"><span data-stu-id="80bb1-104">On a 64-bit computer, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] installs the 64-bit version of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Import and Export Wizard (DTSWizard.exe).</span></span> <span data-ttu-id="80bb1-105">不過，有些資料來源 (例如，Access 或 Excel) 只有 32 位元提供者。</span><span class="sxs-lookup"><span data-stu-id="80bb1-105">However, some data sources, such as Access or Excel, only have a 32-bit provider available.</span></span> <span data-ttu-id="80bb1-106">若要使用這些資料來源，您可能必須安裝並執行此精靈的 32 位元版本。</span><span class="sxs-lookup"><span data-stu-id="80bb1-106">To work with these data sources, you might have to install and run the 32-bit version of the wizard.</span></span> <span data-ttu-id="80bb1-107">若要安裝此精靈的 32 位元版本，您必須在安裝期間選取用戶端工具或 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="80bb1-107">To install the 32-bit version of the wizard, select either Client Tools or [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] during setup.</span></span>  
  
 <span data-ttu-id="80bb1-108">您可以從 [開始] 功能表、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 或命令提示字元，啟動 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 匯入和匯出精靈。</span><span class="sxs-lookup"><span data-stu-id="80bb1-108">You can start the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Import and Export Wizard from the Start menu, from [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], from [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], or at the command prompt.</span></span> <span data-ttu-id="80bb1-109">如需詳細資訊，請參閱[執行 SQL Server 匯入和匯出 Wizard](start-the-sql-server-import-and-export-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="80bb1-109">For more information, see [Run the SQL Server Import and Export Wizard](start-the-sql-server-import-and-export-wizard.md).</span></span>  
  
 <span data-ttu-id="80bb1-110">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 匯入和匯出精靈可以在可用 Managed [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 資料提供者或原生 OLE DB 提供者的任何資料來源之間複製資料。</span><span class="sxs-lookup"><span data-stu-id="80bb1-110">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Import and Export Wizard can copy data to and from any data source for which a managed [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] data provider or a native OLE DB provider is available.</span></span> <span data-ttu-id="80bb1-111">可用提供者的清單包括下列資料來源：</span><span class="sxs-lookup"><span data-stu-id="80bb1-111">The list of available providers includes the following data sources:</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
-   <span data-ttu-id="80bb1-112">一般檔案</span><span class="sxs-lookup"><span data-stu-id="80bb1-112">Flat files</span></span>  
  
-   <span data-ttu-id="80bb1-113">Microsoft Office Access</span><span class="sxs-lookup"><span data-stu-id="80bb1-113">Microsoft Office Access</span></span>  
  
-   <span data-ttu-id="80bb1-114">Microsoft Office Excel</span><span class="sxs-lookup"><span data-stu-id="80bb1-114">Microsoft Office Excel</span></span>  
  
 <span data-ttu-id="80bb1-115">根據您啟動精靈的環境而定，某些精靈功能的運作方式不盡相同：</span><span class="sxs-lookup"><span data-stu-id="80bb1-115">Some wizard features work differently, depending on the environment in which you start the wizard:</span></span>  
  
-   <span data-ttu-id="80bb1-116">如果您在中啟動 [匯 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 入和匯出嚮導] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，請選取 [**立即執行**] 核取方塊以立即執行封裝。</span><span class="sxs-lookup"><span data-stu-id="80bb1-116">If you start the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Import and Export Wizard in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], you run the package immediately by selecting the **Execute immediately** check box.</span></span> <span data-ttu-id="80bb1-117">根據預設，此核取方塊為選取狀態，而且此封裝會立即執行。</span><span class="sxs-lookup"><span data-stu-id="80bb1-117">By default, this check box is selected and the package runs immediately.</span></span>  
  
     <span data-ttu-id="80bb1-118">您也可以決定要將封裝儲存到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 還是檔案系統。</span><span class="sxs-lookup"><span data-stu-id="80bb1-118">You can also decide whether to save the package to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or to the file system.</span></span> <span data-ttu-id="80bb1-119">如果您選擇要儲存封裝，還必須指定封裝保護等級。</span><span class="sxs-lookup"><span data-stu-id="80bb1-119">If you select to save the package, you must also specify a package protection level.</span></span> <span data-ttu-id="80bb1-120">如需封裝保護層級的詳細資訊，請參閱[封裝中的敏感性資料存取控制](../security/access-control-for-sensitive-data-in-packages.md)。</span><span class="sxs-lookup"><span data-stu-id="80bb1-120">For more information about package protection levels, see [Access Control for Sensitive Data in Packages](../security/access-control-for-sensitive-data-in-packages.md).</span></span>  
  
     <span data-ttu-id="80bb1-121">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 匯入和匯出精靈建立封裝並複製資料之後，您可以使用 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師並加入工作、轉換和事件驅動邏輯以開啟和變更已儲存的封裝。</span><span class="sxs-lookup"><span data-stu-id="80bb1-121">After the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Import and Export Wizard has created the package and copied the data, you can use the [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer to open and change the saved package by adding tasks, transformations, and event-driven logic.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="80bb1-122">在 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] 中，無法使用儲存此精靈所建立之封裝的選項。</span><span class="sxs-lookup"><span data-stu-id="80bb1-122">In [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)], the option to save the package created by the wizard is not available.</span></span>  
  
-   <span data-ttu-id="80bb1-123">如果從 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 專案啟動「[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 匯入和匯出精靈」，封裝將無法做為精靈完成過程中的一個步驟來執行，</span><span class="sxs-lookup"><span data-stu-id="80bb1-123">If you start the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Import and Export Wizard from an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], the package cannot be run as a step in completing the wizard.</span></span> <span data-ttu-id="80bb1-124">而是加入到啟動精靈的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="80bb1-124">Instead, the package is added to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project from which you started the wizard.</span></span> <span data-ttu-id="80bb1-125">然後您可以執行此封裝，或透過加入工作、轉換和事件驅動邏輯 (使用 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師) 來進行擴充。</span><span class="sxs-lookup"><span data-stu-id="80bb1-125">You can then run the package or extend it by adding tasks, transformations, and event-driven logic by using [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="80bb1-126">如需詳細資訊，請參閱[執行 SQL Server 匯入和匯出 Wizard](start-the-sql-server-import-and-export-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="80bb1-126">For more information, see [Run the SQL Server Import and Export Wizard](start-the-sql-server-import-and-export-wizard.md).</span></span>  
  
## <a name="permissions-required-by-the-import-and-export-wizard"></a><span data-ttu-id="80bb1-127">匯入和匯出精靈所需的權限</span><span class="sxs-lookup"><span data-stu-id="80bb1-127">Permissions Required by the Import and Export Wizard</span></span>  
 <span data-ttu-id="80bb1-128">若要順利完成 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 匯入和匯出精靈，您至少必須具備下列權限：</span><span class="sxs-lookup"><span data-stu-id="80bb1-128">To complete the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Import and Export Wizard successfully, you must have at least the following permissions:</span></span>  
  
-   <span data-ttu-id="80bb1-129">可以連接到來源及目的地資料庫或檔案共用位置的權限。</span><span class="sxs-lookup"><span data-stu-id="80bb1-129">Permissions to connect to the source and destination databases or file shares.</span></span> <span data-ttu-id="80bb1-130">在 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 中，這需要伺服器與資料庫登入權限。</span><span class="sxs-lookup"><span data-stu-id="80bb1-130">In [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], this requires server and database login rights.</span></span>  
  
-   <span data-ttu-id="80bb1-131">可以讀取來源資料庫或檔案中之資料的權限。</span><span class="sxs-lookup"><span data-stu-id="80bb1-131">Permission to read data from the source database or file.</span></span> <span data-ttu-id="80bb1-132">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中，這需要來源資料表和檢視的 SELECT 權限。</span><span class="sxs-lookup"><span data-stu-id="80bb1-132">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], this requires SELECT permissions on the source tables and views.</span></span>  
  
-   <span data-ttu-id="80bb1-133">可以將資料寫入目的地資料庫或檔案的權限。</span><span class="sxs-lookup"><span data-stu-id="80bb1-133">Permissions to write data to the destination database or file.</span></span> <span data-ttu-id="80bb1-134">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中，這需要目的地資料表的 INSERT 權限。</span><span class="sxs-lookup"><span data-stu-id="80bb1-134">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], this requires INSERT permissions on the destination tables.</span></span>  
  
-   <span data-ttu-id="80bb1-135">如果您想要建立新的目的地資料庫、資料表或檔案，就必須具備能夠建立新資料庫、資料表或檔案的足夠權限。</span><span class="sxs-lookup"><span data-stu-id="80bb1-135">If you want to create a new destination database or table or file, permissions sufficient to create the new database or table or file.</span></span> <span data-ttu-id="80bb1-136">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中，這需要 CREATE DATABASE 或 CREATE TABLE 權限。</span><span class="sxs-lookup"><span data-stu-id="80bb1-136">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], this requires CREATE DATABASE or CREATE TABLE permissions.</span></span>  
  
-   <span data-ttu-id="80bb1-137">如果您想要儲存精靈所建立的封裝，就必須具備能夠寫入 msdb 資料庫或檔案系統的足夠權限。</span><span class="sxs-lookup"><span data-stu-id="80bb1-137">If you want to save the package created by the wizard, permissions sufficient to write to the msdb database or to the file system.</span></span> <span data-ttu-id="80bb1-138">在中 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ，這需要 msdb 資料庫的 INSERT 許可權。</span><span class="sxs-lookup"><span data-stu-id="80bb1-138">In [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], this requires INSERT permissions on the msdb database.</span></span>  
  
## <a name="mapping-data-types-in-the-import-and-export-wizard"></a><span data-ttu-id="80bb1-139">在匯入和匯出精靈中對應資料類型</span><span class="sxs-lookup"><span data-stu-id="80bb1-139">Mapping Data Types in the Import and Export Wizard</span></span>  
 <span data-ttu-id="80bb1-140">「[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 匯入和匯出精靈」提供最基本的轉換功能。</span><span class="sxs-lookup"><span data-stu-id="80bb1-140">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Import and Export Wizard provides minimal transformation capabilities.</span></span> <span data-ttu-id="80bb1-141">除了設定新目的地資料表和檔案中資料行的名稱、資料類型和資料類型屬性之外，「[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 匯入和匯出精靈」不支援資料行層級的轉換。</span><span class="sxs-lookup"><span data-stu-id="80bb1-141">Except for setting the name, the data type, and the data type properties of columns in new destination tables and files, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Import and Export Wizard supports no column-level transformations.</span></span>  
  
 <span data-ttu-id="80bb1-142">「[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 匯入和匯出精靈」使用 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 提供的對應檔案，對應兩個資料庫版本或系統之間的資料類型。</span><span class="sxs-lookup"><span data-stu-id="80bb1-142">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Import and Export Wizard uses the mapping files that [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] provides to map data types from one database version or system to another.</span></span> <span data-ttu-id="80bb1-143">例如，它可以從 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 對應到 Oracle。</span><span class="sxs-lookup"><span data-stu-id="80bb1-143">For example, it can map from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to Oracle.</span></span> <span data-ttu-id="80bb1-144">依預設，XML 格式的對應檔案會安裝在 C:\Program Files\Microsoft SQL Server\100\DTS\MappingFiles。</span><span class="sxs-lookup"><span data-stu-id="80bb1-144">By default, the mapping files in XML format are installed to C:\Program Files\Microsoft SQL Server\100\DTS\MappingFiles.</span></span> <span data-ttu-id="80bb1-145">如果您的企業需要在資料類型之間進行不同的對應，您可以更新對應，以影響精靈執行的對應。</span><span class="sxs-lookup"><span data-stu-id="80bb1-145">If your business requires different mappings between data types, you can update the mappings to affect the mappings that the wizard performs.</span></span> <span data-ttu-id="80bb1-146">例如，如果您想要 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Nchar**資料類型在將資料從傳送至 db2 時，對應到 db2**圖形**資料類型，而不是 db2 **VARGRAPHIC**資料類型 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，您可以將 SqlClientToIBMDB2.xml 對應檔中的**Nchar**對應變更為使用**圖形**，而不是**VARGRAPHIC。**</span><span class="sxs-lookup"><span data-stu-id="80bb1-146">For example, if you want the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **nchar** data type to map to the DB2 **GRAPHIC** data type instead of the DB2 **VARGRAPHIC** data type when transferring data from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to DB2, you change the **nchar** mapping in the SqlClientToIBMDB2.xml mapping file to use **GRAPHIC** instead of **VARGRAPHIC.**</span></span>  
  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="80bb1-147">包含許多常用來源和目的地組合之間的對應，您可以在對應檔目錄中加入新的對應檔，以支援其他來源和目的地。</span><span class="sxs-lookup"><span data-stu-id="80bb1-147">includes mappings between many commonly used source and destination combinations, and you can add new mapping files to the Mapping Files directory to support additional sources and destinations.</span></span> <span data-ttu-id="80bb1-148">新的對應檔必須符合已發行的 XSD 結構描述，並對應來源和目的地的唯一組合。</span><span class="sxs-lookup"><span data-stu-id="80bb1-148">The new mapping files must conform to the published XSD schema and map between a unique combination of source and destination.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="80bb1-149">如果您編輯現有的對應檔案，或將新的對應檔案加入資料夾，就必須關閉再重新開啟 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 匯入和匯出精靈或 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]，才能辨識新的檔案或變更後的檔案。</span><span class="sxs-lookup"><span data-stu-id="80bb1-149">If you edit an existing mapping file, or add a new mapping file to the folder, you must close and reopen the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Import and Export Wizard or [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] for the new or changed files to be recognized.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="80bb1-150">外部資源</span><span class="sxs-lookup"><span data-stu-id="80bb1-150">External Resources</span></span>  
  
-   <span data-ttu-id="80bb1-151">影片，[將 SQL Server 資料匯出至 Excel (在 technet.microsoft.com 上 SQL Server Video) ](https://go.microsoft.com/fwlink/?LinkID=200975)</span><span class="sxs-lookup"><span data-stu-id="80bb1-151">Video, [Exporting SQL Server Data to Excel (SQL Server Video)](https://go.microsoft.com/fwlink/?LinkID=200975), on technet.microsoft.com</span></span>  
  
-   <span data-ttu-id="80bb1-152">CodePlex 範例，[使用 Wizard 從 ODBC 匯出到一般檔案教學課程：課程套件](https://go.microsoft.com/fwlink/?LinkId=217657)，于 msftisprodsamples.codeplex.com</span><span class="sxs-lookup"><span data-stu-id="80bb1-152">CodePlex sample, [Exporting from ODBC to a Flat File Using a Wizard Tutorial: Lesson Packages](https://go.microsoft.com/fwlink/?LinkId=217657), on msftisprodsamples.codeplex.com</span></span>  
  
  
