---
title: 定義指派和其他指令碼命令 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- empty scripts [Analysis Services]
- calculations [Analysis Services], scripts
- MDX [Analysis Services], scripts
- scripts [Analysis Services], calculations
ms.assetid: f28b9b22-3dc7-4a45-b4eb-2d023f2c94b8
author: minewiskan
ms.author: owend
ms.openlocfilehash: 184c998bb4bd27d077cca78e792a7e7712f87666
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598621"
---
# <a name="define-assignments-and-other-script-commands"></a><span data-ttu-id="a850d-102">定義指派和其他指令碼命令</span><span class="sxs-lookup"><span data-stu-id="a850d-102">Define Assignments and Other Script Commands</span></span>
  <span data-ttu-id="a850d-103">在 [Cube 設計師] 的 [計算]\*\*\*\* 索引標籤上，按一下工具列上的**新增指令碼命令**圖示，來建立空的指令碼。</span><span class="sxs-lookup"><span data-stu-id="a850d-103">On the **Calculations** tab of Cube Designer, click the **New ScriptCommand** icon on the toolbar to create an empty script.</span></span> <span data-ttu-id="a850d-104">當您建立新的腳本時，在 [計算] 索引標籤的 [**腳本召集人**] 窗格中，一開始會顯示空白的標題。您在 [計算運算式] 窗格中輸入的字元，會在 [**腳本召集人**] 中顯示為專案的名稱。</span><span class="sxs-lookup"><span data-stu-id="a850d-104">When you create a new script, it initially is displayed with a blank title in the **Script Organizer** pane of the Calculations tab. The characters you type in the Calculation Expressions pane will be visible as the name of the item in **Script Organizer**.</span></span> <span data-ttu-id="a850d-105">所以您可能想要在第一列輸入註解的名稱，以便更輕易地識別 [指令碼組合管理]\*\*\*\* 窗格中的指令碼。</span><span class="sxs-lookup"><span data-stu-id="a850d-105">Therefore, you may want to type a commented name on the first line to more easily identify the script in the **Script Organizer** pane.</span></span> <span data-ttu-id="a850d-106">如需詳細資訊，請參閱 [Introduction to MDX Scripting in Microsoft SQL Server 2005](https://go.microsoft.com/fwlink/?LinkId=81892) (Microsoft SQL Server 2005 的 MDX 指令碼簡介)。</span><span class="sxs-lookup"><span data-stu-id="a850d-106">For more information, see [Introduction to MDX Scripting in Microsoft SQL Server 2005](https://go.microsoft.com/fwlink/?LinkId=81892).</span></span> <span data-ttu-id="a850d-107">如需 MDX 查詢和計算相關效能問題的詳細資訊，請參閱《 [SQL Server 2005 Analysis Services 效能指南》](https://docsbay.net/Microsoft-SQL-Server-2005-Analysis-Services-Performance-Guide)中的「撰寫有效率的 MDX」一節。</span><span class="sxs-lookup"><span data-stu-id="a850d-107">For more information about performance issues related to MDX queries and calculations, see the section "Writing Efficient MDX" in the [SQL Server 2005 Analysis Services Performance Guide](https://docsbay.net/Microsoft-SQL-Server-2005-Analysis-Services-Performance-Guide).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="a850d-108">當您最初切換到 [Cube 設計師] 的 [計算]\*\*\*\* 索引標籤時，[指令碼組合管理]\*\*\*\* 窗格會包含具有 CALCULATE 命令的單一指令碼。</span><span class="sxs-lookup"><span data-stu-id="a850d-108">When you initially switch to the **Calculations** tab of Cube Designer, the **Script Organizer** pane contains a single script with a CALCULATE command.</span></span> <span data-ttu-id="a850d-109">唯有當您想要手動指定要如何彙總 Cube 時，CALCULATE 命令才會控制 Cube 中資料格的彙總，也才需要編輯。</span><span class="sxs-lookup"><span data-stu-id="a850d-109">The CALCULATE command controls the aggregation of the cells in the cube and should be edited only if you intend to manually specify how the cube is to be aggregated.</span></span>  
  
 <span data-ttu-id="a850d-110">您可以使用 [計算運算式] 窗格，來建立採用多維度運算式 (MDX) 語法的運算式。</span><span class="sxs-lookup"><span data-stu-id="a850d-110">You can use the Calculation Expressions pane to build an expression in Multidimensional Expressions (MDX) syntax.</span></span> <span data-ttu-id="a850d-111">當您建立運算式時，可以將 Cube 元件、函數以及範本，從 [計算工具]\*\*\*\* 窗格拖放或複製到 [計算運算式] 窗格。</span><span class="sxs-lookup"><span data-stu-id="a850d-111">While you build the expression, you can drag or copy cube components, functions, and templates from the **Calculation Tools** pane to the Calculation Expressions pane.</span></span> <span data-ttu-id="a850d-112">此舉會將項目的指令碼加入 [計算運算式] 窗格中，您放下或貼上它的位置。</span><span class="sxs-lookup"><span data-stu-id="a850d-112">Doing so adds the script for the item to the Calculation Expressions pane in the location that you drop or paste it.</span></span> <span data-ttu-id="a850d-113">用適當的值來取代引數及其分隔符號 (« 和 »)。</span><span class="sxs-lookup"><span data-stu-id="a850d-113">Replace arguments and their delimiters (« and ») with the appropriate values.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="a850d-114">當使用 [計算運算式] 窗格來撰寫包含多個陳述式的運算式時，請確定 MDX 指令碼的所有列 (除了最後一列之外) 都用分號 (;) 結束。</span><span class="sxs-lookup"><span data-stu-id="a850d-114">When writing an expression that contains multiple statements using the Calculation Expressions pane, ensure that all lines except the last line of the MDX script end with a semi-colon (;).</span></span> <span data-ttu-id="a850d-115">計算會串連成單一 MDX 指令碼，且每個指令碼都附加一個分號，以確定會正確編譯 MDX 指令碼。</span><span class="sxs-lookup"><span data-stu-id="a850d-115">Calculations are concatenated into a single MDX script, and each script has a semi-colon appended to it to ensure that the MDX script compiles correctly.</span></span> <span data-ttu-id="a850d-116">如果您將分號加入 [計算運算式] 窗格中指令碼的最後一列，Cube 就會正確地建立及部署，但您將無法針對它執行查詢。</span><span class="sxs-lookup"><span data-stu-id="a850d-116">If you add a semi-colon to the last line of the script in the Calculation Expressions pane, the cube will build and deploy correctly but you will be unable to run queries against it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a850d-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a850d-117">See Also</span></span>  
 [<span data-ttu-id="a850d-118">多維度模型中的計算</span><span class="sxs-lookup"><span data-stu-id="a850d-118">Calculations in Multidimensional Models</span></span>](calculations-in-multidimensional-models.md)  
  
  
