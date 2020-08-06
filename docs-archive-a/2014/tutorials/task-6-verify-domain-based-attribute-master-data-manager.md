---
title: 工作6：確認已使用主資料管理員建立網域屬性（Attribute） |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 6e90517a-910c-4c33-8f11-92ac3cff4fdc
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: ea26202ca9e607058b1e385957be3ea3d04038b3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584879"
---
# <a name="task-6-verify-that-the-domain-based-attribute-is-created-using-master-data-manager"></a><span data-ttu-id="7e354-102">工作 6：確認已使用主資料管理員建立定義域屬性</span><span class="sxs-lookup"><span data-stu-id="7e354-102">Task 6: Verify that the Domain-Based Attribute is Created using Master Data Manager</span></span>
  <span data-ttu-id="7e354-103">在這項工作中，您會透過 [主資料管理員]\*\*\*\* 來確認 **MDS** 中已建立 **State** 實體，而且 **Supplier** 實體的 **State** 屬性為相依於 **State** 實體的網域屬性。</span><span class="sxs-lookup"><span data-stu-id="7e354-103">In this task, you verify that the **State** entity is created in **MDS** and the **State** attribute of the **Supplier** entity is a domain-based attribute that depends on the **State** entity by using **Master Data Manager**.</span></span>

1.  <span data-ttu-id="7e354-104">切換到 [主資料管理員]\*\*\*\* Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="7e354-104">Switch to the **Master Data Manger** web application.</span></span>

2.  <span data-ttu-id="7e354-105">按一下頂端的 [SQL Server 2012 Master Data Services]\*\*\*\*，回到首頁。</span><span class="sxs-lookup"><span data-stu-id="7e354-105">Click **SQL Server 2012 Master Data Services** at the top to get to the home page.</span></span>

3.  <span data-ttu-id="7e354-106">確定已選取 [Supplier]\*\*\*\* 模型，然後按一下 [總管]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7e354-106">Ensure that **Suppliers** model is selected and click **Explorer**.</span></span> <span data-ttu-id="7e354-107">如果您已經開啟 [總管]\*\*\*\*，可以重新整理頁面。</span><span class="sxs-lookup"><span data-stu-id="7e354-107">You could refresh the page if you already had **Explorer** open.</span></span>

4.  <span data-ttu-id="7e354-108">將滑鼠停留在功能表列的 [實體]\*\*\*\* 上方，並注意現在有兩個實體：**Supplier** 和 **State**。</span><span class="sxs-lookup"><span data-stu-id="7e354-108">Hover your mouse over **Entities** on the menu bar and notice that now there are two entities: **Supplier** and **State**.</span></span>

     <span data-ttu-id="7e354-109">![含 [省/市] 和 [供應商] 的 [實體] 功能表](../../2014/tutorials/media/et-verifythatthedbaiscreatedusingmdm-01.jpg "含 [省/市] 和 [供應商] 的 [實體] 功能表")</span><span class="sxs-lookup"><span data-stu-id="7e354-109">![Entities Menu with State and Supplier](../../2014/tutorials/media/et-verifythatthedbaiscreatedusingmdm-01.jpg "Entities Menu with State and Supplier")</span></span>

5.  <span data-ttu-id="7e354-110">按一下 [State]\*\*\*\* (如果尚未開啟此實體)。</span><span class="sxs-lookup"><span data-stu-id="7e354-110">Click **State** if the entity is not open already.</span></span>

6.  <span data-ttu-id="7e354-111">從清單中選取 [GA]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7e354-111">Select **GA** from the list.</span></span>

7.  <span data-ttu-id="7e354-112">在右邊的 [詳細資料]\*\*\*\* 窗格中，將 [名稱]\*\*\*\* 變更為右窗格\*\*\*\* 的 **Georgia**，然後按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7e354-112">In the **Details** pane to the right, change the **Name** to **Georgia** in the **right pane**, and click **OK**.</span></span>

8.  <span data-ttu-id="7e354-113">針對其他州重複上述步驟。</span><span class="sxs-lookup"><span data-stu-id="7e354-113">Repeat the previous steps for other states.</span></span>

    |<span data-ttu-id="7e354-114">程式碼</span><span class="sxs-lookup"><span data-stu-id="7e354-114">Code</span></span>|<span data-ttu-id="7e354-115">名稱</span><span class="sxs-lookup"><span data-stu-id="7e354-115">Name</span></span>|
    |----------|----------|
    |<span data-ttu-id="7e354-116">CA</span><span class="sxs-lookup"><span data-stu-id="7e354-116">CA</span></span>|<span data-ttu-id="7e354-117">California</span><span class="sxs-lookup"><span data-stu-id="7e354-117">California</span></span>|
    |<span data-ttu-id="7e354-118">CO</span><span class="sxs-lookup"><span data-stu-id="7e354-118">CO</span></span>|<span data-ttu-id="7e354-119">Colorado</span><span class="sxs-lookup"><span data-stu-id="7e354-119">Colorado</span></span>|
    |<span data-ttu-id="7e354-120">IL</span><span class="sxs-lookup"><span data-stu-id="7e354-120">IL</span></span>|<span data-ttu-id="7e354-121">伊利諾州</span><span class="sxs-lookup"><span data-stu-id="7e354-121">Illinois</span></span>|
    |<span data-ttu-id="7e354-122">DC</span><span class="sxs-lookup"><span data-stu-id="7e354-122">DC</span></span>|<span data-ttu-id="7e354-123">District of Columbia</span><span class="sxs-lookup"><span data-stu-id="7e354-123">District of Columbia</span></span>|
    |<span data-ttu-id="7e354-124">FL</span><span class="sxs-lookup"><span data-stu-id="7e354-124">FL</span></span>|<span data-ttu-id="7e354-125">Florida</span><span class="sxs-lookup"><span data-stu-id="7e354-125">Florida</span></span>|
    |<span data-ttu-id="7e354-126">AL</span><span class="sxs-lookup"><span data-stu-id="7e354-126">AL</span></span>|<span data-ttu-id="7e354-127">Alabama</span><span class="sxs-lookup"><span data-stu-id="7e354-127">Alabama</span></span>|
    |<span data-ttu-id="7e354-128">KY</span><span class="sxs-lookup"><span data-stu-id="7e354-128">KY</span></span>|<span data-ttu-id="7e354-129">Kentucky</span><span class="sxs-lookup"><span data-stu-id="7e354-129">Kentucky</span></span>|
    |<span data-ttu-id="7e354-130">MA</span><span class="sxs-lookup"><span data-stu-id="7e354-130">MA</span></span>|<span data-ttu-id="7e354-131">Massachusetts</span><span class="sxs-lookup"><span data-stu-id="7e354-131">Massachusetts</span></span>|
    |<span data-ttu-id="7e354-132">AZ</span><span class="sxs-lookup"><span data-stu-id="7e354-132">AZ</span></span>|<span data-ttu-id="7e354-133">Arizona</span><span class="sxs-lookup"><span data-stu-id="7e354-133">Arizona</span></span>|
    |<span data-ttu-id="7e354-134">MI</span><span class="sxs-lookup"><span data-stu-id="7e354-134">MI</span></span>|<span data-ttu-id="7e354-135">Michigan</span><span class="sxs-lookup"><span data-stu-id="7e354-135">Michigan</span></span>|
    |<span data-ttu-id="7e354-136">MN</span><span class="sxs-lookup"><span data-stu-id="7e354-136">MN</span></span>|<span data-ttu-id="7e354-137">Minnesota</span><span class="sxs-lookup"><span data-stu-id="7e354-137">Minnesota</span></span>|
    |<span data-ttu-id="7e354-138">NJ</span><span class="sxs-lookup"><span data-stu-id="7e354-138">NJ</span></span>|<span data-ttu-id="7e354-139">New Jersey</span><span class="sxs-lookup"><span data-stu-id="7e354-139">New Jersey</span></span>|
    |<span data-ttu-id="7e354-140">NV</span><span class="sxs-lookup"><span data-stu-id="7e354-140">NV</span></span>|<span data-ttu-id="7e354-141">Nevada</span><span class="sxs-lookup"><span data-stu-id="7e354-141">Nevada</span></span>|
    |<span data-ttu-id="7e354-142">NY</span><span class="sxs-lookup"><span data-stu-id="7e354-142">NY</span></span>|<span data-ttu-id="7e354-143">紐約</span><span class="sxs-lookup"><span data-stu-id="7e354-143">New York</span></span>|
    |<span data-ttu-id="7e354-144">OH</span><span class="sxs-lookup"><span data-stu-id="7e354-144">OH</span></span>|<span data-ttu-id="7e354-145">Ohio</span><span class="sxs-lookup"><span data-stu-id="7e354-145">Ohio</span></span>|
    |<span data-ttu-id="7e354-146">確定</span><span class="sxs-lookup"><span data-stu-id="7e354-146">OK</span></span>|<span data-ttu-id="7e354-147">Oklahoma</span><span class="sxs-lookup"><span data-stu-id="7e354-147">Oklahoma</span></span>|
    |<span data-ttu-id="7e354-148">或者</span><span class="sxs-lookup"><span data-stu-id="7e354-148">OR</span></span>|<span data-ttu-id="7e354-149">Oregon</span><span class="sxs-lookup"><span data-stu-id="7e354-149">Oregon</span></span>|
    |<span data-ttu-id="7e354-150">PA</span><span class="sxs-lookup"><span data-stu-id="7e354-150">PA</span></span>|<span data-ttu-id="7e354-151">Pennsylvania</span><span class="sxs-lookup"><span data-stu-id="7e354-151">Pennsylvania</span></span>|
    |<span data-ttu-id="7e354-152">SC</span><span class="sxs-lookup"><span data-stu-id="7e354-152">SC</span></span>|<span data-ttu-id="7e354-153">South Carolina</span><span class="sxs-lookup"><span data-stu-id="7e354-153">South Carolina</span></span>|
    |<span data-ttu-id="7e354-154">KS</span><span class="sxs-lookup"><span data-stu-id="7e354-154">KS</span></span>|<span data-ttu-id="7e354-155">Kansas</span><span class="sxs-lookup"><span data-stu-id="7e354-155">Kansas</span></span>|
    |<span data-ttu-id="7e354-156">TN</span><span class="sxs-lookup"><span data-stu-id="7e354-156">TN</span></span>|<span data-ttu-id="7e354-157">Tennessee</span><span class="sxs-lookup"><span data-stu-id="7e354-157">Tennessee</span></span>|
    |<span data-ttu-id="7e354-158">TX</span><span class="sxs-lookup"><span data-stu-id="7e354-158">TX</span></span>|<span data-ttu-id="7e354-159">Texas</span><span class="sxs-lookup"><span data-stu-id="7e354-159">Texas</span></span>|
    |<span data-ttu-id="7e354-160">UT</span><span class="sxs-lookup"><span data-stu-id="7e354-160">UT</span></span>|<span data-ttu-id="7e354-161">Utah</span><span class="sxs-lookup"><span data-stu-id="7e354-161">Utah</span></span>|
    |<span data-ttu-id="7e354-162">VA</span><span class="sxs-lookup"><span data-stu-id="7e354-162">VA</span></span>|<span data-ttu-id="7e354-163">維吉尼亞州</span><span class="sxs-lookup"><span data-stu-id="7e354-163">Virginia</span></span>|
    |<span data-ttu-id="7e354-164">WA</span><span class="sxs-lookup"><span data-stu-id="7e354-164">WA</span></span>|<span data-ttu-id="7e354-165">Washington</span><span class="sxs-lookup"><span data-stu-id="7e354-165">Washington</span></span>|
    |<span data-ttu-id="7e354-166">WI</span><span class="sxs-lookup"><span data-stu-id="7e354-166">WI</span></span>|<span data-ttu-id="7e354-167">Wisconsin</span><span class="sxs-lookup"><span data-stu-id="7e354-167">Wisconsin</span></span>|
    |<span data-ttu-id="7e354-168">HI</span><span class="sxs-lookup"><span data-stu-id="7e354-168">HI</span></span>|<span data-ttu-id="7e354-169">Hawaii</span><span class="sxs-lookup"><span data-stu-id="7e354-169">Hawaii</span></span>|
    |<span data-ttu-id="7e354-170">MD</span><span class="sxs-lookup"><span data-stu-id="7e354-170">MD</span></span>|<span data-ttu-id="7e354-171">Maryland</span><span class="sxs-lookup"><span data-stu-id="7e354-171">Maryland</span></span>|
    |<span data-ttu-id="7e354-172">CT</span><span class="sxs-lookup"><span data-stu-id="7e354-172">CT</span></span>|<span data-ttu-id="7e354-173">Connecticut</span><span class="sxs-lookup"><span data-stu-id="7e354-173">Connecticut</span></span>|

9. <span data-ttu-id="7e354-174">選取任何州，並從工具列按一下 [檢視交易]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7e354-174">Select any of the state entries and click **View Transactions** from the Toolbar.</span></span> <span data-ttu-id="7e354-175">您應該會看到您剛才更新的交易出現在交易清單中。</span><span class="sxs-lookup"><span data-stu-id="7e354-175">You should see the transaction for the update you just made is in the list of transactions.</span></span>

10. <span data-ttu-id="7e354-176">將滑鼠停留在 [實體]\*\*\*\* 功能表上方，並按一下 [Supplier]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7e354-176">Hover the mouse over **Entities** menu and click **Supplier**.</span></span>

11. <span data-ttu-id="7e354-177">現在，請注意可以使用下拉式清單在 [詳細資料]\*\*\*\* 窗格中變更 [State]\*\*\*\* 欄位的值。</span><span class="sxs-lookup"><span data-stu-id="7e354-177">Now, notice that a value for the **State** field can be changed in the **Details** pane by using the drop-down list.</span></span> <span data-ttu-id="7e354-178">您也可以看到，在左邊的清單中以及 [詳細資料]\*\*\*\* 窗格的下拉式清單中，都會先顯示代碼，然後是大括號中的名稱。</span><span class="sxs-lookup"><span data-stu-id="7e354-178">You can also see that, in the list to the left and in the drop-down list in the **Details** pane, code is displayed first and then the name in curly braces.</span></span> <span data-ttu-id="7e354-179">您也可以在 [詳細資料]\*\*\*\* 窗格中變更其他任何值。</span><span class="sxs-lookup"><span data-stu-id="7e354-179">You can also change any other value in the **Details** pane.</span></span>

     <span data-ttu-id="7e354-180">![含 [更新代碼] 和 [名稱] 的屬性狀態](../../2014/tutorials/media/et-verifythatthedbaiscreatedusingmdm-02.jpg "含 [更新代碼] 和 [名稱] 的屬性狀態")</span><span class="sxs-lookup"><span data-stu-id="7e354-180">![State Attribute with Updated Code and Names](../../2014/tutorials/media/et-verifythatthedbaiscreatedusingmdm-02.jpg "State Attribute with Updated Code and Names")</span></span>

## <a name="next-step"></a><span data-ttu-id="7e354-181">後續步驟</span><span class="sxs-lookup"><span data-stu-id="7e354-181">Next Step</span></span>
 [<span data-ttu-id="7e354-182">工作 7：檢視您在 Excel 中使用主資料管理員所做的更新</span><span class="sxs-lookup"><span data-stu-id="7e354-182">Task 7: Viewing Updates Made using Master Data Manager in Excel</span></span>](../../2014/tutorials/task-7-viewing-updates-made-using-master-data-manager-in-excel.md)


