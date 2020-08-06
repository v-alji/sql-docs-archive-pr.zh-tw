---
title: 修改或刪除 Analysis Services 資料庫 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- databases [Analysis Services], modifying
- removing databases
- deleting databases
- dropping databases
- databases [Analysis Services], deleting
- modifying databases
ms.assetid: e48e3988-c091-4379-aabc-4da62f709a7e
author: minewiskan
ms.author: owend
ms.openlocfilehash: 6182e91bd95754fe639e8a48548b5cab1835bdc7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707945"
---
# <a name="modify-or-delete-an-analysis-services-database"></a><span data-ttu-id="1f16e-102">修改或刪除 Analysis Services 資料庫</span><span class="sxs-lookup"><span data-stu-id="1f16e-102">Modify or Delete an Analysis Services Database</span></span>
  <span data-ttu-id="1f16e-103">在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 中的部署之前和在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 中的部署之後，您可以變更 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]資料庫的名稱和描述。</span><span class="sxs-lookup"><span data-stu-id="1f16e-103">You can change the name and description of an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database before deployment in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] and after deployment in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="1f16e-104">您也可以調整 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 資料庫的其他設定，視環境而定。</span><span class="sxs-lookup"><span data-stu-id="1f16e-104">You can also adjust additional settings on an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database, depending on the environment.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1f16e-105">在線上模式中，您無法使用 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 來變更資料庫屬性。</span><span class="sxs-lookup"><span data-stu-id="1f16e-105">You cannot change database properties using [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] in online mode.</span></span>  
  
## <a name="modifying-databases-using-sql-server-management-studio"></a><span data-ttu-id="1f16e-106">使用 SQL Server Management Studio 修改資料庫</span><span class="sxs-lookup"><span data-stu-id="1f16e-106">Modifying Databases Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="1f16e-107">在部署 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 資料庫之後，您可以使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 來變更 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 在連接到資料庫所包含的資料來源時所使用的模擬模式。</span><span class="sxs-lookup"><span data-stu-id="1f16e-107">Once an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database is deployed, you can use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to change the impersonation mode used by [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] when connecting to data sources contained by the database.</span></span> <span data-ttu-id="1f16e-108">嘗試連接到資料來源以供處理、瀏覽或鑽研時，模擬模式可以讓您指定 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 使用的安全性內容。</span><span class="sxs-lookup"><span data-stu-id="1f16e-108">The impersonation mode allows you to specify the security context used by [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] when attempting to connect to a data source for processing, browsing, or drillthrough purposes.</span></span>  
  
## <a name="modifying-databases-using-sql-server-data-tools"></a><span data-ttu-id="1f16e-109">使用 SQL Server Data Tools 修改資料庫</span><span class="sxs-lookup"><span data-stu-id="1f16e-109">Modifying Databases Using SQL Server Data Tools</span></span>  
 <span data-ttu-id="1f16e-110">在專案模式中，您可以使用 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] ，修改用來定義資料庫之 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 專案的標題和描述的翻譯。</span><span class="sxs-lookup"><span data-stu-id="1f16e-110">You can use [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] in project mode to modify the translations for the caption and description of an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project used to define a database.</span></span> <span data-ttu-id="1f16e-111">如需在資料庫中使用翻譯的詳細資訊 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ，請參閱[Analysis Services Multiidimensional 的全球化案例](../globalization-scenarios-for-analysis-services-multiidimensional.md)。</span><span class="sxs-lookup"><span data-stu-id="1f16e-111">For more information about using translations in an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database, see [Globalization scenarios for Analysis Services Multiidimensional](../globalization-scenarios-for-analysis-services-multiidimensional.md).</span></span>  
  
 <span data-ttu-id="1f16e-112">在資料庫所包含的維度中，您可以設定與帳戶屬性所使用之帳戶類型相關聯的別名和彙總函式。</span><span class="sxs-lookup"><span data-stu-id="1f16e-112">You can also set the aliases and aggregation functions associated with account types used by account attributes in dimensions contained by the database.</span></span> <span data-ttu-id="1f16e-113">針對帳戶圖表中的帳戶類型，別名可讓您選取組織所使用的特定商業用語。</span><span class="sxs-lookup"><span data-stu-id="1f16e-113">Aliases allow you to select the business-specific terminology used by your organization for the account types in a chart of accounts.</span></span> <span data-ttu-id="1f16e-114">帳戶屬性的成員會使用帳戶類型，指出如何使用資料庫包含的每一個帳戶類型所指定的彙總函式，以彙總每一個成員的量值。</span><span class="sxs-lookup"><span data-stu-id="1f16e-114">The account types are used by members of an account attribute to indicate how to aggregate measures over each member by using the aggregation functions specified for each account type contained in the database.</span></span> <span data-ttu-id="1f16e-115">如需帳戶屬性的詳細資訊，請參閱 [屬性和屬性階層](../multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md)。</span><span class="sxs-lookup"><span data-stu-id="1f16e-115">For more information about account attributes, see [Attributes and Attribute Hierarchies](../multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md).</span></span>  
  
## <a name="deleting-databases"></a><span data-ttu-id="1f16e-116">刪除資料庫</span><span class="sxs-lookup"><span data-stu-id="1f16e-116">Deleting Databases</span></span>  
 <span data-ttu-id="1f16e-117">刪除現有的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 資料庫會刪除資料庫和資料庫中所有的 Cube、維度以及採礦模型。</span><span class="sxs-lookup"><span data-stu-id="1f16e-117">Deleting an existing [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database deletes the database and all cubes, dimensions, and mining models in the database.</span></span> <span data-ttu-id="1f16e-118">您只能刪除 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 中現有的 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]資料庫。</span><span class="sxs-lookup"><span data-stu-id="1f16e-118">You can only delete an existing [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
#### <a name="to-delete-an-analysis-services-database"></a><span data-ttu-id="1f16e-119">若要刪除 Analysis Services 資料庫</span><span class="sxs-lookup"><span data-stu-id="1f16e-119">To delete an Analysis Services database</span></span>  
  
1.  <span data-ttu-id="1f16e-120">連接到 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="1f16e-120">Connect to an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance.</span></span>  
  
2.  <span data-ttu-id="1f16e-121">在 [物件總管]\*\*\*\* 中，展開所連接之 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體的節點，並確定可以看見要刪除的物件。</span><span class="sxs-lookup"><span data-stu-id="1f16e-121">In **Object Explorer**, expand the node for the connected [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance and ensure that the object to be deleted is visible.</span></span>  
  
3.  <span data-ttu-id="1f16e-122">以滑鼠右鍵按一下要刪除的物件，並選取 [刪除]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1f16e-122">Right-click the object to be deleted and select **Delete**.</span></span>  
  
4.  <span data-ttu-id="1f16e-123">在 **[刪除物件]** 對話方塊中，按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="1f16e-123">In the **Delete Object** dialog box, click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f16e-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1f16e-124">See Also</span></span>  
 [<span data-ttu-id="1f16e-125">記錄和編寫 Analysis Services 資料庫的指令碼</span><span class="sxs-lookup"><span data-stu-id="1f16e-125">Document and Script an Analysis Services Database</span></span>](document-and-script-an-analysis-services-database.md)  
  
  
