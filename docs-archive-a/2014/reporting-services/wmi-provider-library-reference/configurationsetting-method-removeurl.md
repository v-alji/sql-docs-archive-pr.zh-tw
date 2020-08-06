---
title: RemoveURL 方法 (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- RemoveURL method
ms.assetid: 3d98bd97-e152-48ce-ab1c-bd2c4f8b7fe9
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3a32989e8ce8986b785e829d8cc7fcf58fbbf240
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597011"
---
# <a name="removeurl-method-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="085e6-102">RemoveURL 方法 (WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="085e6-102">RemoveURL Method (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="085e6-103">移除針對報表伺服器所保留的 URL。</span><span class="sxs-lookup"><span data-stu-id="085e6-103">Removes a URL reserved for the report server.</span></span> <span data-ttu-id="085e6-104">如果有多個需要移除的 URL，您就必須呼叫這個 API 來逐一進行此作業。</span><span class="sxs-lookup"><span data-stu-id="085e6-104">If there are multiple URLs that need to be removed, this must be done one by one calling this API.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="085e6-105">語法</span><span class="sxs-lookup"><span data-stu-id="085e6-105">Syntax</span></span>  
  
```vb  
Public Sub RemoveURL(ByVal Application As String, _  
    ByVal UrlString As String, ByVal Lcid As Int32, _  
    ByRef [Error] As String, ByRef HRESULT As Int32)  
```  
  
```csharp  
public void RemoveURL(string Application, string UrlString, int Lcid,   
    out string Error, out int HRESULT);  
```  
  
## <a name="parameters"></a><span data-ttu-id="085e6-106">參數</span><span class="sxs-lookup"><span data-stu-id="085e6-106">Parameters</span></span>  
 <span data-ttu-id="085e6-107">*應用程式*</span><span class="sxs-lookup"><span data-stu-id="085e6-107">*Application*</span></span>  
 <span data-ttu-id="085e6-108">要移除保留項目之應用程式的名稱。</span><span class="sxs-lookup"><span data-stu-id="085e6-108">The name of application for which to remove the reservation.</span></span>  
  
 <span data-ttu-id="085e6-109">*URLString*</span><span class="sxs-lookup"><span data-stu-id="085e6-109">*URLString*</span></span>  
 <span data-ttu-id="085e6-110">保留項目的 URL。</span><span class="sxs-lookup"><span data-stu-id="085e6-110">The URL for the reservation.</span></span>  
  
 <span data-ttu-id="085e6-111">*lcid*</span><span class="sxs-lookup"><span data-stu-id="085e6-111">*lcid*</span></span>  
 <span data-ttu-id="085e6-112">要用於傳回之錯誤訊息的地區設定。</span><span class="sxs-lookup"><span data-stu-id="085e6-112">The locale to use for the error messages returned.</span></span>  
  
 <span data-ttu-id="085e6-113">*錯誤*</span><span class="sxs-lookup"><span data-stu-id="085e6-113">*Error*</span></span>  
 <span data-ttu-id="085e6-114">[out] 發生之錯誤的描述。</span><span class="sxs-lookup"><span data-stu-id="085e6-114">[out] The description of the error that occurred.</span></span>  
  
 <span data-ttu-id="085e6-115">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="085e6-115">*HRESULT*</span></span>  
 <span data-ttu-id="085e6-116">[out] 指出呼叫成功或失敗的值。</span><span class="sxs-lookup"><span data-stu-id="085e6-116">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="085e6-117">傳回值</span><span class="sxs-lookup"><span data-stu-id="085e6-117">Return Value</span></span>  
 <span data-ttu-id="085e6-118">傳回 *HRESULT* ，指出方法呼叫成功或失敗。</span><span class="sxs-lookup"><span data-stu-id="085e6-118">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="085e6-119">值為 0 表示方法呼叫成功。錯誤碼則表示呼叫不成功。</span><span class="sxs-lookup"><span data-stu-id="085e6-119">A value of 0 indicates that the method call was successful; an error code indicates the call was not successful.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="085e6-120">備註</span><span class="sxs-lookup"><span data-stu-id="085e6-120">Remarks</span></span>  
 <span data-ttu-id="085e6-121">*UrlString* 不包含虛擬目錄名稱 - [SetVirtualDirectory 方法 &#40;WMI MSReportServer_ConfigurationSetting&#41;](configurationsetting-method-setvirtualdirectory.md) 方法是針對該目的所提供。</span><span class="sxs-lookup"><span data-stu-id="085e6-121">*UrlString* does not include the Virtual Directory name - the [SetVirtualDirectory Method &#40;WMI MSReportServer_ConfigurationSetting&#41;](configurationsetting-method-setvirtualdirectory.md) method is provided for that purpose.</span></span>  
  
 <span data-ttu-id="085e6-122">呼叫 [ReserveURL](configurationsetting-method-reserveurl.md) 方法之前，您必須針對 *Application* 參數的 VirtualDirectory 組態屬性提供一個值。</span><span class="sxs-lookup"><span data-stu-id="085e6-122">Before calling the [ReserveURL](configurationsetting-method-reserveurl.md) method, you must supply a value for the VirtualDirectory configuration property for the *Application* parameter.</span></span> <span data-ttu-id="085e6-123">您可以使用 [SetVirtualDirectory 方法 &#40;WMI MSReportServer_ConfigurationSetting&#41;](configurationsetting-method-setvirtualdirectory.md) 方法來設定 VirtualDirectory 屬性。</span><span class="sxs-lookup"><span data-stu-id="085e6-123">Use the [SetVirtualDirectory Method &#40;WMI MSReportServer_ConfigurationSetting&#41;](configurationsetting-method-setvirtualdirectory.md) method to set the VirtualDirectory property.</span></span>  
  
 <span data-ttu-id="085e6-124">如果 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 提供了 SSL 憑證，但是沒有其他 URL 需要它，就會移除此憑證。</span><span class="sxs-lookup"><span data-stu-id="085e6-124">If an SSL Certificate was provisioned by [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] and no other URLs need it, it is removed.</span></span>  
  
 <span data-ttu-id="085e6-125">這個方法會導致所有非組態應用程式網域在此作業期間進行硬式回收並停止。在此作業完成之後，應用程式網域就會重新啟動。</span><span class="sxs-lookup"><span data-stu-id="085e6-125">This method causes all non-configuration app domains to hard recycle and stop during this operation; app domains are restarted after this operation complete.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="085e6-126">需求</span><span class="sxs-lookup"><span data-stu-id="085e6-126">Requirements</span></span>  
 <span data-ttu-id="085e6-127">**命名空間：** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="085e6-127">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="085e6-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="085e6-128">See Also</span></span>  
 [<span data-ttu-id="085e6-129">MSReportServer_ConfigurationSetting 成員</span><span class="sxs-lookup"><span data-stu-id="085e6-129">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
