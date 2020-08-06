---
title: 重新命名多維度資料庫 (Analysis Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- renaming databases
ms.assetid: 15fdaec7-f3e4-44d9-9b78-1a1d78c484e0
author: minewiskan
ms.author: owend
ms.openlocfilehash: 3974e7671aff5d1cba22b10563bbc85a129a1dff
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597406"
---
# <a name="rename-a-multidimensional-database-analysis-services"></a><span data-ttu-id="d6070-102">重新命名多維度資料庫 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="d6070-102">Rename a Multidimensional Database (Analysis Services)</span></span>
  <span data-ttu-id="d6070-103">您變更資料庫名稱的方式， [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 取決於連接到資料庫的方式 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="d6070-103">The manner in which you change the name of a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database depends upon how you connect to the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database.</span></span> <span data-ttu-id="d6070-104">若要變更現有資料庫的名稱，您必須以線上模式連接。</span><span class="sxs-lookup"><span data-stu-id="d6070-104">To change the name of an existing database, you must connect in online mode.</span></span> <span data-ttu-id="d6070-105">若要將資料庫名稱變更為 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 專案中要具現化的物件，您必須以專案模式連接。</span><span class="sxs-lookup"><span data-stu-id="d6070-105">To change the name of the database into which objects in an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project will be instantiated, you must connect in project mode.</span></span>  
  
### <a name="to-change-the-database-name-in-online-mode"></a><span data-ttu-id="d6070-106">以線上模式變更資料庫名稱</span><span class="sxs-lookup"><span data-stu-id="d6070-106">To change the database name in online mode</span></span>  
  
1.  <span data-ttu-id="d6070-107">使用 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]直接連接到 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 資料庫。</span><span class="sxs-lookup"><span data-stu-id="d6070-107">Using [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], connect directly to the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database.</span></span>  
  
2.  <span data-ttu-id="d6070-108">在方案總管中，以滑鼠右鍵按一下資料庫，然後按一下 [編輯資料庫]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d6070-108">In Solution Explorer, right-click the database and then click **Edit Database**.</span></span>  
  
3.  <span data-ttu-id="d6070-109">在 **[資料庫名稱]** 文字方塊中，變更資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="d6070-109">In the **Database name** text box, change the database name.</span></span>  
  
4.  <span data-ttu-id="d6070-110">按一下工具列上的 **[儲存]** 或 **[全部儲存]** 、按一下 **[檔案]** 功能表上的 **[儲存選取項目]** 或 **[全部儲存]** ，或是關閉 **[資料庫設計工具]** ，並在出現提示時按一下 **[儲存]** 。</span><span class="sxs-lookup"><span data-stu-id="d6070-110">Click **Save** or **Save All** on the toolbar, click **Save Selected Items** or **Save All** on the **File** menu, or close the **Database Designer** and then click **Save** when prompted.</span></span>  
  
     <span data-ttu-id="d6070-111">即會在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體中更新此資料庫名稱，而且會重新整理 [方案總管] 中的資料庫物件。</span><span class="sxs-lookup"><span data-stu-id="d6070-111">The database name is updated in the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance and the database object in Solution Explorer is refreshed.</span></span>  
  
### <a name="to-change-the-database-name-in-project-mode"></a><span data-ttu-id="d6070-112">在專案模式中變更資料庫名稱</span><span class="sxs-lookup"><span data-stu-id="d6070-112">To change the database name in project mode</span></span>  
  
1.  <span data-ttu-id="d6070-113">開啟 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="d6070-113">Open the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project.</span></span>  
  
2.  <span data-ttu-id="d6070-114">在方案總管中，以滑鼠右鍵按一下 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 專案，然後按一下 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d6070-114">In Solution Explorer, right-click the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="d6070-115">在 **[屬性頁]** 對話方塊中，按一下 **[組態屬性]** 區段中的 **[部署]** 。</span><span class="sxs-lookup"><span data-stu-id="d6070-115">In the **Property Pages** dialog box, click **Deployment** in the **Configuration Properties** section.</span></span>  
  
4.  <span data-ttu-id="d6070-116">將 **[資料庫]** 屬性變更為新的資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="d6070-116">Change the **Database** property to the new database name.</span></span>  
  
     <span data-ttu-id="d6070-117">下次部署 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 專案時，它將會部署成這個新的資料庫名稱；</span><span class="sxs-lookup"><span data-stu-id="d6070-117">The next time the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project is deployed, it will be deployed to this new database name.</span></span> <span data-ttu-id="d6070-118">如果此資料庫已經存在，將會覆寫它。</span><span class="sxs-lookup"><span data-stu-id="d6070-118">If this database already exists, it will be overwritten.</span></span>  
  
### <a name="to-change-the-database-name-using-sql-server-management-studio"></a><span data-ttu-id="d6070-119">若要使用 SQL Server Management Studio 變更資料庫名稱</span><span class="sxs-lookup"><span data-stu-id="d6070-119">To change the database name using SQL Server Management Studio</span></span>  
  
-   <span data-ttu-id="d6070-120">以滑鼠右鍵按一下 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 資料庫並編輯 Name 屬性。</span><span class="sxs-lookup"><span data-stu-id="d6070-120">Right-click the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database and edit the Name property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6070-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d6070-121">See Also</span></span>  
 <span data-ttu-id="d6070-122">[在 Analysis Services 中設定伺服器屬性](../server-properties/server-properties-in-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="d6070-122">[Configure Server Properties in Analysis Services](../server-properties/server-properties-in-analysis-services.md) </span></span>  
 <span data-ttu-id="d6070-123">[設定多維度資料庫屬性 &#40;Analysis Services&#41;](set-multidimensional-database-properties-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="d6070-123">[Set Multidimensional Database Properties &#40;Analysis Services&#41;](set-multidimensional-database-properties-analysis-services.md) </span></span>  
 <span data-ttu-id="d6070-124">[設定 Analysis Services 專案屬性 &#40;SSDT&#41;](configure-analysis-services-project-properties-ssdt.md) </span><span class="sxs-lookup"><span data-stu-id="d6070-124">[Configure Analysis Services Project Properties &#40;SSDT&#41;](configure-analysis-services-project-properties-ssdt.md) </span></span>  
 [<span data-ttu-id="d6070-125">部署 Analysis Services 專案 &#40;SSDT&#41;</span><span class="sxs-lookup"><span data-stu-id="d6070-125">Deploy Analysis Services Projects &#40;SSDT&#41;</span></span>](deploy-analysis-services-projects-ssdt.md)  
  
  
