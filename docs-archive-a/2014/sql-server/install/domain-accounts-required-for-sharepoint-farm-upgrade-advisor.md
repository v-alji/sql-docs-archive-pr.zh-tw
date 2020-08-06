---
title: SharePoint 伺服器陣列 (Upgrade Advisor) 所需的網域帳戶 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 90cd6d3e-a271-4cb8-81f2-fc555b2d3cab
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 7d180fbc12a264256156c878916838f7caeec723
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606606"
---
# <a name="domain-accounts-required-for-sharepoint-farm-upgrade-advisor"></a><span data-ttu-id="968fe-102">SharePoint 伺服陣列所需的網域帳戶 (Upgrade Advisor)</span><span class="sxs-lookup"><span data-stu-id="968fe-102">Domain accounts required for SharePoint farm (Upgrade Advisor)</span></span>
  <span data-ttu-id="968fe-103">針對伺服陣列環境設定的 SharePoint 產品需要使用網域帳戶。</span><span class="sxs-lookup"><span data-stu-id="968fe-103">SharePoint products that are configured for a farm environment require that you use domain accounts.</span></span>  
  
||  
|-|  
|<span data-ttu-id="968fe-104">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]SharePoint 模式。</span><span class="sxs-lookup"><span data-stu-id="968fe-104">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode.</span></span>|  
  
## <a name="component"></a><span data-ttu-id="968fe-105">元件</span><span class="sxs-lookup"><span data-stu-id="968fe-105">Component</span></span>  
 [!INCLUDE[ssRS](../../includes/ssrs.md)]  
  
### <a name="description"></a><span data-ttu-id="968fe-106">描述</span><span class="sxs-lookup"><span data-stu-id="968fe-106">Description</span></span>  
 <span data-ttu-id="968fe-107">針對伺服陣列環境設定的 SharePoint 產品需要將網域帳戶用於服務和資料庫連接。</span><span class="sxs-lookup"><span data-stu-id="968fe-107">SharePoint products that are configured for a farm environment require that you use domain accounts for services and database connections.</span></span> <span data-ttu-id="968fe-108">其中包括您為 Reporting Services 服務帳戶指定的帳戶。</span><span class="sxs-lookup"><span data-stu-id="968fe-108">This includes the account you have specified for the Reporting Services service account.</span></span>  
  
 <span data-ttu-id="968fe-109">如果您並未在 Reporting Services 中使用網域使用者帳戶，您就會在 SharePoint 2010 管理中心頁面中看到問題。</span><span class="sxs-lookup"><span data-stu-id="968fe-109">SharePoint 2010 Central Administration pages are one place you will see problems if you are not using a domain user account for Reporting Services.</span></span> <span data-ttu-id="968fe-110">當您嘗試設定 Reporting Services 整合時，您會看到類似底下的錯誤訊息：</span><span class="sxs-lookup"><span data-stu-id="968fe-110">When you try to configure Reporting Services integration, you will see an error message similar to the following:</span></span>  
  
 <span data-ttu-id="968fe-111">「報表伺服器是以內建的 NT AUTHORITY\NETWORK SERVICE 帳戶執行，但 SharePoint 伺服陣列安裝不支援該帳戶。</span><span class="sxs-lookup"><span data-stu-id="968fe-111">"The report server is running under the built-in NT AUTHORITY\NETWORK SERVICE account, which is not supported by a SharePoint farm installation.</span></span> <span data-ttu-id="968fe-112">請將報表伺服器重新設定成以網域帳戶執行。」</span><span class="sxs-lookup"><span data-stu-id="968fe-112">Please reconfigure the report server to run under a domain account."</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="968fe-113">更正動作</span><span class="sxs-lookup"><span data-stu-id="968fe-113">Corrective Action</span></span>  
 <span data-ttu-id="968fe-114">若是 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 和舊版，請使用 Reporting Services 組態管理員來變更指派為報表伺服器服務帳戶的帳戶。</span><span class="sxs-lookup"><span data-stu-id="968fe-114">For [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] and previous versions, use the Reporting Services Configuration Manager to change the account that is assigned as the report server service account.</span></span>  
  
#### <a name="to-change-the-service-account-from-configuration-manager"></a><span data-ttu-id="968fe-115">若要從組態管理員變更服務帳戶</span><span class="sxs-lookup"><span data-stu-id="968fe-115">To change the service account from Configuration Manager</span></span>  
  
1.  <span data-ttu-id="968fe-116">從 [**開始**] 功能表選取 [**所有程式**]，然後按一下 [ **Microsoft SQL Server 2008 R2**]。</span><span class="sxs-lookup"><span data-stu-id="968fe-116">From the **Start** menu, select **All Programs**, and then click **Microsoft SQL Server 2008 R2**.</span></span>  
  
2.  <span data-ttu-id="968fe-117">選取 [**組態工具**]，然後按一下 [ **Reporting Services 組態管理員**]。</span><span class="sxs-lookup"><span data-stu-id="968fe-117">Select **Configuration Tools**, and then click **Reporting Services Configuration Manager**.</span></span>  
  
3.  <span data-ttu-id="968fe-118">在 Configuration Manager 中，選取 [**服務帳戶**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="968fe-118">In Configuration Manager, select the **Service Account** tab.</span></span>  
  
4.  <span data-ttu-id="968fe-119">選取 [**使用其他帳戶**]，然後輸入網域帳戶的認證。</span><span class="sxs-lookup"><span data-stu-id="968fe-119">Select **Use another account** and enter the credentials for a domain account.</span></span>  
  
5.  <span data-ttu-id="968fe-120">按一下 [套用]。</span><span class="sxs-lookup"><span data-stu-id="968fe-120">Click **Apply**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="968fe-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="968fe-121">See Also</span></span>  
 [<span data-ttu-id="968fe-122">設定報表伺服器服務帳戶 &#40;SSRS 組態管理員&#41;</span><span class="sxs-lookup"><span data-stu-id="968fe-122">Configure the Report Server Service Account &#40;SSRS Configuration Manager&#41;</span></span>](../../reporting-services/install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md)  
  
  
