---
title: DQS 安全性 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 921927f5-1b1e-452a-a79e-c691829fd826
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 3da3cdbe746b69c5c4cfe7c7c796827dd74a433c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700276"
---
# <a name="dqs-security"></a><span data-ttu-id="6bf85-102">DQS 安全性</span><span class="sxs-lookup"><span data-stu-id="6bf85-102">DQS Security</span></span>
  <span data-ttu-id="6bf85-103">[!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) 安全性基礎結構是根據 SQL Server 安全性基礎結構。</span><span class="sxs-lookup"><span data-stu-id="6bf85-103">The [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) security infrastructure is based upon the SQL Server security infrastructure.</span></span> <span data-ttu-id="6bf85-104">資料庫管理員會將使用者與 DQS 角色產生關聯，將一組權限授與該使用者。</span><span class="sxs-lookup"><span data-stu-id="6bf85-104">A database administrator grants a user a set of permissions by associating the user with a DQS role.</span></span> <span data-ttu-id="6bf85-105">這樣做會決定使用者可存取的 DQS 資源以及允許使用者執行的功能活動。</span><span class="sxs-lookup"><span data-stu-id="6bf85-105">Doing so determines the DQS resources that the user has access to and the functional activities that the user is allowed to perform.</span></span>  
  
## <a name="dqs-roles"></a><span data-ttu-id="6bf85-106">DQS 角色</span><span class="sxs-lookup"><span data-stu-id="6bf85-106">DQS Roles</span></span>  
 <span data-ttu-id="6bf85-107">DQS 有四個角色。</span><span class="sxs-lookup"><span data-stu-id="6bf85-107">There are four roles for DQS.</span></span> <span data-ttu-id="6bf85-108">其中一個是資料庫管理員 (DBA)，他主要負責處理產品安裝、資料庫維護和使用者管理。</span><span class="sxs-lookup"><span data-stu-id="6bf85-108">One is the database administrator (DBA) who deals primarily with product installation, database maintenance, and user management.</span></span> <span data-ttu-id="6bf85-109">這個角色主要是使用 SQL Server Management Studio，而不是 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 應用程式。</span><span class="sxs-lookup"><span data-stu-id="6bf85-109">This role primarily uses the SQL Server Management Studio, rather than within the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] application.</span></span> <span data-ttu-id="6bf85-110">其伺服器角色是系統管理員 (sysadmin)。</span><span class="sxs-lookup"><span data-stu-id="6bf85-110">Their server role is sysadmin.</span></span>  
  
 <span data-ttu-id="6bf85-111">還有兩個其他角色，分別是資訊工作者，以及在 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 應用程式中工作來直接使用產品的資料監管。</span><span class="sxs-lookup"><span data-stu-id="6bf85-111">The three other roles are information workers, data stewards who use the product directly by working in the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] application.</span></span> <span data-ttu-id="6bf85-112">這些角色包括下列各項：</span><span class="sxs-lookup"><span data-stu-id="6bf85-112">These roles include the following:</span></span>  
  
-   <span data-ttu-id="6bf85-113">**DQS 系統管理員** (dqs_administrator 角色) 可以在產品的範圍內執行任何工作。</span><span class="sxs-lookup"><span data-stu-id="6bf85-113">The **DQS Administrator** (dqs_administrator role) can do everything in the scope of the product.</span></span> <span data-ttu-id="6bf85-114">管理員可以編輯和執行專案、建立和編輯知識庫、終止活動、停止活動內的程序，也可以變更組態和參考資料服務設定。</span><span class="sxs-lookup"><span data-stu-id="6bf85-114">The administrator can edit and execute a project, create and edit a knowledge base, terminate an activity, stop a process within an activity, and can change the configuration and Reference Data Services settings.</span></span> <span data-ttu-id="6bf85-115">但是 DQS 管理員無法安裝伺服器或新增使用者。</span><span class="sxs-lookup"><span data-stu-id="6bf85-115">The DQS Administrator cannot, however, install the server or add new users.</span></span> <span data-ttu-id="6bf85-116">這必須由資料庫管理員來執行。</span><span class="sxs-lookup"><span data-stu-id="6bf85-116">The database administrator must do that.</span></span>  
  
-   <span data-ttu-id="6bf85-117">**DQS KB 編輯者** (dqs_kb_editor 角色) 可以執行管理以外的所有 DQS 活動。</span><span class="sxs-lookup"><span data-stu-id="6bf85-117">The **DQS KB Editor** (dqs_kb_editor role) can perform all of the DQS activities, except for administration.</span></span> <span data-ttu-id="6bf85-118">KB 編輯者可以編輯和執行專案以及建立和編輯知識庫。</span><span class="sxs-lookup"><span data-stu-id="6bf85-118">The KB Editor can edit and execute a project, and create and edit a knowledge base.</span></span> <span data-ttu-id="6bf85-119">他們可以看到活動監控資料，但不能終止或停止活動或是履行管理職責。</span><span class="sxs-lookup"><span data-stu-id="6bf85-119">They can see the activity monitoring data, but cannot terminate or stop an activity or perform administrative duties.</span></span>  
  
-   <span data-ttu-id="6bf85-120">**DQS KB 操作員** (dqs_kb_operator 角色) 可以編輯和執行專案。</span><span class="sxs-lookup"><span data-stu-id="6bf85-120">The **DQS KB Operator** (dqs_kb_operator role) can edit and execute a project.</span></span> <span data-ttu-id="6bf85-121">他們不能執行任何種類的知識管理，也不能建立或變更知識庫。</span><span class="sxs-lookup"><span data-stu-id="6bf85-121">They cannot perform any kind of knowledge management; they cannot create or change a knowledge base.</span></span> <span data-ttu-id="6bf85-122">他們可以看到活動監控資料，但不能終止活動或履行管理職責。</span><span class="sxs-lookup"><span data-stu-id="6bf85-122">They can see the activity monitoring data, but cannot terminate an activity or perform administrative duties.</span></span>  
  
## <a name="user-management"></a><span data-ttu-id="6bf85-123">使用者管理</span><span class="sxs-lookup"><span data-stu-id="6bf85-123">User Management</span></span>  
 <span data-ttu-id="6bf85-124">資料庫管理員 (DBA) 會建立 DQS 使用者，並在 SQL Server Management Studio 中將這些使用者與 DQS 角色產生關聯。</span><span class="sxs-lookup"><span data-stu-id="6bf85-124">The database administrator (DBA) creates DQS users and associates them with DQS roles in SQL Server Management Studio.</span></span> <span data-ttu-id="6bf85-125">DBA 會管理其權限，方法是新增 SQL 登入當做 DQS_MAIN 資料庫的使用者，並將每一個使用者與其中一個 DQS 角色產生關聯。</span><span class="sxs-lookup"><span data-stu-id="6bf85-125">The DBA manages their permissions by adding SQL Logins as users of the DQS_MAIN database, and associating each user with one of the DQS roles.</span></span> <span data-ttu-id="6bf85-126">每個角色都會被授與 DQS_MAIN 資料庫上一組預存程序的權限。</span><span class="sxs-lookup"><span data-stu-id="6bf85-126">Each role is granted permissions to a set of stored procedures on the DQS_MAIN database.</span></span> <span data-ttu-id="6bf85-127">這三個 DQS 角色不適用於 DQS_PROJECTS 和 DQS_STAGING_DATA 資料庫。</span><span class="sxs-lookup"><span data-stu-id="6bf85-127">The three DQS roles are not available for the DQS_PROJECTS and DQS_STAGING_DATA databases.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="6bf85-128">相關工作</span><span class="sxs-lookup"><span data-stu-id="6bf85-128">Related Tasks</span></span>  
  
|<span data-ttu-id="6bf85-129">工作描述</span><span class="sxs-lookup"><span data-stu-id="6bf85-129">Task Description</span></span>|<span data-ttu-id="6bf85-130">主題</span><span class="sxs-lookup"><span data-stu-id="6bf85-130">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="6bf85-131">描述如何使用 SQL Server Management Studio 建立使用者及授與 DQS 角色。</span><span class="sxs-lookup"><span data-stu-id="6bf85-131">Describes how to create a user and grant DQS roles using SQL Server Management Studio.</span></span>|[<span data-ttu-id="6bf85-132">在 SSMS 中管理 DQS 使用者</span><span class="sxs-lookup"><span data-stu-id="6bf85-132">Manage DQS Users in SSMS</span></span>](../../2014/data-quality-services/manage-dqs-users-in-ssms.md)|  
  
  
