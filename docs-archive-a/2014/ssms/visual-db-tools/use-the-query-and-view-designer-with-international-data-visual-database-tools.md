---
title: 使用查詢和視圖設計工具搭配國際化資料 (Visual Database Tools) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- Visual Database Tools [SQL Server], international data
- queries [SQL Server], international data
- languages [SQL Server], Query and View Designer
- international considerations [SQL Server], Query and View Designer
- Criteria pane
- View Designer, international data
- Query Designer [SQL Server], international data
- localized information in Query and View Designer [SQL Server]
- global considerations [SQL Server], Query and View Designer
- SQL pane [Visual Database Tools]
- multiple language support [SQL Server], Query and View Designer
ms.assetid: 4b51c56f-f902-4e72-b919-e36127369b63
author: stevestein
ms.author: sstein
ms.openlocfilehash: 905e4c6909c792b019c11ef95662a7ec1a113bb4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703669"
---
# <a name="use-the-query-and-view-designer-with-international-data-visual-database-tools"></a><span data-ttu-id="c1655-102">使用查詢和檢視表設計工具操作國際資料 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="c1655-102">Use the Query and View Designer with International Data (Visual Database Tools)</span></span>
  <span data-ttu-id="c1655-103">您可以使用 [查詢和檢視表設計工具](visual-database-tools.md) 處理任何語言的資料，並在任何版本的 Windows 作業系統中執行。</span><span class="sxs-lookup"><span data-stu-id="c1655-103">You can use the [Query and View Designer](visual-database-tools.md) with data in any language and in any version of the Windows operating system.</span></span> <span data-ttu-id="c1655-104">下列方針即簡要說明您將注意到的不同處，並提供管理國際應用程式資料的資訊。</span><span class="sxs-lookup"><span data-stu-id="c1655-104">The following guidelines outline the differences you will notice and provide information about managing data in international applications.</span></span>  
  
## <a name="localized-information-in-the-criteria-and-sql-panes"></a><span data-ttu-id="c1655-105">準則和 SQL 窗格的當地語系化文化資訊</span><span class="sxs-lookup"><span data-stu-id="c1655-105">Localized Information in the Criteria and SQL Panes</span></span>  
 <span data-ttu-id="c1655-106">如果使用 [準則] 窗格建立查詢，可以用符合於您電腦的 Windows [地區選項] 的格式來輸入資訊。</span><span class="sxs-lookup"><span data-stu-id="c1655-106">If you are using the Criteria pane to create your query, you can enter information in the format that corresponds to the Windows Regional Settings for you computer.</span></span> <span data-ttu-id="c1655-107">例如，如果您要搜尋資料，您可以使用您習慣使用的格式在 [準則] 資料行中輸入資料，但以下為例外情況：</span><span class="sxs-lookup"><span data-stu-id="c1655-107">For example, if you are searching for data, you can enter the data in the Criteria columns using whatever format you are accustomed to using, with these exceptions:</span></span>  
  
-   <span data-ttu-id="c1655-108">不支援長資料格式。</span><span class="sxs-lookup"><span data-stu-id="c1655-108">Long data formats are not supported.</span></span>  
  
-   <span data-ttu-id="c1655-109">[準則] 窗格中無法輸入貨幣符號。</span><span class="sxs-lookup"><span data-stu-id="c1655-109">Currency symbols should not be entered in the Criteria pane.</span></span>  
  
-   <span data-ttu-id="c1655-110">貨幣符號將不會顯示在 [結果] 窗格中。</span><span class="sxs-lookup"><span data-stu-id="c1655-110">Currency symbols will not display in the Results pane.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c1655-111">在 [結果] 窗格中，雖然實際上可以輸入符合您電腦的 Windows 地區設定之貨幣符號，但是在 [結果] 窗格中，此符號將會移除且不會顯示。</span><span class="sxs-lookup"><span data-stu-id="c1655-111">In the Results pane, you can actually enter the currency symbol that corresponds to the Windows Regional Settings for your computer, but the symbol will be removed and will not display in the Results pane.</span></span>  
  
-   <span data-ttu-id="c1655-112">不論 [區域設定] 選項為何，一元 (Unary) 負號固定出現在左邊 (例如，-1)。</span><span class="sxs-lookup"><span data-stu-id="c1655-112">Unary minus always appears on the left side (for example, -1) regardless of the Regional Settings options.</span></span>  
  
 <span data-ttu-id="c1655-113">相對的，[SQL] 窗格的資料和關鍵字必須一律為 ANSI (U.S.) 格式。</span><span class="sxs-lookup"><span data-stu-id="c1655-113">In contrast, data and keywords in the SQL pane must always be in ANSI (U.S.) format.</span></span> <span data-ttu-id="c1655-114">例如，查詢和檢視設計師建置某個查詢，該查詢插入所有 ANSI 格式的 SQL 關鍵字，如 SELECT 和 FROM。</span><span class="sxs-lookup"><span data-stu-id="c1655-114">For example, as the Query and View Designer builds a query, it inserts the ANSI form of all SQL keywords such as SELECT and FROM.</span></span> <span data-ttu-id="c1655-115">如果您新增項目至 [SQL] 窗格的陳述式，請務必使用該元件的 ANSI 標準格式。</span><span class="sxs-lookup"><span data-stu-id="c1655-115">If you add elements to the statement in the SQL pane, be sure to use the ANSI standard form for the elements.</span></span>  
  
 <span data-ttu-id="c1655-116">當您在 [準則] 窗格中使用特定地區設定格式輸入資料時，[查詢和檢視設計師] 會在 [SQL] 窗格中自動將該資料轉譯為 ANSI 格式。</span><span class="sxs-lookup"><span data-stu-id="c1655-116">When you enter data using local-specific format in the Criteria pane, the Query and View Designer automatically translates it to ANSI format in the SQL pane.</span></span> <span data-ttu-id="c1655-117">例如，如果您的 [地區設定] 為 Standard German，您可以使用 "31.12.96" 的格式在 [準則] 窗格中輸入資料。</span><span class="sxs-lookup"><span data-stu-id="c1655-117">For example, if your Regional Settings are set to Standard German, you can enter data in the Criteria pane in a format such as "31.12.96."</span></span> <span data-ttu-id="c1655-118">然而，資料將以 ANSI 日期時間的格式出現在 [SQL] 窗格中，如 `{ ts '1996-12-31 00:00:00' }.` 。如果直接在 [SQL] 窗格中輸入資料，則必須以 ANSI 格式輸入。</span><span class="sxs-lookup"><span data-stu-id="c1655-118">However, the date will appear in the SQL pane in ANSI datetime format as `{ ts '1996-12-31 00:00:00' }.` If you enter data directly in the SQL pane, you must enter it in ANSI format.</span></span>  
  
## <a name="sort-order"></a><span data-ttu-id="c1655-119">排序次序</span><span class="sxs-lookup"><span data-stu-id="c1655-119">Sort Order</span></span>  
 <span data-ttu-id="c1655-120">資料庫將決定您查詢中資料的排序次序。</span><span class="sxs-lookup"><span data-stu-id="c1655-120">The sort order of data in your query is determined by the database.</span></span> <span data-ttu-id="c1655-121">您在 Windows [區域設定] 對話方塊中設定的選項並不會影響查詢的排序次序。</span><span class="sxs-lookup"><span data-stu-id="c1655-121">Options that you set in the Windows Regional Settings dialog box do not affect sort order for queries.</span></span> <span data-ttu-id="c1655-122">但在特定查詢中，您可以要求使用特定順序傳回資料列。</span><span class="sxs-lookup"><span data-stu-id="c1655-122">Within any particular query, however, you can request that rows be returned in a particular order.</span></span>  
  
## <a name="using-double-byte-characters"></a><span data-ttu-id="c1655-123">使用雙位元組字元</span><span class="sxs-lookup"><span data-stu-id="c1655-123">Using Double-Byte Characters</span></span>  
 <span data-ttu-id="c1655-124">您可以輸入 DBCS 字元做為常值或資料庫物件名稱，如資料表和檢視名稱或別名。</span><span class="sxs-lookup"><span data-stu-id="c1655-124">You can enter DBCS characters for literals and for database object names such as table and view names or aliases.</span></span> <span data-ttu-id="c1655-125">您也可以使用 DBCS 字元做為參數名稱或參數標記字元。</span><span class="sxs-lookup"><span data-stu-id="c1655-125">You can also use DBCS characters for parameter names and parameter marker characters.</span></span> <span data-ttu-id="c1655-126">但是您無法在 SQL 項目中 (如函數名稱或 SQL 關鍵字) 使用 DBCS 字元。</span><span class="sxs-lookup"><span data-stu-id="c1655-126">However, you cannot use DBCS characters in SQL language elements such as function names or SQL keywords.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1655-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c1655-127">See Also</span></span>  
 [<span data-ttu-id="c1655-128">設計查詢和檢視使用說明主題 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="c1655-128">Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;</span></span>](design-queries-and-views-how-to-topics-visual-database-tools.md)  
  
  
