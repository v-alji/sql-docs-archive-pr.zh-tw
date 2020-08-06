---
title: 第 6 課：將 ReportViewer 控制項新增至應用程式 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: f9492a97-5609-4059-ae76-0fba111d4968
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: bb04008fa47801f0500de711592a3cec45ca3dd6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606080"
---
# <a name="lesson-6-add-a-reportviewer-control-to-the-application"></a><span data-ttu-id="b49c5-102">第 6 課：將 ReportViewer 控制項加入到應用程式</span><span class="sxs-lookup"><span data-stu-id="b49c5-102">Lesson 6: Add a ReportViewer Control to the Application</span></span>
  <span data-ttu-id="b49c5-103">使用 [報表精靈] 設計子報表之後，下一步是要將 ReportViewer 控制項加入至網站應用程式。</span><span class="sxs-lookup"><span data-stu-id="b49c5-103">After you design the child report by using the Report Wizard, your next step is to add a ReportViewer control to the website application.</span></span>  
  
### <a name="to-add-a-reportviewer-control-to-the-application"></a><span data-ttu-id="b49c5-104">若要將 ReportViewer 控制項加入至應用程式</span><span class="sxs-lookup"><span data-stu-id="b49c5-104">To add a ReportViewer control to the application</span></span>  
  
1.  <span data-ttu-id="b49c5-105">在**方案總管**中，以滑鼠右鍵按一下 **Default.aspx**，然後按一下 [檢視表設計師]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b49c5-105">In **Solution Explorer**, right-click **Default.aspx**, and then click **View Designer**.</span></span>  
  
2.  <span data-ttu-id="b49c5-106">從 [**工具箱**] 視窗的 [ **AJAX 擴充**功能] 群組中，將**ScriptManager**控制項拖曳至設計介面。</span><span class="sxs-lookup"><span data-stu-id="b49c5-106">From the **AJAX Extensions** group in the **Toolbox** window, drag a **ScriptManager** control to the design surface.</span></span>  
  
3.  <span data-ttu-id="b49c5-107">從 [報表]\*\*\*\* 群組，將 **ReportViewer** 控制項拖曳至設計介面上的 **ScriptManager** 控制項下方。</span><span class="sxs-lookup"><span data-stu-id="b49c5-107">From the **Reporting** group, drag a **ReportViewer** control to the design surface below the **ScriptManager** control.</span></span>  
  
4.  <span data-ttu-id="b49c5-108">按一下 **ReportViewer** 控制項右上角的箭頭，開啟 [ReportViewer 工作]\*\*\*\* 視窗。</span><span class="sxs-lookup"><span data-stu-id="b49c5-108">Open the **ReportViewer Tasks** window by clicking the arrow in the top right-hand corner of the **ReportViewer** control.</span></span>  
  
5.  <span data-ttu-id="b49c5-109">在 [**選擇報表**] 方塊中，選取您建立的父報表。</span><span class="sxs-lookup"><span data-stu-id="b49c5-109">In the **Choose Report** box, select Parent report you created.</span></span>  
  
     <span data-ttu-id="b49c5-110">當您選取報表時，報表中所使用的資料來源執行個體會自動建立。</span><span class="sxs-lookup"><span data-stu-id="b49c5-110">When you select a report, instances of data sources used in the report are created automatically.</span></span> <span data-ttu-id="b49c5-111">產生的程式碼會具現化每個 DataTable (及其 [DataSet](https://msdn.microsoft.com/library/system.data.dataset\(v=vs.100\).aspx) 容器)。</span><span class="sxs-lookup"><span data-stu-id="b49c5-111">Code is generated to instantiate each DataTable (and its [DataSet](https://msdn.microsoft.com/library/system.data.dataset\(v=vs.100\).aspx) container).</span></span> <span data-ttu-id="b49c5-112">[ObjectDataSource](https://msdn.microsoft.com/library/system.web.ui.webcontrols.objectdatasource\(v=vs.100\).aspx) 控制項會新增至設計介面，對應報表中使用的每個資料來源。</span><span class="sxs-lookup"><span data-stu-id="b49c5-112">An [ObjectDataSource](https://msdn.microsoft.com/library/system.web.ui.webcontrols.objectdatasource\(v=vs.100\).aspx) control is added to the design surface, corresponding to each data source used in the report.</span></span> <span data-ttu-id="b49c5-113">此資料來源控制項會自動設定。</span><span class="sxs-lookup"><span data-stu-id="b49c5-113">This data source control is configured automatically.</span></span>  
  
     <span data-ttu-id="b49c5-114">如果您使用 Microsoft Visual Studio 2012，請確定 ObjectDataSource 控制項與專案命名空間完全符合的 DataSet1 系結，如果完整名稱列在 [**選擇您的商務物件**] 下拉式清單方塊中 (例如，Projectnamespace. DataSet1TableAdapters. projectnamespace.dataset1tableadapters.producttableadapter) 。</span><span class="sxs-lookup"><span data-stu-id="b49c5-114">If you're using Microsoft Visual Studio 2012, make sure that the ObjectDataSource control is bound with DataSet1 that is fully qualified with the project namespace, if the fully qualified name is listed in the **Choose your business object** drop-down list box (for example, Projectnamespace.DataSet1TableAdapters.ProductTableAdapter).</span></span> <span data-ttu-id="b49c5-115">以滑鼠右鍵按一下 [ObjectDataSource]，然後按一下 [**設定資料來源**]，即可存取清單方塊。</span><span class="sxs-lookup"><span data-stu-id="b49c5-115">You access the list box by right-clicking ObjectDataSource, and then clicking **Configure Data Source**.</span></span>  
  
6.  <span data-ttu-id="b49c5-116">在 [建置] 功能表上，按一下 [建置網站]。</span><span class="sxs-lookup"><span data-stu-id="b49c5-116">On the Build menu, click Build website.</span></span>  
  
     <span data-ttu-id="b49c5-117">報表會進行編譯，而報表運算式中的任何錯誤 (像是語法錯誤) 都會出現在 [錯誤清單]  區域中。</span><span class="sxs-lookup"><span data-stu-id="b49c5-117">The report is compiled and any errors such as a syntax error in a report expression appear in the **Error List** area.</span></span> <span data-ttu-id="b49c5-118">按一下 Visual Studio 視窗底部的 [錯誤清單]  ，顯示 [錯誤清單]  區域。</span><span class="sxs-lookup"><span data-stu-id="b49c5-118">Click **Error List** at the bottom of the Visual Studio window to display the **Error List** area.</span></span>  
  
## <a name="next-task"></a><span data-ttu-id="b49c5-119">下一項工作</span><span class="sxs-lookup"><span data-stu-id="b49c5-119">Next Task</span></span>  
 <span data-ttu-id="b49c5-120">您已成功將 ReportViewer 控制項加入至網站應用程式。</span><span class="sxs-lookup"><span data-stu-id="b49c5-120">You have successfully added a ReportViewer control to the website application.</span></span> <span data-ttu-id="b49c5-121">接下來您將在父報表上加入鑽研動作。</span><span class="sxs-lookup"><span data-stu-id="b49c5-121">Next, you will add a drillthrough action on the parent report.</span></span>  
  
  
