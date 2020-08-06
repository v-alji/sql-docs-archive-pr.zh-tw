---
title: 如何：安裝 Upgrade Advisor |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- installing Upgrade Advisor
- Setup [Upgrade Advisor]
- SQL Server Upgrade Advisor, installing
- Upgrade Advisor [SQL Server], installing
ms.assetid: 481b0704-ce79-4543-b141-67306128aa2b
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 3ed5b66522126bfabc94bfa8036ec6c31ac04500
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606048"
---
# <a name="how-to-install-upgrade-advisor"></a><span data-ttu-id="8a8ba-102">如何：安裝 Upgrade Advisor</span><span class="sxs-lookup"><span data-stu-id="8a8ba-102">How to: Install Upgrade Advisor</span></span>
  <span data-ttu-id="8a8ba-103">Upgrade Advisor 支援所有支援元件 ([!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 除外) 的遠端分析。</span><span class="sxs-lookup"><span data-stu-id="8a8ba-103">Upgrade Advisor supports remote analysis of all supported components except [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="8a8ba-104">如果您不要掃描 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 的執行個體，可以將 Upgrade Advisor 安裝在可連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體的任何電腦上。</span><span class="sxs-lookup"><span data-stu-id="8a8ba-104">If you are not scanning instances of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], you can install Upgrade Advisor on any computer that can connect to your instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="8a8ba-105">電腦也必須符合 Upgrade Advisor 必要條件。</span><span class="sxs-lookup"><span data-stu-id="8a8ba-105">The computer must also meet Upgrade Advisor prerequisites.</span></span> <span data-ttu-id="8a8ba-106">如果您要掃描 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]的執行個體，則必須將 Upgrade Advisor 安裝在報表伺服器上。</span><span class="sxs-lookup"><span data-stu-id="8a8ba-106">If you are scanning instances of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], you must install Upgrade Advisor on the report server.</span></span>  
  
 <span data-ttu-id="8a8ba-107">如需詳細資訊，請參閱[安裝 Upgrade Advisor](../../../2014/sql-server/install/installing-upgrade-advisor.md)。</span><span class="sxs-lookup"><span data-stu-id="8a8ba-107">For more information, see [Installing Upgrade Advisor](../../../2014/sql-server/install/installing-upgrade-advisor.md).</span></span>  
  
### <a name="to-install-upgrade-advisor"></a><span data-ttu-id="8a8ba-108">安裝 Upgrade Advisor</span><span class="sxs-lookup"><span data-stu-id="8a8ba-108">To install Upgrade Advisor</span></span>  
  
1.  <span data-ttu-id="8a8ba-109">您可以使用下列其中一種方法來啟動安裝程序：</span><span class="sxs-lookup"><span data-stu-id="8a8ba-109">Start the installation using one of the following methods:</span></span>  
  
    -   <span data-ttu-id="8a8ba-110">如果您是從網站安裝 [!INCLUDE[msCoName](../../includes/msconame-md.md)] ，請按一下 [**下載**] 連結，然後按一下 [**執行**] 按鈕以開始安裝。</span><span class="sxs-lookup"><span data-stu-id="8a8ba-110">If you are installing from the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Web site, click the **Download** link and then click the **Run** button to start the installation.</span></span>  
  
    -   <span data-ttu-id="8a8ba-111">如果您是從產品媒體進行安裝，請開啟 **[可**轉散發套件] 資料夾，開啟**Upgrade Advisor**資料夾，然後按兩下 [ **SQLUA.msi**]。</span><span class="sxs-lookup"><span data-stu-id="8a8ba-111">If you are installing from the product media, open the **redist** folder, open the **Upgrade Advisor** folder, and then double-click **SQLUA.msi**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="8a8ba-112">Upgrade Advisor 需要 [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework 4。</span><span class="sxs-lookup"><span data-stu-id="8a8ba-112">Upgrade Advisor requires the [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework 4.</span></span> <span data-ttu-id="8a8ba-113">如果您沒有安裝此元件，或者擁有發行前版本，系統就會顯示錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="8a8ba-113">If it is not installed, or if you have a pre-release version, an error message will appear.</span></span> <span data-ttu-id="8a8ba-114">請解除安裝任何舊版 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]，然後安裝最新版 .NET Framework 4。</span><span class="sxs-lookup"><span data-stu-id="8a8ba-114">Uninstall any earlier version of the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] and then install the latest version of .NET Framework 4.</span></span>  
    >   
    >  <span data-ttu-id="8a8ba-115">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] ScriptDom 是安裝 upgrade advisor 的必要條件 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ，而且不是由 Upgrade advisor 安裝程式所安裝。</span><span class="sxs-lookup"><span data-stu-id="8a8ba-115">The [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[tsql](../../includes/tsql-md.md)] ScriptDom is a prerequisite for installing [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Upgrade Advisor, and is not installed by Upgrade Advisor Setup.</span></span> <span data-ttu-id="8a8ba-116">安裝程式會要求您 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] 從 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 功能套件下載並安裝 ScriptDom。</span><span class="sxs-lookup"><span data-stu-id="8a8ba-116">The Setup requires you to download and install the [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[tsql](../../includes/tsql-md.md)] ScriptDom from the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Feature Pack.</span></span>  
  
2.  <span data-ttu-id="8a8ba-117">在 [**歡迎使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Upgrade Advisor 安裝程式**] 頁面上，按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="8a8ba-117">On the **Welcome to the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Upgrade Advisor Setup** page, click **Next**.</span></span>  
  
3.  <span data-ttu-id="8a8ba-118">在 [**授權合約**] 頁面上，閱讀授權合約。</span><span class="sxs-lookup"><span data-stu-id="8a8ba-118">On the **License Agreement** page, read the license agreement.</span></span> <span data-ttu-id="8a8ba-119">如果您同意，請選取 **[我接受授權合約**]，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="8a8ba-119">If you agree, select **I accept the license agreement** and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="8a8ba-120">在 [**註冊資訊**] 頁面上，輸入您的姓名和公司。</span><span class="sxs-lookup"><span data-stu-id="8a8ba-120">On the **Registration Information** page, enter your name and company.</span></span>  
  
5.  <span data-ttu-id="8a8ba-121">在 [**特徵選取**] 頁面上，檢查 [**安裝路徑**] 值。</span><span class="sxs-lookup"><span data-stu-id="8a8ba-121">On the **Feature Selection** page, review the **Installation path** value.</span></span> <span data-ttu-id="8a8ba-122">如有需要，請使用 [**流覽]** 按鈕來變更位置。</span><span class="sxs-lookup"><span data-stu-id="8a8ba-122">If necessary, use the **Browse** button to change the location.</span></span> <span data-ttu-id="8a8ba-123">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="8a8ba-123">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="8a8ba-124">在 [**準備安裝程式**] 頁面上，按一下 [**安裝**] 以安裝 Upgrade Advisor。</span><span class="sxs-lookup"><span data-stu-id="8a8ba-124">On the **Ready to Install the Program** page, click **Install** to install Upgrade Advisor.</span></span>  
  
7.  <span data-ttu-id="8a8ba-125">按一下 [完成]\*\*\*\* 結束精靈。</span><span class="sxs-lookup"><span data-stu-id="8a8ba-125">Click **Finish** to exit the wizard.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a8ba-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8a8ba-126">See Also</span></span>  
 [<span data-ttu-id="8a8ba-127">升級建議程式必要條件</span><span class="sxs-lookup"><span data-stu-id="8a8ba-127">Upgrade Advisor Prerequisites</span></span>](../../../2014/sql-server/install/upgrade-advisor-prerequisites.md)  
  
  
