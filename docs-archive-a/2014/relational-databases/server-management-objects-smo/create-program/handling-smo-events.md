---
title: 處理 SMO 事件 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- events [SMO]
- SQL Server Management Objects, events
- SMO [SQL Server], events
- events [SMO], about events
ms.assetid: b4f120dd-ba78-46ff-99c5-e47effac8544
author: stevestein
ms.author: sstein
ms.openlocfilehash: f7ea438142ac283c5ad19670fa827b5e248e80f7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606194"
---
# <a name="handling-smo-events"></a><span data-ttu-id="28cb5-102">處理 SMO 事件</span><span class="sxs-lookup"><span data-stu-id="28cb5-102">Handling SMO Events</span></span>
  <span data-ttu-id="28cb5-103">有些伺服器事件類型可以藉由事件處理常式和 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 物件進行訂閱。</span><span class="sxs-lookup"><span data-stu-id="28cb5-103">There are server event types that can be subscribed to by using an event handler and the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object.</span></span>  
  
 <span data-ttu-id="28cb5-104">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 管理物件 (SMO) 中的許多執行個體類別，都會在伺服器上發生特定動作時觸發事件。</span><span class="sxs-lookup"><span data-stu-id="28cb5-104">Many of the instance classes in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Management Objects (SMO) can trigger events when certain actions on the server occur.</span></span>  
  
 <span data-ttu-id="28cb5-105">這些事件可以藉由設定事件處理常式及訂閱相關事件，以程式設計的方式來處理。</span><span class="sxs-lookup"><span data-stu-id="28cb5-105">These events can be handled programmatically by setting up an event handler and subscribing to the associated events.</span></span> <span data-ttu-id="28cb5-106">這種事件處理類型是暫時性的，因為當 SMO 用戶端程式結束時會將訂閱全數移除。</span><span class="sxs-lookup"><span data-stu-id="28cb5-106">This type of event handling is transient because all the subscriptions are removed when the SMO client program exits.</span></span>  
  
## <a name="connectioncontext-event-handling"></a><span data-ttu-id="28cb5-107">ConnectionContext 事件處理</span><span class="sxs-lookup"><span data-stu-id="28cb5-107">ConnectionContext Event Handling</span></span>  
 <span data-ttu-id="28cb5-108"><xref:Microsoft.SqlServer.Management.Common.ServerConnection> 物件支援數種事件類型。</span><span class="sxs-lookup"><span data-stu-id="28cb5-108">The <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object supports several event types.</span></span> <span data-ttu-id="28cb5-109">事件屬性必須設定為具有適當事件處理常式的執行個體，而事件處理常式物件則必須定義為可以處理事件的受保護函數。</span><span class="sxs-lookup"><span data-stu-id="28cb5-109">The event property must be set to an instance of an appropriate event handler, and the event handler object must be defined as a protected function that handles the event.</span></span>  
  
## <a name="event-subscription"></a><span data-ttu-id="28cb5-110">事件訂閱</span><span class="sxs-lookup"><span data-stu-id="28cb5-110">Event Subscription</span></span>  
 <span data-ttu-id="28cb5-111">您可藉由下列步驟來處理事件：撰寫事件處理常式類別、建立其執行個體、將事件處理常式指派給父物件，然後再訂閱事件。</span><span class="sxs-lookup"><span data-stu-id="28cb5-111">You handle events by writing an event handler class, creating an instance of it, assigning the event handler to the parent object, and then subscribing to the event.</span></span>  
  
 <span data-ttu-id="28cb5-112">您必須撰寫事件處理常式類別，才能處理事件。</span><span class="sxs-lookup"><span data-stu-id="28cb5-112">An event handler class must be written to handle events.</span></span> <span data-ttu-id="28cb5-113">事件處理常式類別可以包含一個以上的事件處理常式函數，而且必須加以安裝，才能處理事件。</span><span class="sxs-lookup"><span data-stu-id="28cb5-113">The event handler class can contain more than one event handler function, and must be installed for the events to be handled.</span></span> <span data-ttu-id="28cb5-114">事件處理常式函式會從*ServerEventNotificatificationArgs*參數接收事件的相關資訊，可用來報告事件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="28cb5-114">The event handler functions receive information about the event from the *ServerEventNotificatificationArgs* parameter that can be used to report information about the event.</span></span>  
  
 <span data-ttu-id="28cb5-115">可以處理的資料庫和伺服器事件種類會列在 <xref:Microsoft.SqlServer.Management.Smo.DatabaseEventSet> 類別和 <xref:Microsoft.SqlServer.Management.Smo.ServerEventSet> 類別中。</span><span class="sxs-lookup"><span data-stu-id="28cb5-115">The types of database and server events that can be handled are listed in the <xref:Microsoft.SqlServer.Management.Smo.DatabaseEventSet> class and the <xref:Microsoft.SqlServer.Management.Smo.ServerEventSet>class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="28cb5-116">範例</span><span class="sxs-lookup"><span data-stu-id="28cb5-116">Example</span></span>  
 [!INCLUDE[ssChooseProgEnv](../../../includes/sschooseprogenv-md.md)]  
  
## <a name="registering-event-handlers-and-subscribing-to-event-handling-in-visual-basic"></a><span data-ttu-id="28cb5-117">在 Visual Basic 中註冊事件處理常式及訂閱事件處理</span><span class="sxs-lookup"><span data-stu-id="28cb5-117">Registering Event Handlers and Subscribing to Event Handling in Visual Basic</span></span>  
 <span data-ttu-id="28cb5-118">此程式碼範例示範如何設定事件處理常式，以及如何訂閱資料庫事件。</span><span class="sxs-lookup"><span data-stu-id="28cb5-118">This code example shows how to set up the event handler, and how to subscribe to the database events.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBEvents1](SMO How to#SMO_VBEvents1)]  -->  
  
## <a name="registering-event-handlers-and-subscribing-to-event-handling-in-visual-c"></a><span data-ttu-id="28cb5-119">在 Visual C# 中註冊事件處理常式及訂閱事件處理</span><span class="sxs-lookup"><span data-stu-id="28cb5-119">Registering Event Handlers and Subscribing to Event Handling in Visual C#</span></span>  
 <span data-ttu-id="28cb5-120">此程式碼範例示範如何設定事件處理常式，以及如何訂閱資料庫事件。</span><span class="sxs-lookup"><span data-stu-id="28cb5-120">This code example shows how to set up the event handler, and how to subscribe to the database events.</span></span>  
  
```  
//Create an event handler subroutine that runs when a table is created.   
private void MyCreateEventHandler(object sender, ServerEventArgs e)   
{   
Console.WriteLine("A table has just been added to the AdventureWorks2012 database.");   
}   
//Create an event handler subroutine that runs when a table is deleted.   
private void MyDropEventHandler(object sender, ServerEventArgs e)   
{   
Console.WriteLine("A table has just been dropped from the AdventureWorks2012 database.");   
}   
public void Main()   
{   
//Connect to the local, default instance of SQL Server.   
Server srv;   
srv = new Server();   
//Reference the AdventureWorks2012 database.   
Database db;   
db = srv.Databases("AdventureWorks2012");   
//Create a database event set that contains the CreateTable event only.   
DatabaseEventSet databaseCreateEventSet = new DatabaseEventSet();   
databaseCreateEventSet.CreateTable = true;   
//Create a server event handler and set it to the first event handler subroutine.   
ServerEventHandler serverCreateEventHandler;   
serverCreateEventHandler = new ServerEventHandler(MyCreateEventHandler);   
//Subscribe to the first server event handler when a CreateTable event occurs.   
db.Events.SubscribeToEvents(databaseCreateEventSet, serverCreateEventHandler);   
    //Create a database event set that contains the DropTable event only.   
DatabaseEventSet databaseDropEventSet = new DatabaseEventSet();   
databaseDropEventSet.DropTable = true;   
//Create a server event handler and set it to the second event handler subroutine.   
ServerEventHandler serverDropEventHandler;   
serverDropEventHandler = new ServerEventHandler(MyDropEventHandler);   
//Subscribe to the second server event handler when a DropTable event occurs.   
db.Events.SubscribeToEvents(databaseDropEventSet, serverDropEventHandler);   
//Start event handling.   
db.Events.StartEvents();   
//Create a table on the database.   
Table tb;   
tb = new Table(db, "Test_Table");   
Column mycol1;   
mycol1 = new Column(tb, "Name", DataType.NChar(50));   
mycol1.Collation = "Latin1_General_CI_AS";   
mycol1.Nullable = true;   
tb.Columns.Add(mycol1);   
tb.Create();   
//Remove the table.   
tb.Drop();   
//Wait until the events have occured.   
int x;   
int y;   
for (x = 1; x <= 1000000000; x++) {   
    y = x * 2;   
}   
//Stop event handling.   
db.Events.StopEvents();   
}  
```  
  
  
