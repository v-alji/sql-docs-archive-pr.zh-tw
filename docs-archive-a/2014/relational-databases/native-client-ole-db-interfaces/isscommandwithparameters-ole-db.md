---
title: ISSCommandWithParameters (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- ISSCommandWithParameters (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- ISSCommandWithParameters interface
ms.assetid: 3419b7f3-36a3-4863-816e-e641e4e90496
author: rothja
ms.author: jroth
ms.openlocfilehash: 295026497a97b4ce13d1a1a68de48079809390ad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594040"
---
# <a name="isscommandwithparameters-ole-db"></a><span data-ttu-id="4bc3f-102">ISSCommandWithParameters (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="4bc3f-102">ISSCommandWithParameters (OLE DB)</span></span>
  <span data-ttu-id="4bc3f-103">**ISSCommandWithParameters**會公開 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (UDT) 的 XML 和使用者定義型別支援。</span><span class="sxs-lookup"><span data-stu-id="4bc3f-103">**ISSCommandWithParameters** exposes support for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] XML and user-defined types (UDT).</span></span> <span data-ttu-id="4bc3f-104">這是選擇性的介面，繼承自核心 OLE DB 介面**ICommandWithParameters**。</span><span class="sxs-lookup"><span data-stu-id="4bc3f-104">This is an optional interface that inherits from the core OLE DB interface **ICommandWithParameters**.</span></span> <span data-ttu-id="4bc3f-105">除了繼承自**ICommandWithParameters**的三個方法以外，**GetParameterInfo**、 **MapParameterNames**和**SetParameterInfo**;**ISSCommandWithParameters**提供兩種新的方法，可用來處理伺服器特定的資料類型。</span><span class="sxs-lookup"><span data-stu-id="4bc3f-105">In addition to the three methods inherited from **ICommandWithParameters**; **GetParameterInfo**, **MapParameterNames**, and **SetParameterInfo**; **ISSCommandWithParameters** provides two new methods that are used to handle server specific data types.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4bc3f-106">使用服務元件時，可以使用**ISSCommandWithParameters**介面，但服務元件本身不會使用此介面。</span><span class="sxs-lookup"><span data-stu-id="4bc3f-106">The **ISSCommandWithParameters** interface can be used when Service Components are used, but the Service Components themselves will not use this interface.</span></span>  
  
|<span data-ttu-id="4bc3f-107">方法</span><span class="sxs-lookup"><span data-stu-id="4bc3f-107">Method</span></span>|<span data-ttu-id="4bc3f-108">描述</span><span class="sxs-lookup"><span data-stu-id="4bc3f-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4bc3f-109">ISSCommandWithParameters::GetParameterProperties &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="4bc3f-109">ISSCommandWithParameters::GetParameterProperties &#40;OLE DB&#41;</span></span>](isscommandwithparameters-getparameterproperties-ole-db.md)|<span data-ttu-id="4bc3f-110">針對傳遞至命令的每個 UDT 或 XML 參數以陣列傳回一個 **SSPARAMPROPS** 屬性集結構，但不會針對其他類型的參數傳回任何項目。</span><span class="sxs-lookup"><span data-stu-id="4bc3f-110">Returns one **SSPARAMPROPS** property set structure in the array for each UDT or XML parameter passed to the command, but none is returned for other types of parameters.</span></span>|  
|[<span data-ttu-id="4bc3f-111">ISSCommandWithParameters::SetParameterProperties &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="4bc3f-111">ISSCommandWithParameters::SetParameterProperties &#40;OLE DB&#41;</span></span>](isscommandwithparameters-setparameterproperties-ole-db.md)|<span data-ttu-id="4bc3f-112">依照序數根據每個參數來設定參數的屬性，或指定 **SSPARAMPROPS** 結構的陣列來設定大量參數屬性。</span><span class="sxs-lookup"><span data-stu-id="4bc3f-112">Sets the parameter properties on a per parameter basis by ordinal, or sets bulk parameter properties by specifying an array of **SSPARAMPROPS** structures.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4bc3f-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4bc3f-113">See Also</span></span>  
 <span data-ttu-id="4bc3f-114">[介面 &#40;OLE DB&#41;](../../database-engine/dev-guide/interfaces-ole-db.md) </span><span class="sxs-lookup"><span data-stu-id="4bc3f-114">[Interfaces &#40;OLE DB&#41;](../../database-engine/dev-guide/interfaces-ole-db.md) </span></span>  
 <span data-ttu-id="4bc3f-115">[使用 XML 資料類型](../native-client/features/using-xml-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="4bc3f-115">[Using XML Data Types](../native-client/features/using-xml-data-types.md) </span></span>  
 [<span data-ttu-id="4bc3f-116">使用使用者定義型別</span><span class="sxs-lookup"><span data-stu-id="4bc3f-116">Using User-Defined Types</span></span>](../native-client/features/using-user-defined-types.md)  
  
  
