---
title: 建立連結的報表 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- linked reports [Reporting Services], creating
ms.assetid: 12be8341-cb57-45e8-a421-2bf66b50234d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ed5e70c9ff8179ae05186685e21303693fc9aed7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597570"
---
# <a name="create-a-linked-report"></a><span data-ttu-id="b1128-102">建立連結報表</span><span class="sxs-lookup"><span data-stu-id="b1128-102">Create a Linked Report</span></span>
  <span data-ttu-id="b1128-103">連結報表是提供現有報表之存取點的報表伺服器項目。</span><span class="sxs-lookup"><span data-stu-id="b1128-103">A linked report is a report server item that provides an access point to an existing report.</span></span> <span data-ttu-id="b1128-104">它在概念上類似於您用來執行程式或開啟檔案的程式捷徑。</span><span class="sxs-lookup"><span data-stu-id="b1128-104">Conceptually, it is similar to a program shortcut that you use to run a program or open a file.</span></span>

 <span data-ttu-id="b1128-105">連結報表是從現有的報表衍生，並保留原始的報表定義。</span><span class="sxs-lookup"><span data-stu-id="b1128-105">A linked report is derived from an existing report and retains the original's report definition.</span></span> <span data-ttu-id="b1128-106">連結報表一律繼承原始報表的報表配置與資料來源屬性。</span><span class="sxs-lookup"><span data-stu-id="b1128-106">A linked report always inherits report layout and data source properties of the original report.</span></span> <span data-ttu-id="b1128-107">其他所有屬性與設定可以和原始報表不同，包括安全性、參數、位置、訂閱，以及排程。</span><span class="sxs-lookup"><span data-stu-id="b1128-107">All other properties and settings can be different from those of the original report, including security, parameters, location, subscriptions, and schedules.</span></span>

 <span data-ttu-id="b1128-108">您想要建立現有報表的其他版本時，可以建立連結報表。</span><span class="sxs-lookup"><span data-stu-id="b1128-108">You can create a linked report when you want to create additional versions of an existing report.</span></span> <span data-ttu-id="b1128-109">例如，您可以使用單一區域銷售報表，來建立您所有銷售地區的區域特定報表。</span><span class="sxs-lookup"><span data-stu-id="b1128-109">For example, you could use a single regional sales report to create region-specific reports for all of your sales territories.</span></span>

 <span data-ttu-id="b1128-110">雖然連結報表通常是以參數化報表為基礎，但參數化報表並不是必要的。</span><span class="sxs-lookup"><span data-stu-id="b1128-110">Although linked reports are typically based on parameterized reports, a parameterized report is not required.</span></span> <span data-ttu-id="b1128-111">每當您想要以不同的設定部署現有的報表時，都可以建立連結報表。</span><span class="sxs-lookup"><span data-stu-id="b1128-111">You can create linked reports whenever you want to deploy an existing report with different settings.</span></span>

### <a name="to-create-a-linked-report"></a><span data-ttu-id="b1128-112">若要建立連結報表</span><span class="sxs-lookup"><span data-stu-id="b1128-112">To create a linked report</span></span>

1.  <span data-ttu-id="b1128-113">在報表管理員中，導覽至包含您要連結之報表的資料夾，然後開啟選項功能表。您可以按一下 **[建立連結報表]**。</span><span class="sxs-lookup"><span data-stu-id="b1128-113">In Report Manager, navigate to the folder containing the report that you want to link to, and then open the options menu can click **Create Linked Report**.</span></span>

2.  <span data-ttu-id="b1128-114">輸入新連結報表的名稱。</span><span class="sxs-lookup"><span data-stu-id="b1128-114">Type a name for the new linked report.</span></span> <span data-ttu-id="b1128-115">選擇性地輸入描述。</span><span class="sxs-lookup"><span data-stu-id="b1128-115">Optionally type a description.</span></span>

3.  <span data-ttu-id="b1128-116">若要選取報表的其他資料夾，請按一下 **[變更位置]**。</span><span class="sxs-lookup"><span data-stu-id="b1128-116">To select a different folder for the report, click **Change Location**.</span></span> <span data-ttu-id="b1128-117">按一下您要使用的資料夾，或者在 **[位置]** 方塊中輸入資料夾名稱。</span><span class="sxs-lookup"><span data-stu-id="b1128-117">Click the folder you want to use, or type the folder name in the **Location** box.</span></span> [!INCLUDE[clickOK](../../../includes/clickok-md.md)] <span data-ttu-id="b1128-118">如果您未選取其他資料夾，則會在目前的資料夾 (儲存基準報表的位置) 中建立連結報表。</span><span class="sxs-lookup"><span data-stu-id="b1128-118">If you do not select a different folder, the linked report is created in the current folder (where the report it is based on is stored).</span></span>

4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)] <span data-ttu-id="b1128-119">連結報表隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="b1128-119">The linked report opens.</span></span>

     <span data-ttu-id="b1128-120">連結報表的圖示與報表伺服器所管理的其他項目不同。</span><span class="sxs-lookup"><span data-stu-id="b1128-120">A linked report's icon differs from other items managed by a report server.</span></span> <span data-ttu-id="b1128-121">下列圖示表示連結報表：</span><span class="sxs-lookup"><span data-stu-id="b1128-121">The following icon indicates a linked report:</span></span>

     <span data-ttu-id="b1128-122">![連結報表圖示](../media/hlp-16linked.gif "連結報表圖示")</span><span class="sxs-lookup"><span data-stu-id="b1128-122">![Linked report icon](../media/hlp-16linked.gif "Linked report icon")</span></span>

## <a name="see-also"></a><span data-ttu-id="b1128-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b1128-123">See Also</span></span>
 <span data-ttu-id="b1128-124">[開啟和關閉報表 &#40;報表管理員&#41;](../reports/open-and-close-a-report-report-manager.md) [新的連結報表頁面 &#40;報表管理員](../new-linked-report-page-report-manager.md)&#41;[選擇專案位置] 頁面 &#40;報表管理員](../choose-item-location-page-report-manager.md)&#41;[一般屬性頁面、報表 &#40;報表管理員](../general-properties-page-reports-report-manager.md)&#41;Reporting Services 的 &#40;[概念&#41;ssrs 報表管理員](../reporting-services-concepts-ssrs.md) [&#40;&#41;ssrs 原生模式](../report-manager-ssrs-native-mode.md)</span><span class="sxs-lookup"><span data-stu-id="b1128-124">[Open and Close a Report &#40;Report Manager&#41;](../reports/open-and-close-a-report-report-manager.md) [New Linked Report Page &#40;Report Manager&#41;](../new-linked-report-page-report-manager.md) [Choose Item Location Page &#40;Report Manager&#41;](../choose-item-location-page-report-manager.md) [General Properties Page, Reports &#40;Report Manager&#41;](../general-properties-page-reports-report-manager.md) [Reporting Services Concepts &#40;SSRS&#41;](../reporting-services-concepts-ssrs.md) [Report Manager  &#40;SSRS Native Mode&#41;](../report-manager-ssrs-native-mode.md)</span></span>


