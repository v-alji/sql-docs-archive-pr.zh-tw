---
title: SetServiceState 方法 (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- SetServiceState (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- SetServiceState method
ms.assetid: 9e1ee42d-b388-4929-89c7-8741b956c3be
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 70b4a29b3379fc1d312af42a1f5b1296ee35dcf3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706045"
---
# <a name="setservicestate-method-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="05a99-102">SetServiceState 方法 (WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="05a99-102">SetServiceState Method (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="05a99-103">開啟和關閉報表伺服器 Windows 與 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="05a99-103">Turns the Report Server Windows and Web services on and off.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05a99-104">語法</span><span class="sxs-lookup"><span data-stu-id="05a99-104">Syntax</span></span>  
  
```vb  
Public Sub SetServiceState(ByVal EnableWindowsService As Boolean, _  
    ByVal EnableWebService As Boolean, ByVal EnableReportManager As Boolean, _  
    ByRef HRESULT As Int32)  
```  
  
```csharp  
public void SetSecureConnectionLevel(Boolean EnableWindowsService,  
    Boolean EnableWebService, Boolean EnableReportManager, out Int32 HRESULT);  
```  
  
## <a name="parameters"></a><span data-ttu-id="05a99-105">參數</span><span class="sxs-lookup"><span data-stu-id="05a99-105">Parameters</span></span>  
 <span data-ttu-id="05a99-106">*EnableWindowsService*</span><span class="sxs-lookup"><span data-stu-id="05a99-106">*EnableWindowsService*</span></span>  
 <span data-ttu-id="05a99-107">表示 Windows 服務狀態的 `Boolean` 值。</span><span class="sxs-lookup"><span data-stu-id="05a99-107">A `Boolean` value indicating the state of the Windows service.</span></span> <span data-ttu-id="05a99-108">值為 `true` 會啟動報表伺服器 Windows 服務。值為 `false` 會停止 Windows 服務。</span><span class="sxs-lookup"><span data-stu-id="05a99-108">A value of `true` starts the Report Server Windows service; a value of `false` stops the Windows service.</span></span>  
  
 <span data-ttu-id="05a99-109">*EnableWebService*</span><span class="sxs-lookup"><span data-stu-id="05a99-109">*EnableWebService*</span></span>  
 <span data-ttu-id="05a99-110">`Boolean`表示 Web 服務狀態的值 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="05a99-110">A `Boolean` value indicating the state of the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Web service.</span></span> <span data-ttu-id="05a99-111">值為 `true` 會啟動報表伺服器 Web 服務。值為 `false` 會停止 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="05a99-111">A value of `true` starts the Report Server Web service; a value of `false` stops the Web service</span></span>  
  
 <span data-ttu-id="05a99-112">*EnableReportManager*</span><span class="sxs-lookup"><span data-stu-id="05a99-112">*EnableReportManager*</span></span>  
 <span data-ttu-id="05a99-113">表示報表管理員所需狀態的 `Boolean` 值。</span><span class="sxs-lookup"><span data-stu-id="05a99-113">A `Boolean` value indicating the desired state of the Report manager.</span></span>  
  
 <span data-ttu-id="05a99-114">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="05a99-114">*HRESULT*</span></span>  
 <span data-ttu-id="05a99-115">[out] 指出呼叫成功或失敗的值。</span><span class="sxs-lookup"><span data-stu-id="05a99-115">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="05a99-116">傳回值</span><span class="sxs-lookup"><span data-stu-id="05a99-116">Return Value</span></span>  
 <span data-ttu-id="05a99-117">傳回 *HRESULT* ，指出方法呼叫成功或失敗。</span><span class="sxs-lookup"><span data-stu-id="05a99-117">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="05a99-118">值為 0 表示方法呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="05a99-118">A value of 0 indicates that the method call was successful.</span></span> <span data-ttu-id="05a99-119">非零值則表示已發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="05a99-119">A non-zero value indicates that an error has occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="05a99-120">備註</span><span class="sxs-lookup"><span data-stu-id="05a99-120">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05a99-121">需求</span><span class="sxs-lookup"><span data-stu-id="05a99-121">Requirements</span></span>  
 <span data-ttu-id="05a99-122">**命名空間：** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05a99-122">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05a99-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="05a99-123">See Also</span></span>  
 [<span data-ttu-id="05a99-124">MSReportServer_ConfigurationSetting 成員</span><span class="sxs-lookup"><span data-stu-id="05a99-124">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
