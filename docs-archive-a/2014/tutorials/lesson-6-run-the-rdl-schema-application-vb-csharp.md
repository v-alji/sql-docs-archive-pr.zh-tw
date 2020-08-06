---
title: '第6課：執行 RDL 架構應用程式 (VB-C # ) |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: a2cd2386-2df8-4b69-ab81-9ad1a31f6d27
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 5a0fc2cd9c12b4b1602f517dc215ca44e686c663
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686551"
---
# <a name="lesson-6-run-the-rdl-schema-application-vb-c"></a><span data-ttu-id="53255-102">第6課：執行 RDL 架構應用程式 (VB-C # ) </span><span class="sxs-lookup"><span data-stu-id="53255-102">Lesson 6: Run the RDL Schema Application (VB-C#)</span></span>
  [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] <span data-ttu-id="53255-103">提供兩種從整合式開發環境 (IDE) 建立與執行主控台應用程式的方法：</span><span class="sxs-lookup"><span data-stu-id="53255-103">offers two methods to build and run a console application from the integrated development environment (IDE):</span></span>  
  
-   <span data-ttu-id="53255-104">啟動並偵錯</span><span class="sxs-lookup"><span data-stu-id="53255-104">Start (with Debugging)</span></span>  
  
-   <span data-ttu-id="53255-105">啟動但不偵錯</span><span class="sxs-lookup"><span data-stu-id="53255-105">Start without Debugging</span></span>  
  
### <a name="to-build-and-run-the-samplerdlschema-application"></a><span data-ttu-id="53255-106">建立並執行 SampleRDLSchema 應用程式</span><span class="sxs-lookup"><span data-stu-id="53255-106">To build and run the SampleRDLSchema application</span></span>  
  
1.  <span data-ttu-id="53255-107">從 [偵錯]\*\*\*\* 功能表，按一下 [啟動但不偵錯]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="53255-107">From the **Debug** menu, click **Start Without Debugging**.</span></span> <span data-ttu-id="53255-108">這能確保在程式執行完成後，主控台視窗仍維持開啟的狀態。</span><span class="sxs-lookup"><span data-stu-id="53255-108">This ensures that the console window remains open after the program has finished executing.</span></span>  
  
     <span data-ttu-id="53255-109">應用程式會列印以下的輸出結果到主控台中：</span><span class="sxs-lookup"><span data-stu-id="53255-109">The application prints the following output to the console:</span></span>  
  
    ```  
    Loading Report Definition  
    Updating Report Definition  
    - Old Description: <Old Report Description>  
    - New Description: <New Report Description>  
    Publishing Report Definition  
    ```  
  
2.  <span data-ttu-id="53255-110">按任意鍵，關閉主控台。</span><span class="sxs-lookup"><span data-stu-id="53255-110">Press any key to close the console.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="53255-111">發生的任何錯誤都會寫入主控台。</span><span class="sxs-lookup"><span data-stu-id="53255-111">Any errors that occur are written to the console.</span></span>  
  
3.  <span data-ttu-id="53255-112">範例應用程式完成執行以後，會將已更新的報表副本儲存至報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="53255-112">When the sample application is finished running an updated copy of the report will be saved to the report server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53255-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="53255-113">See Also</span></span>  
 <span data-ttu-id="53255-114">[使用從 RDL 架構產生的類別更新報表 &#40;SSRS 教學課程&#41;](../../2014/tutorials/updating-reports-using-classes-generated-from-the-rdl-schema-ssrs-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="53255-114">[Updating Reports Using Classes Generated from the RDL Schema &#40;SSRS Tutorial&#41;](../../2014/tutorials/updating-reports-using-classes-generated-from-the-rdl-schema-ssrs-tutorial.md) </span></span>  
 [<span data-ttu-id="53255-115">報表定義語言 &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="53255-115">Report Definition Language &#40;SSRS&#41;</span></span>](../reporting-services/reports/report-definition-language-ssrs.md)  
  
  
