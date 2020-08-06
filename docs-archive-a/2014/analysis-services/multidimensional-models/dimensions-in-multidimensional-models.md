---
title: 多維度模型中的維度 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- OLAP [Analysis Services], dimensions
- dimensions [Analysis Services], about dimensions
- OLAP objects [Analysis Services], dimensions
ms.assetid: 2b62b05c-00fd-4e60-b77f-f707ba83a19b
author: minewiskan
ms.author: owend
ms.openlocfilehash: b9e452453b80de3656abf62cdcd90519cf4a6c99
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708757"
---
# <a name="dimensions-in-multidimensional-models"></a><span data-ttu-id="f7b6c-102">多維度模型中的維度</span><span class="sxs-lookup"><span data-stu-id="f7b6c-102">Dimensions in Multidimensional Models</span></span>
  <span data-ttu-id="f7b6c-103">資料庫維度是相關物件的集合 (稱為屬性)，可用來提供與一或多個 Cube 中的事實資料有關的資訊。</span><span class="sxs-lookup"><span data-stu-id="f7b6c-103">A database dimension is a collection of related objects, called attributes, which can be used to provide information about fact data in one or more cubes.</span></span> <span data-ttu-id="f7b6c-104">例如，產品維度中的典型屬性可能是產品名稱、產品類別目錄、產品線、產品尺寸和產品價格；</span><span class="sxs-lookup"><span data-stu-id="f7b6c-104">For example, typical attributes in a product dimension might be product name, product category, product line, product size, and product price.</span></span> <span data-ttu-id="f7b6c-105">這些物件會繫結到資料來源檢視中一或多個資料表內的一或多個資料行，</span><span class="sxs-lookup"><span data-stu-id="f7b6c-105">These objects are bound to one or more columns in one or more tables in a data source view.</span></span> <span data-ttu-id="f7b6c-106">依預設，這些屬性可以顯示為屬性階層，而且可用來了解 Cube 中的事實資料。</span><span class="sxs-lookup"><span data-stu-id="f7b6c-106">By default, these attributes are visible as attribute hierarchies and can be used to understand the fact data in a cube.</span></span> <span data-ttu-id="f7b6c-107">屬性可以組成使用者自訂階層，在使用者瀏覽 Cube 中的資料時，提供導覽路徑來協助使用者。</span><span class="sxs-lookup"><span data-stu-id="f7b6c-107">Attributes can be organized into user-defined hierarchies that provide navigational paths to assist users when browsing the data in a cube.</span></span>  
  
 <span data-ttu-id="f7b6c-108">Cube 包含使用者的事實資料分析所根據的所有維度；</span><span class="sxs-lookup"><span data-stu-id="f7b6c-108">Cubes contain all the dimensions on which users base their analyses of fact data.</span></span> <span data-ttu-id="f7b6c-109">Cube 中資料庫維度的執行個體稱為 Cube 維度，與 Cube 中的一個或多個量值群組相關。</span><span class="sxs-lookup"><span data-stu-id="f7b6c-109">An instance of a database dimension in a cube is called a cube dimension and relates to one or more measure groups in the cube.</span></span> <span data-ttu-id="f7b6c-110">資料庫維度可在 Cube 中使用多次。</span><span class="sxs-lookup"><span data-stu-id="f7b6c-110">A database dimension can be used multiple times in a cube.</span></span> <span data-ttu-id="f7b6c-111">例如，事實資料表可以有多個時間相關的事實，而且可以定義個別 Cube 維度來協助分析每一個時間相關的事實；</span><span class="sxs-lookup"><span data-stu-id="f7b6c-111">For example, a fact table can have multiple time-related facts, and a separate cube dimension can be defined to assist in analyzing each time-related fact.</span></span> <span data-ttu-id="f7b6c-112">但是，只需要存在一個時間相關的資料庫維度，這也表示只需要存在一個時間相關的關聯式資料庫資料表，就可以支援以時間為根據的多個 Cube 維度。</span><span class="sxs-lookup"><span data-stu-id="f7b6c-112">However, only one time-related database dimension needs to exist, which also means that only one time-related relational database table needs to exist to support multiple cube dimensions based on time.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f7b6c-113"> 如需了解與維度設計相關的效能問題，請參閱 [SQL Server 2008 R2 Analysis Services 效能指南](https://go.microsoft.com/fwlink/?LinkId=306717)。</span><span class="sxs-lookup"><span data-stu-id="f7b6c-113">For performance issues related to dimension design, see the [SQL Server 2008 R2 Analysis Services Performance Guide](https://go.microsoft.com/fwlink/?LinkId=306717).</span></span>  
  
## <a name="defining-dimensions-attributes-and-hierarchies"></a><span data-ttu-id="f7b6c-114">定義維度、屬性和階層</span><span class="sxs-lookup"><span data-stu-id="f7b6c-114">Defining Dimensions, Attributes, and Hierarchies</span></span>  
 <span data-ttu-id="f7b6c-115">定義資料庫和 Cube 維度、屬性和階層最簡單的方法，就是使用 [Cube 精靈]，在定義 Cube 的同時建立維度。</span><span class="sxs-lookup"><span data-stu-id="f7b6c-115">The simplest method for defining database and cube dimensions, attributes, and hierarchies is to use the Cube Wizard to create dimensions at the same time that you define the cube.</span></span> <span data-ttu-id="f7b6c-116">Cube 精靈會根據精靈在資料來源檢視中找到的維度資料表，或您指定要用於 Cube 的維度資料表，來建立維度。</span><span class="sxs-lookup"><span data-stu-id="f7b6c-116">The Cube Wizard will create dimensions based on the dimension tables in the data source view that the wizard identifies or that you specify for use in the cube.</span></span> <span data-ttu-id="f7b6c-117">然後，精靈會建立資料庫維度，並將其加入新的 Cube，以建立 Cube 維度。</span><span class="sxs-lookup"><span data-stu-id="f7b6c-117">The wizard then creates the database dimensions and adds them to the new cube, creating cube dimensions.</span></span>  
  
 <span data-ttu-id="f7b6c-118">建立 Cube 時，也可以將資料庫中的任何現有維度加入新的 Cube 中。</span><span class="sxs-lookup"><span data-stu-id="f7b6c-118">When you create a cube, you can also add to the new cube any dimensions that already exist in the database.</span></span> <span data-ttu-id="f7b6c-119">這些維度可能是先前已經為其他 Cube 定義的維度，或已由維度精靈定義的維度。</span><span class="sxs-lookup"><span data-stu-id="f7b6c-119">These dimensions may have been previously defined for another cube or by the Dimension Wizard.</span></span> <span data-ttu-id="f7b6c-120">定義資料庫維度之後，您可以在維度設計師中修改並設定資料庫維度。</span><span class="sxs-lookup"><span data-stu-id="f7b6c-120">After a database dimension has been defined, you can modify and configure the database dimension in Dimension Designer.</span></span> <span data-ttu-id="f7b6c-121">您也可以在 Cube 設計師中自訂有限範圍的 Cube 維度。</span><span class="sxs-lookup"><span data-stu-id="f7b6c-121">You can also customize the cube dimension, to a limited extent, in Cube Designer.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f7b6c-122">此外，您也可以透過使用 XMLA 或分析管理物件 (AMO)，以程式設計方式設計並設定維度、屬性和階層。</span><span class="sxs-lookup"><span data-stu-id="f7b6c-122">You can also design and configure dimensions, attributes, and hierarchies programmatically by using either XMLA or Analysis Management Objects (AMO).</span></span> <span data-ttu-id="f7b6c-123">如需詳細資訊，請參閱[Analysis Services 指令碼語言 &#40;ASSL&#41; 參考](https://docs.microsoft.com/bi-reference/assl/analysis-services-scripting-language-assl-for-xmla)和[流量分析管理物件 &#40;AMO&#41;進行開發](https://docs.microsoft.com/bi-reference/amo/developing-with-analysis-management-objects-amo)。</span><span class="sxs-lookup"><span data-stu-id="f7b6c-123">For more information, see [Analysis Services Scripting Language &#40;ASSL&#41; Reference](https://docs.microsoft.com/bi-reference/assl/analysis-services-scripting-language-assl-for-xmla) and [Developing with Analysis Management Objects &#40;AMO&#41;](https://docs.microsoft.com/bi-reference/amo/developing-with-analysis-management-objects-amo).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f7b6c-124">本節內容</span><span class="sxs-lookup"><span data-stu-id="f7b6c-124">In This Section</span></span>  
 <span data-ttu-id="f7b6c-125">下表描述此章節的主題。</span><span class="sxs-lookup"><span data-stu-id="f7b6c-125">The following table describes the topics in this section.</span></span>  
  
 [<span data-ttu-id="f7b6c-126">定義資料庫維度</span><span class="sxs-lookup"><span data-stu-id="f7b6c-126">Define Database Dimensions</span></span>](define-database-dimensions.md)  
 <span data-ttu-id="f7b6c-127">描述如何使用維度設計師修改及設定資料庫維度。</span><span class="sxs-lookup"><span data-stu-id="f7b6c-127">Describes how to modify and configure a database dimension by using Dimension Designer.</span></span>  
  
 [<span data-ttu-id="f7b6c-128">維度屬性 (attribute) 屬性 (property) 參考</span><span class="sxs-lookup"><span data-stu-id="f7b6c-128">Dimension Attribute Properties Reference</span></span>](dimension-attribute-properties-reference.md)  
 <span data-ttu-id="f7b6c-129">描述如何使用維度設計師來定義、修改及設定資料庫維度屬性。</span><span class="sxs-lookup"><span data-stu-id="f7b6c-129">Describes how to define, modify, and configure a database dimension attribute by using Dimension Designer.</span></span>  
  
 [<span data-ttu-id="f7b6c-130">定義屬性關聯性</span><span class="sxs-lookup"><span data-stu-id="f7b6c-130">Define Attribute Relationships</span></span>](attribute-relationships-define.md)  
 <span data-ttu-id="f7b6c-131">描述如何使用維度設計師來定義、修改及設定屬性關聯性。</span><span class="sxs-lookup"><span data-stu-id="f7b6c-131">Describes how to define, modify, and configure an attribute relationship by using Dimension Designer.</span></span>  
  
 [<span data-ttu-id="f7b6c-132">建立使用者定義階層</span><span class="sxs-lookup"><span data-stu-id="f7b6c-132">Create User-Defined Hierarchies</span></span>](user-defined-hierarchies-create.md)  
 <span data-ttu-id="f7b6c-133">描述如何使用維度設計師來定義、修改及設定維度屬性的使用者自訂階層。</span><span class="sxs-lookup"><span data-stu-id="f7b6c-133">Describes how to define, modify, and configure a user-defined hierarchy of dimension attributes by using Dimension Designer.</span></span>  
  
 [<span data-ttu-id="f7b6c-134">使用商業智慧精靈增強維度</span><span class="sxs-lookup"><span data-stu-id="f7b6c-134">Use the Business Intelligence Wizard to Enhance Dimensions</span></span>](../use-the-business-intelligence-wizard-to-enhance-dimensions.md)  
 <span data-ttu-id="f7b6c-135">描述如何使用 [商業智慧精靈] 來增強資料庫維度。</span><span class="sxs-lookup"><span data-stu-id="f7b6c-135">Describes how to enhance a database dimension by using the Business Intelligence Wizard.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7b6c-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f7b6c-136">See Also</span></span>  
 [<span data-ttu-id="f7b6c-137">多維度模型中的 Cube</span><span class="sxs-lookup"><span data-stu-id="f7b6c-137">Cubes in Multidimensional Models</span></span>](cubes-in-multidimensional-models.md)  
  
  
