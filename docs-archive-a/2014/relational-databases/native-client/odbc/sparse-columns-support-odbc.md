---
title: " (ODBC) 的稀疏資料行支援 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: 11ae959f-2fb6-4b85-ac5d-1476a82136d4
author: rothja
ms.author: jroth
ms.openlocfilehash: 076709f3f37e92492f7c3f8c20ee692416d9e867
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702857"
---
# <a name="sparse-columns-support-odbc"></a><span data-ttu-id="a3d6b-102">疏鬆資料行支援 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="a3d6b-102">Sparse Columns Support (ODBC)</span></span>
  <span data-ttu-id="a3d6b-103">本主題將描述 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC 對於疏鬆資料行的支援。</span><span class="sxs-lookup"><span data-stu-id="a3d6b-103">This topic describes [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC support for sparse columns.</span></span> <span data-ttu-id="a3d6b-104">如需示範 ODBC 支援的稀疏資料行範例，請參閱[在具有稀疏資料行的資料表上呼叫 SQLColumns](../../native-client-odbc-how-to/call-sqlcolumns-on-a-table-with-sparse-columns.md)。</span><span class="sxs-lookup"><span data-stu-id="a3d6b-104">For a sample demonstrating ODBC support for sparse columns, see [Call SQLColumns on a Table with Sparse Columns](../../native-client-odbc-how-to/call-sqlcolumns-on-a-table-with-sparse-columns.md).</span></span> <span data-ttu-id="a3d6b-105">如需稀疏資料行的詳細資訊，請參閱[SQL Server Native Client 中的稀疏資料行支援](../features/sparse-columns-support-in-sql-server-native-client.md)。</span><span class="sxs-lookup"><span data-stu-id="a3d6b-105">For more information about sparse columns, see [Sparse Columns Support in SQL Server Native Client](../features/sparse-columns-support-in-sql-server-native-client.md).</span></span>  
  
## <a name="statement-metadata"></a><span data-ttu-id="a3d6b-106">陳述式中繼資料</span><span class="sxs-lookup"><span data-stu-id="a3d6b-106">Statement Metadata</span></span>  
 <span data-ttu-id="a3d6b-107">應用程式參數描述項 (APD) 描述項欄位和 SQL_SOPT_SS_NAME_SCOPE 陳述式屬性都會接受額外的值 SQL_SS_NAME_SCOPE_EXTENDED 和 SQL_SS_NAME_SCOPE_SPARSE_COLUMN_SET。</span><span class="sxs-lookup"><span data-stu-id="a3d6b-107">The application parameter descriptor (APD) descriptor field and SQL_SOPT_SS_NAME_SCOPE statement attribute accepts the additional values SQL_SS_NAME_SCOPE_EXTENDED and SQL_SS_NAME_SCOPE_SPARSE_COLUMN_SET.</span></span> <span data-ttu-id="a3d6b-108">這些值會指定哪些資料行包含在[SQLColumns](../../native-client-odbc-api/sqlcolumns.md)所傳回的結果集中。</span><span class="sxs-lookup"><span data-stu-id="a3d6b-108">These values specify which columns are included in the result set returned by [SQLColumns](../../native-client-odbc-api/sqlcolumns.md).</span></span> <span data-ttu-id="a3d6b-109">如需 SQL_SOPT_SS_NAME_SCOPE 的詳細資訊，請參閱[SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md)。</span><span class="sxs-lookup"><span data-stu-id="a3d6b-109">For more information about SQL_SOPT_SS_NAME_SCOPE, see [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md).</span></span>  
  
 <span data-ttu-id="a3d6b-110">新的實作資料列描述項 (IRD) (稱為 SQL_CA_SS_IS_COLUMN_SET 的唯讀 SQLSMALLINT 欄位) 可用來判斷資料行是否為 XML `column_set` 值。</span><span class="sxs-lookup"><span data-stu-id="a3d6b-110">A new implementation row descriptor (IRD), a read-only SQLSMALLINT field called SQL_CA_SS_IS_COLUMN_SET, can be used to determine if a column is an XML `column_set` value.</span></span> <span data-ttu-id="a3d6b-111">SQL_CA_SS_IS_COLUMN_SET 會採用 SQL_TRUE 和 SQL_FALSE 值。</span><span class="sxs-lookup"><span data-stu-id="a3d6b-111">SQL_CA_SS_IS_COLUMN_SET takes the values SQL_TRUE and SQL_FALSE.</span></span>  
  
## <a name="catalog-metadata"></a><span data-ttu-id="a3d6b-112">目錄中繼資料</span><span class="sxs-lookup"><span data-stu-id="a3d6b-112">Catalog Metadata</span></span>  
 <span data-ttu-id="a3d6b-113">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (SS_IS_SPARSE 和 SS_IS_COLUMN_SET) 的兩個特定資料行加入[SQLColumns](../../native-client-odbc-api/sqlcolumns.md)的結果集。</span><span class="sxs-lookup"><span data-stu-id="a3d6b-113">Two [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] specific columns (SS_IS_SPARSE and SS_IS_COLUMN_SET) have been added to the result set for [SQLColumns](../../native-client-odbc-api/sqlcolumns.md).</span></span>  
  
## <a name="odbc-function-support-for-sparse-columns"></a><span data-ttu-id="a3d6b-114">疏鬆資料行的 ODBC 函數支援</span><span class="sxs-lookup"><span data-stu-id="a3d6b-114">ODBC Function Support for Sparse Columns</span></span>  
 <span data-ttu-id="a3d6b-115">下列 ODBC 函數已經更新為支援 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 中的疏鬆資料行：</span><span class="sxs-lookup"><span data-stu-id="a3d6b-115">The following ODBC functions have been updated to support sparse columns in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client:</span></span>  
  
-   [<span data-ttu-id="a3d6b-116">SQLColAttribute</span><span class="sxs-lookup"><span data-stu-id="a3d6b-116">SQLColAttribute</span></span>](../../native-client-odbc-api/sqlcolattribute.md)  
  
-   [<span data-ttu-id="a3d6b-117">SQLColumns</span><span class="sxs-lookup"><span data-stu-id="a3d6b-117">SQLColumns</span></span>](../../native-client-odbc-api/sqlcolumns.md)  
  
-   [<span data-ttu-id="a3d6b-118">SQLGetDescField</span><span class="sxs-lookup"><span data-stu-id="a3d6b-118">SQLGetDescField</span></span>](../../native-client-odbc-api/sqlgetdescfield.md)  
  
-   [<span data-ttu-id="a3d6b-119">SQLSetDescField</span><span class="sxs-lookup"><span data-stu-id="a3d6b-119">SQLSetDescField</span></span>](../../native-client-odbc-api/sqlsetdescfield.md)  
  
-   [<span data-ttu-id="a3d6b-120">SQLSetStmtAttr</span><span class="sxs-lookup"><span data-stu-id="a3d6b-120">SQLSetStmtAttr</span></span>](../../native-client-odbc-api/sqlsetstmtattr.md)  
  
## <a name="see-also"></a><span data-ttu-id="a3d6b-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a3d6b-121">See Also</span></span>  
 [<span data-ttu-id="a3d6b-122">SQL Server Native Client &#40;ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="a3d6b-122">SQL Server Native Client &#40;ODBC&#41;</span></span>](sql-server-native-client-odbc.md)  
  
  
