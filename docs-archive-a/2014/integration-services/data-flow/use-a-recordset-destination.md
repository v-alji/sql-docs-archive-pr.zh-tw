---
title: 使用資料錄集目的地 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Recordset destination
ms.assetid: a7b143dc-8008-404f-83b0-b45ffbca6029
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 34d1d5a7aa76876a9d8718b691b1d24a8835e2e9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599076"
---
# <a name="use-a-recordset-destination"></a><span data-ttu-id="082e4-102">使用資料錄集目的地</span><span class="sxs-lookup"><span data-stu-id="082e4-102">Use a Recordset Destination</span></span>
  <span data-ttu-id="082e4-103">資料錄集目的地不會將資料儲存到外部資料來源，</span><span class="sxs-lookup"><span data-stu-id="082e4-103">The Recordset destination does not save data to an external data source.</span></span> <span data-ttu-id="082e4-104">而是將資料儲存到資料類型為 `Object` 之 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 封裝變數內儲存的資料錄集記憶體中。</span><span class="sxs-lookup"><span data-stu-id="082e4-104">Instead, the Recordset destination saves data in memory in a recordset that is stored in an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package variable of the `Object` data type.</span></span> <span data-ttu-id="082e4-105">當資料錄集目的地儲存資料之後，您通常要使用具有 Foreach ADO 列舉值的 Foreach 迴圈容器來一次處理資料錄集的一個資料列。</span><span class="sxs-lookup"><span data-stu-id="082e4-105">After the Recordset destination saves the data, you typically use a Foreach Loop container with the Foreach ADO enumerator to process one row of the recordset at a time.</span></span> <span data-ttu-id="082e4-106">Foreach ADO 列舉值會將目前資料列的每一資料行值儲存到個別封裝變數之中。</span><span class="sxs-lookup"><span data-stu-id="082e4-106">The Foreach ADO enumerator saves the value from each column of the current row into a separate package variable.</span></span> <span data-ttu-id="082e4-107">接著，您在 Foreach 迴圈容器中設定的工作會讀取這些變數中的值，然後對它們執行一些動作。</span><span class="sxs-lookup"><span data-stu-id="082e4-107">Then, the tasks that you configure inside the Foreach Loop container read those values from the variables and perform some action with them.</span></span>  
  
 <span data-ttu-id="082e4-108">您可以在多種不同情況下使用資料錄集目的地。</span><span class="sxs-lookup"><span data-stu-id="082e4-108">You can use the Recordset destination in many different scenarios.</span></span> <span data-ttu-id="082e4-109">以下是一些範例：</span><span class="sxs-lookup"><span data-stu-id="082e4-109">Here are some examples:</span></span>  
  
-   <span data-ttu-id="082e4-110">您可以使用傳送郵件工作和 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 運算式語言，為資料錄集的每個資料列傳送自訂的電子郵件訊息。</span><span class="sxs-lookup"><span data-stu-id="082e4-110">You can use a Send Mail task and the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] expression language to send a customized e-mail message for each row in the recordset.</span></span>  
  
-   <span data-ttu-id="082e4-111">您可以將指令碼元件設定成資料流程工作中的來源，然後使用該指令碼元件將資料行值讀入資料流程的資料行中。</span><span class="sxs-lookup"><span data-stu-id="082e4-111">You can use a Script component configured as a source, inside a Data Flow task, to read the column values into the columns of the data flow.</span></span> <span data-ttu-id="082e4-112">然後，您可以使用轉換和目的地來轉換和儲存資料列。</span><span class="sxs-lookup"><span data-stu-id="082e4-112">Then, you can use transformations and destinations to transform and save the row.</span></span> <span data-ttu-id="082e4-113">在這個範例中，資料流程工作會為每一個資料列執行一次。</span><span class="sxs-lookup"><span data-stu-id="082e4-113">In this example, the Data Flow task runs once for each row.</span></span>  
  
 <span data-ttu-id="082e4-114">下列章節會先說明使用資料錄集目的地的一般程序，然後提供一個如何使用目的地的明確範例。</span><span class="sxs-lookup"><span data-stu-id="082e4-114">The following sections first describe the general process of using the Recordset destination and then show a specific example of how to use the destination.</span></span>  
  
## <a name="general-steps-to-using-a-recordset-destination"></a><span data-ttu-id="082e4-115">使用資料錄集目的地的一般步驟</span><span class="sxs-lookup"><span data-stu-id="082e4-115">General Steps to Using a Recordset Destination</span></span>  
 <span data-ttu-id="082e4-116">下列程序摘要列出如何將資料儲存到資料錄集目的地，然後使用 Foreach 迴圈容器處理每一個資料列的步驟。</span><span class="sxs-lookup"><span data-stu-id="082e4-116">The following procedure summarizes the steps that are required to save data to a Recordset destination, and then use the Foreach Loop container to process each row.</span></span>  
  
#### <a name="to-save-data-to-a-recordset-destination-and-process-each-row-by-using-the-foreach-loop-container"></a><span data-ttu-id="082e4-117">將資料儲存到資料錄集目的地並使用 Foreach 迴圈容器處理每一個資料列</span><span class="sxs-lookup"><span data-stu-id="082e4-117">To save data to a Recordset destination and process each row by using the Foreach Loop container</span></span>  
  
1.  <span data-ttu-id="082e4-118">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，建立或開啟 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 封裝。</span><span class="sxs-lookup"><span data-stu-id="082e4-118">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], create or open an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package.</span></span>  
  
2.  <span data-ttu-id="082e4-119">建立一個變數，在其中加入由資料錄集目的地儲存到記憶體中的資料錄集，然後將變數類型設為 `Object`。</span><span class="sxs-lookup"><span data-stu-id="082e4-119">Create a variable that will contain the recordset saved into memory by the Recordset destination, and set the variable's type to `Object`.</span></span>  
  
3.  <span data-ttu-id="082e4-120">建立其他適當類型的變數，在其中加入您要使用之資料錄集的每一資料行值。</span><span class="sxs-lookup"><span data-stu-id="082e4-120">Create additional variables of the appropriate types to contain the values of each column in the recordset that you want to use.</span></span>  
  
4.  <span data-ttu-id="082e4-121">根據您計劃用於資料流程中的資料來源，新增並設定需要的連接管理員。</span><span class="sxs-lookup"><span data-stu-id="082e4-121">Add and configure the connection manager required by the data source that you plan to use in your data flow.</span></span>  
  
5.  <span data-ttu-id="082e4-122">將資料流程工作加入封裝中，然後在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師的 [資料流程] 索引標籤上，設定用於載入和轉換資料的來源與轉換。</span><span class="sxs-lookup"><span data-stu-id="082e4-122">Add a Data Flow task to the package, and on the Data Flow tab of [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, configure sources and transformations to load and transform the data.</span></span>  
  
6.  <span data-ttu-id="082e4-123">將資料錄集目的地加入資料流程中，然後將它連接到轉換。</span><span class="sxs-lookup"><span data-stu-id="082e4-123">Add a Recordset destination to the data flow and connect it to the transformations.</span></span> <span data-ttu-id="082e4-124">為資料錄集目的地的 `VariableName` 屬性，輸入您為了保存資料錄集所建立的變數名稱。</span><span class="sxs-lookup"><span data-stu-id="082e4-124">For the `VariableName` property of the Recordset destination, enter the name of the variable that you created to hold the recordset.</span></span>  
  
7.  <span data-ttu-id="082e4-125">在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師的 [控制流程] 索引標籤上，加入 Foreach 迴圈容器並將此容器連接在資料流程工作之後。</span><span class="sxs-lookup"><span data-stu-id="082e4-125">On the Control Flow tab of [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, add a Foreach Loop container and connect this container after the Data Flow task.</span></span> <span data-ttu-id="082e4-126">然後，開啟 Foreach 迴圈編輯器  並依照下列設定來設定容器：</span><span class="sxs-lookup"><span data-stu-id="082e4-126">Then, open the **Foreach Loop Editor** to configure the container with the following settings:</span></span>  
  
    1.  <span data-ttu-id="082e4-127">在 [集合]  頁面上，選取 [Foreach ADO 列舉值]。</span><span class="sxs-lookup"><span data-stu-id="082e4-127">On the **Collection** page, select the Foreach ADO Enumerator.</span></span> <span data-ttu-id="082e4-128">然後，為 [ADO 物件來源變數]  選取包含資料錄集的變數。</span><span class="sxs-lookup"><span data-stu-id="082e4-128">Then, for **ADO object source variable**, select the variable that contains the recordset.</span></span>  
  
    2.  <span data-ttu-id="082e4-129">在 [變數對應]  頁面上，將您要使用的每一個資料行以零為基底之索引對應到適當的變數。</span><span class="sxs-lookup"><span data-stu-id="082e4-129">On the **Variable Mappings** page, map the zero-based index of each column that you want to use to the appropriate variable.</span></span>  
  
         <span data-ttu-id="082e4-130">在迴圈的每個反覆運算中，列舉值會使用目前資料列中的資料行值來擴展這些變數。</span><span class="sxs-lookup"><span data-stu-id="082e4-130">On each iteration of the loop, the enumerator populates these variables with the column values from the current row.</span></span>  
  
8.  <span data-ttu-id="082e4-131">在 Foreach 迴圈容器中加入並設定工作，藉由讀取變數中的值，一次處理資料錄集的一個資料列。</span><span class="sxs-lookup"><span data-stu-id="082e4-131">Inside the Foreach Loop container, add and configure tasks to process one row of the recordset at a time by reading the values from the variables.</span></span>  
  
## <a name="example-of-using-the-recordset-destination"></a><span data-ttu-id="082e4-132">使用資料錄集目的地的範例</span><span class="sxs-lookup"><span data-stu-id="082e4-132">Example of Using the Recordset Destination</span></span>  
 <span data-ttu-id="082e4-133">在下列範例中，資料流程工作會將 Sales.SalesPerson 資料表中有關 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] 員工的資料載入資料錄集目的地中。</span><span class="sxs-lookup"><span data-stu-id="082e4-133">In the following example, the Data Flow task loads information about [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] employees from the Sales.SalesPerson table into a Recordset destination.</span></span> <span data-ttu-id="082e4-134">然後，Foreach 迴圈容器會一次讀取一個資料列，接著呼叫傳送郵件工作。</span><span class="sxs-lookup"><span data-stu-id="082e4-134">Then, a Foreach Loop container reads one row of data at a time, and calls a Send Mail task.</span></span> <span data-ttu-id="082e4-135">傳送郵件工作會使用運算式，將每位銷售人員的獎金金額以自訂的電子郵件訊息傳送給每位銷售人員。</span><span class="sxs-lookup"><span data-stu-id="082e4-135">The Send Mail task uses expressions to send a customized e-mail message to each salesperson about the amount of his or her bonus.</span></span>  
  
#### <a name="to-create-the-project-and-configure-the-variables"></a><span data-ttu-id="082e4-136">建立專案和設定變數</span><span class="sxs-lookup"><span data-stu-id="082e4-136">To create the project and configure the variables</span></span>  
  
1.  <span data-ttu-id="082e4-137">在 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]中，建立新的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="082e4-137">In [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], create a new [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project.</span></span>  
  
2.  <span data-ttu-id="082e4-138">在 [SSIS]  功能表上，選取 [變數]  。</span><span class="sxs-lookup"><span data-stu-id="082e4-138">On the **SSIS** menu, select **Variables**.</span></span>  
  
3.  <span data-ttu-id="082e4-139">在 [變數]  視窗中建立變數，用以保存資料錄集和目前資料列的資料行值：</span><span class="sxs-lookup"><span data-stu-id="082e4-139">In the **Variables** window, create the variables that will hold the recordset and the column values from the current row:</span></span>  
  
    1.  <span data-ttu-id="082e4-140">建立名稱為 `BonusRecordset` 的變數，然後將其類型設為 `Object`。</span><span class="sxs-lookup"><span data-stu-id="082e4-140">Create a variable named, `BonusRecordset`, and set its type to `Object`.</span></span>  
  
         <span data-ttu-id="082e4-141">`BonusRecordset` 變數會保存資料錄集。</span><span class="sxs-lookup"><span data-stu-id="082e4-141">The `BonusRecordset` variable holds the recordset.</span></span>  
  
    2.  <span data-ttu-id="082e4-142">建立名稱為 `EmailAddress` 的變數，然後將其類型設為 `String`。</span><span class="sxs-lookup"><span data-stu-id="082e4-142">Create a variable named, `EmailAddress`, and set its type to `String`.</span></span>  
  
         <span data-ttu-id="082e4-143">`EmailAddress` 變數會保存銷售人員的電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="082e4-143">The `EmailAddress` variable holds the salesperson's e-mail address.</span></span>  
  
    3.  <span data-ttu-id="082e4-144">建立名稱為 `FirstName` 的變數，然後將其類型設為 `String`。</span><span class="sxs-lookup"><span data-stu-id="082e4-144">Create a variable named, `FirstName`, and set its type to `String`.</span></span>  
  
         <span data-ttu-id="082e4-145">`FirstName` 變數會保存銷售人員的名字。</span><span class="sxs-lookup"><span data-stu-id="082e4-145">The `FirstName` variable holds the salesperson's first name.</span></span>  
  
    4.  <span data-ttu-id="082e4-146">建立名稱為 `Bonus` 的變數，然後將其類型設為 `Double`。</span><span class="sxs-lookup"><span data-stu-id="082e4-146">Create a variable named, `Bonus`, and set its type to `Double`.</span></span>  
  
         <span data-ttu-id="082e4-147">`Bonus` 變數會保存銷售人員的獎金金額。</span><span class="sxs-lookup"><span data-stu-id="082e4-147">The `Bonus` variable holds the amount of the salesperson's bonus.</span></span>  
  
#### <a name="to-configure-the-connection-managers"></a><span data-ttu-id="082e4-148">設定連接管理員</span><span class="sxs-lookup"><span data-stu-id="082e4-148">To configure the connection managers</span></span>  
  
1.  <span data-ttu-id="082e4-149">在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師的「連線管理員」區域中，加入並設定連接到 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] 範例資料庫的新 OLE DB 連線管理員。</span><span class="sxs-lookup"><span data-stu-id="082e4-149">In the Connection Managers area of the [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, add and configure a new OLE DB connection manager that connects to the [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] sample database.</span></span>  
  
     <span data-ttu-id="082e4-150">資料流程工作中的 OLE DB 來源，將會使用此連接管理員進行資料擷取。</span><span class="sxs-lookup"><span data-stu-id="082e4-150">The OLE DB source in the Data Flow task will use this connection manager to retrieve data.</span></span>  
  
2.  <span data-ttu-id="082e4-151">在「連接管理員」區域中，加入並設定連接到可用 SMTP 伺服器的新 SMTP 連接管理員。</span><span class="sxs-lookup"><span data-stu-id="082e4-151">In the Connection Managers area, add and configure a new SMTP connection manager that connects to an available SMTP server.</span></span>  
  
     <span data-ttu-id="082e4-152">Foreach 迴圈容器中的傳送郵件工作，將會使用此連接管理員傳送電子郵件。</span><span class="sxs-lookup"><span data-stu-id="082e4-152">The Send Mail task inside the Foreach Loop container will use this connection manager to send emails.</span></span>  
  
#### <a name="to-configure-the-data-flow-and-the-recordset-destination"></a><span data-ttu-id="082e4-153">設定資料流程和資料錄集目的地</span><span class="sxs-lookup"><span data-stu-id="082e4-153">To configure the data flow and the Recordset Destination</span></span>  
  
1.  <span data-ttu-id="082e4-154">在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師的 [控制流程] 索引標籤上，將資料流程工作加入設計介面。</span><span class="sxs-lookup"><span data-stu-id="082e4-154">On the **Control Flow** tab of [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, add a Data Flow task to the design surface.</span></span>  
  
2.  <span data-ttu-id="082e4-155">在 [資料流程]  索引標籤上，將 OLE DB 來源加入至資料流程工作，然後開啟 OLE DB 來源編輯器  。</span><span class="sxs-lookup"><span data-stu-id="082e4-155">On the **Data Flow** tab, add an OLE DB source to the Data Flow task, and then open the **OLE DB Source Editor.**</span></span>  
  
3.  <span data-ttu-id="082e4-156">在編輯器的 [連線管理員]  頁面上，依照下列設定來設定來源：</span><span class="sxs-lookup"><span data-stu-id="082e4-156">On the **Connection Manager** page of the editor, configure the source with the following settings:</span></span>  
  
    1.  <span data-ttu-id="082e4-157">針對 [OLE DB 連線管理員]  ，選取您先前建立的 OLE DB 連線管理員。</span><span class="sxs-lookup"><span data-stu-id="082e4-157">For **OLE DB connection manager**, select the OLE DB connection manager that you previously created.</span></span>  
  
    2.  <span data-ttu-id="082e4-158">針對 [資料存取模式]  ，選取 [SQL 命令]  。</span><span class="sxs-lookup"><span data-stu-id="082e4-158">For **Data access mode**, select **SQL command**.</span></span>  
  
    3.  <span data-ttu-id="082e4-159">針對 [SQL 命令文字]  ，輸入下列查詢：</span><span class="sxs-lookup"><span data-stu-id="082e4-159">For **SQL command text**, enter the following query:</span></span>  
  
        ```  
        SELECT     Person.Contact.EmailAddress, Person.Contact.FirstName, CONVERT(float, Sales.SalesPerson.Bonus) AS Bonus  
        FROM         Sales.SalesPerson INNER JOIN  
                              Person.Contact ON Sales.SalesPerson.SalesPersonID = Person.Contact.ContactID  
        ```  
  
        > [!NOTE]  
        >  <span data-ttu-id="082e4-160">您必須將 Bonus 資料行中的 `currency` 值轉換為 `float`，然後才能將此值載入 `Double` 類型的封裝變數中。</span><span class="sxs-lookup"><span data-stu-id="082e4-160">You have to convert the `currency` value in the Bonus column to a `float` before you can load that value into a package variable whose type is `Double`.</span></span>  
  
4.  <span data-ttu-id="082e4-161">在 [資料流程]  索引標籤上，加入資料錄集目的地，然後將目的地連接到 OLE DB 來源之後。</span><span class="sxs-lookup"><span data-stu-id="082e4-161">On the **Data Flow** tab, add a Recordset destination, and connect the destination after the OLE DB source.</span></span>  
  
5.  <span data-ttu-id="082e4-162">開啟資料錄集目的地編輯器  ，並依照下列設定來設定目的地：</span><span class="sxs-lookup"><span data-stu-id="082e4-162">Open the **Recordset Destination Editor**, and configure the destination with the following settings:</span></span>  
  
    1.  <span data-ttu-id="082e4-163">在 [**元件屬性**] 索引標籤上，針對 [屬性] 選取 [] `VariableName` `User::BonusRecordset` 。</span><span class="sxs-lookup"><span data-stu-id="082e4-163">On the **Component Properties** tab, for `VariableName` property, select `User::BonusRecordset`.</span></span>  
  
    2.  <span data-ttu-id="082e4-164">在 [輸入資料行]  索引標籤上，選取可用的全部三個資料行。</span><span class="sxs-lookup"><span data-stu-id="082e4-164">On the **Input Columns** tab, select all three of the available columns.</span></span>  
  
#### <a name="to-configure-the-foreach-loop-container-and-run-the-package"></a><span data-ttu-id="082e4-165">設定 Foreach 迴圈容器並執行封裝</span><span class="sxs-lookup"><span data-stu-id="082e4-165">To configure the Foreach Loop container and run the package</span></span>  
  
1.  <span data-ttu-id="082e4-166">在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師的 [控制流程] 索引標籤上，加入 Foreach 迴圈容器，並將此容器連接在資料流程工作之後。</span><span class="sxs-lookup"><span data-stu-id="082e4-166">On the **Control Flow** tab of [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, add a Foreach Loop container, and connect the container after the Data Flow task.</span></span>  
  
2.  <span data-ttu-id="082e4-167">開啟 Foreach 迴圈編輯器  ，依照下列設定來設定容器：</span><span class="sxs-lookup"><span data-stu-id="082e4-167">Open the **Foreach Loop Editor**, and configure the container with the following settings:</span></span>  
  
    1.  <span data-ttu-id="082e4-168">在 [**集合**] 頁面上，針對 [**列舉**值] 選取 [ **Foreach ADO 列舉**值]，然後針對 [ **ADO 物件來源變數**] 選取 [] `User::BonusRecordset` 。</span><span class="sxs-lookup"><span data-stu-id="082e4-168">On the **Collection** page, for **Enumerator**, select **Foreach ADO Enumerator**, and for **ADO object source variable**, select `User::BonusRecordset`.</span></span>  
  
    2.  <span data-ttu-id="082e4-169">在 [**變數**對應] 頁面上，對應 `User::EmailAddress` 至索引0、 `User::FirstName` 索引1和 `User::Bonus` 索引2。</span><span class="sxs-lookup"><span data-stu-id="082e4-169">On the **Variable Mappings** page, map `User::EmailAddress` to index 0, `User::FirstName` to index 1, and `User::Bonus` to index 2.</span></span>  
  
3.  <span data-ttu-id="082e4-170">在 [控制流程]  索引標籤上的 Foreach 迴圈容器中，加入傳送郵件工作。</span><span class="sxs-lookup"><span data-stu-id="082e4-170">On the **Control Flow** tab, inside the Foreach Loop container, add a Send Mail task.</span></span>  
  
4.  <span data-ttu-id="082e4-171">開啟傳送郵件工作編輯器  ，然後在 [郵件]  頁面上，依照下列設定來設定工作：</span><span class="sxs-lookup"><span data-stu-id="082e4-171">Open the **Send Mail Task Editor**, and then on the **Mail** page, configure the task with the following settings:</span></span>  
  
    1.  <span data-ttu-id="082e4-172">針對 [SmtpConnection]  ，選取先前設定的 SMTP 連線管理員。</span><span class="sxs-lookup"><span data-stu-id="082e4-172">For **SmtpConnection**, select the SMTP connection manager that was configured previously.</span></span>  
  
    2.  <span data-ttu-id="082e4-173">針對 [From]  ，輸入適當的電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="082e4-173">For **From**, enter an appropriate e-mail address.</span></span>  
  
         <span data-ttu-id="082e4-174">如果使用您自己的電子郵件地址，可以確認封裝是否成功執行。</span><span class="sxs-lookup"><span data-stu-id="082e4-174">If you use your own e-mail address, you will be able to confirm that the package runs successfully.</span></span> <span data-ttu-id="082e4-175">針對由傳送郵件工作傳送到 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]虛構銷售人員的郵件，您將會收到無法傳遞的收件者訊息。</span><span class="sxs-lookup"><span data-stu-id="082e4-175">You will receive undeliverable receipts for the messages sent by the Send Mail task to the fictitious salespersons of [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)].</span></span>  
  
    3.  <span data-ttu-id="082e4-176">針對 [To]  ，輸入預設的電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="082e4-176">For **To**, enter a default e-mail address.</span></span>  
  
         <span data-ttu-id="082e4-177">雖然不會使用這個值，但是這個值會在執行階段由各銷售人員的電子郵件地址所取代。</span><span class="sxs-lookup"><span data-stu-id="082e4-177">This value will not be used, but will be replaced at run time by the e-mail address of each salesperson.</span></span>  
  
    4.  <span data-ttu-id="082e4-178">針對 [Subject]  ，輸入「您的年度獎金」。</span><span class="sxs-lookup"><span data-stu-id="082e4-178">For **Subject**, enter "Your annual bonus".</span></span>  
  
    5.  <span data-ttu-id="082e4-179">針對 [MessageSourceType]  ，選取 [直接輸入]  。</span><span class="sxs-lookup"><span data-stu-id="082e4-179">For **MessageSourceType**, select **Direct Input**.</span></span>  
  
5.  <span data-ttu-id="082e4-180">在傳送郵件工作編輯器  的 [運算式]  頁面上，按一下省略符號按鈕 ( **...** ) 以開啟屬性運算式編輯器  。</span><span class="sxs-lookup"><span data-stu-id="082e4-180">On the **Expressions** page of the **Send Mail Task Editor**, click the ellipsis button (**...**) to open the **Property Expressions Editor**.</span></span>  
  
6.  <span data-ttu-id="082e4-181">在屬性運算式編輯器  中，輸入下列資訊：</span><span class="sxs-lookup"><span data-stu-id="082e4-181">In the **Property Expressions Editor**, enter the following information:</span></span>  
  
    1.  <span data-ttu-id="082e4-182">針對 [ToLine]  ，加入下列運算式：</span><span class="sxs-lookup"><span data-stu-id="082e4-182">For **ToLine**, add the following expression:</span></span>  
  
        ```  
        @[User::EmailAddress]  
        ```  
  
    2.  <span data-ttu-id="082e4-183">針對 [MessageSource]  屬性，加入下列運算式：</span><span class="sxs-lookup"><span data-stu-id="082e4-183">For the **MessageSource** property, add the following expression:</span></span>  
  
        ```  
        "Dear " +  @[User::FirstName] + ": The amount of your bonus for this year is $" +  (DT_WSTR, 12) @[User::Bonus] + ". Thank you!"  
        ```  
  
7.  <span data-ttu-id="082e4-184">執行封裝。</span><span class="sxs-lookup"><span data-stu-id="082e4-184">Run the package.</span></span>  
  
     <span data-ttu-id="082e4-185">如果您指定了有效的 SMTP 伺服器且提供您自己的電子郵件地址，針對由傳送郵件工作傳送到 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]虛構銷售人員的郵件，您將會收到無法傳遞的收件者訊息。</span><span class="sxs-lookup"><span data-stu-id="082e4-185">If you have specified a valid SMTP server and provided your own e-mail address, you will receive undeliverable receipts for the messages that the Send Mail task sends to the fictitious salespersons of [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)].</span></span>  
  
  
