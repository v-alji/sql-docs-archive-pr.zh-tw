---
title: 使用 Cube 回寫 (MDX) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- writeback [Analysis Services], cubes
- cubes [Analysis Services], modifying
- modifying cubes
- UPDATE CUBE statement
- cubes [Analysis Services], writeback
ms.assetid: ae2385fc-7fa0-4f8e-98d7-dcb0a5f0eeea
author: minewiskan
ms.author: owend
ms.openlocfilehash: 3ac43e9206619117c1fc090a594ca32ccbeeeb31
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594737"
---
# <a name="using-cube-writebacks-mdx"></a><span data-ttu-id="a599e-102">使用 Cube 回寫 (MDX)</span><span class="sxs-lookup"><span data-stu-id="a599e-102">Using Cube Writebacks (MDX)</span></span>
  <span data-ttu-id="a599e-103">您可以使用 [UPDATE CUBE](/sql/mdx/mdx-data-manipulation-update-cube) 陳述式更新 Cube。</span><span class="sxs-lookup"><span data-stu-id="a599e-103">You update a cube by using the [UPDATE CUBE](/sql/mdx/mdx-data-manipulation-update-cube) statement.</span></span> <span data-ttu-id="a599e-104">您可以使用此陳述式，來更新具有特定值的 Tuple。</span><span class="sxs-lookup"><span data-stu-id="a599e-104">This statement lets you update a tuple with a specific value.</span></span> <span data-ttu-id="a599e-105">若要有效地使用 UPDATE CUBE 陳述式更新 Cube，您必須了解陳述式的語法、可能發生的錯誤狀況，以及更新在 Cube 上所會產生的影響。</span><span class="sxs-lookup"><span data-stu-id="a599e-105">To effectively use the UPDATE CUBE statement to update a cube, you have to understand the syntax for the statement, the error conditions that can occur, and the affect that updates can have on a cube.</span></span>  
  
## <a name="update-cube-statement-syntax"></a><span data-ttu-id="a599e-106">UPDATE CUBE 陳述式語法</span><span class="sxs-lookup"><span data-stu-id="a599e-106">UPDATE CUBE Statement Syntax</span></span>  
 <span data-ttu-id="a599e-107">以下語法描述 UPDATE CUBE 陳述式：</span><span class="sxs-lookup"><span data-stu-id="a599e-107">The following syntax describes the UPDATE CUBE statement:</span></span>  
  
```  
UPDATE [CUBE] <Cube_Name> SET <tuple>.VALUE = <value> [,<tuple>.VALUE = <value>...]  
 [ USE_EQUAL_ALLOCATION | USE_EQUAL_INCREMENT |  
  USE_WEIGHTED_ALLOCATION [BY <weight value_expression>] |  
  USE_WEIGHTED_INCREMENT [BY <weight value_expression>] ]   
```  
  
 <span data-ttu-id="a599e-108">如果未為 Tuple 指定完整的一組座標，未指定的座標將會使用階層的預設成員。</span><span class="sxs-lookup"><span data-stu-id="a599e-108">If a full set of coordinates is not specified for the tuple, the unspecified coordinates will use the default member of the hierarchy.</span></span> <span data-ttu-id="a599e-109">識別的 Tuple 必須參考以 [Sum](/sql/mdx/sum-mdx) 函數彙總的資料格，而且絕不能使用導出成員作為資料格的其中一個座標。</span><span class="sxs-lookup"><span data-stu-id="a599e-109">The tuple identified must reference a cell that is aggregated with the [Sum](/sql/mdx/sum-mdx) function, and must not use a calculated member as one of the cell's coordinates.</span></span>  
  
 <span data-ttu-id="a599e-110">您可以將 UPDATE CUBE 陳述式視為一個副程式，其會對不可部份完成的資料格產生一系列的個別回寫作業。</span><span class="sxs-lookup"><span data-stu-id="a599e-110">You can think of the UPDATE CUBE statement as a subroutine that generates a series of individual writeback operations to atomic cells.</span></span> <span data-ttu-id="a599e-111">然後，所有個別的回寫作業就會積存到指定總和。</span><span class="sxs-lookup"><span data-stu-id="a599e-111">All these individual writeback operations then roll up into the specified sum.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a599e-112">當更新的資料格未重疊時，`Update Isolation Level` 連接字串屬性可用來增強 UPDATE CUBE 的效能。</span><span class="sxs-lookup"><span data-stu-id="a599e-112">When updated cells do not overlap, the `Update Isolation Level` connection string property can be used to enhance performance for UPDATE CUBE.</span></span> <span data-ttu-id="a599e-113">如需詳細資訊，請參閱<xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.ConnectionString%2A>。</span><span class="sxs-lookup"><span data-stu-id="a599e-113">For more information, see <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.ConnectionString%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a599e-114">範例</span><span class="sxs-lookup"><span data-stu-id="a599e-114">Example</span></span>  
 <span data-ttu-id="a599e-115">您可以在 Adventure Works Cube 中，使用銷售目標量值群組來測試 UPDATE CUBE。</span><span class="sxs-lookup"><span data-stu-id="a599e-115">You can test UPDATE CUBE using the Sales Targets measure group in the Adventure Works cube.</span></span> <span data-ttu-id="a599e-116">此量值群組包含 SUM 彙總的量值，這是 UPDATE CUBE 的需求。</span><span class="sxs-lookup"><span data-stu-id="a599e-116">This measure group consists of measures aggregated by SUM, which is a requirement for UPDATE CUBE.</span></span>  
  
1.  <span data-ttu-id="a599e-117">啟用 Adventure Works 資料庫中銷售目標量值群組的回寫功能。</span><span class="sxs-lookup"><span data-stu-id="a599e-117">Enable writeback for the Sales Targets measure group in the Adventure Works database.</span></span> <span data-ttu-id="a599e-118">在 Management Studio 中，以滑鼠右鍵按一下量值群組，指向 [回寫選項]\*\*\*\*，然後選擇 [啟用回寫]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a599e-118">In Management Studio, right-click a measure group, point to **Write Back Options**, choose **Enable Writeback**.</span></span>  
  
     <span data-ttu-id="a599e-119">您應該會在 [回寫] 資料夾中看到新的回寫資料表。</span><span class="sxs-lookup"><span data-stu-id="a599e-119">You should see a new writeback table in the Writeback folder.</span></span> <span data-ttu-id="a599e-120">資料表名稱為 WriteTable_Fact Sales Quota。</span><span class="sxs-lookup"><span data-stu-id="a599e-120">The table name is WriteTable_Fact Sales Quota.</span></span>  
  
2.  <span data-ttu-id="a599e-121">開啟 MDX 查詢視窗。</span><span class="sxs-lookup"><span data-stu-id="a599e-121">Open an MDX query window.</span></span> <span data-ttu-id="a599e-122">執行下列 SELECT 陳述式以檢視原始值：</span><span class="sxs-lookup"><span data-stu-id="a599e-122">Run the following select statement to view the original value:</span></span>  
  
    ```  
    SELECT [Measures].[Sales Amount Quota] on 0 ,  
    [Employee].[Employee Department].[Title].&[Sales Representative].children on 1  
    FROM [Adventure Works]  
  
    ```  
  
     <span data-ttu-id="a599e-123">您應該會看到每個銷售代表的銷售量配額。</span><span class="sxs-lookup"><span data-stu-id="a599e-123">You should see sales amount quotas for each representative.</span></span>  
  
3.  <span data-ttu-id="a599e-124">執行 UPDATE CUBE 陳述式以回寫新值。</span><span class="sxs-lookup"><span data-stu-id="a599e-124">Run the update cube statement to write back a new value.</span></span> <span data-ttu-id="a599e-125">在此範例中，我們將銷售量配額設為 0。</span><span class="sxs-lookup"><span data-stu-id="a599e-125">In this example, we are setting the sales amount quota to 0.</span></span> <span data-ttu-id="a599e-126">由於新值為 0，因此請勿指定配置方法。</span><span class="sxs-lookup"><span data-stu-id="a599e-126">Because the new value is 0, do not specify an allocation method.</span></span>  
  
    ```  
    UPDATE CUBE [Adventure Works]   
    SET ([Measures].[Sales Amount Quota], [Employee].[Employee Department].[Department].&[Sales]) = 0  
  
    ```  
  
4.  <span data-ttu-id="a599e-127">重新執行 SELECT 陳述式。</span><span class="sxs-lookup"><span data-stu-id="a599e-127">Re-run the SELECT statement.</span></span> <span data-ttu-id="a599e-128">您現在應該會看到配額為零。</span><span class="sxs-lookup"><span data-stu-id="a599e-128">You should now see zero for the quotas.</span></span>  
  
 <span data-ttu-id="a599e-129">回寫值受限於目前的工作階段。</span><span class="sxs-lookup"><span data-stu-id="a599e-129">The writeback value is constrained to the current session.</span></span> <span data-ttu-id="a599e-130">若要跨使用者和工作階段持續使用此值，請處理回寫資料表。</span><span class="sxs-lookup"><span data-stu-id="a599e-130">To persist the value across users and sessions, process the writeback table.</span></span> <span data-ttu-id="a599e-131">在 Management Studio 中，以滑鼠右鍵按一下 WriteTable_Fact Sales Quota，然後選擇 [處理]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a599e-131">In Management Studio, right-click WriteTable_Fact Sales Quota and choose **Process**.</span></span>  
  
 <span data-ttu-id="a599e-132">若要指定配置方法，新值必須大於零。</span><span class="sxs-lookup"><span data-stu-id="a599e-132">To specify an allocation method, the new value must be greater than zero.</span></span> <span data-ttu-id="a599e-133">在此範例中，銷售量配額的新值為兩百萬，而配置方法會將此數量分配給所有銷售代表。</span><span class="sxs-lookup"><span data-stu-id="a599e-133">In this example, the new value for Sales Amount Quota is two million and the allocation method distributes the amount across all sales representatives.</span></span>  
  
```  
UPDATE CUBE [Adventure Works]   
SET ([Measures].[Sales Amount Quota], [Employee].[Employee Department].[Department].&[Sales]) = 2000000   
USE_EQUAL_ALLOCATION  
```  
  
## <a name="error-conditions"></a><span data-ttu-id="a599e-134">錯誤狀況</span><span class="sxs-lookup"><span data-stu-id="a599e-134">Error Conditions</span></span>  
 <span data-ttu-id="a599e-135">下表描述會導致回寫失敗及錯誤結果的狀況。</span><span class="sxs-lookup"><span data-stu-id="a599e-135">The following table describes both what can cause writebacks to fail and the result of those errors.</span></span>  
  
|<span data-ttu-id="a599e-136">錯誤狀況</span><span class="sxs-lookup"><span data-stu-id="a599e-136">Error Condition</span></span>|<span data-ttu-id="a599e-137">結果</span><span class="sxs-lookup"><span data-stu-id="a599e-137">Result</span></span>|  
|---------------------|------------|  
|<span data-ttu-id="a599e-138">更新包括相同維度但未能同時存在的成員。</span><span class="sxs-lookup"><span data-stu-id="a599e-138">Update includes members from the same dimension that do not exist with one another.</span></span>|<span data-ttu-id="a599e-139">更新將會失敗。</span><span class="sxs-lookup"><span data-stu-id="a599e-139">Update will fail.</span></span> <span data-ttu-id="a599e-140">Cube 空間將不會包含參考資料格。</span><span class="sxs-lookup"><span data-stu-id="a599e-140">The cube space will not contain the referenced cell.</span></span>|  
|<span data-ttu-id="a599e-141">更新包括來源為不帶正負號類型的量值。</span><span class="sxs-lookup"><span data-stu-id="a599e-141">Update includes a measure sourced to a measure of an unsigned type.</span></span>|<span data-ttu-id="a599e-142">更新將會失敗。</span><span class="sxs-lookup"><span data-stu-id="a599e-142">Update will fail.</span></span> <span data-ttu-id="a599e-143">遞增需要量值能夠接受負值。</span><span class="sxs-lookup"><span data-stu-id="a599e-143">Increments require that the measure be able to take a negative value.</span></span>|  
|<span data-ttu-id="a599e-144">更新包括非彙總總和的量值。</span><span class="sxs-lookup"><span data-stu-id="a599e-144">Update includes a measure that aggregates other than sum.</span></span>|<span data-ttu-id="a599e-145">引發錯誤。</span><span class="sxs-lookup"><span data-stu-id="a599e-145">An error is raised.</span></span>|  
|<span data-ttu-id="a599e-146">嘗試在 Subcube 進行更新。</span><span class="sxs-lookup"><span data-stu-id="a599e-146">Update was tried on a subcube.</span></span>|<span data-ttu-id="a599e-147">引發錯誤。</span><span class="sxs-lookup"><span data-stu-id="a599e-147">An error is raised.</span></span>|  
  
## <a name="affect-of-cube-changes"></a><span data-ttu-id="a599e-148">Cube 變更的影響</span><span class="sxs-lookup"><span data-stu-id="a599e-148">Affect of Cube Changes</span></span>  
 <span data-ttu-id="a599e-149">以下變更將不會影響到回寫：</span><span class="sxs-lookup"><span data-stu-id="a599e-149">The following changes will not have an effect on a writeback:</span></span>  
  
-   <span data-ttu-id="a599e-150">處理 Cube、Cube 的量值群組，或 Cube 的維度。</span><span class="sxs-lookup"><span data-stu-id="a599e-150">Processing of a cube, the cube's measure groups, or the cube's dimensions.</span></span>  
  
-   <span data-ttu-id="a599e-151">將屬性增加到任何維度。</span><span class="sxs-lookup"><span data-stu-id="a599e-151">Adding attributes to any dimension.</span></span>  
  
-   <span data-ttu-id="a599e-152">增加新的維度。</span><span class="sxs-lookup"><span data-stu-id="a599e-152">Adding a new dimension.</span></span>  
  
-   <span data-ttu-id="a599e-153">刪除不包含回寫的維度。</span><span class="sxs-lookup"><span data-stu-id="a599e-153">Deleting a dimension that does not include the writeback.</span></span>  
  
-   <span data-ttu-id="a599e-154">新增、修改或移除階層。</span><span class="sxs-lookup"><span data-stu-id="a599e-154">Adding, modifying, or removing a hierarchy.</span></span>  
  
-   <span data-ttu-id="a599e-155">增加新的量值。</span><span class="sxs-lookup"><span data-stu-id="a599e-155">Adding a new measure.</span></span>  
  
 <span data-ttu-id="a599e-156">不移除回寫資料，就無法做出以下變更：</span><span class="sxs-lookup"><span data-stu-id="a599e-156">The following changes cannot be made without removing the writeback data:</span></span>  
  
-   <span data-ttu-id="a599e-157">如果回寫中包含屬性在內，但要刪除屬性或其屬性階層。</span><span class="sxs-lookup"><span data-stu-id="a599e-157">Deleting an attribute, or its attribute hierarchy, if the attribute is included in the writeback.</span></span> <span data-ttu-id="a599e-158">這包括明確地移除屬性或其屬性階層，或移除屬性的父維度。</span><span class="sxs-lookup"><span data-stu-id="a599e-158">This includes explicitly removing the attribute, or its attribute hierarchy, or removing the attribute's parent dimension.</span></span>  
  
-   <span data-ttu-id="a599e-159">刪除回寫中包含的量值。</span><span class="sxs-lookup"><span data-stu-id="a599e-159">Deleting a measure included in the writeback.</span></span>  
  
-   <span data-ttu-id="a599e-160">新增一個屬性，而回寫中包含的階層沒有 `(All)` 層級。</span><span class="sxs-lookup"><span data-stu-id="a599e-160">Adding an attribute without an `(All)` level to a dimension included in the writeback.</span></span>  
  
-   <span data-ttu-id="a599e-161">變更回寫中包含之維度的維度資料粒度。</span><span class="sxs-lookup"><span data-stu-id="a599e-161">Changing the dimension granularity for a dimension included in the writeback.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a599e-162">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a599e-162">See Also</span></span>  
 [<span data-ttu-id="a599e-163">修改資料 &#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="a599e-163">Modifying Data &#40;MDX&#41;</span></span>](mdx-data-modification-modifying-data.md)  
  
  
