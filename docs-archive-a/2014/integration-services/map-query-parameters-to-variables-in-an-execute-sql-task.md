---
title: 在執行 SQL 工作中將查詢參數對應至變數 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- queries [Integration Services], parameter mapping
- parameterized SQL commands [Integration Services]
- parameters [Integration Services]
- mapping query parameters to variables [Integration Services]
- Execute SQL task [Integration Services]
- variables [Integration Services], mapping parameters to
ms.assetid: 6a164349-dfcf-4995-80bc-d4e7aee52a83
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8511d70b40f2934680e1cb790763045c04e8204a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595166"
---
# <a name="map-query-parameters-to-variables-in-an-execute-sql-task"></a><span data-ttu-id="fae21-102">在執行 SQL 工作中將查詢參數對應到變數</span><span class="sxs-lookup"><span data-stu-id="fae21-102">Map Query Parameters to Variables in an Execute SQL Task</span></span>

  <span data-ttu-id="fae21-103">此主題描述如何在「執行 SQL」工作中使用參數化 SQL 陳述式，以及建立 SQL 陳述式中變數和參數之間的對應。</span><span class="sxs-lookup"><span data-stu-id="fae21-103">This topic describes how to use a parameterized SQL statement in the Execute SQL task and create mappings between variables and the parameters in the SQL statement.</span></span>  
  
 <span data-ttu-id="fae21-104">若要深入了解如何搭配不同連接類型使用的執行 SQL 工作、參數標記和參數名稱，請參閱 [執行 SQL 工作](control-flow/execute-sql-task.md) 和 [執行 SQL 工作中的參數和傳回碼](../../2014/integration-services/parameters-and-return-codes-in-the-execute-sql-task.md)。</span><span class="sxs-lookup"><span data-stu-id="fae21-104">To learn more about the Execute SQL task, the parameter markers, and parameter names you use with different connection types, see [Execute SQL Task](control-flow/execute-sql-task.md) and [Parameters and Return Codes in the Execute SQL Task](../../2014/integration-services/parameters-and-return-codes-in-the-execute-sql-task.md).</span></span>  
  
### <a name="to-map-a-query-parameter-to-a-variable"></a><span data-ttu-id="fae21-105">將查詢參數對應至變數</span><span class="sxs-lookup"><span data-stu-id="fae21-105">To map a query parameter to a variable</span></span>  
  
1.  <span data-ttu-id="fae21-106">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，開啟您要使用的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 封裝。</span><span class="sxs-lookup"><span data-stu-id="fae21-106">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package you want to work with.</span></span>  
  
2.  <span data-ttu-id="fae21-107">在 [方案總管] 中，按兩下封裝將其開啟。</span><span class="sxs-lookup"><span data-stu-id="fae21-107">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="fae21-108">按一下 **[控制流程]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="fae21-108">Click the **Control Flow** tab.</span></span>  
  
4.  <span data-ttu-id="fae21-109">如果封裝尚未包含執行 SQL 工作，則會加入一個執行 SQL 工作至封裝的控制流程。</span><span class="sxs-lookup"><span data-stu-id="fae21-109">If the package does not already include an Execute SQL task, add one to the control flow of the package.</span></span> <span data-ttu-id="fae21-110">如需詳細資訊，請參閱[在控制流程中加入或刪除工作或容器](control-flow/add-or-delete-a-task-or-a-container-in-a-control-flow.md)</span><span class="sxs-lookup"><span data-stu-id="fae21-110">For more information, see [Add or Delete a Task or a Container in a Control Flow](control-flow/add-or-delete-a-task-or-a-container-in-a-control-flow.md)</span></span>  
  <span data-ttu-id="fae21-111">.</span><span class="sxs-lookup"><span data-stu-id="fae21-111">.</span></span>  
  
5.  <span data-ttu-id="fae21-112">按兩下執行 SQL 工作。</span><span class="sxs-lookup"><span data-stu-id="fae21-112">Double-click the Execute SQL task.</span></span>  
  
6.  <span data-ttu-id="fae21-113">以下列方式的其中之一提供參數化 SQL 命令：</span><span class="sxs-lookup"><span data-stu-id="fae21-113">Provide a parameterized SQL command in one of the following ways:</span></span>  
  
    -   <span data-ttu-id="fae21-114">使用直接輸入，並在 SQLStatement 屬性中輸入 SQL 命令。</span><span class="sxs-lookup"><span data-stu-id="fae21-114">Use direct input and type the SQL command in the SQLStatement property.</span></span>  
  
    -   <span data-ttu-id="fae21-115">使用直接輸入，按一下 [建立查詢]，然後使用「查詢產生器」提供的圖形工具來建立 SQL 命令。</span><span class="sxs-lookup"><span data-stu-id="fae21-115">Use direct input, click **Build Query**, and then create an SQL command using the graphical tools that the Query Builder provides.</span></span>  
  
    -   <span data-ttu-id="fae21-116">使用檔案連接，然後參考包含 SQL 命令的檔案。</span><span class="sxs-lookup"><span data-stu-id="fae21-116">Use a file connection and then reference the file that contains the SQL command.</span></span>  
  
    -   <span data-ttu-id="fae21-117">使用變數，然後參考包含 SQL 命令的變數。</span><span class="sxs-lookup"><span data-stu-id="fae21-117">Use a variable and then reference the variable that contains the SQL command.</span></span>  
  
     <span data-ttu-id="fae21-118">您在參數化 SQL 陳述式中使用的參數標記，需視「執行 SQL」工作所使用的連接類型而定。</span><span class="sxs-lookup"><span data-stu-id="fae21-118">The parameter markers that you use in parameterized SQL statements depend on the connection type that the Execute SQL task uses.</span></span>  
  
    |<span data-ttu-id="fae21-119">連線類型</span><span class="sxs-lookup"><span data-stu-id="fae21-119">Connection type</span></span>|<span data-ttu-id="fae21-120">參數標記</span><span class="sxs-lookup"><span data-stu-id="fae21-120">Parameter marker</span></span>|  
    |---------------------|----------------------|  
    |<span data-ttu-id="fae21-121">ADO</span><span class="sxs-lookup"><span data-stu-id="fae21-121">ADO</span></span>|<span data-ttu-id="fae21-122">?</span><span class="sxs-lookup"><span data-stu-id="fae21-122">?</span></span>|  
    |<span data-ttu-id="fae21-123">ADO.NET 和 SQLMOBILE</span><span class="sxs-lookup"><span data-stu-id="fae21-123">ADO.NET and SQLMOBILE</span></span>|@\<parameter name>|  
    |<span data-ttu-id="fae21-124">ODBC</span><span class="sxs-lookup"><span data-stu-id="fae21-124">ODBC</span></span>|<span data-ttu-id="fae21-125">?</span><span class="sxs-lookup"><span data-stu-id="fae21-125">?</span></span>|  
    |<span data-ttu-id="fae21-126">EXCEL 和 OLE DB</span><span class="sxs-lookup"><span data-stu-id="fae21-126">EXCEL and OLE DB</span></span>|<span data-ttu-id="fae21-127">?</span><span class="sxs-lookup"><span data-stu-id="fae21-127">?</span></span>|  
  
     <span data-ttu-id="fae21-128">下表依照連接管理員類型列出 SELECT 命令的範例。</span><span class="sxs-lookup"><span data-stu-id="fae21-128">The following table lists examples of the SELECT command by connection manager type.</span></span> <span data-ttu-id="fae21-129">參數會在 WHERE 子句中提供篩選值。</span><span class="sxs-lookup"><span data-stu-id="fae21-129">Parameters provide the filter values in the WHERE clauses.</span></span> <span data-ttu-id="fae21-130">這些範例使用 SELECT，從 **中的** Product [!INCLUDE[ssSampleDBUserInputNonLocal](../includes/sssampledbuserinputnonlocal-md.md)] 資料表傳回 **ProductID** 大於及小於兩個參數所指定之值的產品。</span><span class="sxs-lookup"><span data-stu-id="fae21-130">The examples use SELECT to return products from the **Product** table in [!INCLUDE[ssSampleDBUserInputNonLocal](../includes/sssampledbuserinputnonlocal-md.md)] that have a **ProductID** greater than and less than the values specified by two parameters.</span></span>  
  
    |<span data-ttu-id="fae21-131">連線類型</span><span class="sxs-lookup"><span data-stu-id="fae21-131">Connection type</span></span>|<span data-ttu-id="fae21-132">SELECT 語法</span><span class="sxs-lookup"><span data-stu-id="fae21-132">SELECT syntax</span></span>|  
    |---------------------|-------------------|  
    |<span data-ttu-id="fae21-133">EXCEL、ODBC 和 OLEDB</span><span class="sxs-lookup"><span data-stu-id="fae21-133">EXCEL, ODBC, and OLEDB</span></span>|`SELECT* FROM Production.Product WHERE ProductId > ? AND ProductID < ?`|  
    |<span data-ttu-id="fae21-134">ADO</span><span class="sxs-lookup"><span data-stu-id="fae21-134">ADO</span></span>|`SELECT* FROM Production.Product WHERE ProductId > ? AND ProductID < ?`|  
    |[!INCLUDE[vstecado](../includes/vstecado-md.md)]|`SELECT* FROM Production.Product WHERE ProductId > @parmMinProductID AND ProductID < @parmMaxProductID`|  
  
     <span data-ttu-id="fae21-135">如需使用參數搭配預存程序的範例，請參閱[執行 SQL 工作中的參數和傳回碼](../../2014/integration-services/parameters-and-return-codes-in-the-execute-sql-task.md)。</span><span class="sxs-lookup"><span data-stu-id="fae21-135">For examples of using parameters with stored procedures, see [Parameters and Return Codes in the Execute SQL Task](../../2014/integration-services/parameters-and-return-codes-in-the-execute-sql-task.md).</span></span>  
  
7.  <span data-ttu-id="fae21-136">按一下 [參數對應]。</span><span class="sxs-lookup"><span data-stu-id="fae21-136">Click **Parameter Mapping**.</span></span>  
  
8.  <span data-ttu-id="fae21-137">若要加入參數對應，請按一下 [加入]。</span><span class="sxs-lookup"><span data-stu-id="fae21-137">To add a parameter mapping, click **Add**.</span></span>  
  
9. <span data-ttu-id="fae21-138">在 [參數名稱] 方塊中提供名稱。</span><span class="sxs-lookup"><span data-stu-id="fae21-138">Provide a name in the **Parameter Name** box.</span></span>  
  
     <span data-ttu-id="fae21-139">您所使用的參數名稱需視「執行 SQL」工作所使用的連接類型而定。</span><span class="sxs-lookup"><span data-stu-id="fae21-139">The parameter names that you use depend on the connection type that the Execute SQL task uses.</span></span>  
  
    |<span data-ttu-id="fae21-140">連線類型</span><span class="sxs-lookup"><span data-stu-id="fae21-140">Connection type</span></span>|<span data-ttu-id="fae21-141">參數名稱</span><span class="sxs-lookup"><span data-stu-id="fae21-141">Parameter name</span></span>|  
    |---------------------|--------------------|  
    |<span data-ttu-id="fae21-142">ADO</span><span class="sxs-lookup"><span data-stu-id="fae21-142">ADO</span></span>|<span data-ttu-id="fae21-143">Param1, Param2, ...</span><span class="sxs-lookup"><span data-stu-id="fae21-143">Param1, Param2, ...</span></span>|  
    |<span data-ttu-id="fae21-144">ADO.NET 和 SQLMOBILE</span><span class="sxs-lookup"><span data-stu-id="fae21-144">ADO.NET and SQLMOBILE</span></span>|@\<parameter name>|  
    |<span data-ttu-id="fae21-145">ODBC</span><span class="sxs-lookup"><span data-stu-id="fae21-145">ODBC</span></span>|<span data-ttu-id="fae21-146">1, 2, 3, ...</span><span class="sxs-lookup"><span data-stu-id="fae21-146">1, 2, 3, ...</span></span>|  
    |<span data-ttu-id="fae21-147">EXCEL 和 OLE DB</span><span class="sxs-lookup"><span data-stu-id="fae21-147">EXCEL and OLE DB</span></span>|<span data-ttu-id="fae21-148">0, 1, 2, 3, ...</span><span class="sxs-lookup"><span data-stu-id="fae21-148">0, 1, 2, 3, ...</span></span>|  
  
10. <span data-ttu-id="fae21-149">從 [變數名稱] 清單中，選取一個變數。</span><span class="sxs-lookup"><span data-stu-id="fae21-149">From the **Variable Name** list, select a variable.</span></span> <span data-ttu-id="fae21-150">如需詳細資訊，請參閱[加入、刪除、變更封裝中使用者定義變數的範圍](../../2014/integration-services/add-delete-change-scope-of-user-defined-variable-in-a-package.md)。</span><span class="sxs-lookup"><span data-stu-id="fae21-150">For more information, see [Add, Delete, Change Scope of User-Defined Variable in a Package](../../2014/integration-services/add-delete-change-scope-of-user-defined-variable-in-a-package.md).</span></span>  
  
11. <span data-ttu-id="fae21-151">在 [方向] 清單中，指定參數是輸入、輸出還是傳回值。</span><span class="sxs-lookup"><span data-stu-id="fae21-151">In the **Direction** list, specify if the parameter is an input, an output, or a return value.</span></span>  
  
12. <span data-ttu-id="fae21-152">在 [資料類型] 清單中，設定參數的資料類型。</span><span class="sxs-lookup"><span data-stu-id="fae21-152">In the **Data Type** list, set the data type of the parameter.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="fae21-153">參數的資料類型必須與變數的資料類型相容。</span><span class="sxs-lookup"><span data-stu-id="fae21-153">The data type of the parameter must be compatible with the data type of the variable.</span></span>  
  
13. <span data-ttu-id="fae21-154">針對 SQL 陳述式中的每個參數，重複步驟 8 到 11。</span><span class="sxs-lookup"><span data-stu-id="fae21-154">Repeat steps 8 through 11 for each parameter in the SQL statement.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="fae21-155">參數對應的順序必須與參數在 SQL 陳述式中出現的順序相同。</span><span class="sxs-lookup"><span data-stu-id="fae21-155">The order of parameter mappings must be the same as the order in which the parameters appear in the SQL statement.</span></span>  
  
14. <span data-ttu-id="fae21-156">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="fae21-156">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fae21-157">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fae21-157">See Also</span></span>  
 <span data-ttu-id="fae21-158">[執行 SQL 工作](control-flow/execute-sql-task.md) </span><span class="sxs-lookup"><span data-stu-id="fae21-158">[Execute SQL Task](control-flow/execute-sql-task.md) </span></span>  
 <span data-ttu-id="fae21-159">[執行 SQL 工作中的參數和傳回碼](../../2014/integration-services/parameters-and-return-codes-in-the-execute-sql-task.md) </span><span class="sxs-lookup"><span data-stu-id="fae21-159">[Parameters and Return Codes in the Execute SQL Task](../../2014/integration-services/parameters-and-return-codes-in-the-execute-sql-task.md) </span></span>  
 [<span data-ttu-id="fae21-160">Integration Services &#40;SSIS&#41; 變數</span><span class="sxs-lookup"><span data-stu-id="fae21-160">Integration Services &#40;SSIS&#41; Variables</span></span>](integration-services-ssis-variables.md)  
  
  
