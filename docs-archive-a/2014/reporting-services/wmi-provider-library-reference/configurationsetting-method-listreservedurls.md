---
title: ListReservedURLs 方法 (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- ListReservedURLs method
ms.assetid: 32335af1-5eae-4420-a0ef-b1e8a3267166
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 7639741adb0c756961c4c6b63a3bffb627c4a89c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594909"
---
# <a name="listreservedurls-method-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="62436-102">ListReservedURLs 方法 (WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="62436-102">ListReservedURLs Method (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="62436-103">列出針對報表伺服器上所有應用程式保留的 URL。</span><span class="sxs-lookup"><span data-stu-id="62436-103">Lists URLs reserved for all applications on the report server.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62436-104">語法</span><span class="sxs-lookup"><span data-stu-id="62436-104">Syntax</span></span>  
  
```vb  
Public Sub ListReservedUrls(ByRef Application() as String, ByRef UrlString() as String, _  
    ByRef Account() as String, ByRef AccountSID() as String, _  
    ByRef length() as Int32, ByRef HRESULT as Int32)  
```  
  
```csharp  
public void ListReservedUrls(out string[] Application, out string[] UrlString,  
        out string[] Account, out string[] AccountSID,  
        out int[] Length, out int[] HRESULT);  
```  
  
## <a name="parameters"></a><span data-ttu-id="62436-105">參數</span><span class="sxs-lookup"><span data-stu-id="62436-105">Parameters</span></span>  
 <span data-ttu-id="62436-106">*Application[]*</span><span class="sxs-lookup"><span data-stu-id="62436-106">*Application[]*</span></span>  
 <span data-ttu-id="62436-107">[out] 具有 URL 保留項目的應用程式。</span><span class="sxs-lookup"><span data-stu-id="62436-107">[out] The applications that have URL reservations.</span></span>  
  
 <span data-ttu-id="62436-108">*UrlString[]*</span><span class="sxs-lookup"><span data-stu-id="62436-108">*UrlString[]*</span></span>  
 <span data-ttu-id="62436-109">[out] 已保留的 URL。</span><span class="sxs-lookup"><span data-stu-id="62436-109">[out] The URLs that are reserved.</span></span>  
  
 <span data-ttu-id="62436-110">*Account[]*</span><span class="sxs-lookup"><span data-stu-id="62436-110">*Account[]*</span></span>  
 <span data-ttu-id="62436-111">[out] 與 URL 保留項目之帳戶相關聯的帳戶名稱。</span><span class="sxs-lookup"><span data-stu-id="62436-111">[out] The account names associated with the account for the URL reservations.</span></span>  
  
 <span data-ttu-id="62436-112">*AccountSID[]*</span><span class="sxs-lookup"><span data-stu-id="62436-112">*AccountSID[]*</span></span>  
 <span data-ttu-id="62436-113">[out] 與 URL 保留項目之帳戶相關聯的帳戶 SID。</span><span class="sxs-lookup"><span data-stu-id="62436-113">[out] The account SIDs associated with the account for the URL reservations.</span></span>  
  
 <span data-ttu-id="62436-114">*長度*</span><span class="sxs-lookup"><span data-stu-id="62436-114">*Length*</span></span>  
 <span data-ttu-id="62436-115">[out] 此方法所傳回之陣列的長度。</span><span class="sxs-lookup"><span data-stu-id="62436-115">[out] The length of the arrays returned by the method.</span></span>  
  
 <span data-ttu-id="62436-116">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="62436-116">*HRESULT*</span></span>  
 <span data-ttu-id="62436-117">[out] 指出呼叫成功或失敗的值。</span><span class="sxs-lookup"><span data-stu-id="62436-117">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="62436-118">傳回值</span><span class="sxs-lookup"><span data-stu-id="62436-118">Return Value</span></span>  
 <span data-ttu-id="62436-119">傳回 *HRESULT* ，指出方法呼叫成功或失敗。</span><span class="sxs-lookup"><span data-stu-id="62436-119">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="62436-120">值為 0 表示方法呼叫成功。錯誤碼則表示呼叫不成功。</span><span class="sxs-lookup"><span data-stu-id="62436-120">A value of 0 indicates that the method call was successful; an error code indicates the call was not successful.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="62436-121">備註</span><span class="sxs-lookup"><span data-stu-id="62436-121">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="62436-122">需求</span><span class="sxs-lookup"><span data-stu-id="62436-122">Requirements</span></span>  
 <span data-ttu-id="62436-123">**命名空間：** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="62436-123">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62436-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="62436-124">See Also</span></span>  
 [<span data-ttu-id="62436-125">MSReportServer_ConfigurationSetting 成員</span><span class="sxs-lookup"><span data-stu-id="62436-125">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
