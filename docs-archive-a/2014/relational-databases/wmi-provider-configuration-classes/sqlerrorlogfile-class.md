---
title: SqlErrorLogFile 類別 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
ms.assetid: 2b83ae4a-c0d4-414c-b6e5-a41ec7c13159
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: d73f97ebddd7a1d18c73a2cbce7fe79dafc17a77
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687621"
---
# <a name="sqlerrorlogfile-class"></a><span data-ttu-id="67639-102">SqlErrorLogFile 類別</span><span class="sxs-lookup"><span data-stu-id="67639-102">SqlErrorLogFile Class</span></span>
  <span data-ttu-id="67639-103">提供屬性，用來檢視 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 記錄檔的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="67639-103">Provides properties for viewing information about a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] log file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67639-104">語法</span><span class="sxs-lookup"><span data-stu-id="67639-104">Syntax</span></span>  
  
```  
  
class SQLErrorLogFile  
{  
   uint32ArchiveNumber;  
   stringInstanceName;  
   datetimeLastModified;  
   uint32LogFileSize;  
   stringName;  
  
};  
```  
  
## <a name="properties"></a><span data-ttu-id="67639-105">屬性</span><span class="sxs-lookup"><span data-stu-id="67639-105">Properties</span></span>  
 <span data-ttu-id="67639-106">SQLErrorLogFile 類別會定義下列屬性。</span><span class="sxs-lookup"><span data-stu-id="67639-106">The SQLErrorLogFile class defines the following properties.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="67639-107">ArchiveNumber</span><span class="sxs-lookup"><span data-stu-id="67639-107">ArchiveNumber</span></span>|<span data-ttu-id="67639-108">資料類型：`uint32`</span><span class="sxs-lookup"><span data-stu-id="67639-108">Data type: `uint32`</span></span><br /><br /> <span data-ttu-id="67639-109">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="67639-109">Access type: Read-only</span></span><br /><br /> <br /><br /> <span data-ttu-id="67639-110">記錄檔的封存數目。</span><span class="sxs-lookup"><span data-stu-id="67639-110">The archive number for the log file.</span></span>|  
|<span data-ttu-id="67639-111">InstanceName</span><span class="sxs-lookup"><span data-stu-id="67639-111">InstanceName</span></span>|<span data-ttu-id="67639-112">資料類型：`string`</span><span class="sxs-lookup"><span data-stu-id="67639-112">Data type: `string`</span></span><br /><br /> <span data-ttu-id="67639-113">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="67639-113">Access type: Read-only</span></span><br /><br /> <span data-ttu-id="67639-114">限定詞：索引鍵</span><span class="sxs-lookup"><span data-stu-id="67639-114">Qualifiers: Key</span></span><br /><br /> <br /><br /> <span data-ttu-id="67639-115">記錄檔所在的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="67639-115">The name of the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] where the log file resides.</span></span>|  
|<span data-ttu-id="67639-116">LastModified</span><span class="sxs-lookup"><span data-stu-id="67639-116">LastModified</span></span>|<span data-ttu-id="67639-117">資料類型：`datetime`</span><span class="sxs-lookup"><span data-stu-id="67639-117">Data type: `datetime`</span></span><br /><br /> <span data-ttu-id="67639-118">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="67639-118">Access type: Read-only</span></span><br /><br /> <br /><br /> <span data-ttu-id="67639-119">上次修改記錄檔的日期。</span><span class="sxs-lookup"><span data-stu-id="67639-119">The date that the log file was last modified.</span></span>|  
|<span data-ttu-id="67639-120">LogFileSize</span><span class="sxs-lookup"><span data-stu-id="67639-120">LogFileSize</span></span>|<span data-ttu-id="67639-121">資料類型：`uint32`</span><span class="sxs-lookup"><span data-stu-id="67639-121">Data type: `uint32`</span></span><br /><br /> <span data-ttu-id="67639-122">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="67639-122">Access type: Read-only</span></span><br /><br /> <br /><br /> <span data-ttu-id="67639-123">記錄檔的大小 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="67639-123">The log file size, in bytes.</span></span>|  
|<span data-ttu-id="67639-124">名稱</span><span class="sxs-lookup"><span data-stu-id="67639-124">Name</span></span>|<span data-ttu-id="67639-125">資料類型：`string`</span><span class="sxs-lookup"><span data-stu-id="67639-125">Data type: `string`</span></span><br /><br /> <span data-ttu-id="67639-126">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="67639-126">Access type: Read-only</span></span><br /><br /> <span data-ttu-id="67639-127">限定詞：索引鍵</span><span class="sxs-lookup"><span data-stu-id="67639-127">Qualifiers: Key</span></span><br /><br /> <br /><br /> <span data-ttu-id="67639-128">記錄檔的名稱。</span><span class="sxs-lookup"><span data-stu-id="67639-128">The name of the log file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="67639-129">備註</span><span class="sxs-lookup"><span data-stu-id="67639-129">Remarks</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="67639-130">MOF</span><span class="sxs-lookup"><span data-stu-id="67639-130">MOF</span></span>|<span data-ttu-id="67639-131">Sqlmgmprovider xpsp2up.mof</span><span class="sxs-lookup"><span data-stu-id="67639-131">Sqlmgmprovider xpsp2up.mof</span></span>|  
|<span data-ttu-id="67639-132">DLL</span><span class="sxs-lookup"><span data-stu-id="67639-132">DLL</span></span>|<span data-ttu-id="67639-133">Sqlmgmprovider.dll</span><span class="sxs-lookup"><span data-stu-id="67639-133">Sqlmgmprovider.dll</span></span>|  
|<span data-ttu-id="67639-134">命名空間</span><span class="sxs-lookup"><span data-stu-id="67639-134">Namespace</span></span>|<span data-ttu-id="67639-135">\root\Microsoft\SqlServer\ComputerManagement10</span><span class="sxs-lookup"><span data-stu-id="67639-135">\root\Microsoft\SqlServer\ComputerManagement10</span></span>|  
  
## <a name="example"></a><span data-ttu-id="67639-136">範例</span><span class="sxs-lookup"><span data-stu-id="67639-136">Example</span></span>  
 <span data-ttu-id="67639-137">下列範例會抓取 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 指定之實例上所有記錄檔的相關資訊 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="67639-137">The following example retrieves information about all [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] log files on a specified instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="67639-138">若要執行範例，請將取代 \<*Instance_Name*> 為實例的名稱，例如 ' Instance1 '。</span><span class="sxs-lookup"><span data-stu-id="67639-138">To run the example, replace \<*Instance_Name*> with the name of the instance, for example, 'Instance1'.</span></span>  
  
```  
on error resume next  
set strComputer = "."  
set objWMIService = GetObject("winmgmts:\\.\root\Microsoft\SqlServer\ComputerManagement10")  
set LogFiles = objWmiService.ExecQuery("SELECT * FROM SqlErrorLogFile WHERE InstanceName = '<Instance_Name>'")  
  
For Each logFile in LogFiles  
  
WScript.Echo "Instance Name:  " & logFile.InstanceName & vbNewLine _  
    & "Log File Name:  " & logFile.Name & vbNewLine _  
    & "Archive Number: " & logFile.ArchiveNumber & vbNewLine _  
    & "Log File Size:  " & logFile.LogFileSize & " bytes" & vbNewLine _  
    & "Last Modified:  " & logFile.LastModified & vbNewLine _  
  
Next   
```  
  
## <a name="comments"></a><span data-ttu-id="67639-139">註解</span><span class="sxs-lookup"><span data-stu-id="67639-139">Comments</span></span>  
 <span data-ttu-id="67639-140">當 WQL 語句中未提供*InstanceName*時，查詢將會傳回預設實例的資訊。</span><span class="sxs-lookup"><span data-stu-id="67639-140">When *InstanceName* is not provided in the WQL statement, the query will return information for the default instance.</span></span> <span data-ttu-id="67639-141">例如，下列 WQL 陳述式將傳回來自預設執行個體 (MSSQLSERVER) 的所有記錄檔相關資訊。</span><span class="sxs-lookup"><span data-stu-id="67639-141">For example, the following WQL statement will return information about all log files from the default instance (MSSQLSERVER).</span></span>  
  
```  
"SELECT * FROM SqlErrorLogFile"  
```  
  
## <a name="security"></a><span data-ttu-id="67639-142">安全性</span><span class="sxs-lookup"><span data-stu-id="67639-142">Security</span></span>  
 <span data-ttu-id="67639-143">若要 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 透過 WMI 連接到記錄檔，您必須在本機和遠端電腦上都有下列許可權：</span><span class="sxs-lookup"><span data-stu-id="67639-143">To connect to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] log file through WMI, you must have the following permissions on both the local and remote computers:</span></span>  
  
-   <span data-ttu-id="67639-144">**Root\Microsoft\SqlServer\ComputerManagement10** WMI 命名空間的讀取權限。</span><span class="sxs-lookup"><span data-stu-id="67639-144">Read access to the **Root\Microsoft\SqlServer\ComputerManagement10** WMI namespace.</span></span> <span data-ttu-id="67639-145">根據預設，每個人都可從啟用帳戶權限取得讀取權限。</span><span class="sxs-lookup"><span data-stu-id="67639-145">By default, everyone has read access through the Enable Account permission.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="67639-146">如需有關如何驗證 WMI 許可權的詳細資訊，請參閱主題 [[離線記錄](../logs/view-offline-log-files.md)檔] 中的 [安全性] 區段。</span><span class="sxs-lookup"><span data-stu-id="67639-146">For information about how to verify WMI permissions, see the Security section of the topic [View Offline Log Files](../logs/view-offline-log-files.md).</span></span>  
  
-   <span data-ttu-id="67639-147">包含錯誤記錄檔之資料夾的讀取權限。</span><span class="sxs-lookup"><span data-stu-id="67639-147">Read permission to the folder that contains the error logs.</span></span> <span data-ttu-id="67639-148">根據預設，錯誤記錄檔位於下列路徑 (其中 \<*Drive> \* 代表您安裝的磁片磁碟機 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，而 \<*InstanceName*> 是) 實例的名稱 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ：</span><span class="sxs-lookup"><span data-stu-id="67639-148">By default the error logs are located in the following path (where \<*Drive>\* represents the drive where you installed [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and \<*InstanceName*> is the name of the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]):</span></span>  
  
     <span data-ttu-id="67639-149">\*\* \<Drive> ： \PROGRAM Files\Microsoft SQL Server\MSSQL11\*\* **。 \<InstanceName>\MSSQL\Log**</span><span class="sxs-lookup"><span data-stu-id="67639-149">**\<Drive>:\Program Files\Microsoft SQL Server\MSSQL11** **.\<InstanceName>\MSSQL\Log**</span></span>  
  
 <span data-ttu-id="67639-150">如果透過防火牆連接，請確定您已在遠端目標電腦上的 WMI 防火牆中設定例外狀況。</span><span class="sxs-lookup"><span data-stu-id="67639-150">If you are connecting through a firewall, ensure that an exception is set in the firewall for WMI on remote target computers.</span></span> <span data-ttu-id="67639-151">如需詳細資訊，請參閱[從 Windows Vista 開始遠端連線到 WMI](https://go.microsoft.com/fwlink/?LinkId=178848)。</span><span class="sxs-lookup"><span data-stu-id="67639-151">For more information, see [Connecting to WMI Remotely Starting with Windows Vista](https://go.microsoft.com/fwlink/?LinkId=178848).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67639-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="67639-152">See Also</span></span>  
 <span data-ttu-id="67639-153">[SqlErrorLogEvent 類別](sqlerrorlogevent-class.md) </span><span class="sxs-lookup"><span data-stu-id="67639-153">[SqlErrorLogEvent Class](sqlerrorlogevent-class.md) </span></span>  
 [<span data-ttu-id="67639-154">檢視離線記錄檔</span><span class="sxs-lookup"><span data-stu-id="67639-154">View Offline Log Files</span></span>](../logs/view-offline-log-files.md)  
  
  
