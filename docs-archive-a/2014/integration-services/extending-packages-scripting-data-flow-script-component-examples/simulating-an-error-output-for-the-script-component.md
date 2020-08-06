---
title: 模擬指令碼元件的錯誤輸出 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- Script component [Integration Services], error output
- error outputs [Integration Services], Script component
ms.assetid: f8b6ecff-ac99-4231-a0e7-7ce4ad76bad0
author: chugugrace
ms.author: chugu
ms.openlocfilehash: bed458ce378eb26cd863811b4974b5f39429e1b1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688037"
---
# <a name="simulating-an-error-output-for-the-script-component"></a><span data-ttu-id="e8ecc-102">模擬指令碼元件的錯誤輸出</span><span class="sxs-lookup"><span data-stu-id="e8ecc-102">Simulating an Error Output for the Script Component</span></span>
  <span data-ttu-id="e8ecc-103">雖然您無法在指令碼元件中將輸出直接設定為錯誤輸出，以自動處理錯誤資料列，不過可以建立其他輸出並使用指令碼中的條件式邏輯，適時地將資料列導向此輸出，以重新產生內建錯誤輸出的功能。</span><span class="sxs-lookup"><span data-stu-id="e8ecc-103">Although you cannot directly configure an output as an error output in the Script component for automatic handling of error rows, you can reproduce the functionality of a built-in error output by creating an additional output and using conditional logic in your script to direct rows to this output when appropriate.</span></span> <span data-ttu-id="e8ecc-104">您可能會想要加入兩個額外的輸出資料行，以接收發生錯誤的資料行之錯誤碼與識別碼，來模擬內建錯誤輸出的行為。</span><span class="sxs-lookup"><span data-stu-id="e8ecc-104">You may want to imitate the behavior of a built-in error output by adding two additional output columns to receive the error number and the ID of the column in which an error occurred.</span></span>  
  
 <span data-ttu-id="e8ecc-105">如果您需要加入對應至特定預先定義的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 錯誤碼之錯誤描述，可以使用 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.GetErrorDescription%2A> 介面的 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> 方法，這個方法可透過指令碼元件的 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ComponentMetaData%2A> 屬性取得。</span><span class="sxs-lookup"><span data-stu-id="e8ecc-105">If you want to add the error description that corresponds to a specific predefined [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] error code, you can use the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.GetErrorDescription%2A> method of the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> interface, available through the Script component's <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ComponentMetaData%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e8ecc-106">範例</span><span class="sxs-lookup"><span data-stu-id="e8ecc-106">Example</span></span>  
 <span data-ttu-id="e8ecc-107">在此所示的範例使用設定成具有兩個同步輸出之轉換的指令碼元件。</span><span class="sxs-lookup"><span data-stu-id="e8ecc-107">The example shown here uses a Script component configured as a transformation that has two synchronous outputs.</span></span> <span data-ttu-id="e8ecc-108">指令碼元件的目的在於從 AdventureWorks 範例資料庫的地址資料中，篩選出錯誤資料列。</span><span class="sxs-lookup"><span data-stu-id="e8ecc-108">The purpose of the Script component is to filter error rows from address data in the AdventureWorks sample database.</span></span> <span data-ttu-id="e8ecc-109">這個虛構的範例是假設，我們正在為北美的客戶準備促銷活動，並且需要篩選出不在北美的地址。</span><span class="sxs-lookup"><span data-stu-id="e8ecc-109">This fictitious example assumes that we are preparing a promotion for North American customers and need to filter out addresses that are not located in North America.</span></span>  
  
#### <a name="to-configure-the-example"></a><span data-ttu-id="e8ecc-110">若要設定範例</span><span class="sxs-lookup"><span data-stu-id="e8ecc-110">To configure the example</span></span>  
  
1.  <span data-ttu-id="e8ecc-111">在建立新指令碼元件之前，建立連接管理員並設定資料流程來源，以便從 AdventureWorks 範例資料庫選取地址資料。</span><span class="sxs-lookup"><span data-stu-id="e8ecc-111">Before creating the new Script component, create a connection manager and configure a data flow source that selects address data from the AdventureWorks sample database.</span></span> <span data-ttu-id="e8ecc-112">就這個只查看 CountryRegionName 資料行的範例而言，您可以直接使用 Person.vStateCountryProvinceRegion 檢視，或是聯結 Person.Address、Person.StateProvince 和 Person.CountryRegion 資料表以選取資料。</span><span class="sxs-lookup"><span data-stu-id="e8ecc-112">For this example, which only looks at the CountryRegionName column, you can simply use the Person.vStateCountryProvinceRegion view, or you can select data by joining the Person.Address, Person.StateProvince, and Person.CountryRegion tables.</span></span>  
  
2.  <span data-ttu-id="e8ecc-113">將新指令碼元件加入資料流程設計師介面，並將它設定為轉換。</span><span class="sxs-lookup"><span data-stu-id="e8ecc-113">Add a new Script component to the Data Flow designer surface and configure it as a transformation.</span></span> <span data-ttu-id="e8ecc-114">開啟**指令碼轉換編輯器**。</span><span class="sxs-lookup"><span data-stu-id="e8ecc-114">Open the **Script Transformation Editor**.</span></span>  
  
3.  <span data-ttu-id="e8ecc-115">在 [指令碼]  頁面上，將 **ScriptLanguage** 屬性設定成您要用以撰寫指令碼的指令碼語言。</span><span class="sxs-lookup"><span data-stu-id="e8ecc-115">On the **Script** page, set the **ScriptLanguage** property to the script language that you want to use to code the script.</span></span>  
  
4.  <span data-ttu-id="e8ecc-116">按一下 [編輯指令碼]  以開啟 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA)。</span><span class="sxs-lookup"><span data-stu-id="e8ecc-116">Click **Edit Script** to open [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA).</span></span>  
  
5.  <span data-ttu-id="e8ecc-117">在 `Input0_ProcessInputRow` 方法中，輸入或是貼上以下所示的範例程式碼。</span><span class="sxs-lookup"><span data-stu-id="e8ecc-117">In the `Input0_ProcessInputRow` method, type or paste the sample code shown below.</span></span>  
  
6.  <span data-ttu-id="e8ecc-118">關閉 VSTA。</span><span class="sxs-lookup"><span data-stu-id="e8ecc-118">Close VSTA.</span></span>  
  
7.  <span data-ttu-id="e8ecc-119">在 [輸入資料行]  頁面上，選取您要在指令碼轉換中處理的資料行。</span><span class="sxs-lookup"><span data-stu-id="e8ecc-119">On the **Input Columns** page, select the columns that you want to process in the Script transformation.</span></span> <span data-ttu-id="e8ecc-120">此範例只使用 CountryRegionName 資料行。</span><span class="sxs-lookup"><span data-stu-id="e8ecc-120">This example uses only the CountryRegionName column.</span></span> <span data-ttu-id="e8ecc-121">您保留未選取的可用輸入資料行，將會在資料流程中傳遞時保持不變。</span><span class="sxs-lookup"><span data-stu-id="e8ecc-121">Available input columns that you leave unselected will simply be passed through unchanged in the data flow.</span></span>  
  
8.  <span data-ttu-id="e8ecc-122">在 [**輸入和輸出**] 頁面上，加入新的第二個輸出，並將其 `SynchronousInputID` 值設定為輸入的識別碼，也就是 `SynchronousInputID` 預設輸出的屬性值。</span><span class="sxs-lookup"><span data-stu-id="e8ecc-122">On the **Inputs and Outputs** page, add a new, second output, and set its `SynchronousInputID` value to the ID of the input, which is also the value of the `SynchronousInputID` property of the default output.</span></span> <span data-ttu-id="e8ecc-123">將兩個輸出的 `ExclusionGroup` 屬性設定為相同的非零值 (例如 1)，以指出將每個資料列導向僅兩個輸出的其中一個。</span><span class="sxs-lookup"><span data-stu-id="e8ecc-123">Set the `ExclusionGroup` property of both outputs to the same non-zero value (for example, 1) to indicate that each row will be directed to only one of the two outputs.</span></span> <span data-ttu-id="e8ecc-124">提供特殊的名稱給新錯誤輸出，例如 "MyErrorOutput"。</span><span class="sxs-lookup"><span data-stu-id="e8ecc-124">Give the new error output a distinctive name, such as "MyErrorOutput."</span></span>  
  
9. <span data-ttu-id="e8ecc-125">將額外輸出資料行加入新錯誤輸出，以擷取所需的錯誤資訊，這可能包含發生錯誤的資料行之錯誤碼與識別碼，以及或許還有錯誤描述。</span><span class="sxs-lookup"><span data-stu-id="e8ecc-125">Add additional output columns to the new error output to capture the desired error information, which may include the error code, the ID of the column in which the error occurred, and possibly the error description.</span></span> <span data-ttu-id="e8ecc-126">此範例會建立新資料行 ErrorColumn 與 ErrorMessage。</span><span class="sxs-lookup"><span data-stu-id="e8ecc-126">This example creates the new columns, ErrorColumn and ErrorMessage.</span></span> <span data-ttu-id="e8ecc-127">如果您在自己的實作中擷取預先定義的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 錯誤，請確定加入錯誤號碼的 ErrorCode 資料行。</span><span class="sxs-lookup"><span data-stu-id="e8ecc-127">If you are catching predefined [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] errors in your own implementation, make sure to add an ErrorCode column for the error number.</span></span>  
  
10. <span data-ttu-id="e8ecc-128">請記下指令碼元件將檢查錯誤條件之輸入資料行的識別碼值。</span><span class="sxs-lookup"><span data-stu-id="e8ecc-128">Note the ID value of the input column or columns that the Script component will check for error conditions.</span></span> <span data-ttu-id="e8ecc-129">這個範例使用此資料行識別碼以擴展 ErrorColumn 值。</span><span class="sxs-lookup"><span data-stu-id="e8ecc-129">This example uses this column identifier to populate the ErrorColumn value.</span></span>  
  
11. <span data-ttu-id="e8ecc-130">關閉**指令碼轉換編輯器**。</span><span class="sxs-lookup"><span data-stu-id="e8ecc-130">Close the **Script Transformation Editor.**</span></span>  
  
12. <span data-ttu-id="e8ecc-131">將指令碼元件的輸出附加至適當的目的地。</span><span class="sxs-lookup"><span data-stu-id="e8ecc-131">Attach the outputs of the Script component to suitable destinations.</span></span> <span data-ttu-id="e8ecc-132">一般檔案目的地對於特定測試而言是最容易設定的。</span><span class="sxs-lookup"><span data-stu-id="e8ecc-132">Flat file destinations are the easiest to configure for ad hoc testing.</span></span>  
  
13. <span data-ttu-id="e8ecc-133">執行封裝。</span><span class="sxs-lookup"><span data-stu-id="e8ecc-133">Run the package.</span></span>  
  
```vb  
Public Overrides Sub Input0_ProcessInputRow(ByVal Row As Input0Buffer)  
  
  If Row.CountryRegionName <> "Canada" _  
      And Row.CountryRegionName <> "United States" Then  
  
    Row.ErrorColumn = 68 ' ID of CountryRegionName column  
    Row.ErrorMessage = "Address is not in North America."  
    Row.DirectRowToMyErrorOutput()  
  
  Else  
  
    Row.DirectRowToOutput0()  
  
  End If  
  
End Sub  
```  
  
```csharp  
public override void Input0_ProcessInputRow(Input0Buffer Row)  
{  
  
  if (Row.CountryRegionName!="Canada"&&Row.CountryRegionName!="United States")  
  
  {  
    Row.ErrorColumn = 68; // ID of CountryRegionName column  
    Row.ErrorMessage = "Address is not in North America.";  
    Row.DirectRowToMyErrorOutput();  
  
  }  
  else  
  {  
  
    Row.DirectRowToOutput0();  
  
  }  
  
}  
```  
  
<span data-ttu-id="e8ecc-134">![Integration Services 圖示 (小型) ](../media/dts-16.gif "Integration Services 圖示 (小)")會**保持最**新狀態 Integration Services  </span><span class="sxs-lookup"><span data-stu-id="e8ecc-134">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="e8ecc-135">若要取得 Microsoft 的最新下載、文件、範例和影片以及社群中的精選解決方案，請瀏覽 MSDN 上的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 頁面：</span><span class="sxs-lookup"><span data-stu-id="e8ecc-135">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="e8ecc-136">瀏覽 MSDN 上的 Integration Services 頁面</span><span class="sxs-lookup"><span data-stu-id="e8ecc-136">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="e8ecc-137">若要得到這些更新的自動通知，請訂閱該頁面上所提供的 RSS 摘要。</span><span class="sxs-lookup"><span data-stu-id="e8ecc-137">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8ecc-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e8ecc-138">See Also</span></span>  
 <span data-ttu-id="e8ecc-139">[資料中的錯誤處理](../data-flow/error-handling-in-data.md) </span><span class="sxs-lookup"><span data-stu-id="e8ecc-139">[Error Handling in Data](../data-flow/error-handling-in-data.md) </span></span>  
 <span data-ttu-id="e8ecc-140">[在資料流程元件中使用錯誤輸出](../extending-packages-custom-objects/data-flow/using-error-outputs-in-a-data-flow-component.md) </span><span class="sxs-lookup"><span data-stu-id="e8ecc-140">[Using Error Outputs in a Data Flow Component](../extending-packages-custom-objects/data-flow/using-error-outputs-in-a-data-flow-component.md) </span></span>  
 [<span data-ttu-id="e8ecc-141">使用指令碼元件建立同步轉換</span><span class="sxs-lookup"><span data-stu-id="e8ecc-141">Creating a Synchronous Transformation with the Script Component</span></span>](../extending-packages-scripting-data-flow-script-component-types/creating-a-synchronous-transformation-with-the-script-component.md) 
  
  
