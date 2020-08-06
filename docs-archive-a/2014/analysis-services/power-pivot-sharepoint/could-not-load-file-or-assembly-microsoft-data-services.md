---
title: 無法載入 Microsoft.analysisservices 的檔案或元件 &#39;。整合&#39; |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 6e350b67-5e18-4b90-8fb7-a0109cbb27b7
author: minewiskan
ms.author: owend
ms.openlocfilehash: b7ba75bdbd8e25f98d11d822c22fa7881352ad88
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598587"
---
# <a name="could-not-load-file-or-assembly-39microsoftanalysisservicessharepointintegration39"></a><span data-ttu-id="d1df4-102">無法載入 Microsoft.analysisservices 的檔案或元件 &#39;。整合&#39;</span><span class="sxs-lookup"><span data-stu-id="d1df4-102">Could not load file or assembly &#39;Microsoft.AnalysisServices.SharePoint.Integration&#39;</span></span>
  <span data-ttu-id="d1df4-103">在擁有 PowerPivot for SharePoint 的 SharePoint 2010 環境中，如果 PowerPivot 的應用程式層級方案並未正確部署，將會發生這個錯誤。</span><span class="sxs-lookup"><span data-stu-id="d1df4-103">In SharePoint 2010 environments that have PowerPivot for SharePoint, this error will occur if the application-level solution for PowerPivot did not deploy correctly.</span></span>  
  
## <a name="details"></a><span data-ttu-id="d1df4-104">詳細資料</span><span class="sxs-lookup"><span data-stu-id="d1df4-104">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d1df4-105">適用於</span><span class="sxs-lookup"><span data-stu-id="d1df4-105">Applies to</span></span>|<span data-ttu-id="d1df4-106">PowerPivot for SharePoint</span><span class="sxs-lookup"><span data-stu-id="d1df4-106">PowerPivot for SharePoint</span></span>|  
|<span data-ttu-id="d1df4-107">產品版本</span><span class="sxs-lookup"><span data-stu-id="d1df4-107">Product Version</span></span>|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]<span data-ttu-id="d1df4-108">, [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d1df4-108">, [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]</span></span>|  
|<span data-ttu-id="d1df4-109">原因</span><span class="sxs-lookup"><span data-stu-id="d1df4-109">Cause</span></span>|<span data-ttu-id="d1df4-110">Powerpivotwebapp 方案未部署或是未正確部署。</span><span class="sxs-lookup"><span data-stu-id="d1df4-110">Powerpivotwebapp solution is not deployed or did not deploy correctly.</span></span>|  
|<span data-ttu-id="d1df4-111">訊息文字</span><span class="sxs-lookup"><span data-stu-id="d1df4-111">Message Text</span></span>|<span data-ttu-id="d1df4-112">無法載入檔案或組件 'Microsoft.AnalysisServices.SharePoint.Integration'</span><span class="sxs-lookup"><span data-stu-id="d1df4-112">Could not load file or assembly 'Microsoft.AnalysisServices.SharePoint.Integration'</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="d1df4-113">說明</span><span class="sxs-lookup"><span data-stu-id="d1df4-113">Explanation</span></span>  
 <span data-ttu-id="d1df4-114">PowerPivot for SharePoint 使用方案套件將它的功能部署到 SharePoint 伺服器上。</span><span class="sxs-lookup"><span data-stu-id="d1df4-114">PowerPivot for SharePoint uses solution packages to deploy its features on a SharePoint server.</span></span> <span data-ttu-id="d1df4-115">其中一個方案未正確部署。</span><span class="sxs-lookup"><span data-stu-id="d1df4-115">One of the solutions is not deployed correctly.</span></span> <span data-ttu-id="d1df4-116">因此，每當您嘗試開啟 SharePoint 網站上的 PowerPivot 圖庫或其他 PowerPivot 應用程式頁面時，都會出現這個錯誤。</span><span class="sxs-lookup"><span data-stu-id="d1df4-116">As a result, this error appears whenever you try to open PowerPivot Gallery or other PowerPivot application pages on a SharePoint site.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="d1df4-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="d1df4-117">User Action</span></span>  
 <span data-ttu-id="d1df4-118">部署方案套件。</span><span class="sxs-lookup"><span data-stu-id="d1df4-118">Deploy the solution package.</span></span>  
  
1.  <span data-ttu-id="d1df4-119">在管理中心的 [系統設定] 中，按一下 **[管理伺服器陣列方案]**。</span><span class="sxs-lookup"><span data-stu-id="d1df4-119">In Central Administration, in System Settings, click **Manage farm solutions**.</span></span>  
  
2.  <span data-ttu-id="d1df4-120">按一下 [Powerpivotwebapp]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d1df4-120">Click **Powerpivotwebapp**.</span></span>  
  
3.  <span data-ttu-id="d1df4-121">按一下 **[部署方案]**。</span><span class="sxs-lookup"><span data-stu-id="d1df4-121">Click **Deploy Solution**.</span></span>  
  
4.  <span data-ttu-id="d1df4-122">選擇發生這個錯誤的 Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="d1df4-122">Choose the web application for which this error is occurring.</span></span> <span data-ttu-id="d1df4-123">如果有一個以上的 Web 應用程式，請針對所有應用程式重新部署此方案。</span><span class="sxs-lookup"><span data-stu-id="d1df4-123">If there is more than one web application, redeploy the solution for all of hem.</span></span>  
  
5.  <span data-ttu-id="d1df4-124">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="d1df4-124">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1df4-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d1df4-125">See Also</span></span>  
 [<span data-ttu-id="d1df4-126">將 PowerPivot 方案部署到 SharePoint</span><span class="sxs-lookup"><span data-stu-id="d1df4-126">Deploy PowerPivot Solutions to SharePoint</span></span>](deploy-power-pivot-solutions-to-sharepoint.md)  
  
  
