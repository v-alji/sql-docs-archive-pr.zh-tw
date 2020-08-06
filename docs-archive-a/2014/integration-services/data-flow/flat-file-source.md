---
title: 一般檔案來源 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.flatfilesource.f1
helpviewer_keywords:
- sources [Integration Services], Flat File
- text file reading [Integration Services]
- flat files
- Flat File source
ms.assetid: 4a64f7f3-f25d-4db0-93b3-a29496030e58
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b1ca0f38c457256b3f2ed2ddb81bfbd0dc06b6c0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709777"
---
# <a name="flat-file-source"></a><span data-ttu-id="4827c-102">一般檔案來源</span><span class="sxs-lookup"><span data-stu-id="4827c-102">Flat File Source</span></span>
  <span data-ttu-id="4827c-103">「一般檔案」來源會從文字檔讀取資料。</span><span class="sxs-lookup"><span data-stu-id="4827c-103">The Flat File source reads data from a text file.</span></span> <span data-ttu-id="4827c-104">文字檔可以是使用分隔符號、固定寬度或混合的格式。</span><span class="sxs-lookup"><span data-stu-id="4827c-104">The text file can be in delimited, fixed width, or mixed format.</span></span>  
  
-   <span data-ttu-id="4827c-105">分隔符號格式會使用資料行和資料列分隔符號，來定義資料行和資料列。</span><span class="sxs-lookup"><span data-stu-id="4827c-105">Delimited format uses column and row delimiters to define columns and rows.</span></span>  
  
-   <span data-ttu-id="4827c-106">固定寬度格式會使用寬度來定義資料行和資料列。</span><span class="sxs-lookup"><span data-stu-id="4827c-106">Fixed width format uses width to define columns and rows.</span></span> <span data-ttu-id="4827c-107">此格式亦包含將欄位填補成其最大寬度的字元。</span><span class="sxs-lookup"><span data-stu-id="4827c-107">This format also includes a character for padding fields to their maximum width.</span></span>  
  
-   <span data-ttu-id="4827c-108">不齊右格式會使用寬度來定義所有資料行，最後一個資料行除外，其是以資料列分隔符號所分隔。</span><span class="sxs-lookup"><span data-stu-id="4827c-108">Ragged right format uses width to define all columns, except for the last column, which is delimited by the row delimiter.</span></span>  
  
 <span data-ttu-id="4827c-109">您可以利用下列方式設定「一般檔案」來源：</span><span class="sxs-lookup"><span data-stu-id="4827c-109">You can configure the Flat File source in the following ways:</span></span>  
  
-   <span data-ttu-id="4827c-110">將資料行加入至轉換輸出，該輸出包含「一般檔案」來源從中擷取資料的文字檔檔名。</span><span class="sxs-lookup"><span data-stu-id="4827c-110">Add a column to the transformation output that contains the name of the text file from which the Flat File source extracts data.</span></span>  
  
-   <span data-ttu-id="4827c-111">指定「一般檔案」來源是否將資料行中的零長度字串解譯為 Null 值。</span><span class="sxs-lookup"><span data-stu-id="4827c-111">Specify whether the Flat File source interprets zero-length strings in columns as null values.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4827c-112">「一般檔案」來源使用的「一般檔案」連接管理員，必須設定成使用分隔符號格式將零長度字串解譯為 Null。</span><span class="sxs-lookup"><span data-stu-id="4827c-112">The Flat File connection manager that the Flat File source uses must be configured to use a delimited format to interpret zero-length strings as nulls.</span></span> <span data-ttu-id="4827c-113">如果連接管理員使用固定寬度或不齊右格式，則由空格組成的資料就無法解譯為 Null 值。</span><span class="sxs-lookup"><span data-stu-id="4827c-113">If the connection manager uses the fixed width or ragged right formats, data that consists of spaces cannot be interpreted as null values.</span></span>  
  
 <span data-ttu-id="4827c-114">一般檔案來源輸出中的輸出資料行包含 FastParse 屬性。</span><span class="sxs-lookup"><span data-stu-id="4827c-114">The output columns in the output of the Flat File source include the FastParse property.</span></span> <span data-ttu-id="4827c-115">FastParse 可指定資料行要使用 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 所提供之速度較快，但不區分地區設定的快速剖析常式，或要使用會區分地區設定的標準剖析常式。</span><span class="sxs-lookup"><span data-stu-id="4827c-115">FastParse indicates whether the column uses the quicker, but locale-insensitive, fast parsing routines that [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] provides or the locale-sensitive standard parsing routines.</span></span> <span data-ttu-id="4827c-116">如需詳細資訊，請參閱 [快速剖析](../fast-parse.md) 和 [標準剖析](../standard-parse.md)。</span><span class="sxs-lookup"><span data-stu-id="4827c-116">For more information, see [Fast Parse](../fast-parse.md) and [Standard Parse](../standard-parse.md).</span></span>  
  
 <span data-ttu-id="4827c-117">輸出資料行也包含 UseBinaryFormat 屬性。</span><span class="sxs-lookup"><span data-stu-id="4827c-117">Output columns also include the UseBinaryFormat property.</span></span> <span data-ttu-id="4827c-118">您可使用此屬性在檔案中實作二進位資料的支援，例如具有壓縮之十進位格式的資料。</span><span class="sxs-lookup"><span data-stu-id="4827c-118">You use this property to implement support for binary data, such as data with the packed decimal format, in files.</span></span> <span data-ttu-id="4827c-119">根據預設，UseBinaryFormat 會設定為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="4827c-119">By default UseBinaryFormat is set to `false`.</span></span> <span data-ttu-id="4827c-120">如果您想要使用二進位格式，請將 UseBinaryFormat 設為 `true` ，並將輸出資料行上的資料類型設定為 `DT_BYTES` 。</span><span class="sxs-lookup"><span data-stu-id="4827c-120">If you want to use a binary format, set UseBinaryFormat to `true` and the data type on the output column to `DT_BYTES`.</span></span> <span data-ttu-id="4827c-121">當您執行這個動作時，一般檔案來源會略過資料轉換，並將資料直接傳遞到輸出資料行。</span><span class="sxs-lookup"><span data-stu-id="4827c-121">When you do this, the Flat File source skips the data conversion and passes the data to the output column as is.</span></span> <span data-ttu-id="4827c-122">然後您就可以使用「衍生的資料行」或「資料轉換」等轉換，將 `DT_BYTES` 資料轉換成不同的資料類型，或者您可以在「指令碼」轉換中撰寫自訂指令碼來解譯資料。</span><span class="sxs-lookup"><span data-stu-id="4827c-122">You can then use a transformation such as the Derived Column or Data Conversion to cast the `DT_BYTES` data to a different data type, or you can write custom script in a Script transformation to interpret the data.</span></span> <span data-ttu-id="4827c-123">您也可以撰寫自訂的資料流程元件來解譯資料。</span><span class="sxs-lookup"><span data-stu-id="4827c-123">You can also write a custom data flow component to interpret the data.</span></span> <span data-ttu-id="4827c-124">如需您可以轉換成哪些資料類型的詳細資訊 `DT_BYTES` ，請參閱[CAST &#40;SSIS 運算式&#41;](../expressions/cast-ssis-expression.md)。</span><span class="sxs-lookup"><span data-stu-id="4827c-124">For more information about which data types you can cast `DT_BYTES` to, see [Cast &#40;SSIS Expression&#41;](../expressions/cast-ssis-expression.md).</span></span>  
  
 <span data-ttu-id="4827c-125">此來源使用「一般檔案」連接管理員存取文字檔。</span><span class="sxs-lookup"><span data-stu-id="4827c-125">This source uses a Flat File connection manager to access the text file.</span></span> <span data-ttu-id="4827c-126">藉由設定「一般檔案」連接管理員上的屬性，即可提供有關該檔案及其中各資料行的資訊，以及指定「一般檔案」來源應如何處理文字檔中的資料。</span><span class="sxs-lookup"><span data-stu-id="4827c-126">By setting properties on the Flat File connection manager, you can provide information about the file and each column in it, and specify how the Flat File source should handle the data in the text file.</span></span> <span data-ttu-id="4827c-127">例如，您可以指定分隔檔案中資料行和資料列的字元，以及各資料行的資料類型和長度。</span><span class="sxs-lookup"><span data-stu-id="4827c-127">For example, you can specify the characters that delimit columns and rows in the file, and the data type and the length of each column.</span></span> <span data-ttu-id="4827c-128">如需相關資訊，請參閱 [Flat File Connection Manager](../connection-manager/file-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="4827c-128">For more information, see [Flat File Connection Manager](../connection-manager/file-connection-manager.md).</span></span>  
  
 <span data-ttu-id="4827c-129">此來源有一個輸出和一個錯誤輸出。</span><span class="sxs-lookup"><span data-stu-id="4827c-129">This source has one output and one error output.</span></span>  
  
## <a name="configuration-of-the-flat-file-source"></a><span data-ttu-id="4827c-130">設定一般檔案來源</span><span class="sxs-lookup"><span data-stu-id="4827c-130">Configuration of the Flat File Source</span></span>  
 <span data-ttu-id="4827c-131">您可以透過 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師或以程式設計方式設定屬性。</span><span class="sxs-lookup"><span data-stu-id="4827c-131">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="4827c-132">如需有關 **[一般檔案來源編輯器]** 對話方塊中可設定屬性的詳細資訊，請按一下下列其中一個主題：</span><span class="sxs-lookup"><span data-stu-id="4827c-132">For more information about the properties that you can set in the **Flat File Source Editor** dialog box, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="4827c-133">一般檔案來源編輯器 &#40;連線管理員頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="4827c-133">Flat File Source Editor &#40;Connection Manager Page&#41;</span></span>](../flat-file-source-editor-connection-manager-page.md)  
  
-   [<span data-ttu-id="4827c-134">一般檔案來源編輯器 &#40;資料行頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="4827c-134">Flat File Source Editor &#40;Columns Page&#41;</span></span>](../flat-file-source-editor-columns-page.md)  
  
-   [<span data-ttu-id="4827c-135">一般檔案來源編輯器 &#40;錯誤輸出頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="4827c-135">Flat File Source Editor &#40;Error Output Page&#41;</span></span>](../flat-file-source-editor-error-output-page.md)  
  
 <span data-ttu-id="4827c-136">**[進階編輯器]** 對話方塊會反映能以程式設計的方式設定之屬性。</span><span class="sxs-lookup"><span data-stu-id="4827c-136">The **Advanced Editor** dialog box reflects the properties that can be set programmatically.</span></span> <span data-ttu-id="4827c-137">如需有關可以在 **[進階編輯器]** 對話方塊中或以程式設計方式設定之屬性的詳細資訊，請按下列其中一個主題：</span><span class="sxs-lookup"><span data-stu-id="4827c-137">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="4827c-138">Common Properties</span><span class="sxs-lookup"><span data-stu-id="4827c-138">Common Properties</span></span>](../common-properties.md)  
  
-   [<span data-ttu-id="4827c-139">一般檔案自訂屬性</span><span class="sxs-lookup"><span data-stu-id="4827c-139">Flat File Custom Properties</span></span>](flat-file-custom-properties.md)  
  
## <a name="related-tasks"></a><span data-ttu-id="4827c-140">相關工作</span><span class="sxs-lookup"><span data-stu-id="4827c-140">Related Tasks</span></span>  
 <span data-ttu-id="4827c-141">如需如何設定資料流程元件屬性的詳細資訊，請參閱 [Set the Properties of a Data Flow Component](set-the-properties-of-a-data-flow-component.md)(設定資料流程元件的屬性)。</span><span class="sxs-lookup"><span data-stu-id="4827c-141">For details about how to set properties of a data flow component, see [Set the Properties of a Data Flow Component](set-the-properties-of-a-data-flow-component.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4827c-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4827c-142">See Also</span></span>  
 <span data-ttu-id="4827c-143">[一般檔案目的地](flat-file-destination.md) </span><span class="sxs-lookup"><span data-stu-id="4827c-143">[Flat File Destination](flat-file-destination.md) </span></span>  
 [<span data-ttu-id="4827c-144">資料流程</span><span class="sxs-lookup"><span data-stu-id="4827c-144">Data Flow</span></span>](data-flow.md)  
  
  
