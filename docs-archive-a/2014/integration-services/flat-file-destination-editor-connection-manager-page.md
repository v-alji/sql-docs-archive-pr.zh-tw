---
title: '[一般檔案目的地編輯器] (連線管理員頁面) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.flatfiledestadapter.connection.f1
helpviewer_keywords:
- Flat File Destination Editor
ms.assetid: b01571fa-bc19-4742-8eed-ac163172a919
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 6997b72851c2b7bfc56445e6ddb01cfe6e9b04cd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592152"
---
# <a name="flat-file-destination-editor-connection-manager-page"></a><span data-ttu-id="9aeda-102">一般檔案目的地編輯器 (連接管理員頁面)</span><span class="sxs-lookup"><span data-stu-id="9aeda-102">Flat File Destination Editor (Connection Manager Page)</span></span>
  <span data-ttu-id="9aeda-103">使用 [一般檔案目的地編輯器] 對話方塊的 [連線管理員] 頁面，來選取目的地的一般檔案連接，以及指定是否要覆寫或附加至現有的目的地檔案。</span><span class="sxs-lookup"><span data-stu-id="9aeda-103">Use the **Connection Manager** page of the **Flat File Destination Editor** dialog box to select the flat file connection for the destination, and to specify whether to overwrite or append to the existing destination file.</span></span> <span data-ttu-id="9aeda-104">一般檔案目的地會將資料寫入文字檔。</span><span class="sxs-lookup"><span data-stu-id="9aeda-104">The flat file destination writes data to a text file.</span></span> <span data-ttu-id="9aeda-105">此文字檔的格式可以是分隔、固定寬度、固定寬度且具有資料列分隔符號或不齊右格式。</span><span class="sxs-lookup"><span data-stu-id="9aeda-105">This text file can be in delimited, fixed width, fixed width with row delimiter, or ragged right format.</span></span>  
  
 <span data-ttu-id="9aeda-106">若要深入了解一般檔案目的地，請參閱 [一般檔案目的地](data-flow/flat-file-destination.md)。</span><span class="sxs-lookup"><span data-stu-id="9aeda-106">To learn more about the Flat File destination, see [Flat File Destination](data-flow/flat-file-destination.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="9aeda-107">選項。</span><span class="sxs-lookup"><span data-stu-id="9aeda-107">Options</span></span>  
 <span data-ttu-id="9aeda-108">**一般檔案連接管理員**</span><span class="sxs-lookup"><span data-stu-id="9aeda-108">**Flat File connection manager**</span></span>  
 <span data-ttu-id="9aeda-109">使用清單方塊選取現有的連線管理員，或按一下 [新增]  建立新的連接。</span><span class="sxs-lookup"><span data-stu-id="9aeda-109">Select an existing connection manager by using the list box, or create a new connection by clicking **New**.</span></span>  
  
 <span data-ttu-id="9aeda-110">**新增**</span><span class="sxs-lookup"><span data-stu-id="9aeda-110">**New**</span></span>  
 <span data-ttu-id="9aeda-111">使用 [一般檔案格式]  與 [一般檔案連線管理員編輯器]  對話方塊來建立新的連接。</span><span class="sxs-lookup"><span data-stu-id="9aeda-111">Create a new connection by using the **Flat File Format** and **Flat File Connection Manager Editor** dialog boxes.</span></span>  
  
 <span data-ttu-id="9aeda-112">除了標準一般檔案格式的 [使用分隔符號]、[固定寬度] 和 [不齊右] 等選項之外，[一般檔案格式]  對話方塊還有第四個選項 [有資料列分隔符號的固定寬度]  。</span><span class="sxs-lookup"><span data-stu-id="9aeda-112">In addition to the standard flat file formats of delimited, fixed width, and ragged right, the **Flat File Format** dialog box has a fourth option, **Fixed width with row delimiters**.</span></span> <span data-ttu-id="9aeda-113">這個選項代表不齊右格式的特殊狀況， [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 會加入虛擬資料行當做最後資料行。</span><span class="sxs-lookup"><span data-stu-id="9aeda-113">This option represents a special case of the ragged-right format in which [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] adds a dummy column as the final column of data.</span></span> <span data-ttu-id="9aeda-114">這個虛擬資料行可確保最終資料行有固定寬度。</span><span class="sxs-lookup"><span data-stu-id="9aeda-114">This dummy column ensures that the final column has a fixed width.</span></span>  
  
 <span data-ttu-id="9aeda-115">[有資料列分隔符號的固定寬度]  選項不會出現在 [一般檔案連線管理員編輯器]  中。</span><span class="sxs-lookup"><span data-stu-id="9aeda-115">The **Fixed width with row delimiters** option is not available in the **Flat File Connection Manager Editor**.</span></span> <span data-ttu-id="9aeda-116">必要時，您可以在編輯器中模擬這個選項。</span><span class="sxs-lookup"><span data-stu-id="9aeda-116">If necessary, you can emulate this option in the editor.</span></span> <span data-ttu-id="9aeda-117">若要模擬這個選項，請在 [一般檔案連線管理員編輯器] 的 [一般] 頁面上，針對 [格式] 選取 [不齊右]。</span><span class="sxs-lookup"><span data-stu-id="9aeda-117">To emulate this option, on the **General** page of the **Flat File Connection Manager Editor**, for **Format**, select **Ragged right**.</span></span> <span data-ttu-id="9aeda-118">然後在編輯器的 [進階]  頁面上，加入新的虛擬資料行當做最後資料行。</span><span class="sxs-lookup"><span data-stu-id="9aeda-118">Then on the **Advanced** page of the editor, add a new dummy column as the final column of data.</span></span>  
  
 <span data-ttu-id="9aeda-119">**覆寫檔案中的資料**</span><span class="sxs-lookup"><span data-stu-id="9aeda-119">**Overwrite data in the file**</span></span>  
 <span data-ttu-id="9aeda-120">指出是要覆寫現有的檔案，還是將資料附加至檔案中。</span><span class="sxs-lookup"><span data-stu-id="9aeda-120">Indicate whether to overwrite an existing file, or to append data to it.</span></span>  
  
 <span data-ttu-id="9aeda-121">**標頭**</span><span class="sxs-lookup"><span data-stu-id="9aeda-121">**Header**</span></span>  
 <span data-ttu-id="9aeda-122">在寫入任何資料之前，輸入要插入檔案中的文字區塊。</span><span class="sxs-lookup"><span data-stu-id="9aeda-122">Type a block of text to insert into the file before any data is written.</span></span> <span data-ttu-id="9aeda-123">使用此選項來包含其他資訊，例如資料行標題。</span><span class="sxs-lookup"><span data-stu-id="9aeda-123">Use this option to include additional information, such as column headings.</span></span>  
  
 <span data-ttu-id="9aeda-124">**預覽**</span><span class="sxs-lookup"><span data-stu-id="9aeda-124">**Preview**</span></span>  
 <span data-ttu-id="9aeda-125">使用 [資料檢視]  對話方塊來預覽結果。</span><span class="sxs-lookup"><span data-stu-id="9aeda-125">Preview results by using the **Data View** dialog box.</span></span> <span data-ttu-id="9aeda-126">預覽最多可顯示 200 個資料列。</span><span class="sxs-lookup"><span data-stu-id="9aeda-126">Preview can display up to 200 rows.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9aeda-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9aeda-127">See Also</span></span>  
 <span data-ttu-id="9aeda-128">[Integration Services 錯誤和訊息參考](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="9aeda-128">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 [<span data-ttu-id="9aeda-129">一般檔案目的地編輯器 &#40;對應頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="9aeda-129">Flat File Destination Editor &#40;Mappings Page&#41;</span></span>](../../2014/integration-services/flat-file-destination-editor-mappings-page.md)  
  
  
