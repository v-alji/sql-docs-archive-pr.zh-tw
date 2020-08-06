---
title: 角色與權限 (Reporting Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- access controls [Reporting Services]
- permissions [Reporting Services], about permissions
- security [Reporting Services], identity and access control
- authentication [Reporting Services]
- permissions [Reporting Services]
- security [Reporting Services], role-based
- identity [Reporting Services]
ms.assetid: eea655fe-43ed-418d-8233-b288a8f4daa4
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 0e6098a51afde04164e3ef0dfa5e5297457b4440
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596480"
---
# <a name="roles-and-permissions-reporting-services"></a><span data-ttu-id="6dba0-102">角色與權限 (Reporting Services)</span><span class="sxs-lookup"><span data-stu-id="6dba0-102">Roles and Permissions (Reporting Services)</span></span>
  <span data-ttu-id="6dba0-103">Reporting Services 會提供驗證子系統和以角色為基礎的授權模型。</span><span class="sxs-lookup"><span data-stu-id="6dba0-103">Reporting Services provides an authentication subsystem and role-based authorization model.</span></span> <span data-ttu-id="6dba0-104">驗證和授權模型會因報表伺服器是以原生模式或 SharePoint 模式執行而不同。</span><span class="sxs-lookup"><span data-stu-id="6dba0-104">Authentication and authorization models vary depending on whether the report server runs in native mode or SharePoint mode.</span></span> <span data-ttu-id="6dba0-105">如果報表伺服器屬於 SharePoint 部署的一部分，SharePoint 權限將決定擁有報表伺服器存取權的人員。</span><span class="sxs-lookup"><span data-stu-id="6dba0-105">If the report server is part of a SharePoint deployment, SharePoint permissions determine who has access to the report server.</span></span>  
  
## <a name="identity-and-access-control-for-native-mode"></a><span data-ttu-id="6dba0-106">原生模式的識別和存取控制</span><span class="sxs-lookup"><span data-stu-id="6dba0-106">Identity and Access Control for Native Mode</span></span>  
 <span data-ttu-id="6dba0-107">預設驗證是以 Windows 驗證和整合式安全性為基礎。</span><span class="sxs-lookup"><span data-stu-id="6dba0-107">Default authentication is based on Windows Authentication and integrated security.</span></span> <span data-ttu-id="6dba0-108">您可變更這些驗證設定，以便允許報表伺服器回應不同的驗證要求，甚至是將預設的安全性功能取代成您提供的自訂驗證延伸模組。</span><span class="sxs-lookup"><span data-stu-id="6dba0-108">You can change the authentication settings to allow the report server to respond to different authentication requests, or even replace the default security features with a custom authentication extension that you provide.</span></span>  
  
 <span data-ttu-id="6dba0-109">授權是以您指派給原則的角色為基礎。</span><span class="sxs-lookup"><span data-stu-id="6dba0-109">Authorization is based on roles that you assign to a principle.</span></span> <span data-ttu-id="6dba0-110">每個角色都包含一組相關的工作，然後這些工作則包含相關的作業。</span><span class="sxs-lookup"><span data-stu-id="6dba0-110">Each role consists of a set of related tasks, which are in turn composed of related operations.</span></span> <span data-ttu-id="6dba0-111">例如，[管理報表]  工作會授與下列報表伺服器作業的存取權：檢視報表、新增報表、更新報表、刪除報表、排程報表和更新報表屬性。</span><span class="sxs-lookup"><span data-stu-id="6dba0-111">For example, the **Manage reports** task grants access to the following report server operations: view reports, add report, update report, delete report, schedule report, and update report properties.</span></span>  
  
## <a name="identity-and-access-control-for-sharepoint-mode"></a><span data-ttu-id="6dba0-112">SharePoint 模式的識別和存取控制</span><span class="sxs-lookup"><span data-stu-id="6dba0-112">Identity and Access Control for SharePoint Mode</span></span>  
 <span data-ttu-id="6dba0-113">在 SharePoint 整合模式中，驗證和授權會先在 SharePoint 網站上處理，然後要求才會送達報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="6dba0-113">In SharePoint integrated mode, authentication and authorization are handled on the SharePoint site, before requests reach the report server.</span></span> <span data-ttu-id="6dba0-114">根據您設定驗證的方式而定，來自 SharePoint 網站的要求會包含安全性 Token 或受信任的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="6dba0-114">Depending on how you configure authentication, requests from a SharePoint site include a security token or a trusted user name.</span></span> <span data-ttu-id="6dba0-115">您針對 SharePoint 使用者和群組所設定的權限會授權放置於 SharePoint 文件庫中之報表伺服器項目的存取權。</span><span class="sxs-lookup"><span data-stu-id="6dba0-115">Permissions that you set for SharePoint users and groups authorize access to report server items that are placed in SharePoint libraries.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6dba0-116">本節內容</span><span class="sxs-lookup"><span data-stu-id="6dba0-116">In This Section</span></span>  
 [<span data-ttu-id="6dba0-117">在原生模式報表伺服器上授與權限</span><span class="sxs-lookup"><span data-stu-id="6dba0-117">Granting Permissions on a Native Mode Report Server</span></span>](granting-permissions-on-a-native-mode-report-server.md)  
 <span data-ttu-id="6dba0-118">描述提供內容和作業之存取權的以角色為基礎授權模型。</span><span class="sxs-lookup"><span data-stu-id="6dba0-118">Describes the role-based authorization model that provides access to content and operations.</span></span>  
  
 [<span data-ttu-id="6dba0-119">授與 SharePoint 網站上報表伺服器項目的權限</span><span class="sxs-lookup"><span data-stu-id="6dba0-119">Granting Permissions on Report Server Items on a SharePoint Site</span></span>](granting-permissions-on-report-server-items-on-a-sharepoint-site.md)  
 <span data-ttu-id="6dba0-120">說明 SharePoint 群組、權限等級和權限如何用於控制報表伺服器的存取權。</span><span class="sxs-lookup"><span data-stu-id="6dba0-120">Explains how SharePoint groups, permission levels, and permissions are used to control access to a report server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6dba0-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6dba0-121">See Also</span></span>  
 <span data-ttu-id="6dba0-122">[使用報表伺服器驗證](authentication-with-the-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="6dba0-122">[Authentication with the Report Server](authentication-with-the-report-server.md) </span></span>  
 [<span data-ttu-id="6dba0-123">在原生模式報表伺服器上授與權限</span><span class="sxs-lookup"><span data-stu-id="6dba0-123">Granting Permissions on a Native Mode Report Server</span></span>](granting-permissions-on-a-native-mode-report-server.md)  
  
  
