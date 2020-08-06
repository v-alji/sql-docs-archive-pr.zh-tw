---
title: 在管理中心為網站集合啟用 PowerPivot 功能整合 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 62a27e53-446a-42d7-b5db-c009e02d4904
author: minewiskan
ms.author: owend
ms.openlocfilehash: b565434cba197d04327e833d4ac6eab3caf96646
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698578"
---
# <a name="activate-powerpivot-feature-integration-for-site-collections-in-central-administration"></a><span data-ttu-id="ce224-102">在管理中心為網站集合啟用 PowerPivot 功能整合</span><span class="sxs-lookup"><span data-stu-id="ce224-102">Activate PowerPivot Feature Integration for Site Collections in Central Administration</span></span>
  <span data-ttu-id="ce224-103">如果您使用 [現有的伺服陣列] 安裝選項來安裝 SQL Server PowerPivot for SharePoint，就需要為特定的網站集合啟用 PowerPivot 功能整合。</span><span class="sxs-lookup"><span data-stu-id="ce224-103">Activating PowerPivot feature integration for specific site collections is required if you used the Existing Farm installation option to install SQL Server PowerPivot for SharePoint.</span></span> <span data-ttu-id="ce224-104">如果您已使用 [新的伺服器] 選項來安裝 PowerPivot for SharePoint，您可以略過這項工作，因為 SQL Server 安裝程式已經在設定部署時，針對根網站集合啟用 PowerPivot 功能整合。</span><span class="sxs-lookup"><span data-stu-id="ce224-104">If you installed PowerPivot for SharePoint using the New Server option, you can skip this task because SQL Server Setup already activated PowerPivot feature integration for the root site collection when it configured your deployment.</span></span>  
  
 <span data-ttu-id="ce224-105">網站集合層級的功能啟用對於將應用程式頁面和範本提供給網站使用 (包括排程資料重新整理的組態頁面，以及 PowerPivot 圖庫和資料摘要文件庫的應用程式頁面) 是必要的。</span><span class="sxs-lookup"><span data-stu-id="ce224-105">Feature activation at the site collection level is necessary to make application pages and templates available to your sites, including configuration pages for scheduled data refresh and application pages for PowerPivot Gallery and Data Feed libraries.</span></span>  
  
 <span data-ttu-id="ce224-106">您必須為每個支援 PowerPivot 查詢處理的網站集合啟用 PowerPivot 整合。</span><span class="sxs-lookup"><span data-stu-id="ce224-106">You must activate PowerPivot integration for each site collection that supports PowerPivot query processing.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="ce224-107">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="ce224-107">Prerequisites</span></span>  
 <span data-ttu-id="ce224-108">您必須是網站集合管理員。</span><span class="sxs-lookup"><span data-stu-id="ce224-108">You must be a site collection administrator.</span></span>  
  
## <a name="activate-powerpivot-features"></a><span data-ttu-id="ce224-109">啟用 PowerPivot 功能</span><span class="sxs-lookup"><span data-stu-id="ce224-109">Activate PowerPivot Features</span></span>  
  
1.  <span data-ttu-id="ce224-110">按一下 SharePoint 網站上的 [網站動作]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ce224-110">On a SharePoint site, click **Site Actions**.</span></span>  
  
     <span data-ttu-id="ce224-111">根據預設，SharePoint Web 應用程式會經由通訊埠 80 進行存取。</span><span class="sxs-lookup"><span data-stu-id="ce224-111">By default, SharePoint web applications are accessed through port 80.</span></span> <span data-ttu-id="ce224-112">這表示通常只要輸入 http://\<computer name> 即可存取 SharePoint 網站來開啟根網站集合。</span><span class="sxs-lookup"><span data-stu-id="ce224-112">This means that you can often access a SharePoint site by entering http://\<computer name> to open the root site collection.</span></span>  
  
2.  <span data-ttu-id="ce224-113">按一下 **[站台設定]** 。</span><span class="sxs-lookup"><span data-stu-id="ce224-113">Click **Site Settings**.</span></span>  
  
3.  <span data-ttu-id="ce224-114">按一下 [網站集合管理] 中的 [網站集合功能]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ce224-114">In Site Collection Administration, click **Site collection features**.</span></span>  
  
4.  <span data-ttu-id="ce224-115">在您找到**PowerPivot 整合網站集合功能**之前，請向下流覽頁面。</span><span class="sxs-lookup"><span data-stu-id="ce224-115">Scroll down the page until you find **PowerPivot Integration Site Collection Feature**.</span></span>  
  
5.  <span data-ttu-id="ce224-116">按一下 [啟用]。</span><span class="sxs-lookup"><span data-stu-id="ce224-116">Click **Activate**.</span></span>  
  
6.  <span data-ttu-id="ce224-117">開啟每個網站並按一下 [網站動作]\*\*\*\*，為其他網站集合重複執行。</span><span class="sxs-lookup"><span data-stu-id="ce224-117">Repeat for additional site collections by opening each site and clicking **Site Actions**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce224-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ce224-118">See Also</span></span>  
 <span data-ttu-id="ce224-119">[管理中心的 PowerPivot 服務器管理和設定](power-pivot-server-administration-and-configuration-in-central-administration.md) </span><span class="sxs-lookup"><span data-stu-id="ce224-119">[PowerPivot Server Administration and Configuration in Central Administration](power-pivot-server-administration-and-configuration-in-central-administration.md) </span></span>  
 <span data-ttu-id="ce224-120">[初始設定 &#40;PowerPivot for SharePoint&#41;](../../sql-server/install/initial-configuration-powerpivot-for-sharepoint.md) </span><span class="sxs-lookup"><span data-stu-id="ce224-120">[Initial Configuration &#40;PowerPivot for SharePoint&#41;](../../sql-server/install/initial-configuration-powerpivot-for-sharepoint.md) </span></span>  
 [<span data-ttu-id="ce224-121">PowerPivot for SharePoint 2010 安裝</span><span class="sxs-lookup"><span data-stu-id="ce224-121">PowerPivot for SharePoint 2010 Installation</span></span>](../../sql-server/install/powerpivot-for-sharepoint-2010-installation.md)  
  
  
