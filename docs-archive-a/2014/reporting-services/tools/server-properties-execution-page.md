---
title: 伺服器屬性 (執行頁面) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.serverproperties.execution.f1
ms.assetid: 53b77db1-b013-4dac-82dd-30c0de276639
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f0ec8725a0cec9e15cb6d8402f8d654320c38471
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597015"
---
# <a name="server-properties-execution-page"></a><span data-ttu-id="9a181-102">伺服器屬性 (執行頁面)</span><span class="sxs-lookup"><span data-stu-id="9a181-102">Server Properties (Execution Page)</span></span>
  <span data-ttu-id="9a181-103">使用此頁面，即可設定報表執行的逾時值。</span><span class="sxs-lookup"><span data-stu-id="9a181-103">Use this page to set a timeout value for report execution.</span></span> <span data-ttu-id="9a181-104">此值適用於由目前報表伺服器執行個體處理的所有報表。</span><span class="sxs-lookup"><span data-stu-id="9a181-104">This value applies to all reports that are processed by the current report server instance.</span></span> <span data-ttu-id="9a181-105">您可以針對個別報表覆寫此值。</span><span class="sxs-lookup"><span data-stu-id="9a181-105">You can override this value for individual reports.</span></span> <span data-ttu-id="9a181-106">您所指定的值必須配合在報表伺服器上進行的所有報表處理，再加上報表伺服器擷取報表中所使用的資料時，於資料庫伺服器上執行的查詢處理。</span><span class="sxs-lookup"><span data-stu-id="9a181-106">The value you specify must accommodate all report processing that occurs on the report server, plus query processing performed on the database server when the report server retrieves data that is used in the report.</span></span>  
  
 <span data-ttu-id="9a181-107">若要開啟此頁面，請啟動 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、連接至報表伺服器執行個體、以滑鼠右鍵按一下報表伺服器名稱，然後選取 [屬性]  。</span><span class="sxs-lookup"><span data-stu-id="9a181-107">To open this page, start [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to a report server instance, right-click the report server name, and select **Properties**.</span></span> <span data-ttu-id="9a181-108">按一下 **[執行]** ，即可開啟此頁面。</span><span class="sxs-lookup"><span data-stu-id="9a181-108">Click **Execution** to open this page.</span></span>  
  
## <a name="options"></a><span data-ttu-id="9a181-109">選項。</span><span class="sxs-lookup"><span data-stu-id="9a181-109">Options</span></span>  
 <span data-ttu-id="9a181-110">**執行報表時，不要計算逾時值**</span><span class="sxs-lookup"><span data-stu-id="9a181-110">**Do not timeout report execution**</span></span>  
 <span data-ttu-id="9a181-111">讓報表伺服器完成報表處理不受時間限制。</span><span class="sxs-lookup"><span data-stu-id="9a181-111">Allow a report server unlimited time to complete report processing.</span></span>  
  
 <span data-ttu-id="9a181-112">**限制報表僅能執行下列秒數**</span><span class="sxs-lookup"><span data-stu-id="9a181-112">**Limit report execution to the following number of seconds**</span></span>  
 <span data-ttu-id="9a181-113">設定報表執行的時間條件約束。</span><span class="sxs-lookup"><span data-stu-id="9a181-113">Set a time constraint on report execution.</span></span> <span data-ttu-id="9a181-114">要求報表時，系統就會開始計算時間週期。</span><span class="sxs-lookup"><span data-stu-id="9a181-114">The time period starts when the report is requested.</span></span> <span data-ttu-id="9a181-115">如果報表尚未處理完畢而時間週期已結束，報表伺服器就會取消此處理序，以及對外部資料來源的所有同處理序查詢。</span><span class="sxs-lookup"><span data-stu-id="9a181-115">If the time period ends before the report is fully processed, the report server cancels the process and any in-process queries to external data sources.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a181-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9a181-116">See Also</span></span>  
 <span data-ttu-id="9a181-117">[設定報表伺服器屬性 &#40;Management Studio&#41;](set-report-server-properties-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="9a181-117">[Set Report Server Properties &#40;Management Studio&#41;](set-report-server-properties-management-studio.md) </span></span>  
 <span data-ttu-id="9a181-118">[連接至 Management Studio 中的報表伺服器](connect-to-a-report-server-in-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="9a181-118">[Connect to a Report Server in Management Studio](connect-to-a-report-server-in-management-studio.md) </span></span>  
 <span data-ttu-id="9a181-119">[設定報表處理屬性](../report-server/set-report-processing-properties.md) </span><span class="sxs-lookup"><span data-stu-id="9a181-119">[Set Report Processing Properties](../report-server/set-report-processing-properties.md) </span></span>  
 <span data-ttu-id="9a181-120">[設定報表和共用資料集處理的逾時值 &#40;SSRS&#41;](../report-server/setting-time-out-values-for-report-and-shared-dataset-processing-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="9a181-120">[Setting Time-out Values for Report and Shared Dataset Processing &#40;SSRS&#41;](../report-server/setting-time-out-values-for-report-and-shared-dataset-processing-ssrs.md) </span></span>  
 [<span data-ttu-id="9a181-121">Management Studio F1 說明中的報表伺服器</span><span class="sxs-lookup"><span data-stu-id="9a181-121">Report Server in Management Studio F1 Help</span></span>](report-server-in-management-studio-f1-help.md)  
  
  
