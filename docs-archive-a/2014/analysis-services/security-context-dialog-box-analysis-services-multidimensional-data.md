---
title: '[安全性內容] 對話方塊 (Analysis Services-多維度資料) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.browsecube.securitycontext.f1
ms.assetid: 238a4a4b-84bd-4b3d-9f02-f3adf57fa3af
author: minewiskan
ms.author: owend
ms.openlocfilehash: 58d5f71172ac16087ecc342342e70ade234226a2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592907"
---
# <a name="security-context-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="a9d94-102">安全性內容對話方塊 (Analysis Services - 多維度資料)</span><span class="sxs-lookup"><span data-stu-id="a9d94-102">Security Context Dialog Box (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="a9d94-103">使用 **的** [安全性內容] [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 對話方塊，即可變更用來檢查 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 物件之資料或中繼資料的使用者和角色。</span><span class="sxs-lookup"><span data-stu-id="a9d94-103">Use the **Security Context** dialog box in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] to change the user and role used to examine data or metadata for a [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] object.</span></span> <span data-ttu-id="a9d94-104">在 Cube 設計師的 **[計算]** 索引標籤或 **[瀏覽器]** 索引標籤上，按一下 **[工具列]** 窗格的 **[安全性內容]** ，即可顯示 **[安全性內容]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="a9d94-104">You can display the **Security Context** dialog box by clicking **Security Context** in the **Toolbar** pane on either the **Calculations** tab or the **Browser** tab in Cube Designer.</span></span>  
  
## <a name="options"></a><span data-ttu-id="a9d94-105">選項</span><span class="sxs-lookup"><span data-stu-id="a9d94-105">Options</span></span>  
 <span data-ttu-id="a9d94-106">**目前使用者**</span><span class="sxs-lookup"><span data-stu-id="a9d94-106">**Current user**</span></span>  
 <span data-ttu-id="a9d94-107">選取即可使用目前使用者的網域和使用者名稱，來檢視 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 物件的資料和中繼資料。</span><span class="sxs-lookup"><span data-stu-id="a9d94-107">Select to use the domain and user name of the current user while viewing the data and metadata of the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] object.</span></span>  
  
 <span data-ttu-id="a9d94-108">**其他使用者**</span><span class="sxs-lookup"><span data-stu-id="a9d94-108">**Other user**</span></span>  
 <span data-ttu-id="a9d94-109">輸入另一個使用者或群組的網域和使用者名稱，即可在檢視 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 物件的資料和中繼資料時使用。</span><span class="sxs-lookup"><span data-stu-id="a9d94-109">Type the domain and user name of another user or group to use while viewing the data and metadata of the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] object.</span></span>  
  
 <span data-ttu-id="a9d94-110">使用者或群組的網域和名稱會使用下列格式：</span><span class="sxs-lookup"><span data-stu-id="a9d94-110">The domain and name of the user or group uses the following format:</span></span>  
  
 <span data-ttu-id="a9d94-111">*\<Domain name>* **\\** *\<User account name>*</span><span class="sxs-lookup"><span data-stu-id="a9d94-111">*\<Domain name>* **\\** *\<User account name>*</span></span>  
  
 <span data-ttu-id="a9d94-112">**角色**</span><span class="sxs-lookup"><span data-stu-id="a9d94-112">**Roles**</span></span>  
 <span data-ttu-id="a9d94-113">選取即可使用一個或多個指定的角色，來檢視 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 物件的資料和中繼資料。</span><span class="sxs-lookup"><span data-stu-id="a9d94-113">Select to use one or more specified roles when viewing the data and metadata of the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] object.</span></span> <span data-ttu-id="a9d94-114">如果 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 資料庫中有定義多個角色，您就可以選取要使用的角色。</span><span class="sxs-lookup"><span data-stu-id="a9d94-114">You can select the roles to use if multiple roles are defined in the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9d94-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a9d94-115">See Also</span></span>  
 <span data-ttu-id="a9d94-116">[Kpi &#40;Cube 設計師&#41; &#40;Analysis Services-多維度資料&#41;](kpis-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="a9d94-116">[KPIs &#40;Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](kpis-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="a9d94-117">[瀏覽器 &#40;Cube 設計工具&#41; &#40;Analysis Services 多維度資料&#41;](browser-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="a9d94-117">[Browser &#40;Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](browser-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="a9d94-118">Analysis Services 的設計工具和對話方塊 &#40;多維度資料&#41;</span><span class="sxs-lookup"><span data-stu-id="a9d94-118">Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;</span></span>](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)  
  
  
