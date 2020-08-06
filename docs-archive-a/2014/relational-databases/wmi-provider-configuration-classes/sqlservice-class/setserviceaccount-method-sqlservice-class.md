---
title: SetServiceAccount 方法 (SqlService 類別) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetServiceAccount Method (SqlService Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetServiceAccount method
ms.assetid: d5782892-e9d8-4d48-92af-b3afe9610f84
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 6087a531802a7752ea794a44147c79fb7c3fa3ad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687594"
---
# <a name="setserviceaccount-method-sqlservice-class"></a><span data-ttu-id="0ebc3-102">SetServiceAccount 方法 (SqlService 類別)</span><span class="sxs-lookup"><span data-stu-id="0ebc3-102">SetServiceAccount Method (SqlService Class)</span></span>
  <span data-ttu-id="0ebc3-103">嘗試變更服務執行個體執行時所使用的使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="0ebc3-103">Attempts to change the user name and password that the service instance runs under.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ebc3-104">語法</span><span class="sxs-lookup"><span data-stu-id="0ebc3-104">Syntax</span></span>  
  
```  
  
object  
.SetServiceAccount(  
ServiceStartName , ServiceStartPassword  
)  
  
```  
  
## <a name="parts"></a><span data-ttu-id="0ebc3-105">組件</span><span class="sxs-lookup"><span data-stu-id="0ebc3-105">Parts</span></span>  
 <span data-ttu-id="0ebc3-106">*object*</span><span class="sxs-lookup"><span data-stu-id="0ebc3-106">*object*</span></span>  
 <span data-ttu-id="0ebc3-107">表示此服務的 [SqlService 類別](sqlservice-class.md) 物件。</span><span class="sxs-lookup"><span data-stu-id="0ebc3-107">A [SqlService Class](sqlservice-class.md) object that represents the service.</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="0ebc3-108">參數</span><span class="sxs-lookup"><span data-stu-id="0ebc3-108">Parameters</span></span>  
 <span data-ttu-id="0ebc3-109">*ServiceStartName*</span><span class="sxs-lookup"><span data-stu-id="0ebc3-109">*ServiceStartName*</span></span>  
 <span data-ttu-id="0ebc3-110">指定此服務執行時所使用之帳戶名稱的字串值。</span><span class="sxs-lookup"><span data-stu-id="0ebc3-110">A string value that specifies the account name that the service runs under.</span></span> <span data-ttu-id="0ebc3-111">根據服務類型而定，此帳戶名稱可能是 DomainName\Username 的格式。</span><span class="sxs-lookup"><span data-stu-id="0ebc3-111">Depending on the service type, the account name might be in the form of DomainName\Username.</span></span> <span data-ttu-id="0ebc3-112">當它執行時，將會使用兩種格式的其中一種來記錄服務處理序：</span><span class="sxs-lookup"><span data-stu-id="0ebc3-112">When it runs, the service process will be logged using one of two forms:</span></span>  
  
-   <span data-ttu-id="0ebc3-113">如果帳戶屬於內建網域，可以指定 \Username。</span><span class="sxs-lookup"><span data-stu-id="0ebc3-113">If the account belongs to the built-in domain, \Username can be specified.</span></span>  
  
-   <span data-ttu-id="0ebc3-114">如果指定了 Null，服務就會以**LocalSystem**帳戶的身分登入。</span><span class="sxs-lookup"><span data-stu-id="0ebc3-114">If NULL is specified, the service will be logged on as the **LocalSystem** account.</span></span>  
  
 <span data-ttu-id="0ebc3-115">若是核心或系統層級的驅動程式， *StartName*會包含驅動程式物件名稱（\FileSystem\Rdr 或 \driver\xns) ），以供 i/o 系統用來載入設備磁碟機。</span><span class="sxs-lookup"><span data-stu-id="0ebc3-115">For kernel or system-level drivers, *StartName* contains the driver object name, either \FileSystem\Rdr or \Driver\Xns, which the I/O system uses to load the device driver.</span></span> <span data-ttu-id="0ebc3-116">如果指定了 NULL，將會根據類似 DWDOM\Admin 的服務名稱，使用 I/O 系統所建立的預設物件名稱來執行驅動程式。</span><span class="sxs-lookup"><span data-stu-id="0ebc3-116">If NULL is specified, the driver runs with a default object name created by the I/O system based on the service name, for example, DWDOM\Admin.</span></span>  
  
 <span data-ttu-id="0ebc3-117">*ServiceStartPassword*</span><span class="sxs-lookup"><span data-stu-id="0ebc3-117">*ServiceStartPassword*</span></span>  
 <span data-ttu-id="0ebc3-118">字串值，指定*StartName*參數中帳戶名稱的密碼。</span><span class="sxs-lookup"><span data-stu-id="0ebc3-118">A string value that specifies the password for the account name in the *StartName* parameter.</span></span> <span data-ttu-id="0ebc3-119">如果您不要變更密碼，請指定 NULL。</span><span class="sxs-lookup"><span data-stu-id="0ebc3-119">Specify NULL if you are not changing the password.</span></span> <span data-ttu-id="0ebc3-120">如果此服務沒有密碼，請指定空字串。</span><span class="sxs-lookup"><span data-stu-id="0ebc3-120">Specify an empty string if the service has no password.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="0ebc3-121">屬性值/傳回值</span><span class="sxs-lookup"><span data-stu-id="0ebc3-121">Property Value/Return Value</span></span>  
 <span data-ttu-id="0ebc3-122">`uint32` 值，如果已成功修改此服務為 0，如果不支援要求則為 1。</span><span class="sxs-lookup"><span data-stu-id="0ebc3-122">A `uint32` value, which is 0 if the service was successfully modified or 1 if the request is not supported.</span></span> <span data-ttu-id="0ebc3-123">任何其他數字表示發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="0ebc3-123">Any other number indicates an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0ebc3-124">備註</span><span class="sxs-lookup"><span data-stu-id="0ebc3-124">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ebc3-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0ebc3-125">See Also</span></span>  
 <span data-ttu-id="0ebc3-126">[啟動及停止服務](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="0ebc3-126">[Starting and Stopping Services](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span></span>  
  
  
