---
title: ExitCode 屬性 (SqlService 類別) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- ExitCode Property (SqlService Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- ExitCode property
ms.assetid: e6b8bff2-946f-4abe-bd50-1f7bb11fdddf
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: f7f5414afd8507a1fc9c592d6b8226692e9683a0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593881"
---
# <a name="exitcode-property-sqlservice-class"></a><span data-ttu-id="bafce-102">ExitCode 屬性 (SqlService 類別)</span><span class="sxs-lookup"><span data-stu-id="bafce-102">ExitCode Property (SqlService Class)</span></span>
  <span data-ttu-id="bafce-103">取得或設定 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Win32 錯誤碼，該錯誤碼會定義啟動和停止服務時所遇到的問題。</span><span class="sxs-lookup"><span data-stu-id="bafce-103">Gets or sets the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Win32 error code that defines problems encountered when starting and stopping the service.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bafce-104">語法</span><span class="sxs-lookup"><span data-stu-id="bafce-104">Syntax</span></span>  
  
```  
  
object  
.ExitCode [= value]  
```  
  
## <a name="parts"></a><span data-ttu-id="bafce-105">組件</span><span class="sxs-lookup"><span data-stu-id="bafce-105">Parts</span></span>  
 <span data-ttu-id="bafce-106">*object*</span><span class="sxs-lookup"><span data-stu-id="bafce-106">*object*</span></span>  
 <span data-ttu-id="bafce-107">表示此服務的 [SqlService 類別](sqlservice-class.md) 物件。</span><span class="sxs-lookup"><span data-stu-id="bafce-107">A [SqlService Class](sqlservice-class.md) object that represents the service.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="bafce-108">屬性值/傳回值</span><span class="sxs-lookup"><span data-stu-id="bafce-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="bafce-109">指定結束碼的 `uint32` 值。</span><span class="sxs-lookup"><span data-stu-id="bafce-109">A `uint32` value that specifies the exit code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bafce-110">備註</span><span class="sxs-lookup"><span data-stu-id="bafce-110">Remarks</span></span>  
 <span data-ttu-id="bafce-111">當錯誤對於此類別所代表的服務而言是唯一時，此屬性會設定為 ERROR_SERVICE_SPECIFIC_ERROR (1066)。</span><span class="sxs-lookup"><span data-stu-id="bafce-111">This property is set to ERROR_SERVICE_SPECIFIC_ERROR (1066) when the error is unique to the service represented by this class.</span></span> <span data-ttu-id="bafce-112">服務執行時會將此值設定為 NO_ERROR，並在正常結束後再將此值設定為 NO_ERROR。</span><span class="sxs-lookup"><span data-stu-id="bafce-112">The service sets this value to NO_ERROR when running, and again upon normal termination.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bafce-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bafce-113">See Also</span></span>  
 <span data-ttu-id="bafce-114">[啟動及停止服務](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="bafce-114">[Starting and Stopping Services](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span></span>  
  
  
