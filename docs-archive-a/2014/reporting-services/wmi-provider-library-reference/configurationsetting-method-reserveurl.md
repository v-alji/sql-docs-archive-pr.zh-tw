---
title: ReserveURL 方法 (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- ReservedURL method
ms.assetid: b9008a62-3edd-4f8a-99f2-7598c2133899
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 95a58938ada19b4e49f094e3d8d01b241f1a4286
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706074"
---
# <a name="reserveurl-method-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="df7ce-102">ReserveURL 方法 (WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="df7ce-102">ReserveURL Method (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="df7ce-103">加入給定應用程式的 URL 保留項目。</span><span class="sxs-lookup"><span data-stu-id="df7ce-103">Adds a URL reservation for a given application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df7ce-104">語法</span><span class="sxs-lookup"><span data-stu-id="df7ce-104">Syntax</span></span>  
  
```vb  
Public Sub ReserveURL(Application as String, _  
    UrlString as String, Lcid as Int32, _   
    ByRef [Error] as String, ByRef HRESULT as Int32)  
```  
  
```csharp  
public void ReserveURL(string Application, string UrlString, int Lcid,   
    out string error, out int HRESULT);  
```  
  
## <a name="parameters"></a><span data-ttu-id="df7ce-105">參數</span><span class="sxs-lookup"><span data-stu-id="df7ce-105">Parameters</span></span>  
 <span data-ttu-id="df7ce-106">*應用程式*</span><span class="sxs-lookup"><span data-stu-id="df7ce-106">*Application*</span></span>  
 <span data-ttu-id="df7ce-107">要保留 URL 之應用程式的名稱。</span><span class="sxs-lookup"><span data-stu-id="df7ce-107">The name of application to reserve the URL for.</span></span>  
  
 <span data-ttu-id="df7ce-108">*URLString*</span><span class="sxs-lookup"><span data-stu-id="df7ce-108">*URLString*</span></span>  
 <span data-ttu-id="df7ce-109">保留項目的 URL。</span><span class="sxs-lookup"><span data-stu-id="df7ce-109">The URL for the reservation.</span></span>  
  
 <span data-ttu-id="df7ce-110">*lcid*</span><span class="sxs-lookup"><span data-stu-id="df7ce-110">*lcid*</span></span>  
 <span data-ttu-id="df7ce-111">要用於傳回之錯誤訊息的地區設定。</span><span class="sxs-lookup"><span data-stu-id="df7ce-111">The locale to use for the error messages returned.</span></span>  
  
 <span data-ttu-id="df7ce-112">*錯誤*</span><span class="sxs-lookup"><span data-stu-id="df7ce-112">*Error*</span></span>  
 <span data-ttu-id="df7ce-113">[out] 發生之錯誤的描述。</span><span class="sxs-lookup"><span data-stu-id="df7ce-113">[out] The description of the error that occurred.</span></span>  
  
 <span data-ttu-id="df7ce-114">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="df7ce-114">*HRESULT*</span></span>  
 <span data-ttu-id="df7ce-115">[out] 指出呼叫成功或失敗的值。</span><span class="sxs-lookup"><span data-stu-id="df7ce-115">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="df7ce-116">傳回值</span><span class="sxs-lookup"><span data-stu-id="df7ce-116">Return Value</span></span>  
 <span data-ttu-id="df7ce-117">傳回 *HRESULT* ，指出方法呼叫成功或失敗。</span><span class="sxs-lookup"><span data-stu-id="df7ce-117">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="df7ce-118">值為 0 表示方法呼叫成功。錯誤碼則表示呼叫不成功。</span><span class="sxs-lookup"><span data-stu-id="df7ce-118">A value of 0 indicates that the method call was successful; an error code indicates the call was not successful.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="df7ce-119">備註</span><span class="sxs-lookup"><span data-stu-id="df7ce-119">Remarks</span></span>  
 <span data-ttu-id="df7ce-120">*UrlString* 不包含虛擬目錄名稱。</span><span class="sxs-lookup"><span data-stu-id="df7ce-120">*UrlString* does not include the virtual directory name.</span></span> <span data-ttu-id="df7ce-121">[SetVirtualDirectory](configurationsetting-method-setvirtualdirectory.md) 方法是針對該目的提供的。</span><span class="sxs-lookup"><span data-stu-id="df7ce-121">The [SetVirtualDirectory](configurationsetting-method-setvirtualdirectory.md) method is provided for that purpose.</span></span>  
  
 <span data-ttu-id="df7ce-122">URL 保留項目是針對目前的 Windows 服務帳戶所建立的。</span><span class="sxs-lookup"><span data-stu-id="df7ce-122">URL reservations are created for the current windows service account.</span></span> <span data-ttu-id="df7ce-123">變更 Windows 服務帳戶需要手動更新所有 URL 保留項目。</span><span class="sxs-lookup"><span data-stu-id="df7ce-123">Changing the windows service account requires updating all the URL reservations manually.</span></span>  
  
 <span data-ttu-id="df7ce-124">這個方法會導致所有應用程式網域進行硬式回收。</span><span class="sxs-lookup"><span data-stu-id="df7ce-124">This method causes all application domains to hard recycle.</span></span> <span data-ttu-id="df7ce-125">在此作業完成之後，應用程式網域就會重新啟動。</span><span class="sxs-lookup"><span data-stu-id="df7ce-125">Application domains are restarted after this operation is complete.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="df7ce-126">需求</span><span class="sxs-lookup"><span data-stu-id="df7ce-126">Requirements</span></span>  
 <span data-ttu-id="df7ce-127">**命名空間：** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="df7ce-127">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df7ce-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="df7ce-128">See Also</span></span>  
 [<span data-ttu-id="df7ce-129">MSReportServer_ConfigurationSetting 成員</span><span class="sxs-lookup"><span data-stu-id="df7ce-129">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
