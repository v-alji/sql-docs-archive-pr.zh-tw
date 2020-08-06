---
title: 授權方法 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- security [Reporting Services], reports
- authorization [Reporting Services]
- reports [Reporting Services], security
- tasks [Reporting Services]
- roles [Reporting Services], methods
ms.assetid: 45e9cf2c-facf-4801-9482-c855403f42a8
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b04a21b5075e939a4732e2f8ec219e169f4ba440
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704874"
---
# <a name="authorization-methods"></a><span data-ttu-id="352ff-102">授權方法</span><span class="sxs-lookup"><span data-stu-id="352ff-102">Authorization Methods</span></span>
  <span data-ttu-id="352ff-103">您可以使用這些方法在報表伺服器上管理工作、角色和原則。</span><span class="sxs-lookup"><span data-stu-id="352ff-103">You can use these methods to manage tasks, roles, and policies on the report server.</span></span>  
  
|<span data-ttu-id="352ff-104">方法</span><span class="sxs-lookup"><span data-stu-id="352ff-104">Method</span></span>|<span data-ttu-id="352ff-105">動作</span><span class="sxs-lookup"><span data-stu-id="352ff-105">Action</span></span>|  
|------------|------------|  
|<xref:ReportService2010.ReportingService2010.CreateRole%2A>|<span data-ttu-id="352ff-106">將新角色加入至報表伺服器資料庫。</span><span class="sxs-lookup"><span data-stu-id="352ff-106">Adds a new role to the report server database.</span></span> <span data-ttu-id="352ff-107">這個方法只適用於原生模式。</span><span class="sxs-lookup"><span data-stu-id="352ff-107">This method =applies to native mode only.</span></span>|  
|<xref:ReportService2010.ReportingService2010.DeleteRole%2A>|<span data-ttu-id="352ff-108">從報表伺服器資料庫刪除角色。</span><span class="sxs-lookup"><span data-stu-id="352ff-108">Deletes a role from the report server database.</span></span> <span data-ttu-id="352ff-109">這個方法只適用於原生模式。</span><span class="sxs-lookup"><span data-stu-id="352ff-109">This method applies to native mode only.</span></span>|  
|<xref:ReportService2010.ReportingService2010.GetPermissions%2A>|<span data-ttu-id="352ff-110">傳回與報表伺服器資料庫或 SharePoint 文件庫中特定項目關聯的使用者權限。</span><span class="sxs-lookup"><span data-stu-id="352ff-110">Returns the user permissions that are associated with a particular item in the report server database or SharePoint library.</span></span>|  
|<xref:ReportService2010.ReportingService2010.GetPolicies%2A>|<span data-ttu-id="352ff-111">傳回與報表伺服器資料庫或 SharePoint 文件庫中特定項目關聯的原則。</span><span class="sxs-lookup"><span data-stu-id="352ff-111">Returns the policies that are associated with a particular item in the report server database or SharePoint library.</span></span>|  
|<xref:ReportService2010.ReportingService2010.GetRoleProperties%2A>|<span data-ttu-id="352ff-112">傳回角色中繼資料屬性與關聯工作的集合。</span><span class="sxs-lookup"><span data-stu-id="352ff-112">Returns role metadata properties and a collection of associated tasks.</span></span>|  
|<xref:ReportService2010.ReportingService2010.GetSystemPermissions%2A>|<span data-ttu-id="352ff-113">傳回使用者的系統權限。</span><span class="sxs-lookup"><span data-stu-id="352ff-113">Returns the user's system permissions.</span></span> <span data-ttu-id="352ff-114">這個方法只適用於原生模式。</span><span class="sxs-lookup"><span data-stu-id="352ff-114">This method applies to native mode only.</span></span>|  
|<xref:ReportService2010.ReportingService2010.GetSystemPolicies%2A>|<span data-ttu-id="352ff-115">傳回系統原則，包括關聯的群組與角色。</span><span class="sxs-lookup"><span data-stu-id="352ff-115">Returns the system policies, including groups and roles with which they are associated.</span></span> <span data-ttu-id="352ff-116">這個方法只適用於原生模式。</span><span class="sxs-lookup"><span data-stu-id="352ff-116">This method applies to native mode only.</span></span>|  
|<xref:ReportService2010.ReportingService2010.InheritParentSecurity%2A>|<span data-ttu-id="352ff-117">刪除與報表伺服器資料庫中特定項目關聯的原則，並將項目的安全性原則設定為其父項的安全性原則。</span><span class="sxs-lookup"><span data-stu-id="352ff-117">Deletes the policies that are associated with a particular item in the report server database and sets the security policies for the item to those of its parent.</span></span>|  
|<xref:ReportService2010.ReportingService2010.IsSSLRequired%2A>|<span data-ttu-id="352ff-118">傳回布林值，指出是否需要安全通訊端層 (SSL) 通訊協定，以便使用 <xref:ReportService2010> 端點。</span><span class="sxs-lookup"><span data-stu-id="352ff-118">Returns a Boolean value that indicates whether the Secure Socket Layer (SSL) protocol is required to use the <xref:ReportService2010> end point.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ListRoles%2A>|<span data-ttu-id="352ff-119">傳回報表伺服器所管理角色的名稱與描述。</span><span class="sxs-lookup"><span data-stu-id="352ff-119">Returns the names and descriptions of roles that are managed by the report server.</span></span>|  
|<xref:ReportExecution2005.ReportExecutionService.ListSecureMethods%2A>|<span data-ttu-id="352ff-120">傳回在叫用時需要安全連接的 <xref:ReportExecution2005> 端點中，簡易物件存取通訊協定 (SOAP) 方法的清單。</span><span class="sxs-lookup"><span data-stu-id="352ff-120">Returns a list of Simple Object Access Protocol (SOAP) methods in the <xref:ReportExecution2005> endpoint that require a secure connection when invoked.</span></span> <span data-ttu-id="352ff-121">報表伺服器的 `SecureConnectionLevel` 設定是用以決定所要傳回的方法。</span><span class="sxs-lookup"><span data-stu-id="352ff-121">The `SecureConnectionLevel` setting of the report server is used to determine which methods are returned.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ListTasks%2A>|<span data-ttu-id="352ff-122">傳回由報表伺服器所管理的工作。</span><span class="sxs-lookup"><span data-stu-id="352ff-122">Returns the tasks that are managed by the report server.</span></span>|  
|<xref:ReportService2010.ReportingService2010.SetPolicies%2A>|<span data-ttu-id="352ff-123">設定與指定之項目關聯的原則。</span><span class="sxs-lookup"><span data-stu-id="352ff-123">Sets the policies that are associated with a specified item.</span></span>|  
|<xref:ReportService2010.ReportingService2010.SetRoleProperties%2A>|<span data-ttu-id="352ff-124">設定角色中繼資料屬性，並將一組工作與角色相關聯。</span><span class="sxs-lookup"><span data-stu-id="352ff-124">Sets role metadata properties and associates a set of tasks with a role.</span></span> <span data-ttu-id="352ff-125">這個方法只適用於原生模式。</span><span class="sxs-lookup"><span data-stu-id="352ff-125">This method applies to native mode only.</span></span>|  
|<xref:ReportService2010.ReportingService2010.SetSystemPolicies%2A>|<span data-ttu-id="352ff-126">設定系統原則，以定義群組及其關聯的角色。</span><span class="sxs-lookup"><span data-stu-id="352ff-126">Sets the system policy that defines groups and their associated roles.</span></span> <span data-ttu-id="352ff-127">這個方法只適用於原生模式。</span><span class="sxs-lookup"><span data-stu-id="352ff-127">This method applies to native mode only.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="352ff-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="352ff-128">See Also</span></span>  
 <span data-ttu-id="352ff-129">[使用 Web 服務和 .NET Framework 建置應用程式](../net-framework/building-applications-using-the-web-service-and-the-net-framework.md) </span><span class="sxs-lookup"><span data-stu-id="352ff-129">[Building Applications Using the Web Service and the .NET Framework](../net-framework/building-applications-using-the-web-service-and-the-net-framework.md) </span></span>  
 <span data-ttu-id="352ff-130">[報表伺服器 Web 服務](../report-server-web-service.md) </span><span class="sxs-lookup"><span data-stu-id="352ff-130">[Report Server Web Service](../report-server-web-service.md) </span></span>  
 <span data-ttu-id="352ff-131">[報表伺服器 Web 服務方法](report-server-web-service-methods.md) </span><span class="sxs-lookup"><span data-stu-id="352ff-131">[Report Server Web Service Methods](report-server-web-service-methods.md) </span></span>  
 [<span data-ttu-id="352ff-132">技術參考 &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="352ff-132">Technical Reference &#40;SSRS&#41;</span></span>](../../technical-reference-ssrs.md)  
  
  
