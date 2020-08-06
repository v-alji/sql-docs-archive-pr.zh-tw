---
title: 安裝 Analysis Services 多維度模型化教學課程的範例資料和專案 |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: fc475b25-cbb2-408a-901f-9299299538c5
author: minewiskan
ms.author: owend
ms.openlocfilehash: 196f9bad945c69cbc77d2a5dc41a5333e58b33fc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596403"
---
# <a name="install-sample-data-and-projects-for-the-analysis-services-multidimensional-modeling-tutorial"></a><span data-ttu-id="72ea6-102">安裝 Analysis Services 多維度模型化教學課程的範例資料和專案</span><span class="sxs-lookup"><span data-stu-id="72ea6-102">Install Sample Data and Projects for the Analysis Services Multidimensional Modeling Tutorial</span></span>
  <span data-ttu-id="72ea6-103">使用本主題中提供的指示與連結，安裝 Analysis Services 教學課程中所使用的所有資料和專案檔案。</span><span class="sxs-lookup"><span data-stu-id="72ea6-103">Use the instructions and links provided in this topic to install all of the data and project files used in the Analysis Services Tutorials.</span></span>  
  
## <a name="step-1-install-sql-server-software"></a><span data-ttu-id="72ea6-104">步驟 1：安裝 SQL Server 軟體</span><span class="sxs-lookup"><span data-stu-id="72ea6-104">Step 1: Install SQL Server Software</span></span>  
 <span data-ttu-id="72ea6-105">本教學課程中的課程假設您已安裝下列軟體。</span><span class="sxs-lookup"><span data-stu-id="72ea6-105">The lessons in this tutorial assume that you have the following software installed.</span></span> <span data-ttu-id="72ea6-106">下列所有軟體都是使用 SQL Server 安裝媒體進行安裝。</span><span class="sxs-lookup"><span data-stu-id="72ea6-106">All of the following software is installed using SQL Server installation media.</span></span> <span data-ttu-id="72ea6-107">為簡化部署，您可以在一台電腦上安裝所有功能。</span><span class="sxs-lookup"><span data-stu-id="72ea6-107">For simplicity of deployment, you can install all of the features on a single computer.</span></span> <span data-ttu-id="72ea6-108">若要安裝這些功能，請執行 SQL Server 安裝程式，並從 [特徵選取] 頁面中選取這些功能。</span><span class="sxs-lookup"><span data-stu-id="72ea6-108">To install these features, run SQL Server Setup and select them from the Feature Selection page.</span></span> <span data-ttu-id="72ea6-109">如需詳細資訊，請參閱[Install SQL Server 2014 from The 安裝 Wizard &#40;安裝程式&#41;](../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md)。</span><span class="sxs-lookup"><span data-stu-id="72ea6-109">For more information, see [Install SQL Server 2014 from the Installation Wizard &#40;Setup&#41;](../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md).</span></span>  
  
-   <span data-ttu-id="72ea6-110">Database Engine</span><span class="sxs-lookup"><span data-stu-id="72ea6-110">Database Engine</span></span>  
  
-   <span data-ttu-id="72ea6-111">Analysis Services</span><span class="sxs-lookup"><span data-stu-id="72ea6-111">Analysis Services</span></span>  
  
     <span data-ttu-id="72ea6-112">Analysis Services 僅適用於下列版本：Evaluation、Enterprise、Business Intelligence、Standard。</span><span class="sxs-lookup"><span data-stu-id="72ea6-112">Analysis Services is available in these editions only: Evaluation, Enterprise, Business Intelligence, Standard.</span></span>  
  
     <span data-ttu-id="72ea6-113">請注意，SQL Server Express 版本不包含 Analysis Services。</span><span class="sxs-lookup"><span data-stu-id="72ea6-113">Note that SQL Server Express editions do not include Analysis Services.</span></span> <span data-ttu-id="72ea6-114">如果您想要免費試用軟體，請[下載 Evaluation Edition](https://go.microsoft.com/fwlink/?LinkId=392824) 。</span><span class="sxs-lookup"><span data-stu-id="72ea6-114">[Download the Evaluation edition](https://go.microsoft.com/fwlink/?LinkId=392824) if you want to try out the software free of charge.</span></span>  
  
     <span data-ttu-id="72ea6-115">根據預設，Analysis Services 會安裝成多維度執行個體，您可以在 [安裝精靈] 的伺服器組態頁面中選擇 [表格式伺服器模式] 來覆寫。</span><span class="sxs-lookup"><span data-stu-id="72ea6-115">By default, Analysis Services is installed as a multidimensional instance, which you can override by choosing Tabular Server Mode in the server configuration page of the Installation Wizard.</span></span> <span data-ttu-id="72ea6-116">如果您想要同時執行兩種伺服器模式，請在相同電腦上重新執行 SQL Server 安裝程式，以另一個模式來安裝第二個 Analysis Services 執行個體。</span><span class="sxs-lookup"><span data-stu-id="72ea6-116">If you want to run both server modes, rerun SQL Server Setup on the same computer to install a second instance of Analysis Services in the other mode.</span></span>  
  
-   <span data-ttu-id="72ea6-117">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="72ea6-117">SQL Server Management Studio</span></span>  
  
 <span data-ttu-id="72ea6-118">或者，當您進行教學課程時，考慮安裝 Excel 來瀏覽多維度資料。</span><span class="sxs-lookup"><span data-stu-id="72ea6-118">Optionally, consider installing Excel to browse your multidimensional data as you proceed through the tutorial.</span></span> <span data-ttu-id="72ea6-119">安裝 Excel 時會啟用 [在 Excel 中進行分析]\*\*\*\* 功能，此功能會使用 [樞紐分析表] 欄位清單啟動 Excel，而這份清單會連接至您要建立的 Cube。</span><span class="sxs-lookup"><span data-stu-id="72ea6-119">Installing Excel enables the **Analyze in Excel** feature that starts Excel using a PivotTable field list that is connected to the cube you are building.</span></span> <span data-ttu-id="72ea6-120">建議使用 Excel 瀏覽資料，因為您可以快速建立一個可讓您與資料互動的樞紐分析報表。</span><span class="sxs-lookup"><span data-stu-id="72ea6-120">Using Excel to browse data is recommended because you can quickly build a pivot report that lets you interact with the data.</span></span>  
  
 <span data-ttu-id="72ea6-121">或者，您可以使用內建到 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]的內建 MDX 查詢設計工具來瀏覽資料。</span><span class="sxs-lookup"><span data-stu-id="72ea6-121">Alternatively, you can browse data using the built-in MDX query designer that is built into [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="72ea6-122">查詢設計工具會傳回相同的資料，但以一般資料列集呈現的資料除外。</span><span class="sxs-lookup"><span data-stu-id="72ea6-122">The query designer returns the same data, except the data is presented as a flat rowset.</span></span>  
  
## <a name="step-2-download-sql-server-data-tools---business-intelligence-for-visual-studio-2012"></a><span data-ttu-id="72ea6-123">步驟2：下載 SQL Server Data Tools-Visual Studio 2012 的商業智慧</span><span class="sxs-lookup"><span data-stu-id="72ea6-123">Step 2: Download SQL Server Data Tools - Business Intelligence for Visual Studio 2012</span></span>  
 <span data-ttu-id="72ea6-124">在此版本中，SQL Server Data Tools 要與其他 SQL Server 功能分開下載及安裝。</span><span class="sxs-lookup"><span data-stu-id="72ea6-124">In this release, SQL Server Data Tools is downloaded and installed separately from other SQL Server features.</span></span> <span data-ttu-id="72ea6-125">現在可以在網路上免費下載用來建立 BI 模型和報表的設計工具和專案範本。</span><span class="sxs-lookup"><span data-stu-id="72ea6-125">The designers and project templates used to create BI models and reports are now available as a free web download.</span></span>  
  
-   <span data-ttu-id="72ea6-126">[下載商業智慧版 SQL Server Data Tools ](https://go.microsoft.com/fwlink/p/?LinkID=322038)。</span><span class="sxs-lookup"><span data-stu-id="72ea6-126">[Download the Business Intelligence version of SQL Server Data Tools](https://go.microsoft.com/fwlink/p/?LinkID=322038).</span></span> <span data-ttu-id="72ea6-127">檔案會儲存至 Downloads 資料夾。</span><span class="sxs-lookup"><span data-stu-id="72ea6-127">The file is saved to the Downloads folder.</span></span> <span data-ttu-id="72ea6-128">執行安裝程式來安裝該工具。</span><span class="sxs-lookup"><span data-stu-id="72ea6-128">Run setup to install the tool.</span></span>  
  
     <span data-ttu-id="72ea6-129">重新開機以完成安裝。</span><span class="sxs-lookup"><span data-stu-id="72ea6-129">Reboot the computer to complete the installation.</span></span>  
  
## <a name="step-3-install-databases"></a><span data-ttu-id="72ea6-130">步驟 3：安裝資料庫</span><span class="sxs-lookup"><span data-stu-id="72ea6-130">Step 3: Install Databases</span></span>  
 <span data-ttu-id="72ea6-131">Analysis Services 多維度模型使用您從關聯式資料庫管理系統匯入的交易資料。</span><span class="sxs-lookup"><span data-stu-id="72ea6-131">An Analysis Services multidimensional model uses transactional data that you import from a relational database management system.</span></span> <span data-ttu-id="72ea6-132">基於這個教學課程的目的，您將使用下列關聯式資料庫做為您的資料來源。</span><span class="sxs-lookup"><span data-stu-id="72ea6-132">For the purposes of this tutorial, you will use the following relational database as your data source.</span></span>  
  
-   <span data-ttu-id="72ea6-133">**AdventureWorksDW2012** -這是在資料庫引擎實例上執行的關聯式資料倉儲。</span><span class="sxs-lookup"><span data-stu-id="72ea6-133">**AdventureWorksDW2012** - This is a relational data warehouse that runs on a Database Engine instance.</span></span> <span data-ttu-id="72ea6-134">它提供 Analysis Services 資料庫將使用的原始資料，以及您在整個教學課程中建立與部署的專案。</span><span class="sxs-lookup"><span data-stu-id="72ea6-134">It provides the original data that will be used by the Analysis Services databases and projects that you build and deploy throughout the tutorial.</span></span>  
  
     <span data-ttu-id="72ea6-135">您可以將這個範例資料庫用於 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] 和 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="72ea6-135">You can use this sample database with [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] as well as [!INCLUDE[ssSQL11](../includes/sssql11-md.md)].</span></span>  
  
 <span data-ttu-id="72ea6-136">若要安裝此資料庫，請執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="72ea6-136">To install this database, do the following:</span></span>  
  
1.  <span data-ttu-id="72ea6-137">從 codeplex 的產品範例頁面下載 [AdventureWorkDW2012](https://go.microsoft.com/fwlink/p/?LinkID=221770) 資料庫。</span><span class="sxs-lookup"><span data-stu-id="72ea6-137">Download the [AdventureWorkDW2012](https://go.microsoft.com/fwlink/p/?LinkID=221770) database from the product samples page on codeplex.</span></span>  
  
     <span data-ttu-id="72ea6-138">此資料庫檔案名稱為 AdvntureWorksDW2012_Data.mdf。</span><span class="sxs-lookup"><span data-stu-id="72ea6-138">The database file name is AdvntureWorksDW2012_Data.mdf.</span></span> <span data-ttu-id="72ea6-139">此檔案應該在您電腦的 [下載] 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="72ea6-139">The file should be in the Downloads folder on your computer.</span></span>  
  
2.  <span data-ttu-id="72ea6-140">將 AdventureWorksDW2012_Data.mdf 檔案複製到本機 SQL Server Database Engine 執行個體的資料目錄中。</span><span class="sxs-lookup"><span data-stu-id="72ea6-140">Copy the AdventureWorksDW2012_Data.mdf file to the data directory of the local SQL Server Database Engine instance.</span></span> <span data-ttu-id="72ea6-141">根據預設，它位於 C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Data。</span><span class="sxs-lookup"><span data-stu-id="72ea6-141">By default, it is located at C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Data.</span></span>  
  
3.  <span data-ttu-id="72ea6-142">啟動 SQL Server Management Studio，並連接到 Database Engine 執行個體。</span><span class="sxs-lookup"><span data-stu-id="72ea6-142">Start SQL Server Management Studio and connect to the Database Engine instance.</span></span>  
  
4.  <span data-ttu-id="72ea6-143">以滑鼠右鍵按一下 [資料庫]，然後按一下 [附加]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="72ea6-143">Right-click Databases, click **Attach**.</span></span>  
  
5.  <span data-ttu-id="72ea6-144">按一下 [新增] 。</span><span class="sxs-lookup"><span data-stu-id="72ea6-144">Click **Add**.</span></span>  
  
6.  <span data-ttu-id="72ea6-145">選取 **AdventureWorksDW2012_Data.mdf** 資料庫檔案，然後按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="72ea6-145">Select the **AdventureWorksDW2012_Data.mdf** database file and click **OK**.</span></span> <span data-ttu-id="72ea6-146">如果未列出檔案，請檢查 C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Data 資料夾以確認該檔案位於該處。</span><span class="sxs-lookup"><span data-stu-id="72ea6-146">If the file is not listed, check the C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Data folder to be sure the file is there.</span></span>  
  
7.  <span data-ttu-id="72ea6-147">在資料庫詳細資料中，移除記錄檔項目。</span><span class="sxs-lookup"><span data-stu-id="72ea6-147">In database details, remove the Log file entry.</span></span> <span data-ttu-id="72ea6-148">安裝程式會假設您有記錄檔，但是範例中並沒有記錄檔。</span><span class="sxs-lookup"><span data-stu-id="72ea6-148">The setup program assumes you have a log file, but there is no log file in the sample.</span></span> <span data-ttu-id="72ea6-149">附加資料庫時，將自動建立新的記錄檔。</span><span class="sxs-lookup"><span data-stu-id="72ea6-149">A new log file will be created automatically when you attach the database.</span></span> <span data-ttu-id="72ea6-150">選取記錄檔，並按一下 [移除]\*\*\*\*，然後按一下 [確定]\*\*\*\*，即可只附加主要資料庫檔案。</span><span class="sxs-lookup"><span data-stu-id="72ea6-150">Select the log file and click **Remove**, and then click **OK** to attach just the primary database file.</span></span>  
  
## <a name="step-4-grant-database-permissions"></a><span data-ttu-id="72ea6-151">步驟 4：授與資料庫權限</span><span class="sxs-lookup"><span data-stu-id="72ea6-151">Step 4: Grant Database Permissions</span></span>  
 <span data-ttu-id="72ea6-152">範例專案會使用指定匯入或處理資料所使用之安全性內容的資料來源模擬設定。</span><span class="sxs-lookup"><span data-stu-id="72ea6-152">The sample projects use data source impersonation settings that specify the security context under which data is imported or processed.</span></span> <span data-ttu-id="72ea6-153">根據預設，模擬設定會指定 Analysis Services 服務帳戶來存取資料。</span><span class="sxs-lookup"><span data-stu-id="72ea6-153">By default, the impersonation settings specify the Analysis Services service account for accessing the data.</span></span> <span data-ttu-id="72ea6-154">若要使用此預設設定，您必須確認執行 Analysis Services 所使用的服務帳戶擁有 **AdventureWorksDW2012** 資料庫的資料讀取器權限。</span><span class="sxs-lookup"><span data-stu-id="72ea6-154">To use this default setting, you must ensure that the service account under which Analysis Services runs has data reader permissions on the **AdventureWorksDW2012** database.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="72ea6-155">基於學習的目的，建議您使用預設服務帳戶模擬選項，並將資料讀取器權限授與 SQL Server 中的服務帳戶。</span><span class="sxs-lookup"><span data-stu-id="72ea6-155">For learning purposes, it is recommended that you use the default service account impersonation option and grant data reader permissions to the service account in SQL Server.</span></span> <span data-ttu-id="72ea6-156">即使有其他可用的模擬選項，但並非所有選項都適用於處理作業。</span><span class="sxs-lookup"><span data-stu-id="72ea6-156">Although other impersonation options are available, not all of them are suitable for processing operations.</span></span> <span data-ttu-id="72ea6-157">具體而言，不支援使用目前使用者的認證進行處理的選項。</span><span class="sxs-lookup"><span data-stu-id="72ea6-157">Specifically, the option for using the credentials of the current user is not supported for processing.</span></span>  
  
1.  <span data-ttu-id="72ea6-158">判斷服務帳戶。</span><span class="sxs-lookup"><span data-stu-id="72ea6-158">Determine the service account.</span></span> <span data-ttu-id="72ea6-159">您可以使用 SQL Server 組態管理員或 [服務] 主控台應用程式來檢視帳戶資訊。</span><span class="sxs-lookup"><span data-stu-id="72ea6-159">You can use SQL Server Configuration Manager or the Services console application to view account information.</span></span> <span data-ttu-id="72ea6-160">如果您使用預設帳戶安裝 Analysis Services 做為預設執行個體，此服務就會當做 **NT Service\MSSQLServerOLAPService**執行。</span><span class="sxs-lookup"><span data-stu-id="72ea6-160">If you installed Analysis Services as the default instance, using the default account, the service is running as **NT Service\MSSQLServerOLAPService**.</span></span>  
  
2.  <span data-ttu-id="72ea6-161">在 Management Studio 中，連接到 Database Engine 執行個體。</span><span class="sxs-lookup"><span data-stu-id="72ea6-161">In Management Studio, connect to the database engine instance.</span></span>  
  
3.  <span data-ttu-id="72ea6-162">展開 [安全性] 資料夾，以滑鼠右鍵按一下 [登入]，然後選取 [新增登入]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="72ea6-162">Expand the Security folder, right-click Logins and select **New Login**.</span></span>  
  
4.  <span data-ttu-id="72ea6-163">在 [一般] 頁面的 [登入名稱] 中，輸入 **NT Service\MSSQLServerOLAPService** (或執行服務所使用的帳戶)。</span><span class="sxs-lookup"><span data-stu-id="72ea6-163">On the General page, in Login name, type **NT Service\MSSQLServerOLAPService** (or whatever account the service is running as).</span></span>  
  
5.  <span data-ttu-id="72ea6-164">按一下 [使用者對應]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="72ea6-164">Click **User Mapping**.</span></span>  
  
6.  <span data-ttu-id="72ea6-165">選取 **AdventureWorksDW2012** 資料庫旁邊的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="72ea6-165">Select the checkbox next to the **AdventureWorksDW2012** database.</span></span> <span data-ttu-id="72ea6-166">角色成員資格應該會自動包含 **db_datareader** 和 **public**。</span><span class="sxs-lookup"><span data-stu-id="72ea6-166">Role membership should automatically include **db_datareader** and **public**.</span></span> <span data-ttu-id="72ea6-167">按一下 [確定]\*\*\*\*，接受預設值。</span><span class="sxs-lookup"><span data-stu-id="72ea6-167">Click **OK** to accept the defaults.</span></span>  
  
## <a name="step-5-install-projects"></a><span data-ttu-id="72ea6-168">步驟 5：安裝專案</span><span class="sxs-lookup"><span data-stu-id="72ea6-168">Step 5: Install Projects</span></span>  
 <span data-ttu-id="72ea6-169">教學課程包含範例專案，讓您可以對照完成的專案比較您的結果，或開始順序中比較後面的課程。</span><span class="sxs-lookup"><span data-stu-id="72ea6-169">The tutorial includes sample projects so that you can compare your results against a finished project, or start a lesson that is further on in the sequence.</span></span>  
  
 <span data-ttu-id="72ea6-170">第 4 課的專案檔案特別重要，因為它不僅為第 4 課而且還為所有後續課程提供了基礎。</span><span class="sxs-lookup"><span data-stu-id="72ea6-170">The project file for Lesson 4 is particularly important because it provides the basis for not only that lesson, but all the subsequent lessons that follow.</span></span> <span data-ttu-id="72ea6-171">與先前的專案檔案相較之下，教學課程中的步驟會導致完全相同的已完成專案檔案的副本，而第 4 課的範例專案包含新的模型資訊，您在第 1 課到第 3 課內建的模型中找不到該項資訊。</span><span class="sxs-lookup"><span data-stu-id="72ea6-171">In contrast with the previous project files, where the steps in the tutorial result in an exact copy of the completed project files, the Lesson 4 sample project includes new model information that is not found in the model you built in lessons 1 through 3.</span></span> <span data-ttu-id="72ea6-172">第 4 課會假設您要啟動下列下載中提供的範例專案檔案。</span><span class="sxs-lookup"><span data-stu-id="72ea6-172">Lesson 4 assumes that you are starting with a sample project file that is available in the following download.</span></span>  
  
1.  <span data-ttu-id="72ea6-173">在 codeplex 的產品範例頁面上，下載 [Analysis Services 教學課程 SQL Server 2012](https://go.microsoft.com/fwlink/p/?LinkID=221866) 。</span><span class="sxs-lookup"><span data-stu-id="72ea6-173">Download the [Analysis Services Tutorial SQL Server 2012](https://go.microsoft.com/fwlink/p/?LinkID=221866) on the product samples page on codeplex.</span></span>  
  
     <span data-ttu-id="72ea6-174">2012 教學課程對 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] 版本有效。</span><span class="sxs-lookup"><span data-stu-id="72ea6-174">The 2012 tutorials are valid for the [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] release.</span></span>  
  
     <span data-ttu-id="72ea6-175">「Analysis Services 教學課程 SQL Server 2012.zip」檔案會儲存到您電腦上的 [下載] 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="72ea6-175">The "Analysis Services Tutorial SQL Server 2012.zip" file will be saved to the Downloads folder on your computer.</span></span>  
  
2.  <span data-ttu-id="72ea6-176">將 .zip 檔案移至根磁碟機的正下方資料夾 (例如 C:\Tutorial)。</span><span class="sxs-lookup"><span data-stu-id="72ea6-176">Move the .zip file to a folder just below the root drive (for example, C:\Tutorial).</span></span> <span data-ttu-id="72ea6-177">如果您嘗試將 [下載] 資料夾中的檔案解壓縮，則此步驟會降低「路徑太長」錯誤。</span><span class="sxs-lookup"><span data-stu-id="72ea6-177">This step mitigates the "Path too long" error that sometimes occurs if you attempt to unzip the files in the Downloads folder.</span></span>  
  
3.  <span data-ttu-id="72ea6-178">解壓縮範例專案、以滑鼠右鍵按一下該檔案，然後選取 [全部解壓縮]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="72ea6-178">Unzip the sample projects: right-click on the file and select **Extract All**.</span></span> <span data-ttu-id="72ea6-179">解壓縮檔案之後，您應該已經在電腦上安裝下列專案：</span><span class="sxs-lookup"><span data-stu-id="72ea6-179">After you extract the files, you should have the following projects installed on your computer:</span></span>  
  
    -   <span data-ttu-id="72ea6-180">第 1 課完成</span><span class="sxs-lookup"><span data-stu-id="72ea6-180">Lesson 1 Complete</span></span>  
  
    -   <span data-ttu-id="72ea6-181">第 2 課完成</span><span class="sxs-lookup"><span data-stu-id="72ea6-181">Lesson 2 Complete</span></span>  
  
    -   <span data-ttu-id="72ea6-182">第 3 課完成</span><span class="sxs-lookup"><span data-stu-id="72ea6-182">Lesson 3 Complete</span></span>  
  
    -   <span data-ttu-id="72ea6-183">第 4 課完成</span><span class="sxs-lookup"><span data-stu-id="72ea6-183">Lesson 4 Complete</span></span>  
  
    -   <span data-ttu-id="72ea6-184">第 4 課開始</span><span class="sxs-lookup"><span data-stu-id="72ea6-184">Lesson 4 Start</span></span>  
  
    -   <span data-ttu-id="72ea6-185">第 5 課完成</span><span class="sxs-lookup"><span data-stu-id="72ea6-185">Lesson 5 Complete</span></span>  
  
    -   <span data-ttu-id="72ea6-186">第 6 課完成</span><span class="sxs-lookup"><span data-stu-id="72ea6-186">Lesson 6 Complete</span></span>  
  
    -   <span data-ttu-id="72ea6-187">第 7 課完成</span><span class="sxs-lookup"><span data-stu-id="72ea6-187">Lesson 7 Complete</span></span>  
  
    -   <span data-ttu-id="72ea6-188">第 8 課完成</span><span class="sxs-lookup"><span data-stu-id="72ea6-188">Lesson 8 Complete</span></span>  
  
    -   <span data-ttu-id="72ea6-189">第 9 課完成</span><span class="sxs-lookup"><span data-stu-id="72ea6-189">Lesson 9 Complete</span></span>  
  
    -   <span data-ttu-id="72ea6-190">第 10 課完成</span><span class="sxs-lookup"><span data-stu-id="72ea6-190">Lesson 10 Complete</span></span>  
  
4.  <span data-ttu-id="72ea6-191">移除這些檔案的唯讀權限。</span><span class="sxs-lookup"><span data-stu-id="72ea6-191">Remove the read-only permissions on these files.</span></span> <span data-ttu-id="72ea6-192">以滑鼠右鍵按一下上層資料夾 "Analysis Services Tutorial SQL Server 2012"，選取 [屬性]\*\*\*\*，並清除 [唯讀]\*\*\*\* 的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="72ea6-192">Right-click the parent folder, "Analysis Services Tutorial SQL Server 2012", select **Properties**, and clear the checkbox for **Read-only**.</span></span> <span data-ttu-id="72ea6-193">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="72ea6-193">Click **OK**.</span></span> <span data-ttu-id="72ea6-194">將變更套用到此資料夾、子資料夾和檔案。</span><span class="sxs-lookup"><span data-stu-id="72ea6-194">Apply the changes to this folder, subfolders, and files.</span></span>  
  
5.  <span data-ttu-id="72ea6-195">啟動 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="72ea6-195">Start [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
6.  <span data-ttu-id="72ea6-196">開啟對應至您要使用之課程的方案 (.sln) 檔案。</span><span class="sxs-lookup"><span data-stu-id="72ea6-196">Open the solution (.sln) file that corresponds to the lesson you are using.</span></span> <span data-ttu-id="72ea6-197">例如，在名為 "Lesson 1 Complete" 的資料夾中，您會開啟 Analysis Services Tutorial.sln 檔案。</span><span class="sxs-lookup"><span data-stu-id="72ea6-197">For example, in the folder named "Lesson 1 Complete", you would open the Analysis Services Tutorial.sln file.</span></span>  
  
7.  <span data-ttu-id="72ea6-198">部署方案以確認已正確設定資料庫權限和伺服器位置資訊。</span><span class="sxs-lookup"><span data-stu-id="72ea6-198">Deploy the solution to verify that database permissions and server location information is set up correctly.</span></span>  
  
     <span data-ttu-id="72ea6-199">如果 Analysis Services 和 Database Engine 是當做預設執行個體 (MSSQLServer) 安裝，而且所有軟體都在相同的電腦上執行，則您可以按一下 [組建] 功能表上的 [部署方案]\*\*\*\*，以建立範例專案，並將其部署至本機 Analysis Services 執行個體。</span><span class="sxs-lookup"><span data-stu-id="72ea6-199">If Analysis Services and the Database Engine are installed as the default instance (MSSQLServer) and all software is running on the same computer, you can click **Deploy Solution** on the Build menu to build and deploy the sample project to the local Analysis Services instance.</span></span> <span data-ttu-id="72ea6-200">在部署期間，資料將會從本機 Database Engine 執行個體上的 **AdventureWorksDW2012** 資料庫處理 (或匯入)。</span><span class="sxs-lookup"><span data-stu-id="72ea6-200">During deployment, data will be processed (or imported) from the **AdventureWorksDW2012** database on the local Database Engine instance.</span></span> <span data-ttu-id="72ea6-201">Analysis Services 執行個體上將會建立新的 Analysis Services 資料庫，其中包含從 Database Engine 擷取的資料。</span><span class="sxs-lookup"><span data-stu-id="72ea6-201">A new Analysis Services database will be created on the Analysis Services instance that contains the data retrieved from the Database Engine.</span></span>  
  
     <span data-ttu-id="72ea6-202">如果出現錯誤，請檢閱先前有關設定資料庫權限的步驟。</span><span class="sxs-lookup"><span data-stu-id="72ea6-202">If you encounter errors, review the previous steps on setting up database permissions.</span></span> <span data-ttu-id="72ea6-203">另外，您可能也需要變更伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="72ea6-203">Additionally, you might also need to change server names.</span></span> <span data-ttu-id="72ea6-204">預設伺服器名稱為 localhost。</span><span class="sxs-lookup"><span data-stu-id="72ea6-204">The default server name is localhost.</span></span> <span data-ttu-id="72ea6-205">如果您的伺服器是安裝在遠端電腦上，或是安裝成具名執行個體，則必須覆寫預設值，改為使用對您的安裝有效的伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="72ea6-205">If your servers are installed on remote computers or as named instances, you must override the default to use a server name that is valid for your installation.</span></span> <span data-ttu-id="72ea6-206">此外，如果伺服器位於遠端電腦上，您可能需要設定 Windows 防火牆，以允許存取伺服器。</span><span class="sxs-lookup"><span data-stu-id="72ea6-206">Furthermore, if the servers are on remote computers, you might need to configure Windows Firewall to allow access to the servers.</span></span>  
  
     <span data-ttu-id="72ea6-207">用來連接 Database Engine 的伺服器名稱會指定在多維度方案的資料來源物件中 (Adventure Works 教學課程)，顯示在方案總管中。</span><span class="sxs-lookup"><span data-stu-id="72ea6-207">The server name for connecting to the database engine is specified in the Data Source object of the multidimensional solution (Adventure Works Tutorial), visible in Solution Explorer.</span></span>  
  
     <span data-ttu-id="72ea6-208">用來連接 Analysis Services 的伺服器名稱會指定在專案 [屬性] 頁面的 [部署] 索引標籤中，也會出現在方案總管中。</span><span class="sxs-lookup"><span data-stu-id="72ea6-208">The server name for connecting to Analysis Services is specified in the Deployment tab of the Property Pages of the project, also visible in Solution Explorer.</span></span>  
  
8.  <span data-ttu-id="72ea6-209">啟動 SQL Server Management Studio。</span><span class="sxs-lookup"><span data-stu-id="72ea6-209">Start SQL Server Management Studio.</span></span> <span data-ttu-id="72ea6-210">在 SQL Server Management Studio 中，連接到 Analysis Services。</span><span class="sxs-lookup"><span data-stu-id="72ea6-210">In SQL Server Management Studio, connect to Analysis Services.</span></span> <span data-ttu-id="72ea6-211">請確認名為 **Analysis Services 教學課程**的資料庫正在伺服器上執行。</span><span class="sxs-lookup"><span data-stu-id="72ea6-211">Verify that a database named **Analysis Services Tutorial** is running on the server.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="72ea6-212">後續步驟</span><span class="sxs-lookup"><span data-stu-id="72ea6-212">Next Step</span></span>  
 <span data-ttu-id="72ea6-213">您現在可以使用此教學課程。</span><span class="sxs-lookup"><span data-stu-id="72ea6-213">You are now ready to use the tutorial.</span></span> <span data-ttu-id="72ea6-214">如需如何開始使用的詳細資訊，請參閱[多維度模型化 &#40;Adventure Works 教學課程&#41;](multidimensional-modeling-adventure-works-tutorial.md)。</span><span class="sxs-lookup"><span data-stu-id="72ea6-214">For more information about how to get started, see [Multidimensional Modeling &#40;Adventure Works Tutorial&#41;](multidimensional-modeling-adventure-works-tutorial.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72ea6-215">另請參閱</span><span class="sxs-lookup"><span data-stu-id="72ea6-215">See Also</span></span>  
 <span data-ttu-id="72ea6-216">[從安裝精靈安裝 SQL Server 2014 &#40;安裝程式&#41;](../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md) </span><span class="sxs-lookup"><span data-stu-id="72ea6-216">[Install SQL Server 2014 from the Installation Wizard &#40;Setup&#41;](../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md) </span></span>  
 <span data-ttu-id="72ea6-217">[設定 Windows 防火牆以允許 Analysis Services 存取](instances/configure-the-windows-firewall-to-allow-analysis-services-access.md) </span><span class="sxs-lookup"><span data-stu-id="72ea6-217">[Configure the Windows Firewall to Allow Analysis Services Access](instances/configure-the-windows-firewall-to-allow-analysis-services-access.md) </span></span>  
 [<span data-ttu-id="72ea6-218">設定 Windows 防火牆以允許 SQL Server 存取</span><span class="sxs-lookup"><span data-stu-id="72ea6-218">Configure the Windows Firewall to Allow SQL Server Access</span></span>](../../2014/sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md)  
  
  
