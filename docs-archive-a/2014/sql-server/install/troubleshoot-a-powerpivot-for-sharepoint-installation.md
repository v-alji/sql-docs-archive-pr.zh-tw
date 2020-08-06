---
title: 針對 PowerPivot for SharePoint 安裝進行疑難排解 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 97bc2ce7-af04-4372-ad79-c96b8c3417ab
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 3adc27132d976288c14ac702baae0b842e8aef0b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595451"
---
# <a name="troubleshoot-a-powerpivot-for-sharepoint-installation"></a><span data-ttu-id="733a1-102">疑難排解 PowerPivot for SharePoint 安裝</span><span class="sxs-lookup"><span data-stu-id="733a1-102">Troubleshoot a PowerPivot for SharePoint Installation</span></span>
  <span data-ttu-id="733a1-103">如果您看到的是錯誤，而不是預期的頁面和功能，請執行下列操作。</span><span class="sxs-lookup"><span data-stu-id="733a1-103">If you get errors instead of the pages and features you expect, do the following.</span></span>  
  
-   <span data-ttu-id="733a1-104">檢閱 SharePoint 和 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 的版本資訊，取得已知安裝問題的因應措施。</span><span class="sxs-lookup"><span data-stu-id="733a1-104">Review release notes for both SharePoint and [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] to get workarounds for known installation problems.</span></span> <span data-ttu-id="733a1-105">版本資訊會與安裝媒體一起提供，或是在您下載軟體的 Microsoft 網站上提供。</span><span class="sxs-lookup"><span data-stu-id="733a1-105">Release notes are provided with the installation media or on the Microsoft site from which you downloaded the software.</span></span>  
  
    -   <span data-ttu-id="733a1-106">[SQL Server 2014 版本](https://technet.microsoft.com/library/dn169381\(v=sql.15\).aspx)資訊。</span><span class="sxs-lookup"><span data-stu-id="733a1-106">[SQL Server 2014 Release Notes](https://technet.microsoft.com/library/dn169381\(v=sql.15\).aspx).</span></span>  
  
-   <span data-ttu-id="733a1-107">請參閱 Technet Wiki 主題＜ [PowerPivot 安裝疑難排解 (及其他增益集)](https://social.technet.microsoft.com/wiki/contents/articles/13737.troubleshooting-installations-of-powerpivot-and-other-add-ins.aspx)＞。</span><span class="sxs-lookup"><span data-stu-id="733a1-107">See the Technet wiki topic, [Troubleshooting Installations of PowerPivot (and other add-ins)](https://social.technet.microsoft.com/wiki/contents/articles/13737.troubleshooting-installations-of-powerpivot-and-other-add-ins.aspx).</span></span>  
  
## <a name="issues"></a><span data-ttu-id="733a1-108">問題</span><span class="sxs-lookup"><span data-stu-id="733a1-108">Issues</span></span>  
  
### <a name="powerpivot-gallery-thumbnail-images-show-as-a-red-x"></a><span data-ttu-id="733a1-109">PowerPivot 圖庫縮圖顯示為紅色的 X</span><span class="sxs-lookup"><span data-stu-id="733a1-109">PowerPivot Gallery Thumbnail images show as a red X</span></span>  
 <span data-ttu-id="733a1-110">其中一個可能的原因是 **[網站集合的 PowerPivot 功能整合]** 非使用中。</span><span class="sxs-lookup"><span data-stu-id="733a1-110">One Possible cause is the **PowerPivot features Integration for Site Collections** is not active.</span></span> <span data-ttu-id="733a1-111">完成以下動作：</span><span class="sxs-lookup"><span data-stu-id="733a1-111">Complete the following:</span></span>  
  
1.  <span data-ttu-id="733a1-112">在 PowerPivot 圖庫文件庫中，從齒輪圖示 [ ![SharePoint 設定](https://docs.microsoft.com/analysis-services/analysis-services/media/as-sharepoint2013-settings-gear.gif "SharePoint 設定")] 或 [**首頁**] 清單按一下 [**網站設定**]。</span><span class="sxs-lookup"><span data-stu-id="733a1-112">In the PowerPivot Gallery library, click **Site Settings** from either the gear icon ![SharePoint Settings](https://docs.microsoft.com/analysis-services/analysis-services/media/as-sharepoint2013-settings-gear.gif "SharePoint Settings") or the **Home** list.</span></span>  
  
2.  <span data-ttu-id="733a1-113">在 **[網站集合管理]** 區段中，按一下 **[網站集合功能]**。</span><span class="sxs-lookup"><span data-stu-id="733a1-113">In the **Site Collection Administration** section, click **Site Collection Features**.</span></span>  
  
3.  <span data-ttu-id="733a1-114">按一下 **[網站集合功能]**。</span><span class="sxs-lookup"><span data-stu-id="733a1-114">Click **Site Collection Features**.</span></span>  
  
4.  <span data-ttu-id="733a1-115">確認 **[網站集合的 PowerPivot 功能整合]** 為 **[使用中]**。</span><span class="sxs-lookup"><span data-stu-id="733a1-115">Verify **PowerPivot features Integration for Site Collections** is **Active**.</span></span>  
  
 <span data-ttu-id="733a1-116">如需此問題的其他原因，請參閱[PowerPivot 圖庫會針對圖示 (顯示紅色 X](https://support.microsoft.com/kb/2361559) https://support.microsoft.com/kb/2361559) 。</span><span class="sxs-lookup"><span data-stu-id="733a1-116">For additional causes of this issue, see [PowerPivot Gallery shows Red X's for Icons](https://support.microsoft.com/kb/2361559) (https://support.microsoft.com/kb/2361559).</span></span>  
  
  
