---
title: OLE DB 來源 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.oledbsource.f1
helpviewer_keywords:
- sources [Integration Services], OLE DB
- OLE DB source [Integration Services]
ms.assetid: f87cc5f6-b078-40f3-9d87-7a65e13e4c86
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ce0d2a95639dc31ee8cf4dd9cdaca6844ad4a1d9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593480"
---
# <a name="ole-db-source"></a><span data-ttu-id="20059-102">OLE DB 來源</span><span class="sxs-lookup"><span data-stu-id="20059-102">OLE DB Source</span></span>
  <span data-ttu-id="20059-103">OLE DB 來源會使用資料庫資料表、檢視或 SQL 命令，從各種 OLE DB 相容的關聯式資料庫中擷取資料。</span><span class="sxs-lookup"><span data-stu-id="20059-103">The OLE DB source extracts data from a variety of OLE DB-compliant relational databases by using a database table, a view, or an SQL command.</span></span> <span data-ttu-id="20059-104">例如，OLE DB 來源可從 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Office Access 或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫的資料表中擷取資料。</span><span class="sxs-lookup"><span data-stu-id="20059-104">For example, the OLE DB source can extract data from tables in [!INCLUDE[msCoName](../../includes/msconame-md.md)] Office Access or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases.</span></span>  
  
 <span data-ttu-id="20059-105">OLE DB 來源提供四種不同的資料存取模式用來擷取資料：</span><span class="sxs-lookup"><span data-stu-id="20059-105">The OLE DB source provides four different data access modes for extracting data:</span></span>  
  
-   <span data-ttu-id="20059-106">資料表或檢視。</span><span class="sxs-lookup"><span data-stu-id="20059-106">A table or view.</span></span>  
  
-   <span data-ttu-id="20059-107">在變數中指定的資料表或檢視。</span><span class="sxs-lookup"><span data-stu-id="20059-107">A table or view specified in a variable.</span></span>  
  
-   <span data-ttu-id="20059-108">SQL 陳述式的結果。</span><span class="sxs-lookup"><span data-stu-id="20059-108">The results of an SQL statement.</span></span> <span data-ttu-id="20059-109">查詢可以是參數化查詢。</span><span class="sxs-lookup"><span data-stu-id="20059-109">The query can be a parameterized query.</span></span>  
  
-   <span data-ttu-id="20059-110">儲存在變數中之 SQL 陳述式的結果。</span><span class="sxs-lookup"><span data-stu-id="20059-110">The results of an SQL statement stored in a variable.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="20059-111">當您使用 SQL 陳述式呼叫從暫存資料表傳回結果的預存程序時，請使用 WITH RESULT SETS 選項定義結果集的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="20059-111">When you use an SQL statement to invoke a stored procedure that returns results from a temporary table, use the WITH RESULT SETS option to define metadata for the result set.</span></span>  
  
 <span data-ttu-id="20059-112">如果使用參數化查詢，您可以將變數對應到參數，以指定 SQL 陳述式中個別參數的值。</span><span class="sxs-lookup"><span data-stu-id="20059-112">If you use a parameterized query, you can map variables to parameters to specify the values for individual parameters in the SQL statements.</span></span>  
  
 <span data-ttu-id="20059-113">此來源使用 OLE DB 連接管理員連接到資料來源，且連接管理員會指定要使用的 OLE DB 提供者。</span><span class="sxs-lookup"><span data-stu-id="20059-113">This source uses an OLE DB connection manager to connect to a data source, and the connection manager specifies the OLE DB provider to use.</span></span> <span data-ttu-id="20059-114">如需相關資訊，請參閱 [OLE DB Connection Manager](../connection-manager/ole-db-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="20059-114">For more information, see [OLE DB Connection Manager](../connection-manager/ole-db-connection-manager.md).</span></span>  
  
 <span data-ttu-id="20059-115">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 專案也提供資料來源物件，您可從中建立 OLE DB 連接管理員，並提供資料來源和資料檢視讓 OLE DB 來源使用。</span><span class="sxs-lookup"><span data-stu-id="20059-115">An [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project also provides the data source object from which you can create an OLE DB connection manager, making data sources and data source views available to the OLE DB source.</span></span>  
  
 <span data-ttu-id="20059-116">根據 OLE DB 提供者而定，下列限制適用 OLE DB 來源：</span><span class="sxs-lookup"><span data-stu-id="20059-116">Depending on the OLE DB provider, some limitations apply to the OLE DB source:</span></span>  
  
-   <span data-ttu-id="20059-117">[!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB provider for Oracle 不支援 Oracle 資料類型 BLOB、CLOB、NCLOB、BFILE 或 UROWID，且 OLE DB 來源無法從含有這些資料類型之資料行的資料表擷取資料。</span><span class="sxs-lookup"><span data-stu-id="20059-117">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB provider for Oracle does not support the Oracle data types BLOB, CLOB, NCLOB, BFILE, OR UROWID, and the OLE DB source cannot extract data from tables that contain columns with these data types.</span></span>  
  
-   <span data-ttu-id="20059-118">IBM OLE DB DB2 提供者和 [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB DB2 提供者不支援使用呼叫預存程序的 SQL 命令。</span><span class="sxs-lookup"><span data-stu-id="20059-118">The IBM OLE DB DB2 provider and [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB DB2 provider do not support using an SQL command that calls a stored procedure.</span></span> <span data-ttu-id="20059-119">使用這類命令時，OLE DB 來源無法建立資料行中繼資料，結果在資料流程中跟隨 OLE DB 來源的資料流程元件便沒有任何可用的資料行資料，且資料流程執行失敗。</span><span class="sxs-lookup"><span data-stu-id="20059-119">When this kind of command is used, the OLE DB source cannot create the column metadata and, as a result, the data flow components that follow the OLE DB source in the data flow have no column data available and the execution of the data flow fails.</span></span>  
  
 <span data-ttu-id="20059-120">OLE DB 來源有一個一般輸出和一個錯誤輸出。</span><span class="sxs-lookup"><span data-stu-id="20059-120">The OLE DB source has one regular output and one error output.</span></span>  
  
## <a name="using-parameterized-sql-statements"></a><span data-ttu-id="20059-121">使用參數化 SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="20059-121">Using Parameterized SQL Statements</span></span>  
 <span data-ttu-id="20059-122">OLE DB 來源可以使用 SQL 陳述式來擷取資料。</span><span class="sxs-lookup"><span data-stu-id="20059-122">The OLE DB source can use an SQL statement to extract data.</span></span> <span data-ttu-id="20059-123">該陳述式可以是 SELECT 或 EXEC 陳述式。</span><span class="sxs-lookup"><span data-stu-id="20059-123">The statement can be a SELECT or an EXEC statement.</span></span>  
  
 <span data-ttu-id="20059-124">OLE DB 來源使用 OLE DB 連接管理員，以連接到其擷取資料的資料來源。</span><span class="sxs-lookup"><span data-stu-id="20059-124">The OLE DB source uses an OLE DB connection manager to connect to the data source from which it extracts data.</span></span> <span data-ttu-id="20059-125">根據 OLE DB 連接管理員使用的提供者以及連接管理員所連接的關聯式資料庫管理系統 (RDBMS) 而定，參數的命名和列示可能適用不同的規則。</span><span class="sxs-lookup"><span data-stu-id="20059-125">Depending on the provider that the OLE DB connection manager uses and the Relational Database Management System (RDBMS) that the connection manager connects to, different rules apply to the naming and listing of parameters.</span></span> <span data-ttu-id="20059-126">如果從 RDBMS 傳回參數名稱，您可以使用參數名稱，將參數清單中的參數對應到 SQL 陳述式中的參數；否則，參數便會按照它們在參數清單中的序數位置，對應到 SQL 陳述式中的參數。</span><span class="sxs-lookup"><span data-stu-id="20059-126">If the parameter names are returned from the RDBMS, you can use parameter names to map parameters in a parameter list to parameters in an SQL statement; otherwise, the parameters are mapped to the parameter in the SQL statement by their ordinal position in the parameter list.</span></span> <span data-ttu-id="20059-127">支援的參數名稱類型會因提供者而不同。</span><span class="sxs-lookup"><span data-stu-id="20059-127">The types of parameter names that are supported vary by provider.</span></span> <span data-ttu-id="20059-128">例如，某些提供者要求您必須使用變數或資料行名稱，而某些提供者則要求您使用 0 或 Param0 之類的符號名稱。</span><span class="sxs-lookup"><span data-stu-id="20059-128">For example, some providers require that you use the variable or column names, whereas some providers require that you use symbolic names such as 0 or Param0.</span></span> <span data-ttu-id="20059-129">如需有關在 SQL 陳述式中使用之參數名稱的資訊，請參考提供者專用的文件集。</span><span class="sxs-lookup"><span data-stu-id="20059-129">You should see the provider-specific documentation for information about the parameter names to use in SQL statements.</span></span>  
  
 <span data-ttu-id="20059-130">您在使用 OLE DB 連接管理員時無法使用參數化的子查詢，因為 OLE DB 來源無法透過 OLE DB 提供者衍生參數資訊。</span><span class="sxs-lookup"><span data-stu-id="20059-130">When you are use an OLE DB connection manager, you cannot use parameterized subqueries, because the OLE DB source cannot derive parameter information through the OLE DB provider.</span></span> <span data-ttu-id="20059-131">不過，您可以使用運算式來將參數值串連到查詢字串中並設定來源的 SqlCommand 屬性。在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師中，則可使用 [OLE DB 來源編輯器]  對話方塊來設定 OLE DB 來源，並在 [設定查詢參數]  對話方塊中將參數對應到變數。</span><span class="sxs-lookup"><span data-stu-id="20059-131">However, you can use an expression to concatenate the parameter values into the query string and to set the SqlCommand property of the source.In [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, you configure an OLE DB source by using the **OLE DB Source Editor** dialog box and map the parameters to variables in the **Set Query Parameter** dialog box.</span></span>  
  
### <a name="specifying-parameters-by-using-ordinal-positions"></a><span data-ttu-id="20059-132">使用序數位置指定參數</span><span class="sxs-lookup"><span data-stu-id="20059-132">Specifying Parameters by Using Ordinal Positions</span></span>  
 <span data-ttu-id="20059-133">如果沒有傳回任何參數名稱，便會依照參數在 [設定查詢參數]  對話方塊之 [參數]  清單中的列示順序，來控制執行階段中參數所對應的參數標記。</span><span class="sxs-lookup"><span data-stu-id="20059-133">If no parameter names are returned, the order in which the parameters are listed in the **Parameters** list in the **Set Query Parameter** dialog box governs which parameter marker they are mapped to at run time.</span></span> <span data-ttu-id="20059-134">清單中的第一個參數會對應到 SQL 陳述式裡的第一個 ?，</span><span class="sxs-lookup"><span data-stu-id="20059-134">The first parameter in the list maps to the first ?</span></span> <span data-ttu-id="20059-135">第二個參數則對應到第二個 ?，依此類推。</span><span class="sxs-lookup"><span data-stu-id="20059-135">in the SQL statement, the second to the second ?, and so on.</span></span>  
  
 <span data-ttu-id="20059-136">下列 SQL 陳述式會從 **資料庫的** Product [!INCLUDE[ssSampleDBUserInputNonLocal](../../includes/sssampledbuserinputnonlocal-md.md)] 資料表中選取資料列。</span><span class="sxs-lookup"><span data-stu-id="20059-136">The following SQL statement selects rows from the **Product** table in the [!INCLUDE[ssSampleDBUserInputNonLocal](../../includes/sssampledbuserinputnonlocal-md.md)] database.</span></span> <span data-ttu-id="20059-137">[對應]  清單中的第一個參數對應到 **Color** 資料行的第一個參數，第二個參數則對應到 **Size** 資料行。</span><span class="sxs-lookup"><span data-stu-id="20059-137">The first parameter in the **Mappings** list maps to the first parameter to the **Color** column, the second parameter to the **Size** column.</span></span>  
  
 `SELECT * FROM Production.Product WHERE Color = ? AND Size = ?`  
  
 <span data-ttu-id="20059-138">參數名稱無效。</span><span class="sxs-lookup"><span data-stu-id="20059-138">The parameter names have no effect.</span></span> <span data-ttu-id="20059-139">例如，如果參數名稱與它所套用的資料行名稱相同，但並未放在 [參數]  清單中的正確序數位置，則執行階段中發生的參數對應將會使用參數的序數位置，而非參數名稱。</span><span class="sxs-lookup"><span data-stu-id="20059-139">For example, if a parameter is named the same as the column to which it applies, but not put in the correct ordinal position in the **Parameters** list, the parameter mapping that occurs at run time will use the ordinal position of the parameter, not the parameter name.</span></span>  
  
 <span data-ttu-id="20059-140">EXEC 命令通常會要求您使用在程序中提供參數值的變數名稱作為參數名稱。</span><span class="sxs-lookup"><span data-stu-id="20059-140">The EXEC command typically requires that you use the names of the variables that provide parameter values in the procedure as parameter names.</span></span>  
  
### <a name="specifying-parameters-by-using-names"></a><span data-ttu-id="20059-141">使用名稱指定參數</span><span class="sxs-lookup"><span data-stu-id="20059-141">Specifying Parameters by Using Names</span></span>  
 <span data-ttu-id="20059-142">如果由 RDBMS 傳回實際參數名稱，SELECT 和 EXEC 陳述式所使用的參數便會依照名稱進行對應。</span><span class="sxs-lookup"><span data-stu-id="20059-142">If the actual parameter names are returned from the RDBMS, the parameters used by a SELECT and EXEC statement are mapped by name.</span></span> <span data-ttu-id="20059-143">參數名稱必須符合 SELECT 陳述式或 EXEC 陳述式執行之預存程序所預期的名稱。</span><span class="sxs-lookup"><span data-stu-id="20059-143">The parameter names must match the names that the stored procedure, run by the SELECT statement or the EXEC statement, expects.</span></span>  
  
 <span data-ttu-id="20059-144">下列 SQL 陳述式會執行 **uspGetWhereUsedProductID** 預存程序，您可在 [!INCLUDE[ssSampleDBUserInputNonLocal](../../includes/sssampledbuserinputnonlocal-md.md)] 資料庫中找到該預存程序。</span><span class="sxs-lookup"><span data-stu-id="20059-144">The following SQL statement runs the **uspGetWhereUsedProductID** stored procedure, available in the [!INCLUDE[ssSampleDBUserInputNonLocal](../../includes/sssampledbuserinputnonlocal-md.md)] database.</span></span>  
  
 `EXEC uspGetWhereUsedProductID ?, ?`  
  
 <span data-ttu-id="20059-145">預存程序需要有變數 `@StartProductID` 和 `@CheckDate`，才能提供參數值。</span><span class="sxs-lookup"><span data-stu-id="20059-145">The stored procedure expects the variables, `@StartProductID` and `@CheckDate`, to provide parameter values.</span></span> <span data-ttu-id="20059-146">參數出現在 [對應]  清單中的順序並無任何影響。</span><span class="sxs-lookup"><span data-stu-id="20059-146">The order in which the parameters appear in the **Mappings** list is irrelevant.</span></span> <span data-ttu-id="20059-147">唯一的需求是參數名稱必須符合預存程序中的變數名稱，包括 \@ 符號。</span><span class="sxs-lookup"><span data-stu-id="20059-147">The only requirement is that the parameter names match the variable names in the stored procedure, including the \@ sign.</span></span>  
  
### <a name="mapping-parameters-to-variables"></a><span data-ttu-id="20059-148">將參數對應至變數</span><span class="sxs-lookup"><span data-stu-id="20059-148">Mapping Parameters to Variables</span></span>  
 <span data-ttu-id="20059-149">參數會對應到在執行階段中提供參數值的變數。</span><span class="sxs-lookup"><span data-stu-id="20059-149">The parameters are mapped to variables that provide the parameter values at run time.</span></span> <span data-ttu-id="20059-150">這些變數通常是使用者自訂變數，不過您也可以使用 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 提供的系統變數。</span><span class="sxs-lookup"><span data-stu-id="20059-150">The variables are typically user-defined variables, although you can also use the system variables that [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] provides.</span></span> <span data-ttu-id="20059-151">如果您使用的是使用者自訂變數，請務必將資料類型設定為與對應參數所參考之資料行資料類型相容的類型。</span><span class="sxs-lookup"><span data-stu-id="20059-151">If you use user-defined variables, make sure that you set the data type to a type that is compatible with the data type of the column that the mapped parameter references.</span></span> <span data-ttu-id="20059-152">如需詳細資訊，請參閱 [Integration Services &#40;SSIS&#41; 變數](../integration-services-ssis-variables.md)。</span><span class="sxs-lookup"><span data-stu-id="20059-152">For more information, see [Integration Services &#40;SSIS&#41; Variables](../integration-services-ssis-variables.md).</span></span>  
  
## <a name="troubleshooting-the-ole-db-source"></a><span data-ttu-id="20059-153">疑難排解 OLE DB 來源</span><span class="sxs-lookup"><span data-stu-id="20059-153">Troubleshooting the OLE DB Source</span></span>  
 <span data-ttu-id="20059-154">您可以記錄 OLE DB 來源對外部資料提供者所執行的呼叫。</span><span class="sxs-lookup"><span data-stu-id="20059-154">You can log the calls that the OLE DB source makes to external data providers.</span></span> <span data-ttu-id="20059-155">您可以使用這項記錄功能，疑難排解 OLE DB 來源執行的從外部資料來源載入資料的作業。</span><span class="sxs-lookup"><span data-stu-id="20059-155">You can use this logging capability to troubleshoot the loading of data from external data sources that the OLE DB source performs.</span></span> <span data-ttu-id="20059-156">若要記錄 OLE DB 來源對外部資料提供者執行的呼叫，請啟用封裝記錄，然後在封裝層級選取 [診斷]  事件。</span><span class="sxs-lookup"><span data-stu-id="20059-156">To log the calls that the OLE DB source makes to external data providers, enable package logging and select the **Diagnostic** event at the package level.</span></span> <span data-ttu-id="20059-157">如需詳細資訊，請參閱 [封裝執行的疑難排解工具](../troubleshooting/troubleshooting-tools-for-package-execution.md)。</span><span class="sxs-lookup"><span data-stu-id="20059-157">For more information, see [Troubleshooting Tools for Package Execution](../troubleshooting/troubleshooting-tools-for-package-execution.md).</span></span>  
  
## <a name="configuring-the-ole-db-source"></a><span data-ttu-id="20059-158">設定 OLE DB 來源</span><span class="sxs-lookup"><span data-stu-id="20059-158">Configuring the OLE DB Source</span></span>  
 <span data-ttu-id="20059-159">您可以程式設計方式或透過「 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師」設定屬性。</span><span class="sxs-lookup"><span data-stu-id="20059-159">You can set properties programmatically or through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="20059-160">如需可在 [OLE DB 來源編輯器]\*\*\*\* 對話方塊中設定之屬性的詳細資訊，請按下列其中一個主題：</span><span class="sxs-lookup"><span data-stu-id="20059-160">For more information about the properties that you can set in the **OLE DB Source Editor** dialog box, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="20059-161">OLE DB 來源編輯器 &#40;連線管理員頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="20059-161">OLE DB Source Editor &#40;Connection Manager Page&#41;</span></span>](../ole-db-source-editor-connection-manager-page.md)  
  
-   [<span data-ttu-id="20059-162">OLE DB 來源編輯器 &#40;資料行頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="20059-162">OLE DB Source Editor &#40;Columns Page&#41;</span></span>](../ole-db-source-editor-columns-page.md)  
  
-   [<span data-ttu-id="20059-163">OLE DB 來源編輯器 &#40;錯誤輸出頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="20059-163">OLE DB Source Editor &#40;Error Output Page&#41;</span></span>](../ole-db-source-editor-error-output-page.md)  
  
 <span data-ttu-id="20059-164">**[進階編輯器]** 對話方塊會反映能以程式設計的方式設定之屬性。</span><span class="sxs-lookup"><span data-stu-id="20059-164">The **Advanced Editor** dialog box reflects the properties that can be set programmatically.</span></span> <span data-ttu-id="20059-165">如需有關可以在 **[進階編輯器]** 對話方塊中或以程式設計方式設定之屬性的詳細資訊，請按下列其中一個主題：</span><span class="sxs-lookup"><span data-stu-id="20059-165">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="20059-166">Common Properties</span><span class="sxs-lookup"><span data-stu-id="20059-166">Common Properties</span></span>](../common-properties.md)  
  
-   [<span data-ttu-id="20059-167">OLE DB 自訂屬性</span><span class="sxs-lookup"><span data-stu-id="20059-167">OLE DB Custom Properties</span></span>](ole-db-custom-properties.md)  
  
## <a name="related-tasks"></a><span data-ttu-id="20059-168">相關工作</span><span class="sxs-lookup"><span data-stu-id="20059-168">Related Tasks</span></span>  
  
-   [<span data-ttu-id="20059-169">使用 OLE DB 來源來擷取資料</span><span class="sxs-lookup"><span data-stu-id="20059-169">Extract Data by Using the OLE DB Source</span></span>](ole-db-source.md)  
  
-   [<span data-ttu-id="20059-170">在資料流程元件中將查詢參數對應至變數</span><span class="sxs-lookup"><span data-stu-id="20059-170">Map Query Parameters to Variables in a Data Flow Component</span></span>](map-query-parameters-to-variables-in-a-data-flow-component.md)  
  
-   [<span data-ttu-id="20059-171">設定資料流程元件的屬性</span><span class="sxs-lookup"><span data-stu-id="20059-171">Set the Properties of a Data Flow Component</span></span>](set-the-properties-of-a-data-flow-component.md)  
  
-   [<span data-ttu-id="20059-172">排序合併和合併聯結轉換的資料</span><span class="sxs-lookup"><span data-stu-id="20059-172">Sort Data for the Merge and Merge Join Transformations</span></span>](transformations/sort-data-for-the-merge-and-merge-join-transformations.md)  
  
## <a name="related-content"></a><span data-ttu-id="20059-173">相關內容</span><span class="sxs-lookup"><span data-stu-id="20059-173">Related Content</span></span>  
 <span data-ttu-id="20059-174">social.technet.microsoft.com 上的 Wiki 文章： [SSIS with Oracle Connectors](https://go.microsoft.com/fwlink/?LinkId=220670)(SSIS 與 Oracle 連接器)。</span><span class="sxs-lookup"><span data-stu-id="20059-174">Wiki article, [SSIS with Oracle Connectors](https://go.microsoft.com/fwlink/?LinkId=220670), on social.technet.microsoft.com.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20059-175">另請參閱</span><span class="sxs-lookup"><span data-stu-id="20059-175">See Also</span></span>  
 <span data-ttu-id="20059-176">[OLE DB 目的地](ole-db-destination.md) </span><span class="sxs-lookup"><span data-stu-id="20059-176">[OLE DB Destination](ole-db-destination.md) </span></span>  
 <span data-ttu-id="20059-177">[Integration Services &#40;SSIS&#41; 變數](../integration-services-ssis-variables.md) </span><span class="sxs-lookup"><span data-stu-id="20059-177">[Integration Services &#40;SSIS&#41; Variables](../integration-services-ssis-variables.md) </span></span>  
 [<span data-ttu-id="20059-178">資料流程</span><span class="sxs-lookup"><span data-stu-id="20059-178">Data Flow</span></span>](data-flow.md)  
  
  
