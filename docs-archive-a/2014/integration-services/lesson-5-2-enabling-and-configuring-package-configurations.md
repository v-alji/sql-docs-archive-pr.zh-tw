---
title: 步驟 2：啟用和設定套件設定 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 005218ab-8dd5-48e9-a185-6bc60cd43a7a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a804efcd84ebe563a13f61443fe19096788ca809
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593438"
---
# <a name="step-2-enabling-and-configuring-package-configurations"></a><span data-ttu-id="5d2f3-102">步驟 2:啟用和設定封裝組態</span><span class="sxs-lookup"><span data-stu-id="5d2f3-102">Step 2: Enabling and Configuring Package Configurations</span></span>
  <span data-ttu-id="5d2f3-103">在此工作中，您會將專案轉換成封裝部署模型，並使用封裝組態精靈來啟用封裝組態。</span><span class="sxs-lookup"><span data-stu-id="5d2f3-103">In this task, you will convert the project to the Package Deployment Model and enable package configurations using the Package Configuration Wizard.</span></span> <span data-ttu-id="5d2f3-104">您將利用這個精靈來產生 XML 組態檔，它包含 Foreach 迴圈容器的 `Directory` 屬性的組態設定。</span><span class="sxs-lookup"><span data-stu-id="5d2f3-104">You will use this wizard to generate an XML configuration file that contains configuration settings for the `Directory` property of the Foreach Loop container.</span></span> <span data-ttu-id="5d2f3-105">Directory 屬性的值是由新的封裝層級變數提供，您可以在執行階段更新它。</span><span class="sxs-lookup"><span data-stu-id="5d2f3-105">The value of the Directory property is supplied by a new package-level variable that you can update at run time.</span></span> <span data-ttu-id="5d2f3-106">另外，您還會擴展一個要在測試期間使用的新範例資料夾。</span><span class="sxs-lookup"><span data-stu-id="5d2f3-106">Additionally, you will populate a new sample data folder to use during testing.</span></span>  
  
### <a name="to-create-a-new-package-level-variable-mapped-to-the-directory-property"></a><span data-ttu-id="5d2f3-107">若要建立一個對應至 Directory 屬性的新封裝層級變數</span><span class="sxs-lookup"><span data-stu-id="5d2f3-107">To create a new package-level variable mapped to the Directory property</span></span>  
  
1.  <span data-ttu-id="5d2f3-108">按一下 [[!INCLUDE[ssIS](../includes/ssis-md.md)] 設計師] 的 [控制流程]\*\*\*\* 索引標籤的背景。</span><span class="sxs-lookup"><span data-stu-id="5d2f3-108">Click the background of the **Control Flow** tab in [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="5d2f3-109">這樣會將您要建立之變數的範圍設定為封裝。</span><span class="sxs-lookup"><span data-stu-id="5d2f3-109">This sets the scope for the variable you will create to the package.</span></span>  
  
2.  <span data-ttu-id="5d2f3-110">在 [[!INCLUDE[ssIS](../includes/ssis-md.md)]] 功能表上，選取 [變數]  。</span><span class="sxs-lookup"><span data-stu-id="5d2f3-110">On the [!INCLUDE[ssIS](../includes/ssis-md.md)] menu, select **Variables**.</span></span>  
  
3.  <span data-ttu-id="5d2f3-111">在 [變數]\*\*\*\* 視窗中，按一下加入變數圖示。</span><span class="sxs-lookup"><span data-stu-id="5d2f3-111">In the **Variables** window, click the Add Variable icon.</span></span>  
  
4.  <span data-ttu-id="5d2f3-112">在 [名稱]\*\*\*\* 方塊中，輸入 **varFolderName**。</span><span class="sxs-lookup"><span data-stu-id="5d2f3-112">In the **Name** box, type **varFolderName**.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="5d2f3-113">變數名稱會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="5d2f3-113">Variable names are case sensitive.</span></span>  
  
5.  <span data-ttu-id="5d2f3-114">確認 [範圍]\*\*\*\* 方塊顯示套件的名稱，即「第 5 課」。</span><span class="sxs-lookup"><span data-stu-id="5d2f3-114">Verify that the **Scope** box shows the name of the package, Lesson 5.</span></span>  
  
6.  <span data-ttu-id="5d2f3-115">將 `varFolderName` 變數之 [資料類型]  方塊的值設定為 [字串]  。</span><span class="sxs-lookup"><span data-stu-id="5d2f3-115">Set the value of the **Data Type** box of the `varFolderName` variable to **String**.</span></span>  
  
7.  <span data-ttu-id="5d2f3-116">回到 [控制流程]  索引標籤，按兩下 [資料夾的 Foreach 檔案]  容器。</span><span class="sxs-lookup"><span data-stu-id="5d2f3-116">Return to the **Control Flow** tab and double-click the **Foreach File in Folder** container.</span></span>  
  
8.  <span data-ttu-id="5d2f3-117">在 [ **Foreach 迴圈編輯器**] 的 [**集合**] 頁面上，按一下 [**運算式**]，然後按一下省略號按鈕\*\* ( ...] ) \*\*。</span><span class="sxs-lookup"><span data-stu-id="5d2f3-117">On the **Collection** page of the **Foreach Loop Editor**, click **Expressions**, and then click the ellipsis button **(...)**.</span></span>  
  
9. <span data-ttu-id="5d2f3-118">在 [**屬性運算式編輯器**] 中，按一下 [**屬性**] 清單，然後選取 [] `Directory` 。</span><span class="sxs-lookup"><span data-stu-id="5d2f3-118">In the **Property Expressions Editor**, click in the **Property** list, and select `Directory`.</span></span>  
  
10. <span data-ttu-id="5d2f3-119">在 [**運算式**] 方塊中，按一下省略號按鈕\*\* ( ...] ) \*\*。</span><span class="sxs-lookup"><span data-stu-id="5d2f3-119">In the **Expression** box, click the ellipsis button **(...)**.</span></span>  
  
11. <span data-ttu-id="5d2f3-120">在 [運算式產生器]\*\*\*\* 中，展開 [變數] 資料夾，將 **User::varFolderName** 變數拖曳至 [運算式]\*\*\*\* 方塊中。</span><span class="sxs-lookup"><span data-stu-id="5d2f3-120">In the **Expression Builder**, expand the Variables folder, and drag the variable **User::varFolderName** to the **Expression** box.</span></span>  
  
12. <span data-ttu-id="5d2f3-121">按一下 [確定]\*\*\*\* 來結束 [運算式產生器]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="5d2f3-121">Click **OK** to exit the **Expression Builder**.</span></span>  
  
13. <span data-ttu-id="5d2f3-122">按一下 [確定]\*\*\*\* 來結束 [屬性運算式編輯器]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="5d2f3-122">Click **OK** to exit the **Property Expressions Editor**.</span></span>  
  
14. <span data-ttu-id="5d2f3-123">按一下 [確定]\*\*\*\* 來結束 [Foreach 迴圈編輯器]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="5d2f3-123">Click **OK** to exit the **Foreach Loop Editor**.</span></span>  
  
### <a name="to-enable-package-configurations"></a><span data-ttu-id="5d2f3-124">若要啟用封裝組態</span><span class="sxs-lookup"><span data-stu-id="5d2f3-124">To enable package configurations</span></span>  
  
1.  <span data-ttu-id="5d2f3-125">在 [**專案] 功能表**上，按一下 [**轉換為封裝部署模型**]。</span><span class="sxs-lookup"><span data-stu-id="5d2f3-125">On the **Project Menu**, click **Convert to Package Deployment Model**.</span></span>  
  
2.  <span data-ttu-id="5d2f3-126">按一下警告提示上的 [確定]\*\*\*\*，並在轉換完成時按一下 [轉換為封裝部署模型]\*\*\*\* 對話方塊上的 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="5d2f3-126">Click **OK** on the warning prompt and, once the conversion is complete, click **OK** on the **Convert to Package Deployment Model** dialog.</span></span>  
  
3.  <span data-ttu-id="5d2f3-127">按一下 [[!INCLUDE[ssIS](../includes/ssis-md.md)] 設計師] 的 [控制流程]\*\*\*\* 索引標籤的背景。</span><span class="sxs-lookup"><span data-stu-id="5d2f3-127">Click the background of the **Control Flow** tab in [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer.</span></span>  
  
4.  <span data-ttu-id="5d2f3-128">在 [SSIS]  功能表上，按一下 [封裝組態]  。</span><span class="sxs-lookup"><span data-stu-id="5d2f3-128">On the **SSIS** menu, click **Package Configurations**.</span></span>  
  
5.  <span data-ttu-id="5d2f3-129">在 [封裝組態組合管理]\*\*\*\* 對話方塊中，選取 [啟用封裝組態]\*\*\*\*，然後按一下 [加入]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="5d2f3-129">In the **Package Configurations Organizer** dialog box, select **Enable Package Configurations**, and then click **Add**.</span></span>  
  
6.  <span data-ttu-id="5d2f3-130">在 [封裝組態精靈] 的歡迎使用頁面上，按一下 [下一步]  。</span><span class="sxs-lookup"><span data-stu-id="5d2f3-130">On the welcome page of the Package Configuration Wizard, click **Next**.</span></span>  
  
7.  <span data-ttu-id="5d2f3-131">在 [選取組態類型]  頁面上，確認 [組態類型]  是設為 [XML 組態檔]  。</span><span class="sxs-lookup"><span data-stu-id="5d2f3-131">On the **Select Configuration Type** page, verify that the **Configuration type** is set to **XML configuration file**.</span></span>  
  
8.  <span data-ttu-id="5d2f3-132">在 [選取組態類型]\*\*\*\* 頁面上，按一下 [瀏覽]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="5d2f3-132">On the **Select Configuration Type** page, click **Browse**.</span></span>  
  
9. <span data-ttu-id="5d2f3-133">根據預設，[選取組態檔位置]\*\*\*\* 對話方塊開啟時將顯示專案資料夾。</span><span class="sxs-lookup"><span data-stu-id="5d2f3-133">By default, the **Select Configuration File Location** dialog box will open to the project folder.</span></span>  
  
10. <span data-ttu-id="5d2f3-134">在 [選取組態檔位置]\*\*\*\* 對話方塊的 [檔案名稱]\*\*\*\* 中，輸入 **SSISTutorial**，然後按一下 [儲存]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="5d2f3-134">In the **Select Configuration File Location** dialog box, for **File name** type **SSISTutorial**, and then click **Save**.</span></span>  
  
11. <span data-ttu-id="5d2f3-135">在 [**選取設定類型**] 頁面上，按 **[下一步]。**</span><span class="sxs-lookup"><span data-stu-id="5d2f3-135">On the **Select Configuration Type** page, click **Next.**</span></span>  
  
12. <span data-ttu-id="5d2f3-136">在 [選取要匯出的屬性]\*\*\*\* 頁面的 [物件]\*\*\*\* 窗格中，依序展開 [變數]\*\*\*\*、[varFolderName]\*\*\*\* 和 [屬性]\*\*\*\*，然後選取 [值]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="5d2f3-136">On the **Select Properties to Export** page, in the **Objects** pane, expand **Variables**, expand **varFolderName**, expand **Properties**, and then select **Value**.</span></span>  
  
13. <span data-ttu-id="5d2f3-137">在 [選取要匯出的屬性]\*\*\*\* 頁面上，按一下 [下一步]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="5d2f3-137">On the **Select Properties to Export** page, click **Next**.</span></span>  
  
14. <span data-ttu-id="5d2f3-138">在 [正在完成精靈]\*\*\*\* 頁面上，輸入組態的組態名稱，例如 **SSIS 教學課程目錄組態**。</span><span class="sxs-lookup"><span data-stu-id="5d2f3-138">On the **Completing the Wizard** page, type a configuration name for the configuration, such as **SSIS Tutorial Directory configuration**.</span></span> <span data-ttu-id="5d2f3-139">這是顯示在 [封裝組態組合管理]\*\*\*\* 對話方塊中的組態名稱。</span><span class="sxs-lookup"><span data-stu-id="5d2f3-139">This is the configuration name that is displayed in the **Package Configuration Organizer** dialog box.</span></span>  
  
15. <span data-ttu-id="5d2f3-140">按一下 [完成] 。</span><span class="sxs-lookup"><span data-stu-id="5d2f3-140">Click **Finish**.</span></span>  
  
16. <span data-ttu-id="5d2f3-141">按一下 **關閉**。</span><span class="sxs-lookup"><span data-stu-id="5d2f3-141">Click **Close**.</span></span>  
  
17. <span data-ttu-id="5d2f3-142">此 wizard 會建立名為 SSISTutorial. Ssistutorial.dtsconfig 的設定檔，其中包含變數之的設定， `value` 接著會設定列舉值的 `Directory` 屬性。</span><span class="sxs-lookup"><span data-stu-id="5d2f3-142">The wizard creates a configuration file, named SSISTutorial.dtsConfig, that contains configuration settings for the `value` of the variable that in turn sets the `Directory` property of the enumerator.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="5d2f3-143">組態檔通常包含關於封裝屬性的複雜資訊，但在此教學課程中，唯一的組態資訊應該是</span><span class="sxs-lookup"><span data-stu-id="5d2f3-143">A configuration file typically contains complex information about the package properties, but for this tutorial the only configuration information should be</span></span>  
    > <span data-ttu-id="5d2f3-144"><Configuration ConfiguredType="Property"</span><span class="sxs-lookup"><span data-stu-id="5d2f3-144"><Configuration ConfiguredType="Property"</span></span>  
    > <span data-ttu-id="5d2f3-145">Path = "\Package.Variables [User：： varFolderName]。Properties [Value] "ValueType =" 字串 "\></span><span class="sxs-lookup"><span data-stu-id="5d2f3-145">Path="\Package.Variables[User::varFolderName].Properties[Value]" ValueType="String"\></span></span>  
    >  \<ConfiguredValue>\</ConfiguredValue>  
    > <span data-ttu-id="5d2f3-146">\</Configuration>.</span><span class="sxs-lookup"><span data-stu-id="5d2f3-146">\</Configuration>.</span></span>  
  
### <a name="to-create-and-populate-a-new-sample-data-folder"></a><span data-ttu-id="5d2f3-147">若要建立及擴展新的範例資料夾</span><span class="sxs-lookup"><span data-stu-id="5d2f3-147">To create and populate a new sample data folder</span></span>  
  
1.  <span data-ttu-id="5d2f3-148">在 Windows Explorer 中，于磁片磁碟機的根目錄層級 (例如 C： \\) ，建立名為的新資料夾 `New Sample Data` 。</span><span class="sxs-lookup"><span data-stu-id="5d2f3-148">In Windows Explorer, at the root level of your drive (for example, C:\\), create a new folder named `New Sample Data`.</span></span>  
  
2.  <span data-ttu-id="5d2f3-149">尋找電腦上的範例檔案，並從資料夾複製三個檔案。</span><span class="sxs-lookup"><span data-stu-id="5d2f3-149">Locate the sample files on your computer and copy three of the files from the folder.</span></span>  
  
3.  <span data-ttu-id="5d2f3-150">在 `New Sample Data` 資料夾中，貼上複製的檔案。</span><span class="sxs-lookup"><span data-stu-id="5d2f3-150">In the `New Sample Data` folder, paste the copied files.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="5d2f3-151">本課程的下一項工作</span><span class="sxs-lookup"><span data-stu-id="5d2f3-151">Next Task in Lesson</span></span>  
 [<span data-ttu-id="5d2f3-152">步驟 3：修改 Directory 屬性組態值</span><span class="sxs-lookup"><span data-stu-id="5d2f3-152">Step 3: Modifying the Directory Property Configuration Value</span></span>](lesson-5-3-modifying-the-directory-property-configuration-value.md)  
  
  
