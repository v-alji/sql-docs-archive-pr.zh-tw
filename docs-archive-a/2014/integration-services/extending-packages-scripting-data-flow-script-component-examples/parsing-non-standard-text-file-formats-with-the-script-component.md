---
title: 使用指令碼元件剖析非標準文字檔案格式 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- text file reading [Integration Services]
- Script component [Integration Services], non-standard text file formats
- transformations [Integration Services], components
- Script component [Integration Services], examples
ms.assetid: 1fda034d-09e4-4647-9a9f-e8d508c2cc8f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 6a0ca1a0d10bdad40d39a366864a07d2b0a61d13
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688038"
---
# <a name="parsing-non-standard-text-file-formats-with-the-script-component"></a><span data-ttu-id="6f378-102">使用指令碼元件剖析非標準文字檔案格式</span><span class="sxs-lookup"><span data-stu-id="6f378-102">Parsing Non-Standard Text File Formats with the Script Component</span></span>
  <span data-ttu-id="6f378-103">當來源資料是以非標準格式排列時，為了達成相同的結果，您可能會發現將所有剖析邏輯合併在單一指令碼中會比將多個 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 轉換鏈結在一起更方便。</span><span class="sxs-lookup"><span data-stu-id="6f378-103">When your source data is arranged in a non-standard format, you may find it more convenient to consolidate all your parsing logic in a single script than to chain together multiple [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] transformations to achieve the same result.</span></span>  
  
 [<span data-ttu-id="6f378-104">範例 1：剖析以資料列分隔的記錄</span><span class="sxs-lookup"><span data-stu-id="6f378-104">Example 1: Parsing Row-Delimited Records</span></span>](#example1)  
  
 [<span data-ttu-id="6f378-105">範例 2：分割父記錄和子記錄</span><span class="sxs-lookup"><span data-stu-id="6f378-105">Example 2: Splitting Parent and Child Records</span></span>](#example2)  
  
> [!NOTE]  
>  <span data-ttu-id="6f378-106">如果您要建立可以更輕鬆地在多個資料流程工作與多個封裝之間重複使用的元件，請考慮使用這個指令碼元件範例中的程式碼，做為自訂資料流程元件的起點。</span><span class="sxs-lookup"><span data-stu-id="6f378-106">If you want to create a component that you can more easily reuse across multiple Data Flow tasks and multiple packages, consider using the code in this Script component sample as the starting point for a custom data flow component.</span></span> <span data-ttu-id="6f378-107">如需詳細資訊，請參閱 [開發自訂資料流程元件](../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md)。</span><span class="sxs-lookup"><span data-stu-id="6f378-107">For more information, see [Developing a Custom Data Flow Component](../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md).</span></span>  
  
##  <a name="example-1-parsing-row-delimited-records"></a><a name="example1"></a> <span data-ttu-id="6f378-108">範例 1：剖析以資料列分隔的記錄</span><span class="sxs-lookup"><span data-stu-id="6f378-108">Example 1: Parsing Row-Delimited Records</span></span>  
 <span data-ttu-id="6f378-109">這則範例將示範如何取得每個資料行都以個別行顯示的文字檔案，並且使用指令碼元件，將它剖析成目的地資料表。</span><span class="sxs-lookup"><span data-stu-id="6f378-109">This example shows how to take a text file in which each column of data appears on a separate line and parse it into a destination table by using the Script component.</span></span>  
  
 <span data-ttu-id="6f378-110">如需如何設定腳本元件做為資料流程中的轉換的詳細資訊，請參閱[使用腳本元件建立同步轉換](../extending-packages-scripting-data-flow-script-component-types/creating-a-synchronous-transformation-with-the-script-component.md)和[使用腳本元件建立異步轉換](../extending-packages-scripting-data-flow-script-component-types/creating-an-asynchronous-transformation-with-the-script-component.md)。</span><span class="sxs-lookup"><span data-stu-id="6f378-110">For more information about how to configure the Script component for use as a transformation in the data flow, see [Creating a Synchronous Transformation with the Script Component](../extending-packages-scripting-data-flow-script-component-types/creating-a-synchronous-transformation-with-the-script-component.md)and [Creating an Asynchronous Transformation with the Script Component](../extending-packages-scripting-data-flow-script-component-types/creating-an-asynchronous-transformation-with-the-script-component.md).</span></span>  
  
#### <a name="to-configure-this-script-component-example"></a><span data-ttu-id="6f378-111">設定此指令碼元件範例</span><span class="sxs-lookup"><span data-stu-id="6f378-111">To configure this Script Component example</span></span>  
  
1.  <span data-ttu-id="6f378-112">建立並儲存名為 **rowdelimiteddata.txt** 的文字檔案，其中包含下列來源資料：</span><span class="sxs-lookup"><span data-stu-id="6f378-112">Create and save a text file named **rowdelimiteddata.txt** that contains the following source data:</span></span>  
  
    ```  
    FirstName: Nancy  
    LastName: Davolio  
    Title: Sales Representative  
    City: Seattle  
    StateProvince: WA  
  
    FirstName: Andrew  
    LastName: Fuller  
    Title: Vice President, Sales  
    City: Tacoma  
    StateProvince: WA  
  
    FirstName: Steven  
    LastName: Buchanan  
    Title: Sales Manager  
    City: London  
    StateProvince:  
  
    ```  
  
2.  <span data-ttu-id="6f378-113">開啟 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 並連接至 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="6f378-113">Open [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] and connect to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
3.  <span data-ttu-id="6f378-114">選取目的地資料庫，並且開啟新的查詢視窗。</span><span class="sxs-lookup"><span data-stu-id="6f378-114">Select a destination database, and open a new query window.</span></span> <span data-ttu-id="6f378-115">在查詢視窗中，執行下列指令碼來建立目的地資料表：</span><span class="sxs-lookup"><span data-stu-id="6f378-115">In the query window, execute the following script to create the destination table:</span></span>  
  
    ```  
    create table RowDelimitedData  
    (  
    FirstName varchar(32),  
    LastName varchar(32),  
    Title varchar(32),  
    City varchar(32),  
    StateProvince varchar(32)  
    )  
  
    ```  
  
4.  <span data-ttu-id="6f378-116">開啟 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] 並建立名為 ParseRowDelim.dtsx 的新 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 封裝。</span><span class="sxs-lookup"><span data-stu-id="6f378-116">Open [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] and create a new [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package named ParseRowDelim.dtsx.</span></span>  
  
5.  <span data-ttu-id="6f378-117">將一般檔案連接管理員加入至此封裝、將它命名為 RowDelimitedData，並且將它設定為連接至您在先前步驟中建立的 rowdelimiteddata.txt 檔案。</span><span class="sxs-lookup"><span data-stu-id="6f378-117">Add a Flat File connection manager to the package, name it RowDelimitedData, and configure it to connect to the rowdelimiteddata.txt file that you created in a previous step.</span></span>  
  
6.  <span data-ttu-id="6f378-118">將 OLE DB 連接管理員加入至此封裝，並且將它設定為連接至 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的執行個體以及您在其中建立目的地資料表的資料庫。</span><span class="sxs-lookup"><span data-stu-id="6f378-118">Add an OLE DB connection manager to the package and configure it to connect to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and the database in which you created the destination table.</span></span>  
  
7.  <span data-ttu-id="6f378-119">將資料流程工作新增至套件，然後按一下 SSIS 設計工具的 [資料流程]  索引標籤。</span><span class="sxs-lookup"><span data-stu-id="6f378-119">Add a Data Flow task to the package and click the **Data Flow** tab of SSIS Designer.</span></span>  
  
8.  <span data-ttu-id="6f378-120">將一般檔案來源加入至資料流程，並且將它設定為使用 RowDelimitedData 連接管理員。</span><span class="sxs-lookup"><span data-stu-id="6f378-120">Add a Flat File Source to the data flow and configure it to use the RowDelimitedData connection manager.</span></span> <span data-ttu-id="6f378-121">在 [一般檔案來源編輯器] 的 [資料行] 頁面上，選取單一可用的外部資料行。</span><span class="sxs-lookup"><span data-stu-id="6f378-121">On the **Columns** page of the **Flat File Source Editor**, select the single available external column.</span></span>  
  
9. <span data-ttu-id="6f378-122">將指令碼元件加入至資料流程並將它設定為轉換。</span><span class="sxs-lookup"><span data-stu-id="6f378-122">Add a Script Component to the data flow and configure it as a transformation.</span></span> <span data-ttu-id="6f378-123">將一般檔案來源的輸出連接至指令碼元件。</span><span class="sxs-lookup"><span data-stu-id="6f378-123">Connect the output of the Flat File Source to the Script Component.</span></span>  
  
10. <span data-ttu-id="6f378-124">按兩下指令碼元件，以顯示 [指令碼轉換編輯器]  。</span><span class="sxs-lookup"><span data-stu-id="6f378-124">Double-click the Script component to display the **Script Transformation Editor**.</span></span>  
  
11. <span data-ttu-id="6f378-125">在 [指令碼轉換編輯器] 的 [輸入資料行] 頁面上，選取單一可用的輸入資料行。</span><span class="sxs-lookup"><span data-stu-id="6f378-125">On the **Input Columns** page of the **Script Transformation Editor**, select the single available input column.</span></span>  
  
12. <span data-ttu-id="6f378-126">在 [**腳本轉換編輯器**] 的 [**輸入和輸出**] 頁面上，選取 [輸出 0]，並將其設定 `SynchronousInputID` 為 [無]。</span><span class="sxs-lookup"><span data-stu-id="6f378-126">On the **Inputs and Outputs** page of the **Script Transformation Editor**, select Output 0 and set its `SynchronousInputID` to None.</span></span> <span data-ttu-id="6f378-127">建立 5 個輸出資料行，全部都屬於字串 [DT_STR] 類型而且長度為 32：</span><span class="sxs-lookup"><span data-stu-id="6f378-127">Create 5 output columns, all of type string [DT_STR] with a length of 32:</span></span>  
  
    -   <span data-ttu-id="6f378-128">名字</span><span class="sxs-lookup"><span data-stu-id="6f378-128">FirstName</span></span>  
  
    -   <span data-ttu-id="6f378-129">姓氏</span><span class="sxs-lookup"><span data-stu-id="6f378-129">LastName</span></span>  
  
    -   <span data-ttu-id="6f378-130">Title</span><span class="sxs-lookup"><span data-stu-id="6f378-130">Title</span></span>  
  
    -   <span data-ttu-id="6f378-131">City</span><span class="sxs-lookup"><span data-stu-id="6f378-131">City</span></span>  
  
    -   <span data-ttu-id="6f378-132">StateProvince</span><span class="sxs-lookup"><span data-stu-id="6f378-132">StateProvince</span></span>  
  
13. <span data-ttu-id="6f378-133">在 [**腳本轉換編輯器**] 的 [**腳本**] 頁面上，按一下 [**編輯腳本**]，然後輸入範例的類別中所顯示的程式碼 `ScriptMain` 。</span><span class="sxs-lookup"><span data-stu-id="6f378-133">On the **Script** page of the **Script Transformation Editor**, click **Edit Script** and enter the code shown in the `ScriptMain` class of the example.</span></span> <span data-ttu-id="6f378-134">關閉指令碼開發環境以及 [指令碼轉換編輯器]  。</span><span class="sxs-lookup"><span data-stu-id="6f378-134">Close the script development environment and the **Script Transformation Editor**.</span></span>  
  
14. <span data-ttu-id="6f378-135">將 SQL Server 目的地加入至資料流程。</span><span class="sxs-lookup"><span data-stu-id="6f378-135">Add a SQL Server Destination to the data flow.</span></span> <span data-ttu-id="6f378-136">將它設定為使用 OLE DB 連接管理員和 RowDelimitedData 資料表。</span><span class="sxs-lookup"><span data-stu-id="6f378-136">Configure it to use the OLE DB connection manager and the RowDelimitedData table.</span></span> <span data-ttu-id="6f378-137">將指令碼元件的輸出連接至這個目的地。</span><span class="sxs-lookup"><span data-stu-id="6f378-137">Connect the output of the Script Component to this destination.</span></span>  
  
15. <span data-ttu-id="6f378-138">執行封裝。</span><span class="sxs-lookup"><span data-stu-id="6f378-138">Run the package.</span></span> <span data-ttu-id="6f378-139">封裝完成之後，檢查 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 目的地資料表中的記錄。</span><span class="sxs-lookup"><span data-stu-id="6f378-139">After the package has finished, examine the records in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] destination table.</span></span>  
  
```vb  
Public Overrides Sub Input0_ProcessInputRow(ByVal Row As Input0Buffer)  
  
    Dim columnName As String  
    Dim columnValue As String  
  
    ' Check for an empty row.  
    If Row.Column0.Trim.Length > 0 Then  
        columnName = Row.Column0.Substring(0, Row.Column0.IndexOf(":"))  
        ' Check for an empty value after the colon.  
        If Row.Column0.Substring(Row.Column0.IndexOf(":")).TrimEnd.Length > 1 Then  
            ' Extract the column value from after the colon and space.  
            columnValue = Row.Column0.Substring(Row.Column0.IndexOf(":") + 2)  
            Select Case columnName  
                Case "FirstName"  
                    ' The FirstName value indicates a new record.  
                    Me.Output0Buffer.AddRow()  
                    Me.Output0Buffer.FirstName = columnValue  
                Case "LastName"  
                    Me.Output0Buffer.LastName = columnValue  
                Case "Title"  
                    Me.Output0Buffer.Title = columnValue  
                Case "City"  
                    Me.Output0Buffer.City = columnValue  
                Case "StateProvince"  
                    Me.Output0Buffer.StateProvince = columnValue  
            End Select  
        End If  
    End If  
  
End Sub  
```  
  
```csharp  
public override void Input0_ProcessInputRow(Input0Buffer Row)  
    {  
  
        string columnName;  
        string columnValue;  
  
        // Check for an empty row.  
        if (Row.Column0.Trim().Length > 0)  
        {  
            columnName = Row.Column0.Substring(0, Row.Column0.IndexOf(":"));  
            // Check for an empty value after the colon.  
            if (Row.Column0.Substring(Row.Column0.IndexOf(":")).TrimEnd().Length > 1)  
            // Extract the column value from after the colon and space.  
            {  
                columnValue = Row.Column0.Substring(Row.Column0.IndexOf(":") + 2);  
                switch (columnName)  
                {  
                    case "FirstName":  
                        // The FirstName value indicates a new record.  
                        this.Output0Buffer.AddRow();  
                        this.Output0Buffer.FirstName = columnValue;  
                        break;  
                    case "LastName":  
                        this.Output0Buffer.LastName = columnValue;  
                        break;  
                    case "Title":  
                        this.Output0Buffer.Title = columnValue;  
                        break;  
                    case "City":  
                        this.Output0Buffer.City = columnValue;  
                        break;  
                    case "StateProvince":  
                        this.Output0Buffer.StateProvince = columnValue;  
                        break;  
                }  
            }  
        }  
  
    }  
```  
  
##  <a name="example-2-splitting-parent-and-child-records"></a><a name="example2"></a> <span data-ttu-id="6f378-140">範例 2：分割父記錄和子記錄</span><span class="sxs-lookup"><span data-stu-id="6f378-140">Example 2: Splitting Parent and Child Records</span></span>  
 <span data-ttu-id="6f378-141">這則範例將示範如何取得文字檔案 (分隔符號資料列位於父記錄資料列前面，而且後面接著不定數目的子記錄資料列)，並且使用指令碼元件，將它剖析成適當正規化的父和子目的地資料表。</span><span class="sxs-lookup"><span data-stu-id="6f378-141">This example shows how to take a text file, in which a separator row precedes a parent record row that is followed by an indefinite number of child record rows, and parse it into properly normalized parent and child destination tables by using the Script component.</span></span> <span data-ttu-id="6f378-142">您可以針對每筆父記錄和子記錄使用多個資料列或資料行的來源檔案輕鬆地調整這則簡單範例，只要存在可識別每筆記錄之開頭和結尾的方式即可。</span><span class="sxs-lookup"><span data-stu-id="6f378-142">This simple example could easily be adapted for source files that use more than one row or column for each parent and child record, as long as there is some way to identify the beginning and end of each record.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="6f378-143">這則範例僅供示範使用。</span><span class="sxs-lookup"><span data-stu-id="6f378-143">This sample is intended for demonstration purposes only.</span></span> <span data-ttu-id="6f378-144">如果您執行此範例多次，它就會將重複的索引鍵值插入目的地資料表中。</span><span class="sxs-lookup"><span data-stu-id="6f378-144">If you run the sample more than once, it inserts duplicate key values into the destination table.</span></span>  
  
 <span data-ttu-id="6f378-145">如需如何設定腳本元件做為資料流程中的轉換的詳細資訊，請參閱[使用腳本元件建立同步轉換](../extending-packages-scripting-data-flow-script-component-types/creating-a-synchronous-transformation-with-the-script-component.md)和[使用腳本元件建立異步轉換](../extending-packages-scripting-data-flow-script-component-types/creating-an-asynchronous-transformation-with-the-script-component.md)。</span><span class="sxs-lookup"><span data-stu-id="6f378-145">For more information about how to configure the Script component for use as a transformation in the data flow, see [Creating a Synchronous Transformation with the Script Component](../extending-packages-scripting-data-flow-script-component-types/creating-a-synchronous-transformation-with-the-script-component.md)and [Creating an Asynchronous Transformation with the Script Component](../extending-packages-scripting-data-flow-script-component-types/creating-an-asynchronous-transformation-with-the-script-component.md).</span></span>  
  
#### <a name="to-configure-this-script-component-example"></a><span data-ttu-id="6f378-146">設定此指令碼元件範例</span><span class="sxs-lookup"><span data-stu-id="6f378-146">To configure this Script Component example</span></span>  
  
1.  <span data-ttu-id="6f378-147">建立並儲存名為 **parentchilddata.txt** 的文字檔案，其中包含下列來源資料：</span><span class="sxs-lookup"><span data-stu-id="6f378-147">Create and save a text file named **parentchilddata.txt** that contains the following source data:</span></span>  
  
    ```  
    **********  
    PARENT 1 DATA  
    child 1 data  
    child 2 data  
    child 3 data  
    child 4 data  
    **********  
    PARENT 2 DATA  
    child 5 data  
    child 6 data  
    child 7 data  
    child 8 data  
    **********  
  
    ```  
  
2.  <span data-ttu-id="6f378-148">開啟 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 並連接至 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="6f378-148">Open [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] and connect to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
3.  <span data-ttu-id="6f378-149">選取目的地資料庫，並且開啟新的查詢視窗。</span><span class="sxs-lookup"><span data-stu-id="6f378-149">Select a destination database, and open a new query window.</span></span> <span data-ttu-id="6f378-150">在查詢視窗中，執行下列指令碼來建立目的地資料表：</span><span class="sxs-lookup"><span data-stu-id="6f378-150">In the query window, execute the following script to create the destination tables:</span></span>  
  
    ```  
    CREATE TABLE [dbo].[Parents]([ParentID] [int] NOT NULL,  
    [ParentRecord] [varchar](32) NOT NULL,  
     CONSTRAINT [PK_Parents] PRIMARY KEY CLUSTERED   
    ([ParentID] ASC))  
    GO  
    CREATE TABLE [dbo].[Children]([ChildID] [int] NOT NULL,  
    [ParentID] [int] NOT NULL,  
    [ChildRecord] [varchar](32) NOT NULL,  
     CONSTRAINT [PK_Children] PRIMARY KEY CLUSTERED   
    ([ChildID] ASC))  
    GO  
    ALTER TABLE [dbo].[Children] ADD CONSTRAINT [FK_Children_Parents] FOREIGN KEY([ParentID])  
    REFERENCES [dbo].[Parents] ([ParentID])  
  
    ```  
  
4.  <span data-ttu-id="6f378-151">開啟 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 並建立名為 SplitParentChild.dtsx 的新 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 封裝。</span><span class="sxs-lookup"><span data-stu-id="6f378-151">Open [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] and create a new [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package named SplitParentChild.dtsx.</span></span>  
  
5.  <span data-ttu-id="6f378-152">將一般檔案連接管理員加入至此封裝、將它命名為 ParentChildData，並且將它設定為連接至您在先前步驟中建立的 parentchilddata.txt 檔案。</span><span class="sxs-lookup"><span data-stu-id="6f378-152">Add a Flat File connection manager to the package, name it ParentChildData, and configure it to connect to the parentchilddata.txt file that you created in a previous step.</span></span>  
  
6.  <span data-ttu-id="6f378-153">將 OLE DB 連接管理員加入至此封裝，並且將它設定為連接至 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的執行個體以及您在其中建立目的地資料表的資料庫。</span><span class="sxs-lookup"><span data-stu-id="6f378-153">Add an OLE DB connection manager to the package and configure it to connect to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and the database in which you created the destination tables.</span></span>  
  
7.  <span data-ttu-id="6f378-154">將資料流程工作新增至套件，然後按一下 SSIS 設計工具的 [資料流程]  索引標籤。</span><span class="sxs-lookup"><span data-stu-id="6f378-154">Add a Data Flow task to the package and click the **Data Flow** tab of SSIS Designer.</span></span>  
  
8.  <span data-ttu-id="6f378-155">將一般檔案來源加入至資料流程，並且將它設定為使用 ParentChildData 連接管理員。</span><span class="sxs-lookup"><span data-stu-id="6f378-155">Add a Flat File Source to the data flow and configure it to use the ParentChildData connection manager.</span></span> <span data-ttu-id="6f378-156">在 [一般檔案來源編輯器] 的 [資料行] 頁面上，選取單一可用的外部資料行。</span><span class="sxs-lookup"><span data-stu-id="6f378-156">On the **Columns** page of the **Flat File Source Editor**, select the single available external column.</span></span>  
  
9. <span data-ttu-id="6f378-157">將指令碼元件加入至資料流程並將它設定為轉換。</span><span class="sxs-lookup"><span data-stu-id="6f378-157">Add a Script Component to the data flow and configure it as a transformation.</span></span> <span data-ttu-id="6f378-158">將一般檔案來源的輸出連接至指令碼元件。</span><span class="sxs-lookup"><span data-stu-id="6f378-158">Connect the output of the Flat File Source to the Script Component.</span></span>  
  
10. <span data-ttu-id="6f378-159">按兩下指令碼元件，以顯示 [指令碼轉換編輯器]  。</span><span class="sxs-lookup"><span data-stu-id="6f378-159">Double-click the Script component to display the **Script Transformation Editor**.</span></span>  
  
11. <span data-ttu-id="6f378-160">在 [指令碼轉換編輯器] 的 [輸入資料行] 頁面上，選取單一可用的輸入資料行。</span><span class="sxs-lookup"><span data-stu-id="6f378-160">On the **Input Columns** page of the **Script Transformation Editor**, select the single available input column.</span></span>  
  
12. <span data-ttu-id="6f378-161">在 [**腳本轉換編輯器**] 的 [**輸入和輸出**] 頁面上，選取 [輸出 0]，將它重新命名為 ParentRecords，並將其設定 `SynchronousInputID` 為 [無]。</span><span class="sxs-lookup"><span data-stu-id="6f378-161">On the **Inputs and Outputs** page of the **Script Transformation Editor**, select Output 0, rename it to ParentRecords, and set its `SynchronousInputID` to None.</span></span> <span data-ttu-id="6f378-162">建立 2 個輸出資料行：</span><span class="sxs-lookup"><span data-stu-id="6f378-162">Create 2 output columns:</span></span>  
  
    -   <span data-ttu-id="6f378-163">ParentID (主索引鍵)，屬於四位元組帶正負號的整數 [DT_I4] 類型</span><span class="sxs-lookup"><span data-stu-id="6f378-163">ParentID (the primary key), of type four-byte signed integer [DT_I4]</span></span>  
  
    -   <span data-ttu-id="6f378-164">ParentRecord，屬於字串 [DT_STR] 類型而且長度為 32</span><span class="sxs-lookup"><span data-stu-id="6f378-164">ParentRecord, of type string [DT_STR] with a length of 32.</span></span>  
  
13. <span data-ttu-id="6f378-165">建立第二個輸出並將它命名為 ChildRecords。</span><span class="sxs-lookup"><span data-stu-id="6f378-165">Create a second output and name it ChildRecords.</span></span> <span data-ttu-id="6f378-166">新輸出的 `SynchronousInputID` 已經設定為 None。</span><span class="sxs-lookup"><span data-stu-id="6f378-166">The `SynchronousInputID` of the new output is already set to None.</span></span> <span data-ttu-id="6f378-167">建立 3 個輸出資料行：</span><span class="sxs-lookup"><span data-stu-id="6f378-167">Create 3 output columns:</span></span>  
  
    -   <span data-ttu-id="6f378-168">ChildID (主索引鍵)，屬於四位元組帶正負號的整數 [DT_I4] 類型</span><span class="sxs-lookup"><span data-stu-id="6f378-168">ChildID (the primary key), of type four-byte signed integer [DT_I4]</span></span>  
  
    -   <span data-ttu-id="6f378-169">ParentID (外部索引鍵)，也屬於四位元組帶正負號的整數 [DT_I4] 類型</span><span class="sxs-lookup"><span data-stu-id="6f378-169">ParentID (the foreign key), also of type four-byte signed integer [DT_I4]</span></span>  
  
    -   <span data-ttu-id="6f378-170">ChildRecord，屬於字串 [DT_STR] 類型而且長度為 50</span><span class="sxs-lookup"><span data-stu-id="6f378-170">ChildRecord, of type string [DT_STR] with a length of 50</span></span>  
  
14. <span data-ttu-id="6f378-171">在 [指令碼轉換編輯器] 的 [指令碼] 頁面上，按一下 [編輯指令碼]。</span><span class="sxs-lookup"><span data-stu-id="6f378-171">On the **Script** page of the **Script Transformation Editor**, click **Edit Script**.</span></span> <span data-ttu-id="6f378-172">在 `ScriptMain` 類別中，輸入此範例中所示的程式碼。</span><span class="sxs-lookup"><span data-stu-id="6f378-172">In the `ScriptMain` class, enter the code shown in the example.</span></span> <span data-ttu-id="6f378-173">關閉指令碼開發環境以及 [指令碼轉換編輯器]  。</span><span class="sxs-lookup"><span data-stu-id="6f378-173">Close the script development environment and the **Script Transformation Editor**.</span></span>  
  
15. <span data-ttu-id="6f378-174">將 SQL Server 目的地加入至資料流程。</span><span class="sxs-lookup"><span data-stu-id="6f378-174">Add a SQL Server Destination to the data flow.</span></span> <span data-ttu-id="6f378-175">將指令碼元件的 ParentRecords 輸出連接至這個目的地。將它設定為使用 OLE DB 連接管理員和 Parents 資料表。</span><span class="sxs-lookup"><span data-stu-id="6f378-175">Connect the ParentRecords output of the Script Component to this destination.Configure it to use the OLE DB connection manager and the Parents table.</span></span>  
  
16. <span data-ttu-id="6f378-176">將另一個 SQL Server 目的地加入至資料流程。</span><span class="sxs-lookup"><span data-stu-id="6f378-176">Add another SQL Server Destination to the data flow.</span></span> <span data-ttu-id="6f378-177">將指令碼元件的 ChildRecords 輸出連接至這個目的地。</span><span class="sxs-lookup"><span data-stu-id="6f378-177">Connect the ChildRecords output of the Script Component to this destination.</span></span> <span data-ttu-id="6f378-178">將它設定為使用 OLE DB 連接管理員和 Children 資料表。</span><span class="sxs-lookup"><span data-stu-id="6f378-178">Configure it to use the OLE DB connection manager and the Children table.</span></span>  
  
17. <span data-ttu-id="6f378-179">執行封裝。</span><span class="sxs-lookup"><span data-stu-id="6f378-179">Run the package.</span></span> <span data-ttu-id="6f378-180">封裝完成之後，檢查兩個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 目的地資料表中的父記錄和子記錄。</span><span class="sxs-lookup"><span data-stu-id="6f378-180">After the package has finished, examine the parent and child records in the two [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] destination tables.</span></span>  
  
```vb  
Public Overrides Sub Input0_ProcessInputRow(ByVal Row As Input0Buffer)  
  
    Static nextRowIsParent As Boolean = False  
    Static parentCounter As Integer = 0  
    Static childCounter As Integer = 0  
  
    ' If current row starts with separator characters,  
    '  then following row contains new parent record.  
    If Row.Column0.StartsWith("***") Then  
        nextRowIsParent = True  
    Else  
        If nextRowIsParent Then  
            ' Current row contains parent record.  
            parentCounter += 1  
            Me.ParentRecordsBuffer.AddRow()  
            Me.ParentRecordsBuffer.ParentID = parentCounter  
            Me.ParentRecordsBuffer.ParentRecord = Row.Column0  
            nextRowIsParent = False  
        Else  
            ' Current row contains child record.  
            childCounter += 1  
            Me.ChildRecordsBuffer.AddRow()  
            Me.ChildRecordsBuffer.ChildID = childCounter  
            Me.ChildRecordsBuffer.ParentID = parentCounter  
            Me.ChildRecordsBuffer.ChildRecord = Row.Column0  
        End If  
    End If  
  
End Sub  
```  
  
```csharp  
public override void Input0_ProcessInputRow(Input0Buffer Row)  
    {  
  
    int static_Input0_ProcessInputRow_childCounter = 0;  
    int static_Input0_ProcessInputRow_parentCounter = 0;  
    bool static_Input0_ProcessInputRow_nextRowIsParent = false;  
  
        // If current row starts with separator characters,   
        // then following row contains new parent record.   
        if (Row.Column0.StartsWith("***"))  
        {  
            static_Input0_ProcessInputRow_nextRowIsParent = true;  
        }  
        else  
        {  
            if (static_Input0_ProcessInputRow_nextRowIsParent)  
            {  
                // Current row contains parent record.   
                static_Input0_ProcessInputRow_parentCounter += 1;  
                this.ParentRecordsBuffer.AddRow();  
                this.ParentRecordsBuffer.ParentID = static_Input0_ProcessInputRow_parentCounter;  
                this.ParentRecordsBuffer.ParentRecord = Row.Column0;  
                static_Input0_ProcessInputRow_nextRowIsParent = false;  
            }  
            else  
            {  
                // Current row contains child record.   
                static_Input0_ProcessInputRow_childCounter += 1;  
                this.ChildRecordsBuffer.AddRow();  
                this.ChildRecordsBuffer.ChildID = static_Input0_ProcessInputRow_childCounter;  
                this.ChildRecordsBuffer.ParentID = static_Input0_ProcessInputRow_parentCounter;  
                this.ChildRecordsBuffer.ChildRecord = Row.Column0;  
            }  
        }  
  
    }  
```  
  
<span data-ttu-id="6f378-181">![Integration Services 圖示 (小型) ](../media/dts-16.gif "Integration Services 圖示 (小)")會**保持最**新狀態 Integration Services  </span><span class="sxs-lookup"><span data-stu-id="6f378-181">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="6f378-182">若要取得 Microsoft 的最新下載、文件、範例和影片以及社群中的精選解決方案，請瀏覽 MSDN 上的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 頁面：</span><span class="sxs-lookup"><span data-stu-id="6f378-182">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="6f378-183">瀏覽 MSDN 上的 Integration Services 頁面</span><span class="sxs-lookup"><span data-stu-id="6f378-183">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="6f378-184">若要得到這些更新的自動通知，請訂閱該頁面上所提供的 RSS 摘要。</span><span class="sxs-lookup"><span data-stu-id="6f378-184">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f378-185">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6f378-185">See Also</span></span>  
 [<span data-ttu-id="6f378-186">使用指令碼元件建立同步轉換</span><span class="sxs-lookup"><span data-stu-id="6f378-186">Creating a Synchronous Transformation with the Script Component</span></span>](../extending-packages-scripting-data-flow-script-component-types/creating-a-synchronous-transformation-with-the-script-component.md)  
 [<span data-ttu-id="6f378-187">使用指令碼元件建立非同步轉換</span><span class="sxs-lookup"><span data-stu-id="6f378-187">Creating an Asynchronous Transformation with the Script Component</span></span>](../extending-packages-scripting-data-flow-script-component-types/creating-an-asynchronous-transformation-with-the-script-component.md)  
  
  
