---
title: 執行非同步作業 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- initialization [SQL Server Native Client]
- database connections [SQL Server Native Client]
- data access [SQL Server Native Client], asynchronous operations
- connections [SQL Server Native Client]
- asynchronous operations [SQL Server Native Client]
- rowsets [SQL Server], initializing
- SQLNCLI, asynchronous operations
- SQL Server Native Client, asynchronous operations
ms.assetid: 8fbd84b4-69cb-4708-9f0f-bbdf69029bcc
author: rothja
ms.author: jroth
ms.openlocfilehash: 4f7e8f4481923cd7da537f921248865d4fff7280
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698062"
---
# <a name="performing-asynchronous-operations"></a><span data-ttu-id="f7cbb-102">執行非同步作業</span><span class="sxs-lookup"><span data-stu-id="f7cbb-102">Performing Asynchronous Operations</span></span>
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="f7cbb-103">允許應用程式執行非同步資料庫作業。</span><span class="sxs-lookup"><span data-stu-id="f7cbb-103">allows applications to perform asynchronous database operations.</span></span> <span data-ttu-id="f7cbb-104">非同步處理可讓方法立即執行，而不會在呼叫的執行緒上封鎖。</span><span class="sxs-lookup"><span data-stu-id="f7cbb-104">Asynchronous processing enables methods to return immediately without blocking on the calling thread.</span></span> <span data-ttu-id="f7cbb-105">這樣可允許多執行緒的許多功能與彈性，而不需要開發人員明確建立執行緒或處理同步。</span><span class="sxs-lookup"><span data-stu-id="f7cbb-105">This allows much of the power and flexibility of multithreading, without requiring the developer to explicitly create threads or handle synchronization.</span></span> <span data-ttu-id="f7cbb-106">當初始化資料庫連接或初始化執行命令的結果時，應用程式會要求非同步處理。</span><span class="sxs-lookup"><span data-stu-id="f7cbb-106">Applications request asynchronous processing when initializing a database connection, or when initializing the result from the execution of a command.</span></span>  
  
## <a name="opening-and-closing-a-database-connection"></a><span data-ttu-id="f7cbb-107">開啟及關閉資料庫連接</span><span class="sxs-lookup"><span data-stu-id="f7cbb-107">Opening and Closing a Database Connection</span></span>  
 <span data-ttu-id="f7cbb-108">使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者時，設計為以非同步方式初始化資料來源物件的應用程式，可以在呼叫**IDBInitialize：： initialize**之前，在 DBPROP_INIT_ASYNCH 屬性中設定 DBPROPVAL_ASYNCH_INITIALIZE 位。</span><span class="sxs-lookup"><span data-stu-id="f7cbb-108">When using the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider, applications designed to initialize a data source object asynchronously can set the DBPROPVAL_ASYNCH_INITIALIZE bit in the DBPROP_INIT_ASYNCH property prior to calling **IDBInitialize::Initialize**.</span></span> <span data-ttu-id="f7cbb-109">設定此屬性時，如果作業已經立即完成，提供者會使用 S_OK 立即從 **Initialize** 的呼叫傳回；如果初始化是以非同步方式繼續，則會使用 DB_S_ASYNCHRONOUS 從此呼叫傳回。</span><span class="sxs-lookup"><span data-stu-id="f7cbb-109">When this property is set, the provider returns immediately from the call to **Initialize** with either S_OK, if the operation has completed immediately, or DB_S_ASYNCHRONOUS, if the initialization is continuing asynchronously.</span></span> <span data-ttu-id="f7cbb-110">應用程式可以在資料來源物件上查詢**IDBAsynchStatus**或[ISSAsynchStatus](../../native-client-ole-db-interfaces/issasynchstatus-ole-db.md)介面，然後呼叫**IDBAsynchStatus：： GetStatus**或[ISSAsynchStatus：： WaitForAsynchCompletion](../../native-client-ole-db-interfaces/issasynchstatus-waitforasynchcompletion-ole-db.md)來取得初始化的狀態。</span><span class="sxs-lookup"><span data-stu-id="f7cbb-110">Applications can query for the **IDBAsynchStatus** or [ISSAsynchStatus](../../native-client-ole-db-interfaces/issasynchstatus-ole-db.md)interface on the data source object, and then call **IDBAsynchStatus::GetStatus** or[ISSAsynchStatus::WaitForAsynchCompletion](../../native-client-ole-db-interfaces/issasynchstatus-waitforasynchcompletion-ole-db.md) to get the status of the initialization.</span></span>  
  
 <span data-ttu-id="f7cbb-111">此外，SSPROP_ISSAsynchStatus 屬性已加入到 DBPROPSET_SQLSERVERROWSET 屬性集。</span><span class="sxs-lookup"><span data-stu-id="f7cbb-111">In addition, the SSPROP_ISSAsynchStatus property has been added to the DBPROPSET_SQLSERVERROWSET property set.</span></span> <span data-ttu-id="f7cbb-112">支援 **ISSAsynchStatus** 介面的提供者必須使用 VARIANT_TRUE 的值實作此屬性。</span><span class="sxs-lookup"><span data-stu-id="f7cbb-112">Providers that support the **ISSAsynchStatus** interface must implement this property with a value of VARIANT_TRUE.</span></span>  
  
 <span data-ttu-id="f7cbb-113">呼叫 **IDBAsynchStatus::Abort** 或 [ISSAsynchStatus::Abort](../../native-client-ole-db-interfaces/issasynchstatus-abort-ole-db.md) 可以取消非同步的 **Initialize** 呼叫。</span><span class="sxs-lookup"><span data-stu-id="f7cbb-113">**IDBAsynchStatus::Abort** or [ISSAsynchStatus::Abort](../../native-client-ole-db-interfaces/issasynchstatus-abort-ole-db.md) can be called to cancel the asynchronous **Initialize** call.</span></span> <span data-ttu-id="f7cbb-114">取用者必須明確地要求非同步資料來源初始化。</span><span class="sxs-lookup"><span data-stu-id="f7cbb-114">The consumer must explicitly request Asynchronous Data Source Initialization.</span></span> <span data-ttu-id="f7cbb-115">否則，要等到資料來源物件完全初始化之後，**IDBInitialize::Initialize** 才會傳回。</span><span class="sxs-lookup"><span data-stu-id="f7cbb-115">Otherwise, **IDBInitialize::Initialize** does not return until the data source object is completely initialized.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f7cbb-116">用於連接共用的資料來源物件無法在**ISSAsynchStatus** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者中呼叫 ISSAsynchStatus 介面。</span><span class="sxs-lookup"><span data-stu-id="f7cbb-116">Data source objects used for connection pooling cannot call the **ISSAsynchStatus** interface in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider.</span></span> <span data-ttu-id="f7cbb-117">**ISSAsynchStatus** 介面不會針對集區資料來源物件公開。</span><span class="sxs-lookup"><span data-stu-id="f7cbb-117">The **ISSAsynchStatus** interface is not exposed for pooled data source objects.</span></span>  
>   
>  <span data-ttu-id="f7cbb-118">如果應用程式明確地強制使用資料指標引擎，**IOpenRowset::OpenRowset** 和 **IMultipleResults::GetResult** 將不支援非同步處理。</span><span class="sxs-lookup"><span data-stu-id="f7cbb-118">If an application explicitly forces use of the cursor engine, **IOpenRowset::OpenRowset** and **IMultipleResults::GetResult** will not support asynchronous processing.</span></span>  
>   
>  <span data-ttu-id="f7cbb-119">此外， (MDAC 2.8 中的遠端 proxy/stub dll，) 無法在 Native Client 中呼叫**ISSAsynchStatus**介面 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="f7cbb-119">In addition, the remoting proxy/stub dll (in MDAC 2.8) cannot call the **ISSAsynchStatus** interface in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.</span></span> <span data-ttu-id="f7cbb-120">**ISSAsynchStatus** 介面不會透過遠端公開。</span><span class="sxs-lookup"><span data-stu-id="f7cbb-120">The **ISSAsynchStatus** interface is not exposed through remoting.</span></span>  
>   
>  <span data-ttu-id="f7cbb-121">服務元件不支援 **ISSAsynchStatus**。</span><span class="sxs-lookup"><span data-stu-id="f7cbb-121">Service Components do not support **ISSAsynchStatus**.</span></span>  
  
## <a name="execution-and-rowset-initialization"></a><span data-ttu-id="f7cbb-122">執行和資料列集初始化</span><span class="sxs-lookup"><span data-stu-id="f7cbb-122">Execution and Rowset Initialization</span></span>  
 <span data-ttu-id="f7cbb-123">設計為非同步開啟執行命令結果的應用程式可以在 DBPROP_ROWSET_ASYNCH 屬性中設定 DBPROPVAL_ASYNCH_INITIALIZE 位元。</span><span class="sxs-lookup"><span data-stu-id="f7cbb-123">Applications designed to asynchronously open the result from the execution of a command can set the DBPROPVAL_ASYNCH_INITIALIZE bit in the DBPROP_ROWSET_ASYNCH property.</span></span> <span data-ttu-id="f7cbb-124">呼叫 **IDBInitialize::Initialize**、**ICommand::Execute**、**IOpenRowset::OpenRowset** 或 **IMultipleResults::GetResult** 之前設定此位元時，必須將 *riid* 引數設定為 IID_IDBAsynchStatus、IID_ISSAsynchStatus 或 IID_Iunknown。</span><span class="sxs-lookup"><span data-stu-id="f7cbb-124">When setting this bit prior to calling **IDBInitialize::Initialize**, **ICommand::Execute**, **IOpenRowset::OpenRowset** or **IMultipleResults::GetResult**, the *riid* argument must be set to IID_IDBAsynchStatus, IID_ISSAsynchStatus, or IID_IUnknown.</span></span>  
  
 <span data-ttu-id="f7cbb-125">如果資料列集初始化立即完成，此方法會使用 S_OK 立即傳回；如果資料列集在 *ppRowset* 設定為資料列集上要求的介面時，繼續以非同步方式初始化，則會使用 DB_S_ASYNCHRONOUS 傳回此方法。</span><span class="sxs-lookup"><span data-stu-id="f7cbb-125">The method returns immediately with S_OK if the rowset initialization completes immediately, or with DB_S_ASYNCHRONOUS if the rowset continues initializing asynchronously, with *ppRowset* set to the requested interface on the rowset.</span></span> <span data-ttu-id="f7cbb-126">針對 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者，此介面只能是**IDBAsynchStatus**或**ISSAsynchStatus**。</span><span class="sxs-lookup"><span data-stu-id="f7cbb-126">For the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider, this interface can only be **IDBAsynchStatus** or **ISSAsynchStatus**.</span></span> <span data-ttu-id="f7cbb-127">在資料列集完全初始化之前，此介面的行為如同處於已暫停狀態，而且針對 **IID_IDBAsynchStatus** 或 **IID_ISSAsynchStatus** 之外的介面呼叫 **QueryInterface** 可能會傳回 E_NOINTERFACE。</span><span class="sxs-lookup"><span data-stu-id="f7cbb-127">Until the rowset is fully initialized, this interface behaves as if it were in a suspended state, and calling **QueryInterface** for interfaces other than **IID_IDBAsynchStatus** or **IID_ISSAsynchStatus** may return E_NOINTERFACE.</span></span> <span data-ttu-id="f7cbb-128">除非取用者明確地要求非同步處理，否則資料列集會以同步的方式進行初始化。</span><span class="sxs-lookup"><span data-stu-id="f7cbb-128">Unless the consumer explicitly requests asynchronous processing, the rowset is initialized synchronously.</span></span> <span data-ttu-id="f7cbb-129">如果 **IDBAsynchStaus::GetStatus** 或 **ISSAsynchStatus::WaitForAsynchCompletion** 傳回時，指出非同步作業已完成，則可使用所有要求的介面。</span><span class="sxs-lookup"><span data-stu-id="f7cbb-129">All requested interfaces are available when **IDBAsynchStaus::GetStatus** or **ISSAsynchStatus::WaitForAsynchCompletion** returns with the indication that asynchronous operation is complete.</span></span> <span data-ttu-id="f7cbb-130">這不一定表示資料列集已完全擴展，但是該資料列集是完整的，而且完全可以運作。</span><span class="sxs-lookup"><span data-stu-id="f7cbb-130">This does not necessarily mean that the rowset is fully populated, but it is complete and fully functional.</span></span>  
  
 <span data-ttu-id="f7cbb-131">如果執行的命令並未傳回資料列集，它仍然會使用支援 **IDBAsynchStatus** 的物件立即傳回。</span><span class="sxs-lookup"><span data-stu-id="f7cbb-131">If the executed command does not return a rowset, it still returns immediately with an object that supports **IDBAsynchStatus**.</span></span>  
  
 <span data-ttu-id="f7cbb-132">如果您需要從非同步命令執行取得多個結果，您應該：</span><span class="sxs-lookup"><span data-stu-id="f7cbb-132">If you need to get multiple results from asynchronous command execution, you should:</span></span>  
  
-   <span data-ttu-id="f7cbb-133">在執行命令之前，設定 DBPROP_ROWSET_ASYNCH 屬性的 DBPROPVAL_ASYNCH_INITIALIZE 位元。</span><span class="sxs-lookup"><span data-stu-id="f7cbb-133">Set the DBPROPVAL_ASYNCH_INITIALIZE bit of the DBPROP_ROWSET_ASYNCH property, before executing the command.</span></span>  
  
-   <span data-ttu-id="f7cbb-134">呼叫 **ICommand::Execute**，並要求 **IMultipleResults**。</span><span class="sxs-lookup"><span data-stu-id="f7cbb-134">Call **ICommand::Execute**, and request **IMultipleResults**.</span></span>  
  
 <span data-ttu-id="f7cbb-135">接著，使用 **QueryInterface** 來查詢多個結果介面，藉此取得 **IDBAsynchStatus** 和 **ISSAsynchStatus** 介面。</span><span class="sxs-lookup"><span data-stu-id="f7cbb-135">The **IDBAsynchStatus** and **ISSAsynchStatus** interfaces can then be obtained by querying the multiple results interface using **QueryInterface**.</span></span>  
  
 <span data-ttu-id="f7cbb-136">當命令執行完成時，除非同步案例的一個例外，否則可以如常使用 **IMultipleResults**：可以傳回 DB_S_ASYNCHRONOUS，在此情況下，**IDBAsynchStatus** 或 **ISSAsynchStatus** 可用於判斷作業完成的時間。</span><span class="sxs-lookup"><span data-stu-id="f7cbb-136">When the command has finished executing, **IMultipleResults** can be used as normal, with one exception from the synchronous case: DB_S_ASYNCHRONOUS may be returned, in which case **IDBAsynchStatus** or **ISSAsynchStatus** can be used to determine when the operation is complete.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="f7cbb-137">範例</span><span class="sxs-lookup"><span data-stu-id="f7cbb-137">Examples</span></span>  
 <span data-ttu-id="f7cbb-138">在下列範例中，應用程式會呼叫非封鎖的方法、進行其他某些處理，然後返回處理結果。</span><span class="sxs-lookup"><span data-stu-id="f7cbb-138">In the following example, the application calls a non-blocking method, does some other processing, and then returns to process the results.</span></span> <span data-ttu-id="f7cbb-139">**ISSAsynchStatus::WaitForAsynchCompletion** 會等候內部事件物件，直到非同步執行作業完成，或是過了 *dwMilisecTimeOut* 所指定的時間為止。</span><span class="sxs-lookup"><span data-stu-id="f7cbb-139">**ISSAsynchStatus::WaitForAsynchCompletion** waits on the internal event object until the asynchronously executing operation is done or the amount of time specified by *dwMilisecTimeOut* is passed.</span></span>  
  
```  
// Set the DBPROPVAL_ASYNCH_INITIALIZE bit in the   
// DBPROP_ROWSET_ASYNCH property before calling Execute().  
  
DBPROPSET CmdPropset[1];  
DBPROP CmdProperties[1];  
  
CmdPropset[0].rgProperties = CmdProperties;  
CmdPropset[0].cProperties = 1;  
CmdPropset[0].guidPropertySet = DBPROPSET_ROWSET;  
  
// Set asynch mode for command.  
CmdProperties[0].dwPropertyID = DBPROP_ROWSET_ASYNCH;  
CmdProperties[0].vValue.vt = VT_I4;  
CmdProperties[0].vValue.lVal = DBPROPVAL_ASYNCH_INITIALIZE;  
CmdProperties[0].dwOptions = DBPROPOPTIONS_REQUIRED;  
  
hr = pICommandProps->SetProperties(1, CmdPropset);  
  
hr = pICommand->Execute(  
   pUnkOuter,  
   IID_ISSAsynchStatus,  
   pParams,  
   pcRowsAffected,  
   (IUnknown**)&pISSAsynchStatus);  
  
if (hr == DB_S_ASYNCHRONOUS)  
{  
   // Do some work here...  
  
   hr = pISSAsynchStatus->WaitForAsynchCompletion(dwMilisecTimeOut);  
   if ( hr == S_OK)  
   {  
      hr = pISSAsynchStatus->QueryInterface(IID_IRowset, (void**)&pRowset);  
      pISSAsynchStatus->Release();  
   }  
}  
```  
  
 <span data-ttu-id="f7cbb-140">**ISSAsynchStatus::WaitForAsynchCompletion** 會等候內部事件物件，直到非同步執行作業完成，或是過了 *dwMilisecTimeOut* 值為止。</span><span class="sxs-lookup"><span data-stu-id="f7cbb-140">**ISSAsynchStatus::WaitForAsynchCompletion** waits on the internal event object until the asynchronously executing operation is done or the *dwMilisecTimeOut* value is passed.</span></span>  
  
 <span data-ttu-id="f7cbb-141">下列範例會示範利用多個結果集的非同步處理：</span><span class="sxs-lookup"><span data-stu-id="f7cbb-141">The following example shows asynchronous processing with multiple result sets:</span></span>  
  
```  
DBPROP CmdProperties[1];  
  
// Set asynch mode for command.  
CmdProperties[0].dwPropertyID = DBPROP_ROWSET_ASYNCH;  
CmdProperties[0].vValue.vt = VT_I4;  
CmdProperties[0].vValue.lVal = DBPROPVAL_ASYNCH_INITIALIZE;  
  
hr = pICommand->Execute(  
   pUnkOuter,  
   IID_IMultipleResults,  
   pParams,  
   pcRowsAffected,  
   (IUnknown**)&pIMultipleResults);  
  
// Use GetResults for ISSAsynchStatus.  
hr = pIMultipleResults->GetResult(IID_ISSAsynchStatus, (void **) &pISSAsynchStatus);  
  
if (hr == DB_S_ASYNCHRONOUS)  
{  
   // Do some work here...  
  
   hr = pISSAsynchStatus->WaitForAsynchCompletion(dwMilisecTimeOut);  
   if (hr == S_OK)  
   {  
      hr = pISSAsynchStatus->QueryInterface(IID_IRowset, (void**)&pRowset);  
      pISSAsynchStatus->Release();  
   }  
}  
```  
  
 <span data-ttu-id="f7cbb-142">若要防止封鎖，用戶端可以檢查執行中非同步作業的狀態，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="f7cbb-142">To prevent blocking, the client can check the status of a running asynchronous operation, as in the following example:</span></span>  
  
```  
// Set the DBPROPVAL_ASYNCH_INITIALIZE bit in the   
// DBPROP_ROWSET_ASYNCH property before calling Execute().  
hr = pICommand->Execute(  
   pUnkOuter,  
   IID_ISSAsynchStatus,  
   pParams,  
   pcRowsAffected,  
   (IUnknown**)&pISSAsynchStatus);   
  
if (hr == DB_S_ASYNCHRONOUS)  
{  
   do{  
      // Do some work...  
      hr = pISSAsynchStatus->GetStatus(DB_NULL_HCHAPTER, DBASYNCHOP_OPEN, NULL, NULL, &ulAsynchPhase, NULL);  
   }while (DBASYNCHPHASE_COMPLETE != ulAsynchPhase)  
   if SUCCEEDED(hr)  
   {  
      hr = pISSAsynchStatus->QueryInterface(IID_IRowset, (void**)&pRowset);  
   }  
   pIDBAsynchStatus->Release();  
}  
```  
  
 <span data-ttu-id="f7cbb-143">下列範例會示範如何取消目前執行中的非同步作業：</span><span class="sxs-lookup"><span data-stu-id="f7cbb-143">The following example demonstrates how you can cancel the currently running asynchronous operation:</span></span>  
  
```  
// Set the DBPROPVAL_ASYNCH_INITIALIZE bit in the   
// DBPROP_ROWSET_ASYNCH property before calling Execute().  
hr = pICommand->Execute(  
   pUnkOuter,  
   IID_ISSAsynchStatus,  
   pParams,  
   pcRowsAffected,  
   (IUnknown**)&pISSAsynchStatus);  
  
if (hr == DB_S_ASYNCHRONOUS)  
{  
   // Do some work...  
   hr = pISSAsynchStatus->Abort(DB_NULL_HCHAPTER, DBASYNCHOP_OPEN);  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="f7cbb-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f7cbb-144">See Also</span></span>  
 <span data-ttu-id="f7cbb-145">[SQL Server Native Client 功能](sql-server-native-client-features.md) </span><span class="sxs-lookup"><span data-stu-id="f7cbb-145">[SQL Server Native Client Features](sql-server-native-client-features.md) </span></span>  
 <span data-ttu-id="f7cbb-146">[資料列集屬性和行為](../../native-client-ole-db-rowsets/rowset-properties-and-behaviors.md) </span><span class="sxs-lookup"><span data-stu-id="f7cbb-146">[Rowset Properties and Behaviors](../../native-client-ole-db-rowsets/rowset-properties-and-behaviors.md) </span></span>  
 [<span data-ttu-id="f7cbb-147">ISSAsynchStatus &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="f7cbb-147">ISSAsynchStatus &#40;OLE DB&#41;</span></span>](../../native-client-ole-db-interfaces/issasynchstatus-ole-db.md)  
  
  
