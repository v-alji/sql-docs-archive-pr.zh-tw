---
title: 使用 IRow 來擷取單一資料列 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- fetching rows
- IRow interface
- single row fetching [SQL Server Native Client]
- OLE DB rowsets, fetching
- rowsets [OLE DB], fetching
- SQL Server Native Client OLE DB provider, fetching
ms.assetid: 07c803ca-299a-42c5-ba02-360b9631d15f
author: rothja
ms.author: jroth
ms.openlocfilehash: b5573fe1fef39f29329e373323f5f8aaf15f2c58
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598831"
---
# <a name="fetching-a-single-row-with-irow"></a><span data-ttu-id="a4fc2-102">使用 IRow 來提取單一資料列</span><span class="sxs-lookup"><span data-stu-id="a4fc2-102">Fetching a Single Row with IRow</span></span>
  <span data-ttu-id="a4fc2-103">Native Client OLE DB 提供者中的**IRow**介面實 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 已簡化，以提高效能。</span><span class="sxs-lookup"><span data-stu-id="a4fc2-103">The **IRow** interface implementation in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider is simplified to increase performance.</span></span> <span data-ttu-id="a4fc2-104">**IRow** 允許直接存取單一資料列物件的資料行。</span><span class="sxs-lookup"><span data-stu-id="a4fc2-104">**IRow** allows direct access to columns of a single row object.</span></span> <span data-ttu-id="a4fc2-105">如果您事先知道命令執行的結果只會產生單一資料列，**IRow** 就會擷取該資料列的資料行。</span><span class="sxs-lookup"><span data-stu-id="a4fc2-105">If you know beforehand that the result of a command execution will produce exactly one row, **IRow** will retrieve the columns of that row.</span></span> <span data-ttu-id="a4fc2-106">如果結果集包含多個資料列，**IRow** 就只會公開第一個資料列。</span><span class="sxs-lookup"><span data-stu-id="a4fc2-106">If the result set includes multiple rows, **IRow** will expose only the first row.</span></span>  
  
 <span data-ttu-id="a4fc2-107">**IRow** 實作不允許資料列的任何導覽。</span><span class="sxs-lookup"><span data-stu-id="a4fc2-107">The **IRow** implementation does not allow any navigation of the row.</span></span> <span data-ttu-id="a4fc2-108">此資料列中的每個資料行只會存取一次，但有一項例外狀況：您可以存取一次資料行來尋找資料行大小，然後再次存取，以便提取資料。</span><span class="sxs-lookup"><span data-stu-id="a4fc2-108">Each column in the row is accessed only one time with one exception: A column can be accessed one time to find the column size and again to fetch the data.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a4fc2-109">**IRow::Open** 僅支援開啟 DBGUID_STREAM 和 DBGUID_NULL 類型的物件。</span><span class="sxs-lookup"><span data-stu-id="a4fc2-109">**IRow::Open** supports only DBGUID_STREAM and DBGUID_NULL type of objects to be opened.</span></span>  
  
 <span data-ttu-id="a4fc2-110">若要使用 **ICommand::Execute** 方法來取得資料列物件，您必須傳遞 IID_IRow。</span><span class="sxs-lookup"><span data-stu-id="a4fc2-110">To obtain a row object using **ICommand::Execute** method, IID_IRow must be passed.</span></span> <span data-ttu-id="a4fc2-111">**IMultipleResults** 介面必須用來處理多個結果集。</span><span class="sxs-lookup"><span data-stu-id="a4fc2-111">The **IMultipleResults** interface must be used to handle multiple result sets.</span></span> <span data-ttu-id="a4fc2-112">**IMultipleResults** 支援 **IRow** 和 **IRowset**。</span><span class="sxs-lookup"><span data-stu-id="a4fc2-112">**IMultipleResults** supports **IRow** and **IRowset**.</span></span> <span data-ttu-id="a4fc2-113">**IRowset** 可用於大量作業。</span><span class="sxs-lookup"><span data-stu-id="a4fc2-113">**IRowset** is used for bulk operations.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a4fc2-114">本節內容</span><span class="sxs-lookup"><span data-stu-id="a4fc2-114">In This Section</span></span>  
  
-   [<span data-ttu-id="a4fc2-115">使用 IRow::GetColumns</span><span class="sxs-lookup"><span data-stu-id="a4fc2-115">Using IRow::GetColumns</span></span>](using-irow-getcolumns.md)  
  
-   [<span data-ttu-id="a4fc2-116">使用 IRow 擷取 BLOB 資料</span><span class="sxs-lookup"><span data-stu-id="a4fc2-116">Fetching BLOB Data Using IRow</span></span>](../../database-engine/dev-guide/fetching-blob-data-using-irow.md)  
  
## <a name="see-also"></a><span data-ttu-id="a4fc2-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a4fc2-117">See Also</span></span>  
 [<span data-ttu-id="a4fc2-118">資料列集</span><span class="sxs-lookup"><span data-stu-id="a4fc2-118">Rowsets</span></span>](rowsets.md)  
  
  
