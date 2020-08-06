---
title: 新增 (SSAS 表格式) 的資料表 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: d713c432-db99-4983-acc1-52b0fdd58bd6
author: minewiskan
ms.author: owend
ms.openlocfilehash: a80c22c992a89ed2cb3db84809b47a7cd08cb514
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598531"
---
# <a name="add-a-table-ssas-tabular"></a><span data-ttu-id="22038-102">加入資料表 (SSAS 表格式)</span><span class="sxs-lookup"><span data-stu-id="22038-102">Add a Table (SSAS Tabular)</span></span>
  <span data-ttu-id="22038-103">本主題描述如何從您先前將資料匯入模型的資料來源加入資料表。</span><span class="sxs-lookup"><span data-stu-id="22038-103">This topic describes how to add a table from a data source from which you have previously imported data into your model.</span></span> <span data-ttu-id="22038-104">若要從相同的資料來源加入資料表，您可以使用現有的資料來源連接。</span><span class="sxs-lookup"><span data-stu-id="22038-104">To add a table from the same data source, you can use the existing data source connection.</span></span> <span data-ttu-id="22038-105">從單一資料來源匯入任何數目的資料表時，建議您一律使用單一連接。</span><span class="sxs-lookup"><span data-stu-id="22038-105">It is recommended you always use a single connection when importing any number of tables from a single data source.</span></span>  
  
### <a name="to-add-a-table-from-an-existing-data-source"></a><span data-ttu-id="22038-106">若要從現有的資料來源加入資料表</span><span class="sxs-lookup"><span data-stu-id="22038-106">To add a table from an existing data source</span></span>  
  
1.  <span data-ttu-id="22038-107">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，按一下 **[模型]** 功能表，然後再按一下 **[現有連接]**。</span><span class="sxs-lookup"><span data-stu-id="22038-107">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], click the **Model** menu, and then click **Existing Connections**.</span></span>  
  
2.  <span data-ttu-id="22038-108">在 [現有連接]\*\*\*\* 頁面上，選取具有您想要加入之資料表的資料來源連接，然後按一下 [開啟]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="22038-108">On the **Existing Connections** page, select the connection to the data source that has the table you want to add, and then click **Open**.</span></span>  
  
3.  <span data-ttu-id="22038-109">在 [選取資料表和檢視表]\*\*\*\* 頁面上，選取您想要從資料來源加入至模型的資料表。</span><span class="sxs-lookup"><span data-stu-id="22038-109">On the **Select Tables and Views** page, select the table from the data source you want to add to your model.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="22038-110">[選取資料表和檢視表]\*\*\*\* 頁面不會將顯示先前匯入的資料表顯示成已核取。</span><span class="sxs-lookup"><span data-stu-id="22038-110">The **Select Tables and Views** page will not show tables that were previously imported as checked.</span></span>  <span data-ttu-id="22038-111">如果您選取了先前使用此連接來匯入的資料表，而且沒有為資料表提供不同的易記名稱，系統就會將 1 附加至易記名稱。</span><span class="sxs-lookup"><span data-stu-id="22038-111">If you select a table that was previously imported using this connection, and you did not give the table a different friendly name, a 1 will be appended to the friendly name.</span></span> <span data-ttu-id="22038-112">您不需要重新選取先前使用此連接來匯入的任何資料表。</span><span class="sxs-lookup"><span data-stu-id="22038-112">You do not need to re-select any tables that were previously imported by using this connection.</span></span>  
  
4.  <span data-ttu-id="22038-113">必要時，請使用 [預覽和篩選]\*\*\*\* 來單獨選取特定資料行或將篩選套用至要匯入的資料。</span><span class="sxs-lookup"><span data-stu-id="22038-113">If necessary, use **Preview & Filter** to select only certain columns or apply filters to the data to be imported.</span></span>  
  
5.  <span data-ttu-id="22038-114">按一下 [完成]\*\*\*\* 已匯入新的資料表。</span><span class="sxs-lookup"><span data-stu-id="22038-114">Click **Finish** to import the new table.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="22038-115">同時從單一資料來源匯入多個資料表時，系統將自動在模型中建立這些位於來源之資料表之間的任何關聯性。</span><span class="sxs-lookup"><span data-stu-id="22038-115">When importing multiple tables at the same time from a single data source, any relationships between those tables at the source will automatically be created in the model.</span></span> <span data-ttu-id="22038-116">不過，之後加入資料表時，您可能必須在模型中手動建立新加入資料表與先前匯入資料表之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="22038-116">When adding a table later; however, you may need to manually create relationships in the model between newly added tables and the tables that were previously imported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22038-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="22038-117">See Also</span></span>  
 <span data-ttu-id="22038-118">[將資料匯入 &#40;SSAS 表格式&#41;](../import-data-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="22038-118">[Import Data &#40;SSAS Tabular&#41;](../import-data-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="22038-119">刪除資料表 (SSAS 表格式)</span><span class="sxs-lookup"><span data-stu-id="22038-119">Delete a Table &#40;SSAS Tabular&#41;</span></span>](delete-a-table-ssas-tabular.md)  
  
  
