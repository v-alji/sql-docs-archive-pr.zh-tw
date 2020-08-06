---
title: SqlServiceType 屬性 (SqlService 類別) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SqlServiceType Property (SqlService Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SqlServiceType property
ms.assetid: dbff2968-3011-41d6-a141-52d814af0213
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 18e0fc741d19eefbb93dbcb7fb6fd4a221ce86d0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702557"
---
# <a name="sqlservicetype-property-sqlservice-class"></a><span data-ttu-id="34e57-102">SqlServiceType 屬性 (SqlService 類別)</span><span class="sxs-lookup"><span data-stu-id="34e57-102">SqlServiceType Property (SqlService Class)</span></span>
  <span data-ttu-id="34e57-103">取得受管理之服務的類型。</span><span class="sxs-lookup"><span data-stu-id="34e57-103">Gets the type of the managed service.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34e57-104">語法</span><span class="sxs-lookup"><span data-stu-id="34e57-104">Syntax</span></span>  
  
```  
  
object  
.SqlServiceType [= value]  
```  
  
## <a name="parts"></a><span data-ttu-id="34e57-105">組件</span><span class="sxs-lookup"><span data-stu-id="34e57-105">Parts</span></span>  
 <span data-ttu-id="34e57-106">*object*</span><span class="sxs-lookup"><span data-stu-id="34e57-106">*object*</span></span>  
 <span data-ttu-id="34e57-107">表示此服務的 [SqlService 類別](sqlservice-class.md) 物件。</span><span class="sxs-lookup"><span data-stu-id="34e57-107">A [SqlService Class](sqlservice-class.md) object that represents the service.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="34e57-108">屬性值/傳回值</span><span class="sxs-lookup"><span data-stu-id="34e57-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="34e57-109">指定 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 服務類型的 uint32 值。</span><span class="sxs-lookup"><span data-stu-id="34e57-109">A uint32 value that specifies the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="34e57-110">備註</span><span class="sxs-lookup"><span data-stu-id="34e57-110">Remarks</span></span>  
 <span data-ttu-id="34e57-111">傳回值可以是下列其中一個：</span><span class="sxs-lookup"><span data-stu-id="34e57-111">Return values can be one of the following:</span></span>  
  
|<span data-ttu-id="34e57-112">類型</span><span class="sxs-lookup"><span data-stu-id="34e57-112">Type</span></span>|<span data-ttu-id="34e57-113">定義</span><span class="sxs-lookup"><span data-stu-id="34e57-113">Definition</span></span>|  
|----------|----------------|  
|<span data-ttu-id="34e57-114">*1*</span><span class="sxs-lookup"><span data-stu-id="34e57-114">*1*</span></span>|<span data-ttu-id="34e57-115">MSSQLSERVER 是 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 服務。</span><span class="sxs-lookup"><span data-stu-id="34e57-115">MSSQLSERVER is the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service.</span></span>|  
|<span data-ttu-id="34e57-116">*2*</span><span class="sxs-lookup"><span data-stu-id="34e57-116">*2*</span></span>|<span data-ttu-id="34e57-117">SQLSERVERAGENT 是 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent 服務。</span><span class="sxs-lookup"><span data-stu-id="34e57-117">SQLSERVERAGENT is the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent service.</span></span>|  
|<span data-ttu-id="34e57-118">*3*</span><span class="sxs-lookup"><span data-stu-id="34e57-118">*3*</span></span>|<span data-ttu-id="34e57-119">MSFTESQL 是 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 全文檢索搜尋引擎服務。</span><span class="sxs-lookup"><span data-stu-id="34e57-119">MSFTESQL is the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Full-text Search Engine service.</span></span>|  
|<span data-ttu-id="34e57-120">*4*</span><span class="sxs-lookup"><span data-stu-id="34e57-120">*4*</span></span>|<span data-ttu-id="34e57-121">MsDtsServer 是 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 服務。</span><span class="sxs-lookup"><span data-stu-id="34e57-121">MsDtsServer is the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] service.</span></span>|  
|<span data-ttu-id="34e57-122">*5*</span><span class="sxs-lookup"><span data-stu-id="34e57-122">*5*</span></span>|<span data-ttu-id="34e57-123">MSSQLServerOLAPService 是 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 服務。</span><span class="sxs-lookup"><span data-stu-id="34e57-123">MSSQLServerOLAPService is the [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] service.</span></span>|  
|<span data-ttu-id="34e57-124">*6*</span><span class="sxs-lookup"><span data-stu-id="34e57-124">*6*</span></span>|<span data-ttu-id="34e57-125">ReportServer 是 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 服務。</span><span class="sxs-lookup"><span data-stu-id="34e57-125">ReportServer is the [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] service.</span></span>|  
|<span data-ttu-id="34e57-126">*7*</span><span class="sxs-lookup"><span data-stu-id="34e57-126">*7*</span></span>|<span data-ttu-id="34e57-127">SQLBrowser 是 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Browser 服務。</span><span class="sxs-lookup"><span data-stu-id="34e57-127">SQLBrowser is the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Browser service.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="34e57-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="34e57-128">See Also</span></span>  
 <span data-ttu-id="34e57-129">[啟動及停止服務](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="34e57-129">[Starting and Stopping Services](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span></span>  
  
  
