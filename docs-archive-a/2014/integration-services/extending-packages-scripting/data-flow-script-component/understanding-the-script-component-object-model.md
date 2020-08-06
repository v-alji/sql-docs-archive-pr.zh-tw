---
title: 了解指令碼元件物件模型 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- Script component [Integration Services], object model
ms.assetid: 2a0aae82-39cc-4423-b09a-72d2f61033bd
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a11556b00efc5749e8ddb895712d6c61f2459d8b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595193"
---
# <a name="understanding-the-script-component-object-model"></a><span data-ttu-id="9aa74-102">了解指令碼元件物件模型</span><span class="sxs-lookup"><span data-stu-id="9aa74-102">Understanding the Script Component Object Model</span></span>
  <span data-ttu-id="9aa74-103">如 [編碼和偵錯工具腳本元件] 中所述 (.。/extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md，腳本元件專案包含三個專案專案：</span><span class="sxs-lookup"><span data-stu-id="9aa74-103">As discussed in [Coding and Debugging the Script Component](../extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md, the Script component project contains three project items:</span></span>

1.  <span data-ttu-id="9aa74-104">`ScriptMain` 項目，其中包含您用來撰寫程式碼的 `ScriptMain` 類別。</span><span class="sxs-lookup"><span data-stu-id="9aa74-104">The `ScriptMain` item, which contains the `ScriptMain` class in which you write your code.</span></span> <span data-ttu-id="9aa74-105">`ScriptMain` 類別繼承自 `UserComponent` 類別。</span><span class="sxs-lookup"><span data-stu-id="9aa74-105">The `ScriptMain` class inherits from the `UserComponent` class.</span></span>

2.  <span data-ttu-id="9aa74-106">包含 `ComponentWrapper` 類別的 `UserComponent` 項目，該類別是 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> 的執行個體 (其中包含您將用來處理資料以及與封裝互動的方法和屬性)。</span><span class="sxs-lookup"><span data-stu-id="9aa74-106">The `ComponentWrapper` item, which contains the `UserComponent` class, an instance of <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> that contains the methods and properties that you will use to process data and to interact with the package.</span></span> <span data-ttu-id="9aa74-107">`ComponentWrapper` 項目也包含 `Connections` 和 `Variables` 集合類別。</span><span class="sxs-lookup"><span data-stu-id="9aa74-107">The `ComponentWrapper` item also contains `Connections` and `Variables` collection classes.</span></span>

3.  <span data-ttu-id="9aa74-108">包含類別的 `BufferWrapper` 項目，該類別繼承自每一個輸入和輸出的 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptBuffer> 及每一個資料行的具類型屬性。</span><span class="sxs-lookup"><span data-stu-id="9aa74-108">The `BufferWrapper` item, which contains classes that inherits from <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptBuffer> for each input and output, and typed properties for each column.</span></span>

 <span data-ttu-id="9aa74-109">當您在 `ScriptMain` 項目中撰寫程式碼時，您將會使用本主題討論的物件、方法和屬性。</span><span class="sxs-lookup"><span data-stu-id="9aa74-109">As you write your code in the `ScriptMain` item, you will use the objects, methods, and properties discussed in this topic.</span></span> <span data-ttu-id="9aa74-110">並非這裡列出的所有方法都會讓每一個元件使用，但是在使用這些方法時，則會以顯示的順序來使用。</span><span class="sxs-lookup"><span data-stu-id="9aa74-110">Each component will not use all the methods listed here; however, when used, they are used in the sequence shown.</span></span>

 <span data-ttu-id="9aa74-111"><xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> 基底類別不包含本主題討論之方法的任何實作程式碼。</span><span class="sxs-lookup"><span data-stu-id="9aa74-111">The <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> base class does not contain any implementation code for the methods discussed in this topic.</span></span> <span data-ttu-id="9aa74-112">因此，將基底類別實作的呼叫加入到您自己的方法實作中是不必要的，但是這樣做也無害。</span><span class="sxs-lookup"><span data-stu-id="9aa74-112">Therefore it is unnecessary, but harmless, to add a call to the base class implementation to your own implementation of the method.</span></span>

 <span data-ttu-id="9aa74-113">如需如何在特定的指令碼元件類型中使用這些類別的方法和屬性的資訊，請參閱[其他指令碼元件範例](../../extending-packages-scripting-data-flow-script-component-examples/additional-script-component-examples.md)。</span><span class="sxs-lookup"><span data-stu-id="9aa74-113">For information about how to use the methods and properties of these classes in a particular type of Script component, see the section [Additional Script Component Examples](../../extending-packages-scripting-data-flow-script-component-examples/additional-script-component-examples.md).</span></span> <span data-ttu-id="9aa74-114">範例主題也包含完整的程式碼範例。</span><span class="sxs-lookup"><span data-stu-id="9aa74-114">The example topics also contain complete code samples.</span></span>

## <a name="acquireconnections-method"></a><span data-ttu-id="9aa74-115">AcquireConnections 方法</span><span class="sxs-lookup"><span data-stu-id="9aa74-115">AcquireConnections Method</span></span>
 <span data-ttu-id="9aa74-116">來源和目的地通常必須連接到外部資料來源。</span><span class="sxs-lookup"><span data-stu-id="9aa74-116">Sources and destinations generally must connect to an external data source.</span></span> <span data-ttu-id="9aa74-117">覆寫 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.AcquireConnections%2A> 基底類別的 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> 方法，從適當的連接管理員擷取連接或連接資訊。</span><span class="sxs-lookup"><span data-stu-id="9aa74-117">Override the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.AcquireConnections%2A> method of the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> base class to retrieve the connection or the connection information from the appropriate connection manager.</span></span>

 <span data-ttu-id="9aa74-118">下列範例會從 ADO.NET 連接管理員傳回 `System.Data.SqlClient.SqlConnection`。</span><span class="sxs-lookup"><span data-stu-id="9aa74-118">The following example returns a `System.Data.SqlClient.SqlConnection` from an ADO.NET connection manager.</span></span>

```vb
Dim connMgr As IDTSConnectionManager100
Dim sqlConn As SqlConnection

Public Overrides Sub AcquireConnections(ByVal Transaction As Object)

    connMgr = Me.Connections.MyADONETConnection
    sqlConn = CType(connMgr.AcquireConnection(Nothing), SqlConnection)

End Sub
```

 <span data-ttu-id="9aa74-119">下列範例會從一般檔案連接管理員傳回完整的路徑和檔案名稱，然後使用 `System.IO.StreamReader` 開啟檔案。</span><span class="sxs-lookup"><span data-stu-id="9aa74-119">The following example returns a complete path and file name from a Flat File Connection Manager, and then opens the file by using a `System.IO.StreamReader`.</span></span>

```vb
Private textReader As StreamReader
Public Overrides Sub AcquireConnections(ByVal Transaction As Object)

    Dim connMgr As IDTSConnectionManager100 = _
        Me.Connections.MyFlatFileSrcConnectionManager
    Dim exportedAddressFile As String = _
        CType(connMgr.AcquireConnection(Nothing), String)
    textReader = New StreamReader(exportedAddressFile)

End Sub
```

## <a name="preexecute-method"></a><span data-ttu-id="9aa74-120">PreExecute 方法</span><span class="sxs-lookup"><span data-stu-id="9aa74-120">PreExecute Method</span></span>
 <span data-ttu-id="9aa74-121">每當您的處理必須只能在您開始處理資料列以前執行一次時，請覆寫 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.PreExecute%2A> 基底類別的 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> 方法。</span><span class="sxs-lookup"><span data-stu-id="9aa74-121">Override the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.PreExecute%2A> method of the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> base class whenever you have processing that you must perform one time only before you start processing rows of data.</span></span> <span data-ttu-id="9aa74-122">例如在目的地中，您可能會想要設定參數化命令，目的地將會使用該命令將每個資料列插入資料來源中。</span><span class="sxs-lookup"><span data-stu-id="9aa74-122">For example, in a destination, you may want to configure the parameterized command that the destination will use to insert each row of data into the data source.</span></span>

```vb
    Dim sqlConn As SqlConnection
    Dim sqlCmd As SqlCommand
    Dim sqlParam As SqlParameter
...
    Public Overrides Sub PreExecute()

        sqlCmd = New SqlCommand("INSERT INTO Person.Address2(AddressID, City) " & _
            "VALUES(@addressid, @city)", sqlConn)
        sqlParam = New SqlParameter("@addressid", SqlDbType.Int)
        sqlCmd.Parameters.Add(sqlParam)
        sqlParam = New SqlParameter("@city", SqlDbType.NVarChar, 30)
        sqlCmd.Parameters.Add(sqlParam)

    End Sub
```

```csharp
SqlConnection sqlConn; 
SqlCommand sqlCmd; 
SqlParameter sqlParam; 

public override void PreExecute() 
{ 

    sqlCmd = new SqlCommand("INSERT INTO Person.Address2(AddressID, City) " + "VALUES(@addressid, @city)", sqlConn); 
    sqlParam = new SqlParameter("@addressid", SqlDbType.Int); 
    sqlCmd.Parameters.Add(sqlParam); 
    sqlParam = new SqlParameter("@city", SqlDbType.NVarChar, 30); 
    sqlCmd.Parameters.Add(sqlParam); 

}
```

## <a name="processing-inputs-and-outputs"></a><span data-ttu-id="9aa74-123">處理輸入和輸出</span><span class="sxs-lookup"><span data-stu-id="9aa74-123">Processing Inputs and Outputs</span></span>

### <a name="processing-inputs"></a><span data-ttu-id="9aa74-124">處理輸入</span><span class="sxs-lookup"><span data-stu-id="9aa74-124">Processing Inputs</span></span>
 <span data-ttu-id="9aa74-125">設定為轉換或目的地的指令碼元件有一個輸入。</span><span class="sxs-lookup"><span data-stu-id="9aa74-125">Script components that are configured as transformations or destinations have one input.</span></span>

#### <a name="what-the-bufferwrapper-project-item-provides"></a><span data-ttu-id="9aa74-126">BufferWrapper 專案項目提供的內容</span><span class="sxs-lookup"><span data-stu-id="9aa74-126">What the BufferWrapper Project Item Provides</span></span>
 <span data-ttu-id="9aa74-127">如果是您已設定的每一個輸入，`BufferWrapper` 專案項目都會包含一個衍生自 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptBuffer> 的類別，而且名稱與輸入相同。</span><span class="sxs-lookup"><span data-stu-id="9aa74-127">For each input that you have configured, the `BufferWrapper` project item contains a class that derives from <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptBuffer> and has the same name as the input.</span></span> <span data-ttu-id="9aa74-128">每一個輸入緩衝區類別都包含下列屬性、函數和方法：</span><span class="sxs-lookup"><span data-stu-id="9aa74-128">Each input buffer class contains the following properties, functions, and methods:</span></span>

-   <span data-ttu-id="9aa74-129">每一個選定輸入資料行的具名、具類型存取子屬性。</span><span class="sxs-lookup"><span data-stu-id="9aa74-129">Named, typed accessor properties for each selected input column.</span></span> <span data-ttu-id="9aa74-130">這些屬性是唯讀或可讀寫，這取決於在 [指令碼轉換編輯器]  的 [輸入資料行]  頁面上針對資料行所指定的 [使用類型]  。</span><span class="sxs-lookup"><span data-stu-id="9aa74-130">These properties are read-only or read/write depending on the **Usage Type** specified for the column on the **Input Columns** page of the **Script Transformation Editor**.</span></span>

-   <span data-ttu-id="9aa74-131">每一個選定輸入資料行的 **\<column>_IsNull** 屬性。</span><span class="sxs-lookup"><span data-stu-id="9aa74-131">A **\<column>_IsNull** property for each selected input column.</span></span> <span data-ttu-id="9aa74-132">這個屬性也是唯讀或可讀寫，這取決於針對資料行指定的 [使用類型]  而定。</span><span class="sxs-lookup"><span data-stu-id="9aa74-132">This property is also read-only or read/write depending on the **Usage Type** specified for the column.</span></span>

-   <span data-ttu-id="9aa74-133">每一個已設定輸出的 **DirectRowTo\<outputbuffer>** 方法。</span><span class="sxs-lookup"><span data-stu-id="9aa74-133">A **DirectRowTo\<outputbuffer>** method for each configured output.</span></span> <span data-ttu-id="9aa74-134">當您在相同的 `ExclusionGroup` 中將資料列篩選成數個輸出的其中一個時，您將會使用這些方法。</span><span class="sxs-lookup"><span data-stu-id="9aa74-134">You will use these methods when filtering rows to one of several outputs in the same `ExclusionGroup`.</span></span>

-   <span data-ttu-id="9aa74-135">取得下一個輸入資料列的 `NextRow` 函數，以及判斷上一個資料緩衝區是否已經處理的 `EndOfRowset` 函數。</span><span class="sxs-lookup"><span data-stu-id="9aa74-135">A `NextRow` function to get the next input row, and an `EndOfRowset` function to determine whether the last buffer of data has been processed.</span></span> <span data-ttu-id="9aa74-136">當您使用 `UserComponent` 基底類別內所實作的輸入處理方法時，通常不需要這些函數。</span><span class="sxs-lookup"><span data-stu-id="9aa74-136">You typically do not need these functions when you use the input processing methods implemented in the `UserComponent` base class.</span></span> <span data-ttu-id="9aa74-137">下一節會提供有關 `UserComponent` 基底類別的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="9aa74-137">The next section provides more information about the `UserComponent` base class.</span></span>

#### <a name="what-the-componentwrapper-project-item-provides"></a><span data-ttu-id="9aa74-138">ComponentWrapper 專案項目提供的內容</span><span class="sxs-lookup"><span data-stu-id="9aa74-138">What the ComponentWrapper Project Item Provides</span></span>
 <span data-ttu-id="9aa74-139">ComponentWrapper 專案項目包含了衍生自 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> 的 `UserComponent` 類別。</span><span class="sxs-lookup"><span data-stu-id="9aa74-139">The ComponentWrapper project item contains a class named `UserComponent` that derives from <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent>.</span></span> <span data-ttu-id="9aa74-140">接著您撰寫自訂程式碼所使用的 `ScriptMain` 類別就會衍生自 `UserComponent`。</span><span class="sxs-lookup"><span data-stu-id="9aa74-140">The `ScriptMain` class in which you write your custom code derives in turn from `UserComponent`.</span></span> <span data-ttu-id="9aa74-141">`UserComponent` 類別包含以下的方法：</span><span class="sxs-lookup"><span data-stu-id="9aa74-141">The `UserComponent` class contains the following methods:</span></span>

-   <span data-ttu-id="9aa74-142">已覆寫的 `ProcessInput` 方法實作。</span><span class="sxs-lookup"><span data-stu-id="9aa74-142">An overridden implementation of the `ProcessInput` method.</span></span> <span data-ttu-id="9aa74-143">這是資料流程引擎在執行階段的 `PreExecute` 方法之後所呼叫的方法，而且它可呼叫多次。</span><span class="sxs-lookup"><span data-stu-id="9aa74-143">This is the method that the data flow engine calls next at run time after the `PreExecute` method, and it may be called multiple times.</span></span> <span data-ttu-id="9aa74-144">`ProcessInput`將處理交給\*\* \<inputbuffer> _ProcessInput\*\*方法。</span><span class="sxs-lookup"><span data-stu-id="9aa74-144">`ProcessInput` hands off processing to the **\<inputbuffer>_ProcessInput** method.</span></span> <span data-ttu-id="9aa74-145">然後 `ProcessInput` 方法會檢查輸入緩衝區的結尾，如果到達了緩衝區結尾，會呼叫可覆寫的 `FinishOutputs` 方法和私用 `MarkOutputsAsFinished` 方法。</span><span class="sxs-lookup"><span data-stu-id="9aa74-145">Then the `ProcessInput` method checks for the end of the input buffer and, if the end of the buffer has been reached, calls the overridable `FinishOutputs` method and the private `MarkOutputsAsFinished` method.</span></span> <span data-ttu-id="9aa74-146">然後 `MarkOutputsAsFinished` 方法會在最後一個輸出緩衝區上呼叫 `SetEndOfRowset`。</span><span class="sxs-lookup"><span data-stu-id="9aa74-146">The `MarkOutputsAsFinished` method then calls `SetEndOfRowset` on the last output buffer.</span></span>

-   <span data-ttu-id="9aa74-147">可覆寫的 **\<inputbuffer>_ProcessInput** 方法實作。</span><span class="sxs-lookup"><span data-stu-id="9aa74-147">An overridable implementation of the **\<inputbuffer>_ProcessInput** method.</span></span> <span data-ttu-id="9aa74-148">這個預設實作只會在每一個輸入資料列中執行迴圈，並呼叫 **\<inputbuffer>_ProcessInputRow**。</span><span class="sxs-lookup"><span data-stu-id="9aa74-148">This default implementation simply loops through each input row and calls **\<inputbuffer>_ProcessInputRow**.</span></span>

-   <span data-ttu-id="9aa74-149">可覆寫的 **\<inputbuffer>_ProcessInputRow** 方法實作。</span><span class="sxs-lookup"><span data-stu-id="9aa74-149">An overridable implementation of the **\<inputbuffer>_ProcessInputRow** method.</span></span> <span data-ttu-id="9aa74-150">預設的實作是空的。</span><span class="sxs-lookup"><span data-stu-id="9aa74-150">The default implementation is empty.</span></span> <span data-ttu-id="9aa74-151">這是您通常會覆寫，以撰寫自訂資料處理程式碼的方法。</span><span class="sxs-lookup"><span data-stu-id="9aa74-151">This is the method that you will normally override to write your custom data processing code.</span></span>

#### <a name="what-your-custom-code-should-do"></a><span data-ttu-id="9aa74-152">自訂程式碼應該做的事</span><span class="sxs-lookup"><span data-stu-id="9aa74-152">What Your Custom Code Should Do</span></span>
 <span data-ttu-id="9aa74-153">您可以使用下列方法，在 `ScriptMain` 類別中處理輸入：</span><span class="sxs-lookup"><span data-stu-id="9aa74-153">You can use the following methods to process input in the `ScriptMain` class:</span></span>

-   <span data-ttu-id="9aa74-154">覆寫 **\<inputbuffer>_ProcessInputRow**，以處理每一個輸入資料列中通過的資料。</span><span class="sxs-lookup"><span data-stu-id="9aa74-154">Override **\<inputbuffer>_ProcessInputRow** to process the data in each input row as it passes through.</span></span>

-   <span data-ttu-id="9aa74-155">只有當在輸入資料列中執行迴圈時必須執行其他額外動作的時候，才會覆寫 **\<inputbuffer>_ProcessInput**。</span><span class="sxs-lookup"><span data-stu-id="9aa74-155">Override **\<inputbuffer>_ProcessInput** only if you have to do something additional while looping through input rows.</span></span> <span data-ttu-id="9aa74-156"> (例如，您必須在 `EndOfRowset` 處理完所有資料列之後，測試以採取其他動作。 ) 呼\叫\** \<inputbuffer> _ProcessInputRo\w\**來執行資料列處理。</span><span class="sxs-lookup"><span data-stu-id="9aa74-156">(For example, you have to test for `EndOfRowset` to take some other action after all rows have been processed.) Call **\<inputbuffer>_ProcessInputRow** to perform the row processing.</span></span>

-   <span data-ttu-id="9aa74-157">如果您必須在關閉輸出以前先對輸出做某些事，請覆寫 `FinishOutputs`。</span><span class="sxs-lookup"><span data-stu-id="9aa74-157">Override `FinishOutputs` if you have to do something to the outputs before they are closed.</span></span>

 <span data-ttu-id="9aa74-158">`ProcessInput` 方法可確保這些方法會在適當的時間呼叫。</span><span class="sxs-lookup"><span data-stu-id="9aa74-158">The `ProcessInput` method ensures that these methods are called at the appropriate times.</span></span>

### <a name="processing-outputs"></a><span data-ttu-id="9aa74-159">處理輸出</span><span class="sxs-lookup"><span data-stu-id="9aa74-159">Processing Outputs</span></span>
 <span data-ttu-id="9aa74-160">設定為來源或轉換的指令碼元件有一個或多個輸出。</span><span class="sxs-lookup"><span data-stu-id="9aa74-160">Script components configured as sources or transformations have one or more outputs.</span></span>

#### <a name="what-the-bufferwrapper-project-item-provides"></a><span data-ttu-id="9aa74-161">BufferWrapper 專案項目提供的內容</span><span class="sxs-lookup"><span data-stu-id="9aa74-161">What the BufferWrapper Project Item Provides</span></span>
 <span data-ttu-id="9aa74-162">如果是您已設定的每一個輸出，BufferWrapper 專案項目都會包含一個衍生自 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptBuffer> 的類別，而且名稱與輸出相同。</span><span class="sxs-lookup"><span data-stu-id="9aa74-162">For each output that you have configured, the BufferWrapper project item contains a class that derives from <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptBuffer> and has the same name as the output.</span></span> <span data-ttu-id="9aa74-163">每一個輸入緩衝區類別都包含下列屬性和方法：</span><span class="sxs-lookup"><span data-stu-id="9aa74-163">Each input buffer class contains the following properties and methods:</span></span>

-   <span data-ttu-id="9aa74-164">每一個輸出資料行的具名、具類型、唯寫的存取子屬性。</span><span class="sxs-lookup"><span data-stu-id="9aa74-164">Named, typed, write-only accessor properties for each output column.</span></span>

-   <span data-ttu-id="9aa74-165">針對每個選取的輸出資料行，您可以用來將資料行值設定為的僅限寫入\*\* \<column> _IsNull\*\*屬性 `null` 。</span><span class="sxs-lookup"><span data-stu-id="9aa74-165">A write-only **\<column>_IsNull** property for each selected output column that you can use to set the column value to `null`.</span></span>

-   <span data-ttu-id="9aa74-166">要將空白的新資料列加入到輸出緩衝區的 `AddRow` 方法。</span><span class="sxs-lookup"><span data-stu-id="9aa74-166">An `AddRow` method to add an empty new row to the output buffer.</span></span>

-   <span data-ttu-id="9aa74-167">可讓資料流程引擎知道不會預期其他資料緩衝區的 `SetEndOfRowset` 方法。</span><span class="sxs-lookup"><span data-stu-id="9aa74-167">A `SetEndOfRowset` method to let the data flow engine know that no more buffers of data are expected.</span></span> <span data-ttu-id="9aa74-168">也有一個 `EndOfRowset` 函數可判斷目前的緩衝區是否為最後一個資料緩衝區。</span><span class="sxs-lookup"><span data-stu-id="9aa74-168">There is also an `EndOfRowset` function to determine whether the current buffer is the last buffer of data.</span></span> <span data-ttu-id="9aa74-169">當您使用 `UserComponent` 基底類別內所實作的輸入處理方法時，通常不需要這些函數。</span><span class="sxs-lookup"><span data-stu-id="9aa74-169">You generally do not need these functions when you use the input processing methods implemented in the `UserComponent` base class.</span></span>

#### <a name="what-the-componentwrapper-project-item-provides"></a><span data-ttu-id="9aa74-170">ComponentWrapper 專案項目提供的內容</span><span class="sxs-lookup"><span data-stu-id="9aa74-170">What the ComponentWrapper Project Item Provides</span></span>
 <span data-ttu-id="9aa74-171">ComponentWrapper 專案項目包含了衍生自 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> 的 `UserComponent` 類別。</span><span class="sxs-lookup"><span data-stu-id="9aa74-171">The ComponentWrapper project item contains a class named `UserComponent` that derives from <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent>.</span></span> <span data-ttu-id="9aa74-172">接著您撰寫自訂程式碼所使用的 `ScriptMain` 類別就會衍生自 `UserComponent`。</span><span class="sxs-lookup"><span data-stu-id="9aa74-172">The `ScriptMain` class in which you write your custom code derives in turn from `UserComponent`.</span></span> <span data-ttu-id="9aa74-173">`UserComponent` 類別包含以下的方法：</span><span class="sxs-lookup"><span data-stu-id="9aa74-173">The `UserComponent` class contains the following methods:</span></span>

-   <span data-ttu-id="9aa74-174">已覆寫的 `PrimeOutput` 方法實作。</span><span class="sxs-lookup"><span data-stu-id="9aa74-174">An overridden implementation of the `PrimeOutput` method.</span></span> <span data-ttu-id="9aa74-175">資料流程引擎會在執行階段的 `ProcessInput` 之前呼叫這個方法，而且只會呼叫一次。</span><span class="sxs-lookup"><span data-stu-id="9aa74-175">The data flow engine calls this method before `ProcessInput` at run time, and it is only called one time.</span></span> <span data-ttu-id="9aa74-176">`PrimeOutput` 會將處理交給 `CreateNewOutputRows` 方法。</span><span class="sxs-lookup"><span data-stu-id="9aa74-176">`PrimeOutput` hands off processing to the `CreateNewOutputRows` method.</span></span> <span data-ttu-id="9aa74-177">然後，如果此元件是來源 (也就是此元件沒有輸入)，`PrimeOutput` 會呼叫可覆寫的 `FinishOutputs` 方法和私用 `MarkOutputsAsFinished` 方法。</span><span class="sxs-lookup"><span data-stu-id="9aa74-177">Then, if the component is a source (that is, the component has no inputs), `PrimeOutput` calls the overridable `FinishOutputs` method and the private `MarkOutputsAsFinished` method.</span></span> <span data-ttu-id="9aa74-178">`MarkOutputsAsFinished` 方法會在最後一個輸出緩衝區上呼叫 `SetEndOfRowset`。</span><span class="sxs-lookup"><span data-stu-id="9aa74-178">The `MarkOutputsAsFinished` method calls `SetEndOfRowset` on the last output buffer.</span></span>

-   <span data-ttu-id="9aa74-179">可覆寫的 `CreateNewOutputRows` 方法實作。</span><span class="sxs-lookup"><span data-stu-id="9aa74-179">An overridable implementation of the `CreateNewOutputRows` method.</span></span> <span data-ttu-id="9aa74-180">預設的實作是空的。</span><span class="sxs-lookup"><span data-stu-id="9aa74-180">The default implementation is empty.</span></span> <span data-ttu-id="9aa74-181">這是您通常會覆寫，以撰寫自訂資料處理程式碼的方法。</span><span class="sxs-lookup"><span data-stu-id="9aa74-181">This is the method that you will normally override to write your custom data processing code.</span></span>

#### <a name="what-your-custom-code-should-do"></a><span data-ttu-id="9aa74-182">自訂程式碼應該做的事</span><span class="sxs-lookup"><span data-stu-id="9aa74-182">What Your Custom Code Should Do</span></span>
 <span data-ttu-id="9aa74-183">您可以使用下列方法，在 `ScriptMain` 類別中處理輸出：</span><span class="sxs-lookup"><span data-stu-id="9aa74-183">You can use the following methods to process outputs in the `ScriptMain` class:</span></span>

-   <span data-ttu-id="9aa74-184">只有當您在處理輸入資料列以前可以加入及擴展輸出資料列時，才會覆寫 `CreateNewOutputRows`。</span><span class="sxs-lookup"><span data-stu-id="9aa74-184">Override `CreateNewOutputRows` only when you can add and populate output rows before processing input rows.</span></span> <span data-ttu-id="9aa74-185">例如，您可以在來源中使用 `CreateNewOutputRows`，但如果是具有非同步輸出的轉換，您應該在處理輸入資料的期間或之後呼叫 `AddRow`。</span><span class="sxs-lookup"><span data-stu-id="9aa74-185">For example, you can use `CreateNewOutputRows` in a source, but in a transformation with asynchronous outputs, you should call `AddRow` during or after the processing of input data.</span></span>

-   <span data-ttu-id="9aa74-186">如果您必須在關閉輸出以前先對輸出做某些事，請覆寫 `FinishOutputs`。</span><span class="sxs-lookup"><span data-stu-id="9aa74-186">Override `FinishOutputs` if you have to do something to the outputs before they are closed.</span></span>

 <span data-ttu-id="9aa74-187">`PrimeOutput` 方法可確保這些方法會在適當的時間呼叫。</span><span class="sxs-lookup"><span data-stu-id="9aa74-187">The `PrimeOutput` method ensures that these methods are called at the appropriate times.</span></span>

## <a name="postexecute-method"></a><span data-ttu-id="9aa74-188">PostExecute 方法</span><span class="sxs-lookup"><span data-stu-id="9aa74-188">PostExecute Method</span></span>
 <span data-ttu-id="9aa74-189">每當您的處理必須只能在處理資料列之後執行一次時，請覆寫 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.PostExecute%2A> 基底類別的 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> 方法。</span><span class="sxs-lookup"><span data-stu-id="9aa74-189">Override the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.PostExecute%2A> method of the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> base class whenever you have processing that you must perform one time only after you have processed the rows of data.</span></span> <span data-ttu-id="9aa74-190">例如在來源中，您可能會想要關閉已經用來將資料載入資料流程中的 `System.Data.SqlClient.SqlDataReader`。</span><span class="sxs-lookup"><span data-stu-id="9aa74-190">For example, in a source, you may want to close the `System.Data.SqlClient.SqlDataReader` that you have used to load data into the data flow.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="9aa74-191">只有在 `ReadWriteVariables` 方法中才可使用 `PostExecute` 集合。</span><span class="sxs-lookup"><span data-stu-id="9aa74-191">The collection of `ReadWriteVariables` is available only in the `PostExecute` method.</span></span> <span data-ttu-id="9aa74-192">因此您無法在處理每一列資料時，直接增量封裝變數值。</span><span class="sxs-lookup"><span data-stu-id="9aa74-192">Therefore you cannot directly increment the value of a package variable as you process each row of data.</span></span> <span data-ttu-id="9aa74-193">請改為遞增區域變數值，並在處理所有的資料之後，將封裝變數值設定為 `PostExecute` 方法中的區域變數值。</span><span class="sxs-lookup"><span data-stu-id="9aa74-193">Instead, increment the value of a local variable, and set the value of the package variable to the value of the local variable in the `PostExecute` method after all data has been processed.</span></span>

## <a name="releaseconnections-method"></a><span data-ttu-id="9aa74-194">ReleaseConnections 方法</span><span class="sxs-lookup"><span data-stu-id="9aa74-194">ReleaseConnections Method</span></span>
 <span data-ttu-id="9aa74-195">來源和目的地通常必須連接到外部資料來源。</span><span class="sxs-lookup"><span data-stu-id="9aa74-195">Sources and destinations typically must connect to an external data source.</span></span> <span data-ttu-id="9aa74-196">覆寫 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ReleaseConnections%2A> 基底類別的 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> 方法，以關閉及釋放您之前在 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.AcquireConnections%2A> 方法中所開啟的連接。</span><span class="sxs-lookup"><span data-stu-id="9aa74-196">Override the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ReleaseConnections%2A> method of the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> base class to close and release the connection that you have opened previously in the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.AcquireConnections%2A> method.</span></span>

```vb
    Dim connMgr As IDTSConnectionManager100
...
    Public Overrides Sub ReleaseConnections()

        connMgr.ReleaseConnection(sqlConn)

    End Sub
```

```csharp
IDTSConnectionManager100 connMgr;

public override void ReleaseConnections()
{

    connMgr.ReleaseConnection(sqlConn);

}
```

<span data-ttu-id="9aa74-197">![Integration Services 圖示 (小型) ](../../media/dts-16.gif "Integration Services 圖示 (小)")會**保持最**新狀態 Integration Services  </span><span class="sxs-lookup"><span data-stu-id="9aa74-197">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="9aa74-198">若要取得 Microsoft 的最新下載、文件、範例和影片以及社群中的精選解決方案，請瀏覽 MSDN 上的 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 頁面：</span><span class="sxs-lookup"><span data-stu-id="9aa74-198">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="9aa74-199">瀏覽 MSDN 上的 Integration Services 頁面</span><span class="sxs-lookup"><span data-stu-id="9aa74-199">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="9aa74-200">若要得到這些更新的自動通知，請訂閱該頁面上所提供的 RSS 摘要。</span><span class="sxs-lookup"><span data-stu-id="9aa74-200">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>

## <a name="see-also"></a><span data-ttu-id="9aa74-201">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9aa74-201">See Also</span></span>
 <span data-ttu-id="9aa74-202">[在 [腳本元件編輯器] 中設定腳本元件](configuring-the-script-component-in-the-script-component-editor.md)[編寫和調試腳本元件] (]。/extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md</span><span class="sxs-lookup"><span data-stu-id="9aa74-202">[Configuring the Script Component in the Script Component Editor](configuring-the-script-component-in-the-script-component-editor.md) [Coding and Debugging the Script Component](../extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md</span></span>


