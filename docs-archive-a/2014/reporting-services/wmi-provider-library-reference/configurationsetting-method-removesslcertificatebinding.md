---
title: RemoveSSLCertificateBindings 方法 (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- RemoveSSLCertificateBindings method
ms.assetid: b8b484c9-04c4-4ae9-980e-67bbe5aa8481
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d42d17d9c92f2e100a7800e607536ff6c7eab891
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704766"
---
# <a name="removesslcertificatebindings-method-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="80f42-102">RemoveSSLCertificateBindings 方法 (WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="80f42-102">RemoveSSLCertificateBindings Method (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="80f42-103">移除 SSL 憑證繫結。</span><span class="sxs-lookup"><span data-stu-id="80f42-103">Removes an SSL Certificate binding.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80f42-104">語法</span><span class="sxs-lookup"><span data-stu-id="80f42-104">Syntax</span></span>  
  
```vb  
Public Sub RemoveSSLCertificateBinding(ByVal Application As String, _  
    ByVal CertificateHash As String, ByVal IPAddress As String, _  
    ByVal Port As Int32, ByVal Lcid As Int32, _  
    ByRef [Error] As String, ByRef HRESULT As Int32)  
```  
  
```csharp  
public void RemoveSSLCertificateBindings(string Application,  
    string CertificateHash, string IPAddress, Int32 Port, Int32 Lcid,  
    out string Error, out Int32 HRESULT);  
```  
  
## <a name="parameters"></a><span data-ttu-id="80f42-105">參數</span><span class="sxs-lookup"><span data-stu-id="80f42-105">Parameters</span></span>  
 <span data-ttu-id="80f42-106">*應用程式*</span><span class="sxs-lookup"><span data-stu-id="80f42-106">*Application*</span></span>  
 <span data-ttu-id="80f42-107">應該移除憑證繫結之應用程式的名稱。</span><span class="sxs-lookup"><span data-stu-id="80f42-107">The name of application for which the certificate binding should be removed.</span></span>  
  
 <span data-ttu-id="80f42-108">*CertificateHash*</span><span class="sxs-lookup"><span data-stu-id="80f42-108">*CertificateHash*</span></span>  
 <span data-ttu-id="80f42-109">憑證的雜湊。</span><span class="sxs-lookup"><span data-stu-id="80f42-109">The hash for the certificate.</span></span>  
  
 <span data-ttu-id="80f42-110">*IPAddress*</span><span class="sxs-lookup"><span data-stu-id="80f42-110">*IPAddress*</span></span>  
 <span data-ttu-id="80f42-111">應用程式的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="80f42-111">The IP address for the application.</span></span>  
  
 <span data-ttu-id="80f42-112">*通訊埠*</span><span class="sxs-lookup"><span data-stu-id="80f42-112">*Port*</span></span>  
 <span data-ttu-id="80f42-113">與繫結相關聯的 SSL 通訊埠。</span><span class="sxs-lookup"><span data-stu-id="80f42-113">The SSL port associated with the binding.</span></span>  
  
 <span data-ttu-id="80f42-114">*lcid*</span><span class="sxs-lookup"><span data-stu-id="80f42-114">*lcid*</span></span>  
 <span data-ttu-id="80f42-115">要用於傳回之錯誤訊息的地區設定。</span><span class="sxs-lookup"><span data-stu-id="80f42-115">The locale to use for the error messages that are returned.</span></span>  
  
 <span data-ttu-id="80f42-116">*錯誤*</span><span class="sxs-lookup"><span data-stu-id="80f42-116">*Error*</span></span>  
 <span data-ttu-id="80f42-117">[out] 發生之錯誤的描述。</span><span class="sxs-lookup"><span data-stu-id="80f42-117">[out] The description of the error that occurred.</span></span>  
  
 <span data-ttu-id="80f42-118">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="80f42-118">*HRESULT*</span></span>  
 <span data-ttu-id="80f42-119">[out] 指出呼叫成功或失敗的值。</span><span class="sxs-lookup"><span data-stu-id="80f42-119">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="80f42-120">傳回值</span><span class="sxs-lookup"><span data-stu-id="80f42-120">Return Value</span></span>  
 <span data-ttu-id="80f42-121">傳回 *HRESULT* ，指出方法呼叫成功或失敗。</span><span class="sxs-lookup"><span data-stu-id="80f42-121">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="80f42-122">值為 0 表示方法呼叫成功。錯誤碼則表示呼叫不成功。</span><span class="sxs-lookup"><span data-stu-id="80f42-122">A value of 0 indicates that the method call was successful; an error code indicates the call was not successful.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="80f42-123">備註</span><span class="sxs-lookup"><span data-stu-id="80f42-123">Remarks</span></span>  
 <span data-ttu-id="80f42-124">這個方法會從 rsreportserver.config 檔案和 HTTP.SYS (選擇性) 中移除特定繫結。</span><span class="sxs-lookup"><span data-stu-id="80f42-124">This method removes the specific binding from the rsreportserver.config file and optionally HTTP.SYS.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="80f42-125">需求</span><span class="sxs-lookup"><span data-stu-id="80f42-125">Requirements</span></span>  
 <span data-ttu-id="80f42-126">**命名空間：** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="80f42-126">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80f42-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="80f42-127">See Also</span></span>  
 [<span data-ttu-id="80f42-128">MSReportServer_ConfigurationSetting 成員</span><span class="sxs-lookup"><span data-stu-id="80f42-128">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
