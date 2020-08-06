---
title: StartMode 屬性 (SqlService 類別) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- StartMode Property (SqlService Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- StartMode property
ms.assetid: c0c2c7f8-d4ae-44f2-ad8e-aecfcb7c2878
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: bafffcc3c8f82f69896d0a22e9b0a9060e04cd10
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702554"
---
# <a name="startmode-property-sqlservice-class"></a><span data-ttu-id="7493a-102">StartMode 屬性 (SqlService 類別)</span><span class="sxs-lookup"><span data-stu-id="7493a-102">StartMode Property (SqlService Class)</span></span>
  <span data-ttu-id="7493a-103">取得服務的啟動模式。</span><span class="sxs-lookup"><span data-stu-id="7493a-103">Gets the start mode of the service.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7493a-104">語法</span><span class="sxs-lookup"><span data-stu-id="7493a-104">Syntax</span></span>  
  
```  
  
object  
.StartMode [= value]  
```  
  
## <a name="parts"></a><span data-ttu-id="7493a-105">組件</span><span class="sxs-lookup"><span data-stu-id="7493a-105">Parts</span></span>  
 <span data-ttu-id="7493a-106">*object*</span><span class="sxs-lookup"><span data-stu-id="7493a-106">*object*</span></span>  
 <span data-ttu-id="7493a-107">表示此服務的 [SqlService 類別](sqlservice-class.md) 物件。</span><span class="sxs-lookup"><span data-stu-id="7493a-107">A [SqlService Class](sqlservice-class.md) object that represents the service.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="7493a-108">屬性值/傳回值</span><span class="sxs-lookup"><span data-stu-id="7493a-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="7493a-109">指定服務模式的 uint32 值。</span><span class="sxs-lookup"><span data-stu-id="7493a-109">A uint32 value that specifies the mode of the service.</span></span>  
  
 <span data-ttu-id="7493a-110">它可以是下列其中一個值。</span><span class="sxs-lookup"><span data-stu-id="7493a-110">Values can be one of the following.</span></span>  
  
 <span data-ttu-id="7493a-111">Boot</span><span class="sxs-lookup"><span data-stu-id="7493a-111">Boot</span></span>  
 <span data-ttu-id="7493a-112">值 = 0。</span><span class="sxs-lookup"><span data-stu-id="7493a-112">Value = 0.</span></span> <span data-ttu-id="7493a-113">由作業系統載入程式啟動的服務。</span><span class="sxs-lookup"><span data-stu-id="7493a-113">Service started by the operating system loader.</span></span> <span data-ttu-id="7493a-114">這個選項只對驅動程式服務有效。</span><span class="sxs-lookup"><span data-stu-id="7493a-114">This option is valid only for driver services.</span></span>  
  
 <span data-ttu-id="7493a-115">系統</span><span class="sxs-lookup"><span data-stu-id="7493a-115">System</span></span>  
 <span data-ttu-id="7493a-116">值 = 1。</span><span class="sxs-lookup"><span data-stu-id="7493a-116">Value = 1.</span></span> <span data-ttu-id="7493a-117">由 `IoInitSystem` 方法啟動的服務。</span><span class="sxs-lookup"><span data-stu-id="7493a-117">Service started by the `IoInitSystem` method.</span></span> <span data-ttu-id="7493a-118">這個選項只對驅動程式服務有效。</span><span class="sxs-lookup"><span data-stu-id="7493a-118">This option is valid only for driver services.</span></span>  
  
 <span data-ttu-id="7493a-119">自動</span><span class="sxs-lookup"><span data-stu-id="7493a-119">Automatic</span></span>  
 <span data-ttu-id="7493a-120">值 = 2。</span><span class="sxs-lookup"><span data-stu-id="7493a-120">Value = 2.</span></span> <span data-ttu-id="7493a-121">要由服務控制管理員在系統啟動期間自動啟動的服務。</span><span class="sxs-lookup"><span data-stu-id="7493a-121">Service to be started automatically by the service control manager during system startup.</span></span>  
  
 <span data-ttu-id="7493a-122">手動</span><span class="sxs-lookup"><span data-stu-id="7493a-122">Manual</span></span>  
 <span data-ttu-id="7493a-123">值 = 3。</span><span class="sxs-lookup"><span data-stu-id="7493a-123">Value = 3.</span></span> <span data-ttu-id="7493a-124">在處理序呼叫 `StartService` 方法時要由電腦管理員啟動的服務。</span><span class="sxs-lookup"><span data-stu-id="7493a-124">Service to be started by the Computer Manager when a process calls the `StartService` method.</span></span>  
  
 <span data-ttu-id="7493a-125">已停用</span><span class="sxs-lookup"><span data-stu-id="7493a-125">Disabled</span></span>  
 <span data-ttu-id="7493a-126">值 = 4。</span><span class="sxs-lookup"><span data-stu-id="7493a-126">Value = 4.</span></span> <span data-ttu-id="7493a-127">無法啟動服務。</span><span class="sxs-lookup"><span data-stu-id="7493a-127">Service cannot be started.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7493a-128">備註</span><span class="sxs-lookup"><span data-stu-id="7493a-128">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7493a-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7493a-129">See Also</span></span>  
 <span data-ttu-id="7493a-130">[啟動及停止服務](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="7493a-130">[Starting and Stopping Services](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span></span>  
  
  
