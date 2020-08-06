---
title: 設定 DQS 記錄檔的進階設定 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
helpviewer_keywords:
- log files,advanced settings
- dqs log files,advanced settings
ms.assetid: 1d565748-9759-425c-ae38-4d2032a86868
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: ad41b0cac95f9bfe5565ccbac16b0fda3e28ddf6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687174"
---
# <a name="configure-advanced-settings-for-dqs-log-files"></a><span data-ttu-id="0971d-102">設定 DQS 記錄檔的進階設定</span><span class="sxs-lookup"><span data-stu-id="0971d-102">Configure Advanced Settings for DQS Log Files</span></span>
  <span data-ttu-id="0971d-103">本主題描述如何設定 [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] 和 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 記錄檔的進階設定，例如設定記錄檔的輪替檔案大小限制、設定事件的時間戳記模式等等。</span><span class="sxs-lookup"><span data-stu-id="0971d-103">This topic describes how to configure advanced settings for [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] and [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] log files, such as set the rolling file size limit of the log files, set the time stamp pattern of the events, and so on.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0971d-104">這些活動無法使用 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]來執行，而且僅適用於進階使用者。</span><span class="sxs-lookup"><span data-stu-id="0971d-104">These activities cannot be performed using [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)], and is intended for advanced users only.</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="0971d-105">開始之前</span><span class="sxs-lookup"><span data-stu-id="0971d-105">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="0971d-106">Security</span><span class="sxs-lookup"><span data-stu-id="0971d-106">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="0971d-107">權限</span><span class="sxs-lookup"><span data-stu-id="0971d-107">Permissions</span></span>  
  
-   <span data-ttu-id="0971d-108">您的 Windows 使用者帳戶必須是 SQL Server 執行個體上系統管理員 (sysadmin) 固定伺服器角色的成員，才能修改 DQS_MAIN 資料庫中 A_CONFIGURATION 資料表的組態設定。</span><span class="sxs-lookup"><span data-stu-id="0971d-108">Your Windows user account must be a member of the sysadmin fixed server role in the SQL Server instance to modify configuration settings in the A_CONFIGURATION table in the DQS_MAIN database.</span></span>  
  
-   <span data-ttu-id="0971d-109">您必須在想要修改 DQLog.Client.xml 檔案的電腦上，以 Administrators 群組成員的身分登入，才能設定 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 記錄設定。</span><span class="sxs-lookup"><span data-stu-id="0971d-109">You must be logged on as a member of the Administrators group on the computer where you are modifying the DQLog.Client.xml file to configure the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] logging settings.</span></span>  
  
##  <a name="configure-data-quality-server-log-settings"></a><a name="DQSServer"></a><span data-ttu-id="0971d-110">設定資料品質伺服器記錄檔設定</span><span class="sxs-lookup"><span data-stu-id="0971d-110">Configure Data Quality Server Log Settings</span></span>  
 <span data-ttu-id="0971d-111">在 DQS_MAIN 資料庫的 A_CONFIGURATION 資料表中， [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] 記錄設定會以 XML 格式存在 **[ServerLogging]** 資料列的 **[VALUE]** 資料行中。</span><span class="sxs-lookup"><span data-stu-id="0971d-111">The [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] log settings are present in an XML format in the **VALUE** column of the **ServerLogging** row in the A_CONFIGURATION table in the DQS_MAIN database.</span></span> <span data-ttu-id="0971d-112">您可以執行下列 SQL 查詢，以便檢視組態資訊：</span><span class="sxs-lookup"><span data-stu-id="0971d-112">You can run the following SQL query to view the configuration information:</span></span>  
  
```sql  
select * from DQS_MAIN.dbo.A_CONFIGURATION where NAME='ServerLogging'; 
```  
  
 <span data-ttu-id="0971d-113">若要變更 \*\*\*\* 記錄的組態設定，您必須在 **[ServerLogging]** 資料列的 [VALUE] [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] 資料行中更新適當資訊。</span><span class="sxs-lookup"><span data-stu-id="0971d-113">You must update the appropriate information in the **VALUE** column of the **ServerLogging** row to change the configuration settings for [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] logging.</span></span> <span data-ttu-id="0971d-114">在此範例中，我們將更新 [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] 記錄設定，以便將輪替檔案大小限制設定為 25000 KB (預設值為 20000 KB)。</span><span class="sxs-lookup"><span data-stu-id="0971d-114">In this example, we will update the [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] log settings to set the rolling file size limit to 25000 KB (the default is 20000 KB).</span></span>  
  
1.  <span data-ttu-id="0971d-115">啟動 Microsoft SQL Server Management Studio，並連接到適當的 SQL Server 執行個體。</span><span class="sxs-lookup"><span data-stu-id="0971d-115">Start Microsoft SQL Server Management Studio, and connect to the appropriate SQL Server instance.</span></span>  
  
2.  <span data-ttu-id="0971d-116">在 [物件總管] 中，以滑鼠右鍵按一下伺服器，然後按一下 **[新增查詢]**。</span><span class="sxs-lookup"><span data-stu-id="0971d-116">In Object Explorer, right-click the server, and then click **New Query**.</span></span>  
  
3.  <span data-ttu-id="0971d-117">在 [查詢編輯器] 視窗中，複製下列 SQL 陳述式：</span><span class="sxs-lookup"><span data-stu-id="0971d-117">In the Query Editor window, copy the following SQL statements:</span></span>  
  
    ```sql  
    -- Begin the transaction.  
    BEGIN TRAN  
    GO  
    -- set the XML value field for the row with name=ServerLogging  
    update DQS_MAIN.dbo.A_CONFIGURATION   
    set VALUE='<configuration>  
      <configSections>  
        <section name="loggingConfiguration" type="Microsoft.Practices.EnterpriseLibrary.Logging.Configuration.LoggingSettings, Microsoft.Practices.EnterpriseLibrary.Logging, Version=4.1.0.0, Culture=neutral, PublicKeyToken=e44a2bc38ed2c13c" />  
      </configSections>  
      <loggingConfiguration name="Logging Application Block" tracingEnabled="true" defaultCategory="" logWarningsWhenNoCategoriesMatch="true">  
        <listeners>  
          <add fileName="###REPLACE_THIS_WITH_SQL_SERVER_INSTANCE_LOG_FOLDER_NAME###DQServerLog.###REPLACE_THIS_WITH_SQL_CATALOG_NAME###.log" footer="" formatter="Custom Text Formatter" header="" rollFileExistsBehavior="Increment" rollInterval="None" rollSizeKB="25000" timeStampPattern="yyyy-MM-dd" listenerDataType="Microsoft.Practices.EnterpriseLibrary.Logging.Configuration.RollingFlatFileTraceListenerData, Microsoft.Practices.EnterpriseLibrary.Logging, Version=4.1.0.0, Culture=neutral, PublicKeyToken=e44a2bc38ed2c13c" traceOutputOptions="None" filter="All" type="Microsoft.Practices.EnterpriseLibrary.Logging.TraceListeners.RollingFlatFileTraceListener, Microsoft.Practices.EnterpriseLibrary.Logging, Version=4.1.0.0, Culture=neutral, PublicKeyToken=e44a2bc38ed2c13c" name="Rolling Flat File Trace Listener" />  
        </listeners>  
        <formatters>  
          <add template="{timestamp(local)}|[{threadName}]|{dictionary({value}|)}{message}" type="Microsoft.Practices.EnterpriseLibrary.Logging.Formatters.TextFormatter, Microsoft.Practices.EnterpriseLibrary.Logging, Version=4.1.0.0, Culture=neutral, PublicKeyToken=e44a2bc38ed2c13c" name="Custom Text Formatter" />  
        </formatters>  
        <logFilters>  
          <add enabled="true" type="Microsoft.Practices.EnterpriseLibrary.Logging.Filters.LogEnabledFilter, Microsoft.Practices.EnterpriseLibrary.Logging, Version=4.1.0.0, Culture=neutral, PublicKeyToken=e44a2bc38ed2c13c" name="LogEnabled Filter" />  
        </logFilters>  
        <categorySources />  
        <specialSources>  
          <allEvents switchValue="All" name="All Events" />  
          <notProcessed switchValue="All" name="Unprocessed Category" />  
          <errors switchValue="All" name="Logging Errors & Warnings">  
            <listeners>  
              <add name="Rolling Flat File Trace Listener" />  
            </listeners>  
          </errors>  
        </specialSources>  
      </loggingConfiguration>  
    </configuration>'  
    WHERE NAME='ServerLogging'  
    GO  
    -- check the result  
    select * from DQS_MAIN.dbo.A_CONFIGURATION where NAME='ServerLogging'  
  
    -- Commit the transaction.  
    COMMIT TRAN  
  
    ```  
  
4.  <span data-ttu-id="0971d-118">按 F5 執行陳述式。</span><span class="sxs-lookup"><span data-stu-id="0971d-118">Press F5 to execute the statements.</span></span> <span data-ttu-id="0971d-119">檢查 **[結果]** 窗格，確認陳述式是否皆已成功地執行。</span><span class="sxs-lookup"><span data-stu-id="0971d-119">Check the **Results** pane to verify that the statements have executed successfully.</span></span>  
  
5.  <span data-ttu-id="0971d-120">若要將所做的變更套用至 [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] 記錄組態，您必須執行下列 Transact-SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="0971d-120">To apply changes done to the [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] logging configuration, you must run the following Transact-SQL statements.</span></span> <span data-ttu-id="0971d-121">開啟新的 [查詢編輯器] 視窗，並且貼上下列 Transact-SQL 陳述式：</span><span class="sxs-lookup"><span data-stu-id="0971d-121">Open a new Query Editor window, and paste the following Transact-SQL statements:</span></span>  
  
    ```sql  
    USE [DQS_MAIN]  
    GO  
    DECLARE @return_value int  
    EXEC @return_value = [internal_core].[RefreshLogSettings]  
    SELECT 'Return Value' = @return_value  
    GO  
    ```  
  
6.  <span data-ttu-id="0971d-122">按 F5 執行陳述式。</span><span class="sxs-lookup"><span data-stu-id="0971d-122">Press F5 to execute the statements.</span></span> <span data-ttu-id="0971d-123">檢查 **[結果]** 窗格，確認陳述式是否皆已成功地執行。</span><span class="sxs-lookup"><span data-stu-id="0971d-123">Check the **Results** pane to verify that the statements have executed successfully.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0971d-124">[!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] 記錄設定組態是以動態方式產生並儲存在 DQS_MAIN.Log 檔案中，而該檔案通常位於 C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Log (如果您安裝了 SQL Server 預設執行個體的話)。</span><span class="sxs-lookup"><span data-stu-id="0971d-124">The [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] logging settings configuration is dynamically generated and stored in the DQS_MAIN.Log file, which is typically available at C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Log if you installed the default instance of SQL Server.</span></span> <span data-ttu-id="0971d-125">不過，直接在此檔案中進行的變更不會保存，而且 DQS_MAIN 資料庫中 A_CONFIGURATION 資料表的組態設定會覆寫這些變更。</span><span class="sxs-lookup"><span data-stu-id="0971d-125">However, changes done directly in this file do not hold, and are overwritten by the configuration settings in the A_CONFIGURATION table in the DQS_MAIN database.</span></span>  
  
##  <a name="configure-data-quality-client-log-settings"></a><a name="DQSClient"></a><span data-ttu-id="0971d-126">設定 Data Quality Client 記錄檔設定</span><span class="sxs-lookup"><span data-stu-id="0971d-126">Configure Data Quality Client Log Settings</span></span>  
 <span data-ttu-id="0971d-127">[!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]記錄設定設定檔（DQLog.Client.xml）通常是在 C:\Program FILES\MICROSOFT SQL Server\120\Tools\Binn\DQ\config. 中提供。XML 檔案的內容類別似于您稍早針對記錄檔設定所修改的 XML 檔案 [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="0971d-127">The [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] log setting configuration file, DQLog.Client.xml, is typically available at C:\Program Files\Microsoft SQL Server\120\Tools\Binn\DQ\config. The contents of the XML file is similar to the XML file that you modified earlier for the [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] log configuration settings.</span></span> <span data-ttu-id="0971d-128">若要設定 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 記錄設定：</span><span class="sxs-lookup"><span data-stu-id="0971d-128">To configure the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] log settings:</span></span>  
  
1.  <span data-ttu-id="0971d-129">以系統管理員的身分執行任何 XML 編輯工具或 [記事本]。</span><span class="sxs-lookup"><span data-stu-id="0971d-129">Run any XML editing tool or notepad as an administrator.</span></span>  
  
2.  <span data-ttu-id="0971d-130">在工具或 [記事本] 中開啟 DQLog.Client.xml 檔案。</span><span class="sxs-lookup"><span data-stu-id="0971d-130">Open the DQLog.Client.xml file in the tool or notepad.</span></span>  
  
3.  <span data-ttu-id="0971d-131">進行所需的變更，然後儲存檔案，即可套用新的記錄變更。</span><span class="sxs-lookup"><span data-stu-id="0971d-131">Make the required changes, and save the file to apply the new logging changes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0971d-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0971d-132">See Also</span></span>  
 [<span data-ttu-id="0971d-133">為 DQS 記錄檔設定嚴重性層級</span><span class="sxs-lookup"><span data-stu-id="0971d-133">Configure Severity Levels for DQS Log Files</span></span>](../../2014/data-quality-services/configure-severity-levels-for-dqs-log-files.md)  
  
  
