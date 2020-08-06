---
title: FILESTREAM 支援 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- FILESTREAM [SQL Server], SQL Server Native Client
- SQL Server Native Client [FILESTREAM support]
ms.assetid: 1ad3400d-7fcd-40c9-87ae-f5afc61e0374
author: rothja
ms.author: jroth
ms.openlocfilehash: 18e9a002bfb205e2c0807234550998fe48120d20
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698089"
---
# <a name="filestream-support"></a><span data-ttu-id="42561-102">FILESTREAM 支援</span><span class="sxs-lookup"><span data-stu-id="42561-102">FILESTREAM Support</span></span>
  <span data-ttu-id="42561-103">FILESTREAM 提供透過 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 或直接存取 Windows 檔案系統來儲存及存取大型二進位值的方式。</span><span class="sxs-lookup"><span data-stu-id="42561-103">FILESTREAM provides a way to store and access large binary values, either through [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] or by direct access to the Windows file system.</span></span> <span data-ttu-id="42561-104">大型二進位值是大於 2 GB 的值。</span><span class="sxs-lookup"><span data-stu-id="42561-104">A large binary value is a value larger than 2 gigabytes (GB).</span></span> <span data-ttu-id="42561-105">如需有關增強型 FILESTREAM 支援的詳細資訊，請參閱 [FILESTREAM &#40;SQL Server&#41;](../../blob/filestream-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="42561-105">For more information about enhanced FILESTREAM support, see [FILESTREAM &#40;SQL Server&#41;](../../blob/filestream-sql-server.md).</span></span>  
  
 <span data-ttu-id="42561-106">當開啟資料庫連接時，`@@TEXTSIZE` 預設會設定為 -1 (無限制)。</span><span class="sxs-lookup"><span data-stu-id="42561-106">When a database connection is opened, `@@TEXTSIZE` will be set to -1 ("unlimited"), by default.</span></span>  
  
 <span data-ttu-id="42561-107">也可以使用 Windows 檔案系統 API 來存取及更新 FILESTREAM 資料行。</span><span class="sxs-lookup"><span data-stu-id="42561-107">It is also possible to access and update FILESTREAM columns using Windows file system APIs.</span></span>  
  
 <span data-ttu-id="42561-108">如需詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="42561-108">For more information, see the following topics:</span></span>  
  
-   [<span data-ttu-id="42561-109">FILESTREAM 支援 &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="42561-109">FILESTREAM Support &#40;OLE DB&#41;</span></span>](../ole-db/filestream-support-ole-db.md)  
  
-   [<span data-ttu-id="42561-110">FILESTREAM 支援 &#40;ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="42561-110">FILESTREAM Support &#40;ODBC&#41;</span></span>](../odbc/filestream-support-odbc.md)  
  
-   [<span data-ttu-id="42561-111">使用 OpenSqlFilestream 存取 FILESTREAM 資料</span><span class="sxs-lookup"><span data-stu-id="42561-111">Access FILESTREAM Data with OpenSqlFilestream</span></span>](../../blob/access-filestream-data-with-opensqlfilestream.md)  
  
## <a name="querying-for-filestream-columns"></a><span data-ttu-id="42561-112">查詢是否有 FILESTREAM 資料行</span><span class="sxs-lookup"><span data-stu-id="42561-112">Querying for FILESTREAM Columns</span></span>  
 <span data-ttu-id="42561-113">OLE DB 中的結構描述資料列集將不會報告某個資料行是否為 FILESTREAM 資料行。</span><span class="sxs-lookup"><span data-stu-id="42561-113">Schema rowsets in OLE DB will not report whether a column is a FILESTREAM column.</span></span> <span data-ttu-id="42561-114">OLE DB 中的 ITableDefinition 不能用來建立 FILESTREAM 資料行。</span><span class="sxs-lookup"><span data-stu-id="42561-114">ITableDefinition in OLE DB cannot be used to create a FILESTREAM column.</span></span>  
  
 <span data-ttu-id="42561-115">在 ODBC 中的目錄函數（例如 SQLColumns）不會報告資料行是否為 FILESTREAM 資料行。</span><span class="sxs-lookup"><span data-stu-id="42561-115">Catalog functions such as SQLColumns in ODBC will not report whether a column is a FILESTREAM column.</span></span>  
  
 <span data-ttu-id="42561-116">若要建立 FILESTREAM 資料行，或偵測哪些現有的資料行是 FILESTREAM 資料行，您可以使用 `is_filestream` [sys.databases](/sql/relational-databases/system-catalog-views/sys-columns-transact-sql)目錄檢視的資料行。</span><span class="sxs-lookup"><span data-stu-id="42561-116">To create FILESTREAM columns or to detect which existing columns are FILESTREAM columns, you can use the `is_filestream` column of the [sys.columns](/sql/relational-databases/system-catalog-views/sys-columns-transact-sql) catalog view.</span></span>  
  
 <span data-ttu-id="42561-117">以下是一個範例：</span><span class="sxs-lookup"><span data-stu-id="42561-117">The following is an example:</span></span>  
  
```  
-- Create a table with a FILESTREAM column.  
CREATE TABLE Bob_01 (GuidCol1 uniqueidentifier ROWGUIDCOL NOT NULL UNIQUE DEFAULT NEWID(), IntCol2 int, varbinaryCol3 varbinary(max) FILESTREAM);  
  
-- Find FILESTREAM columns.  
SELECT name FROM sys.columns WHERE is_filestream=1;  
  
-- Determine whether a column is a FILESTREAM column.  
SELECT is_filestream FROM sys.columns WHERE name = 'varbinaryCol3' AND object_id IN (SELECT object_id FROM sys.tables WHERE name='Bob_01');  
```  
  
## <a name="down-level-compatibility"></a><span data-ttu-id="42561-118">下層相容性</span><span class="sxs-lookup"><span data-stu-id="42561-118">Down-Level Compatibility</span></span>  
 <span data-ttu-id="42561-119">如果您的用戶端是使用隨附的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native client 版本所編譯 [!INCLUDE[ssVersion2005](../../../includes/sscurrent-md.md)] ，則 `varbinary(max)` 行為會與相容 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="42561-119">If your client was compiled using the version of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client that was included with [!INCLUDE[ssVersion2005](../../../includes/sscurrent-md.md)], `varbinary(max)` behavior will be compatible with [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)].</span></span> <span data-ttu-id="42561-120">也就是說，傳回之資料的大小最大值受限於 2 GB。</span><span class="sxs-lookup"><span data-stu-id="42561-120">That is, the maximum size of returned data will be limited to 2 GB.</span></span> <span data-ttu-id="42561-121">如果結果值大於 2 GB，將會發生截斷，而且將會傳回「字串資料右邊截斷」警告。</span><span class="sxs-lookup"><span data-stu-id="42561-121">For result values larger that 2 GB, truncation will occur and a "string data right truncation" warning will be returned.</span></span>  
  
 <span data-ttu-id="42561-122">當資料類型相容性設定為 80 時，用戶端行為將會與下層用戶端行為一致。</span><span class="sxs-lookup"><span data-stu-id="42561-122">When data-type compatibility is set to 80, client behavior will be consistent with down-level client behavior.</span></span>  
  
 <span data-ttu-id="42561-123">若是使用 SQLOLEDB 的用戶端，或在 Native Client 之前發行的其他提供者 [!INCLUDE[ssVersion2005](../../../includes/ssnoversion-md.md)] ， `varbinary(max)` 將會對應到 image。</span><span class="sxs-lookup"><span data-stu-id="42561-123">For clients that use SQLOLEDB or other providers that were released before the [!INCLUDE[ssVersion2005](../../../includes/ssnoversion-md.md)] Native Client, `varbinary(max)` will be mapped to image.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42561-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="42561-124">See Also</span></span>  
 [<span data-ttu-id="42561-125">SQL Server Native Client 功能</span><span class="sxs-lookup"><span data-stu-id="42561-125">SQL Server Native Client Features</span></span>](sql-server-native-client-features.md)  
  
  
