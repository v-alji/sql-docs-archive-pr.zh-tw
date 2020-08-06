---
title: 刪除 (ODBC) 的資料來源 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- data sources [ODBC]
ms.assetid: 910e3e16-7b91-49d8-80bb-b4243926afaa
author: rothja
ms.author: jroth
ms.openlocfilehash: 6e8acd6414b39b317ff0fcfe1b7b9fbab38ae0a6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594045"
---
# <a name="delete-a-data-source-odbc"></a>刪除資料來源 (ODBC)
  您可以使用 ODBC 管理員來刪除資料來源、使用[SQLConfigDataSource](../native-client-odbc-api/sqlconfigdatasource.md)) 以程式設計方式 (，或在檔案資料來源名稱) 時刪除檔案 (。  
  
### <a name="to-delete-a-data-source-by-using-odbc-administrator"></a>使用 ODBC 管理員刪除資料來源  
  
1.  在 [**控制台**] 中，開啟 [系統**管理工具**]，然後按兩下 [ ** (ODBC) 的資料來源**]。 或者，您也可以從命令提示字元執行 odbcad32.exe。  
  
2.  按一下 [**使用者 DSN**]、[**系統 DSN**] 或 [檔案**DSN** ] 索引標籤。  
  
3.  按一下要刪除的資料來源。  
  
4.  按一下 [**移除**]，然後確認刪除。  
  
## <a name="example"></a>範例  
 若要以程式設計方式刪除資料來源，請使用 ODBC_REMOVE_DSN 或 ODBC_REMOVE_SYS_DSN 做為第二個參數來呼叫[SQLConfigDataSource](../native-client-odbc-api/sqlconfigdatasource.md) 。  
  
 下列範例會示範如何以程式設計的方式刪除資料來源。  
  
```  
// remove_odbc_data_source.cpp  
// compile with: ODBCCP32.lib user32.lib  
#include <iostream>  
#include <windows.h>  
#include <odbcinst.h>  
  
int main() {   
   LPCSTR provider = "SQL Server";   // Windows SQL Server Driver  
   LPCSTR provider = "SQL Server";   // Windows SQL Server driver  
   LPCSTR provider2 = "SQL Server Native Client 11.0";   // SQL Server 2012 Native Client driver  
   LPCSTR dsnname = "DSN=data2";  
   BOOL retval = SQLConfigDataSource(NULL, ODBC_REMOVE_DSN, provider, dsnname);  
   std::cout << retval;   // 1 if successful  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [設定 SQL Server ODBC 驅動程式的使用說明主題](../../database-engine/dev-guide/configuring-the-sql-server-odbc-driver-how-to-topics.md)  
  
  
