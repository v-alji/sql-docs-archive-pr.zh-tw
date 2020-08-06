---
title: 報表參數概念 (報表產生器和 SSRS) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: b0aa2159-4e49-4713-8824-5ef9a9edbc62
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 4b740362daea83b50a62f0b4453ce818ab21ace7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688573"
---
# <a name="report-parameters-concept-report-builder-and-ssrs"></a><span data-ttu-id="f7a3a-102">報表參數概念 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="f7a3a-102">Report Parameters Concept (Report Builder and SSRS)</span></span>
  <span data-ttu-id="f7a3a-103">您可以將參數加入至報表，以便連結相關報表、控制報表外觀、篩選報表資料，或是將報表的範圍縮小至特定使用者或位置。</span><span class="sxs-lookup"><span data-stu-id="f7a3a-103">You can add parameters to a report to link related reports, to control the report appearance, to filter report data, or to narrow the scope of a report to specific users or locations.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
 <span data-ttu-id="f7a3a-104">報表參數是透過下列方式建立：</span><span class="sxs-lookup"><span data-stu-id="f7a3a-104">Report parameters are created in the following ways:</span></span>  
  
-   <span data-ttu-id="f7a3a-105">當您定義包含查詢變數的資料集查詢時自動建立。</span><span class="sxs-lookup"><span data-stu-id="f7a3a-105">Automatically, when you define dataset query that contains query variables.</span></span> <span data-ttu-id="f7a3a-106">系統會針對每個查詢變數建立具有相同名稱的對應資料集查詢參數和報表參數。</span><span class="sxs-lookup"><span data-stu-id="f7a3a-106">For each query variable, a corresponding dataset query parameter and report parameter with the same names are created.</span></span> <span data-ttu-id="f7a3a-107">查詢參數可能是查詢變數的參考，或預存程序之輸入參數的參考。</span><span class="sxs-lookup"><span data-stu-id="f7a3a-107">A query parameter can be a reference to a query variable or to an input parameter for a stored procedure.</span></span>  
  
-   <span data-ttu-id="f7a3a-108">當您加入包含查詢參數之共用資料集的參考時自動建立。</span><span class="sxs-lookup"><span data-stu-id="f7a3a-108">Automatically, when you add a reference to a shared dataset that contains query parameters.</span></span>  
  
-   <span data-ttu-id="f7a3a-109">當您在 [報表資料] 窗格中建立報表參數時手動建立。</span><span class="sxs-lookup"><span data-stu-id="f7a3a-109">Manually, when you create report parameters in the Report Data pane.</span></span> <span data-ttu-id="f7a3a-110">報表是您可以在報表的運算式中包含的其中一個內建集合。</span><span class="sxs-lookup"><span data-stu-id="f7a3a-110">Parameters are one of the built-in collections that you can include in an expression in a report.</span></span> <span data-ttu-id="f7a3a-111">運算式是用來定義整個報表定義中的值，因此，您可以使用參數來控制報表外觀，或將值傳遞到也使用參數的相關子報表或報表中。</span><span class="sxs-lookup"><span data-stu-id="f7a3a-111">Because expressions are used to define values throughout a report definition, you can use parameters to control report appearance or to pass values to related subreports or reports that also use parameters.</span></span>  
  
 <span data-ttu-id="f7a3a-112">如需詳細資訊，請參閱 MSDN 上的 [報表參數 &#40;報表產生器和報表設計師&#41;](report-parameters-report-builder-and-report-designer.md)類型之報表資料來源為基礎的資料集。</span><span class="sxs-lookup"><span data-stu-id="f7a3a-112">For more information, see [Report Parameters &#40;Report Builder and Report Designer&#41;](report-parameters-report-builder-and-report-designer.md).</span></span>  
  
 <span data-ttu-id="f7a3a-113">在將資料傳回報表之前和之後，通常會使用參數來篩選報表資料。</span><span class="sxs-lookup"><span data-stu-id="f7a3a-113">Parameters are frequently used to filter report data both before and after the data is returned to the report.</span></span> <span data-ttu-id="f7a3a-114">如需詳細資訊，請參閱 [篩選、分組和排序資料 &#40;報表產生器及 SSRS&#41;](filter-group-and-sort-data-report-builder-and-ssrs.md)(將互動式排序加入資料表或矩陣 (報表產生器及 SSRS))。</span><span class="sxs-lookup"><span data-stu-id="f7a3a-114">For more information, see [Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;](filter-group-and-sort-data-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="f7a3a-115">當您設計報表時，報表參數會儲存在報表定義中。</span><span class="sxs-lookup"><span data-stu-id="f7a3a-115">When you design a report, report parameters are saved in the report definition.</span></span> <span data-ttu-id="f7a3a-116">當您發行報表時，報表參數會儲存，並且與報表定義分開管理。</span><span class="sxs-lookup"><span data-stu-id="f7a3a-116">When you publish a report, report parameters are saved and managed separately from the report definition.</span></span> <span data-ttu-id="f7a3a-117">將報表儲存到報表伺服器之後，您可以執行下列操作：</span><span class="sxs-lookup"><span data-stu-id="f7a3a-117">After you save the report to the report server, you can do the following:</span></span>  
  
-   <span data-ttu-id="f7a3a-118">直接在報表伺服器上，從報表定義個別變更報表參數值。</span><span class="sxs-lookup"><span data-stu-id="f7a3a-118">Change report parameter values directly on the report server independently from the report definition.</span></span>  
  
-   <span data-ttu-id="f7a3a-119">建立多個連結報表，其中每個連結報表都是一個報表定義的連結，這些報表定義中包含一組個別的參數值，您可以在報表伺服器上分別管理這些參數值。</span><span class="sxs-lookup"><span data-stu-id="f7a3a-119">Create multiple linked reports in which each linked report is a link to the report definition with a separate set of parameter values that can be managed independently on the report server.</span></span>  
  
 <span data-ttu-id="f7a3a-120">如果您打算建立報表快照集、記錄或已發行報表的訂閱，則必須了解報表參數如何影響報表的設計需求。</span><span class="sxs-lookup"><span data-stu-id="f7a3a-120">If you plan to create report snapshots, histories, or subscriptions to a published report, you must understand how report parameters affect the design requirements for the report.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7a3a-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f7a3a-121">See Also</span></span>  
 <span data-ttu-id="f7a3a-122">[報表撰寫概念 &#40;報表產生器和 SSRS&#41;](report-authoring-concepts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f7a3a-122">[Report Authoring Concepts &#40;Report Builder and SSRS&#41;](report-authoring-concepts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="f7a3a-123">[報表內嵌資料集和共用資料集 &#40;報表產生器和 SSRS&#41;](../report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f7a3a-123">[Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;](../report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="f7a3a-124">教學課程：將參數加入至報表 &#40;報表產生器&#41;</span><span class="sxs-lookup"><span data-stu-id="f7a3a-124">Tutorial: Add a Parameter to Your Report &#40;Report Builder&#41;</span></span>](../tutorial-add-a-parameter-to-your-report-report-builder.md)  
  
  
