---
title: SetSecureConnectionLevel 方法 (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- SetSecureConnectionLevel (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- SetSecureConnectionLevel method
ms.assetid: 0fac7d5e-2670-4657-9439-331e7d93babb
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 4361f09eb38b3e5650b68ae6f86b7f2266bbf1a2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706054"
---
# <a name="setsecureconnectionlevel-method-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="3cc69-102">SetSecureConnectionLevel 方法 (WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="3cc69-102">SetSecureConnectionLevel Method (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="3cc69-103">設定報表伺服器的安全連接層級。</span><span class="sxs-lookup"><span data-stu-id="3cc69-103">Sets the secure connection level of the report server.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3cc69-104">語法</span><span class="sxs-lookup"><span data-stu-id="3cc69-104">Syntax</span></span>  
  
```vb  
Public Sub SetSecureConnectionLevel(Level as Integer, _  
    ByRef HRESULT as Int32)  
```  
  
```csharp  
public void SetSecureConnectionLevel(Int32 Level,   
    out Int32 HRESULT);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3cc69-105">參數</span><span class="sxs-lookup"><span data-stu-id="3cc69-105">Parameters</span></span>  
 <span data-ttu-id="3cc69-106">*Level*</span><span class="sxs-lookup"><span data-stu-id="3cc69-106">*Level*</span></span>  
 <span data-ttu-id="3cc69-107">代表安全連接層級的整數值。</span><span class="sxs-lookup"><span data-stu-id="3cc69-107">An integer value representing a secure connection level.</span></span>  
  
 <span data-ttu-id="3cc69-108">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="3cc69-108">*HRESULT*</span></span>  
 <span data-ttu-id="3cc69-109">[out] 指出呼叫成功或失敗的值。</span><span class="sxs-lookup"><span data-stu-id="3cc69-109">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3cc69-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="3cc69-110">Return Value</span></span>  
 <span data-ttu-id="3cc69-111">傳回 *HRESULT* ，指出方法呼叫成功或失敗。</span><span class="sxs-lookup"><span data-stu-id="3cc69-111">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="3cc69-112">值為 0 表示方法呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="3cc69-112">A value of 0 indicates that the method call was successful.</span></span> <span data-ttu-id="3cc69-113">非零值則表示已發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="3cc69-113">A non-zero value indicates that an error has occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3cc69-114">備註</span><span class="sxs-lookup"><span data-stu-id="3cc69-114">Remarks</span></span>  
 <span data-ttu-id="3cc69-115">呼叫時，報表伺服器的 SecureConnectionLevel 屬性會設定為指定的值。</span><span class="sxs-lookup"><span data-stu-id="3cc69-115">When called, the report server SecureConnectionLevel property is set to the value specified.</span></span> <span data-ttu-id="3cc69-116">值為 0 時，表示 SSL 為關閉狀態。</span><span class="sxs-lookup"><span data-stu-id="3cc69-116">A value of 0 indicates that SSL is turned off.</span></span> <span data-ttu-id="3cc69-117">值大於或等於 1 時，表示 SSL 為開啟狀態。</span><span class="sxs-lookup"><span data-stu-id="3cc69-117">A value greater than or equal to 1 indicates that SSL is turned on.</span></span>  
  
-   <span data-ttu-id="3cc69-118">設定值時，報表伺服器設定檔中的 SecureConnectionLevel 元素會變更，而且如果指定的 `URLRoot` *層級*大於或等於1，則設定檔中的元素會設定為使用 "HTTPs://"，如果指定的*層級*為0，則為 "HTTP://"。</span><span class="sxs-lookup"><span data-stu-id="3cc69-118">When the value is set, the SecureConnectionLevel element in the report server configuration file is changed, and the `URLRoot` element in the configuration file is set to use "https://" if the specified *Level* is greater than or equal to 1, or "http://" if the specified *Level* is 0.</span></span>  
  
 <span data-ttu-id="3cc69-119">在 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]中，SecureConnectionLevel 會變成 on/off 開關，預設值為 0。</span><span class="sxs-lookup"><span data-stu-id="3cc69-119">In [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], SecureConnectionLevel is made an on/off switch, default value is 0.</span></span> <span data-ttu-id="3cc69-120">對於大於或等於 1，且通過 SetSecureConnectionLevel 方法 API 的任何值，都會將 SSL 視為開啟狀態，並且在 rsreportserver.config 檔案中據此設定組態屬性 SecureConnectionLevel。</span><span class="sxs-lookup"><span data-stu-id="3cc69-120">For any value greater than or equal to 1 passed through SetSecureConnectionLevel method API, SSL is considered on and the configuration property SecureConnectionLevel is set accordingly in the rsreportserver.config file.</span></span> <span data-ttu-id="3cc69-121">基於回溯相容性，仍然允許使用值 2 和 3。</span><span class="sxs-lookup"><span data-stu-id="3cc69-121">Values of 2 and 3 are still allowed for backward compatibility.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3cc69-122">需求</span><span class="sxs-lookup"><span data-stu-id="3cc69-122">Requirements</span></span>  
 <span data-ttu-id="3cc69-123">**命名空間：** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3cc69-123">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3cc69-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3cc69-124">See Also</span></span>  
 [<span data-ttu-id="3cc69-125">MSReportServer_ConfigurationSetting 成員</span><span class="sxs-lookup"><span data-stu-id="3cc69-125">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
