---
title: CreateSSLCertificateBinding 方法 (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- CreateSSLCertificateBinding
ms.assetid: 407d50e4-0a55-43cb-8ddf-2d82714071b1
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 8b9a5f9394d655f7b0592ea688a46f3ac2b9c153
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594931"
---
# <a name="createsslcertificatebinding-method-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="47558-102">CreateSSLCertificateBinding 方法 (WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="47558-102">CreateSSLCertificateBinding Method (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="47558-103">建立 SSL 憑證繫結。</span><span class="sxs-lookup"><span data-stu-id="47558-103">Creates an SSL Certificate binding.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47558-104">語法</span><span class="sxs-lookup"><span data-stu-id="47558-104">Syntax</span></span>  
  
```vb  
Public Sub CreateSSLCertificateBinding(ByVal Application As String, _  
    ByVal CertificateHash As String, ByVal IPAddress As String, _  
    ByVal Port As Int32, ByVal lcid As Int32, _  
    ByRef [Error] As String, ByRef HRESULT As Int32)  
```  
  
```csharp  
public void CreateSSLCertificateBinding(string application,   
    string certificateHash, string IPAddress, int Port,   
    int lcid, out string error, out int HRESULT);  
```  
  
## <a name="parameters"></a><span data-ttu-id="47558-105">參數</span><span class="sxs-lookup"><span data-stu-id="47558-105">Parameters</span></span>  
 <span data-ttu-id="47558-106">*應用程式*</span><span class="sxs-lookup"><span data-stu-id="47558-106">*Application*</span></span>  
 <span data-ttu-id="47558-107">應該建立憑證繫結之應用程式的名稱。</span><span class="sxs-lookup"><span data-stu-id="47558-107">The name of application that the certificate binding should be created for.</span></span>  
  
 <span data-ttu-id="47558-108">*CertificateHash*</span><span class="sxs-lookup"><span data-stu-id="47558-108">*CertificateHash*</span></span>  
 <span data-ttu-id="47558-109">憑證的雜湊。</span><span class="sxs-lookup"><span data-stu-id="47558-109">The hash for the certificate.</span></span>  
  
 <span data-ttu-id="47558-110">*IPAddress*</span><span class="sxs-lookup"><span data-stu-id="47558-110">*IPAddress*</span></span>  
 <span data-ttu-id="47558-111">應用程式的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="47558-111">The IP address for the application.</span></span>  
  
 <span data-ttu-id="47558-112">*通訊埠*</span><span class="sxs-lookup"><span data-stu-id="47558-112">*Port*</span></span>  
 <span data-ttu-id="47558-113">與繫結相關聯的 SSL 通訊埠。</span><span class="sxs-lookup"><span data-stu-id="47558-113">The SSL port associated with the binding.</span></span>  
  
 <span data-ttu-id="47558-114">*Lcid*</span><span class="sxs-lookup"><span data-stu-id="47558-114">*Lcid*</span></span>  
 <span data-ttu-id="47558-115">要用於傳回之錯誤訊息的地區設定。</span><span class="sxs-lookup"><span data-stu-id="47558-115">The locale to use for the error messages returned.</span></span>  
  
 <span data-ttu-id="47558-116">*錯誤*</span><span class="sxs-lookup"><span data-stu-id="47558-116">*Error*</span></span>  
 <span data-ttu-id="47558-117">[out] 發生之錯誤的描述。</span><span class="sxs-lookup"><span data-stu-id="47558-117">[out] The description of the errors that occurred.</span></span>  
  
 <span data-ttu-id="47558-118">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="47558-118">*HRESULT*</span></span>  
 <span data-ttu-id="47558-119">[out] 指出呼叫成功或失敗的值。</span><span class="sxs-lookup"><span data-stu-id="47558-119">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="47558-120">傳回值</span><span class="sxs-lookup"><span data-stu-id="47558-120">Return Value</span></span>  
 <span data-ttu-id="47558-121">傳回 *HRESULT* ，指出方法呼叫成功或失敗。</span><span class="sxs-lookup"><span data-stu-id="47558-121">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="47558-122">值為 0 表示方法呼叫成功。錯誤碼則表示呼叫不成功。</span><span class="sxs-lookup"><span data-stu-id="47558-122">A value of 0 indicates that the method call was successful; an error code indicates the call was not successful.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="47558-123">備註</span><span class="sxs-lookup"><span data-stu-id="47558-123">Remarks</span></span>  
 <span data-ttu-id="47558-124">這個方法會加入應用程式之 rsreportserver.config 的繫結。</span><span class="sxs-lookup"><span data-stu-id="47558-124">This method adds a binding to rsreportserver.config for the application.</span></span> <span data-ttu-id="47558-125">如果繫結尚未存在 HTTP.SYS 中，就會在該處建立繫結。</span><span class="sxs-lookup"><span data-stu-id="47558-125">If a binding does not already exist in HTTP.SYS, it is created there.</span></span>  
  
 <span data-ttu-id="47558-126">建立繫結之前，此方法呼叫會檢查指定之應用程式的 URL 保留項目，以便判斷 SSL 憑證繫結是否有效。</span><span class="sxs-lookup"><span data-stu-id="47558-126">Before creating the binding, the method call examines the Url Reservations for the specified application to determine if the SSL Certificate Binding is valid.</span></span>  
  
 <span data-ttu-id="47558-127">下列條件會進行驗證而且可能會產生錯誤：</span><span class="sxs-lookup"><span data-stu-id="47558-127">The following conditions are validated and can result in errors:</span></span>  
  
1.  <span data-ttu-id="47558-128">憑證不存在。</span><span class="sxs-lookup"><span data-stu-id="47558-128">Certificate does not exist.</span></span>  
  
2.  <span data-ttu-id="47558-129">指定的 IPAddress 並未對應至這部電腦的 IPAddress。</span><span class="sxs-lookup"><span data-stu-id="47558-129">The IPAddress specified does not correspond to an IPAddress of this computer.</span></span>  
  
3.  <span data-ttu-id="47558-130">指定的 IPAddress 是 DHCP IPAddress (定期變更) - 請改用萬用字元 IP 位址 (0.0.0.0)。</span><span class="sxs-lookup"><span data-stu-id="47558-130">The IPAddress specified is a DHCP IPAddress (changes periodically) - use the Wildcard IP address instead (0.0.0.0).</span></span>  
  
4.  <span data-ttu-id="47558-131">指定的 IPAddress 與 URL 保留項目的 IP 位址不符，而且萬用字元或主機名稱 URL 保留項目不存在。</span><span class="sxs-lookup"><span data-stu-id="47558-131">IPAddress specified does not match the IP address of a URL reservations AND neither a wildcard or host name URL reservation exist.</span></span>  
  
5.  <span data-ttu-id="47558-132">指定主機名稱的 URL 保留項目存在，但是此主機名稱與憑證主機名稱不符。</span><span class="sxs-lookup"><span data-stu-id="47558-132">A URL reservation that specifies a host name exists, but the host name does not match the certificate host name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="47558-133">需求</span><span class="sxs-lookup"><span data-stu-id="47558-133">Requirements</span></span>  
 <span data-ttu-id="47558-134">**命名空間：** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="47558-134">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47558-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="47558-135">See Also</span></span>  
 [<span data-ttu-id="47558-136">MSReportServer_ConfigurationSetting 成員</span><span class="sxs-lookup"><span data-stu-id="47558-136">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
