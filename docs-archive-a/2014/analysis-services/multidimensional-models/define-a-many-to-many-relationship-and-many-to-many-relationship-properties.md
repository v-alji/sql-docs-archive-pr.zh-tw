---
title: 定義多對多關聯性及多對多關聯性屬性 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- many-to-many relationships [Analysis Services]
ms.assetid: edb5f61a-a581-467a-a367-134b7f9b849f
author: minewiskan
ms.author: owend
ms.openlocfilehash: 1cd5d46ce07ff8eb6a3893c0dac261797c6ef19e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599702"
---
# <a name="define-a-many-to-many-relationship-and-many-to-many-relationship-properties"></a><span data-ttu-id="63196-102">定義多對多關聯性及多對多關聯性屬性</span><span class="sxs-lookup"><span data-stu-id="63196-102">Define a Many-to-Many Relationship and Many-to-Many Relationship Properties</span></span>
  <span data-ttu-id="63196-103">本主題說明 Analysis Services 中的多對多維度，包括何時使用這些維度以及如何建立這些維度。</span><span class="sxs-lookup"><span data-stu-id="63196-103">This topic explains many-to-many dimensions in Analysis Services, including when to use them and how to create them.</span></span>  
  
## <a name="introduction"></a><span data-ttu-id="63196-104">簡介</span><span class="sxs-lookup"><span data-stu-id="63196-104">Introduction</span></span>  
 <span data-ttu-id="63196-105">Analysis Services 支援多對多維度，其允許的分析方式比典型星形結構描述中所描述的分析方式更為複雜許多。</span><span class="sxs-lookup"><span data-stu-id="63196-105">Analysis Services supports many-to-many dimensions, allowing for more complex analytics than what can be described in a classic star schema.</span></span> <span data-ttu-id="63196-106">在典型星形結構描述中，所有維度都有包含事實資料表的一對多關聯性。</span><span class="sxs-lookup"><span data-stu-id="63196-106">In a classic star schema, all dimensions have a one-to-many relationship with a fact table.</span></span> <span data-ttu-id="63196-107">每個事實只會聯結到一個維度成員，單一維度成員會與多個事實產生關聯。</span><span class="sxs-lookup"><span data-stu-id="63196-107">Each fact joins to one dimension member; a single dimension member is associated with many facts.</span></span>  
  
 <span data-ttu-id="63196-108">多對多關聯性會移除這個模型化限制，其方式是啟用要與相同維度之多個成員產生關聯的事實 (例如帳戶餘額，聯合帳戶的餘額可歸因於聯合帳戶的兩個或多個擁有者)。</span><span class="sxs-lookup"><span data-stu-id="63196-108">Many-to-many removes this modeling restriction by enabling a fact (such as an account balance) to be associated with multiple members of the same dimension (the balance of a joint account can be attributed to two or more owners of a joint account).</span></span>  
  
 <span data-ttu-id="63196-109">就概念上而言，Analysis Services 中的多對多維度關聯性等於關聯式模型中的多對多關聯性，以便支援相同種類的案例。</span><span class="sxs-lookup"><span data-stu-id="63196-109">Conceptually, a many-to-many dimensional relationship in Analysis Services is equivalent to many-to-many relationships in a relational model, supporting the same kinds of scenarios.</span></span> <span data-ttu-id="63196-110">常見的多對多範例包括：</span><span class="sxs-lookup"><span data-stu-id="63196-110">Common examples of many-to-many include:</span></span>  
  
-   <span data-ttu-id="63196-111">學生註冊許多課程，每個課程都有許多學生。</span><span class="sxs-lookup"><span data-stu-id="63196-111">Students are enrolled in many courses; each course has many students.</span></span>  
  
-   <span data-ttu-id="63196-112">醫生有許多病人，病人有許多醫生。</span><span class="sxs-lookup"><span data-stu-id="63196-112">Doctors have many patients; patients have many doctors.</span></span>  
  
-   <span data-ttu-id="63196-113">客戶擁有許多銀行帳戶，銀行帳戶可能屬於一個以上的客戶。</span><span class="sxs-lookup"><span data-stu-id="63196-113">Customers have many bank accounts; bank accounts might belong to more than one customer.</span></span>  
  
-   <span data-ttu-id="63196-114">在 Adventure Works 中，許多客戶可能基於多個理由而訂購產品，而且銷售原因可以與多筆訂單產生關聯。</span><span class="sxs-lookup"><span data-stu-id="63196-114">In Adventure Works, many customers have many reasons for ordering a product, and a sales reason can be associated with many orders.</span></span>  
  
 <span data-ttu-id="63196-115">就分析而言，多對多關聯性所解決的問題是相對於維度關聯性的計數或總和的精確表示 (通常在執行特定維度成員的計算時會除去重複計數)。</span><span class="sxs-lookup"><span data-stu-id="63196-115">Analytically, the problem that a many-to-many relationship solves is accurate representation of a count or sum relative to the dimensional relationship (usually by eliminating double-counts when performing calculations for a specific dimension member).</span></span> <span data-ttu-id="63196-116">為了釐清這個重點，我們提供了範例。</span><span class="sxs-lookup"><span data-stu-id="63196-116">An example is necessary to clarify this point.</span></span> <span data-ttu-id="63196-117">假設有一個產品或服務屬於一個以上的類別。</span><span class="sxs-lookup"><span data-stu-id="63196-117">Consider a product or service that belongs to more than one category.</span></span> <span data-ttu-id="63196-118">如果您依據類別計算服務數目，您會想要將屬於這兩個類別的服務併入每個類別中。</span><span class="sxs-lookup"><span data-stu-id="63196-118">If you were counting the number of services by category, you would want a service belonging to both categories to be included in each one.</span></span> <span data-ttu-id="63196-119">同時，您不會想要誇大您所提供的服務數目。</span><span class="sxs-lookup"><span data-stu-id="63196-119">At the same time, you would not want to overstate the number of services that you provide.</span></span> <span data-ttu-id="63196-120">藉由指定多對多維度關聯性，當您依類別或服務查詢時，就更有可能取回正確的結果。</span><span class="sxs-lookup"><span data-stu-id="63196-120">By specifying the many-to-many dimensional relationship, you are more likely to get the correct results back when querying by category or by service.</span></span> <span data-ttu-id="63196-121">但是，一定要經由測試才能確定是這個狀況。</span><span class="sxs-lookup"><span data-stu-id="63196-121">However, thorough testing is always necessary to ensure that this is the case.</span></span>  
  
 <span data-ttu-id="63196-122">就結構而言，建立多對多維度關聯性類似於您可能在關聯式資料模型中建立多對多關聯性的方式。</span><span class="sxs-lookup"><span data-stu-id="63196-122">Structurally, creating a many-to-many dimensional relationship is similar to how you might create many-to-many in a relational data model.</span></span> <span data-ttu-id="63196-123">而當關聯式模型使用「聯合資料表」\*\* 來儲存資料列關聯時，多維度模型會使用「中繼量值群組」\*\*。</span><span class="sxs-lookup"><span data-stu-id="63196-123">Whereas a relational model uses a *junction table* to store row associations, a multidimensional model uses an *intermediate measure group*.</span></span> <span data-ttu-id="63196-124">中繼量值群組這個詞彙是用來指稱會對應不同維度之成員的資料表。</span><span class="sxs-lookup"><span data-stu-id="63196-124">Intermediate measure group is the term we use to refer to a table that maps members from different dimensions.</span></span>  
  
 <span data-ttu-id="63196-125">就視覺上而言，Cube 圖表中不會指示多對多維度關聯性。</span><span class="sxs-lookup"><span data-stu-id="63196-125">Visually, a many-to-many dimensional relationship is not indicated in a cube diagram.</span></span> <span data-ttu-id="63196-126">請改用 [維度使用方式] 索引標籤來快速識別模型中的任何多對多關聯性。</span><span class="sxs-lookup"><span data-stu-id="63196-126">Instead, use the Dimension Usage tab to quickly identify any many-to-many relationships in a model.</span></span> <span data-ttu-id="63196-127">以下圖示會指示多對多關聯性。</span><span class="sxs-lookup"><span data-stu-id="63196-127">A many-to-many relationship is indicated by the following icon.</span></span>  
  
 <span data-ttu-id="63196-128">![維度使用方式中的多對多圖示](../media/ssas-m2m-icondimusage.png "維度使用方式中的多對多圖示")</span><span class="sxs-lookup"><span data-stu-id="63196-128">![Many-to-many icon in dimension usage](../media/ssas-m2m-icondimusage.png "Many-to-many icon in dimension usage")</span></span>  
  
 <span data-ttu-id="63196-129">請按一下此按鈕來開啟 [定義關聯性] 對話方塊，以確認關聯性類型為多對多並且檢視關聯性中會使用哪一個中繼量值群組。</span><span class="sxs-lookup"><span data-stu-id="63196-129">Click the button to open the Define Relationship dialog box to verify the relationship type is many-to-many, and to view which intermediate measure group is used in the relationship.</span></span>  
  
 <span data-ttu-id="63196-130">![維度使用方式中的 [定義關聯性] 按鈕](../media/ssas-m2m-btndimusage.png "維度使用方式中的 [定義關聯性] 按鈕")</span><span class="sxs-lookup"><span data-stu-id="63196-130">![Define Relationship button  in dimension usage](../media/ssas-m2m-btndimusage.png "Define Relationship button  in dimension usage")</span></span>  
  
 <span data-ttu-id="63196-131">在後續的章節中，您將會學習如何設定多對多維度及測試模型的行為。</span><span class="sxs-lookup"><span data-stu-id="63196-131">In subsequent sections, you will learn how to set up a many-to-many dimension and test model behaviors.</span></span> <span data-ttu-id="63196-132">如果您想要先檢閱其他資訊或是先嘗試教學課程，請參閱本文結尾的 **深入了解** 。</span><span class="sxs-lookup"><span data-stu-id="63196-132">If you would rather review additional information or try tutorials first, see **Learn More** at the end of this article.</span></span>  
  
## <a name="create-a-many-to-many-dimension"></a><span data-ttu-id="63196-133">建立多對多維度</span><span class="sxs-lookup"><span data-stu-id="63196-133">Create a many-to-many dimension</span></span>  
 <span data-ttu-id="63196-134">簡單的多對多關聯性包含擁有多對多基數的兩個維度、用來排序成員關聯的中繼量值群組，以及包含可測量資料的事實量值群組，例如總銷售總和或是銀行帳戶的餘額。</span><span class="sxs-lookup"><span data-stu-id="63196-134">A simple many-to-many relationship includes two dimensions having a many-to-many cardinality, an intermediate measure group for storing member associations, and a fact measure group containing measurable data, such as sum of total sales or the balance of a bank account.</span></span>  
  
 <span data-ttu-id="63196-135">多對多關聯性中的維度可能擁有 DSV 中的對應資料表，而模型中的每個維度都會根據資料來源中的現有資料表。</span><span class="sxs-lookup"><span data-stu-id="63196-135">Dimensions in a many-to-many relationship might have correspondent tables in the DSV, where each dimension in the model is based on an existing table in a data source.</span></span> <span data-ttu-id="63196-136">相反地，您的模型中的維度可能會衍生自 DSV 中較少或不同的實體資料表。</span><span class="sxs-lookup"><span data-stu-id="63196-136">Conversely, the dimensions in your model might derive from fewer or different physical tables in the DSV.</span></span> <span data-ttu-id="63196-137">Adventure Works 範例 Cube 會使用「銷售原因」和「銷售訂單」當做重點案例來示範多對多關聯性，其中使用以僅限模型資料結構形式存在的維度，而在 DSV 中沒有實體對應項目。</span><span class="sxs-lookup"><span data-stu-id="63196-137">Using Sales Reasons and Sales Orders as a case in point, the Adventure Works sample cube demonstrates a many-to-many relationship using dimensions that exist as model-only data structures, without physical counterparts in the DSV.</span></span> <span data-ttu-id="63196-138">「銷售訂單」維度是根據基礎資料來源中的事實資料表，而不是維度資料表。</span><span class="sxs-lookup"><span data-stu-id="63196-138">The Sales Order dimension is based on a fact table, rather than a dimension table, in the underlying data source.</span></span>  
  
 <span data-ttu-id="63196-139">下一個程序假設您已經知道哪些實體參與多對多關聯性。</span><span class="sxs-lookup"><span data-stu-id="63196-139">The next procedure assumes that you already know which entities participate in the many-to-many relationship.</span></span> <span data-ttu-id="63196-140">如需進一步研究，請參閱 **深入了解** 。</span><span class="sxs-lookup"><span data-stu-id="63196-140">See **Learn More** for further study.</span></span>  
  
 <span data-ttu-id="63196-141">為了說明用來建立多對多關聯性的步驟，這個程序會在 Adventure Works 範例 Cube 中重新建立其中一個多對多關聯性。</span><span class="sxs-lookup"><span data-stu-id="63196-141">To illustrate the steps used to create a many-to-many relationship, this procedure re-creates one of the many-to-many relationships in the Adventure Works sample cube.</span></span> <span data-ttu-id="63196-142">如果您已經將來源資料 (也就是 Adventure Works 範例資料倉儲) 安裝在關聯式資料庫引擎執行個體上，您可以依照以下步驟進行。</span><span class="sxs-lookup"><span data-stu-id="63196-142">If you have the source data (that is, the Adventure Works sample data warehouse) installed on a relational database engine instance, you can follow these steps.</span></span>  
  
#### <a name="step-1-verify-dsv-relationships"></a><span data-ttu-id="63196-143">步驟 1：確認 DSV 關聯性</span><span class="sxs-lookup"><span data-stu-id="63196-143">Step 1: Verify DSV relationships</span></span>  
  
1.  <span data-ttu-id="63196-144">在 SQL Server Data Tools 的多維度專案中，建立 Adventure Works DW 2012 關聯式資料倉儲的資料來源 (裝載於 SQL Server Database Engine 執行個體上)。</span><span class="sxs-lookup"><span data-stu-id="63196-144">In SQL Server Data Tools, in a multidimensional project, create a data source to the Adventure Works DW 2012 relational data warehouse, hosted on a SQL Server Database Engine instance.</span></span>  
  
2.  <span data-ttu-id="63196-145">使用以下現有的資料表建立資料來源檢視：</span><span class="sxs-lookup"><span data-stu-id="63196-145">Create a Data Source View using the following existing tables:</span></span>  
  
    -   <span data-ttu-id="63196-146">FactInternetSales</span><span class="sxs-lookup"><span data-stu-id="63196-146">FactInternetSales</span></span>  
  
    -   <span data-ttu-id="63196-147">FactInternetSalesReason</span><span class="sxs-lookup"><span data-stu-id="63196-147">FactInternetSalesReason</span></span>  
  
    -   <span data-ttu-id="63196-148">DimSalesReason</span><span class="sxs-lookup"><span data-stu-id="63196-148">DimSalesReason</span></span>  
  
3.  <span data-ttu-id="63196-149">確認您打算在多對多關聯性中使用的所有資料表都在 DSV 中透過主索引鍵關聯性產生關聯。</span><span class="sxs-lookup"><span data-stu-id="63196-149">Verify that all of the tables you plan to use in the many-to-many relationships are related in the DSV through primary key relationships.</span></span> <span data-ttu-id="63196-150">這是在後續步驟中建立中繼量值群組之連結的必要條件。</span><span class="sxs-lookup"><span data-stu-id="63196-150">This is a requirement for establishing a link to the intermediate measure group in a subsequent step.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="63196-151">如果基礎資料來源未提供主索引鍵和外部索引鍵關聯性，您可以在 DSV 中手動建立關聯性。</span><span class="sxs-lookup"><span data-stu-id="63196-151">If the underlying data source does not provide primary and foreign key relationships, you can create the relationships manually in the DSV.</span></span> <span data-ttu-id="63196-152">如需詳細資訊，請參閱[在資料來源檢視中定義邏輯關聯性 &#40;Analysis Services&#41;](define-logical-relationships-in-a-data-source-view-analysis-services.md)。</span><span class="sxs-lookup"><span data-stu-id="63196-152">For more information, see [Define Logical Relationships in a Data Source View &#40;Analysis Services&#41;](define-logical-relationships-in-a-data-source-view-analysis-services.md).</span></span>  
  
     <span data-ttu-id="63196-153">以下範例會確認這個程序中所使用的資料表會利用主索引鍵來連結。</span><span class="sxs-lookup"><span data-stu-id="63196-153">The following example confirms that the tables used in this procedure are linked using primary keys.</span></span>  
  
     <span data-ttu-id="63196-154">![顯示相關資料表的 DSV](../media/ssas-m2m-dsvpkeys.PNG "顯示相關資料表的 DSV")</span><span class="sxs-lookup"><span data-stu-id="63196-154">![DSV showing related tables](../media/ssas-m2m-dsvpkeys.PNG "DSV showing related tables")</span></span>  
  
#### <a name="step-2-create-dimensions-and-measure-groups"></a><span data-ttu-id="63196-155">步驟 2：建立維度和量值群組</span><span class="sxs-lookup"><span data-stu-id="63196-155">Step 2: Create dimensions and measure groups</span></span>  
  
1.  <span data-ttu-id="63196-156">在 SQL Server Data Tools 的多維度專案中，以滑鼠右鍵按一下 [維度]\*\*\*\*，然後選取 [新增維度]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="63196-156">In SQL Server Data Tools, in a multidimensional project, right-click **Dimensions** and select **New Dimension**.</span></span>  
  
2.  <span data-ttu-id="63196-157">根據現有的資料表 **DimSalesReason**建立新的維度。</span><span class="sxs-lookup"><span data-stu-id="63196-157">Create a new dimension based on existing table, **DimSalesReason**.</span></span> <span data-ttu-id="63196-158">在指定來源時接受所有預設值。</span><span class="sxs-lookup"><span data-stu-id="63196-158">Accept all of the default values when specifying the source.</span></span>  
  
     <span data-ttu-id="63196-159">針對屬性選取全部的值。</span><span class="sxs-lookup"><span data-stu-id="63196-159">For attributes, select all.</span></span>  
  
     <span data-ttu-id="63196-160">![新維度中的屬性清單](../media/ssas-m2m-dimsalesreason.PNG "新維度中的屬性清單")</span><span class="sxs-lookup"><span data-stu-id="63196-160">![Attributes list in new dimension](../media/ssas-m2m-dimsalesreason.PNG "Attributes list in new dimension")</span></span>  
  
3.  <span data-ttu-id="63196-161">根據現有的資料表 [事實網際網路銷售] 建立第二個維度。</span><span class="sxs-lookup"><span data-stu-id="63196-161">Create a second dimension based on existing table, Fact Internet Sales.</span></span> <span data-ttu-id="63196-162">雖然這是事實資料表，但是它包含了銷售訂單資訊。</span><span class="sxs-lookup"><span data-stu-id="63196-162">Although this is a fact table, it contains Sales Order information.</span></span> <span data-ttu-id="63196-163">我們將會使用它來建立「銷售訂單」維度。</span><span class="sxs-lookup"><span data-stu-id="63196-163">We'll use it to build a Sales Order dimension.</span></span>  
  
4.  <span data-ttu-id="63196-164">在 [指定來源資訊] 中，您將會看到一則警告指出必須指定名稱資料行。</span><span class="sxs-lookup"><span data-stu-id="63196-164">In Specify Source Information, you will see a warning that indicates a Name column must be specified.</span></span> <span data-ttu-id="63196-165">選擇 **SalesOrderNumber** 作為名稱。</span><span class="sxs-lookup"><span data-stu-id="63196-165">Choose **SalesOrderNumber** as the Name.</span></span>  
  
     <span data-ttu-id="63196-166">![顯示名稱欄的銷售訂單維度](../media/ssas-m2m-dimsalesordersource.PNG "顯示名稱欄的銷售訂單維度")</span><span class="sxs-lookup"><span data-stu-id="63196-166">![Sales Order dimension showing the name column](../media/ssas-m2m-dimsalesordersource.PNG "Sales Order dimension showing the name column")</span></span>  
  
5.  <span data-ttu-id="63196-167">在精靈的下一頁選擇屬性。</span><span class="sxs-lookup"><span data-stu-id="63196-167">On the next page of the wizard, choose the attributes.</span></span> <span data-ttu-id="63196-168">在此範例中，您可以只選取 **SalesOrderNumber**。</span><span class="sxs-lookup"><span data-stu-id="63196-168">In this example, you can select just **SalesOrderNumber**.</span></span>  
  
     <span data-ttu-id="63196-169">![顯示屬性清單的銷售訂單維度](../media/ssas-m2m-dimsalesorderattrib.PNG "顯示屬性清單的銷售訂單維度")</span><span class="sxs-lookup"><span data-stu-id="63196-169">![Sales order dimension showing attribute list](../media/ssas-m2m-dimsalesorderattrib.PNG "Sales order dimension showing attribute list")</span></span>  
  
6.  <span data-ttu-id="63196-170">將維度重新命名為 **維度銷售訂單**，好讓您擁有一致的維度命名慣例。</span><span class="sxs-lookup"><span data-stu-id="63196-170">Rename the dimension to **Dim Sales Orders**, so that you have a consistent naming convention for the dimensions.</span></span>  
  
     <span data-ttu-id="63196-171">![顯示維度重新命名的精靈頁面](../media/ssas-m2m-dimsalesorders.PNG "顯示維度重新命名的精靈頁面")</span><span class="sxs-lookup"><span data-stu-id="63196-171">![Wizard page showing dimension rename](../media/ssas-m2m-dimsalesorders.PNG "Wizard page showing dimension rename")</span></span>  
  
7.  <span data-ttu-id="63196-172">以滑鼠右鍵按一下 [Cube]\*\*\*\*，並選取 [新增 Cube]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="63196-172">Right-click **Cubes** and select **New Cube**.</span></span>  
  
8.  <span data-ttu-id="63196-173">在量值群組資料表中，選擇 **FactInternetSales** 和 **FactInternetSalesReason**。</span><span class="sxs-lookup"><span data-stu-id="63196-173">In measure group tables, choose **FactInternetSales** and **FactInternetSalesReason**.</span></span>  
  
     <span data-ttu-id="63196-174">您選擇 **FactInternetSales** ，因為它包含您想要在 Cube 中使用的量值。</span><span class="sxs-lookup"><span data-stu-id="63196-174">You are choosing **FactInternetSales** because it contains the measures you want to use in the cube.</span></span> <span data-ttu-id="63196-175">您選擇 **FactInternetSalesReason** ，因為它是中繼量值群組，提供將銷售訂單與銷售原因產生關聯的成員關聯資料。</span><span class="sxs-lookup"><span data-stu-id="63196-175">You are choosing **FactInternetSalesReason** because it is the intermediate measure group, providing member association data that relates sales orders to sales reasons.</span></span>  
  
9. <span data-ttu-id="63196-176">為每一個事實資料表選擇量值。</span><span class="sxs-lookup"><span data-stu-id="63196-176">Choose measures for each fact table.</span></span>  
  
     <span data-ttu-id="63196-177">若要簡化您的模型，請清除所有量值，然後只選取清單底部的 [銷售量]\*\*\*\* 和 [事實網際網路銷售計數]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="63196-177">To simplify your model, clear all the measures, and then select just **Sales Amount** and **Fact Internet Sales Count** at the bottom of the list.</span></span> <span data-ttu-id="63196-178">**FactInternetSalesReason** 只有一個量值，所以系統會自動為您加以選取。</span><span class="sxs-lookup"><span data-stu-id="63196-178">The **FactInternetSalesReason** only has one measure, so it is selected for you automatically.</span></span>  
  
10. <span data-ttu-id="63196-179">在維度清單中，您應該會看到 [維度銷售原因]\*\*\*\* 和 [維度銷售訂單]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="63196-179">In the dimension list, you should see **Dim Sales Reason** and **Dim Sales Orders**.</span></span>  
  
     <span data-ttu-id="63196-180">在 [選取新維度] 頁面上，精靈會提示您為 [事實網際網路銷售]\*\*\*\* 維度建立新的維度。</span><span class="sxs-lookup"><span data-stu-id="63196-180">In the Select New Dimensions page, the wizard prompts you to create a new dimension for **Fact Internet Sales Dimension**.</span></span> <span data-ttu-id="63196-181">您不需要這個維度，所以可以從清單中將它清除。</span><span class="sxs-lookup"><span data-stu-id="63196-181">You do not need this dimension, so you can clear it from the list.</span></span>  
  
11. <span data-ttu-id="63196-182">為 Cube 命名，然後按一下 [完成]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="63196-182">Name the cube and click **Finish**.</span></span>  
  
#### <a name="step-3-define-many-to-many-relationship"></a><span data-ttu-id="63196-183">步驟 3：定義多對多關聯性</span><span class="sxs-lookup"><span data-stu-id="63196-183">Step 3: Define Many-to-Many relationship</span></span>  
  
1.  <span data-ttu-id="63196-184">在 cube 設計師中，按一下 [維度使用方式] 索引標籤。請注意，[維度**銷售原因**] 和 [**事實網際網路銷售**] 之間已經有多對多關聯性。</span><span class="sxs-lookup"><span data-stu-id="63196-184">In cube designer, click Dimension Usage tab. Notice that there is already a many-to-many relationship between **Dim Sales Reason** and **Fact Internet Sales**.</span></span> <span data-ttu-id="63196-185">記得以下圖示表示多對多關聯性。</span><span class="sxs-lookup"><span data-stu-id="63196-185">Recall that the following icon indicates a many-to-many relationship.</span></span>  
  
     <span data-ttu-id="63196-186">![維度使用方式中的多對多圖示](../media/ssas-m2m-icondimusage.png "維度使用方式中的多對多圖示")</span><span class="sxs-lookup"><span data-stu-id="63196-186">![Many-to-many icon in dimension usage](../media/ssas-m2m-icondimusage.png "Many-to-many icon in dimension usage")</span></span>  
  
2.  <span data-ttu-id="63196-187">按一下 [維度銷售原因]\*\*\*\* 和 [事實網際網路銷售]\*\*\*\* 之間的交集資料格，然後按一下此按鈕來開啟 [定義關聯性] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="63196-187">Click on the intersection cell between **Dim Sales Reason** and **Fact Internet Sales**, and then click the button to open the Define Relationship dialog box.</span></span>  
  
     <span data-ttu-id="63196-188">您可以看到這個對話方塊是用來指定多對多關聯性。</span><span class="sxs-lookup"><span data-stu-id="63196-188">You can see that this dialog box is used to specify a many-to-many relationship.</span></span> <span data-ttu-id="63196-189">如果您改為新增具有一般關聯性的維度，您會使用這個對話方塊將它變更為多對多關聯性。</span><span class="sxs-lookup"><span data-stu-id="63196-189">If you were adding dimensions that had a regular relationship instead, you would use this dialog box to change it to many-to-many.</span></span>  
  
     <span data-ttu-id="63196-190">![維度使用方式中的 [定義關聯性] 按鈕](../media/ssas-m2m-btndimusage.png "維度使用方式中的 [定義關聯性] 按鈕")</span><span class="sxs-lookup"><span data-stu-id="63196-190">![Define Relationship button  in dimension usage](../media/ssas-m2m-btndimusage.png "Define Relationship button  in dimension usage")</span></span>  
  
3.  <span data-ttu-id="63196-191">將專案部署到 Analysis Services 多維度執行個體。</span><span class="sxs-lookup"><span data-stu-id="63196-191">Deploy the project to an Analysis Services multidimensional instance.</span></span> <span data-ttu-id="63196-192">在下一個步驟，您將會瀏覽 Excel 中的 Cube 來驗證其行為。</span><span class="sxs-lookup"><span data-stu-id="63196-192">In the next step, you will browse the cube in Excel to verify its behaviors.</span></span>  
  
## <a name="testing-many-to-many"></a><span data-ttu-id="63196-193">測試多對多</span><span class="sxs-lookup"><span data-stu-id="63196-193">Testing Many-to-Many</span></span>  
 <span data-ttu-id="63196-194">當您在 Cube 中定義多對多關聯性時，一定要進行測試，以確保查詢會傳回預期的結果。</span><span class="sxs-lookup"><span data-stu-id="63196-194">When you define a many-to-many relationship in a cube, testing is imperative to ensure queries return expected results.</span></span> <span data-ttu-id="63196-195">您應該使用將由使用者使用的用戶端應用程式工具來測試 Cube。</span><span class="sxs-lookup"><span data-stu-id="63196-195">You should test the cube using the client application tool that will be used by end-users.</span></span> <span data-ttu-id="63196-196">在下一個程序中，您將會使用 Excel 連接到 Cube 並驗證查詢結果。</span><span class="sxs-lookup"><span data-stu-id="63196-196">In this next procedure, you will use Excel to connect to the cube and verify query results.</span></span>  
  
#### <a name="browse-the-cube-in-excel"></a><span data-ttu-id="63196-197">在 Excel 中瀏覽 Cube</span><span class="sxs-lookup"><span data-stu-id="63196-197">Browse the cube in Excel</span></span>  
  
1.  <span data-ttu-id="63196-198">部署專案，然後瀏覽 Cube 來確認彙總有效。</span><span class="sxs-lookup"><span data-stu-id="63196-198">Deploy the project and then browse the cube to confirm the aggregations are valid.</span></span>  
  
2.  <span data-ttu-id="63196-199">在 Excel 中， **Data**  |  從 Analysis Services 按一下 [**來自其他來源**  |  **的**資料]。</span><span class="sxs-lookup"><span data-stu-id="63196-199">In Excel, click **Data** | **From Other Sources** | **From Analysis Services**.</span></span> <span data-ttu-id="63196-200">輸入伺服器的名稱，並選擇資料庫和 Cube。</span><span class="sxs-lookup"><span data-stu-id="63196-200">Enter the name of the server, choose the database and cube.</span></span>  
  
3.  <span data-ttu-id="63196-201">建立使用以下項目的樞紐分析表：</span><span class="sxs-lookup"><span data-stu-id="63196-201">Create a PivotTable that uses the following:</span></span>  
  
    -   <span data-ttu-id="63196-202">**銷售量** 作為值</span><span class="sxs-lookup"><span data-stu-id="63196-202">**Sales Amount** as the Value</span></span>  
  
    -   <span data-ttu-id="63196-203">資料行上的**銷售原因名稱**</span><span class="sxs-lookup"><span data-stu-id="63196-203">**Sales Reason Name** on Columns</span></span>  
  
    -   <span data-ttu-id="63196-204">資料列上的 [銷售訂單號碼]\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="63196-204">**Sales Order Number** on Rows</span></span>  
  
4.  <span data-ttu-id="63196-205">分析結果。</span><span class="sxs-lookup"><span data-stu-id="63196-205">Analyze the results.</span></span> <span data-ttu-id="63196-206">因為我們使用範例資料，所以最初的印象就是所有銷售訂單都有相同的值。</span><span class="sxs-lookup"><span data-stu-id="63196-206">Because we are using sample data, the initial impression is that all sales orders have identical values.</span></span> <span data-ttu-id="63196-207">但是，如果您向下捲動，您會開始看到資料的變化。</span><span class="sxs-lookup"><span data-stu-id="63196-207">However, if you scroll down, you begin to see data variation.</span></span>  
  
     <span data-ttu-id="63196-208">在往下捲動的過程中，您可以發現訂單號碼 **SO5382**的銷售量和銷售原因。</span><span class="sxs-lookup"><span data-stu-id="63196-208">Part way down, you can find the sales amount and sales reasons for order number **SO5382**.</span></span> <span data-ttu-id="63196-209">這個特別訂單的總計為 **539.99**，而歸因於此訂單的購買原因包括促銷、其他和價格。</span><span class="sxs-lookup"><span data-stu-id="63196-209">Grand total of this particular order is **539.99**, and the purchase reasons attributed to this order include Promotion, Other and Price.</span></span>  
  
     <span data-ttu-id="63196-210">![顯示多對多彙總的 Excel 工作表](../media/ssas-m2m-excel.png "顯示多對多彙總的 Excel 工作表")</span><span class="sxs-lookup"><span data-stu-id="63196-210">![Excel worksheet showing many-to-many aggregations](../media/ssas-m2m-excel.png "Excel worksheet showing many-to-many aggregations")</span></span>  
  
     <span data-ttu-id="63196-211">請注意，已經為訂單正確算出銷售量，整筆訂單為 **539.99** 。</span><span class="sxs-lookup"><span data-stu-id="63196-211">Notice that the Sales Amount is correctly calculated for the order; it is **539.99** for the entire order.</span></span> <span data-ttu-id="63196-212">雖然每個原因都指出 **539.99** ，但是該值並不是所有三個原因的總和，因而錯誤地誇大了總計。</span><span class="sxs-lookup"><span data-stu-id="63196-212">Although **539.99** is indicated for each reason, that value is not summed for all three reasons, erroneously inflating our grand total.</span></span>  
  
     <span data-ttu-id="63196-213">為什麼一開始要將銷售量放在每個銷售原因之下？</span><span class="sxs-lookup"><span data-stu-id="63196-213">Why put a sales amount under each sales reason in the first place?</span></span> <span data-ttu-id="63196-214">答案是因為它可讓我們識別可以歸因於每個原因的銷售量。</span><span class="sxs-lookup"><span data-stu-id="63196-214">The answer is that it allows us to identify the amount of sales we can attribute to each reason.</span></span>  
  
5.  <span data-ttu-id="63196-215">捲動到工作表的底部。</span><span class="sxs-lookup"><span data-stu-id="63196-215">Scroll to the bottom of the worksheet.</span></span> <span data-ttu-id="63196-216">現在很容易看到，相對於其他原因及總計，價格對於客戶購買而言是最重要的原因。</span><span class="sxs-lookup"><span data-stu-id="63196-216">It is now easy to see that Price is the most important reason for customer purchases, relative to other reasons as well as the grand total.</span></span>  
  
     <span data-ttu-id="63196-217">![顯示多對多總計的 Excel 活頁簿](../media/ssas-m2m-excelgrandtotal.png "顯示多對多總計的 Excel 活頁簿")</span><span class="sxs-lookup"><span data-stu-id="63196-217">![Excel workbook showing totals in many-to-many](../media/ssas-m2m-excelgrandtotal.png "Excel workbook showing totals in many-to-many")</span></span>  
  
#### <a name="tips-for-handling-unexpected-query-results"></a><span data-ttu-id="63196-218">處理非預期查詢結果的秘訣</span><span class="sxs-lookup"><span data-stu-id="63196-218">Tips for handling unexpected query results</span></span>  
  
1.  <span data-ttu-id="63196-219">隱藏中繼量值群組中不會在查詢內傳回有意義之結果的量值，例如計數。</span><span class="sxs-lookup"><span data-stu-id="63196-219">Hide measures in the intermediate measure group, such as the count, that do not return meaningful results in a query.</span></span> <span data-ttu-id="63196-220">這樣可避免人們嘗試使用彙總來產生無意義的資料。</span><span class="sxs-lookup"><span data-stu-id="63196-220">This prevents people from trying to use aggregations producing meaningless data.</span></span> <span data-ttu-id="63196-221">若要隱藏量值，請在維度設計師的屬性中將 [可見性]\*\*\*\* 設定為 **False**。</span><span class="sxs-lookup"><span data-stu-id="63196-221">To hide a measure, set **Visibility** to **False** on the attribute in dimension designer.</span></span>  
  
2.  <span data-ttu-id="63196-222">建立檢視方塊來使用量值和維度的子集，以便支援您想要提供的分析體驗。</span><span class="sxs-lookup"><span data-stu-id="63196-222">Create perspectives to use a subset of measures and dimensions that support the analytical experience you want to provide.</span></span> <span data-ttu-id="63196-223">包含許多量值群組和維度的 Cube 有可能無法在所有案例中一起順利運作。</span><span class="sxs-lookup"><span data-stu-id="63196-223">Possibly, a cube that contains many measure groups and dimensions do not work well together in all cases.</span></span> <span data-ttu-id="63196-224">藉由隔離您打算一起使用的維度和量值群組，您可以確保預測度更高的結果。</span><span class="sxs-lookup"><span data-stu-id="63196-224">By isolating the dimensions and measure groups that you intend to be used together, you ensure a more predictable outcome.</span></span>  
  
3.  <span data-ttu-id="63196-225">請務必記得，變更模型之後一定要部署及重新連接。</span><span class="sxs-lookup"><span data-stu-id="63196-225">Always remember to deploy and reconnect after changing a model.</span></span> <span data-ttu-id="63196-226">在 Excel 中，請使用樞紐分析表 [分析] 功能區上的 [重新整理] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="63196-226">In Excel, use the Refresh button on the PivotTable Analyze ribbon.</span></span>  
  
4.  <span data-ttu-id="63196-227">請避免在多個多對多關聯性中使用連結量值群組，特別是當這些關聯性位於不同 Cube 時。</span><span class="sxs-lookup"><span data-stu-id="63196-227">Avoid using linked measure groups in multiple many-to-many relationships, especially when those relationships are in different cubes.</span></span> <span data-ttu-id="63196-228">這樣做可能會導致模糊不清的彙總。</span><span class="sxs-lookup"><span data-stu-id="63196-228">Doing so can result in ambiguous aggregations.</span></span> <span data-ttu-id="63196-229">如需詳細資訊，請參閱 [Incorrect Amounts for Linked Measures in Cubes containing Many-to-Many Relationships (SSAS Troubleshooting)](https://social.technet.microsoft.com/wiki/contents/articles/22911.incorrect-amounts-for-linked-measures-in-cubes-containing-many-to-many-relationships-ssas-troubleshooting.aspx)(包含多對多關聯性之 Cube 中連結量值的數量不正確 (SSAS 疑難排解))。</span><span class="sxs-lookup"><span data-stu-id="63196-229">For more information, see [Incorrect Amounts for Linked Measures in Cubes containing Many-to-Many Relationships](https://social.technet.microsoft.com/wiki/contents/articles/22911.incorrect-amounts-for-linked-measures-in-cubes-containing-many-to-many-relationships-ssas-troubleshooting.aspx).</span></span>  
  
##  <a name="learn-more"></a><a name="bkmk_Learn"></a><span data-ttu-id="63196-230">瞭解更多資訊</span><span class="sxs-lookup"><span data-stu-id="63196-230">Learn more</span></span>  
 <span data-ttu-id="63196-231">使用以下連結來取得可幫助您掌握各個概念的其他資訊。</span><span class="sxs-lookup"><span data-stu-id="63196-231">Use the following links to get additional information that helps you master the concepts.</span></span>  
  
 [<span data-ttu-id="63196-232">我要如何在 Analysis Services 中定義多對多維度</span><span class="sxs-lookup"><span data-stu-id="63196-232">How do I define a many-to-many dimension in Analysis Services</span></span>](../lesson-5-3-defining-a-many-to-many-relationship.md)  
  
 [<span data-ttu-id="63196-233">多對多革命 2.0</span><span class="sxs-lookup"><span data-stu-id="63196-233">The many-to-many Revolution 2.0</span></span>](https://go.microsoft.com/fwlink/?LinkId=324760)  
  
 [<span data-ttu-id="63196-234">教學課程：SQL Server Analysis Services 的多對多維度範例</span><span class="sxs-lookup"><span data-stu-id="63196-234">Tutorial: Many-to-many dimension example for SQL Server Analysis Services</span></span>](https://go.microsoft.com/fwlink/?LinkId=324761)  
  
## <a name="see-also"></a><span data-ttu-id="63196-235">另請參閱</span><span class="sxs-lookup"><span data-stu-id="63196-235">See Also</span></span>  
 <span data-ttu-id="63196-236">[維度關聯性](../multidimensional-models-olap-logical-cube-objects/dimension-relationships.md) </span><span class="sxs-lookup"><span data-stu-id="63196-236">[Dimension Relationships](../multidimensional-models-olap-logical-cube-objects/dimension-relationships.md) </span></span>  
 <span data-ttu-id="63196-237">[安裝 Analysis Services 多維度模型化教學課程的範例資料和專案](../install-sample-data-and-projects.md) </span><span class="sxs-lookup"><span data-stu-id="63196-237">[Install Sample Data and Projects for the Analysis Services Multidimensional Modeling Tutorial](../install-sample-data-and-projects.md) </span></span>  
 <span data-ttu-id="63196-238">[&#40;SSDT 部署 Analysis Services 專案&#41;](deploy-analysis-services-projects-ssdt.md) </span><span class="sxs-lookup"><span data-stu-id="63196-238">[Deploy Analysis Services Projects &#40;SSDT&#41;](deploy-analysis-services-projects-ssdt.md) </span></span>  
 [<span data-ttu-id="63196-239">多維度模型中的檢視方塊</span><span class="sxs-lookup"><span data-stu-id="63196-239">Perspectives in Multidimensional Models</span></span>](perspectives-in-multidimensional-models.md)  
  
  
