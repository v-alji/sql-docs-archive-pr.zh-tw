---
title: 從 Analysis Services (SSAS 表格式) 匯入 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: b9a21b23-3a06-4ef8-bc06-9c79cdc54870
author: minewiskan
ms.author: owend
ms.openlocfilehash: 7d6c3d226e46cdb4101bc8db52830046d27b0706
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687229"
---
# <a name="import-from-analysis-services-ssas-tabular"></a><span data-ttu-id="78b54-102">從 Analysis Services 匯入 (SSAS 表格式)</span><span class="sxs-lookup"><span data-stu-id="78b54-102">Import from Analysis Services (SSAS Tabular)</span></span>
  <span data-ttu-id="78b54-103">本主題描述如何使用 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]的 [從伺服器匯入] 專案範本，從現有的表格式模型匯入中繼資料，以建立新的表格式模型專案。</span><span class="sxs-lookup"><span data-stu-id="78b54-103">This topic describes how to create a new tabular model project by importing the metadata from an existing tabular model by using the Import from Server project template in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
## <a name="create-a-new-model-by-importing-metadata-from-an-existing-model-in-analysis-services"></a><span data-ttu-id="78b54-104">從 Analysis Services 中的現有模型匯入中繼資料來建立新的模型</span><span class="sxs-lookup"><span data-stu-id="78b54-104">Create a new model by importing metadata from an existing model in Analysis Services</span></span>  
 <span data-ttu-id="78b54-105">您可以使用 [從伺服器匯入] 專案範本從 Analysis Services 伺服器上的現有表格式模型複製中繼資料，以建立新的表格式模型專案。</span><span class="sxs-lookup"><span data-stu-id="78b54-105">You can use the Import from Server project template to create a new tabular model project by copying the metadata from an existing tabular model on an Analysis Services server.</span></span> <span data-ttu-id="78b54-106">將會使用與匯入來源之模型相同的資料來源連接、資料表、關聯性、量值、KPI、角色、階層、檢視方塊及資料分割來建立新專案。</span><span class="sxs-lookup"><span data-stu-id="78b54-106">The new project will be created with the same data source connections, tables, relationships, measures, KPIs, roles, hierarchies, perspectives, and partitions as the model it was imported from.</span></span> <span data-ttu-id="78b54-107">但是，資料並不會從現有的模型複製到新模型工作空間。</span><span class="sxs-lookup"><span data-stu-id="78b54-107">The data, however, is not copied from the existing model to the new model workspace.</span></span> <span data-ttu-id="78b54-108">一旦完成匯入程序並建立新模型專案之後，您必須執行「處理全部」將資料從資料來源載入新模型專案的工作空間資料庫。</span><span class="sxs-lookup"><span data-stu-id="78b54-108">Once the import process has completed, and the new model project created, you must run a Process All to load the data from the data sources into the new model project workspace database.</span></span>  
  
#### <a name="to-create-a-new-model-by-importing-metadata-from-an-existing-model"></a><span data-ttu-id="78b54-109">若要從現有的模型匯入中繼資料來建立新模型</span><span class="sxs-lookup"><span data-stu-id="78b54-109">To create a new model by importing metadata from an existing model</span></span>  
  
1.  <span data-ttu-id="78b54-110">在 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]的 **[檔案]** 功能表上，按一下 **[新增]**，然後再按一下 **[專案]**。</span><span class="sxs-lookup"><span data-stu-id="78b54-110">In [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], on the **File** menu, click **New**, and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="78b54-111">在 **[新增專案]** 對話方塊的 **[已安裝的範本]** 下，按一下 **[商業智慧]**，然後再按一下 **[從伺服器匯入]**。</span><span class="sxs-lookup"><span data-stu-id="78b54-111">In the **New Project** dialog box, under **Installed Templates**, click **Business Intelligence**, and then click **Import from Server**.</span></span>  
  
3.  <span data-ttu-id="78b54-112">在 **[名稱]** 中，輸入專案的名稱，並指定位置和方案名稱，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="78b54-112">In **Name**, type a name for the project, then specify a location and solution name, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="78b54-113">在 **[從 Analysis Services 匯入]** 對話方塊的 **[伺服器名稱]** 中，指定包含您要匯入之模型中繼資料的 Analysis Services 伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="78b54-113">In the **Import from Analysis Services** dialog box, in **Server Name**, specify the name of the Analysis Services server that contains the model metadata you want to import.</span></span>  
  
5.  <span data-ttu-id="78b54-114">在 **[資料庫名稱]** 中，選取包含您要匯入之模型中繼資料的表格式模型資料庫，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="78b54-114">In **Database Name**, select the tabular model database that contains the model metadata you want to import, and then click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78b54-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="78b54-115">See Also</span></span>  
 [<span data-ttu-id="78b54-116">專案屬性 &#40;SSAS 表格式&#41;</span><span class="sxs-lookup"><span data-stu-id="78b54-116">Project Properties &#40;SSAS Tabular&#41;</span></span>](properties-ssas-tabular.md)  
  
  
