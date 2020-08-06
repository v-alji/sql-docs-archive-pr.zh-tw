---
title: RemoveCertificate 方法 (SInstance 類別) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- RemoveCertificate Method (SInstance Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- RemoveCertificate method
ms.assetid: 7e5dbafa-a634-4617-9622-510514fce0ce
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 4b876cd75778d1da9c9a46f65f39b915ebee0552
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687634"
---
# <a name="removecertificate-method-sinstance-class"></a><span data-ttu-id="868a5-102">RemoveCertificate 方法 (SInstance 類別)</span><span class="sxs-lookup"><span data-stu-id="868a5-102">RemoveCertificate Method (SInstance Class)</span></span>
  <span data-ttu-id="868a5-103">從 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]執行個體中移除目前的安全性憑證。</span><span class="sxs-lookup"><span data-stu-id="868a5-103">Removes the current security certificate from the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="868a5-104">語法</span><span class="sxs-lookup"><span data-stu-id="868a5-104">Syntax</span></span>  
  
```  
  
object  
.RemoveCertificate()  
  
```  
  
## <a name="parts"></a><span data-ttu-id="868a5-105">組件</span><span class="sxs-lookup"><span data-stu-id="868a5-105">Parts</span></span>  
 <span data-ttu-id="868a5-106">*object*</span><span class="sxs-lookup"><span data-stu-id="868a5-106">*object*</span></span>  
 <span data-ttu-id="868a5-107">代表 [執行個體上之伺服器設定的](sinstance-class.md) SInstance 類別 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]物件。</span><span class="sxs-lookup"><span data-stu-id="868a5-107">An [SInstance Class](sinstance-class.md) object that represents the server settings on an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="868a5-108">屬性值/傳回值</span><span class="sxs-lookup"><span data-stu-id="868a5-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="868a5-109">uint32 值，如果已成功修改此服務為 0，如果不支援要求則為 1，以及其他指示錯誤的任何數字。</span><span class="sxs-lookup"><span data-stu-id="868a5-109">A uint32 value, which is 0 if the service was successfully modified, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="868a5-110">備註</span><span class="sxs-lookup"><span data-stu-id="868a5-110">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="868a5-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="868a5-111">See Also</span></span>  
 <span data-ttu-id="868a5-112">[設定伺服器網路通訊協定與網路程式庫](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span><span class="sxs-lookup"><span data-stu-id="868a5-112">[Configuring Server Network Protocols and Net-Libraries](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span></span>  
  
  
