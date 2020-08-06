---
title: 以指令碼工作查詢 Active Directory| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- Script task [Integration Services], Active Directory access
- SSIS Script task, Active Directory access
- Script task [Integration Services], examples
- Active Directory [Integration Services]
ms.assetid: a88fefbb-9ea2-4a86-b836-e71315bac68e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 624aa56289b9cab9174882b586a37e5d0de7ca9d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592167"
---
# <a name="querying-the-active-directory-with-the-script-task"></a><span data-ttu-id="c41bd-102">以指令碼工作查詢 Active Directory</span><span class="sxs-lookup"><span data-stu-id="c41bd-102">Querying the Active Directory with the Script Task</span></span>
  <span data-ttu-id="c41bd-103">企業資料處理應用程式 (例如 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 封裝) 通常需要根據儲存在 Active Directory 中的職等、工作職稱或是員工的其他特色，以不同的方式處理資料。</span><span class="sxs-lookup"><span data-stu-id="c41bd-103">Enterprise data processing applications, such as [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages, often need to process data differently based on the rank, job title, or other characteristics of employees stored in Active Directory.</span></span> <span data-ttu-id="c41bd-104">Active Directory 是一種 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 目錄服務，可集中儲存中繼資料，這些資料不僅有關使用者，而且還有關電腦與印表機等其他組織資產。</span><span class="sxs-lookup"><span data-stu-id="c41bd-104">Active Directory is a [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows directory service that provides a centralized store of metadata, not only about users, but also about other organizational assets such as computers and printers.</span></span> <span data-ttu-id="c41bd-105">在 Microsoft .NET Framework 中的 `System.DirectoryServices` 命名空間提供使用 Active Directory 的類別，以協助您根據它所儲存的資訊來指示資料處理工作流程。</span><span class="sxs-lookup"><span data-stu-id="c41bd-105">The `System.DirectoryServices` namespace in the Microsoft .NET Framework provides classes for working with Active Directory, to help you direct data processing workflow based on the information that it stores.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c41bd-106">如果您想要建立可更輕鬆地在多個封裝之間重複使用的工作，請考慮使用此指令碼工作範例中的程式碼做為自訂工作的起點。</span><span class="sxs-lookup"><span data-stu-id="c41bd-106">If you want to create a task that you can more easily reuse across multiple packages, consider using the code in this Script task sample as the starting point for a custom task.</span></span> <span data-ttu-id="c41bd-107">如需詳細資訊，請參閱 [開發自訂工作](../extending-packages-custom-objects/task/developing-a-custom-task.md)。</span><span class="sxs-lookup"><span data-stu-id="c41bd-107">For more information, see [Developing a Custom Task](../extending-packages-custom-objects/task/developing-a-custom-task.md).</span></span>  
  
## <a name="description"></a><span data-ttu-id="c41bd-108">描述</span><span class="sxs-lookup"><span data-stu-id="c41bd-108">Description</span></span>  
 <span data-ttu-id="c41bd-109">下列範例根據 `email` 變數值 (包含員工的電子郵件地址)，從 Active Directory 擷取員工的姓名、職稱與電話號碼。</span><span class="sxs-lookup"><span data-stu-id="c41bd-109">The following example retrieves an employee's name, title, and phone number from Active Directory based on the value of the `email` variable, which contains the e-mail address of the employee.</span></span> <span data-ttu-id="c41bd-110">封裝中的優先順序條件約束可以使用擷取的資訊來判斷，例如，根據員工的工作職稱，來判斷要傳送低優先順序的電子郵件訊息或是高優先順序的頁面。</span><span class="sxs-lookup"><span data-stu-id="c41bd-110">Precedence constraints in the package can use the retrieved information to determine, for example, whether to send a low-priority e-mail message or a high-priority page, based on the job title of the employee.</span></span>  
  
#### <a name="to-configure-this-script-task-example"></a><span data-ttu-id="c41bd-111">設定此指令碼工作範例</span><span class="sxs-lookup"><span data-stu-id="c41bd-111">To configure this Script Task example</span></span>  
  
1.  <span data-ttu-id="c41bd-112">建立三個字串變數 `email`、`name` 和 `title`。</span><span class="sxs-lookup"><span data-stu-id="c41bd-112">Create the three string variables `email`, `name`, and `title`.</span></span> <span data-ttu-id="c41bd-113">輸入有效的公司電子郵件地址做為 `email` 變數值。</span><span class="sxs-lookup"><span data-stu-id="c41bd-113">Enter a valid corporate email address as the value of the `email` variable.</span></span>  
  
2.  <span data-ttu-id="c41bd-114">在 [**腳本工作編輯器**] 的 [**腳本**] 頁面上，將 `email` 變數加入至 `ReadOnlyVariables` 屬性。</span><span class="sxs-lookup"><span data-stu-id="c41bd-114">On the **Script** page of the **Script Task Editor**, add the `email` variable to the `ReadOnlyVariables` property.</span></span>  
  
3.  <span data-ttu-id="c41bd-115">將 `name` 與 `title` 變數加入 `ReadWriteVariables` 屬性。</span><span class="sxs-lookup"><span data-stu-id="c41bd-115">Add the `name` and `title` variables to the `ReadWriteVariables` property.</span></span>  
  
4.  <span data-ttu-id="c41bd-116">在指令碼專案中，加入 `System.DirectoryServices` 命名空間的參考。</span><span class="sxs-lookup"><span data-stu-id="c41bd-116">In the script project, add a reference to the `System.DirectoryServices` namespace.</span></span>  
  
5.  <span data-ttu-id="c41bd-117">。</span><span class="sxs-lookup"><span data-stu-id="c41bd-117">.</span></span> <span data-ttu-id="c41bd-118">在您的程式碼中，使用 `Imports` 陳述式匯入 `DirectoryServices` 命名空間。</span><span class="sxs-lookup"><span data-stu-id="c41bd-118">In your code, use an `Imports` statement to import the `DirectoryServices` namespace.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c41bd-119">若要順利執行這個指令碼，您的公司必須在其網路上使用 Active Directory，並儲存這個範例所使用的員工資訊。</span><span class="sxs-lookup"><span data-stu-id="c41bd-119">To run this script successfully, your company must be using Active Directory on its network and storing the employee information that this example uses.</span></span>  
  
### <a name="code"></a><span data-ttu-id="c41bd-120">程式碼</span><span class="sxs-lookup"><span data-stu-id="c41bd-120">Code</span></span>  
  
```vb  
Public Sub Main()  
  
    Dim directory As DirectoryServices.DirectorySearcher  
    Dim result As DirectoryServices.SearchResult  
    Dim email As String  
  
    email = Dts.Variables("email").Value.ToString  
  
    Try  
        directory = New _  
            DirectoryServices.DirectorySearcher("(mail=" & email & ")")  
        result = directory.FindOne  
        Dts.Variables("name").Value = _  
            result.Properties("displayname").ToString  
        Dts.Variables("title").Value = _  
            result.Properties("title").ToString  
        Dts.TaskResult = ScriptResults.Success  
    Catch ex As Exception  
        Dts.Events.FireError(0, _  
            "Script Task Example", _  
            ex.Message & ControlChars.CrLf & ex.StackTrace, _  
            String.Empty, 0)  
        Dts.TaskResult = ScriptResults.Failure  
    End Try  
  
End Sub  
```  
  
```csharp  
public void Main()  
{  
    //  
    DirectorySearcher directory;  
    SearchResult result;  
    string email;  
  
    email = (string)Dts.Variables["email"].Value;  
  
    try  
    {  
        directory = new DirectorySearcher("(mail=" + email + ")");  
        result = directory.FindOne();  
        Dts.Variables["name"].Value = result.Properties["displayname"].ToString();  
        Dts.Variables["title"].Value = result.Properties["title"].ToString();  
        Dts.TaskResult = (int)ScriptResults.Success;  
    }  
    catch (Exception ex)  
    {  
        Dts.Events.FireError(0, "Script Task Example", ex.Message + "\n" + ex.StackTrace, String.Empty, 0);  
        Dts.TaskResult = (int)ScriptResults.Failure;  
    }  
  
}  
```  
  
## <a name="external-resources"></a><span data-ttu-id="c41bd-121">外部資源</span><span class="sxs-lookup"><span data-stu-id="c41bd-121">External Resources</span></span>  
  
-   <span data-ttu-id="c41bd-122">social.technet.microsoft.com 上的技術文件：[Processing Active Directory Information in SSIS](https://go.microsoft.com/fwlink/?LinkId=199588) (在 SSIS 中處理 Active Directory 資訊)</span><span class="sxs-lookup"><span data-stu-id="c41bd-122">Technical article, [Processing Active Directory Information in SSIS](https://go.microsoft.com/fwlink/?LinkId=199588), on social.technet.microsoft.com</span></span>  
  
<span data-ttu-id="c41bd-123">![Integration Services 圖示 (小型) ](../media/dts-16.gif "Integration Services 圖示 (小)")會**保持最**新狀態 Integration Services  </span><span class="sxs-lookup"><span data-stu-id="c41bd-123">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="c41bd-124">若要取得 Microsoft 的最新下載、文件、範例和影片以及社群中的精選解決方案，請瀏覽 MSDN 上的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 頁面：</span><span class="sxs-lookup"><span data-stu-id="c41bd-124">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="c41bd-125">瀏覽 MSDN 上的 Integration Services 頁面</span><span class="sxs-lookup"><span data-stu-id="c41bd-125">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="c41bd-126">若要得到這些更新的自動通知，請訂閱該頁面上所提供的 RSS 摘要。</span><span class="sxs-lookup"><span data-stu-id="c41bd-126">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
  
