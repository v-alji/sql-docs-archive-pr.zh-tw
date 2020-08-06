---
title: 以路徑連接元件 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- data flow [Integration Services], connections
- components [Integration Services], connections
- connections [Integration Services], data flow components
ms.assetid: 05633e4c-1370-4b05-802b-f36b07dd71c8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e11955601406406abe48b53197e95c8224762fee
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706657"
---
# <a name="connect-components-with-paths"></a><span data-ttu-id="c1122-102">以路徑連接元件</span><span class="sxs-lookup"><span data-stu-id="c1122-102">Connect Components with Paths</span></span>
  <span data-ttu-id="c1122-103">您可以在 **設計師中** [資料流程] [!INCLUDE[ssIS](../includes/ssis-md.md)] 索引標籤的設計介面上，建構封裝中的資料流程。</span><span class="sxs-lookup"><span data-stu-id="c1122-103">You construct the data flow in a package on the design surface of the **Data Flow** tab in the [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="c1122-104">如果資料流程包含兩個資料流程元件，將來源或轉換的輸出連接到轉換或目的地的輸入，便可以連接這兩個元件。</span><span class="sxs-lookup"><span data-stu-id="c1122-104">If a data flow contains two data flow components, you can connect them by connecting the output of a source or transformation to the input of a transformation or destination.</span></span> <span data-ttu-id="c1122-105">兩個資料流程元件之間的連接子稱為路徑。</span><span class="sxs-lookup"><span data-stu-id="c1122-105">The connector between two data flow components is called a path.</span></span>

 <span data-ttu-id="c1122-106">下圖顯示的範例資料流程中，包含一個來源元件、兩個轉換、一個目的地元件，以及連接元件的路徑。</span><span class="sxs-lookup"><span data-stu-id="c1122-106">The following diagram shows a simple data flow with a source component, two transformations, a destination component, and the paths that connect them.</span></span>

 <span data-ttu-id="c1122-107">![](media/mw-dts-08.gif "設計師中")</span><span class="sxs-lookup"><span data-stu-id="c1122-107">![Data flow](media/mw-dts-08.gif "Data flow")</span></span>

 <span data-ttu-id="c1122-108">在連接兩個元件之後，您可以在 **[資料流程路徑編輯器]** 中，檢視經由路徑移動的資料之中繼資料，以及路徑的屬性。</span><span class="sxs-lookup"><span data-stu-id="c1122-108">After two components are connected, you can view the metadata of the data that moves through the path and the properties of the path in **Data Flow Path Editor**.</span></span> <span data-ttu-id="c1122-109">如需詳細資訊，請參閱 [Integration Services Paths](data-flow/integration-services-paths.md)。</span><span class="sxs-lookup"><span data-stu-id="c1122-109">For more information, see [Integration Services Paths](data-flow/integration-services-paths.md).</span></span>

 <span data-ttu-id="c1122-110">您也可以將資料檢視器加入路徑。</span><span class="sxs-lookup"><span data-stu-id="c1122-110">You can also add data viewers to paths.</span></span> <span data-ttu-id="c1122-111">資料檢視器可讓您在封裝執行時，檢視在資料流程元件之間移動的資料。</span><span class="sxs-lookup"><span data-stu-id="c1122-111">A data viewer makes it possible to view data moving between data flow components when the package is run.</span></span>

### <a name="to-connect-components-in-a-data-flow"></a><span data-ttu-id="c1122-112">連接資料流程中的元件</span><span class="sxs-lookup"><span data-stu-id="c1122-112">To connect components in a data flow</span></span>

-   [<span data-ttu-id="c1122-113">連接資料流程中的元件</span><span class="sxs-lookup"><span data-stu-id="c1122-113">Connect Components in a Data Flow</span></span>](data-flow/connect-components-in-a-data-flow.md)

### <a name="to-set-path-properties"></a><span data-ttu-id="c1122-114">設定路徑屬性</span><span class="sxs-lookup"><span data-stu-id="c1122-114">To set path properties</span></span>

-   [<span data-ttu-id="c1122-115">使用資料流程路徑編輯器來設定路徑的屬性</span><span class="sxs-lookup"><span data-stu-id="c1122-115">Set the Properties of a Path by Using the Data Flow Path Editor</span></span>](../../2014/integration-services/set-the-properties-of-a-path-by-using-the-data-flow-path-editor.md)

### <a name="to-view-path-metadata"></a><span data-ttu-id="c1122-116">若要檢視路徑中繼資料</span><span class="sxs-lookup"><span data-stu-id="c1122-116">To view path metadata</span></span>

-   [<span data-ttu-id="c1122-117">在資料流程路徑編輯器中檢視路徑中繼資料</span><span class="sxs-lookup"><span data-stu-id="c1122-117">View Path Metadata in the Data Flow Path Editor</span></span>](../../2014/integration-services/view-path-metadata-in-the-data-flow-path-editor.md)

### <a name="to-view-path-metadata"></a><span data-ttu-id="c1122-118">若要檢視路徑中繼資料</span><span class="sxs-lookup"><span data-stu-id="c1122-118">To view path metadata</span></span>

-   [<span data-ttu-id="c1122-119">將資料檢視器新增到資料流程</span><span class="sxs-lookup"><span data-stu-id="c1122-119">Add a Data Viewer to a Data Flow</span></span>](../../2014/integration-services/add-a-data-viewer-to-a-data-flow.md)

## <a name="see-also"></a><span data-ttu-id="c1122-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c1122-120">See Also</span></span>
 <span data-ttu-id="c1122-121">[資料流程工作](control-flow/data-flow-task.md)[資料流程](data-flow/data-flow.md)[轉換資料具有轉換](data-flow/transformations/transform-data-with-transformations.md)[中的錯誤處理資料](data-flow/error-handling-in-data.md)</span><span class="sxs-lookup"><span data-stu-id="c1122-121">[Data Flow Task](control-flow/data-flow-task.md) [Data Flow](data-flow/data-flow.md) [Transform Data with Transformations](data-flow/transformations/transform-data-with-transformations.md) [Error Handling in Data](data-flow/error-handling-in-data.md)</span></span>


