---
title: 使用 SQL Server 擴充事件 (XEvents) 來監視 Analysis Services |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: b57cc2fe-52dc-4fa9-8554-5a866e25c6d7
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9d12d9bc8d6a56702e1b44f8404b25681a1033f0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598038"
---
# <a name="use-sql-server-extended-events-xevents-to-monitor-analysis-services"></a><span data-ttu-id="45674-102">使用 SQL Server 擴充事件 (XEvents) 監視 Analysis Services</span><span class="sxs-lookup"><span data-stu-id="45674-102">Use SQL Server Extended Events (XEvents) to Monitor Analysis Services</span></span>
  <span data-ttu-id="45674-103">Analysis Services 透過使用[擴充事件](../../relational-databases/extended-events/extended-events.md)來提供追蹤功能。</span><span class="sxs-lookup"><span data-stu-id="45674-103">Analysis Services provides tracing capabilities through the usage of [Extended Events](../../relational-databases/extended-events/extended-events.md).</span></span>  
  
 <span data-ttu-id="45674-104">「擴充事件」是一種可針對伺服器系統高度擴充和設定的事件基礎結構。</span><span class="sxs-lookup"><span data-stu-id="45674-104">Extended Events is an event infrastructure that is highly scalable and configurable for server systems.</span></span> <span data-ttu-id="45674-105">「擴充事件」是一種使用極少量效能資源的一種輕量型效能監視系統。</span><span class="sxs-lookup"><span data-stu-id="45674-105">Extended Events is a light weight performance monitoring system that uses very few performance resources.</span></span>  
  
 <span data-ttu-id="45674-106">所有 Analysis Services 事件都可以透過 XEvents 來捕捉，並以[擴充事件](../../relational-databases/extended-events/extended-events.md)中所定義的特定取用者為目標。</span><span class="sxs-lookup"><span data-stu-id="45674-106">All Analysis Services events can be captured and target to specific consumers, as defined in [Extended Events](../../relational-databases/extended-events/extended-events.md), through XEvents.</span></span>  
  
## <a name="initiating-extended-events-in-analysis-services"></a><span data-ttu-id="45674-107">起始 Analysis Services 中的擴充事件</span><span class="sxs-lookup"><span data-stu-id="45674-107">Initiating Extended Events in Analysis Services</span></span>  
 <span data-ttu-id="45674-108">您可以使用類似的 XMLA 建立物件指令碼命令來啟用擴充事件追蹤，如下所示：</span><span class="sxs-lookup"><span data-stu-id="45674-108">Extended Event tracing is enabled using a similar XMLA create object script command as shown below:</span></span>  
  
```  
<Execute ...>  
   <Command>  
      <Batch ...>  
         <Create ...>  
            <ObjectDefinition>  
               <Trace>  
                  <ID>trace_id</ID>  
                  <Name>trace_name</Name>  
                  <ddl300_300:XEvent>  
                     <event_session ...>  
                        <event package="AS" name="AS_event">  
                           <action package="PACKAGE0" .../>  
                        </event>  
                        <target package="PACKAGE0" name="asynchronous_file_target">  
                           <parameter name="filename" value="data_filename.xel"/>  
                           <parameter name="metadatafile" value="metadata_filename.xem"/>  
                        </target>  
                     </event_session>  
                  </ddl300_300:XEvent>  
               </Trace>  
            </ObjectDefinition>  
         </Create>  
      </Batch>  
   </Command>  
   <Properties></Properties>  
</Execute>  
  
```  
  
 <span data-ttu-id="45674-109">其中，下列元素會由使用者根據追蹤需要而定義：</span><span class="sxs-lookup"><span data-stu-id="45674-109">Where the following elements are to be defined by the user, depending on the tracing needs:</span></span>  
  
 <span data-ttu-id="45674-110">*trace_id*</span><span class="sxs-lookup"><span data-stu-id="45674-110">*trace_id*</span></span>  
 <span data-ttu-id="45674-111">定義此追蹤的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="45674-111">Defines the unique identifier for this trace.</span></span>  
  
 <span data-ttu-id="45674-112">*trace_name*</span><span class="sxs-lookup"><span data-stu-id="45674-112">*trace_name*</span></span>  
 <span data-ttu-id="45674-113">提供給此追蹤的名稱；通常是人們可讀取的追蹤定義。</span><span class="sxs-lookup"><span data-stu-id="45674-113">The name given to this trace; usually a human readable definition of the trace.</span></span> <span data-ttu-id="45674-114">使用 *trace_id* 值作為名稱是常見的做法。</span><span class="sxs-lookup"><span data-stu-id="45674-114">It is a common practice to use the *trace_id* value as the name.</span></span>  
  
 <span data-ttu-id="45674-115">*AS_event*</span><span class="sxs-lookup"><span data-stu-id="45674-115">*AS_event*</span></span>  
 <span data-ttu-id="45674-116">要公開的 Analysis Services 事件。</span><span class="sxs-lookup"><span data-stu-id="45674-116">The Analysis Services event to be exposed.</span></span> <span data-ttu-id="45674-117">如需事件的名稱，請參閱 [Analysis Services 追蹤事件](https://docs.microsoft.com/bi-reference/trace-events/analysis-services-trace-events) 。</span><span class="sxs-lookup"><span data-stu-id="45674-117">See [Analysis Services Trace Events](https://docs.microsoft.com/bi-reference/trace-events/analysis-services-trace-events) for names of the events.</span></span>  
  
 <span data-ttu-id="45674-118">*data_filename*</span><span class="sxs-lookup"><span data-stu-id="45674-118">*data_filename*</span></span>  
 <span data-ttu-id="45674-119">包含事件資料之檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="45674-119">The name of the file that contains the events data.</span></span> <span data-ttu-id="45674-120">此名稱的後置字元為時間戳記，以防重複傳送追蹤時，資料遭到覆寫。</span><span class="sxs-lookup"><span data-stu-id="45674-120">This name is suffixed with a time stamp to avoid data overwriting if the trace is sent over and over.</span></span>  
  
 <span data-ttu-id="45674-121">*metadata_filename*</span><span class="sxs-lookup"><span data-stu-id="45674-121">*metadata_filename*</span></span>  
 <span data-ttu-id="45674-122">包含事件中繼資料之檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="45674-122">The name of the file that contains the events metadata.</span></span> <span data-ttu-id="45674-123">此名稱的後置字元為時間戳記，以防重複傳送追蹤時，資料遭到覆寫。</span><span class="sxs-lookup"><span data-stu-id="45674-123">This name is suffixed with a time stamp to avoid data overwriting if the trace is sent over and over.</span></span>  
  
## <a name="stopping-extended-events-in-analysis-services"></a><span data-ttu-id="45674-124">停止 Analysis Services 中的擴充事件</span><span class="sxs-lookup"><span data-stu-id="45674-124">Stopping Extended Events in Analysis Services</span></span>  
 <span data-ttu-id="45674-125">若要停止擴充事件追蹤物件，您需要使用類似的 XMLA 刪除物件指令碼命令來刪除該物件，如下所示：</span><span class="sxs-lookup"><span data-stu-id="45674-125">To stop the Extended Events tracing object you need to delete that object using a similar XMLA delete object script command as shown below:</span></span>  
  
```  
<Execute xmlns="urn:schemas-microsoft-com:xml-analysis">  
   <Command>  
      <Batch ...>  
         <Delete ...>  
            <Object>  
               <TraceID>trace_id</TraceID>  
            </Object>  
         </Delete>  
      </Batch>  
   </Command>  
   <Properties></Properties>  
</Execute>  
  
```  
  
 <span data-ttu-id="45674-126">其中，下列元素會由使用者根據追蹤需要而定義：</span><span class="sxs-lookup"><span data-stu-id="45674-126">Where the following elements are to be defined by the user, depending on the tracing needs:</span></span>  
  
 <span data-ttu-id="45674-127">*trace_id*</span><span class="sxs-lookup"><span data-stu-id="45674-127">*trace_id*</span></span>  
 <span data-ttu-id="45674-128">定義要刪除之追蹤的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="45674-128">Defines the unique identifier for the trace to be deleted.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45674-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="45674-129">See Also</span></span>  
 [<span data-ttu-id="45674-130">擴充事件</span><span class="sxs-lookup"><span data-stu-id="45674-130">Extended Events</span></span>](../../relational-databases/extended-events/extended-events.md)  
  
  
