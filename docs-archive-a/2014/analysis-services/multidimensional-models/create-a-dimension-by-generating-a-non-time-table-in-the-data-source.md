---
title: 藉由在資料來源中產生非時間資料表來建立維度 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data sources [Analysis Services], dimensions without data source
- dimensions [Analysis Services], standard
- dimensions [Analysis Services], creating without data source
- standard dimensions [Analysis Services]
ms.assetid: a37f7a46-7451-4582-ba19-2595196d97bc
author: minewiskan
ms.author: owend
ms.openlocfilehash: 49dbfb0c1fc15c1cbf703514e0fc693dfabf1e9d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705617"
---
# <a name="create-a-dimension-by-generating-a-non-time-table-in-the-data-source"></a><span data-ttu-id="9e7d4-102">在資料來源中產生非時間資料表來建立維度</span><span class="sxs-lookup"><span data-stu-id="9e7d4-102">Create a Dimension by Generating a Non-Time Table in the Data Source</span></span>
  <span data-ttu-id="9e7d4-103">在中 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ，您可以使用中的 [維度] Wizard [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 來建立維度，而不需使用現有的資料來源。</span><span class="sxs-lookup"><span data-stu-id="9e7d4-103">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], you can use the Dimension Wizard in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] to create a dimension without using an existing data source.</span></span> <span data-ttu-id="9e7d4-104">方法是，選取精靈之 [選取建立方法]\*\*\*\* 頁面的 [在資料來源中產生非時間資料表]\*\*\*\* 選項。</span><span class="sxs-lookup"><span data-stu-id="9e7d4-104">You do this by selecting the **Generate a non-time table in the data source** option of the **Select Creation Method** page of the wizard.</span></span> <span data-ttu-id="9e7d4-105">若要在基礎資料來源中建立新的維度資料表，您必須擁有在基礎資料來源中建立物件的權限。</span><span class="sxs-lookup"><span data-stu-id="9e7d4-105">To create a new dimension table in the underlying data source, you must have permission to create objects in the underlying data source.</span></span> <span data-ttu-id="9e7d4-106">在沒有預先定義之資料來源檢視的情況下定義維度時，可以從頭開始定義維度或使用維度範本。</span><span class="sxs-lookup"><span data-stu-id="9e7d4-106">When defining a dimension without a predefined data source view, you can either define the dimension from scratch or use a dimension template.</span></span>  
  
 <span data-ttu-id="9e7d4-107">「維度精靈」提供了一些維度範本範例，讓您可以建立常見的維度類型。</span><span class="sxs-lookup"><span data-stu-id="9e7d4-107">The Dimension Wizard provides sample dimension templates from which you can build a common dimension type.</span></span> <span data-ttu-id="9e7d4-108">您可以從以下維度類型中選擇：</span><span class="sxs-lookup"><span data-stu-id="9e7d4-108">You can select from the following types of dimensions:</span></span>  
  
-   <span data-ttu-id="9e7d4-109">帳戶</span><span class="sxs-lookup"><span data-stu-id="9e7d4-109">Account</span></span>  
  
-   <span data-ttu-id="9e7d4-110">客戶</span><span class="sxs-lookup"><span data-stu-id="9e7d4-110">Customer</span></span>  
  
-   <span data-ttu-id="9e7d4-111">Date</span><span class="sxs-lookup"><span data-stu-id="9e7d4-111">Date</span></span>  
  
-   <span data-ttu-id="9e7d4-112">department</span><span class="sxs-lookup"><span data-stu-id="9e7d4-112">Department</span></span>  
  
-   <span data-ttu-id="9e7d4-113">目的地貨幣</span><span class="sxs-lookup"><span data-stu-id="9e7d4-113">Destination Currency</span></span>  
  
-   <span data-ttu-id="9e7d4-114">員工</span><span class="sxs-lookup"><span data-stu-id="9e7d4-114">Employee</span></span>  
  
-   <span data-ttu-id="9e7d4-115">[地理位置]</span><span class="sxs-lookup"><span data-stu-id="9e7d4-115">Geography</span></span>  
  
-   <span data-ttu-id="9e7d4-116">網際網路銷售訂單的詳細資料</span><span class="sxs-lookup"><span data-stu-id="9e7d4-116">Internet Sales Order Details</span></span>  
  
-   <span data-ttu-id="9e7d4-117">組織</span><span class="sxs-lookup"><span data-stu-id="9e7d4-117">Organization</span></span>  
  
-   <span data-ttu-id="9e7d4-118">產品</span><span class="sxs-lookup"><span data-stu-id="9e7d4-118">Product</span></span>  
  
-   <span data-ttu-id="9e7d4-119">促銷</span><span class="sxs-lookup"><span data-stu-id="9e7d4-119">Promotion</span></span>  
  
-   <span data-ttu-id="9e7d4-120">轉售商銷售訂單的詳細資料</span><span class="sxs-lookup"><span data-stu-id="9e7d4-120">Reseller Sales Order Details</span></span>  
  
-   <span data-ttu-id="9e7d4-121">Reseller</span><span class="sxs-lookup"><span data-stu-id="9e7d4-121">Reseller</span></span>  
  
-   <span data-ttu-id="9e7d4-122">銷售通路</span><span class="sxs-lookup"><span data-stu-id="9e7d4-122">Sales Channel</span></span>  
  
-   <span data-ttu-id="9e7d4-123">銷售原因</span><span class="sxs-lookup"><span data-stu-id="9e7d4-123">Sales Reason</span></span>  
  
-   <span data-ttu-id="9e7d4-124">銷售摘要訂單的詳細資料</span><span class="sxs-lookup"><span data-stu-id="9e7d4-124">Sales Summary Order Details</span></span>  
  
-   <span data-ttu-id="9e7d4-125">銷售地區</span><span class="sxs-lookup"><span data-stu-id="9e7d4-125">Sales Territory</span></span>  
  
-   <span data-ttu-id="9e7d4-126">案例</span><span class="sxs-lookup"><span data-stu-id="9e7d4-126">Scenario</span></span>  
  
-   <span data-ttu-id="9e7d4-127">來源貨幣</span><span class="sxs-lookup"><span data-stu-id="9e7d4-127">Source Currency</span></span>  
  
 <span data-ttu-id="9e7d4-128">每個標準範本都支援可供選擇納入維度的屬性。</span><span class="sxs-lookup"><span data-stu-id="9e7d4-128">Each of the standard templates supports attributes that you can choose to include in the dimension.</span></span> <span data-ttu-id="9e7d4-129">您也可以針對資料常用到的維度，加入自己的範本檔案。</span><span class="sxs-lookup"><span data-stu-id="9e7d4-129">You can also add your own template files for dimensions that are commonly used with your data.</span></span> <span data-ttu-id="9e7d4-130">維度範本位於以下資料夾：</span><span class="sxs-lookup"><span data-stu-id="9e7d4-130">The dimension templates are located in the following folder:</span></span>  
  
 `C:\Program Files\Microsoft SQL Server\100\Tools\Templates\olap\1033\Dimension Templates`  
  
 <span data-ttu-id="9e7d4-131">您可以在完成「維度精靈」之後，使用 [維度設計師] 在維度中加入、移除和設定屬性與階層。</span><span class="sxs-lookup"><span data-stu-id="9e7d4-131">You can use Dimension Designer after you complete the Dimension Wizard to add, remove, and configure attributes and hierarchies in the dimension.</span></span>  
  
 <span data-ttu-id="9e7d4-132">在不使用資料來源的情況下建立非時間維度時，「維度精靈」會引導您透過下列步驟，指定維度類型並識別索引鍵屬性和緩時變維度。</span><span class="sxs-lookup"><span data-stu-id="9e7d4-132">When you are creating a non-time dimension without using a data source, the Dimension Wizard guides you through the steps of specifying the dimension type, and identifying the key attribute and slowly changing dimensions.</span></span>  
  
## <a name="specify-dimension-type"></a><span data-ttu-id="9e7d4-133">指定維度類型</span><span class="sxs-lookup"><span data-stu-id="9e7d4-133">Specify Dimension Type</span></span>  
 <span data-ttu-id="9e7d4-134">在 [維度精靈] 的 [指定維度類型]\*\*\*\* 頁面上，您可以指定維度類型。</span><span class="sxs-lookup"><span data-stu-id="9e7d4-134">On the **Specify Dimension Type** page of the Dimension Wizard, you can specify the dimension type.</span></span> <span data-ttu-id="9e7d4-135">如果您要以範本為基礎建立維度，就會為您定義維度類型。</span><span class="sxs-lookup"><span data-stu-id="9e7d4-135">If you are building the dimension based on a template, the dimension type is defined for you.</span></span> <span data-ttu-id="9e7d4-136">您也可以在此頁面上選取指定之維度類型的標準屬性 (如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="9e7d4-136">On this page, you can also select standard attributes for the specified dimension type if any are available.</span></span>  
  
 <span data-ttu-id="9e7d4-137">如果您選取的範本對應到維度類型，此頁面會使用該維度類型的選項擴展。</span><span class="sxs-lookup"><span data-stu-id="9e7d4-137">If you selected a template that corresponds to a dimension type, this page is populated with the options for that dimension type.</span></span> <span data-ttu-id="9e7d4-138">如果您並未選取範本，或沒有對應的維度類型，預設的維度類型為 [一般]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="9e7d4-138">If you did not select a template, or if there is no corresponding dimension type, the default dimension type is **Regular**.</span></span> <span data-ttu-id="9e7d4-139">如果尚未選取維度類型，請為您建立的維度選取最適當的類型。</span><span class="sxs-lookup"><span data-stu-id="9e7d4-139">If a dimension type is not already selected, select the most appropriate type for the dimension that you are creating.</span></span> <span data-ttu-id="9e7d4-140">如果沒有為 [維度類型]\*\*\*\* 列出的適當類型，請使用 [一般]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="9e7d4-140">If no appropriate type is listed for **Dimension type**, use **Regular**.</span></span>  
  
 <span data-ttu-id="9e7d4-141">選取維度類型時，精靈會在 [維度屬性]\*\*\*\* 下，列出適用於此維度的屬性類型。</span><span class="sxs-lookup"><span data-stu-id="9e7d4-141">When you select a dimension type, the wizard lists the attribute types that apply to this dimension under **Dimension attributes**.</span></span> <span data-ttu-id="9e7d4-142">若要選取屬性類型，請選取該屬性類型旁的 [包含]\*\*\*\* 核取方塊，再於 [維度屬性]\*\*\*\* 下輸入屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="9e7d4-142">To select an attribute type, select the **Include** check box next to the attribute type, and type the name for the attribute under **Dimension Attribute**.</span></span> <span data-ttu-id="9e7d4-143">預設名稱與 [屬性類型]\*\*\*\* 相同。</span><span class="sxs-lookup"><span data-stu-id="9e7d4-143">The default name is the same as **Attribute Type**.</span></span>  
  
## <a name="identify-key-attribute-and-changing-dimensions"></a><span data-ttu-id="9e7d4-144">識別索引鍵屬性與變更維度</span><span class="sxs-lookup"><span data-stu-id="9e7d4-144">Identify Key Attribute and Changing Dimensions</span></span>  
 <span data-ttu-id="9e7d4-145">在 [指定維度索引鍵和類型]\*\*\*\* 頁面上，選取要作為維度之索引鍵屬性的屬性。</span><span class="sxs-lookup"><span data-stu-id="9e7d4-145">On the **Specify Dimension Key and Type** page, select the attribute that you want to be the key attribute for the dimension.</span></span> <span data-ttu-id="9e7d4-146">索引鍵屬性通常會對應到主維度資料表的主索引鍵資料行，並索引維度的分葉成員。</span><span class="sxs-lookup"><span data-stu-id="9e7d4-146">The key attribute typically corresponds to the primary key column in the main dimension table, and it typically indexes the leaf members of the dimension.</span></span>  
  
 <span data-ttu-id="9e7d4-147">如果您選取範本，而且在範本中有定義索引鍵屬性，則該屬性為預設索引鍵屬性。</span><span class="sxs-lookup"><span data-stu-id="9e7d4-147">If you selected a template, and a key attribute is defined in the template, that attribute is the default key attribute.</span></span> <span data-ttu-id="9e7d4-148">如果您選取範本，但是在範本中沒有定義索引鍵屬性，則預設值為清單中的第一個屬性。</span><span class="sxs-lookup"><span data-stu-id="9e7d4-148">If you selected a template but no key attribute is defined in the template, the default is the first attribute in the list.</span></span> <span data-ttu-id="9e7d4-149">此清單包含您在 [指定維度類型]\*\*\*\* 頁面上選取的所有屬性。</span><span class="sxs-lookup"><span data-stu-id="9e7d4-149">The list contains all the attributes that you selected on the **Specify Dimension Type** page.</span></span> <span data-ttu-id="9e7d4-150">您可以選取您在 [指定維度類型]\*\*\*\* 頁面上選取的任何屬性，作為索引鍵屬性。</span><span class="sxs-lookup"><span data-stu-id="9e7d4-150">You can select any one of the attributes that you selected on the **Specify Dimension Type** page to be the key attribute.</span></span> <span data-ttu-id="9e7d4-151">如果您並未選取任何屬性，精靈會自動建立索引鍵屬性，並串連維度名稱與「識別碼」來為其命名。</span><span class="sxs-lookup"><span data-stu-id="9e7d4-151">If you did not select any attributes, the wizard automatically creates a key attribute and names it by concatenating the dimension name and "ID".</span></span>  
  
 <span data-ttu-id="9e7d4-152">最後，指定此維度是否為變更維度。</span><span class="sxs-lookup"><span data-stu-id="9e7d4-152">Finally, specify whether this dimension is a changing dimension.</span></span> <span data-ttu-id="9e7d4-153">變更維度中的成員會隨著時間而移至階層內的不同位置。</span><span class="sxs-lookup"><span data-stu-id="9e7d4-153">Members in a changing dimension move over time to different locations in the hierarchy.</span></span> <span data-ttu-id="9e7d4-154">精靈會產生其他資料行並建立對應到這些資料行的屬性。</span><span class="sxs-lookup"><span data-stu-id="9e7d4-154">The wizard generates additional columns and creates attributes that correspond to those columns.</span></span> <span data-ttu-id="9e7d4-155">這些資料行將會讓使用者以變更中之因數的方式，查詢維度。</span><span class="sxs-lookup"><span data-stu-id="9e7d4-155">These columns will let users query the dimension in such a way as to factor in the change.</span></span> <span data-ttu-id="9e7d4-156">之後使用「結構描述產生精靈」建立的任何封裝，都會根據維度的緩時變維度特性來管理 Surrogate 索引鍵。</span><span class="sxs-lookup"><span data-stu-id="9e7d4-156">Any packages that you subsequently create with the Schema Generation Wizard manage surrogate keys based on slowly changing dimension characteristics of the dimension.</span></span>  
  
 <span data-ttu-id="9e7d4-157">當您選取 [這是變更維度]\*\*\*\* 核取方塊時，[維度精靈] 會定義下表中指出的屬性：</span><span class="sxs-lookup"><span data-stu-id="9e7d4-157">When you select the **This is a changing dimension** check box, the Dimension Wizard defines the attributes indicated in the following table:</span></span>  
  
|<span data-ttu-id="9e7d4-158">屬性</span><span class="sxs-lookup"><span data-stu-id="9e7d4-158">Attribute</span></span>|<span data-ttu-id="9e7d4-159">類型</span><span class="sxs-lookup"><span data-stu-id="9e7d4-159">Type</span></span>|  
|---------------|----------|  
|<span data-ttu-id="9e7d4-160">SCD OriginalID</span><span class="sxs-lookup"><span data-stu-id="9e7d4-160">SCD OriginalID</span></span>|<span data-ttu-id="9e7d4-161">SCDOriginalID</span><span class="sxs-lookup"><span data-stu-id="9e7d4-161">SCDOriginalID</span></span>|  
|<span data-ttu-id="9e7d4-162">SCD 結束日期</span><span class="sxs-lookup"><span data-stu-id="9e7d4-162">SCD End Date</span></span>|<span data-ttu-id="9e7d4-163">SCDEndDate</span><span class="sxs-lookup"><span data-stu-id="9e7d4-163">SCDEndDate</span></span>|  
|<span data-ttu-id="9e7d4-164">SCD 開始日期</span><span class="sxs-lookup"><span data-stu-id="9e7d4-164">SCD Start Date</span></span>|<span data-ttu-id="9e7d4-165">SCDStartDate</span><span class="sxs-lookup"><span data-stu-id="9e7d4-165">SCDStartDate</span></span>|  
|<span data-ttu-id="9e7d4-166">SCD 狀態</span><span class="sxs-lookup"><span data-stu-id="9e7d4-166">SCD Status</span></span>|<span data-ttu-id="9e7d4-167">SCDStatus</span><span class="sxs-lookup"><span data-stu-id="9e7d4-167">SCDStatus</span></span>|  
  
 <span data-ttu-id="9e7d4-168">如果您使用的範本中有定義這些緩時變維度屬性，預設會選取 [這是變更維度]\*\*\*\* 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="9e7d4-168">By default, the **This is a changing dimension** check box is selected if you use a template that has these slowly changing dimension attributes defined.</span></span> <span data-ttu-id="9e7d4-169">如果您清除核取方塊，則會從維度中移除緩時變維度屬性。</span><span class="sxs-lookup"><span data-stu-id="9e7d4-169">If you clear the check box, the slowly changing dimension attributes are removed from the dimension.</span></span>  
  
 <span data-ttu-id="9e7d4-170">您可以使用維度設計師來設定緩時變維度的屬性。</span><span class="sxs-lookup"><span data-stu-id="9e7d4-170">You can use Dimension Designer to configure properties for a slowly changing dimension.</span></span>  
  
## <a name="completing-the-dimension-wizard"></a><span data-ttu-id="9e7d4-171">完成維度精靈</span><span class="sxs-lookup"><span data-stu-id="9e7d4-171">Completing the Dimension Wizard</span></span>  
 <span data-ttu-id="9e7d4-172">在 [正在完成精靈]\*\*\*\* 頁面上，輸入新維度的名稱，然後檢視維度結構。</span><span class="sxs-lookup"><span data-stu-id="9e7d4-172">On the **Completing the Wizard** page, type a name for the new dimension and view the dimension structure.</span></span> <span data-ttu-id="9e7d4-173">選取 [立即產生結構描述]\*\*\*\* 核取方塊，在您按一下 [完成]\*\*\*\* 後即可啟動 [結構描述產生精靈]。</span><span class="sxs-lookup"><span data-stu-id="9e7d4-173">Select the **Generate schema now** check box to start the Schema Generation Wizard after you click **Finish**.</span></span> <span data-ttu-id="9e7d4-174">在大多數情況下，如果您計畫建立其他物件，則不應選取此核取方塊。</span><span class="sxs-lookup"><span data-stu-id="9e7d4-174">In most cases, you should not select this check box if you plan to create additional objects.</span></span> <span data-ttu-id="9e7d4-175">如果您並未選取此核取方塊，也可在稍後使用維度設計師來產生結構描述。</span><span class="sxs-lookup"><span data-stu-id="9e7d4-175">If you do not select this check box, you can use Dimension Designer to generate the schema later.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e7d4-176">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9e7d4-176">See Also</span></span>  
 <span data-ttu-id="9e7d4-177">[藉由產生時間資料表來建立時間維度](create-a-time-dimension-by-generating-a-time-table.md) </span><span class="sxs-lookup"><span data-stu-id="9e7d4-177">[Create a Time Dimension by Generating a Time Table](create-a-time-dimension-by-generating-a-time-table.md) </span></span>  
 [<span data-ttu-id="9e7d4-178">透過產生時間資料表來建立時間維度</span><span class="sxs-lookup"><span data-stu-id="9e7d4-178">Create a Time Dimension by Generating a Time Table</span></span>](create-a-time-dimension-by-generating-a-time-table.md)  
  
  
