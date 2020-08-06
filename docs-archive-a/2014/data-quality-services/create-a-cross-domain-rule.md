---
title: 建立跨定義域規則 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
f1_keywords:
- sql12.dqs.dm.testcdrule.f1
- sql12.dqs.dm.cdrules.f1
ms.assetid: 0f3f5ba4-cc47-4d66-866e-371a042d1f21
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: cddcd9bbd2fc8d95fe8645781de5fe4e936050a9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687160"
---
# <a name="create-a-cross-domain-rule"></a><span data-ttu-id="d42e1-102">建立跨定義域規則</span><span class="sxs-lookup"><span data-stu-id="d42e1-102">Create a Cross-Domain Rule</span></span>
  <span data-ttu-id="d42e1-103">本主題描述如何在 [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) 中的知識庫內建立複合定義域的跨定義域規則。</span><span class="sxs-lookup"><span data-stu-id="d42e1-103">This topic describes how to create a cross-domain rule for a composite domain in a knowledge base in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS).</span></span> <span data-ttu-id="d42e1-104">跨定義域規則會在複合定義域所包含的單一定義域中測試值之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="d42e1-104">A cross-domain rule tests the relationship between values in single domains that are included in a composite domain.</span></span> <span data-ttu-id="d42e1-105">跨定義域規則必須在複合定義域中成立，才能讓定義域值被視為正確且符合商務需求。</span><span class="sxs-lookup"><span data-stu-id="d42e1-105">A cross-domain rule must hold true across a composite domain in order for domain values to be considered accurate and conformant to business requirements.</span></span> <span data-ttu-id="d42e1-106">跨定義域規則是用來驗證、更正並標準化定義域值。</span><span class="sxs-lookup"><span data-stu-id="d42e1-106">A cross-domain rule is used to validate, correct, and standardize domain values.</span></span>  
  
 <span data-ttu-id="d42e1-107">跨定義域規則的 If 子句和 Then 子句是分別針對複合定義域的其中一個單一定義域所定義。</span><span class="sxs-lookup"><span data-stu-id="d42e1-107">The If clause and Then clause of a cross-domain rule are each defined for one of the single domains in the composite domain.</span></span> <span data-ttu-id="d42e1-108">您必須針對不同的單一定義域定義每個子句。</span><span class="sxs-lookup"><span data-stu-id="d42e1-108">Each clause must be defined for a different single domain.</span></span> <span data-ttu-id="d42e1-109">跨定義域規則必須與多個單一定義域相關。您無法針對複合定義域定義簡單定義域規則 (僅適用於單一定義域)。</span><span class="sxs-lookup"><span data-stu-id="d42e1-109">A cross-domain rule must relate to multiple single domains; you cannot define a simple domain rule (for only a single domain) for a composite domain.</span></span> <span data-ttu-id="d42e1-110">您可以針對單一定義域定義定義域規則，藉以進行此作業。</span><span class="sxs-lookup"><span data-stu-id="d42e1-110">You would do so by defining a domain rule for a single domain.</span></span> <span data-ttu-id="d42e1-111">If 子句和 Then 子句可以分別包含一個或多個條件。</span><span class="sxs-lookup"><span data-stu-id="d42e1-111">The If clause and the Then clause can each contain one or more conditions.</span></span>  
  
 <span data-ttu-id="d42e1-112">具有最終條件的跨定義域規則會將規則邏輯套用至條件中值的同義字，以及值本身。</span><span class="sxs-lookup"><span data-stu-id="d42e1-112">A cross-domain rule that has definitive conditions will apply the rules logic to synonyms of the value in the conditions, as well the values themselves.</span></span> <span data-ttu-id="d42e1-113">If 和 Then 子句的最終條件包括 [值等於]、[值不等於]、[值在] 或 [值不在]。</span><span class="sxs-lookup"><span data-stu-id="d42e1-113">The definitive conditions for the If and Then clauses are Value is equal to, Value is not equal to, Value is in, or Value is not in.</span></span> <span data-ttu-id="d42e1-114">例如，假設您擁有複合定義域的下列跨定義域規則：「對於 'City' 而言，如果值等於 'Los Angeles'，則對於 'State' 而言，值等於 'CA'」。</span><span class="sxs-lookup"><span data-stu-id="d42e1-114">For example, suppose that you have the following cross-domain rule for a composite domain: "For 'City', if Value is equal to 'Los Angeles', then for 'State', Value is equal to 'CA'.</span></span> <span data-ttu-id="d42e1-115">如果 'Los Angeles' 和 'LA' 是同義字，此規則會針對 'Los Angeles CA' 和 'LA CA' 傳回正確，而針對 'Los Angeles WA' 和 'LA WA' 傳回錯誤。</span><span class="sxs-lookup"><span data-stu-id="d42e1-115">"If 'Los Angeles' and 'LA' are synonyms, this rule will return correct for 'Los Angeles CA' and 'LA CA' and in error for 'Los Angeles WA' and 'LA WA'.</span></span>  
  
 <span data-ttu-id="d42e1-116">除了只讓您知道跨定義域規則是否有效之外，跨定義域規則中的最終 *Then* 子句 **[值等於]** 也會在資料清理活動期間更正資料。</span><span class="sxs-lookup"><span data-stu-id="d42e1-116">Apart from just letting you know about the validity of a cross-domain rule, the definitive *Then* clause in a cross-domain rule, **Value is equal to**, also corrects the data during the data-cleansing activity.</span></span> <span data-ttu-id="d42e1-117">如需詳細資訊，請參閱＜ [Data Correction using Definitive Cross-Domain Rules](../../2014/data-quality-services/cleanse-data-in-a-composite-domain.md#CDCorrection) ＞中的 [Cleanse Data in a Composite Domain](../../2014/data-quality-services/cleanse-data-in-a-composite-domain.md)。</span><span class="sxs-lookup"><span data-stu-id="d42e1-117">For more information, see [Data Correction using Definitive Cross-Domain Rules](../../2014/data-quality-services/cleanse-data-in-a-composite-domain.md#CDCorrection) in [Cleanse Data in a Composite Domain](../../2014/data-quality-services/cleanse-data-in-a-composite-domain.md).</span></span>  
  
 <span data-ttu-id="d42e1-118">跨定義域規則會在只影響單一定義域的所有簡單規則之後納入考量。</span><span class="sxs-lookup"><span data-stu-id="d42e1-118">Cross-domain rules are taken into consideration after all simple rules that affect only a single domain.</span></span> <span data-ttu-id="d42e1-119">只有當某個值通過單一定義域規則 (如果存在的話) 時，才會套用跨定義域規則。</span><span class="sxs-lookup"><span data-stu-id="d42e1-119">Only if a value passes single domain rules (if they exist) is the cross-domain rule applied.</span></span> <span data-ttu-id="d42e1-120">您必須先定義所有要執行規則的複合定義域和單一定義域，然後才能執行規則。</span><span class="sxs-lookup"><span data-stu-id="d42e1-120">The composite domain and the single domains that a rule is run on must all be defined before the rule can be executed.</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="d42e1-121">開始之前</span><span class="sxs-lookup"><span data-stu-id="d42e1-121">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="d42e1-122">必要條件</span><span class="sxs-lookup"><span data-stu-id="d42e1-122">Prerequisites</span></span>  
 <span data-ttu-id="d42e1-123">若要建立跨定義域規則，您必須已經建立並開啟複合定義域。</span><span class="sxs-lookup"><span data-stu-id="d42e1-123">To create a cross-domain rule, you must have created and opened a composite domain.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="d42e1-124">Security</span><span class="sxs-lookup"><span data-stu-id="d42e1-124">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="d42e1-125">權限</span><span class="sxs-lookup"><span data-stu-id="d42e1-125">Permissions</span></span>  
 <span data-ttu-id="d42e1-126">您必須擁有 DQS_MAIN 資料庫的 dqs_kb_editor 或 dqs_administrator 角色，才能建立跨定義域規則。</span><span class="sxs-lookup"><span data-stu-id="d42e1-126">You must have the dqs_kb_editor or the dqs_administrator role on the DQS_MAIN database to create a cross-domain rule.</span></span>  
  
##  <a name="create-cross-domain-rules"></a><a name="Create"></a> <span data-ttu-id="d42e1-127">建立跨定義域規則</span><span class="sxs-lookup"><span data-stu-id="d42e1-127">Create Cross-Domain Rules</span></span>  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]<span data-ttu-id="d42e1-128">[執行 Data Quality Client 應用程式](../../2014/data-quality-services/run-the-data-quality-client-application.md)。</span><span class="sxs-lookup"><span data-stu-id="d42e1-128">[Run the Data Quality Client Application](../../2014/data-quality-services/run-the-data-quality-client-application.md).</span></span>  
  
2.  <span data-ttu-id="d42e1-129">在 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 首頁畫面上，開啟或建立知識庫。</span><span class="sxs-lookup"><span data-stu-id="d42e1-129">In the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen, open or create a knowledge base.</span></span> <span data-ttu-id="d42e1-130">選取 **[定義域管理]** 當做活動，然後按一下 **[開啟]** 或 **[建立]**。</span><span class="sxs-lookup"><span data-stu-id="d42e1-130">Select **Domain Management** as the activity, and then click **Open** or **Create**.</span></span> <span data-ttu-id="d42e1-131">如需相關資訊，請參閱 [建立知識庫](../../2014/data-quality-services/create-a-knowledge-base.md) 或 [開啟知識庫](../../2014/data-quality-services/open-a-knowledge-base.md)。</span><span class="sxs-lookup"><span data-stu-id="d42e1-131">For more information, see [Create a Knowledge Base](../../2014/data-quality-services/create-a-knowledge-base.md) or [Open a Knowledge Base](../../2014/data-quality-services/open-a-knowledge-base.md).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d42e1-132">定義域管理會在 Data Quality Services 用戶端的頁面上執行，該頁面包含個別定義域管理作業所適用的五個索引標籤。</span><span class="sxs-lookup"><span data-stu-id="d42e1-132">Domain management is performed in a page of the Data Quality Service client that contains five tabs for separate domain management operations.</span></span> <span data-ttu-id="d42e1-133">這不是精靈驅動的程序，任何管理作業都可以個別執行。</span><span class="sxs-lookup"><span data-stu-id="d42e1-133">It is not a wizard-driven process; any management operation can be performed separately.</span></span>  
  
3.  <span data-ttu-id="d42e1-134">從 **[定義域管理]** 頁面的 **[定義域清單]** 中，選取您想要建立定義域規則的複合定義域，或是建立新的複合定義域。</span><span class="sxs-lookup"><span data-stu-id="d42e1-134">From the **Domain list** on the **Domain Management** page, select the composite domain that you want to create a domain rule for, or create a new composite domain.</span></span> <span data-ttu-id="d42e1-135">如果您必須建立新的定義域，請參閱＜ [Create a Composite Domain](../../2014/data-quality-services/create-a-composite-domain.md)＞。</span><span class="sxs-lookup"><span data-stu-id="d42e1-135">If you have to create a new domain, see [Create a Composite Domain](../../2014/data-quality-services/create-a-composite-domain.md).</span></span>  
  
4.  <span data-ttu-id="d42e1-136">按一下 **[CD 規則]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="d42e1-136">Click the **CD Rules** tab.</span></span>  
  
5.  <span data-ttu-id="d42e1-137">按一下 **[加入新的定義域規則]**，然後輸入規則的名稱和描述。</span><span class="sxs-lookup"><span data-stu-id="d42e1-137">Click **Add a new domain rule**, and then enter a name and description for the rule.</span></span>  
  
6.  <span data-ttu-id="d42e1-138">選取 **[使用中]** 指定將要執行此規則 (預設值)，或取消選取以防止執行此規則。</span><span class="sxs-lookup"><span data-stu-id="d42e1-138">Select **Active** to specify that the rule will be run (the default), and deselect to prevent the rule from running.</span></span>  
  
7.  <span data-ttu-id="d42e1-139">依照下列方式建立 If 子句：</span><span class="sxs-lookup"><span data-stu-id="d42e1-139">Create the If clause as follows:</span></span>  
  
    1.  <span data-ttu-id="d42e1-140">在 If 子句窗格的定義域清單中，選取複合定義域所包含的其中一個單一定義域，成為 If 子句的主詞。</span><span class="sxs-lookup"><span data-stu-id="d42e1-140">In the domain list in the If clause pane, select one of the single domains included in the composite domain to be the subject of the If clause.</span></span> <span data-ttu-id="d42e1-141">您可以選取複合定義域中的任何單一定義域。</span><span class="sxs-lookup"><span data-stu-id="d42e1-141">You can select any single domain in the composite domain.</span></span>  
  
    2.  <span data-ttu-id="d42e1-142">從下拉式清單中選取條件，做為子句的第一個條件。</span><span class="sxs-lookup"><span data-stu-id="d42e1-142">Select a condition from the drop-down list for the first condition of the clause.</span></span>  
  
    3.  <span data-ttu-id="d42e1-143">如果條件需要值，請在與條件相關聯的文字方塊中輸入值。</span><span class="sxs-lookup"><span data-stu-id="d42e1-143">If the condition requires a value, enter the value in the text box associated with the condition.</span></span>  
  
    4.  <span data-ttu-id="d42e1-144">如果 If 子句需要另一個條件，請按一下 **[將新條件加入選取的子句]**。</span><span class="sxs-lookup"><span data-stu-id="d42e1-144">If the If clause requires another condition, click **Adds a new condition to the selected clause**.</span></span> <span data-ttu-id="d42e1-145">必要時，請選取運算子、選取條件，然後輸入條件的值。</span><span class="sxs-lookup"><span data-stu-id="d42e1-145">Select the operator, select a condition, and enter a value for the condition, if necessary.</span></span>  
  
    5.  <span data-ttu-id="d42e1-146">若要變更條件的順序，請按一下條件的左側加以選取，然後按一下向上或向下箭號。</span><span class="sxs-lookup"><span data-stu-id="d42e1-146">To change the order of the conditions, select a condition by clicking to its left, and then click the up or down arrow.</span></span>  
  
    6.  <span data-ttu-id="d42e1-147">若要隱藏條件，請按一下定義域名稱左側的減號。</span><span class="sxs-lookup"><span data-stu-id="d42e1-147">To hide the conditions, click the minus sign to the left of the domain name.</span></span> <span data-ttu-id="d42e1-148">按一下加號，即可顯示條件。</span><span class="sxs-lookup"><span data-stu-id="d42e1-148">Click the plus ign to display the conditions.</span></span>  
  
8.  <span data-ttu-id="d42e1-149">在 Then 子句窗格的定義域清單中選取單一定義域 (If 子句主詞以外的定義域)，藉以建立 Then 子句。</span><span class="sxs-lookup"><span data-stu-id="d42e1-149">Create the Then clause by selecting a single domain, other than the subject of the If clause, in the domain list in the Then clause pane.</span></span> <span data-ttu-id="d42e1-150">然後，使用您在建置 If 子句時所進行的相同步驟來建置 Then 子句。</span><span class="sxs-lookup"><span data-stu-id="d42e1-150">Then build the Then clause using the same steps that you did in building the If clause.</span></span>  
  
9. <span data-ttu-id="d42e1-151">繼續進行下列測試程序。</span><span class="sxs-lookup"><span data-stu-id="d42e1-151">Proceed to the testing procedure below.</span></span>  
  
##  <a name="test-cross-domain-rules"></a><a name="Test"></a> <span data-ttu-id="d42e1-152">測試跨定義域規則</span><span class="sxs-lookup"><span data-stu-id="d42e1-152">Test Cross-Domain Rules</span></span>  
  
1.  <span data-ttu-id="d42e1-153">依照下列方式測試跨定義域規則：</span><span class="sxs-lookup"><span data-stu-id="d42e1-153">Test the cross-domain rule as follows:</span></span>  
  
    1.  <span data-ttu-id="d42e1-154">按一下複合定義域窗格右上角的 **[在測試資料上執行選取的定義域規則]** 圖示。</span><span class="sxs-lookup"><span data-stu-id="d42e1-154">Click the **Run the selected domain rule on test data to** icon in the upper right-hand corner of the composite domain pane.</span></span>  
  
    2.  <span data-ttu-id="d42e1-155">在 **[測試定義域規則]** 對話方塊中，按一下 **[加入定義域規則的新測試詞彙]** 圖示。</span><span class="sxs-lookup"><span data-stu-id="d42e1-155">In the **Test Domain Rule** dialog box, click the **Adds a New Testing Term for the Domain Rule** icon.</span></span>  
  
    3.  <span data-ttu-id="d42e1-156">針對與 If 子句相關聯的單一定義域以及與 Then 子句相關聯的單一定義域輸入測試值。</span><span class="sxs-lookup"><span data-stu-id="d42e1-156">Enter test values for the single domain associated with the If clause and the single domain associated with the Then clause.</span></span> <span data-ttu-id="d42e1-157">在 If 子句中輸入的測試值必須符合該子句的條件，否則系統將在 **[有效性]** 資料行中輸入問號，表示跨定義域規則不適用於測試資料。</span><span class="sxs-lookup"><span data-stu-id="d42e1-157">The test values entered in the If clause must meet the conditions for that clause, or a question mark will be entered in the **Validity** column indicating that the cross-domain rule does not apply to the test data.</span></span>  
  
    4.  <span data-ttu-id="d42e1-158">再次按一下 **[加入定義域規則的新測試詞彙]** 圖示，加入另一組測試值。</span><span class="sxs-lookup"><span data-stu-id="d42e1-158">Click the **Adds a new testing term for the domain rule** icon again to add another set of test values.</span></span>  
  
    5.  <span data-ttu-id="d42e1-159">按一下 [**對所有詞彙測試定義域規則**] 圖示。</span><span class="sxs-lookup"><span data-stu-id="d42e1-159">Click the **Test the Domain Rule on All the Terms** icon.</span></span> <span data-ttu-id="d42e1-160">如果某組測試值有效，DQS 就會在該資料列的 **[有效性]** 資料行中輸入核取記號。</span><span class="sxs-lookup"><span data-stu-id="d42e1-160">If a set of test values is valid, DQS will enter a check in the **Validity** column for the row.</span></span> <span data-ttu-id="d42e1-161">如果某組測試值無效，DQS 就會在該資料列的 [有效性] 資料行中輸入含驚嘆號的三角形。</span><span class="sxs-lookup"><span data-stu-id="d42e1-161">If the set of test values is not valid, DQS will enter a triangle with an exclamation point in the Validity column for the row.</span></span>  
  
    6.  <span data-ttu-id="d42e1-162">測試完成之後，請在 **[測試複合定義域規則]** 對話方塊中按一下 **[關閉]** 。</span><span class="sxs-lookup"><span data-stu-id="d42e1-162">After your testing is complete, click **Close** in the **Test Composite Domain Rule** dialog box.</span></span>  
  
2.  <span data-ttu-id="d42e1-163">當您完成跨定義域規則時，請按一下 **[完成]** ，完成定義域管理活動，如＜ [End the Domain Management Activity](../../2014/data-quality-services/end-the-domain-management-activity.md)＞中所述。</span><span class="sxs-lookup"><span data-stu-id="d42e1-163">When you have completed your cross-domain rules, click **Finish** to complete the domain management activity, as described in [End the Domain Management Activity](../../2014/data-quality-services/end-the-domain-management-activity.md).</span></span>  
  
##  <a name="follow-up-after-creating-a-cross-domain-rule"></a><a name="FollowUp"></a> <span data-ttu-id="d42e1-164">後續操作：建立跨定義域規則之後</span><span class="sxs-lookup"><span data-stu-id="d42e1-164">Follow Up: After Creating a Cross-Domain Rule</span></span>  
 <span data-ttu-id="d42e1-165">在建立跨定義域規則之後，您可以針對定義域執行其他定義域管理工作、執行知識探索來將知識加入至定義域，或者將比對原則加入至定義域。</span><span class="sxs-lookup"><span data-stu-id="d42e1-165">After you create a cross-down rule, you can perform other domain management tasks on the domain, you can perform knowledge discovery to add knowledge to the domain, or you can add a matching policy to the domain.</span></span> <span data-ttu-id="d42e1-166">如需詳細資訊，請參閱[執行知識探索](../../2014/data-quality-services/perform-knowledge-discovery.md)、[管理定義域](../../2014/data-quality-services/managing-a-domain.md)或[建立比對原則](../../2014/data-quality-services/create-a-matching-policy.md)。</span><span class="sxs-lookup"><span data-stu-id="d42e1-166">For more information, see [Perform Knowledge Discovery](../../2014/data-quality-services/perform-knowledge-discovery.md), [Managing a Domain](../../2014/data-quality-services/managing-a-domain.md), or [Create a Matching Policy](../../2014/data-quality-services/create-a-matching-policy.md).</span></span>  
  
  
