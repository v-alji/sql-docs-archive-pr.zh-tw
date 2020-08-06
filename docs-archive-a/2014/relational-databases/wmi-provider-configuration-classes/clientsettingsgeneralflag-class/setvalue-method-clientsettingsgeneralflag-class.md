---
title: SetValue 方法 (ClientSettingsGeneralFlag 類別) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetValue Method (ClientSettingsGeneralFlag Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetValue method
ms.assetid: 34443689-a0e0-4668-a811-17532c6fd271
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: fffa44bd8743f96a43ca4d1787d8d2afaad5e6cc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687702"
---
# <a name="setvalue-method-clientsettingsgeneralflag-class"></a><span data-ttu-id="9a375-102">SetValue 方法 (ClientSettingsGeneralFlag 類別)</span><span class="sxs-lookup"><span data-stu-id="9a375-102">SetValue Method (ClientSettingsGeneralFlag Class)</span></span>
  <span data-ttu-id="9a375-103">設定參考之旗標的所有值。</span><span class="sxs-lookup"><span data-stu-id="9a375-103">Sets all the values of the referenced flag.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a375-104">語法</span><span class="sxs-lookup"><span data-stu-id="9a375-104">Syntax</span></span>  
  
```  
  
object  
.SetValue(  
Value  
)  
  
```  
  
## <a name="parts"></a><span data-ttu-id="9a375-105">組件</span><span class="sxs-lookup"><span data-stu-id="9a375-105">Parts</span></span>  
 <span data-ttu-id="9a375-106">*object*</span><span class="sxs-lookup"><span data-stu-id="9a375-106">*object*</span></span>  
 <span data-ttu-id="9a375-107">表示伺服器設定之一般旗標的 [ClientSettingsGeneralFlag 類別](clientsettingsgeneralflag-class.md) 物件。</span><span class="sxs-lookup"><span data-stu-id="9a375-107">A [ClientSettingsGeneralFlag Class](clientsettingsgeneralflag-class.md) object that represents a general flag for the server settings.</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="9a375-108">參數</span><span class="sxs-lookup"><span data-stu-id="9a375-108">Parameters</span></span>  
  
|<span data-ttu-id="9a375-109">參數</span><span class="sxs-lookup"><span data-stu-id="9a375-109">Parameter</span></span>|<span data-ttu-id="9a375-110">描述</span><span class="sxs-lookup"><span data-stu-id="9a375-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9a375-111">*ReplTest1*</span><span class="sxs-lookup"><span data-stu-id="9a375-111">*Value*</span></span>|<span data-ttu-id="9a375-112">指定旗標之值的布林值。</span><span class="sxs-lookup"><span data-stu-id="9a375-112">A Boolean value that specifies the value of the flag.</span></span>|  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="9a375-113">屬性值/傳回值</span><span class="sxs-lookup"><span data-stu-id="9a375-113">Property Value/Return Value</span></span>  
 <span data-ttu-id="9a375-114">`uint32` 值，如果已成功修改此服務為 0，如果不支援要求則為 1，以及其他指示錯誤的任何數字。</span><span class="sxs-lookup"><span data-stu-id="9a375-114">A `uint32` value, which is 0 if the service was successfully modified, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9a375-115">備註</span><span class="sxs-lookup"><span data-stu-id="9a375-115">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a375-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9a375-116">See Also</span></span>  
 [<span data-ttu-id="9a375-117">設定用戶端通訊協定</span><span class="sxs-lookup"><span data-stu-id="9a375-117">Configure Client Protocols</span></span>](https://technet.microsoft.com/library/ms181035.aspx)  
  
  
