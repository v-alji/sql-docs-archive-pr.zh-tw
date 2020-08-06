---
title: 中繼資料探索 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: ec3c0f4f-f838-43ce-85f2-cf2761e2aac5
author: rothja
ms.author: jroth
ms.openlocfilehash: 571df9f21ab46a53c8aba7907039ce02afd6ad05
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698068"
---
# <a name="metadata-discovery"></a><span data-ttu-id="de5fa-102">中繼資料探索</span><span class="sxs-lookup"><span data-stu-id="de5fa-102">Metadata Discovery</span></span>
  <span data-ttu-id="de5fa-103">中的中繼資料探索改進 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] 可讓 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 原生用戶端應用程式確保查詢執行所傳回的資料行或參數中繼資料，與您在執行查詢之前指定的元資料格式完全相同或相容。</span><span class="sxs-lookup"><span data-stu-id="de5fa-103">The metadata discovery improvement in [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] allows [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client applications to ensure that column or parameter metadata returned from the execution of a query is identical to or compatible with the metadata format you specified before you executed the query.</span></span> <span data-ttu-id="de5fa-104">如果查詢執行之後傳回的中繼資料與您在查詢執行之前指定的中繼資料格式不相容，您就會收到錯誤。</span><span class="sxs-lookup"><span data-stu-id="de5fa-104">You will receive an error if the metadata returned after query execution is not compatible with the metadata format you specified before query execution.</span></span>  
  
 <span data-ttu-id="de5fa-105">在 bcp 和 ODBC 函數以及 IBCPSession 和 IBCPSession2 介面中，您現在可以指定延遲讀取 (延遲中繼資料探索)，避免針對查詢輸出作業進行中繼資料探索。</span><span class="sxs-lookup"><span data-stu-id="de5fa-105">In bcp and ODBC functions, and IBCPSession and IBCPSession2 interfaces, you can now specify a delayed read (delayed metadata discovery) to avoid metadata discovery for query out operations.</span></span> <span data-ttu-id="de5fa-106">這樣做可改善效能並排除中繼資料探索失敗。</span><span class="sxs-lookup"><span data-stu-id="de5fa-106">This improves performance and eliminates metadata discovery failures.</span></span>  
  
 <span data-ttu-id="de5fa-107">如果您使用中的 Native Client 開發應用程式 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] ，但連接到早于的伺服器版本 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] ，則中繼資料探索功能將對應至伺服器的版本。</span><span class="sxs-lookup"><span data-stu-id="de5fa-107">If you develop an application using [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client in [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] but connect to a server version earlier than [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)], metadata discovery functionality will correspond to the version of the server.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="de5fa-108">備註</span><span class="sxs-lookup"><span data-stu-id="de5fa-108">Remarks</span></span>  
 <span data-ttu-id="de5fa-109">[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] 已經強化了下列 bcp 函數，以便提供改良的中繼資料探索：</span><span class="sxs-lookup"><span data-stu-id="de5fa-109">The following bcp functions have been enhanced in [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] to provide improved metadata discovery:</span></span>  
  
-   [<span data-ttu-id="de5fa-110">bcp_columns</span><span class="sxs-lookup"><span data-stu-id="de5fa-110">bcp_columns</span></span>](../../native-client-odbc-extensions-bulk-copy-functions/bcp-columns.md)  
  
-   [<span data-ttu-id="de5fa-111">bcp_control</span><span class="sxs-lookup"><span data-stu-id="de5fa-111">bcp_control</span></span>](../../native-client-odbc-extensions-bulk-copy-functions/bcp-control.md)  
  
-   [<span data-ttu-id="de5fa-112">bcp_getcolfmt</span><span class="sxs-lookup"><span data-stu-id="de5fa-112">bcp_getcolfmt</span></span>](../../native-client-odbc-extensions-bulk-copy-functions/bcp-getcolfmt.md)  
  
-   [<span data-ttu-id="de5fa-113">bcp_readfmt</span><span class="sxs-lookup"><span data-stu-id="de5fa-113">bcp_readfmt</span></span>](../../native-client-odbc-extensions-bulk-copy-functions/bcp-readfmt.md)  
  
-   [<span data-ttu-id="de5fa-114">bcp_setcolfmt</span><span class="sxs-lookup"><span data-stu-id="de5fa-114">bcp_setcolfmt</span></span>](../../native-client-odbc-extensions-bulk-copy-functions/bcp-setcolfmt.md)  
  
 <span data-ttu-id="de5fa-115">使用[bcp_setbulkmode](../../native-client-odbc-extensions-bulk-copy-functions/bcp-setbulkmode.md)指定元資料格式時，您也會看到效能改進。</span><span class="sxs-lookup"><span data-stu-id="de5fa-115">You will also see a performance improvement when specifying metadata format using [bcp_setbulkmode](../../native-client-odbc-extensions-bulk-copy-functions/bcp-setbulkmode.md).</span></span>  
  
 <span data-ttu-id="de5fa-116">[bcp_control](../../native-client-odbc-extensions-bulk-copy-functions/bcp-control.md)有一個新的*eOption* ，可控制 bcp_readfmt 的行為： `BCPDELAYREADFMT` 。</span><span class="sxs-lookup"><span data-stu-id="de5fa-116">[bcp_control](../../native-client-odbc-extensions-bulk-copy-functions/bcp-control.md) has a new *eOption* to control the behavior of bcp_readfmt: `BCPDELAYREADFMT`.</span></span>  
  
 <span data-ttu-id="de5fa-117">[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] 已經強化了下列 ODBC 函數，以便提供改良的中繼資料探索：</span><span class="sxs-lookup"><span data-stu-id="de5fa-117">The following ODBC functions have been enhanced in [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] to provide improved metadata discovery:</span></span>  
  
-   [<span data-ttu-id="de5fa-118">SQLNumResultCols</span><span class="sxs-lookup"><span data-stu-id="de5fa-118">SQLNumResultCols</span></span>](../../native-client-odbc-api/sqlnumresultcols.md)  
  
-   [<span data-ttu-id="de5fa-119">SQLDescribeCol</span><span class="sxs-lookup"><span data-stu-id="de5fa-119">SQLDescribeCol</span></span>](../../native-client-odbc-api/sqldescribecol.md)  
  
-   [<span data-ttu-id="de5fa-120">SQLNumParams</span><span class="sxs-lookup"><span data-stu-id="de5fa-120">SQLNumParams</span></span>](../../native-client-odbc-api/sqlnumparams.md)  
  
-   [<span data-ttu-id="de5fa-121">SQLDescribeParam</span><span class="sxs-lookup"><span data-stu-id="de5fa-121">SQLDescribeParam</span></span>](../../native-client-odbc-api/sqldescribeparam.md)  
  
 <span data-ttu-id="de5fa-122">[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] 已經強化了下列 OLE DB 成員函數，以便提供改良的中繼資料探索：</span><span class="sxs-lookup"><span data-stu-id="de5fa-122">The following OLE DB member functions have been enhanced in [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] to provide improved metadata discovery:</span></span>  
  
-   <span data-ttu-id="de5fa-123">IColumnsInfo::GetColumnInfo</span><span class="sxs-lookup"><span data-stu-id="de5fa-123">IColumnsInfo::GetColumnInfo</span></span>  
  
-   <span data-ttu-id="de5fa-124">IColumnsRowset::GetColumnsRowset</span><span class="sxs-lookup"><span data-stu-id="de5fa-124">IColumnsRowset::GetColumnsRowset</span></span>  
  
-   <span data-ttu-id="de5fa-125">ICommandWithParameters::GetParameterInfo (如需詳細資訊，請參閱 [ICommandWithParameters](../../native-client-ole-db-interfaces/icommandwithparameters.md))</span><span class="sxs-lookup"><span data-stu-id="de5fa-125">ICommandWithParameters::GetParameterInfo (see [ICommandWithParameters](../../native-client-ole-db-interfaces/icommandwithparameters.md) for more information)</span></span>  
  
 <span data-ttu-id="de5fa-126">當您使用 IBCPSession::BCPSetBulkMode 來指定中繼資料格式時，也會看見效能改進</span><span class="sxs-lookup"><span data-stu-id="de5fa-126">You will also see a performance improvement when specifying metadata format using IBCPSession::BCPSetBulkMode</span></span>  
  
 <span data-ttu-id="de5fa-127">由於 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 加入了下列兩個預存程序，所以您可以在 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] Native Client 中進行改善的中繼資料探索：</span><span class="sxs-lookup"><span data-stu-id="de5fa-127">The improved metadata discovery in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client is possible because of the addition of two stored procedures in [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]:</span></span>  
  
-   <span data-ttu-id="de5fa-128">sp_describe_first_result_set</span><span class="sxs-lookup"><span data-stu-id="de5fa-128">sp_describe_first_result_set</span></span>  
  
-   <span data-ttu-id="de5fa-129">sp_describe_undeclared_parameters</span><span class="sxs-lookup"><span data-stu-id="de5fa-129">sp_describe_undeclared_parameters</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de5fa-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="de5fa-130">See Also</span></span>  
 [<span data-ttu-id="de5fa-131">SQL Server Native Client 功能</span><span class="sxs-lookup"><span data-stu-id="de5fa-131">SQL Server Native Client Features</span></span>](sql-server-native-client-features.md)  
  
  
