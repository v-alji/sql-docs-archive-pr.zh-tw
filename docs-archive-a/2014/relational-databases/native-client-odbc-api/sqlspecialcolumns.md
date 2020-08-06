---
title: SQLSpecialColumns |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLSpecialColumns function
ms.assetid: dffe02ed-8f79-4c9a-af34-98130bbe5462
author: rothja
ms.author: jroth
ms.openlocfilehash: c36ff73606e95ed7ee5e713b81acf7c177a42563
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595960"
---
# <a name="sqlspecialcolumns"></a>SQLSpecialColumns
   (*IdentifierType* SQL_BEST_ROWID) 要求資料列識別碼時， **SQLSpecialColumns**會針對) 以外的任何要求範圍，傳回空的結果集 (不 SQL_SCOPE_CURROW 任何資料列。 產生的結果集表示資料行只有在這個範圍中才是有效的。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 不支援識別碼的虛擬資料行。 **SQLSpecialColumns**結果集會將所有資料行識別為 SQL_PC_NOT_PSEUDO。  
  
 **SQLSpecialColumns**可以在靜態資料指標上執行。 嘗試在可更新的 (索引鍵集驅動或動態) 上執行**SQLSpecialColumns**時，會傳回 SQL_SUCCESS_WITH_INFO 指出資料指標類型已變更。  
  
## <a name="sqlspecialcolumns-support-for-enhanced-date-and-time-features"></a>增強型日期和時間功能的 SQLSpecialColumns 支援  
 如需日期/時間類型 DATA_TYPE、TYPE_NAME、COLUMN_SIZE、BUFFER_LENGTH 和 DECIMAL_DIGTS 之資料行傳回值的相關資訊，請參閱[目錄中繼資料](../native-client-odbc-date-time/metadata-catalog.md)。  
  
 如需更多一般資訊，請參閱[ODBC&#41;&#40;的日期和時間改善](../native-client-odbc-date-time/date-and-time-improvements-odbc.md)。  
  
## <a name="sqlspecialcolumns-support-for-large-clr-udts"></a>大型 CLR UDT 的 SQLSpecialColumns 支援  
 **SQLSpecialColumns**支援 (udt) 的大型 CLR 使用者定義類型。 如需詳細資訊，請參閱[&#40;ODBC&#41;的大型 CLR 使用者定義類型](../native-client/odbc/large-clr-user-defined-types-odbc.md)。  
  
## <a name="see-also"></a>另請參閱  
 [SQLSpecialColumns 函式](https://go.microsoft.com/fwlink/?LinkId=59371)   
 [ODBC API 實作詳細資料](odbc-api-implementation-details.md)  
  
  
