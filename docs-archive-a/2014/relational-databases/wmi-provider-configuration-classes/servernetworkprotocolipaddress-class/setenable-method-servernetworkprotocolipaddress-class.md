---
title: SetEnable 方法 (ServerNetworkProtocolIPAddress 類別) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetEnable Method (ServerNetworkProtocolIPAddress Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetEnable method
ms.assetid: baa86deb-95dd-416f-b2c7-cec1dfb91ab4
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 5be9c30acacaedba320fd68363e531b178918271
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597031"
---
# <a name="setenable-method-servernetworkprotocolipaddress-class"></a><span data-ttu-id="e1a07-102">SetEnable 方法 (ServerNetworkProtocolIPAddress 類別)</span><span class="sxs-lookup"><span data-stu-id="e1a07-102">SetEnable Method (ServerNetworkProtocolIPAddress Class)</span></span>
  <span data-ttu-id="e1a07-103">啟用 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="e1a07-103">Enables the IP address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1a07-104">語法</span><span class="sxs-lookup"><span data-stu-id="e1a07-104">Syntax</span></span>  
  
```  
  
object  
.SetEnable()  
  
```  
  
## <a name="parts"></a><span data-ttu-id="e1a07-105">組件</span><span class="sxs-lookup"><span data-stu-id="e1a07-105">Parts</span></span>  
 <span data-ttu-id="e1a07-106">*object*</span><span class="sxs-lookup"><span data-stu-id="e1a07-106">*object*</span></span>  
 <span data-ttu-id="e1a07-107">代表實例上網路通訊協定之 IP 位址的[ServerNetworkProtocolIPAdress 類別](servernetworkprotocolipaddress-class.md)物件 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="e1a07-107">A [ServerNetworkProtocolIPAdress Class](servernetworkprotocolipaddress-class.md) object that represents an IP address for the network protocol on the instance of [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="e1a07-108">屬性值/傳回值</span><span class="sxs-lookup"><span data-stu-id="e1a07-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="e1a07-109">`uint32` 值，如果已成功修改此服務為 0，如果不支援要求則為 1，以及其他指示錯誤的任何數字。</span><span class="sxs-lookup"><span data-stu-id="e1a07-109">A `uint32` value, which is 0 if the service was successfully modified, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e1a07-110">備註</span><span class="sxs-lookup"><span data-stu-id="e1a07-110">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1a07-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e1a07-111">See Also</span></span>  
 <span data-ttu-id="e1a07-112">[設定伺服器網路通訊協定與網路程式庫](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span><span class="sxs-lookup"><span data-stu-id="e1a07-112">[Configuring Server Network Protocols and Net-Libraries](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span></span>  
  
  
