---
title: 多維度模型中的動作 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- actions [Analysis Services], creating
- report actions [Analysis Services]
- drillthrough actions [Analysis Services]
- cubes [Analysis Services], actions
ms.assetid: b9fee2b9-05a5-4077-848d-d8457326dc27
author: minewiskan
ms.author: owend
ms.openlocfilehash: ce42907190363be085e8f4d8e9adfbab52a70590
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594761"
---
# <a name="actions-in-multidimensional-models"></a><span data-ttu-id="b71fc-102">多維度模型中的動作</span><span class="sxs-lookup"><span data-stu-id="b71fc-102">Actions in Multidimensional Models</span></span>
  <span data-ttu-id="b71fc-103">動作是使用者在所選取的 Cube 或部分 Cube 上所起始的作業。</span><span class="sxs-lookup"><span data-stu-id="b71fc-103">An action is an end user-initiated operation upon a selected cube or portion of a cube.</span></span> <span data-ttu-id="b71fc-104">這個作業可以使用所選取項目做為參數來啟動應用程式，或擷取關於所選取項目的資訊。</span><span class="sxs-lookup"><span data-stu-id="b71fc-104">The operation can start an application with the selected item as a parameter, or it can retrieve information about the selected item.</span></span> <span data-ttu-id="b71fc-105">如需動作的詳細資訊，請參閱[動作 &#40;Analysis Services - 多維度資料&#41;](actions-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="b71fc-105">For more information about actions, see [Actions &#40;Analysis Services - Multidimensional Data&#41;](actions-analysis-services-multidimensional-data.md).</span></span>  
  
 <span data-ttu-id="b71fc-106">使用 Cube 設計師的 [動作]\*\*\*\* 索引標籤來建立 Cube 的動作。</span><span class="sxs-lookup"><span data-stu-id="b71fc-106">Use the **Actions** tab of Cube Designer to build actions for a cube.</span></span> <span data-ttu-id="b71fc-107">指定下列項目：</span><span class="sxs-lookup"><span data-stu-id="b71fc-107">Specify the following:</span></span>  
  
 <span data-ttu-id="b71fc-108">**名稱**</span><span class="sxs-lookup"><span data-stu-id="b71fc-108">**Name**</span></span>  
 <span data-ttu-id="b71fc-109">選取用來識別動作的名稱。</span><span class="sxs-lookup"><span data-stu-id="b71fc-109">Select a name that identifies the action.</span></span>  
  
 <span data-ttu-id="b71fc-110">**動作目標**</span><span class="sxs-lookup"><span data-stu-id="b71fc-110">**Action Target**</span></span>  
 <span data-ttu-id="b71fc-111">選取動作所附加的對象物件。</span><span class="sxs-lookup"><span data-stu-id="b71fc-111">Select the object to which the action is attached.</span></span> <span data-ttu-id="b71fc-112">一般而言，在用戶端應用程式中，當使用者選取目標物件時便會顯示動作；但是，用戶端程式會決定哪一個使用者作業顯示動作。</span><span class="sxs-lookup"><span data-stu-id="b71fc-112">Generally, in client applications, the action is displayed when end users select the target object; however, the client application determines which end-user operation displays actions.</span></span> <span data-ttu-id="b71fc-113">若為 [目標類型]\*\*\*\*，請從下列物件中選取：</span><span class="sxs-lookup"><span data-stu-id="b71fc-113">For **Target type**, select from the following objects:</span></span>  
  
-   <span data-ttu-id="b71fc-114">屬性成員</span><span class="sxs-lookup"><span data-stu-id="b71fc-114">Attribute members</span></span>  
  
-   <span data-ttu-id="b71fc-115">資料格</span><span class="sxs-lookup"><span data-stu-id="b71fc-115">Cells</span></span>  
  
-   <span data-ttu-id="b71fc-116">Cube</span><span class="sxs-lookup"><span data-stu-id="b71fc-116">Cube</span></span>  
  
-   <span data-ttu-id="b71fc-117">維度成員</span><span class="sxs-lookup"><span data-stu-id="b71fc-117">Dimension members</span></span>  
  
-   <span data-ttu-id="b71fc-118">階層</span><span class="sxs-lookup"><span data-stu-id="b71fc-118">Hierarchy</span></span>  
  
-   <span data-ttu-id="b71fc-119">階層成員</span><span class="sxs-lookup"><span data-stu-id="b71fc-119">Hierarchy members</span></span>  
  
-   <span data-ttu-id="b71fc-120">層級</span><span class="sxs-lookup"><span data-stu-id="b71fc-120">Level</span></span>  
  
-   <span data-ttu-id="b71fc-121">層級成員</span><span class="sxs-lookup"><span data-stu-id="b71fc-121">Level members</span></span>  
  
 <span data-ttu-id="b71fc-122">選取目標物件類型之後，在 [目標物件]\*\*\*\* 下，選取指定類型的 Cube 物件。</span><span class="sxs-lookup"><span data-stu-id="b71fc-122">After you select the target object type, under **Target object**, select the cube object of the designated type.</span></span>  
  
 <span data-ttu-id="b71fc-123">**條件 (選擇性)**</span><span class="sxs-lookup"><span data-stu-id="b71fc-123">**Condition (Optional)**</span></span>  
 <span data-ttu-id="b71fc-124">指定解析成布林值的選擇性多維度運算式 (MDX) 運算式。</span><span class="sxs-lookup"><span data-stu-id="b71fc-124">Specify an optional Multidimensional Expressions (MDX) expression that resolves to a Boolean value.</span></span> <span data-ttu-id="b71fc-125">如果值為 `True`，就會在指定的目標上執行動作。</span><span class="sxs-lookup"><span data-stu-id="b71fc-125">If the value is `True`, the action is performed on the specified target.</span></span> <span data-ttu-id="b71fc-126">如果值為 `False`，則不會執行動作。</span><span class="sxs-lookup"><span data-stu-id="b71fc-126">If the value is `False`, the action is not performed.</span></span>  
  
 <span data-ttu-id="b71fc-127">**動作內容**</span><span class="sxs-lookup"><span data-stu-id="b71fc-127">**Action Content**</span></span>  
 <span data-ttu-id="b71fc-128">選取動作的類型。</span><span class="sxs-lookup"><span data-stu-id="b71fc-128">Select the type of action.</span></span> <span data-ttu-id="b71fc-129">下表摘要可以使用的類型。</span><span class="sxs-lookup"><span data-stu-id="b71fc-129">The following table summarizes the available types.</span></span>  
  
|<span data-ttu-id="b71fc-130">類型</span><span class="sxs-lookup"><span data-stu-id="b71fc-130">Type</span></span>|<span data-ttu-id="b71fc-131">描述</span><span class="sxs-lookup"><span data-stu-id="b71fc-131">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="b71fc-132">資料集</span><span class="sxs-lookup"><span data-stu-id="b71fc-132">Data Set</span></span>|<span data-ttu-id="b71fc-133">擷取資料集。</span><span class="sxs-lookup"><span data-stu-id="b71fc-133">Retrieves a dataset.</span></span>|  
|<span data-ttu-id="b71fc-134">專屬</span><span class="sxs-lookup"><span data-stu-id="b71fc-134">Proprietary</span></span>|<span data-ttu-id="b71fc-135">使用不同於此資料表列出的介面來執行作業。</span><span class="sxs-lookup"><span data-stu-id="b71fc-135">Performs an operation by using an interface other than those listed in this table.</span></span>|  
|<span data-ttu-id="b71fc-136">資料列集</span><span class="sxs-lookup"><span data-stu-id="b71fc-136">Row Set</span></span>|<span data-ttu-id="b71fc-137">擷取資料列集。</span><span class="sxs-lookup"><span data-stu-id="b71fc-137">Retrieves a rowset.</span></span>|  
|<span data-ttu-id="b71fc-138">陳述式</span><span class="sxs-lookup"><span data-stu-id="b71fc-138">Statement</span></span>|<span data-ttu-id="b71fc-139">執行 OLE DB 命令。</span><span class="sxs-lookup"><span data-stu-id="b71fc-139">Runs an OLE DB command.</span></span>|  
|<span data-ttu-id="b71fc-140">URL</span><span class="sxs-lookup"><span data-stu-id="b71fc-140">URL</span></span>|<span data-ttu-id="b71fc-141">在網際網路瀏覽器中顯示變數網頁。</span><span class="sxs-lookup"><span data-stu-id="b71fc-141">Displays a variable page in an Internet browser.</span></span>|  
  
 <span data-ttu-id="b71fc-142">若為 [動作運算式]\*\*\*\*，指定執行動作時會傳遞的參數。</span><span class="sxs-lookup"><span data-stu-id="b71fc-142">For **Action Expression**, specify the parameters that are passed when the action is run.</span></span> <span data-ttu-id="b71fc-143">語法必須評估為字串，而且必須包含以 MDX 撰寫的運算式。</span><span class="sxs-lookup"><span data-stu-id="b71fc-143">The syntax must evaluate to a string, and you must include an expression written in MDX.</span></span> <span data-ttu-id="b71fc-144">例如，您的 MDX 運算式可以表示語法中所包含之 Cube 的一部分。</span><span class="sxs-lookup"><span data-stu-id="b71fc-144">For example, your MDX expression can indicate a part of the cube that is included in the syntax.</span></span> <span data-ttu-id="b71fc-145">在傳遞參數之前會先評估 MDX 運算式。</span><span class="sxs-lookup"><span data-stu-id="b71fc-145">MDX expressions are evaluated before the parameters are passed.</span></span> <span data-ttu-id="b71fc-146">另外，MDX 產生器可以協助您建立 MDX 運算式。</span><span class="sxs-lookup"><span data-stu-id="b71fc-146">Also, MDX Builder is available to help you build MDX expressions.</span></span>  
  
 <span data-ttu-id="b71fc-147">**其他屬性**</span><span class="sxs-lookup"><span data-stu-id="b71fc-147">**Additional Properties**</span></span>  
 <span data-ttu-id="b71fc-148">選取屬性。</span><span class="sxs-lookup"><span data-stu-id="b71fc-148">Select the property.</span></span> <span data-ttu-id="b71fc-149">下表摘要可以使用的屬性。</span><span class="sxs-lookup"><span data-stu-id="b71fc-149">The following table summarizes the available properties.</span></span>  
  
|<span data-ttu-id="b71fc-150">屬性</span><span class="sxs-lookup"><span data-stu-id="b71fc-150">Property</span></span>|<span data-ttu-id="b71fc-151">描述</span><span class="sxs-lookup"><span data-stu-id="b71fc-151">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="b71fc-152">**引動過程**</span><span class="sxs-lookup"><span data-stu-id="b71fc-152">**Invocation**</span></span>|<span data-ttu-id="b71fc-153">指定動作如何執行。</span><span class="sxs-lookup"><span data-stu-id="b71fc-153">Specifies how the action is run.</span></span> <span data-ttu-id="b71fc-154">預設為互動式，會指定使用者存取物件時執行的動作。</span><span class="sxs-lookup"><span data-stu-id="b71fc-154">Interactive, the default, specifies that the action is run when a user accesses an object.</span></span> <span data-ttu-id="b71fc-155">可能的設定有：</span><span class="sxs-lookup"><span data-stu-id="b71fc-155">The possible settings are:</span></span><br /><br /> <span data-ttu-id="b71fc-156">Batch</span><span class="sxs-lookup"><span data-stu-id="b71fc-156">Batch</span></span><br /><br /> <span data-ttu-id="b71fc-157">互動式</span><span class="sxs-lookup"><span data-stu-id="b71fc-157">Interactive</span></span><br /><br /> <span data-ttu-id="b71fc-158">開啟時</span><span class="sxs-lookup"><span data-stu-id="b71fc-158">On Open</span></span>|  
|<span data-ttu-id="b71fc-159">**應用程式**</span><span class="sxs-lookup"><span data-stu-id="b71fc-159">**Application**</span></span>|<span data-ttu-id="b71fc-160">描述動作的應用程式。</span><span class="sxs-lookup"><span data-stu-id="b71fc-160">Describes the application of the action.</span></span>|  
|<span data-ttu-id="b71fc-161">**說明**</span><span class="sxs-lookup"><span data-stu-id="b71fc-161">**Description**</span></span>|<span data-ttu-id="b71fc-162">描述動作。</span><span class="sxs-lookup"><span data-stu-id="b71fc-162">Describes the action.</span></span>|  
|<span data-ttu-id="b71fc-163">**Caption**</span><span class="sxs-lookup"><span data-stu-id="b71fc-163">**Caption**</span></span>|<span data-ttu-id="b71fc-164">提供為動作顯示的標題。</span><span class="sxs-lookup"><span data-stu-id="b71fc-164">Provides a caption that is displayed for the action.</span></span> <span data-ttu-id="b71fc-165">如果標題是 MDX，請 `True` 針對 [**標題是 mdx**] 指定。</span><span class="sxs-lookup"><span data-stu-id="b71fc-165">If the caption is MDX, specify `True` for **Caption is MDX**.</span></span>|  
|<span data-ttu-id="b71fc-166">**標題是 MDX**</span><span class="sxs-lookup"><span data-stu-id="b71fc-166">**Caption is MDX**</span></span>|<span data-ttu-id="b71fc-167">如果標題是 MDX，請指定 `True`；如果不是 MDX，則指定 `False`。</span><span class="sxs-lookup"><span data-stu-id="b71fc-167">Specify `True` if the caption is MDX or `False` if it is not.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="b71fc-168">您必須使用 Analysis Services 指令碼語言 (ASSL) 或分析管理物件 (AMO) 來定義 HTML 和命令列動作類型。</span><span class="sxs-lookup"><span data-stu-id="b71fc-168">You must use Analysis Services Scripting Language (ASSL) or Analysis Management Objects (AMO) to define HTML and Command Line action types.</span></span> <span data-ttu-id="b71fc-169">如需詳細資訊，請參閱 [Action 元素 &#40;ASSL&#41;](https://docs.microsoft.com/bi-reference/assl/objects/action-element-assl)、[Type 元素 &#40;Action&#41; &#40;ASSL&#41;](https://docs.microsoft.com/bi-reference/assl/properties/type-element-action-assl) 和[設計 AMO OLAP 進階物件的程式](https://docs.microsoft.com/bi-reference/amo/programming-amo-olap-advanced-objects)。</span><span class="sxs-lookup"><span data-stu-id="b71fc-169">For more information, see [Action Element &#40;ASSL&#41;](https://docs.microsoft.com/bi-reference/assl/objects/action-element-assl), [Type Element &#40;Action&#41; &#40;ASSL&#41;](https://docs.microsoft.com/bi-reference/assl/properties/type-element-action-assl), and [Programming AMO OLAP Advanced Objects](https://docs.microsoft.com/bi-reference/amo/programming-amo-olap-advanced-objects).</span></span>  
  
## <a name="creating-a-reporting-action"></a><span data-ttu-id="b71fc-170">建立報表動作</span><span class="sxs-lookup"><span data-stu-id="b71fc-170">Creating a Reporting Action</span></span>  
 <span data-ttu-id="b71fc-171">報表伺服器會回應以 URL 為基礎的報表要求。</span><span class="sxs-lookup"><span data-stu-id="b71fc-171">The report server responds to URL-based requests for reports.</span></span> <span data-ttu-id="b71fc-172">若要建立報表動作，請在 [Cube]\*\*\*\* 功能表上，按一下 [新增報表動作]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b71fc-172">To create a reporting action, on the **Cube** menu, click **New Reporting Action**.</span></span> <span data-ttu-id="b71fc-173">下列選項是報表動作特有的選項。</span><span class="sxs-lookup"><span data-stu-id="b71fc-173">The following options are specific to a reporting action.</span></span>  
  
 <span data-ttu-id="b71fc-174">**報表伺服器**</span><span class="sxs-lookup"><span data-stu-id="b71fc-174">**Report Server**</span></span>  
 <span data-ttu-id="b71fc-175">下表中描述的屬性是為報表伺服器指定的。</span><span class="sxs-lookup"><span data-stu-id="b71fc-175">The properties described in the following table are specified for the report server.</span></span>  
  
|<span data-ttu-id="b71fc-176">屬性</span><span class="sxs-lookup"><span data-stu-id="b71fc-176">Property</span></span>|<span data-ttu-id="b71fc-177">描述</span><span class="sxs-lookup"><span data-stu-id="b71fc-177">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="b71fc-178">**伺服器名稱**</span><span class="sxs-lookup"><span data-stu-id="b71fc-178">**Server name**</span></span>|<span data-ttu-id="b71fc-179">正在執行報表伺服器的電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="b71fc-179">The name of the computer running report server.</span></span>|  
|<span data-ttu-id="b71fc-180">**伺服器路徑**</span><span class="sxs-lookup"><span data-stu-id="b71fc-180">**Server path**</span></span>|<span data-ttu-id="b71fc-181">報表伺服器所公開的路徑。</span><span class="sxs-lookup"><span data-stu-id="b71fc-181">The path exposed by report server.</span></span>|  
|<span data-ttu-id="b71fc-182">**報表格式**</span><span class="sxs-lookup"><span data-stu-id="b71fc-182">**Report format**</span></span>|<span data-ttu-id="b71fc-183">HTML5、HTML3、Excel 或 PDF。</span><span class="sxs-lookup"><span data-stu-id="b71fc-183">HTML5, HTML3, Excel, or PDF.</span></span>|  
  
 <span data-ttu-id="b71fc-184">**參數 (選擇性)**</span><span class="sxs-lookup"><span data-stu-id="b71fc-184">**Parameters (Optional)**</span></span>  
 <span data-ttu-id="b71fc-185">建立動作時，會將參數傳送到伺服器做為 URL 字串的一部分。</span><span class="sxs-lookup"><span data-stu-id="b71fc-185">The parameters are sent to the server as part of the URL string when the action is created.</span></span> <span data-ttu-id="b71fc-186">這些參數包括 [參數名稱]\*\*\*\* 和 [參數值]\*\*\*\*，後者為 MDX 運算式。</span><span class="sxs-lookup"><span data-stu-id="b71fc-186">They include **Parameter Name** and **Parameter Value**, which is an MDX expression.</span></span>  
  
 <span data-ttu-id="b71fc-187">報表伺服器 URL 的建構如下：</span><span class="sxs-lookup"><span data-stu-id="b71fc-187">The report server URL is constructed as follows:</span></span>  
  
```  
  
http://  
host  
/  
virtualdirectory  
/Path&  
parametername1  
=  
parametervalue1  
& ...  
```  
  
 <span data-ttu-id="b71fc-188">例如：</span><span class="sxs-lookup"><span data-stu-id="b71fc-188">For example:</span></span>  
  
```  
http://localhost/ReportServer/Sales/YearlySalesByCategory?rs:Command=Render&Region=West  
```  
  
## <a name="creating-a-drillthrough-action"></a><span data-ttu-id="b71fc-189">建立鑽研動作</span><span class="sxs-lookup"><span data-stu-id="b71fc-189">Creating a Drillthrough Action</span></span>  
 <span data-ttu-id="b71fc-190">鑽研動作是由資料列集動作定義的，會傳回到用戶端應用程式做為鑽研陳述式。</span><span class="sxs-lookup"><span data-stu-id="b71fc-190">A drillthrough action is defined by a rowset action, which is returned to the client application as a drillthrough statement.</span></span> <span data-ttu-id="b71fc-191">動作目標是量值群組的成員。</span><span class="sxs-lookup"><span data-stu-id="b71fc-191">The action target is a member of a measure group.</span></span> <span data-ttu-id="b71fc-192">若要建立新的鑽研動作，請在 [Cube]\*\*\*\* 功能表上，按一下 [新增鑽研動作]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b71fc-192">To create a new drillthrough action, on the **Cube** menu, click **New Drillthrough Action**.</span></span> <span data-ttu-id="b71fc-193">下列選項是鑽研動作特有的選項：</span><span class="sxs-lookup"><span data-stu-id="b71fc-193">The following options are specific to a drillthrough action:</span></span>  
  
 <span data-ttu-id="b71fc-194">**鑽研資料行**</span><span class="sxs-lookup"><span data-stu-id="b71fc-194">**Drillthrough Columns**</span></span>  
 <span data-ttu-id="b71fc-195">選取一或多個維度，並針對每一個維度，選取由動作傳回到用戶端應用程式的鑽研資料行。</span><span class="sxs-lookup"><span data-stu-id="b71fc-195">Select one or more dimensions and, for each dimension, the drillthrough columns returned to the client application by the action.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b71fc-196">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b71fc-196">See Also</span></span>  
 [<span data-ttu-id="b71fc-197">多維度模型中的 Cube</span><span class="sxs-lookup"><span data-stu-id="b71fc-197">Cubes in Multidimensional Models</span></span>](cubes-in-multidimensional-models.md)  
  
  
