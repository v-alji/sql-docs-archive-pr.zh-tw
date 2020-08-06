---
title: 變更 DirectQuery 資料分割 (SSAS 表格式) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: f9df1e66-dd23-41b4-95eb-af110d10eda4
author: minewiskan
ms.author: owend
ms.openlocfilehash: 43d14785f72d9bfe6406e2b81d3f1b97e9b7cc2e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593709"
---
# <a name="change-the-directquery-partition-ssas-tabular"></a><span data-ttu-id="f7929-102">變更 DirectQuery 資料分割 (SSAS 表格式)</span><span class="sxs-lookup"><span data-stu-id="f7929-102">Change the DirectQuery Partition (SSAS Tabular)</span></span>
  <span data-ttu-id="f7929-103">因為資料表中只有一個資料分割可以指定為 DirectQuery 資料分割，所以根據預設，Analysis Services 會使用資料表中建立的第一個資料分割。</span><span class="sxs-lookup"><span data-stu-id="f7929-103">Because only one partition in a table can be designated as the DirectQuery partition, by default, Analysis Services uses the first partition that was created in the table.</span></span> <span data-ttu-id="f7929-104">在模型專案撰寫期間，您可以藉由使用 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中的 [資料分割管理員] 對話方塊來變更 DirectQuery 資料分割。</span><span class="sxs-lookup"><span data-stu-id="f7929-104">During model project authoring, you can change the DirectQuery partition by using the Partition Manager dialog box in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="f7929-105">如果是部署的模型，您可以使用 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]來變更 DirectQuery 資料分割。</span><span class="sxs-lookup"><span data-stu-id="f7929-105">For deployed models, you can change the DirectQuery partition by using [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
### <a name="change-the-directquery-partition-for-a-tabular-model-project"></a><span data-ttu-id="f7929-106">變更表格式模型專案的 DirectQuery 資料分割</span><span class="sxs-lookup"><span data-stu-id="f7929-106">Change the DirectQuery partition for a tabular model project</span></span>  
  
1.  <span data-ttu-id="f7929-107">在 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]中，於模型設計師中按一下包含分割資料表的資料表 (標籤)。</span><span class="sxs-lookup"><span data-stu-id="f7929-107">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], in the model designer, click on the table (tab) that contains the partitioned table.</span></span>  
  
2.  <span data-ttu-id="f7929-108">按一下 **[資料表]** 功能表，然後按一下 **[資料分割]**。</span><span class="sxs-lookup"><span data-stu-id="f7929-108">Click on the **Table** menu, and then click **Partitions**.</span></span>  
  
3.  <span data-ttu-id="f7929-109">在 [資料分割管理員]\*\*\*\* 中，作為目前直接查詢資料分割的資料分割是由資料分割名稱上的前置詞 **(DirectQuery)** 所表示。</span><span class="sxs-lookup"><span data-stu-id="f7929-109">In **Partition Manager**, the partition that is the current Direct Query partition in indicated by the prefix **(DirectQuery)** on the partition name.</span></span>  
  
     <span data-ttu-id="f7929-110">從 [資料分割]\*\*\*\* 清單中選取其他資料分割，然後按一下 [設為 DirectQuery]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f7929-110">Select a different partition from the **Partitions** list, and then click **Set as DirectQuery**.</span></span> <span data-ttu-id="f7929-111">選取目前的 DirectQuery 資料分割時，[設為 DirectQuery]\*\*\*\* 按鈕不會啟用，而且在模型尚未啟用直接查詢模式時，看不到此按鈕。</span><span class="sxs-lookup"><span data-stu-id="f7929-111">The **Set as DirectQuery** button is not enabled when the current DirectQuery partition is selected, and is not visible if the model has not been enabled for Direct Query mode.</span></span>  
  
4.  <span data-ttu-id="f7929-112">如果需要，請變更處理選項，然後按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f7929-112">If necessary, change the processing options, and then click **OK**.</span></span>  
  
### <a name="change-the-directquery-partition-for-a-deployed-tabular-model"></a><span data-ttu-id="f7929-113">變更已部署的表格式模型的 DirectQuery 資料分割</span><span class="sxs-lookup"><span data-stu-id="f7929-113">Change the DirectQuery partition for a deployed tabular model</span></span>  
  
1.  <span data-ttu-id="f7929-114">在 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]的物件總管中，開啟模型資料庫。</span><span class="sxs-lookup"><span data-stu-id="f7929-114">In [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], open the model database in Object Explorer.</span></span>  
  
2.  <span data-ttu-id="f7929-115">展開 [資料表]\*\*\*\* 節點，然後以滑鼠右鍵按一下資料分割資料表，再選取 [資料分割]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f7929-115">Expand the **Tables** node, then right-click the partitioned table, and then select **Partitions**.</span></span>  
  
     <span data-ttu-id="f7929-116">指定用於 DirectQuery 模式的資料分割在資料分割名稱上具有前置詞 (DirectQuery)。</span><span class="sxs-lookup"><span data-stu-id="f7929-116">The partition that is designated for use with DirectQuery mode has the prefix (DirectQuery) on the partition name.</span></span>  
  
3.  <span data-ttu-id="f7929-117">若要變更為其他資料分割，請按一下 [直接查詢]\*\*\*\* 工具列圖示以開啟 [設定 DirectQuery 資料分割]\*\*\*\* 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="f7929-117">To change to a different partition, click the **Direct Query** toolbar icon to open the **Set DirectQuery Partition** dialog box.</span></span> <span data-ttu-id="f7929-118">在尚未啟用直接查詢的模型上，無法使用 DirectQuery 工具列圖示。</span><span class="sxs-lookup"><span data-stu-id="f7929-118">The DirectQuery toolbar icon is not available on models that have not been enabled for Direct Query.</span></span>  
  
4.  <span data-ttu-id="f7929-119">從 [資料分割名稱]\*\*\*\* 下拉式清單中選擇其他資料分割，然後視需要變更該資料分割的處理選項。</span><span class="sxs-lookup"><span data-stu-id="f7929-119">Choose a different partition from the **Partition Name** dropdown list, and then change processing options on the partition if necessary.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7929-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f7929-120">See Also</span></span>  
 [<span data-ttu-id="f7929-121">資料分割 &#40;SSAS 表格式&#41;</span><span class="sxs-lookup"><span data-stu-id="f7929-121">Partitions &#40;SSAS Tabular&#41;</span></span>](tabular-models/partitions-ssas-tabular.md)  
  
  
