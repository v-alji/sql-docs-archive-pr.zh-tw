---
title: 以程式設計的方式啟用記錄 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SQL Server Integration Services packages, logs
- SSIS packages, logs
- Integration Services packages, logs
- SSIS logging
- log providers [Integration Services]
- logs [Integration Services], enabling
- LoggingMode property
- LogProvider object
- packages [Integration Services], logs
ms.assetid: 3222a1ed-83eb-421c-b299-a53b67bba740
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ff7f81aca330960e4e94b0343080a37ded8c1273
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700153"
---
# <a name="enabling-logging-programmatically"></a><span data-ttu-id="1c9cc-102">以程式設計的方式啟用記錄</span><span class="sxs-lookup"><span data-stu-id="1c9cc-102">Enabling Logging Programmatically</span></span>
  <span data-ttu-id="1c9cc-103">執行階段引擎提供 <xref:Microsoft.SqlServer.Dts.Runtime.LogProvider> 物件的集合，允許在封裝驗證和執行期間擷取事件特定資訊。</span><span class="sxs-lookup"><span data-stu-id="1c9cc-103">The run-time engine provides a collection of <xref:Microsoft.SqlServer.Dts.Runtime.LogProvider> objects that enable event-specific information to be captured during package validation and execution.</span></span> <span data-ttu-id="1c9cc-104"><xref:Microsoft.SqlServer.Dts.Runtime.LogProvider> 物件可供 <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer> 物件使用，包括 <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost>、<xref:Microsoft.SqlServer.Dts.Runtime.Package>、<xref:Microsoft.SqlServer.Dts.Runtime.ForLoop> 和 <xref:Microsoft.SqlServer.Dts.Runtime.ForEachLoop> 物件。</span><span class="sxs-lookup"><span data-stu-id="1c9cc-104"><xref:Microsoft.SqlServer.Dts.Runtime.LogProvider> objects are available to <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer> objects, including the <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost>, <xref:Microsoft.SqlServer.Dts.Runtime.Package>, <xref:Microsoft.SqlServer.Dts.Runtime.ForLoop>, and <xref:Microsoft.SqlServer.Dts.Runtime.ForEachLoop> objects.</span></span> <span data-ttu-id="1c9cc-105">在個別容器或是整個封裝上啟用記錄。</span><span class="sxs-lookup"><span data-stu-id="1c9cc-105">Logging is enabled on individual containers, or on the whole package.</span></span>

 <span data-ttu-id="1c9cc-106">有好幾種類型的記錄提供者可供容器使用。</span><span class="sxs-lookup"><span data-stu-id="1c9cc-106">There are several types of log providers that are available for a container to use.</span></span> <span data-ttu-id="1c9cc-107">這可提供以多種格式建立和儲存記錄資訊的彈性。</span><span class="sxs-lookup"><span data-stu-id="1c9cc-107">This provides the flexibility to create and store log information in many formats.</span></span> <span data-ttu-id="1c9cc-108">在記錄中編列容器物件是兩個步驟的程序：首先啟用記錄，然後選取記錄提供者。</span><span class="sxs-lookup"><span data-stu-id="1c9cc-108">Enlisting a container object in logging is a two-step process: first logging is enabled, and then a log provider is selected.</span></span> <span data-ttu-id="1c9cc-109">該容器的 <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.LoggingOptions%2A> 與 <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.LoggingMode%2A> 屬性是用以指定記錄的事件並選取記錄提供者。</span><span class="sxs-lookup"><span data-stu-id="1c9cc-109">The <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.LoggingOptions%2A> and <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.LoggingMode%2A> properties of the container are used to specify the logged events and to select the log provider.</span></span>

## <a name="enabling-logging"></a><span data-ttu-id="1c9cc-110">啟用記錄</span><span class="sxs-lookup"><span data-stu-id="1c9cc-110">Enabling Logging</span></span>
 <span data-ttu-id="1c9cc-111">在每個可以執行記錄的容器中所找到的 <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.LoggingMode%2A> 屬性，可判斷容器的事件資訊是否記錄到事件記錄檔中。</span><span class="sxs-lookup"><span data-stu-id="1c9cc-111">The <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.LoggingMode%2A> property, found in each container that can perform logging, determines whether the container's event information is recorded to the event log.</span></span> <span data-ttu-id="1c9cc-112">將會從 <xref:Microsoft.SqlServer.Dts.Runtime.DTSLoggingMode> 結構指派值給這個屬性，而且預設會從容器的父系繼承。</span><span class="sxs-lookup"><span data-stu-id="1c9cc-112">This property is assigned a value from the <xref:Microsoft.SqlServer.Dts.Runtime.DTSLoggingMode> structure, and is inherited from the container's parent by default.</span></span> <span data-ttu-id="1c9cc-113">如果容器是封裝，也因此沒有父系，則屬性會使用 <xref:Microsoft.SqlServer.Dts.Runtime.DTSLoggingMode.UseParentSetting>，而其預設值為 `Disabled`。</span><span class="sxs-lookup"><span data-stu-id="1c9cc-113">If the container is a package, and therefore has no parent, the property uses the <xref:Microsoft.SqlServer.Dts.Runtime.DTSLoggingMode.UseParentSetting>, which defaults to `Disabled`.</span></span>

### <a name="selecting-a-log-provider"></a><span data-ttu-id="1c9cc-114">選取記錄提供者</span><span class="sxs-lookup"><span data-stu-id="1c9cc-114">Selecting a Log Provider</span></span>
 <span data-ttu-id="1c9cc-115">在將 <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.LoggingMode%2A> 屬性設定為 `Enabled` 之後，已將記錄提供者加入容器的 <xref:Microsoft.SqlServer.Dts.Runtime.SelectedLogProviders> 集合以完成該程序。</span><span class="sxs-lookup"><span data-stu-id="1c9cc-115">After the <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.LoggingMode%2A> property is set to `Enabled`, a log provider is added to the <xref:Microsoft.SqlServer.Dts.Runtime.SelectedLogProviders> collection of the container to complete the process.</span></span> <span data-ttu-id="1c9cc-116"><xref:Microsoft.SqlServer.Dts.Runtime.SelectedLogProviders> 集合可在 <xref:Microsoft.SqlServer.Dts.Runtime.LoggingOptions> 物件上使用，而且包含為容器所選取的記錄提供者。</span><span class="sxs-lookup"><span data-stu-id="1c9cc-116">The <xref:Microsoft.SqlServer.Dts.Runtime.SelectedLogProviders> collection is available on the <xref:Microsoft.SqlServer.Dts.Runtime.LoggingOptions> object, and contains the log providers selected for the container.</span></span> <span data-ttu-id="1c9cc-117">會呼叫 <xref:Microsoft.SqlServer.Dts.Runtime.SelectedLogProviders.Add%2A> 方法以建立提供者並將它加入集合中。</span><span class="sxs-lookup"><span data-stu-id="1c9cc-117">The <xref:Microsoft.SqlServer.Dts.Runtime.SelectedLogProviders.Add%2A> method is called to create a provider and add it to the collection.</span></span> <span data-ttu-id="1c9cc-118">該方法接著會傳回加入集合的記錄提供者。</span><span class="sxs-lookup"><span data-stu-id="1c9cc-118">The method then returns the log provider that was added to the collection.</span></span> <span data-ttu-id="1c9cc-119">每個提供者都有該提供者唯一的組態設定，而且這些屬性是使用 <xref:Microsoft.SqlServer.Dts.Runtime.LogProvider.ConfigString%2A> 屬性來設定。</span><span class="sxs-lookup"><span data-stu-id="1c9cc-119">Each provider has configuration settings that are unique to that provider, and these properties are set using the <xref:Microsoft.SqlServer.Dts.Runtime.LogProvider.ConfigString%2A> property.</span></span>

 <span data-ttu-id="1c9cc-120">下列表格列出可用的記錄提供者、其說明及其 <xref:Microsoft.SqlServer.Dts.Runtime.LogProvider.ConfigString%2A> 資訊。</span><span class="sxs-lookup"><span data-stu-id="1c9cc-120">The following table lists the available log providers, their description, and their <xref:Microsoft.SqlServer.Dts.Runtime.LogProvider.ConfigString%2A> information.</span></span>

|<span data-ttu-id="1c9cc-121">提供者</span><span class="sxs-lookup"><span data-stu-id="1c9cc-121">Provider</span></span>|<span data-ttu-id="1c9cc-122">描述</span><span class="sxs-lookup"><span data-stu-id="1c9cc-122">Description</span></span>|<span data-ttu-id="1c9cc-123">ConfigString 屬性</span><span class="sxs-lookup"><span data-stu-id="1c9cc-123">ConfigString property</span></span>|
|--------------|-----------------|---------------------------|
|<span data-ttu-id="1c9cc-124">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="1c9cc-124">SQL Server Profiler</span></span>|<span data-ttu-id="1c9cc-125">產生可能在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Profiler 中擷取和檢視的 SQL 追蹤。</span><span class="sxs-lookup"><span data-stu-id="1c9cc-125">Generates SQL traces that may be captured and viewed in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Profiler.</span></span> <span data-ttu-id="1c9cc-126">此提供者的預設副檔名為 .trc。</span><span class="sxs-lookup"><span data-stu-id="1c9cc-126">The default file name extension for this provider is .trc.</span></span>|<span data-ttu-id="1c9cc-127">不需要組態。</span><span class="sxs-lookup"><span data-stu-id="1c9cc-127">No configuration is required.</span></span>|
|<span data-ttu-id="1c9cc-128">SQL Server</span><span class="sxs-lookup"><span data-stu-id="1c9cc-128">SQL Server</span></span>|<span data-ttu-id="1c9cc-129">將事件記錄項目寫入任何 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫中的 **sysssislog** 資料表中。</span><span class="sxs-lookup"><span data-stu-id="1c9cc-129">Writes event log entries to the **sysssislog** table in any [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database.</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="1c9cc-130">提供者需要指定連至資料庫的連接，還須指定目標資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="1c9cc-130">provider requires that the connection to the database be specified, and also the target database name.</span></span>|
|<span data-ttu-id="1c9cc-131">文字檔</span><span class="sxs-lookup"><span data-stu-id="1c9cc-131">Text File</span></span>|<span data-ttu-id="1c9cc-132">將事件記錄項目以逗號分隔值 (CSV) 的格式寫入 ASCII 文字檔。</span><span class="sxs-lookup"><span data-stu-id="1c9cc-132">Writes event log entries to ASCII text files in a comma-separated value (CSV) format.</span></span> <span data-ttu-id="1c9cc-133">此提供者的預設副檔名為 .log。</span><span class="sxs-lookup"><span data-stu-id="1c9cc-133">The default file name extension for this provider is .log.</span></span>|<span data-ttu-id="1c9cc-134">檔案連接管理員的名稱。</span><span class="sxs-lookup"><span data-stu-id="1c9cc-134">The name of a file connection manager.</span></span>|
|<span data-ttu-id="1c9cc-135">Windows 事件記錄檔</span><span class="sxs-lookup"><span data-stu-id="1c9cc-135">Windows Event Log</span></span>|<span data-ttu-id="1c9cc-136">記錄到本機電腦上「應用程式」記錄中的標準 Windows 事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="1c9cc-136">Logs to standard Windows Event Log on the local computer in the Application log.</span></span>|<span data-ttu-id="1c9cc-137">不需要組態。</span><span class="sxs-lookup"><span data-stu-id="1c9cc-137">No configuration is required.</span></span>|
|<span data-ttu-id="1c9cc-138">XML 檔案</span><span class="sxs-lookup"><span data-stu-id="1c9cc-138">XML File</span></span>|<span data-ttu-id="1c9cc-139">將事件記錄檔項目寫入 XML 格式化的檔案。</span><span class="sxs-lookup"><span data-stu-id="1c9cc-139">Writes event log entries to XML formatted file.</span></span> <span data-ttu-id="1c9cc-140">此提供者的預設副檔名為 .xml。</span><span class="sxs-lookup"><span data-stu-id="1c9cc-140">The default file name extension for this provider is .xml</span></span>|<span data-ttu-id="1c9cc-141">檔案連接管理員的名稱。</span><span class="sxs-lookup"><span data-stu-id="1c9cc-141">The name of a file connection manager.</span></span>|

 <span data-ttu-id="1c9cc-142">透過設定容器的 `EventFilterKind` 與 `EventFilter` 屬性，會將事件包括在事件記錄檔中或排除在外。</span><span class="sxs-lookup"><span data-stu-id="1c9cc-142">Events are included in or excluded from the event log by setting the `EventFilterKind` and the `EventFilter` properties of the container.</span></span> <span data-ttu-id="1c9cc-143">`EventFilterKind` 結構包含兩個值：`ExclusionFilter` 與 `InclusionFilter`，它們指出加入 `EventFilter` 的事件是否包括在事件記錄檔中。</span><span class="sxs-lookup"><span data-stu-id="1c9cc-143">The `EventFilterKind` structure contains two values, `ExclusionFilter` and `InclusionFilter`, that indicate whether the events that are added to the `EventFilter` are included in the event log.</span></span> <span data-ttu-id="1c9cc-144">接著會指派含有是篩選主旨之事件名稱的字串陣列給 `EventFilter` 屬性。</span><span class="sxs-lookup"><span data-stu-id="1c9cc-144">The `EventFilter` property is then assigned a string array that contains the names of the events that are the subject of the filtering.</span></span>

 <span data-ttu-id="1c9cc-145">下列程式碼允許在封裝上記錄、將文字檔的記錄提供者加入 <xref:Microsoft.SqlServer.Dts.Runtime.SelectedLogProviders> 集合，並指定將事件清單包括在記錄輸出中。</span><span class="sxs-lookup"><span data-stu-id="1c9cc-145">The following code enables logging on a package, adds the log provider for Text files to the <xref:Microsoft.SqlServer.Dts.Runtime.SelectedLogProviders> collection, and specifies a list of events to include in the logging output.</span></span>

## <a name="sample"></a><span data-ttu-id="1c9cc-146">範例</span><span class="sxs-lookup"><span data-stu-id="1c9cc-146">Sample</span></span>

```csharp
using System;
using Microsoft.SqlServer.Dts.Runtime;

namespace Microsoft.SqlServer.Dts.Samples
{
  class Program
  {
    static void Main(string[] args)
    {
      Package p = new Package();

      ConnectionManager loggingConnection = p.Connections.Add("FILE");
      loggingConnection.ConnectionString = @"C:\SSISPackageLog.txt";

      LogProvider provider = p.LogProviders.Add("DTS.LogProviderTextFile.2");
      provider.ConfigString = loggingConnection.Name;
      p.LoggingOptions.SelectedLogProviders.Add(provider);
      p.LoggingOptions.EventFilterKind = DTSEventFilterKind.Inclusion;
      p.LoggingOptions.EventFilter = new String[] { "OnPreExecute", 
         "OnPostExecute", "OnError", "OnWarning", "OnInformation" };
      p.LoggingMode = DTSLoggingMode.Enabled;

      // Add tasks and other objects to the package.

    }
  }
}
```

```vb
Imports Microsoft.SqlServer.Dts.Runtime

Module Module1

  Sub Main()

    Dim p As Package = New Package()

    Dim loggingConnection As ConnectionManager = p.Connections.Add("FILE")
    loggingConnection.ConnectionString = "C:\SSISPackageLog.txt"

    Dim provider As LogProvider = p.LogProviders.Add("DTS.LogProviderTextFile.2")
    provider.ConfigString = loggingConnection.Name
    p.LoggingOptions.SelectedLogProviders.Add(provider)
    p.LoggingOptions.EventFilterKind = DTSEventFilterKind.Inclusion
    p.LoggingOptions.EventFilter = New String() {"OnPreExecute", _
       "OnPostExecute", "OnError", "OnWarning", "OnInformation"}
    p.LoggingMode = DTSLoggingMode.Enabled

    ' Add tasks and other objects to the package.

  End Sub

End Module
```

<span data-ttu-id="1c9cc-147">![Integration Services 圖示 (小型) ](../media/dts-16.gif "Integration Services 圖示 (小)")會**保持最**新狀態 Integration Services  </span><span class="sxs-lookup"><span data-stu-id="1c9cc-147">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="1c9cc-148">若要取得 Microsoft 的最新下載、文件、範例和影片以及社群中的精選解決方案，請瀏覽 MSDN 上的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 頁面：</span><span class="sxs-lookup"><span data-stu-id="1c9cc-148">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="1c9cc-149">瀏覽 MSDN 上的 Integration Services 頁面</span><span class="sxs-lookup"><span data-stu-id="1c9cc-149">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="1c9cc-150">若要得到這些更新的自動通知，請訂閱該頁面上所提供的 RSS 摘要。</span><span class="sxs-lookup"><span data-stu-id="1c9cc-150">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>

## <a name="see-also"></a><span data-ttu-id="1c9cc-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1c9cc-151">See Also</span></span>
 [<span data-ttu-id="1c9cc-152">Integration Services &#40;SSIS&#41; 記錄</span><span class="sxs-lookup"><span data-stu-id="1c9cc-152">Integration Services &#40;SSIS&#41; Logging</span></span>](../performance/integration-services-ssis-logging.md)


