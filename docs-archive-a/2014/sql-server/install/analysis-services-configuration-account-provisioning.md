---
title: Analysis Services 設定-帳戶提供 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Analysis Services configuration
- account provisioning
ms.assetid: 169b1af2-6fe2-467f-8ca4-919f24c620ce
author: heidisteen
ms.author: heidist
ms.openlocfilehash: 109b5d9ddddf2b78c0bb8947cfa876d233f804ea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595538"
---
# <a name="analysis-services-configuration---account-provisioning"></a><span data-ttu-id="3ad22-102">Analysis Services 組態 - 帳戶提供</span><span class="sxs-lookup"><span data-stu-id="3ad22-102">Analysis Services Configuration - Account Provisioning</span></span>
  <span data-ttu-id="3ad22-103">此用此頁面可以設定伺服器模式，以及將管理權限授與需要無限制存取 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 的使用者或服務。</span><span class="sxs-lookup"><span data-stu-id="3ad22-103">Use this page to set the server mode, and to grant administrative permissions to users or services requiring unrestricted access to [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="3ad22-104">安裝程式不會自動將本機 Windows 群組 BUILTIN\Administrators 加入您所安裝之執行個體的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 伺服器管理員角色。</span><span class="sxs-lookup"><span data-stu-id="3ad22-104">Setup does not automatically add the local Windows Group BUILTIN\Administrators to the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] server administrator role of the instance you are installing.</span></span> <span data-ttu-id="3ad22-105">如果您想要將本機 Administrators 群組加入至伺服器管理員角色，就必須明確指定該群組。</span><span class="sxs-lookup"><span data-stu-id="3ad22-105">If you want to add the local Administrators group to the server administrator role, you must explicitly specify that group.</span></span>  
  
 <span data-ttu-id="3ad22-106">如果您要安裝 [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]，請務必將管理權限授與負責在 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 伺服陣列中進行 [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] 部署的 SharePoint 伺服陣列管理員或服務管理員。</span><span class="sxs-lookup"><span data-stu-id="3ad22-106">If you are installing [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)], be sure to grant administrative permissions to SharePoint farm administrators or service administrators who are responsible for a [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] server deployment in a [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] farm.</span></span> <span data-ttu-id="3ad22-107">如需有關 [!INCLUDE[ssGeminiMTS](../../includes/ssgeminimts-md.md)] 安裝和服務帳戶需求的詳細資訊，請參閱[使用 SharePoint &#40;PowerPivot 和 Reporting Services&#41;安裝 SQL Server BI 功能](../../../2014/sql-server/install/install-sql-server-bi-features-sharepoint-powerpivot-reporting-services.md)。</span><span class="sxs-lookup"><span data-stu-id="3ad22-107">For more information about [!INCLUDE[ssGeminiMTS](../../includes/ssgeminimts-md.md)] installation and service account requirements, see [Install SQL Server BI Features with SharePoint &#40;PowerPivot and Reporting Services&#41;](../../../2014/sql-server/install/install-sql-server-bi-features-sharepoint-powerpivot-reporting-services.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="3ad22-108">選項</span><span class="sxs-lookup"><span data-stu-id="3ad22-108">Options</span></span>  
 <span data-ttu-id="3ad22-109">**伺服器模式** - 伺服器模式指定可以部署到伺服器的 Analysis Services 資料庫類型。</span><span class="sxs-lookup"><span data-stu-id="3ad22-109">**Server Mode** - The server mode specifies the type of Analysis Services databases that can be deployed to the server.</span></span> <span data-ttu-id="3ad22-110">伺服器模式是在安裝期間決定，之後不能修改。</span><span class="sxs-lookup"><span data-stu-id="3ad22-110">Server modes are determined during Setup and cannot be modified later.</span></span> <span data-ttu-id="3ad22-111">每個模式是互斥的，也就是說，您需要兩個 Analysis Services 執行個體，各設定為不同的模式，以便同時支援傳統 OLAP 和表格式模型方案。</span><span class="sxs-lookup"><span data-stu-id="3ad22-111">Each mode is mutually exclusive, which means that you will need two instances of Analysis Services, each configured for a different mode, to support both classic OLAP and tabular model solutions.</span></span>  
  
 <span data-ttu-id="3ad22-112">**指定管理員** - 您必須為 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體至少指定一個伺服器管理員。</span><span class="sxs-lookup"><span data-stu-id="3ad22-112">**Specify Administrators** - You must specify at least one server administrator for the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="3ad22-113">您所指定的使用者或群組將成為所安裝之 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體的伺服器管理員角色成員。</span><span class="sxs-lookup"><span data-stu-id="3ad22-113">The users or groups that you specify will become members of the server administrator role of the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance you are installing.</span></span> <span data-ttu-id="3ad22-114">這些都必須是與安裝該軟體的電腦處於相同網域中的 Windows 網域使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="3ad22-114">These must be Windows domain user accounts in the same domain as the computer on which you are installing the software.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3ad22-115">使用者帳戶控制 (UAC) 為 Windows 安全性功能，會要求系統管理員明確地核准系統管理動作或應用程式，之後才會允許這些項目執行。</span><span class="sxs-lookup"><span data-stu-id="3ad22-115">User Account Control (UAC) is a Windows security feature that requires an administrator to specifically approve administrative actions or applications before they are allowed to run.</span></span> <span data-ttu-id="3ad22-116">由於 UAC 預設為開啟，系統將會提示您允許需要更高權限的特定作業。</span><span class="sxs-lookup"><span data-stu-id="3ad22-116">Because UAC is on by default, you will be prompted to allow specific operations that require elevated privileges.</span></span> <span data-ttu-id="3ad22-117">您可以設定 UAC，以變更預設行為或針對特定程式自訂 UAC。</span><span class="sxs-lookup"><span data-stu-id="3ad22-117">You can configure UAC to change the default behavior or customize UAC for specific programs.</span></span> <span data-ttu-id="3ad22-118">如需 UAC 和 UAC 設定的詳細資訊，請參閱[使用者帳戶控制逐步指南](https://go.microsoft.com/fwlink/?linkid=196350)和[使用者帳戶控制 (維琪百科) ](https://go.microsoft.com/fwlink/?linkid=196351)。</span><span class="sxs-lookup"><span data-stu-id="3ad22-118">For more information about UAC and UAC configuration, see [User Account Control Step by Step Guide](https://go.microsoft.com/fwlink/?linkid=196350) and [User Account Control (Wikipedia)](https://go.microsoft.com/fwlink/?linkid=196351).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ad22-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3ad22-119">See Also</span></span>  
 <span data-ttu-id="3ad22-120">[設定服務帳戶 &#40;Analysis Services&#41;](../../../2014/analysis-services/instances/configure-service-accounts-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="3ad22-120">[Configure Service Accounts &#40;Analysis Services&#41;](../../../2014/analysis-services/instances/configure-service-accounts-analysis-services.md) </span></span>  
 [<span data-ttu-id="3ad22-121">設定 Windows 服務帳戶與權限</span><span class="sxs-lookup"><span data-stu-id="3ad22-121">Configure Windows Service Accounts and Permissions</span></span>](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)  
  
  
