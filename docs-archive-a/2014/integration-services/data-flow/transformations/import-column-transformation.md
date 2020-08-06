---
title: 匯入資料行轉換 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.importcolumntrans.f1
helpviewer_keywords:
- Import Column transformation [Integration Services]
- columns [Integration Services], importing
- importing data, SSIS packages
- inserting data
ms.assetid: ac3b74c1-ef54-4297-8062-1734324fffcc
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f4330438614cce7892e74dc9a1dcbb6680b72972
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599102"
---
# <a name="import-column-transformation"></a><span data-ttu-id="222d5-102">匯入資料行轉換</span><span class="sxs-lookup"><span data-stu-id="222d5-102">Import Column Transformation</span></span>
  <span data-ttu-id="222d5-103">「匯入資料行」轉換會從檔案讀取資料，並將資料加入至資料流程中的資料行。</span><span class="sxs-lookup"><span data-stu-id="222d5-103">The Import Column transformation reads data from files and adds the data to columns in a data flow.</span></span> <span data-ttu-id="222d5-104">封裝可使用此轉換將其他檔案中儲存的文字和影像加入至資料流程。</span><span class="sxs-lookup"><span data-stu-id="222d5-104">Using this transformation, a package can add text and images stored in separate files to a data flow.</span></span> <span data-ttu-id="222d5-105">例如，將資料載入儲存產品資訊之資料表中的資料流程，即可加入「匯入資料行」轉換，以便從檔案匯入客戶對每項產品的檢閱，然後將檢閱加入至資料流程。</span><span class="sxs-lookup"><span data-stu-id="222d5-105">For example, a data flow that loads data into a table that stores product information can include the Import Column transformation to import customer reviews of each product from files and add the reviews to the data flow.</span></span>  
  
 <span data-ttu-id="222d5-106">您可以利用下列方式設定「匯入資料行」轉換：</span><span class="sxs-lookup"><span data-stu-id="222d5-106">You can configure the Import Column transformation in the following ways:</span></span>  
  
-   <span data-ttu-id="222d5-107">指定轉換要加入資料的資料行。</span><span class="sxs-lookup"><span data-stu-id="222d5-107">Specify the columns to which the transformation adds data.</span></span>  
  
-   <span data-ttu-id="222d5-108">指定轉換是否需要位元組順序標示 (BOM)。</span><span class="sxs-lookup"><span data-stu-id="222d5-108">Specify whether the transformation expects a byte-order mark (BOM).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="222d5-109">BOM 只有在資料的資料類型為 DT_NTEXT 時才需要。</span><span class="sxs-lookup"><span data-stu-id="222d5-109">A BOM is only expected if the data has the DT_NTEXT data type.</span></span>  
  
 <span data-ttu-id="222d5-110">轉換輸入中的資料行包含擁有該資料的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="222d5-110">A column in the transformation input contains the names of files that hold the data.</span></span> <span data-ttu-id="222d5-111">資料集中的每一個資料列都可指定不同的檔案。</span><span class="sxs-lookup"><span data-stu-id="222d5-111">Each row in the dataset can specify a different file.</span></span> <span data-ttu-id="222d5-112">當「匯入資料行」轉換處理某一個資料列時，會讀取檔名、開啟檔案系統中對應的檔案，以及將檔案內容載入輸出資料行。</span><span class="sxs-lookup"><span data-stu-id="222d5-112">When the Import Column transformation processes a row, it reads the file name, opens the corresponding file in the file system, and loads the file content into an output column.</span></span> <span data-ttu-id="222d5-113">輸出資料行的資料類型必須為 DT_TEXT、DT_NTEXT 或 DT_IMAGE。</span><span class="sxs-lookup"><span data-stu-id="222d5-113">The data type of the output column must be DT_TEXT, DT_NTEXT, or DT_IMAGE.</span></span> <span data-ttu-id="222d5-114">如需詳細資訊，請參閱 [Integration Services 資料類型](../integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="222d5-114">For more information, see [Integration Services Data Types](../integration-services-data-types.md).</span></span>  
  
 <span data-ttu-id="222d5-115">這個轉換有一個輸入、一個輸出與一個錯誤輸出。</span><span class="sxs-lookup"><span data-stu-id="222d5-115">This transformation has one input, one output, and one error output.</span></span>  
  
## <a name="configuration-of-the-import-column-transformation"></a><span data-ttu-id="222d5-116">匯入資料行轉換的組態</span><span class="sxs-lookup"><span data-stu-id="222d5-116">Configuration of the Import Column Transformation</span></span>  
 <span data-ttu-id="222d5-117">您可以透過 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 設計師或以程式設計方式設定屬性。</span><span class="sxs-lookup"><span data-stu-id="222d5-117">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="222d5-118">**[進階編輯器]** 對話方塊會反映能以程式設計的方式設定之屬性。</span><span class="sxs-lookup"><span data-stu-id="222d5-118">The **Advanced Editor** dialog box reflects the properties that can be set programmatically.</span></span> <span data-ttu-id="222d5-119">如需有關可以在 **[進階編輯器]** 對話方塊中或以程式設計方式設定之屬性的詳細資訊，請按下列其中一個主題：</span><span class="sxs-lookup"><span data-stu-id="222d5-119">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="222d5-120">Common Properties</span><span class="sxs-lookup"><span data-stu-id="222d5-120">Common Properties</span></span>](../../common-properties.md)  
  
-   [<span data-ttu-id="222d5-121">轉換自訂屬性</span><span class="sxs-lookup"><span data-stu-id="222d5-121">Transformation Custom Properties</span></span>](transformation-custom-properties.md)  
  
## <a name="related-tasks"></a><span data-ttu-id="222d5-122">相關工作</span><span class="sxs-lookup"><span data-stu-id="222d5-122">Related Tasks</span></span>  
 <span data-ttu-id="222d5-123">如需如何設定此元件屬性的資訊，請參閱 [設定資料流程元件的屬性](../set-the-properties-of-a-data-flow-component.md)。</span><span class="sxs-lookup"><span data-stu-id="222d5-123">For information about how to set properties of this component, see [Set the Properties of a Data Flow Component](../set-the-properties-of-a-data-flow-component.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="222d5-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="222d5-124">See Also</span></span>  
 <span data-ttu-id="222d5-125">[匯出資料行轉換](export-column-transformation.md) </span><span class="sxs-lookup"><span data-stu-id="222d5-125">[Export Column Transformation](export-column-transformation.md) </span></span>  
 <span data-ttu-id="222d5-126">[資料流程](../data-flow.md) </span><span class="sxs-lookup"><span data-stu-id="222d5-126">[Data Flow](../data-flow.md) </span></span>  
 [<span data-ttu-id="222d5-127">Integration Services 轉換</span><span class="sxs-lookup"><span data-stu-id="222d5-127">Integration Services Transformations</span></span>](integration-services-transformations.md)  
  
  
