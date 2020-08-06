---
title: 載入本機套件的輸出 | Microsoft Docs
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
- data flow [Integration Services], loading results
- loading data flow results
ms.assetid: aba8ecb7-0dcf-40d0-a2a8-64da0da94b93
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 6799e593ab9d5ae1a9358bf54f4927838991ebd0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707670"
---
# <a name="loading-the-output-of-a-local-package"></a><span data-ttu-id="b44e2-102">載入本機封裝的輸出</span><span class="sxs-lookup"><span data-stu-id="b44e2-102">Loading the Output of a Local Package</span></span>
  <span data-ttu-id="b44e2-103">使用 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 將輸出儲存到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 目的地時，或使用 **System.IO** 命名空間，將輸出儲存到一般檔案目的地時，用戶端應用程式可以讀取 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 套件的輸出。</span><span class="sxs-lookup"><span data-stu-id="b44e2-103">Client applications can read the output of [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages when the output is saved to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] destinations by using [!INCLUDE[vstecado](../../includes/vstecado-md.md)], or when the output is saved to a flat file destination by using the classes in the **System.IO** namespace.</span></span> <span data-ttu-id="b44e2-104">但用戶端應用程式也可直接從記憶體讀取封裝的輸出，而無須在程序中間執行保存資料的步驟。</span><span class="sxs-lookup"><span data-stu-id="b44e2-104">However, a client application can also read the output of a package directly from memory, without the need for an intermediate step to persist the data.</span></span> <span data-ttu-id="b44e2-105">此解決方案的關鍵在於 `Microsoft.SqlServer.Dts.DtsClient` 命名空間，其中包含 `IDbConnection` `IDbCommand` 來自**system.web**命名空間的、和**IDbDataParameter**介面的特製化執行。</span><span class="sxs-lookup"><span data-stu-id="b44e2-105">The key to this solution is the `Microsoft.SqlServer.Dts.DtsClient` namespace, which contains specialized implementations of the `IDbConnection`, `IDbCommand`, and **IDbDataParameter** interfaces from the **System.Data** namespace.</span></span> <span data-ttu-id="b44e2-106">預設會在 **%ProgramFiles%\Microsoft SQL Server\100\DTS\Binn** 中安裝 Microsoft.SqlServer.Dts.DtsClient.dll 組件。</span><span class="sxs-lookup"><span data-stu-id="b44e2-106">The assembly Microsoft.SqlServer.Dts.DtsClient.dll is installed by default in **%ProgramFiles%\Microsoft SQL Server\100\DTS\Binn**.</span></span>

> [!NOTE]
>  <span data-ttu-id="b44e2-107">本主題所述之程序需要將資料流程工作與任何父物件的 DelayValidation 屬性，設定成其預設值 **False**。</span><span class="sxs-lookup"><span data-stu-id="b44e2-107">The procedure described in this topic requires that the DelayValidation property of the Data Flow task and of any parent objects be set to its default value of **False**.</span></span>

## <a name="description"></a><span data-ttu-id="b44e2-108">描述</span><span class="sxs-lookup"><span data-stu-id="b44e2-108">Description</span></span>
 <span data-ttu-id="b44e2-109">這個程序示範如何以 Managed 程式碼開發用戶端應用程式，這個程式碼使用 DataReader 目的地直接從記憶體載入封裝的輸出。</span><span class="sxs-lookup"><span data-stu-id="b44e2-109">This procedure demonstrates how to develop a client application in managed code that loads the output of a package with a DataReader destination directly from memory.</span></span> <span data-ttu-id="b44e2-110">這裡所摘要的步驟將在接下來的程式碼範例中示範。</span><span class="sxs-lookup"><span data-stu-id="b44e2-110">The steps summarized here are demonstrated in the code sample that follows.</span></span>

#### <a name="to-load-data-package-output-into-a-client-application"></a><span data-ttu-id="b44e2-111">將資料封裝輸出載入用戶端應用程式</span><span class="sxs-lookup"><span data-stu-id="b44e2-111">To load data package output into a client application</span></span>

1.  <span data-ttu-id="b44e2-112">在封裝中，設定 DataReader 目的地以接收您要讀到用戶端應用程式中的輸出。</span><span class="sxs-lookup"><span data-stu-id="b44e2-112">In the package, configure a DataReader destination to receive the output that you want to read into the client application.</span></span> <span data-ttu-id="b44e2-113">給 DataReader 目的地一個描述性名稱，因為您稍後將在用戶端應用程式中使用這個名稱。</span><span class="sxs-lookup"><span data-stu-id="b44e2-113">Give the DataReader destination a descriptive name, since you will use this name later in your client application.</span></span> <span data-ttu-id="b44e2-114">記下 DataReader 目的地的名稱。</span><span class="sxs-lookup"><span data-stu-id="b44e2-114">Make a note of the name of the DataReader destination.</span></span>

2.  <span data-ttu-id="b44e2-115">在開發專案中，藉 `Microsoft.SqlServer.Dts.DtsClient` 由找出元件**Microsoft.SqlServer.Dts.DtsClient.dll**來設定命名空間的參考。</span><span class="sxs-lookup"><span data-stu-id="b44e2-115">In the development project, set a reference to the `Microsoft.SqlServer.Dts.DtsClient` namespace by locating the assembly **Microsoft.SqlServer.Dts.DtsClient.dll**.</span></span> <span data-ttu-id="b44e2-116">此組件預設安裝在 **C:\Program Files\Microsoft SQL Server\100\DTS\Binn** 中。</span><span class="sxs-lookup"><span data-stu-id="b44e2-116">By default, this assembly is installed in **C:\Program Files\Microsoft SQL Server\100\DTS\Binn**.</span></span> <span data-ttu-id="b44e2-117">使用 c # 或語句，將命名空間匯入您的程式碼中 `Using` [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] `Imports` 。</span><span class="sxs-lookup"><span data-stu-id="b44e2-117">Import the namespace into your code by using the C# `Using` or the [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] `Imports` statement.</span></span>

3.  <span data-ttu-id="b44e2-118">在您的程式碼中，使用連接字串建立類型的物件， `DtsClient.DtsConnection` 其中包含**dtexec.exe**執行封裝所需的命令列參數。</span><span class="sxs-lookup"><span data-stu-id="b44e2-118">In your code, create an object of type `DtsClient.DtsConnection` with a connection string that contains the command-line parameters required by **dtexec.exe** to run the package.</span></span> <span data-ttu-id="b44e2-119">如需詳細資訊，請參閱 [dtexec Utility](../packages/dtexec-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="b44e2-119">For more information, see [dtexec Utility](../packages/dtexec-utility.md).</span></span> <span data-ttu-id="b44e2-120">然後使用此連接字串開啟連接。</span><span class="sxs-lookup"><span data-stu-id="b44e2-120">Then open the connection with this connection string.</span></span> <span data-ttu-id="b44e2-121">您也可以使用 **dtexecui** 公用程式，以視覺化方式建立所需的連接字串。</span><span class="sxs-lookup"><span data-stu-id="b44e2-121">You can also use the **dtexecui** utility to create the required connection string visually.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="b44e2-122">範例程式碼透過使用 `/FILE <path and filename>` 語法示範從檔案系統載入封裝。</span><span class="sxs-lookup"><span data-stu-id="b44e2-122">The sample code demonstrates loading the package from the file system by using the `/FILE <path and filename>` syntax.</span></span> <span data-ttu-id="b44e2-123">不過，您也可以使用 `/SQL <package name>` 語法從 MSDB 資料庫載入封裝，或是使用 `/DTS \<folder name>\<package name>` 語法從 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 封裝存放區載入。</span><span class="sxs-lookup"><span data-stu-id="b44e2-123">However you can also load the package from the MSDB database by using the `/SQL <package name>` syntax, or from the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package store by using the `/DTS \<folder name>\<package name>` syntax.</span></span>

4.  <span data-ttu-id="b44e2-124">建立類型為 `DtsClient.DtsCommand` 的物件，以使用先前建立的 `DtsConnection` 並將其 `CommandText` 屬性設定為封裝中的 DataReader 目的地名稱。</span><span class="sxs-lookup"><span data-stu-id="b44e2-124">Create an object of type `DtsClient.DtsCommand` that uses the previously created `DtsConnection` and set its `CommandText` property to the name of the DataReader destination in the package.</span></span> <span data-ttu-id="b44e2-125">然後呼叫命令物件的 `ExecuteReader` 方法，將封裝結果載入新的 DataReader。</span><span class="sxs-lookup"><span data-stu-id="b44e2-125">Then call the `ExecuteReader` method of the command object to load the package results into a new DataReader.</span></span>

5.  <span data-ttu-id="b44e2-126">您可以選擇性地使用 `DtsDataParameter` 物件上的 `DtsCommand` 物件集合，間接地參數化封裝輸出，以便將值傳遞給定義在封裝中的變數。</span><span class="sxs-lookup"><span data-stu-id="b44e2-126">Optionally, you can indirectly parameterize the output of the package by using the collection of `DtsDataParameter` objects on the `DtsCommand` object to pass values to variables defined in the package.</span></span> <span data-ttu-id="b44e2-127">您可以在封裝中使用這些變數做為查詢參數，或在運算式中加以運用，藉此影響傳回 DataReader 目的地的結果。</span><span class="sxs-lookup"><span data-stu-id="b44e2-127">Within the package, you can use these variables as query parameters or in expressions to affect the results returned to the DataReader destination.</span></span> <span data-ttu-id="b44e2-128">您必須在**DtsClient**命名空間的封裝中定義這些變數，才能將它們與 `DtsDataParameter` 用戶端應用程式中的物件搭配使用。</span><span class="sxs-lookup"><span data-stu-id="b44e2-128">You must define these variables in the package in the **DtsClient** namespace before you can use them with the `DtsDataParameter` object from a client application.</span></span> <span data-ttu-id="b44e2-129"> (您可能需要按一下 [**變數**] 視窗中的 [**選擇變數資料行**] 工具列按鈕，以顯示**命名空間**資料行。當您在用戶端程式代碼中 ) ，當您將加入至的集合時， `DtsDataParameter` `Parameters` `DtsCommand` 請省略變數名稱中的 DtsClient 命名空間參考。</span><span class="sxs-lookup"><span data-stu-id="b44e2-129">(You may need to click the **Choose Variable Columns** toolbar button in the **Variables** window to display the **Namespace** column.) In your client code, when you add a `DtsDataParameter` to the `Parameters` collection of the `DtsCommand`, omit the DtsClient namespace reference from the variable name.</span></span> <span data-ttu-id="b44e2-130">例如：</span><span class="sxs-lookup"><span data-stu-id="b44e2-130">For example:</span></span>

    ```
    command.Parameters.Add(new DtsDataParameter("MyVariable", 1));
    ```

6.  <span data-ttu-id="b44e2-131">視需要以重複方式呼叫 DataReader 的 `Read` 方法，在輸出資料的資料列中執行迴圈。</span><span class="sxs-lookup"><span data-stu-id="b44e2-131">Call the `Read` method of the DataReader repeatedly as needed to loop through the rows of output data.</span></span> <span data-ttu-id="b44e2-132">在用戶端應用程式中使用資料或是儲存資料以供稍後使用。</span><span class="sxs-lookup"><span data-stu-id="b44e2-132">Use the data, or save the data for later use, in the client application.</span></span>

    > [!IMPORTANT]
    >  <span data-ttu-id="b44e2-133">在讀取最後一列的資料之後，實作 DataReader 的 `Read` 方法會再傳回 `true` 一次。</span><span class="sxs-lookup"><span data-stu-id="b44e2-133">The `Read` method of this implementation of the DataReader returns `true` one more time after the last row of data has been read.</span></span> <span data-ttu-id="b44e2-134">這使得在 `Read` 傳回 `true` 時，難以使用在 DataReader 中執行迴圈的一般程式碼。</span><span class="sxs-lookup"><span data-stu-id="b44e2-134">This makes it difficult to use the usual code that loops through the DataReader while `Read` returns `true`.</span></span> <span data-ttu-id="b44e2-135">如果您的程式碼在讀取預期數目的資料列之後，嘗試關閉 DataReader 或是連接，而沒有額外或最後呼叫 `Read` 方法，則程式碼將引發未處理的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="b44e2-135">If your code attempts to close the DataReader or the connection after reading the expected number of rows, without an additional, final call to the `Read` method, the code will raise an unhandled exception.</span></span> <span data-ttu-id="b44e2-136">不過，如果您的程式碼嘗試在迴圈的這個最後反覆運算中讀取資料，當 `Read` 仍然傳回 `true`，但是已經傳遞最後一個資料列時，則程式碼將會引發未處理的 `ApplicationException`，並產生「SSIS IDataReader 超過結果集的結尾」的訊息。</span><span class="sxs-lookup"><span data-stu-id="b44e2-136">However, if your code attempts to read data on this final iteration through a loop, when `Read` still returns `true` but the last row has been passed, the code will raise an unhandled `ApplicationException` with the message, "The SSIS IDataReader is past the end of the resultset."</span></span> <span data-ttu-id="b44e2-137">這個行為與其他 DataReader 實作的行為不同。</span><span class="sxs-lookup"><span data-stu-id="b44e2-137">This behavior is different from that of other DataReader implementations.</span></span> <span data-ttu-id="b44e2-138">因此，當使用迴圈讀取 DataReader 中的資料列，而 `Read` 傳回 `true` 時，您需要針對最後一次成功地呼叫 `ApplicationException` 方法，來撰寫程式碼以擷取、測試和捨棄這個預期的 `Read`。</span><span class="sxs-lookup"><span data-stu-id="b44e2-138">Therefore, when using a loop to read through the rows in the DataReader while `Read` returns `true`, you need to write code to catch, test, and discard this anticipated `ApplicationException` on the last successful call to the `Read` method.</span></span> <span data-ttu-id="b44e2-139">或者，如果您事先知道預期的資料列數目，就可以處理資料列，然後在關閉 DataReader 與連接之前，再呼叫一次 `Read` 方法。</span><span class="sxs-lookup"><span data-stu-id="b44e2-139">Or, if you know in advance the number of rows expected, you can process the rows, and then call the `Read` method one more time before closing the DataReader and the connection.</span></span>

7.  <span data-ttu-id="b44e2-140">呼叫 `Dispose` 物件的 `DtsCommand` 方法。</span><span class="sxs-lookup"><span data-stu-id="b44e2-140">Call the `Dispose` method of the `DtsCommand` object.</span></span> <span data-ttu-id="b44e2-141">如果您已經使用任何 `DtsDataParameter` 物件，這將特別重要。</span><span class="sxs-lookup"><span data-stu-id="b44e2-141">This is particularly important if you have used any `DtsDataParameter` objects.</span></span>

8.  <span data-ttu-id="b44e2-142">關閉 DataReader 和連接物件。</span><span class="sxs-lookup"><span data-stu-id="b44e2-142">Close the DataReader and the connection objects.</span></span>

## <a name="example"></a><span data-ttu-id="b44e2-143">範例</span><span class="sxs-lookup"><span data-stu-id="b44e2-143">Example</span></span>
 <span data-ttu-id="b44e2-144">下列範例執行的封裝，會計算單一彙總值並將值儲存到 DataReader 目的地，然後從 DataReader 讀取這個值，並在 Windows Form 的文字方塊中顯示值。</span><span class="sxs-lookup"><span data-stu-id="b44e2-144">The following example runs a package that calculates a single aggregate value and saves the value to a DataReader destination, and then reads this value from the DataReader and displays the value in a text box on a Windows Form.</span></span>

 <span data-ttu-id="b44e2-145">將封裝的輸出載入用戶端應用程式時，不需要使用參數。</span><span class="sxs-lookup"><span data-stu-id="b44e2-145">The use of parameters is not required when loading the output of a package into a client application.</span></span> <span data-ttu-id="b44e2-146">如果您不想要使用參數，可以在**DtsClient**命名空間中省略變數的使用，並省略使用物件的程式碼 `DtsDataParameter` 。</span><span class="sxs-lookup"><span data-stu-id="b44e2-146">If you do not want to use a parameter, you can omit the use of the variable in the **DtsClient** namespace, and omit the code that uses the `DtsDataParameter` object.</span></span>

#### <a name="to-create-the-test-package"></a><span data-ttu-id="b44e2-147">建立測試封裝</span><span class="sxs-lookup"><span data-stu-id="b44e2-147">To create the test package</span></span>

1.  <span data-ttu-id="b44e2-148">建立新的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 封裝。</span><span class="sxs-lookup"><span data-stu-id="b44e2-148">Create a new [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package.</span></span> <span data-ttu-id="b44e2-149">範例程式碼使用 "DtsClientWParamPkg.dtsx" 做為封裝的名稱。</span><span class="sxs-lookup"><span data-stu-id="b44e2-149">The sample code uses "DtsClientWParamPkg.dtsx" as the name of the package.</span></span>

2.  <span data-ttu-id="b44e2-150">在 DtsClient 命名空間中加入 String 類型的變數。</span><span class="sxs-lookup"><span data-stu-id="b44e2-150">Add a variable of type String in the DtsClient namespace.</span></span> <span data-ttu-id="b44e2-151">範例程式碼使用 Country 做為變數的名稱 </span><span class="sxs-lookup"><span data-stu-id="b44e2-151">The sample code use Country as the name of the variable.</span></span> <span data-ttu-id="b44e2-152">(您可能需要按一下 [變數]\*\*\*\* 視窗中的 [選擇變數資料行]\*\*\*\* 工具列按鈕，才會顯示 [命名空間]\*\*\*\* 資料行)。</span><span class="sxs-lookup"><span data-stu-id="b44e2-152">(You may need to click the **Choose Variable Columns** toolbar button in the **Variables** window to display the **Namespace** column.)</span></span>

3.  <span data-ttu-id="b44e2-153">加入連接至 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] 範例資料庫的 OLE DB 連接管理員。</span><span class="sxs-lookup"><span data-stu-id="b44e2-153">Add an OLE DB connection manager that connects to the [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] sample database.</span></span>

4.  <span data-ttu-id="b44e2-154">將資料流程工作加入封裝，並切換至資料流程設計介面。</span><span class="sxs-lookup"><span data-stu-id="b44e2-154">Add a data flow task to the package and switch to the Data Flow design surface.</span></span>

5.  <span data-ttu-id="b44e2-155">將 OLE DB 來源加入資料流程並將它設定成使用先前建立的 OLE DB 連接管理員，並加入下列 SQL 命令：</span><span class="sxs-lookup"><span data-stu-id="b44e2-155">Add an OLE DB source to the data flow and configure it to use the OLE DB connection manager created previously, and the following SQL command:</span></span>

    ```
    SELECT * FROM Sales.vIndividualCustomer WHERE CountryRegionName = ?
    ```

6.  <span data-ttu-id="b44e2-156">按一下， `Parameters` 然後在 [**設定查詢參數**] 對話方塊中，將查詢中的單一輸入參數（parameter0 對應）對應到 DtsClient：： Country 變數。</span><span class="sxs-lookup"><span data-stu-id="b44e2-156">Click `Parameters` and, in the **Set Query Parameters** dialog box, map the single input parameter in the query, Parameter0, to the DtsClient::Country variable.</span></span>

7.  <span data-ttu-id="b44e2-157">將彙總轉換加入資料流程，然後將 OLE DB 來源的輸出連接到轉換。</span><span class="sxs-lookup"><span data-stu-id="b44e2-157">Add an Aggregate transformation to the data flow, and connect the output of the OLE DB source to the transformation.</span></span> <span data-ttu-id="b44e2-158">開啟 [匯總轉換編輯器]，並將它設定為在所有輸入資料行上執行「全部計數」作業 ( \* ) 並使用別名 CustomerCount 輸出匯總值。</span><span class="sxs-lookup"><span data-stu-id="b44e2-158">Open the Aggregate Transformation Editor and configure it to perform a "Count all" operation on all input columns (\*) and to output the aggregated value with the alias CustomerCount.</span></span>

8.  <span data-ttu-id="b44e2-159">將 DataReader 目的地加入資料流程，然後將彙總轉換的輸出連接到 DataReader 目的地。</span><span class="sxs-lookup"><span data-stu-id="b44e2-159">Add a DataReader destination to the data flow and connect the output of the Aggregate transformation to the DataReader destination.</span></span> <span data-ttu-id="b44e2-160">範例程式碼使用 "DataReaderDest" 做為 DataReader 的名稱。</span><span class="sxs-lookup"><span data-stu-id="b44e2-160">The sample code uses "DataReaderDest" as the name of the DataReader.</span></span> <span data-ttu-id="b44e2-161">為目的地選取單一可用的輸入資料行 CustomerCount。</span><span class="sxs-lookup"><span data-stu-id="b44e2-161">Select the single available input column, CustomerCount, for the destination.</span></span>

9. <span data-ttu-id="b44e2-162">儲存封裝。</span><span class="sxs-lookup"><span data-stu-id="b44e2-162">Save the package.</span></span> <span data-ttu-id="b44e2-163">建立的測試應用程式將執行封裝並直接從記憶體擷取其輸出。</span><span class="sxs-lookup"><span data-stu-id="b44e2-163">The test application created next will run the package and retrieve its output directly from memory.</span></span>

#### <a name="to-create-the-test-application"></a><span data-ttu-id="b44e2-164">建立測試應用程式</span><span class="sxs-lookup"><span data-stu-id="b44e2-164">To create the test application</span></span>

1.  <span data-ttu-id="b44e2-165">建立新的 Windows Form 應用程式。</span><span class="sxs-lookup"><span data-stu-id="b44e2-165">Create a new Windows Forms application.</span></span>

2.  <span data-ttu-id="b44e2-166">藉 `Microsoft.SqlServer.Dts.DtsClient` 由流覽至 **%ProgramFiles%\Microsoft SQL Server\100\DTS\Binn**中相同名稱的元件，加入命名空間的參考。</span><span class="sxs-lookup"><span data-stu-id="b44e2-166">Add a reference to the `Microsoft.SqlServer.Dts.DtsClient` namespace by browsing to the assembly of the same name in **%ProgramFiles%\Microsoft SQL Server\100\DTS\Binn**.</span></span>

3.  <span data-ttu-id="b44e2-167">將下列範例程式碼複製並貼入表單的程式碼模組。</span><span class="sxs-lookup"><span data-stu-id="b44e2-167">Copy and paste the following sample code into the code module for the form.</span></span>

4.  <span data-ttu-id="b44e2-168">視需要修改變數的值， `dtexecArgs` 使其包含**dtexec.exe**執行封裝所需的命令列參數。</span><span class="sxs-lookup"><span data-stu-id="b44e2-168">Modify the value of the `dtexecArgs` variable as required so that it contains the command-line parameters required by **dtexec.exe** to run the package.</span></span> <span data-ttu-id="b44e2-169">範例程式碼會從檔案系統載入封裝。</span><span class="sxs-lookup"><span data-stu-id="b44e2-169">The sample code loads the package from the file system.</span></span>

5.  <span data-ttu-id="b44e2-170">視需要修改變數的值， `dataReaderName` 使其包含封裝中 DataReader 目的地的名稱。</span><span class="sxs-lookup"><span data-stu-id="b44e2-170">Modify the value of the `dataReaderName` variable as required so that it contains the name of the DataReader destination in the package.</span></span>

6.  <span data-ttu-id="b44e2-171">在表單上放置按鈕與文字方塊。</span><span class="sxs-lookup"><span data-stu-id="b44e2-171">Put a button and a text box on the form.</span></span> <span data-ttu-id="b44e2-172">範例程式碼會使用 `btnRun` 做為按鈕的名稱，以及 `txtResults` 做為文字方塊的名稱。</span><span class="sxs-lookup"><span data-stu-id="b44e2-172">The sample code uses `btnRun` as the name of the button, and `txtResults` as the name of the text box.</span></span>

7.  <span data-ttu-id="b44e2-173">執行應用程式，然後按一下按鈕。</span><span class="sxs-lookup"><span data-stu-id="b44e2-173">Run the application and click the button.</span></span> <span data-ttu-id="b44e2-174">在簡短地暫停封裝執行之後，您應該會在表單的文字方塊中，看到封裝計算的彙總值 (加拿大的客戶計數)。</span><span class="sxs-lookup"><span data-stu-id="b44e2-174">After a brief pause while the package runs, you should see the aggregate value calculated by the package (the count of customers in Canada) displayed in the text box on the form.</span></span>

### <a name="sample-code"></a><span data-ttu-id="b44e2-175">範例程式碼</span><span class="sxs-lookup"><span data-stu-id="b44e2-175">Sample Code</span></span>

```vb
Imports System.Data
Imports Microsoft.SqlServer.Dts.DtsClient

Public Class Form1

  Private Sub btnRun_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnRun.Click

    Dim dtexecArgs As String
    Dim dataReaderName As String
    Dim countryName As String

    Dim dtsConnection As DtsConnection
    Dim dtsCommand As DtsCommand
    Dim dtsDataReader As IDataReader
    Dim dtsParameter As DtsDataParameter

    Windows.Forms.Cursor.Current = Cursors.WaitCursor

    dtexecArgs = "/FILE ""C:\...\DtsClientWParamPkg.dtsx"""
    dataReaderName = "DataReaderDest"
    countryName = "Canada"

    dtsConnection = New DtsConnection()
    With dtsConnection
      .ConnectionString = dtexecArgs
      .Open()
    End With

    dtsCommand = New DtsCommand(dtsConnection)
    dtsCommand.CommandText = dataReaderName

    dtsParameter = New DtsDataParameter("Country", DbType.String)
    dtsParameter.Direction = ParameterDirection.Input
    dtsCommand.Parameters.Add(dtsParameter)

    dtsParameter.Value = countryName

    dtsDataReader = dtsCommand.ExecuteReader(CommandBehavior.Default)

    With dtsDataReader
      .Read()
      txtResults.Text = .GetInt32(0).ToString("N0")
    End With

    'After reaching the end of data rows,
    ' call the Read method one more time.
    Try
      dtsDataReader.Read()
    Catch ex As Exception
      MessageBox.Show("Exception on final call to Read method:" & ControlChars.CrLf & _
      ex.Message & ControlChars.CrLf & _
      ex.InnerException.Message, "Exception on final call to Read method", _
      MessageBoxButtons.OK, MessageBoxIcon.Error)
    End Try

    ' The following method is a best practice, and is
    '  required when using DtsDataParameter objects.
    dtsCommand.Dispose()

    Try
      dtsDataReader.Close()
    Catch ex As Exception
      MessageBox.Show("Exception closing DataReader:" & ControlChars.CrLf & _
      ex.Message & ControlChars.CrLf & _
      ex.InnerException.Message, "Exception closing DataReader", _
      MessageBoxButtons.OK, MessageBoxIcon.Error)
    End Try

    Try
      dtsConnection.Close()
    Catch ex As Exception
      MessageBox.Show("Exception closing connection:" & ControlChars.CrLf & _
      ex.Message & ControlChars.CrLf & _
      ex.InnerException.Message, "Exception closing connection", _
      MessageBoxButtons.OK, MessageBoxIcon.Error)
    End Try

    Windows.Forms.Cursor.Current = Cursors.Default

  End Sub

End Class
```

```csharp
using System;
using System.Windows.Forms;
using System.Data;
using Microsoft.SqlServer.Dts.DtsClient;

namespace DtsClientWParamCS
{
  public partial class Form1 : Form
  {
    public Form1()
    {
      InitializeComponent();
      this.btnRun.Click += new System.EventHandler(this.btnRun_Click);
    }

    private void btnRun_Click(object sender, EventArgs e)
    {
      string dtexecArgs;
      string dataReaderName;
      string countryName;

      DtsConnection dtsConnection;
      DtsCommand dtsCommand;
      IDataReader dtsDataReader;
      DtsDataParameter dtsParameter;

      Cursor.Current = Cursors.WaitCursor;

      dtexecArgs = @"/FILE ""C:\...\DtsClientWParamPkg.dtsx""";
      dataReaderName = "DataReaderDest";
      countryName = "Canada";

      dtsConnection = new DtsConnection();
      {
        dtsConnection.ConnectionString = dtexecArgs;
        dtsConnection.Open();
      }

      dtsCommand = new DtsCommand(dtsConnection);
      dtsCommand.CommandText = dataReaderName;

      dtsParameter = new DtsDataParameter("Country", DbType.String);
      dtsParameter.Direction = ParameterDirection.Input;
      dtsCommand.Parameters.Add(dtsParameter);

      dtsParameter.Value = countryName;

      dtsDataReader = dtsCommand.ExecuteReader(CommandBehavior.Default);

      {
        dtsDataReader.Read();
        txtResults.Text = dtsDataReader.GetInt32(0).ToString("N0");
      }

      //After reaching the end of data rows,
      // call the Read method one more time.
      try
      {
        dtsDataReader.Read();
      }
      catch (Exception ex)
      {
        MessageBox.Show(
          "Exception on final call to Read method:\n" + ex.Message + "\n" + ex.InnerException.Message,
          "Exception on final call to Read method", MessageBoxButtons.OK, MessageBoxIcon.Error);
      }

      // The following method is a best practice, and is
      //  required when using DtsDataParameter objects.
      dtsCommand.Dispose();

      try
      {
        dtsDataReader.Close();
      }
      catch (Exception ex)
      {
        MessageBox.Show(
          "Exception closing DataReader:\n" + ex.Message + "\n" + ex.InnerException.Message,
          "Exception closing DataReader", MessageBoxButtons.OK, MessageBoxIcon.Error);
      }

      try
      {
        dtsConnection.Close();
      }
      catch (Exception ex)
      {
        MessageBox.Show(
          "Exception closing connection:\n" + ex.Message + "\n" + ex.InnerException.Message,
          "Exception closing connection", MessageBoxButtons.OK, MessageBoxIcon.Error);
      }

      Cursor.Current = Cursors.Default;

    }
  }
}
```

<span data-ttu-id="b44e2-176">![Integration Services 圖示 (小型) ](../media/dts-16.gif "Integration Services 圖示 (小)")會**保持最**新狀態 Integration Services  </span><span class="sxs-lookup"><span data-stu-id="b44e2-176">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="b44e2-177">若要取得 Microsoft 的最新下載、文件、範例和影片以及社群中的精選解決方案，請瀏覽 MSDN 上的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 頁面：</span><span class="sxs-lookup"><span data-stu-id="b44e2-177">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="b44e2-178">瀏覽 MSDN 上的 Integration Services 頁面</span><span class="sxs-lookup"><span data-stu-id="b44e2-178">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="b44e2-179">若要得到這些更新的自動通知，請訂閱該頁面上所提供的 RSS 摘要。</span><span class="sxs-lookup"><span data-stu-id="b44e2-179">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>

## <a name="see-also"></a><span data-ttu-id="b44e2-180">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b44e2-180">See Also</span></span>
 <span data-ttu-id="b44e2-181">[瞭解本機和遠端執行](../run-manage-packages-programmatically/understanding-the-differences-between-local-and-remote-execution.md)[載入以及](../run-manage-packages-programmatically/loading-and-running-a-local-package-programmatically.md)以程式設計方式[載入和執行遠端封裝](../run-manage-packages-programmatically/loading-and-running-a-remote-package-programmatically.md)的本機封裝之間的差異</span><span class="sxs-lookup"><span data-stu-id="b44e2-181">[Understanding the Differences between Local and Remote Execution](../run-manage-packages-programmatically/understanding-the-differences-between-local-and-remote-execution.md) [Loading and Running a Local Package Programmatically](../run-manage-packages-programmatically/loading-and-running-a-local-package-programmatically.md) [Loading and Running a Remote Package Programmatically](../run-manage-packages-programmatically/loading-and-running-a-remote-package-programmatically.md)</span></span>


