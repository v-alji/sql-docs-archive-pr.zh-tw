---
title: 設定管理概念的 WMI 提供者 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
helpviewer_keywords:
- WMI Provider for Configuration Management
- SQL Server WMI Provider
- configuration management [WMI]
- WMI Provider for Configuration Management, about WMI Provider for Configuration Management
ms.assetid: 7e41db24-b915-4eb8-a1d6-e6948ee915b7
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: be0682e7d6de5cb8c3d67a2f300bb89122213652
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593873"
---
# <a name="wmi-provider-for-configuration-management-concepts"></a><span data-ttu-id="828de-102">組態管理的 WMI 提供者概念</span><span class="sxs-lookup"><span data-stu-id="828de-102">WMI Provider for Configuration Management Concepts</span></span>
  <span data-ttu-id="828de-103">WMI 提供者是一種已發行的層，可搭配 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[msCoName](../../includes/msconame-md.md)] 管理主控台 (MMC) 和 Configuration Manager 的 Configuration Manager 嵌入式管理單元使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="828de-103">The WMI provider is a published layer that is used with the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager snap-in for [!INCLUDE[msCoName](../../includes/msconame-md.md)] Management Console (MMC) and the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager.</span></span> <span data-ttu-id="828de-104">它會提供統一的方式來協助您連結管理 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 組態管理員所要求之登錄作業的 API 呼叫，並在選取的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務上，提供增強的控制和操作功能。</span><span class="sxs-lookup"><span data-stu-id="828de-104">It provides a unified way for interfacing with the API calls that manage the registry operations requested by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager and provides enhanced control and manipulation over the selected [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services.</span></span>  
  
 <span data-ttu-id="828de-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] WMI 提供者是一個 DLL 和 MOF 檔案，會透過 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝程式自動編譯。</span><span class="sxs-lookup"><span data-stu-id="828de-105">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] WMI Provider is a DLL and a MOF file, which are compiled automatically by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup.</span></span>  
  
 <span data-ttu-id="828de-106">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] WMI 提供者包含一組物件類別，用於透過下列方法控制 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務：</span><span class="sxs-lookup"><span data-stu-id="828de-106">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] WMI Provider contains a set of object classes used to control the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services using the following methods:</span></span>  
  
-   <span data-ttu-id="828de-107">可在其中內嵌 Windows 查詢語言 (WQL) 的指令碼語言，例如，VBScript、[!INCLUDE[jsprjscript](../../includes/jsprjscript-md.md)] 或 Perl。</span><span class="sxs-lookup"><span data-stu-id="828de-107">A script language such as VBScript, [!INCLUDE[jsprjscript](../../includes/jsprjscript-md.md)], or Perl, in which Windows Query Language (WQL) can be embedded.</span></span>  
  
-   <span data-ttu-id="828de-108">SMO Managed 程式碼程式中的 <xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer> 物件。</span><span class="sxs-lookup"><span data-stu-id="828de-108">The <xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer> object in an SMO managed code program.</span></span>  
  
-   <span data-ttu-id="828de-109">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 組態管理員或包含 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] WMI 提供者嵌入式管理單元的 MMC。</span><span class="sxs-lookup"><span data-stu-id="828de-109">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager or MMC with the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] WMI provider snap-in.</span></span>  
  
## <a name="using-a-script-language"></a><span data-ttu-id="828de-110">使用指令碼語言</span><span class="sxs-lookup"><span data-stu-id="828de-110">Using a Script Language</span></span>  
 <span data-ttu-id="828de-111">使用指令碼語言的優點包括：</span><span class="sxs-lookup"><span data-stu-id="828de-111">The advantages of using a script language include the following:</span></span>  
  
-   <span data-ttu-id="828de-112">不需要開發環境。</span><span class="sxs-lookup"><span data-stu-id="828de-112">A development environment is not required.</span></span>  
  
-   <span data-ttu-id="828de-113">支援指令碼語言的檔案隨處可得。</span><span class="sxs-lookup"><span data-stu-id="828de-113">The files that support the script language are widely available.</span></span>  
  
 <span data-ttu-id="828de-114">除了 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] WMI 提供者之外，指令碼也可以使用其他 WMI 提供者。</span><span class="sxs-lookup"><span data-stu-id="828de-114">The script can also work with other WMI Providers in addition to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] WMI Provider.</span></span> <span data-ttu-id="828de-115">網域管理員可以使用指令碼，在網路內的多部電腦上設定服務、網路設定以及別名設定。</span><span class="sxs-lookup"><span data-stu-id="828de-115">A domain administrator can use a script to set up the services, network settings, and alias settings on multiple computers on a network.</span></span>  
  
 <span data-ttu-id="828de-116">本節以更詳細的方式處理從指令碼存取組態管理的 WMI 提供者。</span><span class="sxs-lookup"><span data-stu-id="828de-116">This section deals with accessing the WMI Provider for Configuration Management from scripts in further detail.</span></span>  
  
## <a name="using-the-smo-managedcomputer-object"></a><span data-ttu-id="828de-117">使用 SMO ManagedCompute 物件</span><span class="sxs-lookup"><span data-stu-id="828de-117">Using the SMO ManagedComputer Object</span></span>  
 <span data-ttu-id="828de-118"><xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer> 物件是一個 Managed SMO 物件，可存取組態管裡的 WMI 提供者。</span><span class="sxs-lookup"><span data-stu-id="828de-118">The <xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer> object is a managed SMO object that provides access to the WMI Provider for Configuration Management.</span></span> <span data-ttu-id="828de-119">透過使用 SMO 程式，<xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer> 物件可用於檢視與修改 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務、網路設定以及別名設定。</span><span class="sxs-lookup"><span data-stu-id="828de-119">By using an SMO program, the <xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer> object can be used to view and modify [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services, network settings, and alias settings.</span></span> <span data-ttu-id="828de-120">如需詳細資訊，請參閱[使用 WMI 提供者管理服務和網路設定](../server-management-objects-smo/tasks/managing-services-and-network-settings-by-using-wmi-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="828de-120">For more information, see [Managing Services and Network Settings by Using WMI Provider](../server-management-objects-smo/tasks/managing-services-and-network-settings-by-using-wmi-provider.md).</span></span>  
  
## <a name="using-the-microsoft-management-console-or-sql-server-configuration-manager"></a><span data-ttu-id="828de-121">使用 Microsoft Management Console 或 SQL Server 組態管理員</span><span class="sxs-lookup"><span data-stu-id="828de-121">Using the Microsoft Management Console or SQL Server Configuration Manager</span></span>  
 <span data-ttu-id="828de-122">Microsoft Management Console (MMC) 提供一個管理 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務 (而非指令碼語言或 Managed 程式碼程式) 的介面。</span><span class="sxs-lookup"><span data-stu-id="828de-122">Microsoft Management Console (MMC) provides an interface to manage [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services, as opposed to a scripting language or managed code program.</span></span> <span data-ttu-id="828de-123">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management MMC 嵌入式管理單元可用於停止和啟動服務，以及變更服務帳戶。</span><span class="sxs-lookup"><span data-stu-id="828de-123">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management MMC snap-in can be used to stop and start services, and to change service accounts.</span></span>  
  
 <span data-ttu-id="828de-124">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 組態管理員也可用於管理 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務、用戶端與伺服器通訊協定，以及伺服器別名</span><span class="sxs-lookup"><span data-stu-id="828de-124">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager can also be used to manage [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services, client and server protocols, and server aliases</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="828de-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="828de-125">See Also</span></span>  
 <span data-ttu-id="828de-126">[瞭解設定管理的 WMI 提供者](understanding-the-wmi-provider-for-configuration-management.md) </span><span class="sxs-lookup"><span data-stu-id="828de-126">[Understanding the WMI Provider for Configuration Management](understanding-the-wmi-provider-for-configuration-management.md) </span></span>  
 <span data-ttu-id="828de-127">[使用 WMI 提供者進行設定管理](working-with-the-wmi-provider-for-configuration-management.md) </span><span class="sxs-lookup"><span data-stu-id="828de-127">[Working with the WMI Provider for Configuration Management](working-with-the-wmi-provider-for-configuration-management.md) </span></span>  
 [<span data-ttu-id="828de-128">搭配組態管理的 WMI 提供者使用 WQL 與指令碼語言</span><span class="sxs-lookup"><span data-stu-id="828de-128">Using WQL and Scripting Languages with the WMI Provider for Configuration Management</span></span>](using-wql-and-scripting-languages-with-the-wmi-provider.md)  
  
  
