---
title: 連接到 (ODBC) 的資料來源 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- checking connection states
- ODBC data sources, connections
- data sources [SQL Server Native Client]
- SQLBrowseConnect function
- ODBC applications, connections
- ODBC applications, data sources
- connections [SQL Server Native Client]
- SQLConnect function
- SQLDriveConnect function
- verifying connection states
- SQL Server Native Client ODBC driver, data sources
- SQL Server Native Client ODBC driver, connections
ms.assetid: ae30dd1d-06ae-452b-9618-8fd8cd7ba074
author: rothja
ms.author: jroth
ms.openlocfilehash: 25ce5954e45bb8070b5e99d8ebb7bfa9ad149c3a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595946"
---
# <a name="connecting-to-a-data-source-odbc"></a><span data-ttu-id="ba9c0-102">連接至資料來源 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="ba9c0-102">Connecting to a Data Source (ODBC)</span></span>
  <span data-ttu-id="ba9c0-103">配置環境與連接控制代碼，並設定任何連接屬性之後，應用程式會連接到資料來源或驅動程式。</span><span class="sxs-lookup"><span data-stu-id="ba9c0-103">After allocating environment and connection handles and setting any connection attributes, the application connects to the data source or driver.</span></span> <span data-ttu-id="ba9c0-104">您可以用來連接的函數有三種：</span><span class="sxs-lookup"><span data-stu-id="ba9c0-104">There are three functions you can use to connect:</span></span>  
  
-   <span data-ttu-id="ba9c0-105">**SQLConnect**</span><span class="sxs-lookup"><span data-stu-id="ba9c0-105">**SQLConnect**</span></span>  
  
-   <span data-ttu-id="ba9c0-106">**SQLDriverConnect**</span><span class="sxs-lookup"><span data-stu-id="ba9c0-106">**SQLDriverConnect**</span></span>  
  
-   <span data-ttu-id="ba9c0-107">**SQLBrowseConnect**</span><span class="sxs-lookup"><span data-stu-id="ba9c0-107">**SQLBrowseConnect**</span></span>  
  
 <span data-ttu-id="ba9c0-108">如需有關建立資料來源連接的詳細資訊，包括可用的各種連接字串選項，請參閱搭配[使用連接字串關鍵字與 SQL Server Native Client](../native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md)。</span><span class="sxs-lookup"><span data-stu-id="ba9c0-108">For more information about making connections to a data source, including the various connection string options available, see [Using Connection String Keywords with SQL Server Native Client](../native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md).</span></span>  
  
## <a name="sqlconnect"></a><span data-ttu-id="ba9c0-109">SQLConnect</span><span class="sxs-lookup"><span data-stu-id="ba9c0-109">SQLConnect</span></span>  
 <span data-ttu-id="ba9c0-110">**SQLConnect**是最簡單的連接功能。</span><span class="sxs-lookup"><span data-stu-id="ba9c0-110">**SQLConnect** is the simplest connection function.</span></span> <span data-ttu-id="ba9c0-111">它接受三種參數：資料來源名稱、使用者識別碼與密碼。</span><span class="sxs-lookup"><span data-stu-id="ba9c0-111">It accepts three parameters: a data source name, a user ID, and a password.</span></span> <span data-ttu-id="ba9c0-112">當這三個參數包含連接到資料庫所需的所有資訊時，請使用**SQLConnect** 。</span><span class="sxs-lookup"><span data-stu-id="ba9c0-112">Use **SQLConnect** when these three parameters contain all the information needed to connect to the database.</span></span> <span data-ttu-id="ba9c0-113">若要這麼做，請使用**SQLDataSources**建立資料來源的清單。提示使用者輸入資料來源、使用者識別碼和密碼;然後呼叫**SQLConnect**。</span><span class="sxs-lookup"><span data-stu-id="ba9c0-113">To do this, build a list of data sources using **SQLDataSources**; prompt the user for a data source, user ID, and password; and then call **SQLConnect**.</span></span>  
  
 <span data-ttu-id="ba9c0-114">**SQLConnect**會假設資料來源名稱、使用者識別碼和密碼足以連接至資料來源，而且 odbc 資料來源包含 odbc 驅動程式進行連接所需的所有其他資訊。</span><span class="sxs-lookup"><span data-stu-id="ba9c0-114">**SQLConnect** assumes that a data source name, user ID, and password are sufficient to connect to a data source and that the ODBC data source contains all other information the ODBC driver needs to make the connection.</span></span> <span data-ttu-id="ba9c0-115">不同于[SQLDriverConnect](../native-client-odbc-api/sqldriverconnect.md)和[SQLBrowseConnect](../native-client-odbc-api/sqlbrowseconnect.md)， **SQLConnect**不會使用連接字串。</span><span class="sxs-lookup"><span data-stu-id="ba9c0-115">Unlike [SQLDriverConnect](../native-client-odbc-api/sqldriverconnect.md) and [SQLBrowseConnect](../native-client-odbc-api/sqlbrowseconnect.md), **SQLConnect** does not use a connection string.</span></span>  
  
## <a name="sqldriverconnect"></a><span data-ttu-id="ba9c0-116">SQLDriverConnect</span><span class="sxs-lookup"><span data-stu-id="ba9c0-116">SQLDriverConnect</span></span>  
 <span data-ttu-id="ba9c0-117">當需要的資訊超過資料來源名稱、使用者識別碼和密碼時，會使用**SQLDriverConnect** 。</span><span class="sxs-lookup"><span data-stu-id="ba9c0-117">**SQLDriverConnect** is used when more information than the data source name, user ID, and password is required.</span></span> <span data-ttu-id="ba9c0-118">其中一個要**SQLDriverConnect**的參數是包含驅動程式特定資訊的連接字串。</span><span class="sxs-lookup"><span data-stu-id="ba9c0-118">One of the parameters to **SQLDriverConnect** is a connection string containing driver-specific information.</span></span> <span data-ttu-id="ba9c0-119">基於下列原因，您可能會使用**SQLDriverConnect**而不是**SQLConnect** ：</span><span class="sxs-lookup"><span data-stu-id="ba9c0-119">You might use **SQLDriverConnect** instead of **SQLConnect** for the following reasons:</span></span>  
  
-   <span data-ttu-id="ba9c0-120">在連接階段指定驅動程式專屬的資訊。</span><span class="sxs-lookup"><span data-stu-id="ba9c0-120">To specify driver-specific information at connect time.</span></span>  
  
-   <span data-ttu-id="ba9c0-121">要求驅動程式提示使用者輸入連接資訊。</span><span class="sxs-lookup"><span data-stu-id="ba9c0-121">To request that the driver prompt the user for connection information.</span></span>  
  
-   <span data-ttu-id="ba9c0-122">不使用 ODBC 資料來源連接。</span><span class="sxs-lookup"><span data-stu-id="ba9c0-122">To connect without using an ODBC data source.</span></span>  
  
 <span data-ttu-id="ba9c0-123">**SQLDriverConnect**連接字串包含一系列的關鍵字-值組，可指定 ODBC 驅動程式支援的所有連接資訊。</span><span class="sxs-lookup"><span data-stu-id="ba9c0-123">The **SQLDriverConnect** connection string contains a series of keyword-value pairs that specify all connection information supported by an ODBC driver.</span></span> <span data-ttu-id="ba9c0-124">除了供驅動程式支援之所有連接資訊使用的驅動程式專屬關鍵字之外，每個驅動程式還支援標準 ODBC 關鍵字 (DSN、FILEDSN、DRIVER、UID、PWD 和 SAVEFILE)。</span><span class="sxs-lookup"><span data-stu-id="ba9c0-124">Each driver supports the standard ODBC keywords (DSN, FILEDSN, DRIVER, UID, PWD, and SAVEFILE) in addition to driver-specific keywords for all connection information supported by the driver.</span></span> <span data-ttu-id="ba9c0-125">**SQLDriverConnect**可以用來連接，而不需要資料來源。</span><span class="sxs-lookup"><span data-stu-id="ba9c0-125">**SQLDriverConnect** can be used to connect without a data source.</span></span> <span data-ttu-id="ba9c0-126">例如，設計用來對實例進行「無 DSN」連接的應用程式 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 可以使用連接字串來呼叫**SQLDriverConnect** ，以定義登入識別碼、密碼、網路程式庫、要連接的伺服器名稱，以及要使用的預設資料庫。</span><span class="sxs-lookup"><span data-stu-id="ba9c0-126">For example, an application that is designed to make a "DSN-less" connection to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] can call **SQLDriverConnect** with a connection string that defines the login ID, password, network library, server name to connect to, and default database to use.</span></span>  
  
 <span data-ttu-id="ba9c0-127">使用**SQLDriverConnect**時，有兩個選項可提示使用者輸入任何需要的連接資訊：</span><span class="sxs-lookup"><span data-stu-id="ba9c0-127">When using **SQLDriverConnect**, there are two options for prompting the user for any needed connection information:</span></span>  
  
-   <span data-ttu-id="ba9c0-128">應用程式對話方塊</span><span class="sxs-lookup"><span data-stu-id="ba9c0-128">Application dialog box</span></span>  
  
     <span data-ttu-id="ba9c0-129">您可以建立應用程式對話方塊，以提示輸入連接資訊，然後使用 Null 視窗控制碼呼叫**SQLDriverConnect** ，並將*DriverCompletion*設定為 SQL_DRIVER_NOPROMPT。</span><span class="sxs-lookup"><span data-stu-id="ba9c0-129">You can create an application dialog box that prompts for connection information, and then calls **SQLDriverConnect** with a NULL window handle and *DriverCompletion* set to SQL_DRIVER_NOPROMPT.</span></span> <span data-ttu-id="ba9c0-130">這些參數設定可防止 ODBC 驅動程式開啟自己的對話方塊。</span><span class="sxs-lookup"><span data-stu-id="ba9c0-130">These parameter settings prevent the ODBC driver from opening its own dialog box.</span></span> <span data-ttu-id="ba9c0-131">當控制應用程式的使用者介面相當重要時，使用此方法。</span><span class="sxs-lookup"><span data-stu-id="ba9c0-131">This method is used when it is important to control the user interface of the application.</span></span>  
  
-   <span data-ttu-id="ba9c0-132">驅動程式對話方塊</span><span class="sxs-lookup"><span data-stu-id="ba9c0-132">Driver dialog box</span></span>  
  
     <span data-ttu-id="ba9c0-133">您可以撰寫應用程式的程式碼，將有效的視窗控制碼傳遞給**SQLDriverConnect** ，並將*DriverCompletion*參數設定為 SQL_DRIVER_COMPLETE、SQL_DRIVER_PROMPT 或 SQL_DRIVER_COMPLETE_REQUIRED。</span><span class="sxs-lookup"><span data-stu-id="ba9c0-133">You can code the application to pass a valid window handle to **SQLDriverConnect** and set the *DriverCompletion* parameter to SQL_DRIVER_COMPLETE, SQL_DRIVER_PROMPT, or SQL_DRIVER_COMPLETE_REQUIRED.</span></span> <span data-ttu-id="ba9c0-134">接著，驅動程式會產生一個對話方塊來提示使用者輸入連接資訊。</span><span class="sxs-lookup"><span data-stu-id="ba9c0-134">The driver then generates a dialog box to prompt the user for connection information.</span></span> <span data-ttu-id="ba9c0-135">這個方法會簡化應用程式的程式碼。</span><span class="sxs-lookup"><span data-stu-id="ba9c0-135">This method simplifies the application code.</span></span>  
  
## <a name="sqlbrowseconnect"></a><span data-ttu-id="ba9c0-136">SQLBrowseConnect</span><span class="sxs-lookup"><span data-stu-id="ba9c0-136">SQLBrowseConnect</span></span>  
 <span data-ttu-id="ba9c0-137">**SQLBrowseConnect**（例如**SQLDriverConnect**）會使用連接字串。</span><span class="sxs-lookup"><span data-stu-id="ba9c0-137">**SQLBrowseConnect**, like **SQLDriverConnect**, uses a connection string.</span></span> <span data-ttu-id="ba9c0-138">不過，藉由使用**SQLBrowseConnect**，應用程式可以在執行時間與資料來源反復地建立完整的連接字串。</span><span class="sxs-lookup"><span data-stu-id="ba9c0-138">However, by using **SQLBrowseConnect**, an application can construct a complete connection string iteratively with the data source at run time.</span></span> <span data-ttu-id="ba9c0-139">這可以讓應用程式執行兩個動作：</span><span class="sxs-lookup"><span data-stu-id="ba9c0-139">This allows the application to do two things:</span></span>  
  
-   <span data-ttu-id="ba9c0-140">建立自己的對話方塊來提示輸入此資訊，藉此保持對其使用者介面的控制。</span><span class="sxs-lookup"><span data-stu-id="ba9c0-140">Build its own dialog boxes to prompt for this information, thereby retaining control over its user interface.</span></span>  
  
-   <span data-ttu-id="ba9c0-141">瀏覽系統中，特定驅動程式可使用的資料來源 (可能是透過數個步驟)。</span><span class="sxs-lookup"><span data-stu-id="ba9c0-141">Browse the system for data sources that can be used by a particular driver, possibly in several steps.</span></span>  
  
     <span data-ttu-id="ba9c0-142">例如，使用者介面可能會先瀏覽網路中的伺服器，然後在選擇伺服器之後，瀏覽伺服器中可由驅動程式存取的資料庫。</span><span class="sxs-lookup"><span data-stu-id="ba9c0-142">For example, the user might first browse the network for servers and, after choosing a server, browse the server for databases accessible by the driver.</span></span>  
  
 <span data-ttu-id="ba9c0-143">當**SQLBrowseConnect**完成成功的連接時，它會傳回可在後續呼叫**SQLDriverConnect**時使用的連接字串。</span><span class="sxs-lookup"><span data-stu-id="ba9c0-143">When **SQLBrowseConnect** completes a successful connection, it returns a connection string that can be used on subsequent calls to **SQLDriverConnect**.</span></span>  
  
 <span data-ttu-id="ba9c0-144">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native CLIENT ODBC 驅動程式一律會傳回成功**SQLConnect**、 **SQLDriverConnect**或**SQLBrowseConnect**上的 SQL_SUCCESS_WITH_INFO。</span><span class="sxs-lookup"><span data-stu-id="ba9c0-144">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver always returns SQL_SUCCESS_WITH_INFO on a successful **SQLConnect**, **SQLDriverConnect**, or **SQLBrowseConnect**.</span></span> <span data-ttu-id="ba9c0-145">當 ODBC 應用程式在取得 SQL_SUCCESS_WITH_INFO 之後呼叫**SQLGetDiagRec**時，它會收到下列訊息：</span><span class="sxs-lookup"><span data-stu-id="ba9c0-145">When an ODBC application calls **SQLGetDiagRec** after getting SQL_SUCCESS_WITH_INFO, it can receive the following messages:</span></span>  
  
 <span data-ttu-id="ba9c0-146">5701</span><span class="sxs-lookup"><span data-stu-id="ba9c0-146">5701</span></span>  
 <span data-ttu-id="ba9c0-147">表示 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 將使用者的內容放入資料來源中定義的預設資料庫，或在資料來源沒有預設資料庫時，放入針對連接中所使用之登入識別碼所定義的預設資料庫中。</span><span class="sxs-lookup"><span data-stu-id="ba9c0-147">Indicates that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] put the user's context into the default database defined in the data source, or into the default database defined for the login ID used in the connection if the data source did not have a default database.</span></span>  
  
 <span data-ttu-id="ba9c0-148">5703</span><span class="sxs-lookup"><span data-stu-id="ba9c0-148">5703</span></span>  
 <span data-ttu-id="ba9c0-149">表示在伺服器上所使用的語言。</span><span class="sxs-lookup"><span data-stu-id="ba9c0-149">Indicates the language being used on the server.</span></span>  
  
 <span data-ttu-id="ba9c0-150">下列範例會顯示針對系統管理員之成功連接所傳回的訊息：</span><span class="sxs-lookup"><span data-stu-id="ba9c0-150">The following example shows the message returned on a successful connection by the system administrator:</span></span>  
  
```  
szSqlState = "01000", *pfNativeError = 5701,  
szErrorMsg="[Microsoft][SQL Server Native Client][SQL Server]  
       Changed database context to 'pubs'."  
szSqlState = "01000", *pfNativeError = 5703,  
szErrorMsg="[Microsoft][SQL Server Native Client][SQL Server]  
       Changed language setting to 'us_english'."  
```  
  
 <span data-ttu-id="ba9c0-151">您可以忽略訊息 5701 和 5703；這些訊息僅供參考。</span><span class="sxs-lookup"><span data-stu-id="ba9c0-151">You can ignore messages 5701 and 5703; they are only informational.</span></span> <span data-ttu-id="ba9c0-152">不過，您不得忽略 SQL_SUCCESS_WITH_INFO 傳回碼，因為可能會傳回 5701 或 5703 之外的訊息。</span><span class="sxs-lookup"><span data-stu-id="ba9c0-152">You should not, however, ignore a SQL_SUCCESS_WITH_INFO return code because messages other than 5701 or 5703 may be returned.</span></span> <span data-ttu-id="ba9c0-153">例如，如果驅動程式連接到執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 具有過時目錄預存程式之實例的伺服器，在 SQL_SUCCESS_WITH_INFO 之後，透過**SQLGetDiagRec**傳回的其中一個錯誤就是：</span><span class="sxs-lookup"><span data-stu-id="ba9c0-153">For example, if a driver connects to a server running an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] with outdated catalog stored procedures, one of the errors returned through **SQLGetDiagRec** after a SQL_SUCCESS_WITH_INFO is:</span></span>  
  
```  
SqlState:   01000  
pfNative:   0  
szErrorMsg: "[Microsoft][SQL Server Native Client]The ODBC  
            catalog stored procedures installed on server  
            my65server are version 06.50.0193; version 07.00.0205  
            or later is required to ensure proper operation.  
            Please contact your system administrator."  
```  
  
 <span data-ttu-id="ba9c0-154">連接之應用程式的錯誤處理函式 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 應該會呼叫**SQLGetDiagRec** ，直到它傳回 SQL_NO_DATA 為止。</span><span class="sxs-lookup"><span data-stu-id="ba9c0-154">The error handling function of an application for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connections should call **SQLGetDiagRec** until it returns SQL_NO_DATA.</span></span> <span data-ttu-id="ba9c0-155">接著，它應該對*pfNative*碼為5701或5703的任何訊息採取動作。</span><span class="sxs-lookup"><span data-stu-id="ba9c0-155">It should then act on any messages other than the ones with a *pfNative* code of 5701 or 5703.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba9c0-156">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ba9c0-156">See Also</span></span>  
 [<span data-ttu-id="ba9c0-157">與 SQL Server &#40;ODBC&#41;通訊</span><span class="sxs-lookup"><span data-stu-id="ba9c0-157">Communicating with SQL Server &#40;ODBC&#41;</span></span>](communicating-with-sql-server-odbc.md)  
  
  
