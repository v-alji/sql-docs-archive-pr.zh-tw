---
title: DeleteEncryptedInformation 方法 (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- DeleteEncryptedInformation (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- DeleteEncryptedInformation method
ms.assetid: c14ed187-bdd9-4304-88e3-72072f03c21b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d00dc3e90816cd04c84f124cdc3d25a9ac122bba
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594929"
---
# <a name="deleteencryptedinformation-method-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="6d76a-102">DeleteEncryptedInformation 方法 (WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="6d76a-102">DeleteEncryptedInformation Method (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="6d76a-103">從報表伺服器資料庫中刪除加密的資訊。</span><span class="sxs-lookup"><span data-stu-id="6d76a-103">Deletes the encrypted information from the report server database.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d76a-104">語法</span><span class="sxs-lookup"><span data-stu-id="6d76a-104">Syntax</span></span>  
  
```vb  
Public Sub DeleteEncryptedInformation(ByRef HRESULT As Int32, ByRef ExtendedErrors() As String)  
```  
  
```csharp  
public void DeleteEncryptedInformation(out Int32 HRESULT, out string[] ExtendedErrors);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6d76a-105">參數</span><span class="sxs-lookup"><span data-stu-id="6d76a-105">Parameters</span></span>  
 <span data-ttu-id="6d76a-106">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="6d76a-106">*HRESULT*</span></span>  
 <span data-ttu-id="6d76a-107">[out] 指出呼叫成功或失敗的值。</span><span class="sxs-lookup"><span data-stu-id="6d76a-107">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
 <span data-ttu-id="6d76a-108">*ExtendedErrors[]*</span><span class="sxs-lookup"><span data-stu-id="6d76a-108">*ExtendedErrors[]*</span></span>  
 <span data-ttu-id="6d76a-109">[out] 包含呼叫所傳回之其他錯誤的字串陣列。</span><span class="sxs-lookup"><span data-stu-id="6d76a-109">[out] A string array containing additional errors returned by the call.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6d76a-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="6d76a-110">Return Value</span></span>  
 <span data-ttu-id="6d76a-111">傳回 *HRESULT* ，指出方法呼叫成功或失敗。</span><span class="sxs-lookup"><span data-stu-id="6d76a-111">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="6d76a-112">值為 0 表示方法呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="6d76a-112">A value of 0 indicates that the method call was successful.</span></span> <span data-ttu-id="6d76a-113">非零值則表示已發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="6d76a-113">A non-zero value indicates that an error has occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6d76a-114">備註</span><span class="sxs-lookup"><span data-stu-id="6d76a-114">Remarks</span></span>  
 <span data-ttu-id="6d76a-115">叫用這個方法時，就會刪除下列資料：</span><span class="sxs-lookup"><span data-stu-id="6d76a-115">When this method is invoked, the following data is deleted:</span></span>  
  
-   <span data-ttu-id="6d76a-116">已加密的資料來源資訊，包括使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="6d76a-116">Data source information that is encrypted, including user name and password.</span></span>  
  
-   <span data-ttu-id="6d76a-117">使用傳遞延伸模組介面加密的訂閱資料。</span><span class="sxs-lookup"><span data-stu-id="6d76a-117">Subscription data that is encrypted using the delivery extension interfaces.</span></span>  
  
-   <span data-ttu-id="6d76a-118">來自報表伺服器資料庫中索引鍵資料表的所有資訊。</span><span class="sxs-lookup"><span data-stu-id="6d76a-118">All the information from the keys table in the report server database.</span></span>  
  
 <span data-ttu-id="6d76a-119">叫用這個方法之後，使用者必須初始化使用報表伺服器資料庫的每部電腦。</span><span class="sxs-lookup"><span data-stu-id="6d76a-119">After this method is invoked, the user must initialize each computer that uses the report server database.</span></span>  
  
 <span data-ttu-id="6d76a-120">呼叫 DeleteEncryptedInformation 方法並不會影響報表伺服器組態檔。</span><span class="sxs-lookup"><span data-stu-id="6d76a-120">Calling the DeleteEncryptedInformation method does not affect the report server configuration file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d76a-121">需求</span><span class="sxs-lookup"><span data-stu-id="6d76a-121">Requirements</span></span>  
 <span data-ttu-id="6d76a-122">**命名空間：** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d76a-122">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d76a-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6d76a-123">See Also</span></span>  
 [<span data-ttu-id="6d76a-124">MSReportServer_ConfigurationSetting 成員</span><span class="sxs-lookup"><span data-stu-id="6d76a-124">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
