---
title: SetDefaults 方法 (ServerSettings 類別) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetDefaults Method (ServerSettings Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetDefaults method
ms.assetid: 76e4cfab-4b15-4da4-bb2f-8aac6f927f79
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 93dd2eee5a395d4d7463ebf9b85530fcf82d1888
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699337"
---
# <a name="setdefaults-method-serversettings-class"></a><span data-ttu-id="44298-102">SetDefaults 方法 (ServerSettings 類別)</span><span class="sxs-lookup"><span data-stu-id="44298-102">SetDefaults Method (ServerSettings Class)</span></span>
  <span data-ttu-id="44298-103">[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 使用覆寫現有資料的選項，設定實例的所有預設值。</span><span class="sxs-lookup"><span data-stu-id="44298-103">Sets all the default values for the instance of [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] with the option to overwrite existing data.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44298-104">語法</span><span class="sxs-lookup"><span data-stu-id="44298-104">Syntax</span></span>  
  
```  
  
object  
.SetDefaults(  
OverwriteAll  
)  
  
```  
  
## <a name="parts"></a><span data-ttu-id="44298-105">組件</span><span class="sxs-lookup"><span data-stu-id="44298-105">Parts</span></span>  
 <span data-ttu-id="44298-106">*object*</span><span class="sxs-lookup"><span data-stu-id="44298-106">*object*</span></span>  
 <span data-ttu-id="44298-107">代表用戶端實例的[ServerSettings 類別](serversettings-class.md)物件 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="44298-107">A [ServerSettings Class](serversettings-class.md) object that represents a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] client instance.</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="44298-108">參數</span><span class="sxs-lookup"><span data-stu-id="44298-108">Parameters</span></span>  
  
|<span data-ttu-id="44298-109">參數</span><span class="sxs-lookup"><span data-stu-id="44298-109">Parameter</span></span>|<span data-ttu-id="44298-110">描述</span><span class="sxs-lookup"><span data-stu-id="44298-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="44298-111">*OverwriteAll*</span><span class="sxs-lookup"><span data-stu-id="44298-111">*OverwriteAll*</span></span>|<span data-ttu-id="44298-112">指定是否要覆寫 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體上之現有值的布林值。`true` 表示要覆寫現有的資料，`false` 表示不覆寫現有的資料。</span><span class="sxs-lookup"><span data-stu-id="44298-112">A Boolean value that specifies whether to overwrite existing values on the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: `true` to overwrite existing data, or `false` if existing data is not to be overwritten.</span></span>|  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="44298-113">屬性值/傳回值</span><span class="sxs-lookup"><span data-stu-id="44298-113">Property Value/Return Value</span></span>  
 <span data-ttu-id="44298-114">u`int32` 值，如果已成功修改此服務為 0，如果不支援要求則為 1，以及其他指示錯誤的任何數字。</span><span class="sxs-lookup"><span data-stu-id="44298-114">A u`int32` value, which is 0 if the service was successfully modified, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="44298-115">備註</span><span class="sxs-lookup"><span data-stu-id="44298-115">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44298-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="44298-116">See Also</span></span>  
 <span data-ttu-id="44298-117">[設定伺服器網路通訊協定與網路程式庫](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span><span class="sxs-lookup"><span data-stu-id="44298-117">[Configuring Server Network Protocols and Net-Libraries](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span></span>  
  
  
