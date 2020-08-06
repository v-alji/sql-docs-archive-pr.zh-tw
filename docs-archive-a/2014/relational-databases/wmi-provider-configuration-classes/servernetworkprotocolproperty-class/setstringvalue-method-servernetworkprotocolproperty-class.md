---
title: SetStringValue 方法 (ServerNetworkProtocolProperty 類別) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetStringValue Method (ServerNetworkProtocolProperty Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetStringValue method
ms.assetid: 0911df30-55f7-4fca-a1fb-01d2c91c1467
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 8eb4a27d700d801e3ca94362663c6d7feaa7dc86
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687665"
---
# <a name="setstringvalue-method-servernetworkprotocolproperty-class"></a><span data-ttu-id="da79d-102">SetStringValue 方法 (ServerNetworkProtocolProperty 類別)</span><span class="sxs-lookup"><span data-stu-id="da79d-102">SetStringValue Method (ServerNetworkProtocolProperty Class)</span></span>
  <span data-ttu-id="da79d-103">設定參考之屬性的字串值。</span><span class="sxs-lookup"><span data-stu-id="da79d-103">Sets the string value of the referenced property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da79d-104">語法</span><span class="sxs-lookup"><span data-stu-id="da79d-104">Syntax</span></span>  
  
```  
  
object  
.SetStringValue(  
StrValue  
)  
  
```  
  
## <a name="parts"></a><span data-ttu-id="da79d-105">組件</span><span class="sxs-lookup"><span data-stu-id="da79d-105">Parts</span></span>  
 <span data-ttu-id="da79d-106">*object*</span><span class="sxs-lookup"><span data-stu-id="da79d-106">*object*</span></span>  
 <span data-ttu-id="da79d-107">代表實例上網路通訊協定之屬性的[ServerNetworkProtocolProperty 類別](servernetworkprotocolproperty-class.md)物件 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="da79d-107">A [ServerNetworkProtocolProperty Class](servernetworkprotocolproperty-class.md) object that represents an attribute of the network protocol on the instance of [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="da79d-108">參數</span><span class="sxs-lookup"><span data-stu-id="da79d-108">Parameters</span></span>  
  
|<span data-ttu-id="da79d-109">參數</span><span class="sxs-lookup"><span data-stu-id="da79d-109">Parameter</span></span>|<span data-ttu-id="da79d-110">描述</span><span class="sxs-lookup"><span data-stu-id="da79d-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="da79d-111">*StrValue*</span><span class="sxs-lookup"><span data-stu-id="da79d-111">*StrValue*</span></span>|<span data-ttu-id="da79d-112">指定目前屬性之新值的字串值。</span><span class="sxs-lookup"><span data-stu-id="da79d-112">A string value that specifies the new value of the current property.</span></span>|  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="da79d-113">屬性值/傳回值</span><span class="sxs-lookup"><span data-stu-id="da79d-113">Property Value/Return Value</span></span>  
 <span data-ttu-id="da79d-114">`uint32` 值，如果已成功修改此服務為 0，如果不支援要求則為 1，以及其他指示錯誤的任何數字。</span><span class="sxs-lookup"><span data-stu-id="da79d-114">A `uint32` value, which is 0 if the service was successfully modified, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="da79d-115">備註</span><span class="sxs-lookup"><span data-stu-id="da79d-115">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da79d-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="da79d-116">See Also</span></span>  
 <span data-ttu-id="da79d-117">[設定伺服器網路通訊協定與網路程式庫](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span><span class="sxs-lookup"><span data-stu-id="da79d-117">[Configuring Server Network Protocols and Net-Libraries](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span></span>  
  
  
