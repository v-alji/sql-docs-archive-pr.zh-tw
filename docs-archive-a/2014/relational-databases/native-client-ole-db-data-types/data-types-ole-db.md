---
title: 資料類型 (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- mapping data types [OLE DB]
- SQL Server Native Client OLE DB provider, data types
- data types [OLE DB]
- OLE DB, data types
ms.assetid: 15953706-f0d1-45f5-a2eb-a8bd36e1a5fc
author: rothja
ms.author: jroth
ms.openlocfilehash: 860d188f7a934e707766b157d4c089a88207ce02
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708230"
---
# <a name="data-types-ole-db"></a><span data-ttu-id="f7035-102">資料類型 (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="f7035-102">Data Types (OLE DB)</span></span>
  <span data-ttu-id="f7035-103">若要 [!INCLUDE[tsql](../../includes/tsql-md.md)] 使用 Native client OLE DB 提供者來執行語句並處理結果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，您必須知道 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native client OLE DB 提供者在系結 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料列集中的參數或資料行時，如何將資料類型對應到 OLE DB 的資料類型，以及當它使用**ITableDefinition**介面在中建立資料表時 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="f7035-103">In order to execute [!INCLUDE[tsql](../../includes/tsql-md.md)] statements and process the results using the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider, you must know how the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider maps [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data types to OLE DB data types when binding parameters or columns in a rowset, and when it uses the **ITableDefinition** interface to create a table in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f7035-104">本節內容</span><span class="sxs-lookup"><span data-stu-id="f7035-104">In This Section</span></span>  
  
-   [<span data-ttu-id="f7035-105">資料列集和參數中的資料類型對應</span><span class="sxs-lookup"><span data-stu-id="f7035-105">Data Type Mapping in Rowsets and Parameters</span></span>](data-type-mapping-in-rowsets-and-parameters.md)  
  
-   [<span data-ttu-id="f7035-106">ITableDefinition 中的資料類型對應</span><span class="sxs-lookup"><span data-stu-id="f7035-106">Data Type Mapping in ITableDefinition</span></span>](data-type-mapping-in-itabledefinition.md)  
  
-   [<span data-ttu-id="f7035-107">SSVARIANT 結構</span><span class="sxs-lookup"><span data-stu-id="f7035-107">SSVARIANT Structure</span></span>](ssvariant-structure.md)  
  
## <a name="see-also"></a><span data-ttu-id="f7035-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f7035-108">See Also</span></span>  
 [<span data-ttu-id="f7035-109">SQL Server Native Client &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="f7035-109">SQL Server Native Client &#40;OLE DB&#41;</span></span>](../native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  
