---
title: 刪除 (SSAS 表格式) 的資料行 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 703db83b-e554-450e-813e-23ad08c1cdad
author: minewiskan
ms.author: owend
ms.openlocfilehash: 06af0b7fd9879661db95bb2073cced545bb4eef5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596922"
---
# <a name="delete-a-column-ssas-tabular"></a><span data-ttu-id="7222e-102">刪除資料行 (SSAS 表格式)</span><span class="sxs-lookup"><span data-stu-id="7222e-102">Delete a Column (SSAS Tabular)</span></span>
  <span data-ttu-id="7222e-103">本主題描述的是如何從表格式模型資料表中刪除資料行。</span><span class="sxs-lookup"><span data-stu-id="7222e-103">This topic describes how to delete a column from a tabular model table.</span></span>  
  
## <a name="delete-a-model-table-column"></a><span data-ttu-id="7222e-104">刪除模型資料表資料行</span><span class="sxs-lookup"><span data-stu-id="7222e-104">Delete a Model Table Column</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7222e-105">從模型資料表中刪除資料行時，並不會從資料分割查詢定義中刪除該資料行。</span><span class="sxs-lookup"><span data-stu-id="7222e-105">Deleting a column from a model table does not delete the column from a partition query definition.</span></span> <span data-ttu-id="7222e-106">如果您要刪除的資料行屬於資料分割的一部分，就必須從資料分割查詢定義中手動刪除該資料行。</span><span class="sxs-lookup"><span data-stu-id="7222e-106">If the column you are deleting is part of a partition, you must manually delete the column from the partition query definition.</span></span> <span data-ttu-id="7222e-107">如果沒有從資料分割查詢定義中刪除資料行，將會導致系統在處理作業期間查詢該資料行並且傳回資料，但是不會擴展至模型資料表。</span><span class="sxs-lookup"><span data-stu-id="7222e-107">Failure to delete the column from the partition query definition will cause the column to be queried and data returned, but not populated to the model table, during processing operations.</span></span> <span data-ttu-id="7222e-108">如需詳細資訊，請參閱 [資料分割 &#40;SSAS 表格式&#41;](partitions-ssas-tabular.md)。</span><span class="sxs-lookup"><span data-stu-id="7222e-108">For more information, see [Partitions &#40;SSAS Tabular&#41;](partitions-ssas-tabular.md).</span></span>  
  
#### <a name="to-delete-a-model-table-column"></a><span data-ttu-id="7222e-109">若要刪除模型資料表資料行</span><span class="sxs-lookup"><span data-stu-id="7222e-109">To delete a model table column</span></span>  
  
-   <span data-ttu-id="7222e-110">在模型設計師中，於包含您想要刪除之資料行的資料表內，以滑鼠右鍵按一下資料行，然後按一下 [刪除]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7222e-110">In the model designer, in the table that contains the column you want to delete, right-click on the column, and then click **Delete**.</span></span>  
  
#### <a name="to-delete-a-model-table-column-by-using-the-table-properties-dialog-box"></a><span data-ttu-id="7222e-111">若要使用資料表屬性對話方塊來刪除模型資料表資料行</span><span class="sxs-lookup"><span data-stu-id="7222e-111">To delete a model table column by using the Table Properties dialog box</span></span>  
  
1.  <span data-ttu-id="7222e-112">在模型設計師中，按一下包含您想要刪除之資料行的資料表、按一下 [資料表]\*\*\*\* 功能表，然後按一下 [資料表屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7222e-112">In the model designer, click on the table which contains the column you want to delete, then click the **Table** menu, and then click  **Table Properties**.</span></span>  
  
2.  <span data-ttu-id="7222e-113">在 [資料行名稱來自]\*\*\*\* 中，選取 [模型]\*\*\*\* (使用模型資料表資料行名稱，如果與來源不同的話\*\*)。</span><span class="sxs-lookup"><span data-stu-id="7222e-113">In **Column names from**, select **Model** (*to use model table column names, if different from source*).</span></span>  
  
3.  <span data-ttu-id="7222e-114">在 [編輯資料表屬性]\*\*\*\* 對話方塊的 [資料表預覽] 視窗中，取消核取您想要刪除的資料行，然後按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7222e-114">In the **Edit Table Properties** dialog box, in the table preview window, uncheck the column you want to delete, and then click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7222e-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7222e-115">See Also</span></span>  
 <span data-ttu-id="7222e-116">[將資料行新增至 &#40;SSAS 表格式&#41;的資料表](add-columns-to-a-table-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="7222e-116">[Add Columns to a Table &#40;SSAS Tabular&#41;](add-columns-to-a-table-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="7222e-117">資料分割 &#40;SSAS 表格式&#41;</span><span class="sxs-lookup"><span data-stu-id="7222e-117">Partitions &#40;SSAS Tabular&#41;</span></span>](partitions-ssas-tabular.md)  
  
  
