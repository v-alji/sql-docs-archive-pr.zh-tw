---
title: 建立 SQL Server Native Client ODBC 驅動程式應用程式 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC, architecture
- SQL Server Native Client ODBC driver, creating applications
- ODBC function calls
- ODBC, header files
- ODBC applications
- ODBC applications, creating
- SQL Server Native Client ODBC driver, extensions
- applications [SQL Server Native Client]
- SQL Server Native Client ODBC driver, ODBC architecture
- extensions [ODBC]
- ODBC, driver extensions
- function calls [ODBC]
ms.assetid: c83c36e2-734e-4960-bc7e-92235910bc6f
author: rothja
ms.author: jroth
ms.openlocfilehash: c8a1719f8b60885810d9b2f8a1f1023a7ffe6e47
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706390"
---
# <a name="creating-a-sql-server-native-client-odbc-driver-application"></a><span data-ttu-id="cc78a-102">建立 SQL Server Native Client ODBC 驅動程式應用程式</span><span class="sxs-lookup"><span data-stu-id="cc78a-102">Creating a SQL Server Native Client ODBC Driver Application</span></span>
  <span data-ttu-id="cc78a-103">ODBC 架構包含四個執行下列函數的元件。</span><span class="sxs-lookup"><span data-stu-id="cc78a-103">ODBC architecture has four components that perform the following functions.</span></span>  
  
|<span data-ttu-id="cc78a-104">元件</span><span class="sxs-lookup"><span data-stu-id="cc78a-104">Component</span></span>|<span data-ttu-id="cc78a-105">函式</span><span class="sxs-lookup"><span data-stu-id="cc78a-105">Function</span></span>|  
|---------------|--------------|  
|<span data-ttu-id="cc78a-106">應用程式</span><span class="sxs-lookup"><span data-stu-id="cc78a-106">Application</span></span>|<span data-ttu-id="cc78a-107">呼叫 ODBC 函數與 ODBC 資料來源進行通訊、提交 SQL 陳述式，以及處理結果集。</span><span class="sxs-lookup"><span data-stu-id="cc78a-107">Calls ODBC functions to communicate with an ODBC data source, submits SQL statements, and processes result sets.</span></span>|  
|<span data-ttu-id="cc78a-108">驅動程式管理員</span><span class="sxs-lookup"><span data-stu-id="cc78a-108">Driver Manager</span></span>|<span data-ttu-id="cc78a-109">管理應用程式與應用程式所使用之所有 ODBC 驅動程式之間的通訊。</span><span class="sxs-lookup"><span data-stu-id="cc78a-109">Manages communication between an application and all ODBC drivers used by the application.</span></span>|  
|<span data-ttu-id="cc78a-110">驅動程式</span><span class="sxs-lookup"><span data-stu-id="cc78a-110">Driver</span></span>|<span data-ttu-id="cc78a-111">處理來自應用程式的所有 ODBC 函數呼叫、連接到資料來源、將 SQL 陳述式從應用程式傳遞到資料來源，以及將結果傳回到應用程式。</span><span class="sxs-lookup"><span data-stu-id="cc78a-111">Processes all ODBC function calls from the application, connects to a data source, passes SQL statements from the application to the data source, and returns results to the application.</span></span> <span data-ttu-id="cc78a-112">如果必要，取動程式會將 ODBC SQL 從應用程式轉譯成資料來源所使用的原生 SQL。</span><span class="sxs-lookup"><span data-stu-id="cc78a-112">If necessary, the driver translates ODBC SQL from the application to native SQL used by the data source.</span></span>|  
|<span data-ttu-id="cc78a-113">資料來源</span><span class="sxs-lookup"><span data-stu-id="cc78a-113">Data source</span></span>|<span data-ttu-id="cc78a-114">包含驅動程式在 DBMS 中存取特定資料執行個體所需的所有資訊。</span><span class="sxs-lookup"><span data-stu-id="cc78a-114">Contains all information a driver needs to access a specific instance of data in a DBMS.</span></span>|  
  
 <span data-ttu-id="cc78a-115">使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native CLIENT ODBC 驅動程式與實例進行通訊的應用程式會 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="cc78a-115">An application that uses the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver to communicate with an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] performs the following tasks:</span></span>  
  
-   <span data-ttu-id="cc78a-116">與資料來源連接</span><span class="sxs-lookup"><span data-stu-id="cc78a-116">Connects with a data source</span></span>  
  
-   <span data-ttu-id="cc78a-117">將 SQL 陳述式傳送到資料來源</span><span class="sxs-lookup"><span data-stu-id="cc78a-117">Sends SQL statements to the data source</span></span>  
  
-   <span data-ttu-id="cc78a-118">從資料來源處理陳述式的結果</span><span class="sxs-lookup"><span data-stu-id="cc78a-118">Processes the results of statements from the data source</span></span>  
  
-   <span data-ttu-id="cc78a-119">處理錯誤與訊息</span><span class="sxs-lookup"><span data-stu-id="cc78a-119">Processes errors and messages</span></span>  
  
-   <span data-ttu-id="cc78a-120">結束資料來源的連接</span><span class="sxs-lookup"><span data-stu-id="cc78a-120">Terminates the connection to the data source</span></span>  
  
 <span data-ttu-id="cc78a-121">針對 Native Client ODBC 驅動程式撰寫的更複雜應用程式 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 可能也會執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="cc78a-121">A more complex application written for the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver might also perform the following tasks:</span></span>  
  
-   <span data-ttu-id="cc78a-122">使用資料指標控制結果集中的位置</span><span class="sxs-lookup"><span data-stu-id="cc78a-122">Use cursors to control location in a result set</span></span>  
  
-   <span data-ttu-id="cc78a-123">要求交易控制的認可或復原作業</span><span class="sxs-lookup"><span data-stu-id="cc78a-123">Request commit or rollback operations for transaction control</span></span>  
  
-   <span data-ttu-id="cc78a-124">執行包含兩部或多部伺服器的分散式交易</span><span class="sxs-lookup"><span data-stu-id="cc78a-124">Perform distributed transactions involving two or more servers</span></span>  
  
-   <span data-ttu-id="cc78a-125">在遠端伺服器上執行預存程序</span><span class="sxs-lookup"><span data-stu-id="cc78a-125">Run stored procedures on the remote server</span></span>  
  
-   <span data-ttu-id="cc78a-126">呼叫目錄函數來查詢結果集的屬性</span><span class="sxs-lookup"><span data-stu-id="cc78a-126">Call catalog functions to inquire about the attributes of a result set</span></span>  
  
-   <span data-ttu-id="cc78a-127">執行大量複製作業</span><span class="sxs-lookup"><span data-stu-id="cc78a-127">Perform bulk copy operations</span></span>  
  
-   <span data-ttu-id="cc78a-128">管理大型資料 (\*\*Varchar (max) \*\*、 **Nvarchar (max) **和**Varbinary (max**) 資料行) 作業</span><span class="sxs-lookup"><span data-stu-id="cc78a-128">Manage large data (**varchar(max)**, **nvarchar(max)**, and **varbinary(max)** columns) operations</span></span>  
  
-   <span data-ttu-id="cc78a-129">設定資料庫鏡像時，使用重新連接邏輯來簡化容錯移轉</span><span class="sxs-lookup"><span data-stu-id="cc78a-129">Use reconnection logic to facilitate failover when database mirroring is configured</span></span>  
  
-   <span data-ttu-id="cc78a-130">記錄效能資料和長時間執行的查詢</span><span class="sxs-lookup"><span data-stu-id="cc78a-130">Log performance data and long-running queries</span></span>  
  
 <span data-ttu-id="cc78a-131">若要進行 ODBC 函數呼叫，C 或 C++ 應用程式必須包含 sql.h、sqlext.h 和 sqltypes.h 標頭檔。</span><span class="sxs-lookup"><span data-stu-id="cc78a-131">To make ODBC function calls, a C or C++ application must include the sql.h, sqlext.h, and sqltypes.h header files.</span></span> <span data-ttu-id="cc78a-132">若要呼叫 ODBC 安裝程式 API 函數，應用程式必須包含 odbcinst.h 標頭檔。</span><span class="sxs-lookup"><span data-stu-id="cc78a-132">To make calls to the ODBC installer API functions, an application must include the odbcinst.h header file.</span></span> <span data-ttu-id="cc78a-133">Unicode ODBC 應用程式必須包含 sqlucode.h 標頭檔。</span><span class="sxs-lookup"><span data-stu-id="cc78a-133">A Unicode ODBC application must include the sqlucode.h header file.</span></span> <span data-ttu-id="cc78a-134">ODBC 應用程式必須與 odbc32.lib 檔連結。</span><span class="sxs-lookup"><span data-stu-id="cc78a-134">ODBC applications must be linked with the odbc32.lib file.</span></span> <span data-ttu-id="cc78a-135">呼叫 ODBC 安裝程式 API 函數的 ODBC 應用程式必須與 odbccp32.lib 檔連結。</span><span class="sxs-lookup"><span data-stu-id="cc78a-135">ODBC applications that call the ODBC installer API functions must be linked with the odbccp32.lib file.</span></span> <span data-ttu-id="cc78a-136">這些檔案包含在 Windows Platform SDK 中。</span><span class="sxs-lookup"><span data-stu-id="cc78a-136">These files are included in the Windows Platform SDK.</span></span>  
  
 <span data-ttu-id="cc78a-137">許多 ODBC 驅動程式（包括 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native CLIENT odbc 驅動程式）都會提供驅動程式專屬的 odbc 延伸模組。</span><span class="sxs-lookup"><span data-stu-id="cc78a-137">Many ODBC drivers, including the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver, offer driver-specific ODBC extensions.</span></span> <span data-ttu-id="cc78a-138">若要利用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native CLIENT ODBC 驅動程式特定的擴充功能，應用程式應該包含 sqlncli 標頭檔。</span><span class="sxs-lookup"><span data-stu-id="cc78a-138">To take advantage of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver-specific extensions, an application should include the sqlncli.h header file.</span></span> <span data-ttu-id="cc78a-139">這個標頭檔包含：</span><span class="sxs-lookup"><span data-stu-id="cc78a-139">This header file contains:</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]<span data-ttu-id="cc78a-140">Native Client ODBC 驅動程式特定的連接屬性。</span><span class="sxs-lookup"><span data-stu-id="cc78a-140">Native Client ODBC driver-specific connection attributes.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]<span data-ttu-id="cc78a-141">Native Client ODBC 驅動程式特定的語句屬性。</span><span class="sxs-lookup"><span data-stu-id="cc78a-141">Native Client ODBC driver-specific statement attributes.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]<span data-ttu-id="cc78a-142">Native Client ODBC 驅動程式特有的資料行屬性。</span><span class="sxs-lookup"><span data-stu-id="cc78a-142">Native Client ODBC driver-specific column attributes.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="cc78a-143">專屬的資料類型。</span><span class="sxs-lookup"><span data-stu-id="cc78a-143">-specific data types.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="cc78a-144">專屬的使用者定義資料類型。</span><span class="sxs-lookup"><span data-stu-id="cc78a-144">-specific user-defined data types.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]<span data-ttu-id="cc78a-145">Native Client ODBC 驅動程式特定的[SQLGetInfo](../../native-client-odbc-api/sqlgetinfo.md)類型。</span><span class="sxs-lookup"><span data-stu-id="cc78a-145">Native Client ODBC driver-specific [SQLGetInfo](../../native-client-odbc-api/sqlgetinfo.md) types.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]<span data-ttu-id="cc78a-146">Native Client ODBC 驅動程式診斷欄位。</span><span class="sxs-lookup"><span data-stu-id="cc78a-146">Native Client ODBC driver diagnostics fields.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="cc78a-147">專屬的診斷動態函數程式碼。</span><span class="sxs-lookup"><span data-stu-id="cc78a-147">-specific diagnostic dynamic function codes.</span></span>  
  
-   <span data-ttu-id="cc78a-148">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 專屬原生 C 資料類型的 C/C++ 類型定義 (當資料行繫結至 C 資料類型 SQL_C_BINARY 時傳回)。</span><span class="sxs-lookup"><span data-stu-id="cc78a-148">C/C++ type definitions for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-specific native C data types (returned when columns bound to C data type SQL_C_BINARY).</span></span>  
  
-   <span data-ttu-id="cc78a-149">SQLPERF 資料結構的類型定義。</span><span class="sxs-lookup"><span data-stu-id="cc78a-149">Type definition for the SQLPERF data structure.</span></span>  
  
-   <span data-ttu-id="cc78a-150">支援透過 ODBC 連接使用大量複製 API 的大量複製巨集和原型。</span><span class="sxs-lookup"><span data-stu-id="cc78a-150">Bulk copy macros and prototypes to support bulk copy API usage through an ODBC connection.</span></span>  
  
-   <span data-ttu-id="cc78a-151">針對連結之伺服器及其目錄的清單，呼叫分散式查詢中繼資料 API 函數。</span><span class="sxs-lookup"><span data-stu-id="cc78a-151">Call the distributed query metadata API functions for lists of linked servers and their catalogs.</span></span>  
  
 <span data-ttu-id="cc78a-152">任何使用 Native Client ODBC 驅動程式之大量複製功能的 C 或 c + + ODBC 應用程式，都 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 必須與 sqlncli11 連結。</span><span class="sxs-lookup"><span data-stu-id="cc78a-152">Any C or C++ ODBC application that uses the bulk copy feature of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver must be linked with the sqlncli11.lib file.</span></span> <span data-ttu-id="cc78a-153">呼叫分散式查詢中繼資料 API 函數的應用程式也必須與 sqlncli11.lib 連結。</span><span class="sxs-lookup"><span data-stu-id="cc78a-153">Applications calling the distributed query metadata API functions must also be linked with sqlncli11.lib.</span></span> <span data-ttu-id="cc78a-154">Sqlncli 和 sqlncli11 檔案會散發為 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 開發人員工具的一部分。</span><span class="sxs-lookup"><span data-stu-id="cc78a-154">The sqlncli.h and sqlncli11.lib files are distributed as part of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] developer's tools.</span></span> <span data-ttu-id="cc78a-155">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的 Include 和 Lib 目錄應該位於編譯器的 INCLUDE 和 LIB 路徑，如下所示：</span><span class="sxs-lookup"><span data-stu-id="cc78a-155">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Include and Lib directories should be in the compiler's INCLUDE and LIB paths as in the following:</span></span>  
  
```  
LIB=c:\Program Files\Microsoft Data Access SDK 2.8\Libs\x86\lib;C:\Program Files\Microsoft SQL Server\100\Tools\SDK\Lib;  
INCLUDE=c:\Program Files\Microsoft Data Access SDK 2.8\inc;C:\Program Files\Microsoft SQL Server\100\Tools\SDK\Include;  
```  
  
 <span data-ttu-id="cc78a-156">先前在建立應用程式的過程中所做的其中一個設計決策為：應用程式是否需要同時讓多個 ODBC 呼叫未完成。</span><span class="sxs-lookup"><span data-stu-id="cc78a-156">One design decision made early in the process of building an application is whether the application needs to have multiple ODBC calls outstanding at the same time.</span></span> <span data-ttu-id="cc78a-157">有兩種方法可以支援同時呼叫多個 ODBC，本節其他主題將會有完整說明。</span><span class="sxs-lookup"><span data-stu-id="cc78a-157">There are two methods for supporting multiple concurrent ODBC calls, which are described in the remaining topics in this section.</span></span> <span data-ttu-id="cc78a-158">如需詳細資訊，請參閱 ODBC 程式設計[人員參考](https://go.microsoft.com/fwlink/?LinkId=45250)。</span><span class="sxs-lookup"><span data-stu-id="cc78a-158">For more information, see the [ODBC Programmer's Reference](https://go.microsoft.com/fwlink/?LinkId=45250).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="cc78a-159">本節內容</span><span class="sxs-lookup"><span data-stu-id="cc78a-159">In This Section</span></span>  
  
-   [<span data-ttu-id="cc78a-160">非同步模式和 SQLCancel</span><span class="sxs-lookup"><span data-stu-id="cc78a-160">Asynchronous Mode and SQLCancel</span></span>](../../native-client-odbc-api/sqlcancel.md)  
  
-   [<span data-ttu-id="cc78a-161">多執行緒應用程式</span><span class="sxs-lookup"><span data-stu-id="cc78a-161">Multithreaded Applications</span></span>](creating-a-driver-application-multithreaded-applications.md)  
  
## <a name="see-also"></a><span data-ttu-id="cc78a-162">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cc78a-162">See Also</span></span>  
 [<span data-ttu-id="cc78a-163">SQL Server Native Client &#40;ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="cc78a-163">SQL Server Native Client &#40;ODBC&#41;</span></span>](sql-server-native-client-odbc.md)  
  
  
