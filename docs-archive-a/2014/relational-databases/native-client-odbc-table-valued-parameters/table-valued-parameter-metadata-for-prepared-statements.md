---
title: 備妥之語句的資料表值參數中繼資料 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (ODBC), metadata for prepared statements
ms.assetid: fd2fc705-2e98-4011-9822-c7e6cca4a535
author: rothja
ms.author: jroth
ms.openlocfilehash: ad1394bd5e5bedc69a98308ba67a98434559c146
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709305"
---
# <a name="table-valued-parameter-metadata-for-prepared-statements"></a><span data-ttu-id="2c4f6-102">已備妥之陳述式的資料表值參數中繼資料</span><span class="sxs-lookup"><span data-stu-id="2c4f6-102">Table-Valued Parameter Metadata for Prepared Statements</span></span>
  <span data-ttu-id="2c4f6-103">應用程式可以透過 SQLNumParams 和 SQLDescribeParam 取得已備妥之程序呼叫的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="2c4f6-103">An application can obtain metadata for a prepared procedure call through SQLNumParams and SQLDescribeParam.</span></span> <span data-ttu-id="2c4f6-104">若為數據表值參數， *DataTypePtr*會設定為 SQL_SS_TABLE。</span><span class="sxs-lookup"><span data-stu-id="2c4f6-104">For table-valued parameters, *DataTypePtr* is set to SQL_SS_TABLE.</span></span> <span data-ttu-id="2c4f6-105">SQL_CA_SS_TYPE_NAME、SQL_CA_SS_CATALOG_NAME 和 SQL_CA_SS_SCHEMA_NAME 可以透過 SQLGetDescField 取得額外的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="2c4f6-105">Additional metadata is available through SQLGetDescField for SQL_CA_SS_TYPE_NAME, SQL_CA_SS_CATALOG_NAME, and SQL_CA_SS_SCHEMA_NAME.</span></span>  
  
 <span data-ttu-id="2c4f6-106">SQL_CA_SS_TYPE_NAME、SQL_CA_SS_CATALOG_NAME 和 SQL_CA_SS_SCHEMA_NAME 可以與 SQLColumns 搭配使用，以取得與資料表值參數相關聯之資料表類型的資料行中繼資料。</span><span class="sxs-lookup"><span data-stu-id="2c4f6-106">SQL_CA_SS_TYPE_NAME, SQL_CA_SS_CATALOG_NAME, and SQL_CA_SS_SCHEMA_NAME can be used with SQLColumns to obtain column metadata for table types associated with table-valued parameters.</span></span> <span data-ttu-id="2c4f6-107">在此情況下，在呼叫 SQLColumns 之前，必須將 SQL_SOPT_SS_NAME_SCOPE 設為 SQL_SS_NAME_SCOPE_TABLE_TYPE。</span><span class="sxs-lookup"><span data-stu-id="2c4f6-107">In this case, SQL_SOPT_SS_NAME_SCOPE must be set to SQL_SS_NAME_SCOPE_TABLE_TYPE before SQLColumns is called.</span></span> <span data-ttu-id="2c4f6-108">當應用程式完成資料表值參數資料行中繼資料的擷取時，SQL_SOPT_SS_NAME_SCOPE 應該設回預設值 SQL_SS_NAME_SCOPE_TABLE。</span><span class="sxs-lookup"><span data-stu-id="2c4f6-108">SQL_SOPT_SS_NAME_SCOPE should then be set back to the default value, SQL_SS_NAME_SCOPE_TABLE, when the application has finished retrieving table-valued parameter column metadata.</span></span>  
  
 <span data-ttu-id="2c4f6-109">SQL_CA_SS_TYPE_NAME、SQL_CA_SS_CATALOG_NAME 和 SQL_CA_SS_SCHEMA_NAME 也可以搭配 CLR 使用者定義型別參數使用。</span><span class="sxs-lookup"><span data-stu-id="2c4f6-109">SQL_CA_SS_TYPE_NAME , SQL_CA_SS_CATALOG_NAME, and SQL_CA_SS_SCHEMA_NAME can also be used with CLR user-defined type parameters.</span></span>  
  
 <span data-ttu-id="2c4f6-110">您無法針對不是預存程序呼叫的已備妥陳述式來取得資料表值參數中繼資料。</span><span class="sxs-lookup"><span data-stu-id="2c4f6-110">You cannot obtain table-valued parameter metadata for prepared statements that are not stored procedure calls.</span></span> <span data-ttu-id="2c4f6-111">如果您嘗試這樣做，應用程式會傳回 SQL_ERROR，其中包含 SQLSTATE 42000 和「語法錯誤或違規存取」訊息。</span><span class="sxs-lookup"><span data-stu-id="2c4f6-111">If you try to do this, the application returns SQL_ERROR with SQLSTATE 42000 and the message "Syntax error or access violation".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c4f6-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2c4f6-112">See Also</span></span>  
 [<span data-ttu-id="2c4f6-113">ODBC&#41;&#40;的資料表值參數</span><span class="sxs-lookup"><span data-stu-id="2c4f6-113">Table-Valued Parameters &#40;ODBC&#41;</span></span>](table-valued-parameters-odbc.md)  
  
  
