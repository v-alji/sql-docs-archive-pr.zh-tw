---
title: RemoveCertificate 方法 (ServerSettings 類別) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- RemoveCertificate Method (ServerSettings Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- RemoveCertificate method
ms.assetid: 9ffdbc39-93f5-48fb-859a-86a3ad545827
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 00731fab5c4bdec61848df93829dd5013a7454f5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687638"
---
# <a name="removecertificate-method-serversettings-class"></a><span data-ttu-id="1e30c-102">RemoveCertificate 方法 (ServerSettings 類別)</span><span class="sxs-lookup"><span data-stu-id="1e30c-102">RemoveCertificate Method (ServerSettings Class)</span></span>
  <span data-ttu-id="1e30c-103">從 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]執行個體中移除目前的安全性憑證。</span><span class="sxs-lookup"><span data-stu-id="1e30c-103">Removes the current security certificate from the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e30c-104">語法</span><span class="sxs-lookup"><span data-stu-id="1e30c-104">Syntax</span></span>  
  
```  
  
object  
.RemoveCertificate()  
  
```  
  
## <a name="parts"></a><span data-ttu-id="1e30c-105">組件</span><span class="sxs-lookup"><span data-stu-id="1e30c-105">Parts</span></span>  
 <span data-ttu-id="1e30c-106">*object*</span><span class="sxs-lookup"><span data-stu-id="1e30c-106">*object*</span></span>  
 <span data-ttu-id="1e30c-107">表示 [執行個體上之伺服器設定的](serversettings-class.md) ServerSettings 類別 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]物件。</span><span class="sxs-lookup"><span data-stu-id="1e30c-107">A [ServerSettings Class](serversettings-class.md) object that represents the server settings on an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="1e30c-108">屬性值/傳回值</span><span class="sxs-lookup"><span data-stu-id="1e30c-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="1e30c-109">u`int32` 值，如果已成功修改此服務為 0，如果不支援要求則為 1，以及其他指示錯誤的任何數字。</span><span class="sxs-lookup"><span data-stu-id="1e30c-109">A u`int32` value, which is 0 if the service was successfully modified, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1e30c-110">備註</span><span class="sxs-lookup"><span data-stu-id="1e30c-110">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e30c-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1e30c-111">See Also</span></span>  
 <span data-ttu-id="1e30c-112">[設定伺服器網路通訊協定與網路程式庫](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span><span class="sxs-lookup"><span data-stu-id="1e30c-112">[Configuring Server Network Protocols and Net-Libraries](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span></span>  
  
  
