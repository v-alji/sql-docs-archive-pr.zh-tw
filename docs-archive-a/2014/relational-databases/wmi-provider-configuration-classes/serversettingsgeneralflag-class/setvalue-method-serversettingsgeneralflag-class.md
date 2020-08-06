---
title: SetValue 方法 (ServerSettingsGeneralFlag 類別) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetValue Method (ServerSettingsGeneralFlag Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetValue method
ms.assetid: a889feac-c0e0-4635-b506-843863d86967
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 74c4c189b72b7a469794e0828faf062a88cdf46f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710489"
---
# <a name="setvalue-method-serversettingsgeneralflag-class"></a><span data-ttu-id="a8151-102">SetValue 方法 (ServerSettingsGeneralFlag 類別)</span><span class="sxs-lookup"><span data-stu-id="a8151-102">SetValue Method (ServerSettingsGeneralFlag Class)</span></span>
  <span data-ttu-id="a8151-103">設定參考之旗標的所有值。</span><span class="sxs-lookup"><span data-stu-id="a8151-103">Sets all the values of the referenced flag.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8151-104">語法</span><span class="sxs-lookup"><span data-stu-id="a8151-104">Syntax</span></span>  
  
```  
  
object  
.SetValue(  
Value  
)  
  
```  
  
## <a name="parts"></a><span data-ttu-id="a8151-105">組件</span><span class="sxs-lookup"><span data-stu-id="a8151-105">Parts</span></span>  
 <span data-ttu-id="a8151-106">*object*</span><span class="sxs-lookup"><span data-stu-id="a8151-106">*object*</span></span>  
 <span data-ttu-id="a8151-107">表示伺服器設定之一般旗標的 [ServerSettingsGeneralFlag 類別](serversettingsgeneralflag-class.md) 物件。</span><span class="sxs-lookup"><span data-stu-id="a8151-107">A [ServerSettingsGeneralFlag Class](serversettingsgeneralflag-class.md) object that represents a general flag for the server settings.</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="a8151-108">參數</span><span class="sxs-lookup"><span data-stu-id="a8151-108">Parameters</span></span>  
  
|<span data-ttu-id="a8151-109">參數</span><span class="sxs-lookup"><span data-stu-id="a8151-109">Parameter</span></span>|<span data-ttu-id="a8151-110">描述</span><span class="sxs-lookup"><span data-stu-id="a8151-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a8151-111">*ReplTest1*</span><span class="sxs-lookup"><span data-stu-id="a8151-111">*Value*</span></span>|<span data-ttu-id="a8151-112">指定旗標之值的布林值。</span><span class="sxs-lookup"><span data-stu-id="a8151-112">A Boolean value that specifies the value of the flag.</span></span>|  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="a8151-113">屬性值/傳回值</span><span class="sxs-lookup"><span data-stu-id="a8151-113">Property Value/Return Value</span></span>  
 <span data-ttu-id="a8151-114">`uint32` 值，如果已成功修改此服務為 0，如果不支援要求則為 1，以及其他指示錯誤的任何數字。</span><span class="sxs-lookup"><span data-stu-id="a8151-114">A `uint32` value, which is 0 if the service was successfully modified, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a8151-115">備註</span><span class="sxs-lookup"><span data-stu-id="a8151-115">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8151-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a8151-116">See Also</span></span>  
 <span data-ttu-id="a8151-117">[設定伺服器網路通訊協定與網路程式庫](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span><span class="sxs-lookup"><span data-stu-id="a8151-117">[Configuring Server Network Protocols and Net-Libraries](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span></span>  
  
  
