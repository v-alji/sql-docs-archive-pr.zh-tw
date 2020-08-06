---
title: InitializeReportServer 方法 (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- InitializeReportServer (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- InitializeReportServer method
ms.assetid: 0304acc2-1fd7-437b-94d9-1c1073dd3ca4
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c6a8e44a98320ca2c9add6a1b6eef9362eef7731
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594918"
---
# <a name="initializereportserver-method-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="25d35-102">InitializeReportServer 方法 (WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="25d35-102">InitializeReportServer Method (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="25d35-103">初始化指定的報表服務執行個體。</span><span class="sxs-lookup"><span data-stu-id="25d35-103">Initializes the specified report service instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25d35-104">語法</span><span class="sxs-lookup"><span data-stu-id="25d35-104">Syntax</span></span>  
  
```vb  
Public Sub InitializeReportServer(ByVal InstallationID As String, _  
    ByRef HRESULT As Int32, ByRef ExtendedErrors() As String)  
```  
  
```csharp  
public void InitializeReportServer(string InstallationID,   
    out Int32 HRESULT, out string[] ExtendedErrors);  
```  
  
## <a name="parameters"></a><span data-ttu-id="25d35-105">參數</span><span class="sxs-lookup"><span data-stu-id="25d35-105">Parameters</span></span>  
 <span data-ttu-id="25d35-106">*InstallationID*</span><span class="sxs-lookup"><span data-stu-id="25d35-106">*InstallationID*</span></span>  
 <span data-ttu-id="25d35-107">用來在傳回加密金鑰之前進行加密的字串。</span><span class="sxs-lookup"><span data-stu-id="25d35-107">A string used to encrypt the encryption key before it is returned.</span></span>  
  
 <span data-ttu-id="25d35-108">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="25d35-108">*HRESULT*</span></span>  
 <span data-ttu-id="25d35-109">[out] 指出呼叫成功或失敗的值。</span><span class="sxs-lookup"><span data-stu-id="25d35-109">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
 <span data-ttu-id="25d35-110">*ExtendedErrors[]*</span><span class="sxs-lookup"><span data-stu-id="25d35-110">*ExtendedErrors[]*</span></span>  
 <span data-ttu-id="25d35-111">[out] 包含呼叫所傳回之其他錯誤的字串陣列。</span><span class="sxs-lookup"><span data-stu-id="25d35-111">[out] A string array containing additional errors returned by the call.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="25d35-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="25d35-112">Return Value</span></span>  
 <span data-ttu-id="25d35-113">傳回 *HRESULT* ，指出方法呼叫成功或失敗。</span><span class="sxs-lookup"><span data-stu-id="25d35-113">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="25d35-114">值為 0 表示方法呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="25d35-114">A value of 0 indicates that the method call was successful.</span></span> <span data-ttu-id="25d35-115">非零值則表示已發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="25d35-115">A non-zero value indicates that an error has occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="25d35-116">備註</span><span class="sxs-lookup"><span data-stu-id="25d35-116">Remarks</span></span>  
 <span data-ttu-id="25d35-117">呼叫這個方法時，系統會使用 *InstallationID*所識別之報表伺服器的公開金鑰來加密存取報表伺服器資料庫安全資訊的加密金鑰。</span><span class="sxs-lookup"><span data-stu-id="25d35-117">When this method is called, the encryption key that accesses the report server database secure information is encrypted using the public key of the report server identified by *InstallationID*.</span></span>  
  
 <span data-ttu-id="25d35-118">所指定報表伺服器的公開金鑰必須已經事先寫入報表伺服器資料庫中。</span><span class="sxs-lookup"><span data-stu-id="25d35-118">The specified report server's public key must have previously been written into the report server database.</span></span>  
  
 <span data-ttu-id="25d35-119">您必須針對已經擁有安全資訊之存取權的報表伺服器呼叫 *InitializeReportServer* 方法，才能讓它解密加密金鑰。</span><span class="sxs-lookup"><span data-stu-id="25d35-119">The *InitializeReportServer* method must be called against a report server that already has access to the secure information so that it can decrypt the encryption key.</span></span> <span data-ttu-id="25d35-120">然後，所產生且已加密的加密金鑰密就會儲存在報表伺服器資料庫中。</span><span class="sxs-lookup"><span data-stu-id="25d35-120">The resulting encrypted encryption key is then stored in the report server database.</span></span>  
  
 <span data-ttu-id="25d35-121">如果在呼叫 InitializeReportServer 方法時，報表伺服器的[IsInitialized](configurationsetting-property-isinitialized.md)屬性設定為 `true` ，則方法會傳回成功，而不會嘗試加密加密金鑰。</span><span class="sxs-lookup"><span data-stu-id="25d35-121">If the report server's [IsInitialized](configurationsetting-property-isinitialized.md) property is set to `true` when the InitializeReportServer method is called, the method returns success without trying to encrypt the encryption key.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25d35-122">需求</span><span class="sxs-lookup"><span data-stu-id="25d35-122">Requirements</span></span>  
 <span data-ttu-id="25d35-123">**命名空間：** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="25d35-123">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25d35-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="25d35-124">See Also</span></span>  
 [<span data-ttu-id="25d35-125">MSReportServer_ConfigurationSetting 成員</span><span class="sxs-lookup"><span data-stu-id="25d35-125">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
