---
title: 新的連結報表頁面 (報表管理員) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: fefb46e8-6901-4d50-a3f8-7c49ad72e7b1
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 61138e51cfd9bb6e1ee124dd4aa3bc224d8aebcf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598240"
---
# <a name="new-linked-report-page-report-manager"></a><span data-ttu-id="29b79-102">新增連結報表頁面 (報表管理員)</span><span class="sxs-lookup"><span data-stu-id="29b79-102">New Linked Report Page (Report Manager)</span></span>
  <span data-ttu-id="29b79-103">使用 [新增連結報表] 頁面即可建立連結報表。</span><span class="sxs-lookup"><span data-stu-id="29b79-103">Use the New Linked Report page to create a linked report.</span></span> <span data-ttu-id="29b79-104">連結報表具有專屬的設定值和屬性，但連結至另一個報表的報表定義。</span><span class="sxs-lookup"><span data-stu-id="29b79-104">A linked report is a report with settings and properties of its own, but links to the report definition of another report.</span></span> <span data-ttu-id="29b79-105">當您有想要針對特定群組或使用者改變的基底報表時，連結報表就很有用。例如，根據您指定為參數之區域碼傳回不同資料的區域報表。</span><span class="sxs-lookup"><span data-stu-id="29b79-105">Linked reports are useful when you have a base report that you want to vary for specific groups or users; for example, a regional report that returns different data based on a regional code that you specify as a parameter.</span></span> <span data-ttu-id="29b79-106">通常是在變更參數化的報表時建立連結報表，然後以不同的參數值儲存每一個報表執行個體。</span><span class="sxs-lookup"><span data-stu-id="29b79-106">A linked report is typically created from a parameterized report when you want to vary and then save different parameter values with each report instance.</span></span> <span data-ttu-id="29b79-107">不過，可以從您有權存取的任何報表來建立連結報表。</span><span class="sxs-lookup"><span data-stu-id="29b79-107">However, you can create a linked report from any report to which you have access.</span></span>  
  
 <span data-ttu-id="29b79-108">連結報表可以有自己的名稱、描述、位置、參數屬性、報表執行屬性、報表記錄屬性、權限和訂閱。</span><span class="sxs-lookup"><span data-stu-id="29b79-108">A linked report can have its own name, description, location, parameter properties, report execution properties, report history properties, permissions, and subscriptions.</span></span> <span data-ttu-id="29b79-109">不過，連結報表必須使用提供報表定義之基底報表的資料來源屬性和配置。</span><span class="sxs-lookup"><span data-stu-id="29b79-109">However, a linked report must use the data source properties and layout of the base report that provides the report definition.</span></span>  
  
## <a name="navigation"></a><span data-ttu-id="29b79-110">導覽</span><span class="sxs-lookup"><span data-stu-id="29b79-110">Navigation</span></span>  
 <span data-ttu-id="29b79-111">您可以使用下列程序，在使用者介面 (UI) 中導覽至這個位置。</span><span class="sxs-lookup"><span data-stu-id="29b79-111">Use the following procedures to navigate to this location in the user interface (UI).</span></span>  
  
###### <a name="to-open-the-new-linked-report-page-from-the-contents-page"></a><span data-ttu-id="29b79-112">若要從內容頁面開啟新增連結報表頁面</span><span class="sxs-lookup"><span data-stu-id="29b79-112">To open the New Linked Report page from the Contents page</span></span>  
  
1.  <span data-ttu-id="29b79-113">開啟報表管理員，然後找出您想要建立連結報表的報表。</span><span class="sxs-lookup"><span data-stu-id="29b79-113">Open Report Manager, and locate a report for which you want to create a linked report.</span></span>  
  
2.  <span data-ttu-id="29b79-114">將滑鼠停留在該報表上，然後按一下下拉箭號。</span><span class="sxs-lookup"><span data-stu-id="29b79-114">Hover over the report, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="29b79-115">在下拉式功能表中，按一下 **[建立連結報表]**。</span><span class="sxs-lookup"><span data-stu-id="29b79-115">In the drop-down menu, click **Create Linked Report**.</span></span>  
  
###### <a name="to-open-the-new-linked-report-page-from-the-general-properties-page-of-a-report"></a><span data-ttu-id="29b79-116">若要從報表的一般屬性頁面開啟新增連結報表頁面</span><span class="sxs-lookup"><span data-stu-id="29b79-116">To open the New Linked Report page from the General properties page of a report</span></span>  
  
1.  <span data-ttu-id="29b79-117">開啟報表管理員，然後找出您想要建立連結報表的報表。</span><span class="sxs-lookup"><span data-stu-id="29b79-117">Open Report Manager, and locate a report for which you want to create a linked report.</span></span>  
  
2.  <span data-ttu-id="29b79-118">將滑鼠停留在該報表上，然後按一下下拉箭號。</span><span class="sxs-lookup"><span data-stu-id="29b79-118">Hover over the report, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="29b79-119">在下拉式功能表中，按一下 **[管理]**。</span><span class="sxs-lookup"><span data-stu-id="29b79-119">In the drop-down menu, click **Manage**.</span></span> <span data-ttu-id="29b79-120">這樣就會開啟該報表的 [一般] 屬性頁面。</span><span class="sxs-lookup"><span data-stu-id="29b79-120">This opens the General properties page for the report.</span></span>  
  
4.  <span data-ttu-id="29b79-121">在項目工具列中，按一下 **[建立連結報表]**。</span><span class="sxs-lookup"><span data-stu-id="29b79-121">In the item toolbar, click **Create Linked Report**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="29b79-122">選項。</span><span class="sxs-lookup"><span data-stu-id="29b79-122">Options</span></span>  
 <span data-ttu-id="29b79-123">**名稱**</span><span class="sxs-lookup"><span data-stu-id="29b79-123">**Name**</span></span>  
 <span data-ttu-id="29b79-124">指定連結報表的名稱。</span><span class="sxs-lookup"><span data-stu-id="29b79-124">Specify the name of the linked report.</span></span> <span data-ttu-id="29b79-125">名稱必須至少包含一個英數字元。</span><span class="sxs-lookup"><span data-stu-id="29b79-125">A name must contain at least one alphanumeric character.</span></span> <span data-ttu-id="29b79-126">也可以包含空格和特定符號。</span><span class="sxs-lookup"><span data-stu-id="29b79-126">It can also include spaces and certain symbols.</span></span> <span data-ttu-id="29b79-127">不過，您不可以使用 ; ?</span><span class="sxs-lookup"><span data-stu-id="29b79-127">However, you must not use the characters ; ?</span></span> <span data-ttu-id="29b79-128">： \@ & = +，$/\* \< > |"或/指定名稱時。</span><span class="sxs-lookup"><span data-stu-id="29b79-128">: \@ & = + , $ / \* \< > | " or / when specifying a name.</span></span>  
  
 <span data-ttu-id="29b79-129">**說明**</span><span class="sxs-lookup"><span data-stu-id="29b79-129">**Description**</span></span>  
 <span data-ttu-id="29b79-130">輸入報表內容的描述。</span><span class="sxs-lookup"><span data-stu-id="29b79-130">Type a description of the report contents.</span></span> <span data-ttu-id="29b79-131">此描述顯示在有權存取此報表的使用者的 [內容] 頁面上。</span><span class="sxs-lookup"><span data-stu-id="29b79-131">This description appears in the Contents page to users who have permission to access the report.</span></span>  
  
 <span data-ttu-id="29b79-132">**位置**</span><span class="sxs-lookup"><span data-stu-id="29b79-132">**Location**</span></span>  
 <span data-ttu-id="29b79-133">指定含有此報表的資料夾路徑。</span><span class="sxs-lookup"><span data-stu-id="29b79-133">Specify the folder path that contains the report.</span></span> <span data-ttu-id="29b79-134">在預設狀況下，建立的連結報表與基礎報表為同層級。</span><span class="sxs-lookup"><span data-stu-id="29b79-134">By default, linked reports are created as siblings to the base report.</span></span> <span data-ttu-id="29b79-135">按一下 **[變更位置]** 即可將連結報表置於不同的資料夾中。</span><span class="sxs-lookup"><span data-stu-id="29b79-135">Click **Change Location** to put the linked report in a different folder.</span></span>  
  
 <span data-ttu-id="29b79-136">**確定**</span><span class="sxs-lookup"><span data-stu-id="29b79-136">**OK**</span></span>  
 <span data-ttu-id="29b79-137">按一下 **[確定]** 即可儲存變更，並回到基底報表的 [一般] 屬性頁面。</span><span class="sxs-lookup"><span data-stu-id="29b79-137">Click **OK** to save your changes and return to the General properties page of the base report.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29b79-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="29b79-138">See Also</span></span>  
 <span data-ttu-id="29b79-139">[建立連結報表](reports/create-a-linked-report.md) </span><span class="sxs-lookup"><span data-stu-id="29b79-139">[Create a Linked Report](reports/create-a-linked-report.md) </span></span>  
 <span data-ttu-id="29b79-140">[一般屬性頁面、報表 &#40;報表管理員&#41;](../../2014/reporting-services/general-properties-page-reports-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="29b79-140">[General Properties Page, Reports &#40;Report Manager&#41;](../../2014/reporting-services/general-properties-page-reports-report-manager.md) </span></span>  
 [<span data-ttu-id="29b79-141">報表管理員 F1 說明</span><span class="sxs-lookup"><span data-stu-id="29b79-141">Report Manager F1 Help</span></span>](../../2014/reporting-services/report-manager-f1-help.md)  
  
  
