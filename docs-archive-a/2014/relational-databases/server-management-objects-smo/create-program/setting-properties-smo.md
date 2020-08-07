---
title: 設定屬性 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SMO [SQL Server], properties
- SQL Server Management Objects, properties
- properties [SMO]
ms.assetid: 342569ba-d2f7-44d2-8f3f-ae9c701c7f0f
author: stevestein
ms.author: sstein
ms.openlocfilehash: de381f8e4e9dfe9f6590638742e988f866ccabdc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704009"
---
# <a name="setting-properties"></a><span data-ttu-id="11798-102">設定屬性</span><span class="sxs-lookup"><span data-stu-id="11798-102">Setting Properties</span></span>
  <span data-ttu-id="11798-103">屬性是儲存有關物件之描述性資訊的值。</span><span class="sxs-lookup"><span data-stu-id="11798-103">Properties are values that store descriptive information about the object.</span></span> <span data-ttu-id="11798-104">例如，設定 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 選項會以 <xref:Microsoft.SqlServer.Management.Smo.Server.Configuration%2A> 物件的屬性來表示。</span><span class="sxs-lookup"><span data-stu-id="11798-104">For example, [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] configuration options are represented by the <xref:Microsoft.SqlServer.Management.Smo.Server.Configuration%2A> object's properties.</span></span> <span data-ttu-id="11798-105">您可以使用屬性集合來直接或間接地存取屬性。</span><span class="sxs-lookup"><span data-stu-id="11798-105">Properties can be accessed either directly or indirectly by using the property collection.</span></span> <span data-ttu-id="11798-106">直接存取屬性會使用下列語法：</span><span class="sxs-lookup"><span data-stu-id="11798-106">Accessing properties directly uses the following syntax:</span></span>  
  
 `objInstance.PropertyName`  
  
 <span data-ttu-id="11798-107">您可以根據屬性是否具有讀/寫存取權或唯讀存取權來修改或擷取屬性值。</span><span class="sxs-lookup"><span data-stu-id="11798-107">A property value can be modified or retrieved depending on whether the property has read/write access or read-only access.</span></span> <span data-ttu-id="11798-108">也必須先設定特定的屬性，才能建立物件。</span><span class="sxs-lookup"><span data-stu-id="11798-108">It is also necessary to set certain properties before an object can be created.</span></span> <span data-ttu-id="11798-109">如需詳細資訊，請參閱該特定物件的 SMO 參考。</span><span class="sxs-lookup"><span data-stu-id="11798-109">For more information, see the SMO reference for the particular object.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="11798-110">子物件的集合會顯示為物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="11798-110">Collections of child objects appear as the property of an object.</span></span> <span data-ttu-id="11798-111">例如，`Tables` 集合是 `Server` 物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="11798-111">For example, the `Tables` collection is a property of a `Server` object.</span></span> <span data-ttu-id="11798-112">如需詳細資訊，請參閱 [Using Collections](using-collections.md)。</span><span class="sxs-lookup"><span data-stu-id="11798-112">For more information, see [Using Collections](using-collections.md).</span></span>  
  
 <span data-ttu-id="11798-113">物件的屬性是 Properties 集合的成員。</span><span class="sxs-lookup"><span data-stu-id="11798-113">The properties of an object are members of the Properties collection.</span></span> <span data-ttu-id="11798-114">Properties 集合可用來反覆運算物件的每個屬性。</span><span class="sxs-lookup"><span data-stu-id="11798-114">The Properties collection can be used to iterate through every property of an object.</span></span>  
  
 <span data-ttu-id="11798-115">有時屬性會因為下列原因而無法使用：</span><span class="sxs-lookup"><span data-stu-id="11798-115">Sometimes a property is not available for the following reasons:</span></span>  
  
-   <span data-ttu-id="11798-116">伺服器版本不支援該屬性，例如您在舊版的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 上嘗試存取的屬性代表新增的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]功能。</span><span class="sxs-lookup"><span data-stu-id="11798-116">The server version does not support the property, such as if you try to access a property that represents a new [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] feature on an older version of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="11798-117">伺服器沒有提供該屬性的資料，例如您嘗試存取的屬性代表未安裝的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 元件。</span><span class="sxs-lookup"><span data-stu-id="11798-117">The server does not provide data for the property, such as if you try to access a property that represents a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] component that is not installed.</span></span>  
  
 <span data-ttu-id="11798-118">您可以藉由捕捉 <xref:Microsoft.SqlServer.Management.Smo.UnknownPropertyException> 和 <xref:Microsoft.SqlServer.Management.Smo.PropertyCannotBeRetrievedException> SMO 例外狀況來處理這些情況。</span><span class="sxs-lookup"><span data-stu-id="11798-118">You can handle these circumstances by catching the <xref:Microsoft.SqlServer.Management.Smo.UnknownPropertyException> and the <xref:Microsoft.SqlServer.Management.Smo.PropertyCannotBeRetrievedException> SMO exceptions.</span></span>  
  
## <a name="setting-default-initialization-fields"></a><span data-ttu-id="11798-119">設定預設的初始化欄位</span><span class="sxs-lookup"><span data-stu-id="11798-119">Setting Default Initialization Fields</span></span>  
 <span data-ttu-id="11798-120">SMO 在擷取物件時會執行最佳化。</span><span class="sxs-lookup"><span data-stu-id="11798-120">SMO performs an optimization when retrieving objects.</span></span> <span data-ttu-id="11798-121">最佳化會藉由在下列狀況之間自動調整，而將載入的屬性數目最小化：</span><span class="sxs-lookup"><span data-stu-id="11798-121">The optimization minimizes the number of properties loaded by automatically scaling between the following states:</span></span>  
  
1.  <span data-ttu-id="11798-122">部分載入。</span><span class="sxs-lookup"><span data-stu-id="11798-122">Partially loaded.</span></span> <span data-ttu-id="11798-123">初次參考物件時，該物件會擁有最少的可用屬性 (例如「名稱」和「結構描述」)。</span><span class="sxs-lookup"><span data-stu-id="11798-123">When an object is first referenced it has a minimum of properties available (such as Name and Schema).</span></span>  
  
2.  <span data-ttu-id="11798-124">完整載入。</span><span class="sxs-lookup"><span data-stu-id="11798-124">Fully loaded.</span></span> <span data-ttu-id="11798-125">在參考任何屬性時，系統會初始化可快速載入的剩餘屬性並使這些屬性可供使用。</span><span class="sxs-lookup"><span data-stu-id="11798-125">When any property is referenced, the remaining properties that are quick to load, are initialized and are made available.</span></span>  
  
3.  <span data-ttu-id="11798-126">使用大量記憶體的屬性。</span><span class="sxs-lookup"><span data-stu-id="11798-126">Properties that use lots of memory.</span></span> <span data-ttu-id="11798-127">不可使用的剩餘屬性會使用許多記憶體，並具有 true 的 <xref:Microsoft.SqlServer.Management.Smo.Property.Expensive%2A> 屬性值 (例如，<xref:Microsoft.SqlServer.Management.Smo.Database.DataSpaceUsage%2A>)。</span><span class="sxs-lookup"><span data-stu-id="11798-127">The remaining unavailable properties use lots of memory and have an <xref:Microsoft.SqlServer.Management.Smo.Property.Expensive%2A> property value of true (such as <xref:Microsoft.SqlServer.Management.Smo.Database.DataSpaceUsage%2A>).</span></span> <span data-ttu-id="11798-128">這些屬性只有在特別參考時才會載入。</span><span class="sxs-lookup"><span data-stu-id="11798-128">These properties are loaded only when specifically referenced.</span></span>  
  
 <span data-ttu-id="11798-129">如果您的應用程式真的會擷取額外的屬性，則除了以部分載入狀態提供的屬性外，該應用程式還會提交查詢以擷取這些額外的屬性，並擴充至完全載入的狀態。</span><span class="sxs-lookup"><span data-stu-id="11798-129">If your application does fetch extra properties, besides the ones provided in the partially loaded state, it submits a query to retrieve these extra properties and scales up to the fully loaded state.</span></span> <span data-ttu-id="11798-130">這樣可能會造成用戶端和伺服器之間出現不必要的傳輸。</span><span class="sxs-lookup"><span data-stu-id="11798-130">This can cause unnecessary traffic between the client and server.</span></span> <span data-ttu-id="11798-131">呼叫 <xref:Microsoft.SqlServer.Management.Smo.Server.SetDefaultInitFields%2A> 方法可以達到更高的最佳化。</span><span class="sxs-lookup"><span data-stu-id="11798-131">More optimization can be achieved by calling the <xref:Microsoft.SqlServer.Management.Smo.Server.SetDefaultInitFields%2A> method.</span></span> <span data-ttu-id="11798-132"><xref:Microsoft.SqlServer.Management.Smo.Server.SetDefaultInitFields%2A> 方法可用來指定在物件初始化時載入的屬性。</span><span class="sxs-lookup"><span data-stu-id="11798-132">The <xref:Microsoft.SqlServer.Management.Smo.Server.SetDefaultInitFields%2A> method allows specification of the properties that are loaded when the object is initialized.</span></span>  
  
 <span data-ttu-id="11798-133"><xref:Microsoft.SqlServer.Management.Smo.Server.SetDefaultInitFields%2A> 方法會針對其餘的應用程式設定屬性載入行為，或等到應用程式重設為止。</span><span class="sxs-lookup"><span data-stu-id="11798-133">The <xref:Microsoft.SqlServer.Management.Smo.Server.SetDefaultInitFields%2A> method sets the property loading behavior for the rest of application or until it is reset.</span></span> <span data-ttu-id="11798-134">您可以使用 <xref:Microsoft.SqlServer.Management.Smo.Server.GetDefaultInitFields%2A> 方法來儲存原始的行為，並依需求加以還原。</span><span class="sxs-lookup"><span data-stu-id="11798-134">You can save the original behavior by using the <xref:Microsoft.SqlServer.Management.Smo.Server.GetDefaultInitFields%2A> method and restore it as required.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="11798-135">範例</span><span class="sxs-lookup"><span data-stu-id="11798-135">Examples</span></span>  
 [!INCLUDE[ssChooseProgEnv](../../../includes/sschooseprogenv-md.md)]  
  
## <a name="getting-and-setting-a-property-in-visual-basic"></a><span data-ttu-id="11798-136">在 Visual Basic 中取得和設定屬性</span><span class="sxs-lookup"><span data-stu-id="11798-136">Getting and Setting a Property in Visual Basic</span></span>  
 <span data-ttu-id="11798-137">此程式碼範例示範如何取得 <xref:Microsoft.SqlServer.Management.Smo.Information.Edition%2A> 物件的 <xref:Microsoft.SqlServer.Management.Smo.Information> 屬性，以及如何將 <xref:Microsoft.SqlServer.Management.Common.ServerConnection.SqlExecutionModes%2A> 屬性的 <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A> 屬性設定為 <xref:Microsoft.SqlServer.Management.Common.SqlExecutionModes> 列舉型別的 `ExecuteSql` 成員。</span><span class="sxs-lookup"><span data-stu-id="11798-137">This code example shows how to get the <xref:Microsoft.SqlServer.Management.Smo.Information.Edition%2A> property of the <xref:Microsoft.SqlServer.Management.Smo.Information> object and how to set the <xref:Microsoft.SqlServer.Management.Common.ServerConnection.SqlExecutionModes%2A> property of the <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A> property to the `ExecuteSql` member of the <xref:Microsoft.SqlServer.Management.Common.SqlExecutionModes> enumerated type.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBProperties1](SMO How to#SMO_VBProperties1)]  -->  
  
## <a name="getting-and-setting-a-property-in-visual-c"></a><span data-ttu-id="11798-138">在 Visual C# 中取得和設定屬性</span><span class="sxs-lookup"><span data-stu-id="11798-138">Getting and Setting a Property in Visual C#</span></span>  
 <span data-ttu-id="11798-139">此程式碼範例示範如何取得 <xref:Microsoft.SqlServer.Management.Smo.Information.Edition%2A> 物件的 <xref:Microsoft.SqlServer.Management.Smo.Information> 屬性，以及如何將 <xref:Microsoft.SqlServer.Management.Common.ServerConnection.SqlExecutionModes%2A> 屬性的 <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A> 屬性設定為 <xref:Microsoft.SqlServer.Management.Common.SqlExecutionModes> 列舉型別的 `ExecuteSql` 成員。</span><span class="sxs-lookup"><span data-stu-id="11798-139">This code example shows how to get the <xref:Microsoft.SqlServer.Management.Smo.Information.Edition%2A> property of the <xref:Microsoft.SqlServer.Management.Smo.Information> object and how to set the <xref:Microsoft.SqlServer.Management.Common.ServerConnection.SqlExecutionModes%2A> property of the <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A> property to the `ExecuteSql` member of the <xref:Microsoft.SqlServer.Management.Common.SqlExecutionModes> enumerated type.</span></span>  
  
```  
{   
//Connect to the local, default instance of SQL Server.   
Server srv;   
srv = new Server();   
//Get a property.   
Console.WriteLine(srv.Information.Version);   
//Set a property.   
srv.ConnectionContext.SqlExecutionModes = SqlExecutionModes.ExecuteSql;   
}  
```  
  
## <a name="setting-various-properties-before-an-object-is-created-in-visual-basic"></a><span data-ttu-id="11798-140">在 Visual Basic 中建立物件之前先設定各種屬性</span><span class="sxs-lookup"><span data-stu-id="11798-140">Setting Various Properties Before an Object is Created in Visual Basic</span></span>  
 <span data-ttu-id="11798-141">此程式碼範例示範如何直接設定 <xref:Microsoft.SqlServer.Management.Smo.Table.AnsiNullsStatus%2A> 物件的 <xref:Microsoft.SqlServer.Management.Smo.Table> 屬性，以及如何在建立 <xref:Microsoft.SqlServer.Management.Smo.Table> 物件之前，先建立和加入資料行。</span><span class="sxs-lookup"><span data-stu-id="11798-141">This code example shows how to directly set the <xref:Microsoft.SqlServer.Management.Smo.Table.AnsiNullsStatus%2A> property of the <xref:Microsoft.SqlServer.Management.Smo.Table> object, and how to create and add columns before you create the <xref:Microsoft.SqlServer.Management.Smo.Table> object.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBProperties2](SMO How to#SMO_VBProperties2)]  -->  
  
## <a name="setting-various-properties-before-an-object-is-created-in-visual-c"></a><span data-ttu-id="11798-142">在 Visual C# 中建立物件之前先設定各種屬性</span><span class="sxs-lookup"><span data-stu-id="11798-142">Setting Various Properties Before an Object is Created in Visual C#</span></span>  
 <span data-ttu-id="11798-143">此程式碼範例示範如何直接設定 <xref:Microsoft.SqlServer.Management.Smo.Table.AnsiNullsStatus%2A> 物件的 <xref:Microsoft.SqlServer.Management.Smo.Table> 屬性，以及如何在建立 <xref:Microsoft.SqlServer.Management.Smo.Table> 物件之前，先建立和加入資料行。</span><span class="sxs-lookup"><span data-stu-id="11798-143">This code example shows how to directly set the <xref:Microsoft.SqlServer.Management.Smo.Table.AnsiNullsStatus%2A> property of the <xref:Microsoft.SqlServer.Management.Smo.Table> object, and how to create and add columns before you create the <xref:Microsoft.SqlServer.Management.Smo.Table> object.</span></span>  
  
```  
{   
//Connect to the local, default instance of SQL Server.   
Server srv;   
srv = new Server();   
//Create a new table in the AdventureWorks2012 database.   
Database db;   
db = srv.Databases("AdventureWorks2012");   
Table tb;   
//Specify the parent database, table schema, and the table name in the constructor.   
tb = new Table(db, "Test_Table", "HumanResources");   
//Add columns because the table requires columns before it can be created.   
Column c1;   
//Specify the parent table, the column name, and data type in the constructor.   
c1 = new Column(tb, "ID", DataType.Int);   
tb.Columns.Add(c1);   
c1.Nullable = false;   
c1.Identity = true;   
c1.IdentityIncrement = 1;   
c1.IdentitySeed = 0;   
Column c2;   
c2 = new Column(tb, "Name", DataType.NVarChar(100));   
c2.Nullable = false;   
tb.Columns.Add(c2);   
tb.AnsiNullsStatus = true;   
//Create the table on the instance of SQL Server.   
tb.Create();   
}  
```  
  
## <a name="iterating-through-all-properties-of-an-object-in-visual-basic"></a><span data-ttu-id="11798-144">在 Visual Basic 中反覆運算物件的所有屬性</span><span class="sxs-lookup"><span data-stu-id="11798-144">Iterating Through All Properties of an Object in Visual Basic</span></span>  
 <span data-ttu-id="11798-145">此程式碼範例會反覆運算 <xref:Microsoft.SqlServer.Management.Smo.StoredProcedure> 物件的 `Properties` 集合，並在 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 輸出畫面上加以顯示。</span><span class="sxs-lookup"><span data-stu-id="11798-145">This code example iterates through the `Properties` collection of the <xref:Microsoft.SqlServer.Management.Smo.StoredProcedure> object and displays them on the [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Output screen.</span></span>  
  
 <span data-ttu-id="11798-146">在此範例中已將 <xref:Microsoft.SqlServer.Management.Smo.Property> 物件放入方括號中，因為它也是 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="11798-146">In the example, the <xref:Microsoft.SqlServer.Management.Smo.Property> object has been put in square parentheses because it is also a [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] keyword.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBProperties3](SMO How to#SMO_VBProperties3)]  -->  
  
## <a name="iterating-through-all-properties-of-an-object-in-visual-c"></a><span data-ttu-id="11798-147">在 Visual C# 中反覆運算物件的所有屬性</span><span class="sxs-lookup"><span data-stu-id="11798-147">Iterating Through All Properties of an Object in Visual C#</span></span>  
 <span data-ttu-id="11798-148">此程式碼範例會反覆運算 <xref:Microsoft.SqlServer.Management.Smo.StoredProcedure> 物件的 `Properties` 集合，並在 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 輸出畫面上加以顯示。</span><span class="sxs-lookup"><span data-stu-id="11798-148">This code example iterates through the `Properties` collection of the <xref:Microsoft.SqlServer.Management.Smo.StoredProcedure> object and displays them on the [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Output screen.</span></span>  
  
```  
{   
//Connect to the local, default instance of SQL Server.   
Server srv;   
srv = new Server();   
//Set properties on the uspGetEmployeedManagers stored procedure on the AdventureWorks2012 database.   
Database db;   
db = srv.Databases("AdventureWorks2012");   
StoredProcedure sp;   
sp = db.StoredProcedures("uspGetEmployeeManagers");   
sp.AnsiNullsStatus = false;   
sp.QuotedIdentifierStatus = false;   
//Iterate through the properties of the stored procedure and display.   
  Property p;   
  foreach ( p in sp.Properties) {   
    Console.WriteLine(p.Name + p.Value);   
  }   
}  
```  
  
## <a name="setting-default-initialization-fields-in-visual-basic"></a><span data-ttu-id="11798-149">在 Visual Basic 中設定預設的初始化欄位</span><span class="sxs-lookup"><span data-stu-id="11798-149">Setting Default Initialization Fields in Visual Basic</span></span>  
 <span data-ttu-id="11798-150">此程式碼範例示範如何將在 SMO 程式中初始化的物件屬性數目最小化。</span><span class="sxs-lookup"><span data-stu-id="11798-150">This code example shows how to minimize the number of object properties initialized in an SMO program.</span></span> <span data-ttu-id="11798-151">您必須包含 `using System.Collections.Specialized`，即使用 <xref:System.Collections.Specialized.StringCollection> 物件的陳述式。</span><span class="sxs-lookup"><span data-stu-id="11798-151">You have to include the `using System.Collections.Specialized`; statement to use the <xref:System.Collections.Specialized.StringCollection> object.</span></span>  
  
 [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] <span data-ttu-id="11798-152">可用來將此最佳化與傳送至 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體的數字陳述式進行比較。</span><span class="sxs-lookup"><span data-stu-id="11798-152">can be used to compare the number statements sent to the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] with this optimization.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBDefaultInitFields1](SMO How to#SMO_VBDefaultInitFields1)]  -->  
  
## <a name="setting-default-initialization-fields-in-visual-c"></a><span data-ttu-id="11798-153">在 Visual C# 中設定預設的初始化欄位</span><span class="sxs-lookup"><span data-stu-id="11798-153">Setting Default Initialization Fields in Visual C#</span></span>  
 <span data-ttu-id="11798-154">此程式碼範例示範如何將在 SMO 程式中初始化的物件屬性數目最小化。</span><span class="sxs-lookup"><span data-stu-id="11798-154">This code example shows how to minimize the number of object properties initialized in an SMO program.</span></span> <span data-ttu-id="11798-155">您必須包含 `using System.Collections.Specialized`，即使用 <xref:System.Collections.Specialized.StringCollection> 物件的陳述式。</span><span class="sxs-lookup"><span data-stu-id="11798-155">You have to include the `using System.Collections.Specialized`; statement to use the <xref:System.Collections.Specialized.StringCollection> object.</span></span>  
  
 [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] <span data-ttu-id="11798-156">可用來將此最佳化與傳送至 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體的數字陳述式進行比較。</span><span class="sxs-lookup"><span data-stu-id="11798-156">can be used to compare the number statements sent to the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] with this optimization.</span></span>  
  
```  
{   
//Connect to the local, default instance of SQL Server.   
Server srv;   
srv = new Server();   
//Reference the AdventureWorks2012 database.   
Database db;   
db = srv.Databases("AdventureWorks2012");   
//Assign the Table object type to a System.Type object variable.   
Table tb;   
Type typ;   
tb = new Table();   
typ = tb.GetType;   
//Assign the current default initialization fields for the Table object type to a   
//StringCollection object variable.   
StringCollection sc;   
sc = srv.GetDefaultInitFields(typ);   
//Set the default initialization fields for the Table object type to the CreateDate property.   
srv.SetDefaultInitFields(typ, "CreateDate");   
//Retrieve the Schema, Name, and CreateDate properties for every table in AdventureWorks2012.   
   //Note that the improvement in performance can be viewed in SQL Server Profiler.   
foreach ( tb in db.Tables) {   
   Console.WriteLine(tb.Schema + "." + tb.Name + " " + tb.CreateDate);   
}   
//Set the default initialization fields for the Table object type back to the original settings.   
srv.SetDefaultInitFields(typ, sc);   
}  
```  
  
  
