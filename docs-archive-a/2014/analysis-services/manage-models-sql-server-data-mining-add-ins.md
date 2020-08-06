---
title: 管理 (SQL Server 資料採礦增益集的模型) |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models, importing
- mining models, deleting
- mining models, managing
- mining models, training
- mining models, processing
- mining models, exporting
ms.assetid: c11380f0-7c24-4668-9cdf-9c53e4aff665
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5f4b5961ec79bb949bf7fa5f53a980f066e81379
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598634"
---
# <a name="manage-models-sql-server-data-mining-add-ins"></a><span data-ttu-id="bb22d-102">管理模型 (SQL Server 資料採礦增益集)</span><span class="sxs-lookup"><span data-stu-id="bb22d-102">Manage Models (SQL Server Data Mining Add-ins)</span></span>
  <span data-ttu-id="bb22d-103">![資料採礦功能區中的管理模型按鈕](media/dmc-manage.gif "資料採礦功能區中的管理模型按鈕")</span><span class="sxs-lookup"><span data-stu-id="bb22d-103">![Manage Models button, Data Mining ribbon](media/dmc-manage.gif "Manage Models button, Data Mining ribbon")</span></span>  
  
 <span data-ttu-id="bb22d-104">[**管理模型**] 對話方塊可讓您與 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 目前所連接之伺服器中儲存的現有「採礦模型」和「採礦結構」進行互動。</span><span class="sxs-lookup"><span data-stu-id="bb22d-104">The **Manage Models** dialog box enables you to interact with existing mining models and mining structures that are stored in the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] server to which you are currently connected.</span></span> <span data-ttu-id="bb22d-105">您也可以檢視及管理目前工作階段期間已建立的暫時性結構和模型。</span><span class="sxs-lookup"><span data-stu-id="bb22d-105">You can also view and manage temporary structures and models that have been created during the current session.</span></span> <span data-ttu-id="bb22d-106">如果您已使用工作階段模型和伺服器上儲存的模型，對話方塊中會顯示這兩種模型。</span><span class="sxs-lookup"><span data-stu-id="bb22d-106">If you have used both session models and models stored on a server, both are visible in the dialog box.</span></span>  
  
## <a name="using-the-manage-models-wizard"></a><span data-ttu-id="bb22d-107">使用管理模型精靈</span><span class="sxs-lookup"><span data-stu-id="bb22d-107">Using the Manage Models Wizard</span></span>  
 <span data-ttu-id="bb22d-108">當您按一下 [**管理模型**] 時，會開啟 [**管理採礦結構和模型**] 對話方塊，提供下列功能的存取權來管理現有的資料採礦模型和結構：</span><span class="sxs-lookup"><span data-stu-id="bb22d-108">When you click **Manage Models**, the **Manage Mining Structures and Models** dialog box opens, providing access to the following functionality for managing existing data mining models and structures:</span></span>  
  
-   <span data-ttu-id="bb22d-109">重新命名採礦模型或結構</span><span class="sxs-lookup"><span data-stu-id="bb22d-109">Rename a mining model or structure</span></span>  
  
-   <span data-ttu-id="bb22d-110">刪除採礦模型或結構</span><span class="sxs-lookup"><span data-stu-id="bb22d-110">Delete a mining model or structure</span></span>  
  
-   <span data-ttu-id="bb22d-111">清除採礦模型或結構</span><span class="sxs-lookup"><span data-stu-id="bb22d-111">Clear a mining model or structure</span></span>  
  
-   <span data-ttu-id="bb22d-112">使用新的或現有的資料來處理採礦結構</span><span class="sxs-lookup"><span data-stu-id="bb22d-112">Process a mining structure, using either new or existing data</span></span>  
  
-   <span data-ttu-id="bb22d-113">匯出或匯入採礦模型或結構</span><span class="sxs-lookup"><span data-stu-id="bb22d-113">Export or import a mining model or structure</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bb22d-114">您無法使用這個對話方塊建立查詢或模型。</span><span class="sxs-lookup"><span data-stu-id="bb22d-114">You cannot create queries or models by using this dialog box.</span></span> <span data-ttu-id="bb22d-115">若要建立新的採礦結構，請使用適用于 Excel 的資料採礦用戶端中提供的其中一個嚮導，或使用**資料採礦查詢進階編輯器**。</span><span class="sxs-lookup"><span data-stu-id="bb22d-115">To create a new mining structure, use one of the wizards provided in the Data Mining Client for Excel, or use the **Data Mining Query Advanced Editor**.</span></span>  
  
### <a name="requirements"></a><span data-ttu-id="bb22d-116">需求</span><span class="sxs-lookup"><span data-stu-id="bb22d-116">Requirements</span></span>  
 <span data-ttu-id="bb22d-117">若要管理資料採礦模型，您必須先建立與 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 執行個體的連接。</span><span class="sxs-lookup"><span data-stu-id="bb22d-117">To manage data mining models, you must first create a connection to an instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="bb22d-118">即使您使用儲存在暫存檔中的工作階段模型，還是需要連接。</span><span class="sxs-lookup"><span data-stu-id="bb22d-118">A connection is required even if you are working with session models stored in a temporary file.</span></span> <span data-ttu-id="bb22d-119">如需有關如何建立或變更連接的詳細資訊，請參閱[連接到來源資料 &#40;適用于 Excel&#41;的資料採礦用戶端](connect-to-source-data-data-mining-client-for-excel.md)。</span><span class="sxs-lookup"><span data-stu-id="bb22d-119">For more information about how to create or change a connection, see [Connect to Source Data &#40;Data Mining Client for Excel&#41;](connect-to-source-data-data-mining-client-for-excel.md).</span></span>  
  
 <span data-ttu-id="bb22d-120">如果您連接的 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 執行個體沒有包含任何現有的資料採礦結構或資料採礦模型，您可以使用精靈或此增益集提供的其他工具來建立它們。</span><span class="sxs-lookup"><span data-stu-id="bb22d-120">If the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] that you connect to does not contain any existing data mining structures or data mining models, you can create them by using the wizards and other tools provided by this add-in.</span></span> <span data-ttu-id="bb22d-121">您也可以使用**資料採礦模型進階編輯器**建立新的模型。</span><span class="sxs-lookup"><span data-stu-id="bb22d-121">You can also create new models by using the **Data Mining Model Advanced Editor**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb22d-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bb22d-122">See Also</span></span>  
 <span data-ttu-id="bb22d-123">[記載 &#40;適用于 Excel 的資料採礦增益集&#41;的採礦模型](documenting-mining-models-data-mining-add-ins-for-excel.md) </span><span class="sxs-lookup"><span data-stu-id="bb22d-123">[Documenting Mining Models &#40;Data Mining Add-ins for Excel&#41;](documenting-mining-models-data-mining-add-ins-for-excel.md) </span></span>  
 [<span data-ttu-id="bb22d-124">&#40;適用于 Excel 的資料採礦增益集部署和調整採礦模型&#41;</span><span class="sxs-lookup"><span data-stu-id="bb22d-124">Deploying and Scaling Mining Models &#40;Data Mining Add-ins for Excel&#41;</span></span>](deploying-and-scaling-mining-models-data-mining-add-ins-for-excel.md)   

  
