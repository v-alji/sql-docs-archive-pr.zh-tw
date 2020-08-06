---
title: RSWindowsExtendedProtectionLevel 屬性 (WMI MSReportServer_ConfigurationSetting) |Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 162ffe86-69c3-49d2-b9ed-49d097c05551
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 02ff3bad42ae25adf6cfa563944d89bac2c600e0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594895"
---
# <a name="rswindowsextendedprotectionlevel-property-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="6057d-102">RSWindowsExtendedProtectionLevel 屬性 (WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="6057d-102">RSWindowsExtendedProtectionLevel Property (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="6057d-103">傳回字串值，表示報表伺服器設定為支援的保護等級。</span><span class="sxs-lookup"><span data-stu-id="6057d-103">Returns a string value that indicates the level of protection the report server is configured to support.</span></span> <span data-ttu-id="6057d-104">這個屬性是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="6057d-104">This property is read-only.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6057d-105">語法</span><span class="sxs-lookup"><span data-stu-id="6057d-105">Syntax</span></span>  
  
```vb  
Public Dim RSWindowsExtendedProtectionLevel As String  
```  
  
```csharp  
public string RSWindowsExtendedProtectionLevel;  
```  
  
## <a name="remarks"></a><span data-ttu-id="6057d-106">備註</span><span class="sxs-lookup"><span data-stu-id="6057d-106">Remarks</span></span>  
 <span data-ttu-id="6057d-107">傳回字串值，表示報表伺服器設定為支援的保護等級。</span><span class="sxs-lookup"><span data-stu-id="6057d-107">Returns a string value that indicates the level of protection the report server is configured to support.</span></span> <span data-ttu-id="6057d-108">如果 WMI 提供者連線的報表伺服器不支援擴充保護，則會傳回 "" (空字串)。</span><span class="sxs-lookup"><span data-stu-id="6057d-108">If the report server that the WMI provider is connected to does not support extended protection, "" (empty string) is returned.</span></span> <span data-ttu-id="6057d-109">下列清單顯示有效值：</span><span class="sxs-lookup"><span data-stu-id="6057d-109">The following list shows valid values:</span></span>  
  
 `"Off" | "Allow" | "Require"`  
  
## <a name="example-code"></a><span data-ttu-id="6057d-110">範例程式碼</span><span class="sxs-lookup"><span data-stu-id="6057d-110">Example Code</span></span>  
 [<span data-ttu-id="6057d-111">MSReportServer_ConfigurationSetting 類別</span><span class="sxs-lookup"><span data-stu-id="6057d-111">MSReportServer_ConfigurationSetting Class</span></span>](msreportserver-configurationsetting-class.md)  
  
## <a name="see-also"></a><span data-ttu-id="6057d-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6057d-112">See Also</span></span>  
 <span data-ttu-id="6057d-113">[RSWindowsExtendedProtectionScenario 屬性 &#40;WMI MSReportServer_ConfigurationSetting&#41;](rswindowsextendedprotectionscenario-property.md) </span><span class="sxs-lookup"><span data-stu-id="6057d-113">[RSWindowsExtendedProtectionScenario Property &#40;WMI MSReportServer_ConfigurationSetting&#41;](rswindowsextendedprotectionscenario-property.md) </span></span>  
 <span data-ttu-id="6057d-114">[SetExtendedProtectionSettings 方法 &#40;WMI MSReportServer_ConfigurationSetting&#41;](configurationsetting-method-setextendedprotectionsettings.md) </span><span class="sxs-lookup"><span data-stu-id="6057d-114">[SetExtendedProtectionSettings Method &#40;WMI MSReportServer_ConfigurationSetting&#41;](configurationsetting-method-setextendedprotectionsettings.md) </span></span>  
 <span data-ttu-id="6057d-115">[Reporting Services 的驗證擴充保護](../security/extended-protection-for-authentication-with-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="6057d-115">[Extended Protection for Authentication with Reporting Services](../security/extended-protection-for-authentication-with-reporting-services.md) </span></span>  
 [<span data-ttu-id="6057d-116">RSReportServer 設定檔</span><span class="sxs-lookup"><span data-stu-id="6057d-116">RSReportServer Configuration File</span></span>](../report-server/rsreportserver-config-configuration-file.md)  
  
  
