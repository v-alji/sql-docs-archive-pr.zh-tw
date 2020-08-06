---
title: 加入及驗證資料連線或資料來源 (報表產生器和 SSRS) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 1d3b2573-e29d-480d-9dde-d26379c86618
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d86b3e6598c12545f0e24ef1d162eeb1131bd15d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585091"
---
# <a name="add-and-verify-a-data-connection-or-data-source-report-builder-and-ssrs"></a><span data-ttu-id="a9b4c-102">加入及驗證資料連接或資料來源 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="a9b4c-102">Add and Verify a Data Connection or Data Source (Report Builder and SSRS)</span></span>
  <span data-ttu-id="a9b4c-103">在報表產生器中，您可以從報表伺服器加入共用資料來源，或是為您的報表建立內嵌資料來源。</span><span class="sxs-lookup"><span data-stu-id="a9b4c-103">In Report Builder, you can add a shared data source from the report server or create an embedded data source for your report.</span></span> <span data-ttu-id="a9b4c-104">在報表設計師中，您可以建立共用資料來源或內嵌資料來源，並將它部署至報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="a9b4c-104">In Report Designer, you can create a shared data source or an embedded data source and deploy it to a report server.</span></span>  
  
 <span data-ttu-id="a9b4c-105">若要將共用資料來源加入至報表中，請瀏覽至報表伺服器，並選取共用資料來源。</span><span class="sxs-lookup"><span data-stu-id="a9b4c-105">To add a shared data source to your report, browse to a report server and select a shared data source.</span></span> <span data-ttu-id="a9b4c-106">報表中的共用資料來源會指向報表伺服器上的共用資料來源定義。</span><span class="sxs-lookup"><span data-stu-id="a9b4c-106">The shared data source in your report points to the shared data source definition on the report server.</span></span>  
  
 <span data-ttu-id="a9b4c-107">若要建立內嵌資料來源，您必須具有外部資料來源的連接資訊，而且必須知道存取資料必須擁有哪些權限。</span><span class="sxs-lookup"><span data-stu-id="a9b4c-107">To create an embedded data source, you must have connection information to the external source of data and you must know which permissions you need to access the data.</span></span> <span data-ttu-id="a9b4c-108">這項資訊通常是來自於資料來源的擁有者。</span><span class="sxs-lookup"><span data-stu-id="a9b4c-108">This information usually comes from the owner of the data source.</span></span> <span data-ttu-id="a9b4c-109">您可以測試此連接，以確認指定的認證是否足夠。</span><span class="sxs-lookup"><span data-stu-id="a9b4c-109">You can test the connection to verify that the credentials that are specified are sufficient.</span></span>  
  
 <span data-ttu-id="a9b4c-110">如需詳細資訊，請參閱[報表產生器中的資料連線、資料來源及連接字串](../data-connections-data-sources-and-connection-strings-in-report-builder.md)和[在報表產生器中指定認證](../specify-credentials-in-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="a9b4c-110">For more information, see [Data Connections, Data Sources, and Connection Strings in Report Builder](../data-connections-data-sources-and-connection-strings-in-report-builder.md) and [Specify Credentials in Report Builder](../specify-credentials-in-report-builder.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-create-a-reference-to-a-shared-data-source"></a><span data-ttu-id="a9b4c-111">建立共用資料來源的參考</span><span class="sxs-lookup"><span data-stu-id="a9b4c-111">To create a reference to a shared data source</span></span>  
  
1.  <span data-ttu-id="a9b4c-112">在 [報表資料] 窗格的工具列上，按一下 **[新增]** ，然後按一下 **[資料來源]** 。</span><span class="sxs-lookup"><span data-stu-id="a9b4c-112">On the toolbar in the Report Data pane, click **New,** and then click **Data Source**.</span></span> <span data-ttu-id="a9b4c-113">**[資料來源屬性]** 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="a9b4c-113">The **Data Source Properties** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="a9b4c-114">在 **[名稱]** 文字方塊中，輸入資料來源的名稱。</span><span class="sxs-lookup"><span data-stu-id="a9b4c-114">In the **Name** text box, type a name for the data source.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a9b4c-115">這個名稱會儲存在本機報表定義中。</span><span class="sxs-lookup"><span data-stu-id="a9b4c-115">This name is saved in the local report definition.</span></span> <span data-ttu-id="a9b4c-116">這個名稱不是共用資料來源在報表伺服器上的名稱。</span><span class="sxs-lookup"><span data-stu-id="a9b4c-116">This name is not the name of the shared data source on the report server.</span></span>  
  
3.  <span data-ttu-id="a9b4c-117">選取 **[使用共用連接或報表模型]** 。</span><span class="sxs-lookup"><span data-stu-id="a9b4c-117">Select **Use a shared connection or report model**.</span></span> <span data-ttu-id="a9b4c-118">隨即出現最近使用的共用資料來源和報表模型清單。</span><span class="sxs-lookup"><span data-stu-id="a9b4c-118">The list of recently used shared data sources and report models appears.</span></span> <span data-ttu-id="a9b4c-119">若要從報表伺服器選取其中一個項目，請按一下 **[瀏覽]** 並瀏覽至報表伺服器上提供共用資料來源的資料夾。</span><span class="sxs-lookup"><span data-stu-id="a9b4c-119">To select one from a report server, click **Browse** and browse to the folder on the report server where shared data sources are available.</span></span>  
  
4.  <span data-ttu-id="a9b4c-120">選取該共用資料來源，然後按一下 **[開啟]** 。</span><span class="sxs-lookup"><span data-stu-id="a9b4c-120">Select the shared data source and then click **Open**.</span></span>  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
 <span data-ttu-id="a9b4c-121">資料來源會出現在 [報表資料] 窗格中。</span><span class="sxs-lookup"><span data-stu-id="a9b4c-121">The data source appears in the Report Data pane.</span></span>  
  
### <a name="to-create-an-embedded-data-source"></a><span data-ttu-id="a9b4c-122">建立內嵌資料來源</span><span class="sxs-lookup"><span data-stu-id="a9b4c-122">To create an embedded data source</span></span>  
  
1.  <span data-ttu-id="a9b4c-123">在 [報表資料] 窗格的工具列上，按一下 [**新增**]，然後按一下 [**資料來源**]。</span><span class="sxs-lookup"><span data-stu-id="a9b4c-123">On the toolbar in the Report Data pane, click **New**, and then click **Data Source**.</span></span> <span data-ttu-id="a9b4c-124">**[資料來源屬性]** 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="a9b4c-124">The **Data Source Properties** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="a9b4c-125">在 **[名稱]** 文字方塊中，輸入資料來源的名稱或接受預設值。</span><span class="sxs-lookup"><span data-stu-id="a9b4c-125">In the **Name** text box, type a name for the data source or accept the default.</span></span>  
  
3.  <span data-ttu-id="a9b4c-126">確認已選取 **[使用內嵌於我的報表的連接]** 。</span><span class="sxs-lookup"><span data-stu-id="a9b4c-126">Verify that **Use a connection embedded in my report** is selected.</span></span>  
  
    1.  <span data-ttu-id="a9b4c-127">從 [選取連線類型]\*\*\*\* 下拉式清單中，選取資料來源類型，例如 [Microsoft SQL Server]\*\*\*\* 或 [OLE DB]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a9b4c-127">From the **Select connection type** drop-down list, select a data source type; for example, **Microsoft SQL Server** or **OLE DB**.</span></span>  
  
    2.  <span data-ttu-id="a9b4c-128">使用以下其中一個替代方式來指定連接字串：</span><span class="sxs-lookup"><span data-stu-id="a9b4c-128">Specify a connection string by using one of the following alternatives:</span></span>  
  
    -   <span data-ttu-id="a9b4c-129">在 **[連接字串]** 文字方塊中直接輸入連接字串。</span><span class="sxs-lookup"><span data-stu-id="a9b4c-129">Type the connection string directly in the **Connection string** text box.</span></span> <span data-ttu-id="a9b4c-130">如需連接字串範例的清單，請參閱 [報表產生器中的資料連接、資料來源及連接字串](../data-connections-data-sources-and-connection-strings-in-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="a9b4c-130">For a list of example connection strings, see [Data Connections, Data Sources, and Connection Strings in Report Builder](../data-connections-data-sources-and-connection-strings-in-report-builder.md).</span></span>  
  
    -   <span data-ttu-id="a9b4c-131">按一下運算式 (**fx)** 按鈕，即可建立一個評估為連接字串的運算式。</span><span class="sxs-lookup"><span data-stu-id="a9b4c-131">Click the expression (**fx)** button to create an expression that evaluates to a connection string.</span></span> <span data-ttu-id="a9b4c-132">在 **[運算式]** 對話方塊的 [運算式] 窗格內，輸入運算式。</span><span class="sxs-lookup"><span data-stu-id="a9b4c-132">In the **Expression** dialog box, type the expression in the Expression pane.</span></span> [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
    -   <span data-ttu-id="a9b4c-133">按一下 **[建立]** ，針對您在步驟 2 中選擇的資料來源類型開啟 **[連接屬性]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="a9b4c-133">Click **Build** to open the **Connection Properties** dialog box for the data source type that you chose in step 2.</span></span>  
  
         <span data-ttu-id="a9b4c-134">依照此資料來源類型適合的情況，填入 **[連接屬性]** 對話方塊中的欄位。</span><span class="sxs-lookup"><span data-stu-id="a9b4c-134">Fill in the fields in the **Connection Properties** dialog box as appropriate for the data source type.</span></span> <span data-ttu-id="a9b4c-135">連接屬性包括資料來源的類型、資料來源的名稱以及要使用的認證。</span><span class="sxs-lookup"><span data-stu-id="a9b4c-135">Connection properties include the type of data source, the name of the data source, and the credentials to use.</span></span> <span data-ttu-id="a9b4c-136">當您在此對話方塊中指定值之後，請按一下 **[測試連接]** 來確認此資料來源確實可用，而且您指定的認證正確無誤。</span><span class="sxs-lookup"><span data-stu-id="a9b4c-136">After you specify values in this dialog box, click **Test Connection** to verify that the data source is available and that the credentials you specified are correct.</span></span>  
  
4.  <span data-ttu-id="a9b4c-137">按一下 **[認證]**。</span><span class="sxs-lookup"><span data-stu-id="a9b4c-137">Click **Credentials**.</span></span>  
  
     <span data-ttu-id="a9b4c-138">指定用於這個資料來源的認證。</span><span class="sxs-lookup"><span data-stu-id="a9b4c-138">Specify the credentials to use for this data source.</span></span> <span data-ttu-id="a9b4c-139">資料來源的擁有者會選擇支援的認證類型。</span><span class="sxs-lookup"><span data-stu-id="a9b4c-139">The owner of the data source chooses the type of credentials that are supported.</span></span> <span data-ttu-id="a9b4c-140">在某些情況下，資料來源的擁有者會在報表伺服器上維護共用資料來源，並且使用您可以使用的認證來設定資料來源。</span><span class="sxs-lookup"><span data-stu-id="a9b4c-140">In some cases, the owner of the data source maintains a shared data source on a report server and configures the data source with credentials that you can use.</span></span> <span data-ttu-id="a9b4c-141">如需這項資訊，請連絡資料來源擁有者。</span><span class="sxs-lookup"><span data-stu-id="a9b4c-141">Contact the data source owner for this information.</span></span> <span data-ttu-id="a9b4c-142">如需詳細資訊，請參閱 [在報表產生器中指定認證](../specify-credentials-in-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="a9b4c-142">For more information, see [Specify Credentials in Report Builder](../specify-credentials-in-report-builder.md).</span></span>  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
 <span data-ttu-id="a9b4c-143">資料來源會出現在 [報表資料] 窗格中。</span><span class="sxs-lookup"><span data-stu-id="a9b4c-143">The data source appears in the Report Data pane.</span></span>  
  
### <a name="to-verify-a-data-connection"></a><span data-ttu-id="a9b4c-144">若要驗證資料連接</span><span class="sxs-lookup"><span data-stu-id="a9b4c-144">To verify a data connection</span></span>  
  
1.  <span data-ttu-id="a9b4c-145">在工具列的 [報表資料] 窗格中，按兩下此資料來源。</span><span class="sxs-lookup"><span data-stu-id="a9b4c-145">On the toolbar in the Report Data pane, double-click the data source.</span></span> <span data-ttu-id="a9b4c-146">**[資料來源屬性]** 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="a9b4c-146">The **Data Source Properties** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="a9b4c-147">按一下 **[測試連接]** 。</span><span class="sxs-lookup"><span data-stu-id="a9b4c-147">Click **Test Connection**.</span></span>  
  
3.  <span data-ttu-id="a9b4c-148">如果連接成功，將會出現下列訊息：「成功建立連接」。</span><span class="sxs-lookup"><span data-stu-id="a9b4c-148">If the connection is successful, the following message appears: "Connection created successfully".</span></span> [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
4.  <span data-ttu-id="a9b4c-149">如果連接未能成功，將會出現下列訊息：「無法連接到資料來源」。</span><span class="sxs-lookup"><span data-stu-id="a9b4c-149">If the connection is not successful, the following message appears: "Unable to connect to the data source."</span></span>  
  
5.  <span data-ttu-id="a9b4c-150">按一下 **[詳細資料]**，並使用該資訊來更正問題。</span><span class="sxs-lookup"><span data-stu-id="a9b4c-150">Click **Details**, and use the information to correct the issue.</span></span>  
  
     <span data-ttu-id="a9b4c-151">如需詳細資訊，請參閱 [在報表產生器中指定認證](../specify-credentials-in-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="a9b4c-151">For more information, see [Specify Credentials in Report Builder](../specify-credentials-in-report-builder.md).</span></span>  
  
6.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="a9b4c-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a9b4c-152">See Also</span></span>  
 <span data-ttu-id="a9b4c-153">[將資料加入報表 &#40;報表產生器和 SSRS&#41;](report-datasets-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="a9b4c-153">[Add Data to a Report &#40;Report Builder and SSRS&#41;](report-datasets-ssrs.md) </span></span>  
 <span data-ttu-id="a9b4c-154">[報表內嵌資料集和共用資料集 &#40;報表產生器和 SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="a9b4c-154">[Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="a9b4c-155">[尋找、查看和管理報表 &#40;報表產生器和 SSRS &#41;](../report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="a9b4c-155">[Finding, Viewing, and Managing Reports &#40;Report Builder and SSRS &#41;](../report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="a9b4c-156">報表產生器中的資料連接、資料來源及連接字串</span><span class="sxs-lookup"><span data-stu-id="a9b4c-156">Data Connections, Data Sources, and Connection Strings in Report Builder</span></span>](../data-connections-data-sources-and-connection-strings-in-report-builder.md)  
  
  
