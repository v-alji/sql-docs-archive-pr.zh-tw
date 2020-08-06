---
title: ListIPAddresses 方法 (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- ListIPAddresses method
ms.assetid: 7e7cf182-fba0-4604-a474-098461e23e9d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 845f7ba7db02a0b860f966184463580733af0faf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594912"
---
# <a name="listipaddresses-method-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="d4ab0-102">ListIPAddresses 方法 (WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="d4ab0-102">ListIPAddresses Method (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="d4ab0-103">列出報表伺服器電腦的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="d4ab0-103">Lists the IP addresses for the report server computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4ab0-104">語法</span><span class="sxs-lookup"><span data-stu-id="d4ab0-104">Syntax</span></span>  
  
```vb  
Public Sub ListIPAddresses (ByRef IPAddress() as String, _  
    ByRef IPVersion()as String, ByRef IsDhcpEnabled () as Boolean, _   
    ByRef Length as Int32, ByRef HRESULT as Int32)  
```  
  
```csharp  
public void ListIPAddresses (out string[] IPAddress,   
    out string[] IPVersion, out bool[] isDhcpEnabled, out int length,   
    out int HRESULT);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d4ab0-105">參數</span><span class="sxs-lookup"><span data-stu-id="d4ab0-105">Parameters</span></span>  
 <span data-ttu-id="d4ab0-106">*IPAddress[]*</span><span class="sxs-lookup"><span data-stu-id="d4ab0-106">*IPAddress[]*</span></span>  
 <span data-ttu-id="d4ab0-107">[out] 電腦的 IP 位址清單。</span><span class="sxs-lookup"><span data-stu-id="d4ab0-107">[out] The list of IP address for the computer.</span></span>  
  
 <span data-ttu-id="d4ab0-108">*IPVersion[]*</span><span class="sxs-lookup"><span data-stu-id="d4ab0-108">*IPVersion[]*</span></span>  
 <span data-ttu-id="d4ab0-109">[out] IP 位址的版本。</span><span class="sxs-lookup"><span data-stu-id="d4ab0-109">[out] The version for the IP addresses.</span></span>  
  
 <span data-ttu-id="d4ab0-110">*IsDhcpEnabled[]*</span><span class="sxs-lookup"><span data-stu-id="d4ab0-110">*IsDhcpEnabled[]*</span></span>  
 <span data-ttu-id="d4ab0-111">[out] 指出 IP 位址是否已啟用 DHCP。</span><span class="sxs-lookup"><span data-stu-id="d4ab0-111">[out] Indicates whether the IP addresses are DHCP enabled.</span></span>  
  
 <span data-ttu-id="d4ab0-112">*長度*</span><span class="sxs-lookup"><span data-stu-id="d4ab0-112">*Length*</span></span>  
 <span data-ttu-id="d4ab0-113">[out] 此方法所傳回之陣列的長度。</span><span class="sxs-lookup"><span data-stu-id="d4ab0-113">[out] The length of the array returned by the method.</span></span>  
  
 <span data-ttu-id="d4ab0-114">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="d4ab0-114">*HRESULT*</span></span>  
 <span data-ttu-id="d4ab0-115">[out] 指出呼叫成功或失敗的值。</span><span class="sxs-lookup"><span data-stu-id="d4ab0-115">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d4ab0-116">傳回值</span><span class="sxs-lookup"><span data-stu-id="d4ab0-116">Return Value</span></span>  
 <span data-ttu-id="d4ab0-117">傳回 *HRESULT* ，指出方法呼叫成功或失敗。</span><span class="sxs-lookup"><span data-stu-id="d4ab0-117">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="d4ab0-118">值為 0 表示方法呼叫成功。錯誤碼則表示呼叫不成功。</span><span class="sxs-lookup"><span data-stu-id="d4ab0-118">A value of 0 indicates that the method call was successful; an error code indicates the call was not successful.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d4ab0-119">備註</span><span class="sxs-lookup"><span data-stu-id="d4ab0-119">Remarks</span></span>  
 <span data-ttu-id="d4ab0-120">*IPVersion* 字串為 V4 或 V6。</span><span class="sxs-lookup"><span data-stu-id="d4ab0-120">*IPVersion* strings are V4, V6.</span></span>  
  
 <span data-ttu-id="d4ab0-121">如果*IsDhcpEnabled*為 `True` ，則*IPAddress*是動態的。</span><span class="sxs-lookup"><span data-stu-id="d4ab0-121">If *IsDhcpEnabled* is `True`, the *IPAddress* is dynamic.</span></span> <span data-ttu-id="d4ab0-122">它就不應該用於 SSL 繫結。</span><span class="sxs-lookup"><span data-stu-id="d4ab0-122">It should not be used for SSL bindings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4ab0-123">需求</span><span class="sxs-lookup"><span data-stu-id="d4ab0-123">Requirements</span></span>  
 <span data-ttu-id="d4ab0-124">**命名空間：** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4ab0-124">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4ab0-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d4ab0-125">See Also</span></span>  
 [<span data-ttu-id="d4ab0-126">MSReportServer_ConfigurationSetting 成員</span><span class="sxs-lookup"><span data-stu-id="d4ab0-126">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
