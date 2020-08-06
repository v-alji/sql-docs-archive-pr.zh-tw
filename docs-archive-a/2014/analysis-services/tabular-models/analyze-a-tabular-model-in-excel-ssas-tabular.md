---
title: 在 Excel 中分析方格式模型 (SSAS 表格式) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.chooseperspect.f1
ms.assetid: 47fa45fc-60ab-41a1-bde3-5781c8462889
author: minewiskan
ms.author: owend
ms.openlocfilehash: fae542ffb5b470d23d9cf27fcc11367f571e7cec
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598529"
---
# <a name="analyze-a-tabular-model-in-excel-ssas-tabular"></a><span data-ttu-id="77c6c-102">在 Excel 中分析表格式模型 (SSAS 表格式)</span><span class="sxs-lookup"><span data-stu-id="77c6c-102">Analyze a Tabular Model in Excel (SSAS Tabular)</span></span>
  <span data-ttu-id="77c6c-103">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 中的 [在 Excel 中進行分析] 功能會開啟 Microsoft Excel、建立模型工作空間資料庫的資料來源連接，以及將樞紐分析表加入工作表。</span><span class="sxs-lookup"><span data-stu-id="77c6c-103">The Analyze in Excel feature in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] opens Microsoft Excel, creates a data source connection to the model workspace database, and adds a PivotTable to the worksheet.</span></span> <span data-ttu-id="77c6c-104">模型物件 (資料表、資料行、量值、階層和 KPI) 會包含在樞紐分析表欄位清單中當做欄位。</span><span class="sxs-lookup"><span data-stu-id="77c6c-104">Model objects (tables, columns, measures, hierarchies, and KPIs) are included as fields in the PivotTable field list.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="77c6c-105">為了使用 [在 Excel 中進行分析] 功能，您必須在與 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]相同的電腦上安裝 Microsoft Office 2003 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="77c6c-105">To use the Analyze in Excel feature, you must have Microsoft Office 2003 or later installed on the same computer as [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)].</span></span> <span data-ttu-id="77c6c-106">如果未將 Office 安裝在相同的電腦上，您可以在其他電腦上使用 Excel，然後連接至模型工作空間資料庫當做資料來源。</span><span class="sxs-lookup"><span data-stu-id="77c6c-106">If Office is not installed on the same computer, you can use Excel on another computer and connect to the model workspace database as a data source.</span></span> <span data-ttu-id="77c6c-107">然後即可手動將樞紐分析表加入工作表。</span><span class="sxs-lookup"><span data-stu-id="77c6c-107">You can then manually add a PivotTable to the worksheet.</span></span> <span data-ttu-id="77c6c-108">模型物件 (資料表、資料行、量值及 KPI) 會包含在樞紐分析表欄位清單中當做欄位。</span><span class="sxs-lookup"><span data-stu-id="77c6c-108">Model objects (tables, columns, measures, and KPIs) are included as fields in the PivotTable field list.</span></span>  
  
## <a name="tasks"></a><span data-ttu-id="77c6c-109">工作</span><span class="sxs-lookup"><span data-stu-id="77c6c-109">Tasks</span></span>  
  
#### <a name="to-analyze-a-tabular-model-project-by-using-the-analyze-in-excel-feature"></a><span data-ttu-id="77c6c-110">若要使用在 Excel 中進行分析功能來分析表格式模型專案</span><span class="sxs-lookup"><span data-stu-id="77c6c-110">To analyze a tabular model project by using the Analyze in Excel feature</span></span>  
  
1.  <span data-ttu-id="77c6c-111">在 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]中，按一下 **[模型]** 功能表，然後按一下 **[在 Excel 中進行分析]**。</span><span class="sxs-lookup"><span data-stu-id="77c6c-111">In [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], click the **Model** menu, and then click **Analyze in Excel**.</span></span>  
  
2.  <span data-ttu-id="77c6c-112">在 **[選擇認證和檢視方塊]** 對話方塊中，選取下列其中一個認證選項，以連接至模型工作空間資料來源：</span><span class="sxs-lookup"><span data-stu-id="77c6c-112">In the **Choose Credential and Perspective** dialog box, select one of the following credential options to connect to the model workspace data source:</span></span>  
  
    -   <span data-ttu-id="77c6c-113">若要使用目前的使用者帳戶，請選取 **[目前的 Windows 使用者]**。</span><span class="sxs-lookup"><span data-stu-id="77c6c-113">To use the current user account, select **Current Windows User**.</span></span>  
  
    -   <span data-ttu-id="77c6c-114">若要使用其他使用者帳戶，請選取 **[其他 Windows 使用者]**。</span><span class="sxs-lookup"><span data-stu-id="77c6c-114">To use a different user account, select **Other Windows User**.</span></span>  
  
         <span data-ttu-id="77c6c-115">此使用者帳戶通常是角色的成員。</span><span class="sxs-lookup"><span data-stu-id="77c6c-115">Typically, this user account will be a member of a role.</span></span> <span data-ttu-id="77c6c-116">不需要密碼。</span><span class="sxs-lookup"><span data-stu-id="77c6c-116">No password is required.</span></span> <span data-ttu-id="77c6c-117">只能在工作空間資料庫的 Excel 連接環境中使用此帳戶。</span><span class="sxs-lookup"><span data-stu-id="77c6c-117">The account can only be used in the context of an Excel connection to the workspace database.</span></span>  
  
    -   <span data-ttu-id="77c6c-118">若要使用安全性角色，請選取 **[角色]**，然後在清單方塊中選取一個或多個角色。</span><span class="sxs-lookup"><span data-stu-id="77c6c-118">To use a security role, select **Role**, and then in the listbox, select one or more roles.</span></span>  
  
         <span data-ttu-id="77c6c-119">您必須使用角色管理員定義安全性角色。</span><span class="sxs-lookup"><span data-stu-id="77c6c-119">Security roles must be defined using the Role Manager.</span></span> <span data-ttu-id="77c6c-120">如需詳細資訊，請參閱[建立及管理角色 &#40;SSAS 表格式&#41;](roles-ssas-tabular.md)。</span><span class="sxs-lookup"><span data-stu-id="77c6c-120">For more information, see [Create and Manage Roles &#40;SSAS Tabular&#41;](roles-ssas-tabular.md).</span></span>  
  
3.  <span data-ttu-id="77c6c-121">若要使用檢視方塊，請在 **[檢視方塊]** 清單方塊中選取檢視方塊。</span><span class="sxs-lookup"><span data-stu-id="77c6c-121">To use a perspective, in the **Perspective** listbox, select a perspective.</span></span>  
  
     <span data-ttu-id="77c6c-122">您必須使用 [檢視方塊] 對話方塊定義檢視方塊 (非預設值)。</span><span class="sxs-lookup"><span data-stu-id="77c6c-122">Perspectives (other than default) must be defined using the Perspectives dialog box.</span></span> <span data-ttu-id="77c6c-123">如需詳細資訊，請參閱[建立和管理 &#40;SSAS 表格式&#41;的觀點](perspectives-ssas-tabular.md)。</span><span class="sxs-lookup"><span data-stu-id="77c6c-123">For more information, see [Create and Manage Perspectives &#40;SSAS Tabular&#41;](perspectives-ssas-tabular.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="77c6c-124">當您在模型設計師中變更模型專案時，Excel 的樞紐分析表欄位清單不會自動重新整理。</span><span class="sxs-lookup"><span data-stu-id="77c6c-124">The PivotTable Field List in Excel does not refresh automatically as you make changes to the model project in the model designer.</span></span> <span data-ttu-id="77c6c-125">若要重新整理樞紐分析表欄位清單，請在 Excel 的 **[選項]** 功能區上，按一下 **[重新整理]**。</span><span class="sxs-lookup"><span data-stu-id="77c6c-125">To refresh the PivotTable Field List, in Excel, on the **Options** ribbon, click **Refresh**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77c6c-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="77c6c-126">See Also</span></span>  
 [<span data-ttu-id="77c6c-127">在 Excel 中進行分析 &#40;SSAS 表格式&#41;</span><span class="sxs-lookup"><span data-stu-id="77c6c-127">Analyze in Excel &#40;SSAS Tabular&#41;</span></span>](analyze-in-excel-ssas-tabular.md)  
  
  
