---
title: SqlErrorLogEvent 類別 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
helpviewer_keywords:
- SqlErrorLogEvent class
- SqlErrorLogFile class
ms.assetid: bde6c467-38d0-4766-a7af-d6c9d6302b07
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 358b6906e422be2984f2ebdbde636ad0b8376993
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594962"
---
# <a name="sqlerrorlogevent-class"></a><span data-ttu-id="0abbc-102">SqlErrorLogEvent 類別</span><span class="sxs-lookup"><span data-stu-id="0abbc-102">SqlErrorLogEvent Class</span></span>
  <span data-ttu-id="0abbc-103">提供屬性，用來檢視指定之 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 記錄檔中的事件。</span><span class="sxs-lookup"><span data-stu-id="0abbc-103">Provides properties for viewing events in a specified [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] log file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0abbc-104">語法</span><span class="sxs-lookup"><span data-stu-id="0abbc-104">Syntax</span></span>  
  
```  
  
class SQLErrorLogEvent   
{  
   stringFileName;  
   stringInstanceName;  
   datetimeLogDate;  
   stringMessage;  
   stringProcessInfo;  
};  
```  
  
## <a name="properties"></a><span data-ttu-id="0abbc-105">屬性</span><span class="sxs-lookup"><span data-stu-id="0abbc-105">Properties</span></span>  
 <span data-ttu-id="0abbc-106">SQLErrorLogEvent 類別會定義下列屬性。</span><span class="sxs-lookup"><span data-stu-id="0abbc-106">The SQLErrorLogEvent class defines the following properties.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0abbc-107">FileName</span><span class="sxs-lookup"><span data-stu-id="0abbc-107">FileName</span></span>|<span data-ttu-id="0abbc-108">資料類型：`string`</span><span class="sxs-lookup"><span data-stu-id="0abbc-108">Data type: `string`</span></span><br /><br /> <span data-ttu-id="0abbc-109">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="0abbc-109">Access type: Read-only</span></span><br /><br /> <br /><br /> <span data-ttu-id="0abbc-110">錯誤記錄檔的名稱。</span><span class="sxs-lookup"><span data-stu-id="0abbc-110">The name of the error log file.</span></span>|  
|<span data-ttu-id="0abbc-111">InstanceName</span><span class="sxs-lookup"><span data-stu-id="0abbc-111">InstanceName</span></span>|<span data-ttu-id="0abbc-112">資料類型：`string`</span><span class="sxs-lookup"><span data-stu-id="0abbc-112">Data type: `string`</span></span><br /><br /> <span data-ttu-id="0abbc-113">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="0abbc-113">Access type: Read-only</span></span><br /><br /> <span data-ttu-id="0abbc-114">限定詞：索引鍵</span><span class="sxs-lookup"><span data-stu-id="0abbc-114">Qualifiers: Key</span></span><br /><br /> <span data-ttu-id="0abbc-115">記錄檔所在的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="0abbc-115">The name of the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] where the log file resides.</span></span>|  
|<span data-ttu-id="0abbc-116">LogDate</span><span class="sxs-lookup"><span data-stu-id="0abbc-116">LogDate</span></span>|<span data-ttu-id="0abbc-117">資料類型：`datetime`</span><span class="sxs-lookup"><span data-stu-id="0abbc-117">Data type: `datetime`</span></span><br /><br /> <span data-ttu-id="0abbc-118">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="0abbc-118">Access type: Read-only</span></span><br /><br /> <span data-ttu-id="0abbc-119">限定詞：索引鍵</span><span class="sxs-lookup"><span data-stu-id="0abbc-119">Qualifiers: Key</span></span><br /><br /> <br /><br /> <span data-ttu-id="0abbc-120">將事件記錄到記錄檔中的日期和時間。</span><span class="sxs-lookup"><span data-stu-id="0abbc-120">The date and time that the event was recorded in the log file.</span></span>|  
|<span data-ttu-id="0abbc-121">訊息</span><span class="sxs-lookup"><span data-stu-id="0abbc-121">Message</span></span>|<span data-ttu-id="0abbc-122">資料類型：`string`</span><span class="sxs-lookup"><span data-stu-id="0abbc-122">Data type: `string`</span></span><br /><br /> <span data-ttu-id="0abbc-123">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="0abbc-123">Access type: Read-only</span></span><br /><br /> <br /><br /> <span data-ttu-id="0abbc-124">事件訊息。</span><span class="sxs-lookup"><span data-stu-id="0abbc-124">The event message.</span></span>|  
|<span data-ttu-id="0abbc-125">ProcessInfo</span><span class="sxs-lookup"><span data-stu-id="0abbc-125">ProcessInfo</span></span>|<span data-ttu-id="0abbc-126">資料類型：`string`</span><span class="sxs-lookup"><span data-stu-id="0abbc-126">Data type: `string`</span></span><br /><br /> <span data-ttu-id="0abbc-127">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="0abbc-127">Access type: Read-only</span></span><br /><br /> <br /><br /> <span data-ttu-id="0abbc-128">事件之來源伺服器處理序識別碼 (SPID) 的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="0abbc-128">Information about the source server process ID (SPID) for the event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0abbc-129">備註</span><span class="sxs-lookup"><span data-stu-id="0abbc-129">Remarks</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0abbc-130">MOF</span><span class="sxs-lookup"><span data-stu-id="0abbc-130">MOF</span></span>|<span data-ttu-id="0abbc-131">Sqlmgmproviderxpsp2up.mof</span><span class="sxs-lookup"><span data-stu-id="0abbc-131">Sqlmgmproviderxpsp2up.mof</span></span>|  
|<span data-ttu-id="0abbc-132">DLL</span><span class="sxs-lookup"><span data-stu-id="0abbc-132">DLL</span></span>|<span data-ttu-id="0abbc-133">Sqlmgmprovider.dll</span><span class="sxs-lookup"><span data-stu-id="0abbc-133">Sqlmgmprovider.dll</span></span>|  
|<span data-ttu-id="0abbc-134">命名空間</span><span class="sxs-lookup"><span data-stu-id="0abbc-134">Namespace</span></span>|<span data-ttu-id="0abbc-135">\root\Microsoft\SqlServer\ComputerManagement10</span><span class="sxs-lookup"><span data-stu-id="0abbc-135">\root\Microsoft\SqlServer\ComputerManagement10</span></span>|  
  
## <a name="example"></a><span data-ttu-id="0abbc-136">範例</span><span class="sxs-lookup"><span data-stu-id="0abbc-136">Example</span></span>  
 <span data-ttu-id="0abbc-137">下列範例會顯示如何擷取指定的記錄檔中所有已記錄事件的值。</span><span class="sxs-lookup"><span data-stu-id="0abbc-137">The following example shows how to retrieve values for all logged events in a specified log file.</span></span> <span data-ttu-id="0abbc-138">若要執行範例，請將取代為 \<*Instance_Name*> 實例的名稱 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，例如 ' Instance1 '，並以錯誤記錄檔的名稱取代 ' File_Name '，例如 ' 錯誤記錄檔 1 '。</span><span class="sxs-lookup"><span data-stu-id="0abbc-138">To run the example, replace \<*Instance_Name*> with the name of the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], such as 'Instance1', and replace 'File_Name' with the name of the error log file, such as 'ERRORLOG.1'.</span></span>  
  
```  
on error resume next  
strComputer = "."  
Set objWMIService = GetObject("winmgmts:" _  
    & "{impersonationLevel=impersonate}!\\" _  
    & strComputer & "\root\MICROSOFT\SqlServer\ComputerManagement10")  
set logEvents = objWmiService.ExecQuery("SELECT * FROM SqlErrorLogEvent WHERE InstanceName = '<Instance_Name>' AND FileName = 'File_Name'")  
  
For Each logEvent in logEvents  
WScript.Echo "Instance Name: " & logEvent.InstanceName & vbNewLine _  
    & "Log Date: " & logEvent.LogDate & vbNewLine _  
    & "Log File Name: " & logEvent.FileName & vbNewLine _  
    & "Process Info: " & logEvent.ProcessInfo & vbNewLine _  
    & "Message: " & logEvent.Message & vbNewLine _  
  
Next  
```  
  
## <a name="comments"></a><span data-ttu-id="0abbc-139">註解</span><span class="sxs-lookup"><span data-stu-id="0abbc-139">Comments</span></span>  
 <span data-ttu-id="0abbc-140">當 WQL 語句中未提供*InstanceName*或*FileName*時，查詢將會傳回預設實例和目前記錄檔的資訊 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="0abbc-140">When *InstanceName* or *FileName* are not provided in the WQL statement, the query will return information for the default instance and the current [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] log file.</span></span> <span data-ttu-id="0abbc-141">例如，下列 WQL 陳述式將傳回來自預設執行個體 (MSSQLSERVER) 上之目前記錄檔 (ERRORLOG) 的所有記錄事件。</span><span class="sxs-lookup"><span data-stu-id="0abbc-141">For example, the following WQL statement will return all log events from the current log file (ERRORLOG) on the default instance (MSSQLSERVER).</span></span>  
  
```  
"SELECT * FROM SqlErrorLogEvent"  
```  
  
## <a name="security"></a><span data-ttu-id="0abbc-142">安全性</span><span class="sxs-lookup"><span data-stu-id="0abbc-142">Security</span></span>  
 <span data-ttu-id="0abbc-143">若要 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 透過 WMI 連接到記錄檔，您必須在本機和遠端電腦上都有下列許可權：</span><span class="sxs-lookup"><span data-stu-id="0abbc-143">To connect to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] log file through WMI, you must have the following permissions on both the local and remote computers:</span></span>  
  
-   <span data-ttu-id="0abbc-144">**Root\Microsoft\SqlServer\ComputerManagement10** WMI 命名空間的讀取權限。</span><span class="sxs-lookup"><span data-stu-id="0abbc-144">Read access to the **Root\Microsoft\SqlServer\ComputerManagement10** WMI namespace.</span></span> <span data-ttu-id="0abbc-145">根據預設，每個人都可從啟用帳戶權限取得讀取權限。</span><span class="sxs-lookup"><span data-stu-id="0abbc-145">By default, everyone has read access through the Enable Account permission.</span></span>  
  
-   <span data-ttu-id="0abbc-146">包含錯誤記錄檔之資料夾的讀取權限。</span><span class="sxs-lookup"><span data-stu-id="0abbc-146">Read permission to the folder that contains the error logs.</span></span> <span data-ttu-id="0abbc-147">根據預設，錯誤記錄檔位於下列路徑 (其中 \<*Drive> \* 代表您安裝的磁片磁碟機 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，而 \<*InstanceName*> 是) 實例的名稱 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ：</span><span class="sxs-lookup"><span data-stu-id="0abbc-147">By default the error logs are located in the following path (where \<*Drive>\* represents the drive where you installed [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and \<*InstanceName*> is the name of the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]):</span></span>  
  
     <span data-ttu-id="0abbc-148">\*\* \<Drive> ： \PROGRAM Files\Microsoft SQL Server\MSSQL12\*\* **。 \<InstanceName>\MSSQL\Log**</span><span class="sxs-lookup"><span data-stu-id="0abbc-148">**\<Drive>:\Program Files\Microsoft SQL Server\MSSQL12** **.\<InstanceName>\MSSQL\Log**</span></span>  
  
 <span data-ttu-id="0abbc-149">如果透過防火牆連接，請確定您已在遠端目標電腦上的 WMI 防火牆中設定例外狀況。</span><span class="sxs-lookup"><span data-stu-id="0abbc-149">If you are connecting through a firewall, ensure that an exception is set in the firewall for WMI on remote target computers.</span></span> <span data-ttu-id="0abbc-150">如需詳細資訊，請參閱[從 Windows Vista 開始遠端連線到 WMI](https://go.microsoft.com/fwlink/?LinkId=178848)。</span><span class="sxs-lookup"><span data-stu-id="0abbc-150">For more information, see [Connecting to WMI Remotely Starting with Windows Vista](https://go.microsoft.com/fwlink/?LinkId=178848).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0abbc-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0abbc-151">See Also</span></span>  
 <span data-ttu-id="0abbc-152">[SqlErrorLogFile 類別](sqlerrorlogfile-class.md) </span><span class="sxs-lookup"><span data-stu-id="0abbc-152">[SqlErrorLogFile Class](sqlerrorlogfile-class.md) </span></span>  
 [<span data-ttu-id="0abbc-153">檢視離線記錄檔</span><span class="sxs-lookup"><span data-stu-id="0abbc-153">View Offline Log Files</span></span>](../logs/view-offline-log-files.md)  
  
  
