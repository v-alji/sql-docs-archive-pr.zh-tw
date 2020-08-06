---
title: 使用嵌套資料表資料當做精確度圖表的輸入 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Mining Accuracy Chart [Analysis Services], nested tables
- Mining Accuracy Chart [Analysis Services], input tables
- nested tables
- adding nested tables
ms.assetid: 162e0686-ada3-4dd3-9151-9589926e6613
author: minewiskan
ms.author: owend
ms.openlocfilehash: 97d5bbd75d09b1a9e4276c4723ad6986dbabf9e4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584822"
---
# <a name="using-nested-table-data-as-an-input-for-an-accuracy-chart"></a><span data-ttu-id="c221a-102">使用巢狀資料表當做精確度圖表的輸入</span><span class="sxs-lookup"><span data-stu-id="c221a-102">Using Nested Table Data as an Input for an Accuracy Chart</span></span>
  <span data-ttu-id="c221a-103">當您使用外部資料測試採礦模型的精確度時，如果採礦模型包含巢狀資料表，則外部資料必須也包含案例資料表和相關聯的巢狀資料表。</span><span class="sxs-lookup"><span data-stu-id="c221a-103">When you test the accuracy of a mining model by using external data, if the mining model contains nested tables, the external data must also contain a case table and an associated nested table.</span></span>  
  
 <span data-ttu-id="c221a-104">本主題描述如何處理用於模型測試的巢狀資料表、如何對應模式和外部資料中的巢狀與案例資料表，以及如何將篩選套用至巢狀資料表。</span><span class="sxs-lookup"><span data-stu-id="c221a-104">This topic describes how to work with nested tables used for model testing, how to map nested and case tables in the mode and in the external data, and how to apply a filter to a nested table.</span></span>  
  
 <span data-ttu-id="c221a-105">在處理巢狀資料表時，請牢記以下要訣：</span><span class="sxs-lookup"><span data-stu-id="c221a-105">When working with nested tables, keep in mind these tips:</span></span>  
  
-   <span data-ttu-id="c221a-106">如果選取了 **[使用採礦模型測試案例]** 或 **[使用採礦結構測試案例]** 選項，就不需要指定案例資料表或巢狀資料表。</span><span class="sxs-lookup"><span data-stu-id="c221a-106">If you select the option **Use mining model test cases** or **Use mining structure test cases**, you do not need to specify a case table or nested table.</span></span> <span data-ttu-id="c221a-107">使用這些選項時，測試資料的定義會儲存在採礦結構中，而且當您建立精確度圖表時會自動選取測試資料。</span><span class="sxs-lookup"><span data-stu-id="c221a-107">With those options, the definition of the test data is stored in the mining structure and the test data is automatically selected when you create the accuracy chart.</span></span>  
  
-   <span data-ttu-id="c221a-108">如果資料來源中的案例與巢狀資料表之間已經有關聯性存在，則採礦結構中的資料行會自動對應到輸入資料表中的同名資料行。</span><span class="sxs-lookup"><span data-stu-id="c221a-108">If a relationship already exists between the case and nested table in the data source, the columns in the mining structure are automatically mapped to the columns that have the same name in the input table.</span></span>  
  
-   <span data-ttu-id="c221a-109">在指定案例資料表之前，無法選取巢狀資料表。</span><span class="sxs-lookup"><span data-stu-id="c221a-109">You cannot select a nested table until you have specified the case table.</span></span> <span data-ttu-id="c221a-110">此外，除非採礦模型也使用案例資料表和巢狀資料表結構，否則您無法指定巢狀資料表當做輸入。</span><span class="sxs-lookup"><span data-stu-id="c221a-110">Also, you cannot specify a nested table as an input unless the mining model also uses a case table and nested table structure.</span></span>  
  
### <a name="use-a-nested-table-as-input-to-an-accuracy-chart"></a><span data-ttu-id="c221a-111">使用巢狀資料表當做精確度圖表的輸入</span><span class="sxs-lookup"><span data-stu-id="c221a-111">Use a nested table as input to an accuracy chart</span></span>  
  
1.  <span data-ttu-id="c221a-112">按兩下採礦結構，在資料採礦設計師中將它開啟。</span><span class="sxs-lookup"><span data-stu-id="c221a-112">Double-click the mining structure to open it in Data Mining Designer.</span></span>  
  
2.  <span data-ttu-id="c221a-113">選取 **[採礦精確度圖表]** 索引標籤，然後選取 **[輸入選擇]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="c221a-113">Select the **Mining Accuracy Chart** tab, and then select the **Input Selection** tab.</span></span>  
  
3.  <span data-ttu-id="c221a-114">在 **[選取要用於精確度圖表的資料集]** 中選取 **[指定不同的資料集]** 選項。</span><span class="sxs-lookup"><span data-stu-id="c221a-114">In **Select data set to be used for accuracy chart**, select the option **Specify a different data set**.</span></span>  
  
4.  <span data-ttu-id="c221a-115">按一下 [流覽] 按鈕\*\* ( ...] ) \*\* ，從目前伺服器上的資料來源視圖清單中選擇外部資料集。</span><span class="sxs-lookup"><span data-stu-id="c221a-115">Click the browse button **(...)** to choose the external data set from a list of data source views on the current server.</span></span>  
  
5.  <span data-ttu-id="c221a-116">按一下 [選取案例資料表] \*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c221a-116">Click **Select Case Table**.</span></span> <span data-ttu-id="c221a-117">在 **[選取資料表]** 對話方塊中，從資料來源檢視中選取包含案例資料的資料表，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="c221a-117">In the **Select Table** dialog box, choose the table from the data source view that contains the case data, and then click **OK**.</span></span>  
  
6.  <span data-ttu-id="c221a-118">按一下 **[選取巢狀資料表]**。</span><span class="sxs-lookup"><span data-stu-id="c221a-118">Click **Select Nested Table**.</span></span> <span data-ttu-id="c221a-119">在 **[選取資料表]** 對話方塊中，選取包含巢狀資料的資料表，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="c221a-119">In the **Select Table** dialog box, select the table that contains the nested data, and then click **OK**.</span></span>  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
     <span data-ttu-id="c221a-120">如果您需要修改巢狀資料表與案例資料表之間的關聯性，請按一下 **[修改聯結]** ，開啟 **[建立關聯性]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="c221a-120">If you need to modify the relationship between the nested table and the case table, click **Modify Join** to open the **Create Relationship** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c221a-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c221a-121">See Also</span></span>  
 <span data-ttu-id="c221a-122">[選擇和對應模型測試資料](choose-and-map-model-testing-data.md) </span><span class="sxs-lookup"><span data-stu-id="c221a-122">[Choose and Map Model Testing Data](choose-and-map-model-testing-data.md) </span></span>  
 [<span data-ttu-id="c221a-123">將篩選套用至模型測試資料</span><span class="sxs-lookup"><span data-stu-id="c221a-123">Apply Filters to Model Testing Data</span></span>](apply-filters-to-model-testing-data.md)  
  
  
