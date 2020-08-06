---
title: XML 輸出檔案格式 (ssbdiagnose) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- XML output file format [ssbdiagnose]
- ssbdiagnose
ms.assetid: 3ceb991b-6f15-4504-8828-de5adf448bc5
author: stevestein
ms.author: sstein
ms.openlocfilehash: 612b317f7220f502faf1adc82cf9c1dcc8bc20a8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704533"
---
# <a name="xml-output-file-format-ssbdiagnose"></a><span data-ttu-id="45cc6-102">XML 輸出檔格式 (ssbdiagnose)</span><span class="sxs-lookup"><span data-stu-id="45cc6-102">XML Output File Format (ssbdiagnose)</span></span>
  <span data-ttu-id="45cc6-103">當您執行 **ssbdiagnose** 公用程式搭配 **-XML** 參數時，此公用程式就會將其輸出傳遞成 XML 檔。</span><span class="sxs-lookup"><span data-stu-id="45cc6-103">The **ssbdiagnose** utility delivers its output as an XML file when you run it with the **-XML** switch.</span></span> <span data-ttu-id="45cc6-104">其 XML 輸出檔會列出標頭資訊以及它在分析之 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 組態或交談中找到的錯誤。</span><span class="sxs-lookup"><span data-stu-id="45cc6-104">The XML output file lists header information and the errors that it found in the [!INCLUDE[ssSB](../../includes/sssb-md.md)] configuration or conversation that was analyzed.</span></span> <span data-ttu-id="45cc6-105">您可以撰寫應用程式來分析或報告該檔案中所列的錯誤。</span><span class="sxs-lookup"><span data-stu-id="45cc6-105">You can write an application to analyze or report on the errors listed in the file.</span></span> <span data-ttu-id="45cc6-106">或者，您可以在一般 XML 編輯器 (例如 XML Notepad) 中檢視此 XML 檔。</span><span class="sxs-lookup"><span data-stu-id="45cc6-106">Or, you can view the XML file in a general XML editor, such as XML Notepad.</span></span>  
  
 <span data-ttu-id="45cc6-107">**ssbdiangose** 輸出檔包含具有兩種子類型的 DiagnosticInformation 根元素：</span><span class="sxs-lookup"><span data-stu-id="45cc6-107">An **ssbdiangose** output file contains a DiagnosticInformation root element with two child types:</span></span>  
  
-   <span data-ttu-id="45cc6-108">具有標頭資訊的 Banner 元素。</span><span class="sxs-lookup"><span data-stu-id="45cc6-108">A Banner element with header information.</span></span>  
  
-   <span data-ttu-id="45cc6-109">**ssbdiagnose**所報告之每個問題的 Issue 元素。</span><span class="sxs-lookup"><span data-stu-id="45cc6-109">An Issue element for each issue that is reported by **ssbdiagnose**.</span></span>  
  
## <a name="diagnosticinformation-root-element"></a><span data-ttu-id="45cc6-110">DiagnosticInformation 根元素</span><span class="sxs-lookup"><span data-stu-id="45cc6-110">DiagnosticInformation Root Element</span></span>  
  
-   [<span data-ttu-id="45cc6-111">DiagnosticInformation 元素 &#40;ssbdiagnose&#41;</span><span class="sxs-lookup"><span data-stu-id="45cc6-111">DiagnosticInformation Element &#40;ssbdiagnose&#41;</span></span>](diagnosticinformation-element-ssbdiagnose.md)  
  
## <a name="banner-element"></a><span data-ttu-id="45cc6-112">Banner 元素</span><span class="sxs-lookup"><span data-stu-id="45cc6-112">Banner Element</span></span>  
  
-   [<span data-ttu-id="45cc6-113">Banner 元素 &#40;ssbdiagnose&#41;</span><span class="sxs-lookup"><span data-stu-id="45cc6-113">Banner Element &#40;ssbdiagnose&#41;</span></span>](banner-element-ssbdiagnose.md)  
  
## <a name="issue-element"></a><span data-ttu-id="45cc6-114">Issue 元素</span><span class="sxs-lookup"><span data-stu-id="45cc6-114">Issue Element</span></span>  
  
-   [<span data-ttu-id="45cc6-115">Issue 元素 &#40;ssbdiagnose&#41;</span><span class="sxs-lookup"><span data-stu-id="45cc6-115">Issue Element &#40;ssbdiagnose&#41;</span></span>](issue-element-ssbdiagnose.md)  
  
## <a name="see-also"></a><span data-ttu-id="45cc6-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="45cc6-116">See Also</span></span>  
 [<span data-ttu-id="45cc6-117">ssbdiagnose 公用程式 &#40;Service Broker&#41;</span><span class="sxs-lookup"><span data-stu-id="45cc6-117">ssbdiagnose Utility &#40;Service Broker&#41;</span></span>](ssbdiagnose-utility-service-broker.md)  
  
  
