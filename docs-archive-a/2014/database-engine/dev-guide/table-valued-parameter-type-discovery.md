---
title: 資料表值參數類型探索 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
helpviewer_keywords:
- table-valued parameters, type discovery
ms.assetid: f55818c2-ebb5-4cf6-8c0c-0da41f592560
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: ab8d837e4ddf74256e4bae70f772557ec8ff67f7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701710"
---
# <a name="table-valued-parameter-type-discovery"></a><span data-ttu-id="93dca-102">資料表值參數類型探索</span><span class="sxs-lookup"><span data-stu-id="93dca-102">Table-Valued Parameter Type Discovery</span></span>
  <span data-ttu-id="93dca-103">取用者（也就是使用 Native Client OLE DB 提供者的用戶端應用程式）， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 如果命令文字已提供給 OLE DB 提供者，就可以探索每個命令參數的型別。</span><span class="sxs-lookup"><span data-stu-id="93dca-103">The consumer-that is, the client application using the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB Provider-can discover the type of each command parameter if the command text has been given to the OLE DB Provider.</span></span> <span data-ttu-id="93dca-104">知道了資料表值參數的類型之後，取用者就可以針對資料表值參數的每一個個別資料行來探索中繼資料資訊。</span><span class="sxs-lookup"><span data-stu-id="93dca-104">After the type of a table-valued parameter is known, the consumer can discover the metadata information for each individual column of the table-valued parameter.</span></span>  
  
 <span data-ttu-id="93dca-105">ICommandWithParameters::GetParameterInfo 可針對大多數的參數類型來支援程序參數的類型資訊。</span><span class="sxs-lookup"><span data-stu-id="93dca-105">The type information of procedure parameters is supported by ICommandWithParameters::GetParameterInfo for most parameter types.</span></span> <span data-ttu-id="93dca-106">從開始 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] ，隨著使用者定義型別和資料類型的引進 `xml` ，GetParameterInfo 方法並不足以因應此用途，因為無法透過 ICommandWithParameters 提供使用者定義的類型資訊 (名稱、架構和目錄) 。</span><span class="sxs-lookup"><span data-stu-id="93dca-106">Beginning with [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], with the introduction of user-defined types and the `xml` data type, the GetParameterInfo method was not sufficient for this purpose because it was not possible to provide user-defined type information (name, schema, and catalog) through ICommandWithParameters.</span></span> <span data-ttu-id="93dca-107">因此定義了新的介面 ISSCommandWithParameters 來提供擴充類型資訊。</span><span class="sxs-lookup"><span data-stu-id="93dca-107">A new interface, ISSCommandWithParameters, was defined to provide extended type information.</span></span>  
  
 <span data-ttu-id="93dca-108">如果是資料表值參數，您也可以使用 ISSCommandWithParameters 介面來探索詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="93dca-108">For table-valued parameters, you also use the ISSCommandWithParameters interface to discover detailed information.</span></span> <span data-ttu-id="93dca-109">在準備命令物件之後，用戶端會呼叫 ISSCommandWithParameters::GetParameterInfo。</span><span class="sxs-lookup"><span data-stu-id="93dca-109">The client calls ISSCommandWithParameters::GetParameterInfo after preparing the command object.</span></span> <span data-ttu-id="93dca-110">如果是資料表值參數，DBPARAMINFO 結構的 *wType* 成員會由提供者設定為 DBTYPE_TABLE。</span><span class="sxs-lookup"><span data-stu-id="93dca-110">For table-valued parameters, the *wType* member of the DBPARAMINFO structure is set to DBTYPE_TABLE by the provider.</span></span> <span data-ttu-id="93dca-111">DBPARAMINFO 結構的 *ulParamSize* 欄位具有 ~0 的值。</span><span class="sxs-lookup"><span data-stu-id="93dca-111">The *ulParamSize* field of DBPARAMINFO structure has a value of ~0.</span></span>  
  
 <span data-ttu-id="93dca-112">然後取用者會使用 ISSCommandWithParameters::GetParameterProperties 來要求其他屬性 (資料表值參數類型目錄名稱、資料表值參數類型結構描述名稱、資料表值參數類型名稱、資料行排序和預設資料行)。</span><span class="sxs-lookup"><span data-stu-id="93dca-112">The consumer would then request additional properties (table-valued parameter type catalog name, table-valued parameter type schema name, table-valued parameter type name, column ordering, and default columns) by using ISSCommandWithParameters::GetParameterProperties.</span></span>  
  
 <span data-ttu-id="93dca-113">如果在知道了類型名稱之後要擷取個別資料行資訊，取用者必須呼叫 IOpenRowset::OpenRowsetor 或取得 DBSCHEMA_TABLE_TYPE_COLUMNS 資料列集，其方式是將資料表值參數類型名稱指定為資料表名稱。</span><span class="sxs-lookup"><span data-stu-id="93dca-113">After the type name is known, to retrieve the individual column information the consumer must either call IOpenRowset::OpenRowsetor obtain the DBSCHEMA_TABLE_TYPE_COLUMNS rowset by specifying the table-valued parameter type name as the table name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93dca-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="93dca-114">See Also</span></span>  
 <span data-ttu-id="93dca-115">[資料表值參數 &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-table-valued-parameters/table-valued-parameters-ole-db.md) </span><span class="sxs-lookup"><span data-stu-id="93dca-115">[Table-Valued Parameters &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-table-valued-parameters/table-valued-parameters-ole-db.md) </span></span>  
 [<span data-ttu-id="93dca-116">使用資料表值參數 &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="93dca-116">Use Table-Valued Parameters &#40;OLE DB&#41;</span></span>](../../relational-databases/native-client-ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  
