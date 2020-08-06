---
title: 將組件參考新增至報表 (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- code [Reporting Services]
- custom assemblies [Reporting Services], referencing
- custom code [Reporting Services]
- adding assembly references
- assemblies [Reporting Services], references
ms.assetid: 0a03939e-48ce-4c30-b227-98533f2e0ccb
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 23dda0c65589e55849f906c621e42ce70f0d7ab5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598219"
---
# <a name="add-an-assembly-reference-to-a-report-ssrs"></a><span data-ttu-id="e11dc-102">將組件參考加入至報表 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="e11dc-102">Add an Assembly Reference to a Report (SSRS)</span></span>
  <span data-ttu-id="e11dc-103">當您內嵌的自訂程式碼包含 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 類別的參考，而該類別不在 <xref:System.Math> 或 <xref:System.Convert> 中時，則必須提供此報表的組件參考以讓報表處理器可以解析名稱。</span><span class="sxs-lookup"><span data-stu-id="e11dc-103">When you embed custom code that contains references to [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] classes that are not in <xref:System.Math> or <xref:System.Convert>, you must provide an assembly reference to the report so that the report processor can resolve the names.</span></span> <span data-ttu-id="e11dc-104">如需詳細資訊，請參閱[將程式碼加入至報表 &#40;SSRS&#41;](add-code-to-a-report-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="e11dc-104">For more information, see [Add Code to a Report &#40;SSRS&#41;](add-code-to-a-report-ssrs.md).</span></span>  
  
### <a name="to-add-an-assembly-reference-to-a-report"></a><span data-ttu-id="e11dc-105">若要將組件參考加入至報表</span><span class="sxs-lookup"><span data-stu-id="e11dc-105">To add an assembly reference to a report</span></span>  
  
1.  <span data-ttu-id="e11dc-106">在 [設計]  檢視中，以滑鼠右鍵按一下報表框線外面的設計介面，然後按一下 [報表屬性]  。</span><span class="sxs-lookup"><span data-stu-id="e11dc-106">In **Design** view, right-click the design surface outside the border of the report and click **Report Properties**.</span></span>  
  
2.  <span data-ttu-id="e11dc-107">按一下 **[參考]** 。</span><span class="sxs-lookup"><span data-stu-id="e11dc-107">Click **References**.</span></span>  
  
3.  <span data-ttu-id="e11dc-108">在 **[加入或移除組件]** 中，按一下 **[加入]** ，然後按一下省略符號按鈕，瀏覽至該組件。</span><span class="sxs-lookup"><span data-stu-id="e11dc-108">In **Add or remove assemblies**, click **Add** and then click the ellipsis button to browse to the assembly.</span></span>  
  
4.  <span data-ttu-id="e11dc-109">在 **[加入或移除類別]** 中，按一下 **[加入]** ，然後輸入類別的名稱，再提供報表內所要使用的執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="e11dc-109">In **Add or remove classes**, click **Add** and then type name of the class and provide an instance name to use within the report.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e11dc-110">只針對以執行個體為基礎的成員，指定類別和執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="e11dc-110">Specify a class and instance name only for instance-based members.</span></span> <span data-ttu-id="e11dc-111">請勿指定 **[類別]** 清單中的靜態成員。</span><span class="sxs-lookup"><span data-stu-id="e11dc-111">Do not specify static members in the **Classes** list.</span></span> <span data-ttu-id="e11dc-112">如需詳細資訊，請參閱 [報表設計師中運算式的自訂程式碼及組件參考 &#40;SSRS&#41;](custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="e11dc-112">For more information, see [Custom Code and Assembly References in Expressions in Report Designer &#40;SSRS&#41;](custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md).</span></span>  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e11dc-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e11dc-113">See Also</span></span>  
 <span data-ttu-id="e11dc-114">[將自訂組件與報表搭配使用](../custom-assemblies/using-custom-assemblies-with-reports.md) </span><span class="sxs-lookup"><span data-stu-id="e11dc-114">[Using Custom Assemblies with Reports](../custom-assemblies/using-custom-assemblies-with-reports.md) </span></span>  
 [<span data-ttu-id="e11dc-115">報表屬性對話方塊、參考</span><span class="sxs-lookup"><span data-stu-id="e11dc-115">Report Properties Dialog Box, References</span></span>](../report-properties-dialog-box-references.md)  
  
  
