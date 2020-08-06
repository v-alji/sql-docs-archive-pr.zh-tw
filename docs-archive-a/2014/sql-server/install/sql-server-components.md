---
title: SQL Server 元件 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Upgrade Advisor, components
- listing components to analyze
- Upgrade Advisor [SQL Server], components
- component analysis [Upgrade Advisor]
- finding components to analyze
- locating components to analyze
- detecting components to analyze
- server names [Upgrade Advisor]
- analyzing system [Upgrade Advisor], component list
- identifying components to analyze
ms.assetid: 539b9525-ce3f-4950-9146-5527a5a297ee
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 95fe39ce8e616b238cf7c70763e7cf1819341f16
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710141"
---
# <a name="sql-server-components"></a><span data-ttu-id="061d7-102">SQL Server 元件</span><span class="sxs-lookup"><span data-stu-id="061d7-102">SQL Server Components</span></span>
  <span data-ttu-id="061d7-103">您可以針對已 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 安裝、、或的本機或遠端電腦執行 Upgrade Advisor 分析 Wizard [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="061d7-103">You can run the Upgrade Advisor Analysis Wizard against a local or remote computer that has [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], or [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] installed.</span></span> <span data-ttu-id="061d7-104">升級前分析的第一個步驟是識別要分析的電腦和元件。</span><span class="sxs-lookup"><span data-stu-id="061d7-104">The first step in the pre-upgrade analysis is to identify the computer and components for analysis.</span></span>  
  
## <a name="options"></a><span data-ttu-id="061d7-105">選項</span><span class="sxs-lookup"><span data-stu-id="061d7-105">Options</span></span>  
 <span data-ttu-id="061d7-106">**電腦名稱**</span><span class="sxs-lookup"><span data-stu-id="061d7-106">**Computer name**</span></span>  
 <span data-ttu-id="061d7-107">指定要分析之電腦的名稱。</span><span class="sxs-lookup"><span data-stu-id="061d7-107">Specifies the name of the computer to analyze.</span></span> <span data-ttu-id="061d7-108">Upgrade Advisor 會在 [**伺服器名稱**] 方塊中填入本機電腦名稱稱。</span><span class="sxs-lookup"><span data-stu-id="061d7-108">Upgrade Advisor populates the **Server name** box with the local computer name.</span></span> <span data-ttu-id="061d7-109">您也可以使用 "." 和 "localhost" 來連接至本機電腦。</span><span class="sxs-lookup"><span data-stu-id="061d7-109">You can also use "." and "localhost" to connect to the local computer.</span></span>  
  
 <span data-ttu-id="061d7-110">若要分析不同的電腦，請使用下列指導方針：</span><span class="sxs-lookup"><span data-stu-id="061d7-110">To analyze a different computer, use the following guidelines:</span></span>  
  
-   <span data-ttu-id="061d7-111">若要掃描非叢集實例，請輸入電腦名稱稱。</span><span class="sxs-lookup"><span data-stu-id="061d7-111">To scan nonclustered instances, enter the computer name.</span></span>  
  
-   <span data-ttu-id="061d7-112">若要掃描叢集執行個體，請輸入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 容錯移轉叢集執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="061d7-112">To scan clustered instances, enter the name of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster instance.</span></span>  
  
-   <span data-ttu-id="061d7-113">若要掃描安裝在叢集節點上的非叢集元件，請輸入容錯移轉叢集節點的電腦名稱稱。</span><span class="sxs-lookup"><span data-stu-id="061d7-113">To scan nonclustered components that are installed on a node of a cluster, enter the computer name of the failover cluster node.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="061d7-114">請勿包含 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="061d7-114">Do not include the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance name.</span></span>  
  
 <span data-ttu-id="061d7-115">除了指定電腦名稱以外，您也可以指定 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="061d7-115">Instead of specifying the computer name, you can specify the IP address.</span></span>  
  
 <span data-ttu-id="061d7-116">若要掃描 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]，您必須指定本機電腦的名稱。</span><span class="sxs-lookup"><span data-stu-id="061d7-116">If scanning [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], you must specify the name of the local computer.</span></span> <span data-ttu-id="061d7-117">Upgrade Advisor 只會掃描本機報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="061d7-117">Upgrade Advisor scans local report servers only.</span></span>  
  
 <span data-ttu-id="061d7-118">**偵測**</span><span class="sxs-lookup"><span data-stu-id="061d7-118">**Detect**</span></span>  
 <span data-ttu-id="061d7-119">[偵測 **] 按鈕會**存取指定的電腦，並偵測要分析的元件：</span><span class="sxs-lookup"><span data-stu-id="061d7-119">The **Detect** button accesses the specified computer and detects components to analyze:</span></span>  
  
-   <span data-ttu-id="061d7-120">如果要分析遠端電腦上的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體，則必須在遠端電腦上啟用遠端登錄服務。</span><span class="sxs-lookup"><span data-stu-id="061d7-120">If you are analyzing a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance on a remote computer, you must enable the remote registry services on the remote computer.</span></span>  
  
-   <span data-ttu-id="061d7-121">如果在電腦的登錄中找到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]、[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 或 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 執行個體，就會偵測到 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="061d7-121">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is detected if an instance of [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], or [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] is found in the computer's registry.</span></span>  
  
-   <span data-ttu-id="061d7-122">如果在電腦的登錄中找到 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體，就會偵測出 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="061d7-122">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] is detected if an instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] is found in the computer's registry.</span></span>  
  
-   <span data-ttu-id="061d7-123">如果在電腦的登錄中找到 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]，就會偵測出 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="061d7-123">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] is detected if [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] is found in the computer's registry.</span></span> <span data-ttu-id="061d7-124">不過，Upgrade Advisor 只會掃描本機報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="061d7-124">However, Upgrade Advisor scans local report servers only.</span></span>  
  
 <span data-ttu-id="061d7-125">**元件**</span><span class="sxs-lookup"><span data-stu-id="061d7-125">**Components**</span></span>  
 <span data-ttu-id="061d7-126">選取要分析的元件。</span><span class="sxs-lookup"><span data-stu-id="061d7-126">Select the components to analyze.</span></span> <span data-ttu-id="061d7-127">您可以按一下 [偵測] 按鈕，以選取安裝在電腦**上的所有**元件。</span><span class="sxs-lookup"><span data-stu-id="061d7-127">You can click the **Detect** button to select all the components installed on the computer.</span></span> <span data-ttu-id="061d7-128">偵測出安裝在電腦上的元件旁將顯示一個核取記號。</span><span class="sxs-lookup"><span data-stu-id="061d7-128">A check mark will appear next to the components that are detected as installed on the computer.</span></span> <span data-ttu-id="061d7-129">您也可以選取或清除每個元件旁的核取方塊，藉以手動選取要分析的元件。</span><span class="sxs-lookup"><span data-stu-id="061d7-129">You can also manually select the components to analyze by selecting or clearing the check box next to each component.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="061d7-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="061d7-130">See Also</span></span>  
 <span data-ttu-id="061d7-131">[使用 Upgrade Advisor](../../../2014/sql-server/install/working-with-upgrade-advisor.md) </span><span class="sxs-lookup"><span data-stu-id="061d7-131">[Working with Upgrade Advisor](../../../2014/sql-server/install/working-with-upgrade-advisor.md) </span></span>  
 [<span data-ttu-id="061d7-132">Upgrade Advisor 使用者介面參考</span><span class="sxs-lookup"><span data-stu-id="061d7-132">Upgrade Advisor User Interface Reference</span></span>](../../../2014/sql-server/install/upgrade-advisor-user-interface-reference.md)  
  
  
