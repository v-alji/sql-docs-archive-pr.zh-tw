---
title: RestoreEncryptionKey 方法 (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- RestoreEncryptionKey (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- RestoreEncryptionKey method
ms.assetid: 37e949f5-15af-4858-848a-f482ee94fcd9
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: e67478541bab615a6d441ae273ed3385a8654203
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706073"
---
# <a name="restoreencryptionkey-method-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="f82fa-102">RestoreEncryptionKey 方法 (WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="f82fa-102">RestoreEncryptionKey Method (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="f82fa-103">將指定的加密金鑰重新套用至報表伺服器資料庫。</span><span class="sxs-lookup"><span data-stu-id="f82fa-103">Reapplies the specified encryption key to the report server database.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f82fa-104">語法</span><span class="sxs-lookup"><span data-stu-id="f82fa-104">Syntax</span></span>  
  
```vb  
Public Sub RestoreEncryptionKey(ByRef KeyFile() As Integer, _  
    ByRef Length As Int32, ByVal Password As String, _  
    ByRef HRESULT As Int32, ByRef ExtendedErrors() As String)  
```  
  
```csharp  
public void RestoreEncryptionKey(out Byte[] KeyFile, out Int32 Length,   
            string Password, out Int32 HRESULT, out string[] ExtendedErrors);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f82fa-105">參數</span><span class="sxs-lookup"><span data-stu-id="f82fa-105">Parameters</span></span>  
 <span data-ttu-id="f82fa-106">*KeyFile[]*</span><span class="sxs-lookup"><span data-stu-id="f82fa-106">*KeyFile[]*</span></span>  
 <span data-ttu-id="f82fa-107">[out] 包含已加密之加密金鑰的陣列。</span><span class="sxs-lookup"><span data-stu-id="f82fa-107">[out] An array containing the encrypted encryption key.</span></span>  
  
 <span data-ttu-id="f82fa-108">*長度*</span><span class="sxs-lookup"><span data-stu-id="f82fa-108">*Length*</span></span>  
 <span data-ttu-id="f82fa-109">[out] 此方法所傳回之陣列的長度。</span><span class="sxs-lookup"><span data-stu-id="f82fa-109">[out] The length of the array returned by the method.</span></span>  
  
 <span data-ttu-id="f82fa-110">*密碼*</span><span class="sxs-lookup"><span data-stu-id="f82fa-110">*Password*</span></span>  
 <span data-ttu-id="f82fa-111">用來加密加密金鑰的字串。</span><span class="sxs-lookup"><span data-stu-id="f82fa-111">A string used to encrypt the encryption key.</span></span>  
  
 <span data-ttu-id="f82fa-112">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="f82fa-112">*HRESULT*</span></span>  
 <span data-ttu-id="f82fa-113">[out] 指出呼叫成功或失敗的值。</span><span class="sxs-lookup"><span data-stu-id="f82fa-113">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
 <span data-ttu-id="f82fa-114">*ExtendedErrors[]*</span><span class="sxs-lookup"><span data-stu-id="f82fa-114">*ExtendedErrors[]*</span></span>  
 <span data-ttu-id="f82fa-115">[out] 包含呼叫所傳回之其他錯誤的字串陣列。</span><span class="sxs-lookup"><span data-stu-id="f82fa-115">[out] A string array containing additional errors returned by the call.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f82fa-116">傳回值</span><span class="sxs-lookup"><span data-stu-id="f82fa-116">Return Value</span></span>  
 <span data-ttu-id="f82fa-117">傳回 *HRESULT* ，指出方法呼叫成功或失敗。</span><span class="sxs-lookup"><span data-stu-id="f82fa-117">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="f82fa-118">值為 0 表示方法呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="f82fa-118">A value of 0 indicates that the method call was successful.</span></span> <span data-ttu-id="f82fa-119">非零值則表示已發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="f82fa-119">A non-zero value indicates that an error has occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f82fa-120">備註</span><span class="sxs-lookup"><span data-stu-id="f82fa-120">Remarks</span></span>  
 <span data-ttu-id="f82fa-121">如果報表伺服器的項目已經存在報表伺服器資料庫中，就會刪除此項目。</span><span class="sxs-lookup"><span data-stu-id="f82fa-121">If an entry already exists for the report server in the report server database, it is deleted.</span></span> <span data-ttu-id="f82fa-122">然後，系統會使用指定的加密金鑰和報表伺服器的公開金鑰來建立新項目。</span><span class="sxs-lookup"><span data-stu-id="f82fa-122">The new entry is then created using the specified encryption key and the report server's public key.</span></span>  
  
 <span data-ttu-id="f82fa-123">在清除加密金鑰清單的 [DeleteEncryptionKey](configurationsetting-method-deleteencryptionkey.md) 方法之後呼叫此方法最有效。</span><span class="sxs-lookup"><span data-stu-id="f82fa-123">The method is most effective when called after the [DeleteEncryptionKey](configurationsetting-method-deleteencryptionkey.md) method, which clears the list of encryption keys.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f82fa-124">需求</span><span class="sxs-lookup"><span data-stu-id="f82fa-124">Requirements</span></span>  
 <span data-ttu-id="f82fa-125">**命名空間：** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f82fa-125">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f82fa-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f82fa-126">See Also</span></span>  
 [<span data-ttu-id="f82fa-127">MSReportServer_ConfigurationSetting 成員</span><span class="sxs-lookup"><span data-stu-id="f82fa-127">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
