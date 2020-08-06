---
title: 全文檢索索引資料行對話方塊 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.dlgbox.fulltextcolumn
ms.assetid: a6f41c5c-d950-4d64-9e42-d062925917b6
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7f1cd2c94739a13e1820d8c05b338abd91d8a908
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708890"
---
# <a name="full-text-index-columns-dialog-box-visual-database-tools"></a><span data-ttu-id="f13a7-102">全文檢索索引資料行對話方塊 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="f13a7-102">Full-Text Index Columns Dialog Box (Visual Database Tools)</span></span>
  <span data-ttu-id="f13a7-103">這個對話方塊會列出 [資料表設計工具] 開啟的資料表中，參與全文檢索索引的資料行。</span><span class="sxs-lookup"><span data-stu-id="f13a7-103">This dialog box lists the columns participating in the full-text index for the table open in Table Designer.</span></span> <span data-ttu-id="f13a7-104">若要存取這個對話方塊，請在資料表設計工具中的資料表上按一下滑鼠右鍵、選擇 [全文檢索索引]  ，然後在 [全文檢索索引]  對話方塊中，依序按一下想要檢視或編輯的資料行索引、右側方格的 [資料行]  欄位，再按一下省略符號 ( **...** )。</span><span class="sxs-lookup"><span data-stu-id="f13a7-104">To access this dialog box, right-click the table in Table Designer, choose **Full-Text Index**, and in the **Full-Text Index** dialog box, click the index with columns you want to view or edit, click the **Columns** field in the grid to the right, and click the ellipses (**...**).</span></span>  
  
## <a name="options"></a><span data-ttu-id="f13a7-105">選項。</span><span class="sxs-lookup"><span data-stu-id="f13a7-105">Options</span></span>  
 <span data-ttu-id="f13a7-106">**資料行**</span><span class="sxs-lookup"><span data-stu-id="f13a7-106">**Column**</span></span>  
 <span data-ttu-id="f13a7-107">顯示參與全文檢索索引之資料行的名稱。</span><span class="sxs-lookup"><span data-stu-id="f13a7-107">Shows the names of columns participating in the full-text index.</span></span> <span data-ttu-id="f13a7-108">若要加入資料行，請按一下第一個空的資料格，然後從下拉式清單中選擇資料行。</span><span class="sxs-lookup"><span data-stu-id="f13a7-108">To add a column, click in the first empty cell and choose a column from the drop-down list.</span></span> <span data-ttu-id="f13a7-109">只可以存取資料類型為文字基礎或影像的資料行。</span><span class="sxs-lookup"><span data-stu-id="f13a7-109">Only columns with either text-based or image data types will be accessible.</span></span>  
  
 <span data-ttu-id="f13a7-110">**資料類型**</span><span class="sxs-lookup"><span data-stu-id="f13a7-110">**Data Type**</span></span>  
 <span data-ttu-id="f13a7-111">顯示每一資料行的資料類型。</span><span class="sxs-lookup"><span data-stu-id="f13a7-111">Shows the data type for each column.</span></span> <span data-ttu-id="f13a7-112">這是一個唯讀屬性。</span><span class="sxs-lookup"><span data-stu-id="f13a7-112">This is a read-only property.</span></span> <span data-ttu-id="f13a7-113">若要變更資料類型，請在資料表設計工具中開啟資料表、按一下資料行，然後編輯 [資料行屬性]  索引標籤中的資料類型。</span><span class="sxs-lookup"><span data-stu-id="f13a7-113">To change a data type, open the table in Table Designer, click the column, and edit the data type in the **Column Properties** tab.</span></span>  
  
 <span data-ttu-id="f13a7-114">**依資料行排列類型**</span><span class="sxs-lookup"><span data-stu-id="f13a7-114">**Typed by Column**</span></span>  
 <span data-ttu-id="f13a7-115">只適用於資料類型為 `image` 的資料行。</span><span class="sxs-lookup"><span data-stu-id="f13a7-115">Applies only to columns with the data type `image`.</span></span> <span data-ttu-id="f13a7-116">提供下拉式清單，您可在此選取代表本資料行之資料類型的其他資料行。</span><span class="sxs-lookup"><span data-stu-id="f13a7-116">Provides a drop-down list from which you can choose which of the other columns represent the data type of this column.</span></span> <span data-ttu-id="f13a7-117">如果此資料行的資料類型不是 `image`，值將會是 [無]。</span><span class="sxs-lookup"><span data-stu-id="f13a7-117">If this column is not of the `image` data type the value will be None.</span></span>  
  
 <span data-ttu-id="f13a7-118">資料類型為 `image` 的資料行可包含 Microsoft Office 檔案 (.doc、.xls 與 .ppt 檔案)、文字檔 (.txt 檔) 與 HTML 檔案 (.htm 檔)，將該資料行之資料類型設定為影像，可使全文檢索搜尋進行檔案內容的搜尋。</span><span class="sxs-lookup"><span data-stu-id="f13a7-118">Columns with the data type `image` can contain Microsoft Office files (.doc, .xls, and .ppt files), text files (.txt files), and HTML files (.htm files), and setting the data type of that column to image allows the full-text search to search the contents of the files.</span></span>  
  
 <span data-ttu-id="f13a7-119">**語言**</span><span class="sxs-lookup"><span data-stu-id="f13a7-119">**Language**</span></span>  
 <span data-ttu-id="f13a7-120">列出可用的語言。</span><span class="sxs-lookup"><span data-stu-id="f13a7-120">Lists available languages.</span></span> <span data-ttu-id="f13a7-121">從下拉式清單選擇適合您資料行資料的語言。</span><span class="sxs-lookup"><span data-stu-id="f13a7-121">Choose the language from the drop-down list appropriate for your column data.</span></span> <span data-ttu-id="f13a7-122">例如，如果您使用英文作業系統，但您要索引含有德文文字的資料行，則請從下拉式清單中選擇 [德文]，以提升索引的效能。</span><span class="sxs-lookup"><span data-stu-id="f13a7-122">For example, if you are using an English operating system, but you want to index a column that contains German text, choose German from the drop-down list to improve the index's performance.</span></span>  
  
 <span data-ttu-id="f13a7-123">**統計語意**</span><span class="sxs-lookup"><span data-stu-id="f13a7-123">**Statistical Semantics**</span></span>  
 <span data-ttu-id="f13a7-124">選取是否要針對選取的資料行啟用語意索引。</span><span class="sxs-lookup"><span data-stu-id="f13a7-124">Select whether to enable semantic indexing for the selected column.</span></span> <span data-ttu-id="f13a7-125">如需詳細資訊，請參閱[語意搜尋 &#40;SQL Server&#41;](../../relational-databases/search/semantic-search-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="f13a7-125">For more information, see [Semantic Search &#40;SQL Server&#41;](../../relational-databases/search/semantic-search-sql-server.md).</span></span>  
  
 <span data-ttu-id="f13a7-126">如果您在選取 **[統計語意]** 之前選取 **[語言]** ，而且選取的語言沒有相關聯的語意語言模型，則會停用 **[統計語意]** 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="f13a7-126">If you select a **Language** prior to selecting **Statistical Semantics**, and the selected language does not have an associated Semantic Language Model, then the **Statistical Semantics** checkbox is disabled.</span></span> <span data-ttu-id="f13a7-127">如果您在選取 [語言] 之前選取 [統計語意]，則下拉式方塊中提供的語言將受限為有語意語言模型支援的語言。</span><span class="sxs-lookup"><span data-stu-id="f13a7-127">If you select **Statistical Semantics** prior to selecting a **Language**, the languages available in the drop-down combo box will be restricted to those for which there is Semantic Language Model support.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f13a7-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f13a7-128">See Also</span></span>  
 [<span data-ttu-id="f13a7-129">全文檢索索引對話方塊 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="f13a7-129">Full-Text Index Dialog Box &#40;Visual Database Tools&#41;</span></span>](visual-database-tools.md)  
  
  
