---
title: 將清理專案值匯入定義域 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
f1_keywords:
- sql12.dqs.kb.importprojectvalues.f1
ms.assetid: f23e38e2-39e0-42d7-abd5-34d8fcca5d2a
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 38616da5a0a8fb9c8f149d9f55a08b63dee5ff6a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700252"
---
# <a name="import-cleansing-project-values-into-a-domain"></a><span data-ttu-id="52e4a-102">將清理專案值匯入定義域中</span><span class="sxs-lookup"><span data-stu-id="52e4a-102">Import Cleansing Project Values into a Domain</span></span>
  <span data-ttu-id="52e4a-103">在 [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) 中，您可以將清理程序期間，於資料品質清理專案或 Integration Services 封裝 (包含 DQS 清理元件) 中所收集的資料品質知識，匯入定義域中。</span><span class="sxs-lookup"><span data-stu-id="52e4a-103">In [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS), you can import data quality knowledge gathered during the cleansing process in a data quality cleansing project or an Integration Services package containing the DQS Cleansing component into a domain.</span></span> <span data-ttu-id="52e4a-104">如此可確保可靠的知識不會遺失，而且會持續改良知識庫。</span><span class="sxs-lookup"><span data-stu-id="52e4a-104">This ensures that trusted knowledge is not lost, and that the knowledge base is continually improved.</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="52e4a-105">開始之前</span><span class="sxs-lookup"><span data-stu-id="52e4a-105">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="52e4a-106">必要條件</span><span class="sxs-lookup"><span data-stu-id="52e4a-106">Prerequisites</span></span>  
  
-   <span data-ttu-id="52e4a-107">若要將清理專案值匯入定義域，您必須已經在 Data Quality Client 或 Integration Services 封裝 (包含 DQS 清理元件) 的清理專案中使用該定義域。</span><span class="sxs-lookup"><span data-stu-id="52e4a-107">To import cleansing project values into a domain, the domain must have been used in the cleansing project in Data Quality Client or in the Integration Services package containing a DQS Cleansing component.</span></span>  
  
-   <span data-ttu-id="52e4a-108">您必須已經順利執行完 Data Quality Client 或 Integration Services 封裝 (包含 DQS 清理元件) 中的清理專案。</span><span class="sxs-lookup"><span data-stu-id="52e4a-108">The cleansing project in Data Quality Client or the Integration Services package containing the DQS Cleansing component must have successfully completed.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="52e4a-109">Security</span><span class="sxs-lookup"><span data-stu-id="52e4a-109">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="52e4a-110">權限</span><span class="sxs-lookup"><span data-stu-id="52e4a-110">Permissions</span></span>  
 <span data-ttu-id="52e4a-111">您必須擁有 DQS_MAIN 資料庫的 dqs_kb_editor 角色或 dqs_administrator 角色，才能將清理程序期間所收集的資料品質知識匯入定義域中。</span><span class="sxs-lookup"><span data-stu-id="52e4a-111">You must have the dqs_kb_editor or the dqs_administrator role on the DQS_MAIN database to import data quality knowledge gathered during the cleansing process into a domain.</span></span>  
  
##  <a name="import-cleansing-project-values"></a><a name="Import"></a> <span data-ttu-id="52e4a-112">匯入清理專案值</span><span class="sxs-lookup"><span data-stu-id="52e4a-112">Import Cleansing Project Values</span></span>  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]<span data-ttu-id="52e4a-113">[執行 Data Quality Client 應用程式](../../2014/data-quality-services/run-the-data-quality-client-application.md)。</span><span class="sxs-lookup"><span data-stu-id="52e4a-113">[Run the Data Quality Client Application](../../2014/data-quality-services/run-the-data-quality-client-application.md).</span></span>  
  
2.  <span data-ttu-id="52e4a-114">在 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 首頁畫面中，於 [定義域管理] 活動中開啟知識庫。</span><span class="sxs-lookup"><span data-stu-id="52e4a-114">In the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen, open a knowledge base in the Domain Management activity.</span></span>  
  
3.  <span data-ttu-id="52e4a-115">如果您要將值加入至現有的定義域，請在定義域清單中選取定義域。</span><span class="sxs-lookup"><span data-stu-id="52e4a-115">If adding values to an existing domain, select the domain in the domain list.</span></span>  
  
4.  <span data-ttu-id="52e4a-116">按一下 **[定義域值]** 索引標籤、按一下圖示列中的 **[匯入值]** 圖示，然後按一下 **[匯入專案值]**。</span><span class="sxs-lookup"><span data-stu-id="52e4a-116">Click the **Domain Values** tab, click the **Import Values** icon in the icon bar, and then click **Import project values**.</span></span> <span data-ttu-id="52e4a-117">**[匯入專案值]** 對話方塊隨即顯示，並提供使用定義域進行清理之資料品質專案和 Integration Services 封裝的清單。</span><span class="sxs-lookup"><span data-stu-id="52e4a-117">The **Import Project Values** dialog box appears with a list of data quality projects and Integration Services packages that were cleansed using the domain.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="52e4a-118"> 如果尚未使用定義域或是其連結的任何定義域建立任何專案，或者專案尚未完成，將無法使用 **[匯入專案值]** 選項。</span><span class="sxs-lookup"><span data-stu-id="52e4a-118">If no project has been created using the domain or any of its linked domains, or the project was not finished, the **Import project values** option will not be available.</span></span>  
  
5.  <span data-ttu-id="52e4a-119">在 **[匯入專案值]** 對話方塊中：</span><span class="sxs-lookup"><span data-stu-id="52e4a-119">In the **Import Project Values** dialog box:</span></span>  
  
    -   <span data-ttu-id="52e4a-120">在 **[已匯入]** 下拉式清單中，選取 **[全部]** 顯示所有專案，或選取 **[否]** 只顯示尚未匯入值的專案。</span><span class="sxs-lookup"><span data-stu-id="52e4a-120">Select **All** in the **Imported** drop-down list to display all projects, or **No** to display only projects whose values have not been imported yet.</span></span>  
  
    -   <span data-ttu-id="52e4a-121">選取要匯入的值來自於哪一個專案。</span><span class="sxs-lookup"><span data-stu-id="52e4a-121">Select the project that you want to import values from.</span></span>  
  
    -   <span data-ttu-id="52e4a-122">選取 **[加入 [新增] 索引標籤中的值]** ，除了 **[正確]** 和 **[更正]** 索引標籤中的值以外，也匯入 [新增] 索引標籤中的值。</span><span class="sxs-lookup"><span data-stu-id="52e4a-122">Select **Add values from New tab** to import values in the new tab, in addition to values in the **Correct** and **Corrected** tabs.</span></span>  
  
    -   <span data-ttu-id="52e4a-123">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="52e4a-123">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="52e4a-124">當您返回 **[定義域值]** 索引標籤之後，成功匯入值的訊息隨即顯示。</span><span class="sxs-lookup"><span data-stu-id="52e4a-124">You return to the **Domain Values** tab, and a message is displayed on successful import of the values.</span></span> <span data-ttu-id="52e4a-125">已經匯入所以對定義域而言為新增的值將會顯示在 **[值]** 資料表中。</span><span class="sxs-lookup"><span data-stu-id="52e4a-125">Values that have been imported, and so are new to the domain, will be displayed in the **Values** table.</span></span>  
  
7.  <span data-ttu-id="52e4a-126">取消選取 **[只顯示新值]** ，顯示定義域中的所有值。</span><span class="sxs-lookup"><span data-stu-id="52e4a-126">Deselect **Show Only New** to display all values that are in the domain.</span></span>  
  
8.  <span data-ttu-id="52e4a-127">選取 **[正確]**、 **[錯誤]** 或 **[無效]** ，只顯示所選類型的值。</span><span class="sxs-lookup"><span data-stu-id="52e4a-127">Select **Correct**, **Error**, or **Invalid** to display only those values of the selected type.</span></span>  
  
9. <span data-ttu-id="52e4a-128">若要搜尋特定字串，請在 **[尋找]** 文字方塊中輸入此字串。</span><span class="sxs-lookup"><span data-stu-id="52e4a-128">To search for a specific string, enter the string in the **Find** text box.</span></span> <span data-ttu-id="52e4a-129">按一下向上或向下箭號，逐步瀏覽符合搜尋準則的值。</span><span class="sxs-lookup"><span data-stu-id="52e4a-129">Click the up or down arrow to step through the values that meet the search criteria.</span></span> <span data-ttu-id="52e4a-130">這些值將會以黃色反白顯示。</span><span class="sxs-lookup"><span data-stu-id="52e4a-130">They will be highlighted in yellow.</span></span>  
  
10. <span data-ttu-id="52e4a-131">按一下 [完成] 。</span><span class="sxs-lookup"><span data-stu-id="52e4a-131">Click **Finish**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="52e4a-132"> 如需有關使用 **[定義域值]** 索引標籤中之值的詳細資訊，請參閱＜ [Change Domain Values](../../2014/data-quality-services/change-domain-values.md)＞。</span><span class="sxs-lookup"><span data-stu-id="52e4a-132">For more information on working with values in the **Domain Values** tab, see [Change Domain Values](../../2014/data-quality-services/change-domain-values.md).</span></span>  
  
##  <a name="follow-up-after-importing-project-values-into-a-domain"></a><a name="FollowUp"></a> <span data-ttu-id="52e4a-133">後續操作：將專案值匯入定義域之後</span><span class="sxs-lookup"><span data-stu-id="52e4a-133">Follow Up: After Importing Project Values into a Domain</span></span>  
 <span data-ttu-id="52e4a-134">在您將清理程序期間所收集的資料品質知識匯入定義域之後，您可以針對定義域和值執行其他定義域管理工作。</span><span class="sxs-lookup"><span data-stu-id="52e4a-134">After you import data quality knowledge gathered during the cleansing process into a domain, you can perform other domain management tasks on the domain and the values.</span></span> <span data-ttu-id="52e4a-135">如需詳細資訊，請參閱[管理定義域](../../2014/data-quality-services/managing-a-domain.md)。</span><span class="sxs-lookup"><span data-stu-id="52e4a-135">For more information, see [Managing a Domain](../../2014/data-quality-services/managing-a-domain.md).</span></span>  
  
##  <a name="values-that-will-be-imported"></a><a name="Values"></a> <span data-ttu-id="52e4a-136">將會匯入的值</span><span class="sxs-lookup"><span data-stu-id="52e4a-136">Values that Will Be Imported</span></span>  
 <span data-ttu-id="52e4a-137">以下的值將會從專案匯入定義域中：</span><span class="sxs-lookup"><span data-stu-id="52e4a-137">The following values will be imported from a project into a domain:</span></span>  
  
-   <span data-ttu-id="52e4a-138">只有字串值會匯入定義域。</span><span class="sxs-lookup"><span data-stu-id="52e4a-138">Only string values are imported to the domain.</span></span>  
  
-   <span data-ttu-id="52e4a-139">只會匯入 **[清理]** 活動的 **[管理和檢視結果]** 頁面上，位於 **[正確]** 、 **[更正]** 和 **[新增]** 索引標籤中的值。</span><span class="sxs-lookup"><span data-stu-id="52e4a-139">Only values from the **Correct**, **Corrected**, and **New** tabs on the **Manage and View results** page of the **Cleansing** activity will be imported.</span></span> <span data-ttu-id="52e4a-140">**[新增]** 索引標籤中的值只有已在 **[匯入專案值]** 對話方塊中選取 **[加入 [新增] 索引標籤中的值]** 核取方塊時才會匯入。</span><span class="sxs-lookup"><span data-stu-id="52e4a-140">Values from the **New** tab will be imported only if the **Add values from New tab** check box in the **Import Project Values** dialog box has been selected.</span></span>  
  
-   <span data-ttu-id="52e4a-141">值將會以正確值或是包含更正的錯誤形式匯入。</span><span class="sxs-lookup"><span data-stu-id="52e4a-141">Values will be imported as correct or as an error with its correction.</span></span> <span data-ttu-id="52e4a-142">只會匯入包含更正值的錯誤值。</span><span class="sxs-lookup"><span data-stu-id="52e4a-142">Only an error value with a correction value will be imported.</span></span>  
  
-   <span data-ttu-id="52e4a-143">更正值將會是不存在於知識庫中的新值，或是現有的正確值。</span><span class="sxs-lookup"><span data-stu-id="52e4a-143">The correction value will be either a new value that does not exist in the knowledge base or an existing correct value.</span></span>  
  
-   <span data-ttu-id="52e4a-144">只有在值層級而不是記錄層級執行的更正才會匯入知識庫中。</span><span class="sxs-lookup"><span data-stu-id="52e4a-144">Only corrections performed on the value level, not the record level, will be imported into the knowledge base.</span></span>  
  
-   <span data-ttu-id="52e4a-145">如果匯入的值與定義域規則衝突，將會建立無效的值。</span><span class="sxs-lookup"><span data-stu-id="52e4a-145">Invalid values will be created if the imported value contradicts a domain rule.</span></span>  
  
-   <span data-ttu-id="52e4a-146">如果您一次匯入幾個專案中的值，則會循序匯入這些值。</span><span class="sxs-lookup"><span data-stu-id="52e4a-146">If you import values from several projects at once, the values are imported in a sequential order.</span></span>  
  
-   <span data-ttu-id="52e4a-147">定義域中以詞彙為主的關聯所產生的更正將會當做正確值 (而不是錯誤) 匯入。</span><span class="sxs-lookup"><span data-stu-id="52e4a-147">A correction made as a result of a term-based relation in a domain is imported as a correct value (not as an error).</span></span>  
  
##  <a name="values-that-will-not-be-imported"></a><a name="ValuesNot"></a> <span data-ttu-id="52e4a-148">將不會匯入的值</span><span class="sxs-lookup"><span data-stu-id="52e4a-148">Values that Will Not Be Imported</span></span>  
 <span data-ttu-id="52e4a-149">以下的值將不會從專案匯入定義域中：</span><span class="sxs-lookup"><span data-stu-id="52e4a-149">The following values will not be imported from a project into a domain:</span></span>  
  
-   <span data-ttu-id="52e4a-150">**[清理]** 活動的 **[管理和檢視結果]** 頁面上 **[建議]** 和 **[無效]** 索引標籤中的值將不會匯入。</span><span class="sxs-lookup"><span data-stu-id="52e4a-150">Values from the **Suggested** and **Invalid** tabs on the **Manage and View results** page of the **Cleansing** activity will not be imported.</span></span>  
  
-   <span data-ttu-id="52e4a-151">如果清理專案中找到的值與定義域中的現有值衝突，則會略過專案中找到的值。</span><span class="sxs-lookup"><span data-stu-id="52e4a-151">If a value found in the cleansing project contradicts an existing value in the domain, the value found in the project is skipped.</span></span> <span data-ttu-id="52e4a-152">這包括清理值與知識庫值之間的衝突。</span><span class="sxs-lookup"><span data-stu-id="52e4a-152">This will include conflicts between cleansing and knowledge base values.</span></span>  
  
-   <span data-ttu-id="52e4a-153">在記錄層級執行的更正將不會匯入知識庫中。</span><span class="sxs-lookup"><span data-stu-id="52e4a-153">Corrections performed on the record level will not be imported into the knowledge base.</span></span>  
  
-   <span data-ttu-id="52e4a-154">如果將取代的值已更正或是由參考資料服務核准為正確，則不會將任何值匯入定義域中。</span><span class="sxs-lookup"><span data-stu-id="52e4a-154">No value will be imported to a domain if the value that it would replace was corrected or approved as correct by a reference data service.</span></span>  
  
-   <span data-ttu-id="52e4a-155">如果更正值以無效或錯誤值的形式出現在知識庫中，則錯誤和更正值都不會匯入。</span><span class="sxs-lookup"><span data-stu-id="52e4a-155">If a correction value appears in the knowledge base as an invalid or error value, neither the error nor the correction value will be imported.</span></span>  
  
-   <span data-ttu-id="52e4a-156">如果定義域是複合定義域的一部分，而且已針對複合定義域執行清理，則不會匯入任何值。</span><span class="sxs-lookup"><span data-stu-id="52e4a-156">If the domain is part of a composite domain, and the cleansing was performed on the composite domain, no values will be imported.</span></span>  
  
-   <span data-ttu-id="52e4a-157">只有當知識庫的狀態為工作中，而且知識庫由正在匯入的使用者鎖定時，您才可以從專案匯入值。</span><span class="sxs-lookup"><span data-stu-id="52e4a-157">You can import values from a project only when the knowledge base has a state of in-work and the knowledge base is locked by the user who is importing.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52e4a-158">另請參閱</span><span class="sxs-lookup"><span data-stu-id="52e4a-158">See Also</span></span>  
 <span data-ttu-id="52e4a-159">[資料清理](../../2014/data-quality-services/data-cleansing.md) </span><span class="sxs-lookup"><span data-stu-id="52e4a-159">[Data Cleansing](../../2014/data-quality-services/data-cleansing.md) </span></span>  
 [<span data-ttu-id="52e4a-160">DQS 清理轉換</span><span class="sxs-lookup"><span data-stu-id="52e4a-160">DQS Cleansing Transformation</span></span>](../integration-services/data-flow/transformations/dqs-cleansing-transformation.md)  
  
  
