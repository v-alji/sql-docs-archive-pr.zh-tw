---
title: ssbdiagnose 公用程式 (Service Broker) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- Service Broker, runtime reports
- Service Broker, command prompt utilities
- troubleshooting [Service Broker], conversations
- troubleshooting [Service Broker], configurations
- command prompt utilities [Service Broker]
- Service Broker, troubleshooting
- Service Broker, configuration reports
- Service Broker, tools
- troubleshooting [Service Broker], runtime
- conversations [Service Broker], troubleshooting
- troubleshooting [Service Broker], ssbdiagnose utility
- tools [Service Broker], ssbdiagnose
- Service Broker, ssbdiagnose utility
- ssbdiagnose
ms.assetid: 0c1636e8-a3db-438e-be4c-1ea40d1f4877
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8efc581eebd7d8fa7fa265abb54168af78b57ca2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704546"
---
# <a name="ssbdiagnose-utility-service-broker"></a><span data-ttu-id="c3dfb-102">ssbdiagnose 公用程式 [Service Broker]</span><span class="sxs-lookup"><span data-stu-id="c3dfb-102">ssbdiagnose Utility (Service Broker)</span></span>
  <span data-ttu-id="c3dfb-103">**ssbdiagnose** 公用程式會報告 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 交談或 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 服務組態中的問題。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-103">The **ssbdiagnose** utility reports issues in [!INCLUDE[ssSB](../../includes/sssb-md.md)] conversations or the configuration of [!INCLUDE[ssSB](../../includes/sssb-md.md)] services.</span></span> <span data-ttu-id="c3dfb-104">您可以針對兩個服務或單一服務進行組態檢查。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-104">Configuration checks can be made for either two services or a single service.</span></span> <span data-ttu-id="c3dfb-105">問題會在命令提示字元視窗中報告成人們可讀取的文字，或可重新導向至檔案或其他程式的格式化 XML。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-105">Issues are reported either in the command prompt window as human-readable text, or as formatted XML that can be redirected to a file or another program.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3dfb-106">語法</span><span class="sxs-lookup"><span data-stu-id="c3dfb-106">Syntax</span></span>  
  
```  
  
      ssbdiagnose   
[ [ -XML ]  
    [ -LEVEL { ERROR | WARNING | INFO } ]  
  [-IGNOREerror_id ] [ ...n]  
    [ <baseconnectionoptions> ]  
  { <configurationreport> | <runtimereport> }  
]  
| -?  
  
<configurationreport> ::=  
    CONFIGURATION  
  { [ FROM SERVICEservice_name  
      [ <fromconnectionoptions> ]  
      [ MIRROR <mirrorconnectionoptions> ]  
    ]  
    [ TO SERVICEservice_name[, broker_id ]  
      [ <toconnectionoptions> ]  
      [ MIRROR <mirrorconnectionoptions> ]  
    ]  
  }  
    ON CONTRACTcontract_name  
  [ ENCRYPTION { ON | OFF | ANONYMOUS } ]  
  
<runtime_report> ::=  
    RUNTIME  
    [-SHOWEVENTS ]  
        [ -NEW  
         [ -ID { conversation_handle  
                | conversation_group_id  
                 | conversation_id  
                  }  
        ] [ ...n]  
        ]  
    [ -TIMEOUTtimeout_interval ]  
    [ <runtimeconnectionoptions> ]  
  
<baseconnectionoptions> ::=  
  <connectionoptions>  
  
<fromconnectionoptions> ::=  
  <connectionoptions>  
  
<toconnectionoptions> ::=  
  <connectionoptions>  
  
<mirrorconnectionoptions> ::=  
  <connectionoptions>  
  
<runtimeconnectionoptions> ::=  
  [ CONNECT TO <connectionoptions> ] [ ...n]  
  
<connectionoptions> ::=  
    [ -E | { -Ulogin_id [ -Ppassword ] } ]  
  [ -Sserver_name[\instance_name] ]  
  [ -ddatabase_name ]  
  [ -llogin_timeout ]  
  
```  
  
## <a name="command-line-options"></a><span data-ttu-id="c3dfb-107">命令列選項</span><span class="sxs-lookup"><span data-stu-id="c3dfb-107">Command Line Options</span></span>  
 <span data-ttu-id="c3dfb-108">**-XML**</span><span class="sxs-lookup"><span data-stu-id="c3dfb-108">**-XML**</span></span>  
 <span data-ttu-id="c3dfb-109">指定 **ssbdiagnose** 輸出要產生為格式化的 XML。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-109">Specifies that the **ssbdiagnose** output be generated as formatted XML.</span></span> <span data-ttu-id="c3dfb-110">這種輸出可重新導向至檔案或其他應用程式。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-110">This can be redirected to a file or to another application.</span></span> <span data-ttu-id="c3dfb-111">如未指定 **-XML** ，則 **ssbdiagnose** 輸出就會格式化成一般人看得懂的文字。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-111">If **-XML** is not specified, the **ssbdiagnose** output is formatted as human-readable text.</span></span>  
  
 <span data-ttu-id="c3dfb-112">**-LEVEL** { **ERROR** | **WARNING** | **INFO**}</span><span class="sxs-lookup"><span data-stu-id="c3dfb-112">**-LEVEL** { **ERROR** | **WARNING** | **INFO**}</span></span>  
 <span data-ttu-id="c3dfb-113">指定要報告的訊息層級。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-113">Specifies the level of messages to report.</span></span>  
  
 <span data-ttu-id="c3dfb-114">**ERROR**：僅報告錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-114">**ERROR**: report only error messages.</span></span>  
  
 <span data-ttu-id="c3dfb-115">**WARNING**：報告錯誤和警告訊息。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-115">**WARNING**: report error and warning messages.</span></span>  
  
 <span data-ttu-id="c3dfb-116">**INFO**：報告錯誤、警告和參考用訊息。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-116">**INFO**: report error, warning, and informational messages.</span></span>  
  
 <span data-ttu-id="c3dfb-117">預設設定為 **WARNING**。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-117">The default setting is **WARNING**.</span></span>  
  
 <span data-ttu-id="c3dfb-118">**-IGNORE** *error_id*</span><span class="sxs-lookup"><span data-stu-id="c3dfb-118">**-IGNORE** *error_id*</span></span>  
 <span data-ttu-id="c3dfb-119">指定具有指定之 *error_id* 的錯誤或訊息，不要包含在報表中。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-119">Specifies that errors or messages that have the specified *error_id* not be included in reports.</span></span> <span data-ttu-id="c3dfb-120">您可以多次指定 **-IGNORE** ，以隱藏多個訊息識別碼。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-120">You can specify **-IGNORE** multiple times to suppress multiple message IDs.</span></span>  
  
 **\<baseconnectionoptions>**  
 <span data-ttu-id="c3dfb-121">指定當特定子句中未包含連線選項時， **ssbdiagnose** 所使用的基底連線資訊。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-121">Specifies the base connection information that is used by **ssbdiagnose** when connection options are not included in a specific clause.</span></span> <span data-ttu-id="c3dfb-122">在特定子句中提供的連接資訊，會覆寫 **baseconnectionoption** 資訊。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-122">The connection information that is given in a specific clause overrides the **baseconnectionoption** information.</span></span> <span data-ttu-id="c3dfb-123">這會針對每項參數個別執行。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-123">This is performed separately for each parameter.</span></span> <span data-ttu-id="c3dfb-124">例如， **baseconnetionoptions** 中同時指定了 **-S** 和 **-d**，而 **toconnetionoptions** 中只指定了 **-d**，則 **ssbdiagnose** 會使用 **baseconnetionoptions** 的 -S 和 **toconnetionoptions**的 -d。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-124">For example, if both **-S** and **-d** are specified in **baseconnetionoptions**, and only **-d** is specified in **toconnetionoptions**, **ssbdiagnose** uses -S from **baseconnetionoptions** and -d from **toconnetionoptions**.</span></span>  
  
 <span data-ttu-id="c3dfb-125">**CONFIGURATION**</span><span class="sxs-lookup"><span data-stu-id="c3dfb-125">**CONFIGURATION**</span></span>  
 <span data-ttu-id="c3dfb-126">要求一組 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 服務之間或單一服務的組態錯誤報表。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-126">Requests a report of configuration errors between a pair of [!INCLUDE[ssSB](../../includes/sssb-md.md)] services, or for a single service.</span></span>  
  
 <span data-ttu-id="c3dfb-127">**FROM SERVICE** *service_name*</span><span class="sxs-lookup"><span data-stu-id="c3dfb-127">**FROM SERVICE** *service_name*</span></span>  
 <span data-ttu-id="c3dfb-128">指定起始交談的服務。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-128">Specifies the service that initiates conversations.</span></span>  
  
 **\<fromconnectionoptions>**  
 <span data-ttu-id="c3dfb-129">指定連接至保留起始端服務之資料庫所需的資訊。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-129">Specifies the information that is required to connect to the database that holds the initiator service.</span></span> <span data-ttu-id="c3dfb-130">如未指定 **fromconnectionoptions** ，則 **ssbdiagnose** 會使用 **baseconnectionoptions** 中的連接資訊連接至起始端資料庫。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-130">If **fromconnectionoptions** is not specified, **ssbdiagnose** uses the connection information from **baseconnectionoptions** to connect to the initiator database.</span></span> <span data-ttu-id="c3dfb-131">如果指定了 **fromconnectionoptions** ，它就必須包括含有起始端服務的資料庫。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-131">If **fromconnectionoptions** is specified it must include the database that contains the initiator service.</span></span> <span data-ttu-id="c3dfb-132">如未指定 **fromconnectionoptions** ，則 **baseconnectionoptions** 必須指定起始端資料庫。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-132">If **fromconnectionoptions** is not specified, the **baseconnectionoptions** must specify the initiator database.</span></span>  
  
 <span data-ttu-id="c3dfb-133">**TO SERVICE** *service_name*[, *broker_id* ]</span><span class="sxs-lookup"><span data-stu-id="c3dfb-133">**TO SERVICE** *service_name*[, *broker_id* ]</span></span>  
 <span data-ttu-id="c3dfb-134">指定用於交談的服務。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-134">Specifies the service that is the target for the conversations.</span></span>  
  
 <span data-ttu-id="c3dfb-135">*service_name*：指定目標服務的名稱。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-135">*service_name*: specifies the name of the target service.</span></span>  
  
 <span data-ttu-id="c3dfb-136">*broker_id*：指定可識別目標資料庫的 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 識別碼。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-136">*broker_id*: specifies the [!INCLUDE[ssSB](../../includes/sssb-md.md)] ID that identifies the target database.</span></span> <span data-ttu-id="c3dfb-137">*broker_id* 是 GUID。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-137">*broker_id* is a GUID.</span></span> <span data-ttu-id="c3dfb-138">您可以在目標資料庫中執行下列查詢，以便尋找此識別碼：</span><span class="sxs-lookup"><span data-stu-id="c3dfb-138">You can run the following query in the target database to find it:</span></span>  
  
```  
SELECT service_broker_guid  
FROM sys.databases  
WHERE database_id = DB_ID();  
```  
  
 **\<toconnectionoptions>**  
 <span data-ttu-id="c3dfb-139">指定連接至保存目標服務之資料庫所需的資訊。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-139">Specifies the information that is required to connect the database that holds the target service.</span></span> <span data-ttu-id="c3dfb-140">如未指定 **toconnectionoptions** ，則 **ssbdiagnose** 會使用 **baseconnectionoptions** 中的連接資訊連接至目標資料庫。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-140">If **toconnectionoptions** is not specified, **ssbdiagnose** uses the connection information from **baseconnectionoptions** to connect to the target database.</span></span>  
  
 <span data-ttu-id="c3dfb-141">**MIRROR**</span><span class="sxs-lookup"><span data-stu-id="c3dfb-141">**MIRROR**</span></span>  
 <span data-ttu-id="c3dfb-142">指定相關聯的 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 服務由鏡像資料庫所主控。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-142">Specifies that the associated [!INCLUDE[ssSB](../../includes/sssb-md.md)] service is hosted in a mirrored database.</span></span> <span data-ttu-id="c3dfb-143">**ssbdiagnose** 會確認服務的路由為鏡像路由，其中 MIRROR_ADDRESS 是在 CREATE ROUTE 上指定。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-143">**ssbdiagnose** verifies that the route to the service is a mirrored route, where MIRROR_ADDRESS was specified on CREATE ROUTE.</span></span>  
  
 **\<mirrorconnectionoptions>**  
 <span data-ttu-id="c3dfb-144">指定連接至鏡像資料庫所需的資訊。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-144">Specifies the information that is required to connect to the mirror database.</span></span> <span data-ttu-id="c3dfb-145">如未指定 **mirrorconnectionoptions** ，則 **ssbdiagnose** 會使用 **baseconnectionoptions** 中的連接資訊連接至鏡像資料庫。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-145">If **mirrorconnectionoptions** is not specified, **ssbdiagnose** uses the connection information from **baseconnectionoptions** to connect to the mirror database.</span></span>  
  
 <span data-ttu-id="c3dfb-146">**ON CONTRACT** *contract_name*</span><span class="sxs-lookup"><span data-stu-id="c3dfb-146">**ON CONTRACT** *contract_name*</span></span>  
 <span data-ttu-id="c3dfb-147">要求 **ssbdiagnose** 只檢查使用指定合約的組態。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-147">Requests that **ssbdiagnose** only check configurations that use the specified contract.</span></span> <span data-ttu-id="c3dfb-148">如未指定 ON CONTRACT，則 **ssbdiagnose** 就會針對名為 DEFAULT 的合約進行報告。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-148">If ON CONTRACT is not specified, **ssbdiagnose** reports on the contract named DEFAULT.</span></span>  
  
 <span data-ttu-id="c3dfb-149">**ENCRYPTION** { **ON** | **OFF** | **ANONYMOUS** }</span><span class="sxs-lookup"><span data-stu-id="c3dfb-149">**ENCRYPTION** { **ON** | **OFF** | **ANONYMOUS** }</span></span>  
 <span data-ttu-id="c3dfb-150">要求確認是否已針對指定的加密層級正確設定對話：</span><span class="sxs-lookup"><span data-stu-id="c3dfb-150">Requests verification that the dialog is correctly configured for the specified level of encryption:</span></span>  
  
 <span data-ttu-id="c3dfb-151">**ON**：預設設定。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-151">**ON**: Default setting.</span></span> <span data-ttu-id="c3dfb-152">已設定完整的對話安全性。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-152">Full dialog security is configured.</span></span> <span data-ttu-id="c3dfb-153">已經在對話的兩端部署了憑證、存在遠端服務繫結，而且目標服務的 GRANT SEND 陳述式已指定了起始端使用者。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-153">Certificates have been deployed on both sides of the dialog, a remote service binding is present, and the GRANT SEND statement for the target service specified the initiator user.</span></span>  
  
 <span data-ttu-id="c3dfb-154">**OFF**：未設定任何對話安全性。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-154">**OFF**: No dialog security is configured.</span></span> <span data-ttu-id="c3dfb-155">沒有部署任何憑證、沒有建立任何遠端服務繫結，而且起始端服務的 GRANT SEND 已指定了 **Public** 角色。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-155">No certificates have been deployed, no remote service binding was created, and the GRANT SEND for the initiator service specified the **public** role.</span></span>  
  
 <span data-ttu-id="c3dfb-156">**ANONYMOUS**：已設定匿名對話安全性。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-156">**ANONYMOUS**: Anonymous dialog security is configured.</span></span> <span data-ttu-id="c3dfb-157">已經部署了一個憑證、遠端服務繫結已指定了匿名子句，而且目標服務的 GRANT SEND 已指定了 **Public** 角色。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-157">One certificate has been deployed, the remote service binding specified the anonymous clause, and the GRANT SEND for the target service specified the **public** role.</span></span>  
  
 <span data-ttu-id="c3dfb-158">**RUNTIME**</span><span class="sxs-lookup"><span data-stu-id="c3dfb-158">**RUNTIME**</span></span>  
 <span data-ttu-id="c3dfb-159">要求導致 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 交談發生執行階段錯誤之問題的報表。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-159">Requests a report of issues that cause runtime errors for a [!INCLUDE[ssSB](../../includes/sssb-md.md)] conversation.</span></span> <span data-ttu-id="c3dfb-160">如未指定 **-NEW** 或 **-ID** ， **ssbdiagnose** 就會監視連線選項中指定之所有資料庫中的所有交談。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-160">If neither **-NEW** or **-ID** are specified, **ssbdiagnose** monitors all conversations in all databases specified in the connection options.</span></span> <span data-ttu-id="c3dfb-161">如果指定了 **-NEW** 或 **-ID** ， **ssbdiagnose** 就會建立參數中指定的識別碼清單。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-161">If **-NEW** or **-ID** are specified, **ssbdiagnose** builds a list of the IDs specified in the parameters.</span></span>  
  
 <span data-ttu-id="c3dfb-162">當 **ssbdiagnose** 在執行時，它會記錄所有指出執行階段錯誤的 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 事件。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-162">While **ssbdiagnose** is running, it records all [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] events that indicate runtime errors.</span></span> <span data-ttu-id="c3dfb-163">它會記錄針對指定之識別碼發生的事件，以及系統層級事件。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-163">It records the events that occur for the specified IDs, plus system-level events.</span></span> <span data-ttu-id="c3dfb-164">如果發生執行階段錯誤， **ssbdiagnose** 就會針對相關聯的組態執行組態報表。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-164">If runtime errors are encountered, **ssbdiagnose** runs a configuration report on the associated configuration.</span></span>  
  
 <span data-ttu-id="c3dfb-165">根據預設，輸出報表不會包含執行階段錯誤，只會包含組態分析的結果。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-165">By default, runtime errors are not included in the output report, only the results of the configuration analysis.</span></span> <span data-ttu-id="c3dfb-166">您可以使用 **-SHOWEVENTS** ，在報表中包含執行階段錯誤。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-166">Use **-SHOWEVENTS** to have the runtime errors included in the report.</span></span>  
  
 <span data-ttu-id="c3dfb-167">**-SHOWEVENTS**</span><span class="sxs-lookup"><span data-stu-id="c3dfb-167">**-SHOWEVENTS**</span></span>  
 <span data-ttu-id="c3dfb-168">指定 **ssbdiagnose** 在 RUNTIME 報表期間報告 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 事件。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-168">Specifies that **ssbdiagnose** report [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] events during a RUNTIME report.</span></span> <span data-ttu-id="c3dfb-169">僅報告被視為錯誤條件的事件。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-169">Only events that are considered error conditions are reported.</span></span> <span data-ttu-id="c3dfb-170">**ssbdiagnose** 預設只監視錯誤事件，不會在輸出中報告這些事件。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-170">By default, **ssbdiagnose** only monitors error events; it does not report them in the output.</span></span>  
  
 <span data-ttu-id="c3dfb-171">**-NEW**</span><span class="sxs-lookup"><span data-stu-id="c3dfb-171">**-NEW**</span></span>  
 <span data-ttu-id="c3dfb-172">要求監視在 **ssbdiagnose** 開始執行之後開始的第一個交談執行階段。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-172">Requests runtime monitoring of the first conversation that begins after **ssbdiagnose** starts running.</span></span>  
  
 <span data-ttu-id="c3dfb-173">**-ID**</span><span class="sxs-lookup"><span data-stu-id="c3dfb-173">**-ID**</span></span>  
 <span data-ttu-id="c3dfb-174">要求指定的交談元素之執行階段監視。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-174">Requests runtime monitoring of the specified conversation elements.</span></span> <span data-ttu-id="c3dfb-175">您可以指定多次 **-ID** 。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-175">You can specify **-ID** multiple times.</span></span>  
  
 <span data-ttu-id="c3dfb-176">如果您指定了交談控制代碼，系統就只會報告與相關聯之交談端點相關聯的事件。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-176">If you specify a conversation handle, only events associated with the associated conversation endpoint are reported.</span></span> <span data-ttu-id="c3dfb-177">如果您指定了交談識別碼，系統就會報告該交談及其起始端和目標端點的所有事件。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-177">If you specify a conversation ID, all events for that conversation and its initiator and target endpoints are reported.</span></span> <span data-ttu-id="c3dfb-178">如果您指定了交談群組識別碼，系統就會報告該交談群組中所有交談和端點的所有事件。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-178">If a conversation group ID is specified, all events for all conversations and endpoints in the conversation group are reported.</span></span>  
  
 <span data-ttu-id="c3dfb-179">*conversation_handle*</span><span class="sxs-lookup"><span data-stu-id="c3dfb-179">*conversation_handle*</span></span>  
 <span data-ttu-id="c3dfb-180">可識別應用程式中某個交談端點的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-180">A unique identifier that identifies a conversation endpoint in an application.</span></span> <span data-ttu-id="c3dfb-181">交談控制代碼對於交談的某個端點而言是唯一的，而起始端和目標端點具有不同的交談控制代碼。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-181">Conversation handles are unique to one endpoint of a conversation, the initiator and target endpoints have separate conversation handles.</span></span>  
  
 <span data-ttu-id="c3dfb-182">*@dialog_handle* **BEGIN DIALOG**語句的參數和 `conversation_handle` **RECEIVE**語句結果集中的資料行，會將交談控制碼傳回到應用程式。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-182">Conversation handles are returned to applications by the *@dialog_handle* parameter of the **BEGIN DIALOG** statement, and the `conversation_handle` column in the result set of a **RECEIVE** statement.</span></span>  
  
 <span data-ttu-id="c3dfb-183">`conversation_handle` **Transmission_queue**和**sys.databases conversation_endpoints**目錄檢視的資料行中會報告交談控制碼。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-183">Conversation handles are reported in the `conversation_handle` column of the **sys.transmission_queue** and **sys.conversation_endpoints** catalog views.</span></span>  
  
 <span data-ttu-id="c3dfb-184">*conversation_group_id*</span><span class="sxs-lookup"><span data-stu-id="c3dfb-184">*conversation_group_id*</span></span>  
 <span data-ttu-id="c3dfb-185">識別交談群組且不重複的識別碼。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-185">The unique identifier that identifies a conversation group.</span></span>  
  
 <span data-ttu-id="c3dfb-186">*@conversation_group_id* **GET 交談 group**語句的參數和 `conversation_group_id` **RECEIVE**語句結果集中的資料行，會將交談群組識別碼傳回給應用程式。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-186">Conversation group IDs are returned to applications by the *@conversation_group_id* parameter of the **GET CONVERSATION GROUP** statement and the `conversation_group_id` column in the result set of a **RECEIVE** statement.</span></span>  
  
 <span data-ttu-id="c3dfb-187">`conversation_group_id` **Conversation_groups**和**sys.databases conversation_endpoints**目錄檢視的資料行中，會報告交談群組識別碼。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-187">Conversation group IDs are reported in the `conversation_group_id` columns of the **sys.conversation_groups** and **sys.conversation_endpoints** catalog views.</span></span>  
  
 <span data-ttu-id="c3dfb-188">*conversation_id*</span><span class="sxs-lookup"><span data-stu-id="c3dfb-188">*conversation_id*</span></span>  
 <span data-ttu-id="c3dfb-189">識別交談且不重複的識別碼。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-189">The unique identifier that identifies a conversation.</span></span> <span data-ttu-id="c3dfb-190">對於交談的起始端和目標端點而言，其交談識別碼都相同。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-190">Conversation IDs are the same for both the initiator and target endpoints of a conversation.</span></span>  
  
 <span data-ttu-id="c3dfb-191">`conversation_id` **Conversation_endpoints**目錄檢視的資料行中會報告交談識別碼。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-191">Conversation IDs are reported in the `conversation_id` column of the **sys.conversation_endpoints** catalog view.</span></span>  
  
 <span data-ttu-id="c3dfb-192">**-TIMEOUT** *timeout_interval*</span><span class="sxs-lookup"><span data-stu-id="c3dfb-192">**-TIMEOUT** *timeout_interval*</span></span>  
 <span data-ttu-id="c3dfb-193">指定 **RUNTIME** 報表要執行的秒數。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-193">Specifies the number of seconds for a **RUNTIME** report to run.</span></span> <span data-ttu-id="c3dfb-194">如未指定 **-TIMEOUT** ，執行階段報表就會無限期地執行。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-194">If **-TIMEOUT** is not specified the runtime report runs indefinitely.</span></span> <span data-ttu-id="c3dfb-195">**-TIMEOUT** 僅用於 **RUNTIME** 報表，不用在 **CONFIGURATION** 報表。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-195">**-TIMEOUT** is used only on **RUNTIME** reports, not **CONFIGURATION** reports.</span></span> <span data-ttu-id="c3dfb-196">如果沒有指定 **ssbdiagnose** if **-TIMEOUT** 間隔到期之前結束執行階段報表，您可以使用 CTRL + C 結束 **-** 。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-196">Use ctrl + C to quit **ssbdiagnose** if **-TIMEOUT** was not specified or to end a runtime report before the time**-** out interval expires.</span></span> <span data-ttu-id="c3dfb-197">*timeout_interval* 必須是介於 1 和 2,147,483,647 之間的數字。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-197">*timeout_interval* must be a number between 1 and 2,147,483,647.</span></span>  
  
 **\<runtimeconnectionoptions>**  
 <span data-ttu-id="c3dfb-198">指定資料庫的連接資訊，而這些資料庫包含與受監視之交談元素相關聯的服務。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-198">Specifies the connection information for the databases that contain the services associated with conversation elements being monitored.</span></span> <span data-ttu-id="c3dfb-199">如果所有服務都位於相同的資料庫中，您就只需要指定一個 **CONNECT TO** 子句。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-199">If all the services are in the same database, you only have to specify one **CONNECT TO** clause.</span></span> <span data-ttu-id="c3dfb-200">如果各項服務位於不同的資料庫中，您就必須針對每個資料庫提供一個 **CONNECT TO** 子句。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-200">If the services are in separate databases you must supply a **CONNECT TO** clause for each database.</span></span> <span data-ttu-id="c3dfb-201">如未指定 **runtimeconnectionoptions** ，則 **ssbdiagnose** 會使用 **baseconnectionoptions**中的連接資訊。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-201">If **runtimeconnectionoptions** is not specified, **ssbdiagnose** uses the connection information from **baseconnectionoptions**.</span></span>  
  
 <span data-ttu-id="c3dfb-202">**-E**</span><span class="sxs-lookup"><span data-stu-id="c3dfb-202">**-E**</span></span>  
 <span data-ttu-id="c3dfb-203">使用您目前的 Windows 帳戶作為登入識別碼，藉以開啟 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 執行個體的 Windows 驗證連線。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-203">Open a Windows Authentication connection to an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] by using your current Windows account as the login ID.</span></span> <span data-ttu-id="c3dfb-204">登入必須是 **系統管理員** 固定伺服器角色的成員。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-204">The login must be a member of the **sysadmin** fixed-server role.</span></span>  
  
 <span data-ttu-id="c3dfb-205">-E 選項會忽略 SQLCMDUSER 和 SQLCMDPASSWORD 環境變數的使用者與密碼設定。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-205">The -E option ignores the user and password settings of the SQLCMDUSER and SQLCMDPASSWORD environment variables.</span></span>  
  
 <span data-ttu-id="c3dfb-206">如未指定 **-E** 也未指定 **-U** ， **ssbdiagnose** 就會使用 SQLCMDUSER 環境變數的值。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-206">If neither **-E** nor **-U** is specified, **ssbdiagnose** uses the value from the SQLCMDUSER environment variable.</span></span> <span data-ttu-id="c3dfb-207">如果也沒有設定 SQLCMDUSER， **ssbdiagnose** 就會使用 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-207">If SQLCMDUSER is not set either, **ssbdiagnose** uses Windows Authentication.</span></span>  
  
 <span data-ttu-id="c3dfb-208">如果同時使用 **-E** 選項和 **-U** 或 **-P** 選項，就會產生錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-208">If the **-E** option is used together with the **-U** option or the **-P** option, an error message is generated.</span></span>  
  
 <span data-ttu-id="c3dfb-209">**-U** *login_id*</span><span class="sxs-lookup"><span data-stu-id="c3dfb-209">**-U** *login_id*</span></span>  
 <span data-ttu-id="c3dfb-210">使用指定的登入識別碼，藉以開啟 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證連線。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-210">Open a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication connection by using the specified login ID.</span></span> <span data-ttu-id="c3dfb-211">登入必須是 **系統管理員** 固定伺服器角色的成員。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-211">The login must be a member of the **sysadmin** fixed-server role.</span></span>  
  
 <span data-ttu-id="c3dfb-212">如未指定 **-E** 也未指定 **-U** ， **ssbdiagnose** 就會使用 SQLCMDUSER 環境變數的值。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-212">If neither **-E** nor **-U** is specified, **ssbdiagnose** uses the value from the SQLCMDUSER environment variable.</span></span> <span data-ttu-id="c3dfb-213">如果也沒有設定 SQLCMDUSER， **ssbdiagnose** 就會根據正在執行 **ssbdiagnose**的使用者 Windows 帳戶，使用 Windows 驗證模式嘗試連接。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-213">If SQLCMDUSER is not set either, **ssbdiagnose** tries to connect by using Windows Authentication mode based on the Windows account of the user who is running **ssbdiagnose**.</span></span>  
  
 <span data-ttu-id="c3dfb-214">如果同時使用 **-U** 選項和 **-E** 選項，就會產生錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-214">If the **-U** option is used together with the **-E** option, an error message is generated.</span></span> <span data-ttu-id="c3dfb-215">如果 **-U** 選項後面有多個引數，就會產生錯誤訊息並結束程式。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-215">If the **-U** option is followed by more than one argument, an error message is generated and the program exits.</span></span>  
  
 <span data-ttu-id="c3dfb-216">**-P** *password*</span><span class="sxs-lookup"><span data-stu-id="c3dfb-216">**-P** *password*</span></span>  
 <span data-ttu-id="c3dfb-217">指定 **-U** 登入識別碼的密碼。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-217">Specifies the password for the **-U** login ID.</span></span> <span data-ttu-id="c3dfb-218">密碼會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-218">Passwords are case sensitive.</span></span> <span data-ttu-id="c3dfb-219">如果使用了 **-U** 選項，但沒有使用 **-P** 選項， **ssbdiagnose** 就會使用 SQLCMDPASSWORD 環境變數的值。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-219">If the **-U** option is used and the **-P** option is not used, **ssbdiagnose** uses the value from the SQLCMDPASSWORD environment variable.</span></span> <span data-ttu-id="c3dfb-220">如果也沒有設定 SQLCMDPASSWORD， **ssbdiagnose** 就會提示使用者輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-220">If SQLCMDPASSWORD is not set either, **ssbdiagnose** prompts the user for a password.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="c3dfb-221">當您輸入 SET SQLCMDPASSWORD 命令時，任何能夠查看監視器的人都可以看到密碼。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-221">When you type a SET SQLCMDPASSWORD command, your password will be visible to anyone who can see your monitor.</span></span>  
  
 <span data-ttu-id="c3dfb-222">如果指定了 **-P** 選項但無密碼， **ssbdiagnose** 就會使用預設密碼 (NULL)。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-222">If the **-P** option is specified without a password **ssbdiagnose** uses the default password (NULL).</span></span>  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteStrongPass](../../includes/ssnotestrongpass-md.md)] <span data-ttu-id="c3dfb-223">如需詳細資訊，請參閱[增強式密碼](../../relational-databases/security/strong-passwords.md)。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-223">For more information, see [Strong Passwords](../../relational-databases/security/strong-passwords.md).</span></span>  
  
 <span data-ttu-id="c3dfb-224">密碼提示的顯示方式，會以將密碼提示輸出到主控台的方式顯示，如： `Password:`</span><span class="sxs-lookup"><span data-stu-id="c3dfb-224">The password prompt is displayed by printing the password prompt to the console, as follows: `Password:`</span></span>  
  
 <span data-ttu-id="c3dfb-225">使用者輸入為隱藏狀態。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-225">User input is hidden.</span></span> <span data-ttu-id="c3dfb-226">這表示畫面上不會顯示任何內容，而且游標也不會移動。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-226">This means that nothing is displayed and the cursor stays in position.</span></span>  
  
 <span data-ttu-id="c3dfb-227">如果同時使用 **-P** 選項和 **-E** 選項，就會產生錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-227">If the **-P** option is used with the **-E** option, an error message is generated.</span></span>  
  
 <span data-ttu-id="c3dfb-228">如果 **-P** 選項後面有多個引數，就會產生錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-228">If the **-P** option is followed by more than one argument, an error message is generated.</span></span>  
  
 <span data-ttu-id="c3dfb-229">**-S** *server_name*[\\*instance_name*]</span><span class="sxs-lookup"><span data-stu-id="c3dfb-229">**-S** *server_name*[\\*instance_name*]</span></span>  
 <span data-ttu-id="c3dfb-230">指定保存要分析之 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 服務的 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-230">Specifies the instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] that holds the [!INCLUDE[ssSB](../../includes/sssb-md.md)] services to be analyzed.</span></span>  
  
 <span data-ttu-id="c3dfb-231">指定 *server_name* ，即可連接至該伺服器上之 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的預設執行個體。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-231">Specify *server_name* to connect to the default instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] on that server.</span></span> <span data-ttu-id="c3dfb-232">指定*server_name ***\\*** instance_name* ，以連接到該伺服器上之的已命名實例 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-232">Specify *server_name***\\***instance_name* to connect to a named instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] on that server.</span></span> <span data-ttu-id="c3dfb-233">如未指定 **-S** ，則 **ssbdiagnose** 會使用 SQLCMDSERVER 環境變數的值。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-233">If **-S** is not specified, **ssbdiagnose** uses the value of the SQLCMDSERVER environment variable.</span></span> <span data-ttu-id="c3dfb-234">如果也沒有設定 SQLCMDSERVER， **ssbdiagnose** 就會連接至本機電腦上的 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 預設執行個體。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-234">If SQLCMDSERVER is not set either, **ssbdiagnose** connects to the default instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] on the local computer.</span></span>  
  
 <span data-ttu-id="c3dfb-235">**-d** *database_name*</span><span class="sxs-lookup"><span data-stu-id="c3dfb-235">**-d** *database_name*</span></span>  
 <span data-ttu-id="c3dfb-236">指定保存要分析之 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 服務的資料庫。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-236">Specifies the database that holds the [!INCLUDE[ssSB](../../includes/sssb-md.md)] services to be analyzed.</span></span> <span data-ttu-id="c3dfb-237">如果此資料庫不存在，就會產生錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-237">If the database does not exist, an error message is generated.</span></span> <span data-ttu-id="c3dfb-238">如未指定 **-d** ，預設值就是登入之預設資料庫屬性中所指定的資料庫。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-238">If **-d** is not specified, the default is the database specified in the default-database property for your login.</span></span>  
  
 <span data-ttu-id="c3dfb-239">**-l** *login_timeout*</span><span class="sxs-lookup"><span data-stu-id="c3dfb-239">**-l** *login_timeout*</span></span>  
 <span data-ttu-id="c3dfb-240">指定嘗試連接至伺服器會發生逾時之前，所經過的秒數。如未指定 **-l** ， **ssbdiagnose** 就會使用針對 SQLCMDLOGINTIMEOUT 環境變數所設定的值。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-240">Specifies the number of seconds before an attempt to connect to a server times out. If **-l** is not specified, **ssbdiagnose** uses the value set for the SQLCMDLOGINTIMEOUT environment variable.</span></span> <span data-ttu-id="c3dfb-241">如果也沒有指定 SQLCMDLOGINTIMEOUT，預設的逾時就是三十秒。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-241">If SQLCMDLOGINTIMEOUT is not set either, the default time-out is thirty seconds.</span></span> <span data-ttu-id="c3dfb-242">此登入逾時必須是介於 0 和 65534 之間的數字。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-242">The login time-out must be a number between 0 and 65534.</span></span> <span data-ttu-id="c3dfb-243">如果所提供的值不是數值或不在該範圍內， **ssbdiagnose** 就會產生錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-243">If the value that is supplied is not numeric or does not fall into that range, **ssbdiagnose** generates an error message.</span></span> <span data-ttu-id="c3dfb-244">0 值指定逾時值無限。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-244">A value of 0 specifies time-out to be infinite.</span></span>  
  
 <span data-ttu-id="c3dfb-245">**-?**</span><span class="sxs-lookup"><span data-stu-id="c3dfb-245">**-?**</span></span>  
 <span data-ttu-id="c3dfb-246">顯示命令列說明。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-246">Displays command line help.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c3dfb-247">備註</span><span class="sxs-lookup"><span data-stu-id="c3dfb-247">Remarks</span></span>  
 <span data-ttu-id="c3dfb-248">您可以使用 **ssbdiagnose** 執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="c3dfb-248">Use **ssbdiagnose** to do the following:</span></span>  
  
-   <span data-ttu-id="c3dfb-249">在新設定的 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 應用程式中，確認沒有任何組態錯誤。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-249">Confirm that there are no configuration errors in a newly configured [!INCLUDE[ssSB](../../includes/sssb-md.md)] application.</span></span>  
  
-   <span data-ttu-id="c3dfb-250">在您變更現有 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 應用程式的組態之後，確認沒有任何組態錯誤。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-250">Confirm that there are no configuration errors after changing the configuration of an existing [!INCLUDE[ssSB](../../includes/sssb-md.md)] application.</span></span>  
  
-   <span data-ttu-id="c3dfb-251">在 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 資料庫卸離，然後重新附加至新的 [!INCLUDE[ssDE](../../includes/ssde-md.md)]執行個體之後，確認沒有任何組態錯誤。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-251">Confirm that there are no configuration errors after a [!INCLUDE[ssSB](../../includes/sssb-md.md)] database is detached and then reattached to a new instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
-   <span data-ttu-id="c3dfb-252">當訊息無法順利在服務之間傳輸時，研究是否存在組態錯誤。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-252">Research whether there are configuration errors when messages are not successfully transmitted between services.</span></span>  
  
-   <span data-ttu-id="c3dfb-253">取得在一組 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 交談元素中發生之任何錯誤的報表。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-253">Get a report of any errors that occur in a set of [!INCLUDE[ssSB](../../includes/sssb-md.md)] conversation elements.</span></span>  
  
## <a name="configuration-reporting"></a><span data-ttu-id="c3dfb-254">組態報表</span><span class="sxs-lookup"><span data-stu-id="c3dfb-254">Configuration Reporting</span></span>  
 <span data-ttu-id="c3dfb-255">若要正確分析交談所使用的組態，請執行與交談使用相同選項的 **ssbdiagnose** 組態報表。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-255">To correctly analyze the configuration used by a conversation, run a **ssbdiagnose** configuration report that uses the same options that are used by the conversation.</span></span> <span data-ttu-id="c3dfb-256">如果您為 **ssbdiagnose** 指定的選項層級低於交談所使用的選項層級，則 **ssbdiagnose** 可能不會報告交談所需的條件。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-256">If you specify a lower level of options for **ssbdiagnose** than are used by the conversation, **ssbdiagnose** might not report conditions that are required by the conversation.</span></span> <span data-ttu-id="c3dfb-257">如果您為 **ssbdiagnose**指定較高的選項層級，它可能會報告交談所不需要的報表項目。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-257">If you specify a higher level of options for **ssbdiagnose**, it might report items that are not required by the conversation.</span></span> <span data-ttu-id="c3dfb-258">例如，在相同資料庫中兩個服務之間的交談，可能會在 ENCPRYPTION OFF 的情況下執行。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-258">For example, a conversation between two services in the same database can be run with ENCPRYPTION OFF.</span></span> <span data-ttu-id="c3dfb-259">如果您執行 **ssbdiagnose** 以驗證這兩個服務之間的組態，但卻使用預設的 ENCRYPTION ON 設定， **ssbdiagnose** 就會報告資料庫缺少主要金鑰。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-259">If you run **ssbdiagnose** to validate the configuration between the two services, but use the default ENCRYPTION ON setting, **ssbdiagnose** reports that the database is missing a master key.</span></span> <span data-ttu-id="c3dfb-260">這種交談不需要使用主要金鑰。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-260">A master key is not required for the conversation.</span></span>  
  
 <span data-ttu-id="c3dfb-261">每次執行 **ssbdiagnose** 組態報表時，它只會分析一個 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 服務或一對服務。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-261">The **ssbdiagnose** configuration report analyzes only one [!INCLUDE[ssSB](../../includes/sssb-md.md)] service or a single pair of services every time it is run.</span></span> <span data-ttu-id="c3dfb-262">若要報告多對 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 服務，請建立多次呼叫 **ssbdiagnose** 的 .cmd 命令檔。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-262">To report on multiple pairs of [!INCLUDE[ssSB](../../includes/sssb-md.md)] services, build a .cmd command file that calls **ssbdiagnose** multiple times.</span></span>  
  
## <a name="runtime-reporting"></a><span data-ttu-id="c3dfb-263">執行階段報表</span><span class="sxs-lookup"><span data-stu-id="c3dfb-263">Runtime Reporting</span></span>  
 <span data-ttu-id="c3dfb-264">指定 -RUNTIME 時， **ssbdiagnose** 會搜尋 **runtimeconnectionoptions** 和 **baseconnectionoptions** 中指定的所有資料庫，建立一份 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 識別碼清單。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-264">When -RUNTIME is specified, **ssbdiagnose** searches all databases specified in **runtimeconnectionoptions** and **baseconnectionoptions** to build a list of [!INCLUDE[ssSB](../../includes/sssb-md.md)] IDs.</span></span> <span data-ttu-id="c3dfb-265">所建立的完整識別碼清單會因針對 -NEW 和 -ID 指定的內容而不同：</span><span class="sxs-lookup"><span data-stu-id="c3dfb-265">The full list of IDs built depends on what is specified for -NEW and -ID:</span></span>  
  
-   <span data-ttu-id="c3dfb-266">如未指定 **-NEW** 或 **-ID** ，此清單就會包含連線選項中指定之所有資料庫的所有交談。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-266">If neither **-NEW** or **-ID** are specified, the list includes all conversations for all databases specified in the connection options.</span></span>  
  
-   <span data-ttu-id="c3dfb-267">如果指定了 **-NEW** ， **ssbdiagnose** 就會包含 **ssbdiagnose** 執行之後開始的第一個交談的元素。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-267">If **-NEW** is specified, **ssbdiagnose** includes the elements for the first conversation that starts after **ssbdiagnose** is run.</span></span> <span data-ttu-id="c3dfb-268">這同時包括目標和起始端交談端點的交談識別碼與交談控制代碼。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-268">This includes the conversation ID and the conversation handles for both the target and initiator conversation endpoints.</span></span>  
  
-   <span data-ttu-id="c3dfb-269">如果指定了 **-ID** 與交談控制代碼，只有該控制代碼會包含在清單中。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-269">If **-ID** is specified with a conversation handle, only that handle is included in the list.</span></span>  
  
-   <span data-ttu-id="c3dfb-270">如果指定了 **-ID** 與交談識別碼，則交談識別碼及其兩個交談端點的控制代碼都會加入清單中。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-270">If **-ID** is specified with a conversation ID, the conversation ID and the handles for both of its conversation endpoints are added to the list.</span></span>  
  
-   <span data-ttu-id="c3dfb-271">如果指定了 **-ID** 與交談群組識別碼，則該群組中的所有交談識別碼和交談控制代碼都會加入清單中。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-271">If **-ID** is specified with a conversation group ID, all the conversation IDs and conversation handles in that group are added to the list.</span></span>  
  
 <span data-ttu-id="c3dfb-272">此清單不會包含連接選項未涵蓋之資料庫的元素。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-272">The list does not include elements from databases that are not covered by the connection options.</span></span> <span data-ttu-id="c3dfb-273">例如，假設您使用 **-ID** 指定交談識別碼，但是僅針對起始端資料庫 (而非目標資料庫) 提供 **runtimeconnectionoptions** 子句。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-273">For example, assume that you use **-ID** to specify a conversation ID, but only provide a **runtimeconnectionoptions** clause for the initiator database and not the target database.</span></span> <span data-ttu-id="c3dfb-274">**ssbdiagnose** 不會在其識別碼清單中包含目標交談控制代碼，而只會包含交談識別碼和起始端交談控制代碼。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-274">**ssbdiagnose** will not include the target conversation handle in its list of IDs, only the conversation ID and the initiator conversation handle.</span></span>  
  
 <span data-ttu-id="c3dfb-275">**ssbdiagnose** 監視 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] runtimeconnectionoptions **和** baseconnectionoptions **涵蓋的資料庫**事件。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-275">**ssbdiagnose** monitors the [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] events from the databases covered by **runtimeconnectionoptions** and **baseconnectionoptions**.</span></span> <span data-ttu-id="c3dfb-276">它會搜尋 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 事件，指出執行階段清單中一或多個 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 識別碼發生的錯誤。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-276">It searches for [!INCLUDE[ssSB](../../includes/sssb-md.md)] events that indicate an error was encountered by one or more of the [!INCLUDE[ssSB](../../includes/sssb-md.md)] IDs in the runtime list.</span></span> <span data-ttu-id="c3dfb-277">**ssbdiagnose** 也會搜尋未特別與任何交談群組相關聯的系統層級 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 錯誤事件。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-277">**ssbdiagnose** also searches for system-level [!INCLUDE[ssSB](../../includes/sssb-md.md)] error events not specifically associated with any conversation group.</span></span>  
  
 <span data-ttu-id="c3dfb-278">如果 **ssbdiagnose** 找到交談錯誤，此公用程式就會透過同時執行組態報表，嘗試報告事件的根本原因。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-278">If **ssbdiagnose** finds conversation errors, the utility will attempt to report on the root cause of the events by also running a configuration report.</span></span> <span data-ttu-id="c3dfb-279">**ssbdiagnose** 會使用資料庫內的中繼資料，嘗試判斷交談所使用的執行個體、 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 識別碼、資料庫、服務與合約。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-279">**ssbdiagnose** uses the metadata in the databases to try to determine the instances, [!INCLUDE[ssSB](../../includes/sssb-md.md)] IDs, databases, services, and contracts used by the conversation.</span></span> <span data-ttu-id="c3dfb-280">然後，它會使用所有可用的資訊來執行組態報表。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-280">It then runs a configuration report using all available information.</span></span>  
  
 <span data-ttu-id="c3dfb-281">**ssbdiagnose** 預設不會報告錯誤事件。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-281">By default, **ssbdiagnose** does not report error events.</span></span> <span data-ttu-id="c3dfb-282">它只會報告在組態檢查期間所找到的基礎問題。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-282">It only reports the underlying issues found during the configuration check.</span></span> <span data-ttu-id="c3dfb-283">如此會將報告的資訊量減到最少，協助您將焦點集中在基礎組態問題。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-283">This minimizes the amount of information reported and helps you focus on the underlying configuration issues.</span></span> <span data-ttu-id="c3dfb-284">您可以指定 **-SHOWEVENTS** ，以便查看 **ssbdiagnose**所遇到的錯誤事件。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-284">You can specify **-SHOWEVENTS** to see the error events encountered by **ssbdiagnose**.</span></span>  
  
## <a name="issues-reported-by-ssbdiagnose"></a><span data-ttu-id="c3dfb-285">ssbdiagnose 所報告的問題</span><span class="sxs-lookup"><span data-stu-id="c3dfb-285">Issues Reported by ssbdiagnose</span></span>  
 <span data-ttu-id="c3dfb-286">**ssbdiagnose** 會報告三種問題類別。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-286">**ssbdiagnose** reports three classes of issues.</span></span> <span data-ttu-id="c3dfb-287">在 XML 輸出檔中，每種問題類別都會報告成個別的 Issue 元素類型。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-287">In the XML output file, each class of issue is reported as a separate type of the Issue element.</span></span> <span data-ttu-id="c3dfb-288">**ssbdiagnose** 所報告的三種問題類型如下：</span><span class="sxs-lookup"><span data-stu-id="c3dfb-288">The three types of issues reported by **ssbdiagnose** are as follows:</span></span>  
  
 <span data-ttu-id="c3dfb-289">**診斷**</span><span class="sxs-lookup"><span data-stu-id="c3dfb-289">**Diagnosis**</span></span>  
 <span data-ttu-id="c3dfb-290">報告組態問題。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-290">Reports a configuration issue.</span></span> <span data-ttu-id="c3dfb-291">這包括在 **CONFIGURATION** 報表執行時或 **RUNTIME** 報表的組態階段期間所發現的問題。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-291">This includes issues found either a **CONFIGURATION** report is running, or during the configuration phase of a **RUNTIME** report.</span></span> <span data-ttu-id="c3dfb-292">**ssbdiagnose** 每個組態問題只報告一次。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-292">**ssbdiagnose** reports each configuration issue one time.</span></span>  
  
 <span data-ttu-id="c3dfb-293">**事件**</span><span class="sxs-lookup"><span data-stu-id="c3dfb-293">**Event**</span></span>  
 <span data-ttu-id="c3dfb-294">報告 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 事件，指出在 **RUNTIME** 報表期間監視的交談所遇到的問題。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-294">Reports a [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] event that indicates a problem was encountered by a conversation being monitored during a **RUNTIME** report.</span></span> <span data-ttu-id="c3dfb-295">**ssbdiagnose** 會在每次事件產生時報告這些事件。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-295">**ssbdiagnose** reports events every time they are generated.</span></span> <span data-ttu-id="c3dfb-296">如果許多交談都遇到該問題，可能會報告多次該事件。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-296">Events can be reported multiple times if several conversations encounter the problem.</span></span>  
  
 <span data-ttu-id="c3dfb-297">**問題**</span><span class="sxs-lookup"><span data-stu-id="c3dfb-297">**Problem**</span></span>  
 <span data-ttu-id="c3dfb-298">報告會讓 **ssbdiagnose** 無法完成組態分析或無法監視交談的問題。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-298">Reports an issue that is preventing **ssbdiagnose** from completing a configuration analysis or from monitoring conversations.</span></span>  
  
## <a name="sqlcmd-environment-variables"></a><span data-ttu-id="c3dfb-299">sqlcmd 環境變數</span><span class="sxs-lookup"><span data-stu-id="c3dfb-299">sqlcmd Environment Variables</span></span>  
 <span data-ttu-id="c3dfb-300">**ssbdiagnose** 公用程式支援 **sqlcmd** 公用程式也使用的 SQLCMDSERVER、SQLCMDUSER、SQLCMDPASSWORD 和 SQLCMDLOGINTIMOUT 環境變數。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-300">The **ssbdiagnose** utility supports the SQLCMDSERVER, SQLCMDUSER, SQLCMDPASSWORD, and SQLCMDLOGINTIMOUT environment variables that are also used by the **sqlcmd** utility.</span></span> <span data-ttu-id="c3dfb-301">您可以使用命令提示字元 SET 命令，或在用 **sqlcmd** 執行的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 指令碼中使用 **setvar**命令，來設定這些環境變數。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-301">You can set the environment variables either by using the command prompt SET command, or by using the **setvar** command in [!INCLUDE[tsql](../../includes/tsql-md.md)] scripts that you run by using **sqlcmd**.</span></span> <span data-ttu-id="c3dfb-302">如需如何在 **sqlcmd** 中使用 **setvar**的詳細資訊，請參閱 [以指令碼變數使用 sqlcmd](../../relational-databases/scripting/sqlcmd-use-with-scripting-variables.md)。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-302">For more information about how to use **setvar** in **sqlcmd**, see [Use sqlcmd with Scripting Variables](../../relational-databases/scripting/sqlcmd-use-with-scripting-variables.md).</span></span>  
  
## <a name="permissions"></a><span data-ttu-id="c3dfb-303">權限</span><span class="sxs-lookup"><span data-stu-id="c3dfb-303">Permissions</span></span>  
 <span data-ttu-id="c3dfb-304">在每個 **connectionoptions** 子句中，使用 **-E** 或 **-U** 指定的登入，必須是以 **-S** 所指定之執行個體內 **系統管理員**固定伺服器角色的成員。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-304">In each **connectionoptions** clause, the login specified with either **-E** or **-U** must be a member of the **sysadmin** fixed-server role in the instance specified in **-S**.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="c3dfb-305">範例</span><span class="sxs-lookup"><span data-stu-id="c3dfb-305">Examples</span></span>  
 <span data-ttu-id="c3dfb-306">本節包含在命令提示字元處使用 **ssbdiagnose** 的範例。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-306">This section contains examples of using **ssbdiagnose** at a command prompt.</span></span>  
  
### <a name="a-checking-the-configuration-of-two-services-in-the-same-database"></a><span data-ttu-id="c3dfb-307">A.</span><span class="sxs-lookup"><span data-stu-id="c3dfb-307">A.</span></span> <span data-ttu-id="c3dfb-308">檢查相同的資料庫中兩個服務的組態</span><span class="sxs-lookup"><span data-stu-id="c3dfb-308">Checking the Configuration of Two Services in the Same Database</span></span>  
 <span data-ttu-id="c3dfb-309">下列範例將示範如何在下列條件成立時要求組態報表：</span><span class="sxs-lookup"><span data-stu-id="c3dfb-309">The following example shows how to request a configuration report when the following are true;</span></span>  
  
-   <span data-ttu-id="c3dfb-310">起始端和目標服務位於相同的資料庫中。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-310">The initiator and target service are in the same database.</span></span>  
  
-   <span data-ttu-id="c3dfb-311">資料庫位於 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的預設執行個體中。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-311">The database is in the default instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
-   <span data-ttu-id="c3dfb-312">執行個體位於執行 **ssbdiagnose** 的同一部電腦上。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-312">The instances is on the same computer on which **ssbdiagnose** is run.</span></span>  
  
 <span data-ttu-id="c3dfb-313">**ssbdiagnose** 公用程式會報告使用 DEFAULT 合約的組態，因為沒有指定 ON CONTRACT。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-313">The **ssbdiagnose** utility reports the configuration that uses the DEFAULT contract because ON CONTRACT is not specified.</span></span>  
  
```  
ssbdiagnose -E -d MyDatabase CONFIGURATION FROM SERVICE /test/initiator TO SERVICE /test/target  
```  
  
### <a name="b-checking-the-configuration-of-two-services-on-separate-computers-that-use-one-login"></a><span data-ttu-id="c3dfb-314">B.</span><span class="sxs-lookup"><span data-stu-id="c3dfb-314">B.</span></span> <span data-ttu-id="c3dfb-315">檢查使用單一登入之不同電腦上的兩個服務之組態</span><span class="sxs-lookup"><span data-stu-id="c3dfb-315">Checking the Configuration of Two Services on Separate Computers That Use One Login</span></span>  
 <span data-ttu-id="c3dfb-316">下列範例將示範如何在起始端和目標服務位於不同的電腦，但是可以使用相同的 Windows 驗證登入存取時，要求組態報表。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-316">The following example shows how to request a configuration report when the initiator and target service are on separate computers, but can be accessed by using the same Windows Authentication login.</span></span>  
  
```  
ssbdiagnose -E CONFIGURATION FROM SERVICE /text/initiator -S InitiatorComputer -d InitiatorDatabase TO SERVICE /test/target -S TargetComputer -d TargetDatabase ON CONTRACT TestContract  
```  
  
### <a name="c-checking-the-configuration-of-two-services-on-separate-computers-that-use-separate-logins"></a><span data-ttu-id="c3dfb-317">C.</span><span class="sxs-lookup"><span data-stu-id="c3dfb-317">C.</span></span> <span data-ttu-id="c3dfb-318">檢查使用不同登入之不同電腦上兩個服務的組態</span><span class="sxs-lookup"><span data-stu-id="c3dfb-318">Checking the Configuration of Two Services on Separate Computers That Use Separate Logins</span></span>  
 <span data-ttu-id="c3dfb-319">下列範例將示範如何在起始端和目標服務位於不同的電腦，而且每個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體都需要不同的 [!INCLUDE[ssDE](../../includes/ssde-md.md)]驗證登入時，要求組態報表。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-319">The following example shows how to request a configuration report when the initiator and target service are on separate computers, and separate [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication logins are required for each instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
```  
ssbdiagnose CONFIGURATION FROM SERVICE /text/initiator   
-S InitiatorComputer -U InitiatorLogin -p !wEx23Dvb   
-d InitiatorDatabase TO SERVICE /test/target -S TargetComputer   
-U TargetLogin -p ER!49jiy -d TargetDatabase ON CONTRACT TestContract  
```  
  
### <a name="d-checking-mirrored-service-configurations-on-separate-computers-with-anonymous-encryption"></a><span data-ttu-id="c3dfb-320">D.</span><span class="sxs-lookup"><span data-stu-id="c3dfb-320">D.</span></span> <span data-ttu-id="c3dfb-321">檢查具有匿名加密的不同電腦上之鏡像服務組態</span><span class="sxs-lookup"><span data-stu-id="c3dfb-321">Checking Mirrored Service Configurations on Separate Computers With Anonymous Encryption</span></span>  
 <span data-ttu-id="c3dfb-322">下列範例將示範如何在起始端和目標服務位於不同的電腦，而且起始端鏡像至具名執行個體時，要求組態報表。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-322">The following example shows how to request a configuration report when the initiator and target service are on separate computers and the initiator is mirrored to a named instance.</span></span> <span data-ttu-id="c3dfb-323">此報表也會確認這些服務都設定為使用匿名加密。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-323">The report also verifies that the services are configured to use anonymous encryption.</span></span>  
  
```  
ssbdiagnose -E CONFIGURATION FROM SERVICE /text/initiator   
-S InitiatorComputer -d InitiatorDatabase MIRROR   
-S MirrorComputer/MirrorInstance TO SERVICE /test/target   
-S TargetComputer -d TargetDatabase ON CONTRACT TestContract ENCRYPTION ANONYMOUS  
```  
  
### <a name="e-checking-the-configuration-of-two-contracts"></a><span data-ttu-id="c3dfb-324">E.</span><span class="sxs-lookup"><span data-stu-id="c3dfb-324">E.</span></span> <span data-ttu-id="c3dfb-325">檢查兩個合約的組態</span><span class="sxs-lookup"><span data-stu-id="c3dfb-325">Checking the Configuration of Two Contracts</span></span>  
 <span data-ttu-id="c3dfb-326">下列範例將示範如何建立命令檔，以便在下列條件成立時要求組態報表：</span><span class="sxs-lookup"><span data-stu-id="c3dfb-326">The following example shows how to build a command file that requests configuration reports when the following are true:</span></span>  
  
-   <span data-ttu-id="c3dfb-327">起始端和目標服務位於相同的資料庫中。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-327">The initiator and target service are in the same database.</span></span>  
  
-   <span data-ttu-id="c3dfb-328">資料庫位於 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的預設執行個體中。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-328">The database is in the default instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
-   <span data-ttu-id="c3dfb-329">執行個體位於執行 **ssbdiagnose** 的同一部電腦上。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-329">The instance is on the same computer on which **ssbdiagnose** is run.</span></span>  
  
 <span data-ttu-id="c3dfb-330">每次執行 **ssbdiagnose** 時，它就會針對相同服務之間的不同合約報告組態。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-330">Each time **ssbdiagnose** is run it reports the configuration for a different contract between the same services.</span></span>  
  
```  
ssbdiagnose -E -d MyDatabase CONFIGURATION FROM SERVICE   
/test/initiator TO SERVICE /test/target ON CONTRACT PayRaiseContract  
ssbdiagnose -E -d MyDatabase CONFIGURATION FROM SERVICE /test/initiator   
TO SERVICE /test/target ON CONTRACT PromotionContract  
```  
  
### <a name="f-monitor-the-status-of-a-specific-conversation-on-the-local-computer-with-a-time-out"></a><span data-ttu-id="c3dfb-331">F.</span><span class="sxs-lookup"><span data-stu-id="c3dfb-331">F.</span></span> <span data-ttu-id="c3dfb-332">在具有逾時之本機電腦上監視特定交談的狀態</span><span class="sxs-lookup"><span data-stu-id="c3dfb-332">Monitor the status of a specific conversation on the local computer with a time out</span></span>  
 <span data-ttu-id="c3dfb-333">下列範例將示範如何監視特定交談，其中起始端和目標服務位於執行 **ssbdiagnose**之相同電腦的預設執行個體內的相同資料庫中。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-333">The following example shows how to monitor a specific conversation where the initiator and target services are in the same database in the default instance of the same computer that is running **ssbdiagnose**.</span></span> <span data-ttu-id="c3dfb-334">其逾時間隔設定為 20 秒。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-334">The time-out interval is set to 20 seconds.</span></span>  
  
```  
ssbdiagnose -E -d TestDatabase RUNTIME -ID D68D77A9-B1CF-41BF-A5CE-279ABCAB140D -TIMEOUT 20  
```  
  
### <a name="g-monitor-the-status-of-a-conversation-that-spans-two-computers"></a><span data-ttu-id="c3dfb-335">G.</span><span class="sxs-lookup"><span data-stu-id="c3dfb-335">G.</span></span> <span data-ttu-id="c3dfb-336">監視跨越兩部電腦之交談的狀態</span><span class="sxs-lookup"><span data-stu-id="c3dfb-336">Monitor the status of a conversation that spans two computers</span></span>  
 <span data-ttu-id="c3dfb-337">下列範例將示範如何監視特定交談，其中起始端和目標服務位於不同的電腦上。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-337">The following example shows how to monitor a specific conversation where the initiator and target services are on separate computers.</span></span>  
  
```  
ssbdiagnose RUNTIME -ID D68D77A9-B1CF-41BF-A5CE-279ABCAB140D   
-TIMEOUT 10 CONNECT TO -E -S InitiatorComputer/InitiatorInstance   
-d InitiatorDatabase CONNECT TO -E -S TargetComputer/TargetInstance   
-d TargetDatabase  
```  
  
### <a name="h-monitor-the-status-of-a-conversation-in-two-databases-in-the-same-instance"></a><span data-ttu-id="c3dfb-338">H.</span><span class="sxs-lookup"><span data-stu-id="c3dfb-338">H.</span></span> <span data-ttu-id="c3dfb-339">監視相同執行個體內兩個資料庫中的交談狀態</span><span class="sxs-lookup"><span data-stu-id="c3dfb-339">Monitor the status of a conversation in two databases in the same instance</span></span>  
 <span data-ttu-id="c3dfb-340">下列範例將示範如何監視特定交談，其中起始端和目標服務位於相同 [!INCLUDE[ssDE](../../includes/ssde-md.md)]執行個體的不同資料庫中。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-340">The following example shows how to monitor a specific conversation where the initiator and target services are in separate databases in the same instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span> <span data-ttu-id="c3dfb-341">此範例會使用 **baseconnectionoptions** 指定執行個體和登入資訊，並且使用兩個 CONNECT TO 子句來指定資料庫。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-341">The example uses the **baseconnectionoptions** to specify the instance and login information, and two CONNECT TO clauses to specify the databases.</span></span> <span data-ttu-id="c3dfb-342">此外，也指定了 -SHOWEVENTS，如此所有執行階段事件都會包含在報表輸出中。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-342">-SHOWEVENTS is specified so that all runtime events are included in the report output.</span></span>  
  
```  
ssbdiagnose -E -S TestComputer/DevTestInstance RUNTIME -SHOWEVENTS   
-ID 5094d4a7-e38c-4c37-da37-1d58b1cb8455 -TIMEOUT 10 CONNECT TO   
-d InitiatorDatabase CONNECT TO -d TargetDatabase  
```  
  
### <a name="i-monitor-the-status-of-two-conversations-between-two-databases"></a><span data-ttu-id="c3dfb-343">I.</span><span class="sxs-lookup"><span data-stu-id="c3dfb-343">I.</span></span> <span data-ttu-id="c3dfb-344">監視兩個資料庫之間兩個交談的狀態</span><span class="sxs-lookup"><span data-stu-id="c3dfb-344">Monitor the status of two conversations between two databases</span></span>  
 <span data-ttu-id="c3dfb-345">下列範例將示範如何監視兩個交談，其中起始端和目標服務位於相同 [!INCLUDE[ssDE](../../includes/ssde-md.md)]執行個體的不同資料庫中。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-345">The following example shows how to monitor two conversations where the initiator and target services are in separate databases in the same instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span> <span data-ttu-id="c3dfb-346">此範例會使用 **baseconnectionoptions** 指定執行個體和登入資訊，並且使用兩個 CONNECT TO 子句來指定資料庫。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-346">The example uses the **baseconnectionoptions** to specify the instance and login information, and two CONNECT TO clauses to specify the databases.</span></span>  
  
```  
ssbdiagnose -E -S TestComputer/DevTestInstance RUNTIME   
-ID 5094d4a7-e38c-4c37-da37-1d58b1cb8455   
-ID 9b293be9-226b-4e22-e169-1d2c2c15be86 -TIMEOUT 10 CONNECT TO   
-d InitiatorDatabase CONNECT TO -d TargetDatabase  
```  
  
### <a name="j-monitor-the-status-of-all-conversations-between-two-databases"></a><span data-ttu-id="c3dfb-347">J.</span><span class="sxs-lookup"><span data-stu-id="c3dfb-347">J.</span></span> <span data-ttu-id="c3dfb-348">監視兩個資料庫之間的所有交談狀態</span><span class="sxs-lookup"><span data-stu-id="c3dfb-348">Monitor the status of all conversations between two databases</span></span>  
 <span data-ttu-id="c3dfb-349">下列範例將示範如何監視相同 [!INCLUDE[ssDE](../../includes/ssde-md.md)]執行個體中兩個資料庫之間的所有交談。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-349">The following example shows how to monitor all the conversation between two databases in the same instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span> <span data-ttu-id="c3dfb-350">此範例會使用 **baseconnectionoptions** 指定執行個體和登入資訊，並且使用兩個 CONNECT TO 子句來指定資料庫。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-350">The example uses the **baseconnectionoptions** to specify the instance and login information, and two CONNECT TO clauses to specify the databases.</span></span>  
  
```  
ssbdiagnose -E -S TestComputer/DevTestInstance RUNTIME   
-TIMEOUT 10 CONNECT TO -d InitiatorDatabase CONNECT TO   
-d TargetDatabase  
```  
  
### <a name="k-ignore-specific-errors"></a><span data-ttu-id="c3dfb-351">K.</span><span class="sxs-lookup"><span data-stu-id="c3dfb-351">K.</span></span> <span data-ttu-id="c3dfb-352">忽略特定錯誤</span><span class="sxs-lookup"><span data-stu-id="c3dfb-352">Ignore Specific Errors</span></span>  
 <span data-ttu-id="c3dfb-353">下列範例將示範如何在目前已設定啟用方式的測試系統中忽略已知的錯誤 (303 和 304)。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-353">The following example shows how to ignore known errors (303 and 304) in how activation is currently configured in a test system.</span></span>  
  
```  
ssbdiagnose -IGNORE 303 -IGNORE 304 -E -d TestDatabase   
CONFIGURATION FROM SERVICE /test/initiator TO SERVICE /test/target   
ON CONTRACT TextContract  
```  
  
### <a name="l-redirecting-ssbdiagnose-xml-output"></a><span data-ttu-id="c3dfb-354">L.</span><span class="sxs-lookup"><span data-stu-id="c3dfb-354">L.</span></span> <span data-ttu-id="c3dfb-355">重新導向 ssbdiagnose XML 輸出</span><span class="sxs-lookup"><span data-stu-id="c3dfb-355">Redirecting ssbdiagnose XML Output</span></span>  
 <span data-ttu-id="c3dfb-356">下列範例將示範如何要求 **ssbdiagnose** 將其輸出產生為 XML 檔，以便重新導向至檔案。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-356">The following example shows how to request that **ssbdiagnose** generate its output as an XML file that is redirected to a file.</span></span> <span data-ttu-id="c3dfb-357">然後，應用程式可以開啟 TestDiag.xml 檔，以便分析或報告 **ssbdiagnose** XML 檔。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-357">The TestDiag.xml file can then be opened by an application to analyze or report **ssbdiagnose** XML files.</span></span> <span data-ttu-id="c3dfb-358">或者，您可以從一般 XML 編輯器 (例如 XML Notepad) 中檢視此檔案。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-358">Or, you can view it from a general XML editor such as XML Notepad.</span></span>  
  
```  
ssbdiagnose -XML -E -d MyDatabase CONFIGURATION FROM SERVICE   
/test/initiator TO SERVICE /test/target > c:\MyDiagnostics\TestDiag.xml  
```  
  
### <a name="m-using-an-environment-variable"></a><span data-ttu-id="c3dfb-359">M.</span><span class="sxs-lookup"><span data-stu-id="c3dfb-359">M.</span></span> <span data-ttu-id="c3dfb-360">使用環境變數</span><span class="sxs-lookup"><span data-stu-id="c3dfb-360">Using an Environment Variable</span></span>  
 <span data-ttu-id="c3dfb-361">下列範例會先設定 SQLCMDSERVER 環境變數，以便保存伺服器名稱，然後在不指定 **-S** 的情況下執行 **ssbdiagnose**。</span><span class="sxs-lookup"><span data-stu-id="c3dfb-361">The following example first sets the SQLCMDSERVER environment variable to hold the server name, and then runs **ssbdiagnose** without specifying **-S**.</span></span>  
  
```  
SET SQLCMDSERVER=MyComputer  
ssbdiagnose -XML -E -d MyDatabase CONFIGURATION FROM SERVICE   
/test/initiator TO SERVICE /test/target  
```  
  
## <a name="see-also"></a><span data-ttu-id="c3dfb-362">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c3dfb-362">See Also</span></span>  
 <span data-ttu-id="c3dfb-363">[SQL Server Service Broker](../../database-engine/configure-windows/sql-server-service-broker.md) </span><span class="sxs-lookup"><span data-stu-id="c3dfb-363">[SQL Server Service Broker](../../database-engine/configure-windows/sql-server-service-broker.md) </span></span>  
 <span data-ttu-id="c3dfb-364">[BEGIN DIALOG CONVERSATION &#40;Transact-SQL&#41;](/sql/t-sql/statements/begin-dialog-conversation-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c3dfb-364">[BEGIN DIALOG CONVERSATION &#40;Transact-SQL&#41;](/sql/t-sql/statements/begin-dialog-conversation-transact-sql) </span></span>  
 <span data-ttu-id="c3dfb-365">[CREATE BROKER PRIORITY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-broker-priority-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c3dfb-365">[CREATE BROKER PRIORITY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-broker-priority-transact-sql) </span></span>  
 <span data-ttu-id="c3dfb-366">[CREATE CERTIFICATE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-certificate-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c3dfb-366">[CREATE CERTIFICATE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-certificate-transact-sql) </span></span>  
 <span data-ttu-id="c3dfb-367">[CREATE CONTRACT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-contract-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c3dfb-367">[CREATE CONTRACT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-contract-transact-sql) </span></span>  
 <span data-ttu-id="c3dfb-368">[CREATE ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-endpoint-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c3dfb-368">[CREATE ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-endpoint-transact-sql) </span></span>  
 <span data-ttu-id="c3dfb-369">[CREATE MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-master-key-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c3dfb-369">[CREATE MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-master-key-transact-sql) </span></span>  
 <span data-ttu-id="c3dfb-370">[CREATE MESSAGE TYPE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-message-type-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c3dfb-370">[CREATE MESSAGE TYPE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-message-type-transact-sql) </span></span>  
 <span data-ttu-id="c3dfb-371">[CREATE QUEUE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-queue-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c3dfb-371">[CREATE QUEUE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-queue-transact-sql) </span></span>  
 <span data-ttu-id="c3dfb-372">[CREATE REMOTE SERVICE BINDING &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-remote-service-binding-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c3dfb-372">[CREATE REMOTE SERVICE BINDING &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-remote-service-binding-transact-sql) </span></span>  
 <span data-ttu-id="c3dfb-373">[CREATE ROUTE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-route-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c3dfb-373">[CREATE ROUTE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-route-transact-sql) </span></span>  
 <span data-ttu-id="c3dfb-374">[CREATE SERVICE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-service-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c3dfb-374">[CREATE SERVICE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-service-transact-sql) </span></span>  
 <span data-ttu-id="c3dfb-375">[RECEIVE &#40;Transact-SQL&#41;](/sql/t-sql/statements/receive-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c3dfb-375">[RECEIVE &#40;Transact-SQL&#41;](/sql/t-sql/statements/receive-transact-sql) </span></span>  
 <span data-ttu-id="c3dfb-376">[sys.transmission_queue &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-transmission-queue-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c3dfb-376">[sys.transmission_queue &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-transmission-queue-transact-sql) </span></span>  
 <span data-ttu-id="c3dfb-377">[sys.conversation_endpoints &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-conversation-endpoints-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c3dfb-377">[sys.conversation_endpoints &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-conversation-endpoints-transact-sql) </span></span>  
 [<span data-ttu-id="c3dfb-378">sys.conversation_groups &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="c3dfb-378">sys.conversation_groups &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-conversation-groups-transact-sql)  
  
  
