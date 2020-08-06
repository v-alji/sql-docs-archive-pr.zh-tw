---
title: SetStartMode 方法 (SqlService 類別) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetStartMode Method (SqlService Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetStartMode method
ms.assetid: f6f198b4-f9a4-468c-8977-76462ef06e61
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: a9b7310623f526d7b106485ed9681df3aa100129
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585197"
---
# <a name="setstartmode-method-sqlservice-class"></a><span data-ttu-id="71813-102">SetStartMode 方法 (SqlService 類別)</span><span class="sxs-lookup"><span data-stu-id="71813-102">SetStartMode Method (SqlService Class)</span></span>
  <span data-ttu-id="71813-103">修改服務執行個體的啟動模式。</span><span class="sxs-lookup"><span data-stu-id="71813-103">Modifies the start mode of the service instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71813-104">語法</span><span class="sxs-lookup"><span data-stu-id="71813-104">Syntax</span></span>  
  
```  
  
object  
.SetStartMode(  
StartMode  
)  
  
```  
  
## <a name="parts"></a><span data-ttu-id="71813-105">組件</span><span class="sxs-lookup"><span data-stu-id="71813-105">Parts</span></span>  
 <span data-ttu-id="71813-106">*object*</span><span class="sxs-lookup"><span data-stu-id="71813-106">*object*</span></span>  
 <span data-ttu-id="71813-107">表示此服務的 [SqlService 類別](sqlservice-class.md) 物件。</span><span class="sxs-lookup"><span data-stu-id="71813-107">A [SqlService Class](sqlservice-class.md) object that represents the service.</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="71813-108">參數</span><span class="sxs-lookup"><span data-stu-id="71813-108">Parameters</span></span>  
 <span data-ttu-id="71813-109">*StartMode*</span><span class="sxs-lookup"><span data-stu-id="71813-109">*StartMode*</span></span>  
 <span data-ttu-id="71813-110">指定服務執行個體之啟動模式的 `uint32` 值。</span><span class="sxs-lookup"><span data-stu-id="71813-110">A `uint32` value that specifies the start mode of the service instance.</span></span>  
  
 <span data-ttu-id="71813-111">有效值如下：</span><span class="sxs-lookup"><span data-stu-id="71813-111">The valid values are as follows:</span></span>  
  
 <span data-ttu-id="71813-112">值 = 0。</span><span class="sxs-lookup"><span data-stu-id="71813-112">Value = 0.</span></span> <span data-ttu-id="71813-113">Boot - 由作業系統載入程式啟動的裝置驅動程式。</span><span class="sxs-lookup"><span data-stu-id="71813-113">Boot - Device driver started by the operating system loader.</span></span> <span data-ttu-id="71813-114">這個值只適用於驅動程式服務。</span><span class="sxs-lookup"><span data-stu-id="71813-114">This value is valid only for driver services.</span></span>  
  
 <span data-ttu-id="71813-115">值 = 1。</span><span class="sxs-lookup"><span data-stu-id="71813-115">Value = 1.</span></span> <span data-ttu-id="71813-116">System - 由 `IoInitSystem` 方法啟動的裝置驅動程式。</span><span class="sxs-lookup"><span data-stu-id="71813-116">System - Device driver started by the `IoInitSystem` method.</span></span> <span data-ttu-id="71813-117">這個值只適用於驅動程式服務。</span><span class="sxs-lookup"><span data-stu-id="71813-117">This value is valid only for driver services.</span></span>  
  
 <span data-ttu-id="71813-118">值 = 2。</span><span class="sxs-lookup"><span data-stu-id="71813-118">Value = 2.</span></span> <span data-ttu-id="71813-119">Automatic - 要由服務控制管理員在系統啟動期間自動啟動的服務。</span><span class="sxs-lookup"><span data-stu-id="71813-119">Automatic - Service to be started automatically by the service control manager during system startup.</span></span>  
  
 <span data-ttu-id="71813-120">值 = 3。</span><span class="sxs-lookup"><span data-stu-id="71813-120">Value = 3.</span></span> <span data-ttu-id="71813-121">Manual - 在處理序呼叫 `StartService` 方法時要由電腦管理員啟動的服務。</span><span class="sxs-lookup"><span data-stu-id="71813-121">Manual - Service to be started by the Computer Manager when a process calls the `StartService` method.</span></span>  
  
 <span data-ttu-id="71813-122">值 = 4。</span><span class="sxs-lookup"><span data-stu-id="71813-122">Value = 4.</span></span> <span data-ttu-id="71813-123">Disabled - 無法再啟動服務。</span><span class="sxs-lookup"><span data-stu-id="71813-123">Disabled - Service can no longer be started.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="71813-124">屬性值/傳回值</span><span class="sxs-lookup"><span data-stu-id="71813-124">Property Value/Return Value</span></span>  
 <span data-ttu-id="71813-125">`uint32` 值，如果已成功修改此服務為 0，如果不支援要求則為 1。</span><span class="sxs-lookup"><span data-stu-id="71813-125">A `uint32` value, which is 0 if the service was successfully modified or 1 if the request is not supported.</span></span> <span data-ttu-id="71813-126">任何其他數字表示發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="71813-126">Any other number indicates an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="71813-127">備註</span><span class="sxs-lookup"><span data-stu-id="71813-127">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71813-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="71813-128">See Also</span></span>  
 <span data-ttu-id="71813-129">[啟動及停止服務](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="71813-129">[Starting and Stopping Services](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span></span>  
  
  
