---
title: DeleteEncryptionKey 方法 (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- DeleteEncryptionKey (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- DeleteEncryptionKey method
ms.assetid: ed2f25b6-6a63-468d-9279-a577ca01b096
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 0e302659615bd620b3b0ed802b83aafc4e9506d6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594922"
---
# <a name="deleteencryptionkey-method-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="9da6e-102">DeleteEncryptionKey 方法 (WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="9da6e-102">DeleteEncryptionKey Method (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="9da6e-103">從報表伺服器資料庫中刪除加密金鑰。</span><span class="sxs-lookup"><span data-stu-id="9da6e-103">Deletes the encryption keys from the report server database.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9da6e-104">語法</span><span class="sxs-lookup"><span data-stu-id="9da6e-104">Syntax</span></span>  
  
```vb  
Public Sub DeleteEncryptionKeys(ByVal InstallationID As String, _  
    ByRef HRESULT As Int32, ByRef ExtendedErrors() As String)  
```  
  
```csharp  
public void DeleteEncryptionKeys(string InstallationID, out Int32 HRESULT,   
    out string[] ExtendedErrors);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9da6e-105">參數</span><span class="sxs-lookup"><span data-stu-id="9da6e-105">Parameters</span></span>  
 <span data-ttu-id="9da6e-106">*InstallationID*</span><span class="sxs-lookup"><span data-stu-id="9da6e-106">*InstallationID*</span></span>  
 <span data-ttu-id="9da6e-107">位於報表伺服器資料庫之索引鍵資料表中的報表伺服器的安裝識別碼。</span><span class="sxs-lookup"><span data-stu-id="9da6e-107">The installation ID of a report server that is in the keys table of the report server database.</span></span>  
  
 <span data-ttu-id="9da6e-108">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="9da6e-108">*HRESULT*</span></span>  
 <span data-ttu-id="9da6e-109">[out] 指出呼叫成功或失敗的值。</span><span class="sxs-lookup"><span data-stu-id="9da6e-109">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
 <span data-ttu-id="9da6e-110">*ExtendedErrors[]*</span><span class="sxs-lookup"><span data-stu-id="9da6e-110">*ExtendedErrors[]*</span></span>  
 <span data-ttu-id="9da6e-111">[out] 包含呼叫所傳回之其他錯誤的字串陣列。</span><span class="sxs-lookup"><span data-stu-id="9da6e-111">[out] A string array containing additional errors returned by the call.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9da6e-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="9da6e-112">Return Value</span></span>  
 <span data-ttu-id="9da6e-113">傳回 HRESULT，指出方法呼叫成功或失敗。</span><span class="sxs-lookup"><span data-stu-id="9da6e-113">Returns an HRESULT indicating success or failure of the method call.</span></span> <span data-ttu-id="9da6e-114">值為 0 表示方法呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="9da6e-114">A value of 0 indicates that the method call was successful.</span></span> <span data-ttu-id="9da6e-115">非零值則表示已發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="9da6e-115">A non-zero value indicates that an error has occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9da6e-116">備註</span><span class="sxs-lookup"><span data-stu-id="9da6e-116">Remarks</span></span>  
 <span data-ttu-id="9da6e-117">*DeleteEncryptionKey* 方法會針對具有報表伺服器資料庫中安全資訊之存取權的任何報表伺服器，從索引鍵資料表中刪除項目。</span><span class="sxs-lookup"><span data-stu-id="9da6e-117">The *DeleteEncryptionKey* method deletes entries from the keys table for any report servers that have access to the secure information in the report server database.</span></span> <span data-ttu-id="9da6e-118">如果指定的 *InstallationID* 參數沒有對應至資料庫中的安裝識別碼，此方法就會傳回錯誤。</span><span class="sxs-lookup"><span data-stu-id="9da6e-118">If the *InstallationID* parameter specified does not correspond to an installation ID in the database, the method returns an error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9da6e-119">需求</span><span class="sxs-lookup"><span data-stu-id="9da6e-119">Requirements</span></span>  
 <span data-ttu-id="9da6e-120">**命名空間：** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9da6e-120">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9da6e-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9da6e-121">See Also</span></span>  
 [<span data-ttu-id="9da6e-122">MSReportServer_ConfigurationSetting 成員</span><span class="sxs-lookup"><span data-stu-id="9da6e-122">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
