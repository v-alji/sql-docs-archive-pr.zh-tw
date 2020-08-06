---
title: 工作8：在 Excel 中為 State 實體加入新的值 |Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: a763d76b-06a3-4d51-9614-01fc9fb1c158
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: cace99419997e48088420c331a823cdf3639a3ad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703477"
---
# <a name="task-8-adding-a-new-value-for-state-entity-in-excel"></a><span data-ttu-id="d5d6c-102">工作 8：在 Excel 中為 State 實體新增值</span><span class="sxs-lookup"><span data-stu-id="d5d6c-102">Task 8: Adding a New Value for State Entity in Excel</span></span>
  <span data-ttu-id="d5d6c-103">在這項工作中，您會在 Excel 中加入 State 實體的值，並將變更發行到 MDS 伺服器。</span><span class="sxs-lookup"><span data-stu-id="d5d6c-103">In this task, you add a value for the State entity in Excel and publish the change to the MDS server.</span></span>  
  
1.  <span data-ttu-id="d5d6c-104">按一下底部的 [新增] 索引標籤，在 Excel 中加入**工作表**。</span><span class="sxs-lookup"><span data-stu-id="d5d6c-104">Add a **work sheet** in Excel by clicking the new tab at the bottom.</span></span>  
  
     <span data-ttu-id="d5d6c-105">![Excel - [新工作表] 索引標籤](../../2014/tutorials/media/et-addinganewvalueforstateentityinexcel-01.jpg "Excel - [新工作表] 索引標籤")</span><span class="sxs-lookup"><span data-stu-id="d5d6c-105">![Excel - New Worksheet Tab](../../2014/tutorials/media/et-addinganewvalueforstateentityinexcel-01.jpg "Excel - New Worksheet Tab")</span></span>  
  
2.  <span data-ttu-id="d5d6c-106">在**Excel**中，按一下功能表上的 [**主要資料**] 索引標籤，然後按一下功能區上的 [**顯示瀏覽器**]。</span><span class="sxs-lookup"><span data-stu-id="d5d6c-106">In **Excel**, click the **Master Data** tab on the menu, and then click **Show Explorer** on the ribbon.</span></span>  
  
3.  <span data-ttu-id="d5d6c-107">在 [**主要] 資料總管**中，選取 [適用于**模型**的**供應商**]。</span><span class="sxs-lookup"><span data-stu-id="d5d6c-107">In the **Master Data Explorer**, select **Suppliers** for **Model**.</span></span> <span data-ttu-id="d5d6c-108">您應該會在實體清單中看到兩個實體：**供應商**和**狀態**。</span><span class="sxs-lookup"><span data-stu-id="d5d6c-108">You should see two entities: **Supplier** and **State** in the entity list.</span></span>  
  
4.  <span data-ttu-id="d5d6c-109">按兩下清單中的 [**狀態**]。</span><span class="sxs-lookup"><span data-stu-id="d5d6c-109">Double-click **State** in the list.</span></span> <span data-ttu-id="d5d6c-110">MDS 中**狀態**實體的所有成員都應該顯示在工作表中。</span><span class="sxs-lookup"><span data-stu-id="d5d6c-110">All the members of the **State** entity from MDS should be displayed in the worksheet.</span></span>  
  
5.  <span data-ttu-id="d5d6c-111">現在，在結尾加入包含下列值的資料列：適用于程式**代碼**的**名稱**和**NC**的**北卡羅萊納州**。</span><span class="sxs-lookup"><span data-stu-id="d5d6c-111">Now, add a row at the end with the following values: **North Carolina** for **Name** and **NC** for **Code**.</span></span> <span data-ttu-id="d5d6c-112">色彩編碼會區分任何新增/更新的記錄與其他記錄。</span><span class="sxs-lookup"><span data-stu-id="d5d6c-112">The color coding differentiates any new/updated records from the other records.</span></span>  
  
     <span data-ttu-id="d5d6c-113">![Excel-將北卡羅萊納州新增至州](../../2014/tutorials/media/et-addinganewvalueforstateentityinexcel-02.jpg "Excel-將北卡羅萊納州新增至州")</span><span class="sxs-lookup"><span data-stu-id="d5d6c-113">![Excel - Add North Carolina to States](../../2014/tutorials/media/et-addinganewvalueforstateentityinexcel-02.jpg "Excel - Add North Carolina to States")</span></span>  
  
6.  <span data-ttu-id="d5d6c-114">按一下功能區上的 [**發佈**]，將變更發佈至 MDS。</span><span class="sxs-lookup"><span data-stu-id="d5d6c-114">Click **Publish** on the ribbon to publish the change to MDS.</span></span>  
  
     <span data-ttu-id="d5d6c-115">![Excel - [主要資料] 索引標籤上的 [發佈] 按鈕](../../2014/tutorials/media/et-addinganewvalueforstateentityinexcel-03.jpg "Excel - [主要資料] 索引標籤上的 [發佈] 按鈕")</span><span class="sxs-lookup"><span data-stu-id="d5d6c-115">![Excel - Publish Button on Master Data Tab](../../2014/tutorials/media/et-addinganewvalueforstateentityinexcel-03.jpg "Excel - Publish Button on Master Data Tab")</span></span>  
  
7.  <span data-ttu-id="d5d6c-116">請注意，在 [**發行並批註**] 對話方塊中，已選取 [**針對所有變更使用相同的注釋**]。</span><span class="sxs-lookup"><span data-stu-id="d5d6c-116">On the **Publish and Annotate** dialog box, notice that the **Use same annotation for all changes** is selected.</span></span> <span data-ttu-id="d5d6c-117">您可以針對這裡的所有變更輸入單一註解。</span><span class="sxs-lookup"><span data-stu-id="d5d6c-117">You can enter a single annotation for all the changes here.</span></span>  
  
8.  <span data-ttu-id="d5d6c-118">選取 [**檢查變更並個別提供批註**] 選項，以提供每項變更的注釋 (在此情況下，只有一個) 。</span><span class="sxs-lookup"><span data-stu-id="d5d6c-118">Select **Review changes and provide annotations individually** option to provide annotation for each change (in this case, only one).</span></span>  
  
     <span data-ttu-id="d5d6c-119">![Excel - [發行並註解] 對話方塊](../../2014/tutorials/media/et-addinganewvalueforstateentityinexcel-04.jpg "Excel - [發行並註解] 對話方塊")</span><span class="sxs-lookup"><span data-stu-id="d5d6c-119">![Excel - Publish and Annotate Dialog Box](../../2014/tutorials/media/et-addinganewvalueforstateentityinexcel-04.jpg "Excel - Publish and Annotate Dialog Box")</span></span>  
  
9. <span data-ttu-id="d5d6c-120">按一下 [**發佈**]，將資料發行至 MDS。</span><span class="sxs-lookup"><span data-stu-id="d5d6c-120">Click **Publish** to publish data to MDS.</span></span>  
  
10. <span data-ttu-id="d5d6c-121">請注意，以**北卡羅萊納州**作為**狀態**的資料列的**色彩編碼**與現在的其他記錄相同。</span><span class="sxs-lookup"><span data-stu-id="d5d6c-121">Notice that **color coding** for the row with **North Carolina** as the **State** is same as other records now.</span></span>  
  
11. <span data-ttu-id="d5d6c-122">**選擇性：** 使用**主資料管理員**中的**Explorer** ，確認新的成員 (NC) 已加入至**State**實體。</span><span class="sxs-lookup"><span data-stu-id="d5d6c-122">**Optional:** Verify that the new member (NC) is added to the **State** entity by using the **Explorer** in **Master Data Manager**.</span></span>  
  
12. <span data-ttu-id="d5d6c-123">在 Excel 中，以滑鼠右鍵按一下底部的**狀態**工作表，然後按一下 [**刪除**] 以刪除工作表。</span><span class="sxs-lookup"><span data-stu-id="d5d6c-123">In Excel, right-click the **State** worksheet at the bottom, and click **Delete** to delete the worksheet.</span></span> <span data-ttu-id="d5d6c-124">刪除工作表並不會從 MDS 伺服器刪除任何資料。</span><span class="sxs-lookup"><span data-stu-id="d5d6c-124">Deleting the worksheet does not delete any data from the MDS server.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="d5d6c-125">後續步驟</span><span class="sxs-lookup"><span data-stu-id="d5d6c-125">Next Step</span></span>  
 [<span data-ttu-id="d5d6c-126">工作 9：使用主資料管理員建立衍生階層</span><span class="sxs-lookup"><span data-stu-id="d5d6c-126">Task 9: Creating a Derived Hierarchy using Master Data Manager</span></span>](../../2014/tutorials/task-9-creating-a-derived-hierarchy-using-master-data-manager.md)  
  
  
