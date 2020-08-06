---
title: OLE DB 操作說明主題 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- OLE DB, how-to topics
ms.assetid: fbfab1b0-433d-497e-ae07-9b21a5c6903c
author: rothja
ms.author: jroth
ms.openlocfilehash: 006962c1a28cc4a21f3e2efaa63b45b0871e208f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594976"
---
# <a name="ole-db-how-to-topics"></a><span data-ttu-id="37286-102">OLE DB 的使用說明主題</span><span class="sxs-lookup"><span data-stu-id="37286-102">OLE DB How-to Topics</span></span>
  <span data-ttu-id="37286-103">若要使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者，您必須瞭解如何建立與伺服器的連接、執行命令，以及處理結果。</span><span class="sxs-lookup"><span data-stu-id="37286-103">To use the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider, you have to understand how to make a connection to the server, execute the command, and process the results.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="37286-104">本節內容</span><span class="sxs-lookup"><span data-stu-id="37286-104">In This Section</span></span>  
  
-   [<span data-ttu-id="37286-105">處理結果操作說明主題 &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="37286-105">Processing Results How-to Topics &#40;OLE DB&#41;</span></span>](results/processing-results-how-to-topics-ole-db.md)  
  
-   [<span data-ttu-id="37286-106">設定大型資料 &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="37286-106">Set Large Data &#40;OLE DB&#41;</span></span>](set-large-data-ole-db.md)  
  
-   [<span data-ttu-id="37286-107">列舉 OLE DB 資料來源 &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="37286-107">Enumerate OLE DB Data Sources &#40;OLE DB&#41;</span></span>](enumerate-ole-db-data-sources-ole-db.md)  
  
-   [<span data-ttu-id="37286-108">使用 IRowsetFastLoad 大量複製資料 &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="37286-108">Bulk Copy Data Using IRowsetFastLoad &#40;OLE DB&#41;</span></span>](../native-client-ole-db-interfaces/irowsetfastload-ole-db.md)  
  
-   [<span data-ttu-id="37286-109">取得 FAST_FORWARD 資料指標</span><span class="sxs-lookup"><span data-stu-id="37286-109">Obtain a FAST_FORWARD Cursor</span></span>](obtain-a-fast-forward-cursor.md)  
  
-   [<span data-ttu-id="37286-110">使用書籤擷取資料列 &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="37286-110">Retrieve Rows Using Bookmarks &#40;OLE DB&#41;</span></span>](retrieve-rows-using-bookmarks-ole-db.md)  
  
-   [<span data-ttu-id="37286-111">使用 IRow::GetColumns &#40;或 IRow::Open&#41; 和 ISequentialStream 擷取資料行</span><span class="sxs-lookup"><span data-stu-id="37286-111">Fetch Columns Using IRow::GetColumns &#40;or IRow::Open&#41; and ISequentialStream</span></span>](fetch-columns-using-irow-getcolumns-or-irow-open-and-isequentialstream.md)  
  
-   [<span data-ttu-id="37286-112">使用 IRow::GetColumns 擷取資料行 &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="37286-112">Fetch Columns Using IRow::GetColumns &#40;OLE DB&#41;</span></span>](fetch-columns-using-irow-getcolumns-ole-db.md)  
  
-   [<span data-ttu-id="37286-113">變更 SQL Server 驗證使用者密碼 &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="37286-113">Change a SQL Server Authentication User Password &#40;OLE DB&#41;</span></span>](change-a-sql-server-authentication-user-password-ole-db.md)  
  
-   [<span data-ttu-id="37286-114">使用增強型日期和時間功能 &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="37286-114">Use Enhanced Date and Time Features &#40;OLE DB&#41;</span></span>](use-enhanced-date-and-time-features-ole-db.md)  
  
-   [<span data-ttu-id="37286-115">檔案資料流及 OLE DB</span><span class="sxs-lookup"><span data-stu-id="37286-115">Filestream and OLE DB</span></span>](filestream/filestream-and-ole-db.md)  
  
-   [<span data-ttu-id="37286-116">使用 IROWSETFASTLOAD 和 ISEQUENTIALSTREAM 將 BLOB 資料傳送到 SQL SERVER &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="37286-116">Send BLOB Data to SQL SERVER Using IROWSETFASTLOAD and ISEQUENTIALSTREAM &#40;OLE DB&#41;</span></span>](send-blob-data-to-sql-server-using-irowsetfastload-and-isequentialstream-ole-db.md)  
  
-   [<span data-ttu-id="37286-117">使用大型 CLR UDT &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="37286-117">Use Large CLR UDTs &#40;OLE DB&#41;</span></span>](use-large-clr-udts-ole-db.md)  
  
-   [<span data-ttu-id="37286-118">顯示資料行與疏鬆資料行的目錄中繼資料 &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="37286-118">Display Column and Catalog Metadata for Sparse Columns &#40;OLE DB&#41;</span></span>](display-column-and-catalog-metadata-for-sparse-columns-ole-db.md)  
  
-   [<span data-ttu-id="37286-119">整合式 Kerberos 驗證 &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="37286-119">Integrated Kerberos Authentication &#40;OLE DB&#41;</span></span>](integrated-kerberos-authentication-ole-db.md)  
  
-   [<span data-ttu-id="37286-120">使用資料表值參數 &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="37286-120">Use Table-Valued Parameters &#40;OLE DB&#41;</span></span>](../native-client-ole-db-table-valued-parameters/table-valued-parameters-ole-db.md)  
  
## <a name="see-also"></a><span data-ttu-id="37286-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="37286-121">See Also</span></span>  
 [<span data-ttu-id="37286-122">SQL Server Native Client 程式設計</span><span class="sxs-lookup"><span data-stu-id="37286-122">SQL Server Native Client Programming</span></span>](../native-client/sql-server-native-client-programming.md)  
  
  
