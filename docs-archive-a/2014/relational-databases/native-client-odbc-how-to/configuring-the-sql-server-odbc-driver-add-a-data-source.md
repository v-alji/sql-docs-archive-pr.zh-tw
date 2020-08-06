---
title: 將資料來源加入 (ODBC) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- data sources [ODBC]
ms.assetid: b4ac6f0e-8e6a-4b1a-9a7e-60e0a69b2180
author: rothja
ms.author: jroth
ms.openlocfilehash: 519990e9dd9d84f75c4efc6c76b910f0a359f52f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594047"
---
# <a name="add-a-data-source-odbc"></a><span data-ttu-id="6149c-102">加入資料來源 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="6149c-102">Add a Data Source (ODBC)</span></span>
  <span data-ttu-id="6149c-103">您可以使用 ODBC 管理員，以程式設計方式 (使用[SQLConfigDataSource](../native-client-odbc-api/sqlconfigdatasource.md)) 或藉由建立檔案來加入資料來源。</span><span class="sxs-lookup"><span data-stu-id="6149c-103">You can add a data source by using ODBC Administrator, programmatically (by using [SQLConfigDataSource](../native-client-odbc-api/sqlconfigdatasource.md)), or by creating a file.</span></span>  
  
### <a name="to-add-a-data-source-by-using-odbc-administrator"></a><span data-ttu-id="6149c-104">使用 ODBC 管理員加入資料來源</span><span class="sxs-lookup"><span data-stu-id="6149c-104">To add a data source by using ODBC Administrator</span></span>  
  
1.  <span data-ttu-id="6149c-105">從 [**控制台**] 中，存取 [系統**管理工具**]，然後\*\* (ODBC) 的 [資料來源\*\*]。</span><span class="sxs-lookup"><span data-stu-id="6149c-105">From the **Control Panel**, access **Administrative Tools** and then **Data Sources (ODBC)**.</span></span> <span data-ttu-id="6149c-106">或者，您可以叫用 odbcad32.exe。</span><span class="sxs-lookup"><span data-stu-id="6149c-106">Alternatively, you can invoke odbcad32.exe.</span></span>  
  
2.  <span data-ttu-id="6149c-107">按一下 [**使用者 DSN**]、[**系統 DSN**] 或 [檔案**DSN** ] 索引標籤，然後按一下 [**新增**]。</span><span class="sxs-lookup"><span data-stu-id="6149c-107">Click the **User DSN**, **System DSN**, or **File DSN** tab, and then click **Add**.</span></span>  
  
3.  <span data-ttu-id="6149c-108">按一下 [ **SQL Server**]，然後按一下 **[完成]**。</span><span class="sxs-lookup"><span data-stu-id="6149c-108">Click **SQL Server**, and then click **Finish**.</span></span>  
  
4.  <span data-ttu-id="6149c-109">完成「建立新的資料來源至 SQL Server」精靈中的步驟。</span><span class="sxs-lookup"><span data-stu-id="6149c-109">Complete the Steps in the Create a New Data Source to SQL Server Wizard.</span></span>  
  
### <a name="to-add-a-data-source-programmatically"></a><span data-ttu-id="6149c-110">以程式設計方式加入資料來源</span><span class="sxs-lookup"><span data-stu-id="6149c-110">To add a data source programmatically</span></span>  
  
1.  <span data-ttu-id="6149c-111">呼叫[SQLConfigDataSource](../native-client-odbc-api/sqlconfigdatasource.md) ，並將第二個參數設定為 ODBC_ADD_DSN 或 ODBC_ADD_SYS_DSN。</span><span class="sxs-lookup"><span data-stu-id="6149c-111">Call [SQLConfigDataSource](../native-client-odbc-api/sqlconfigdatasource.md) with the second parameter set to either ODBC_ADD_DSN or ODBC_ADD_SYS_DSN.</span></span>  
  
### <a name="to-add-a-file-data-source"></a><span data-ttu-id="6149c-112">加入檔案資料來源</span><span class="sxs-lookup"><span data-stu-id="6149c-112">To add a file data source</span></span>  
  
1.  <span data-ttu-id="6149c-113">在連接字串中使用 SAVEFILE = file_name 參數來呼叫[SQLDriverConnect](../native-client-odbc-api/sqldriverconnect.md) 。</span><span class="sxs-lookup"><span data-stu-id="6149c-113">Call [SQLDriverConnect](../native-client-odbc-api/sqldriverconnect.md) with a SAVEFILE=file_name parameter in the connect string.</span></span> <span data-ttu-id="6149c-114">如果連接成功，ODBC 驅動程式會利用 SAVEFILE 參數所指向位置中的連接參數建立檔案資料來源。</span><span class="sxs-lookup"><span data-stu-id="6149c-114">If the connect is successful, the ODBC driver creates a file data source with the connection parameters in the location pointed to by the SAVEFILE parameter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6149c-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6149c-115">See Also</span></span>  
 [<span data-ttu-id="6149c-116">設定 SQL Server ODBC 驅動程式的使用說明主題</span><span class="sxs-lookup"><span data-stu-id="6149c-116">Configuring the SQL Server ODBC Driver How-to Topics</span></span>](../../database-engine/dev-guide/configuring-the-sql-server-odbc-driver-how-to-topics.md)  
  
  
