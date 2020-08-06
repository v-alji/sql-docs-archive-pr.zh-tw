---
title: ReencryptSecureInformation 方法 (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- ReencryptSecureInformation (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- ReencryptSecureInformation method
ms.assetid: 8a487497-c207-45b2-8c92-87c58cc68716
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 1a0c657b69d624df8895ae4d5a6d12277b011b24
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598202"
---
# <a name="reencryptsecureinformation-method-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="7765b-102">ReencryptSecureInformation 方法 (WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="7765b-102">ReencryptSecureInformation Method (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="7765b-103">產生新的加密金鑰，並且使用這個新的金鑰來重新加密目錄中的所有安全資訊。</span><span class="sxs-lookup"><span data-stu-id="7765b-103">Generates a new encryption key and re-encrypts all secure information in the catalog using this new key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7765b-104">語法</span><span class="sxs-lookup"><span data-stu-id="7765b-104">Syntax</span></span>  
  
```vb  
Public Sub ReencryptSecureInformation(ByRef HRESULT as Int32, ByRef ExtendedErrors() As String)  
```  
  
```csharp  
public void ReencryptSecureInformation (out Int32 HRESULT, out string[] ExtendedErrors);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7765b-105">參數</span><span class="sxs-lookup"><span data-stu-id="7765b-105">Parameters</span></span>  
 <span data-ttu-id="7765b-106">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="7765b-106">*HRESULT*</span></span>  
 <span data-ttu-id="7765b-107">[out] 指出呼叫成功或失敗的值。</span><span class="sxs-lookup"><span data-stu-id="7765b-107">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
 <span data-ttu-id="7765b-108">*ExtendedErrors[]*</span><span class="sxs-lookup"><span data-stu-id="7765b-108">*ExtendedErrors[]*</span></span>  
 <span data-ttu-id="7765b-109">[out] 包含呼叫所傳回之其他錯誤的字串陣列。</span><span class="sxs-lookup"><span data-stu-id="7765b-109">[out] A string array containing additional errors returned by the call.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7765b-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="7765b-110">Return Value</span></span>  
 <span data-ttu-id="7765b-111">傳回 *HRESULT* ，指出方法呼叫成功或失敗。</span><span class="sxs-lookup"><span data-stu-id="7765b-111">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="7765b-112">值為 0 表示方法呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="7765b-112">A value of 0 indicates that the method call was successful.</span></span> <span data-ttu-id="7765b-113">非零值則表示已發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="7765b-113">A non-zero value indicates that an error has occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7765b-114">備註</span><span class="sxs-lookup"><span data-stu-id="7765b-114">Remarks</span></span>  
 <span data-ttu-id="7765b-115">ReencryptSecureInformation 方法可讓管理員將現有的加密金鑰取代成新的金鑰。</span><span class="sxs-lookup"><span data-stu-id="7765b-115">The ReencryptSecureInformation method allows the administrator to replace the existing encryption key with a new key.</span></span>  
  
 <span data-ttu-id="7765b-116">叫用這個方法時，報表伺服器就會產生新的加密金鑰，並且逐一查看所有加密的內容，以便使用新的加密金鑰來重新加密內容。</span><span class="sxs-lookup"><span data-stu-id="7765b-116">When this method is invoked, the report server generates a new encryption key and iterates through all encrypted content to re-encrypt it with the new encryption key.</span></span>  
  
 <span data-ttu-id="7765b-117">傳遞延伸模組可以將安全資訊儲存在其傳遞設定結構中。</span><span class="sxs-lookup"><span data-stu-id="7765b-117">Delivery extensions can store secured information in their delivery settings structures.</span></span> <span data-ttu-id="7765b-118">呼叫 ReencryptSecureInformation 時，報表伺服器就會載入每個訂閱和對應的傳遞延伸模組，以便重新加密儲存在相關聯設定中的資訊。</span><span class="sxs-lookup"><span data-stu-id="7765b-118">When ReencryptSecureInformation is called, the report server loads each subscription and the corresponding delivery extension to re-encrypt information stored in the associated settings.</span></span>  
  
 <span data-ttu-id="7765b-119">如果這個方法是在向外延展部署中的電腦上執行，則向外延展部署中的每部電腦都必須再次初始化。</span><span class="sxs-lookup"><span data-stu-id="7765b-119">If this method is run on a computer in a scale-out deployment, each computer in the scale-out deployment will need to be initialized again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7765b-120">需求</span><span class="sxs-lookup"><span data-stu-id="7765b-120">Requirements</span></span>  
 <span data-ttu-id="7765b-121">**命名空間：** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7765b-121">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7765b-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7765b-122">See Also</span></span>  
 [<span data-ttu-id="7765b-123">MSReportServer_ConfigurationSetting 成員</span><span class="sxs-lookup"><span data-stu-id="7765b-123">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
