---
title: SetExtendedProtectionSettings 方法 (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 2d8e7232-42f4-41b6-98eb-c856f6c85d8c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ee937747b74bcf8d53012721b4be5bfca04185df
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706061"
---
# <a name="setextendedprotectionsettings-method-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="a0d13-102">SetExtendedProtectionSettings 方法 (WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="a0d13-102">SetExtendedProtectionSettings Method (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="a0d13-103">使用 SetExtendedProtectionSettings 方法可在 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 組態檔 RSReportServer.config 中設定 RSWindowsExtendedProtectionLevel 和 RSWindowsExtendedProtectionScenario 屬性。</span><span class="sxs-lookup"><span data-stu-id="a0d13-103">The SetExtendedProtectionSettings method is used to set the RSWindowsExtendedProtectionLevel and the RSWindowsExtendedProtectionScenario properties in the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] configuration file RSReportServer.config.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0d13-104">語法</span><span class="sxs-lookup"><span data-stu-id="a0d13-104">Syntax</span></span>  
  
```vb  
Public Sub SetExtendedProtectionSettings( _  
        ByVal ExtendedProtectionLevel As String, _  
        ByVal ExtendedProtectionScenario As String, _  
        ByRef Warnings() As String, _  
        ByRef Length As Int32, _  
        ByRef HRESULT As Int32)  
```  
  
```csharp  
public void SetExtendedProtectionSettings(  
            string ExtendedProtectionLevel,  
            string ExtendedProtectionScenario,  
            out string[] Warnings,  
            out Int32 Length,  
            out Int32 HRESULT);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a0d13-105">參數</span><span class="sxs-lookup"><span data-stu-id="a0d13-105">Parameters</span></span>  
 <span data-ttu-id="a0d13-106">*ExtendedProtectionLevel*</span><span class="sxs-lookup"><span data-stu-id="a0d13-106">*ExtendedProtectionLevel*</span></span>  
 <span data-ttu-id="a0d13-107">在 RSRreportserver.config 檔案中設定 RSWindowsExtendedProtectionLevel。</span><span class="sxs-lookup"><span data-stu-id="a0d13-107">Sets the RSWindowsExtendedProtectionLevel in the RSRreportserver.config file.</span></span> <span data-ttu-id="a0d13-108">所需的值不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="a0d13-108">The required value is not case sensitive.</span></span>  
  
 <span data-ttu-id="a0d13-109">下列清單顯示有效值：</span><span class="sxs-lookup"><span data-stu-id="a0d13-109">The following list shows valid values:</span></span>  
  
 `"Off | Allow | Require"`  
  
 <span data-ttu-id="a0d13-110">*ExtendedProtectionScenario*</span><span class="sxs-lookup"><span data-stu-id="a0d13-110">*ExtendedProtectionScenario*</span></span>  
 <span data-ttu-id="a0d13-111">在 RSReportserver.config 檔案中設定 RSWindowsExtendedProtectionScenario。</span><span class="sxs-lookup"><span data-stu-id="a0d13-111">Sets the RSWindowsExtendedProtectionScenario in the RSReportserver.config file.</span></span> <span data-ttu-id="a0d13-112">所需的值不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="a0d13-112">The required value is not case sensitive.</span></span>  
  
 <span data-ttu-id="a0d13-113">下列清單顯示有效值：</span><span class="sxs-lookup"><span data-stu-id="a0d13-113">The following list shows valid values:</span></span>  
  
 `"Any" | "Proxy" | "Direct"`  
  
## <a name="remarks"></a><span data-ttu-id="a0d13-114">備註</span><span class="sxs-lookup"><span data-stu-id="a0d13-114">Remarks</span></span>  
 <span data-ttu-id="a0d13-115">當 RSReportServer.config 檔案中的 AuthenticationTypes 包括 RSWindowNTLM、RSWindowsNegotiate 或 RSWindowsKerberos 時，便會套用 RSWindowsExtendedProtectionLevel 和 the RSWindowsExtendedProtectionScenario 屬性。</span><span class="sxs-lookup"><span data-stu-id="a0d13-115">The RSWindowsExtendedProtectionLevel and the RSWindowsExtendedProtectionScenario properties apply when the AuthenticationTypes in the RSReportServer.config file include RSWindowNTLM, RSWindowsNegotiate, or RSWindowsKerberos.</span></span> <span data-ttu-id="a0d13-116">設定這些屬性會影響使用者和用戶端軟體向報表伺服器驗證的方式。</span><span class="sxs-lookup"><span data-stu-id="a0d13-116">Setting these properties affects how users and client software authenticate with a report server.</span></span> <span data-ttu-id="a0d13-117">建議您先閱讀擴充保護的文件，然後再將 ExtendedProtectionLevel 設定為 `Allow` 或 `Require`。</span><span class="sxs-lookup"><span data-stu-id="a0d13-117">It is recommended that you read the documentation for extended protection before setting ExtendedProtectionLevel to either `Allow` or `Require`.</span></span>  
  
 <span data-ttu-id="a0d13-118">若要設定 ExtendedProtectionLevel，使用者必須是報表伺服器上 BUILTIN\Administrators 群組的成員。</span><span class="sxs-lookup"><span data-stu-id="a0d13-118">To set the ExtendedProtectionLevel, the user must be a member of the BUILTIN\Administrators group on the report server.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a0d13-119">需求</span><span class="sxs-lookup"><span data-stu-id="a0d13-119">Requirements</span></span>  
 <span data-ttu-id="a0d13-120">**命名空間：** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a0d13-120">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0d13-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a0d13-121">See Also</span></span>  
 <span data-ttu-id="a0d13-122">[RSWindowsExtendedProtectionScenario 屬性 &#40;WMI MSReportServer_ConfigurationSetting&#41;](rswindowsextendedprotectionscenario-property.md) </span><span class="sxs-lookup"><span data-stu-id="a0d13-122">[RSWindowsExtendedProtectionScenario Property &#40;WMI MSReportServer_ConfigurationSetting&#41;](rswindowsextendedprotectionscenario-property.md) </span></span>  
 <span data-ttu-id="a0d13-123">[RSWindowsExtendedProtectionLevel 屬性 &#40;WMI MSReportServer_ConfigurationSetting&#41;](rswindowsextendedprotectionlevel-property.md) </span><span class="sxs-lookup"><span data-stu-id="a0d13-123">[RSWindowsExtendedProtectionLevel Property &#40;WMI MSReportServer_ConfigurationSetting&#41;](rswindowsextendedprotectionlevel-property.md) </span></span>  
 <span data-ttu-id="a0d13-124">[Reporting Services 的驗證擴充保護](../security/extended-protection-for-authentication-with-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="a0d13-124">[Extended Protection for Authentication with Reporting Services](../security/extended-protection-for-authentication-with-reporting-services.md) </span></span>  
 [<span data-ttu-id="a0d13-125">RSReportServer 設定檔</span><span class="sxs-lookup"><span data-stu-id="a0d13-125">RSReportServer Configuration File</span></span>](../report-server/rsreportserver-config-configuration-file.md)  
  
  
