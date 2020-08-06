---
title: 處理 SMO 例外狀況 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- SMO [SQL Server], exceptions
- exceptions [SMO]
- SQL Server Management Objects, exceptions
- inner exceptions [SMO]
ms.assetid: 4c725ff2-6588-44ca-b86a-87979e164153
author: stevestein
ms.author: sstein
ms.openlocfilehash: f4ae9e475a019c9bf874ee3f8365f3f3ac8e19d5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606186"
---
# <a name="handling-smo-exceptions"></a><span data-ttu-id="e83a3-102">處理 SMO 例外狀況</span><span class="sxs-lookup"><span data-stu-id="e83a3-102">Handling SMO Exceptions</span></span>
  <span data-ttu-id="e83a3-103">在 Managed 程式碼中發生錯誤時會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="e83a3-103">In managed code, exceptions are thrown when an error occurs.</span></span> <span data-ttu-id="e83a3-104">SMO 方法和屬性不會在傳回值中報告成功或失敗，</span><span class="sxs-lookup"><span data-stu-id="e83a3-104">SMO methods and properties do not report success or failure in the return value.</span></span> <span data-ttu-id="e83a3-105">而是由例外處理常式攔截和處理例外狀況。</span><span class="sxs-lookup"><span data-stu-id="e83a3-105">Instead, exceptions can be caught and handled by an exception handler.</span></span>  
  
 <span data-ttu-id="e83a3-106">SMO 中有不同的例外狀況類別。</span><span class="sxs-lookup"><span data-stu-id="e83a3-106">Different exception classes exist in the SMO.</span></span> <span data-ttu-id="e83a3-107">有關例外狀況的資訊可以擷取自例外狀況屬性，例如 `Message` 屬性，此屬性會提供有關例外狀況的文字訊息。</span><span class="sxs-lookup"><span data-stu-id="e83a3-107">Information about the exception can be extracted from the exception properties such as the `Message` property that gives a text message about the exception.</span></span>  
  
 <span data-ttu-id="e83a3-108">例外狀況處理陳述式會依程式語言而定。</span><span class="sxs-lookup"><span data-stu-id="e83a3-108">The exception handling statements are specific to the programming language.</span></span> <span data-ttu-id="e83a3-109">例如，在 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic 中是 `Catch` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="e83a3-109">For example, in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic it is the `Catch` statement.</span></span>  
  
## <a name="inner-exceptions"></a><span data-ttu-id="e83a3-110">內部例外狀況</span><span class="sxs-lookup"><span data-stu-id="e83a3-110">Inner Exceptions</span></span>  
 <span data-ttu-id="e83a3-111">例外狀況可以是一般或特定的。</span><span class="sxs-lookup"><span data-stu-id="e83a3-111">Exceptions can either be general or specific.</span></span> <span data-ttu-id="e83a3-112">一般例外狀況包含一組特定的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="e83a3-112">General exceptions contain a set of specific exceptions.</span></span> <span data-ttu-id="e83a3-113">可以用數個 `Catch` 陳述式來處理預期的錯誤，而讓剩餘的錯誤通過以留待一般例外狀況處理程式碼處理。</span><span class="sxs-lookup"><span data-stu-id="e83a3-113">Several `Catch` statements can be used to handle anticipated errors and let remaining errors fall through to general exception handling code.</span></span> <span data-ttu-id="e83a3-114">例外狀況通常是以串聯式序列發生。</span><span class="sxs-lookup"><span data-stu-id="e83a3-114">Exceptions often occur in a cascading sequence.</span></span> <span data-ttu-id="e83a3-115">SMO 例外狀況經常是由 SQL 例外狀況所導致。</span><span class="sxs-lookup"><span data-stu-id="e83a3-115">Frequently, an SMO exception might have been caused by an SQL exception.</span></span> <span data-ttu-id="e83a3-116">偵測此種狀況的方法是連續使用 `InnerException` 屬性來判斷導致最後之最上層例外狀況的原始例外狀況。</span><span class="sxs-lookup"><span data-stu-id="e83a3-116">The way to detect this is to use the `InnerException` property successively to determine the original exception that caused the final, top-level exception.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e83a3-117">`SQLException`例外狀況是在**SqlClient**命名空間中宣告的。</span><span class="sxs-lookup"><span data-stu-id="e83a3-117">The `SQLException` exception is declared in the **System.Data.SqlClient** namespace.</span></span>  
  
 <span data-ttu-id="e83a3-118">![顯示 excp 等級的長條圖](../../../database-engine/dev-guide/media/exception-flow.gif "顯示 excp 等級的長條圖")</span><span class="sxs-lookup"><span data-stu-id="e83a3-118">![A diagram that shows the levels from which an excp](../../../database-engine/dev-guide/media/exception-flow.gif "A diagram that shows the levels from which an excp")</span></span>  
  
 <span data-ttu-id="e83a3-119">此圖顯示應用程式層級中的例外狀況流程。</span><span class="sxs-lookup"><span data-stu-id="e83a3-119">The diagram shows the flow of exceptions through the layers of the application.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e83a3-120">範例</span><span class="sxs-lookup"><span data-stu-id="e83a3-120">Example</span></span>  
 <span data-ttu-id="e83a3-121">如果要使用所提供的任何程式碼範例，您必須選擇建立應用程式用的程式設計環境、程式設計範本，及程式設計語言。</span><span class="sxs-lookup"><span data-stu-id="e83a3-121">To use any code example that is provided, you will have to choose the programming environment, the programming template, and the programming language in which to create your application.</span></span> <span data-ttu-id="e83a3-122">如需詳細資訊，請參閱[在 Visual Studio .net 中建立 Visual C&#35; SMO 專案](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)或[在 Visual Studio .net 中建立 Visual Basic SMO 專案](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md)。</span><span class="sxs-lookup"><span data-stu-id="e83a3-122">For more information, see [Create a Visual C&#35; SMO Project in Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md) or [Create a Visual Basic SMO Project in Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md).</span></span>  
  
## <a name="catching-an-exception-in-visual-basic"></a><span data-ttu-id="e83a3-123">在 Visual Basic 中攔截例外狀況</span><span class="sxs-lookup"><span data-stu-id="e83a3-123">Catching an Exception in Visual Basic</span></span>  
 <span data-ttu-id="e83a3-124">這個程式碼範例示範如何使用 `Try...Catch...Finally`[!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] 陳述式來攔截 SMO 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="e83a3-124">This code example shows how to use the `Try...Catch...Finally`[!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] statement to catch a SMO exception.</span></span> <span data-ttu-id="e83a3-125">所有的 SMO 例外狀況都具有 SmoException 類型，而且會列於 SMO 參考中。</span><span class="sxs-lookup"><span data-stu-id="e83a3-125">All SMO exceptions have the type SmoException, and are listed in the SMO reference.</span></span> <span data-ttu-id="e83a3-126">內部例外狀況的順序會顯示，以指出錯誤的根源所在。</span><span class="sxs-lookup"><span data-stu-id="e83a3-126">The sequence of inner exceptions is displayed to show the root of the error.</span></span> <span data-ttu-id="e83a3-127">如需詳細資訊，請參閱 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] .NET 文件集。</span><span class="sxs-lookup"><span data-stu-id="e83a3-127">For more information, see the [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] .NET documentation.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBExceptions1](SMO How to#SMO_VBExceptions1)]  -->  
  
## <a name="catching-an-exception-in-visual-c"></a><span data-ttu-id="e83a3-128">在 Visual C# 中攔截例外狀況</span><span class="sxs-lookup"><span data-stu-id="e83a3-128">Catching an Exception in Visual C#</span></span>  
 <span data-ttu-id="e83a3-129">此程式碼範例示範如何使用 `Try...Catch...Finally` Visual C# 陳述式來攔截 SMO 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="e83a3-129">This code example shows how to use the `Try...Catch...Finally` Visual C# statement to catch a SMO exception.</span></span> <span data-ttu-id="e83a3-130">所有的 SMO 例外狀況都具有 SmoException 類型，而且會列於 SMO 參考中。</span><span class="sxs-lookup"><span data-stu-id="e83a3-130">All SMO exceptions have the type SmoException, and are listed in the SMO reference.</span></span> <span data-ttu-id="e83a3-131">內部例外狀況的順序會顯示，以指出錯誤的根源所在。</span><span class="sxs-lookup"><span data-stu-id="e83a3-131">The sequence of inner exceptions is displayed to show the root of the error.</span></span> <span data-ttu-id="e83a3-132">如需詳細資訊，請參閱 Visual C# 文件集。</span><span class="sxs-lookup"><span data-stu-id="e83a3-132">For more information, see the Visual C# documentation.</span></span>  
  
```  
{   
//This sample requires the Microsoft.SqlServer.Management.Smo.Agent namespace to be included.   
//Connect to the local, default instance of SQL Server.   
Server srv;   
srv = new Server();   
//Define an Operator object variable by supplying the parent SQL Agent and the name arguments in the constructor.   
//Note that the Operator type requires [] parenthesis to differentiate it from a Visual Basic key word.   
op = new Operator(srv.JobServer, "Test_Operator");   
op.Create();   
//Start exception handling.   
try {   
    //Create the operator again to cause an SMO exception.   
    OperatorCategory opx;   
    opx = new OperatorCategory(srv.JobServer, "Test_Operator");   
    opx.Create();   
}   
//Catch the SMO exception   
catch (SmoException smoex) {   
    Console.WriteLine("This is an SMO Exception");   
   //Display the SMO exception message.   
   Console.WriteLine(smoex.Message);   
   //Display the sequence of non-SMO exceptions that caused the SMO exception.   
   Exception ex;   
   ex = smoex.InnerException;   
   while (!object.ReferenceEquals(ex.InnerException, (null))) {   
      Console.WriteLine(ex.InnerException.Message);   
      ex = ex.InnerException;   
    }   
    }   
   //Catch other non-SMO exceptions.   
   catch (Exception ex) {   
      Console.WriteLine("This is not an SMO exception.");   
}   
}  
```  
  
  
