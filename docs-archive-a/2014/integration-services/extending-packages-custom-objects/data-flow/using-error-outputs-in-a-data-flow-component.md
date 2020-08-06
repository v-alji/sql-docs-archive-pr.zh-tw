---
title: 在資料流程元件中使用錯誤輸出 | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- errors [Integration Services], alternative outputs
- synchronous error outputs [Integration Services]
- alternative error outputs [Integration Services]
- custom data flow components [Integration Services], error outputs
- data flow components [Integration Services], error outputs
- populating error columns [Integration Services]
- redirecting error output [Integration Services]
- error outputs [Integration Services]
- asynchronous error outputs [Integration Services]
ms.assetid: a2a3e7c8-1de2-45b3-97fb-60415d3b0934
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a05a41065c52fadbe7f7fc065771727310e58149
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584645"
---
# <a name="using-error-outputs-in-a-data-flow-component"></a><span data-ttu-id="8081c-102">使用資料流程元件中的錯誤輸出</span><span class="sxs-lookup"><span data-stu-id="8081c-102">Using Error Outputs in a Data Flow Component</span></span>
  <span data-ttu-id="8081c-103">您可以將呼叫錯誤輸出的特殊 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100> 物件加入元件，讓元件將無法在執行期間處理的資料列重新導向。</span><span class="sxs-lookup"><span data-stu-id="8081c-103">Special <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100> objects called error outputs can be added to components to let the component redirect rows that it cannot process during execution.</span></span> <span data-ttu-id="8081c-104">元件可能遇到的問題通常會歸類為錯誤或是截斷，而且是每個元件特有的。</span><span class="sxs-lookup"><span data-stu-id="8081c-104">The problems a component may encounter are generally categorized as errors or truncations, and are specific to each component.</span></span> <span data-ttu-id="8081c-105">提供錯誤輸出的元件透過從結果集篩選出錯誤資料列、當問題發生時讓元件失敗，以及忽略錯誤並繼續，讓元件的使用者有處理錯誤狀況的彈性。</span><span class="sxs-lookup"><span data-stu-id="8081c-105">Components that provide error outputs give users of the component the flexibility to handle error conditions by filtering error rows out of the result set, by failing the component when a problem occurs, or by ignoring errors and continuing.</span></span>  
  
 <span data-ttu-id="8081c-106">若要實作和支援元件中的錯誤輸出，您必須先將元件的 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.UsesDispositions%2A> 屬性設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="8081c-106">To implement and support error outputs in a component, you must first set the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.UsesDispositions%2A> property of the component to `true`.</span></span> <span data-ttu-id="8081c-107">接著您必須將輸出加入其 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100.IsErrorOut%2A> 屬性設定為 `true`的元件。</span><span class="sxs-lookup"><span data-stu-id="8081c-107">Then you must add an output to the component that has its <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100.IsErrorOut%2A> property set to `true`.</span></span> <span data-ttu-id="8081c-108">最後，元件必須包含錯誤或截斷發生時會將資料列導向錯誤輸出的程式碼。</span><span class="sxs-lookup"><span data-stu-id="8081c-108">Finally, the component must contain code that redirects rows to the error output when errors or truncations occur.</span></span> <span data-ttu-id="8081c-109">本主題涵蓋這三個步驟並說明同步與非同步錯誤輸出之間的差異。</span><span class="sxs-lookup"><span data-stu-id="8081c-109">This topic covers these three steps and explains the differences between synchronous and asynchronous error outputs.</span></span>  
  
## <a name="creating-an-error-output"></a><span data-ttu-id="8081c-110">建立錯誤輸出</span><span class="sxs-lookup"><span data-stu-id="8081c-110">Creating an Error Output</span></span>  
 <span data-ttu-id="8081c-111">您可以呼叫 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputCollection100.New%2A> 的 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.OutputCollection%2A> 方法，然後將新輸出的 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100.IsErrorOut%2A> 屬性設定為 `true`，以建立錯誤輸出。</span><span class="sxs-lookup"><span data-stu-id="8081c-111">You create an error output by calling the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputCollection100.New%2A> method of the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.OutputCollection%2A>, and then setting the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100.IsErrorOut%2A> property of the new output to `true`.</span></span> <span data-ttu-id="8081c-112">如果輸出是非同步，則不需要對輸出再執行任何動作。</span><span class="sxs-lookup"><span data-stu-id="8081c-112">If the output is asynchronous, nothing else must be done to the output.</span></span> <span data-ttu-id="8081c-113">如果輸出是同步的，而且對同一個輸入而言有另一個同步的輸出，則也必須設定 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100.ExclusionGroup%2A> 與 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100.SynchronousInputID%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="8081c-113">If the output is synchronous, and there is another output that is synchronous to the same input, you must also set the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100.ExclusionGroup%2A> and <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100.SynchronousInputID%2A> properties.</span></span> <span data-ttu-id="8081c-114">對同一個輸入而言屬同步的兩個輸出間，這兩個屬性值必須相同。</span><span class="sxs-lookup"><span data-stu-id="8081c-114">Both properties should have the same values as the other output that is synchronous to the same input.</span></span> <span data-ttu-id="8081c-115">如果這些屬性不是設定成非零的值，輸入所提供的資料列會傳送至對輸入同步的兩個輸出。</span><span class="sxs-lookup"><span data-stu-id="8081c-115">If these properties are not set to a non-zero value, the rows provided by the input are sent to both outputs that are synchronous to the input.</span></span>  
  
 <span data-ttu-id="8081c-116">當元件在執行期間遇到錯誤或是截斷，它會根據發生錯誤之輸入或輸出，或是輸入或輸出資料行的 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSInput100.ErrorRowDisposition%2A> 與 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSInput100.TruncationRowDisposition%2A> 屬性的設定繼續。</span><span class="sxs-lookup"><span data-stu-id="8081c-116">When a component encounters an error or truncation during execution, it proceeds based on the settings of the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSInput100.ErrorRowDisposition%2A> and <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSInput100.TruncationRowDisposition%2A> properties of the input or output, or input or output column, where the error occurred.</span></span> <span data-ttu-id="8081c-117">這些屬性值預設應該設定為 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSRowDisposition.RD_NotUsed>。</span><span class="sxs-lookup"><span data-stu-id="8081c-117">The value of these properties should be set by default to <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSRowDisposition.RD_NotUsed>.</span></span> <span data-ttu-id="8081c-118">當元件的錯誤輸出連接到下游元件時，會由元件的使用者設定這個屬性，並讓使用者控制元件處理錯誤或截斷的方式。</span><span class="sxs-lookup"><span data-stu-id="8081c-118">When the error output of the component is connected to a downstream component, this property is set by the user of the component and lets the user control how the component handles the error or truncation.</span></span>  
  
## <a name="populating-error-columns"></a><span data-ttu-id="8081c-119">擴展錯誤資料行</span><span class="sxs-lookup"><span data-stu-id="8081c-119">Populating Error Columns</span></span>  
 <span data-ttu-id="8081c-120">在建立錯誤輸出時，資料流程工作會自動將兩個資料行加入輸出資料行集合。</span><span class="sxs-lookup"><span data-stu-id="8081c-120">When an error output is created, the data flow task automatically adds two columns to the output column collection.</span></span> <span data-ttu-id="8081c-121">元件使用這些資料行來指定造成錯誤或是截斷的資料行識別碼，並提供元件特定的錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="8081c-121">These columns are used by components to specify the ID of the column that caused the error or truncation, and to provide the component-specific error code.</span></span> <span data-ttu-id="8081c-122">這些資料行是自動產生，但是資料行中所含的值必須由元件設定。</span><span class="sxs-lookup"><span data-stu-id="8081c-122">These columns are generated automatically, but the values contained in the columns must be set by the component.</span></span>  
  
 <span data-ttu-id="8081c-123">用以設定這些資料行值的方法，須視錯誤輸出是同步或非同步而定。</span><span class="sxs-lookup"><span data-stu-id="8081c-123">The method used to set the values of these columns depends on whether the error output is synchronous or asynchronous.</span></span> <span data-ttu-id="8081c-124">有同步輸出的元件會呼叫 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.DirectErrorRow%2A> 方法 (將在下一節做更詳細的討論)，並以參數方式提供錯誤碼與錯誤資料行值。</span><span class="sxs-lookup"><span data-stu-id="8081c-124">Components with synchronous outputs call the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.DirectErrorRow%2A> method, discussed in more detail in the next section, and provide the error code and error column values as parameters.</span></span> <span data-ttu-id="8081c-125">具有非同步輸出的元件有兩個設定這些資料行值的選擇。</span><span class="sxs-lookup"><span data-stu-id="8081c-125">Components with asynchronous outputs have two choices for setting the values of these columns.</span></span> <span data-ttu-id="8081c-126">它們可以呼叫輸出緩衝區的 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetErrorInfo%2A> 方法並提供值，或是透過使用 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSBufferManager100.FindColumnByLineageID%2A> 來找出緩衝區中的錯誤資料行，並直接為資料行設定值。</span><span class="sxs-lookup"><span data-stu-id="8081c-126">They can either call the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetErrorInfo%2A> method of the output buffer and supply the values, or locate the error columns in the buffer by using <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSBufferManager100.FindColumnByLineageID%2A> and set the values for the columns directly.</span></span> <span data-ttu-id="8081c-127">不過，因為資料行名稱可能已經變更，或是其在輸出資料行集合中的位置可能已經修改，第二個方法可能不可靠。</span><span class="sxs-lookup"><span data-stu-id="8081c-127">However, because the names of the columns may have been changed, or their location in the output column collection may have been modified, the latter method may not be reliable.</span></span> <span data-ttu-id="8081c-128"><xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetErrorInfo%2A> 方法會自動在這些錯誤資料行中設定值，而不必手動尋找它們。</span><span class="sxs-lookup"><span data-stu-id="8081c-128">The <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetErrorInfo%2A> method automatically sets the values in these error columns without having to locate them manually.</span></span>  
  
 <span data-ttu-id="8081c-129">如果您需要取得對應至特定錯誤碼的錯誤描述，可以使用 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.GetErrorDescription%2A> 介面 (透過元件的<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> 屬性取得) 的 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ComponentMetaData%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="8081c-129">If you need to obtain the error description that corresponds to a specific error code, you can use the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.GetErrorDescription%2A> method of the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> interface, available through the component's <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ComponentMetaData%2A> property.</span></span>  
  
 <span data-ttu-id="8081c-130">下列程式碼範例顯示具有一個輸入與兩個輸出的元件，包括錯誤輸出。</span><span class="sxs-lookup"><span data-stu-id="8081c-130">The following code examples show a component that has an input and two outputs, including an error output.</span></span> <span data-ttu-id="8081c-131">第一個範例顯示如何建立與輸入同步的錯誤輸出。</span><span class="sxs-lookup"><span data-stu-id="8081c-131">The first example shows how to create an error output that is synchronous to the input.</span></span> <span data-ttu-id="8081c-132">第二個範例顯示如何建立非同步的錯誤輸出。</span><span class="sxs-lookup"><span data-stu-id="8081c-132">The second example shows how to create an error output that is asynchronous.</span></span>  
  
```csharp  
public override void ProvideComponentProperties()  
{  
    // Specify that the component has an error output.  
    ComponentMetaData.UsesDispositions = true;  
    // Create the input.  
    IDTSInput100 input = ComponentMetaData.InputCollection.New();  
    input.Name = "Input";  
    input.ErrorRowDisposition = DTSRowDisposition.RD_NotUsed;  
    input.ErrorOrTruncationOperation = "A string describing the possible error or truncation that may occur during execution.";  
  
    // Create the default output.  
    IDTSOutput100 output = ComponentMetaData.OutputCollection.New();  
    output.Name = "Output";  
    output.SynchronousInputID = input.ID;  
    output.ExclusionGroup = 1;  
  
    // Create the error output.  
    IDTSOutput100 errorOutput = ComponentMetaData.OutputCollection.New();  
    errorOutput.IsErrorOut = true;  
    errorOutput.Name = "ErrorOutput";  
    errorOutput.SynchronousInputID = input.ID;  
    errorOutput.ExclusionGroup = 1;  
  
}  
```  
  
```vb  
Public  Overrides Sub ProvideComponentProperties()   
  
 ' Specify that the component has an error output.  
 ComponentMetaData.UsesDispositions = True   
  
 Dim input As IDTSInput100 = ComponentMetaData.InputCollection.New   
  
 ' Create the input.  
 input.Name = "Input"   
 input.ErrorRowDisposition = DTSRowDisposition.RD_NotUsed   
 input.ErrorOrTruncationOperation = "A string describing the possible error or truncation that may occur during execution."   
  
 ' Create the default output.  
 Dim output As IDTSOutput100 = ComponentMetaData.OutputCollection.New   
 output.Name = "Output"   
 output.SynchronousInputID = input.ID   
 output.ExclusionGroup = 1   
  
 ' Create the error output.  
 Dim errorOutput As IDTSOutput100 = ComponentMetaData.OutputCollection.New   
 errorOutput.IsErrorOut = True   
 errorOutput.Name = "ErrorOutput"   
 errorOutput.SynchronousInputID = input.ID   
 errorOutput.ExclusionGroup = 1   
  
End Sub  
```  
  
 <span data-ttu-id="8081c-133">下列程式碼範例會建立非同步的錯誤輸出。</span><span class="sxs-lookup"><span data-stu-id="8081c-133">The following code example creates an error output that is asynchronous.</span></span>  
  
```csharp  
public override void ProvideComponentProperties()  
{  
    // Specify that the component has an error output.  
    ComponentMetaData.UsesDispositions = true;  
  
    // Create the input.  
    IDTSInput100 input = ComponentMetaData.InputCollection.New();  
    input.Name = "Input";  
    input.ErrorRowDisposition = DTSRowDisposition.RD_NotUsed;  
    input.ErrorOrTruncationOperation = "A string describing the possible error or truncation that may occur during execution.";  
  
    // Create the default output.  
    IDTSOutput100 output = ComponentMetaData.OutputCollection.New();  
    output.Name = "Output";  
  
    // Create the error output.  
    IDTSOutput100 errorOutput = ComponentMetaData.OutputCollection.New();  
    errorOutput.Name = "ErrorOutput";  
    errorOutput.IsErrorOut = true;  
}  
```  
  
```vb  
Public  Overrides Sub ProvideComponentProperties()   
  
 ' Specify that the component has an error output.  
 ComponentMetaData.UsesDispositions = True   
  
 ' Create the input.  
 Dim input As IDTSInput100 = ComponentMetaData.InputCollection.New   
  
 ' Create the default output.  
 input.Name = "Input"   
 input.ErrorRowDisposition = DTSRowDisposition.RD_NotUsed   
 input.ErrorOrTruncationOperation = "A string describing the possible error or truncation that may occur during execution."   
  
 ' Create the error output.  
 Dim output As IDTSOutput100 = ComponentMetaData.OutputCollection.New   
 output.Name = "Output"   
 Dim errorOutput As IDTSOutput100 = ComponentMetaData.OutputCollection.New   
 errorOutput.Name = "ErrorOutput"   
 errorOutput.IsErrorOut = True   
  
End Sub  
```  
  
## <a name="redirecting-a-row-to-an-error-output"></a><span data-ttu-id="8081c-134">將資料列重新導向至錯誤輸出</span><span class="sxs-lookup"><span data-stu-id="8081c-134">Redirecting a Row to an Error Output</span></span>  
 <span data-ttu-id="8081c-135">在將錯誤輸出加入元件之後，您必須提供程式碼以處理元件特定的錯誤或是截斷狀況，並將錯誤或是截斷資料列重新導向至錯誤輸出。</span><span class="sxs-lookup"><span data-stu-id="8081c-135">After adding an error output to a component, you must provide code that handles the error or truncation conditions specific to the component and redirects the error or truncation rows to the error output.</span></span> <span data-ttu-id="8081c-136">您可以用這兩種方式來執行這項動作，端視錯誤輸出是同步或非同步而定。</span><span class="sxs-lookup"><span data-stu-id="8081c-136">You can do this in two ways, depending on whether the error output is synchronous or asynchronous.</span></span>  
  
### <a name="redirecting-a-row-with-synchronous-outputs"></a><span data-ttu-id="8081c-137">重新導向具有同步輸出的資料列</span><span class="sxs-lookup"><span data-stu-id="8081c-137">Redirecting a Row with Synchronous Outputs</span></span>  
 <span data-ttu-id="8081c-138">透過呼叫 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.DirectErrorRow%2A> 類別的 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer> 方法，將資料列傳送到同步輸出。</span><span class="sxs-lookup"><span data-stu-id="8081c-138">Rows are sent to synchronous outputs by calling the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.DirectErrorRow%2A> method of the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer> class.</span></span> <span data-ttu-id="8081c-139">這個方法呼叫包括以參數傳遞錯誤輸出的識別碼、元件定義的錯誤碼以及元件無法處理之資料行的索引。</span><span class="sxs-lookup"><span data-stu-id="8081c-139">The method call includes as parameters the ID of the error output, the component-defined error code, and the index of the column that the component was unable to process.</span></span>  
  
 <span data-ttu-id="8081c-140">下列程式碼範例示範如何使用 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.DirectErrorRow%2A> 方法，將緩衝區中的資料列導向至同步錯誤輸出。</span><span class="sxs-lookup"><span data-stu-id="8081c-140">The following code example demonstrates how to direct a row in a buffer to a synchronous error output using the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.DirectErrorRow%2A> method.</span></span>  
  
```csharp  
public override void ProcessInput(int inputID, PipelineBuffer buffer)  
{  
        IDTSInput100 input = ComponentMetaData.InputCollection.GetObjectByID(inputID);  
  
        // This code sample assumes the component has two outputs, one the default,  
        // the other the error output. If the errorOutputIndex returned from GetErrorOutputInfo  
        // is 0, then the default output is the second output in the collection.  
        int defaultOutputID = -1;  
        int errorOutputID = -1;  
        int errorOutputIndex = -1;  
  
        GetErrorOutputInfo(ref errorOutputID,ref errorOutputIndex);  
  
        if (errorOutputIndex == 0)  
            defaultOutputID = ComponentMetaData.OutputCollection[1].ID;  
        else  
            defaultOutputID = ComponentMetaData.OutputCollection[0].ID;  
  
        while (buffer.NextRow())  
        {  
            try  
            {  
                // TODO: Implement code to process the columns in the buffer row.  
  
                // Ideally, your code should detect potential exceptions before they occur, rather  
                // than having a generic try/catch block such as this.   
                // However, because the error or truncation implementation is specific to each component,  
                // this sample focuses on actually directing the row, and not a single error or truncation.  
  
                // Unless an exception occurs, direct the row to the default   
                buffer.DirectRow(defaultOutputID);  
            }  
            catch  
            {  
                // Yes, has the user specified to redirect the row?  
                if (input.ErrorRowDisposition == DTSRowDisposition.RD_RedirectRow)  
                {  
                    // Yes, direct the row to the error output.  
                    // TODO: Add code to include the errorColumnIndex.  
                    buffer.DirectErrorRow(errorOutputID, 0, errorColumnIndex);  
                }  
                else if (input.ErrorRowDisposition == DTSRowDisposition.RD_FailComponent || input.ErrorRowDisposition == DTSRowDisposition.RD_NotUsed)  
                {  
                    // No, the user specified to fail the component, or the error row disposition was not set.  
                    throw new Exception("An error occurred, and the DTSRowDisposition is either not set, or is set to fail component.");  
                }  
                else  
                {  
                    // No, the user specified to ignore the failure so   
                    // direct the row to the default output.  
                    buffer.DirectRow(defaultOutputID);  
                }  
  
            }  
        }  
}  
```  
  
```vb  
Public  Overrides Sub ProcessInput(ByVal inputID As Integer, ByVal buffer As PipelineBuffer)   
   Dim input As IDTSInput100 = ComponentMetaData.InputCollection.GetObjectByID(inputID)   
  
   ' This code sample assumes the component has two outputs, one the default,  
   ' the other the error output. If the errorOutputIndex returned from GetErrorOutputInfo  
   ' is 0, then the default output is the second output in the collection.  
   Dim defaultOutputID As Integer = -1   
   Dim errorOutputID As Integer = -1   
   Dim errorOutputIndex As Integer = -1   
  
   GetErrorOutputInfo(errorOutputID, errorOutputIndex)   
  
   If errorOutputIndex = 0 Then   
     defaultOutputID = ComponentMetaData.OutputCollection(1).ID   
   Else   
     defaultOutputID = ComponentMetaData.OutputCollection(0).ID   
   End If   
  
   While buffer.NextRow   
     Try   
       ' TODO: Implement code to process the columns in the buffer row.  
  
       ' Ideally, your code should detect potential exceptions before they occur, rather  
       ' than having a generic try/catch block such as this.   
       ' However, because the error or truncation implementation is specific to each component,  
       ' this sample focuses on actually directing the row, and not a single error or truncation.  
  
       ' Unless an exception occurs, direct the row to the default   
       buffer.DirectRow(defaultOutputID)   
     Catch   
       ' Yes, has the user specified to redirect the row?  
       If input.ErrorRowDisposition = DTSRowDisposition.RD_RedirectRow Then   
         ' Yes, direct the row to the error output.  
         ' TODO: Add code to include the errorColumnIndex.  
         buffer.DirectErrorRow(errorOutputID, 0, errorColumnIndex)   
       Else   
         If input.ErrorRowDisposition = DTSRowDisposition.RD_FailComponent OrElse input.ErrorRowDisposition = DTSRowDisposition.RD_NotUsed Then   
           ' No, the user specified to fail the component, or the error row disposition was not set.  
           Throw New Exception("An error occurred, and the DTSRowDisposition is either not set, or is set to fail component.")   
         Else   
           ' No, the user specified to ignore the failure so   
           ' direct the row to the default output.  
           buffer.DirectRow(defaultOutputID)   
         End If   
       End If   
     End Try   
   End While   
End Sub  
```  
  
### <a name="redirecting-a-row-with-asynchronous-outputs"></a><span data-ttu-id="8081c-141">重新導向具有非同步輸出的資料列</span><span class="sxs-lookup"><span data-stu-id="8081c-141">Redirecting a Row with Asynchronous Outputs</span></span>  
 <span data-ttu-id="8081c-142">具有同步錯誤輸出的元件是將資料列導向輸出，而具有非同步輸出的元件則是明確地將資料列加入輸出 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer>，以便將資料列傳送到錯誤輸出。</span><span class="sxs-lookup"><span data-stu-id="8081c-142">Instead of directing rows to an output, as is done with synchronous error outputs, components with asynchronous outputs send a row to an error output by explicitly adding a row to the output <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer>.</span></span> <span data-ttu-id="8081c-143">實作使用非同步錯誤輸出的元件，需要將資料行加入提供給下游元件的錯誤輸出，並且為 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> 方法期間提供給元件的錯誤輸出快取輸出緩衝區。</span><span class="sxs-lookup"><span data-stu-id="8081c-143">Implementing a component that uses asynchronous error outputs requires adding columns to the error output that are provided to downstream components, and caching the output buffer for the error output that is provided to the component during the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> method.</span></span> <span data-ttu-id="8081c-144">實作具有非同步輸出之元件的詳細資料，將於[開發具有非同步輸出的自訂轉換元件](../../extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-asynchronous-outputs.md)主題中詳細說明。</span><span class="sxs-lookup"><span data-stu-id="8081c-144">The details of implementing a component with asynchronous outputs are covered in detail in the topic [Developing a Custom Transformation Component with Asynchronous Outputs](../../extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-asynchronous-outputs.md).</span></span> <span data-ttu-id="8081c-145">如果資料行未明確地加入錯誤輸出，則加入輸出緩衝區的緩衝區資料列只會包含兩個錯誤資料行。</span><span class="sxs-lookup"><span data-stu-id="8081c-145">If columns are not explicitly added to the error output, the buffer row that is added to the output buffer contains only the two error columns.</span></span>  
  
 <span data-ttu-id="8081c-146">若要將資料列傳送到非同步錯誤輸出，則必須將資料列加入錯誤輸出緩衝區。</span><span class="sxs-lookup"><span data-stu-id="8081c-146">To send a row to an asynchronous error output, you must add a row to the error output buffer.</span></span> <span data-ttu-id="8081c-147">有時，資料列可能已經加入非錯誤輸出緩衝區，而您必須使用 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.RemoveRow%2A> 方法來移除此資料列。</span><span class="sxs-lookup"><span data-stu-id="8081c-147">Sometimes, a row may have already been added to the non-error output buffer and you must remove this row by using the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.RemoveRow%2A> method.</span></span> <span data-ttu-id="8081c-148">接下來您要設定輸出緩衝區資料行值，最後則是呼叫 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetErrorInfo%2A> 方法，以提供元件特定的錯誤碼與錯誤資料行值。</span><span class="sxs-lookup"><span data-stu-id="8081c-148">Next you set the output buffer columns values, and finally, you call the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetErrorInfo%2A> method to provide the component-specific error code and the error column value.</span></span>  
  
 <span data-ttu-id="8081c-149">下列範例示範如何使用具有非同步輸出之元件的錯誤輸出。</span><span class="sxs-lookup"><span data-stu-id="8081c-149">The following example demonstrates how to use an error output for a component with asynchronous outputs.</span></span> <span data-ttu-id="8081c-150">當模擬的錯誤發生時，元件會將資料列加入錯誤輸出緩衝區、將之前加入非錯誤輸出緩衝區的值複製到錯誤輸出緩衝區、移除加入非錯誤輸出緩衝區的資料列，最後再透過呼叫 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetErrorInfo%2A> 方法，設定錯誤碼與錯誤資料行值。</span><span class="sxs-lookup"><span data-stu-id="8081c-150">When the simulated error occurs, the component adds a row to the error output buffer, copies the values that were previously added to the non-error output buffer to the error output buffer, removes the row that was added to the non-error output buffer, and, finally, sets the error code and error column values by calling the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetErrorInfo%2A> method.</span></span>  
  
```csharp  
int []columnIndex;  
int errorOutputID = -1;  
int errorOutputIndex = -1;  
  
public override void PreExecute()  
{  
    IDTSOutput100 defaultOutput = null;  
  
    this.GetErrorOutputInfo(ref errorOutputID, ref errorOutputIndex);  
    foreach (IDTSOutput100 output in ComponentMetaData.OutputCollection)  
    {  
        if (output.ID != errorOutputID)  
            defaultOutput = output;  
    }  
  
    columnIndex = new int[defaultOutput.OutputColumnCollection.Count];  
  
    for(int col =0 ; col < defaultOutput.OutputColumnCollection.Count; col++)  
    {  
        IDTSOutputColumn100 column = defaultOutput.OutputColumnCollection[col];  
        columnIndex[col] = BufferManager.FindColumnByLineageID(defaultOutput.Buffer, column.LineageID);  
    }  
}  
  
public override void PrimeOutput(int outputs, int[] outputIDs, PipelineBuffer[] buffers)  
{  
    for( int x=0; x < outputs; x++ )  
    {  
        if (outputIDs[x] == errorOutputID)  
            this.errorBuffer = buffers[x];  
        else  
            this.defaultBuffer = buffers[x];  
    }  
  
    int rows = 100;  
  
    Random random = new Random(System.DateTime.Now.Millisecond);  
  
    for (int row = 0; row < rows; row++)  
    {  
        try  
        {  
            defaultBuffer.AddRow();  
  
            for (int x = 0; x < columnIndex.Length; x++)  
                defaultBuffer[columnIndex[x]] = random.Next();  
  
            // Simulate an error.  
            if ((row % 2) == 0)  
                throw new Exception("A simulated error.");  
        }  
        catch  
        {  
            // Add a row to the error buffer.  
            errorBuffer.AddRow();  
  
            // Get the values from the default buffer  
            // and copy them to the error buffer.  
            for (int x = 0; x < columnIndex.Length; x++)  
                errorBuffer[columnIndex[x]] = defaultBuffer[columnIndex[x]];  
  
            // Set the error information.  
            errorBuffer.SetErrorInfo(errorOutputID, 1, 0);  
  
            // Remove the row that was added to the default buffer.  
            defaultBuffer.RemoveRow();  
        }  
    }  
  
    if (defaultBuffer != null)  
        defaultBuffer.SetEndOfRowset();  
  
    if (errorBuffer != null)  
        errorBuffer.SetEndOfRowset();  
}  
```  
  
```vb  
Private columnIndex As Integer()   
Private errorOutputID As Integer = -1   
Private errorOutputIndex As Integer = -1   
  
Public  Overrides Sub PreExecute()   
 Dim defaultOutput As IDTSOutput100 = Nothing   
 Me.GetErrorOutputInfo(errorOutputID, errorOutputIndex)   
 For Each output As IDTSOutput100 In ComponentMetaData.OutputCollection   
   If Not (output.ID = errorOutputID) Then   
     defaultOutput = output   
   End If   
 Next   
 columnIndex = New Integer(defaultOutput.OutputColumnCollection.Count) {}   
 Dim col As Integer = 0   
 While col < defaultOutput.OutputColumnCollection.Count   
   Dim column As IDTSOutputColumn100 = defaultOutput.OutputColumnCollection(col)   
   columnIndex(col) = BufferManager.FindColumnByLineageID(defaultOutput.Buffer, column.LineageID)   
   System.Math.Min(System.Threading.Interlocked.Increment(col),col-1)   
 End While   
End Sub   
  
Public  Overrides Sub PrimeOutput(ByVal outputs As Integer, ByVal outputIDs As Integer(), ByVal buffers As PipelineBuffer())   
 Dim x As Integer = 0   
 While x < outputs   
   If outputIDs(x) = errorOutputID Then   
     Me.errorBuffer = buffers(x)   
   Else   
     Me.defaultBuffer = buffers(x)   
   End If   
   System.Math.Min(System.Threading.Interlocked.Increment(x),x-1)   
 End While   
 Dim rows As Integer = 100   
 Dim random As Random = New Random(System.DateTime.Now.Millisecond)   
 Dim row As Integer = 0   
 While row < rows   
   Try   
     defaultBuffer.AddRow   
     Dim x As Integer = 0   
     While x < columnIndex.Length   
       defaultBuffer(columnIndex(x)) = random.Next   
       System.Math.Min(System.Threading.Interlocked.Increment(x),x-1)   
     End While   
     ' Simulate an error.  
     If (row Mod 2) = 0 Then   
       Throw New Exception("A simulated error.")   
     End If   
   Catch   
     ' Add a row to the error buffer.  
     errorBuffer.AddRow   
     ' Get the values from the default buffer  
     ' and copy them to the error buffer.  
     Dim x As Integer = 0   
     While x < columnIndex.Length   
       errorBuffer(columnIndex(x)) = defaultBuffer(columnIndex(x))   
       System.Math.Min(System.Threading.Interlocked.Increment(x),x-1)   
     End While   
     ' Set the error information.  
     errorBuffer.SetErrorInfo(errorOutputID, 1, 0)   
     ' Remove the row that was added to the default buffer.  
     defaultBuffer.RemoveRow   
   End Try   
   System.Math.Min(System.Threading.Interlocked.Increment(row),row-1)   
 End While   
 If Not (defaultBuffer Is Nothing) Then   
   defaultBuffer.SetEndOfRowset   
 End If   
 If Not (errorBuffer Is Nothing) Then   
   errorBuffer.SetEndOfRowset   
 End If   
End Sub  
```  
  
<span data-ttu-id="8081c-151">![Integration Services 圖示 (小型) ](../../media/dts-16.gif "Integration Services 圖示 (小)")會**保持最**新狀態 Integration Services  </span><span class="sxs-lookup"><span data-stu-id="8081c-151">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="8081c-152">若要取得 Microsoft 的最新下載、文件、範例和影片以及社群中的精選解決方案，請瀏覽 MSDN 上的 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 頁面：</span><span class="sxs-lookup"><span data-stu-id="8081c-152">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="8081c-153">瀏覽 MSDN 上的 Integration Services 頁面</span><span class="sxs-lookup"><span data-stu-id="8081c-153">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="8081c-154">若要得到這些更新的自動通知，請訂閱該頁面上所提供的 RSS 摘要。</span><span class="sxs-lookup"><span data-stu-id="8081c-154">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8081c-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8081c-155">See Also</span></span>  
 <span data-ttu-id="8081c-156">[資料中的錯誤處理](../../data-flow/error-handling-in-data.md) </span><span class="sxs-lookup"><span data-stu-id="8081c-156">[Error Handling in Data](../../data-flow/error-handling-in-data.md) </span></span>  
 [<span data-ttu-id="8081c-157">使用錯誤輸出</span><span class="sxs-lookup"><span data-stu-id="8081c-157">Using Error Outputs</span></span>](using-error-outputs-in-a-data-flow-component.md)  
  
  
