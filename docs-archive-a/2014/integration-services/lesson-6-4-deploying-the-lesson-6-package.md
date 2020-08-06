---
title: 步驟 4：部署第 6 課的套件 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: b613cef7-7993-4d89-a429-a8251d74d435
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8c5109dc96af138bbd0c8c0087e8b73cf3bac435
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606987"
---
# <a name="step-4-deploying-the-lesson-6-package"></a><span data-ttu-id="cfa33-102">步驟 4：部署第 6 課的封裝</span><span class="sxs-lookup"><span data-stu-id="cfa33-102">Step 4: Deploying the Lesson 6 Package</span></span>
  <span data-ttu-id="cfa33-103">部署封裝時，需要將封裝新增至 SSISDB 目錄中的 SQL Server 執行個體上的整合服務。</span><span class="sxs-lookup"><span data-stu-id="cfa33-103">Deploying the package involves adding the package to the SSISDB catalog in Integration Services on an instance of SQL Server.</span></span> <span data-ttu-id="cfa33-104">在本課程中您會將第 6 課封裝加入至 SSISDB 目錄、 設定參數，以及執行封裝。</span><span class="sxs-lookup"><span data-stu-id="cfa33-104">In this lesson you will add the Lesson 6 package to the SSISDB catalog, set the parameter, and execute the package.</span></span> <span data-ttu-id="cfa33-105">本課程中引導您使用 SQL Server Management Studio 來將第 6 課封裝加入至 SSISDB 目錄，以及部署封裝。</span><span class="sxs-lookup"><span data-stu-id="cfa33-105">For this lesson you will use SQL Server Management Studio to add the Lesson 6 package to the SSISDB catalog, and deploy the package.</span></span> <span data-ttu-id="cfa33-106">在部署封裝之後，您將修改參數指向新位置，然後執行封裝。</span><span class="sxs-lookup"><span data-stu-id="cfa33-106">After deploying the package you will modify the parameter to point to a new location then execute the package.</span></span>  
  
 <span data-ttu-id="cfa33-107">在這一課中，您將會：</span><span class="sxs-lookup"><span data-stu-id="cfa33-107">In this lesson you will:</span></span>  
  
-   <span data-ttu-id="cfa33-108">將封裝加入至 SSISDB 目錄在 SQL Server 中的 [SSIS] 節點。</span><span class="sxs-lookup"><span data-stu-id="cfa33-108">Add the package to the SSISDB catalog in the SSIS node in SQL Server.</span></span>  
  
-   <span data-ttu-id="cfa33-109">部署封裝。</span><span class="sxs-lookup"><span data-stu-id="cfa33-109">Deploy the package.</span></span>  
  
-   <span data-ttu-id="cfa33-110">設定封裝的參數值。</span><span class="sxs-lookup"><span data-stu-id="cfa33-110">Set the package parameter value.</span></span>  
  
-   <span data-ttu-id="cfa33-111">在 SSMS 中執行封裝。</span><span class="sxs-lookup"><span data-stu-id="cfa33-111">Execute the package in SSMS.</span></span>  
  
### <a name="to-locate-or-add-the-ssisdb-catalog"></a><span data-ttu-id="cfa33-112">尋找或新增 SSISDB 目錄</span><span class="sxs-lookup"><span data-stu-id="cfa33-112">To Locate or add the SSISDB catalog</span></span>  
  
1.  <span data-ttu-id="cfa33-113">按一下 [開始]，指向 [所有程式]、 指向 Microsoft SQL Server 2012，，然後按一下 [SQL Management Studio]。</span><span class="sxs-lookup"><span data-stu-id="cfa33-113">Click Start, point to All Programs, point to Microsoft SQL Server 2012, and then click SQL Management Studio.</span></span>  
  
2.  <span data-ttu-id="cfa33-114">在 [連接到伺服器] 對話方塊中，驗證預設值，再按一下 [連接]。</span><span class="sxs-lookup"><span data-stu-id="cfa33-114">On the Connect to Server dialog box, verify the default settings, and then click Connect.</span></span> <span data-ttu-id="cfa33-115">若要連接，[伺服器名稱] 方塊必須包含已安裝 SQL Server 的電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="cfa33-115">To connect, the Server name box must contain the name of the computer where SQL Server is installed.</span></span> <span data-ttu-id="cfa33-116">如果資料庫引擎是具名執行個體，[伺服器名稱] 方塊也應該包含執行個體名稱，其格式為 <電腦名稱>\\<執行個體名稱>。</span><span class="sxs-lookup"><span data-stu-id="cfa33-116">If the Database Engine is a named instance, the Server name box should also contain the instance name in the format <computer_name>\\<instance_name>.</span></span>  
  
3.  <span data-ttu-id="cfa33-117">在 [物件總管] 中展開 [Integration Services 目錄]。</span><span class="sxs-lookup"><span data-stu-id="cfa33-117">In Object Explorer expand Integration Services Catalogs.</span></span>  
  
4.  <span data-ttu-id="cfa33-118">如果沒有列在 [Integration Services 目錄] 下的目錄則新增 SSISDB 目錄。</span><span class="sxs-lookup"><span data-stu-id="cfa33-118">If there are no catalogs listed under Integration Services Catalogs then add the SSISDB catalog.</span></span>  
  
5.  <span data-ttu-id="cfa33-119">若要新增 SSISDB 目錄，以滑鼠右鍵按一下 [Integration Services 目錄]，並按一下 [建立類別目錄]。</span><span class="sxs-lookup"><span data-stu-id="cfa33-119">To Add the SSISDB catalog, right-click Integration Services Catalogs and click Create Catalog.</span></span>  
  
6.  <span data-ttu-id="cfa33-120">在 [建立類別目錄] 對話方塊中選取 [啟用 CLR 整合]。</span><span class="sxs-lookup"><span data-stu-id="cfa33-120">On the Create Catalog dialog box select Enable CLR Integration.</span></span>  
  
7.  <span data-ttu-id="cfa33-121">在 [密碼] 方塊中，輸入新密碼，然後在 [重新輸入密碼] 方塊中再次輸入。</span><span class="sxs-lookup"><span data-stu-id="cfa33-121">In the Password box, type a new password then type it again in the Retype Password box.</span></span> <span data-ttu-id="cfa33-122">請務必記得您輸入的密碼。</span><span class="sxs-lookup"><span data-stu-id="cfa33-122">Be sure to remember the password you type.</span></span>  
  
8.  <span data-ttu-id="cfa33-123">按一下 [確定] 以新增 SSISDB 目錄。</span><span class="sxs-lookup"><span data-stu-id="cfa33-123">Click OK to add the SSISDB catalog.</span></span>  
  
### <a name="to-add-the-package-to-the-ssisdb-catalog"></a><span data-ttu-id="cfa33-124">若要將封裝加入至 SSISDB 目錄</span><span class="sxs-lookup"><span data-stu-id="cfa33-124">To add the package to the SSISDB catalog</span></span>  
  
1.  <span data-ttu-id="cfa33-125">在 [物件總管] 中以滑鼠右鍵按一下 [SSISDB] 並按一下 [建立資料夾]。</span><span class="sxs-lookup"><span data-stu-id="cfa33-125">In Object Explorer, right-click SSISDB and click Create Folder.</span></span>  
  
2.  <span data-ttu-id="cfa33-126">在 [建立資料夾] 對話方塊中，請在 [資料夾名稱] 方塊中輸入 SSIS 教學課程，然後按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="cfa33-126">In the Create Folder dialog box type SSIS Tutorial in the Folder name box and click OK.</span></span>  
  
3.  <span data-ttu-id="cfa33-127">展開 [SSIS 教學課程] 資料夾、 以滑鼠右鍵按一下專案，再按一下 [匯入套件]。</span><span class="sxs-lookup"><span data-stu-id="cfa33-127">Expand the SSIS Tutorial folder, right-click Projects, and click Import Packages.</span></span>  
  
4.  <span data-ttu-id="cfa33-128">在 [Integration Services 專案轉換精靈簡介] 頁面上按一下 [下一步]。</span><span class="sxs-lookup"><span data-stu-id="cfa33-128">On the Integration Services Project Conversion Wizard Introduction page click Next.</span></span>  
  
5.  <span data-ttu-id="cfa33-129">在 [尋找封裝] 頁面中，確定已選取 [來源] 清單中的 [檔案] 系統，然後按一下 [瀏覽]。</span><span class="sxs-lookup"><span data-stu-id="cfa33-129">On the Locate Packages page, ensure that File system is selected in the Source list, then click Browse.</span></span>  
  
6.  <span data-ttu-id="cfa33-130">在 [瀏覽資料夾] 對話方塊中，瀏覽至包含 SSIS 教學課程專案的資料夾，然後按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="cfa33-130">On the Browse For Folder dialog box, browse to the folder containing the SSIS Tutorial project, then click OK.</span></span>  
  
7.  <span data-ttu-id="cfa33-131">按一下 [下一步]。</span><span class="sxs-lookup"><span data-stu-id="cfa33-131">Click Next.</span></span>  
  
8.  <span data-ttu-id="cfa33-132">在 [選取封裝] 頁面上，您應該看到從 SSIS 教學課程的所有六個封裝。</span><span class="sxs-lookup"><span data-stu-id="cfa33-132">On the Select Packages page you should see all six packages from the SSIS Tutorial.</span></span> <span data-ttu-id="cfa33-133">在封裝清單中，選取 [Lesson 6.dtsx]，然後按一下 [下一步]。</span><span class="sxs-lookup"><span data-stu-id="cfa33-133">In the Packages list, select Lesson 6.dtsx, then click Next.</span></span>  
  
9. <span data-ttu-id="cfa33-134">在 [選取目的地] 頁面中，在 [專案名稱] 方塊中輸入 SSIS 教學課程部署，然後按一下 [下一步]。</span><span class="sxs-lookup"><span data-stu-id="cfa33-134">On the Select Destination page, type SSIS Tutorial Deployment in the Project Name box then click Next.</span></span>  
  
10. <span data-ttu-id="cfa33-135">接下來在每個其餘的精靈頁面上按一下 [下一步] 直到到達 [檢閱] 頁面。</span><span class="sxs-lookup"><span data-stu-id="cfa33-135">Click Next on each of the remaining wizard pages until you get to the Review page.</span></span>  
  
11. <span data-ttu-id="cfa33-136">在 [檢閱] 頁面中，按一下 [轉換]。</span><span class="sxs-lookup"><span data-stu-id="cfa33-136">On the Review page, click Convert.</span></span>  
  
12. <span data-ttu-id="cfa33-137">轉換完成時，請按一下 [關閉]。</span><span class="sxs-lookup"><span data-stu-id="cfa33-137">When the conversion completes, click Close.</span></span>  
  
 <span data-ttu-id="cfa33-138">當您關閉 Integration Services 專案轉換精靈時，SSIS 會顯示 Integration Services 部署精靈。</span><span class="sxs-lookup"><span data-stu-id="cfa33-138">When you close the Integration Services Project Conversion Wizard, SSIS displays the Integration Services Deployment Wizard.</span></span> <span data-ttu-id="cfa33-139">現在您將使用此精靈部署第 6 課封裝。</span><span class="sxs-lookup"><span data-stu-id="cfa33-139">You will use this wizard now to deploy the Lesson 6 package.</span></span>  
  
1.  <span data-ttu-id="cfa33-140">在 [Integration Services 部署精靈簡介] 頁面中，檢閱部署專案的步驟，然後按一下 [下一步]。</span><span class="sxs-lookup"><span data-stu-id="cfa33-140">On the Integration Services Deployment Wizard Introduction page, review the steps for deploying the project, then click Next.</span></span>  
  
2.  <span data-ttu-id="cfa33-141">在 [選取目的地] 頁面上確認伺服器名稱是包含 SSISDB 目錄的 SQL Server 執行個體和路徑顯示 SSIS 教學課程部署，然後按一下 [下一步]。</span><span class="sxs-lookup"><span data-stu-id="cfa33-141">On the Select Destination page verify that the server name is the instance of SQL Server containing the SSISDB catalog and that the path shows SSIS Tutorial Deployment, then click Next.</span></span>  
  
3.  <span data-ttu-id="cfa33-142">在 [檢閱] 頁面上檢閱摘要，然後按一下 [部署]。</span><span class="sxs-lookup"><span data-stu-id="cfa33-142">On the Review page, review the Summary then click Deploy.</span></span>  
  
4.  <span data-ttu-id="cfa33-143">部署完成時，請按一下 [關閉]。</span><span class="sxs-lookup"><span data-stu-id="cfa33-143">When the deployment completes, click Close.</span></span>  
  
5.  <span data-ttu-id="cfa33-144">在 [物件總管] 中以滑鼠右鍵按一下 [Integration Services 目錄]，並按一下 [重新整理]。</span><span class="sxs-lookup"><span data-stu-id="cfa33-144">In Object Explorer, right-click Integration Services Catalogs and click Refresh.</span></span>  
  
6.  <span data-ttu-id="cfa33-145">依序展開 Integration Services 目錄 SSISDB。</span><span class="sxs-lookup"><span data-stu-id="cfa33-145">Expand Integration Services Catalogs then expand SSISDB.</span></span> <span data-ttu-id="cfa33-146">繼續展開下 SSIS 教學課程的樹狀目錄，直到您已經完全展開專案。</span><span class="sxs-lookup"><span data-stu-id="cfa33-146">Continue to Expand the tree under SSIS Tutorial until you have completely expanded the project.</span></span> <span data-ttu-id="cfa33-147">您應該會看到 [SSIS 教學課程部署] 節點的 [封裝] 節點下的 Lesson 6.dtsx。</span><span class="sxs-lookup"><span data-stu-id="cfa33-147">You should see Lesson 6.dtsx under the Packages node of the SSIS Tutorial Deployment node.</span></span>  
  
 <span data-ttu-id="cfa33-148">若要確認封裝已完成，以滑鼠右鍵按一下 Lesson 6.dtsx 並按一下 [設定]。</span><span class="sxs-lookup"><span data-stu-id="cfa33-148">To verify that the package is complete, right-click Lesson 6.dtsx and click Configure.</span></span> <span data-ttu-id="cfa33-149">在 [設定] 對話方塊中，選取參數並確認有作為容器的 Lesson 6.dtsx 項目、作為名稱的 VarFolderName 及作為值的新範例資料的路徑，然後按一下 [關閉]。</span><span class="sxs-lookup"><span data-stu-id="cfa33-149">On the Configure dialog box, select Parameters and verify that there is an entry with Lesson 6.dtsx as the Container, VarFolderName as the Name and the path to New Sample Data as the value, then click Close.</span></span>  
  
 <span data-ttu-id="cfa33-150">繼續建立新的範例資料資料夾之前，命名為 [範例資料兩個]，並將任何三個原始範例檔案複製到其中。</span><span class="sxs-lookup"><span data-stu-id="cfa33-150">Before continuing create a new sample data folder, name it Sample Data Two, and copy any three of the original sample files into it.</span></span>  
  
### <a name="to-create-and-populate-a-new-sample-data-folder"></a><span data-ttu-id="cfa33-151">若要建立及擴展新的範例資料夾</span><span class="sxs-lookup"><span data-stu-id="cfa33-151">To create and populate a new sample data folder</span></span>  
  
1.  <span data-ttu-id="cfa33-152">在 Windows 檔案總管中，於磁碟機的根目錄層級 (例如 C:\\) 建立一個稱為 Sample Data Two 的新資料夾。</span><span class="sxs-lookup"><span data-stu-id="cfa33-152">In Windows Explorer, at the root level of your drive (for example, C:\\), create a new folder named Sample Data Two.</span></span>  
  
2.  <span data-ttu-id="cfa33-153">開啟 c:\Program Files\Microsoft SQL Server\110\Samples\Integration Services\Tutorial\Creating a Simple ETL Package\Sample Data 資料夾，然後從資料夾複製三個範例檔案。</span><span class="sxs-lookup"><span data-stu-id="cfa33-153">Open the c:\Program Files\Microsoft SQL Server\110\Samples\Integration Services\Tutorial\Creating a Simple ETL Package\Sample Data folder and then copy any three of the sample files from the folder.</span></span>  
  
3.  <span data-ttu-id="cfa33-154">在新範例資料資料夾，貼上已複製的檔案。</span><span class="sxs-lookup"><span data-stu-id="cfa33-154">In the New Sample Data folder, paste the copied files.</span></span>  
  
### <a name="to-change-the-package-parameter-to-point-to-the-new-sample-data"></a><span data-ttu-id="cfa33-155">若要變更為指向新的範例資料的封裝參數</span><span class="sxs-lookup"><span data-stu-id="cfa33-155">To change the package parameter to point to the new sample data</span></span>  
  
1.  <span data-ttu-id="cfa33-156">在 [物件總管] 中以滑鼠右鍵按一下 Lesson 6.dtsx 並按一下 [設定]。</span><span class="sxs-lookup"><span data-stu-id="cfa33-156">In Object Explorer, right click Lesson 6.dtsx and click Configure.</span></span>  
  
2.  <span data-ttu-id="cfa33-157">在 [設定] 對話方塊中，變更參數值為 [範例資料兩個] 的路徑。</span><span class="sxs-lookup"><span data-stu-id="cfa33-157">On the Configure dialog box, change the parameter value to the path to Sample Data Two.</span></span> <span data-ttu-id="cfa33-158">例如 C:\範例資料兩個，如果您在 C 磁碟機上的根資料夾中放置新的資料夾。</span><span class="sxs-lookup"><span data-stu-id="cfa33-158">For example C:\Sample Data Two if you placed the new folder in the root folder on the C drive.</span></span>  
  
3.  <span data-ttu-id="cfa33-159">按一下 [確定] 關閉 [設定] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="cfa33-159">Click OK to close the Configure dialog box.</span></span>  
  
### <a name="to-test-the-lesson-6-package-deployment"></a><span data-ttu-id="cfa33-160">若要測試第 6 課封裝部署</span><span class="sxs-lookup"><span data-stu-id="cfa33-160">To test the Lesson 6 package deployment</span></span>  
  
1.  <span data-ttu-id="cfa33-161">在 [物件總管] 中以滑鼠右鍵按一下 Lesson 6.dtsx 並按一下 [執行]。</span><span class="sxs-lookup"><span data-stu-id="cfa33-161">In Object Explorer, right click Lesson 6.dtsx and click Execute.</span></span>  
  
2.  <span data-ttu-id="cfa33-162">在 [執行封裝] 對話方塊中，按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="cfa33-162">On the Execute Package dialog box, click OK.</span></span>  
  
3.  <span data-ttu-id="cfa33-163">在訊息對話方塊中按一下 [是] 以開啟概觀報表。</span><span class="sxs-lookup"><span data-stu-id="cfa33-163">On the message dialog box click Yes to open Overview Report.</span></span>  
  
 <span data-ttu-id="cfa33-164">概觀報表中的封裝便會顯示名稱的封裝和狀態摘要。</span><span class="sxs-lookup"><span data-stu-id="cfa33-164">The Overview report for the package is displayed showing the name of the package and a status summary.</span></span> <span data-ttu-id="cfa33-165">[執行概觀] 一節顯示封裝中的每個工作的結果，而 [使用參數] 一節顯示封裝中所有使用參數的名稱和值，包括 VarFolderName 所用的所有參數。</span><span class="sxs-lookup"><span data-stu-id="cfa33-165">The Execution Overview section shows the result from each task in the package and the Parameters Used section shows the names and values of all parameters used in the package execution, including VarFolderName.</span></span>  
  
  
