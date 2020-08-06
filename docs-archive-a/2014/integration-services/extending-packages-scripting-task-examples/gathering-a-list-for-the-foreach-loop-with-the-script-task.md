---
title: 以指令碼工作蒐集 ForEach 迴圈的清單 | Microsoft Docs
ms.custom: ''
ms.date: 08/22/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- Foreach Loop containers
- Script task [Integration Services], Foreach loops
- Script task [Integration Services], examples
- SSIS Script task, Foreach loops
ms.assetid: 694f0462-d0c5-4191-b64e-821b1bdef055
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 039860da121efaa52115bb515b158ea10373e459
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688034"
---
# <a name="gathering-a-list-for-the-foreach-loop-with-the-script-task"></a><span data-ttu-id="d3437-102">以指令碼工作蒐集 ForEach 迴圈的清單</span><span class="sxs-lookup"><span data-stu-id="d3437-102">Gathering a List for the ForEach Loop with the Script Task</span></span>
  <span data-ttu-id="d3437-103">Foreach from Variable 列舉值會透過以變數傳遞給它的清單中之項目來列舉，並針對每個項目執行相同的工作。</span><span class="sxs-lookup"><span data-stu-id="d3437-103">The Foreach from Variable Enumerator enumerates over the items in a list that is passed to it in a variable and performs the same tasks on each item.</span></span> <span data-ttu-id="d3437-104">您可以在指令碼工作中使用自訂程式碼，針對此目的填入清單。</span><span class="sxs-lookup"><span data-stu-id="d3437-104">You can use custom code in a Script task to populate a list for this purpose.</span></span> <span data-ttu-id="d3437-105">如需列舉值的詳細資訊，請參閱 [Foreach 迴圈容器](../control-flow/foreach-loop-container.md)。</span><span class="sxs-lookup"><span data-stu-id="d3437-105">For more information about the enumerator, see [Foreach Loop Container](../control-flow/foreach-loop-container.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d3437-106">如果您想要建立可更輕鬆地在多個封裝之間重複使用的工作，請考慮使用此指令碼工作範例中的程式碼做為自訂工作的起點。</span><span class="sxs-lookup"><span data-stu-id="d3437-106">If you want to create a task that you can more easily reuse across multiple packages, consider using the code in this Script task sample as the starting point for a custom task.</span></span> <span data-ttu-id="d3437-107">如需詳細資訊，請參閱 [開發自訂工作](../extending-packages-custom-objects/task/developing-a-custom-task.md)。</span><span class="sxs-lookup"><span data-stu-id="d3437-107">For more information, see [Developing a Custom Task](../extending-packages-custom-objects/task/developing-a-custom-task.md).</span></span>  
  
## <a name="description"></a><span data-ttu-id="d3437-108">描述</span><span class="sxs-lookup"><span data-stu-id="d3437-108">Description</span></span>  
 <span data-ttu-id="d3437-109">下列範例使用 `System.IO` 命名空間的方法，蒐集電腦上的 Excel 活頁簿清單，這些活頁簿比使用者在變數中所指定的天數還要新或是還要舊。</span><span class="sxs-lookup"><span data-stu-id="d3437-109">The following example uses methods from the `System.IO` namespace to gather a list of Excel workbooks on the computer that are either newer or older than a number of days specified by the user in a variable.</span></span> <span data-ttu-id="d3437-110">它會在磁碟 C 上以遞迴方式搜尋目錄中有 .xls 副檔名的檔案，並檢查檔案最後修改的日期，以判斷檔案是否應歸屬於清單中。</span><span class="sxs-lookup"><span data-stu-id="d3437-110">It searches directories on Drive C recursively for files that have the .xls extension and examines the date on which each file was last modified to determine whether the file belongs in the list.</span></span> <span data-ttu-id="d3437-111">它會將符合的檔案加入 `ArrayList`，並將 `ArrayList` 儲存到變數，以供稍後使用於 Foreach 迴圈容器。</span><span class="sxs-lookup"><span data-stu-id="d3437-111">It adds qualifying files to an `ArrayList` and saves the `ArrayList` to a variable for later use in a Foreach Loop container.</span></span> <span data-ttu-id="d3437-112">Foreach Loop 容器是設定為從 Variable 列舉值使用 Foreach。</span><span class="sxs-lookup"><span data-stu-id="d3437-112">The Foreach Loop container is configured to use the Foreach from Variable enumerator.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d3437-113">從 Variable 列舉值與 Foreach 搭配使用的變數必須是 `Object` 類型。</span><span class="sxs-lookup"><span data-stu-id="d3437-113">The variable that you use with the Foreach from Variable Enumerator must be of type `Object`.</span></span> <span data-ttu-id="d3437-114">您放置在變數中的物件，必須實作下列其中一個介面：`System.Collections.IEnumerable`, `System.Runtime.InteropServices.ComTypes.IEnumVARIANT`、`System.ComponentModel IListSource` 或 `Microsoft.SqlServer.Dts.Runtime.Wrapper.ForEachEnumeratorHost`。</span><span class="sxs-lookup"><span data-stu-id="d3437-114">The object that you place in the variable must implement one of the following interfaces: `System.Collections.IEnumerable`, `System.Runtime.InteropServices.ComTypes.IEnumVARIANT`, `System.ComponentModel IListSource`, or `Microsoft.SqlServer.Dts.Runtime.Wrapper.ForEachEnumeratorHost`.</span></span> <span data-ttu-id="d3437-115">常用的是 `Array` 或 `ArrayList`。</span><span class="sxs-lookup"><span data-stu-id="d3437-115">An `Array` or `ArrayList` is commonly used.</span></span> <span data-ttu-id="d3437-116">`ArrayList` 需要參考以及 `Imports` 命名空間的 `System.Collections` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="d3437-116">The `ArrayList` requires a reference and an `Imports` statement for the `System.Collections` namespace.</span></span>  
  
 <span data-ttu-id="d3437-117">您可以透過為 `FileAge` 封裝變數使用不同的正值與負值，來試驗這項工作。</span><span class="sxs-lookup"><span data-stu-id="d3437-117">You can experiment with this task by using different positive and negative values for the `FileAge` package variable.</span></span> <span data-ttu-id="d3437-118">例如，您可以輸入 5 以搜尋在過去五天內建立的檔案，或是輸入 3 搜尋已建立超過三天的檔案。</span><span class="sxs-lookup"><span data-stu-id="d3437-118">For example, you can enter 5 to search for files created in the last five days, or enter -3 to search for files that were created more than three days ago.</span></span> <span data-ttu-id="d3437-119">這項工作可能需要花費一兩分鐘，以搜尋磁碟機上的許多資料夾。</span><span class="sxs-lookup"><span data-stu-id="d3437-119">This task may take a minute or two on a drive with many folders to search.</span></span>  
  
#### <a name="to-configure-this-script-task-example"></a><span data-ttu-id="d3437-120">設定此指令碼工作範例</span><span class="sxs-lookup"><span data-stu-id="d3437-120">To configure this Script Task example</span></span>  
  
1.  <span data-ttu-id="d3437-121">建立名為 `FileAge` 且類型為整數的封裝孌數，並輸入正整數值或負整數值。</span><span class="sxs-lookup"><span data-stu-id="d3437-121">Create a package variable named `FileAge` of type integer and enter a positive or negative integer value.</span></span> <span data-ttu-id="d3437-122">當值為正數時，程式碼會搜尋比指定天數還要新的檔案，當值為負數時，會搜尋比指定的天數還要舊的檔案。</span><span class="sxs-lookup"><span data-stu-id="d3437-122">When the value is positive, the code searches for files newer than the specified number of days; when negative, for files older than the specified number of days.</span></span>  
  
2.  <span data-ttu-id="d3437-123">建立類型為 `Object` 且名為 `FileList` 的變數，以接收指令碼工作蒐集的檔案清單，以便稍後供 Variable 列舉值的 Foreach 使用。</span><span class="sxs-lookup"><span data-stu-id="d3437-123">Create a package variable named `FileList` of type `Object` to receive the list of files gathered by the Script task for later use by the Foreach from Variable Enumerator.</span></span>  
  
3.  <span data-ttu-id="d3437-124">將 `FileAge` 變數加入指令碼工作的 `ReadOnlyVariables` 屬性，然後將 `FileList` 變數加入 `ReadWriteVariables` 屬性。</span><span class="sxs-lookup"><span data-stu-id="d3437-124">Add the `FileAge` variable to the Script task's `ReadOnlyVariables` property, and add the `FileList` variable to the `ReadWriteVariables` property.</span></span>  
  
4.  <span data-ttu-id="d3437-125">在您的程式碼中，匯入 `System.Collections` 與 `System.IO` 命名空間。</span><span class="sxs-lookup"><span data-stu-id="d3437-125">In your code, import the `System.Collections` and the `System.IO` namespaces.</span></span>  
  
### <a name="code"></a><span data-ttu-id="d3437-126">程式碼</span><span class="sxs-lookup"><span data-stu-id="d3437-126">Code</span></span>  
  
```vb  
Imports System  
Imports System.Data  
Imports System.Math  
Imports Microsoft.SqlServer.Dts.Runtime  
Imports System.Collections  
Imports System.IO  
  
Public Class ScriptMain  
  
  Private Const FILE_AGE As Integer = -50  
  
  Private Const FILE_ROOT As String = "C:\"  
  Private Const FILE_FILTER As String = "*.xls"  
  
  Private isCheckForNewer As Boolean = True  
  Dim fileAgeLimit As Integer  
  Private listForEnumerator As ArrayList  
  
  Public Sub Main()  
  
    fileAgeLimit = DirectCast(Dts.Variables("FileAge").Value, Integer)  
  
    ' If value provided is positive, we want files NEWER THAN n days.  
    '  If negative, we want files OLDER THAN n days.  
    If fileAgeLimit < 0 Then  
      isCheckForNewer = False  
    End If  
    ' Extract number of days as positive integer.  
    fileAgeLimit = Math.Abs(fileAgeLimit)  
  
    listForEnumerator = New ArrayList  
  
    GetFilesInFolder(FILE_ROOT)  
  
    ' Return the list of files to the variable  
    '  for later use by the Foreach from Variable enumerator.  
    System.Windows.Forms.MessageBox.Show("Matching files: " & listForEnumerator.Count.ToString, "Results", Windows.Forms.MessageBoxButtons.OK, Windows.Forms.MessageBoxIcon.Information)  
    Dts.Variables("FileList").Value = listForEnumerator  
  
    Dts.TaskResult = ScriptResults.Success  
  
  End Sub  
  
  Private Sub GetFilesInFolder(ByVal folderPath As String)  
  
    Dim localFiles() As String  
    Dim localFile As String  
    Dim fileChangeDate As Date  
    Dim fileAge As TimeSpan  
    Dim fileAgeInDays As Integer  
    Dim childFolder As String  
  
    Try  
      localFiles = Directory.GetFiles(folderPath, FILE_FILTER)  
      For Each localFile In localFiles  
        fileChangeDate = File.GetLastWriteTime(localFile)  
        fileAge = DateTime.Now.Subtract(fileChangeDate)  
        fileAgeInDays = fileAge.Days  
        CheckAgeOfFile(localFile, fileAgeInDays)  
      Next  
  
      If Directory.GetDirectories(folderPath).Length > 0 Then  
        For Each childFolder In Directory.GetDirectories(folderPath)  
          GetFilesInFolder(childFolder)  
        Next  
      End If  
  
    Catch  
      ' Ignore exceptions on special folders such as System Volume Information.  
    End Try  
  
  End Sub  
  
  Private Sub CheckAgeOfFile(ByVal localFile As String, ByVal fileAgeInDays As Integer)  
  
    If isCheckForNewer Then  
      If fileAgeInDays <= fileAgeLimit Then  
        listForEnumerator.Add(localFile)  
      End If  
    Else  
      If fileAgeInDays > fileAgeLimit Then  
        listForEnumerator.Add(localFile)  
      End If  
    End If  
  
  End Sub  
  
End Class  
```  
  
```csharp  
using System;  
using System.Data;  
using System.Math;  
using Microsoft.SqlServer.Dts.Runtime;  
using System.Collections;  
using System.IO;  
  
public partial class ScriptMain : Microsoft.SqlServer.Dts.Tasks.ScriptTask.VSTARTScriptObjectModelBase  
    {  
  
        private const int FILE_AGE = -50;  
  
        private const string FILE_ROOT = "C:\\";  
        private const string FILE_FILTER = "*.xls";  
  
        private bool isCheckForNewer = true;  
        int fileAgeLimit;  
        private ArrayList listForEnumerator;  
  
        public void Main()  
  {  
  
    fileAgeLimit = (int)(Dts.Variables["FileAge"].Value);  
  
    // If value provided is positive, we want files NEWER THAN n days.  
    // If negative, we want files OLDER THAN n days.  
    if (fileAgeLimit<0)  
    {  
      isCheckForNewer = false;  
    }  
    // Extract number of days as positive integer.  
    fileAgeLimit = Math.Abs(fileAgeLimit);  
  
    ArrayList listForEnumerator = new ArrayList();  
  
    GetFilesInFolder(FILE_ROOT);  
  
    // Return the list of files to the variable  
    // for later use by the Foreach from Variable enumerator.  
    System.Windows.Forms.MessageBox.Show("Matching files: "+ listForEnumerator.Count, "Results",   
MessageBoxButtons.OK, MessageBoxIcon.Information);  
    Dts.Variables["FileList"].Value = listForEnumerator;  
  
    Dts.TaskResult = (int)ScriptResults.Success;  
  
  }  
  
        private void GetFilesInFolder(string folderPath)  
        {  
  
            string[] localFiles;  
            DateTime fileChangeDate;  
            TimeSpan fileAge;  
            int fileAgeInDays;  
  
            try  
            {  
                localFiles = Directory.GetFiles(folderPath, FILE_FILTER);  
                foreach (string localFile in localFiles)  
                {  
                    fileChangeDate = File.GetLastWriteTime(localFile);  
                    fileAge = DateTime.Now.Subtract(fileChangeDate);  
                    fileAgeInDays = fileAge.Days;  
                    CheckAgeOfFile(localFile, fileAgeInDays);  
                }  
  
                if (Directory.GetDirectories(folderPath).Length > 0)  
                {  
                    foreach (string childFolder in Directory.GetDirectories(folderPath))  
                    {  
                        GetFilesInFolder(childFolder);  
                    }  
                }  
  
            }  
            catch  
            {  
                // Ignore exceptions on special folders, such as System Volume Information.  
            }  
  
        }  
  
        private void CheckAgeOfFile(string localFile, int fileAgeInDays)  
        {  
  
            if (isCheckForNewer)  
            {  
                if (fileAgeInDays <= fileAgeLimit)  
                {  
                    listForEnumerator.Add(localFile);  
                }  
            }  
            else  
            {  
                if (fileAgeInDays > fileAgeLimit)  
                {  
                    listForEnumerator.Add(localFile);  
                }  
            }  
  
        }  
  
    }  
```  
  
<span data-ttu-id="d3437-127">![Integration Services 圖示 (小型) ](../media/dts-16.gif "Integration Services 圖示 (小)")會**保持最**新狀態 Integration Services  </span><span class="sxs-lookup"><span data-stu-id="d3437-127">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="d3437-128">若要取得 Microsoft 的最新下載、文件、範例和影片以及社群中的精選解決方案，請瀏覽 MSDN 上的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 頁面：</span><span class="sxs-lookup"><span data-stu-id="d3437-128">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="d3437-129">瀏覽 MSDN 上的 Integration Services 頁面</span><span class="sxs-lookup"><span data-stu-id="d3437-129">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="d3437-130">若要得到這些更新的自動通知，請訂閱該頁面上所提供的 RSS 摘要。</span><span class="sxs-lookup"><span data-stu-id="d3437-130">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3437-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d3437-131">See Also</span></span>  
 <span data-ttu-id="d3437-132">[Foreach 迴圈容器](../control-flow/foreach-loop-container.md) </span><span class="sxs-lookup"><span data-stu-id="d3437-132">[Foreach Loop Container](../control-flow/foreach-loop-container.md) </span></span>  
 [<span data-ttu-id="d3437-133">設定 Foreach 迴圈容器</span><span class="sxs-lookup"><span data-stu-id="d3437-133">Configure a Foreach Loop Container</span></span>](../configure-a-foreach-loop-container.md)  
  
  
