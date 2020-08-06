---
title: 以指令碼工作傳送 HTML 郵件訊息 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- Send Mail task [Integration Services]
- Script task [Integration Services], examples
- Script task [Integration Services], HTML mail message
ms.assetid: dd2b1eef-b04f-4946-87ab-7bc56bb525ce
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 6c1a967b52a84e1ff9c2e54c48e40f4d149b2dbc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687056"
---
# <a name="sending-an-html-mail-message-with-the-script-task"></a><span data-ttu-id="0404d-102">使用指令碼工作傳送 HTML 郵件訊息</span><span class="sxs-lookup"><span data-stu-id="0404d-102">Sending an HTML Mail Message with the Script Task</span></span>
  <span data-ttu-id="0404d-103">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] SendMail 工作只支援純文字格式的郵件訊息。</span><span class="sxs-lookup"><span data-stu-id="0404d-103">The [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] SendMail task only supports mail messages in plain text format.</span></span> <span data-ttu-id="0404d-104">不過您可以使用指令碼工作與 .NET Framework 的郵件功能，輕鬆地傳送 HTML 郵件訊息。</span><span class="sxs-lookup"><span data-stu-id="0404d-104">However you can easily send HTML mail messages by using the Script task and the mail capabilities of the .NET Framework.</span></span>

> [!NOTE]
>  <span data-ttu-id="0404d-105">如果您想要建立可更輕鬆地在多個封裝之間重複使用的工作，請考慮使用此指令碼工作範例中的程式碼做為自訂工作的起點。</span><span class="sxs-lookup"><span data-stu-id="0404d-105">If you want to create a task that you can more easily reuse across multiple packages, consider using the code in this Script task sample as the starting point for a custom task.</span></span> <span data-ttu-id="0404d-106">如需詳細資訊，請參閱 [開發自訂工作](../extending-packages-custom-objects/task/developing-a-custom-task.md)。</span><span class="sxs-lookup"><span data-stu-id="0404d-106">For more information, see [Developing a Custom Task](../extending-packages-custom-objects/task/developing-a-custom-task.md).</span></span>

## <a name="description"></a><span data-ttu-id="0404d-107">描述</span><span class="sxs-lookup"><span data-stu-id="0404d-107">Description</span></span>
 <span data-ttu-id="0404d-108">下列範例使用 `System.Net.Mail` 命名空間來設定和傳送 HTML 郵件訊息。</span><span class="sxs-lookup"><span data-stu-id="0404d-108">The following example uses the `System.Net.Mail` namespace to configure and send an HTML mail message.</span></span> <span data-ttu-id="0404d-109">指令碼會從封裝變數取得電子郵件的收件者、寄件者、主旨以及本文、使用它們來建立新的 `MailMessag`e 並將其 `IsBodyHtml` 屬性設定為 `True`。</span><span class="sxs-lookup"><span data-stu-id="0404d-109">The script obtains the To, From, Subject, and body of the e-mail from package variables, uses them to create a new `MailMessag`e, and sets its `IsBodyHtml` property to `True`.</span></span> <span data-ttu-id="0404d-110">然後它會從其他封裝變數取得 SMTP 伺服器名稱、初始化 `System.Net.Mail.SmtpClient` 的執行個體，然後呼叫其 `Send` 方法以傳送 HTML 訊息。</span><span class="sxs-lookup"><span data-stu-id="0404d-110">Then it obtains the SMTP server name from another package variable, initializes an instance of `System.Net.Mail.SmtpClient`, and calls its `Send` method to send the HTML message.</span></span> <span data-ttu-id="0404d-111">這個範例會封裝在副程式中傳送功能的訊息，副程式本身可在其他指令碼中重複使用。</span><span class="sxs-lookup"><span data-stu-id="0404d-111">The sample encapsulates the message sending functionality in a subroutine that could be reused in other scripts.</span></span>

#### <a name="to-configure-this-script-task-example-without-an-smtp-connection-manager"></a><span data-ttu-id="0404d-112">若要不使用 SMTP 連接管理員來設定這個指令碼工作範例</span><span class="sxs-lookup"><span data-stu-id="0404d-112">To configure this Script Task example without an SMTP Connection Manager</span></span>

1.  <span data-ttu-id="0404d-113">建立名為 `HtmlEmailTo`、`HtmlEmailFrom` 和 `HtmlEmailSubject` 的字串變數，並為有效的測試訊息指派適當的值給它們。</span><span class="sxs-lookup"><span data-stu-id="0404d-113">Create string variables named `HtmlEmailTo`, `HtmlEmailFrom`, and `HtmlEmailSubject` and assign appropriate values to them for a valid test message.</span></span>

2.  <span data-ttu-id="0404d-114">建立名為 `HtmlEmailBody` 的字串變數，並將 HTML 標記的字串指派給它。</span><span class="sxs-lookup"><span data-stu-id="0404d-114">Create a string variable named `HtmlEmailBody` and assign a string of HTML markup to it.</span></span> <span data-ttu-id="0404d-115">例如：</span><span class="sxs-lookup"><span data-stu-id="0404d-115">For example:</span></span>

    ```
    <html><body><h1>Testing</h1><p>This is a <b>test</b> message.</p></body></html>
    ```

3.  <span data-ttu-id="0404d-116">建立名為 `HtmlEmailServer` 的字串變數，並指派可用的 SMTP 伺服器名稱，以接受匿名的外寄訊息。</span><span class="sxs-lookup"><span data-stu-id="0404d-116">Create a string variable named `HtmlEmailServer` and assign the name of an available SMTP server that accepts anonymous outgoing messages.</span></span>

4.  <span data-ttu-id="0404d-117">將這五個變數全部都指派到新指令碼工作的 **ReadOnlyVariables** 屬性。</span><span class="sxs-lookup"><span data-stu-id="0404d-117">Assign all five of these variables to the **ReadOnlyVariables** property of a new Script task.</span></span>

5.  <span data-ttu-id="0404d-118">將 `System.Net` 與 `System.Net.Mail` 命名空間匯入您的程式碼。</span><span class="sxs-lookup"><span data-stu-id="0404d-118">Import the `System.Net` and `System.Net.Mail` namespaces into your code.</span></span>

 <span data-ttu-id="0404d-119">本主題中的範例程式碼會從封裝變數取得 SMTP 伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="0404d-119">The sample code in this topic obtains the SMTP server name from a package variable.</span></span> <span data-ttu-id="0404d-120">不過，您也可以利用 SMTP 連接管理員封裝連接資訊，並從程式碼中的連接管理員擷取伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="0404d-120">However, you could also take advantage of an SMTP connection manager to encapsulate the connection information, and extract the server name from the connection manager in your code.</span></span> <span data-ttu-id="0404d-121">SMTP 連接管理員的 <xref:Microsoft.SqlServer.Dts.ManagedConnections.SMTPConn.AcquireConnection%2A> 方法會以下列格式傳回字串：</span><span class="sxs-lookup"><span data-stu-id="0404d-121">The <xref:Microsoft.SqlServer.Dts.ManagedConnections.SMTPConn.AcquireConnection%2A> method of the SMTP connection manager returns a string in the following format:</span></span>

 `SmtpServer=smtphost;UseWindowsAuthentication=False;EnableSsl=False;`

 <span data-ttu-id="0404d-122">您可以使用 `String.Split` 方法，在每個分號 (;) 或是等號 (=) 將此引數清單分隔成個別字串的陣列，然後從陣列中擷取第二個引數 (標註 1) 做為伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="0404d-122">You can use the `String.Split` method to separate this argument list into an array of individual strings at each semicolon (;) or equal sign (=), and then extract the second argument (subscript 1) from the array as the server name.</span></span>

#### <a name="to-configure-this-script-task-example-with-an-smtp-connection-manager"></a><span data-ttu-id="0404d-123">若要使用 SMTP 連接管理員來設定這個指令碼工作範例</span><span class="sxs-lookup"><span data-stu-id="0404d-123">To configure this Script Task example with an SMTP Connection Manager</span></span>

1.  <span data-ttu-id="0404d-124">透過從 **ReadOnlyVariables** 清單中移除 `HtmlEmailServer` 變數，以修改之前設定的指令碼工作。</span><span class="sxs-lookup"><span data-stu-id="0404d-124">Modify the Script task configured earlier by removing the `HtmlEmailServer` variable from the list of **ReadOnlyVariables**.</span></span>

2.  <span data-ttu-id="0404d-125">取代用以取得伺服器名稱的程式碼行：</span><span class="sxs-lookup"><span data-stu-id="0404d-125">Replace the line of code that obtains the server name:</span></span>

    ```
    Dim smtpServer As String = _
      Dts.Variables("HtmlEmailServer").Value.ToString
    ```

     <span data-ttu-id="0404d-126">使用下列這些行：</span><span class="sxs-lookup"><span data-stu-id="0404d-126">with the following lines:</span></span>

    ```
    Dim smtpConnectionString As String = _
      DirectCast(Dts.Connections("SMTP Connection Manager").AcquireConnection(Dts.Transaction), String)
    Dim smtpServer As String = _
      smtpConnectionString.Split(New Char() {"="c, ";"c})(1)
    ```

## <a name="code"></a><span data-ttu-id="0404d-127">程式碼</span><span class="sxs-lookup"><span data-stu-id="0404d-127">Code</span></span>

```vb
Public Sub Main()

  Dim htmlMessageTo As String = _
    Dts.Variables("HtmlEmailTo").Value.ToString
  Dim htmlMessageFrom As String = _
    Dts.Variables("HtmlEmailFrom").Value.ToString
  Dim htmlMessageSubject As String = _
    Dts.Variables("HtmlEmailSubject").Value.ToString
  Dim htmlMessageBody As String = _
    Dts.Variables("HtmlEmailBody").Value.ToString
  Dim smtpServer As String = _
    Dts.Variables("HtmlEmailServer").Value.ToString

  SendMailMessage( _
      htmlMessageTo, htmlMessageFrom, _
      htmlMessageSubject, htmlMessageBody, _
      True, smtpServer)

  Dts.TaskResult = ScriptResults.Success

End Sub

Private Sub SendMailMessage( _
    ByVal SendTo As String, ByVal From As String, _
    ByVal Subject As String, ByVal Body As String, _
    ByVal IsBodyHtml As Boolean, ByVal Server As String)

  Dim htmlMessage As MailMessage
  Dim mySmtpClient As SmtpClient

  htmlMessage = New MailMessage( _
    SendTo, From, Subject, Body)
  htmlMessage.IsBodyHtml = IsBodyHtml

  mySmtpClient = New SmtpClient(Server)
  mySmtpClient.Credentials = CredentialCache.DefaultNetworkCredentials
  mySmtpClient.Send(htmlMessage)

End Sub
```

```csharp
public void Main()
        {

            string htmlMessageTo = Dts.Variables["HtmlEmailTo"].Value.ToString();
            string htmlMessageFrom = Dts.Variables["HtmlEmailFrom"].Value.ToString();
            string htmlMessageSubject = Dts.Variables["HtmlEmailSubject"].Value.ToString();
            string htmlMessageBody = Dts.Variables["HtmlEmailBody"].Value.ToString();
            string smtpServer = Dts.Variables["HtmlEmailServer"].Value.ToString();

            SendMailMessage(htmlMessageTo, htmlMessageFrom, htmlMessageSubject, htmlMessageBody, true, smtpServer);

            Dts.TaskResult = (int)ScriptResults.Success;

        }

        private void SendMailMessage(string SendTo, string From, string Subject, string Body, bool IsBodyHtml, string Server)
        {

            MailMessage htmlMessage;
            SmtpClient mySmtpClient;

            htmlMessage = new MailMessage(SendTo, From, Subject, Body);
            htmlMessage.IsBodyHtml = IsBodyHtml;

            mySmtpClient = new SmtpClient(Server);
            mySmtpClient.Credentials = CredentialCache.DefaultNetworkCredentials;
            mySmtpClient.Send(htmlMessage);

        }
```

<span data-ttu-id="0404d-128">![Integration Services 圖示 (小型) ](../media/dts-16.gif "Integration Services 圖示 (小)")會**保持最**新狀態 Integration Services  </span><span class="sxs-lookup"><span data-stu-id="0404d-128">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="0404d-129">若要取得 Microsoft 的最新下載、文件、範例和影片以及社群中的精選解決方案，請瀏覽 MSDN 上的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 頁面：</span><span class="sxs-lookup"><span data-stu-id="0404d-129">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="0404d-130">瀏覽 MSDN 上的 Integration Services 頁面</span><span class="sxs-lookup"><span data-stu-id="0404d-130">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="0404d-131">若要得到這些更新的自動通知，請訂閱該頁面上所提供的 RSS 摘要。</span><span class="sxs-lookup"><span data-stu-id="0404d-131">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>

## <a name="see-also"></a><span data-ttu-id="0404d-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0404d-132">See Also</span></span>
 [<span data-ttu-id="0404d-133">傳送電子郵件工作</span><span class="sxs-lookup"><span data-stu-id="0404d-133">Send Mail Task</span></span>](../control-flow/send-mail-task.md)


