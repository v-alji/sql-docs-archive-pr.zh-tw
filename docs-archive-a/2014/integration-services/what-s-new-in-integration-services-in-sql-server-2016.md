---
title: 新 (Integration Services) 的&#39;|Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Integration Services, what's new
- what's new [Integration Services]
ms.assetid: da6999c7-e5e3-4a59-a284-1da635995af1
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 84f0b668407c89e1d6acc3c8cfbda73f129ca19a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599563"
---
# <a name="what39s-new-integration-services"></a><span data-ttu-id="71c5d-102">&#39;s 新 (Integration Services) </span><span class="sxs-lookup"><span data-stu-id="71c5d-102">What&#39;s New (Integration Services)</span></span>
  [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]<span data-ttu-id="71c5d-103">與 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 舊版不相同。</span><span class="sxs-lookup"><span data-stu-id="71c5d-103">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] is unchanged from the previous release.</span></span>  
  
 <span data-ttu-id="71c5d-104">如需其他 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] 產品和技術的相關資訊，請參閱[SQL Server 2014 中的新功能](../sql-server/what-s-new-in-sql-server-2016.md)。</span><span class="sxs-lookup"><span data-stu-id="71c5d-104">For information about other [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] products and technologies, see [What's New in SQL Server 2014](../sql-server/what-s-new-in-sql-server-2016.md).</span></span>  
  
 <span data-ttu-id="71c5d-105">如需商業智慧相關變更的詳細資訊 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ，請參閱[Analysis Services 和商業智慧的新功能](https://docs.microsoft.com/analysis-services/what-s-new-in-analysis-services)。</span><span class="sxs-lookup"><span data-stu-id="71c5d-105">For more information about changes related to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Business Intelligence, see [What's New in Analysis Services and Business Intelligence](https://docs.microsoft.com/analysis-services/what-s-new-in-analysis-services).</span></span>  
  
##  <a name="rich-xml-validation-output-in-the-xml-task"></a><a name="ValidateXML"></a> <span data-ttu-id="71c5d-106">XML 工作中詳細的 XML 驗證輸出</span><span class="sxs-lookup"><span data-stu-id="71c5d-106">Rich XML validation output in the XML Task</span></span>  
 <span data-ttu-id="71c5d-107">驗證 XML 文件，並啟用 XML 工作的 `ValidationDetails` 屬性以取得詳細的錯誤輸出。</span><span class="sxs-lookup"><span data-stu-id="71c5d-107">Validate XML documents and get rich error output by enabling the `ValidationDetails` property of the XML Task.</span></span> <span data-ttu-id="71c5d-108">在提供 `ValidationDetails` 屬性前，XML 工作所執行的 XML 驗證只會傳回結果為 True 或 False，而不會有錯誤的相關資訊及其位置。</span><span class="sxs-lookup"><span data-stu-id="71c5d-108">Before the `ValidationDetails` property was available, XML validation by the XML Task returned only a true or false result, with no information about errors or their locations.</span></span> <span data-ttu-id="71c5d-109">現在，當您將 `ValidationDetails` 設定為 True 時，輸出檔案即涵蓋每項錯誤的詳細資訊，包括行號及位置。</span><span class="sxs-lookup"><span data-stu-id="71c5d-109">Now, when you set `ValidationDetails` to true, the output file contains detailed information about every error including the line number and the position.</span></span> <span data-ttu-id="71c5d-110">您可以使用此資訊來了解、尋找及修正 XML 文件中的錯誤。</span><span class="sxs-lookup"><span data-stu-id="71c5d-110">You can use this information to understand, locate, and fix errors in XML documents.</span></span> <span data-ttu-id="71c5d-111">如需詳細資訊，請參閱＜ [Validate XML with the XML Task](control-flow/xml-task.md)＞。</span><span class="sxs-lookup"><span data-stu-id="71c5d-111">For more info, see [Validate XML with the XML Task](control-flow/xml-task.md).</span></span>  
  
 [!INCLUDE[ssIS](../includes/ssis-md.md)] <span data-ttu-id="71c5d-112">在 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] Service Pack 2 中引進了 `ValidationDetails` 屬性。</span><span class="sxs-lookup"><span data-stu-id="71c5d-112">introduced the `ValidationDetails` property in [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] Service Pack 2.</span></span> <span data-ttu-id="71c5d-113">這項新的屬性目前尚未經過宣布或記載。</span><span class="sxs-lookup"><span data-stu-id="71c5d-113">This new property was not announced or documented at that time.</span></span> <span data-ttu-id="71c5d-114">[!INCLUDE[ssSQL14](../includes/sssql14-md.md)] 及 SQL Server 2016 也提供 `ValidationDetails` 屬性。</span><span class="sxs-lookup"><span data-stu-id="71c5d-114">The `ValidationDetails` property is also available in [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] and in SQL Server 2016.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71c5d-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="71c5d-115">See Also</span></span>  
 [<span data-ttu-id="71c5d-116">SQL Server 2014 各版本所支援的功能</span><span class="sxs-lookup"><span data-stu-id="71c5d-116">Features Supported by the Editions of SQL Server 2014</span></span>](../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)  
  
  
