---
title: 建立和改變 (XMLA) 的物件 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- objects [XML for Analysis]
- subordinate objects [XML for Analysis]
- XML for Analysis, objects
- modifying objects
- removing objects
- deleting objects
- XMLA, objects
ms.assetid: a2080867-e130-440c-92eb-f768869f34a8
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2390c0b921368e7e06f0e5563a7eb59769d99c17
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599238"
---
# <a name="creating-and-altering-objects-xmla"></a><span data-ttu-id="4b787-102">建立和改變物件 (XMLA)</span><span class="sxs-lookup"><span data-stu-id="4b787-102">Creating and Altering Objects (XMLA)</span></span>
  <span data-ttu-id="4b787-103">主要物件可以獨立建立、改變和刪除。</span><span class="sxs-lookup"><span data-stu-id="4b787-103">Major objects can be independently created, altered, and deleted.</span></span> <span data-ttu-id="4b787-104">主要物件包括下列物件：</span><span class="sxs-lookup"><span data-stu-id="4b787-104">Major objects include the following objects:</span></span>  
  
-   <span data-ttu-id="4b787-105">伺服器</span><span class="sxs-lookup"><span data-stu-id="4b787-105">Servers</span></span>  
  
-   <span data-ttu-id="4b787-106">資料庫</span><span class="sxs-lookup"><span data-stu-id="4b787-106">Databases</span></span>  
  
-   <span data-ttu-id="4b787-107">維度</span><span class="sxs-lookup"><span data-stu-id="4b787-107">Dimensions</span></span>  
  
-   <span data-ttu-id="4b787-108">Cube</span><span class="sxs-lookup"><span data-stu-id="4b787-108">Cubes</span></span>  
  
-   <span data-ttu-id="4b787-109">量值群組</span><span class="sxs-lookup"><span data-stu-id="4b787-109">Measure groups</span></span>  
  
-   <span data-ttu-id="4b787-110">資料分割</span><span class="sxs-lookup"><span data-stu-id="4b787-110">Partitions</span></span>  
  
-   <span data-ttu-id="4b787-111">檢視方塊</span><span class="sxs-lookup"><span data-stu-id="4b787-111">Perspectives</span></span>  
  
-   <span data-ttu-id="4b787-112">採礦模型</span><span class="sxs-lookup"><span data-stu-id="4b787-112">Mining models</span></span>  
  
-   <span data-ttu-id="4b787-113">角色</span><span class="sxs-lookup"><span data-stu-id="4b787-113">Roles</span></span>  
  
-   <span data-ttu-id="4b787-114">與伺服器或資料庫相關聯的命令</span><span class="sxs-lookup"><span data-stu-id="4b787-114">Commands associated with a server or database</span></span>  
  
-   <span data-ttu-id="4b787-115">資料來源</span><span class="sxs-lookup"><span data-stu-id="4b787-115">Data sources</span></span>  
  
 <span data-ttu-id="4b787-116">您可以使用[create](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/create-element-xmla)命令在的實例上建立主要物件 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ，以及 alter 命令來[Alter](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/alter-element-xmla)改變實例上現有的主要物件。</span><span class="sxs-lookup"><span data-stu-id="4b787-116">You use the [Create](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/create-element-xmla) command to create a major object on an instance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], and the [Alter](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/alter-element-xmla) command to alter an existing major object on an instance.</span></span> <span data-ttu-id="4b787-117">這兩個命令都是使用[Execute](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute)方法來執行。</span><span class="sxs-lookup"><span data-stu-id="4b787-117">Both commands are run using the [Execute](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute) method.</span></span>  
  
## <a name="creating-objects"></a><span data-ttu-id="4b787-118">建立物件</span><span class="sxs-lookup"><span data-stu-id="4b787-118">Creating Objects</span></span>  
 <span data-ttu-id="4b787-119">當您使用 `Create` 方法建立物件時，必須先識別包含要建立的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 物件之父物件。</span><span class="sxs-lookup"><span data-stu-id="4b787-119">When you create objects by using the `Create` method, you must first identify the parent object that contains the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] object to be created.</span></span> <span data-ttu-id="4b787-120">您可以在命令的[ParentObject](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla)屬性中提供物件參考，以識別父物件 `Create` 。</span><span class="sxs-lookup"><span data-stu-id="4b787-120">You identify the parent object by providing an object reference in the [ParentObject](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla) property of the `Create` command.</span></span> <span data-ttu-id="4b787-121">每個物件參考都包含唯一識別 `Create` 命令的父物件所需的物件識別碼。</span><span class="sxs-lookup"><span data-stu-id="4b787-121">Each object reference contains the object identifiers needed to uniquely identify the parent object for the `Create` command.</span></span> <span data-ttu-id="4b787-122">如需物件參考的詳細資訊，請參閱[&#40;XMLA&#41;定義和識別物件](https://docs.microsoft.com/bi-reference/xmla/xml-elements-objects)。</span><span class="sxs-lookup"><span data-stu-id="4b787-122">For more information about object references, see [Defining and Identifying Objects &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-objects).</span></span>  
  
 <span data-ttu-id="4b787-123">例如，您必須提供物件參考給 Cube，來為 Cube 建立新的量值群組。</span><span class="sxs-lookup"><span data-stu-id="4b787-123">For example, you must provide an object reference to a cube to create a new measure group for the cube.</span></span> <span data-ttu-id="4b787-124">在 `ParentObject` 屬性中的 Cube 之物件參考，包含資料庫識別碼與 Cube 識別碼，因為相同的 Cube 識別碼可能會用於不同的資料庫。</span><span class="sxs-lookup"><span data-stu-id="4b787-124">The object reference for the cube in the `ParentObject` property contains both a database identifier and a cube identifier, as the same cube identifier could potentially be used on a different database.</span></span>  
  
 <span data-ttu-id="4b787-125">[ObjectDefinition](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/objectdefinition-element-xmla)元素包含 Analysis Services 指令碼語言 (ASSL) 元素，這些專案會定義要建立的主要物件。</span><span class="sxs-lookup"><span data-stu-id="4b787-125">The [ObjectDefinition](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/objectdefinition-element-xmla) element contains Analysis Services Scripting Language (ASSL) elements that define the major object to be created.</span></span> <span data-ttu-id="4b787-126">如需 ASSL 的詳細資訊，請參閱[使用 Analysis Services 指令碼語言進行開發 &#40;ASSL&#41;](../multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md)。</span><span class="sxs-lookup"><span data-stu-id="4b787-126">For more information about ASSL, see [Developing with Analysis Services Scripting Language &#40;ASSL&#41;](../multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md).</span></span>  
  
 <span data-ttu-id="4b787-127">如果您將 `AllowOverwrite` 命令的 `Create` 屬性設定為 True，可以覆寫具有指定識別碼的現有主要物件。</span><span class="sxs-lookup"><span data-stu-id="4b787-127">If you set the `AllowOverwrite` attribute of the `Create` command to true, you can overwrite an existing major object that has the specified identifier.</span></span> <span data-ttu-id="4b787-128">否則，如果具有指定識別碼的主要物件已經在父物件中，就會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="4b787-128">Otherwise, an error occurs if a major object that has the specified identifier already exists in the parent object.</span></span>  
  
 <span data-ttu-id="4b787-129">如需命令的詳細資訊 `Create` ，請參閱[Create ELEMENT &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/create-element-xmla)。</span><span class="sxs-lookup"><span data-stu-id="4b787-129">For more information about the `Create` command, see [Create Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/create-element-xmla).</span></span>  
  
### <a name="creating-session-objects"></a><span data-ttu-id="4b787-130">建立工作階段物件</span><span class="sxs-lookup"><span data-stu-id="4b787-130">Creating Session Objects</span></span>  
 <span data-ttu-id="4b787-131">工作階段物件是只能用於用戶端應用程式所使用的明確或隱含工作階段的暫存物件，而且會在結束工作階段時刪除。</span><span class="sxs-lookup"><span data-stu-id="4b787-131">Session objects are temporary objects that are available only to the explicit or implicit session used by a client application and are deleted when the session is ended.</span></span> <span data-ttu-id="4b787-132">您可以藉由將 `Scope` 命令的屬性設定 `Create` 為*session*來建立會話物件。</span><span class="sxs-lookup"><span data-stu-id="4b787-132">You can create session objects by setting the `Scope` attribute of the `Create` command to *Session*.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4b787-133">使用*會話*設定時，元素只能 `ObjectDefinition` 包含[Dimension](https://docs.microsoft.com/bi-reference/assl/objects/dimension-element-assl)、 [Cube](https://docs.microsoft.com/bi-reference/assl/objects/cube-element-assl)或[MiningModel](https://docs.microsoft.com/bi-reference/assl/objects/miningmodel-element-assl) ASSL 元素。</span><span class="sxs-lookup"><span data-stu-id="4b787-133">When using the *Session* setting, the `ObjectDefinition` element can only contain [Dimension](https://docs.microsoft.com/bi-reference/assl/objects/dimension-element-assl), [Cube](https://docs.microsoft.com/bi-reference/assl/objects/cube-element-assl), or [MiningModel](https://docs.microsoft.com/bi-reference/assl/objects/miningmodel-element-assl) ASSL elements.</span></span>  
  
## <a name="altering-objects"></a><span data-ttu-id="4b787-134">改變物件</span><span class="sxs-lookup"><span data-stu-id="4b787-134">Altering Objects</span></span>  
 <span data-ttu-id="4b787-135">使用方法修改物件時 `Alter` ，您必須先在命令的[object](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla)屬性中提供物件參考，以識別要修改的物件 `Alter` 。</span><span class="sxs-lookup"><span data-stu-id="4b787-135">When modifying objects by using the `Alter` method, you must first identify the object to be modified by providing an object reference in the [Object](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla) property of the `Alter` command.</span></span> <span data-ttu-id="4b787-136">每個物件參考都包含唯一識別 `Alter` 命令的物件所需的物件識別碼。</span><span class="sxs-lookup"><span data-stu-id="4b787-136">Each object reference contains the object identifiers needed to uniquely identify the object for the `Alter` command.</span></span> <span data-ttu-id="4b787-137">如需物件參考的詳細資訊，請參閱[&#40;XMLA&#41;定義和識別物件](https://docs.microsoft.com/bi-reference/xmla/xml-elements-objects)。</span><span class="sxs-lookup"><span data-stu-id="4b787-137">For more information about object references, see [Defining and Identifying Objects &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-objects).</span></span>  
  
 <span data-ttu-id="4b787-138">例如，您必須提供物件參考給 Cube，以修改 Cube 的結構。</span><span class="sxs-lookup"><span data-stu-id="4b787-138">For example, you must provide an object reference to a cube in order to modify the structure of a cube.</span></span> <span data-ttu-id="4b787-139">在 `Object` 屬性中的 Cube 之物件參考，包含資料庫識別碼與 Cube 識別碼，因為相同的 Cube 識別碼可能會用於不同的資料庫。</span><span class="sxs-lookup"><span data-stu-id="4b787-139">The object reference for the cube in the `Object` property contains both a database identifier and a cube identifier, as the same cube identifier could potentially be used on a different database.</span></span>  
  
 <span data-ttu-id="4b787-140">`ObjectDefinition` 元素包含定義要修改的主要物件之 ASSL 元素。</span><span class="sxs-lookup"><span data-stu-id="4b787-140">The `ObjectDefinition` element contains ASSL elements that define the major object to be modified.</span></span> <span data-ttu-id="4b787-141">如需 ASSL 的詳細資訊，請參閱[使用 Analysis Services 指令碼語言進行開發 &#40;ASSL&#41;](../multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md)。</span><span class="sxs-lookup"><span data-stu-id="4b787-141">For more information about ASSL, see [Developing with Analysis Services Scripting Language &#40;ASSL&#41;](../multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md).</span></span>  
  
 <span data-ttu-id="4b787-142">如果您將 `AllowCreate` 命令的 `Alter` 屬性設定為 True，只要物件不存在，即可建立指定的主要物件。</span><span class="sxs-lookup"><span data-stu-id="4b787-142">If you set the `AllowCreate` attribute of the `Alter` command to true, you can create the specified major object if the object does not exist.</span></span> <span data-ttu-id="4b787-143">否則，如果指定的主要物件尚未存在，就會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="4b787-143">Otherwise, an error occurs if a specified major object does not already exist.</span></span>  
  
### <a name="using-the-objectexpansion-attribute"></a><span data-ttu-id="4b787-144">使用 ObjectExpansion 屬性</span><span class="sxs-lookup"><span data-stu-id="4b787-144">Using the ObjectExpansion Attribute</span></span>  
 <span data-ttu-id="4b787-145">如果您只變更主要物件的屬性，而且不會重新定義主要物件所包含的次要物件，您可以將命令的屬性設定 `ObjectExpansion` `Alter` 為*ObjectProperties*。</span><span class="sxs-lookup"><span data-stu-id="4b787-145">If you are changing only the properties of the major object and are not redefining minor objects that are contained by the major object, you can set the `ObjectExpansion` attribute of the `Alter` command to *ObjectProperties*.</span></span> <span data-ttu-id="4b787-146">`ObjectDefinition` 屬性就只需要包含主要物件之屬性的元素，而且 `Alter` 命令不會改變與主要物件關聯的次要物件。</span><span class="sxs-lookup"><span data-stu-id="4b787-146">The `ObjectDefinition` property then only has to contain the elements for the properties of the major object, and the `Alter` command leaves minor objects associated with the major object untouched.</span></span>  
  
 <span data-ttu-id="4b787-147">若要重新定義主要物件的次要物件，您必須將 `ObjectExpansion` 屬性設定為*ExpandFull* ，而且物件定義必須包含主要物件所包含的所有次要物件。</span><span class="sxs-lookup"><span data-stu-id="4b787-147">To redefine minor objects for a major object, you must set the `ObjectExpansion` attribute to *ExpandFull* and the object definition must include all minor objects that are contained by the major object.</span></span> <span data-ttu-id="4b787-148">如果 `ObjectDefinition` 命令的 `Alter` 屬性未明確包括主要物件所含的次要物件，則會刪除未包括的次要物件。</span><span class="sxs-lookup"><span data-stu-id="4b787-148">If the `ObjectDefinition` property of the `Alter` command does not explicitly include a minor object that is contained by the major object, the minor object that was not included is deleted.</span></span>  
  
### <a name="altering-session-objects"></a><span data-ttu-id="4b787-149">改變工作階段物件</span><span class="sxs-lookup"><span data-stu-id="4b787-149">Altering Session Objects</span></span>  
 <span data-ttu-id="4b787-150">若要修改命令所建立的會話物件 `Create` ，請將 `Scope` 命令的屬性設定 `Alter` 為*session*。</span><span class="sxs-lookup"><span data-stu-id="4b787-150">To modify session objects created by the `Create` command, set the `Scope` attribute of the `Alter` command to *Session*.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4b787-151">使用*會話*設定時，元素只能 `ObjectDefinition` 包含[Dimension](https://docs.microsoft.com/bi-reference/assl/objects/dimension-element-assl)、 [Cube](https://docs.microsoft.com/bi-reference/assl/objects/cube-element-assl)或[MiningModel](https://docs.microsoft.com/bi-reference/assl/objects/miningmodel-element-assl) ASSL 元素。</span><span class="sxs-lookup"><span data-stu-id="4b787-151">When using the *Session* setting, the `ObjectDefinition` element can only contain [Dimension](https://docs.microsoft.com/bi-reference/assl/objects/dimension-element-assl), [Cube](https://docs.microsoft.com/bi-reference/assl/objects/cube-element-assl), or [MiningModel](https://docs.microsoft.com/bi-reference/assl/objects/miningmodel-element-assl) ASSL elements.</span></span>  
  
## <a name="creating-or-altering-subordinate-objects"></a><span data-ttu-id="4b787-152">建立或改變從屬物件</span><span class="sxs-lookup"><span data-stu-id="4b787-152">Creating or Altering Subordinate Objects</span></span>  
 <span data-ttu-id="4b787-153">雖然 `Create` 或 `Alter` 命令只會建立或修改一個最主要的物件，所建立或修改的主要物件，在其他主要物件或是其從屬的次要物件之封閉式 `ObjectDefinition` 屬性中，仍可包含定義。</span><span class="sxs-lookup"><span data-stu-id="4b787-153">Although a `Create` or `Alter` command creates or alters only one topmost major object, the major object being created or modified can contain definitions within the enclosing `ObjectDefinition` property for other major and minor objects that are subordinate to it.</span></span> <span data-ttu-id="4b787-154">例如，如果您定義一個 Cube，在 `ParentObject` 中指定父資料庫，並且在 `ObjectDefinition` 的 Cube 定義中，可以為 Cube 定義量值群組，而且在量值群組中，可以為每個量值群組，定義資料分割。</span><span class="sxs-lookup"><span data-stu-id="4b787-154">For example, if you define a cube, you specify the parent database in `ParentObject`, and within the cube definition in `ObjectDefinition` you can define measure groups for the cube, and within the measure groups you can define partitions for each measure group.</span></span> <span data-ttu-id="4b787-155">次要物件只能在包含它的主要物件之下定義。</span><span class="sxs-lookup"><span data-stu-id="4b787-155">A minor object can be defined only under the major object that contains it.</span></span> <span data-ttu-id="4b787-156">如需主要和次要物件的詳細資訊，請參閱[資料庫物件 &#40;Analysis Services 多維度資料&#41;](../multidimensional-models/olap-logical/database-objects-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="4b787-156">For more information about major and minor objects, see [Database Objects &#40;Analysis Services - Multidimensional Data&#41;](../multidimensional-models/olap-logical/database-objects-analysis-services-multidimensional-data.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="4b787-157">範例</span><span class="sxs-lookup"><span data-stu-id="4b787-157">Examples</span></span>  
  
### <a name="description"></a><span data-ttu-id="4b787-158">描述</span><span class="sxs-lookup"><span data-stu-id="4b787-158">Description</span></span>  
 <span data-ttu-id="4b787-159">下列範例會建立參考範例資料庫的關聯式資料來源 [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="4b787-159">The following example creates a relational data source that references the [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] sample [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database.</span></span>  
  
### <a name="code"></a><span data-ttu-id="4b787-160">程式碼</span><span class="sxs-lookup"><span data-stu-id="4b787-160">Code</span></span>  
  
```  
<Create xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">  
    <ParentObject>  
        <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
    </ParentObject>  
    <ObjectDefinition>  
        <DataSource xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:type="RelationalDataSource">  
            <ID>AdventureWorksDW2012</ID>  
            <Name>AdventureWorksDW2012</Name>  
            <ConnectionString>Data Source=localhost;Initial Catalog=AdventureWorksDW2008R2;Integrated Security=True</ConnectionString>  
            <ImpersonationInfo>  
                <ImpersonationMode>ImpersonateServiceAccount</ImpersonationMode>  
            </ImpersonationInfo>  
            <ManagedProvider>System.Data.SqlClient</ManagedProvider>  
            <Timeout>PT0S</Timeout>  
        </DataSource>  
    </ObjectDefinition>  
</Create>  
```  
  
### <a name="description"></a><span data-ttu-id="4b787-161">描述</span><span class="sxs-lookup"><span data-stu-id="4b787-161">Description</span></span>  
 <span data-ttu-id="4b787-162">下列範例修改前面範例中所建立的關聯式資料來源，以便將資料來源的查詢逾時設定成 30 秒。</span><span class="sxs-lookup"><span data-stu-id="4b787-162">The following example alters the relational data source created in the previous example to set the query time-out for the data source to 30 seconds.</span></span>  
  
### <a name="code"></a><span data-ttu-id="4b787-163">程式碼</span><span class="sxs-lookup"><span data-stu-id="4b787-163">Code</span></span>  
  
```  
<Alter ObjectExpansion="ObjectProperties" xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">  
    <Object>  
        <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
        <DataSourceID>AdventureWorksDW2012</DataSourceID>  
    </Object>  
    <ObjectDefinition>  
        <DataSource xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:type="RelationalDataSource">  
            <ID>AdventureWorksDW2012</ID>  
            <Name>AdventureWorksDW2012</Name>  
            <ConnectionString>Data Source=fr-dwk-02;Initial Catalog=AdventureWorksDW2008R2;Integrated Security=True</ConnectionString>  
            <ManagedProvider>System.Data.SqlClient</ManagedProvider>  
            <Timeout>PT30S</Timeout>  
        </DataSource>  
    </ObjectDefinition>  
</Alter>  
```  
  
### <a name="comments"></a><span data-ttu-id="4b787-164">註解</span><span class="sxs-lookup"><span data-stu-id="4b787-164">Comments</span></span>  
 <span data-ttu-id="4b787-165">`ObjectExpansion`命令的屬性 `Alter` 已設定為*ObjectProperties*。</span><span class="sxs-lookup"><span data-stu-id="4b787-165">The `ObjectExpansion` attribute of the `Alter` command was set to *ObjectProperties*.</span></span> <span data-ttu-id="4b787-166">此設定可讓[ImpersonationInfo](https://docs.microsoft.com/bi-reference/assl/properties/impersonationinfo-element-assl)元素（次要物件）從中定義的資料來源中排除 `ObjectDefinition` 。</span><span class="sxs-lookup"><span data-stu-id="4b787-166">This setting allows the [ImpersonationInfo](https://docs.microsoft.com/bi-reference/assl/properties/impersonationinfo-element-assl) element, a minor object, to be excluded from the data source defined in `ObjectDefinition`.</span></span> <span data-ttu-id="4b787-167">因此，資料來源的模擬資訊仍然會設定成服務帳號，如第一個範例中所指定。</span><span class="sxs-lookup"><span data-stu-id="4b787-167">Therefore, the impersonation information for that data source remains set to the service account, as specified in the first example.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b787-168">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4b787-168">See Also</span></span>  
 <span data-ttu-id="4b787-169">[XMLA&#41;的 Execute 方法 &#40;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute) </span><span class="sxs-lookup"><span data-stu-id="4b787-169">[Execute Method &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute) </span></span>  
 <span data-ttu-id="4b787-170">[使用 Analysis Services 指令碼語言進行開發 &#40;ASSL&#41;](../multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md) </span><span class="sxs-lookup"><span data-stu-id="4b787-170">[Developing with Analysis Services Scripting Language &#40;ASSL&#41;](../multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md) </span></span>  
 [<span data-ttu-id="4b787-171">在 Analysis Services 中使用 XMLA 進行開發</span><span class="sxs-lookup"><span data-stu-id="4b787-171">Developing with XMLA in Analysis Services</span></span>](developing-with-xmla-in-analysis-services.md)  
  
  
