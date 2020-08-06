---
title: 疑難排解工具套件連接 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Integration Services packages, troubleshooting
- SSIS packages, troubleshooting
- Integration Services, troubleshooting
- connectivity [Integration Services], troubleshooting
- errors [Integration Services], troubleshooting
- packages [Integration Services], troubleshooting
ms.assetid: 08a019f5-8ba7-4527-97c1-e9846d4022ff
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1baac9af5a30fdc0f5b15e8ac56eb5badacc0edb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700000"
---
# <a name="troubleshooting-tools-package-connectivity"></a><span data-ttu-id="56702-102">疑難排解工具封裝連接</span><span class="sxs-lookup"><span data-stu-id="56702-102">Troubleshooting Tools Package Connectivity</span></span>
  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="56702-103">所含的功能及工具，可以讓您用於疑難排解封裝與封裝擷取及載入資料之資料來源之間的連接。</span><span class="sxs-lookup"><span data-stu-id="56702-103">includes features and tools that you can use to troubleshoot connectivity between packages and the data sources from which packages extract and load data.</span></span>  
  
## <a name="troubleshooting-issues-with-external-data-providers"></a><span data-ttu-id="56702-104">疑難排解外部資料提供者的問題</span><span class="sxs-lookup"><span data-stu-id="56702-104">Troubleshooting Issues with External Data Providers</span></span>  
 <span data-ttu-id="56702-105">與外部資料提供者互動期間發生許多封裝失敗。</span><span class="sxs-lookup"><span data-stu-id="56702-105">Many packages fail during interactions with external data providers.</span></span> <span data-ttu-id="56702-106">但是，這些提供者傳回 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 的訊息經常未提供足夠的資訊，導致無法開始進行互動的疑難排解。</span><span class="sxs-lookup"><span data-stu-id="56702-106">However, the messages that those providers return to [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] frequently do not provide enough information to start troubleshooting the interaction.</span></span> <span data-ttu-id="56702-107">為了解決這個疑難排解需要， [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包括新的記錄訊息，可供您用於針對封裝與外部資料來源之間的互動進行疑難排解。</span><span class="sxs-lookup"><span data-stu-id="56702-107">To address this troubleshooting need, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] includes logging messages that you can use to troubleshoot a package's interaction with external data sources.</span></span>  
  
-   <span data-ttu-id="56702-108">**啟用記錄並選取封裝的 [診斷] 事件以查看新的疑難排解訊息**。</span><span class="sxs-lookup"><span data-stu-id="56702-108">**Enable logging and select the package's Diagnostic event to see the troubleshooting messages**.</span></span> <span data-ttu-id="56702-109">下列 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 元件將能夠在每次呼叫外部資料提供者之前和之後，於記錄中寫入訊息：</span><span class="sxs-lookup"><span data-stu-id="56702-109">The following [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] components are capable of writing a message to the log before and after every call to an external data provider:</span></span>  
  
    -   <span data-ttu-id="56702-110">OLE DB 連接管理員、OLE DB 來源和 OLE DB 目的地</span><span class="sxs-lookup"><span data-stu-id="56702-110">OLE DB connection manager, OLE DB source, and OLE DB destination</span></span>  
  
    -   [!INCLUDE[vstecado](../../includes/vstecado-md.md)] <span data-ttu-id="56702-111">連線管理員和 ADO NET 來源</span><span class="sxs-lookup"><span data-stu-id="56702-111">connection manager and ADO NET source</span></span>  
  
    -   <span data-ttu-id="56702-112">執行 SQL 工作</span><span class="sxs-lookup"><span data-stu-id="56702-112">Execute SQL task</span></span>  
  
    -   <span data-ttu-id="56702-113">查閱轉換、OLE DB 命令轉換和緩時變維度轉換</span><span class="sxs-lookup"><span data-stu-id="56702-113">Lookup transformation, OLE DB Command transformation, and Slowly Changing Dimension transformation</span></span>  
  
     <span data-ttu-id="56702-114">記錄訊息包括所呼叫方法的名稱。</span><span class="sxs-lookup"><span data-stu-id="56702-114">The log messages include the name of the method being called.</span></span> <span data-ttu-id="56702-115">例如，這些記錄訊息可能包括 OLE DB `Open` 物件的 `Connection` 方法，或 `ExecuteNonQuery` 物件的 `Command` 方法。</span><span class="sxs-lookup"><span data-stu-id="56702-115">For example, these log messages might include the `Open` method of an OLE DB `Connection` object or the `ExecuteNonQuery` method of a `Command` object.</span></span> <span data-ttu-id="56702-116">訊息的格式如下，其中 '%1!s!'</span><span class="sxs-lookup"><span data-stu-id="56702-116">The messages have the following format, where '%1!s!'</span></span> <span data-ttu-id="56702-117">是方法資訊的預留位置：</span><span class="sxs-lookup"><span data-stu-id="56702-117">is a placeholder for the method information:</span></span>  
  
    ```  
    ExternalRequest_pre: The object is ready to make the following external request: '%1!s!'.  
    ExternalRequest_post: '%1!s!'. The external request has completed.  
    ```  
  
     <span data-ttu-id="56702-118">若要疑難排解與外部資料提供者之間的互動，請檢閱記錄，查看是不是每個「呼叫前」訊息 (`ExternalRequest_pre`) 都有一個對應的「呼叫後」訊息 (`ExternalRequest_post`)。</span><span class="sxs-lookup"><span data-stu-id="56702-118">To troubleshoot the interaction with the external data provider, review the log to see whether every "before" message (`ExternalRequest_pre`) has a corresponding "after" message (`ExternalRequest_post`).</span></span> <span data-ttu-id="56702-119">如果沒有對應的「呼叫後」訊息，您就知道外部資料提供者並未如預期方式回應。</span><span class="sxs-lookup"><span data-stu-id="56702-119">If there is no corresponding "after" message, you know that the external data provider did not respond as expected.</span></span>  
  
     <span data-ttu-id="56702-120">下列範例顯示記錄中的一些範例資料列，其中包含這些記錄訊息：</span><span class="sxs-lookup"><span data-stu-id="56702-120">The following example shows some sample rows from a log that contains these logging messages:</span></span>  
  
    ```  
    ExternalRequest_pre: The object is ready to make the following external request: 'ITransactionJoin::JoinTransaction'.  
    ExternalRequest_post: 'ITransactionJoin::JoinTransaction succeeded'. The external request has completed.  
    ExternalRequest_pre: The object is ready to make the following external request: 'IDbConnection.Open'.  
    ExternalRequest_post: 'IDbConnection.Open succeeded'. The external request has completed.  
    ExternalRequest_pre: The object is ready to make the following external request: 'IDbConnection.CreateCommand'.  
    ExternalRequest_post: 'IDbConnection.CreateCommand finished'. The external request has completed."  
    ExternalRequest_pre: The object is ready to make the following external request: 'IDbCommand.ExecuteReader'.  
    ExternalRequest_post: 'IDbCommand.ExecuteReader finished'. The external request has completed."  
    ExternalRequest_pre: The object is ready to make the following external request: 'IDataReader.GetSchemaTable'.  
    ExternalRequest_post: 'IDataReader.GetSchemaTable finished'. The external request has completed."  
    ExternalRequest_pre: The object is ready to make the following external request: 'IDataReader.Close'.  
    ExternalRequest_post: 'IDataReader.Close finished'. The external request has completed."  
    ExternalRequest_pre: The object is ready to make the following external request: 'IDbConnection.Close'.  
    ExternalRequest_post: 'IDbConnection.Close finished'. The external request has completed."  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="56702-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="56702-121">See Also</span></span>  
 <span data-ttu-id="56702-122">[疑難排解封裝開發的工具](troubleshooting-tools-for-package-development.md) </span><span class="sxs-lookup"><span data-stu-id="56702-122">[Troubleshooting Tools for Package Development](troubleshooting-tools-for-package-development.md) </span></span>  
 [<span data-ttu-id="56702-123">套件執行的疑難排解工具</span><span class="sxs-lookup"><span data-stu-id="56702-123">Troubleshooting Tools for Package Execution</span></span>](troubleshooting-tools-for-package-execution.md)  
  
  
