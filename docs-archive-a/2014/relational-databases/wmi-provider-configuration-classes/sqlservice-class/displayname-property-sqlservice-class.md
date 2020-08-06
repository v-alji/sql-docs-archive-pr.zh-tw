---
title: DisplayName 屬性 (SqlService 類別) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- DisplayName Property (SqlService Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- DisplayName property
ms.assetid: 49c408aa-6eb4-45cd-8d5c-60f065f24f5c
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 147fc298d6d263caf1e4ad6852d4b02f86911572
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706317"
---
# <a name="displayname-property-sqlservice-class"></a><span data-ttu-id="dfcca-102">DisplayName 屬性 (SqlService 類別)</span><span class="sxs-lookup"><span data-stu-id="dfcca-102">DisplayName Property (SqlService Class)</span></span>
  <span data-ttu-id="dfcca-103">取得服務的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="dfcca-103">Gets the display name of the service.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dfcca-104">語法</span><span class="sxs-lookup"><span data-stu-id="dfcca-104">Syntax</span></span>  
  
```  
  
object  
.DisplayName [= value]  
```  
  
## <a name="parts"></a><span data-ttu-id="dfcca-105">組件</span><span class="sxs-lookup"><span data-stu-id="dfcca-105">Parts</span></span>  
 <span data-ttu-id="dfcca-106">*object*</span><span class="sxs-lookup"><span data-stu-id="dfcca-106">*object*</span></span>  
 <span data-ttu-id="dfcca-107">表示此服務的 [SqlService 類別](sqlservice-class.md) 物件。</span><span class="sxs-lookup"><span data-stu-id="dfcca-107">A [SqlService Class](sqlservice-class.md) object that represents the service.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="dfcca-108">屬性值/傳回值</span><span class="sxs-lookup"><span data-stu-id="dfcca-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="dfcca-109">指定此服務之顯示名稱的字串值。</span><span class="sxs-lookup"><span data-stu-id="dfcca-109">A string value that specifies the display name of the service.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dfcca-110">備註</span><span class="sxs-lookup"><span data-stu-id="dfcca-110">Remarks</span></span>  
 <span data-ttu-id="dfcca-111">這個字串的最大長度為 256 個字元。</span><span class="sxs-lookup"><span data-stu-id="dfcca-111">This string has a maximum length of 256 characters.</span></span> <span data-ttu-id="dfcca-112">此名稱在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 組態管理員中有保留大小寫。</span><span class="sxs-lookup"><span data-stu-id="dfcca-112">The name is case-preserved in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Configuration Manager.</span></span> <span data-ttu-id="dfcca-113">不過，顯示名稱比較一定不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="dfcca-113">However, display name comparisons are always case-insensitive.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dfcca-114">範例</span><span class="sxs-lookup"><span data-stu-id="dfcca-114">Example</span></span>  
  
```  
mysqlservice.DisplayName = "Atdisk"  
```  
  
## <a name="see-also"></a><span data-ttu-id="dfcca-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dfcca-115">See Also</span></span>  
 <span data-ttu-id="dfcca-116">[啟動及停止服務](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="dfcca-116">[Starting and Stopping Services](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span></span>  
  
  
