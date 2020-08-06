---
title: 處理 (MDX) 時發生錯誤 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- scripts [MDX], exceptions
- exceptions [MDX]
ms.assetid: bc6ff0af-9fe6-44d6-bc3c-801d71ea41a9
author: minewiskan
ms.author: owend
ms.openlocfilehash: 357194b9f789fdeacfb65ce3c894d4747867eafb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598619"
---
# <a name="error-handling-mdx"></a><span data-ttu-id="c5423-102">錯誤處理 (MDX)</span><span class="sxs-lookup"><span data-stu-id="c5423-102">Error Handling (MDX)</span></span>
  <span data-ttu-id="c5423-103">每個 Cube 都可以控制多維度運算式 (MDX) 指令碼內錯誤的處理方式。</span><span class="sxs-lookup"><span data-stu-id="c5423-103">Each cube can control how errors within a Multidimensional Expressions (MDX) script are handled.</span></span> <span data-ttu-id="c5423-104">透過 `ScriptErrorHandlingMode` 列舉值便可完成錯誤處理。</span><span class="sxs-lookup"><span data-stu-id="c5423-104">Error handling is done through the `ScriptErrorHandlingMode` enumerator.</span></span> <span data-ttu-id="c5423-105">此列舉值可能出現的值如下：</span><span class="sxs-lookup"><span data-stu-id="c5423-105">The possible values for this enumerator are:</span></span>  
  
 `IgnoreNone`  
 <span data-ttu-id="c5423-106">當 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 發現 MDX 腳本中有任何錯誤時，會導致伺服器引發錯誤。</span><span class="sxs-lookup"><span data-stu-id="c5423-106">Causes the server to raise an error when [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] finds any error in the MDX script.</span></span>  
  
 `IgnoreAll`  
 <span data-ttu-id="c5423-107">使伺服器忽略 MDX 指令碼中內含錯誤的所有命令，包括語法錯誤、名稱解析錯誤等等。</span><span class="sxs-lookup"><span data-stu-id="c5423-107">Causes the server to ignore all commands in the MDX script that contain an error, including syntax errors, name resolution errors, and more.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5423-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c5423-108">See Also</span></span>  
 <xref:Microsoft.AnalysisServices.Cube.ScriptErrorHandlingMode%2A>  
  
  
