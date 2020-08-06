---
title: SetEnable 方法 (ClientNetworkProtocol 類別) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetEnable Method (ClientNetworkProtocol Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetEnable method
ms.assetid: a66c756a-1311-4f4a-8088-818f8ed90056
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: dfba695506dd04ded82083b85bfbb751913fbcbb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606100"
---
# <a name="setenable-method-clientnetworkprotocol-class"></a><span data-ttu-id="03224-102">SetEnable 方法 (ClientNetworkProtocol 類別)</span><span class="sxs-lookup"><span data-stu-id="03224-102">SetEnable Method (ClientNetworkProtocol Class)</span></span>
  <span data-ttu-id="03224-103">啟用[設定用戶端通訊協定](https://technet.microsoft.com/library/ms181035.aspx)所指定的用戶端網路通訊協定。</span><span class="sxs-lookup"><span data-stu-id="03224-103">Enables the client network protocol that is specified by the [Configure Client Protocols](https://technet.microsoft.com/library/ms181035.aspx).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03224-104">語法</span><span class="sxs-lookup"><span data-stu-id="03224-104">Syntax</span></span>  
  
```  
  
object  
.SetEnableMethod()  
  
```  
  
## <a name="parts"></a><span data-ttu-id="03224-105">組件</span><span class="sxs-lookup"><span data-stu-id="03224-105">Parts</span></span>  
 <span data-ttu-id="03224-106">*object*</span><span class="sxs-lookup"><span data-stu-id="03224-106">*object*</span></span>  
 <span data-ttu-id="03224-107">代表用戶端所使用之網路通訊協定的[ClientNetworkProtocol 類別](clientnetworkprotocol-class.md)物件 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="03224-107">A [ClientNetworkProtocol Class](clientnetworkprotocol-class.md) object that represents the network protocol used by the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] client.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="03224-108">屬性值/傳回值</span><span class="sxs-lookup"><span data-stu-id="03224-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="03224-109">`uint32` 值，如果已成功修改此服務為 0，如果不支援要求則為 1，以及其他指示錯誤的任何數字。</span><span class="sxs-lookup"><span data-stu-id="03224-109">A `uint32` value, which is 0 if the service was successfully modified, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="03224-110">備註</span><span class="sxs-lookup"><span data-stu-id="03224-110">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03224-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="03224-111">See Also</span></span>  
 [<span data-ttu-id="03224-112">設定用戶端網路通訊協定和網路程式庫</span><span class="sxs-lookup"><span data-stu-id="03224-112">Configuring Client Network Protocols and Net-Libraries</span></span>](https://technet.microsoft.com/library/ms181035.aspx)  
  
  
