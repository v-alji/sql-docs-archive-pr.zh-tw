---
title: 搭配 WMI 提供者使用 WQL 和指令碼語言來進行設定管理 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
helpviewer_keywords:
- queries [WMI]
- scripts [WMI]
- query language [WMI]
- WMI Query Language [WMI]
- WQL [WMI]
- WMI Provider for Configuration Management, WQL
- WMI Provider for Configuration Management, scripts
ms.assetid: c1e64905-3c2b-4974-88f4-abf17cf7e289
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: d8c903cd0e993728865bce3371c349a2d0ba7485
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595842"
---
# <a name="using-wql-and-scripting-languages-with-the-wmi-provider-for-configuration-management"></a><span data-ttu-id="cecda-102">搭配組態管理的 WMI 提供者使用 WQL 與指令碼語言</span><span class="sxs-lookup"><span data-stu-id="cecda-102">Using WQL and Scripting Languages with the WMI Provider for Configuration Management</span></span>
  <span data-ttu-id="cecda-103">管理應用程式會以兩種方式，使用組態管理物件的 Windows Management Instrumentation (WMI) 提供者，存取 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務與網路設定：</span><span class="sxs-lookup"><span data-stu-id="cecda-103">Management applications access [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services and network settings using the Windows Management Instrumentation (WMI) Provider for Configuration Management objects in two ways:</span></span>  
  
-   <span data-ttu-id="cecda-104">使用 WQL 編輯器或查詢工具 (例如，WBEMTest.exe) 來查訊利用 Windows Management Instrumentation 語言 (WQL) 設定的物件。</span><span class="sxs-lookup"><span data-stu-id="cecda-104">Using a WQL editor or query tool, such as WBEMTest.exe to query the object set with the Windows Management Instrumentation Language (WQL).</span></span>  
  
-   <span data-ttu-id="cecda-105">使用指令碼語言，例如 VBScript。</span><span class="sxs-lookup"><span data-stu-id="cecda-105">Using a scripting language, such as VBScript.</span></span>  
  
 <span data-ttu-id="cecda-106">或者，可以使用 SMO 中的 WMI Managed 物件，以程式設計方式管理 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務與網路設定。</span><span class="sxs-lookup"><span data-stu-id="cecda-106">Alternatively, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services and network settings can be managed programmatically using the WMI managed objects in SMO.</span></span> <span data-ttu-id="cecda-107">如需 WMI 受管理物件程式設計的詳細資訊，請參閱[使用 Wmi 提供者管理服務和網路設定](../server-management-objects-smo/tasks/managing-services-and-network-settings-by-using-wmi-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="cecda-107">For more information about programming WMI managed objects, see [Managing Services and Network Settings by Using WMI Provider](../server-management-objects-smo/tasks/managing-services-and-network-settings-by-using-wmi-provider.md).</span></span>  
  
 <span data-ttu-id="cecda-108">組態管理的 WMI 提供者可以使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 組態管理員和 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Management Console 來進行存取。</span><span class="sxs-lookup"><span data-stu-id="cecda-108">The WMI provider for Configuration Management can be accessed by using the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager and [!INCLUDE[msCoName](../../includes/msconame-md.md)] Management Console.</span></span> <span data-ttu-id="cecda-109">如需從使用者介面存取 WMI 提供者的詳細資訊，請參閱[管理服務的如何主題 &#40;SQL Server 組態管理員&#41;](../../database-engine/managing-services-how-to-topics-sql-server-configuration-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="cecda-109">For more information about accessing the WMI provider from a user interface, see [Managing Services How-to Topics &#40;SQL Server Configuration Manager&#41;](../../database-engine/managing-services-how-to-topics-sql-server-configuration-manager.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cecda-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cecda-110">See Also</span></span>  
 <span data-ttu-id="cecda-111">[使用 WQL 存取設定管理的 WMI 提供者](access-wmi-provider-for-configuration-management-using-wql.md) </span><span class="sxs-lookup"><span data-stu-id="cecda-111">[Access WMI Provider for Configuration Management using WQL](access-wmi-provider-for-configuration-management-using-wql.md) </span></span>  
 [<span data-ttu-id="cecda-112">使用 VBScript 修改 SQL Server 服務進階屬性</span><span class="sxs-lookup"><span data-stu-id="cecda-112">Modify SQL Server Service Advanced Properties using VBScript</span></span>](access-wmi-provider-for-configuration-management-using-vbscript.md)  
  
  
