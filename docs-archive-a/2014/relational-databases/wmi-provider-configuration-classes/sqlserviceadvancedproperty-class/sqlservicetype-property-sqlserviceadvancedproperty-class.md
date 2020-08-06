---
title: SqlServiceType 屬性 (SqlServiceAdvancedProperty 類別) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SqlServiceType Property (SqlServiceAdvancedProperty Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SqlServiceType property
ms.assetid: 20f1663a-9a14-4f14-8c1b-8aa133e272c3
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 774c8599fd21e330fa3228336ab1ed3c73d65c85
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606664"
---
# <a name="sqlservicetype-property-sqlserviceadvancedproperty-class"></a><span data-ttu-id="b2c2b-102">SqlServiceType 屬性 (SqlServiceAdvancedProperty 類別)</span><span class="sxs-lookup"><span data-stu-id="b2c2b-102">SqlServiceType Property (SqlServiceAdvancedProperty Class)</span></span>
  <span data-ttu-id="b2c2b-103">取得與進階屬性相關之受管理服務的類型。</span><span class="sxs-lookup"><span data-stu-id="b2c2b-103">Gets the type of the managed service associated with the advanced property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2c2b-104">語法</span><span class="sxs-lookup"><span data-stu-id="b2c2b-104">Syntax</span></span>  
  
```  
  
object  
.SetBoolValue(  
NumValue  
)  
  
```  
  
## <a name="parts"></a><span data-ttu-id="b2c2b-105">組件</span><span class="sxs-lookup"><span data-stu-id="b2c2b-105">Parts</span></span>  
 <span data-ttu-id="b2c2b-106">*object*</span><span class="sxs-lookup"><span data-stu-id="b2c2b-106">*object*</span></span>  
 <span data-ttu-id="b2c2b-107">代表進階屬性的 [SqlServiceAdvancedProperty 類別](sqlserviceadvancedproperty-class.md) 物件。</span><span class="sxs-lookup"><span data-stu-id="b2c2b-107">A [SqlServiceAdvancedProperty Class](sqlserviceadvancedproperty-class.md) object that represents an advanced property.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="b2c2b-108">屬性值/傳回值</span><span class="sxs-lookup"><span data-stu-id="b2c2b-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="b2c2b-109">指定 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 服務類型的 uint32 值。</span><span class="sxs-lookup"><span data-stu-id="b2c2b-109">A uint32 value that specifies the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Service type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b2c2b-110">備註</span><span class="sxs-lookup"><span data-stu-id="b2c2b-110">Remarks</span></span>  
 <span data-ttu-id="b2c2b-111">傳回值可以是下列其中一個：</span><span class="sxs-lookup"><span data-stu-id="b2c2b-111">Return values can be one of the following:</span></span>  
  
|<span data-ttu-id="b2c2b-112">類型</span><span class="sxs-lookup"><span data-stu-id="b2c2b-112">Type</span></span>|<span data-ttu-id="b2c2b-113">定義</span><span class="sxs-lookup"><span data-stu-id="b2c2b-113">Definition</span></span>|  
|----------|----------------|  
|<span data-ttu-id="b2c2b-114">*1*</span><span class="sxs-lookup"><span data-stu-id="b2c2b-114">*1*</span></span>|<span data-ttu-id="b2c2b-115">MSSQLSERVER 是 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 服務。</span><span class="sxs-lookup"><span data-stu-id="b2c2b-115">MSSQLSERVER is the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service.</span></span>|  
|<span data-ttu-id="b2c2b-116">*2*</span><span class="sxs-lookup"><span data-stu-id="b2c2b-116">*2*</span></span>|<span data-ttu-id="b2c2b-117">SQLSERVERAGENT 是 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent 服務。</span><span class="sxs-lookup"><span data-stu-id="b2c2b-117">SQLSERVERAGENT is the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent service.</span></span>|  
|<span data-ttu-id="b2c2b-118">*3*</span><span class="sxs-lookup"><span data-stu-id="b2c2b-118">*3*</span></span>|<span data-ttu-id="b2c2b-119">MSFTESQL 是 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 全文檢索搜尋引擎服務。</span><span class="sxs-lookup"><span data-stu-id="b2c2b-119">MSFTESQL is the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Full-text Search Engine service.</span></span>|  
|<span data-ttu-id="b2c2b-120">*4*</span><span class="sxs-lookup"><span data-stu-id="b2c2b-120">*4*</span></span>|<span data-ttu-id="b2c2b-121">MsDtsServer 是 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 服務。</span><span class="sxs-lookup"><span data-stu-id="b2c2b-121">MsDtsServer is the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] service.</span></span>|  
|<span data-ttu-id="b2c2b-122">*5*</span><span class="sxs-lookup"><span data-stu-id="b2c2b-122">*5*</span></span>|<span data-ttu-id="b2c2b-123">MSSQLServerOLAPService 是 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 服務。</span><span class="sxs-lookup"><span data-stu-id="b2c2b-123">MSSQLServerOLAPService is the [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] service.</span></span>|  
|<span data-ttu-id="b2c2b-124">*6*</span><span class="sxs-lookup"><span data-stu-id="b2c2b-124">*6*</span></span>|<span data-ttu-id="b2c2b-125">ReportServer 是 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 服務。</span><span class="sxs-lookup"><span data-stu-id="b2c2b-125">ReportServer is the [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] service.</span></span>|  
|<span data-ttu-id="b2c2b-126">*7*</span><span class="sxs-lookup"><span data-stu-id="b2c2b-126">*7*</span></span>|<span data-ttu-id="b2c2b-127">SQLBrowser 是 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Browser 服務。</span><span class="sxs-lookup"><span data-stu-id="b2c2b-127">SQLBrowser is the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Browser service.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b2c2b-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b2c2b-128">See Also</span></span>  
 <span data-ttu-id="b2c2b-129">[啟動及停止服務](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="b2c2b-129">[Starting and Stopping Services](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span></span>  
  
  
