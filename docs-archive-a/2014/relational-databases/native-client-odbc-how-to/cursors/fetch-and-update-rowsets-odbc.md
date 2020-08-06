---
title: " (ODBC) 提取和更新資料列集 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- rowsets [ODBC]
ms.assetid: cf0eb3b4-8b72-49fc-a845-95edc360cf93
author: rothja
ms.author: jroth
ms.openlocfilehash: e09a3033e0883452ecd69b82c9375ed28c920da0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584477"
---
# <a name="fetch-and-update-rowsets-odbc"></a>提取和更新資料列集 (ODBC)
    
### <a name="to-fetch-and-update-rowsets"></a>提取和更新資料列集  
  
1.  （選擇性）使用 SQL_ROW_ARRAY_SIZE 呼叫[SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md) ，以變更資料列集中 (R) 的資料列數目。  
  
2.  呼叫[SQLFetch](https://go.microsoft.com/fwlink/?LinkId=58401)或[SQLFetchScroll](../../native-client-odbc-api/sqlfetchscroll.md)以取得資料列集。  
  
3.  如果使用繫結資料行，請將繫結資料行緩衝區中目前可用的資料值和資料長度用於資料列集。  
  
     如果使用未系結的資料行，則會針對每個使用 SQL_POSITION [SQLSetPos](https://go.microsoft.com/fwlink/?LinkId=58407)的資料列呼叫來設定資料指標位置。然後，針對每個未系結的資料行：  
  
    -   呼叫[SQLGetData](../../native-client-odbc-api/sqlgetdata.md)一次或多次，以取得資料列集最後一個系結資料行之後未系結資料行的資料。 對[SQLGetData](../../native-client-odbc-api/sqlgetdata.md)的呼叫應依照增加的資料行編號排序。  
  
    -   呼叫 [SQLGetData](../../native-client-odbc-api/sqlgetdata.md) 多次，以便從 text 或 image 資料行取得資料。  
  
4.  設定任何資料執行中的 text 或 image 資料行。  
  
5.  呼叫[SQLSetPos](https://go.microsoft.com/fwlink/?LinkId=58407)或[SQLBulkOperations](https://go.microsoft.com/fwlink/?LinkId=58398) ，以在資料列集內設定資料指標位置、重新整理、更新、刪除或加入 (s) 。  
  
     如果資料執行中的 text 或 image 資料行用於更新或加入作業，請處理它們。  
  
6.  （選擇性）執行定位的 UPDATE 或 DELETE 子句，指定[SQLGetCursorName](../../native-client-odbc-api/sqlgetcursorname.md)) 提供的資料指標名稱 (，並在相同的連接上使用不同的語句控制碼。  
  
## <a name="see-also"></a>另請參閱  
 [使用資料指標的 how to 主題 &#40;ODBC&#41;](using-cursors-how-to-topics-odbc.md)  
  
  
