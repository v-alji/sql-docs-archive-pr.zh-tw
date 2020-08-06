---
title: 使用轉換來轉換資料 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- data flow [Integration Services], transformations
- transformations [Integration Services], about transformations
- transforming data [Integration Services]
ms.assetid: e1340b6f-ef75-4b14-af6f-823586eff0ed
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 952d8ea4eeea2dd8010a17a2b3deba41447b6231
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606434"
---
# <a name="transform-data-with-transformations"></a><span data-ttu-id="e008e-102">使用轉換來轉換資料</span><span class="sxs-lookup"><span data-stu-id="e008e-102">Transform Data with Transformations</span></span>
  [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] <span data-ttu-id="e008e-103">包含三種類型的資料流程元件：來源、轉換與目的地。</span><span class="sxs-lookup"><span data-stu-id="e008e-103">includes three types of data flow components: sources, transformations, and destinations.</span></span>  
  
 <span data-ttu-id="e008e-104">下圖顯示包含一個來源、兩個轉換及一個目的地的簡單資料流程。</span><span class="sxs-lookup"><span data-stu-id="e008e-104">The following diagram shows a simple data flow that has a source, two transformations, and a destination.</span></span>  
  
 <span data-ttu-id="e008e-105">![](../../media/mw-dts-08.gif "設計師中")</span><span class="sxs-lookup"><span data-stu-id="e008e-105">![Data flow](../../media/mw-dts-08.gif "Data flow")</span></span>  
  
 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] <span data-ttu-id="e008e-106">轉換提供下列功能：</span><span class="sxs-lookup"><span data-stu-id="e008e-106">transformations provide the following functionality:</span></span>  
  
-   <span data-ttu-id="e008e-107">分割、複製以及合併資料列集，並執行查閱作業。</span><span class="sxs-lookup"><span data-stu-id="e008e-107">Splitting, copying, and merging rowsets and performing lookup operations.</span></span>  
  
-   <span data-ttu-id="e008e-108">透過套用轉換，例如變更小寫為大寫，來更新資料行值及新建資料行。</span><span class="sxs-lookup"><span data-stu-id="e008e-108">Updating column values and creating new columns by applying transformations such as changing lowercase to uppercase.</span></span>  
  
-   <span data-ttu-id="e008e-109">執行商業智慧作業，例如清除資料、採礦文字或執行資料採礦預測查詢等。</span><span class="sxs-lookup"><span data-stu-id="e008e-109">Performing business intelligence operations such as cleaning data, mining text, or running data mining prediction queries.</span></span>  
  
-   <span data-ttu-id="e008e-110">新建包含彙總值或排序值、範例資料或樞紐和取消樞紐資料的資料列集。</span><span class="sxs-lookup"><span data-stu-id="e008e-110">Creating new rowsets that consist of aggregate or sorted values, sample data, or pivoted and unpivoted data.</span></span>  
  
-   <span data-ttu-id="e008e-111">執行例如匯出和匯入資料、提供稽核資訊以及使用緩時變維度等工作。</span><span class="sxs-lookup"><span data-stu-id="e008e-111">Performing tasks such as exporting and importing data, providing audit information, and working with slowly changing dimensions.</span></span>  
  
 <span data-ttu-id="e008e-112">如需詳細資訊，請參閱 [Integration Services 轉換](integration-services-transformations.md)。</span><span class="sxs-lookup"><span data-stu-id="e008e-112">For more information, see [Integration Services Transformations](integration-services-transformations.md).</span></span>  
  
 <span data-ttu-id="e008e-113">您也可以撰寫自訂轉換。</span><span class="sxs-lookup"><span data-stu-id="e008e-113">You can also write custom transformations.</span></span> <span data-ttu-id="e008e-114">如需詳細資訊，請參閱 [開發自訂資料流程元件](../../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md) 和 [開發特定類型的資料流程元件](../../extending-packages-custom-objects-data-flow-types/developing-specific-types-of-data-flow-components.md)。</span><span class="sxs-lookup"><span data-stu-id="e008e-114">For more information, see [Developing a Custom Data Flow Component](../../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md) and [Developing Specific Types of Data Flow Components](../../extending-packages-custom-objects-data-flow-types/developing-specific-types-of-data-flow-components.md).</span></span>  
  
 <span data-ttu-id="e008e-115">在將轉換加入資料流程設計師之後，設定轉換之前，您可以透過將資料流程中另一轉換或來源的輸出連接到轉換的輸入，以將此轉換連接到資料流程。</span><span class="sxs-lookup"><span data-stu-id="e008e-115">After you add the transformation to the data flow designer, but before you configure the transformation, you connect the transformation to the data flow by connecting the output of another transformation or source in the data flow to the input of this transformation.</span></span> <span data-ttu-id="e008e-116">兩個資料流程元件之間的連接子稱為路徑。</span><span class="sxs-lookup"><span data-stu-id="e008e-116">The connector between two data flow components is called a path.</span></span> <span data-ttu-id="e008e-117">如需連接元件以及使用路徑的詳細資訊，請參閱 [以路徑連接元件](../../connect-components-with-paths.md)。</span><span class="sxs-lookup"><span data-stu-id="e008e-117">For more information about connecting components and working with paths, see [Connect Components with Paths](../../connect-components-with-paths.md).</span></span>  
  
### <a name="to-add-a-transformation-to-a-data-flow"></a><span data-ttu-id="e008e-118">將轉換加入資料流程</span><span class="sxs-lookup"><span data-stu-id="e008e-118">To add a transformation to a data flow</span></span>  
  
-   [<span data-ttu-id="e008e-119">在資料流程中加入或刪除元件</span><span class="sxs-lookup"><span data-stu-id="e008e-119">Add or Delete a Component in a Data Flow</span></span>](../add-or-delete-a-component-in-a-data-flow.md)  
  
### <a name="to-connect-a-transformation-to-a-data-flow"></a><span data-ttu-id="e008e-120">將轉換連接到資料流程</span><span class="sxs-lookup"><span data-stu-id="e008e-120">To connect a transformation to a data flow</span></span>  
  
-   [<span data-ttu-id="e008e-121">連接資料流程中的元件</span><span class="sxs-lookup"><span data-stu-id="e008e-121">Connect Components in a Data Flow</span></span>](../connect-components-in-a-data-flow.md)  
  
### <a name="to-set-the-properties-of-a-transformation"></a><span data-ttu-id="e008e-122">設定轉換的屬性</span><span class="sxs-lookup"><span data-stu-id="e008e-122">To set the properties of a transformation</span></span>  
  
-   [<span data-ttu-id="e008e-123">設定資料流程元件的屬性</span><span class="sxs-lookup"><span data-stu-id="e008e-123">Set the Properties of a Data Flow Component</span></span>](../set-the-properties-of-a-data-flow-component.md)  
  
## <a name="see-also"></a><span data-ttu-id="e008e-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e008e-124">See Also</span></span>  
 <span data-ttu-id="e008e-125">[資料流程工作](../../control-flow/data-flow-task.md) </span><span class="sxs-lookup"><span data-stu-id="e008e-125">[Data Flow Task](../../control-flow/data-flow-task.md) </span></span>  
 <span data-ttu-id="e008e-126">[資料流程](../data-flow.md) </span><span class="sxs-lookup"><span data-stu-id="e008e-126">[Data Flow](../data-flow.md) </span></span>  
 <span data-ttu-id="e008e-127">[以路徑連接元件](../../connect-components-with-paths.md) </span><span class="sxs-lookup"><span data-stu-id="e008e-127">[Connect Components with Paths](../../connect-components-with-paths.md) </span></span>  
 <span data-ttu-id="e008e-128">[資料中的錯誤處理](../error-handling-in-data.md) </span><span class="sxs-lookup"><span data-stu-id="e008e-128">[Error Handling in Data](../error-handling-in-data.md) </span></span>  
 [<span data-ttu-id="e008e-129">資料流程</span><span class="sxs-lookup"><span data-stu-id="e008e-129">Data Flow</span></span>](../data-flow.md)  
  
  
