---
title: ListSSLCertificateBindings 方法 (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- ListSSLCertificateBindings method
ms.assetid: d12d280c-9b6f-47a8-bcd9-34cde31c8886
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 56b19a138dc95b94a20183909dd444c90b158b26
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594903"
---
# <a name="listsslcertificatebindings-method-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="6c644-102">ListSSLCertificateBindings 方法 (WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="6c644-102">ListSSLCertificateBindings Method (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="6c644-103">傳回電腦上已安裝之 SSL 憑證的清單。</span><span class="sxs-lookup"><span data-stu-id="6c644-103">Returns a list of installed SSL certificates on the computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c644-104">語法</span><span class="sxs-lookup"><span data-stu-id="6c644-104">Syntax</span></span>  
  
```vb  
Public Sub ListSSLCertificateBindings(ByVal LCID As Int32, ByRef Application() As String, _  
    ByRef CertificateHash() As String, ByRef IPAddresses() As String, ByRef Port() As Int32, _  
    ByRef Errors() As String, ByRef Length As Int32, _  
    ByRef HRESULT As Int32)  
```  
  
```csharp  
public void ListSSLCertificateBindings(Int32 Lcid, out string[] Application,   
    out string[] CertificateHash,out string[] IPAddress,   
    out Int32[] Port, out string Errors,   
    out Int32 length, out Int32 HRESULT);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6c644-105">參數</span><span class="sxs-lookup"><span data-stu-id="6c644-105">Parameters</span></span>  
 <span data-ttu-id="6c644-106">*LCID*</span><span class="sxs-lookup"><span data-stu-id="6c644-106">*LCID*</span></span>  
 <span data-ttu-id="6c644-107">要用於傳回之錯誤訊息的地區設定。</span><span class="sxs-lookup"><span data-stu-id="6c644-107">The locale to use for the error messages that are returned.</span></span>  
  
 <span data-ttu-id="6c644-108">*Application[]*</span><span class="sxs-lookup"><span data-stu-id="6c644-108">*Application[]*</span></span>  
 <span data-ttu-id="6c644-109">[out] 具有憑證繫結的應用程式。</span><span class="sxs-lookup"><span data-stu-id="6c644-109">[out] The applications that have certificate bindings.</span></span>  
  
 <span data-ttu-id="6c644-110">*CertificateHash[]*</span><span class="sxs-lookup"><span data-stu-id="6c644-110">*CertificateHash[]*</span></span>  
 <span data-ttu-id="6c644-111">[out] 憑證的雜湊。</span><span class="sxs-lookup"><span data-stu-id="6c644-111">[out] The hashes for the certificates.</span></span>  
  
 <span data-ttu-id="6c644-112">*IPAddress[]*</span><span class="sxs-lookup"><span data-stu-id="6c644-112">*IPAddress[]*</span></span>  
 <span data-ttu-id="6c644-113">[out] 應用程式的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="6c644-113">[out] The IP address for the applications.</span></span>  
  
 <span data-ttu-id="6c644-114">*Port[]*</span><span class="sxs-lookup"><span data-stu-id="6c644-114">*Port[]*</span></span>  
 <span data-ttu-id="6c644-115">[out] 儲存在 rsreportserver.config 之繫結中的通訊埠編號。</span><span class="sxs-lookup"><span data-stu-id="6c644-115">[out] The port number stored in the binding in rsreportserver.config.</span></span>  
  
 <span data-ttu-id="6c644-116">*Errors[]*</span><span class="sxs-lookup"><span data-stu-id="6c644-116">*Errors[]*</span></span>  
 <span data-ttu-id="6c644-117">[out] 發生之錯誤的描述。</span><span class="sxs-lookup"><span data-stu-id="6c644-117">[out] The descriptions for errors that occurred.</span></span>  
  
 <span data-ttu-id="6c644-118">*長度*</span><span class="sxs-lookup"><span data-stu-id="6c644-118">*Length*</span></span>  
 <span data-ttu-id="6c644-119">[out] 此方法所傳回之陣列的長度。</span><span class="sxs-lookup"><span data-stu-id="6c644-119">[out] The length of the array returned by the method.</span></span>  
  
 <span data-ttu-id="6c644-120">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="6c644-120">*HRESULT*</span></span>  
 <span data-ttu-id="6c644-121">[out] 指出呼叫成功或失敗的值。</span><span class="sxs-lookup"><span data-stu-id="6c644-121">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6c644-122">傳回值</span><span class="sxs-lookup"><span data-stu-id="6c644-122">Return Value</span></span>  
 <span data-ttu-id="6c644-123">傳回 *HRESULT* ，指出方法呼叫成功或失敗。</span><span class="sxs-lookup"><span data-stu-id="6c644-123">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="6c644-124">值為 0 表示方法呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="6c644-124">A value of 0 indicates that the method call was successful.</span></span> <span data-ttu-id="6c644-125">非零值則表示已發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="6c644-125">A non-zero value indicates that an error has occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6c644-126">備註</span><span class="sxs-lookup"><span data-stu-id="6c644-126">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c644-127">需求</span><span class="sxs-lookup"><span data-stu-id="6c644-127">Requirements</span></span>  
 <span data-ttu-id="6c644-128">**命名空間：** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6c644-128">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c644-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6c644-129">See Also</span></span>  
 [<span data-ttu-id="6c644-130">MSReportServer_ConfigurationSetting 成員</span><span class="sxs-lookup"><span data-stu-id="6c644-130">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
