---
title: 使用變數和參數 (MDX) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- parameters [MDX]
- queries [MDX], variables
- queries [MDX], parameters
- variables [MDX]
ms.assetid: a4754d16-d9c4-49f6-9be0-392180b912e4
author: minewiskan
ms.author: owend
ms.openlocfilehash: fd01cf78ea5e3284aa51cad7dc848176a5dc9298
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705569"
---
# <a name="using-variables-and-parameters-mdx"></a><span data-ttu-id="6d005-102">使用變數與參數 (MDX)</span><span class="sxs-lookup"><span data-stu-id="6d005-102">Using Variables and Parameters (MDX)</span></span>
  <span data-ttu-id="6d005-103">在中 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] ，您可以 (MDX) 語句參數化多維度運算式。</span><span class="sxs-lookup"><span data-stu-id="6d005-103">In [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], you can parameterize a Multidimensional Expressions (MDX) statement.</span></span> <span data-ttu-id="6d005-104">您可以使用參數化陳述式，建立可在執行階段自訂的一般陳述式。</span><span class="sxs-lookup"><span data-stu-id="6d005-104">A parameterized statement lets you create generic statements that can be customized at runtime.</span></span>  
  
 <span data-ttu-id="6d005-105">在建立參數化陳述式時，您可以在名稱前面加上 @ 符號，來識別參數名稱。</span><span class="sxs-lookup"><span data-stu-id="6d005-105">In creating a parameterized statement, you identify the parameter name by prefixing the name with the at sign (@).</span></span> <span data-ttu-id="6d005-106">例如， @Year 會是有效的參數名稱</span><span class="sxs-lookup"><span data-stu-id="6d005-106">For example, @Year would be a valid parameter name</span></span>  
  
 <span data-ttu-id="6d005-107">MDX 只支援常值或純量值的參數。</span><span class="sxs-lookup"><span data-stu-id="6d005-107">MDX supports only parameters for literal or scalar values.</span></span> <span data-ttu-id="6d005-108">若要建立參考成員、集合或 Tuple 的參數，您必須使用函數，例如 [StrToMember](/sql/mdx/strtomember-mdx) 或 [StrToSet](/sql/mdx/strtoset-mdx)。</span><span class="sxs-lookup"><span data-stu-id="6d005-108">To create a parameter that references a member, set, or tuple, you would have to use a function such as [StrToMember](/sql/mdx/strtomember-mdx) or [StrToSet](/sql/mdx/strtoset-mdx).</span></span>  
  
 <span data-ttu-id="6d005-109">在下列 XML for Analysis 中 (XMLA) 範例中， @CountryName 參數會包含取得客戶資料的國家/地區：</span><span class="sxs-lookup"><span data-stu-id="6d005-109">In the following XML for Analysis (XMLA) example, the @CountryName parameter will contain the country for which customer data is retrieved:</span></span>  
  
```  
<Envelope xmlns="http://schemas.xmlsoap.org/soap/envelope/">  
  <Body>  
    <Execute xmlns="urn:schemas-microsoft-com:xml-analysis">  
      <Command>  
        <Statement>  
select [Measures].members on 0,   
       Filter(Customer.[Customer Geography].Country.members,   
              Customer.[Customer Geography].CurrentMember.Name =  
              @CountryName) on 1  
from [Adventure Works]  
</Statement>  
      </Command>  
      <Properties />  
      <Parameters>  
        <Parameter>  
          <Name>CountryName</Name>  
          <Value>'United Kingdom'</Value>  
        </Parameter>  
      </Parameters>  
    </Execute>  
  </Body>  
</Envelope>  
```  
  
 <span data-ttu-id="6d005-110">若要將此功能與 OLE DB 搭配使用，您可以使用 `ICommandWithParameters` 介面。</span><span class="sxs-lookup"><span data-stu-id="6d005-110">To use this functionality with OLE DB, you would use the `ICommandWithParameters` interface.</span></span> <span data-ttu-id="6d005-111">此功能若要與 ADOMD.Net 搭配使用，您可以使用 **AdomdCommand.Parameters** 集合。</span><span class="sxs-lookup"><span data-stu-id="6d005-111">To use this functionality with ADOMD.Net, you would use the **AdomdCommand.Parameters** collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d005-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6d005-112">See Also</span></span>  
 [<span data-ttu-id="6d005-113">MDX 指令碼基礎觀念 &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="6d005-113">MDX Scripting Fundamentals &#40;Analysis Services&#41;</span></span>](mdx-scripting-fundamentals-analysis-services.md)  
  
  
