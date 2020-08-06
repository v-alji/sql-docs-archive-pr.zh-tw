---
title: 第 9 課：建置並執行應用程式 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: f52d3f3a-0b09-4b34-9112-0b3655271587
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 068deb075f0f60dde634ac29f6f8f934448dc6a5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592507"
---
# <a name="lesson-9-build-and-run-the-application"></a><span data-ttu-id="ab663-102">Lesson 9: Build and Run the Application</span><span class="sxs-lookup"><span data-stu-id="ab663-102">Lesson 9: Build and Run the Application</span></span>
  <span data-ttu-id="ab663-103">建立資料表的資料篩選後，下一步是要建置和執行網站應用程式。</span><span class="sxs-lookup"><span data-stu-id="ab663-103">After you create a data filter for the data table, your next step is to build and run the website application.</span></span>

### <a name="to-build-and-run-the-application"></a><span data-ttu-id="ab663-104">若要建置並執行應用程式</span><span class="sxs-lookup"><span data-stu-id="ab663-104">To build and run the application</span></span>

1.  <span data-ttu-id="ab663-105">按下 **CTRL+F5** 執行 Default.aspx 頁面，但不偵錯；或按 F5 執行頁面並偵錯。</span><span class="sxs-lookup"><span data-stu-id="ab663-105">Press **CTRL+F5** to run the Default.aspx page without debugging, or press F5 to run the page with debugging.</span></span>

     <span data-ttu-id="ab663-106">在建置過程中，報表會進行編譯，而找到的任何錯誤 (例如報表中所使用運算式的語法錯誤) 都會加入至位於 Visual Studio 視窗底部的 **[工作清單]** 。</span><span class="sxs-lookup"><span data-stu-id="ab663-106">As part of the build process, the report is compiled and any errors found (such as a syntax error in an expression used in the report) are added to the **Task List** that is located at the bottom of the Visual Studio window.</span></span>

     <span data-ttu-id="ab663-107">網頁會出現在瀏覽器中。</span><span class="sxs-lookup"><span data-stu-id="ab663-107">The webpage appears in the browser.</span></span> <span data-ttu-id="ab663-108">ReportViewer 控制項會顯示報表。</span><span class="sxs-lookup"><span data-stu-id="ab663-108">The ReportViewer control displays the report.</span></span> <span data-ttu-id="ab663-109">您可以使用工具列瀏覽報表、縮放，以及將報表匯出至 Excel。</span><span class="sxs-lookup"><span data-stu-id="ab663-109">You can use the toolbar to browse through the report, zoom, and export the report to Excel.</span></span>

2.  <span data-ttu-id="ab663-110">將滑鼠停留在 **[名稱]** 資料行底下的任何資料列上方。</span><span class="sxs-lookup"><span data-stu-id="ab663-110">Hover the mouse over any of the rows under **Name** column.</span></span> <span data-ttu-id="ab663-111">滑鼠游標會顯示手掌符號。</span><span class="sxs-lookup"><span data-stu-id="ab663-111">The mouse cursor will display a Hand symbol.</span></span>

3.  <span data-ttu-id="ab663-112">按一下 **[名稱]** 資料行中的值。</span><span class="sxs-lookup"><span data-stu-id="ab663-112">Click a value in the **Name** column.</span></span> <span data-ttu-id="ab663-113">子報表隨即顯示，並且包含對應的篩選資料。</span><span class="sxs-lookup"><span data-stu-id="ab663-113">The child report is shown with the corresponding filtered data.</span></span>

4.  <span data-ttu-id="ab663-114">按一下 **ReportViewer**工具列中的 **[返回父報表]** 圖示，導覽回 **[父]** 報表。</span><span class="sxs-lookup"><span data-stu-id="ab663-114">Click the icon, **Go back to parent report**, in the **ReportViewer** tool bar to navigate back to the **Parent** report.</span></span>

     <span data-ttu-id="ab663-115">![ssrs 使用 ReportViewer 演練](../../2014/tutorials/media/ssrs-drillthrough-report.png "ssrs 使用 ReportViewer 演練")</span><span class="sxs-lookup"><span data-stu-id="ab663-115">![ssrs drill through using ReportViewer](../../2014/tutorials/media/ssrs-drillthrough-report.png "ssrs drill through using ReportViewer")</span></span>

5.  <span data-ttu-id="ab663-116">關閉瀏覽器即可結束。</span><span class="sxs-lookup"><span data-stu-id="ab663-116">Close the browser to exit.</span></span>


