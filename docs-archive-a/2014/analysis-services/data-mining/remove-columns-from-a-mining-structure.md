---
title: 從採礦結構移除資料行 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining structures [Analysis Services], columns
- removing columns
- deleting columns
- columns [data mining], mining structure columns
ms.assetid: 41073ffe-9351-416b-9f0c-62634bc213f9
author: minewiskan
ms.author: owend
ms.openlocfilehash: 44ad1de08d57d00fd9798e1ceeddb85d146d7111
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584838"
---
# <a name="remove-columns-from-a-mining-structure"></a><span data-ttu-id="fe0fa-102">從採礦結構中移除資料行</span><span class="sxs-lookup"><span data-stu-id="fe0fa-102">Remove Columns from a Mining Structure</span></span>
  <span data-ttu-id="fe0fa-103">在建立採礦結構之後，您可以使用資料採礦設計師，從採礦結構中移除資料行。</span><span class="sxs-lookup"><span data-stu-id="fe0fa-103">You can use Data Mining Designer to remove columns from a mining structure after the structure has already been created.</span></span> <span data-ttu-id="fe0fa-104">移除採礦結構資料行的原因可能包含下列：</span><span class="sxs-lookup"><span data-stu-id="fe0fa-104">Reasons to remove a mining structure column might include the following:</span></span>  
  
-   <span data-ttu-id="fe0fa-105">採礦結構包含某個資料行的多個複本並且您想要在模型中避免使用重複資料。</span><span class="sxs-lookup"><span data-stu-id="fe0fa-105">The mining structure contains multiple copies of a column and you want to avoid the use of duplicate data in a model.</span></span>  
  
-   <span data-ttu-id="fe0fa-106">資料應受到保護，但已啟用鑽研。</span><span class="sxs-lookup"><span data-stu-id="fe0fa-106">The data should be protected, but drillthrough has been enabled.</span></span>  
  
-   <span data-ttu-id="fe0fa-107">資料未在模型化中使用並且不應處理。</span><span class="sxs-lookup"><span data-stu-id="fe0fa-107">The data is unused in modeling and should not be processed.</span></span>  
  
 <span data-ttu-id="fe0fa-108">從採礦結構中刪除資料行並不會在資料來源檢視或外部資料中變更該資料行，只刪除中繼資料。</span><span class="sxs-lookup"><span data-stu-id="fe0fa-108">Deleting a column from the mining structure does not change the column in the data source view or in the external data; only metadata is deleted.</span></span> <span data-ttu-id="fe0fa-109">但在您變更採礦結構中使用的資料行時，必須重新處理採礦結構和以它為基礎的所有模型。</span><span class="sxs-lookup"><span data-stu-id="fe0fa-109">However, when you change the columns used in a mining structure, you must reprocess the structure and any models based on it.</span></span>  
  
### <a name="to-remove-a-column-from-the-mining-structure"></a><span data-ttu-id="fe0fa-110">若要從採礦結構中移除資料行</span><span class="sxs-lookup"><span data-stu-id="fe0fa-110">To remove a column from the mining structure</span></span>  
  
1.  <span data-ttu-id="fe0fa-111">選取資料採礦設計師中的 **[採礦結構]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="fe0fa-111">Select the **Mining Structure** tab in Data Mining Designer.</span></span>  
  
2.  <span data-ttu-id="fe0fa-112">展開採礦結構的樹狀，以顯示所有資料行。</span><span class="sxs-lookup"><span data-stu-id="fe0fa-112">Expand the tree for the mining structure, to show all the columns.</span></span>  
  
3.  <span data-ttu-id="fe0fa-113">以滑鼠右鍵按一下您想要刪除的資料行，然後選取 [刪除]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="fe0fa-113">Right-click the column that you want to delete, and then select **Delete**.</span></span>  
  
4.  <span data-ttu-id="fe0fa-114">在 **[刪除物件]** 對話方塊中，按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="fe0fa-114">In the **Delete Objects** dialog box, click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe0fa-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fe0fa-115">See Also</span></span>  
 [<span data-ttu-id="fe0fa-116">採礦結構工作和使用說明</span><span class="sxs-lookup"><span data-stu-id="fe0fa-116">Mining Structure Tasks and How-tos</span></span>](mining-structure-tasks-and-how-tos.md)  
  
  
