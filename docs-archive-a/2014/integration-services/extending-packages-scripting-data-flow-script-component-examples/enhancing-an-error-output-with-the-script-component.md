---
title: 使用指令碼元件增強錯誤輸出 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- transformations [Integration Services], components
- Script component [Integration Services], examples
- error outputs [Integration Services], enhancing
- Script component [Integration Services], transformation components
ms.assetid: f7c02709-f1fa-4ebd-b255-dc8b81feeaa5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 18637aa1e147ce989645ae859681929f4d0c438a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606428"
---
# <a name="enhancing-an-error-output-with-the-script-component"></a><span data-ttu-id="9ccb4-102">使用指令碼元件增強錯誤輸出</span><span class="sxs-lookup"><span data-stu-id="9ccb4-102">Enhancing an Error Output with the Script Component</span></span>
  <span data-ttu-id="9ccb4-103">依預設，[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 錯誤輸出中的兩個額外資料行 ErrorCode 與 ErrorColumn 只包含數字碼，代表錯誤號碼及發生錯誤之資料行的識別碼。</span><span class="sxs-lookup"><span data-stu-id="9ccb4-103">By default, the two extra columns in an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] error output, ErrorCode and ErrorColumn, contain only numeric codes that represent an error number, and the ID of the column in which the error occurred.</span></span> <span data-ttu-id="9ccb4-104">這些數值若無對應的錯誤描述，則用途有限。</span><span class="sxs-lookup"><span data-stu-id="9ccb4-104">These numeric values may be of limited use without the corresponding error description.</span></span>  
  
 <span data-ttu-id="9ccb4-105">此主題描述如何使用指令碼元件，將錯誤描述資料行加入資料流程中的現有錯誤輸出資料。</span><span class="sxs-lookup"><span data-stu-id="9ccb4-105">This topic describes how to add an error description column to existing error output data in the data flow by using the Script component.</span></span> <span data-ttu-id="9ccb4-106">此範例使用 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.GetErrorDescription%2A> 介面的 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> 方法 (可透過指令碼元件的 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ComponentMetaData%2A> 屬性取得)，加入對應至特定預先定義的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 錯誤碼之錯誤描述。</span><span class="sxs-lookup"><span data-stu-id="9ccb4-106">The example adds the error description that corresponds to a specific predefined [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] error code by using the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.GetErrorDescription%2A> method of the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> interface, available through the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ComponentMetaData%2A> property of the Script component.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9ccb4-107">如果您要建立可以更輕鬆地在多個資料流程工作與多個封裝之間重複使用的元件，請考慮使用這個指令碼元件範例中的程式碼，做為自訂資料流程元件的起點。</span><span class="sxs-lookup"><span data-stu-id="9ccb4-107">If you want to create a component that you can more easily reuse across multiple Data Flow tasks and multiple packages, consider using the code in this Script component sample as the starting point for a custom data flow component.</span></span> <span data-ttu-id="9ccb4-108">如需詳細資訊，請參閱 [開發自訂資料流程元件](../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md)。</span><span class="sxs-lookup"><span data-stu-id="9ccb4-108">For more information, see [Developing a Custom Data Flow Component](../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9ccb4-109">範例</span><span class="sxs-lookup"><span data-stu-id="9ccb4-109">Example</span></span>  
 <span data-ttu-id="9ccb4-110">在這裡顯示的範例使用設定成轉換的指令碼元件，將錯誤描述資料行加入資料流程中的現有錯誤輸出資料。</span><span class="sxs-lookup"><span data-stu-id="9ccb4-110">The example shown here uses a Script component configured as a transformation to add an error description column to existing error output data in the data flow.</span></span>  
  
 <span data-ttu-id="9ccb4-111">如需如何設定腳本元件做為資料流程中的轉換的詳細資訊，請參閱[使用腳本元件建立同步轉換](../extending-packages-scripting-data-flow-script-component-types/creating-a-synchronous-transformation-with-the-script-component.md)和[使用腳本元件建立異步轉換](../extending-packages-scripting-data-flow-script-component-types/creating-an-asynchronous-transformation-with-the-script-component.md)。</span><span class="sxs-lookup"><span data-stu-id="9ccb4-111">For more information about how to configure the Script component for use as a transformation in the data flow, see [Creating a Synchronous Transformation with the Script Component](../extending-packages-scripting-data-flow-script-component-types/creating-a-synchronous-transformation-with-the-script-component.md)and [Creating an Asynchronous Transformation with the Script Component](../extending-packages-scripting-data-flow-script-component-types/creating-an-asynchronous-transformation-with-the-script-component.md).</span></span>  
  
#### <a name="to-configure-this-script-component-example"></a><span data-ttu-id="9ccb4-112">設定此指令碼元件範例</span><span class="sxs-lookup"><span data-stu-id="9ccb4-112">To configure this Script Component example</span></span>  
  
1.  <span data-ttu-id="9ccb4-113">在建立新指令碼元件之前，請先設定資料流程中的上游元件，使它在錯誤或截斷發生時將資料列重新導向至其錯誤輸出。</span><span class="sxs-lookup"><span data-stu-id="9ccb4-113">Before creating the new Script component, configure an upstream component in the data flow to redirect rows to its error output when an error or truncation occurs.</span></span> <span data-ttu-id="9ccb4-114">為了進行測試，您可能會想要以確定錯誤將發生的方式設定元件，例如，在查閱將失敗的兩個資料表之間，設定「查閱」轉換。</span><span class="sxs-lookup"><span data-stu-id="9ccb4-114">For testing purposes, you may want to configure a component in a manner that ensures that errors will occur-for example, by configuring a Lookup transformation between two tables where the lookup will fail.</span></span>  
  
2.  <span data-ttu-id="9ccb4-115">將新指令碼元件加入資料流程設計師介面，並將它設定為轉換。</span><span class="sxs-lookup"><span data-stu-id="9ccb4-115">Add a new Script component to the Data Flow designer surface and configure it as a transformation.</span></span>  
  
3.  <span data-ttu-id="9ccb4-116">從上游元件將錯誤輸出連接至新指令碼元件。</span><span class="sxs-lookup"><span data-stu-id="9ccb4-116">Connect the error output from the upstream component to the new Script component.</span></span>  
  
4.  <span data-ttu-id="9ccb4-117">開啟**指令碼轉換編輯器**，然後在 [指令碼]\*\*\*\* 頁面上選取 **ScriptLanguage** 屬性的指令碼語言。</span><span class="sxs-lookup"><span data-stu-id="9ccb4-117">Open the **Script Transformation Editor**, and on the **Script** page, for the **ScriptLanguage** property, select the script language.</span></span>  
  
5.  <span data-ttu-id="9ccb4-118">按一下 [編輯指令碼]\*\*\*\* 以開啟 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA) IDE，並新增以下所示的範例程式碼。</span><span class="sxs-lookup"><span data-stu-id="9ccb4-118">Click **Edit Script** to open the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA) IDE and add the sample code shown below.</span></span>  
  
6.  <span data-ttu-id="9ccb4-119">關閉 VSTA。</span><span class="sxs-lookup"><span data-stu-id="9ccb4-119">Close VSTA.</span></span>  
  
7.  <span data-ttu-id="9ccb4-120">在 [腳本轉換編輯器] 的 [**輸入資料行**] 頁面上，選取 [ErrorCode] 資料行。</span><span class="sxs-lookup"><span data-stu-id="9ccb4-120">In the Script Transformation Editor, on the **Input Columns** page, select the ErrorCode column.</span></span>  
  
8.  <span data-ttu-id="9ccb4-121">在 [**輸入和輸出**] 頁面上，加入 `String` 名為**ErrorDescription**之類型的新輸出資料行。</span><span class="sxs-lookup"><span data-stu-id="9ccb4-121">On the **Inputs and Outputs** page, add a new output column of type `String` named **ErrorDescription**.</span></span> <span data-ttu-id="9ccb4-122">將新資料行的預設長度增加至 255，以支援長訊息。</span><span class="sxs-lookup"><span data-stu-id="9ccb4-122">Increase the default length of the new column to 255 to support long messages.</span></span>  
  
9. <span data-ttu-id="9ccb4-123">關閉**指令碼轉換編輯器**。</span><span class="sxs-lookup"><span data-stu-id="9ccb4-123">Close the **Script Transformation Editor.**</span></span>  
  
10. <span data-ttu-id="9ccb4-124">將指令碼元件的輸出附加至適當的目的地。</span><span class="sxs-lookup"><span data-stu-id="9ccb4-124">Attach the output of the Script component to a suitable destination.</span></span> <span data-ttu-id="9ccb4-125">一般檔案目的地對於特定測試而言是最容易設定的。</span><span class="sxs-lookup"><span data-stu-id="9ccb4-125">A Flat File destination is the easiest to configure for ad hoc testing.</span></span>  
  
11. <span data-ttu-id="9ccb4-126">執行封裝。</span><span class="sxs-lookup"><span data-stu-id="9ccb4-126">Run the package.</span></span>  
  
```vb  
Public Class ScriptMain  
    Inherits UserComponent  
    Public Overrides Sub Input0_ProcessInputRow(ByVal Row As Input0Buffer)  
  
  Row.ErrorDescription = _  
    Me.ComponentMetaData.GetErrorDescription(Row.ErrorCode)  
  
    End Sub  
End Class  
```  
  
```csharp  
public class ScriptMain:  
    UserComponent  
{  
    public override void Input0_ProcessInputRow(Input0Buffer Row)  
    {  
  
  Row.ErrorDescription = this.ComponentMetaData.GetErrorDescription(Row.ErrorCode);  
  
    }  
}  
  
```  
  
<span data-ttu-id="9ccb4-127">![Integration Services 圖示 (小型) ](../media/dts-16.gif "Integration Services 圖示 (小)")會**保持最**新狀態 Integration Services  </span><span class="sxs-lookup"><span data-stu-id="9ccb4-127">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="9ccb4-128">若要取得 Microsoft 的最新下載、文件、範例和影片以及社群中的精選解決方案，請瀏覽 MSDN 上的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 頁面：</span><span class="sxs-lookup"><span data-stu-id="9ccb4-128">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="9ccb4-129">瀏覽 MSDN 上的 Integration Services 頁面</span><span class="sxs-lookup"><span data-stu-id="9ccb4-129">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="9ccb4-130">若要得到這些更新的自動通知，請訂閱該頁面上所提供的 RSS 摘要。</span><span class="sxs-lookup"><span data-stu-id="9ccb4-130">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ccb4-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9ccb4-131">See Also</span></span>  
 <span data-ttu-id="9ccb4-132">[資料中的錯誤處理](../data-flow/error-handling-in-data.md) </span><span class="sxs-lookup"><span data-stu-id="9ccb4-132">[Error Handling in Data](../data-flow/error-handling-in-data.md) </span></span>  
 <span data-ttu-id="9ccb4-133">[在資料流程元件中使用錯誤輸出](../extending-packages-custom-objects/data-flow/using-error-outputs-in-a-data-flow-component.md) </span><span class="sxs-lookup"><span data-stu-id="9ccb4-133">[Using Error Outputs in a Data Flow Component](../extending-packages-custom-objects/data-flow/using-error-outputs-in-a-data-flow-component.md) </span></span>  
 [<span data-ttu-id="9ccb4-134">使用指令碼元件建立同步轉換</span><span class="sxs-lookup"><span data-stu-id="9ccb4-134">Creating a Synchronous Transformation with the Script Component</span></span>](../extending-packages-scripting-data-flow-script-component-types/creating-a-synchronous-transformation-with-the-script-component.md) 
  
  
