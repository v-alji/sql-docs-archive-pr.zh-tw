---
title: 程式碼大綱
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Query Editor [SQL Server Management Studio], outlining code
- Query Editor [SQL Server Management Studio], hiding code
ms.assetid: 556c7dfe-7bc8-4cab-a36f-2b753a05d3f1
author: rothja
ms.author: jroth
ms.openlocfilehash: 0a142ca8fbdcdfcfbfd1b71de06c0b0fd4c5339c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594458"
---
# <a name="code-outlining"></a><span data-ttu-id="ac5a0-102">程式碼大綱</span><span class="sxs-lookup"><span data-stu-id="ac5a0-102">Code Outlining</span></span>
  <span data-ttu-id="ac5a0-103">您可以使用 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 查詢編輯器中的大綱功能，在您編輯查詢時選擇性地隱藏程式碼。</span><span class="sxs-lookup"><span data-stu-id="ac5a0-103">You can use the outlining feature in the [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] query editors to selectively hide code when you edit queries.</span></span> <span data-ttu-id="ac5a0-104">這可讓您更輕易地檢視正在處理的程式碼，尤其是處理大型查詢檔案的情況。</span><span class="sxs-lookup"><span data-stu-id="ac5a0-104">This enables you to more easily view the code you are working on, especially in large query files.</span></span>

## <a name="outlining-overview"></a><span data-ttu-id="ac5a0-105">大綱概觀</span><span class="sxs-lookup"><span data-stu-id="ac5a0-105">Outlining Overview</span></span>
 <span data-ttu-id="ac5a0-106">根據預設，當您開啟查詢編輯器視窗時，所有程式碼都會顯示出來。</span><span class="sxs-lookup"><span data-stu-id="ac5a0-106">By default, all code is visible when you open a query editor window.</span></span> <span data-ttu-id="ac5a0-107">您可以摺疊程式碼的區域，以便隱藏這些程式碼。</span><span class="sxs-lookup"><span data-stu-id="ac5a0-107">Regions of the code can be collapsed to hide it from view.</span></span> <span data-ttu-id="ac5a0-108">編輯器視窗左邊緣的垂直線會使用含有減號 (-) 的正方形來識別每個可摺疊程式碼區域的開頭。</span><span class="sxs-lookup"><span data-stu-id="ac5a0-108">A vertical line on the left edge of the editor window uses a square with a minus sign (-) to identify the start of each collapsible code region.</span></span> <span data-ttu-id="ac5a0-109">當您按一下減號時，程式碼區域的文字就會被取代成包含三個句號 (...) 的方塊，而且減號會變更為加號 (+)。</span><span class="sxs-lookup"><span data-stu-id="ac5a0-109">When you click a minus sign, the text of the code region is replaced with a box that contains three periods (...), and the minus sign changes to a plus sign (+).</span></span> <span data-ttu-id="ac5a0-110">當您按一下加號時，摺疊的程式碼就會顯示出來，而且加號會變更為減號。</span><span class="sxs-lookup"><span data-stu-id="ac5a0-110">When you click a plus sign, the collapsed code appears and the plus sign changes to a minus sign.</span></span> <span data-ttu-id="ac5a0-111">當您將指標移至具有三個句號的方塊上方時，就會出現一個工具提示，其中顯示已摺疊區段中的程式碼。</span><span class="sxs-lookup"><span data-stu-id="ac5a0-111">When you move the pointer over a box that has three periods, a tooltip appears that shows the code in the collapsed section.</span></span>

## <a name="system-outline-regions"></a><span data-ttu-id="ac5a0-112">系統大綱區域</span><span class="sxs-lookup"><span data-stu-id="ac5a0-112">System Outline Regions</span></span>
 <span data-ttu-id="ac5a0-113">每個 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 編輯器都會產生一組預設的系統定義大綱區域。</span><span class="sxs-lookup"><span data-stu-id="ac5a0-113">Each [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] editor generates a set of default, system-defined outline regions.</span></span>

 <span data-ttu-id="ac5a0-114">MDX 和 DMX 程式碼編輯器會針對每個多行陳述式建立大綱區域。</span><span class="sxs-lookup"><span data-stu-id="ac5a0-114">The MDX and DMX code editors create outline regions for each multiline statement.</span></span> <span data-ttu-id="ac5a0-115">這是這些編輯器唯一支援的大綱層級。</span><span class="sxs-lookup"><span data-stu-id="ac5a0-115">This is the only level of outlining that these editors support.</span></span>

### <a name="analysis-services-xmla-query-editor-regions"></a><span data-ttu-id="ac5a0-116">Analysis Services XMLA 查詢編輯器區域</span><span class="sxs-lookup"><span data-stu-id="ac5a0-116">Analysis Services XMLA Query Editor Regions</span></span>
 <span data-ttu-id="ac5a0-117">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] XMLA 查詢編輯器會針對每個多行 XML 屬性產生一個大綱區域。</span><span class="sxs-lookup"><span data-stu-id="ac5a0-117">The [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] XMLA Query Editor generates an outline region for each multiline XML attribute.</span></span> <span data-ttu-id="ac5a0-118">此編輯器會針對巢狀標記建立大綱區域的巢狀結構。</span><span class="sxs-lookup"><span data-stu-id="ac5a0-118">The editor nests the outline regions for nested tags.</span></span> <span data-ttu-id="ac5a0-119">例如，XMLA 編輯器會針對下列文件建立三個大綱區域。</span><span class="sxs-lookup"><span data-stu-id="ac5a0-119">For example, the XMLA Editor creates three outline regions for the following document.</span></span>

 <span data-ttu-id="ac5a0-120">![顯示大綱的 XML 程式碼](../../database-engine/media/editoutlinexmlfull.gif "顯示大綱的 XML 程式碼")</span><span class="sxs-lookup"><span data-stu-id="ac5a0-120">![XML code showing outlining](../../database-engine/media/editoutlinexmlfull.gif "XML code showing outlining")</span></span>

 <span data-ttu-id="ac5a0-121">當您按一下該行的減號時 \<InnerTag> ，只會折迭 g，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="ac5a0-121">When you click the minus sign on the \<InnerTag> line, just the InnerTag is collapsed, as shown in the following illustration.</span></span>

 <span data-ttu-id="ac5a0-122">![具有內部隱藏節點的 XML 程式碼](../../database-engine/media/editoutlinexmlinnercol.gif "具有內部隱藏節點的 XML 程式碼")</span><span class="sxs-lookup"><span data-stu-id="ac5a0-122">![XML code with inner node hidden](../../database-engine/media/editoutlinexmlinnercol.gif "XML code with inner node hidden")</span></span>

 <span data-ttu-id="ac5a0-123">當您將指標移至具有三個句號 (...) 的方塊上方時，已摺疊區域中的程式碼就會顯示在工具提示中，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="ac5a0-123">When you move the pointer over the box that has the three periods (...), the code in the collapsed region appears in a tooltip, as shown in the following illustration.</span></span>

 <span data-ttu-id="ac5a0-124">![顯示隱藏程式碼的 XML 程式碼工具提示](../../database-engine/media/editoutlinexmlmouse.gif "顯示隱藏程式碼的 XML 程式碼工具提示")</span><span class="sxs-lookup"><span data-stu-id="ac5a0-124">![XML code with tooltip showing hidden code](../../database-engine/media/editoutlinexmlmouse.gif "XML code with tooltip showing hidden code")</span></span>

 <span data-ttu-id="ac5a0-125">當您按一下該行的減號時 \<MiddleTag> ，MiddleTag 和 g 都會折迭，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="ac5a0-125">When you click the minus sign on the \<MiddleTag> line, both the MiddleTag and InnerTag are collapsed, as shown in the following illustration.</span></span>

 <span data-ttu-id="ac5a0-126">![隱藏內部和中間標籤的 XML 程式碼](../../database-engine/media/editoutlinexmlmiddlecol.gif "具有內部及中間隱藏標籤的 XML 程式碼")</span><span class="sxs-lookup"><span data-stu-id="ac5a0-126">![XML code with inner and middle tags hidden](../../database-engine/media/editoutlinexmlmiddlecol.gif "XML code with inner and middle tags hidden")</span></span>

 <span data-ttu-id="ac5a0-127">當您按一下該行的減號時，就會折迭 \<OuterTag> 這三行，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="ac5a0-127">When you click the minus sign on the \<OuterTag> line, all three lines are collapsed, as shown in the following illustration.</span></span>

 <span data-ttu-id="ac5a0-128">![顯示所有三個隱藏標籤的 XML 程式碼](../../database-engine/media/editoutlinexmloutercol.gif "顯示所有三個隱藏標籤的 XML 程式碼")</span><span class="sxs-lookup"><span data-stu-id="ac5a0-128">![XML code showing all three tags hidden](../../database-engine/media/editoutlinexmloutercol.gif "XML code showing all three tags hidden")</span></span>

### <a name="database-engine-query-editor-regions"></a><span data-ttu-id="ac5a0-129">Database Engine 查詢編輯器區域</span><span class="sxs-lookup"><span data-stu-id="ac5a0-129">Database Engine Query Editor Regions</span></span>
 <span data-ttu-id="ac5a0-130">[!INCLUDE[ssDE](../../../includes/ssde-md.md)] 查詢編輯器會針對下列階層中的每個元素產生大綱區域：</span><span class="sxs-lookup"><span data-stu-id="ac5a0-130">The [!INCLUDE[ssDE](../../../includes/ssde-md.md)] Query Editor generates outline regions for each element in the following hierarchy:</span></span>

1.  <span data-ttu-id="ac5a0-131">批次。</span><span class="sxs-lookup"><span data-stu-id="ac5a0-131">Batches.</span></span> <span data-ttu-id="ac5a0-132">第一個批次是從檔案開頭到第一個 GO 命令或檔案結尾 (如果沒有 GO 命令的話) 的程式碼。</span><span class="sxs-lookup"><span data-stu-id="ac5a0-132">The first batch is the code from the start of the file to either the first GO command or the end of the file when there are no GO commands.</span></span> <span data-ttu-id="ac5a0-133">在第一個 GO 之後，從每個 GO 命令到下一個 GO 命令或檔案結尾還有一個批次。</span><span class="sxs-lookup"><span data-stu-id="ac5a0-133">After the first GO, there is one batch from each GO command to either the next GO command or the end of the file.</span></span>

2.  <span data-ttu-id="ac5a0-134">以下列關鍵字分隔的區塊：</span><span class="sxs-lookup"><span data-stu-id="ac5a0-134">Blocks delimited by the following keywords:</span></span>

    -   <span data-ttu-id="ac5a0-135">BEGIN - END</span><span class="sxs-lookup"><span data-stu-id="ac5a0-135">BEGIN - END</span></span>

    -   <span data-ttu-id="ac5a0-136">BEGIN TRY - END TRY</span><span class="sxs-lookup"><span data-stu-id="ac5a0-136">BEGIN TRY - END TRY</span></span>

    -   <span data-ttu-id="ac5a0-137">BEGIN CATCH - END CATCH</span><span class="sxs-lookup"><span data-stu-id="ac5a0-137">BEGIN CATCH - END CATCH</span></span>

3.  <span data-ttu-id="ac5a0-138">多行陳述式。</span><span class="sxs-lookup"><span data-stu-id="ac5a0-138">Multiline statements.</span></span>

 <span data-ttu-id="ac5a0-139">例如， [!INCLUDE[ssDE](../../../includes/ssde-md.md)] 查詢編輯器會針對下列查詢建立三個大綱區域：</span><span class="sxs-lookup"><span data-stu-id="ac5a0-139">For example, the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] Query Editor creates three outline regions for the following query:</span></span>

```
CREATE PROCEDURE Sales.SampleProc --Outline region 1
AS
BEGIN --Outline region 2 
  SELECT GETDATE() AS TimeOfQuery;
  SELECT * --Outline region 3
  FROM sys.transmission_queue;
  SELECT @@VERSION;
END;
GO
```

 <span data-ttu-id="ac5a0-140">您可以按一下 `SELECT *` 行的減號，以便單獨摺疊該 `SELECT` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="ac5a0-140">You can click the minus sign on the `SELECT *` line to collapse just that `SELECT` statement.</span></span> <span data-ttu-id="ac5a0-141">若要摺疊整個 `BEGIN - END` 區塊，請按一下 `BEGIN` 行的減號。</span><span class="sxs-lookup"><span data-stu-id="ac5a0-141">To collapse the whole `BEGIN - END` block, click the minus sign on the `BEGIN` line.</span></span> <span data-ttu-id="ac5a0-142">若要摺疊整個批次至 `GO` 命令，請按一下 `CREATE PROCEDURE` 行的減號。</span><span class="sxs-lookup"><span data-stu-id="ac5a0-142">To collapse the whole batch to the `GO` command, click the minus sign on the `CREATE PROCEDURE` line.</span></span> <span data-ttu-id="ac5a0-143">您無法個別摺疊 `SELECT GETDATE()` 或 `SELECT @@VERSION` 行，因為它們是單行陳述式而且沒有取得大綱區域。</span><span class="sxs-lookup"><span data-stu-id="ac5a0-143">You cannot collapse the `SELECT GETDATE()` or `SELECT @@VERSION` lines individually because they are single line statements and do not get outlining regions.</span></span>


