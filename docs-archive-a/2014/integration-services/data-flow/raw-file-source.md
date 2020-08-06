---
title: 原始檔案來源 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.rawfilesource.f1
helpviewer_keywords:
- sources [Integration Services], Raw File
- raw data [Integration Services]
- Raw File source
ms.assetid: 5b4daea5-7f76-4674-aa77-0a79f9f97f7d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4cbc5800c4fb2b90b74e66b6ff161118b2b550f2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593463"
---
# <a name="raw-file-source"></a><span data-ttu-id="3a7e4-102">原始檔案來源</span><span class="sxs-lookup"><span data-stu-id="3a7e4-102">Raw File Source</span></span>
  <span data-ttu-id="3a7e4-103">「原始檔案」來源會從檔案讀取原始資料。</span><span class="sxs-lookup"><span data-stu-id="3a7e4-103">The Raw File source reads raw data from a file.</span></span> <span data-ttu-id="3a7e4-104">由於資料的表示法對於來源而言是原生的，因此資料不需翻譯，也幾乎不需要剖析。</span><span class="sxs-lookup"><span data-stu-id="3a7e4-104">Because the representation of the data is native to the source, the data requires no translation and almost no parsing.</span></span> <span data-ttu-id="3a7e4-105">這表示，「原始檔案」來源可比其他來源更快讀取資料，例如「一般檔案」和 OLE DB 來源。</span><span class="sxs-lookup"><span data-stu-id="3a7e4-105">This means that the Raw File source can read data more quickly than other sources such as the Flat File and the OLE DB sources.</span></span>  
  
 <span data-ttu-id="3a7e4-106">「原始檔案」來源是用來擷取之前由「原始檔案」目的地撰寫的原始資料。</span><span class="sxs-lookup"><span data-stu-id="3a7e4-106">The Raw File source is used to retrieve raw data that was previously written by the Raw File destination.</span></span> <span data-ttu-id="3a7e4-107">您也可以將原始檔案來源指向僅包含資料行 (僅中繼資料的檔案) 的空白原始檔案。</span><span class="sxs-lookup"><span data-stu-id="3a7e4-107">You can also point the Raw File source to an empty raw file that contains only the columns (metadata-only file).</span></span> <span data-ttu-id="3a7e4-108">您可以使用原始檔案目的地產生僅中繼資料的檔案，而不必執行封裝。</span><span class="sxs-lookup"><span data-stu-id="3a7e4-108">You use the Raw File destination to generate the metadata-only file without having to run the package.</span></span> <span data-ttu-id="3a7e4-109">如需相關資訊，請參閱 [Raw File Destination](raw-file-destination.md)。</span><span class="sxs-lookup"><span data-stu-id="3a7e4-109">For more information, see [Raw File Destination](raw-file-destination.md).</span></span>  
  
 <span data-ttu-id="3a7e4-110">原始檔案格式包含排序資訊。</span><span class="sxs-lookup"><span data-stu-id="3a7e4-110">The raw file format contains sort information.</span></span> <span data-ttu-id="3a7e4-111">原始檔案目的地會儲存所有排序資訊，包括字串資料行的比較旗標。</span><span class="sxs-lookup"><span data-stu-id="3a7e4-111">The Raw File Destination saves all the sort information including the comparison flags for string columns.</span></span> <span data-ttu-id="3a7e4-112">原始檔案來源會讀取並接受排序資訊。</span><span class="sxs-lookup"><span data-stu-id="3a7e4-112">The Raw File source reads and honors the sort information.</span></span> <span data-ttu-id="3a7e4-113">您可以使用進階編輯器，選擇將原始檔案來源設定為忽略檔案中的排序旗標。</span><span class="sxs-lookup"><span data-stu-id="3a7e4-113">You do have the option of configuring the Raw File Source to ignore the sort flags in the file, using the Advanced Editor.</span></span> <span data-ttu-id="3a7e4-114">如需比較旗標的詳細資訊，請參閱 [比較字串資料](comparing-string-data.md)。</span><span class="sxs-lookup"><span data-stu-id="3a7e4-114">For more information about comparison flags, see [Comparing String Data](comparing-string-data.md).</span></span>  
  
 <span data-ttu-id="3a7e4-115">您可指定「原始檔案」來源讀取的檔名，藉此設定「原始檔案」。</span><span class="sxs-lookup"><span data-stu-id="3a7e4-115">You configure the Raw File by specifying the name of the name of the file that the Raw File source reads.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3a7e4-116">此來源不會使用連接管理員。</span><span class="sxs-lookup"><span data-stu-id="3a7e4-116">This source does not use a connection manager.</span></span>  
  
 <span data-ttu-id="3a7e4-117">此來源擁有一個輸出。</span><span class="sxs-lookup"><span data-stu-id="3a7e4-117">This source has one output.</span></span> <span data-ttu-id="3a7e4-118">它不支援錯誤輸出。</span><span class="sxs-lookup"><span data-stu-id="3a7e4-118">It does not support an error output.</span></span>  
  
## <a name="configuration-of-the-raw-file-source"></a><span data-ttu-id="3a7e4-119">設定原始檔案來源</span><span class="sxs-lookup"><span data-stu-id="3a7e4-119">Configuration of the Raw File Source</span></span>  
 <span data-ttu-id="3a7e4-120">您可以透過 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師或以程式設計方式設定屬性。</span><span class="sxs-lookup"><span data-stu-id="3a7e4-120">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="3a7e4-121">**[進階編輯器]** 對話方塊會反映能以程式設計的方式設定之屬性。</span><span class="sxs-lookup"><span data-stu-id="3a7e4-121">The **Advanced Editor** dialog box reflects the properties that can be set programmatically.</span></span> <span data-ttu-id="3a7e4-122">如需有關可以在 **[進階編輯器]** 對話方塊中或以程式設計方式設定之屬性的詳細資訊，請按下列其中一個主題：</span><span class="sxs-lookup"><span data-stu-id="3a7e4-122">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="3a7e4-123">Common Properties</span><span class="sxs-lookup"><span data-stu-id="3a7e4-123">Common Properties</span></span>](../common-properties.md)  
  
-   [<span data-ttu-id="3a7e4-124">原始檔案自訂屬性</span><span class="sxs-lookup"><span data-stu-id="3a7e4-124">Raw File Custom Properties</span></span>](raw-file-custom-properties.md)  
  
## <a name="related-tasks"></a><span data-ttu-id="3a7e4-125">相關工作</span><span class="sxs-lookup"><span data-stu-id="3a7e4-125">Related Tasks</span></span>  
 <span data-ttu-id="3a7e4-126">如需如何設定此元件屬性的資訊，請參閱 [設定資料流程元件的屬性](set-the-properties-of-a-data-flow-component.md)。</span><span class="sxs-lookup"><span data-stu-id="3a7e4-126">For information about how to set the properties of the component, see [Set the Properties of a Data Flow Component](set-the-properties-of-a-data-flow-component.md).</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="3a7e4-127">相關內容</span><span class="sxs-lookup"><span data-stu-id="3a7e4-127">Related Content</span></span>  
  
-   <span data-ttu-id="3a7e4-128">sqlservercentral.com 上的部落格文章： [Raw Files Are Awesome](https://www.sqlservercentral.com/blogs/31-days-of-ssis-%e2%80%93-raw-files-are-awesome-131)(原始檔案太酷了)</span><span class="sxs-lookup"><span data-stu-id="3a7e4-128">Blog entry, [Raw Files Are Awesome](https://www.sqlservercentral.com/blogs/31-days-of-ssis-%e2%80%93-raw-files-are-awesome-131), on sqlservercentral.com</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a7e4-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3a7e4-129">See Also</span></span>  
 <span data-ttu-id="3a7e4-130">[原始檔案目的地](raw-file-destination.md) </span><span class="sxs-lookup"><span data-stu-id="3a7e4-130">[Raw File Destination](raw-file-destination.md) </span></span>  
 [<span data-ttu-id="3a7e4-131">資料流程</span><span class="sxs-lookup"><span data-stu-id="3a7e4-131">Data Flow</span></span>](data-flow.md)  
  
  
