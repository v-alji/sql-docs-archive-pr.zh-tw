---
title: 使用 URL 存取搜尋報表 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- searching reports
- text searches [Reporting Services]
- URL access [Reporting Services], report searches
ms.assetid: 6f3410c4-7944-448f-bae8-bab3e8152d46
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b45f3fabf58a0980d41ee7b4b89a771655477d02
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707037"
---
# <a name="search-a-report-using-url-access"></a><span data-ttu-id="02b6a-102">使用 URL 存取搜尋報表</span><span class="sxs-lookup"><span data-stu-id="02b6a-102">Search a Report Using URL Access</span></span>
  <span data-ttu-id="02b6a-103">您可以使用 URL 存取來搜尋特定文字集的報表。</span><span class="sxs-lookup"><span data-stu-id="02b6a-103">You can search a report for a specific set of text using URL access.</span></span> <span data-ttu-id="02b6a-104">若要搜尋報表，請在 URL 上將 *rc:FindString* 參數的值設定為等於您要搜尋的文字。</span><span class="sxs-lookup"><span data-stu-id="02b6a-104">To search a report, set the value of the *rc:FindString* parameter on the URL equal to the text for which you want to search.</span></span> <span data-ttu-id="02b6a-105">此外，請使用 *rc:StartFind* 和 *rc:EndFind* 參數，將搜尋縮小到報表內的特定頁面。</span><span class="sxs-lookup"><span data-stu-id="02b6a-105">Additionally, use the *rc:StartFind* and *rc:EndFind* parameters to narrow your search to specific pages within the report.</span></span>  
  
## <a name="example"></a><span data-ttu-id="02b6a-106">範例</span><span class="sxs-lookup"><span data-stu-id="02b6a-106">Example</span></span>  
 <span data-ttu-id="02b6a-107">下列的 URL 存取範例會在 Product Catalog 範例報表中搜尋第一個出現的 "Mountain-400" 文字 (搜尋開始於頁面 1，終止於頁面 5)：</span><span class="sxs-lookup"><span data-stu-id="02b6a-107">The following URL access example searches for the first occurrence of the text "Mountain-400" in the Product Catalog sample report starting with page one and ending with page five:</span></span>  
  
```  
http://server/Reportserver?/SampleReports/Product Catalog&rs:Command=Render&rc:StartFind=1&rc:EndFind=5&rc:FindString=Mountain-400  
```  
  
## <a name="see-also"></a><span data-ttu-id="02b6a-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="02b6a-108">See Also</span></span>  
 <span data-ttu-id="02b6a-109">[URL 存取 &#40;SSRS&#41;](url-access-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="02b6a-109">[URL Access &#40;SSRS&#41;](url-access-ssrs.md) </span></span>  
 [<span data-ttu-id="02b6a-110">URL 存取參數參考</span><span class="sxs-lookup"><span data-stu-id="02b6a-110">URL Access Parameter Reference</span></span>](url-access-parameter-reference.md)  
  
  
