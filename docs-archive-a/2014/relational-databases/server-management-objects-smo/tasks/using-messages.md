---
title: 使用訊息 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- messages [SMO]
ms.assetid: 4037a866-4826-4c1f-890c-e7e3658adf13
author: stevestein
ms.author: sstein
ms.openlocfilehash: 53b2e0fa4be2dfd53cdd8f4f0cacb7ae0bd79edb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599439"
---
# <a name="using-messages"></a><span data-ttu-id="798fd-102">使用訊息</span><span class="sxs-lookup"><span data-stu-id="798fd-102">Using Messages</span></span>
  <span data-ttu-id="798fd-103">在 SMO 中，系統訊息是由屬於 `Server` 物件的 <xref:Microsoft.SqlServer.Management.Smo.SystemMessageCollection> 物件表示。</span><span class="sxs-lookup"><span data-stu-id="798fd-103">In SMO, system messages are represented by the <xref:Microsoft.SqlServer.Management.Smo.SystemMessageCollection> object that belongs to the `Server` object.</span></span> <span data-ttu-id="798fd-104">因為系統訊息無法修改，所以 `SystemMessage` 物件屬性是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="798fd-104">Because the system messages cannot be modified, `SystemMessage` object properties are read-only.</span></span>  
  
 <span data-ttu-id="798fd-105">在 SMO 中，使用者定義的訊息是由 <xref:Microsoft.SqlServer.Management.Smo.UserDefinedMessageCollection> 物件以程式設計的方式表示。</span><span class="sxs-lookup"><span data-stu-id="798fd-105">User-defined messages are represented programmatically in SMO by the <xref:Microsoft.SqlServer.Management.Smo.UserDefinedMessageCollection> object.</span></span> <span data-ttu-id="798fd-106">現有的使用者定義的訊息可以藉由反覆運算集合而找到。</span><span class="sxs-lookup"><span data-stu-id="798fd-106">Existing user-defined messages can be discovered by iterating through the collection.</span></span> <span data-ttu-id="798fd-107">新的使用者定義訊息則可藉由具現化新的 `UserDefinedMessage` 物件和設定適當的屬性來建立。</span><span class="sxs-lookup"><span data-stu-id="798fd-107">New user-defined messages can be created by instantiating a new `UserDefinedMessage` object and setting the appropriate properties.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="798fd-108">範例</span><span class="sxs-lookup"><span data-stu-id="798fd-108">Examples</span></span>  
 <span data-ttu-id="798fd-109">在下列的程式碼範例中，您必須選取用於建立應用程式的程式設計環境、程式設計範本和程式設計語言。</span><span class="sxs-lookup"><span data-stu-id="798fd-109">For the following code examples, you will have to select the programming environment, programming template and the programming language to create your application.</span></span> <span data-ttu-id="798fd-110">如需詳細資訊，請參閱[在 Visual Studio .net 中建立 VISUAL BASIC SMO 專案](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md)和[在 Visual Studio .Net 中建立 VISUAL C&#35; SMO 專案](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)。</span><span class="sxs-lookup"><span data-stu-id="798fd-110">For more information, see [Create a Visual Basic SMO Project in Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) and [Create a Visual C&#35; SMO Project in Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).</span></span>  
  
## <a name="finding-a-particular-system-message-in-visual-basic"></a><span data-ttu-id="798fd-111">在 Visual Basic 中尋找特定的系統訊息</span><span class="sxs-lookup"><span data-stu-id="798fd-111">Finding a Particular System Message in Visual Basic</span></span>  
 <span data-ttu-id="798fd-112">此程式碼範例示範如何依識別碼辨識系統訊息並加以顯示。</span><span class="sxs-lookup"><span data-stu-id="798fd-112">The code example shows how to identify a system message by ID number and display the message.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBMessages1](SMO How to#SMO_VBMessages1)]  -->  
  
## <a name="finding-a-particular-system-message-in-visual-c"></a><span data-ttu-id="798fd-113">在 Visual C# 中尋找特定的系統訊息</span><span class="sxs-lookup"><span data-stu-id="798fd-113">Finding a Particular System Message in Visual C#</span></span>  
 <span data-ttu-id="798fd-114">此程式碼範例示範如何依識別碼辨識系統訊息並加以顯示。</span><span class="sxs-lookup"><span data-stu-id="798fd-114">The code example shows how to identify a system message by ID number and display the message.</span></span>  
  
```csharp
{  
            //Connect to the local, default instance of SQL Server.   
            Server srv = new Server();  
            //Reference an existing system message using the   
            //ItemByIdAndLanguage method.   
            SystemMessage msg = default(SystemMessage);  
            msg = srv.SystemMessages.ItemByIdAndLanguage(14126, "us_english");  
            //Display the message ID and text.   
            Console.WriteLine(msg.ID.ToString() + " " + msg.Text);  
        }  
```  
  
## <a name="finding-a-particular-system-message-in-powershell"></a><span data-ttu-id="798fd-115">在 PowerShell 中尋找特定的系統訊息</span><span class="sxs-lookup"><span data-stu-id="798fd-115">Finding a Particular System Message in PowerShell</span></span>  
 <span data-ttu-id="798fd-116">此程式碼範例示範如何依識別碼辨識系統訊息並加以顯示。</span><span class="sxs-lookup"><span data-stu-id="798fd-116">The code example shows how to identify a system message by ID number and display the message.</span></span>  
  
```powershell
# Set the path context to the local, default instance of SQL Server.  
CD \sql\localhost\  
$srv = Get-Item default  
  
#Get the message 14126 in US English and display it  
$msg = $srv.SystemMessages.ItemByIdAndLanguage(14126, "us_english")  
$msg.ID.ToString() + " "+ $msg.Text  
```  
  
## <a name="adding-a-new-user-defined-message-in-visual-basic"></a><span data-ttu-id="798fd-117">在 Visual Basic 中加入新的使用者自訂訊息</span><span class="sxs-lookup"><span data-stu-id="798fd-117">Adding a New User-Defined Message in Visual Basic</span></span>  
 <span data-ttu-id="798fd-118">此程式碼範例示範如何建立識別碼大於 50000 的使用者定義訊息。</span><span class="sxs-lookup"><span data-stu-id="798fd-118">The code example demonstrates how to create a user-defined message with an ID greater than 50000.</span></span>  
  
```vb
Dim mysrv As Server  
mysrv = New Server  
Dim udm As UserDefinedMessage  
udm = New UserDefinedMessage(mysrv, 50003, "us_english", 16, "Test message")  
udm.Create()  
```  
  
## <a name="adding-a-new-user-defined-message-in-visual-c"></a><span data-ttu-id="798fd-119">在 Visual C# 中加入新的使用者自訂訊息</span><span class="sxs-lookup"><span data-stu-id="798fd-119">Adding a New User-Defined Message in Visual C#</span></span>  
 <span data-ttu-id="798fd-120">此程式碼範例示範如何建立識別碼大於 50000 的使用者定義訊息。</span><span class="sxs-lookup"><span data-stu-id="798fd-120">The code example demonstrates how to create a user-defined message with an ID greater than 50000.</span></span>  
  
```csharp
{
            Server mysrv = new Server();  
  
            UserDefinedMessage udm = new UserDefinedMessage(mysrv, 50030, "us_english",16, "Test message");  
            udm.Create();  
             UserDefinedMessage  msg = mysrv.UserDefinedMessages.ItemByIdAndLanguage(50030, "us_english");  
            //Display the message ID and text.   
            Console.WriteLine(msg.ID.ToString() + " " + msg.Text);  
  
        }  
```  
  
## <a name="adding-a-new-user-defined-message-in-powershell"></a><span data-ttu-id="798fd-121">在 PowerShell 中加入新的使用者自訂訊息</span><span class="sxs-lookup"><span data-stu-id="798fd-121">Adding a New User-Defined Message in PowerShell</span></span>
 <span data-ttu-id="798fd-122">此程式碼範例示範如何建立識別碼大於 50000 的使用者定義訊息。</span><span class="sxs-lookup"><span data-stu-id="798fd-122">The code example demonstrates how to create a user-defined message with an ID greater than 50000.</span></span>  
  
```powershell
#Get a server object which corresponds to the default instance  
$srv = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Server  
  
#Create a new message
$udm = New-Object -TypeName Microsoft.SqlServer.Management.SMO.UserDefinedMessage -ArgumentList `  
$srv, 50030, "us_english", 16, "Test message"  
$udm.Create()  
$msg = $srv.UserDefinedMessages.ItemByIdAndLanguage(50030, "us_english");  
$msg  
```  
