---
title: 建立函數以擷取變更資料 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- incremental load [Integration Services],creating function
ms.assetid: 55dd0946-bd67-4490-9971-12dfb5b9de94
author: chugugrace
ms.author: chugu
ms.openlocfilehash: cc1d5af0a64225aca4ff54570ad6504d25d62812
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707730"
---
# <a name="create-the-function-to-retrieve-the-change-data"></a><span data-ttu-id="7bb5e-102">建立函數以擷取變更資料</span><span class="sxs-lookup"><span data-stu-id="7bb5e-102">Create the Function to Retrieve the Change Data</span></span>
  <span data-ttu-id="7bb5e-103">完成執行累加式變更資料載入之 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 封裝的控制流程後，下一個工作是建立可擷取變更資料的資料表值函式。</span><span class="sxs-lookup"><span data-stu-id="7bb5e-103">After completing the control flow for an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that performs an incremental load of change data, the next task is to create a table-valued function that retrieves the change data.</span></span> <span data-ttu-id="7bb5e-104">第一次累加式載入前，您僅需要建立一次這個函數。</span><span class="sxs-lookup"><span data-stu-id="7bb5e-104">You only have to create this function one time before the first incremental load.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7bb5e-105">建立可擷取變更資料的函數是建立執行累加式變更資料載入之封裝程序的第二個步驟。</span><span class="sxs-lookup"><span data-stu-id="7bb5e-105">The creation of a function to retrieve the change data is the second step in the process of creating a package that performs an incremental load of change data.</span></span> <span data-ttu-id="7bb5e-106">如需建立此封裝之完整程序的描述，請參閱[變更資料擷取 &#40;SSIS&#41;](change-data-capture-ssis.md)。</span><span class="sxs-lookup"><span data-stu-id="7bb5e-106">For a description of the overall process for creating this package, see [Change Data Capture &#40;SSIS&#41;](change-data-capture-ssis.md).</span></span>  
  
## <a name="design-considerations-for-change-data-capture-functions"></a><span data-ttu-id="7bb5e-107">異動資料擷取函數的設計考量</span><span class="sxs-lookup"><span data-stu-id="7bb5e-107">Design Considerations for Change Data Capture Functions</span></span>  
 <span data-ttu-id="7bb5e-108">若要擷取變更資料，封裝之資料流程中的來源元件會呼叫下列其中一個異動資料擷取查詢函數：</span><span class="sxs-lookup"><span data-stu-id="7bb5e-108">To retrieve change data, a source component in the data flow of the package calls one of the following change data capture query functions:</span></span>  
  
-   <span data-ttu-id="7bb5e-109">**cdc.fn_cdc_get_net_changes_<capture_instance>** 對此查詢，會針對每個更新傳回單一資料列，其中包含每個變更資料列的最終狀態。</span><span class="sxs-lookup"><span data-stu-id="7bb5e-109">**cdc.fn_cdc_get_net_changes_<capture_instance>** For this query, the single row returned for each update contains the final state of each changed row.</span></span> <span data-ttu-id="7bb5e-110">在大部分的情況下，及僅需要淨變更查詢所傳回的資料。</span><span class="sxs-lookup"><span data-stu-id="7bb5e-110">In most cases, you only need the data returned by a query for net changes.</span></span> <span data-ttu-id="7bb5e-111">如需詳細資訊，請參閱 [cdc.fn_cdc_get_net_changes_&#60;capture_instance&#62; &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/cdc-fn-cdc-get-net-changes-capture-instance-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="7bb5e-111">For more information, see [cdc.fn_cdc_get_net_changes_&#60;capture_instance&#62; &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/cdc-fn-cdc-get-net-changes-capture-instance-transact-sql).</span></span>  
  
-   <span data-ttu-id="7bb5e-112">**cdc.fn_cdc_get_all_changes_<capture_instance>** 此查詢會傳回擷取間隔期間，在每個資料列中發生的所有變更。</span><span class="sxs-lookup"><span data-stu-id="7bb5e-112">**cdc.fn_cdc_get_all_changes_<capture_instance>** This query returns all the changes that have occurred in each row during the capture interval.</span></span> <span data-ttu-id="7bb5e-113">如需詳細資訊，請參閱 [cdc.fn_cdc_get_all_changes_&#60;capture_instance&#62; &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/cdc-fn-cdc-get-all-changes-capture-instance-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="7bb5e-113">For more information, see [cdc.fn_cdc_get_all_changes_&#60;capture_instance&#62;  &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/cdc-fn-cdc-get-all-changes-capture-instance-transact-sql).</span></span>  
  
 <span data-ttu-id="7bb5e-114">接著，來源元件會接收函數所傳回的結果，並將這些結果傳遞到下游的轉換和目的地，以便將變更資料套用到最終的目的地。</span><span class="sxs-lookup"><span data-stu-id="7bb5e-114">The source component then takes the results returned by the function and passes them to downstream transformations and destinations, which apply the change data to the final destination.</span></span>  
  
 <span data-ttu-id="7bb5e-115">不過， [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 來源元件無法直接呼叫這些異動資料擷取函數。</span><span class="sxs-lookup"><span data-stu-id="7bb5e-115">However, an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] source component cannot call these change data capture functions directly.</span></span> <span data-ttu-id="7bb5e-116">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 來源元件需要查詢所傳回之資料行的相關中繼資料。</span><span class="sxs-lookup"><span data-stu-id="7bb5e-116">An [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] source component requires metadata about the columns that the query returns.</span></span> <span data-ttu-id="7bb5e-117">異動資料擷取函數不會定義其輸出資料表的資料行。</span><span class="sxs-lookup"><span data-stu-id="7bb5e-117">The change data capture functions do not define the columns of their output table.</span></span> <span data-ttu-id="7bb5e-118">因此，這些函數不會針對 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 來源元件傳回足夠的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="7bb5e-118">Thus, these functions do not return sufficient metadata for an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] source component.</span></span>  
  
 <span data-ttu-id="7bb5e-119">但是，由於資料表值包裝函數會在其 RETURNS 子句中，明確定義其輸出資料表的資料行，因此您可以使用此種函數。</span><span class="sxs-lookup"><span data-stu-id="7bb5e-119">Instead, you use a table-valued wrapper function because this kind of function explicitly defines the columns of its output table in its RETURNS clause.</span></span> <span data-ttu-id="7bb5e-120">此資料行的明確定義會提供 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 來源元件所需的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="7bb5e-120">This explicit definition of columns provides the metadata that an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] source component needs.</span></span> <span data-ttu-id="7bb5e-121">您必須針對每個您要擷取其變更資料的資料表，建立這個函數。</span><span class="sxs-lookup"><span data-stu-id="7bb5e-121">You have to create this function for each table for which you want to retrieve change data.</span></span>  
  
 <span data-ttu-id="7bb5e-122">您有兩個選擇，可以建立呼叫異動資料擷取查詢函數的資料表值包裝函數：</span><span class="sxs-lookup"><span data-stu-id="7bb5e-122">You have two options for creating the table-valued wrapper function that calls the change data capture query function:</span></span>  
  
-   <span data-ttu-id="7bb5e-123">您可以呼叫 **sys.sp_cdc_generate_wrapper_function** 系統預存程序來建立資料表值函式。</span><span class="sxs-lookup"><span data-stu-id="7bb5e-123">You can call the **sys.sp_cdc_generate_wrapper_function** system stored procedure to create the table-valued functions for you.</span></span>  
  
-   <span data-ttu-id="7bb5e-124">您可以使用本主題中的指導方針與範例，撰寫自己的資料表值函式。</span><span class="sxs-lookup"><span data-stu-id="7bb5e-124">You can write your own table-valued function by using the guidelines and the example in this topic.</span></span>  
  
## <a name="calling-a-stored-procedure-to-create-the-table-valued-function"></a><span data-ttu-id="7bb5e-125">呼叫預存程序來建立資料表值函式</span><span class="sxs-lookup"><span data-stu-id="7bb5e-125">Calling a Stored Procedure to Create the Table-valued Function</span></span>  
 <span data-ttu-id="7bb5e-126">建立您需要之資料表值函式最快速而且簡單的方式，就是呼叫 **sys.sp_cdc_generate_wrapper_function** 系統預存程序。</span><span class="sxs-lookup"><span data-stu-id="7bb5e-126">The quickest and easiest way to create the table-valued functions that you need is to call the **sys.sp_cdc_generate_wrapper_function** system stored procedure.</span></span> <span data-ttu-id="7bb5e-127">此預存程序會產生指令碼來建立特別設計的包裝函式，以符合 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 來源元件的需求。</span><span class="sxs-lookup"><span data-stu-id="7bb5e-127">This stored procedure generates scripts to create wrapper functions that are designed specifically to meet the needs of an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] source component.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="7bb5e-128">**sys.sp_cdc_generate_wrapper_function** 系統預存程序不會直接建立包裝函式。</span><span class="sxs-lookup"><span data-stu-id="7bb5e-128">The **sys.sp_cdc_generate_wrapper_function** system stored procedure does not directly create the wrapper functions.</span></span> <span data-ttu-id="7bb5e-129">但是，預存程序會針對包裝函數產生 CREATE 指令碼。</span><span class="sxs-lookup"><span data-stu-id="7bb5e-129">Instead, the stored procedure generates the CREATE scripts for the wrapper functions.</span></span> <span data-ttu-id="7bb5e-130">開發人員必須先執行預存程序所產生的 CREATE 指令碼，累加式載入封裝才能呼叫包裝函數。</span><span class="sxs-lookup"><span data-stu-id="7bb5e-130">The developer must run the CREATE scripts that the stored procedure generates before an incremental load package can call the wrapper functions.</span></span>  
  
 <span data-ttu-id="7bb5e-131">若要了解如何使用此系統預存程序，您應該先了解程序的用途、程序所產生的指令碼，以及指令碼所建立的包裝函數。</span><span class="sxs-lookup"><span data-stu-id="7bb5e-131">To understand how to use this system stored procedure, you should understand what the procedure does, what scripts the procedure generates, and what wrapper functions the scripts create.</span></span>  
  
### <a name="understanding-and-using-the-stored-procedure"></a><span data-ttu-id="7bb5e-132">了解與使用預存程序</span><span class="sxs-lookup"><span data-stu-id="7bb5e-132">Understanding and Using the Stored Procedure</span></span>  
 <span data-ttu-id="7bb5e-133">**sys.sp_cdc_generate_wrapper_function** 系統預存程序會產生指令碼來建立 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 封裝使用的包裝函式。</span><span class="sxs-lookup"><span data-stu-id="7bb5e-133">The **sys.sp_cdc_generate_wrapper_function** system stored procedure generates scripts to create wrapper functions for use by [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages.</span></span>  
  
 <span data-ttu-id="7bb5e-134">此處為預存程序定義的前幾行：</span><span class="sxs-lookup"><span data-stu-id="7bb5e-134">Here are the first few lines of the definition of the stored procedure:</span></span>  
  
 `CREATE PROCEDURE sys.sp_cdc_generate_wrapper_function`  
  
 `(`  
  
 `@capture_instance sysname = null`  
  
 `@closed_high_end_point bit = 1,`  
  
 `@column_list = null,`  
  
 `@update_flag_list = null`  
  
 `)`  
  
 <span data-ttu-id="7bb5e-135">預存程序的所有參數都是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="7bb5e-135">All the parameters for the stored procedure are optional.</span></span> <span data-ttu-id="7bb5e-136">如果您在不提供任何參數值的情況下呼叫預存程序，預存程序就會為您可存取的所有擷取執行個體建立包裝函數。</span><span class="sxs-lookup"><span data-stu-id="7bb5e-136">If you call the stored procedure without supplying values for any of the parameters, the stored procedure creates wrapper functions for all the capture instances to which you have access.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7bb5e-137">如需此預存程序之語法及其參數的詳細資訊，請參閱 [sys.sp_cdc_generate_wrapper_function &#40;Transact-SQL &#41;](/sql/relational-databases/system-stored-procedures/sys-sp-cdc-generate-wrapper-function-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="7bb5e-137">For more information about the syntax of this stored procedure and its parameters, see [sys.sp_cdc_generate_wrapper_function &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-cdc-generate-wrapper-function-transact-sql).</span></span>  
  
 <span data-ttu-id="7bb5e-138">預存程序永遠會產生一個包裝函數來傳回每個擷取執行個體的所有變更。</span><span class="sxs-lookup"><span data-stu-id="7bb5e-138">The stored procedure always generates a wrapper function to return all changes from each capture instance.</span></span> <span data-ttu-id="7bb5e-139">如果在建立 *@supports_net_changes* capture 實例時設定了參數，預存程式也會產生一個包裝函式，以從每個適用的 capture 實例傳回淨變更。</span><span class="sxs-lookup"><span data-stu-id="7bb5e-139">If the *@supports_net_changes* parameter was set when the capture instance was created, the stored procedure also generates a wrapper function to return net changes from each applicable capture instance.</span></span>  
  
 <span data-ttu-id="7bb5e-140">預存程序會傳回包含兩個資料行的結果集：</span><span class="sxs-lookup"><span data-stu-id="7bb5e-140">The stored procedure returns a result set with two columns:</span></span>  
  
-   <span data-ttu-id="7bb5e-141">預存程序產生之包裝函數的名稱。</span><span class="sxs-lookup"><span data-stu-id="7bb5e-141">The name of the wrapper function that the stored procedure has generated.</span></span> <span data-ttu-id="7bb5e-142">此預存程序會從擷取執行個體的名稱衍生函數名稱</span><span class="sxs-lookup"><span data-stu-id="7bb5e-142">This stored procedure derives the function name from the name of the capture instance name.</span></span> <span data-ttu-id="7bb5e-143">(函數名稱為 'fn_all_changes_'，後面接著擷取執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="7bb5e-143">(The function name is 'fn_all_changes_' followed by the capture instance name.</span></span> <span data-ttu-id="7bb5e-144">用於淨變更函數 (如果有建立) 的前置詞為 'fn_net_changes_')。</span><span class="sxs-lookup"><span data-stu-id="7bb5e-144">The prefix used for the net changes function, if it is created, is 'fn_net_changes_'.)</span></span>  
  
-   <span data-ttu-id="7bb5e-145">適用於包裝函數的 CREATE 陳述式</span><span class="sxs-lookup"><span data-stu-id="7bb5e-145">The CREATE statement for the wrapper function.</span></span>  
  
### <a name="understanding-and-using-the-scripts-created-by-the-stored-procedure"></a><span data-ttu-id="7bb5e-146">了解與使用預存程序所建立的指令碼</span><span class="sxs-lookup"><span data-stu-id="7bb5e-146">Understanding and Using the Scripts Created by the Stored Procedure</span></span>  
 <span data-ttu-id="7bb5e-147">開發人員通常會使用 INSERT...EXEC 陳述式來呼叫 **sys.sp_cdc_generate_wrapper_function** 預存程序，並將預存程序所建立的指令碼儲存到暫存資料表中。</span><span class="sxs-lookup"><span data-stu-id="7bb5e-147">Typically, a developer would use an INSERT...EXEC statement to call the **sys.sp_cdc_generate_wrapper_function** stored procedure and save the scripts that the stored procedure creates to a temporary table.</span></span> <span data-ttu-id="7bb5e-148">接著，您可以個別選取並執行每個指令碼，以建立對應的包裝函數。</span><span class="sxs-lookup"><span data-stu-id="7bb5e-148">Each script could then be individually selected and run to create the corresponding wrapper function.</span></span> <span data-ttu-id="7bb5e-149">不過，開發人員也可以使用一組 SQL 命令來執行所有 CREATE 指令碼，如下列範例程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="7bb5e-149">However, a developer could also use one set of SQL commands to run all the CREATE scripts, as shown in the following sample code:</span></span>  
  
```  
create table #wrapper_functions  
      (function_name sysname, create_stmt nvarchar(max))  
insert into #wrapper_functions  
exec sys.sp_cdc_generate_wrapper_function  
  
declare @stmt nvarchar(max)  
declare #hfunctions cursor local fast_forward for   
      select create_stmt from #wrapper_functions  
open #hfunctions  
fetch #hfunctions into @stmt  
while (@@fetch_status <> -1)  
begin  
      exec sp_executesql @stmt  
      fetch #hfunctions into @stmt  
end  
close #hfunctions  
deallocate #hfunctions  
```  
  
### <a name="understanding-and-using-the-functions-created-by-the-stored-procedure"></a><span data-ttu-id="7bb5e-150">了解與使用預存程序所建立的函數</span><span class="sxs-lookup"><span data-stu-id="7bb5e-150">Understanding and Using the Functions Created by the Stored Procedure</span></span>  
 <span data-ttu-id="7bb5e-151">若要有系統地逐步解說已捕捉變更資料的時間軸，所產生的包裝函式 *@end_time* 會預期一個間隔的參數將會是 *@start_time* 後續間隔的參數。</span><span class="sxs-lookup"><span data-stu-id="7bb5e-151">To systematically walk the timeline of captured change data, the generated wrapper functions expect that the *@end_time* parameter for one interval will be the *@start_time* parameter for the subsequent interval.</span></span> <span data-ttu-id="7bb5e-152">遵循此慣例時，所產生的包裝函數可以進行下列工作：</span><span class="sxs-lookup"><span data-stu-id="7bb5e-152">When this convention is followed, the generated wrapper functions can do the following tasks:</span></span>  
  
-   <span data-ttu-id="7bb5e-153">將日期/時間值對應到內部使用的 LSN 值。</span><span class="sxs-lookup"><span data-stu-id="7bb5e-153">Map the date/time values to the LSN values that are used internally.</span></span>  
  
-   <span data-ttu-id="7bb5e-154">請確定沒有資料遺失或重複。</span><span class="sxs-lookup"><span data-stu-id="7bb5e-154">Ensure that no data is lost or repeated.</span></span>  
  
 <span data-ttu-id="7bb5e-155">為讓變更資料表之所有資料列的查詢更為簡單，所產生的包裝函數也支援下列慣例：</span><span class="sxs-lookup"><span data-stu-id="7bb5e-155">To make querying for all rows of a change table simpler, the generated wrapper functions also support the following conventions:</span></span>  
  
-   <span data-ttu-id="7bb5e-156">如果 @start_time 參數為 Null，包裝函數會使用擷取執行個體中最低的 LSN 值，作為查詢的下限。</span><span class="sxs-lookup"><span data-stu-id="7bb5e-156">If the @start_time parameter is null, the wrapper functions use the lowest LSN value in the capture instance as the lower bound of the query.</span></span>  
  
-   <span data-ttu-id="7bb5e-157">如果 @end_time 參數為 Null，包裝函數會使用擷取執行個體中最高的 LSN 值，作為查詢的上限。</span><span class="sxs-lookup"><span data-stu-id="7bb5e-157">If the @end_time parameter is null, the wrapper functions use the highest LSN value in the capture instance as the upper bound of the query.</span></span>  
  
 <span data-ttu-id="7bb5e-158">大部分使用者應該都可以在不修改的情況下，使用 **sys.sp_cdc_generate_wrapper_function** 系統預存程序所建立的包裝函式。</span><span class="sxs-lookup"><span data-stu-id="7bb5e-158">Most users should be able to use the wrapper functions that the **sys.sp_cdc_generate_wrapper_function** system stored procedure creates without modification.</span></span> <span data-ttu-id="7bb5e-159">不過，若要自訂包裝函數，您必須先自訂 CREATE 指令碼，然後再執行這些指令碼。</span><span class="sxs-lookup"><span data-stu-id="7bb5e-159">However, to customize the wrapper functions, you have to customize the CREATE scripts before you run the scripts.</span></span>  
  
 <span data-ttu-id="7bb5e-160">當您的封裝呼叫包裝函數時，該封裝必須提供三個參數的值。</span><span class="sxs-lookup"><span data-stu-id="7bb5e-160">When your package calls the wrapper functions, the package must supply values for three parameters.</span></span> <span data-ttu-id="7bb5e-161">這三個參數就像異動資料擷取函數所使用的三個參數。</span><span class="sxs-lookup"><span data-stu-id="7bb5e-161">These three parameters are like the three parameters that the change data capture functions use.</span></span> <span data-ttu-id="7bb5e-162">這三個參數如下所示：</span><span class="sxs-lookup"><span data-stu-id="7bb5e-162">These three parameters are as follows:</span></span>  
  
-   <span data-ttu-id="7bb5e-163">間隔的開始日期/時間值和結束日期/時間值。</span><span class="sxs-lookup"><span data-stu-id="7bb5e-163">The starting date/time value and the ending date/time value for the interval.</span></span> <span data-ttu-id="7bb5e-164">當包裝函數使用日期/時間值做為查詢間隔的端點時，異動資料擷取函數會使用兩個 LSN 值做為端點。</span><span class="sxs-lookup"><span data-stu-id="7bb5e-164">While the wrapper functions use date/time values as the end points for the query interval, the change data capture functions use two LSN values as the end points.</span></span>  
  
-   <span data-ttu-id="7bb5e-165">資料列篩選器。</span><span class="sxs-lookup"><span data-stu-id="7bb5e-165">The row filter.</span></span> <span data-ttu-id="7bb5e-166">對於包裝函式和變更資料捕獲函數而言， *@row_filter_option* 參數相同。</span><span class="sxs-lookup"><span data-stu-id="7bb5e-166">For both the wrapper functions and the change data capture functions, the *@row_filter_option* parameter is the same.</span></span> <span data-ttu-id="7bb5e-167">如需詳細資訊，請參閱 [cdc.fn_cdc_get_all_changes_&#60;capture_instance&#62; &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/cdc-fn-cdc-get-all-changes-capture-instance-transact-sql) 和 [cdc.fn_cdc_get_net_changes_&#60;capture_instance&#62; &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/cdc-fn-cdc-get-net-changes-capture-instance-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="7bb5e-167">For more information, see [cdc.fn_cdc_get_all_changes_&#60;capture_instance&#62;  &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/cdc-fn-cdc-get-all-changes-capture-instance-transact-sql) and [cdc.fn_cdc_get_net_changes_&#60;capture_instance&#62; &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/cdc-fn-cdc-get-net-changes-capture-instance-transact-sql).</span></span>  
  
 <span data-ttu-id="7bb5e-168">包裝函數所傳回的結果集包含下列資料：</span><span class="sxs-lookup"><span data-stu-id="7bb5e-168">The result set returned by the wrapper functions includesthe following data:</span></span>  
  
-   <span data-ttu-id="7bb5e-169">異動資料的所有要求資料行。</span><span class="sxs-lookup"><span data-stu-id="7bb5e-169">All of the requested columns of change data.</span></span>  
  
-   <span data-ttu-id="7bb5e-170">名稱為 __CDC_OPERATION 的資料行使用一或兩個字元欄位來識別與資料列關聯的作業。</span><span class="sxs-lookup"><span data-stu-id="7bb5e-170">A column named __CDC_OPERATION that uses a one- or two-character field to identify the operation that is associated with the row.</span></span> <span data-ttu-id="7bb5e-171">此欄位的有效值如下：'I' 用於插入、'D' 用於刪除、'UO'’ 用於更新舊值，而 'UN' 用於更新新值。</span><span class="sxs-lookup"><span data-stu-id="7bb5e-171">The valid values for this field are as follows: 'I' for insert, 'D' for delete, 'UO' for update old values, and 'UN' for update new values.</span></span>  
  
-   <span data-ttu-id="7bb5e-172">當您要求旗標時，會在作業碼之後以位資料行顯示，並以參數中指定的順序出現 *@update_flag_list* 。</span><span class="sxs-lookup"><span data-stu-id="7bb5e-172">Update flags, when you request them, that appear as bit columns after the operation code and in the order that is specified in the *@update_flag_list* parameter.</span></span> <span data-ttu-id="7bb5e-173">這些資料行的命名方式是將 '_uflag' 附加到相關聯的資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="7bb5e-173">These columns are named by appending '_uflag' to the associated column name.</span></span>  
  
 <span data-ttu-id="7bb5e-174">如果您的封裝呼叫查詢所有變更的包裝函式，該包裝函式也會傳回 __CDC_STARTLSN 和 \__CDC_SEQVAL 資料行。</span><span class="sxs-lookup"><span data-stu-id="7bb5e-174">If your package calls a wrapper function that queries for all changes, the wrapper function also returns the columns, __CDC_STARTLSN and \__CDC_SEQVAL.</span></span> <span data-ttu-id="7bb5e-175">這兩個資料行會分別成為結果集的第一和第二個資料行。</span><span class="sxs-lookup"><span data-stu-id="7bb5e-175">These two columns become the first and second columns, respectively, of the result set.</span></span> <span data-ttu-id="7bb5e-176">此包裝函數也會根據這兩個資料行，排序結果集。</span><span class="sxs-lookup"><span data-stu-id="7bb5e-176">The wrapper function also sorts the result set based on these two columns.</span></span>  
  
## <a name="writing-your-own-table-value-function"></a><span data-ttu-id="7bb5e-177">撰寫您自己的資料表值函式</span><span class="sxs-lookup"><span data-stu-id="7bb5e-177">Writing Your Own Table-Value Function</span></span>  
 <span data-ttu-id="7bb5e-178">您也可以改用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 撰寫呼叫異動資料擷取查詢函數的資料表值包裝函式，並將資料表值包裝函式儲存在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中。</span><span class="sxs-lookup"><span data-stu-id="7bb5e-178">You can also use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to write your own table-valued wrapper function that calls the change data capture query function, and store the table-valued wrapper function in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="7bb5e-179">如需如何建立 Transact-SQL 函數的詳細資訊，請參閱 [CREATE FUNCTION &#40;Transact-SQL &#41;](/sql/t-sql/statements/create-function-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="7bb5e-179">For more information about how to create a Transact-SQL function, see [CREATE FUNCTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-function-transact-sql).</span></span>  
  
 <span data-ttu-id="7bb5e-180">下列範例定義的資料表值函式可從 Customer 資料表中擷取指定之變更間隔的變更。</span><span class="sxs-lookup"><span data-stu-id="7bb5e-180">The following example defines a table-valued function that retrieves changes from a Customer table for the specified change interval.</span></span> <span data-ttu-id="7bb5e-181">此函數會使用異動資料擷取函數，將 `datetime` 值對應到變更資料表在內部使用的二進位記錄序號 (LSN) 值。</span><span class="sxs-lookup"><span data-stu-id="7bb5e-181">This function uses change data capture functions to map the `datetime` values to the binary log sequence number (LSN) values that the change tables use internally.</span></span> <span data-ttu-id="7bb5e-182">此函數也會處理數個特殊狀況：</span><span class="sxs-lookup"><span data-stu-id="7bb5e-182">This function also handles several special conditions:</span></span>  
  
-   <span data-ttu-id="7bb5e-183">針對開始時間傳遞 null 值時，此函數會使用最早可用的值。</span><span class="sxs-lookup"><span data-stu-id="7bb5e-183">When a null value is passed for the starting time, this function uses the earliest available value.</span></span>  
  
-   <span data-ttu-id="7bb5e-184">針對結束時間傳遞 null 值時，此函數會使用最晚可用的值。</span><span class="sxs-lookup"><span data-stu-id="7bb5e-184">When a null value is passed for the ending time, this function uses the latest available value.</span></span>  
  
-   <span data-ttu-id="7bb5e-185">當開始 LSN 等於結束 LSN (通常表示沒有所選間隔的記錄) 時，此函數會結束。</span><span class="sxs-lookup"><span data-stu-id="7bb5e-185">When the starting LSN is equal to the ending LSN, which usually indicates that there are no records for the selected interval, this function exits.</span></span>  
  
### <a name="example-of-a-table-value-function-that-queries-for-change-data"></a><span data-ttu-id="7bb5e-186">查詢變更資料之資料表值函式的範例</span><span class="sxs-lookup"><span data-stu-id="7bb5e-186">Example of a Table-Value Function that Queries for Change Data</span></span>  
  
```  
CREATE function CDCSample.uf_Customer (  
     @start_time datetime  
    ,@end_time datetime  
)  
returns @Customer table (  
     CustomerID int  
    ,TerritoryID int  
    ,CustomerType nchar(1)  
    ,rowguid uniqueidentifier  
    ,ModifiedDate datetime  
    ,CDC_OPERATION varchar(1)  
) as  
begin  
    declare @from_lsn binary(10), @to_lsn binary(10)  
  
    if (@start_time is null)  
        select @from_lsn = sys.fn_cdc_get_min_lsn('Customer')  
    else  
        select @from_lsn = sys.fn_cdc_increment_lsn(sys.fn_cdc_map_time_to_lsn('largest less than or equal',@start_time))  
  
    if (@end_time is null)  
        select @to_lsn = sys.fn_cdc_get_max_lsn()  
    else  
        select @to_lsn = sys.fn_cdc_map_time_to_lsn('largest less than or equal',@end_time)  
  
    if (@from_lsn = sys.fn_cdc_increment_lsn(@to_lsn))  
        return  
  
    -- Query for change data  
    insert into @Customer  
    select   
        CustomerID,      
        TerritoryID,   
        CustomerType,   
        rowguid,   
        ModifiedDate,   
        case __$operation  
                when 1 then 'D'  
                when 2 then 'I'  
                when 4 then 'U'  
                else null  
         end as CDC_OPERATION  
    from   
        cdc.fn_cdc_get_net_changes_Customer(@from_lsn, @to_lsn, 'all')  
  
    return  
end   
go  
  
```  
  
### <a name="retrieving-additional-metadata-with-the-change-data"></a><span data-ttu-id="7bb5e-187">擷取包含異動資料的其他中繼資料</span><span class="sxs-lookup"><span data-stu-id="7bb5e-187">Retrieving Additional Metadata with the Change Data</span></span>  
 <span data-ttu-id="7bb5e-188">雖然之前顯示之使用者建立的資料表值函式僅使用 **__$operation** 資料行，但 **cdc.fn_cdc_get_net_changes_<capture_instance>** 函式會針對每個變更資料列傳回四個中繼資料。</span><span class="sxs-lookup"><span data-stu-id="7bb5e-188">Although the user-created table-valued function shown earlier uses only the **__$operation** column, the **cdc.fn_cdc_get_net_changes_<capture_instance>** function returns four columns of metadata for each change row.</span></span> <span data-ttu-id="7bb5e-189">如果您要在資料流程中使用這些值，您可以傳回它們，當做資料表值包裝函數的其他資料行。</span><span class="sxs-lookup"><span data-stu-id="7bb5e-189">If you want to use these values in your data flow, you can return them as additional columns from the table-valued wrapper function.</span></span>  
  
|<span data-ttu-id="7bb5e-190">資料行名稱</span><span class="sxs-lookup"><span data-stu-id="7bb5e-190">Column name</span></span>|<span data-ttu-id="7bb5e-191">資料類型</span><span class="sxs-lookup"><span data-stu-id="7bb5e-191">Data type</span></span>|<span data-ttu-id="7bb5e-192">描述</span><span class="sxs-lookup"><span data-stu-id="7bb5e-192">Description</span></span>|  
|-----------------|---------------|-----------------|  
|<span data-ttu-id="7bb5e-193">**__$start_lsn**</span><span class="sxs-lookup"><span data-stu-id="7bb5e-193">**__$start_lsn**</span></span>|`binary(10)`|<span data-ttu-id="7bb5e-194">與變更之認可交易相關聯的 LSN。</span><span class="sxs-lookup"><span data-stu-id="7bb5e-194">LSN associated with the commit transaction for the change.</span></span><br /><br /> <span data-ttu-id="7bb5e-195">在相同交易中認可的所有變更都會共用相同的認可 LSN。</span><span class="sxs-lookup"><span data-stu-id="7bb5e-195">All changes committed in the same transaction share the same commit LSN.</span></span> <span data-ttu-id="7bb5e-196">例如，如果來源資料表上的更新作業修改了兩個不同的資料列，此變更資料表將會包含四個資料列 (其中兩個是舊值，而另外兩個是新值)，而且每個資料列都包含相同的 **__$start_lsn** 值。</span><span class="sxs-lookup"><span data-stu-id="7bb5e-196">For example, if an update operation on the source table modifies two different rows, the change table will contain four rows (two with the old values and two with the new values), each with the same **__$start_lsn** value.</span></span>|  
|<span data-ttu-id="7bb5e-197">**__$seqval**</span><span class="sxs-lookup"><span data-stu-id="7bb5e-197">**__$seqval**</span></span>|`binary(10)`|<span data-ttu-id="7bb5e-198">用來排序交易內資料列變更的序列值。</span><span class="sxs-lookup"><span data-stu-id="7bb5e-198">Sequence value that is used to order the row changes in a transaction.</span></span>|  
|<span data-ttu-id="7bb5e-199">**__$operation**</span><span class="sxs-lookup"><span data-stu-id="7bb5e-199">**__$operation**</span></span>|`int`|<span data-ttu-id="7bb5e-200">與變更相關聯的資料操作語言 (DML) 作業。</span><span class="sxs-lookup"><span data-stu-id="7bb5e-200">The data manipulation language (DML) operation associated with the change.</span></span> <span data-ttu-id="7bb5e-201">可以是下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="7bb5e-201">Can be one of the following:</span></span><br /><br /> <span data-ttu-id="7bb5e-202">1 = 刪除</span><span class="sxs-lookup"><span data-stu-id="7bb5e-202">1 = delete</span></span><br /><br /> <span data-ttu-id="7bb5e-203">2 = 插入</span><span class="sxs-lookup"><span data-stu-id="7bb5e-203">2 = insert</span></span><br /><br /> <span data-ttu-id="7bb5e-204">3 = 更新 (更新作業之前的值)。</span><span class="sxs-lookup"><span data-stu-id="7bb5e-204">3 = update (Values before the update operation.)</span></span><br /><br /> <span data-ttu-id="7bb5e-205">4 = 更新 (更新作業之後的值)。</span><span class="sxs-lookup"><span data-stu-id="7bb5e-205">4 = update (Values after the update operation.)</span></span>|  
|<span data-ttu-id="7bb5e-206">**__$update_mask**</span><span class="sxs-lookup"><span data-stu-id="7bb5e-206">**__$update_mask**</span></span>|`varbinary(128)`|<span data-ttu-id="7bb5e-207">位元遮罩，可根據變更資料表的資料行序數識別這些變更的資料行。</span><span class="sxs-lookup"><span data-stu-id="7bb5e-207">A bitmask that is based on the column ordinals of the change table identifying those columns that changed.</span></span> <span data-ttu-id="7bb5e-208">如果您必須判斷已經變更的資料行，可以檢查這個值。</span><span class="sxs-lookup"><span data-stu-id="7bb5e-208">You could examine this value if you had to determine which columns have changed.</span></span>|  
|**\<captured source table columns>**|<span data-ttu-id="7bb5e-209">視情況而異</span><span class="sxs-lookup"><span data-stu-id="7bb5e-209">varies</span></span>|<span data-ttu-id="7bb5e-210">這個函數所傳回的其餘資料行都是建立擷取執行個體時，在來源資料表中識別成擷取資料行的資料行。</span><span class="sxs-lookup"><span data-stu-id="7bb5e-210">The remaining columns returned by the function are the columns from the source table that were identified as captured columns when the capture instance was created.</span></span> <span data-ttu-id="7bb5e-211">如果擷取的資料行清單中沒有以序數指定任何資料行，就會傳回來源資料表中的所有資料行。</span><span class="sxs-lookup"><span data-stu-id="7bb5e-211">If no columns were originally specified in the captured column list, all columns in the source table are returned.</span></span>|  
  
 <span data-ttu-id="7bb5e-212">如需詳細資訊，請參閱 [cdc.fn_cdc_get_net_changes_&#60;capture_instance&#62; &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/cdc-fn-cdc-get-net-changes-capture-instance-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="7bb5e-212">For more information, see [cdc.fn_cdc_get_net_changes_&#60;capture_instance&#62; &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/cdc-fn-cdc-get-net-changes-capture-instance-transact-sql).</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="7bb5e-213">後續步驟</span><span class="sxs-lookup"><span data-stu-id="7bb5e-213">Next Step</span></span>  
 <span data-ttu-id="7bb5e-214">建立查詢變更資料的資料表值函式後，下一個步驟是開始在封裝中設計資料流程。</span><span class="sxs-lookup"><span data-stu-id="7bb5e-214">After you have created the table-valued function that queries for change data, the next step is to start designing the data flow in the package.</span></span>  
  
 <span data-ttu-id="7bb5e-215">**下一個主題：** [擷取與了解變更資料](retrieve-and-understand-the-change-data.md)</span><span class="sxs-lookup"><span data-stu-id="7bb5e-215">**Next topic:** [Retrieve and Understand the Change Data](retrieve-and-understand-the-change-data.md)</span></span>  
  
  
