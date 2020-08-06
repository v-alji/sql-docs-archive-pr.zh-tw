---
title: 授與物件中繼資料的讀取定義許可權 (Analysis Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- metadata [Analysis Services]
- permissions [Analysis Services], read metadata
- read metadata permissions
ms.assetid: c857e48e-64b0-4ffe-900d-a0a3ddafcefb
author: minewiskan
ms.author: owend
ms.openlocfilehash: 1e3b18b913ed4b678baf0969b006f1386ba748e3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596938"
---
# <a name="grant-read-definition-permissions-on-object-metadata-analysis-services"></a><span data-ttu-id="09458-102">授與物件中繼資料的讀取定義權限 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="09458-102">Grant read definition permissions on object metadata (Analysis Services)</span></span>
  <span data-ttu-id="09458-103">讀取所選物件上的物件定義或中繼資料的權限，可讓管理員授與檢視物件資訊的權限，而不必同時授與修改物件定義、修改物件結構或檢視物件實際資料的權限。</span><span class="sxs-lookup"><span data-stu-id="09458-103">Permission to read an object definition, or metadata, on selected objects lets an administrator grant permission to view object information, without also granting permission to modify the object's definition, modify the object's structure, or view the actual data for the object.</span></span> <span data-ttu-id="09458-104">`Read Definition`可以在資料庫、資料來源、維度、採礦結構和採礦模型層級授與許可權。</span><span class="sxs-lookup"><span data-stu-id="09458-104">`Read Definition` permissions can be granted at the database, data source, dimension, mining structure, and mining model levels.</span></span> <span data-ttu-id="09458-105">如果您需要 `Read Definition` cube 的許可權，您必須 `Read Definition` 針對資料庫啟用。請記住，許可權是附加的。</span><span class="sxs-lookup"><span data-stu-id="09458-105">If you require `Read Definition` permissions for a cube, you must enable `Read Definition` for the database.Remember that permissions are additive.</span></span> <span data-ttu-id="09458-106">例如，某個角色會授與讀取 Cube 之中繼資料的權限，而第二個角色則會授與讀取維度之中繼資料的相同使用者權限。</span><span class="sxs-lookup"><span data-stu-id="09458-106">For example, one role grants permission to read the metadata for a cube, while a second role grants the same user permission to read the metadata for a dimension.</span></span> <span data-ttu-id="09458-107">兩個不同角色的權限結合之後，使用者就會同時擁有讀取該資料庫內 Cube 之中繼資料和維度之中繼資料的權限。</span><span class="sxs-lookup"><span data-stu-id="09458-107">The permissions from the two different roles combine to give the user permission to both read metadata for the cube and the metadata for the dimension within that database.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="09458-108">讀取資料庫之中繼資料的權限，是要使用 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 或 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 連接到 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]資料庫所需的最少權限。</span><span class="sxs-lookup"><span data-stu-id="09458-108">Permission to read a database's metadata is the minimum permission required to connect to an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database using either [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] or [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)].</span></span> <span data-ttu-id="09458-109">有權限讀取中繼資料的使用者．也可以使用 DISCOVER_XML_METADATA 結構描述資料列集，來查詢物件和檢視其中繼資料。</span><span class="sxs-lookup"><span data-stu-id="09458-109">A user who has permission to read metadata can also use the DISCOVER_XML_METADATA schema rowset to query the object and view its metadata.</span></span> <span data-ttu-id="09458-110">如需詳細資訊，請參閱 [DISCOVER_XML_METADATA Rowset](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-xml-metadata-rowset)。</span><span class="sxs-lookup"><span data-stu-id="09458-110">For more information, see [DISCOVER_XML_METADATA Rowset](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-xml-metadata-rowset).</span></span>  
  
## <a name="set-read-definition-permissions-on-a-database"></a><span data-ttu-id="09458-111">設定資料庫的讀取定義權限</span><span class="sxs-lookup"><span data-stu-id="09458-111">Set read definition permissions on a database</span></span>  
 <span data-ttu-id="09458-112">授與讀取資料庫中繼資料的權限時，也會授與讀取資料庫中所有物件之中繼資料的權限。</span><span class="sxs-lookup"><span data-stu-id="09458-112">Granting permission to read database metadata also grants permission to read the metadata of all objects in the database.</span></span>  
  
 <span data-ttu-id="09458-113">建議您在 `Read Definition` 設定專用處理的角色時，在資料庫層級包含許可權。</span><span class="sxs-lookup"><span data-stu-id="09458-113">We suggest that you include the `Read Definition` permission at the database level whenever you are setting up roles for dedicated processing.</span></span> <span data-ttu-id="09458-114">擁有 `Read Definition` 可讓非系統管理員在中查看模型的物件階層 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，並流覽至個別的物件以進行後續處理。</span><span class="sxs-lookup"><span data-stu-id="09458-114">Having `Read Definition` allows non-administrators to view a model's object hierarchy in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] and navigate to individual objects for subsequent processing.</span></span>  
  
1.  <span data-ttu-id="09458-115">在中 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，連接到的實例 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 、在物件總管中展開適當資料庫的 [**角色**]，然後按一下資料庫角色 (或建立新的資料庫角色) 。</span><span class="sxs-lookup"><span data-stu-id="09458-115">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to the instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], expand **Roles** for the appropriate database in Object Explorer, and then click a database role (or create a new database role).</span></span>  
  
2.  <span data-ttu-id="09458-116">在 [**一般**] 索引標籤上，選取 `Read Definition` 選項。</span><span class="sxs-lookup"><span data-stu-id="09458-116">On the **General** tab, select the `Read Definition` option.</span></span>  
  
3.  <span data-ttu-id="09458-117">在 [成員資格]\*\*\*\* 窗格中，輸入使用這個角色連線到 Analysis Services 的 Windows 使用者和群組帳戶。</span><span class="sxs-lookup"><span data-stu-id="09458-117">In the **Membership** pane, enter the Windows user and group accounts that connect to Analysis Services using this role.</span></span>  
  
4.  <span data-ttu-id="09458-118">按一下 [確定]\*\*\*\*，完成角色的建立。</span><span class="sxs-lookup"><span data-stu-id="09458-118">Click **OK** to finish creating the role.</span></span>  
  
## <a name="set-read-definition-permissions-on-individual-objects"></a><span data-ttu-id="09458-119">設定個別物件的讀取定義權限</span><span class="sxs-lookup"><span data-stu-id="09458-119">Set read definition permissions on individual objects</span></span>  
  
1.  <span data-ttu-id="09458-120">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中，連線到 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 的執行個體、開啟 [資料庫]\*\*\*\* 資料夾、選取資料庫、在物件總管中展開適當資料庫的 [角色]\*\*\*\*，然後按一下資料庫角色 (或建立新的資料庫角色)。</span><span class="sxs-lookup"><span data-stu-id="09458-120">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to the instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], open the **Databases** folder, select a database, expand **Roles** for the appropriate database in Object Explorer, and then click a database role (or create a new database role).</span></span>  
  
2.  <span data-ttu-id="09458-121">在 [**一般**] 窗格中，清除的資料庫許可權 `Read Definition` 。</span><span class="sxs-lookup"><span data-stu-id="09458-121">In the **General** pane, clear the database permission for `Read Definition`.</span></span> <span data-ttu-id="09458-122">這個步驟會移除權限繼承，因此，您可以設定個別物件的權限。</span><span class="sxs-lookup"><span data-stu-id="09458-122">This step removes permission inheritance so that you can set permissions on individual objects.</span></span>  
  
3.  <span data-ttu-id="09458-123">選取您要為其指定屬性的物件 `Read Definition` ：</span><span class="sxs-lookup"><span data-stu-id="09458-123">Select the object for which you are specifying `Read Definition` properties:</span></span>  
  
    -   <span data-ttu-id="09458-124">在 [**資料來源**] 窗格中，按一下 `Read Definition` 該資料來源的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="09458-124">In the **Data Sources** pane, click the `Read Definition` check box for that data source.</span></span> <span data-ttu-id="09458-125">角色成員可以檢視連線至資料來源的連線字串，包含伺服器名稱，可能也包含使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="09458-125">Role members can view the connection string to the data source, including the server name and possibly the user name.</span></span> <span data-ttu-id="09458-126">如果您想要提供連線字串資訊，可以使用這個權限，不需要同時授與修改連線字串或檢視任何其他物件之定義的權限。</span><span class="sxs-lookup"><span data-stu-id="09458-126">This permission is available in case you want to provide connection string information, without also granting permission to modify the connection string or view the definitions of any other objects.</span></span>  
  
    -   <span data-ttu-id="09458-127">在 [**維度**] 窗格中，按一下 `Read Definition` 該維度的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="09458-127">In the **Dimensions** pane, click the `Read Definition` check box for that dimension.</span></span> <span data-ttu-id="09458-128">有經驗的分析師與開發人員可能需要檢視定義，而不需要修改它或檢視其他物件 (例如，其他維度、Cube 物件，或者採礦結構和模型) 之定義的權限。</span><span class="sxs-lookup"><span data-stu-id="09458-128">Experienced analysts and developers may need to view the definition without permission to modify it or view the definitions of other objects (such as other dimensions, cube objects, or mining structures and models).</span></span>  
  
    -   <span data-ttu-id="09458-129">在 [採礦結構] 窗格中，按一下 [ `Read Definition` 資料採礦結構] 或 [模型] 的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="09458-129">In the Mining Structures pane, click the `Read Definition` check box for data mining structures or models.</span></span> <span data-ttu-id="09458-130">`Read Definition`需要用來流覽資料模型。</span><span class="sxs-lookup"><span data-stu-id="09458-130">`Read Definition` is required for browsing the data model.</span></span> <span data-ttu-id="09458-131">請參閱[授與資料採礦結構和模型的權限 &#40;Analysis Services&#41;](grant-permissions-on-data-mining-structures-and-models-analysis-services.md)。</span><span class="sxs-lookup"><span data-stu-id="09458-131">See [Grant permissions on data mining structures and models &#40;Analysis Services&#41;](grant-permissions-on-data-mining-structures-and-models-analysis-services.md) for details.</span></span>  
  
4.  <span data-ttu-id="09458-132">在 [成員資格]\*\*\*\* 窗格中，輸入使用這個角色連線到 Analysis Services 的 Windows 使用者和群組帳戶。</span><span class="sxs-lookup"><span data-stu-id="09458-132">In the **Membership** pane, enter the Windows user and group accounts that connect to Analysis Services using this role.</span></span>  
  
5.  <span data-ttu-id="09458-133">按一下 [確定]\*\*\*\*，完成角色的建立。</span><span class="sxs-lookup"><span data-stu-id="09458-133">Click **OK** to finish creating the role.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09458-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="09458-134">See Also</span></span>  
 <span data-ttu-id="09458-135">[授與資料庫許可權 &#40;Analysis Services&#41;](grant-database-permissions-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="09458-135">[Grant database permissions &#40;Analysis Services&#41;](grant-database-permissions-analysis-services.md) </span></span>  
 [<span data-ttu-id="09458-136">授與處理權限 &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="09458-136">Grant process permissions &#40;Analysis Services&#41;</span></span>](grant-process-permissions-analysis-services.md)  
  
  
