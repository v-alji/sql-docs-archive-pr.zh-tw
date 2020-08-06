---
title: SetDisable 方法 (ServerNetworkProtocolIPAddress 類別) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetDisable Method (ServerNetworkProtocolIPAddress Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetDisable method
ms.assetid: 7a7cc8cc-9fb8-4bf5-b483-2150d633ee10
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 9fbe928de1144c3065ddabb07bfd48606fdcea51
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687673"
---
# <a name="setdisable-method-servernetworkprotocolipaddress-class"></a><span data-ttu-id="0c18f-102">SetDisable 方法 (ServerNetworkProtocolIPAddress 類別)</span><span class="sxs-lookup"><span data-stu-id="0c18f-102">SetDisable Method (ServerNetworkProtocolIPAddress Class)</span></span>
  <span data-ttu-id="0c18f-103">停用 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="0c18f-103">Disables the IP address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c18f-104">語法</span><span class="sxs-lookup"><span data-stu-id="0c18f-104">Syntax</span></span>  
  
```  
  
object  
.SetDisable()  
  
```  
  
## <a name="parts"></a><span data-ttu-id="0c18f-105">組件</span><span class="sxs-lookup"><span data-stu-id="0c18f-105">Parts</span></span>  
 <span data-ttu-id="0c18f-106">*object*</span><span class="sxs-lookup"><span data-stu-id="0c18f-106">*object*</span></span>  
 <span data-ttu-id="0c18f-107">[ServerNetworkProtocolIPAdress 類別] servernetworkprotocolipaddress-class.md) 物件，代表實例上網路通訊協定的 IP 位址 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="0c18f-107">A [ServerNetworkProtocolIPAdress Class]servernetworkprotocolipaddress-class.md) object that represents an IP address for the network protocol on an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="0c18f-108">屬性值/傳回值</span><span class="sxs-lookup"><span data-stu-id="0c18f-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="0c18f-109">uint32 值，如果已成功修改此服務為 0，如果不支援要求則為 1，以及其他指示錯誤的任何數字。</span><span class="sxs-lookup"><span data-stu-id="0c18f-109">A uint32 value, which is 0 if the service was successfully modified, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0c18f-110">備註</span><span class="sxs-lookup"><span data-stu-id="0c18f-110">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c18f-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0c18f-111">See Also</span></span>  
 <span data-ttu-id="0c18f-112">[設定伺服器網路通訊協定與網路程式庫](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span><span class="sxs-lookup"><span data-stu-id="0c18f-112">[Configuring Server Network Protocols and Net-Libraries](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span></span>  
  
  
