---
title: Reporting Services WMI 提供者程式庫參考 (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- Reporting Services WMI Provider Library
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- WMI provider [Reporting Services], library
ms.assetid: 17ba711d-7eff-4423-9168-63dc425a3428
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2a98ca22f9d34627e484a698dcf540b31808d07e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594892"
---
# <a name="reporting-services-wmi-provider-library-reference-ssrs"></a><span data-ttu-id="e0599-102">Reporting Services WMI 提供者程式庫參考 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="e0599-102">Reporting Services WMI Provider Library Reference (SSRS)</span></span>
  <span data-ttu-id="e0599-103">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Windows Management Instrumentation (WMI) 提供者支援 WMI 作業，可讓您寫入指令碼和程式碼，以便修改報表伺服器和報表管理員的設定。</span><span class="sxs-lookup"><span data-stu-id="e0599-103">The [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Windows Management Instrumentation (WMI) provider supports WMI operations that enable you to write scripts and code to modify settings of the report server and Report Manager.</span></span>  
  
 <span data-ttu-id="e0599-104">例如，如果您想要變更報表伺服器連接至報表伺服器資料庫時是否使用整合式安全性的設定，請建立 MSReportServer_ConfigurationSetting 類別的執行個體，然後使用報表伺服器執行個體的 DatabaseIntegratedSecurity 屬性。</span><span class="sxs-lookup"><span data-stu-id="e0599-104">For example, if you want to change whether integrated security is used when the report server connects to the report server database, create an instance of the MSReportServer_ConfigurationSetting class and use the DatabaseIntegratedSecurity property of the of the report server instance.</span></span> <span data-ttu-id="e0599-105">下表所列出的類別代表 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 元件。</span><span class="sxs-lookup"><span data-stu-id="e0599-105">The classes shown in the following table represent [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] components.</span></span> <span data-ttu-id="e0599-106">這些類別定義於 [!INCLUDE[ssRSWMInmspc](../../includes/ssrswminmspc-md.md)] 或 [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)] 命名空間中。</span><span class="sxs-lookup"><span data-stu-id="e0599-106">The classes are defined in either the [!INCLUDE[ssRSWMInmspc](../../includes/ssrswminmspc-md.md)] or the [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)] namespaces.</span></span> <span data-ttu-id="e0599-107">其中每個類別都支援讀取和寫入作業。</span><span class="sxs-lookup"><span data-stu-id="e0599-107">Each of the classes support read and write operations.</span></span> <span data-ttu-id="e0599-108">但是，不支援建立作業。</span><span class="sxs-lookup"><span data-stu-id="e0599-108">Create operations are not supported.</span></span>  
  
## <a name="classes"></a><span data-ttu-id="e0599-109">類別</span><span class="sxs-lookup"><span data-stu-id="e0599-109">Classes</span></span>  
 [<span data-ttu-id="e0599-110">MSReportServer_Instance 類別</span><span class="sxs-lookup"><span data-stu-id="e0599-110">MSReportServer_Instance Class</span></span>](msreportserver-instance-class.md)  
 <span data-ttu-id="e0599-111">提供用戶端連接至已安裝之報表伺服器所需的基本資訊。</span><span class="sxs-lookup"><span data-stu-id="e0599-111">Provides basic information required for a client to connect to an installed report server.</span></span>  
  
 [<span data-ttu-id="e0599-112">MSReportServer_ConfigurationSetting 類別</span><span class="sxs-lookup"><span data-stu-id="e0599-112">MSReportServer_ConfigurationSetting Class</span></span>](msreportserver-configurationsetting-class.md)  
 <span data-ttu-id="e0599-113">代表報表伺服器執行個體的安裝與執行階段參數。</span><span class="sxs-lookup"><span data-stu-id="e0599-113">Represents the installation and run-time parameters of a report server instance.</span></span> <span data-ttu-id="e0599-114">這些參數是儲存在報表伺服器的組態檔中。</span><span class="sxs-lookup"><span data-stu-id="e0599-114">These parameters are stored in the configuration file for the report server.</span></span>  
  
 <span data-ttu-id="e0599-115">如需 WMI 作業的詳細資訊，請參閱 SDK 隨附的 WMI SDK 檔 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="e0599-115">For more information about WMI operations, see the WMI SDK documentation included with the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0599-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e0599-116">See Also</span></span>  
 <span data-ttu-id="e0599-117">[存取 Reporting Services WMI 提供者](../tools/access-the-reporting-services-wmi-provider.md) </span><span class="sxs-lookup"><span data-stu-id="e0599-117">[Access the Reporting Services WMI Provider](../tools/access-the-reporting-services-wmi-provider.md) </span></span>  
 [<span data-ttu-id="e0599-118">技術參考 &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="e0599-118">Technical Reference &#40;SSRS&#41;</span></span>](../technical-reference-ssrs.md)  
  
  
