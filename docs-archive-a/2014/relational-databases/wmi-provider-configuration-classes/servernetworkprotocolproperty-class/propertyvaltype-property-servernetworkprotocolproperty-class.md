---
title: PropertyValType 屬性 (ServerNetworkProtocolProperty 類別) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- PropertyValType Property (ServerNetworkProtocolProperty Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- PropertyValType property
ms.assetid: fbd42e8e-0642-4a19-b3c8-6ce88345145f
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: be6c42fbaa36080ec8144d95abb045a3b4328057
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707314"
---
# <a name="propertyvaltype-property-servernetworkprotocolproperty-class"></a><span data-ttu-id="1a015-102">PropertyValType 屬性 (ServerNetworkProtocolProperty 類別)</span><span class="sxs-lookup"><span data-stu-id="1a015-102">PropertyValType Property (ServerNetworkProtocolProperty Class)</span></span>
  <span data-ttu-id="1a015-103">取得儲存於參考之屬性內之值的資料類型。</span><span class="sxs-lookup"><span data-stu-id="1a015-103">Gets the data type of the value stored in the referenced property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a015-104">語法</span><span class="sxs-lookup"><span data-stu-id="1a015-104">Syntax</span></span>  
  
```  
  
object  
.PropertyValType [= value]  
```  
  
## <a name="parts"></a><span data-ttu-id="1a015-105">組件</span><span class="sxs-lookup"><span data-stu-id="1a015-105">Parts</span></span>  
 <span data-ttu-id="1a015-106">*object*</span><span class="sxs-lookup"><span data-stu-id="1a015-106">*object*</span></span>  
 <span data-ttu-id="1a015-107">代表實例上網路通訊協定之屬性的[ServerNetworkProtocolProperty 類別](servernetworkprotocolproperty-class.md)物件 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="1a015-107">A [ServerNetworkProtocolProperty Class](servernetworkprotocolproperty-class.md) object that represents an attribute of the network protocol on the instance of [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="1a015-108">屬性值/傳回值</span><span class="sxs-lookup"><span data-stu-id="1a015-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="1a015-109">指定屬性值之資料類型的 `uint32` 值。</span><span class="sxs-lookup"><span data-stu-id="1a015-109">A `uint32` value that specifies the data type of the property value.</span></span> <span data-ttu-id="1a015-110">如果是字串值，它會傳回 0，如果是數值類型則傳回 1。</span><span class="sxs-lookup"><span data-stu-id="1a015-110">It returns 0 for a string value and 1 for a numerical type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1a015-111">備註</span><span class="sxs-lookup"><span data-stu-id="1a015-111">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a015-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1a015-112">See Also</span></span>  
 <span data-ttu-id="1a015-113">[設定伺服器網路通訊協定與網路程式庫](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span><span class="sxs-lookup"><span data-stu-id="1a015-113">[Configuring Server Network Protocols and Net-Libraries](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span></span>  
  
  
