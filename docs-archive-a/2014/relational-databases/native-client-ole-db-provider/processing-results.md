---
title: 處理結果 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, results processing
- OLE DB, processing results
- rowsets [SQL Server], results processing
- results [SQL Server Native Client]
ms.assetid: 20887ac4-f649-4e7f-92e6-f929e2e70952
author: rothja
ms.author: jroth
ms.openlocfilehash: b9e5bf00b4d2e554536c9f2ba1a328390b93a8a6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598832"
---
# <a name="processing-results"></a><span data-ttu-id="95b05-102">處理結果</span><span class="sxs-lookup"><span data-stu-id="95b05-102">Processing Results</span></span>
  <span data-ttu-id="95b05-103">如果資料列集物件是由命令的執行所產生或是直接從提供者產生資料列集物件而產生，則取用者需要擷取及存取此資料列集中的資料。</span><span class="sxs-lookup"><span data-stu-id="95b05-103">If a rowset object is produced by either the execution of a command or the generation of a rowset object directly from the provider, the consumer needs to retrieve and access data in the rowset.</span></span>  
  
 <span data-ttu-id="95b05-104">資料列集是中央物件，可讓 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者以表格式格式公開資料。</span><span class="sxs-lookup"><span data-stu-id="95b05-104">Rowsets are the central objects that enable the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider to expose data in tabular form.</span></span> <span data-ttu-id="95b05-105">就概念上來說，資料列集是一組資料列，其中各個資料列都有資料行。</span><span class="sxs-lookup"><span data-stu-id="95b05-105">Conceptually, a rowset is a set of rows in which each row has column data.</span></span> <span data-ttu-id="95b05-106">資料列集物件會公開介面，例如 **IRowset** (其中包含一些方法來從資料列集循序擷取資料列)、**IAccessor** (允許一組資料行繫結的定義，以描述表格式資料繫結至取用者程式變數的方式)、**IColumnsInfo** (提供有關資料列集內之資料行的資訊) 及 **IRowsetInfo** (提供有關資料列集的資訊)。</span><span class="sxs-lookup"><span data-stu-id="95b05-106">A rowset object exposes interfaces such as **IRowset** (contains methods for fetching rows from the rowset sequentially), **IAccessor** (permits the definition of a group of column bindings describing the way tabular data is bound to consumer program variables), **IColumnsInfo** (provides information about columns in the rowset), and **IRowsetInfo** (provides information about rowset).</span></span>  
  
 <span data-ttu-id="95b05-107">取用者可以呼叫 **IRowset::GetData** 方法，將資料列集中的資料列擷取到緩衝區。</span><span class="sxs-lookup"><span data-stu-id="95b05-107">A consumer can call the **IRowset::GetData** method to retrieve a row of data from the rowset into a buffer.</span></span> <span data-ttu-id="95b05-108">在呼叫 **GetData** 之前，取用者會使用一組 DBBINDING 結構來描述緩衝區。</span><span class="sxs-lookup"><span data-stu-id="95b05-108">Before **GetData** is called, the consumer describes the buffer using a set of DBBINDING structures.</span></span> <span data-ttu-id="95b05-109">每一個繫結都會描述資料列集中的資料行是如何儲存在取用者緩衝區內，並包含以下項目：</span><span class="sxs-lookup"><span data-stu-id="95b05-109">Each binding describes how a column in a rowset is stored in a consumer buffer and contains the following:</span></span>  
  
-   <span data-ttu-id="95b05-110">套用繫結之資料行 (或參數) 的序數。</span><span class="sxs-lookup"><span data-stu-id="95b05-110">Ordinal of the column (or parameter) to which the binding applies.</span></span>  
  
-   <span data-ttu-id="95b05-111">有關繫結內容的資訊 (例如資料值、資料的長度和它的繫結狀態)。</span><span class="sxs-lookup"><span data-stu-id="95b05-111">Information about what is bound (for example, data value, length of the data, and its binding status).</span></span>  
  
-   <span data-ttu-id="95b05-112">有關緩衝區內對每一個部分之位移的資訊。</span><span class="sxs-lookup"><span data-stu-id="95b05-112">Information about what is offset in the buffer to each of these parts.</span></span>  
  
-   <span data-ttu-id="95b05-113">存在於取用者緩衝區內之資料值的長度和類型。</span><span class="sxs-lookup"><span data-stu-id="95b05-113">Length and type of the data values as they exist in the consumer buffer.</span></span>  
  
 <span data-ttu-id="95b05-114">當取得資料時，提供者會使用每一個繫結中的資訊來判斷要從取用者緩衝區的何處擷取資料以及擷取方式為何。</span><span class="sxs-lookup"><span data-stu-id="95b05-114">When getting the data, the provider uses information in each binding to determine where and how to retrieve data from the consumer buffer.</span></span> <span data-ttu-id="95b05-115">在取用者緩衝區內設定資料時，提供者會使用每一個繫結中的資訊來判斷要從取用者緩衝區的何處傳回資料以及傳回方式為何。</span><span class="sxs-lookup"><span data-stu-id="95b05-115">When setting data in the consumer buffer, the provider uses information in each binding to determine where and how to return data in the consumer's buffer.</span></span>  
  
 <span data-ttu-id="95b05-116">當指定了 DBBINDING 結構之後，就會建立存取子 (**IAccessor::CreateAccessor**)。</span><span class="sxs-lookup"><span data-stu-id="95b05-116">After the DBBINDING structures are specified, an accessor is created (**IAccessor::CreateAccessor**).</span></span> <span data-ttu-id="95b05-117">存取子是繫結的集合，可用來取得或設定取用者緩衝區內的資料。</span><span class="sxs-lookup"><span data-stu-id="95b05-117">An accessor is a collection of bindings and is used to get or set the data in the consumer buffer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95b05-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="95b05-118">See Also</span></span>  
 <span data-ttu-id="95b05-119">[建立 SQL Server Native Client OLE DB 提供者應用程式](creating-a-sql-server-native-client-ole-db-provider-application.md) </span><span class="sxs-lookup"><span data-stu-id="95b05-119">[Creating a SQL Server Native Client OLE DB Provider Application](creating-a-sql-server-native-client-ole-db-provider-application.md) </span></span>  
 [<span data-ttu-id="95b05-120">OLE DB 的使用說明主題</span><span class="sxs-lookup"><span data-stu-id="95b05-120">OLE DB How-to Topics</span></span>](../native-client-ole-db-how-to/ole-db-how-to-topics.md)  
  
  
