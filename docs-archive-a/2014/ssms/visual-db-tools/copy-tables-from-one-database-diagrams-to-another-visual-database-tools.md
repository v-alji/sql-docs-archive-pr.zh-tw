---
title: 將資料表從一個資料庫關係圖複製到另一個 (Visual Database Tools) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- copying tables
- duplicating tables
ms.assetid: 155a4f09-9321-4887-a7d4-aa2ce6b51277
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7e90c8f324e80f7c59674def06a77e93a5bf0cb1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686691"
---
# <a name="copy-tables-from-one-database-diagrams-to-another-visual-database-tools"></a><span data-ttu-id="fa336-102">將資料表從一個資料庫圖表複製至另一個資料庫圖表 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="fa336-102">Copy Tables from One Database Diagrams to Another (Visual Database Tools)</span></span>
  <span data-ttu-id="fa336-103">您可以在相同資料庫中，將資料表從一個資料庫圖表複製至另一個資料庫圖表中。</span><span class="sxs-lookup"><span data-stu-id="fa336-103">You can copy a table from one database diagram to another in the same database.</span></span>  
  
 <span data-ttu-id="fa336-104">將資料表從一個資料庫圖表複製到另一個資料庫圖表，會在第二個圖表中加入該資料表的參考。</span><span class="sxs-lookup"><span data-stu-id="fa336-104">Copying a table from one database diagram to another diagram adds a reference to the table in the second diagram.</span></span> <span data-ttu-id="fa336-105">並未在資料庫中複製資料表。</span><span class="sxs-lookup"><span data-stu-id="fa336-105">The table is not duplicated in your database.</span></span> <span data-ttu-id="fa336-106">例如，若要從一個資料庫圖表複製 `authors` 資料表至另一個資料庫圖表，則每個圖表都參考資料庫中相同的 `authors` 資料表。</span><span class="sxs-lookup"><span data-stu-id="fa336-106">For example, if you copy the `authors` table from one database diagram to another, each diagram references the same `authors` table in the database.</span></span>  
  
### <a name="to-copy-a-table-from-another-database-diagram"></a><span data-ttu-id="fa336-107">若要從另一個資料庫圖表複製資料表</span><span class="sxs-lookup"><span data-stu-id="fa336-107">To copy a table from another database diagram</span></span>  
  
1.  <span data-ttu-id="fa336-108">確定您已經連接想要複製其資料表的資料庫。</span><span class="sxs-lookup"><span data-stu-id="fa336-108">Make sure you are connected to the database whose table you want to copy.</span></span>  
  
2.  <span data-ttu-id="fa336-109">開啟來源和目標資料庫圖表，然後在來源圖表中選取要複製至目標圖表的資料表。</span><span class="sxs-lookup"><span data-stu-id="fa336-109">Open the source and target database diagrams and within the source diagram, select the table that you want to copy to the target diagram.</span></span>  
  
3.  <span data-ttu-id="fa336-110">按一下工具列上的 [複製]  按鈕。</span><span class="sxs-lookup"><span data-stu-id="fa336-110">Click the **Copy** button on the toolbar.</span></span> <span data-ttu-id="fa336-111">這一動作會將選取的資料表定義放在剪貼簿中。</span><span class="sxs-lookup"><span data-stu-id="fa336-111">This action places the selected table definition on the Clipboard.</span></span>  
  
4.  <span data-ttu-id="fa336-112">切換至目標圖表。</span><span class="sxs-lookup"><span data-stu-id="fa336-112">Switch to the target diagram.</span></span> <span data-ttu-id="fa336-113">這一圖表必須與來源圖表在同一資料庫中。</span><span class="sxs-lookup"><span data-stu-id="fa336-113">This diagram must be in the same database as the source diagram.</span></span>  
  
5.  <span data-ttu-id="fa336-114">按一下工具列上的 [貼上]  按鈕。</span><span class="sxs-lookup"><span data-stu-id="fa336-114">Click the **Paste** button on the toolbar.</span></span> <span data-ttu-id="fa336-115">剪貼簿的內容會出現在新位置，而且仍保持反白顯示，直到您按一下別處。</span><span class="sxs-lookup"><span data-stu-id="fa336-115">The Clipboard contents appear at the new location and remain highlighted until you click elsewhere.</span></span> <span data-ttu-id="fa336-116">如果選取的資料表與目標圖表中的其他資料表之間有關聯性，則會自動繪出關聯線。</span><span class="sxs-lookup"><span data-stu-id="fa336-116">If relationships exist between the selected tables and other tables in the target diagram, relationship lines are automatically drawn.</span></span>  
  
 <span data-ttu-id="fa336-117">在任一圖表中編輯資料表時，您所做的變更會同時反應在兩個圖表中。</span><span class="sxs-lookup"><span data-stu-id="fa336-117">When you edit the table in either diagram, your changes are reflected in both diagrams.</span></span> <span data-ttu-id="fa336-118">同理，在任一圖表中儲存資料表，則任一圖表中的資料表都不會再被視為「已修改」。</span><span class="sxs-lookup"><span data-stu-id="fa336-118">Similarly, once you save the table in either diagram, the table is no longer considered "modified" in either diagram.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa336-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fa336-119">See Also</span></span>  
 <span data-ttu-id="fa336-120">[使用資料庫關係圖 &#40;Visual Database Tools&#41;](visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="fa336-120">[Work with Database Diagrams &#40;Visual Database Tools&#41;](visual-database-tools.md) </span></span>  
 [<span data-ttu-id="fa336-121">將資料表新增至圖表 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="fa336-121">Add Tables to Diagrams &#40;Visual Database Tools&#41;</span></span>](add-tables-to-diagrams-visual-database-tools.md)  
  
  
