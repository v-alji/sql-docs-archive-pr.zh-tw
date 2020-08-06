---
title: 使用 Database Mail |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- e-mail [SMO]
- Database Mail [SMO]
- mail [SMO]
ms.assetid: 7605390f-b485-48cc-8d97-e364a066067b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 86ceec7417638f53427ed5a62101f2fdb6d7440a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700918"
---
# <a name="using-database-mail"></a><span data-ttu-id="d0698-102">使用 Database Mail</span><span class="sxs-lookup"><span data-stu-id="d0698-102">Using Database Mail</span></span>
  <span data-ttu-id="d0698-103">在 SMO 中，Database Mail 子系統是由 <xref:Microsoft.SqlServer.Management.Smo.Mail.SqlMail> 屬性所參考的 <xref:Microsoft.SqlServer.Management.Smo.Server.Mail%2A> 物件表示。</span><span class="sxs-lookup"><span data-stu-id="d0698-103">In SMO, the Database Mail subsystem is represented by the <xref:Microsoft.SqlServer.Management.Smo.Mail.SqlMail> object that is referenced by the <xref:Microsoft.SqlServer.Management.Smo.Server.Mail%2A> property.</span></span> <span data-ttu-id="d0698-104">藉由使用 SMO <xref:Microsoft.SqlServer.Management.Smo.Mail.SqlMail> 物件，您可以設定 Database Mail 子系統，並且管理設定檔和郵件帳戶。</span><span class="sxs-lookup"><span data-stu-id="d0698-104">By using the SMO <xref:Microsoft.SqlServer.Management.Smo.Mail.SqlMail> object, you can configure the Database Mail subsystem and manage profiles and mail accounts.</span></span> <span data-ttu-id="d0698-105">SMO <xref:Microsoft.SqlServer.Management.Smo.Mail.SqlMail> 物件屬於 `Server` 物件，代表郵件帳戶的範圍是伺服器層級。</span><span class="sxs-lookup"><span data-stu-id="d0698-105">The SMO <xref:Microsoft.SqlServer.Management.Smo.Mail.SqlMail> object belongs to the `Server` object, meaning that scope of the mail accounts is at the server level.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="d0698-106">範例</span><span class="sxs-lookup"><span data-stu-id="d0698-106">Examples</span></span>  
 <span data-ttu-id="d0698-107">如果要使用所提供的任何程式碼範例，您必須選擇建立應用程式用的程式設計環境、程式設計範本，及程式設計語言。</span><span class="sxs-lookup"><span data-stu-id="d0698-107">To use any code example that is provided, you will have to choose the programming environment, the programming template, and the programming language in which to create your application.</span></span> <span data-ttu-id="d0698-108">如需詳細資訊，請參閱[在 Visual Studio .net 中建立 VISUAL BASIC SMO 專案](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md)或[在 Visual Studio .Net 中建立 VISUAL C&#35; SMO 專案](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)。</span><span class="sxs-lookup"><span data-stu-id="d0698-108">For more information, see [Create a Visual Basic SMO Project in Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) or [Create a Visual C&#35; SMO Project in Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).</span></span>  
  
 <span data-ttu-id="d0698-109">對於使用 Database Mail 的程式 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ，您必須包含 `Imports` 語句以限定郵件命名空間。</span><span class="sxs-lookup"><span data-stu-id="d0698-109">For programs that use [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Database Mail, you must include the `Imports` statement to qualify the Mail namespace.</span></span> <span data-ttu-id="d0698-110">將陳述式插入至其他 `Imports` 陳述式之後、在應用程式中的任何宣告之前，例如：</span><span class="sxs-lookup"><span data-stu-id="d0698-110">Insert the statement after the other `Imports` statements, before any declarations in the application, such as:</span></span>  
  
 `Imports Microsoft.SqlServer.Management.Smo`  
  
 `Imports Microsoft.SqlServer.Management.Common`  
  
 `Imports Microsoft.SqlServer.Management.Smo.Mail`  
  
## <a name="creating-a-database-mail-account-by-using-visual-basic"></a><span data-ttu-id="d0698-111">使用 Visual Basic 建立 Database Mail 帳戶</span><span class="sxs-lookup"><span data-stu-id="d0698-111">Creating a Database Mail Account by Using Visual Basic</span></span>  
 <span data-ttu-id="d0698-112">此程式碼範例示範如何在 SMO 中建立電子郵件帳戶。</span><span class="sxs-lookup"><span data-stu-id="d0698-112">This code example shows how to create an e-mail account in SMO.</span></span> <span data-ttu-id="d0698-113">Database Mail 是由 <xref:Microsoft.SqlServer.Management.Smo.Mail.SqlMail> 物件表示，且由 <xref:Microsoft.SqlServer.Management.Smo.Server.Mail%2A> 物件的 <xref:Microsoft.SqlServer.Management.Smo.Server> 屬性參考。</span><span class="sxs-lookup"><span data-stu-id="d0698-113">Database Mail is represented by the <xref:Microsoft.SqlServer.Management.Smo.Mail.SqlMail> object and referenced by the <xref:Microsoft.SqlServer.Management.Smo.Server.Mail%2A> property of the <xref:Microsoft.SqlServer.Management.Smo.Server> object.</span></span> <span data-ttu-id="d0698-114">SMO 可用於以程式設計的方式設定 Database Mail，但不能用於傳送或處理已收到的電子郵件。</span><span class="sxs-lookup"><span data-stu-id="d0698-114">SMO can be used to programmatically configure Database Mail, but it cannot be used to send or handle received e-mail.</span></span>  
  
 <span data-ttu-id="d0698-115">VB.NET</span><span class="sxs-lookup"><span data-stu-id="d0698-115">VB.NET</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBMail1](SMO How to#SMO_VBMail1)]  -->  
  
## <a name="creating-a-database-mail-account-by-using-visual-c"></a><span data-ttu-id="d0698-116">使用 Visual C# 建立 Database Mail 帳戶</span><span class="sxs-lookup"><span data-stu-id="d0698-116">Creating a Database Mail Account by Using Visual C#</span></span>  
 <span data-ttu-id="d0698-117">此程式碼範例示範如何在 SMO 中建立電子郵件帳戶。</span><span class="sxs-lookup"><span data-stu-id="d0698-117">This code example shows how to create an e-mail account in SMO.</span></span> <span data-ttu-id="d0698-118">Database Mail 是由 <xref:Microsoft.SqlServer.Management.Smo.Mail.SqlMail> 物件表示，且由 <xref:Microsoft.SqlServer.Management.Smo.Server.Mail%2A> 物件的 <xref:Microsoft.SqlServer.Management.Smo.Server> 屬性參考。</span><span class="sxs-lookup"><span data-stu-id="d0698-118">Database Mail is represented by the <xref:Microsoft.SqlServer.Management.Smo.Mail.SqlMail> object and referenced by the <xref:Microsoft.SqlServer.Management.Smo.Server.Mail%2A> property of the <xref:Microsoft.SqlServer.Management.Smo.Server> object.</span></span> <span data-ttu-id="d0698-119">SMO 可用於以程式設計的方式設定 Database Mail，但不能用於傳送或處理已收到的電子郵件。</span><span class="sxs-lookup"><span data-stu-id="d0698-119">SMO can be used to programmatically configure Database Mail, but it cannot be used to send or handle received e-mail.</span></span>  
  
```csharp  
{  
         //Connect to the local, default instance of SQL Server.  
         Server srv = default(Server);   
           srv = new Server();   
           //Define the Database Mail service with a SqlMail object variable   
           //and reference it using the Server Mail property.   
           SqlMail sm;   
           sm = srv.Mail;   
           //Define and create a mail account by supplying the Database Mail  
           //service, name, description, display name, and email address  
           //arguments in the constructor.   
           MailAccount a = default(MailAccount);   
           a = new MailAccount(sm, "AdventureWorks2012 Administrator", "AdventureWorks2012 Automated Mailer", "Mail account for administrative e-mail.", "dba@Adventure-Works.com");   
           a.Create();    
}  
```  
  
## <a name="creating-a-database-mail-account-by-using-powershell"></a><span data-ttu-id="d0698-120">使用 PowerShell 建立 Database Mail 帳戶</span><span class="sxs-lookup"><span data-stu-id="d0698-120">Creating a Database Mail Account by Using PowerShell</span></span>  
 <span data-ttu-id="d0698-121">此程式碼範例示範如何在 SMO 中建立電子郵件帳戶。</span><span class="sxs-lookup"><span data-stu-id="d0698-121">This code example shows how to create an e-mail account in SMO.</span></span> <span data-ttu-id="d0698-122">Database Mail 是由 <xref:Microsoft.SqlServer.Management.Smo.Mail.SqlMail> 物件表示，且由 <xref:Microsoft.SqlServer.Management.Smo.Server.Mail%2A> 物件的 <xref:Microsoft.SqlServer.Management.Smo.Server> 屬性參考。</span><span class="sxs-lookup"><span data-stu-id="d0698-122">Database Mail is represented by the <xref:Microsoft.SqlServer.Management.Smo.Mail.SqlMail> object and referenced by the <xref:Microsoft.SqlServer.Management.Smo.Server.Mail%2A> property of the <xref:Microsoft.SqlServer.Management.Smo.Server> object.</span></span> <span data-ttu-id="d0698-123">SMO 可用於以程式設計的方式設定 Database Mail，但不能用於傳送或處理已收到的電子郵件。</span><span class="sxs-lookup"><span data-stu-id="d0698-123">SMO can be used to programmatically configure Database Mail, but it cannot be used to send or handle received e-mail.</span></span>
  
```powershell  
#Connect to the local, default instance of SQL Server.  
  
#Get a server object which corresponds to the default instance  
$srv = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Server  
  
#Define the Database Mail; reference it using the Server Mail property.  
$sm = $srv.Mail  
  
#Define and create a mail account by supplying the Database Mail service,  
#name, description, display name, and email address arguments in the constructor.  
$a = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Mail.MailAccount -ArgumentList $sm, `  
"Adventure Works Administrator", "Adventure Works Automated Mailer",`  
 "Mail account for administrative e-mail.", "dba@Adventure-Works.com"  
$a.Create()  
```  
