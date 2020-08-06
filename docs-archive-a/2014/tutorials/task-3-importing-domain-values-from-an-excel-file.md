---
title: 工作3：從 Excel 檔案匯入定義域值 |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 242e8309-1195-495b-9cd5-aa127748c185
ms.author: lle
author: lrtoyou1223
ms.openlocfilehash: 707a3925bb6d0014e2a1248f904123b076024e2c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592392"
---
# <a name="task-3-importing-domain-values-from-an-excel-file"></a><span data-ttu-id="860f1-102">工作 3：從 Excel 檔案匯入定義域值</span><span class="sxs-lookup"><span data-stu-id="860f1-102">Task 3: Importing Domain Values from an Excel File</span></span>

  <span data-ttu-id="860f1-103">在此工作中，您會從 Excel 檔案的工作表匯入**State**定義域的值。</span><span class="sxs-lookup"><span data-stu-id="860f1-103">In this task, you import values for the **State** domain from a worksheet of an Excel file.</span></span>

1.  <span data-ttu-id="860f1-104">按一下 [**定義域清單**] 中的 [**狀態**網域]。</span><span class="sxs-lookup"><span data-stu-id="860f1-104">Click **State** domain in the **Domain list**.</span></span>

2.  <span data-ttu-id="860f1-105">確定 [**定義域值**] 索引標籤在右窗格中為作用中。</span><span class="sxs-lookup"><span data-stu-id="860f1-105">Ensure that the **Domain Values** tab is active in the right pane.</span></span>

3.  <span data-ttu-id="860f1-106">在右窗格中，從工具列按一下 [匯**入值**] 按鈕旁邊的**向下箭**號，然後按一下 [**從 Excel 匯入有效值**]。</span><span class="sxs-lookup"><span data-stu-id="860f1-106">In the right pane, from the toolbar, click **down arrow** next to the **Import Values** button, and click **Import Valid Values from Excel**.</span></span>

     <span data-ttu-id="860f1-107">![[從 Excel 匯入有效值] 功能表](../../2014/tutorials/media/et-importingdomainvaluesfromanexcelfile-01.jpg "[從 Excel 匯入有效值] 功能表")</span><span class="sxs-lookup"><span data-stu-id="860f1-107">![Import Valid Values from Excel Menu](../../2014/tutorials/media/et-importingdomainvaluesfromanexcelfile-01.jpg "Import Valid Values from Excel Menu")</span></span>

4.  <span data-ttu-id="860f1-108">按一下 **[流覽]**，選取 [ **Suppliers.xls**]，然後按一下 [**開啟**]。</span><span class="sxs-lookup"><span data-stu-id="860f1-108">Click **Browse**, select **Suppliers.xls**, and click **Open**.</span></span>

5.  <span data-ttu-id="860f1-109">針對**工作表**選取 [ **StatesToImport $** ]。</span><span class="sxs-lookup"><span data-stu-id="860f1-109">Select **StatesToImport$** for the **Worksheet**.</span></span>

     <span data-ttu-id="860f1-110">![[匯入定義域值] 對話方塊](../../2014/tutorials/media/et-importingdomainvaluesfromanexcelfile-02.jpg "[匯入定義域值] 對話方塊")</span><span class="sxs-lookup"><span data-stu-id="860f1-110">![Import Domain Values Dialog Box](../../2014/tutorials/media/et-importingdomainvaluesfromanexcelfile-02.jpg "Import Domain Values Dialog Box")</span></span>

6.  <span data-ttu-id="860f1-111">按一下 **[確定**] 以關閉 [匯**入定義域值**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="860f1-111">Click **OK** to close the **Import Domain Values** dialog box.</span></span> <span data-ttu-id="860f1-112">您應該會看到您已匯入到清單中的所有州別名稱。</span><span class="sxs-lookup"><span data-stu-id="860f1-112">You should see all the names of states you imported in the list.</span></span> <span data-ttu-id="860f1-113">請注意，匯入之後會自動選取 [**只顯示新**選項]。</span><span class="sxs-lookup"><span data-stu-id="860f1-113">Notice that **Show Only New** option is automatically selected after importing.</span></span> <span data-ttu-id="860f1-114">當您匯入值，但沒有看到清單中的舊值時，這是因為在匯入之後會自動啟用此選項。</span><span class="sxs-lookup"><span data-stu-id="860f1-114">When you import values and you don't see the old values in the list, it is because this option is automatically enabled after importing.</span></span> <span data-ttu-id="860f1-115">若要查看所有值，請清除核取方塊。</span><span class="sxs-lookup"><span data-stu-id="860f1-115">To see all the values, clear the check box.</span></span> <span data-ttu-id="860f1-116">如果您重新匯入相同的一組值，任何值都不會匯入，因為它們已經存在於定義域中。</span><span class="sxs-lookup"><span data-stu-id="860f1-116">If you import the same set of values again, none of the values are imported as they already exist in the domain.</span></span>

     <span data-ttu-id="860f1-117">![只顯示定義域值上的新核取方塊](../../2014/tutorials/media/et-importingdomainvaluesfromanexcelfile-03.jpg "只顯示定義域值上的新核取方塊")</span><span class="sxs-lookup"><span data-stu-id="860f1-117">![Show Only New Checkbox on Domain Values](../../2014/tutorials/media/et-importingdomainvaluesfromanexcelfile-03.jpg "Show Only New Checkbox on Domain Values")</span></span>

## <a name="next-step"></a><span data-ttu-id="860f1-118">後續步驟</span><span class="sxs-lookup"><span data-stu-id="860f1-118">Next Step</span></span>
 [<span data-ttu-id="860f1-119">工作 4：設定定義域規則</span><span class="sxs-lookup"><span data-stu-id="860f1-119">Task 4: Setting Domain Rules</span></span>](../../2014/tutorials/task-4-setting-domain-rules.md)


