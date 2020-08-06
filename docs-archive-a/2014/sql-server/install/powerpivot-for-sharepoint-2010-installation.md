---
title: PowerPivot for SharePoint 2010 安裝 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 8d47dde7-c941-4280-a934-e2fe3f9a938f
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: ba04dfdc69b1c510a800c062586e45f8873c8e8a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598717"
---
# <a name="powerpivot-for-sharepoint-2010-installation"></a><span data-ttu-id="32d64-102">PowerPivot for SharePoint 2010 安裝</span><span class="sxs-lookup"><span data-stu-id="32d64-102">PowerPivot for SharePoint 2010 Installation</span></span>
  [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] <span data-ttu-id="32d64-103">是一種伺服器元件的集合，針對發行至 SharePoint 的 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 活頁簿提供查詢處理和管理控制。</span><span class="sxs-lookup"><span data-stu-id="32d64-103">is a collection of server components that provide query processing and management control over [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] workbooks that you publish to SharePoint.</span></span> <span data-ttu-id="32d64-104">服務包括 Analysis Services 引擎和 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 系統服務。</span><span class="sxs-lookup"><span data-stu-id="32d64-104">Services include the Analysis Services engine and [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] System Service.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="32d64-105">如需有關 [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] 與含 SharePoint Server 2013 安裝的詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="32d64-105">For information regarding [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] and installation with SharePoint Server 2013, see the following:</span></span>  
>   
>  -   <span data-ttu-id="32d64-106">[SQL Server 服務安裝的總覽](../../../2014/sql-server/install/overview-of-sql-server-servicing-installation.md)中的「SQL SERVER 2012 SP1」一節。</span><span class="sxs-lookup"><span data-stu-id="32d64-106">The "SQL Server 2012 SP1" section of [Overview of SQL Server Servicing Installation](../../../2014/sql-server/install/overview-of-sql-server-servicing-installation.md).</span></span>  
  
 <span data-ttu-id="32d64-107">Analysis Services 會為含有 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 資料的 Excel 工作簿，提供伺服器端的處理。</span><span class="sxs-lookup"><span data-stu-id="32d64-107">Analysis Services provides server-side processing for Excel workbooks that contain [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] data.</span></span> [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] <span data-ttu-id="32d64-108">系統服務會與 Analysis Services 一起運作，並加入 SharePoint 整合、負載平衡及連接管理。</span><span class="sxs-lookup"><span data-stu-id="32d64-108">System Service works alongside Analysis Services, adding SharePoint integration, load balancing and connection management.</span></span> [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]<span data-ttu-id="32d64-109">藉由將其大規模資料處理功能與 Excel 提供的資料轉譯服務配對，來擴充 Excel Services。</span><span class="sxs-lookup"><span data-stu-id="32d64-109">extends Excel Services by pairing its large scale data processing capability with the data rendering services that Excel provides.</span></span>  
  
 <span data-ttu-id="32d64-110">若要安裝 [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]，請使用 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 安裝媒體。</span><span class="sxs-lookup"><span data-stu-id="32d64-110">To install [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)], use the [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]installation media.</span></span>  
  
 <span data-ttu-id="32d64-111">如需有關先進部署案例的指示，請參閱[部署檢查清單： Reporting Services、Power View 和 PowerPivot for SharePoint](deployment-checklist-reporting-services-power-view-power-pivot-for-sharepoint.md)和[部署檢查清單：將 PowerPivot 服務器新增至 SharePoint 2010 伺服器陣列以向外](../../../2014/sql-server/install/deployment-checklist-scale-out-adding-powerpivot-servers-sharepoint-2010-farm.md)延展。</span><span class="sxs-lookup"><span data-stu-id="32d64-111">For instructions on advanced deployment scenarios, see [Deployment Checklist: Reporting Services, Power View, and PowerPivot for SharePoint](deployment-checklist-reporting-services-power-view-power-pivot-for-sharepoint.md) and [Deployment Checklist: Scale-out by adding PowerPivot Servers to a SharePoint 2010 farm](../../../2014/sql-server/install/deployment-checklist-scale-out-adding-powerpivot-servers-sharepoint-2010-farm.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="32d64-112">本節內容</span><span class="sxs-lookup"><span data-stu-id="32d64-112">In This Section</span></span>  
 [<span data-ttu-id="32d64-113">安裝 PowerPivot for SharePoint 2010</span><span class="sxs-lookup"><span data-stu-id="32d64-113">Install PowerPivot for SharePoint 2010</span></span>](../../../2014/sql-server/install/install-powerpivot-for-sharepoint-2010.md)  
  
 [<span data-ttu-id="32d64-114">在 SharePoint 伺服器上安裝 Analysis Services OLE DB 提供者</span><span class="sxs-lookup"><span data-stu-id="32d64-114">Install the Analysis Services OLE DB Provider on SharePoint Servers</span></span>](../../../2014/sql-server/install/install-the-analysis-services-ole-db-provider-on-sharepoint-servers.md)  
  
 [<span data-ttu-id="32d64-115">在執行管理中心的 Web 前端伺服器上安裝 ADOMD.NET</span><span class="sxs-lookup"><span data-stu-id="32d64-115">Install ADOMD.NET on Web Front-End Servers Running Central Administration</span></span>](../../../2014/sql-server/install/install-adomd-net-on-web-front-end-servers-running-central-administration.md)  
  
 [<span data-ttu-id="32d64-116">如何：安裝 ADO.NET Data Services 以支援 SharePoint 清單的資料摘要匯出</span><span class="sxs-lookup"><span data-stu-id="32d64-116">Install ADO.NET Data Services to support data feed exports of SharePoint lists</span></span>](../../../2014/sql-server/install/install-ado-net-data-services-to-support-data-feed-exports-of-sharepoint-lists.md)  
  
 [<span data-ttu-id="32d64-117">從命令提示字元安裝 PowerPivot</span><span class="sxs-lookup"><span data-stu-id="32d64-117">Install PowerPivot from the Command Prompt</span></span>](../../../2014/sql-server/install/install-powerpivot-from-the-command-prompt.md)  
  
 [<span data-ttu-id="32d64-118">解除安裝 PowerPivot for SharePoint</span><span class="sxs-lookup"><span data-stu-id="32d64-118">Uninstall PowerPivot for SharePoint</span></span>](../../../2014/sql-server/install/uninstall-power-pivot-for-sharepoint.md)  
  
 [<span data-ttu-id="32d64-119">修復 PowerPivot for SharePoint</span><span class="sxs-lookup"><span data-stu-id="32d64-119">Repair PowerPivot for SharePoint</span></span>](../../../2014/sql-server/install/repair-powerpivot-for-sharepoint.md)  
  
 [<span data-ttu-id="32d64-120">初始設定 &#40;PowerPivot for SharePoint&#41;</span><span class="sxs-lookup"><span data-stu-id="32d64-120">Initial Configuration &#40;PowerPivot for SharePoint&#41;</span></span>](../../../2014/sql-server/install/initial-configuration-powerpivot-for-sharepoint.md)  
  
## <a name="see-also"></a><span data-ttu-id="32d64-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="32d64-121">See Also</span></span>  
 [<span data-ttu-id="32d64-122">管理中心的 PowerPivot 伺服器管理和設定</span><span class="sxs-lookup"><span data-stu-id="32d64-122">PowerPivot Server Administration and Configuration in Central Administration</span></span>](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/power-pivot-server-administration-and-configuration-in-central-administration)  
  
  
