---
title: 選擇資料來源 (SQL Server 匯入和匯出精靈) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.impexpwizard.chooseadatasource.f1
ms.assetid: ebf28a62-dfc1-4b39-9db5-df1919e5fccb
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 246c3b03bfefad83cbfc1d0110e1fd4cf0cedf7f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597953"
---
# <a name="choose-a-data-source-sql-server-import-and-export-wizard"></a><span data-ttu-id="11ad7-102">選擇資料來源 (SQL Server 匯入和匯出精靈)</span><span class="sxs-lookup"><span data-stu-id="11ad7-102">Choose a Data Source (SQL Server Import and Export Wizard)</span></span>
  <span data-ttu-id="11ad7-103">使用 [**選擇資料來源**] 頁面，即可指定您想要複製之資料的來源。</span><span class="sxs-lookup"><span data-stu-id="11ad7-103">Use the **Choose a Data Source** page to specify the source of the data that you want to copy.</span></span>  
  
 <span data-ttu-id="11ad7-104">若要深入瞭解此嚮導，請參閱[SQL Server 匯入和匯出嚮導](import-and-export-data-with-the-sql-server-import-and-export-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="11ad7-104">To learn more about this wizard, see [SQL Server Import and Export Wizard](import-and-export-data-with-the-sql-server-import-and-export-wizard.md).</span></span> <span data-ttu-id="11ad7-105">若要瞭解啟動精靈的選項，以及成功執行嚮導所需的許可權，請參閱[執行 SQL Server 匯入和匯出嚮導](start-the-sql-server-import-and-export-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="11ad7-105">To learn about the options for starting the wizard, and about the permissions required to run the wizard successfully, see [Run the SQL Server Import and Export Wizard](start-the-sql-server-import-and-export-wizard.md).</span></span>  
  
 <span data-ttu-id="11ad7-106">「[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 匯入和匯出精靈」的用途是將資料從來源複製到目的地。</span><span class="sxs-lookup"><span data-stu-id="11ad7-106">The purpose of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Import and Export Wizard is to copy data from a source to a destination.</span></span> <span data-ttu-id="11ad7-107">這個精靈也可以為您建立目的地資料庫和目的地資料表。</span><span class="sxs-lookup"><span data-stu-id="11ad7-107">The wizard can also create a destination database and destination tables for you.</span></span> <span data-ttu-id="11ad7-108">不過，如果您必須複製多個資料庫或資料表，或複製其他種類的資料庫物件，則應該改用「複製資料庫精靈」。</span><span class="sxs-lookup"><span data-stu-id="11ad7-108">However, if you have to copy multiple databases or tables, or other kinds of database objects, you should use the Copy Database Wizard instead.</span></span> <span data-ttu-id="11ad7-109">如需詳細資訊，請參閱 [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="11ad7-109">For more information, see [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="11ad7-110">選項</span><span class="sxs-lookup"><span data-stu-id="11ad7-110">Options</span></span>  
 <span data-ttu-id="11ad7-111">**資料來源**</span><span class="sxs-lookup"><span data-stu-id="11ad7-111">**Data Source**</span></span>  
 <span data-ttu-id="11ad7-112">選擇符合來源之資料儲存格式的資料提供者。</span><span class="sxs-lookup"><span data-stu-id="11ad7-112">Choose the data provider that matches the data storage format of the source.</span></span> <span data-ttu-id="11ad7-113">您的資料來源可能有一個以上的提供者可用。</span><span class="sxs-lookup"><span data-stu-id="11ad7-113">There may be more than one provider available for your data source.</span></span> <span data-ttu-id="11ad7-114">例如， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 您可以使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client、SQL Server 的 .NET Framework Data Provider，或 SQL Server 的 Microsoft OLE DB 提供者。</span><span class="sxs-lookup"><span data-stu-id="11ad7-114">For example, with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] you can use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client, the .NET Framework Data Provider for SQL Server, or the Microsoft OLE DB Provider for SQL Server.</span></span>  
  
 <span data-ttu-id="11ad7-115">[**資料來源**] 屬性具有數量不定的選項，視電腦上安裝的提供者而定。</span><span class="sxs-lookup"><span data-stu-id="11ad7-115">The **Data Source** property has a variable number of options, which depend on the providers installed on the computer.</span></span> <span data-ttu-id="11ad7-116">下表列出一些經常使用之目的地的選項。</span><span class="sxs-lookup"><span data-stu-id="11ad7-116">The following tables list the options for some frequently used destinations.</span></span> <span data-ttu-id="11ad7-117">若為其他提供者，請參閱提供者特定文件集。</span><span class="sxs-lookup"><span data-stu-id="11ad7-117">For other providers, see the provider-specific documentation.</span></span>  
  
## <a name="dynamic-options"></a><span data-ttu-id="11ad7-118">動態選項</span><span class="sxs-lookup"><span data-stu-id="11ad7-118">Dynamic Options</span></span>  
 <span data-ttu-id="11ad7-119">下列章節顯示數個資料來源可用的選項。</span><span class="sxs-lookup"><span data-stu-id="11ad7-119">The following sections show the options available for several data sources.</span></span> <span data-ttu-id="11ad7-120">此處並未列出 [資料來源] 下拉式清單中所有可用的資料來源。</span><span class="sxs-lookup"><span data-stu-id="11ad7-120">Not all the data sources that are available in the Data Source drop-down are listed here.</span></span>  
  
### <a name="data-source--sql-server-native-client-and-microsoft-ole-db-provider-for-sql-server"></a><span data-ttu-id="11ad7-121">資料來源 = SQL Server Native Client 和 Microsoft OLE DB Provider for SQL Server</span><span class="sxs-lookup"><span data-stu-id="11ad7-121">Data Source = SQL Server Native Client and Microsoft OLE DB Provider for SQL Server</span></span>  
 <span data-ttu-id="11ad7-122">**伺服器名稱**</span><span class="sxs-lookup"><span data-stu-id="11ad7-122">**Server name**</span></span>  
 <span data-ttu-id="11ad7-123">輸入包含資料之伺服器的名稱，或者從清單中選擇伺服器。</span><span class="sxs-lookup"><span data-stu-id="11ad7-123">Type the name of the server that contains the data, or choose a server from the list.</span></span>  
  
 <span data-ttu-id="11ad7-124">**[使用 Windows 驗證]**</span><span class="sxs-lookup"><span data-stu-id="11ad7-124">**Use Windows Authentication**</span></span>  
 <span data-ttu-id="11ad7-125">指定封裝是否應使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 驗證來登入資料庫。</span><span class="sxs-lookup"><span data-stu-id="11ad7-125">Specify whether the package should use [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Authentication to log in to the database.</span></span> <span data-ttu-id="11ad7-126">建議使用 Windows 驗證，以獲得較佳的安全性。</span><span class="sxs-lookup"><span data-stu-id="11ad7-126">Windows Authentication is recommended for better security.</span></span>  
  
 <span data-ttu-id="11ad7-127">**[使用 SQL Server 驗證]**</span><span class="sxs-lookup"><span data-stu-id="11ad7-127">**Use SQL Server Authentication**</span></span>  
 <span data-ttu-id="11ad7-128">指定封裝是否應使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證來登入資料庫。</span><span class="sxs-lookup"><span data-stu-id="11ad7-128">Specify whether the package should use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication to log in to the database.</span></span> <span data-ttu-id="11ad7-129">如果您使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證，就必須提供使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="11ad7-129">If you use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication, you must provide a user name and password.</span></span>  
  
 <span data-ttu-id="11ad7-130">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="11ad7-130">**User name**</span></span>  
 <span data-ttu-id="11ad7-131">使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證時，請指定資料庫連接的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="11ad7-131">Specify a user name for the database connection when you are using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
 <span data-ttu-id="11ad7-132">**密碼**</span><span class="sxs-lookup"><span data-stu-id="11ad7-132">**Password**</span></span>  
 <span data-ttu-id="11ad7-133">使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證時，請提供資料庫連接的密碼。</span><span class="sxs-lookup"><span data-stu-id="11ad7-133">Provide the password for the database connection when you are using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
 <span data-ttu-id="11ad7-134">**Database**</span><span class="sxs-lookup"><span data-stu-id="11ad7-134">**Database**</span></span>  
 <span data-ttu-id="11ad7-135">從 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 之指定執行個體上的資料庫清單中選取。</span><span class="sxs-lookup"><span data-stu-id="11ad7-135">Select from the list of databases on the specified instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="11ad7-136">**[重新整理]**</span><span class="sxs-lookup"><span data-stu-id="11ad7-136">**Refresh**</span></span>  
 <span data-ttu-id="11ad7-137">按一下 [重新整理]\*\*\*\* 來還原可用資料庫的清單。</span><span class="sxs-lookup"><span data-stu-id="11ad7-137">Restore the list of available databases by clicking **Refresh**.</span></span>  
  
### <a name="data-source--net-framework-data-provider-for-sql-server"></a><span data-ttu-id="11ad7-138">資料來源 = .NET Framework Data Provider for SQL Server</span><span class="sxs-lookup"><span data-stu-id="11ad7-138">Data Source = .NET Framework Data Provider for SQL Server</span></span>  
 <span data-ttu-id="11ad7-139">此頁面會依字母順序呈現 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] Data Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的選項清單。</span><span class="sxs-lookup"><span data-stu-id="11ad7-139">This page presents an alphabetical list of options for the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] Data Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="11ad7-140">最重要的選項列於下表中。</span><span class="sxs-lookup"><span data-stu-id="11ad7-140">The most important options are listed in the following table.</span></span>  
  
 <span data-ttu-id="11ad7-141">**資料來源**</span><span class="sxs-lookup"><span data-stu-id="11ad7-141">**Data Source**</span></span>  
 <span data-ttu-id="11ad7-142">輸入包含資料之伺服器的名稱，或者從清單中選擇伺服器。</span><span class="sxs-lookup"><span data-stu-id="11ad7-142">Type the name of the server that contains the data, or choose a server from the list.</span></span>  
  
 <span data-ttu-id="11ad7-143">**初始目錄**</span><span class="sxs-lookup"><span data-stu-id="11ad7-143">**Initial Catalog**</span></span>  
 <span data-ttu-id="11ad7-144">輸入來源資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="11ad7-144">Type the name of the source database.</span></span>  
  
 <span data-ttu-id="11ad7-145">**整合式安全性**</span><span class="sxs-lookup"><span data-stu-id="11ad7-145">**Integrated Security**</span></span>  
 <span data-ttu-id="11ad7-146">指定 `True` 以使用 Windows 整合式驗證進行連接 (建議使用)，或指定 `False` 以使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證進行連接。</span><span class="sxs-lookup"><span data-stu-id="11ad7-146">Specify `True` to connect by using Windows integrated authentication, which is recommended, or `False` to connect by using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="11ad7-147">如果您指定 `False`，則必須輸入使用者識別碼和密碼。</span><span class="sxs-lookup"><span data-stu-id="11ad7-147">If you specify `False`, you must enter a user ID and password.</span></span> <span data-ttu-id="11ad7-148">預設值是 `False`。</span><span class="sxs-lookup"><span data-stu-id="11ad7-148">The default value is `False`.</span></span>  
  
 <span data-ttu-id="11ad7-149">**使用者識別碼**</span><span class="sxs-lookup"><span data-stu-id="11ad7-149">**User ID**</span></span>  
 <span data-ttu-id="11ad7-150">使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證時，請指定資料庫連接的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="11ad7-150">Specify a user name for the database connection when you are using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
 <span data-ttu-id="11ad7-151">**密碼**</span><span class="sxs-lookup"><span data-stu-id="11ad7-151">**Password**</span></span>  
 <span data-ttu-id="11ad7-152">使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證時，請提供資料庫連接的密碼。</span><span class="sxs-lookup"><span data-stu-id="11ad7-152">Provide the password for the database connection when you are using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
 <span data-ttu-id="11ad7-153">選取此提供者時所列出的其他選項並非必要的，即可成功連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 來源資料庫。</span><span class="sxs-lookup"><span data-stu-id="11ad7-153">The additional options that are listed when you select this provider are not required to connect successfully to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] source database.</span></span> <span data-ttu-id="11ad7-154">如需其他選項的描述，請參閱 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] Software Development Kit 中，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Data Provider for [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 的文件集。</span><span class="sxs-lookup"><span data-stu-id="11ad7-154">For a description of these additional options, see the documentation for the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] Data Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] Software Development Kit.</span></span>  
  
### <a name="data-source--microsoft-excel"></a><span data-ttu-id="11ad7-155">資料來源 = Microsoft Excel</span><span class="sxs-lookup"><span data-stu-id="11ad7-155">Data Source = Microsoft Excel</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="11ad7-156">只有當您想要連接到使用 Excel 2003 或更早版本的資料來源時，才選取 [ **Microsoft Excel** ]。</span><span class="sxs-lookup"><span data-stu-id="11ad7-156">Select **Microsoft Excel** only if you want to connect to a data source that uses Excel 2003 or earlier.</span></span> <span data-ttu-id="11ad7-157">若要連接到使用 Excel 2007 的資料來源，請選取 [ **Microsoft Office 12.0 存取資料庫引擎 OLE DB 提供者**]，按一下 [**屬性**]，然後在 [**資料連結屬性**] 對話方塊的 [**全部**] 索引標籤上，輸入 `Excel 12.0` 作為 [**擴充屬性**] 的值。</span><span class="sxs-lookup"><span data-stu-id="11ad7-157">To connect to a data source that uses Excel 2007, select **Microsoft Office 12.0 Access Database Engine OLE DB Provider**, click **Properties**, and then on the **All** tab of the **Data Link Properties** dialog box, enter `Excel 12.0` as the value for **Extended Properties**.</span></span>  
  
 <span data-ttu-id="11ad7-158">**Excel 檔案路徑**</span><span class="sxs-lookup"><span data-stu-id="11ad7-158">**Excel file path**</span></span>  
 <span data-ttu-id="11ad7-159">指定要從中匯入資料之試算表的路徑和檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="11ad7-159">Specify the path and file name for the spreadsheet from which to import the data.</span></span> <span data-ttu-id="11ad7-160">例如， **C:\MyData.xls， \\\Sales\Database\Northwind.xls**。</span><span class="sxs-lookup"><span data-stu-id="11ad7-160">For example, **C:\MyData.xls, \\\Sales\Database\Northwind.xls**.</span></span> <span data-ttu-id="11ad7-161">或按一下 [瀏覽]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="11ad7-161">Or, click **Browse**.</span></span>  
  
 <span data-ttu-id="11ad7-162">**瀏覽**</span><span class="sxs-lookup"><span data-stu-id="11ad7-162">**Browse**</span></span>  
 <span data-ttu-id="11ad7-163">使用 [開啟]\*\*\*\* 對話方塊來找出試算表。</span><span class="sxs-lookup"><span data-stu-id="11ad7-163">Locate the spreadsheet by using the **Open** dialog box.</span></span>  
  
 <span data-ttu-id="11ad7-164">**Excel 版本**</span><span class="sxs-lookup"><span data-stu-id="11ad7-164">**Excel version**</span></span>  
 <span data-ttu-id="11ad7-165">選取儲存來源資料之 Excel 的版本。</span><span class="sxs-lookup"><span data-stu-id="11ad7-165">Select the version of Excel that the source data is stored in.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="11ad7-166">當您從 [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] 來源匯入資料時，精靈會使用 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Excel 來源元件。</span><span class="sxs-lookup"><span data-stu-id="11ad7-166">When you import data from a [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] source, the wizard uses the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Excel Source component.</span></span> <span data-ttu-id="11ad7-167">如需使用方式考量與已知問題的資訊，請參閱 [Excel 來源](../data-flow/excel-source.md)。</span><span class="sxs-lookup"><span data-stu-id="11ad7-167">For information about usage considerations and known issues, see [Excel Source](../data-flow/excel-source.md).</span></span>  
  
### <a name="data-source--microsoft-access"></a><span data-ttu-id="11ad7-168">資料來源 = Microsoft Access</span><span class="sxs-lookup"><span data-stu-id="11ad7-168">Data Source = Microsoft Access</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="11ad7-169">只有當您想要連接到使用2003或更早版本的資料庫時，才選取 [ **Microsoft Access** ]。</span><span class="sxs-lookup"><span data-stu-id="11ad7-169">Select **Microsoft Access** only if you want to connect to a database that uses Access 2003 or earlier.</span></span> <span data-ttu-id="11ad7-170">若要連接到使用存取2007的資料庫，請改為選取 [ **Microsoft Office 12.0 存取資料庫引擎 OLE DB 提供者**]。</span><span class="sxs-lookup"><span data-stu-id="11ad7-170">To connect to a database that uses Access 2007, select **Microsoft Office 12.0 Access Database Engine OLE DB Provider** instead.</span></span>  
  
 <span data-ttu-id="11ad7-171">**檔案名稱**</span><span class="sxs-lookup"><span data-stu-id="11ad7-171">**File name**</span></span>  
 <span data-ttu-id="11ad7-172">指定要從中匯入資料之資料庫檔案的路徑和檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="11ad7-172">Specify the path and file name for the database file from which to import the data.</span></span> <span data-ttu-id="11ad7-173">例如 **C:\MyData.mdb, \\\Sales\Database\Northwind.mdb**。</span><span class="sxs-lookup"><span data-stu-id="11ad7-173">For example, **C:\MyData.mdb, \\\Sales\Database\Northwind.mdb**.</span></span> <span data-ttu-id="11ad7-174">或按一下 [瀏覽]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="11ad7-174">Or, click **Browse**.</span></span>  
  
 <span data-ttu-id="11ad7-175">**瀏覽**</span><span class="sxs-lookup"><span data-stu-id="11ad7-175">**Browse**</span></span>  
 <span data-ttu-id="11ad7-176">使用 [開啟]\*\*\*\* 對話方塊來找出資料庫檔案。</span><span class="sxs-lookup"><span data-stu-id="11ad7-176">Locate the database file by using the **Open** dialog box.</span></span>  
  
 <span data-ttu-id="11ad7-177">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="11ad7-177">**User name**</span></span>  
 <span data-ttu-id="11ad7-178">當工作群組資訊檔案與資料庫相關聯時，請指定該資料庫連接的有效使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="11ad7-178">Specify a valid user name for the database connection when a workgroup information file is associated with the database.</span></span>  
  
 <span data-ttu-id="11ad7-179">**密碼**</span><span class="sxs-lookup"><span data-stu-id="11ad7-179">**Password**</span></span>  
 <span data-ttu-id="11ad7-180">當工作群組資訊檔案與資料庫相關聯時，請提供該資料庫連接的使用者密碼。</span><span class="sxs-lookup"><span data-stu-id="11ad7-180">Provide the user's password for the database connection when a workgroup information file is associated with the database.</span></span> <span data-ttu-id="11ad7-181">不過，如果資料庫受到所有使用者的單一密碼保護，您就必須在 [**資料連結屬性**] 對話方塊中提供這個值，按一下 [ **Advanced**] 即可存取此對話方塊。</span><span class="sxs-lookup"><span data-stu-id="11ad7-181">However, if the database is protected with a single password for all users, you must provide this value in the **Data Link Properties** dialog box, which is accessed by clicking **Advanced**.</span></span>  
  
 <span data-ttu-id="11ad7-182">**進階**</span><span class="sxs-lookup"><span data-stu-id="11ad7-182">**Advanced**</span></span>  
 <span data-ttu-id="11ad7-183">使用 [**資料連結屬性**] 對話方塊，您可能會想要指定 advanced 選項，例如資料庫密碼或非預設工作組資訊檔案。</span><span class="sxs-lookup"><span data-stu-id="11ad7-183">You may want to specify advanced options, such as the database password or a non-default workgroup information file, by using the **Data Link Properties** dialog box.</span></span> <span data-ttu-id="11ad7-184">如需有關 OLE DB 提供者屬性的詳細資訊，請在[MSDN library](https://go.microsoft.com/fwlink/?linkid=62553)的資料存取區段中搜尋。</span><span class="sxs-lookup"><span data-stu-id="11ad7-184">For more information about OLE DB provider properties, search in the Data Access section of the [MSDN library](https://go.microsoft.com/fwlink/?linkid=62553).</span></span>  
  
### <a name="data-source--flat-file-source"></a><span data-ttu-id="11ad7-185">資料來源 = 一般檔案來源</span><span class="sxs-lookup"><span data-stu-id="11ad7-185">Data Source = Flat File Source</span></span>  
 <span data-ttu-id="11ad7-186">如需有關一般檔案資料來源之選項的資訊，請參閱下列主題。</span><span class="sxs-lookup"><span data-stu-id="11ad7-186">See the following topics for information about the options for a flat file data source.</span></span>  
  
 [<span data-ttu-id="11ad7-187">一般檔案連線管理員編輯器 &#40;一般頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="11ad7-187">Flat File Connection Manager Editor &#40;General Page&#41;</span></span>](../general-page-of-integration-services-designers-options.md)  
  
 <span data-ttu-id="11ad7-188">[一般檔案連線管理員編輯器 &#40;[資料行] 頁面&#41;](../flat-file-connection-manager-editor-columns-page.md)</span><span class="sxs-lookup"><span data-stu-id="11ad7-188">[Flat File Connection Manager Editor &#40;Columns Page&#41;](../flat-file-connection-manager-editor-columns-page.md)</span></span>  
  
 [<span data-ttu-id="11ad7-189">一般檔案連線管理員編輯器 &#40;進階頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="11ad7-189">Flat File Connection Manager Editor &#40;Advanced Page&#41;</span></span>](../flat-file-connection-manager-editor-advanced-page.md)  
  
 [<span data-ttu-id="11ad7-190">一般檔案連線管理員編輯器 &#40;預覽頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="11ad7-190">Flat File Connection Manager Editor &#40;Preview Page&#41;</span></span>](../flat-file-connection-manager-editor-preview-page.md)  
  
  
