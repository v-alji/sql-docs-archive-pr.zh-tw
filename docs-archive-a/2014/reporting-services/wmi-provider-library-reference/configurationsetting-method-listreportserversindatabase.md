---
title: ListReportServersInDatabase 方法 (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- ListReportServersInDatabase (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- ListReportServersInDatabase method
ms.assetid: a4bf5968-c46f-484f-a510-65e2dde65a0d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9eaea72c0737124d89c86b55281326073597fb38
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594911"
---
# <a name="listreportserversindatabase-method-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="3fcaf-102">ListReportServersInDatabase 方法 (WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="3fcaf-102">ListReportServersInDatabase Method (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="3fcaf-103">傳回存在報表伺服器資料庫中之報表伺服器安裝的清單，不論它們是否具有安全資訊的存取權都一樣。</span><span class="sxs-lookup"><span data-stu-id="3fcaf-103">Returns the list of report server installations that are present in the report server database, regardless of whether they have access to secure information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3fcaf-104">語法</span><span class="sxs-lookup"><span data-stu-id="3fcaf-104">Syntax</span></span>  
  
```vb  
Public Sub ListReportServersInDatabase(ByRef MachineNames() As String, _  
    ByRef InstanceNames() As String, ByRef InstallationIDs() As String, _  
    ByRef IsInitialized() As Boolean, ByRef Length As Int32, _  
    ByRef HRESULT As Int32, ByRef ExtendedErrors() As String)  
```  
  
```csharp  
public void ListReportServersInDatabase (out string[] MachineNames,   
    out string[] InstanceNames, out string[] InstallationIDs,   
    out Boolean[] IsInitialized,out Int32 Length, out Int32 HRESULT,    
    out string[] ExtendedErrors);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3fcaf-105">參數</span><span class="sxs-lookup"><span data-stu-id="3fcaf-105">Parameters</span></span>  
 <span data-ttu-id="3fcaf-106">*MachineNames[]*</span><span class="sxs-lookup"><span data-stu-id="3fcaf-106">*MachineNames[]*</span></span>  
 <span data-ttu-id="3fcaf-107">[out] 包含資料庫中報表伺服器安裝之電腦名稱的陣列。</span><span class="sxs-lookup"><span data-stu-id="3fcaf-107">[out] An array containing the machine names for the report server installations in the database.</span></span>  
  
 <span data-ttu-id="3fcaf-108">*InstanceNames[]*</span><span class="sxs-lookup"><span data-stu-id="3fcaf-108">*InstanceNames[]*</span></span>  
 <span data-ttu-id="3fcaf-109">[out] 包含資料庫中每個報表伺服器安裝之執行個體名稱的陣列。</span><span class="sxs-lookup"><span data-stu-id="3fcaf-109">[out] An array containing the instance names of each of the report server installations in the database.</span></span>  
  
 <span data-ttu-id="3fcaf-110">*InstallationIDs[]*</span><span class="sxs-lookup"><span data-stu-id="3fcaf-110">*InstallationIDs[]*</span></span>  
 <span data-ttu-id="3fcaf-111">[out] 包含資料庫中每個報表伺服器安裝之安裝識別碼的陣列。</span><span class="sxs-lookup"><span data-stu-id="3fcaf-111">[out] An array containing the installation IDs of each report server installation in the database.</span></span>  
  
 <span data-ttu-id="3fcaf-112">*IsInitialized[]*</span><span class="sxs-lookup"><span data-stu-id="3fcaf-112">*IsInitialized[]*</span></span>  
 <span data-ttu-id="3fcaf-113">[out] 包含資料庫中每個報表伺服器安裝之初始化狀態的陣列。</span><span class="sxs-lookup"><span data-stu-id="3fcaf-113">[out] An array containing initialization status for each report server installation in the database.</span></span>  
  
 <span data-ttu-id="3fcaf-114">*長度*</span><span class="sxs-lookup"><span data-stu-id="3fcaf-114">*Length*</span></span>  
 <span data-ttu-id="3fcaf-115">[out] 此方法所傳回之陣列的長度。</span><span class="sxs-lookup"><span data-stu-id="3fcaf-115">[out] The length of the arrays returned by the method.</span></span> <span data-ttu-id="3fcaf-116">所有傳回的陣列都具有相同的長度。</span><span class="sxs-lookup"><span data-stu-id="3fcaf-116">All returned arrays have the same length.</span></span>  
  
 <span data-ttu-id="3fcaf-117">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="3fcaf-117">*HRESULT*</span></span>  
 <span data-ttu-id="3fcaf-118">[out] 指出呼叫成功或失敗的值。</span><span class="sxs-lookup"><span data-stu-id="3fcaf-118">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
 <span data-ttu-id="3fcaf-119">*ExtendedErrors[]*</span><span class="sxs-lookup"><span data-stu-id="3fcaf-119">*ExtendedErrors[]*</span></span>  
 <span data-ttu-id="3fcaf-120">[out] 包含呼叫所傳回之其他錯誤的字串陣列。</span><span class="sxs-lookup"><span data-stu-id="3fcaf-120">[out] A string array containing additional errors returned by the call.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3fcaf-121">傳回值</span><span class="sxs-lookup"><span data-stu-id="3fcaf-121">Return Value</span></span>  
 <span data-ttu-id="3fcaf-122">傳回 *HRESULT* ，指出方法呼叫成功或失敗。</span><span class="sxs-lookup"><span data-stu-id="3fcaf-122">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="3fcaf-123">值為 0 表示方法呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="3fcaf-123">A value of 0 indicates that the method call was successful.</span></span> <span data-ttu-id="3fcaf-124">非零值則表示已發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="3fcaf-124">A non-zero value indicates that an error has occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3fcaf-125">備註</span><span class="sxs-lookup"><span data-stu-id="3fcaf-125">Remarks</span></span>  
 <span data-ttu-id="3fcaf-126">ListReportServersInDatabase 會列出存在報表伺服器資料庫中的報表伺服器安裝，不論它們是否具有安全資訊的存取權都一樣，並且傳回一組包含每個安裝之資訊的相符陣列。</span><span class="sxs-lookup"><span data-stu-id="3fcaf-126">ListReportServersInDatabase lists the report server installations that are present in the report server database, regardless of whether they have access to secure information, and returns a matched set of arrays containing information about each installation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3fcaf-127">需求</span><span class="sxs-lookup"><span data-stu-id="3fcaf-127">Requirements</span></span>  
 <span data-ttu-id="3fcaf-128">**命名空間：** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3fcaf-128">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fcaf-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3fcaf-129">See Also</span></span>  
 [<span data-ttu-id="3fcaf-130">MSReportServer_ConfigurationSetting 成員</span><span class="sxs-lookup"><span data-stu-id="3fcaf-130">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
