---
title: 步驟 2：新增和設定 Foreach 迴圈容器 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 88a973cc-0f23-4ecf-adb6-5b06279c2df6
author: chugugrace
ms.author: chugu
ms.openlocfilehash: de5e8875c43edda618ccef4839c88c3b84a003cf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592119"
---
# <a name="step-2-adding-and-configuring-the-foreach-loop-container"></a><span data-ttu-id="73880-102">步驟 2:新增和設定 Foreach 迴圈容器</span><span class="sxs-lookup"><span data-stu-id="73880-102">Step 2: Adding and Configuring the Foreach Loop Container</span></span>
  <span data-ttu-id="73880-103">在這項工作中，您將加入功能，於一般檔案的資料夾中形成迴圈，並對每個一般檔案套用在第 1 課使用的相同資料流程轉換。</span><span class="sxs-lookup"><span data-stu-id="73880-103">In this task, you will add the ability to loop through a folder of flat files and apply the same data flow transformation used in Lesson 1 to each of those flat files.</span></span> <span data-ttu-id="73880-104">您的作法是在控制流程中加入和設定 Foreach 迴圈容器。</span><span class="sxs-lookup"><span data-stu-id="73880-104">You do this by adding and configuring a Foreach Loop container to the control flow.</span></span>  
  
 <span data-ttu-id="73880-105">您加入的 Foreach 迴圈容器必須能夠連接到資料夾的每個一般檔案。</span><span class="sxs-lookup"><span data-stu-id="73880-105">The Foreach Loop container that you add must be able to connect to each flat file in the folder.</span></span> <span data-ttu-id="73880-106">由於資料夾的所有檔案都具有相同格式，所以 Foreach 迴圈容器可以使用相同的一般檔案連接管理員來連接每一個檔案。</span><span class="sxs-lookup"><span data-stu-id="73880-106">Because all the files in the folder have the same format, the Foreach Loop container can use the same Flat File connection manager to connect to each of these files.</span></span> <span data-ttu-id="73880-107">容器要使用的一般檔案連接管理員與您在第 1 課建立的一般檔案連接管理員相同。</span><span class="sxs-lookup"><span data-stu-id="73880-107">The Flat File connection manager that the container will use is the same Flat File connection manager that you created in Lesson 1.</span></span>  
  
 <span data-ttu-id="73880-108">目前，第 1 課的一般檔案連接管理員只連接一個特定的一般檔案。</span><span class="sxs-lookup"><span data-stu-id="73880-108">Currently, the Flat File connection manager from Lesson 1 connects to only one, specific flat file.</span></span> <span data-ttu-id="73880-109">若要反覆連接到資料夾的每個一般檔案，您必須同時設定 Foreach 迴圈容器和一般檔案連接管理員，如下所示：</span><span class="sxs-lookup"><span data-stu-id="73880-109">To iteratively connect to each flat file in the folder, you will have to configure both the Foreach Loop container and the Flat File connection manager as follows:</span></span>  
  
-   <span data-ttu-id="73880-110">**Foreach 迴圈容器** ：您將容器的列舉值對應至使用者定義的套件變數。</span><span class="sxs-lookup"><span data-stu-id="73880-110">**Foreach Loop container:** You will map the enumerated value of the container to a user-defined package variable.</span></span> <span data-ttu-id="73880-111">然後容器會使用此使用者自訂變數，動態修改一般檔案連接管理員的 `ConnectionString` 屬性，並反覆連接到資料夾的每個一般檔案。</span><span class="sxs-lookup"><span data-stu-id="73880-111">The container will then use this user-defined variable to dynamically modify the `ConnectionString` property of the Flat File connection manager and iteratively connect to each flat file in the folder.</span></span>  
  
-   <span data-ttu-id="73880-112">一般檔案**連線管理員：** 您將使用使用者定義變數來填入連接管理員的屬性，以修改第1課所建立的連線管理員 `ConnectionString` 。</span><span class="sxs-lookup"><span data-stu-id="73880-112">**Flat File connection manager:** You will modify the connection manager that was created in Lesson 1 by using a user-defined variable to populate the connection manager's `ConnectionString` property.</span></span>  
  
 <span data-ttu-id="73880-113">這項工作中的程序說明如何建立和修改 Foreach 迴圈容器，以利用使用者自訂封裝變數，並且將資料流程工作加入迴圈中。</span><span class="sxs-lookup"><span data-stu-id="73880-113">The procedures in this task show you how to create and modify the Foreach Loop container to use a user-defined package variable and to add the data flow task to the loop.</span></span> <span data-ttu-id="73880-114">在下一項工作中，您會學到如何修改一般檔案連接管理員來使用使用者自訂變數。</span><span class="sxs-lookup"><span data-stu-id="73880-114">You will learn how to modify the Flat File connection manager to use a user-defined variable in the next task.</span></span>  
  
 <span data-ttu-id="73880-115">對封裝做了這些修改之後，當封裝執行時，Foreach 迴圈容器將反覆進行範例資料夾內的檔案集合。</span><span class="sxs-lookup"><span data-stu-id="73880-115">After you have made these modifications to the package, when the package is run, the Foreach Loop Container will iterate through the collection of files in the Sample Data folder.</span></span> <span data-ttu-id="73880-116">每次發現符合準則的檔案時，Foreach 迴圈容器就會在使用者自訂變數中填入檔案名稱，將使用者自訂變數對應至 [範例貨幣資料一般檔案] 連接管理員的 `ConnectionString` 屬性，然後對該檔案執行資料流程。</span><span class="sxs-lookup"><span data-stu-id="73880-116">Each time a file is found that matches the criteria, the Foreach Loop Container will populate the user-defined variable with the file name, map the user-defined variable to the `ConnectionString` property of the Sample Currency Data Flat File connection manager, and then run the data flow against that file.</span></span> <span data-ttu-id="73880-117">因此，在 Foreach 迴圈的每個反覆運算中，資料流程工作將取用不同的一般檔案。</span><span class="sxs-lookup"><span data-stu-id="73880-117">Therefore, in each iteration of the Foreach Loop the Data Flow task will consume a different flat file.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="73880-118">因為 [!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 隔開控制流程與資料流程，所以您要加入控制流程中的任何迴圈都不需要對資料流程做修改。</span><span class="sxs-lookup"><span data-stu-id="73880-118">Because [!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] separates control flow from data flow, any looping that you add to the control flow will not require modification to the data flow.</span></span> <span data-ttu-id="73880-119">因此，您在第 1 課建立的資料流程不必改變。</span><span class="sxs-lookup"><span data-stu-id="73880-119">Therefore, the data flow that you created in Lesson 1 does not have to be changed.</span></span>  
  
### <a name="to-add-a-foreach-loop-container"></a><span data-ttu-id="73880-120">若要加入 Foreach 迴圈容器</span><span class="sxs-lookup"><span data-stu-id="73880-120">To add a Foreach Loop container</span></span>  
  
1.  <span data-ttu-id="73880-121">在 SQL Server Data Tools\*\*\*\* 中，請按一下 [控制流程]\*\*\*\* 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="73880-121">In **SQL Server Data Tools**, click the **Control Flow** tab.</span></span>  
  
2.  <span data-ttu-id="73880-122">在 [SSIS 工具箱]  中，展開 [容器]  ，然後將 [Foreach 迴圈容器]  拖曳至 [控制流程]  索引標籤的設計介面中。</span><span class="sxs-lookup"><span data-stu-id="73880-122">In the **SSIS Toolbox**, expand **Containers**, and then drag a **Foreach Loop Container** onto the design surface of the **Control Flow** tab.</span></span>  
  
3.  <span data-ttu-id="73880-123">以滑鼠右鍵按一下剛新增的 [Foreach 迴圈容器]\*\*\*\*，並選取 [編輯]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="73880-123">Right-click the newly added **Foreach Loop Container** and select **Edit**.</span></span>  
  
4.  <span data-ttu-id="73880-124">在 [ **Foreach 迴圈編輯器**] 對話方塊的 [**一般**] 頁面上，針對 [**名稱**] 輸入 `Foreach File in Folder` 。</span><span class="sxs-lookup"><span data-stu-id="73880-124">In the **Foreach Loop Editor** dialog box, on the **General** page, for **Name**, enter `Foreach File in Folder`.</span></span> <span data-ttu-id="73880-125">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="73880-125">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="73880-126">以滑鼠右鍵按一下 [Foreach 迴圈] 容器，按一下 [**屬性**]，然後在 [屬性視窗中，確認 `LocaleID` 屬性已設為 [\*\*英文] ([美國]) \*\*。</span><span class="sxs-lookup"><span data-stu-id="73880-126">Right-click the Foreach Loop container, click **Properties**, and in the Properties window, verify that the `LocaleID` property is set to **English (United States)**.</span></span>  
  
### <a name="to-configure-the-enumerator-for-the-foreach-loop-container"></a><span data-ttu-id="73880-127">若要設定 Foreach 迴圈容器的列舉值</span><span class="sxs-lookup"><span data-stu-id="73880-127">To configure the enumerator for the Foreach Loop container</span></span>  
  
1.  <span data-ttu-id="73880-128">按兩下 [Foreach File in Folder] 以重新開啟 [ **Foreach 迴圈編輯器**]。</span><span class="sxs-lookup"><span data-stu-id="73880-128">Double-click Foreach File in Folder to reopen the **Foreach Loop Editor**.</span></span>  
  
2.  <span data-ttu-id="73880-129">按一下 [集合]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="73880-129">Click **Collection**.</span></span>  
  
3.  <span data-ttu-id="73880-130">在 [集合]  頁面上，選取 [Foreach 檔案列舉值]  。</span><span class="sxs-lookup"><span data-stu-id="73880-130">On the **Collection** page, select **Foreach File Enumerator**.</span></span>  
  
4.  <span data-ttu-id="73880-131">在 [列舉值組態]\*\*\*\* 群組中，按一下 [瀏覽]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="73880-131">In the **Enumerator configuration** group, click **Browse**.</span></span>  
  
5.  <span data-ttu-id="73880-132">在 [瀏覽資料夾]\*\*\*\* 對話方塊中，尋找電腦上包含 Currency_\*.txt 檔案的資料夾。</span><span class="sxs-lookup"><span data-stu-id="73880-132">In the **Browse for Folder** dialog box, locate the folder on your machine that contains the Currency_\*.txt files.</span></span>  
  
     <span data-ttu-id="73880-133">此範例資料隨附在 [!INCLUDE[ssIS](../includes/ssis-md.md)] 課程封裝中。</span><span class="sxs-lookup"><span data-stu-id="73880-133">This sample data is included with the [!INCLUDE[ssIS](../includes/ssis-md.md)] lesson packages.</span></span> <span data-ttu-id="73880-134">若要下載範例資料和課程封裝，請執行下列動作。</span><span class="sxs-lookup"><span data-stu-id="73880-134">To download the sample data and the lesson packages, do the following.</span></span>  
  
    1.  <span data-ttu-id="73880-135">導覽至 [Integration Services 產品範例](https://go.microsoft.com/fwlink/?LinkId=275027)</span><span class="sxs-lookup"><span data-stu-id="73880-135">Navigate to [Integration Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=275027)</span></span>  
  
    2.  <span data-ttu-id="73880-136">按一下 [**下載**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="73880-136">Click the **DOWNLOADS** tab.</span></span>  
  
    3.  <span data-ttu-id="73880-137">按一下超連結 " https://msftisprodsamples.codeplex.com/downloads/get/578097 " SQL2012.Integration_Services.Create_Simple_ETL_Tutorial.Sample.zip 檔案。</span><span class="sxs-lookup"><span data-stu-id="73880-137">Click the  HYPERLINK "https://msftisprodsamples.codeplex.com/downloads/get/578097" SQL2012.Integration_Services.Create_Simple_ETL_Tutorial.Sample.zip file.</span></span>  
  
6.  <span data-ttu-id="73880-138">在 [檔案]\*\*\*\* 方塊中，輸入 **Currency_\*.txt**。</span><span class="sxs-lookup"><span data-stu-id="73880-138">In the **Files** box, type **Currency_\*.txt**.</span></span>  
  
### <a name="to-map-the-enumerator-to-a-user-defined-variable"></a><span data-ttu-id="73880-139">若要將列舉值對應至使用者自訂變數</span><span class="sxs-lookup"><span data-stu-id="73880-139">To map the enumerator to a user-defined variable</span></span>  
  
1.  <span data-ttu-id="73880-140">按一下 [變數對應]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="73880-140">Click **Variable Mappings**.</span></span>  
  
2.  <span data-ttu-id="73880-141">在 [**變數**對應] 頁面的 [**變數**] 資料行中，按一下空白資料格，然後選取 **\<New Variable...>** 。</span><span class="sxs-lookup"><span data-stu-id="73880-141">On the **Variable Mappings** page, in the **Variable** column, click the empty cell and select **\<New Variable...>**.</span></span>  
  
3.  <span data-ttu-id="73880-142">在 [**加入變數**] 對話方塊中，針對 [**名稱**] 輸入 `varFileName` 。</span><span class="sxs-lookup"><span data-stu-id="73880-142">In the **Add Variable** dialog box, for **Name**, type `varFileName`.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="73880-143">變數名稱會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="73880-143">Variable names are case sensitive.</span></span>  
  
4.  <span data-ttu-id="73880-144">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="73880-144">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="73880-145">再按一下 [確定]\*\*\*\* 來結束 [Foreach 迴圈編輯器]\*\*\*\* 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="73880-145">Click **OK** again to exit the **Foreach Loop Editor** dialog box.</span></span>  
  
### <a name="to-add-the-data-flow-task-to-the-loop"></a><span data-ttu-id="73880-146">若要將資料流程工作加入迴圈中</span><span class="sxs-lookup"><span data-stu-id="73880-146">To add the data flow task to the loop</span></span>  
  
-   <span data-ttu-id="73880-147">將 [**解壓縮範例貨幣資料**] 資料流程工作拖曳至 [Foreach 迴圈] 容器現在已重新命名 `Foreach File in Folder` 。</span><span class="sxs-lookup"><span data-stu-id="73880-147">Drag the **Extract Sample Currency Data** data flow task onto the Foreach Loop container now renamed `Foreach File in Folder`.</span></span>  
  
## <a name="next-lesson-task"></a><span data-ttu-id="73880-148">下一課的工作</span><span class="sxs-lookup"><span data-stu-id="73880-148">Next Lesson Task</span></span>  
 [<span data-ttu-id="73880-149">步驟 3：修改一般檔案連線管理員</span><span class="sxs-lookup"><span data-stu-id="73880-149">Step 3: Modifying the Flat File Connection Manager</span></span>](lesson-2-3-modifying-the-flat-file-connection-manager.md)  
  
## <a name="see-also"></a><span data-ttu-id="73880-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="73880-150">See Also</span></span>  
 <span data-ttu-id="73880-151">[設定 Foreach 迴圈容器](control-flow/foreach-loop-container.md) </span><span class="sxs-lookup"><span data-stu-id="73880-151">[Configure a Foreach Loop Container](control-flow/foreach-loop-container.md) </span></span>  
 [<span data-ttu-id="73880-152">在封裝中使用變數</span><span class="sxs-lookup"><span data-stu-id="73880-152">Use Variables in Packages</span></span>](use-variables-in-packages.md)  
  
