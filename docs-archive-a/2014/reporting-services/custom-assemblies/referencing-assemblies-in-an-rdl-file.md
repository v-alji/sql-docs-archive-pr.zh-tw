---
title: 參考在 RDL 檔案中的組件 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- RDL [Reporting Services], referencing assemblies
- referencing custom assemblies
- custom assemblies [Reporting Services], referencing
- Report Definition Language, referencing assemblies
- report definition files [Reporting Services]
ms.assetid: 9a48e552-7d47-4243-9be1-894990c506d9
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 14593717d2319d7d702fd0c414e0c24428006f51
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687545"
---
# <a name="referencing-assemblies-in-an-rdl-file"></a><span data-ttu-id="6ad9b-102">參考在 RDL 檔案中的組件</span><span class="sxs-lookup"><span data-stu-id="6ad9b-102">Referencing Assemblies in an RDL File</span></span>
  <span data-ttu-id="6ad9b-103">為了支援報表定義檔案中自訂程式碼組件的用法，在 RDL 規格中加入了兩個報表定義語言 (RDL) 項目：**CodeModules** 項目與 **Classes** 項目。</span><span class="sxs-lookup"><span data-stu-id="6ad9b-103">To support the use of custom code assemblies in report definition files, two Report Definition Language (RDL) elements are included in the RDL specification: the **CodeModules** element and the **Classes** element.</span></span>  
  
 <span data-ttu-id="6ad9b-104">**CodeModules** 項目可讓您參考報表運算式中的 Managed 程式碼組件。</span><span class="sxs-lookup"><span data-stu-id="6ad9b-104">The **CodeModules** element enables you to refer to managed code assemblies in report expressions.</span></span> <span data-ttu-id="6ad9b-105">**CodeModules** 是最上層的項目，包含在報表定義檔案中用以呼叫特定函式的組件參考。</span><span class="sxs-lookup"><span data-stu-id="6ad9b-105">**CodeModules** is a top-level element that contains the reference to the assembly that you use in your report definition files to call specialized functions.</span></span> <span data-ttu-id="6ad9b-106">支援自訂組件用法的報表定義中的項目可能如下所示：</span><span class="sxs-lookup"><span data-stu-id="6ad9b-106">An entry in a report definition that supports the use of a custom assembly might look like the following:</span></span>  
  
```  
<CodeModules>  
   <CodeModule>CurrencyConversion, Version=1.0.1363.31103, Culture=neutral, PublicKeyToken=null</CodeModule>  
</CodeModules>  
```  
  
 <span data-ttu-id="6ad9b-107">請不要從自訂程式碼呼叫 <xref:System.Reflection.Assembly.Load%2A>，而是透過將 **CodeModule** 項目手動新增至 RDL 檔案，或是透過使用 [報表屬性]\*\*\*\* 對話方塊的 [參考]\*\*\*\* 索引標籤來註冊自訂組件。</span><span class="sxs-lookup"><span data-stu-id="6ad9b-107">Instead of calling <xref:System.Reflection.Assembly.Load%2A> from your custom code, register your custom assemblies by either manually adding **CodeModule** elements to your RDL file or by using the **References** tab of the **Report Properties** dialog.</span></span> <span data-ttu-id="6ad9b-108">如需詳細資訊，請參閱 [報表設計師中運算式的自訂程式碼及組件參考 &#40;SSRS&#41;](../report-design/custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="6ad9b-108">For more information, see [Custom Code and Assembly References in Expressions in Report Designer &#40;SSRS&#41;](../report-design/custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md).</span></span>  
  
 <span data-ttu-id="6ad9b-109">**Classes** 項目支援在報表定義中使用執行個體成員。</span><span class="sxs-lookup"><span data-stu-id="6ad9b-109">The **Classes** element supports the use of instance members in a report definition.</span></span> <span data-ttu-id="6ad9b-110">**Classes** 是最上層項目，包含類別名稱與執行個體名稱的參考。</span><span class="sxs-lookup"><span data-stu-id="6ad9b-110">**Classes** is a top-level element that contains a reference to the class name and an instance name.</span></span> <span data-ttu-id="6ad9b-111">支援使用執行個體成員之報表定義中的項目可能如下所示：</span><span class="sxs-lookup"><span data-stu-id="6ad9b-111">An entry in a report definition that supports the use of instance members might look like the following:</span></span>  
  
```  
<Classes>  
   <Class>  
      <ClassName>CurrencyConversion.DollarCurrencyConversion</ClassName>  
      <InstanceName>m_myDollarConversion</InstanceName>  
   </Class>  
</Classes>  
```  
  
 <span data-ttu-id="6ad9b-112">如需詳細資訊，請參閱[透過運算式存取自訂組件](accessing-custom-assemblies-through-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="6ad9b-112">For more information, see [Accessing Custom Assemblies Through Expressions](accessing-custom-assemblies-through-expressions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ad9b-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6ad9b-113">See Also</span></span>  
 [<span data-ttu-id="6ad9b-114">將自訂組件與報表搭配使用</span><span class="sxs-lookup"><span data-stu-id="6ad9b-114">Using Custom Assemblies with Reports</span></span>](using-custom-assemblies-with-reports.md)  
  
  
