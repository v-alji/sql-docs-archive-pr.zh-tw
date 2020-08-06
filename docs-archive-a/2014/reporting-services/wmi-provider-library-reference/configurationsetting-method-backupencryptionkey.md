---
title: BackupEncryptionKey 方法 (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- BackupEncryptionKey Method (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- BackupEncryptionKey method
ms.assetid: da1d5dae-2517-448e-96fb-5379c93222ea
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d625401324e2117ee1e9677d840854fa7b63c6e5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706089"
---
# <a name="backupencryptionkey-method-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="982f9-102">BackupEncryptionKey 方法 (WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="982f9-102">BackupEncryptionKey Method (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="982f9-103">備份指定之報表伺服器執行個體的加密金鑰。</span><span class="sxs-lookup"><span data-stu-id="982f9-103">Backs up the encryption key for the specified report server instance.</span></span> <span data-ttu-id="982f9-104">此加密金鑰會以密碼加密的方式儲存。</span><span class="sxs-lookup"><span data-stu-id="982f9-104">The encryption key is stored encrypted with a password.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="982f9-105">語法</span><span class="sxs-lookup"><span data-stu-id="982f9-105">Syntax</span></span>  
  
```vb  
Public Sub BackupEncryptionKey(Password as String, _  
    ByRef KeyFile() as Integer, ByRef Length as Int32, _  
    ByRef HRESULT as Int32, ByRef ExtendedErrors() as String)  
  
```  
  
```csharp  
public void BackupEncryptionKey(string Password, out Byte[] KeyFile,   
    out Int32 Length, out Int32 HRESULT, out string[] ExtendedErrors);  
```  
  
## <a name="parameters"></a><span data-ttu-id="982f9-106">參數</span><span class="sxs-lookup"><span data-stu-id="982f9-106">Parameters</span></span>  
 <span data-ttu-id="982f9-107">*密碼*</span><span class="sxs-lookup"><span data-stu-id="982f9-107">*Password*</span></span>  
 <span data-ttu-id="982f9-108">用來在傳回加密金鑰之前進行加密的字串。</span><span class="sxs-lookup"><span data-stu-id="982f9-108">A string used to encrypt the encryption key before it is returned.</span></span>  
  
 <span data-ttu-id="982f9-109">*KeyFile[]*</span><span class="sxs-lookup"><span data-stu-id="982f9-109">*KeyFile[]*</span></span>  
 <span data-ttu-id="982f9-110">[out] 包含已加密之加密金鑰的陣列。</span><span class="sxs-lookup"><span data-stu-id="982f9-110">[out] An array containing the encrypted encryption key.</span></span>  
  
 <span data-ttu-id="982f9-111">*長度*</span><span class="sxs-lookup"><span data-stu-id="982f9-111">*Length*</span></span>  
 <span data-ttu-id="982f9-112">[out] 此方法所傳回之陣列的長度。</span><span class="sxs-lookup"><span data-stu-id="982f9-112">[out] The length of the array returned by the method.</span></span>  
  
 <span data-ttu-id="982f9-113">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="982f9-113">*HRESULT*</span></span>  
 <span data-ttu-id="982f9-114">[out] 指出呼叫成功或失敗的值。</span><span class="sxs-lookup"><span data-stu-id="982f9-114">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
 <span data-ttu-id="982f9-115">*ExtendedErrors[]*</span><span class="sxs-lookup"><span data-stu-id="982f9-115">*ExtendedErrors[]*</span></span>  
 <span data-ttu-id="982f9-116">[out] 包含呼叫所傳回之其他錯誤的字串陣列。</span><span class="sxs-lookup"><span data-stu-id="982f9-116">[out] A string array containing additional errors returned by the call.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="982f9-117">傳回值</span><span class="sxs-lookup"><span data-stu-id="982f9-117">Return Value</span></span>  
 <span data-ttu-id="982f9-118">傳回 *HRESULT* ，指出方法呼叫成功或失敗。</span><span class="sxs-lookup"><span data-stu-id="982f9-118">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="982f9-119">值為 0 表示方法呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="982f9-119">A value of 0 indicates that the method call was successful.</span></span> <span data-ttu-id="982f9-120">非零值則表示已發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="982f9-120">A non-zero value indicates that an error has occurred.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="982f9-121">需求</span><span class="sxs-lookup"><span data-stu-id="982f9-121">Requirements</span></span>  
 <span data-ttu-id="982f9-122">**命名空間：** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="982f9-122">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="982f9-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="982f9-123">See Also</span></span>  
 [<span data-ttu-id="982f9-124">MSReportServer_ConfigurationSetting 成員</span><span class="sxs-lookup"><span data-stu-id="982f9-124">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
