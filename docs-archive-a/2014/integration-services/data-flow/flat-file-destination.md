---
title: 一般檔案目的地 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.flatfiledest.f1
helpviewer_keywords:
- flat files
- Flat File destination
- text file writing [Integration Services]
- destinations [Integration Services], Flat File
ms.assetid: e0d6e356-8db4-48aa-ba66-029397f98f61
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a961b7528b13a4eaa3297343e91f1deaf2fa3226
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709778"
---
# <a name="flat-file-destination"></a><span data-ttu-id="47a72-102">一般檔案目的地</span><span class="sxs-lookup"><span data-stu-id="47a72-102">Flat File Destination</span></span>
  <span data-ttu-id="47a72-103">「一般檔案」目的地會將資料寫入文字檔。</span><span class="sxs-lookup"><span data-stu-id="47a72-103">The Flat File destination writes data to a text file.</span></span> <span data-ttu-id="47a72-104">該文字檔的格式可以是使用分隔符號、固定寬度、具有資料列分隔符號的固定寬度，或不齊右。</span><span class="sxs-lookup"><span data-stu-id="47a72-104">The text file can be in delimited, fixed width, fixed width with row delimiter, or ragged right format.</span></span>  
  
 <span data-ttu-id="47a72-105">您可以利用下列方式設定「一般檔案」目的地：</span><span class="sxs-lookup"><span data-stu-id="47a72-105">You can configure the Flat File destination in the following ways:</span></span>  
  
-   <span data-ttu-id="47a72-106">提供寫入任何資料前插入到檔案的文字區塊。</span><span class="sxs-lookup"><span data-stu-id="47a72-106">Provide a block of text that is inserted in the file before any data is written.</span></span> <span data-ttu-id="47a72-107">該文字可提供如資料行標題等資訊。</span><span class="sxs-lookup"><span data-stu-id="47a72-107">The text can provide information such as column headings.</span></span>  
  
-   <span data-ttu-id="47a72-108">指定是否覆寫同名目的地檔案中的資料。</span><span class="sxs-lookup"><span data-stu-id="47a72-108">Specify whether to overwrite a data in a destination file that has the same name.</span></span>  
  
 <span data-ttu-id="47a72-109">此目的地使用「一般檔案」連接管理員來存取文字檔。</span><span class="sxs-lookup"><span data-stu-id="47a72-109">This destination uses a Flat File connection manager to access the text file.</span></span> <span data-ttu-id="47a72-110">透過設定「一般檔案」目的地使用之「一般檔案」連接管理員上的屬性，您可以指定「一般檔案」目的地如何格式化並寫入文字檔。</span><span class="sxs-lookup"><span data-stu-id="47a72-110">By setting properties on the Flat File connection manager that the Flat File destination uses, you can specify how the Flat File destination formats and writes the text file.</span></span> <span data-ttu-id="47a72-111">設定「一般檔案」連接管理員時，可以指定有關該檔案以及檔案中每一資料行的資訊。</span><span class="sxs-lookup"><span data-stu-id="47a72-111">When you configure the Flat File connection manager, you specify information about the file and about each column in the file.</span></span> <span data-ttu-id="47a72-112">例如，指定分隔檔案中資料行和資料列的字元，以及各資料行的資料類型和長度。</span><span class="sxs-lookup"><span data-stu-id="47a72-112">For example, you specify the characters that delimit columns and rows in the file, and you specify the data type and the length of each column.</span></span> <span data-ttu-id="47a72-113">如需相關資訊，請參閱 [Flat File Connection Manager](../connection-manager/file-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="47a72-113">For more information, see [Flat File Connection Manager](../connection-manager/file-connection-manager.md).</span></span>  
  
 <span data-ttu-id="47a72-114">一般檔案目的地包含 [標頭] 自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="47a72-114">The Flat File destination includes the Header custom property.</span></span> <span data-ttu-id="47a72-115">屬性運算式可以在載入封裝時更新這個屬性。</span><span class="sxs-lookup"><span data-stu-id="47a72-115">This property can be updated by a property expression when the package is loaded.</span></span> <span data-ttu-id="47a72-116">如需詳細資訊，請參閱 [Integration Services &#40;SSIS&#41; 運算式](../expressions/integration-services-ssis-expressions.md)、[在封裝中使用屬性運算式](../expressions/use-property-expressions-in-packages.md)和[一般檔案自訂屬性](flat-file-custom-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="47a72-116">For more information, see [Integration Services &#40;SSIS&#41; Expressions](../expressions/integration-services-ssis-expressions.md), [Use Property Expressions in Packages](../expressions/use-property-expressions-in-packages.md), and [Flat File Custom Properties](flat-file-custom-properties.md).</span></span>  
  
 <span data-ttu-id="47a72-117">此目的地擁有一個輸出。</span><span class="sxs-lookup"><span data-stu-id="47a72-117">This destination has one output.</span></span> <span data-ttu-id="47a72-118">它不支援錯誤輸出。</span><span class="sxs-lookup"><span data-stu-id="47a72-118">It does not support an error output.</span></span>  
  
## <a name="configuration-of-the-flat-file-destination"></a><span data-ttu-id="47a72-119">一般檔案目的地的組態</span><span class="sxs-lookup"><span data-stu-id="47a72-119">Configuration of the Flat File Destination</span></span>  
 <span data-ttu-id="47a72-120">您可以透過 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師或以程式設計方式設定屬性。</span><span class="sxs-lookup"><span data-stu-id="47a72-120">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="47a72-121">如需有關 **[一般檔案來源編輯器]** 對話方塊中可設定屬性的詳細資訊，請按一下下列其中一個主題：</span><span class="sxs-lookup"><span data-stu-id="47a72-121">For more information about the properties that you can set in the **Flat File Source Editor** dialog box, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="47a72-122">一般檔案目的地編輯器 &#40;連線管理員頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="47a72-122">Flat File Destination Editor &#40;Connection Manager Page&#41;</span></span>](../flat-file-destination-editor-connection-manager-page.md)  
  
-   [<span data-ttu-id="47a72-123">一般檔案目的地編輯器 &#40;對應頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="47a72-123">Flat File Destination Editor &#40;Mappings Page&#41;</span></span>](../flat-file-destination-editor-mappings-page.md)  
  
 <span data-ttu-id="47a72-124">**[進階編輯器]** 對話方塊會反映能以程式設計的方式設定之屬性。</span><span class="sxs-lookup"><span data-stu-id="47a72-124">The **Advanced Editor** dialog box reflects the properties that can be set programmatically.</span></span> <span data-ttu-id="47a72-125">如需有關可以在 **[進階編輯器]** 對話方塊中或以程式設計方式設定之屬性的詳細資訊，請按下列其中一個主題：</span><span class="sxs-lookup"><span data-stu-id="47a72-125">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="47a72-126">Common Properties</span><span class="sxs-lookup"><span data-stu-id="47a72-126">Common Properties</span></span>](../common-properties.md)  
  
-   [<span data-ttu-id="47a72-127">一般檔案自訂屬性</span><span class="sxs-lookup"><span data-stu-id="47a72-127">Flat File Custom Properties</span></span>](flat-file-custom-properties.md)  
  
## <a name="related-tasks"></a><span data-ttu-id="47a72-128">相關工作</span><span class="sxs-lookup"><span data-stu-id="47a72-128">Related Tasks</span></span>  
 <span data-ttu-id="47a72-129">如需如何設定資料流程元件屬性的資訊，請參閱 [設定資料流程元件的屬性](set-the-properties-of-a-data-flow-component.md)。</span><span class="sxs-lookup"><span data-stu-id="47a72-129">For information about how to set the properties of a data flow component, see [Set the Properties of a Data Flow Component](set-the-properties-of-a-data-flow-component.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47a72-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="47a72-130">See Also</span></span>  
 <span data-ttu-id="47a72-131">[一般檔案來源](flat-file-source.md) </span><span class="sxs-lookup"><span data-stu-id="47a72-131">[Flat File Source](flat-file-source.md) </span></span>  
 [<span data-ttu-id="47a72-132">資料流程</span><span class="sxs-lookup"><span data-stu-id="47a72-132">Data Flow</span></span>](data-flow.md)  
  
  
