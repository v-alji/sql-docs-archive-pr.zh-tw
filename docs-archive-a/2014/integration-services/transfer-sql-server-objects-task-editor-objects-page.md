---
title: 傳送 SQL Server 物件工作編輯器 (物件頁面) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transfersqlserverobjects.objects.f1
helpviewer_keywords:
- Transfer SQL Server Objects Task Editor
ms.assetid: 8cc09118-70ac-4013-8308-d87f8411ca0c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7038939b02d17b2449a374be51f7f9fa42eae7d8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703109"
---
# <a name="transfer-sql-server-objects-task-editor-objects-page"></a><span data-ttu-id="1f987-102">傳送 SQL Server 物件工作編輯器 (物件頁面)</span><span class="sxs-lookup"><span data-stu-id="1f987-102">Transfer SQL Server Objects Task Editor (Objects Page)</span></span>
  <span data-ttu-id="1f987-103">使用 [傳送 SQL Server 物件工作編輯器] 對話方塊的 [物件] 頁面，即可指定用於從某個 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 執行個體將一或多個 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 物件複製到另一個執行個體的屬性。</span><span class="sxs-lookup"><span data-stu-id="1f987-103">Use the **Objects** page of the **Transfer SQL Server Objects Task Editor** dialog box to specify properties for copying one or more [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] objects from one instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] to another.</span></span> <span data-ttu-id="1f987-104">資料表、檢視、預存程序和使用者自訂函數是您可以複製的一些 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 物件範例。</span><span class="sxs-lookup"><span data-stu-id="1f987-104">Tables, views, stored procedures, and user-defined functions are a few examples of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] objects that you can copy.</span></span> <span data-ttu-id="1f987-105">如需有關這項工作的詳細資訊，請參閱＜ [Transfer SQL Server Objects Task](control-flow/transfer-sql-server-objects-task.md)＞。</span><span class="sxs-lookup"><span data-stu-id="1f987-105">For more information about this task, see [Transfer SQL Server Objects Task](control-flow/transfer-sql-server-objects-task.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1f987-106">建立傳送 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 物件工作的使用者必須具有來源伺服器物件的足夠權限，才能選取它們以進行複製，也要具有存取會從該處傳送物件之目的地伺服器資料庫的權限。</span><span class="sxs-lookup"><span data-stu-id="1f987-106">The user who creates the Transfer [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Objects task must have sufficient permissions on the source server objects to select them for copying, and permission to access the destination server database where the objects will be transferred.</span></span>  
  
## <a name="static-options"></a><span data-ttu-id="1f987-107">靜態選項</span><span class="sxs-lookup"><span data-stu-id="1f987-107">Static Options</span></span>  
 <span data-ttu-id="1f987-108">**SourceConnection**</span><span class="sxs-lookup"><span data-stu-id="1f987-108">**SourceConnection**</span></span>  
 <span data-ttu-id="1f987-109">在清單中選取一個 SMO 連線管理員，或按一下 **\<New connection...>** ，以建立新的來源伺服器連線。</span><span class="sxs-lookup"><span data-stu-id="1f987-109">Select a SMO connection manager in the list, or click **\<New connection...>** to create a new connection to the source server.</span></span>  
  
 <span data-ttu-id="1f987-110">**SourceDatabase**</span><span class="sxs-lookup"><span data-stu-id="1f987-110">**SourceDatabase**</span></span>  
 <span data-ttu-id="1f987-111">在來源伺服器上選取會從中複製物件的資料庫。</span><span class="sxs-lookup"><span data-stu-id="1f987-111">Select a database on the source server from which objects will be copied.</span></span>  
  
 <span data-ttu-id="1f987-112">**DestinationConnection**</span><span class="sxs-lookup"><span data-stu-id="1f987-112">**DestinationConnection**</span></span>  
 <span data-ttu-id="1f987-113">在清單中選取一個 SMO 連線管理員，或按一下 **\<New connection...>** ，以建立新的目的地伺服器連線。</span><span class="sxs-lookup"><span data-stu-id="1f987-113">Select a SMO connection manager in the list, or click **\<New connection...>** to create a new connection to the destination server.</span></span>  
  
 <span data-ttu-id="1f987-114">**DestinationDatabase**</span><span class="sxs-lookup"><span data-stu-id="1f987-114">**DestinationDatabase**</span></span>  
 <span data-ttu-id="1f987-115">在目的地伺服器上選取物件會被複製到的資料庫。</span><span class="sxs-lookup"><span data-stu-id="1f987-115">Select a database on the destination server to which objects will be copied.</span></span>  
  
 <span data-ttu-id="1f987-116">**DropObjectsFirst**</span><span class="sxs-lookup"><span data-stu-id="1f987-116">**DropObjectsFirst**</span></span>  
 <span data-ttu-id="1f987-117">選取在複製之前，是否先在目的地伺服器上卸除選取的物件。</span><span class="sxs-lookup"><span data-stu-id="1f987-117">Select whether the selected objects will be dropped first on the destination server before copying.</span></span>  
  
 <span data-ttu-id="1f987-118">**IncludeExtendedProperties**</span><span class="sxs-lookup"><span data-stu-id="1f987-118">**IncludeExtendedProperties**</span></span>  
 <span data-ttu-id="1f987-119">選取當物件從來源伺服器複製到目的地伺服器時是否包含擴充屬性。</span><span class="sxs-lookup"><span data-stu-id="1f987-119">Select whether extended properties will be included when objects are copied from the source to the destination server.</span></span>  
  
 <span data-ttu-id="1f987-120">**CopyData**</span><span class="sxs-lookup"><span data-stu-id="1f987-120">**CopyData**</span></span>  
 <span data-ttu-id="1f987-121">選取當物件從來源伺服器複製到目的地伺服器時是否包含資料。</span><span class="sxs-lookup"><span data-stu-id="1f987-121">Select whether data will be included when objects are copied from the source to the destination server.</span></span>  
  
 <span data-ttu-id="1f987-122">**ExistingData**</span><span class="sxs-lookup"><span data-stu-id="1f987-122">**ExistingData**</span></span>  
 <span data-ttu-id="1f987-123">指定如何將資料複製到目的地伺服器。</span><span class="sxs-lookup"><span data-stu-id="1f987-123">Specify how data will be copied to the destination server.</span></span> <span data-ttu-id="1f987-124">此屬性具有下表所列的選項：</span><span class="sxs-lookup"><span data-stu-id="1f987-124">This property has the options listed in the following table:</span></span>  
  
|<span data-ttu-id="1f987-125">值</span><span class="sxs-lookup"><span data-stu-id="1f987-125">Value</span></span>|<span data-ttu-id="1f987-126">描述</span><span class="sxs-lookup"><span data-stu-id="1f987-126">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1f987-127">**Replace**</span><span class="sxs-lookup"><span data-stu-id="1f987-127">**Replace**</span></span>|<span data-ttu-id="1f987-128">目的地伺服器上的資料會被覆寫。</span><span class="sxs-lookup"><span data-stu-id="1f987-128">Data on the destination server will be overwritten.</span></span>|  
|<span data-ttu-id="1f987-129">**Append**</span><span class="sxs-lookup"><span data-stu-id="1f987-129">**Append**</span></span>|<span data-ttu-id="1f987-130">從來源伺服器複製的資料會附加至目的地伺服器上的現有資料。</span><span class="sxs-lookup"><span data-stu-id="1f987-130">Data copied from the source server will be appended to existing data on the destination server.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="1f987-131">只有 [CopyData] 設定為 [True] 時，才能使用 [ExistingData] 選項。</span><span class="sxs-lookup"><span data-stu-id="1f987-131">The **ExistingData** option is only available when **CopyData** is set to **True**.</span></span>  
  
 <span data-ttu-id="1f987-132">**CopySchema**</span><span class="sxs-lookup"><span data-stu-id="1f987-132">**CopySchema**</span></span>  
 <span data-ttu-id="1f987-133">選取在傳送 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 物件工作期間是否複製結構描述。</span><span class="sxs-lookup"><span data-stu-id="1f987-133">Select whether the schema is copied during the Transfer [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Objects task.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1f987-134">**CopySchema** 只適用於 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="1f987-134">**CopySchema** is only available for [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="1f987-135">**UseCollation**</span><span class="sxs-lookup"><span data-stu-id="1f987-135">**UseCollation**</span></span>  
 <span data-ttu-id="1f987-136">選取物件的傳送是否應該包含在來源伺服器上所指定的定序。</span><span class="sxs-lookup"><span data-stu-id="1f987-136">Select whether the transfer of objects should include the collation specified on the source server.</span></span>  
  
 <span data-ttu-id="1f987-137">**IncludeDependentObjects**</span><span class="sxs-lookup"><span data-stu-id="1f987-137">**IncludeDependentObjects**</span></span>  
 <span data-ttu-id="1f987-138">選取複製所選取物件時是否要串聯，以包含相依於選取要複製之物件的其他物件。</span><span class="sxs-lookup"><span data-stu-id="1f987-138">Select whether copying the selected objects will cascade to include other objects that depend on the objects selected for copying.</span></span>  
  
 <span data-ttu-id="1f987-139">**CopyAllObjects**</span><span class="sxs-lookup"><span data-stu-id="1f987-139">**CopyAllObjects**</span></span>  
 <span data-ttu-id="1f987-140">選取工作會複製指定之來源資料庫中的所有物件，或僅複製選取的物件。</span><span class="sxs-lookup"><span data-stu-id="1f987-140">Select whether the task will copy all objects in the specified source database or only selected objects.</span></span>  <span data-ttu-id="1f987-141">將此選項設定為 False，可讓您選擇在 [CopyAllObjects]  區段中選取要傳送的物件以及顯示動態選項。</span><span class="sxs-lookup"><span data-stu-id="1f987-141">Setting this option to False gives you the option to select the objects to transfer, and displays the dynamic options in the section, **CopyAllObjects**.</span></span>  
  
 <span data-ttu-id="1f987-142">**ObjectsToCopy**</span><span class="sxs-lookup"><span data-stu-id="1f987-142">**ObjectsToCopy**</span></span>  
 <span data-ttu-id="1f987-143">展開 [ObjectsToCopy]  ，即可指定應從來源資料庫複製到目的地資料庫的物件。</span><span class="sxs-lookup"><span data-stu-id="1f987-143">Expand **ObjectsToCopy** to specify which objects should be copied from the source database to the destination database.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1f987-144">只有 **CopyAllObjects** 設定為 **False** 時，才能使用 **ObjectsToCopy**。</span><span class="sxs-lookup"><span data-stu-id="1f987-144">**ObjectsToCopy** is only available when **CopyAllObjects** is set to **False**.</span></span>  
  
 <span data-ttu-id="1f987-145">只有 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]才支援用來複製下列類型之物件的選項：</span><span class="sxs-lookup"><span data-stu-id="1f987-145">The options to copy the following types of objects are supported only on [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]:</span></span>  
  
 <span data-ttu-id="1f987-146">組件</span><span class="sxs-lookup"><span data-stu-id="1f987-146">Assemblies</span></span>  
  
 <span data-ttu-id="1f987-147">資料分割函數</span><span class="sxs-lookup"><span data-stu-id="1f987-147">Partition functions</span></span>  
  
 <span data-ttu-id="1f987-148">資料分割配置</span><span class="sxs-lookup"><span data-stu-id="1f987-148">Partition schemes</span></span>  
  
 <span data-ttu-id="1f987-149">結構描述</span><span class="sxs-lookup"><span data-stu-id="1f987-149">Schemas</span></span>  
  
 <span data-ttu-id="1f987-150">使用者自訂彙總</span><span class="sxs-lookup"><span data-stu-id="1f987-150">User-defined aggregates</span></span>  
  
 <span data-ttu-id="1f987-151">使用者定義型別</span><span class="sxs-lookup"><span data-stu-id="1f987-151">User-defined types</span></span>  
  
 <span data-ttu-id="1f987-152">XML 結構描述集合</span><span class="sxs-lookup"><span data-stu-id="1f987-152">XML schema collections</span></span>  
  
 <span data-ttu-id="1f987-153">**CopyDatabaseUsers**</span><span class="sxs-lookup"><span data-stu-id="1f987-153">**CopyDatabaseUsers**</span></span>  
 <span data-ttu-id="1f987-154">指定資料庫使用者是否應該包含在傳送中。</span><span class="sxs-lookup"><span data-stu-id="1f987-154">Specify whether database users should be included in the transfer.</span></span>  
  
 <span data-ttu-id="1f987-155">**CopyDatabaseRoles**</span><span class="sxs-lookup"><span data-stu-id="1f987-155">**CopyDatabaseRoles**</span></span>  
 <span data-ttu-id="1f987-156">指定資料庫角色是否應該包含在傳送中。</span><span class="sxs-lookup"><span data-stu-id="1f987-156">Specify whether database roles should be included in the transfer.</span></span>  
  
 <span data-ttu-id="1f987-157">**CopySqlServerLogins**</span><span class="sxs-lookup"><span data-stu-id="1f987-157">**CopySqlServerLogins**</span></span>  
 <span data-ttu-id="1f987-158">指定 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 登入是否應該包含在傳送中。</span><span class="sxs-lookup"><span data-stu-id="1f987-158">Specify whether [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] logins should be included in the transfer.</span></span>  
  
 <span data-ttu-id="1f987-159">**CopyObjectLevelPermissions**</span><span class="sxs-lookup"><span data-stu-id="1f987-159">**CopyObjectLevelPermissions**</span></span>  
 <span data-ttu-id="1f987-160">指定物件層級權限是否應該包含在傳送中。</span><span class="sxs-lookup"><span data-stu-id="1f987-160">Specify whether object-level permissions should be included in the transfer.</span></span>  
  
 <span data-ttu-id="1f987-161">**CopyIndexes**</span><span class="sxs-lookup"><span data-stu-id="1f987-161">**CopyIndexes**</span></span>  
 <span data-ttu-id="1f987-162">指定索引是否應該包含在傳送中。</span><span class="sxs-lookup"><span data-stu-id="1f987-162">Specify whether indexes should be included in the transfer.</span></span>  
  
 <span data-ttu-id="1f987-163">**CopyTriggers**</span><span class="sxs-lookup"><span data-stu-id="1f987-163">**CopyTriggers**</span></span>  
 <span data-ttu-id="1f987-164">指定觸發程序是否應該包含在傳送中。</span><span class="sxs-lookup"><span data-stu-id="1f987-164">Specify whether triggers should be included in the transfer.</span></span>  
  
 <span data-ttu-id="1f987-165">**CopyFullTextIndexes**</span><span class="sxs-lookup"><span data-stu-id="1f987-165">**CopyFullTextIndexes**</span></span>  
 <span data-ttu-id="1f987-166">指定全文檢索索引是否應該包含在傳送中。</span><span class="sxs-lookup"><span data-stu-id="1f987-166">Specify whether full-text indexes should be included in the transfer.</span></span>  
  
 <span data-ttu-id="1f987-167">**CopyPrimaryKeys**</span><span class="sxs-lookup"><span data-stu-id="1f987-167">**CopyPrimaryKeys**</span></span>  
 <span data-ttu-id="1f987-168">指定主索引鍵是否應包含在傳送中。</span><span class="sxs-lookup"><span data-stu-id="1f987-168">Specify whether primary keys should be included in the transfer.</span></span>  
  
 <span data-ttu-id="1f987-169">**CopyForeignKeys**</span><span class="sxs-lookup"><span data-stu-id="1f987-169">**CopyForeignKeys**</span></span>  
 <span data-ttu-id="1f987-170">指定外部索引鍵是否應該包含在傳送中。</span><span class="sxs-lookup"><span data-stu-id="1f987-170">Specify whether foreign keys should be included in the transfer.</span></span>  
  
 <span data-ttu-id="1f987-171">**GenerateScriptsInUnicode**</span><span class="sxs-lookup"><span data-stu-id="1f987-171">**GenerateScriptsInUnicode**</span></span>  
 <span data-ttu-id="1f987-172">指定產生的傳送指令碼是否為 Unicode 格式。</span><span class="sxs-lookup"><span data-stu-id="1f987-172">Specify whether the generated transfer scripts are in Unicode format.</span></span>  
  
## <a name="dynamic-options"></a><span data-ttu-id="1f987-173">動態選項</span><span class="sxs-lookup"><span data-stu-id="1f987-173">Dynamic Options</span></span>  
  
### <a name="copyallobjects--false"></a><span data-ttu-id="1f987-174">CopyAllObjects = False</span><span class="sxs-lookup"><span data-stu-id="1f987-174">CopyAllObjects = False</span></span>  
 <span data-ttu-id="1f987-175">**CopyAllTables**</span><span class="sxs-lookup"><span data-stu-id="1f987-175">**CopyAllTables**</span></span>  
 <span data-ttu-id="1f987-176">選取工作會複製指定之來源資料庫中的所有資料表，或僅複製選取的資料表。</span><span class="sxs-lookup"><span data-stu-id="1f987-176">Select whether the task will copy all tables in the specified source database or only the selected tables.</span></span>  
  
 <span data-ttu-id="1f987-177">**TablesList**</span><span class="sxs-lookup"><span data-stu-id="1f987-177">**TablesList**</span></span>  
 <span data-ttu-id="1f987-178">按一下即可開啟 [選取資料表]  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="1f987-178">Click to open the **Select Tables** dialog box.</span></span>  
  
 <span data-ttu-id="1f987-179">**CopyAllViews**</span><span class="sxs-lookup"><span data-stu-id="1f987-179">**CopyAllViews**</span></span>  
 <span data-ttu-id="1f987-180">選取工作會複製指定之來源資料庫中的所有檢視，或僅複製選取的檢視。</span><span class="sxs-lookup"><span data-stu-id="1f987-180">Select whether the task will copy all views in the specified source database or only the selected views.</span></span>  
  
 <span data-ttu-id="1f987-181">**ViewsList**</span><span class="sxs-lookup"><span data-stu-id="1f987-181">**ViewsList**</span></span>  
 <span data-ttu-id="1f987-182">按一下即可開啟 [選取檢視]  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="1f987-182">Click to open the **Select Views** dialog box.</span></span>  
  
 <span data-ttu-id="1f987-183">**CopyAllStoredProcedures**</span><span class="sxs-lookup"><span data-stu-id="1f987-183">**CopyAllStoredProcedures**</span></span>  
 <span data-ttu-id="1f987-184">選取工作會複製指定之來源資料庫中的所有使用者自訂預存程序，或僅複製選取的程序。</span><span class="sxs-lookup"><span data-stu-id="1f987-184">Select whether the task will copy all user-defined stored procedures in the specified source database or only the selected procedures.</span></span>  
  
 <span data-ttu-id="1f987-185">**StoredProceduresList**</span><span class="sxs-lookup"><span data-stu-id="1f987-185">**StoredProceduresList**</span></span>  
 <span data-ttu-id="1f987-186">按一下即可開啟 [選取預存程序]  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="1f987-186">Click to open the **Select Stored Procedures** dialog box.</span></span>  
  
 <span data-ttu-id="1f987-187">**CopyAllUserDefinedFunctions**</span><span class="sxs-lookup"><span data-stu-id="1f987-187">**CopyAllUserDefinedFunctions**</span></span>  
 <span data-ttu-id="1f987-188">選取工作會複製指定之來源資料庫中的所有使用者自訂函數，或僅複製選取的 UDF。</span><span class="sxs-lookup"><span data-stu-id="1f987-188">Select whether the task will copy all user-defined functions in the specified source database or only the selected UDFs.</span></span>  
  
 <span data-ttu-id="1f987-189">**UserDefinedFunctionsList**</span><span class="sxs-lookup"><span data-stu-id="1f987-189">**UserDefinedFunctionsList**</span></span>  
 <span data-ttu-id="1f987-190">按一下即可開啟 [選取使用者自訂函數]  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="1f987-190">Click to open the **Select User Defined Functions** dialog box.</span></span>  
  
 <span data-ttu-id="1f987-191">**CopyAllDefaults**</span><span class="sxs-lookup"><span data-stu-id="1f987-191">**CopyAllDefaults**</span></span>  
 <span data-ttu-id="1f987-192">選取工作會複製指定之來源資料庫中的所有預設值，或僅複製選取的預設值。</span><span class="sxs-lookup"><span data-stu-id="1f987-192">Select whether the task will copy all defaults in the specified source database or only the selected defaults.</span></span>  
  
 <span data-ttu-id="1f987-193">**DefaultsList**</span><span class="sxs-lookup"><span data-stu-id="1f987-193">**DefaultsList**</span></span>  
 <span data-ttu-id="1f987-194">按一下即可開啟 [選取預設值]  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="1f987-194">Click to open the **Select Defaults** dialog box.</span></span>  
  
 <span data-ttu-id="1f987-195">**CopyAllUserDefinedDataTypes**</span><span class="sxs-lookup"><span data-stu-id="1f987-195">**CopyAllUserDefinedDataTypes**</span></span>  
 <span data-ttu-id="1f987-196">選取工作會複製指定之來源資料庫中的所有使用者自訂資料類型，或僅複製選取的使用者自訂資料類型。</span><span class="sxs-lookup"><span data-stu-id="1f987-196">Select whether the task will copy all user-defined data types in the specified source database or only the selected user-defined data types.</span></span>  
  
 <span data-ttu-id="1f987-197">**UserDefinedDataTypesList**</span><span class="sxs-lookup"><span data-stu-id="1f987-197">**UserDefinedDataTypesList**</span></span>  
 <span data-ttu-id="1f987-198">按一下即可開啟 [選取使用者自訂資料類型]  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="1f987-198">Click to open the **Select User-Defined Data Types** dialog box.</span></span>  
  
 <span data-ttu-id="1f987-199">**CopyAllPartitionFunctions**</span><span class="sxs-lookup"><span data-stu-id="1f987-199">**CopyAllPartitionFunctions**</span></span>  
 <span data-ttu-id="1f987-200">選取工作會複製指定之來源資料庫中的所有使用者自訂資料分割函數，或僅複製選取的資料分割函數。</span><span class="sxs-lookup"><span data-stu-id="1f987-200">Select whether the task will copy all user-defined partition functions in the specified source database or only the selected partition functions.</span></span> <span data-ttu-id="1f987-201">只有 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]才支援。</span><span class="sxs-lookup"><span data-stu-id="1f987-201">Supported only on [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="1f987-202">**PartitionFunctionsList**</span><span class="sxs-lookup"><span data-stu-id="1f987-202">**PartitionFunctionsList**</span></span>  
 <span data-ttu-id="1f987-203">按一下即可開啟 [選取資料分割函數]  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="1f987-203">Click to open the **Select Partition Functions** dialog box.</span></span>  
  
 <span data-ttu-id="1f987-204">**CopyAllPartitionSchemes**</span><span class="sxs-lookup"><span data-stu-id="1f987-204">**CopyAllPartitionSchemes**</span></span>  
 <span data-ttu-id="1f987-205">選取工作會複製指定之來源資料庫中的所有資料分割配置，或僅複製選取的資料分割配置。</span><span class="sxs-lookup"><span data-stu-id="1f987-205">Select whether the task will copy all partition schemes in the specified source database or only the selected partition schemes.</span></span> <span data-ttu-id="1f987-206">只有 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]才支援。</span><span class="sxs-lookup"><span data-stu-id="1f987-206">Supported only on [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="1f987-207">**PartitionSchemesList**</span><span class="sxs-lookup"><span data-stu-id="1f987-207">**PartitionSchemesList**</span></span>  
 <span data-ttu-id="1f987-208">按一下即可開啟 [選取資料分割配置]  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="1f987-208">Click to open the **Select Partition Schemes** dialog box.</span></span>  
  
 <span data-ttu-id="1f987-209">**CopyAllSchemas**</span><span class="sxs-lookup"><span data-stu-id="1f987-209">**CopyAllSchemas**</span></span>  
 <span data-ttu-id="1f987-210">選取工作會複製指定之來源資料庫中的所有結構描述，或僅複製選取的結構描述。</span><span class="sxs-lookup"><span data-stu-id="1f987-210">Select whether the task will copy all schemas in the specified source database or only the selected schemas.</span></span> <span data-ttu-id="1f987-211">只有 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]才支援。</span><span class="sxs-lookup"><span data-stu-id="1f987-211">Supported only on [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="1f987-212">**SchemasList**</span><span class="sxs-lookup"><span data-stu-id="1f987-212">**SchemasList**</span></span>  
 <span data-ttu-id="1f987-213">按一下即可開啟 [選取結構描述]  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="1f987-213">Click to open the **Select Schemas** dialog box.</span></span>  
  
 <span data-ttu-id="1f987-214">**CopyAllSqlAssemblies**</span><span class="sxs-lookup"><span data-stu-id="1f987-214">**CopyAllSqlAssemblies**</span></span>  
 <span data-ttu-id="1f987-215">選取工作會複製指定之來源資料庫中的所有 SQL 組件，或僅複製選取的 SQL 組件。</span><span class="sxs-lookup"><span data-stu-id="1f987-215">Select whether the task will copy all SQL assemblies in the specified source database or only the selected SQL assemblies.</span></span> <span data-ttu-id="1f987-216">只有 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]才支援。</span><span class="sxs-lookup"><span data-stu-id="1f987-216">Supported only on [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="1f987-217">**SqlAssembliesList**</span><span class="sxs-lookup"><span data-stu-id="1f987-217">**SqlAssembliesList**</span></span>  
 <span data-ttu-id="1f987-218">按一下即可開啟 [選取 SQL 組件]  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="1f987-218">Click to open the **Select SQL Assemblies** dialog box.</span></span>  
  
 <span data-ttu-id="1f987-219">**CopyAllUserDefinedAggregates**</span><span class="sxs-lookup"><span data-stu-id="1f987-219">**CopyAllUserDefinedAggregates**</span></span>  
 <span data-ttu-id="1f987-220">選取工作會複製指定之來源資料庫中的所有使用者自訂彙總，或僅複製選取的使用者自訂彙總。</span><span class="sxs-lookup"><span data-stu-id="1f987-220">Select whether the task will copy all user-defined aggregates in the specified source database or only the selected user-defined aggregates.</span></span> <span data-ttu-id="1f987-221">只有 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]才支援。</span><span class="sxs-lookup"><span data-stu-id="1f987-221">Supported only on [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="1f987-222">**UserDefinedAggregatesList**</span><span class="sxs-lookup"><span data-stu-id="1f987-222">**UserDefinedAggregatesList**</span></span>  
 <span data-ttu-id="1f987-223">按一下即可開啟 [選取使用者自訂彙總]  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="1f987-223">Click to open the **Select User-Defined Aggregates** dialog box.</span></span>  
  
 <span data-ttu-id="1f987-224">**CopyAllUserDefinedTypes**</span><span class="sxs-lookup"><span data-stu-id="1f987-224">**CopyAllUserDefinedTypes**</span></span>  
 <span data-ttu-id="1f987-225">選取工作會複製指定之來源資料庫中的所有使用者定義型別，或僅複製選取的 UDT。</span><span class="sxs-lookup"><span data-stu-id="1f987-225">Select whether the task will copy all user-defined types in the specified source database or only the selected UDTs.</span></span> <span data-ttu-id="1f987-226">只有 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]才支援。</span><span class="sxs-lookup"><span data-stu-id="1f987-226">Supported only on [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="1f987-227">**UserDefinedTypes**</span><span class="sxs-lookup"><span data-stu-id="1f987-227">**UserDefinedTypes**</span></span>  
 <span data-ttu-id="1f987-228">按一下即可開啟 [選取使用者定義型別]  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="1f987-228">Click to open the **Select User-Defined Types** dialog box.</span></span>  
  
 <span data-ttu-id="1f987-229">**CopyAllXmlSchemaCollections**</span><span class="sxs-lookup"><span data-stu-id="1f987-229">**CopyAllXmlSchemaCollections**</span></span>  
 <span data-ttu-id="1f987-230">選取工作會複製指定之來源資料庫中的所有 XML 結構描述集合，或僅複製選取的 XML 結構描述集合。</span><span class="sxs-lookup"><span data-stu-id="1f987-230">Select whether the task will copy all XML Schema collections in the specified source database or only the selected XML schema collections.</span></span> <span data-ttu-id="1f987-231">只有 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]才支援。</span><span class="sxs-lookup"><span data-stu-id="1f987-231">Supported only on [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="1f987-232">**XmlSchemaCollectionsList**</span><span class="sxs-lookup"><span data-stu-id="1f987-232">**XmlSchemaCollectionsList**</span></span>  
 <span data-ttu-id="1f987-233">按一下即可開啟 [選取 XML 結構描述集合]  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="1f987-233">Click to open the **Select XML Schema Collections** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f987-234">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1f987-234">See Also</span></span>  
 <span data-ttu-id="1f987-235">[Integration Services 錯誤和訊息參考](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="1f987-235">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="1f987-236">[Integration Services 工作](control-flow/integration-services-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="1f987-236">[Integration Services Tasks](control-flow/integration-services-tasks.md) </span></span>  
 <span data-ttu-id="1f987-237">[傳送 SQL Server 物件工作編輯器 &#40;一般頁面&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="1f987-237">[Transfer SQL Server Objects Task Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="1f987-238">[運算式頁面](expressions/expressions-page.md) </span><span class="sxs-lookup"><span data-stu-id="1f987-238">[Expressions Page](expressions/expressions-page.md) </span></span>  
 <span data-ttu-id="1f987-239">[大量匯入或大量匯出的資料格式 &#40;SQL Server&#41;](../relational-databases/import-export/data-formats-for-bulk-import-or-bulk-export-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="1f987-239">[Data Formats for Bulk Import or Bulk Export &#40;SQL Server&#41;](../relational-databases/import-export/data-formats-for-bulk-import-or-bulk-export-sql-server.md) </span></span>  
 [<span data-ttu-id="1f987-240">SQL Server 安裝的安全性考量</span><span class="sxs-lookup"><span data-stu-id="1f987-240">Security Considerations for a SQL Server Installation</span></span>](../../2014/sql-server/install/security-considerations-for-a-sql-server-installation.md)  
  
  
