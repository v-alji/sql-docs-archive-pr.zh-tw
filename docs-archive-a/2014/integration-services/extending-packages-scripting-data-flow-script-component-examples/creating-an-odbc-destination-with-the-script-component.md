---
title: 使用指令碼元件建立 ODBC 目的地 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- Script component [Integration Services], destination components
- ODBC destination [Integration Services]
- destinations [Integration Services], components
- Script component [Integration Services], examples
ms.assetid: d198c866-78f4-4a50-ae15-333160645815
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 10adff11a7e1db24d9a244c3e83949a010b606c7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597221"
---
# <a name="creating-an-odbc-destination-with-the-script-component"></a><span data-ttu-id="0b5cf-102">使用指令碼元件建立 ODBC 目的地</span><span class="sxs-lookup"><span data-stu-id="0b5cf-102">Creating an ODBC Destination with the Script Component</span></span>
  <span data-ttu-id="0b5cf-103">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 中，您通常會使用 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 目的地與 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] Data Provider for ODB 來將資料儲存到 ODBC 目的地。</span><span class="sxs-lookup"><span data-stu-id="0b5cf-103">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], you typically save data to an ODBC destination by using an [!INCLUDE[vstecado](../../includes/vstecado-md.md)] destination and the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] Data Provider for ODBC.</span></span> <span data-ttu-id="0b5cf-104">不過，您也可以建立在單一封裝中要使用的特定 ODBC 目的地。</span><span class="sxs-lookup"><span data-stu-id="0b5cf-104">However, you can also create an ad hoc ODBC destination for use in a single package.</span></span> <span data-ttu-id="0b5cf-105">若要建立這個特定的 ODBC 目的地，可以使用如下列範例所示的指令碼元件。</span><span class="sxs-lookup"><span data-stu-id="0b5cf-105">To create this ad hoc ODBC destination, you use the Script component as shown in the following example.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0b5cf-106">如果您要建立可以更輕鬆地在多個資料流程工作與多個封裝之間重複使用的元件，請考慮使用這個指令碼元件範例中的程式碼，做為自訂資料流程元件的起點。</span><span class="sxs-lookup"><span data-stu-id="0b5cf-106">If you want to create a component that you can more easily reuse across multiple Data Flow tasks and multiple packages, consider using the code in this Script component sample as the starting point for a custom data flow component.</span></span> <span data-ttu-id="0b5cf-107">如需詳細資訊，請參閱 [開發自訂資料流程元件](../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md)。</span><span class="sxs-lookup"><span data-stu-id="0b5cf-107">For more information, see [Developing a Custom Data Flow Component](../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0b5cf-108">範例</span><span class="sxs-lookup"><span data-stu-id="0b5cf-108">Example</span></span>  
 <span data-ttu-id="0b5cf-109">下列範例示範如何建立一個目的地元件，以使用現有的 ODBC 連線管理員來將資料從資料流程儲存到 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料表。</span><span class="sxs-lookup"><span data-stu-id="0b5cf-109">The following example demonstrates how to create a destination component that uses an existing ODBC connection manager to save data from the data flow into a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span>  
  
 <span data-ttu-id="0b5cf-110">此範例是[使用指令碼元件建立目的地](../extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md)主題中所示範的自訂 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 目的地之修改版本。</span><span class="sxs-lookup"><span data-stu-id="0b5cf-110">This example is a modified version of the custom [!INCLUDE[vstecado](../../includes/vstecado-md.md)] destination that was demonstrated in the topic, [Creating a Destination with the Script Component](../extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md).</span></span> <span data-ttu-id="0b5cf-111">不過，在這個範例中，已修改自訂 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 目的地以搭配 ODBC 連接管理員使用，並將資料儲存到 ODBC 目的地。</span><span class="sxs-lookup"><span data-stu-id="0b5cf-111">However, in this example, the custom [!INCLUDE[vstecado](../../includes/vstecado-md.md)] destination has been modified to work with an ODBC connection manager and save data to an ODBC destination.</span></span> <span data-ttu-id="0b5cf-112">這些修改也包括下列變更：</span><span class="sxs-lookup"><span data-stu-id="0b5cf-112">These modifications also include the following changes:</span></span>  
  
-   <span data-ttu-id="0b5cf-113">您無法從 Managed 程式碼呼叫 ODBC 連接管理員的 `AcquireConnection` 方法，因為它會傳回原生物件。</span><span class="sxs-lookup"><span data-stu-id="0b5cf-113">You cannot call the `AcquireConnection` method of the ODBC connection manager from managed code, because it returns a native object.</span></span> <span data-ttu-id="0b5cf-114">因此，這個範例使用連接管理員的連接字串以 Managed ODBC [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 資料提供者直接連到資料來源。</span><span class="sxs-lookup"><span data-stu-id="0b5cf-114">Therefore, this sample uses the connection string of the connection manager to connect to the data source directly by using the managed ODBC [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] Data Provider.</span></span>  
  
-   <span data-ttu-id="0b5cf-115">`OdbcCommand` 需要位置參數。</span><span class="sxs-lookup"><span data-stu-id="0b5cf-115">The `OdbcCommand` expects positional parameters.</span></span> <span data-ttu-id="0b5cf-116">參數的位置由命令文字中的問號 (?) 指出</span><span class="sxs-lookup"><span data-stu-id="0b5cf-116">The positions of the parameters are indicated by the question marks (?) in the text of the command.</span></span> <span data-ttu-id="0b5cf-117">(相較之下，`SqlCommand` 需要具名的參數)。</span><span class="sxs-lookup"><span data-stu-id="0b5cf-117">(In contrast, a `SqlCommand` expects named parameters.)</span></span>  
  
 <span data-ttu-id="0b5cf-118">此範例使用 **AdventureWorks** 範例資料庫中的 **Person.Address** 資料表。</span><span class="sxs-lookup"><span data-stu-id="0b5cf-118">This example uses the **Person.Address** table in the **AdventureWorks** sample database.</span></span> <span data-ttu-id="0b5cf-119">此範例會透過資料流程傳遞第一個和第四個數據行，也就是這個資料表的**int \* AddressID**\* 和**Nvarchar (30) City**資料行。</span><span class="sxs-lookup"><span data-stu-id="0b5cf-119">The example passes the first and fourth columns, the **int\*AddressID**\* and **nvarchar(30)City** columns, of this table through the data flow.</span></span> <span data-ttu-id="0b5cf-120">在[開發特定類型的指令碼元件](../extending-packages-scripting-data-flow-script-component-types/developing-specific-types-of-script-components.md)主題中，這個相同的資料用於來源、轉換和目的地範例中。</span><span class="sxs-lookup"><span data-stu-id="0b5cf-120">This same data is used in the source, transformation, and destination samples in the topic, [Developing Specific Types of Script Components](../extending-packages-scripting-data-flow-script-component-types/developing-specific-types-of-script-components.md).</span></span>  
  
#### <a name="to-configure-this-script-component-example"></a><span data-ttu-id="0b5cf-121">設定此指令碼元件範例</span><span class="sxs-lookup"><span data-stu-id="0b5cf-121">To configure this Script Component example</span></span>  
  
1.  <span data-ttu-id="0b5cf-122">建立 ODBC 連線管理員，以連線至 **AdventureWorks** 資料庫。</span><span class="sxs-lookup"><span data-stu-id="0b5cf-122">Create an ODBC connection manager that connects to the **AdventureWorks** database.</span></span>  
  
2.  <span data-ttu-id="0b5cf-123">在 **AdventureWorks** 資料庫中執行下列 Transact-SQL 命令，以建立目的地資料表：</span><span class="sxs-lookup"><span data-stu-id="0b5cf-123">Create a destination table by running the following Transact-SQL command in the **AdventureWorks** database:</span></span>  
  
    ```  
    CREATE TABLE [Person].[Address2]([AddressID] [int] NOT NULL,  
        [City] [nvarchar](30) NOT NULL)  
    ```  
  
3.  <span data-ttu-id="0b5cf-124">將新的指令碼元件加入至資料流程設計師介面，並將它設定為目的地。</span><span class="sxs-lookup"><span data-stu-id="0b5cf-124">Add a new Script component to the Data Flow designer surface and configure it as a destination.</span></span>  
  
4.  <span data-ttu-id="0b5cf-125">將上游來源或轉換的輸出連接到 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師中的目的地元件</span><span class="sxs-lookup"><span data-stu-id="0b5cf-125">Connect the output of an upstream source or transformation to the destination component in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="0b5cf-126">(您不需要進行任何轉換，就可以直接將來源連線到目的地。)為了確保這個範例可運作，上游元件的輸出必須至少包含 **AdventureWorks** 範例資料庫中 **Person.Address** 資料表的 **AddressID** 和 **City** 資料行。</span><span class="sxs-lookup"><span data-stu-id="0b5cf-126">(You can connect a source directly to a destination without any transformations.) To ensure that this sample works, the output of the upstream component must include at least the **AddressID** and **City** columns from the **Person.Address** table of the **AdventureWorks** sample database.</span></span>  
  
5.  <span data-ttu-id="0b5cf-127">開啟**指令碼轉換編輯器**。</span><span class="sxs-lookup"><span data-stu-id="0b5cf-127">Open the **Script Transformation Editor**.</span></span> <span data-ttu-id="0b5cf-128">在 [輸入資料行]  頁面上，選取 [AddressID]  與 [City]  資料行。</span><span class="sxs-lookup"><span data-stu-id="0b5cf-128">On the **Input Columns** page, select the **AddressID** and **City** columns.</span></span>  
  
6.  <span data-ttu-id="0b5cf-129">在 [輸入及輸出]  頁面上，以更具描述性的名稱重新命名輸入，例如 **MyAddressInput**。</span><span class="sxs-lookup"><span data-stu-id="0b5cf-129">On the **Inputs and Outputs** page, rename the input with a more descriptive name such as **MyAddressInput**.</span></span>  
  
7.  <span data-ttu-id="0b5cf-130">在 [連線管理員]  頁面上，使用 **MyODBCConnectionManager** 之類的描述性名稱，新增或建立 ODBC 連線管理員。</span><span class="sxs-lookup"><span data-stu-id="0b5cf-130">On the **Connection Managers** page, add or create the ODBC connection manager with a descriptive name such as **MyODBCConnectionManager**.</span></span>  
  
8.  <span data-ttu-id="0b5cf-131">在 [**腳本**] 頁面上，按一下 [**編輯腳本**]，然後在類別中輸入如下所示的腳本 `ScriptMain` 。</span><span class="sxs-lookup"><span data-stu-id="0b5cf-131">On the **Script** page, click **Edit Script**, and then enter the script shown below in the `ScriptMain` class.</span></span>  
  
9. <span data-ttu-id="0b5cf-132">依序關閉指令碼開發環境和**指令碼轉換編輯器**，然後執行此範例。</span><span class="sxs-lookup"><span data-stu-id="0b5cf-132">Close the script development environment, close the **Script Transformation Editor**, and then run the sample.</span></span>  
  
    ```vb  
    Imports System.Data.Odbc  
    ...  
    Public Class ScriptMain  
        Inherits UserComponent  
  
        Dim odbcConn As OdbcConnection  
        Dim odbcCmd As OdbcCommand  
        Dim odbcParam As OdbcParameter  
  
        Public Overrides Sub AcquireConnections(ByVal Transaction As Object)  
  
            Dim connectionString As String  
            connectionString = Me.Connections.MyODBCConnectionManager.ConnectionString  
            odbcConn = New OdbcConnection(connectionString)  
            odbcConn.Open()  
  
        End Sub  
  
        Public Overrides Sub PreExecute()  
  
            odbcCmd = New OdbcCommand("INSERT INTO Person.Address2(AddressID, City) " & _  
                "VALUES(?, ?)", odbcConn)  
            odbcParam = New OdbcParameter("@addressid", OdbcType.Int)  
            odbcCmd.Parameters.Add(odbcParam)  
            odbcParam = New OdbcParameter("@city", OdbcType.NVarChar, 30)  
            odbcCmd.Parameters.Add(odbcParam)  
  
        End Sub  
  
        Public Overrides Sub MyAddressInput_ProcessInputRow(ByVal Row As MyAddressInputBuffer)  
  
            With odbcCmd  
                .Parameters("@addressid").Value = Row.AddressID  
                .Parameters("@city").Value = Row.City  
                .ExecuteNonQuery()  
            End With  
  
        End Sub  
  
        Public Overrides Sub ReleaseConnections()  
  
            odbcConn.Close()  
  
        End Sub  
  
    End Class  
    ```  
  
    ```csharp  
    using System.Data.Odbc;  
    ...  
    public class ScriptMain :  
        UserComponent  
    {  
        OdbcConnection odbcConn;  
        OdbcCommand odbcCmd;  
        OdbcParameter odbcParam;  
  
        public override void AcquireConnections(object Transaction)  
        {  
  
            string connectionString;  
            connectionString = this.Connections.MyODBCConnectionManager.ConnectionString;  
            odbcConn = new OdbcConnection(connectionString);  
            odbcConn.Open();  
  
        }  
  
        public override void PreExecute()  
        {  
  
            odbcCmd = new OdbcCommand("INSERT INTO Person.Address2(AddressID, City) " +  
                "VALUES(?, ?)", odbcConn);  
            odbcParam = new OdbcParameter("@addressid", OdbcType.Int);  
            odbcCmd.Parameters.Add(odbcParam);  
            odbcParam = new OdbcParameter("@city", OdbcType.NVarChar, 30);  
            odbcCmd.Parameters.Add(odbcParam);  
  
        }  
  
        public override void MyAddressInput_ProcessInputRow(MyAddressInputBuffer Row)  
        {  
  
            {  
                odbcCmd.Parameters["@addressid"].Value = Row.AddressID;  
                odbcCmd.Parameters["@city"].Value = Row.City;  
                odbcCmd.ExecuteNonQuery();  
            }  
  
        }  
  
        public override void ReleaseConnections()  
        {  
  
            odbcConn.Close();  
  
        }  
    }  
    ```  
  
<span data-ttu-id="0b5cf-133">![Integration Services 圖示 (小型) ](../media/dts-16.gif "Integration Services 圖示 (小)")會**保持最**新狀態 Integration Services  </span><span class="sxs-lookup"><span data-stu-id="0b5cf-133">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="0b5cf-134">若要取得 Microsoft 的最新下載、文件、範例和影片以及社群中的精選解決方案，請瀏覽 MSDN 上的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 頁面：</span><span class="sxs-lookup"><span data-stu-id="0b5cf-134">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="0b5cf-135">瀏覽 MSDN 上的 Integration Services 頁面</span><span class="sxs-lookup"><span data-stu-id="0b5cf-135">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="0b5cf-136">若要得到這些更新的自動通知，請訂閱該頁面上所提供的 RSS 摘要。</span><span class="sxs-lookup"><span data-stu-id="0b5cf-136">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b5cf-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0b5cf-137">See Also</span></span>  
 [<span data-ttu-id="0b5cf-138">使用指令碼元件建立目的地</span><span class="sxs-lookup"><span data-stu-id="0b5cf-138">Creating a Destination with the Script Component</span></span>](../extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md)  
  
  
