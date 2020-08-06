---
title: RSWindowsExtendedProtectionScenario 屬性 (WMI MSReportServer_ConfigurationSetting) |Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 5ac7ab80-9adf-4f65-abfa-fedf53b082b5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 84e14d056cc0352b0d1d85bc12c9c873a1b89ced
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703746"
---
# <a name="rswindowsextendedprotectionscenario-property-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="1df39-102">RSWindowsExtendedProtectionScenario 屬性 (WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="1df39-102">RSWindowsExtendedProtectionScenario Property (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="1df39-103">傳回字串值，表示報表伺服器設定為允許的擴充保護案例。</span><span class="sxs-lookup"><span data-stu-id="1df39-103">Returns a string value that indicates the extended protection scenario the report server is configured to allow.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1df39-104">語法</span><span class="sxs-lookup"><span data-stu-id="1df39-104">Syntax</span></span>  
  
```vb  
Public Dim RSWindowsExtendedProtectionScenario As String  
```  
  
```csharp  
public string RSWindowsExtendedProtectionScenario;  
```  
  
## <a name="remarks"></a><span data-ttu-id="1df39-105">備註</span><span class="sxs-lookup"><span data-stu-id="1df39-105">Remarks</span></span>  
 <span data-ttu-id="1df39-106">傳回字串值，表示報表伺服器設定為允許的擴充保護案例。</span><span class="sxs-lookup"><span data-stu-id="1df39-106">Returns a string value that indicates the extended protection scenario the report server is configured to allow.</span></span> <span data-ttu-id="1df39-107">如果 WMI 提供者連線的報表伺服器不支援擴充保護，則會傳回 "" (空字串)。</span><span class="sxs-lookup"><span data-stu-id="1df39-107">If the report server that the WMI provider is connected to does not support extended protection, "" (empty string) is returned.</span></span>  
  
 <span data-ttu-id="1df39-108">下列清單顯示有效值：</span><span class="sxs-lookup"><span data-stu-id="1df39-108">The following list shows valid values:</span></span>  
  
 `"Any | Proxy | Direct"`  
  
## <a name="example-code"></a><span data-ttu-id="1df39-109">範例程式碼</span><span class="sxs-lookup"><span data-stu-id="1df39-109">Example Code</span></span>  
 [<span data-ttu-id="1df39-110">MSReportServer_ConfigurationSetting 類別</span><span class="sxs-lookup"><span data-stu-id="1df39-110">MSReportServer_ConfigurationSetting Class</span></span>](msreportserver-configurationsetting-class.md)  
  
## <a name="see-also"></a><span data-ttu-id="1df39-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1df39-111">See Also</span></span>  
 <span data-ttu-id="1df39-112">[RSWindowsExtendedProtectionLevel 屬性 &#40;WMI MSReportServer_ConfigurationSetting&#41;](rswindowsextendedprotectionlevel-property.md) </span><span class="sxs-lookup"><span data-stu-id="1df39-112">[RSWindowsExtendedProtectionLevel Property &#40;WMI MSReportServer_ConfigurationSetting&#41;](rswindowsextendedprotectionlevel-property.md) </span></span>  
 <span data-ttu-id="1df39-113">[SetExtendedProtectionSettings 方法 &#40;WMI MSReportServer_ConfigurationSetting&#41;](configurationsetting-method-setextendedprotectionsettings.md) </span><span class="sxs-lookup"><span data-stu-id="1df39-113">[SetExtendedProtectionSettings Method &#40;WMI MSReportServer_ConfigurationSetting&#41;](configurationsetting-method-setextendedprotectionsettings.md) </span></span>  
 <span data-ttu-id="1df39-114">[Reporting Services 的驗證擴充保護](../security/extended-protection-for-authentication-with-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="1df39-114">[Extended Protection for Authentication with Reporting Services](../security/extended-protection-for-authentication-with-reporting-services.md) </span></span>  
 [<span data-ttu-id="1df39-115">RSReportServer 設定檔</span><span class="sxs-lookup"><span data-stu-id="1df39-115">RSReportServer Configuration File</span></span>](../report-server/rsreportserver-config-configuration-file.md)  
  
  
