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
# <a name="delete-a-data-source-odbc"></a><span data-ttu-id="5a3c7-102">刪除資料來源 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="5a3c7-102">Delete a Data Source (ODBC)</span></span>
  <span data-ttu-id="5a3c7-103">您可以使用 ODBC 管理員來刪除資料來源、使用[SQLConfigDataSource](../native-client-odbc-api/sqlconfigdatasource.md)) 以程式設計方式 (，或在檔案資料來源名稱) 時刪除檔案 (。</span><span class="sxs-lookup"><span data-stu-id="5a3c7-103">You can delete a data source by using ODBC Administrator, programmatically (by using [SQLConfigDataSource](../native-client-odbc-api/sqlconfigdatasource.md)), or by deleting a file (if a file data source name).</span></span>  
  
### <a name="to-delete-a-data-source-by-using-odbc-administrator"></a><span data-ttu-id="5a3c7-104">使用 ODBC 管理員刪除資料來源</span><span class="sxs-lookup"><span data-stu-id="5a3c7-104">To delete a data source by using ODBC Administrator</span></span>  
  
1.  <span data-ttu-id="5a3c7-105">在 [**控制台**] 中，開啟 [系統**管理工具**]，然後按兩下 [ \*\* (ODBC) 的資料來源\*\*]。</span><span class="sxs-lookup"><span data-stu-id="5a3c7-105">In **Control Panel**, open **Administrative Tools**, and then double-click **Data Sources (ODBC)**.</span></span> <span data-ttu-id="5a3c7-106">或者，您也可以從命令提示字元執行 odbcad32.exe。</span><span class="sxs-lookup"><span data-stu-id="5a3c7-106">Alternatively, you can run odbcad32.exe from the command prompt.</span></span>  
  
2.  <span data-ttu-id="5a3c7-107">按一下 [**使用者 DSN**]、[**系統 DSN**] 或 [檔案**DSN** ] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="5a3c7-107">Click the **User DSN**, **System DSN**, or **File DSN** tab.</span></span>  
  
3.  <span data-ttu-id="5a3c7-108">按一下要刪除的資料來源。</span><span class="sxs-lookup"><span data-stu-id="5a3c7-108">Click the data source to delete.</span></span>  
  
4.  <span data-ttu-id="5a3c7-109">按一下 [**移除**]，然後確認刪除。</span><span class="sxs-lookup"><span data-stu-id="5a3c7-109">Click **Remove**, and then confirm the deletion.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5a3c7-110">範例</span><span class="sxs-lookup"><span data-stu-id="5a3c7-110">Example</span></span>  
 <span data-ttu-id="5a3c7-111">若要以程式設計方式刪除資料來源，請使用 ODBC_REMOVE_DSN 或 ODBC_REMOVE_SYS_DSN 做為第二個參數來呼叫[SQLConfigDataSource](../native-client-odbc-api/sqlconfigdatasource.md) 。</span><span class="sxs-lookup"><span data-stu-id="5a3c7-111">To programmatically delete a data source, call [SQLConfigDataSource](../native-client-odbc-api/sqlconfigdatasource.md) using either ODBC_REMOVE_DSN or ODBC_REMOVE_SYS_DSN as the second parameter.</span></span>  
  
 <span data-ttu-id="5a3c7-112">下列範例會示範如何以程式設計的方式刪除資料來源。</span><span class="sxs-lookup"><span data-stu-id="5a3c7-112">The following sample shows how you can programmatically delete a data source.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5a3c7-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5a3c7-113">See Also</span></span>  
 [<span data-ttu-id="5a3c7-114">設定 SQL Server ODBC 驅動程式的使用說明主題</span><span class="sxs-lookup"><span data-stu-id="5a3c7-114">Configuring the SQL Server ODBC Driver How-to Topics</span></span>](../../database-engine/dev-guide/configuring-the-sql-server-odbc-driver-how-to-topics.md)  
  
  
