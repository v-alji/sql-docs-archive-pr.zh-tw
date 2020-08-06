---
title: 將程式碼新增至報表 (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- code [Reporting Services]
- custom code [Reporting Services]
- expressions [Reporting Services], code
- adding code
- reports [Reporting Services], code
ms.assetid: 00ef8fc6-99fe-49b2-8a22-7eb475881dc4
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c1964e69d00e1a27da29ce8cfb73b7bee1bece7a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702486"
---
# <a name="add-code-to-a-report-ssrs"></a><span data-ttu-id="cea6f-102">將程式碼加入至報表 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="cea6f-102">Add Code to a Report (SSRS)</span></span>
  <span data-ttu-id="cea6f-103">在任何運算式中，您可以呼叫自己的自訂程式碼。</span><span class="sxs-lookup"><span data-stu-id="cea6f-103">In any expression, you can call your own custom code.</span></span> <span data-ttu-id="cea6f-104">您可以透過下列兩個方法來提供程式碼：</span><span class="sxs-lookup"><span data-stu-id="cea6f-104">You can provide code in the following two ways:</span></span>  
  
-   <span data-ttu-id="cea6f-105">將以 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 撰寫的程式碼直接內嵌在報表中。</span><span class="sxs-lookup"><span data-stu-id="cea6f-105">Embed code written in [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] directly in your report.</span></span> <span data-ttu-id="cea6f-106">如果程式碼參考的是非 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 或 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 的 <xref:System.Math> <xref:System.Convert>，則您必須在報表中新增參考。</span><span class="sxs-lookup"><span data-stu-id="cea6f-106">If your code refers to a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] that is not <xref:System.Math> or <xref:System.Convert>, you must add the reference to the report.</span></span> <span data-ttu-id="cea6f-107">如需詳細資訊，請參閱 [將組件參考加入至報表 &#40;SSRS&#41;](add-an-assembly-reference-to-a-report-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="cea6f-107">For more information, see [Add an Assembly Reference to a Report &#40;SSRS&#41;](add-an-assembly-reference-to-a-report-ssrs.md).</span></span> <span data-ttu-id="cea6f-108">如需可從程式碼建立之其他參考的詳細資訊，請參閱[報表設計師中運算式的自訂程式碼及組件參考 &#40;SSRS&#41;](custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="cea6f-108">For more information about other references you can make from your code, see [Custom Code and Assembly References in Expressions in Report Designer &#40;SSRS&#41;](custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md).</span></span>  
  
-   <span data-ttu-id="cea6f-109">藉由使用 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]來提供自訂程式碼組件。</span><span class="sxs-lookup"><span data-stu-id="cea6f-109">Provide a custom code assembly by using the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="cea6f-110">如果您提供自訂組件，您必須同時將它安裝在您撰寫報表的電腦上及檢視報表的報表伺服器上。</span><span class="sxs-lookup"><span data-stu-id="cea6f-110">If you provide a custom assembly, you must install it on both the computer where you author the report and the report server where you view the report.</span></span> <span data-ttu-id="cea6f-111">如需詳細資訊，請參閱 [Using Custom Assemblies with Reports](../custom-assemblies/using-custom-assemblies-with-reports.md)。</span><span class="sxs-lookup"><span data-stu-id="cea6f-111">For more information, see [Using Custom Assemblies with Reports](../custom-assemblies/using-custom-assemblies-with-reports.md).</span></span>  
  
### <a name="to-add-embedded-code-to-a-report"></a><span data-ttu-id="cea6f-112">將內嵌程式碼加入報表中</span><span class="sxs-lookup"><span data-stu-id="cea6f-112">To add embedded code to a report</span></span>  
  
1.  <span data-ttu-id="cea6f-113">在 [設計]  檢視中，以滑鼠右鍵按一下報表框線外面的設計介面，然後按一下 [報表屬性]  。</span><span class="sxs-lookup"><span data-stu-id="cea6f-113">In **Design** view, right-click the design surface outside the border of the report and click **Report Properties**.</span></span>  
  
2.  <span data-ttu-id="cea6f-114">按一下 **[程式碼]** 。</span><span class="sxs-lookup"><span data-stu-id="cea6f-114">Click **Code**.</span></span>  
  
3.  <span data-ttu-id="cea6f-115">在 **[自訂程式碼]** 中，輸入程式碼。</span><span class="sxs-lookup"><span data-stu-id="cea6f-115">In **Custom code**, type the code.</span></span> <span data-ttu-id="cea6f-116">當報表執行時，程式碼中的錯誤會產生警告。</span><span class="sxs-lookup"><span data-stu-id="cea6f-116">Errors in the code produce warnings when the report runs.</span></span> <span data-ttu-id="cea6f-117">下列範例會建立名為 `ChangeWord` 的自訂函數，以 "`Bike`" 取代 "`Bicycle`" 一字。</span><span class="sxs-lookup"><span data-stu-id="cea6f-117">The following example creates a custom function named `ChangeWord` that replaces the word "`Bike`" with "`Bicycle`".</span></span>  
  
    ```  
    Public Function ChangeWord(ByVal s As String) As String  
       Dim strBuilder As New System.Text.StringBuilder(s)  
       If s.Contains("Bike") Then  
          strBuilder.Replace("Bike", "Bicycle")  
          Return strBuilder.ToString()  
          Else : Return s  
       End If  
    End Function  
    ```  
  
4.  <span data-ttu-id="cea6f-118">下列範例示範如何在運算式中將名為 Category 的資料集欄位傳遞給這個函數：</span><span class="sxs-lookup"><span data-stu-id="cea6f-118">The following example shows how to pass a dataset field named Category to this function in an expression:</span></span>  
  
    ```  
    =Code.ChangeWord(Fields!Category.Value)  
    ```  
  
     <span data-ttu-id="cea6f-119">如果您將此運算式加入至顯示類別目錄值的資料表資料格，則每當 "Bike" 一字位於該資料列的資料集欄位中時，此資料表資料格值就會改為顯示 "Bicycle" 一字。</span><span class="sxs-lookup"><span data-stu-id="cea6f-119">If you add this expression to a table cell that displays category values, whenever the word "Bike" is in the dataset field for that row, the table cell value displays the word "Bicycle" instead.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cea6f-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cea6f-120">See Also</span></span>  
 <span data-ttu-id="cea6f-121">[報表屬性對話方塊、程式碼](../report-properties-dialog-box-code.md) </span><span class="sxs-lookup"><span data-stu-id="cea6f-121">[Report Properties Dialog Box, Code](../report-properties-dialog-box-code.md) </span></span>  
 <span data-ttu-id="cea6f-122">[運算式範例 &#40;報表產生器及 SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="cea6f-122">[Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="cea6f-123">參數集合參考 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="cea6f-123">Parameters Collection References &#40;Report Builder and SSRS&#41;</span></span>](built-in-collections-parameters-collection-references-report-builder.md)  
  
  
