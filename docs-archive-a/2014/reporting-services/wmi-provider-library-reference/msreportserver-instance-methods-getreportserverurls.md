---
title: GetReportServerUrls 方法 (WMI MSReportServer_Instance) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- GetReportServerUrls method
ms.assetid: 4865e32c-0114-465a-be8c-be223a7bc09e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f36a5ba10c05276cffabc155e5289d675db8dae7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702354"
---
# <a name="getreportserverurls-method-wmi-msreportserver_instance"></a><span data-ttu-id="3cf5d-102">GetReportServerUrls 方法 (WMI MSReportServer_Instance)</span><span class="sxs-lookup"><span data-stu-id="3cf5d-102">GetReportServerUrls Method (WMI MSReportServer_Instance)</span></span>
  <span data-ttu-id="3cf5d-103">傳回使用者可用來存取報表伺服器和報表管理員的 URL 清單。</span><span class="sxs-lookup"><span data-stu-id="3cf5d-103">Returns a list of URLs users can use to access the report server and report manager.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3cf5d-104">語法</span><span class="sxs-lookup"><span data-stu-id="3cf5d-104">Syntax</span></span>  
  
```vb  
Public Sub GetReportServerUrls (ByRef ApplicationName() As String, ByRef URLs()_  
    As String, ByRef Length As Int32, ByRef HRESULT As Int32)  
```  
  
```csharp  
public void GetReportServerUrls(out string[] applicationName,   
    out string[] URLs, out int length, out int HRESULT);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3cf5d-105">參數</span><span class="sxs-lookup"><span data-stu-id="3cf5d-105">Parameters</span></span>  
 <span data-ttu-id="3cf5d-106">*ApplicationName[]*</span><span class="sxs-lookup"><span data-stu-id="3cf5d-106">*ApplicationName[]*</span></span>  
 <span data-ttu-id="3cf5d-107">包含已安裝之應用程式的陣列。</span><span class="sxs-lookup"><span data-stu-id="3cf5d-107">An array that contains the applications that are installed.</span></span> <span data-ttu-id="3cf5d-108">值為 `ReportServerWebService` 或 `ReportManager`。</span><span class="sxs-lookup"><span data-stu-id="3cf5d-108">Values are either `ReportServerWebService` or `ReportManager`.</span></span>  
  
 <span data-ttu-id="3cf5d-109">*URLs[]*</span><span class="sxs-lookup"><span data-stu-id="3cf5d-109">*URLs[]*</span></span>  
 <span data-ttu-id="3cf5d-110">包含成功註冊之 URL 的陣列。</span><span class="sxs-lookup"><span data-stu-id="3cf5d-110">An array that contains the successfully registered Urls.</span></span>  
  
 <span data-ttu-id="3cf5d-111">*長度*</span><span class="sxs-lookup"><span data-stu-id="3cf5d-111">*Length*</span></span>  
 <span data-ttu-id="3cf5d-112">包含傳回之陣列長度的整數值。</span><span class="sxs-lookup"><span data-stu-id="3cf5d-112">An integer value that contains the length of the arrays returned.</span></span>  
  
 <span data-ttu-id="3cf5d-113">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="3cf5d-113">*HRESULT*</span></span>  
 <span data-ttu-id="3cf5d-114">表示成功的值或錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="3cf5d-114">A value that indicates success or an error code.</span></span>  
  
## <a name="return-values"></a><span data-ttu-id="3cf5d-115">傳回值</span><span class="sxs-lookup"><span data-stu-id="3cf5d-115">Return Values</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3cf5d-116">備註</span><span class="sxs-lookup"><span data-stu-id="3cf5d-116">Remarks</span></span>  
 <span data-ttu-id="3cf5d-117">WMI 管理物件所公開的方法是透過 InvokeMethod 函數呼叫的。</span><span class="sxs-lookup"><span data-stu-id="3cf5d-117">Methods exposed by WMI management objects are called through the InvokeMethod function.</span></span> <span data-ttu-id="3cf5d-118">如需詳細資訊，請參閱 [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework WMI 文件集中的＜針對管理物件執行方法＞。</span><span class="sxs-lookup"><span data-stu-id="3cf5d-118">For more information, please see "Executing Methods on Management Objects" in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework WMI documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3cf5d-119">需求</span><span class="sxs-lookup"><span data-stu-id="3cf5d-119">Requirements</span></span>  
 <span data-ttu-id="3cf5d-120">**命名空間：** [!INCLUDE[ssRSWMInmspc](../../includes/ssrswminmspc-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3cf5d-120">**Namespace:** [!INCLUDE[ssRSWMInmspc](../../includes/ssrswminmspc-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3cf5d-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3cf5d-121">See Also</span></span>  
 [<span data-ttu-id="3cf5d-122">MSReportServer_ConfigurationSetting 成員</span><span class="sxs-lookup"><span data-stu-id="3cf5d-122">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
