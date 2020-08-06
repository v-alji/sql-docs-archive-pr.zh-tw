---
title: 匯出和匯入資料採礦物件 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- backing up databases [Analysis Services]
- exporting mining models
- exporting mining structures
- mining structures [Analysis Services], creating
- mining structures [DMX], exporting
- mining models [Analysis Services], migration
ms.assetid: 10a83b13-2640-4ff5-80c8-a35e1d692908
author: minewiskan
ms.author: owend
ms.openlocfilehash: 01e8651dd7e9d59012b0ba065bccb9ea62a1ee54
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598056"
---
# <a name="export-and-import-data-mining-objects"></a><span data-ttu-id="ea4d2-102">匯出及匯入資料採礦物件</span><span class="sxs-lookup"><span data-stu-id="ea4d2-102">Export and Import Data Mining Objects</span></span>
  <span data-ttu-id="ea4d2-103">除了在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 中針對備份、還原和移轉方案提供的功能之外，SQL Server 資料採礦還可以使用資料採礦延伸模組 (DMX)，在不同的伺服器之間快速傳送資料採礦結構和模型。</span><span class="sxs-lookup"><span data-stu-id="ea4d2-103">In addition to the functionality provided in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] for backing up, restoring, and migrating solutions, SQL Server Data Mining provides the ability to quickly transfer data mining structures and models between different servers by using Data Mining Extensions (DMX).</span></span>  
  
 <span data-ttu-id="ea4d2-104">如果您的資料採礦方案使用關聯式資料，而非多維度資料庫，則使用 `EXPORT` 和 `IMPORT` 傳送模型要比使用資料庫還原或部署整個方案更為快速而且容易。</span><span class="sxs-lookup"><span data-stu-id="ea4d2-104">If your data mining solution uses relational data instead of a multidimensional database, transferring models by using `EXPORT` and `IMPORT` is much faster and easier than either using database restore or deploying an entire solution.</span></span>  
  
 <span data-ttu-id="ea4d2-105">本節提供如何使用 DMX 陳述式傳送資料採礦結構與模型的概觀。</span><span class="sxs-lookup"><span data-stu-id="ea4d2-105">This section provides an overview of how to transfer data mining structures and models by using DMX statements.</span></span> <span data-ttu-id="ea4d2-106">如需語法及範例的詳細資訊，請參閱 [EXPORT &#40;DMX&#41;](/sql/dmx/export-dmx) 和 [IMPORT &#40;DMX&#41;](/sql/dmx/import-dmx)。</span><span class="sxs-lookup"><span data-stu-id="ea4d2-106">For details of the syntax, together with examples, see [EXPORT &#40;DMX&#41;](/sql/dmx/export-dmx) and [IMPORT &#40;DMX&#41;](/sql/dmx/import-dmx).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ea4d2-107">您必須是資料庫或伺服器管理員，才能從 Microsoft SQL Server Analysis Services 資料庫匯出或匯入物件。</span><span class="sxs-lookup"><span data-stu-id="ea4d2-107">You must be a database or server administrator to export or import objects from a Microsoft SQL Server Analysis Services database.</span></span>  
  
## <a name="exporting-data-mining-structures"></a><span data-ttu-id="ea4d2-108">匯出資料採礦結構</span><span class="sxs-lookup"><span data-stu-id="ea4d2-108">Exporting Data Mining Structures</span></span>  
 <span data-ttu-id="ea4d2-109">當您匯出採礦結構時，EXPORT 陳述式會自動匯出所有關聯的模型。</span><span class="sxs-lookup"><span data-stu-id="ea4d2-109">When you export a mining structure, the EXPORT statement automatically exports all associated models.</span></span> <span data-ttu-id="ea4d2-110">如果您要控制匯出的物件，必須依名稱指定每個物件。</span><span class="sxs-lookup"><span data-stu-id="ea4d2-110">If you want to control the objects that are exported, you must specify each object by name.</span></span>  
  
 <span data-ttu-id="ea4d2-111">當您匯出採礦結構時，如果採礦結構已經過處理，而且結果已經經過快取 (這是預設行為)，定義則包含結構所依據之資料的摘要。</span><span class="sxs-lookup"><span data-stu-id="ea4d2-111">If the mining structure has been processed and the results have been cached, which is the default behavior, when you export the mining structure, the definition contains a summary of the data on which the structure is based.</span></span> <span data-ttu-id="ea4d2-112">若要移除此摘要，您必須執行 `Process Clear Structure` 作業，清除與採礦結構關聯的快取。</span><span class="sxs-lookup"><span data-stu-id="ea4d2-112">To remove this summary, you must clear the cache associated with the mining structure by performing a `Process Clear Structure` operation.</span></span> <span data-ttu-id="ea4d2-113">如需詳細資訊，請參閱 [處理採礦結構](process-a-mining-structure.md)。</span><span class="sxs-lookup"><span data-stu-id="ea4d2-113">For more information, see [Process a Mining Structure](process-a-mining-structure.md).</span></span>  
  
### <a name="exporting-data-mining-models"></a><span data-ttu-id="ea4d2-114">匯出資料採礦模型</span><span class="sxs-lookup"><span data-stu-id="ea4d2-114">Exporting Data Mining Models</span></span>  
 <span data-ttu-id="ea4d2-115">您可以使用 `WITH DEPENDENCIES` 關鍵字匯出資料來源與資料來源檢視定義，以及採礦模型及其結構。</span><span class="sxs-lookup"><span data-stu-id="ea4d2-115">You can use the `WITH DEPENDENCIES` keyword to export the data source and data source view definition together with the mining model and its structure.</span></span>  
  
 <span data-ttu-id="ea4d2-116">當您匯出採礦模型而不匯出其相依性時，EXPORT 陳述式會匯出採礦模型及其採礦結構的定義，但是不會匯出資料來源的定義。</span><span class="sxs-lookup"><span data-stu-id="ea4d2-116">When you export a mining model without exporting its dependencies, the EXPORT statement will export the definition of the mining model and its mining structure, but does not export the definition of the data sources.</span></span> <span data-ttu-id="ea4d2-117">因此，在您匯入模型後，您將能夠立即瀏覽模型，但是，如果您要在目標伺服器上重新處理採礦模型，或針對基礎資料執行查詢，則必須在目的地伺服器上建立對應的資料來源。</span><span class="sxs-lookup"><span data-stu-id="ea4d2-117">As a consequence, after you import the model you will be able to browse the model immediately, but if you want to reprocess the mining model on the target server, or run queries against the underlying data, you must create a corresponding data source on the destination server.</span></span>  
  
## <a name="importing-data-mining-structures-and-models"></a><span data-ttu-id="ea4d2-118">匯入資料採礦結構和模型</span><span class="sxs-lookup"><span data-stu-id="ea4d2-118">Importing Data Mining Structures and Models</span></span>  
 <span data-ttu-id="ea4d2-119">當您匯入資料採礦物件時，該物件會匯入您執行 IMPORT 陳述式時所連接的伺服器和資料庫。</span><span class="sxs-lookup"><span data-stu-id="ea4d2-119">When you import a data mining object, the object is imported to the server and database to which you are connected when you execute the IMPORT statement.</span></span> <span data-ttu-id="ea4d2-120">如果匯入檔案包含的資料庫不存在於伺服器上，則會建立資料庫。</span><span class="sxs-lookup"><span data-stu-id="ea4d2-120">If the import file includes a database that does not exist on the server, the database will be created.</span></span>  
  
 <span data-ttu-id="ea4d2-121">您也可以使用 `Restore` 命令匯入採礦結構或採礦模型。</span><span class="sxs-lookup"><span data-stu-id="ea4d2-121">You can also import a mining structure or mining model by using the `Restore` command.</span></span> <span data-ttu-id="ea4d2-122">您的模型或結構將會還原到與匯出之來源資料庫同名的資料庫中。</span><span class="sxs-lookup"><span data-stu-id="ea4d2-122">Your models or structures will be restored into the database that has the same name as the database from which they were exported.</span></span> <span data-ttu-id="ea4d2-123">如需詳細資訊，請參閱 [Restore Options](../multidimensional-models/restore-options.md)。</span><span class="sxs-lookup"><span data-stu-id="ea4d2-123">For more information, see [Restore Options](../multidimensional-models/restore-options.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ea4d2-124">備註</span><span class="sxs-lookup"><span data-stu-id="ea4d2-124">Remarks</span></span>  
 <span data-ttu-id="ea4d2-125">如果伺服器上已存在相同名稱的模型或結構，則無法將該模型或結構匯入到該伺服器中。</span><span class="sxs-lookup"><span data-stu-id="ea4d2-125">You cannot import a model or structure to a server if a model or structure of the same name already exists on that server.</span></span> <span data-ttu-id="ea4d2-126">同時，您無法匯入資料採礦物件，然後在匯出檔案中修改該物件的名稱。</span><span class="sxs-lookup"><span data-stu-id="ea4d2-126">Also, you cannot export a data mining object and then modify the name of that object in the export file.</span></span> <span data-ttu-id="ea4d2-127">因此，如果您預期會發生命名衝突，應該刪除目標伺服器上的資料採礦物件，或在匯出定義前，先重新命名該資料採礦物件。</span><span class="sxs-lookup"><span data-stu-id="ea4d2-127">Therefore, if you anticipate naming conflicts, you should either delete the data mining object on the target server, or rename the data mining object before you export the definition.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea4d2-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ea4d2-128">See Also</span></span>  
 [<span data-ttu-id="ea4d2-129">資料採礦方案與物件的管理</span><span class="sxs-lookup"><span data-stu-id="ea4d2-129">Management of Data Mining Solutions and Objects</span></span>](management-of-data-mining-solutions-and-objects.md)  
  
  
