---
title: 在 Server Core 上安裝 SQL Server 2014 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: 1dd294cc-5b69-4d0c-9005-3e307b75678b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d2614c43bb763757db7db46b1c7a966221da96f7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688186"
---
# <a name="install-sql-server-2014-on-server-core"></a><span data-ttu-id="6cff3-102">在 Server Core 上安裝 SQL Server 2014</span><span class="sxs-lookup"><span data-stu-id="6cff3-102">Install SQL Server 2014 on Server Core</span></span>
  <span data-ttu-id="6cff3-103">您可以在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SP1 或 [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] 的 Server Core 安裝上安裝 [!INCLUDE[win8srv](../../includes/win8srv-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="6cff3-103">You can install [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on a Server Core installation of [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 or [!INCLUDE[win8srv](../../includes/win8srv-md.md)].</span></span> <span data-ttu-id="6cff3-104">本主題提供在 Server Core 上安裝 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 的安裝程式特定詳細資料。</span><span class="sxs-lookup"><span data-stu-id="6cff3-104">This topic provides setup-specific details for installing [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] on Server Core.</span></span>  
  
 <span data-ttu-id="6cff3-105">[!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] 或 [!INCLUDE[win8srv](../../includes/win8srv-md.md)] 作業系統的 Server Core 安裝選項提供執行特定伺服器角色的基本環境，</span><span class="sxs-lookup"><span data-stu-id="6cff3-105">The Server Core installation option for the [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] or [!INCLUDE[win8srv](../../includes/win8srv-md.md)] operating system provides a minimal environment for running specific server roles.</span></span> <span data-ttu-id="6cff3-106">可協助降低這些伺服器角色的維護和管理需求，以及減少其攻擊面。</span><span class="sxs-lookup"><span data-stu-id="6cff3-106">This helps to reduce maintenance and management requirements and the attack surface for those server roles.</span></span> <span data-ttu-id="6cff3-107">如需在上執行之 Server Core 的詳細資訊 [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] ，請參閱[server Core For Windows Server 2008 R2](https://go.microsoft.com/fwlink/?LinkId=202439) (https://go.microsoft.com/fwlink/?LinkId=202439) 。</span><span class="sxs-lookup"><span data-stu-id="6cff3-107">For more information on Server Core as implemented on [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)], see [Server Core for Windows Server 2008 R2](https://go.microsoft.com/fwlink/?LinkId=202439) (https://go.microsoft.com/fwlink/?LinkId=202439).</span></span> <span data-ttu-id="6cff3-108">如需在 [!INCLUDE[win8srv](../../includes/win8srv-md.md)] 上實作之 Server Core 的詳細資訊，請參閱 [Server Core for Windows Server 2012](https://msdn.microsoft.com/library/hh846323\(VS.85\).aspx) (https://msdn.microsoft.com/library/hh846323(VS.85).aspx) 。</span><span class="sxs-lookup"><span data-stu-id="6cff3-108">For more information on Server Core as implemented on [!INCLUDE[win8srv](../../includes/win8srv-md.md)], see [Server Core for Windows Server 2012](https://msdn.microsoft.com/library/hh846323\(VS.85\).aspx) (https://msdn.microsoft.com/library/hh846323(VS.85).aspx).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="6cff3-109">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="6cff3-109">Prerequisites</span></span>  
  
|<span data-ttu-id="6cff3-110">需求</span><span class="sxs-lookup"><span data-stu-id="6cff3-110">Requirement</span></span>|<span data-ttu-id="6cff3-111">安裝方式</span><span class="sxs-lookup"><span data-stu-id="6cff3-111">How to install</span></span>|  
|-----------------|--------------------|  
|[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] <span data-ttu-id="6cff3-112">2.0 SP2</span><span class="sxs-lookup"><span data-stu-id="6cff3-112">2.0 SP2</span></span>|<span data-ttu-id="6cff3-113">包含在 [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 和 [!INCLUDE[win8srv](../../includes/win8srv-md.md)]的 Server Core 安裝中。</span><span class="sxs-lookup"><span data-stu-id="6cff3-113">Included in Server Core installation of [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 and [!INCLUDE[win8srv](../../includes/win8srv-md.md)].</span></span> <span data-ttu-id="6cff3-114">如果未啟用，安裝程式預設會予以啟用。</span><span class="sxs-lookup"><span data-stu-id="6cff3-114">If it is not enabled, Setup enables it by default.</span></span><br /><br /> <span data-ttu-id="6cff3-115">2.0、3.0 和 3.5 無法在同一部電腦上並行執行。</span><span class="sxs-lookup"><span data-stu-id="6cff3-115">It is not possible to run versions 2.0, 3.0, and 3.5 side by side on a computer.</span></span> <span data-ttu-id="6cff3-116">當您安裝 .NET Framework 3.5 SP1 時，會自動取得 2.0 和 3.0 層。</span><span class="sxs-lookup"><span data-stu-id="6cff3-116">When you install the .NET Framework 3.5 SP1, you get the 2.0 and 3.0 layers automatically.</span></span>|  
|[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] <span data-ttu-id="6cff3-117">3.5 SP1 Full Profile</span><span class="sxs-lookup"><span data-stu-id="6cff3-117">3.5 SP1 Full Profile</span></span>|<span data-ttu-id="6cff3-118">包含在 [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 的 Server Core 安裝中。</span><span class="sxs-lookup"><span data-stu-id="6cff3-118">Included in Server Core installation of [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1.</span></span> <span data-ttu-id="6cff3-119">如果未啟用，安裝程式預設會予以啟用。</span><span class="sxs-lookup"><span data-stu-id="6cff3-119">If it is not enabled, Setup enables it by default.</span></span><br /><br /> <span data-ttu-id="6cff3-120">在 Windows 伺服器作業系統的電腦上，您必須先下載及安裝 .NET Framework 3.5 SP1，才能執行安裝程式以安裝相依於 .NET 3.5 SP1 的元件。</span><span class="sxs-lookup"><span data-stu-id="6cff3-120">On a computer with Windows server operating system you must download and install .NET Framework 3.5 SP1 before you run Setup, to install components dependent on .NET 3.5 SP1.</span></span><br /><br /> <span data-ttu-id="6cff3-121">如需有關如何在中取得和啟用 .NET Framework 3.5 的建議和指導的詳細資訊 [!INCLUDE[win8srv](../../includes/win8srv-md.md)] ，請參閱[Microsoft .NET Framework 3.5 部署考慮](https://msdn.microsoft.com/library/windows/hardware/hh975396) (https://msdn.microsoft.com/library/windows/hardware/hh975396) 。</span><span class="sxs-lookup"><span data-stu-id="6cff3-121">For more information about the recommendations and guidance on how to acquire and enable .NET Framework 3.5 in [!INCLUDE[win8srv](../../includes/win8srv-md.md)], see [Microsoft .NET Framework 3.5 Deployment Considerations](https://msdn.microsoft.com/library/windows/hardware/hh975396) (https://msdn.microsoft.com/library/windows/hardware/hh975396).</span></span>|  
|[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] <span data-ttu-id="6cff3-122">4 Server Core Profile</span><span class="sxs-lookup"><span data-stu-id="6cff3-122">4 Server Core Profile</span></span>|<span data-ttu-id="6cff3-123">若是 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 以外的所有 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]版本，安裝程式會將 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 4 Server Core Profile 安裝為必要元件。</span><span class="sxs-lookup"><span data-stu-id="6cff3-123">For all editions of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] except [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)], Setup installs the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 4 Server Core Profile as a prerequisite.</span></span><br /><br /> <span data-ttu-id="6cff3-124">若是 [!INCLUDE[ssExpressEd11](../../includes/ssexpressed11-md.md)] ，請 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 從[Microsoft .NET Framework 4 (獨立安裝 () 程式](https://www.microsoft.com/download/details.aspx?id=17718)下載 4 server core 設定檔 https://www.microsoft.com/download/details.aspx?id=17718) ，然後再繼續進行安裝程式。</span><span class="sxs-lookup"><span data-stu-id="6cff3-124">For [!INCLUDE[ssExpressEd11](../../includes/ssexpressed11-md.md)], download the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 4 Server Core Profile from [Microsoft .NET Framework 4 (Standalone Installer) for Server Core](https://www.microsoft.com/download/details.aspx?id=17718) (https://www.microsoft.com/download/details.aspx?id=17718), and install it before you proceed with the setup.</span></span>|  
|<span data-ttu-id="6cff3-125">Windows Installer 4.5</span><span class="sxs-lookup"><span data-stu-id="6cff3-125">Windows Installer 4.5</span></span>|<span data-ttu-id="6cff3-126">隨附於 [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 和 [!INCLUDE[win8srv](../../includes/win8srv-md.md)]的 Server Core 安裝。</span><span class="sxs-lookup"><span data-stu-id="6cff3-126">Shipped with Server Core installation of [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 and [!INCLUDE[win8srv](../../includes/win8srv-md.md)].</span></span>|  
|<span data-ttu-id="6cff3-127">Windows PowerShell 2.0</span><span class="sxs-lookup"><span data-stu-id="6cff3-127">Windows PowerShell 2.0</span></span>|<span data-ttu-id="6cff3-128">隨附於 [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 和 [!INCLUDE[win8srv](../../includes/win8srv-md.md)]的 Server Core 安裝。</span><span class="sxs-lookup"><span data-stu-id="6cff3-128">Shipped with Server Core installation of [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 and [!INCLUDE[win8srv](../../includes/win8srv-md.md)].</span></span>|  
  
##  <a name="supported-features"></a><a name="BK_SupportedFeatures"></a> <span data-ttu-id="6cff3-129">支援的功能</span><span class="sxs-lookup"><span data-stu-id="6cff3-129">Supported Features</span></span>  
 <span data-ttu-id="6cff3-130">您可以使用下表來尋找 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] SP1 和 [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] 的 Server Core 安裝上 [!INCLUDE[win8srv](../../includes/win8srv-md.md)]中支援的功能。</span><span class="sxs-lookup"><span data-stu-id="6cff3-130">Use the following table to find which features are supported in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] on a Server Core installation of [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 and [!INCLUDE[win8srv](../../includes/win8srv-md.md)].</span></span>  
  
|<span data-ttu-id="6cff3-131">功能</span><span class="sxs-lookup"><span data-stu-id="6cff3-131">Feature</span></span>|<span data-ttu-id="6cff3-132">支援</span><span class="sxs-lookup"><span data-stu-id="6cff3-132">Supported</span></span>|  
|-------------|---------------|  
|[!INCLUDE[ssDE](../../includes/ssde-md.md)] <span data-ttu-id="6cff3-133">服務</span><span class="sxs-lookup"><span data-stu-id="6cff3-133">Services</span></span>|<span data-ttu-id="6cff3-134">是</span><span class="sxs-lookup"><span data-stu-id="6cff3-134">Yes</span></span>|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="6cff3-135">複寫</span><span class="sxs-lookup"><span data-stu-id="6cff3-135">Replication</span></span>|<span data-ttu-id="6cff3-136">是</span><span class="sxs-lookup"><span data-stu-id="6cff3-136">Yes</span></span>|  
|<span data-ttu-id="6cff3-137">全文檢索搜尋</span><span class="sxs-lookup"><span data-stu-id="6cff3-137">Full Text Search</span></span>|<span data-ttu-id="6cff3-138">是</span><span class="sxs-lookup"><span data-stu-id="6cff3-138">Yes</span></span>|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]|<span data-ttu-id="6cff3-139">是</span><span class="sxs-lookup"><span data-stu-id="6cff3-139">Yes</span></span>|  
|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|<span data-ttu-id="6cff3-140">否</span><span class="sxs-lookup"><span data-stu-id="6cff3-140">No</span></span>|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="6cff3-141">Data Tools (SSDT)</span><span class="sxs-lookup"><span data-stu-id="6cff3-141">Data Tools (SSDT)</span></span>|<span data-ttu-id="6cff3-142">否</span><span class="sxs-lookup"><span data-stu-id="6cff3-142">No</span></span>|  
|<span data-ttu-id="6cff3-143">用戶端工具連接性</span><span class="sxs-lookup"><span data-stu-id="6cff3-143">Client Tools Connectivity</span></span>|<span data-ttu-id="6cff3-144">是</span><span class="sxs-lookup"><span data-stu-id="6cff3-144">Yes</span></span>|  
|<span data-ttu-id="6cff3-145">Integration Services 伺服器<sup>[1]</sup></span><span class="sxs-lookup"><span data-stu-id="6cff3-145">Integration Services Server<sup>[1]</sup></span></span>|<span data-ttu-id="6cff3-146">是</span><span class="sxs-lookup"><span data-stu-id="6cff3-146">Yes</span></span>|  
|<span data-ttu-id="6cff3-147">用戶端工具回溯相容性</span><span class="sxs-lookup"><span data-stu-id="6cff3-147">Client Tools Backward Compatibility</span></span>|<span data-ttu-id="6cff3-148">否</span><span class="sxs-lookup"><span data-stu-id="6cff3-148">No</span></span>|  
|<span data-ttu-id="6cff3-149">用戶端工具 SDK</span><span class="sxs-lookup"><span data-stu-id="6cff3-149">Client Tools SDK</span></span>|<span data-ttu-id="6cff3-150">否</span><span class="sxs-lookup"><span data-stu-id="6cff3-150">No</span></span>|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="6cff3-151">線上叢書</span><span class="sxs-lookup"><span data-stu-id="6cff3-151">Books Online</span></span>|<span data-ttu-id="6cff3-152">否</span><span class="sxs-lookup"><span data-stu-id="6cff3-152">No</span></span>|  
|<span data-ttu-id="6cff3-153">管理工具 - 基本</span><span class="sxs-lookup"><span data-stu-id="6cff3-153">Management Tools - Basic</span></span>|<span data-ttu-id="6cff3-154">僅限遠端<sup>[2]</sup></span><span class="sxs-lookup"><span data-stu-id="6cff3-154">Remote Only<sup>[2]</sup></span></span>|  
|<span data-ttu-id="6cff3-155">管理工具 - 完整</span><span class="sxs-lookup"><span data-stu-id="6cff3-155">Management Tools - Complete</span></span>|<span data-ttu-id="6cff3-156">僅限遠端<sup>[2]</sup></span><span class="sxs-lookup"><span data-stu-id="6cff3-156">Remote Only<sup>[2]</sup></span></span>|  
|<span data-ttu-id="6cff3-157">Distributed Replay Controller</span><span class="sxs-lookup"><span data-stu-id="6cff3-157">Distributed Replay Controller</span></span>|<span data-ttu-id="6cff3-158">否</span><span class="sxs-lookup"><span data-stu-id="6cff3-158">No</span></span>|  
|<span data-ttu-id="6cff3-159">Distributed Replay Client</span><span class="sxs-lookup"><span data-stu-id="6cff3-159">Distributed Replay Client</span></span>|<span data-ttu-id="6cff3-160">僅限遠端<sup>[2]</sup></span><span class="sxs-lookup"><span data-stu-id="6cff3-160">Remote Only<sup>[2]</sup></span></span>|  
|<span data-ttu-id="6cff3-161">SQL 用戶端連接性 SDK</span><span class="sxs-lookup"><span data-stu-id="6cff3-161">SQL Client Connectivity SDK</span></span>|<span data-ttu-id="6cff3-162">是</span><span class="sxs-lookup"><span data-stu-id="6cff3-162">Yes</span></span>|  
|<span data-ttu-id="6cff3-163">Microsoft Sync Framework</span><span class="sxs-lookup"><span data-stu-id="6cff3-163">Microsoft Sync Framework</span></span>|<span data-ttu-id="6cff3-164">是<sup>[3]</sup></span><span class="sxs-lookup"><span data-stu-id="6cff3-164">Yes<sup>[3]</sup></span></span>|  
|[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]|<span data-ttu-id="6cff3-165">否</span><span class="sxs-lookup"><span data-stu-id="6cff3-165">No</span></span>|  
|[!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)]|<span data-ttu-id="6cff3-166">否</span><span class="sxs-lookup"><span data-stu-id="6cff3-166">No</span></span>|  
  
 <span data-ttu-id="6cff3-167"><sup>[1]</sup>如需有關中新 Integration Services 伺服器及其功能的詳細資訊 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ，請參閱[INTEGRATION SERVICES &#40;SSIS&#41; Server](../../integration-services/catalog/integration-services-ssis-server-and-catalog.md)。</span><span class="sxs-lookup"><span data-stu-id="6cff3-167"><sup>[1]</sup>For more information about the new Integration Services Server and its features in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], see [Integration Services &#40;SSIS&#41; Server](../../integration-services/catalog/integration-services-ssis-server-and-catalog.md).</span></span>  
  
 <span data-ttu-id="6cff3-168"><sup>[2]</sup>不支援在 Server Core 上安裝這些功能。</span><span class="sxs-lookup"><span data-stu-id="6cff3-168"><sup>[2]</sup>Installation of these features on Server Core is not supported.</span></span> <span data-ttu-id="6cff3-169">這些元件可以安裝在與 [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] Server Core SP1 或 [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Server Core 不同的伺服器上，並連接至安裝在 Server Core 上的 [!INCLUDE[ssDE](../../includes/ssde-md.md)] Services。</span><span class="sxs-lookup"><span data-stu-id="6cff3-169">These components can be installed on a different server that is not [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] Server Core SP1 or [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Server Core, and connected to the [!INCLUDE[ssDE](../../includes/ssde-md.md)] services installed on Server Core.</span></span>  
  
 <span data-ttu-id="6cff3-170"><sup>[3]</sup>Microsoft Sync Framework 未包含在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 安裝套件中。</span><span class="sxs-lookup"><span data-stu-id="6cff3-170"><sup>[3]</sup>Microsoft Sync Framework is not included in the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] installation package.</span></span> <span data-ttu-id="6cff3-171">您可以從這個[Microsoft 下載中心](https://go.microsoft.com/fwlink/?LinkId=221788) (] 頁面下載適當的 Sync Framework 版本 https://go.microsoft.com/fwlink/?LinkId=221788) ，並將它安裝在執行 SP1 或之 Server Core 安裝的電腦上 [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] [!INCLUDE[win8srv](../../includes/win8srv-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="6cff3-171">You can download the appropriate version of Sync Framework from this [Microsoft Download Center](https://go.microsoft.com/fwlink/?LinkId=221788) (https://go.microsoft.com/fwlink/?LinkId=221788) page and install it on a computer that is running Server Core installation of [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 or [!INCLUDE[win8srv](../../includes/win8srv-md.md)].</span></span>  
  
## <a name="supported-scenario-matrix"></a><span data-ttu-id="6cff3-172">支援的案例矩陣</span><span class="sxs-lookup"><span data-stu-id="6cff3-172">Supported Scenario Matrix</span></span>  
 <span data-ttu-id="6cff3-173">下表顯示在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] SP1 和 [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] 的 Server Core 安裝上安裝 [!INCLUDE[win8srv](../../includes/win8srv-md.md)]的支援案例矩陣。</span><span class="sxs-lookup"><span data-stu-id="6cff3-173">The following table shows the supported scenario matrix for installing [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] on a Server Core installation of [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 and [!INCLUDE[win8srv](../../includes/win8srv-md.md)].</span></span>  
  
|||  
|-|-|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="6cff3-174">版本</span><span class="sxs-lookup"><span data-stu-id="6cff3-174">editions</span></span>|<span data-ttu-id="6cff3-175">所有 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 64 位版本<sup>[1]</sup></span><span class="sxs-lookup"><span data-stu-id="6cff3-175">All [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 64-bit editions<sup>[1]</sup></span></span>|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="6cff3-176">語言</span><span class="sxs-lookup"><span data-stu-id="6cff3-176">language</span></span>|<span data-ttu-id="6cff3-177">所有語言</span><span class="sxs-lookup"><span data-stu-id="6cff3-177">All languages</span></span>|  
|<span data-ttu-id="6cff3-178">作業系統語言/地區設定上的[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 語言 (組合)</span><span class="sxs-lookup"><span data-stu-id="6cff3-178">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] language on OS language/locale (combination)</span></span>|<span data-ttu-id="6cff3-179">JPN (日文) Windows 上的 ENG [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6cff3-179">ENG [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on JPN (Japanese) Windows</span></span><br /><br /> <span data-ttu-id="6cff3-180">GER (德文) Windows 上的 ENG [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6cff3-180">ENG [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on GER (German) Windows</span></span><br /><br /> <span data-ttu-id="6cff3-181">CHS (簡體中文) Windows 上的 ENG [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6cff3-181">ENG [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on CHS (Chinese-China) Windows</span></span><br /><br /> <span data-ttu-id="6cff3-182">ARA (阿拉伯文 (SA)) Windows 上的 ENG [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6cff3-182">ENG [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on ARA (Arabic (SA)) Windows</span></span><br /><br /> <span data-ttu-id="6cff3-183">THA (泰文) Windows 上的 ENG [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6cff3-183">ENG [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on THA (Thai) Windows</span></span><br /><br /> <span data-ttu-id="6cff3-184">TRK (土耳其文) Windows 上的 ENG [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6cff3-184">ENG [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on TRK (Turkish) Windows</span></span><br /><br /> <span data-ttu-id="6cff3-185">pt-PT (葡萄牙文 - 葡萄牙) Windows 上的 ENG [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6cff3-185">ENG [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on pt-PT (Portuguese Portugal) Windows</span></span><br /><br /> <span data-ttu-id="6cff3-186">ENG (英文) Windows 上的 ENG [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6cff3-186">ENG [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on ENG (English) Windows</span></span>|  
|<span data-ttu-id="6cff3-187">Windows 版本</span><span class="sxs-lookup"><span data-stu-id="6cff3-187">Windows edition</span></span>|[!INCLUDE[win8srv](../../includes/win8srv-md.md)] <span data-ttu-id="6cff3-188">64 位元 x64 Datacenter</span><span class="sxs-lookup"><span data-stu-id="6cff3-188">64-bit x64 Datacenter</span></span><br /><br /> [!INCLUDE[win8srv](../../includes/win8srv-md.md)] <span data-ttu-id="6cff3-189">64 位元 x64 Standard</span><span class="sxs-lookup"><span data-stu-id="6cff3-189">64-bit x64 Standard</span></span><br /><br /> [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] <span data-ttu-id="6cff3-190">SP1 64 位元 x64 Data Center Server Core</span><span class="sxs-lookup"><span data-stu-id="6cff3-190">SP1 64-bit x64 Data Center Server Core</span></span><br /><br /> [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] <span data-ttu-id="6cff3-191">SP1 64 位元 x64 Enterprise Server Core</span><span class="sxs-lookup"><span data-stu-id="6cff3-191">SP1 64-bit x64 Enterprise Server Core</span></span><br /><br /> [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] <span data-ttu-id="6cff3-192">SP1 64 位元 x64 Standard Server Core</span><span class="sxs-lookup"><span data-stu-id="6cff3-192">SP1 64-bit x64 Standard Server Core</span></span><br /><br /> [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] <span data-ttu-id="6cff3-193">SP1 64 位元 x64 Web Server Core</span><span class="sxs-lookup"><span data-stu-id="6cff3-193">SP1 64-bit x64 Web Server Core</span></span>|  
  
 <span data-ttu-id="6cff3-194"><sup>[1]</sup>[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]在 Server Core 上不支援安裝32位版本的版本。</span><span class="sxs-lookup"><span data-stu-id="6cff3-194"><sup>[1]</sup>Installing the 32-bit version of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] editions is not supported on Server Core.</span></span>  
  
## <a name="upgrading"></a><span data-ttu-id="6cff3-195">升級中</span><span class="sxs-lookup"><span data-stu-id="6cff3-195">Upgrading</span></span>  
 <span data-ttu-id="6cff3-196">在 Server Core 安裝中，可支援從 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 升級至 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="6cff3-196">On Server Core installations, upgrading from [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] to [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] is supported.</span></span>  
  
## <a name="installation"></a><span data-ttu-id="6cff3-197">安裝</span><span class="sxs-lookup"><span data-stu-id="6cff3-197">Installation</span></span>  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="6cff3-198">不支援在 Server Core 作業系統上使用 [安裝精靈] 進行安裝。</span><span class="sxs-lookup"><span data-stu-id="6cff3-198">does not support setup by using the installation wizard on the Server Core operating system.</span></span> <span data-ttu-id="6cff3-199">在 Server Core 上安裝時， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝程式支援使用 /Q 參數的完整無訊息模式或使用 /QS 參數的簡單無訊息模式。</span><span class="sxs-lookup"><span data-stu-id="6cff3-199">When installing on Server Core, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup supports full quiet mode by using the /Q parameter, or Quiet Simple mode by using the /QS parameter.</span></span> <span data-ttu-id="6cff3-200">如需詳細資訊，請參閱[從命令提示字元安裝 SQL Server 2014](install-sql-server-from-the-command-prompt.md)。</span><span class="sxs-lookup"><span data-stu-id="6cff3-200">For more information, see [Install SQL Server 2014 from the Command Prompt](install-sql-server-from-the-command-prompt.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="6cff3-201">在執行 [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] Server Core SP1 或 [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Server Core 的電腦上，無法將 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 與舊版 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 並行安裝。</span><span class="sxs-lookup"><span data-stu-id="6cff3-201">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] cannot be installed side-by-side with earlier versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on a computer that is running [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] Server Core SP1 or [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Server Core.</span></span>  
  
 <span data-ttu-id="6cff3-202">除非軟體的使用方式受到個別的合約 (例如 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 大量授權合約或與 ISV 或 OEM 簽訂的協力廠商合約) 所管制，否則不論安裝方法為何，您都必須確認以個人身分或代表實體接受軟體授權條款。</span><span class="sxs-lookup"><span data-stu-id="6cff3-202">Regardless of the installation method, you are required to confirm acceptance of the software license terms as an individual or on behalf of an entity, unless your use of the software is governed by a separate agreement such as a [!INCLUDE[msCoName](../../includes/msconame-md.md)] volume licensing agreement or a third-party agreement with an ISV or OEM.</span></span>  
  
 <span data-ttu-id="6cff3-203">這些授權條款會顯示在安裝程式使用者介面中，供您檢閱和接受。</span><span class="sxs-lookup"><span data-stu-id="6cff3-203">The license terms are displayed for review and acceptance in the Setup user interface.</span></span> <span data-ttu-id="6cff3-204">自動安裝 (使用 /Q 或 /QS 參數) 必須包括 /IACCEPTSQLSERVERLICENSETERMS 參數。</span><span class="sxs-lookup"><span data-stu-id="6cff3-204">Unattended installations (using the /Q or /QS parameters) must include the /IACCEPTSQLSERVERLICENSETERMS parameter.</span></span> <span data-ttu-id="6cff3-205">您可以另外在 [Microsoft 軟體授權合約](https://go.microsoft.com/fwlink/?LinkId=148209)檢閱授權條款。</span><span class="sxs-lookup"><span data-stu-id="6cff3-205">You can review the license terms separately at [Microsoft Software License Terms](https://go.microsoft.com/fwlink/?LinkId=148209).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6cff3-206">根據您收到本軟體的方式 (例如，透過 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 大量授權)，軟體的使用方式可能會受到其他條款與條件的限制。</span><span class="sxs-lookup"><span data-stu-id="6cff3-206">Depending on how you received the software (for example, through [!INCLUDE[msCoName](../../includes/msconame-md.md)] volume licensing), your use of the software may be subject to additional terms and conditions.</span></span>  
  
 <span data-ttu-id="6cff3-207">若要安裝特定功能，請使用 /FEATURES 參數，然後指定父功能或功能值。</span><span class="sxs-lookup"><span data-stu-id="6cff3-207">To install specific features, use the /FEATURES parameter and specify the parent feature or feature values.</span></span> <span data-ttu-id="6cff3-208">如需有關功能參數及其用法的詳細資訊，請參閱下列章節。</span><span class="sxs-lookup"><span data-stu-id="6cff3-208">For more information about feature parameters and their use, see the following sections.</span></span>  
  
### <a name="feature-parameters"></a><span data-ttu-id="6cff3-209">功能參數</span><span class="sxs-lookup"><span data-stu-id="6cff3-209">Feature Parameters</span></span>  
  
|<span data-ttu-id="6cff3-210">功能參數</span><span class="sxs-lookup"><span data-stu-id="6cff3-210">Feature parameter</span></span>|<span data-ttu-id="6cff3-211">描述</span><span class="sxs-lookup"><span data-stu-id="6cff3-211">Description</span></span>|  
|-----------------------|-----------------|  
|<span data-ttu-id="6cff3-212">SQLENGINE</span><span class="sxs-lookup"><span data-stu-id="6cff3-212">SQLENGINE</span></span>|<span data-ttu-id="6cff3-213">只安裝 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="6cff3-213">Installs only the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>|  
|<span data-ttu-id="6cff3-214">複寫</span><span class="sxs-lookup"><span data-stu-id="6cff3-214">REPLICATION</span></span>|<span data-ttu-id="6cff3-215">安裝 [!INCLUDE[ssDE](../../includes/ssde-md.md)]時一併安裝複寫元件。</span><span class="sxs-lookup"><span data-stu-id="6cff3-215">Installs the Replication component along with [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>|  
|<span data-ttu-id="6cff3-216">FULLTEXT</span><span class="sxs-lookup"><span data-stu-id="6cff3-216">FULLTEXT</span></span>|<span data-ttu-id="6cff3-217">安裝 [!INCLUDE[ssDE](../../includes/ssde-md.md)]時一併安裝全文檢索元件。</span><span class="sxs-lookup"><span data-stu-id="6cff3-217">Installs the FullText component along with [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>|  
|<span data-ttu-id="6cff3-218">AS</span><span class="sxs-lookup"><span data-stu-id="6cff3-218">AS</span></span>|<span data-ttu-id="6cff3-219">安裝所有 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 元件。</span><span class="sxs-lookup"><span data-stu-id="6cff3-219">Installs all [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] components.</span></span>|  
|<span data-ttu-id="6cff3-220">IS</span><span class="sxs-lookup"><span data-stu-id="6cff3-220">IS</span></span>|<span data-ttu-id="6cff3-221">安裝所有 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 元件。</span><span class="sxs-lookup"><span data-stu-id="6cff3-221">Installs all [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] components.</span></span>|  
|<span data-ttu-id="6cff3-222">CONN</span><span class="sxs-lookup"><span data-stu-id="6cff3-222">CONN</span></span>|<span data-ttu-id="6cff3-223">安裝連接元件。</span><span class="sxs-lookup"><span data-stu-id="6cff3-223">Installs the connectivity components.</span></span>|  
  
 <span data-ttu-id="6cff3-224">請參閱下列功能參數用法的範例：</span><span class="sxs-lookup"><span data-stu-id="6cff3-224">See the following examples of the usage of feature parameters:</span></span>  
  
|<span data-ttu-id="6cff3-225">參數和值</span><span class="sxs-lookup"><span data-stu-id="6cff3-225">Parameter and values</span></span>|<span data-ttu-id="6cff3-226">描述</span><span class="sxs-lookup"><span data-stu-id="6cff3-226">Description</span></span>|  
|--------------------------|-----------------|  
|<span data-ttu-id="6cff3-227">/FEATURES=SQLEngine</span><span class="sxs-lookup"><span data-stu-id="6cff3-227">/FEATURES=SQLEngine</span></span>|<span data-ttu-id="6cff3-228">只安裝 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="6cff3-228">Installs only the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>|  
|<span data-ttu-id="6cff3-229">/FEATURES=SQLEngine,FullText</span><span class="sxs-lookup"><span data-stu-id="6cff3-229">/FEATURES=SQLEngine,FullText</span></span>|<span data-ttu-id="6cff3-230">安裝 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 和全文檢索。</span><span class="sxs-lookup"><span data-stu-id="6cff3-230">Installs the [!INCLUDE[ssDE](../../includes/ssde-md.md)] and full-text.</span></span>|  
|<span data-ttu-id="6cff3-231">/FEATURES=SQLEngine,Conn</span><span class="sxs-lookup"><span data-stu-id="6cff3-231">/FEATURES=SQLEngine,Conn</span></span>|<span data-ttu-id="6cff3-232">安裝 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 和連接元件。</span><span class="sxs-lookup"><span data-stu-id="6cff3-232">Installs the [!INCLUDE[ssDE](../../includes/ssde-md.md)] and the connectivity components.</span></span>|  
|<span data-ttu-id="6cff3-233">/FEATURES=SQLEngine,AS,IS,Conn</span><span class="sxs-lookup"><span data-stu-id="6cff3-233">/FEATURES=SQLEngine,AS,IS,Conn</span></span>|<span data-ttu-id="6cff3-234">安裝 [!INCLUDE[ssDE](../../includes/ssde-md.md)]、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]及連接元件。</span><span class="sxs-lookup"><span data-stu-id="6cff3-234">Installs the [!INCLUDE[ssDE](../../includes/ssde-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], and the connectivity components.</span></span>|  
  
### <a name="installation-options"></a><span data-ttu-id="6cff3-235">安裝選項</span><span class="sxs-lookup"><span data-stu-id="6cff3-235">Installation Options</span></span>  
 <span data-ttu-id="6cff3-236">在 Server Core 作業系統上安裝 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 時，安裝程式支援下列安裝選項：</span><span class="sxs-lookup"><span data-stu-id="6cff3-236">The Setup supports the following installation options while installing [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] on a Server Core operating system:</span></span>  
  
1.  <span data-ttu-id="6cff3-237">**從命令列安裝**</span><span class="sxs-lookup"><span data-stu-id="6cff3-237">**Installation from Command Line**</span></span>  
  
     <span data-ttu-id="6cff3-238">若要使用命令提示字元安裝選項安裝特定功能，請使用 /FEATURES 參數，然後指定父功能或功能值。</span><span class="sxs-lookup"><span data-stu-id="6cff3-238">To install specific features using the command prompt installation option, use the /FEATURES parameter and specify the parent feature or feature values.</span></span> <span data-ttu-id="6cff3-239">下面是有關從命令列使用參數的範例：</span><span class="sxs-lookup"><span data-stu-id="6cff3-239">The following is an example of using the parameters from the command line:</span></span>  
  
    ```cmd
    setup.exe /qs /ACTION=Install /FEATURES=SQLEngine,Replication /INSTANCENAME=MSSQLSERVER /SQLSVCACCOUNT="<DomainName\UserName>" /SQLSVCPASSWORD="<StrongPassword>" /SQLSYSADMINACCOUNTS="<DomainName\UserName>" /AGTSVCACCOUNT="NT AUTHORITY\Network Service" /TCPENABLED=1 /IACCEPTSQLSERVERLICENSETERMS  
    ```  
  
2.  <span data-ttu-id="6cff3-240">**使用組態檔安裝**</span><span class="sxs-lookup"><span data-stu-id="6cff3-240">**Installation using Configuration File**</span></span>  
  
     <span data-ttu-id="6cff3-241">安裝程式僅支援透過命令提示字元使用組態檔。</span><span class="sxs-lookup"><span data-stu-id="6cff3-241">Setup supports the use of the configuration file only through the command prompt.</span></span> <span data-ttu-id="6cff3-242">組態檔是包含參數 (名稱/值組) 和描述性註解基本結構的文字檔。</span><span class="sxs-lookup"><span data-stu-id="6cff3-242">The configuration file is a text file with the basic structure of a parameter (name/value pair) and a descriptive comment.</span></span> <span data-ttu-id="6cff3-243">在命令提示字元指定的組態檔副檔名應該是 .INI。</span><span class="sxs-lookup"><span data-stu-id="6cff3-243">The configuration file specified at the command prompt should have an .INI file name extension.</span></span> <span data-ttu-id="6cff3-244">請參閱下列 ConfigurationFile.INI 的範例：</span><span class="sxs-lookup"><span data-stu-id="6cff3-244">See the following examples of ConfigurationFile.INI:</span></span>  
  
    -   <span data-ttu-id="6cff3-245">安裝 [!INCLUDE[ssDE](../../includes/ssde-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6cff3-245">Installing [!INCLUDE[ssDE](../../includes/ssde-md.md)]</span></span>  
  
         <span data-ttu-id="6cff3-246">下列範例示範如何安裝包含 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssDE](../../includes/ssde-md.md)]的新獨立執行個體：</span><span class="sxs-lookup"><span data-stu-id="6cff3-246">The following example shows how to install a new stand-alone instance that includes the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssDE](../../includes/ssde-md.md)]:</span></span>  
  
        ```  
        ; ssNoVersion Configuration File  
        [OPTIONS]  
  
        ; Specifies a Setup work flow, like INSTALL, UNINSTALL, or UPGRADE. This is a required parameter.   
  
        ACTION="Install"  
  
        ; Specifies features to install, uninstall, or upgrade. The lists of features include SQLEngine, FullText, Replication, AS, IS, and Conn.   
  
        FEATURES=SQLENGINE  
  
        ; Specify a default or named instance. MSSQLSERVER is the default instance for non-Express editions and SQLExpress for Express editions. This parameter is required when installing the ssNoVersion Database Engine, and Analysis Services (AS).  
  
        INSTANCENAME="MSSQLSERVER"  
  
        ; Specify the Instance ID for the ssNoVersion features you have specified. ssNoVersion directory structure, registry structure, and service names will incorporate the instance ID of the ssNoVersion instance.   
  
        INSTANCEID="MSSQLSERVER"  
  
        ; Account for ssNoVersion service: Domain\User or system account.   
  
        SQLSVCACCOUNT="NT Service\MSSQLSERVER"  
  
        ; Windows account(s) to provision as ssNoVersion system administrators.   
  
        SQLSYSADMINACCOUNTS="<DomainName\UserName>"  
  
        ; Accept the License agreement to continue with Installation  
  
        IAcceptSQLServerLicenseTerms="True"
        ```  
  
    -   <span data-ttu-id="6cff3-247">安裝連接元件</span><span class="sxs-lookup"><span data-stu-id="6cff3-247">Installing connectivity components</span></span>  
  
         <span data-ttu-id="6cff3-248">下列範例示範如何安裝連接元件：</span><span class="sxs-lookup"><span data-stu-id="6cff3-248">The following example shows how to install the connectivity components:</span></span>  
  
        ```  
        ; ssNoVersion Configuration File  
        [OPTIONS]  
  
        ; Specifies a Setup work flow, like INSTALL, UNINSTALL, or UPGRADE. This is a required parameter.   
  
        ACTION="Install"  
  
        ; Specifies features to install, uninstall, or upgrade. The lists of features include SQLEngine, FullText, Replication, AS, IS, and Conn.   
  
        FEATURES=Conn  
  
        ; Specifies acceptance of License Terms  
  
        IAcceptSQLServerLicenseTerms="True
        ```  
  
    -   <span data-ttu-id="6cff3-249">安裝所有支援的功能</span><span class="sxs-lookup"><span data-stu-id="6cff3-249">Installing all supported features</span></span>  
  
         <span data-ttu-id="6cff3-250">下列範例示範如何在 Server Core 上安裝 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 支援的所有功能：</span><span class="sxs-lookup"><span data-stu-id="6cff3-250">The following example shows how to install all supported features of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] on Server Core:</span></span>  
  
        ```  
        ; ssNoVersion Configuration File  
        [OPTIONS]  
        ; Specifies a Setup work flow, like INSTALL, UNINSTALL, or UPGRADE. This is a required parameter.   
  
        ACTION="Install"  
  
        ; Specifies features to install, uninstall, or upgrade. The lists of features include SQLEngine, FullText, Replication, AS, IS, and Conn.   
  
        FEATURES=SQLENGINE,FullText,Replication,AS,IS,Conn  
  
        ; Specify a default or named instance. MSSQLSERVER is the default instance for non-Express editions and SQLExpress for Express editions. This parameter is required when installing the ssNoVersion Database Engine (SQL), or Analysis Services (AS).  
  
        INSTANCENAME="MSSQLSERVER"  
  
        ; Specify the Instance ID for the ssNoVersion features you have specified. ssNoVersion directory structure, registry structure, and service names will incorporate the instance ID of the ssNoVersion instance.   
  
        INSTANCEID="MSSQLSERVER"  
  
        ; Account for ssNoVersion service: Domain\User or system account.   
  
        SQLSVCACCOUNT="NT Service\MSSQLSERVER"  
  
        ; Windows account(s) to provision as ssNoVersion system administrators.   
  
        SQLSYSADMINACCOUNTS="<DomainName\UserName>"  
  
        ; The name of the account that the Analysis Services service runs under.   
  
        ASSVCACCOUNT= "NT Service\MSSQLServerOLAPService"  
  
        ; Specifies the list of administrator accounts that need to be provisioned.   
  
        ASSYSADMINACCOUNTS="<DomainName\UserName>"  
  
        ; Specifies the server mode of the Analysis Services instance. Valid values are MULTIDIMENSIONAL, POWERPIVOT or TABULAR. ASSERVERMODE is case-sensitive. All values must be expressed in upper case.   
  
        ASSERVERMODE="MULTIDIMENSIONAL"  
  
        ; Optional value, which specifies the state of the TCP protocol for the ssNoVersion service. Supported values are: 0 to disable the TCP protocol, and 1 to enable the TCP protocol.  
  
        TCPENABLED=1  
  
        ;Specifies acceptance of License Terms  
  
        IAcceptSQLServerLicenseTerms="True"  
        ```  
  
     <span data-ttu-id="6cff3-251">下列範例顯示如何使用組態檔啟動安裝程式。</span><span class="sxs-lookup"><span data-stu-id="6cff3-251">The following examples show how you can launch the Setup using a configuration file.</span></span>  
  
    -   <span data-ttu-id="6cff3-252">組態檔</span><span class="sxs-lookup"><span data-stu-id="6cff3-252">Configuration file</span></span>  
  
         <span data-ttu-id="6cff3-253">以下是有關如何使用組態檔的部分範例：</span><span class="sxs-lookup"><span data-stu-id="6cff3-253">Following are some examples of how to use the configuration file:</span></span>  
  
        -   <span data-ttu-id="6cff3-254">若要在命令提示字元中指定組態檔：</span><span class="sxs-lookup"><span data-stu-id="6cff3-254">To specify the configuration file at the command prompt:</span></span>  
  
        ```cmd
        setup.exe /QS /ConfigurationFile=MyConfigurationFile.INI  
        ```  
  
        -   <span data-ttu-id="6cff3-255">若要在命令提示字元而非組態檔中指定密碼：</span><span class="sxs-lookup"><span data-stu-id="6cff3-255">To specify passwords at the command prompt instead of in the configuration file:</span></span>  
  
        ```cmd
        setup.exe /QS /SQLSVCPASSWORD="************" /ASSVCPASSWORD="************"  /ConfigurationFile=MyConfigurationFile.INI  
        ```  
  
    -   <span data-ttu-id="6cff3-256">DefaultSetup.ini</span><span class="sxs-lookup"><span data-stu-id="6cff3-256">DefaultSetup.ini</span></span>  
  
         <span data-ttu-id="6cff3-257">如果您在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 來源媒體根層級的 \x86 和 \x64 資料夾中具有 DefaultSetup.ini 檔案，請開啟 DefaultSetup.ini 檔案，然後將 *Features* 參數加入檔案。</span><span class="sxs-lookup"><span data-stu-id="6cff3-257">If you have the DefaultSetup.ini file in the \x86 and \x64 folders at the root level of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] source media, open the DefaultSetup.ini file, and then add the *Features* parameter to the file.</span></span>  
  
         <span data-ttu-id="6cff3-258">如果 DefaultSetup.ini 檔案不存在，請建立檔案並將其複製到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 來源媒體根層級的 \x86 和 \x64 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="6cff3-258">If the DefaultSetup.ini file does not exist, you can create it and copy it to the \x86 and \x64 folders at the root level of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] source media.</span></span>  
  
## <a name="configuring-remote-access-of-ssnoversion-running-on-server-core"></a><span data-ttu-id="6cff3-259">設定在 Server Core 上執行之 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的遠端存取</span><span class="sxs-lookup"><span data-stu-id="6cff3-259">Configuring Remote Access of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Running on Server Core</span></span>  
 <span data-ttu-id="6cff3-260">執行下面描述的動作，以設定在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] SP1 或 [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] 的 Server Core 安裝上執行之 [!INCLUDE[win8srv](../../includes/win8srv-md.md)]執行個體的遠端存取。</span><span class="sxs-lookup"><span data-stu-id="6cff3-260">Perform the actions described below to configure remote access of a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] instance that is running on a Server Core installation of [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 or [!INCLUDE[win8srv](../../includes/win8srv-md.md)].</span></span>  
  
### <a name="enable-remote-connections-on-the-instance-of-ssnoversion"></a><span data-ttu-id="6cff3-261">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的執行個體上啟用遠端連接</span><span class="sxs-lookup"><span data-stu-id="6cff3-261">Enable remote connections on the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span></span>  
 <span data-ttu-id="6cff3-262">若要啟用遠端連接，請在本機使用 SQLCMD.exe，然後針對 Server Core 執行個體執行下列陳述式：</span><span class="sxs-lookup"><span data-stu-id="6cff3-262">To enable remote connections, use SQLCMD.exe locally and execute the following statements against the Server Core instance:</span></span>  
  
-   `EXEC sys.sp_configure N'remote access', N'1'`  
  
     `GO`  
  
-   `RECONFIGURE WITH OVERRIDE`  
  
     `GO`  
  
### <a name="enable-and-start-the-ssnoversion-browser-service"></a><span data-ttu-id="6cff3-263">啟用及啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser 服務</span><span class="sxs-lookup"><span data-stu-id="6cff3-263">Enable and start the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser service</span></span>  
 <span data-ttu-id="6cff3-264">根據預設，Browser 服務是停用的。</span><span class="sxs-lookup"><span data-stu-id="6cff3-264">By default, the Browser service is disabled.</span></span>  <span data-ttu-id="6cff3-265">如果在 Server Core 上執行的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體已停用此服務，請從命令提示字元執行下列命令，以啟用服務：</span><span class="sxs-lookup"><span data-stu-id="6cff3-265">If it is disabled on an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] running on Server Core, run the following command from the command prompt to enable it:</span></span>  
  
 `sc config SQLBROWSER start= auto`  
  
 <span data-ttu-id="6cff3-266">啟用後，請從命令提示字元執行下列命令，以啟動服務：</span><span class="sxs-lookup"><span data-stu-id="6cff3-266">After it is enabled, run the following command from the command prompt to start the service:</span></span>  
  
 `net start SQLBROWSER`  
  
### <a name="create-exceptions-in-windows-firewall"></a><span data-ttu-id="6cff3-267">在 Windows 防火牆中建立例外狀況</span><span class="sxs-lookup"><span data-stu-id="6cff3-267">Create exceptions in Windows Firewall</span></span>  
 <span data-ttu-id="6cff3-268">若要在 Windows 防火牆中建立 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 存取的例外狀況，請遵循 [設定 Windows 防火牆以允許 SQL Server 存取](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md)中指定的步驟。</span><span class="sxs-lookup"><span data-stu-id="6cff3-268">To create exceptions for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] access in Windows Firewall, follow the steps specified in [Configure the Windows Firewall to Allow SQL Server Access](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md).</span></span>  
  
### <a name="enable-tcpip-on-the-instance-of-ssnoversion"></a><span data-ttu-id="6cff3-269">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的執行個體上啟用 TCP/IP</span><span class="sxs-lookup"><span data-stu-id="6cff3-269">Enable TCP/IP on the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span></span>  
 <span data-ttu-id="6cff3-270">您可以針對 Server Core 上的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體，透過 Windows PowerShell 啟用 TCP/IP 通訊協定。</span><span class="sxs-lookup"><span data-stu-id="6cff3-270">The TCP/IP protocol can be enabled through Windows PowerShell for an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on Server Core.</span></span> <span data-ttu-id="6cff3-271">請遵循下列步驟：</span><span class="sxs-lookup"><span data-stu-id="6cff3-271">Follow these steps:</span></span>  
  
1.  <span data-ttu-id="6cff3-272">在執行 [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] Server Core SP1 或 [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Server Core 的電腦上，啟動 [工作管理員]。</span><span class="sxs-lookup"><span data-stu-id="6cff3-272">On the computer that is running [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] Server Core SP1 or [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Server Core, launch Task Manager.</span></span>  
  
2.  <span data-ttu-id="6cff3-273">在 [應用程式] 索引標籤上，按一下 [新工作]。</span><span class="sxs-lookup"><span data-stu-id="6cff3-273">On the **Applications** tab, click **New Task**.</span></span>  
  
3.  <span data-ttu-id="6cff3-274">在 [建立新工作] 對話方塊的 [開啟] 欄位中輸入 **sqlps.exe**，然後按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="6cff3-274">In the **Create New Task** dialog box, type **sqlps.exe** in the **Open** field and then click **OK**.</span></span> <span data-ttu-id="6cff3-275">這會開啟\*\* [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Powershell\*\*視窗。</span><span class="sxs-lookup"><span data-stu-id="6cff3-275">This opens the **[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Powershell** window.</span></span>  
  
4.  <span data-ttu-id="6cff3-276">在 [**Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Powershell**] 視窗中，執行下列指令碼以啟用 TCP/IP 通訊協定：</span><span class="sxs-lookup"><span data-stu-id="6cff3-276">In the **Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Powershell** window, run the following script to enable the TCP/IP protocol:</span></span>  
  
```powershell
$smo = 'Microsoft.SqlServer.Management.Smo.'  
$wmi = New-Object ($smo + 'Wmi.ManagedComputer')  
# Enable the TCP protocol on the default instance.  If the instance is named, replace MSSQLSERVER with the instance name in the following line.  
$uri = "ManagedComputer[@Name='" + (get-item env:\computername).Value + "']/ServerInstance[@Name='MSSQLSERVER']/ServerProtocol[@Name='Tcp']"  
$Tcp = $wmi.GetSmoObject($uri)  
$Tcp.IsEnabled = $true  
$Tcp.Alter()  
$Tcp  
```  
  
## <a name="uninstallation"></a><span data-ttu-id="6cff3-277">解除安裝</span><span class="sxs-lookup"><span data-stu-id="6cff3-277">Uninstallation</span></span>  
 <span data-ttu-id="6cff3-278">在登入執行 [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] Server Core SP1 或 [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Server Core 的電腦之後，即可透過系統管理員命令提示字元使用有限的桌面環境。</span><span class="sxs-lookup"><span data-stu-id="6cff3-278">After you log on to a computer that is running [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] Server Core SP1 or [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Server Core, you have a limited desktop environment with an Administrator command prompt.</span></span> <span data-ttu-id="6cff3-279">您可以使用此命令提示字元啟動 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]執行個體的解除安裝。</span><span class="sxs-lookup"><span data-stu-id="6cff3-279">You can use this command prompt to initiate uninstallation of an instance of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="6cff3-280">若要解除安裝 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]的執行個體，請在使用 /Q 參數的完整無訊息模式或使用 /QS 參數的簡單無訊息模式中，從命令提示字元啟動解除安裝。</span><span class="sxs-lookup"><span data-stu-id="6cff3-280">To uninstall an instance of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], launch the uninstallation from the command prompt in full quiet mode by using the /Q parameter, or quiet simple mode by using the /QS parameter.</span></span> <span data-ttu-id="6cff3-281">/QS 參數透過 UI 顯示進度，但是不接受任何輸入。</span><span class="sxs-lookup"><span data-stu-id="6cff3-281">The /QS parameter shows progress through the UI, but does not accept any input.</span></span> <span data-ttu-id="6cff3-282">/Q 會在不含任何使用者介面的無訊息模式中執行。</span><span class="sxs-lookup"><span data-stu-id="6cff3-282">/Q runs in a quiet mode without any user interface.</span></span>  
  
 <span data-ttu-id="6cff3-283">解除安裝現有的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體：</span><span class="sxs-lookup"><span data-stu-id="6cff3-283">To uninstall an existing instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
```cmd
setup.exe /Q /Action=Uninstall /FEATURES=SQLEngine,AS,IS /INSTANCENAME=MSSQLSERVER  
```  
  
 <span data-ttu-id="6cff3-284">若要移除具名執行個體，請在上述範例中指定執行個體的名稱，而非 "MSSQLSERVER"。</span><span class="sxs-lookup"><span data-stu-id="6cff3-284">To remove a named instance, specify the name of the instance instead of "MSSQLSERVER" in the preceding example.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="6cff3-285">如果您不小心關閉命令提示字元，您可以遵循下列步驟啟動新的命令提示字元：</span><span class="sxs-lookup"><span data-stu-id="6cff3-285">If you accidentally close the command prompt, you can start a new command prompt by following these steps:</span></span>  
> 
>  1.  <span data-ttu-id="6cff3-286">按 Ctrl+Shift+Esc 鍵顯示 [工作管理員]。</span><span class="sxs-lookup"><span data-stu-id="6cff3-286">Press Ctrl+Shift+Esc to display Task Manager.</span></span>  
> 2.  <span data-ttu-id="6cff3-287">在 [應用程式] 索引標籤上，按一下 [新工作]。</span><span class="sxs-lookup"><span data-stu-id="6cff3-287">On the **Applications** tab, click **New Task**.</span></span>  
> 3.  <span data-ttu-id="6cff3-288">在 [建立新工作] 對話方塊的 [開啟] 欄位中，輸入 **cmd**，然後[!INCLUDE[clickOK](../../includes/clickok-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="6cff3-288">In the **Create New Task** dialog box, type **cmd** in the **Open** field and then [!INCLUDE[clickOK](../../includes/clickok-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6cff3-289">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6cff3-289">See Also</span></span>  
 <span data-ttu-id="6cff3-290">[使用設定檔安裝 SQL Server 2014](install-sql-server-using-a-configuration-file.md) </span><span class="sxs-lookup"><span data-stu-id="6cff3-290">[Install SQL Server 2014 Using a Configuration File](install-sql-server-using-a-configuration-file.md) </span></span>  
 <span data-ttu-id="6cff3-291">[從命令提示字元安裝 SQL Server 2014](install-sql-server-from-the-command-prompt.md) </span><span class="sxs-lookup"><span data-stu-id="6cff3-291">[Install SQL Server 2014 from the Command Prompt](install-sql-server-from-the-command-prompt.md) </span></span>  
 <span data-ttu-id="6cff3-292">[SQL Server 2014 版本所支援的功能](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md) </span><span class="sxs-lookup"><span data-stu-id="6cff3-292">[Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md) </span></span>  
 <span data-ttu-id="6cff3-293">[Server Core 安裝選項消費者入門指南](https://go.microsoft.com/fwlink/?LinkId=221422) </span><span class="sxs-lookup"><span data-stu-id="6cff3-293">[Server Core Installation Option Getting Started Guide](https://go.microsoft.com/fwlink/?LinkId=221422) </span></span>  
 <span data-ttu-id="6cff3-294">[設定 Server Core 安裝：總覽](https://go.microsoft.com/fwlink/?LinkId=221423) </span><span class="sxs-lookup"><span data-stu-id="6cff3-294">[Configuring a Server Core installation: Overview](https://go.microsoft.com/fwlink/?LinkId=221423) </span></span>  
 <span data-ttu-id="6cff3-295">[Windows PowerShell 中由工作焦點列出的容錯移轉叢集 Cmdlet](https://go.microsoft.com/fwlink/?LinkId=221419) </span><span class="sxs-lookup"><span data-stu-id="6cff3-295">[Failover Cluster Cmdlets in Windows PowerShell Listed by Task Focus](https://go.microsoft.com/fwlink/?LinkId=221419) </span></span>  
 [<span data-ttu-id="6cff3-296">Mapping Cluster.exe Commands to Windows PowerShell Cmdlets for Failover Clusters (針對容錯移轉叢集將 Cluster.exe 命令對應到 Windows PowerShell Cmdlet)</span><span class="sxs-lookup"><span data-stu-id="6cff3-296">Mapping Cluster.exe Commands to Windows PowerShell Cmdlets for Failover Clusters</span></span>](https://go.microsoft.com/fwlink/?LinkId=221421)  
