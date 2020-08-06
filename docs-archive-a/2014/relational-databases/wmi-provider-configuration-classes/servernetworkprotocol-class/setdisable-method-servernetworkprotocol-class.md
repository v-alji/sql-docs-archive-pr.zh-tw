---
title: SetDisable 方法 (ServerNetworkProtocol 類別) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetDisable Method (ServerNetworkProtocol Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetDisable method
ms.assetid: 0ebbe0c5-07ad-4a76-a918-e379930adf71
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 3176227aba4de1e5aca1be35ec1f071a15caa49e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593897"
---
# <a name="setdisable-method-servernetworkprotocol-class"></a><span data-ttu-id="21989-102">SetDisable 方法 (ServerNetworkProtocol 類別)</span><span class="sxs-lookup"><span data-stu-id="21989-102">SetDisable Method (ServerNetworkProtocol Class)</span></span>
  <span data-ttu-id="21989-103">停用伺服器網路通訊協定。</span><span class="sxs-lookup"><span data-stu-id="21989-103">Disables the server network protocol.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21989-104">語法</span><span class="sxs-lookup"><span data-stu-id="21989-104">Syntax</span></span>  
  
```  
  
object  
.SetDisable()  
  
```  
  
## <a name="parts"></a><span data-ttu-id="21989-105">組件</span><span class="sxs-lookup"><span data-stu-id="21989-105">Parts</span></span>  
 <span data-ttu-id="21989-106">*object*</span><span class="sxs-lookup"><span data-stu-id="21989-106">*object*</span></span>  
 <span data-ttu-id="21989-107">[ServerNetworkProtocol 類別] ServerNetworkProtocol-class.md) 物件，表示實例所使用的網路通訊協定 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="21989-107">A [ServerNetworkProtocol Class]servernetworkprotocol-class.md) object that represents the network protocol used by the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="21989-108">屬性值/傳回值</span><span class="sxs-lookup"><span data-stu-id="21989-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="21989-109">uint32 值，如果已成功修改此服務為 0，如果不支援要求則為 1，以及其他指示錯誤的任何數字。</span><span class="sxs-lookup"><span data-stu-id="21989-109">A uint32 value, which is 0 if the service was successfully modified, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="21989-110">備註</span><span class="sxs-lookup"><span data-stu-id="21989-110">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21989-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="21989-111">See Also</span></span>  
 <span data-ttu-id="21989-112">[設定伺服器網路通訊協定與網路程式庫](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span><span class="sxs-lookup"><span data-stu-id="21989-112">[Configuring Server Network Protocols and Net-Libraries](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span></span>  
  
  
