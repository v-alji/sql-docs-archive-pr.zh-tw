---
title: 在方案總管 (SSAS 多維度) 中刪除資料來源 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.deleteobjects.f1
helpviewer_keywords:
- data sources [Analysis Services], deleting
- deleting data sources
- removing data sources
ms.assetid: b45441ef-f909-4736-98b9-cc80d0acac99
author: minewiskan
ms.author: owend
ms.openlocfilehash: d6101c8704579894590994d88e0286197148b694
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606456"
---
# <a name="delete-a-data-source-in-solution-explorer-ssas-multidimensional"></a><span data-ttu-id="2386e-102">在方案總管中刪除資料來源 (SSAS 多維度)</span><span class="sxs-lookup"><span data-stu-id="2386e-102">Delete a Data Source in Solution Explorer (SSAS Multidimensional)</span></span>
  <span data-ttu-id="2386e-103">您可以刪除資料來源物件，以便從 Analysis Services 多維度模型專案中將它永久移除。</span><span class="sxs-lookup"><span data-stu-id="2386e-103">You can delete a data source object to permanently remove it from an Analysis Services multidimensional model project.</span></span>  
  
 <span data-ttu-id="2386e-104">在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]中，資料來源會提供建構資料來源檢視的基礎，而接著會使用資料來源檢視，於 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 專案或資料庫中定義維度、Cube 和採礦結構。</span><span class="sxs-lookup"><span data-stu-id="2386e-104">In [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], data sources provide the basis on which data source views are constructed, and data source views are in turn used to define dimensions, cubes, and mining structures in an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project or database.</span></span> <span data-ttu-id="2386e-105">因此，刪除資料來源會使 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 專案中的其他 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 物件無效。</span><span class="sxs-lookup"><span data-stu-id="2386e-105">Therefore, deleting a data source may invalidate other [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] objects in an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project.</span></span> <span data-ttu-id="2386e-106">刪除物件之前，一定要檢閱所提供的相依物件清單。</span><span class="sxs-lookup"><span data-stu-id="2386e-106">You should always review the list of dependent objects that is provided before deleting the object.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="2386e-107">您無法從 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 以線上模式開啟的 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 資料庫中，刪除其他物件所相依的資料來源。</span><span class="sxs-lookup"><span data-stu-id="2386e-107">Data sources on which other objects depend cannot be deleted from an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database opened by [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] in online mode.</span></span> <span data-ttu-id="2386e-108">在刪除資料來源之前，您必須先刪除相依於該資料來源之 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 資料庫中的所有物件。</span><span class="sxs-lookup"><span data-stu-id="2386e-108">You must delete all objects in the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database that depend on that data source before deleting the data source.</span></span> <span data-ttu-id="2386e-109">如需線上模式的詳細資訊，請參閱 [在連線模式下連接至 Analysis Services 資料庫](connect-in-online-mode-to-an-analysis-services-database.md)。</span><span class="sxs-lookup"><span data-stu-id="2386e-109">For more information about online mode, see [Connect in Online Mode to an Analysis Services Database](connect-in-online-mode-to-an-analysis-services-database.md).</span></span>  
  
### <a name="to-delete-a-data-source"></a><span data-ttu-id="2386e-110">若要刪除資料來源</span><span class="sxs-lookup"><span data-stu-id="2386e-110">To delete a data source</span></span>  
  
1.  <span data-ttu-id="2386e-111">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，開啟您想要從中刪除資料來源的專案，或是連接到您想要從中刪除資料來源的資料庫。</span><span class="sxs-lookup"><span data-stu-id="2386e-111">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the project or connect to the database from which you want to delete a data source.</span></span>  
  
2.  <span data-ttu-id="2386e-112">在**方案總管**中，展開 [資料來源]\*\*\*\* 資料夾。</span><span class="sxs-lookup"><span data-stu-id="2386e-112">In **Solution Explorer**, expand the **Data Sources** folder.</span></span>  
  
3.  <span data-ttu-id="2386e-113">以滑鼠右鍵按一下該資料來源，然後按一下 [刪除]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2386e-113">Right-click the data source, and then click **Delete**.</span></span> <span data-ttu-id="2386e-114">[刪除物件]\*\*\*\* 對話方塊隨即出現，其中顯示刪除資料來源之後將失效的物件。</span><span class="sxs-lookup"><span data-stu-id="2386e-114">The **Delete Objects**  dialog box appears, showing the objects that will be invalidated if you delete the data source.</span></span> <span data-ttu-id="2386e-115">按一下 [確定]\*\*\*\* 刪除資料來源之前，請先仔細檢閱這份清單。</span><span class="sxs-lookup"><span data-stu-id="2386e-115">Review this list carefully before clicking **OK** to delete the data source.</span></span>  
  
4.  <span data-ttu-id="2386e-116">儲存專案。</span><span class="sxs-lookup"><span data-stu-id="2386e-116">Save the project.</span></span>  
  
     <span data-ttu-id="2386e-117">從 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 專案刪除資料來源之後，您必須儲存修改過的專案，否則下次開啟此專案時會收到錯誤，因為當此專案嘗試載入已刪除的資料來源時，該資料來源的基礎 XML 檔案將會遺失。</span><span class="sxs-lookup"><span data-stu-id="2386e-117">After deleting a data source from an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project, you must save the modified project or you will receive an error the next time you open the project because the underlying XML file for the deleted data source will be missing when the project attempts to load the deleted data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2386e-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2386e-118">See Also</span></span>  
 <span data-ttu-id="2386e-119">[多維度模型中的資料來源](data-sources-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="2386e-119">[Data Sources in Multidimensional Models](data-sources-in-multidimensional-models.md) </span></span>  
 [<span data-ttu-id="2386e-120">&#40;SSAS 多維度&#41;支援的資料來源</span><span class="sxs-lookup"><span data-stu-id="2386e-120">Data Sources Supported &#40;SSAS Multidimensional&#41;</span></span>](supported-data-sources-ssas-multidimensional.md)  
  
  
