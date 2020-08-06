---
title: 如何：執行 Upgrade Advisor 分析嚮導 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Upgrade Advisor Analysis Wizard
ms.assetid: d7d2a1e2-1179-4c05-9b0f-555b04dd1199
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 7c3e5e8a52c3b166b076aedb122e68f860037edf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606045"
---
# <a name="how-to-run-the-upgrade-advisor-analysis-wizard"></a><span data-ttu-id="14b9e-102">如何：執行 Upgrade Advisor 分析精靈</span><span class="sxs-lookup"><span data-stu-id="14b9e-102">How to: Run the Upgrade Advisor Analysis Wizard</span></span>
  <span data-ttu-id="14b9e-103">您可以從 Upgrade Advisor 開始頁面啟動 Upgrade Advisor 分析精靈。</span><span class="sxs-lookup"><span data-stu-id="14b9e-103">You start the Upgrade Advisor Analysis Wizard from the Upgrade Advisor start page.</span></span> <span data-ttu-id="14b9e-104">此主題描述如何執行 Upgrade Advisor 分析精靈。</span><span class="sxs-lookup"><span data-stu-id="14b9e-104">This topic describes how to run the Upgrade Advisor Analysis Wizard.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="14b9e-105">執行 Upgrade Advisor 分析精靈時，Upgrade Advisor 會將報表儲存在預設報表資料夾中。</span><span class="sxs-lookup"><span data-stu-id="14b9e-105">When you run the Upgrade Advisor Analysis Wizard, Upgrade Advisor saves the reports in the default report folder.</span></span> <span data-ttu-id="14b9e-106">但是，報表檢視器只顯示最近儲存的五個報表。</span><span class="sxs-lookup"><span data-stu-id="14b9e-106">However, the report viewer displays only the five latest saved reports.</span></span> <span data-ttu-id="14b9e-107">報表的預設位置是 [我的文件] [ \\ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 升級 advisor\110\reports。]</span><span class="sxs-lookup"><span data-stu-id="14b9e-107">The default location for the reports is My Documents\\[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Upgrade Advisor\110\Reports.</span></span>  
  
### <a name="to-run-the-upgrade-advisor-analysis-wizard"></a><span data-ttu-id="14b9e-108">若要執行 Upgrade Advisor 分析精靈</span><span class="sxs-lookup"><span data-stu-id="14b9e-108">To run the Upgrade Advisor Analysis Wizard</span></span>  
  
1.  <span data-ttu-id="14b9e-109">在 Upgrade Advisor 開始頁面上，按一下 [**啟動 Upgrade Advisor 分析嚮導]**。</span><span class="sxs-lookup"><span data-stu-id="14b9e-109">On the Upgrade Advisor start page, click **Launch Upgrade Advisor Analysis Wizard**.</span></span>  
  
2.  <span data-ttu-id="14b9e-110">在 [ \*\* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 元件**] 頁面上，于 [**伺服器名稱**] 方塊中輸入要掃描的伺服器名稱，然後**按一下 [\*\* 偵測]。</span><span class="sxs-lookup"><span data-stu-id="14b9e-110">On the **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Components** page, enter the name of the server to scan in the **Server name** box, and then click **Detect**.</span></span> <span data-ttu-id="14b9e-111">請按照下列伺服器名稱的指導方針進行：</span><span class="sxs-lookup"><span data-stu-id="14b9e-111">Use the following guidelines for the server name:</span></span>  
  
    -   <span data-ttu-id="14b9e-112">若要掃描非叢集實例，請輸入電腦名稱稱。</span><span class="sxs-lookup"><span data-stu-id="14b9e-112">To scan nonclustered instances, enter the computer name.</span></span>  
  
    -   <span data-ttu-id="14b9e-113">若要掃描叢集執行個體，請輸入虛擬 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 名稱。</span><span class="sxs-lookup"><span data-stu-id="14b9e-113">To scan clustered instances, enter the virtual [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] name.</span></span>  
  
    -   <span data-ttu-id="14b9e-114">若要掃描安裝在叢集節點上的非叢集元件，請輸入節點名稱。</span><span class="sxs-lookup"><span data-stu-id="14b9e-114">To scan nonclustered components that are installed on a node of a cluster, enter the node name.</span></span>  
  
    > [!WARNING]  
    >  <span data-ttu-id="14b9e-115">Upgrade Advisor 不支援連接到未設定為使用標準通訊埠 (1433) 進行用戶端連接的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="14b9e-115">Upgrade Advisor does not support connecting to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance that is not set to use the standard port (1433) for client connections.</span></span> <span data-ttu-id="14b9e-116">如果要連接到不使用標準通訊埠 (1433) 的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體，請使用 IP 位址和通訊埠建立別名。</span><span class="sxs-lookup"><span data-stu-id="14b9e-116">If you want to connect to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance that does not use the standard port (1433), create an alias using the IP address and the port.</span></span> <span data-ttu-id="14b9e-117">如需有關設定用戶端通訊協定及建立實例別名的詳細資訊 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，請參閱[設定用戶端通訊協定](../../database-engine/configure-windows/configure-client-protocols.md)。</span><span class="sxs-lookup"><span data-stu-id="14b9e-117">For more information about configuring client protocols and creating an alias for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instances, see [Configure Client Protocols](../../database-engine/configure-windows/configure-client-protocols.md).</span></span>  
    >   
    >  <span data-ttu-id="14b9e-118">如果您未在執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Upgrade Advisor 的電腦上安裝，請按一下 [**開始**]，然後執行 `cliconfg` 。</span><span class="sxs-lookup"><span data-stu-id="14b9e-118">If you do not have [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installed on the computer on which you are running Upgrade Advisor, click **Start**, and then run  `cliconfg`.</span></span> <span data-ttu-id="14b9e-119">這會開啟 [ \*\* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 用戶端網路公用程式\*\*] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="14b9e-119">This opens the **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client Network Utility** dialog box.</span></span> <span data-ttu-id="14b9e-120">使用 [**別名**] 索引標籤來建立別名。</span><span class="sxs-lookup"><span data-stu-id="14b9e-120">Use the **Alias** tab to create the alias.</span></span>  
  
3.  <span data-ttu-id="14b9e-121">查看偵測到的元件清單，視需要修改選取專案，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="14b9e-121">Review the list of components detected, modify the selections as necessary, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="14b9e-122">在 [**連接參數**] 頁面上，選取 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 您想要掃描的實例，選取驗證方法，並視需要輸入使用者名稱和密碼資訊，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="14b9e-122">On the **Connection Parameters** page, select the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] you want to scan, select the authentication method and, if necessary, enter user name and password information, and then click **Next**.</span></span>  
  
     <span data-ttu-id="14b9e-123">預設執行個體名稱是 MSSQLSERVER。</span><span class="sxs-lookup"><span data-stu-id="14b9e-123">The default instance name is MSSQLSERVER.</span></span>  
  
5.  <span data-ttu-id="14b9e-124">針對選取的元件，輸入要求的資訊。</span><span class="sxs-lookup"><span data-stu-id="14b9e-124">For selected components, enter the requested information.</span></span> <span data-ttu-id="14b9e-125">如需個別對話方塊的詳細資訊，請參閱[Upgrade Advisor 使用者介面參考](../../../2014/sql-server/install/upgrade-advisor-user-interface-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="14b9e-125">For more information about individual dialog boxes, see [Upgrade Advisor User Interface Reference](../../../2014/sql-server/install/upgrade-advisor-user-interface-reference.md).</span></span>  
  
6.  <span data-ttu-id="14b9e-126">在 [**確認 Upgrade Advisor 設定**] 頁面上，檢查您輸入的資訊。</span><span class="sxs-lookup"><span data-stu-id="14b9e-126">On the **Confirm Upgrade Advisor Setting** page, review the information that you entered.</span></span> <span data-ttu-id="14b9e-127">如果您想要提交升級報表，可以選取 [\*\*傳送報表給 [!INCLUDE[msCoName](../../includes/msconame-md.md)] \*\* ]。</span><span class="sxs-lookup"><span data-stu-id="14b9e-127">You can select **Send reports to [!INCLUDE[msCoName](../../includes/msconame-md.md)]** if you want to submit your upgrade report.</span></span> <span data-ttu-id="14b9e-128">您也可以檢閱隱私權原則。</span><span class="sxs-lookup"><span data-stu-id="14b9e-128">You can also review the privacy policy.</span></span>  
  
7.  <span data-ttu-id="14b9e-129">按一下 [**執行**] 來分析的實例 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="14b9e-129">Click **Run** to analyze the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
8.  <span data-ttu-id="14b9e-130">當分析完成時，請按一下 [**啟動報表**]，以查看偵測到的升級問題。</span><span class="sxs-lookup"><span data-stu-id="14b9e-130">When the analysis is finished, click **Launch Report** to view the detected upgrade issues.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14b9e-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="14b9e-131">See Also</span></span>  
 <span data-ttu-id="14b9e-132">[如何：啟動 Upgrade Advisor](../../../2014/sql-server/install/how-to-launch-upgrade-advisor.md) </span><span class="sxs-lookup"><span data-stu-id="14b9e-132">[How to: Launch Upgrade Advisor](../../../2014/sql-server/install/how-to-launch-upgrade-advisor.md) </span></span>  
 <span data-ttu-id="14b9e-133">[正在執行 Upgrade Advisor &#40;使用者介面&#41;](../../../2014/sql-server/install/running-upgrade-advisor-user-interface.md) </span><span class="sxs-lookup"><span data-stu-id="14b9e-133">[Running Upgrade Advisor &#40;User Interface&#41;](../../../2014/sql-server/install/running-upgrade-advisor-user-interface.md) </span></span>  
 [<span data-ttu-id="14b9e-134">使用升級建議程式</span><span class="sxs-lookup"><span data-stu-id="14b9e-134">Working with Upgrade Advisor</span></span>](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
