---
title: ISQLServerErrorInfo (OLE DB) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- ISQLServerErrorInfo interface
ms.assetid: a8323b5c-686a-4235-a8d2-bda43617b3a1
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 222349bcaa88058dea1d9c5302883667c22d4092
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709853"
---
# <a name="isqlservererrorinfo-ole-db"></a><span data-ttu-id="0cd47-102">ISQLServerErrorInfo (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="0cd47-102">ISQLServerErrorInfo (OLE DB)</span></span>
  <span data-ttu-id="0cd47-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供者會定義**ISQLServerErrorInfo**錯誤介面。</span><span class="sxs-lookup"><span data-stu-id="0cd47-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider defines the **ISQLServerErrorInfo** error interface.</span></span> <span data-ttu-id="0cd47-104">此介面會傳回來自 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 錯誤的詳細資料，包括其嚴重性和狀態。</span><span class="sxs-lookup"><span data-stu-id="0cd47-104">This interface returns details from a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error, including its severity and state.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0cd47-105">本節內容</span><span class="sxs-lookup"><span data-stu-id="0cd47-105">In This Section</span></span>  
  
|<span data-ttu-id="0cd47-106">方法</span><span class="sxs-lookup"><span data-stu-id="0cd47-106">Method</span></span>|<span data-ttu-id="0cd47-107">描述</span><span class="sxs-lookup"><span data-stu-id="0cd47-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0cd47-108">ISQLServerErrorInfo：： GetErrorInfo &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="0cd47-108">ISQLServerErrorInfo::GetErrorInfo &#40;OLE DB&#41;</span></span>](../../relational-databases/native-client-ole-db-interfaces/isqlservererrorinfo-geterrorinfo-ole-db.md)|<span data-ttu-id="0cd47-109">傳回 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 包含 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 錯誤詳細資料之 Native Client OLE DB 提供者 SSERRORINFO 結構的指標。</span><span class="sxs-lookup"><span data-stu-id="0cd47-109">Returns a pointer to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider SSERRORINFO structure that contains the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error details.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0cd47-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0cd47-110">See Also</span></span>  
 <span data-ttu-id="0cd47-111">[介面 &#40;OLE DB&#41;](../../../2014/database-engine/dev-guide/interfaces-ole-db.md) </span><span class="sxs-lookup"><span data-stu-id="0cd47-111">[Interfaces &#40;OLE DB&#41;](../../../2014/database-engine/dev-guide/interfaces-ole-db.md) </span></span>  
 [<span data-ttu-id="0cd47-112">SQL Server 錯誤詳細資料</span><span class="sxs-lookup"><span data-stu-id="0cd47-112">SQL Server Error Detail</span></span>](../../relational-databases/native-client-ole-db-errors/sql-server-error-detail.md)  
  
  
