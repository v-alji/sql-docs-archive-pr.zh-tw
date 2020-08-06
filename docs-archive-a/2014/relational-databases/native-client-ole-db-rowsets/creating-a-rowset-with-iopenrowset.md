---
title: 以 IOpenRowset 建立資料列集 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- IOpenRowset interface
- rowsets [OLE DB], creating
- SQL Server Native Client OLE DB provider, rowsets
- OLE DB rowsets, creating
ms.assetid: e8bc3de7-4b97-4de9-8df8-e11947d24045
author: rothja
ms.author: jroth
ms.openlocfilehash: bf74466a698d39f74b9531adaa54c79c75e50ef2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707450"
---
# <a name="creating-a-rowset-with-iopenrowset"></a><span data-ttu-id="b772f-102">以 IOpenRowset 建立資料列集</span><span class="sxs-lookup"><span data-stu-id="b772f-102">Creating a Rowset with IOpenRowset</span></span>
  <span data-ttu-id="b772f-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供者支援**IOpenRowset：： OpenRowset**方法，但有下列限制：</span><span class="sxs-lookup"><span data-stu-id="b772f-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider supports the **IOpenRowset::OpenRowset** method with the following restrictions:</span></span>  
  
-   <span data-ttu-id="b772f-104">*pTableID* 參數指向的資料庫識別碼 (DBID) 結構中必須指定基底資料表或檢視表。</span><span class="sxs-lookup"><span data-stu-id="b772f-104">A base table or view must be specified in a database ID (DBID) structure that the *pTableID* parameter points to.</span></span>  
  
-   <span data-ttu-id="b772f-105">DBID *eKind* 成員必須指示 DBKIND_NAME。</span><span class="sxs-lookup"><span data-stu-id="b772f-105">The DBID *eKind* member must indicate DBKIND_NAME.</span></span>  
  
-   <span data-ttu-id="b772f-106">DBID *uName* 成員必須將現有基底資料表或檢視表的名稱指定為 Unicode 字元字串。</span><span class="sxs-lookup"><span data-stu-id="b772f-106">The DBID *uName* member must specify the name of an existing base table or a view as a Unicode character string.</span></span>  
  
-   <span data-ttu-id="b772f-107">**OpenRowset** 的 *pIndexID* 參數必須為 NULL。</span><span class="sxs-lookup"><span data-stu-id="b772f-107">The *pIndexID* parameter of **OpenRowset** must be NULL.</span></span>  
  
 <span data-ttu-id="b772f-108">**IOpenRowset::OpenRowset** 的結果集包含單一資料列集。</span><span class="sxs-lookup"><span data-stu-id="b772f-108">The result set of **IOpenRowset::OpenRowset** contains a single rowset.</span></span> <span data-ttu-id="b772f-109">資料指標可以支援包含單一資料列集的結果集 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="b772f-109">Result sets that contain a single rowset can be supported by [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cursors.</span></span> <span data-ttu-id="b772f-110">資料指標支援可讓開發人員使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 並行機制。</span><span class="sxs-lookup"><span data-stu-id="b772f-110">Cursor support allows the developer to use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] concurrency mechanisms.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b772f-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b772f-111">See Also</span></span>  
 [<span data-ttu-id="b772f-112">資料列集</span><span class="sxs-lookup"><span data-stu-id="b772f-112">Rowsets</span></span>](rowsets.md)  
  
  
