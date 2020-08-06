---
title: 工作4：管理和查看結果 |Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: ecc3ba7e-fecf-478f-8825-6e4764b00e99
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 34fc2a7821fc275a0a0787f703d61a74ea3ee000
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698983"
---
# <a name="task-4-manaing-and-viewing-results"></a><span data-ttu-id="5cb1e-102">工作 4：管理和檢視結果</span><span class="sxs-lookup"><span data-stu-id="5cb1e-102">Task 4: Manaing and Viewing Results</span></span>
  <span data-ttu-id="5cb1e-103">在這項工作中，您會檢閱電腦輔助清理的結果，同時針對供應商資料執行互動式清理。</span><span class="sxs-lookup"><span data-stu-id="5cb1e-103">In this task, you review the results of computer-assisted cleansing and also perform interactive cleansing on the supplier data.</span></span> <span data-ttu-id="5cb1e-104">如需詳細資訊，請參閱[互動式清理階段](https://msdn.microsoft.com/library/hh213061.aspx#Interactive)。</span><span class="sxs-lookup"><span data-stu-id="5cb1e-104">See [Interactive Cleansing Stage](https://msdn.microsoft.com/library/hh213061.aspx#Interactive) for more details.</span></span>  
  
1.  <span data-ttu-id="5cb1e-105">從網域清單中選取 [**連絡人電子郵件**網域]。</span><span class="sxs-lookup"><span data-stu-id="5cb1e-105">Select **Contact Email** domain from the list of domains.</span></span>  
  
2.  <span data-ttu-id="5cb1e-106">切換至右窗格中的 [**無效**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="5cb1e-106">Switch to the **Invalid** tab in the right pane.</span></span> <span data-ttu-id="5cb1e-107">請注意，結尾處遺漏字元 ' 的兩個電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="5cb1e-107">Notice that two email addresses that were missing character 's' at the end.</span></span> <span data-ttu-id="5cb1e-108">這兩個電子郵件是由要求所有電子郵件地址結尾為 ' ) 的\*\* \@ adventure-works.com\*\* (的網域規則所無效。</span><span class="sxs-lookup"><span data-stu-id="5cb1e-108">These two emails that were found to be invalid by the domain rule that requires all email addresses to end with **\@adventure-works.com** (with 's').</span></span> <span data-ttu-id="5cb1e-109">DQS 會在清理時使用此定義域規則，以判斷電子郵件是否有效。</span><span class="sxs-lookup"><span data-stu-id="5cb1e-109">DQS uses the domain rule while cleansing to determine whether an email is a valid one or not.</span></span> <span data-ttu-id="5cb1e-110">此索引標籤會顯示在知識庫中標示為無效或未能通過定義域規則的定義域值。</span><span class="sxs-lookup"><span data-stu-id="5cb1e-110">This tab displays the domain values that were either marked as invalid in the knowledge base or failed a domain rule.</span></span> <span data-ttu-id="5cb1e-111">在此情況下，這些值未通過定義域規則 (電子郵件驗證)。</span><span class="sxs-lookup"><span data-stu-id="5cb1e-111">In this case, these values failed the domain rule (Email Validation).</span></span>  
  
3.  <span data-ttu-id="5cb1e-112">在 [**更正為**] 資料行中，輸入以\*\* \@ adventure-works.com\*\* (結尾為 ' ) 的正確電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="5cb1e-112">In the **Correct To** column, type the right email address that end with **\@adventure-works.com** (with 's').</span></span>  
  
     <span data-ttu-id="5cb1e-113">![電子郵件驗證提供的更正規則](../../2014/tutorials/media/et-managingandviewingresults-01.jpg "電子郵件驗證提供的更正規則")</span><span class="sxs-lookup"><span data-stu-id="5cb1e-113">![Corrections from Email Validation Rule](../../2014/tutorials/media/et-managingandviewingresults-01.jpg "Corrections from Email Validation Rule")</span></span>  
  
4.  <span data-ttu-id="5cb1e-114">針對這兩個記錄按一下 [**核准**]，以同時核准這兩項變更。</span><span class="sxs-lookup"><span data-stu-id="5cb1e-114">Click **Approve** for both the records to approve both the changes.</span></span> <span data-ttu-id="5cb1e-115">當您核准時，記錄會移至 [已**更正**] 索引標籤。您可以使用 [**核准所有詞彙**] 工具列按鈕一次核准所有變更，而不是分別核准每個專案。</span><span class="sxs-lookup"><span data-stu-id="5cb1e-115">When you approve, the records move to the **Corrected** tab. Instead of approving each item separately, you can approve all the changes at once using the **Approve all terms** toolbar button.</span></span>  
  
5.  <span data-ttu-id="5cb1e-116">切換至右窗格中的 [**新增**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="5cb1e-116">Switch to the **New** tab in the right pane.</span></span> <span data-ttu-id="5cb1e-117">此索引標籤的值是 DQS 在知識庫中還沒有足夠資訊的值，因此無法判斷這些值是否正確。</span><span class="sxs-lookup"><span data-stu-id="5cb1e-117">The values on this tab are the values for which DQS does not have enough information in the knowledge base yet to determine whether the values are correct.</span></span> <span data-ttu-id="5cb1e-118">因此，它無法變更或建議定義域值的變更。</span><span class="sxs-lookup"><span data-stu-id="5cb1e-118">Therefore, it cannot change or suggest changes to the domain values.</span></span>  
  
6.  <span data-ttu-id="5cb1e-119">請檢查這些值，以確認所有電子郵件的結尾都是\*\* \@ adventure-works.com\*\* ，然後按一下工具列上的 [**核准所有詞彙**]。</span><span class="sxs-lookup"><span data-stu-id="5cb1e-119">Review the values to confirm that all the emails end with **\@adventure-works.com** and click **Approve all terms** on the toolbar.</span></span> <span data-ttu-id="5cb1e-120">此索引標籤中的核准值會移至**正確**的索引標籤。</span><span class="sxs-lookup"><span data-stu-id="5cb1e-120">The approved values from this tab move to the **Correct** tab.</span></span>  
  
7.  <span data-ttu-id="5cb1e-121">從網域清單中選取 [**國家/地區**] 網域。</span><span class="sxs-lookup"><span data-stu-id="5cb1e-121">Select the **Country** domain from the list of domains.</span></span>  
  
8.  <span data-ttu-id="5cb1e-122">切換至右窗格中的 [**更正**] 索引標籤，並請注意，「**美國**」的值會自動校正為「**美國**」結尾的 ' s '。</span><span class="sxs-lookup"><span data-stu-id="5cb1e-122">Switch to the **Corrected** tab in the right pane and notice that **United State** value is automatically corrected to the **United States** with 's' at the end.</span></span> <span data-ttu-id="5cb1e-123">此規則不是您為 [**國家/地區**] 定義域定義的規則，但 DQS 的**83%** 確信正確的值為 [**美國**]。</span><span class="sxs-lookup"><span data-stu-id="5cb1e-123">This rule is not a rule you defined for the **Country** domain, but DQS is **83%** confident that the correct value is **United States**.</span></span> <span data-ttu-id="5cb1e-124">所有已**更正**的專案都會自動選取 [**核准**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="5cb1e-124">The **Approve** button is automatically selected for all the **Corrected** items.</span></span> <span data-ttu-id="5cb1e-125">您可以覆寫這個行為並拒絕變更。</span><span class="sxs-lookup"><span data-stu-id="5cb1e-125">You can override this behavior and reject a change.</span></span>  
  
9. <span data-ttu-id="5cb1e-126">請注意 **，美國已更正**為**美國**，因為它們是同義字，而**美國**是前置的 (慣用) 值。</span><span class="sxs-lookup"><span data-stu-id="5cb1e-126">Notice that **USA** is corrected to **United States** because they are synonyms and **United States** is the leading (preferred) value.</span></span>  
  
     <span data-ttu-id="5cb1e-127">![根據同義字進行的更正](../../2014/tutorials/media/et-managingandviewingresults-02.jpg "根據同義字進行的更正")</span><span class="sxs-lookup"><span data-stu-id="5cb1e-127">![Corrections based on Synonyms](../../2014/tutorials/media/et-managingandviewingresults-02.jpg "Corrections based on Synonyms")</span></span>  
  
10. <span data-ttu-id="5cb1e-128">請注意，已針對這些已更正的值選取 [**核准**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="5cb1e-128">Notice that the **Approve** button is already selected for these corrected values.</span></span> <span data-ttu-id="5cb1e-129">這是更正值的預設行為。</span><span class="sxs-lookup"><span data-stu-id="5cb1e-129">This behavior is the default for the corrected values.</span></span> <span data-ttu-id="5cb1e-130">您可以拒絕變更，而當您這麼做時，值會移至 [**無效**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="5cb1e-130">You can reject a change and when you do so, the value moves to the **Invalid** tab.</span></span>  
  
11. <span data-ttu-id="5cb1e-131">從網域清單中選取 [**供應商名稱**]。</span><span class="sxs-lookup"><span data-stu-id="5cb1e-131">Select **Supplier Name** from the list of domains.</span></span>  
  
12. <span data-ttu-id="5cb1e-132">切換至右窗格中的 [**更正**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="5cb1e-132">Switch to the **Corrected** tab in the right pane.</span></span>  
  
     <span data-ttu-id="5cb1e-133">![更正的供應商名稱](../../2014/tutorials/media/et-managingandviewingresults-03.jpg "更正的供應商名稱")</span><span class="sxs-lookup"><span data-stu-id="5cb1e-133">![Corrected Supplier Names](../../2014/tutorials/media/et-managingandviewingresults-03.jpg "Corrected Supplier Names")</span></span>  
  
    1.  <span data-ttu-id="5cb1e-134">請注意， **a. Datum Corp**已更正為**a. Datum Corporation** ，**原因**是設定為以詞彙為主的**關聯。A. Datum Corporation**是 DQS 的已知定義域值，因為它是在知識探索程式期間探索到的。</span><span class="sxs-lookup"><span data-stu-id="5cb1e-134">Notice that **A. Datum Corp.** is corrected to **A. Datum Corporation** and the **Reason** is set to **Term based relation. A. Datum Corporation** is a known domain value to DQS because it was discovered during the knowledge discovery process.</span></span> <span data-ttu-id="5cb1e-135">因此，DQS 對於這種更正有**100% 的信心**。</span><span class="sxs-lookup"><span data-stu-id="5cb1e-135">Therefore, DQS is **100% confident** about this correction.</span></span>  
  
    2.  <span data-ttu-id="5cb1e-136">請注意，[**延遲國家**/地區 Storex] 已更正為 [ **lazy country Store**]、[**信賴等級**] 設定為 [ **100%**]，而 [**原因**] 設定為 [**定義域值**]。</span><span class="sxs-lookup"><span data-stu-id="5cb1e-136">Notice that **Lazy Country Storex** is corrected to **Lazy Country Store**, **Confidence Level** is set to **100%**, and the **Reason** is set to **Domain Value**.</span></span> <span data-ttu-id="5cb1e-137">在知識探索程式期間，您會將 [**延遲國家/地區 Storex** ] 設定為 [**延遲國家/地區存放區**] 做為**更正**的錯誤，因此 DQS 對於進行這種更正會有**100% 的信心**。</span><span class="sxs-lookup"><span data-stu-id="5cb1e-137">During the knowledge discovery process, you set **Lazy Country Storex** as an error with **Lazy Country Store** as the **correction**, so DQS is **100% confident** about making this correction.</span></span>  
  
    3.  <span data-ttu-id="5cb1e-138">DQS 不熟悉清單中的其他值，但它會使用**拼寫檢查**來找到這些值的更正，並建議適當的更正。</span><span class="sxs-lookup"><span data-stu-id="5cb1e-138">DQS is not familiar with the other values in the list, but it found the corrections for these values using the **Spell Checker** and proposes the appropriate corrections.</span></span> <span data-ttu-id="5cb1e-139">DQS 不會對這些更正進行**100%** 的信心，但信賴等級高於80%，這是進行更正的臨界值層級，因此 DQS 會建議更正。</span><span class="sxs-lookup"><span data-stu-id="5cb1e-139">DQS is **not 100%** confident about these corrections, but the confidence level is above 80%, which is the threshold level for making corrections, so DQS proposes the corrections.</span></span>  
  
13. <span data-ttu-id="5cb1e-140">請注意，所有值都會自動啟用 [**核准**]。</span><span class="sxs-lookup"><span data-stu-id="5cb1e-140">Notice that the **Approve** is automatically enabled for all the values.</span></span> <span data-ttu-id="5cb1e-141">您可依適當情況覆寫更正值或拒絕變更。</span><span class="sxs-lookup"><span data-stu-id="5cb1e-141">You can override the corrected value or reject the change as appropriate.</span></span> <span data-ttu-id="5cb1e-142">根據預設，會針對 [**更正**] 索引標籤上的所有值選取 [**核准**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="5cb1e-142">By default the **Approve** button is selected for all the values on the **Corrected** tab.</span></span>  
  
14. <span data-ttu-id="5cb1e-143">切換至 [**新增**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="5cb1e-143">Switch to the **New** tab.</span></span>  
  
15. <span data-ttu-id="5cb1e-144">請注意 **，Corp.** 已更正**為 Corporation**、 **Co。** 已更正為**公司**，而**inc.** 已更正為**納入**。</span><span class="sxs-lookup"><span data-stu-id="5cb1e-144">Notice that **Corp.** is corrected to **Corporation**, **Co.** is corrected to **Company**, and **Inc.** is corrected to **Incorporated**.</span></span> <span data-ttu-id="5cb1e-145">例如，**合併 Inc.** 已更正為合併**合併**和**合併的共同。** 已更正為**合併的公司**，且**Frabrikam Corp。** 已更正為**Fabrikam Corporation**。</span><span class="sxs-lookup"><span data-stu-id="5cb1e-145">For example, **Consolidate Inc.** is corrected to **Consolidate Incorporated** and **Consolidated Co.** is corrected to **Consolidated Company**, and **Frabrikam Corp.** is corrected to **Fabrikam Corporation**.</span></span>  <span data-ttu-id="5cb1e-146">您可以看到以**詞彙**為主的關聯就是原因。</span><span class="sxs-lookup"><span data-stu-id="5cb1e-146">You can see that **term-based relation** is mentioned as the reason.</span></span> <span data-ttu-id="5cb1e-147">這些變更是使用您在定義域管理活動期間所定義之以詞彙為主的關聯所建議。</span><span class="sxs-lookup"><span data-stu-id="5cb1e-147">These changes are proposed by using the term-based relations you defined during the domain management activity.</span></span> <span data-ttu-id="5cb1e-148">您可以在這裡手動將更正的值變更**為**。</span><span class="sxs-lookup"><span data-stu-id="5cb1e-148">You can change the **Correct To** values manually here.</span></span>  
  
16. <span data-ttu-id="5cb1e-149">將清單滾動至**Hunxgry Coyote Store** ，並顯示紅色波浪線。</span><span class="sxs-lookup"><span data-stu-id="5cb1e-149">Scroll the list to see **Hunxgry Coyote Store** with a red squiggly line.</span></span> <span data-ttu-id="5cb1e-150">在其上按一下滑鼠右鍵，然後按一下 [ **Hungy Coyote Store** (，但不包含 ' x ' ) 。</span><span class="sxs-lookup"><span data-stu-id="5cb1e-150">Right-click on it and click **Hungy Coyote Store** (with no 'x').</span></span> <span data-ttu-id="5cb1e-151">[**更正為**] 資料行應該會自動填入較大的**Coyote 存放區**。</span><span class="sxs-lookup"><span data-stu-id="5cb1e-151">The **Correct To** column should be automatically populated with **Hungry Coyote Store**.</span></span> <span data-ttu-id="5cb1e-152">您也可以在 [更正為] 資料行中手動輸入值。</span><span class="sxs-lookup"><span data-stu-id="5cb1e-152">You can also manually type a value in the Correct To column.</span></span>  
  
17. <span data-ttu-id="5cb1e-153">按一下工具列中的 [**核准所有詞彙**]。</span><span class="sxs-lookup"><span data-stu-id="5cb1e-153">Click **Approve all terms** from the toolbar.</span></span> <span data-ttu-id="5cb1e-154">指定的 [**更正為**] 值的定義域值會移至 [**更正**] 索引標籤，而沒有關聯的**正確**值的新值則會移至 [**正確**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="5cb1e-154">The domain values with the **Correct To** value specified move to the **Corrected** tab and the new values with no associated **Correct To** values move to the **Correct** tab.</span></span>  
  
18. <span data-ttu-id="5cb1e-155">從 [定義域] 清單中選取 [**位址驗證**] 複合定義域。</span><span class="sxs-lookup"><span data-stu-id="5cb1e-155">Select the **Address Validation** composite domain from the domain list.</span></span>  
  
19. <span data-ttu-id="5cb1e-156">在右窗格中，切換到 [**正確**] 索引標籤。在**Azure Marketplace**上，您應該會看到**Melissa 資料位址檢查**DQS 服務所發現的正確位址。</span><span class="sxs-lookup"><span data-stu-id="5cb1e-156">In the right pane, switch to the **Correct** tab. You should see the addresses that are found to be correct by the **Melissa Data - Address Check** DQS service on the **Azure Marketplace**.</span></span>  
  
20. <span data-ttu-id="5cb1e-157">切換至 [已**更正**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="5cb1e-157">Switch to the **Corrected** tab.</span></span>  
  
21. <span data-ttu-id="5cb1e-158">請注意，[ **City** as 洛杉磯] 記錄的**狀態**會**設定為**[ **CA** ]。</span><span class="sxs-lookup"><span data-stu-id="5cb1e-158">Notice that **State** for the record that has **City** as **Los Angeles** is set to **CA** now.</span></span> <span data-ttu-id="5cb1e-159">請注意，[**原因**] 欄位是**由規則「城市-狀態規則」更正**。</span><span class="sxs-lookup"><span data-stu-id="5cb1e-159">Notice in the **Reason** field is that **Corrected by Rule 'City-State Rule'**.</span></span>  
  
     <span data-ttu-id="5cb1e-160">![縣/市-省/市規則更正](../../2014/tutorials/media/et-managingandviewingresults-04.jpg "縣/市-省/市規則更正")</span><span class="sxs-lookup"><span data-stu-id="5cb1e-160">![City-State Rule Correction](../../2014/tutorials/media/et-managingandviewingresults-04.jpg "City-State Rule Correction")</span></span>  
  
22. <span data-ttu-id="5cb1e-161">請注意，清單中的這個專案已選取 [**核准**] 選項按鈕。</span><span class="sxs-lookup"><span data-stu-id="5cb1e-161">Notice that the **Approve** radio button is already selected for this item in the list.</span></span> <span data-ttu-id="5cb1e-162">這是 [**更正**] 索引標籤上專案的預設行為。</span><span class="sxs-lookup"><span data-stu-id="5cb1e-162">This is the default behavior for items on the **Corrected** tab.</span></span>  
  
23. <span data-ttu-id="5cb1e-163">切換至 [**建議**] 索引標籤。**請檢查 Melissa 的資料位址檢查**服務所建議的變更。</span><span class="sxs-lookup"><span data-stu-id="5cb1e-163">Switch to the **Suggested** tab. Review the changes suggested by the **Melissa Data - Address Check** service.</span></span>  
  
24. <span data-ttu-id="5cb1e-164">按一下工具列按鈕上的 [**核准所有詞彙**]，然後按一下 [**確認**] 訊息方塊上的 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="5cb1e-164">**Click Approve all terms** on the toolbar button and click **OK** on the **Confirmation** message box.</span></span>  
  
     <span data-ttu-id="5cb1e-165">![[核准所有詞彙] 工具列按鈕](../../2014/tutorials/media/et-managingandviewingresults-05.jpg "[核准所有詞彙] 工具列按鈕")</span><span class="sxs-lookup"><span data-stu-id="5cb1e-165">![Approve All Terms Toolbar Button](../../2014/tutorials/media/et-managingandviewingresults-05.jpg "Approve All Terms Toolbar Button")</span></span>  
  
25. <span data-ttu-id="5cb1e-166">按 **[下一步]** 切換至 [**匯出**] 頁面。</span><span class="sxs-lookup"><span data-stu-id="5cb1e-166">Click **Next** to switch to the **Export** page.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="5cb1e-167">後續步驟</span><span class="sxs-lookup"><span data-stu-id="5cb1e-167">Next Step</span></span>  
 [<span data-ttu-id="5cb1e-168">工作 5：將清理結果匯出到 Excel 檔案</span><span class="sxs-lookup"><span data-stu-id="5cb1e-168">Task 5: Exporting Cleansing Results to an Excel File</span></span>](../../2014/tutorials/task-5-exporting-cleansing-results-to-an-excel-file.md)  
  
  
