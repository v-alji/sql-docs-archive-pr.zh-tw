---
title: Integration Services (SSIS) 變數 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- variables [Integration Services], passing between packages
- user-defined variables [Integration Services]
- scope [Integration Services]
- system variables [Integration Services]
- variables [Integration Services]
- variables [Integration Services], about variables
- values [Integration Services]
ms.assetid: c1e81ad6-628b-46d4-9b09-d2866517b6ca
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 956211ec971d69dc2fdb430dcada82a097280808
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596156"
---
# <a name="integration-services-ssis-variables"></a><span data-ttu-id="fe55a-102">Integration Services (SSIS) 變數</span><span class="sxs-lookup"><span data-stu-id="fe55a-102">Integration Services (SSIS) Variables</span></span>
  <span data-ttu-id="fe55a-103">變數會儲存 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 套件及其容器、工作與事件處理常式在執行階段所能使用的值。</span><span class="sxs-lookup"><span data-stu-id="fe55a-103">Variables store values that a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package and its containers, tasks, and event handlers can use at run time.</span></span> <span data-ttu-id="fe55a-104">「指令碼」工作和「指令碼」元件中的指令碼也可以使用變數。</span><span class="sxs-lookup"><span data-stu-id="fe55a-104">The scripts in the Script task and the Script component can also use variables.</span></span> <span data-ttu-id="fe55a-105">將工作和容器排序成工作流程的優先順序條件約束，可在其條件約束定義含有運算式時使用變數。</span><span class="sxs-lookup"><span data-stu-id="fe55a-105">The precedence constraints that sequence tasks and containers into a workflow can use variables when their constraint definitions include expressions.</span></span>  
  
 <span data-ttu-id="fe55a-106">您可將 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 封裝中的變數用於下列用途：</span><span class="sxs-lookup"><span data-stu-id="fe55a-106">You can use variables in [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] packages for the following purposes:</span></span>  
  
-   <span data-ttu-id="fe55a-107">在執行階段更新封裝元素的屬性。</span><span class="sxs-lookup"><span data-stu-id="fe55a-107">Updating properties of package elements at run time.</span></span> <span data-ttu-id="fe55a-108">例如，您可以動態設定「Foreach 迴圈」容器允許的並行可執行檔數目。</span><span class="sxs-lookup"><span data-stu-id="fe55a-108">For example, you can dynamically set the number of concurrent executables that a Foreach Loop container allows.</span></span>  
  
-   <span data-ttu-id="fe55a-109">包含記憶體中的查閱資料表。</span><span class="sxs-lookup"><span data-stu-id="fe55a-109">Including an in-memory lookup table.</span></span> <span data-ttu-id="fe55a-110">例如，封裝可執行用以載入一個具有資料值之變數的「執行 SQL」工作。</span><span class="sxs-lookup"><span data-stu-id="fe55a-110">For example, a package can run an Execute SQL task that loads a variable with data values.</span></span>  
  
-   <span data-ttu-id="fe55a-111">載入具有資料值的變數，然後將其用於指定 WHERE 子句中的搜尋條件。</span><span class="sxs-lookup"><span data-stu-id="fe55a-111">Loading variables with data values and then using them to specify a search condition in a WHERE clause.</span></span> <span data-ttu-id="fe55a-112">例如，「指令碼」工作中的指令碼可以更新 Transact-SQL 陳述式在「執行 SQL」工作中所使用的變數值。</span><span class="sxs-lookup"><span data-stu-id="fe55a-112">For example, the script in a Script task can update the value of a variable that is used by a Transact-SQL statement in an Execute SQL task.</span></span>  
  
-   <span data-ttu-id="fe55a-113">載入一個值為整數的變數，然後將該值用於控制封裝控制流程中的迴圈。</span><span class="sxs-lookup"><span data-stu-id="fe55a-113">Loading a variable with an integer and then using the value to control looping within a package control flow.</span></span> <span data-ttu-id="fe55a-114">例如，您可以使用「For 迴圈」容器之評估運算式中的變數來控制反覆運算。</span><span class="sxs-lookup"><span data-stu-id="fe55a-114">For example, you can use a variable in the evaluation expression of a For Loop container to control iteration.</span></span>  
  
-   <span data-ttu-id="fe55a-115">在執行階段擴展 Transact-SQL 陳述式的參數值。</span><span class="sxs-lookup"><span data-stu-id="fe55a-115">Populating parameter values for Transact-SQL statements at run time.</span></span> <span data-ttu-id="fe55a-116">例如，封裝可執行「執行 SQL」工作，然後使用變數動態設定 Transact-SQL 陳述式中的參數。</span><span class="sxs-lookup"><span data-stu-id="fe55a-116">For example, a package can run an Execute SQL task and then use variables to dynamically set the parameters in a Transact-SQL statement.</span></span>  
  
-   <span data-ttu-id="fe55a-117">建立包含變數值的運算式。</span><span class="sxs-lookup"><span data-stu-id="fe55a-117">Building expressions that include variable values.</span></span> <span data-ttu-id="fe55a-118">例如，「衍生的資料行」轉換可使用變數值乘以資料行值而取得的結果來擴展資料行。</span><span class="sxs-lookup"><span data-stu-id="fe55a-118">For example, the Derived Column transformation can populate a column with the result obtained by multiplying a variable value by a column value.</span></span>  
  
## <a name="system-and-user-defined-variables"></a><span data-ttu-id="fe55a-119">系統及使用者定義變數</span><span class="sxs-lookup"><span data-stu-id="fe55a-119">System and User-Defined Variables</span></span>  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="fe55a-120">支援兩種類型的變數：使用者自訂變數和系統變數。</span><span class="sxs-lookup"><span data-stu-id="fe55a-120">supports two types of variables: user-defined variables and system variables.</span></span> <span data-ttu-id="fe55a-121">使用者自訂變數由封裝開發人員定義，而系統變數則由 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]定義。</span><span class="sxs-lookup"><span data-stu-id="fe55a-121">User-defined variables are defined by package developers, and system variables are defined by [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].</span></span> <span data-ttu-id="fe55a-122">您可以根據封裝需要建立許多使用者自訂變數，但無法建立其他系統變數。</span><span class="sxs-lookup"><span data-stu-id="fe55a-122">You can create as many user-defined variables as a package requires, but you cannot create additional system variables.</span></span>  
  
 <span data-ttu-id="fe55a-123">所有的變數 (系統變數和使用者定義變數) 都可在「執行 SQL」工作用來將變數對應至 SQL 陳述式之參數的參數繫結中使用。</span><span class="sxs-lookup"><span data-stu-id="fe55a-123">All variables-system and user-defined-can be used in the parameter bindings that the Execute SQL task uses to map variables to parameters in SQL statements.</span></span> <span data-ttu-id="fe55a-124">如需詳細資訊，請參閱 [執行 SQL 工作](control-flow/execute-sql-task.md) 和 [執行 SQL 工作中的參數和傳回碼](../../2014/integration-services/parameters-and-return-codes-in-the-execute-sql-task.md)。</span><span class="sxs-lookup"><span data-stu-id="fe55a-124">For more information, see [Execute SQL Task](control-flow/execute-sql-task.md) and [Parameters and Return Codes in the Execute SQL Task](../../2014/integration-services/parameters-and-return-codes-in-the-execute-sql-task.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fe55a-125">使用者自訂變數和系統變數的名稱會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="fe55a-125">The names of user-defined and system variables are case sensitive.</span></span>  
  
 <span data-ttu-id="fe55a-126">您可以為下列所有 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 容器類型建立使用者自訂變數：封裝、Foreach 迴圈容器、For 迴圈容器、時序容器、工作和事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="fe55a-126">You can create user-defined variables for all [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] container types: packages, Foreach Loop containers, For Loop containers, Sequence containers, tasks, and event handlers.</span></span> <span data-ttu-id="fe55a-127">使用者自訂變數是容器 Variables 集合的成員。</span><span class="sxs-lookup"><span data-stu-id="fe55a-127">User-defined variables are members of the Variables collection of the container.</span></span>  
  
 <span data-ttu-id="fe55a-128">如果您使用 [!INCLUDE[ssIS](../includes/ssis-md.md)] 設計師建立封裝，則可以在 [!INCLUDE[ssIS](../includes/ssis-md.md)] 設計師之封裝總管索引標籤上的 [變數] 資料夾中，查看 Variables 集合的成員。</span><span class="sxs-lookup"><span data-stu-id="fe55a-128">If you create the package using [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer, you can see the members of the Variables collections in the **Variables** folders on the **Package Explorer** tab of [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="fe55a-129">資料夾會列出使用者自訂變數和系統變數。</span><span class="sxs-lookup"><span data-stu-id="fe55a-129">The folders list user-defined variables and system variables.</span></span>  
  
 <span data-ttu-id="fe55a-130">您可以利用下列方式設定使用者自訂變數：</span><span class="sxs-lookup"><span data-stu-id="fe55a-130">You can configure user-defined variables in the following ways:</span></span>  
  
-   <span data-ttu-id="fe55a-131">提供變數的名稱和描述。</span><span class="sxs-lookup"><span data-stu-id="fe55a-131">Provide a name and description for the variable.</span></span>  
  
-   <span data-ttu-id="fe55a-132">指定變數的命名空間。</span><span class="sxs-lookup"><span data-stu-id="fe55a-132">Specify a namespace for the variable.</span></span>  
  
-   <span data-ttu-id="fe55a-133">指示其值變更時變數是否會引發事件。</span><span class="sxs-lookup"><span data-stu-id="fe55a-133">Indicate whether the variable raises an event when its value changes.</span></span>  
  
-   <span data-ttu-id="fe55a-134">指示變數是唯讀還是可讀寫。</span><span class="sxs-lookup"><span data-stu-id="fe55a-134">Indicate whether the variable is read-only or read/write.</span></span>  
  
-   <span data-ttu-id="fe55a-135">使用運算式的評估結果，以設定變數值。</span><span class="sxs-lookup"><span data-stu-id="fe55a-135">Use the evaluation result of an expression to set the variable value.</span></span>  
  
-   <span data-ttu-id="fe55a-136">建立封裝或封裝物件 (例如工作) 範圍內的變數。</span><span class="sxs-lookup"><span data-stu-id="fe55a-136">Create the variable in the scope of the package or a package object such as a task.</span></span>  
  
-   <span data-ttu-id="fe55a-137">指定變數的值和資料類型。</span><span class="sxs-lookup"><span data-stu-id="fe55a-137">Specify the value and data type of the variable.</span></span>  
  
 <span data-ttu-id="fe55a-138">系統變數上唯一可設定的選項是指定其變更值時，它們是否會引發事件。</span><span class="sxs-lookup"><span data-stu-id="fe55a-138">The only configurable option on system variables is specifying whether they raise an event when they change value.</span></span>  
  
 <span data-ttu-id="fe55a-139">針對不同的容器類型可使用一組不同的系統變數。</span><span class="sxs-lookup"><span data-stu-id="fe55a-139">A different set of system variables is available for different container types.</span></span> <span data-ttu-id="fe55a-140">如需封裝及其元素所使用之系統變數的詳細資訊，請參閱 [系統變數](system-variables.md)。</span><span class="sxs-lookup"><span data-stu-id="fe55a-140">For more information about the system variables used by packages and their elements, see [System Variables](system-variables.md).</span></span>  
  
 <span data-ttu-id="fe55a-141">如需變數之實際使用狀況的詳細資訊，請參閱 [在封裝中使用變數](../../2014/integration-services/use-variables-in-packages.md)。</span><span class="sxs-lookup"><span data-stu-id="fe55a-141">For more information about real-life use scenarios for variables, see [Use Variables in Packages](../../2014/integration-services/use-variables-in-packages.md).</span></span>  
  
## <a name="variable-properties"></a><span data-ttu-id="fe55a-142">變數屬性</span><span class="sxs-lookup"><span data-stu-id="fe55a-142">Variable Properties</span></span>  
 <span data-ttu-id="fe55a-143">您可以透過在 [變數]  視窗或 [屬性]  視窗中設定下列屬性來設定使用者定義變數。</span><span class="sxs-lookup"><span data-stu-id="fe55a-143">You can configure user-defined variables by setting the following properties in either the **Variables** window or the **Properties** window.</span></span> <span data-ttu-id="fe55a-144">但某些屬性只能在 [屬性] 視窗中設定。</span><span class="sxs-lookup"><span data-stu-id="fe55a-144">Certain properties are available only in the Properties window.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fe55a-145">系統變數上唯一可設定的選項是指定其變更值時，它們是否會引發事件。</span><span class="sxs-lookup"><span data-stu-id="fe55a-145">The only configurable option on system variables is specifying whether they raise an event when they change value.</span></span>  
  
 <span data-ttu-id="fe55a-146">描述</span><span class="sxs-lookup"><span data-stu-id="fe55a-146">Description</span></span>  
 <span data-ttu-id="fe55a-147">指定變數的描述。</span><span class="sxs-lookup"><span data-stu-id="fe55a-147">Specifies the description of the variable.</span></span>  
  
 <span data-ttu-id="fe55a-148">EvaluateAsExpression</span><span class="sxs-lookup"><span data-stu-id="fe55a-148">EvaluateAsExpression</span></span>  
 <span data-ttu-id="fe55a-149">當屬性設定為時 `True` ，所提供的運算式會用來設定變數值。</span><span class="sxs-lookup"><span data-stu-id="fe55a-149">When the property is set to `True`, the expression provided is used to set the variable value.</span></span>  
  
 <span data-ttu-id="fe55a-150">運算是</span><span class="sxs-lookup"><span data-stu-id="fe55a-150">Expression</span></span>  
 <span data-ttu-id="fe55a-151">指定指派給變數的運算式。</span><span class="sxs-lookup"><span data-stu-id="fe55a-151">Specifies the expression that is assigned to the variable.</span></span>  
  
 <span data-ttu-id="fe55a-152">名稱</span><span class="sxs-lookup"><span data-stu-id="fe55a-152">Name</span></span>  
 <span data-ttu-id="fe55a-153">指定變數名稱。</span><span class="sxs-lookup"><span data-stu-id="fe55a-153">Specifies the variable name.</span></span>  
  
 <span data-ttu-id="fe55a-154">命名空間</span><span class="sxs-lookup"><span data-stu-id="fe55a-154">Namespace</span></span>  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="fe55a-155">提供兩個命名空間：**User** 和 **System**。</span><span class="sxs-lookup"><span data-stu-id="fe55a-155">provides two namespaces, **User** and **System**.</span></span> <span data-ttu-id="fe55a-156">依預設，自訂變數屬於 **User** 命名空間，而系統變數則屬於 **System** 命名空間。</span><span class="sxs-lookup"><span data-stu-id="fe55a-156">By default, custom variables are in the **User** namespace, and system variables are in the **System** namespace.</span></span> <span data-ttu-id="fe55a-157">您可以為使用者定義變數建立其他命名空間，並變更 **User** 命名空間的名稱，但是您無法變更 **System** 命名空間的名稱，也無法將變數加入 **System** 命名空間或將系統變數指派給其他命名空間。</span><span class="sxs-lookup"><span data-stu-id="fe55a-157">You can create additional namespaces for user-defined variables and change the name of the **User** namespace, but you cannot change the name of the **System** namespace, add variables to the **System** namespace, or assign system variables to a different namespace.</span></span>  
  
 <span data-ttu-id="fe55a-158">RaiseChangedEvent</span><span class="sxs-lookup"><span data-stu-id="fe55a-158">RaiseChangedEvent</span></span>  
 <span data-ttu-id="fe55a-159">當此屬性設為 `True` 時，`OnVariableValueChanged` 事件會在變數將值變更時產生。</span><span class="sxs-lookup"><span data-stu-id="fe55a-159">When the property is set to `True`, the `OnVariableValueChanged` event is raised when the variable changes value.</span></span>  
  
 <span data-ttu-id="fe55a-160">唯讀</span><span class="sxs-lookup"><span data-stu-id="fe55a-160">ReadOnly</span></span>  
 <span data-ttu-id="fe55a-161">當此屬性設為 `False`，表示變數可讀取\寫入。</span><span class="sxs-lookup"><span data-stu-id="fe55a-161">When the property is set to `False`, the variable is read\write.</span></span>  
  
 <span data-ttu-id="fe55a-162">範圍</span><span class="sxs-lookup"><span data-stu-id="fe55a-162">Scope</span></span>  
 > [!NOTE]  
>  <span data-ttu-id="fe55a-163">您只能透過按一下 [變數] 視窗中的 [移動變數] 來變更此屬性設定。</span><span class="sxs-lookup"><span data-stu-id="fe55a-163">You can change this property setting only by clicking **Move Variable** in the **Variables** window.</span></span>  
  
 <span data-ttu-id="fe55a-164">變數建立於封裝範圍之內，或封裝中的容器、工作或事件處理常式範圍之內。</span><span class="sxs-lookup"><span data-stu-id="fe55a-164">A variable is created within the scope of a package or within the scope of a container, task, or event handler in the package.</span></span> <span data-ttu-id="fe55a-165">因為封裝容器位於容器階層的最上層，所以具有封裝範圍的變數在功能上與全域變數相同，且可以由封裝內的所有容器使用。</span><span class="sxs-lookup"><span data-stu-id="fe55a-165">Because the package container is at the top of the container hierarchy, variables with package scope function like global variables and can be used by all containers in the package.</span></span> <span data-ttu-id="fe55a-166">同樣地，在容器 (例如「For 迴圈」容器) 範圍中定義的變數可由「For 迴圈」容器內的所有工作或容器使用。</span><span class="sxs-lookup"><span data-stu-id="fe55a-166">Similarly, variables defined within the scope of a container such as a For Loop container can be used by all tasks or containers within the For Loop container.</span></span>  
  
 <span data-ttu-id="fe55a-167">如果封裝使用「執行封裝」工作來執行其他封裝，則在呼叫封裝或「執行封裝」工作範圍中定義的變數可用於所呼叫的封裝，方法是使用「父封裝變數」組態類型。</span><span class="sxs-lookup"><span data-stu-id="fe55a-167">If a package runs other packages by using the Execute Package task, the variables defined in the scope of the calling package or the Execute Package task can be made available to the called package by using the Parent Package Variable configuration type.</span></span> <span data-ttu-id="fe55a-168">如需相關資訊，請參閱 [Package Configurations](../../2014/integration-services/package-configurations.md)。</span><span class="sxs-lookup"><span data-stu-id="fe55a-168">For more information, see [Package Configurations](../../2014/integration-services/package-configurations.md).</span></span>  
  
 <span data-ttu-id="fe55a-169">IncludeInDebugDump</span><span class="sxs-lookup"><span data-stu-id="fe55a-169">IncludeInDebugDump</span></span>  
 <span data-ttu-id="fe55a-170">指出偵錯傾印檔案中是否要包含變數值。</span><span class="sxs-lookup"><span data-stu-id="fe55a-170">Indicate whether the variable value is included in the debug dump files.</span></span>  
  
 <span data-ttu-id="fe55a-171">針對使用者自訂變數和系統變數， **InclueInDebugDump**選項的預設值為 `true` 。</span><span class="sxs-lookup"><span data-stu-id="fe55a-171">For user-defined variables and system variables, the default value for the **InclueInDebugDump** option is `true`.</span></span>  
  
 <span data-ttu-id="fe55a-172">不過，對於使用者定義的變數，系統會在**IncludeInDebugDump** `false` 符合下列條件時，將 IncludeInDebugDump 選項重設為：</span><span class="sxs-lookup"><span data-stu-id="fe55a-172">However, for user-defined variables, the system resets the **IncludeInDebugDump** option to `false` when the following conditions are met:</span></span>  
  
-   <span data-ttu-id="fe55a-173">如果**EvaluateAsExpression**變數屬性設定為，系統就會將 `true` **IncludeInDebugDump**選項重設為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="fe55a-173">If the **EvaluateAsExpression** variable property is set to `true`, the system resets the **IncludeInDebugDump** option to `false`.</span></span>  
  
     <span data-ttu-id="fe55a-174">若要在 debug 傾印檔案中包含運算式的文字做為變數值，請將**IncludeInDebugDump**選項設定為 `true` 。</span><span class="sxs-lookup"><span data-stu-id="fe55a-174">To include the text of the expression as the variable value in the debug dump files, set the **IncludeInDebugDump** option to `true`.</span></span>  
  
-   <span data-ttu-id="fe55a-175">如果變數資料類型變更為字串，系統會將**IncludeInDebugDump**選項重設為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="fe55a-175">If the variable data type is changed to a string, the system resets the **IncludeInDebugDump** option to `false`.</span></span>  
  
 <span data-ttu-id="fe55a-176">當系統將**IncludeInDebugDump**選項重設為時 `false` ，這可能會覆寫使用者所選取的值。</span><span class="sxs-lookup"><span data-stu-id="fe55a-176">When the system resets the **IncludeInDebugDump** option to `false`, this might override the value selected by the user.</span></span>  
  
 <span data-ttu-id="fe55a-177">值</span><span class="sxs-lookup"><span data-stu-id="fe55a-177">Value</span></span>  
 <span data-ttu-id="fe55a-178">使用者自訂變數值可以是常值或是運算式。</span><span class="sxs-lookup"><span data-stu-id="fe55a-178">The value of a user-defined variable can be a literal or an expression.</span></span> <span data-ttu-id="fe55a-179">變數包含設定變數值和該值之資料類型的選項。</span><span class="sxs-lookup"><span data-stu-id="fe55a-179">A variable includes options for setting the variable value and the data type of the value.</span></span> <span data-ttu-id="fe55a-180">兩個屬性必須相容：例如，同時使用字串值和整數資料類型是無效的。</span><span class="sxs-lookup"><span data-stu-id="fe55a-180">The two properties must be compatible: for example, the use of a string value together with an integer data type is not valid.</span></span>  
  
 <span data-ttu-id="fe55a-181">如果變數設定為做為運算式評估，則必須提供運算式。</span><span class="sxs-lookup"><span data-stu-id="fe55a-181">If the variable is configured to evaluate as an expression, you must provide an expression.</span></span> <span data-ttu-id="fe55a-182">在執行階段會評估運算式，且會將變數值設定為評估結果。</span><span class="sxs-lookup"><span data-stu-id="fe55a-182">At run time, the expression is evaluated, and the variable is set to the evaluation result.</span></span> <span data-ttu-id="fe55a-183">例如，如果變數使用運算式 `DATEPART("month", GETDATE())` ，則變數的值將為目前日期所在之月份數。</span><span class="sxs-lookup"><span data-stu-id="fe55a-183">For example, if a variable uses the expression `DATEPART("month", GETDATE())` the value of the variable is the number equivalent of the month for the current date.</span></span> <span data-ttu-id="fe55a-184">運算式必須是使用 [!INCLUDE[ssIS](../includes/ssis-md.md)] 運算式文法語法的有效運算式。</span><span class="sxs-lookup"><span data-stu-id="fe55a-184">The expression must be a valid expression that uses the [!INCLUDE[ssIS](../includes/ssis-md.md)] expression grammar syntax.</span></span> <span data-ttu-id="fe55a-185">當運算式搭配變數使用時，運算式可以使用運算式文法提供的常值、運算子和函數，但是運算式無法參考封裝中資料流程的資料行。</span><span class="sxs-lookup"><span data-stu-id="fe55a-185">When an expression is used with variables, the expression can use literals and the operators and functions that the expression grammar provides, but the expression cannot reference the columns from a data flow in the package.</span></span> <span data-ttu-id="fe55a-186">運算式的最大長度為 4000 個字元。</span><span class="sxs-lookup"><span data-stu-id="fe55a-186">The maximum length of an expression is 4000 characters.</span></span> <span data-ttu-id="fe55a-187">如需詳細資訊，請參閱 [Integration Services &#40;SSIS&#41; 運算式](expressions/integration-services-ssis-expressions.md)為止。</span><span class="sxs-lookup"><span data-stu-id="fe55a-187">For more information, see [Integration Services &#40;SSIS&#41; Expressions](expressions/integration-services-ssis-expressions.md).</span></span>  
  
 <span data-ttu-id="fe55a-188">ValueType</span><span class="sxs-lookup"><span data-stu-id="fe55a-188">ValueType</span></span>  
 > [!NOTE]  
>  <span data-ttu-id="fe55a-189">此屬性值會顯示在 [變數]\*\*\*\* 視窗中的 [資料類型]\*\*\*\* 資料行中。</span><span class="sxs-lookup"><span data-stu-id="fe55a-189">The property value appears in the **Data type** column in the **Variables** window.</span></span>  
  
 <span data-ttu-id="fe55a-190">指定變數值的資料類型。</span><span class="sxs-lookup"><span data-stu-id="fe55a-190">Specifies the data type of the variable value.</span></span>  
  
## <a name="configuring-variables"></a><span data-ttu-id="fe55a-191">設定變數</span><span class="sxs-lookup"><span data-stu-id="fe55a-191">Configuring Variables</span></span>  
 <span data-ttu-id="fe55a-192">您可以透過 [!INCLUDE[ssIS](../includes/ssis-md.md)] 設計師或以程式設計方式設定屬性。</span><span class="sxs-lookup"><span data-stu-id="fe55a-192">You can set properties through [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="fe55a-193">如需可以在 [ [!INCLUDE[ssIS](../includes/ssis-md.md)] 設計師] 中設定之屬性的詳細資訊，請參閱 [變數視窗](../../2014/integration-services/variables-window.md)。</span><span class="sxs-lookup"><span data-stu-id="fe55a-193">For more information about the properties that you can set in [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer, see [Variables Window](../../2014/integration-services/variables-window.md).</span></span>  
  
 <span data-ttu-id="fe55a-194">若要了解有關變數屬性，以及有關以程式設計方式設定這些屬性的詳細資訊，請參閱 <xref:Microsoft.SqlServer.Dts.Runtime.Variable>。</span><span class="sxs-lookup"><span data-stu-id="fe55a-194">To learn more about variable properties, and for more information about programmatically setting these properties, see <xref:Microsoft.SqlServer.Dts.Runtime.Variable>.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="fe55a-195">相關工作</span><span class="sxs-lookup"><span data-stu-id="fe55a-195">Related Tasks</span></span>  
 [<span data-ttu-id="fe55a-196">加入、刪除、變更封裝中使用者定義變數的範圍</span><span class="sxs-lookup"><span data-stu-id="fe55a-196">Add, Delete, Change Scope of User-Defined Variable in a Package</span></span>](../../2014/integration-services/add-delete-change-scope-of-user-defined-variable-in-a-package.md)  
  
 [<span data-ttu-id="fe55a-197">設定使用者定義變數的屬性</span><span class="sxs-lookup"><span data-stu-id="fe55a-197">Set the Properties of a User-Defined Variable</span></span>](../../2014/integration-services/set-the-properties-of-a-user-defined-variable.md)  
  
 [<span data-ttu-id="fe55a-198">在子封裝中使用變數和參數的值</span><span class="sxs-lookup"><span data-stu-id="fe55a-198">Use the Values of Variables and Parameters in a Child Package</span></span>](../../2014/integration-services/use-the-values-of-variables-and-parameters-in-a-child-package.md)  
  
 [<span data-ttu-id="fe55a-199">在資料流程元件中將查詢參數對應至變數</span><span class="sxs-lookup"><span data-stu-id="fe55a-199">Map Query Parameters to Variables in a Data Flow Component</span></span>](data-flow/map-query-parameters-to-variables-in-a-data-flow-component.md)  
  
  
