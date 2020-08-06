---
title: ListSSLCertificates 方法 (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- ListSSLCertificates method
ms.assetid: 88cd0936-b202-4ab8-90f2-d9c3f66d37f4
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 6a5ced8371817adc44bbbc89400dc83e0dfccef0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594900"
---
# <a name="listsslcertificates-method-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="a9918-102">ListSSLCertificates 方法 (WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="a9918-102">ListSSLCertificates Method (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="a9918-103">傳回報表伺服器電腦上的憑證清單。</span><span class="sxs-lookup"><span data-stu-id="a9918-103">Returns a list of certificates on the report server computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9918-104">語法</span><span class="sxs-lookup"><span data-stu-id="a9918-104">Syntax</span></span>  
  
```vb  
Public Sub CreateSSLCertificateBinding (ByRef CertificateHash() as String, _  
    ByRef CertName() as String, ByRef HostName() as String, ByRef Length as Int32, _   
    ByRef HRESULT as Int32)  
```  
  
```csharp  
public void ListSSLCertificates(out string[] CertificateHash,   
    out string[] CertName, out string[] Hostname, out Int32 length,   
    out Int32 HRESULT);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a9918-105">參數</span><span class="sxs-lookup"><span data-stu-id="a9918-105">Parameters</span></span>  
 <span data-ttu-id="a9918-106">*CertificateHash[]*</span><span class="sxs-lookup"><span data-stu-id="a9918-106">*CertificateHash[]*</span></span>  
 <span data-ttu-id="a9918-107">[out] 憑證雜湊。</span><span class="sxs-lookup"><span data-stu-id="a9918-107">[out] The certificate hashes.</span></span>  
  
 <span data-ttu-id="a9918-108">*CertName]*</span><span class="sxs-lookup"><span data-stu-id="a9918-108">*CertName[]*</span></span>  
 <span data-ttu-id="a9918-109">[out] 憑證的名稱。</span><span class="sxs-lookup"><span data-stu-id="a9918-109">[out] Names of the certificate.</span></span>  
  
 <span data-ttu-id="a9918-110">*HostName[]*</span><span class="sxs-lookup"><span data-stu-id="a9918-110">*HostName[]*</span></span>  
 <span data-ttu-id="a9918-111">[out] 憑證的主機名稱。</span><span class="sxs-lookup"><span data-stu-id="a9918-111">[out] The host names for the certificates.</span></span>  
  
 <span data-ttu-id="a9918-112">*長度*</span><span class="sxs-lookup"><span data-stu-id="a9918-112">*Length*</span></span>  
 <span data-ttu-id="a9918-113">[out] 代表 *CertificateHash*、 *CertName* 和 *HostName* 陣列的長度。</span><span class="sxs-lookup"><span data-stu-id="a9918-113">[out] Represents the length of the *CertificateHash*, *CertName* and *HostName* arrays.</span></span>  
  
 <span data-ttu-id="a9918-114">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="a9918-114">*HRESULT*</span></span>  
 <span data-ttu-id="a9918-115">[out] 指出呼叫成功或失敗的值。</span><span class="sxs-lookup"><span data-stu-id="a9918-115">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a9918-116">傳回值</span><span class="sxs-lookup"><span data-stu-id="a9918-116">Return Value</span></span>  
 <span data-ttu-id="a9918-117">傳回 *HRESULT* ，指出方法呼叫成功或失敗。</span><span class="sxs-lookup"><span data-stu-id="a9918-117">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="a9918-118">值為 0 表示方法呼叫成功。錯誤碼則表示呼叫不成功。</span><span class="sxs-lookup"><span data-stu-id="a9918-118">A value of 0 indicates that the method call was successful; an error code indicates the call was not successful.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a9918-119">備註</span><span class="sxs-lookup"><span data-stu-id="a9918-119">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a9918-120">需求</span><span class="sxs-lookup"><span data-stu-id="a9918-120">Requirements</span></span>  
 <span data-ttu-id="a9918-121">**命名空間：** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9918-121">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9918-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a9918-122">See Also</span></span>  
 [<span data-ttu-id="a9918-123">MSReportServer_ConfigurationSetting 成員</span><span class="sxs-lookup"><span data-stu-id="a9918-123">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
