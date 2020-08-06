---
title: 選擇目的地 (SQL Server 匯入和匯出精靈) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.impexpwizard.chooseadestination.f1
ms.assetid: 1898be15-3e69-42d3-8ecb-3733c9f6c8e3
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e4bf9b717ef9de20d84d32c18eb3caa4c54cad87
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597947"
---
# <a name="choose-a-destination-sql-server-import-and-export-wizard"></a><span data-ttu-id="a50c5-102">選擇目的地 (SQL Server 匯入和匯出精靈)</span><span class="sxs-lookup"><span data-stu-id="a50c5-102">Choose a Destination (SQL Server Import and Export Wizard)</span></span>
  <span data-ttu-id="a50c5-103">使用 [**選擇目的地**] 頁面，即可指定您想要複製之資料的目的地。</span><span class="sxs-lookup"><span data-stu-id="a50c5-103">Use the **Choose a Destination** page to specify the destination of the data that you want to copy.</span></span>  
  
 <span data-ttu-id="a50c5-104">若要深入瞭解此嚮導，請參閱[SQL Server 匯入和匯出嚮導](import-and-export-data-with-the-sql-server-import-and-export-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="a50c5-104">To learn more about this wizard, see [SQL Server Import and Export Wizard](import-and-export-data-with-the-sql-server-import-and-export-wizard.md).</span></span> <span data-ttu-id="a50c5-105">若要瞭解用來啟動精靈的選項，以及成功執行嚮導所需的許可權，請參閱[執行 SQL Server 匯入和匯出嚮導](start-the-sql-server-import-and-export-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="a50c5-105">To learn about the options for starting the wizard, as well as the permissions required to run the wizard successfully, see [Run the SQL Server Import and Export Wizard](start-the-sql-server-import-and-export-wizard.md).</span></span>  
  
 <span data-ttu-id="a50c5-106">「[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 匯入和匯出精靈」的用途是將資料從來源複製到目的地。</span><span class="sxs-lookup"><span data-stu-id="a50c5-106">The purpose of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Import and Export Wizard is to copy data from a source to a destination.</span></span> <span data-ttu-id="a50c5-107">這個精靈也可以為您建立目的地資料庫和目的地資料表。</span><span class="sxs-lookup"><span data-stu-id="a50c5-107">The wizard can also create a destination database and destination tables for you.</span></span> <span data-ttu-id="a50c5-108">不過，如果您必須複製多個資料庫或資料表，或複製其他種類的資料庫物件，則應該改用「複製資料庫精靈」。</span><span class="sxs-lookup"><span data-stu-id="a50c5-108">However, if you have to copy multiple databases or tables, or other kinds of database objects, you should use the Copy Database Wizard instead.</span></span> <span data-ttu-id="a50c5-109">如需詳細資訊，請參閱 [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="a50c5-109">For more information, see [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).</span></span>  
  
## <a name="static-options"></a><span data-ttu-id="a50c5-110">靜態選項</span><span class="sxs-lookup"><span data-stu-id="a50c5-110">Static Options</span></span>  
 <span data-ttu-id="a50c5-111">**目的地**</span><span class="sxs-lookup"><span data-stu-id="a50c5-111">**Destination**</span></span>  
 <span data-ttu-id="a50c5-112">選擇符合目的地資料儲存格式的資料提供者。</span><span class="sxs-lookup"><span data-stu-id="a50c5-112">Choose the data provider that matches the data storage format of the destination.</span></span> <span data-ttu-id="a50c5-113">您的資料來源可能有一個以上的提供者可用。</span><span class="sxs-lookup"><span data-stu-id="a50c5-113">There may be more than one provider available for your data source.</span></span> <span data-ttu-id="a50c5-114">例如， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 您可以使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client、SQL Server 的 .NET Framework Data Provider，或 SQL Server 的 Microsoft OLE DB 提供者。</span><span class="sxs-lookup"><span data-stu-id="a50c5-114">For example, with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] you can use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client, the .NET Framework Data Provider for SQL Server, or the Microsoft OLE DB Provider for SQL Server.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a50c5-115">若要將資料儲存到 ODBC 目的地，請選取 .NET Framework Data Provider for ODBC。</span><span class="sxs-lookup"><span data-stu-id="a50c5-115">To save data to an ODBC destination, select the .NET Framework Data Provider for ODBC.</span></span>  
  
 <span data-ttu-id="a50c5-116">[**資料來源**] 屬性的選項數目不定，視電腦上安裝的提供者而定。</span><span class="sxs-lookup"><span data-stu-id="a50c5-116">The **Data Source** property has a variable number of options, which change depending on the providers installed on the computer.</span></span> <span data-ttu-id="a50c5-117">下表列出部分常用目的地的選項。</span><span class="sxs-lookup"><span data-stu-id="a50c5-117">The following tables list the options for some commonly used destinations.</span></span> <span data-ttu-id="a50c5-118">若為其他提供者，請參閱提供者特定文件集。</span><span class="sxs-lookup"><span data-stu-id="a50c5-118">For other providers, see the provider-specific documentation.</span></span>  
  
## <a name="dynamic-options"></a><span data-ttu-id="a50c5-119">動態選項</span><span class="sxs-lookup"><span data-stu-id="a50c5-119">Dynamic Options</span></span>  
 <span data-ttu-id="a50c5-120">下列章節顯示數個資料來源可用的選項。</span><span class="sxs-lookup"><span data-stu-id="a50c5-120">The following sections show the options available for several data sources.</span></span> <span data-ttu-id="a50c5-121">這裡並未列出 [目的地] 下拉式清單提供的所有目的地。</span><span class="sxs-lookup"><span data-stu-id="a50c5-121">Not all the destinations that are available in the Destination drop-down are listed here.</span></span>  
  
### <a name="destination--sql-server-native-client-or-microsoft-ole-db-provider-for-sql-server"></a><span data-ttu-id="a50c5-122">目的地 = SQL Server Native Client 或 Microsoft OLE DB Provider for SQL Server</span><span class="sxs-lookup"><span data-stu-id="a50c5-122">Destination = SQL Server Native Client or Microsoft OLE DB Provider for SQL Server</span></span>  
 <span data-ttu-id="a50c5-123">**伺服器名稱**</span><span class="sxs-lookup"><span data-stu-id="a50c5-123">**Server name**</span></span>  
 <span data-ttu-id="a50c5-124">輸入接收資料的伺服器名稱，或從清單中選擇伺服器。</span><span class="sxs-lookup"><span data-stu-id="a50c5-124">Type the name of the server to receive the data, or choose a server from the list.</span></span>  
  
 <span data-ttu-id="a50c5-125">**[使用 Windows 驗證]**</span><span class="sxs-lookup"><span data-stu-id="a50c5-125">**Use Windows Authentication**</span></span>  
 <span data-ttu-id="a50c5-126">指定封裝是否使用 Microsoft Windows 驗證來登入資料庫。</span><span class="sxs-lookup"><span data-stu-id="a50c5-126">Specify whether the package should use Microsoft Windows Authentication to log in to the database.</span></span> <span data-ttu-id="a50c5-127">建議使用 Windows 驗證，以獲得較佳的安全性。</span><span class="sxs-lookup"><span data-stu-id="a50c5-127">Windows Authentication is recommended for better security.</span></span>  
  
 <span data-ttu-id="a50c5-128">**[使用 SQL Server 驗證]**</span><span class="sxs-lookup"><span data-stu-id="a50c5-128">**Use SQL Server Authentication**</span></span>  
 <span data-ttu-id="a50c5-129">指定封裝是否應使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證來登入資料庫。</span><span class="sxs-lookup"><span data-stu-id="a50c5-129">Specify whether the package should use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication to log in to the database.</span></span> <span data-ttu-id="a50c5-130">如果您使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證，就必須提供使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="a50c5-130">If you use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication, you must provide a user name and password.</span></span>  
  
 <span data-ttu-id="a50c5-131">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="a50c5-131">**User name**</span></span>  
 <span data-ttu-id="a50c5-132">使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證時，請指定資料庫連接的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="a50c5-132">Specify a user name for the database connection when you are using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
 <span data-ttu-id="a50c5-133">**密碼**</span><span class="sxs-lookup"><span data-stu-id="a50c5-133">**Password**</span></span>  
 <span data-ttu-id="a50c5-134">使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證時，請提供資料庫連接的密碼。</span><span class="sxs-lookup"><span data-stu-id="a50c5-134">Provide the password for the database connection when you are using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
 <span data-ttu-id="a50c5-135">**Database**</span><span class="sxs-lookup"><span data-stu-id="a50c5-135">**Database**</span></span>  
 <span data-ttu-id="a50c5-136">從指定之實例上的資料庫清單中選取 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，或按一下 [**新增**] 來建立新的資料庫。</span><span class="sxs-lookup"><span data-stu-id="a50c5-136">Select from the list of databases on the specified instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], or create a new database by clicking **New**.</span></span>  
  
 <span data-ttu-id="a50c5-137">**[重新整理]**</span><span class="sxs-lookup"><span data-stu-id="a50c5-137">**Refresh**</span></span>  
 <span data-ttu-id="a50c5-138">按一下 [重新整理]\*\*\*\* 來還原可用資料庫的清單。</span><span class="sxs-lookup"><span data-stu-id="a50c5-138">Restore the list of available databases by clicking **Refresh**.</span></span>  
  
 <span data-ttu-id="a50c5-139">**新增**</span><span class="sxs-lookup"><span data-stu-id="a50c5-139">**New**</span></span>  
 <span data-ttu-id="a50c5-140">使用 [**建立資料庫**] 對話方塊來建立新的目的地資料庫。</span><span class="sxs-lookup"><span data-stu-id="a50c5-140">Create a new destination database by using the **Create Database** dialog box.</span></span>  
  
### <a name="destination--flat-file-destination"></a><span data-ttu-id="a50c5-141">目的地 = 一般檔案目的地</span><span class="sxs-lookup"><span data-stu-id="a50c5-141">Destination = Flat File Destination</span></span>  
 <span data-ttu-id="a50c5-142">**檔案名稱**</span><span class="sxs-lookup"><span data-stu-id="a50c5-142">**File name**</span></span>  
 <span data-ttu-id="a50c5-143">指定儲存資料之檔案的路徑和檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="a50c5-143">Specify the path and file name for the file in which to store the data.</span></span> <span data-ttu-id="a50c5-144">或按一下 [瀏覽]\*\*\*\* 找出檔案。</span><span class="sxs-lookup"><span data-stu-id="a50c5-144">Or, click **Browse** to locate a file.</span></span>  
  
 <span data-ttu-id="a50c5-145">**瀏覽**</span><span class="sxs-lookup"><span data-stu-id="a50c5-145">**Browse**</span></span>  
 <span data-ttu-id="a50c5-146">使用 [開啟]\*\*\*\* 對話方塊來找出檔案。</span><span class="sxs-lookup"><span data-stu-id="a50c5-146">Locate a file by using the **Open** dialog box.</span></span>  
  
 <span data-ttu-id="a50c5-147">**地區設定**</span><span class="sxs-lookup"><span data-stu-id="a50c5-147">**Locale**</span></span>  
 <span data-ttu-id="a50c5-148">指定用來定義字元排序順序及日期和時間格式的地區設定識別碼 (LCID)。</span><span class="sxs-lookup"><span data-stu-id="a50c5-148">Specify the locale ID (LCID) that defines character sort orders and date and time formatting.</span></span>  
  
 <span data-ttu-id="a50c5-149">**Unicode**</span><span class="sxs-lookup"><span data-stu-id="a50c5-149">**Unicode**</span></span>  
 <span data-ttu-id="a50c5-150">指出是否使用 Unicode。</span><span class="sxs-lookup"><span data-stu-id="a50c5-150">Indicate whether to use Unicode.</span></span> <span data-ttu-id="a50c5-151">如果使用 Unicode，您就不必指定字碼頁。</span><span class="sxs-lookup"><span data-stu-id="a50c5-151">If you use Unicode, you do not have to specify a code page.</span></span>  
  
 <span data-ttu-id="a50c5-152">**字碼頁**</span><span class="sxs-lookup"><span data-stu-id="a50c5-152">**Code page**</span></span>  
 <span data-ttu-id="a50c5-153">指定您要使用之語言的字碼頁。</span><span class="sxs-lookup"><span data-stu-id="a50c5-153">Specify the code page for the language you want to use.</span></span>  
  
 <span data-ttu-id="a50c5-154">**格式**</span><span class="sxs-lookup"><span data-stu-id="a50c5-154">**Format**</span></span>  
 <span data-ttu-id="a50c5-155">指出是要使用分隔符號、固定寬度或不齊右的格式。</span><span class="sxs-lookup"><span data-stu-id="a50c5-155">Indicate whether to use delimited, fixed width, or ragged right formatting.</span></span>  
  
|<span data-ttu-id="a50c5-156">值</span><span class="sxs-lookup"><span data-stu-id="a50c5-156">Value</span></span>|<span data-ttu-id="a50c5-157">描述</span><span class="sxs-lookup"><span data-stu-id="a50c5-157">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a50c5-158">Delimited (分隔檔)</span><span class="sxs-lookup"><span data-stu-id="a50c5-158">Delimited</span></span>|<span data-ttu-id="a50c5-159">資料行是以分隔符號分隔，並在 [資料**行**] 頁面上指定。</span><span class="sxs-lookup"><span data-stu-id="a50c5-159">Columns are separated by a delimiter, specified on the **Columns** page.</span></span>|  
|<span data-ttu-id="a50c5-160">固定寬度</span><span class="sxs-lookup"><span data-stu-id="a50c5-160">Fixed width</span></span>|<span data-ttu-id="a50c5-161">資料行具有固定寬度。</span><span class="sxs-lookup"><span data-stu-id="a50c5-161">Columns have a fixed width.</span></span>|  
|<span data-ttu-id="a50c5-162">不齊右</span><span class="sxs-lookup"><span data-stu-id="a50c5-162">Ragged right</span></span>|<span data-ttu-id="a50c5-163">不齊右檔案就是除了最後一個資料行是由資料列分隔符號所分隔之外，其他所有資料行都有固定寬度的檔案。</span><span class="sxs-lookup"><span data-stu-id="a50c5-163">Ragged right files are files in which every column has a fixed width, except for the last column, which is delimited by the row delimiter.</span></span>|  
  
 <span data-ttu-id="a50c5-164">**文字定位項**</span><span class="sxs-lookup"><span data-stu-id="a50c5-164">**Text qualifier**</span></span>  
 <span data-ttu-id="a50c5-165">輸入要使用的文字限定詞。</span><span class="sxs-lookup"><span data-stu-id="a50c5-165">Type the text qualifier to use.</span></span> <span data-ttu-id="a50c5-166">例如，您可以指定每一個文字資料行都加上引號。</span><span class="sxs-lookup"><span data-stu-id="a50c5-166">For example, you can specify that each text column be surrounded with quotation marks.</span></span>  
  
 <span data-ttu-id="a50c5-167">**第一個資料列的資料行名稱**</span><span class="sxs-lookup"><span data-stu-id="a50c5-167">**Column names in first data row**</span></span>  
 <span data-ttu-id="a50c5-168">指出是否在第一個資料列顯示資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="a50c5-168">Indicate whether you want to display column names in the first data row.</span></span>  
  
### <a name="destination--microsoft-excel"></a><span data-ttu-id="a50c5-169">目的地 = Microsoft Excel</span><span class="sxs-lookup"><span data-stu-id="a50c5-169">Destination = Microsoft Excel</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a50c5-170">只有當您想要連接到使用 Excel 2003 或更早版本的資料來源時，才選取 [ **Microsoft Excel** ]。</span><span class="sxs-lookup"><span data-stu-id="a50c5-170">Select **Microsoft Excel** only if you want to connect to a data source that uses Excel 2003 or earlier.</span></span> <span data-ttu-id="a50c5-171">若要連接到使用 Excel 2007 的資料來源，請選取 [ **Microsoft Office 12.0 存取資料庫引擎 OLE DB 提供者**]，按一下 [**屬性**]，然後在 [**資料連結屬性**] 對話方塊的 [**全部**] 索引標籤上，針對 [**擴充屬性**] 輸入 `Excel 12.0` 。</span><span class="sxs-lookup"><span data-stu-id="a50c5-171">To connect to a data source that uses Excel 2007, select **Microsoft Office 12.0 Access Database Engine OLE DB Provider**, click **Properties**, and then on the **All** tab of the **Data Link Properties** dialog box, for **Extended Properties**, enter `Excel 12.0`.</span></span>  
  
 <span data-ttu-id="a50c5-172">**Excel 檔案路徑**</span><span class="sxs-lookup"><span data-stu-id="a50c5-172">**Excel file path**</span></span>  
 <span data-ttu-id="a50c5-173">指定用來儲存資料之活頁簿的路徑和檔案名 (例如，C:\MyData.xls， \\\Sales\Database\Northwind.xls) 。</span><span class="sxs-lookup"><span data-stu-id="a50c5-173">Specify the path and file name for the workbook in which to store the data (for example, C:\MyData.xls, \\\Sales\Database\Northwind.xls).</span></span> <span data-ttu-id="a50c5-174">或者，按一下 **[流覽]** 以找出活頁簿。</span><span class="sxs-lookup"><span data-stu-id="a50c5-174">Or, click **Browse** to locate a workbook.</span></span>  
  
 <span data-ttu-id="a50c5-175">**瀏覽**</span><span class="sxs-lookup"><span data-stu-id="a50c5-175">**Browse**</span></span>  
 <span data-ttu-id="a50c5-176">使用 [**開啟**] 對話方塊來找出 Excel 活頁簿。</span><span class="sxs-lookup"><span data-stu-id="a50c5-176">Locate an Excel workbook by using the **Open** dialog box.</span></span>  
  
 <span data-ttu-id="a50c5-177">**Excel 版本**</span><span class="sxs-lookup"><span data-stu-id="a50c5-177">**Excel version**</span></span>  
 <span data-ttu-id="a50c5-178">選取目的地活頁簿所使用的 Excel 版本。</span><span class="sxs-lookup"><span data-stu-id="a50c5-178">Select the version of Excel that is used by the destination workbook.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a50c5-179">當您將資料匯出至 [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] 目的地時，精靈會使用 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Excel 目的地元件。</span><span class="sxs-lookup"><span data-stu-id="a50c5-179">When you export data to a [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] destination, the wizard uses the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Excel Destination component.</span></span> <span data-ttu-id="a50c5-180">如需有關使用考慮和已知問題的詳細資訊，請參閱[Excel 目的地](../data-flow/excel-destination.md)。</span><span class="sxs-lookup"><span data-stu-id="a50c5-180">For information on some usage considerations and known issues, see [Excel Destination](../data-flow/excel-destination.md).</span></span>  
  
### <a name="destination--microsoft-access"></a><span data-ttu-id="a50c5-181">目的地 = Microsoft Access</span><span class="sxs-lookup"><span data-stu-id="a50c5-181">Destination = Microsoft Access</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a50c5-182">只有當您想要連接到使用2003或更早版本的資料庫時，才選取 [ **Microsoft Access** ]。</span><span class="sxs-lookup"><span data-stu-id="a50c5-182">Select **Microsoft Access** only if you want to connect to a database that uses Access 2003 or earlier.</span></span> <span data-ttu-id="a50c5-183">若要連接到使用存取2007的資料庫，請選取 [ **Microsoft Office 12.0 存取資料庫引擎 OLE DB 提供者**]。</span><span class="sxs-lookup"><span data-stu-id="a50c5-183">To connect to a database that uses Access 2007, select **Microsoft Office 12.0 Access Database Engine OLE DB Provider**.</span></span>  
  
 <span data-ttu-id="a50c5-184">**檔案名稱**</span><span class="sxs-lookup"><span data-stu-id="a50c5-184">**File name**</span></span>  
 <span data-ttu-id="a50c5-185">指定資料庫檔案的路徑和檔案名，以在其中儲存資料 (例如 C:\MyData.mdb、 \\ \Sales\Database\Northwind.mdb) 。</span><span class="sxs-lookup"><span data-stu-id="a50c5-185">Specify the path and file name for the database file in which to store the data (for example, C:\MyData.mdb, \\\Sales\Database\Northwind.mdb).</span></span> <span data-ttu-id="a50c5-186">或者，按一下 **[流覽]** 以找出資料庫檔案。</span><span class="sxs-lookup"><span data-stu-id="a50c5-186">Or, click **Browse** to locate a database file.</span></span>  
  
 <span data-ttu-id="a50c5-187">**瀏覽**</span><span class="sxs-lookup"><span data-stu-id="a50c5-187">**Browse**</span></span>  
 <span data-ttu-id="a50c5-188">使用 [**開啟**] 對話方塊，流覽至資料庫檔案。</span><span class="sxs-lookup"><span data-stu-id="a50c5-188">Browse to the database file by using the **Open** dialog box.</span></span>  
  
 <span data-ttu-id="a50c5-189">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="a50c5-189">**User name**</span></span>  
 <span data-ttu-id="a50c5-190">當工作群組資訊檔案與資料庫相關聯時，請指定該資料庫連接的有效使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="a50c5-190">Specify a valid user name for the database connection when a workgroup information file is associated with the database.</span></span>  
  
 <span data-ttu-id="a50c5-191">**密碼**</span><span class="sxs-lookup"><span data-stu-id="a50c5-191">**Password**</span></span>  
 <span data-ttu-id="a50c5-192">當工作群組資訊檔案與資料庫相關聯時，請提供該資料庫連接的使用者密碼。</span><span class="sxs-lookup"><span data-stu-id="a50c5-192">Provide the user's password for the database connection when a workgroup information file is associated with the database.</span></span> <span data-ttu-id="a50c5-193">不過，如果資料庫受到所有使用者的單一密碼保護，您就必須在 [**資料連結屬性**] 對話方塊中提供這個值，這可從 [ **Advanced** ] 按鈕存取。</span><span class="sxs-lookup"><span data-stu-id="a50c5-193">However, if the database is protected with a single password for all users, you must provide this value in the **Data Link Properties** dialog box, which is accessed from the **Advanced** button.</span></span>  
  
 <span data-ttu-id="a50c5-194">**進階**</span><span class="sxs-lookup"><span data-stu-id="a50c5-194">**Advanced**</span></span>  
 <span data-ttu-id="a50c5-195">使用 [資料連結屬性]\*\*\*\* 對話方塊來指定進階選項，例如資料庫密碼或非預設工作群組資訊檔案。</span><span class="sxs-lookup"><span data-stu-id="a50c5-195">Specify advanced options, such as the database password or a non-default workgroup information file, by using the **Data Link Properties** dialog box.</span></span> <span data-ttu-id="a50c5-196">如需有關 OLE DB 提供者屬性的詳細資訊，請在[MSDN library](https://go.microsoft.com/fwlink/?linkid=62553)的資料存取區段中搜尋。</span><span class="sxs-lookup"><span data-stu-id="a50c5-196">For more information about OLE DB provider properties, search in the Data Access section of the [MSDN Library](https://go.microsoft.com/fwlink/?linkid=62553).</span></span>  
  
  
