---
title: 安裝程式角色 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: c7e9db15-89f2-4d4d-8860-1e64c5821c4d
author: heidisteen
ms.author: heidist
ms.openlocfilehash: add000eed671303c78ab0500303f826bafe4ab77
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595453"
---
# <a name="setup-role"></a><span data-ttu-id="28c06-102">安裝程式角色</span><span class="sxs-lookup"><span data-stu-id="28c06-102">Setup Role</span></span>
  <span data-ttu-id="28c06-103">您可以使用此頁面來指定要使用 [特徵選取] 頁面選取個別功能，還是使用安裝程式角色進行安裝。</span><span class="sxs-lookup"><span data-stu-id="28c06-103">Use this page to specify whether to use the Feature Selection page to select individual features, or to install using a setup role.</span></span>  
  
 <span data-ttu-id="28c06-104">`setup role` 是實作預先定義 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 組態所需之所有功能與共用元件的固定選項。</span><span class="sxs-lookup"><span data-stu-id="28c06-104">A `setup role` is a fixed selection of all the features and shared components that are required to implement a predefined [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] configuration.</span></span>  
  
## <a name="options"></a><span data-ttu-id="28c06-105">選項</span><span class="sxs-lookup"><span data-stu-id="28c06-105">Options</span></span>  
 <span data-ttu-id="28c06-106">**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]功能安裝**</span><span class="sxs-lookup"><span data-stu-id="28c06-106">**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Feature Installation**</span></span>  
 <span data-ttu-id="28c06-107">選擇此選項來選取個別功能與共用元件。</span><span class="sxs-lookup"><span data-stu-id="28c06-107">Choose this option to select individual features and shared components.</span></span> <span data-ttu-id="28c06-108">執行個體功能包括 Database Engine Services、Analysis Services (原生模式) 和 Reporting Services。</span><span class="sxs-lookup"><span data-stu-id="28c06-108">Instance features include Database Engine Services, Analysis Services (native mode), and Reporting Services.</span></span>  
  
 <span data-ttu-id="28c06-109">**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]PowerPivot for SharePoint**</span><span class="sxs-lookup"><span data-stu-id="28c06-109">**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerPivot for SharePoint**</span></span>  
 <span data-ttu-id="28c06-110">選擇此選項將 Analysis Services 伺服器元件安裝在 SharePoint 2010 伺服陣列中。</span><span class="sxs-lookup"><span data-stu-id="28c06-110">Choose this option to install Analysis Services server components in a SharePoint 2010 farm.</span></span> <span data-ttu-id="28c06-111">此選項會在伺服陣列中部署 PowerPivot 系統服務與 Analysis Services 伺服器，讓您針對包含內嵌 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 資料的已發行 Excel 活頁簿進行查詢與資料處理。</span><span class="sxs-lookup"><span data-stu-id="28c06-111">This option deploys the PowerPivot System Service and the Analysis Services server in a farm, enabling query and data processing for published Excel workbooks that contain embedded [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] data.</span></span>  
  
 <span data-ttu-id="28c06-112">如果需要關聯式資料庫引擎執行個體以裝載 SharePoint 伺服器陣列的資料庫，可以選擇在安裝中新增關聯式資料庫引擎執行個體。</span><span class="sxs-lookup"><span data-stu-id="28c06-112">Optionally, you can add a relational database engine instance to your installation if you require it to host databases in a SharePoint farm.</span></span> <span data-ttu-id="28c06-113">如果已設定伺服器陣列，您就可以略過此選項。</span><span class="sxs-lookup"><span data-stu-id="28c06-113">If the farm is already configured, you can skip this option.</span></span>  
  
 <span data-ttu-id="28c06-114">安裝完成後，必須使用下列其中一個方法設定軟體：PowerPivot 配置工具、PowerShell 指令程式或 SharePoint 2010 管理中心。</span><span class="sxs-lookup"><span data-stu-id="28c06-114">After Setup is finished, you must configure the software using one of the following approaches: PowerPivot Configuration tool, PowerShell cmdlets, or SharePoint 2010 Central Administration.</span></span> <span data-ttu-id="28c06-115">相對於舊版，安裝程式不再執行 PowerPivot 安裝的任何組態工作。</span><span class="sxs-lookup"><span data-stu-id="28c06-115">In contrast with previous releases, Setup no longer performs any configuration tasks for a PowerPivot installation.</span></span>  
  
 <span data-ttu-id="28c06-116">以角色為基礎的安裝不包含 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerPivot for Excel 用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="28c06-116">A role-based installation does not include the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerPivot for Excel client application.</span></span> <span data-ttu-id="28c06-117">用戶端應用程式要另外安裝。</span><span class="sxs-lookup"><span data-stu-id="28c06-117">The client application is installed separately.</span></span>  
  
 <span data-ttu-id="28c06-118">**具有預設值的所有功能**</span><span class="sxs-lookup"><span data-stu-id="28c06-118">**All Features With Defaults**</span></span>  
 <span data-ttu-id="28c06-119">選擇此安裝程式角色來安裝可用於此版本的所有功能。</span><span class="sxs-lookup"><span data-stu-id="28c06-119">Choose this setup role to install all features that are available for this release.</span></span> <span data-ttu-id="28c06-120">請注意，這個角色中會排除 PowerPivot for SharePoint。</span><span class="sxs-lookup"><span data-stu-id="28c06-120">Note that PowerPivot for SharePoint is excluded from this role.</span></span> <span data-ttu-id="28c06-121">您必須使用 PowerPivot for SharePoint 安裝程式角色來安裝該功能。</span><span class="sxs-lookup"><span data-stu-id="28c06-121">You must use the PowerPivot for SharePoint setup role to install that feature.</span></span>  
  
 <span data-ttu-id="28c06-122">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 設定為使用 **NT AUTHORITY\NETWORK SERVICE** 帳戶啟動。</span><span class="sxs-lookup"><span data-stu-id="28c06-122">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] is configured to start using the **NT AUTHORITY\NETWORK SERVICE** account.</span></span> <span data-ttu-id="28c06-123">目前的使用者將會當作 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**系統管理員** 角色的成員提供。</span><span class="sxs-lookup"><span data-stu-id="28c06-123">The current user will be provisioned as a member of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**sysadmin** role.</span></span> <span data-ttu-id="28c06-124">此選項所設定的值可透過指定其他命令行參數來覆寫。</span><span class="sxs-lookup"><span data-stu-id="28c06-124">Values set by this option can be overridden by specifying additional command line parameters.</span></span>  
  
 <span data-ttu-id="28c06-125">當作業系統不是網域控制站時，Database Engine 和 Reporting Services 預設會使用 NTAUTHORITY\NETWORK SERVICE 帳戶、Integration Services 會使用 NTAUTHORITY\NETWORK SERVICE 帳戶，而 SQL 全文檢索篩選背景程式啟動器則會使用 NTAUTHORITY\LOCAL SERVICE 帳戶。</span><span class="sxs-lookup"><span data-stu-id="28c06-125">When the operating system is not a domain controller, by default the Database Engine and Reporting Services will use the NTAUTHORITY\NETWORK SERVICE account, Integration Services will use the NTAUTHORITY\NETWORK SERVICE account, and the SQL Full text Filter Daemon Launcher will use the NTAUTHORITY\LOCAL SERVICE account.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28c06-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="28c06-126">See Also</span></span>  
 <span data-ttu-id="28c06-127">[安裝 PowerPivot for SharePoint](https://go.microsoft.com/fwlink/?LinkId=206906) </span><span class="sxs-lookup"><span data-stu-id="28c06-127">[Installing PowerPivot for SharePoint](https://go.microsoft.com/fwlink/?LinkId=206906) </span></span>  
 <span data-ttu-id="28c06-128">[硬體和軟體需求 (PowerPivot for SharePoint](https://go.microsoft.com/fwlink/?LinkId=216823) </span><span class="sxs-lookup"><span data-stu-id="28c06-128">[Hardware and Software Requirements (PowerPivot for SharePoint](https://go.microsoft.com/fwlink/?LinkId=216823) </span></span>  
 [<span data-ttu-id="28c06-129">特徵選取</span><span class="sxs-lookup"><span data-stu-id="28c06-129">Feature Selection</span></span>](../../../2014/sql-server/install/feature-selection.md)  
  
  
