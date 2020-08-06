---
title: 解除封裝 DAC 封裝 | Microsoft 文件
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- wizard [DAC], unpack
- data-tier application [SQL Server], unpack
- How to [DAC], unpack
- unpack DAC
ms.assetid: 697b69b3-f157-4e22-ac4e-f65c5fc2d0ad
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5ba0930f79a47696a6c9a9c1bfe028316601f64b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606880"
---
# <a name="unpack-a-dac-package"></a><span data-ttu-id="d97a1-102">解除封裝 DAC 封裝</span><span class="sxs-lookup"><span data-stu-id="d97a1-102">Unpack a DAC Package</span></span>
  <span data-ttu-id="d97a1-103">使用 [解除封裝資料層應用程式] 對話方塊可從資料層應用程式 (DAC) 封裝解壓縮指令碼和檔案。</span><span class="sxs-lookup"><span data-stu-id="d97a1-103">Use the Unpack Data-tier Application dialog box to unzip the scripts and files from a data-tier application (DAC) package.</span></span> <span data-ttu-id="d97a1-104">這些指令碼和檔案會放置在某個資料夾中，使用此封裝來將 DAC 部署到實際執行系統之前便可以進行檢閱。</span><span class="sxs-lookup"><span data-stu-id="d97a1-104">The scripts and files are placed in a folder where they can be reviewed before the package is used to deploy the DAC into a production system.</span></span> <span data-ttu-id="d97a1-105">DAC 的內容也可以與解除封裝到另一個資料夾的另一個封裝內容相比較。</span><span class="sxs-lookup"><span data-stu-id="d97a1-105">The contents of one DAC can also be compared with the contents of another package unpacked to another folder.</span></span>  
  
1.  <span data-ttu-id="d97a1-106">**開始之前：** [安全性](#Security)</span><span class="sxs-lookup"><span data-stu-id="d97a1-106">**Before you begin:**  [Security](#Security)</span></span>  
  
2.  <span data-ttu-id="d97a1-107">**若要解除封裝 DAC，請使用下列方式：** [解除封裝資料層應用程式對話方塊](#UnpackDACDial)、[檢查 DAC 套件的內容](#ExamDACPack)</span><span class="sxs-lookup"><span data-stu-id="d97a1-107">**To unpack a DAC, using:**  [Unpack Data-tier Application Dialog](#UnpackDACDial), [Examine the Contents of a DAC Package](#ExamDACPack)</span></span>  
  
##  <a name="security"></a><a name="Security"></a> <span data-ttu-id="d97a1-108">Security</span><span class="sxs-lookup"><span data-stu-id="d97a1-108">Security</span></span>  
 <span data-ttu-id="d97a1-109">建議您不要部署來源不明或來源不受信任的 DAC 封裝。</span><span class="sxs-lookup"><span data-stu-id="d97a1-109">We recommend that you do not deploy a DAC package from unknown or untrusted sources.</span></span> <span data-ttu-id="d97a1-110">這類 DAC 可能包含惡意程式碼，因此可能會執行非預期的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 程式碼，或是修改結構描述而造成錯誤。</span><span class="sxs-lookup"><span data-stu-id="d97a1-110">Such DACs could contain malicious code that might execute unintended [!INCLUDE[tsql](../../includes/tsql-md.md)] code or cause errors by modifying the schema.</span></span> <span data-ttu-id="d97a1-111">在您使用來源不明或來源不受信任的 DAC 之前，請將它部署到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的隔離測試執行個體、解除封裝 DAC 並檢查程式碼，例如預存程序或其他使用者定義的程式碼。</span><span class="sxs-lookup"><span data-stu-id="d97a1-111">Before you use a DAC from an unknown or untrusted source, deploy it on an isolated test instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)], unpack the DAC and examine the code, such as stored procedures or other user-defined code.</span></span>  
  
##  <a name="unpack-data-tier-application-dialog"></a><a name="UnpackDACDial"></a> <span data-ttu-id="d97a1-112">解除封裝資料層應用程式對話方塊</span><span class="sxs-lookup"><span data-stu-id="d97a1-112">Unpack Data-tier Application Dialog</span></span>  
 <span data-ttu-id="d97a1-113">**解除封裝 DAC 封裝檔案**</span><span class="sxs-lookup"><span data-stu-id="d97a1-113">**To Unpack a DAC Package File**</span></span>  
  
-   <span data-ttu-id="d97a1-114">在 Windows 檔案總管  中，巡覽至 DAC 封裝 (.dacpac) 檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="d97a1-114">In **Windows Explorer**, navigate to the location of a DAC package (.dacpac) file.</span></span>  
  
-   <span data-ttu-id="d97a1-115">使用這兩種方法的其中一種，來開啟 [解除封裝資料層應用程式] 對話方塊：</span><span class="sxs-lookup"><span data-stu-id="d97a1-115">Use one of these two methods to open the Unpack Data-tier Application dialog:</span></span>  
  
    1.  <span data-ttu-id="d97a1-116">以滑鼠右鍵按一下 DAC 封裝 (.dacpac) 檔案，並選取 [解除封裝]  。</span><span class="sxs-lookup"><span data-stu-id="d97a1-116">Right-click the DAC package (.dacpac) file and select **Unpack**.</span></span>  
  
    2.  <span data-ttu-id="d97a1-117">按兩下 DAC 封裝檔案。</span><span class="sxs-lookup"><span data-stu-id="d97a1-117">Double-click the DAC package file.</span></span>  
  
-   <span data-ttu-id="d97a1-118">完成對話方塊：</span><span class="sxs-lookup"><span data-stu-id="d97a1-118">Complete the dialogs:</span></span>  
  
    -   [<span data-ttu-id="d97a1-119">解除封裝 Microsoft SQL Server DAC 封裝檔案</span><span class="sxs-lookup"><span data-stu-id="d97a1-119">Unpack Microsoft SQL Server DAC Package File</span></span>](#Unpack)  
  
    -   [<span data-ttu-id="d97a1-120">瀏覽資料夾</span><span class="sxs-lookup"><span data-stu-id="d97a1-120">Browse for Folder</span></span>](#Browse)  
  
###  <a name="unpack-microsoft-sql-server-dac-package-file"></a><a name="Unpack"></a> <span data-ttu-id="d97a1-121">解除封裝 Microsoft SQL Server DAC 封裝檔案</span><span class="sxs-lookup"><span data-stu-id="d97a1-121">Unpack Microsoft SQL Server DAC Package File</span></span>  
 <span data-ttu-id="d97a1-122">使用此頁面可指定要放置解除封裝檔案的目的地資料夾，然後執行解除封裝作業。</span><span class="sxs-lookup"><span data-stu-id="d97a1-122">Use this page to specify the destination folder in which to place the unpacked files, and then run the unpack operation.</span></span>  
  
 <span data-ttu-id="d97a1-123">**檔案將解除封裝至這個資料夾** - 指定放置解除封裝檔案之資料夾的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="d97a1-123">**Files will be unpacked to this folder:** - Specify the full path to the folder for the unpacked files.</span></span> <span data-ttu-id="d97a1-124">如果此資料夾已經存在，而且您知道完整路徑，請在方塊中輸入路徑。</span><span class="sxs-lookup"><span data-stu-id="d97a1-124">If the folder exists and you know the full path, type the path in the box.</span></span> <span data-ttu-id="d97a1-125">如果不存在，請按一下 **[瀏覽]** 按鈕，導覽至資料夾或建立新的資料夾。</span><span class="sxs-lookup"><span data-stu-id="d97a1-125">If not, click the **Browse** button to navigate to a folder or create a new folder.</span></span>  
  
 <span data-ttu-id="d97a1-126">**瀏覽** - 開啟 [瀏覽資料夾]  頁面，您可以在這裡導覽檔案階層來選擇資料夾或建立新的資料夾。</span><span class="sxs-lookup"><span data-stu-id="d97a1-126">**Browse** - Opens the **Browse for Folder** page where you can choose a folder by navigating the file hierarchy, or create a new folder.</span></span>  
  
 <span data-ttu-id="d97a1-127">**解除封裝** - 開始解除封裝作業。</span><span class="sxs-lookup"><span data-stu-id="d97a1-127">**Unpack** - Starts the unpack operation.</span></span>  
  
 <span data-ttu-id="d97a1-128">**取消** - 結束此對話方塊，而不解除封裝 DAC 封裝。</span><span class="sxs-lookup"><span data-stu-id="d97a1-128">**Cancel** - Terminates the dialog box without unpacking the DAC package.</span></span>  
  
###  <a name="browse-for-folder"></a><a name="Browse"></a> <span data-ttu-id="d97a1-129">瀏覽資料夾</span><span class="sxs-lookup"><span data-stu-id="d97a1-129">Browse for Folder</span></span>  
 <span data-ttu-id="d97a1-130">使用此頁面可選擇解除封裝作業的目的地資料夾。</span><span class="sxs-lookup"><span data-stu-id="d97a1-130">Use this page to choose the destination folder for the unpack operation.</span></span> <span data-ttu-id="d97a1-131">您也可以選擇建立新的資料夾。</span><span class="sxs-lookup"><span data-stu-id="d97a1-131">Optionally, you can also create a new folder.</span></span>  
  
 <span data-ttu-id="d97a1-132">**資料夾清單** - 顯示電腦的檔案階層。</span><span class="sxs-lookup"><span data-stu-id="d97a1-132">**Folder list** - Displays the file hierarchy for your computer.</span></span> <span data-ttu-id="d97a1-133">展開節點，導覽至要解除封裝 DAC 封裝的資料夾。</span><span class="sxs-lookup"><span data-stu-id="d97a1-133">Expand the nodes to navigate to the folder in which to unpack the DAC package.</span></span> <span data-ttu-id="d97a1-134">按一下此資料夾，然後按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="d97a1-134">Click on the folder and then click **OK**.</span></span>  
  
 <span data-ttu-id="d97a1-135">**建立新資料夾** - 開啟對話方塊，您可以在其中指定您目前在資料夾階層中選取之資料夾內所要建立的新資料夾名稱。</span><span class="sxs-lookup"><span data-stu-id="d97a1-135">**Make New Folder** - Opens a dialog in which you can specify the name for a new folder to be created in the folder you have currently selected in the folder hierarchy.</span></span>  
  
 <span data-ttu-id="d97a1-136">**確定** - 放置您在 [解除封裝 DAC 封裝檔案]  頁面之 [檔案將解除封裝至這個資料夾]  方塊內所選取之資料夾的路徑，並讓您回到這個頁面。</span><span class="sxs-lookup"><span data-stu-id="d97a1-136">**OK** - Places the path to the folder you selected in the **Files will be unpacked to this folder** box of the **Unpack DAC Package File** page and returns you to that page.</span></span>  
  
 <span data-ttu-id="d97a1-137">**取消** - 結束此對話方塊，而不選取資料夾。</span><span class="sxs-lookup"><span data-stu-id="d97a1-137">**Cancel** - Terminates the dialog box without selecting a folder.</span></span>  
  
##  <a name="examine-the-contents-of-a-dac-package"></a><a name="ExamDACPack"></a> <span data-ttu-id="d97a1-138">檢查 DAC 封裝的內容</span><span class="sxs-lookup"><span data-stu-id="d97a1-138">Examine the Contents of a DAC Package</span></span>  
 <span data-ttu-id="d97a1-139">在解除封裝之後，您可以檢查 [解除封裝資料層應用程式]  對話方塊所產生的檔案。</span><span class="sxs-lookup"><span data-stu-id="d97a1-139">After unpacking the package, you can examine the files produced by the **Unpack Data-tier Application** dialog.</span></span> <span data-ttu-id="d97a1-140">此對話方塊會在選取的目的地資料夾中建置下列檔案：</span><span class="sxs-lookup"><span data-stu-id="d97a1-140">The dialog box builds the following files in the selected destination folder:</span></span>  
  
1.  <span data-ttu-id="d97a1-141">Transact-SQL 指令碼，其中包含建立 DAC 中所定義之物件的陳述式。</span><span class="sxs-lookup"><span data-stu-id="d97a1-141">A Transact-SQL script that contains the statements for creating the objects defined in the DAC.</span></span> <span data-ttu-id="d97a1-142">檔案名稱為 *DACName*.sql，其中 *DACName* 是 DAC 的名稱。</span><span class="sxs-lookup"><span data-stu-id="d97a1-142">The file name is *DACName*.sql, where *DACName* is the name of the DAC.</span></span>  
  
2.  <span data-ttu-id="d97a1-143">封裝中的所有 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="d97a1-143">All XML files from the package.</span></span>  
  
3.  <span data-ttu-id="d97a1-144">DAC [其他檔案] 區段中的所有檔案，例如 DAC 預先部署或部署後的檔案。</span><span class="sxs-lookup"><span data-stu-id="d97a1-144">All files from the Extra Files section of the DAC, such as the DAC pre-deployment or post-deployment files.</span></span>  
  
 <span data-ttu-id="d97a1-145">如需詳細資訊，請參閱 [Validate a DAC Package](validate-a-dac-package.md)。</span><span class="sxs-lookup"><span data-stu-id="d97a1-145">For more information, see [Validate a DAC Package](validate-a-dac-package.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d97a1-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d97a1-146">See Also</span></span>  
 <span data-ttu-id="d97a1-147">[資料層應用程式](data-tier-applications.md) </span><span class="sxs-lookup"><span data-stu-id="d97a1-147">[Data-tier Applications](data-tier-applications.md) </span></span>  
 <span data-ttu-id="d97a1-148">[部署資料層應用程式](deploy-a-data-tier-application.md) </span><span class="sxs-lookup"><span data-stu-id="d97a1-148">[Deploy a Data-tier Application](deploy-a-data-tier-application.md) </span></span>  
 [<span data-ttu-id="d97a1-149">升級資料層應用程式</span><span class="sxs-lookup"><span data-stu-id="d97a1-149">Upgrade a Data-tier Application</span></span>](upgrade-a-data-tier-application.md)  
  
  
