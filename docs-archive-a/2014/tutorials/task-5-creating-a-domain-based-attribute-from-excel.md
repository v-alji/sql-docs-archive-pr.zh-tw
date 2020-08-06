---
title: 工作5：從 Excel 建立以網域為基礎的屬性 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 07cbc624-2c6b-4568-96e4-f18663a05d80
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: b866478150fb4c06a3c4ea1ee6c227527f963219
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700492"
---
# <a name="task-5-creating-a-domain-based-attribute-from-excel"></a><span data-ttu-id="182fe-102">工作 5：從 Excel 建立定義域屬性</span><span class="sxs-lookup"><span data-stu-id="182fe-102">Task 5: Creating a Domain-Based Attribute from Excel</span></span>
  <span data-ttu-id="182fe-103">在這項工作中，您會將**供應商**實體的**State**屬性轉換為**網域屬性**。</span><span class="sxs-lookup"><span data-stu-id="182fe-103">In this task, you convert the **State** attribute of the **Supplier** entity as a **domain-based attribute**.</span></span> <span data-ttu-id="182fe-104">在您將 State 屬性設定為網域型，並將其發行至 MDS 之後，將會在 MDS 伺服器上建立名為**State**的新實體，其中包含資料行中的所有值，而**供應商**實體的**State**屬性將會填入**State**實體中的值。</span><span class="sxs-lookup"><span data-stu-id="182fe-104">After you configure the State attribute to be a domain-based one and publish it to MDS, a new entity named **State** will be created on MDS server with all the values in the column and the **State** attribute of the **Supplier** entity will be populated with values from the **State** entity.</span></span> <span data-ttu-id="182fe-105">現在，**供應商**模型應該有兩個實體 **：供應商和\*\*\*\*狀態**，其中**供應商**實體的**State**屬性是相依于**State**實體的網域屬性。</span><span class="sxs-lookup"><span data-stu-id="182fe-105">Now, the **Suppliers** model should have two entities: **Supplier** and **State** where the **State** attribute of the **Supplier** entity is a domain-based attribute that depends on **State** entity.</span></span>  
  
1.  <span data-ttu-id="182fe-106">切換至具有**清理和相符 Suppliers.xlsx**開啟的**Excel**視窗。</span><span class="sxs-lookup"><span data-stu-id="182fe-106">Switch to **Excel** window that has **Cleansed and Matched Suppliers.xlsx** open.</span></span>  
  
2.  <span data-ttu-id="182fe-107">按一下**功能**區上的 [重新整理] 按鈕，以從 MDS 取得最新的更新。</span><span class="sxs-lookup"><span data-stu-id="182fe-107">Click **Refresh** button on the ribbon to get the latest updates from MDS.</span></span> <span data-ttu-id="182fe-108">如果您已執行選用的工作**4**，您應該會看到這兩個記錄。</span><span class="sxs-lookup"><span data-stu-id="182fe-108">You should see the two more records if you have performed the optional **Task 4**.</span></span>  
  
3.  <span data-ttu-id="182fe-109">按一下標題列中的 [**資料行**名稱**狀態**] (儲存格**I1**) 。</span><span class="sxs-lookup"><span data-stu-id="182fe-109">Click column name **State** (cell **I1**) in the **header row**.</span></span>  
  
     <span data-ttu-id="182fe-110">![Excel - [屬性內容] 按鈕](../../2014/tutorials/media/et-creatingadomainbasedattributefromexcel-01.jpg "Excel - [屬性內容] 按鈕")</span><span class="sxs-lookup"><span data-stu-id="182fe-110">![Excel - Attribute Properties Button](../../2014/tutorials/media/et-creatingadomainbasedattributefromexcel-01.jpg "Excel - Attribute Properties Button")</span></span>  
  
4.  <span data-ttu-id="182fe-111">按一下功能區上的 [**屬性屬性**]。</span><span class="sxs-lookup"><span data-stu-id="182fe-111">Click **Attribute Properties** on the ribbon.</span></span>  
  
5.  <span data-ttu-id="182fe-112">在 [**屬性內容] 對話方塊**中，針對 [**屬性類型**] 選取 [\*\*受條件約束的清單] ([網域型) \*\* ]。</span><span class="sxs-lookup"><span data-stu-id="182fe-112">In the **Attribute Properties** dialog box, select **Constrained list (Domain-based)** for the **Attribute type**.</span></span>  
  
6.  <span data-ttu-id="182fe-113">輸入**新機構名稱**的**狀態**，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="182fe-113">Type **State** for the **New entity name** and click **OK**.</span></span>  
  
     <span data-ttu-id="182fe-114">![Excel - [屬性內容] 對話方塊](../../2014/tutorials/media/et-creatingadomainbasedattributefromexcel-02.jpg "Excel - [屬性內容] 對話方塊")</span><span class="sxs-lookup"><span data-stu-id="182fe-114">![Excel - Attribute Properties Dialog Box](../../2014/tutorials/media/et-creatingadomainbasedattributefromexcel-02.jpg "Excel - Attribute Properties Dialog Box")</span></span>  
  
7.  <span data-ttu-id="182fe-115">現在，在 Excel 中，當您按一下 [ **State** ] 資料行中的任何值時，您應該會看到**向下箭**號。</span><span class="sxs-lookup"><span data-stu-id="182fe-115">Now, in Excel, you should see **down arrow** when you click any value in the **State** column.</span></span> <span data-ttu-id="182fe-116">您可以視需要使用下拉式清單變更此值。</span><span class="sxs-lookup"><span data-stu-id="182fe-116">You can change the value by using the drop-down list if you need.</span></span>  
  
     <span data-ttu-id="182fe-117">![Excel - 含 [美國各州] 的下拉式清單](../../2014/tutorials/media/et-creatingadomainbasedattributefromexcel-03.jpg "Excel - 含 [美國各州] 的下拉式清單")</span><span class="sxs-lookup"><span data-stu-id="182fe-117">![Excel - Drop Down List with States](../../2014/tutorials/media/et-creatingadomainbasedattributefromexcel-03.jpg "Excel - Drop Down List with States")</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="182fe-118">後續步驟</span><span class="sxs-lookup"><span data-stu-id="182fe-118">Next Step</span></span>  
 [<span data-ttu-id="182fe-119">工作 6：確認已使用主資料管理員建立定義域屬性</span><span class="sxs-lookup"><span data-stu-id="182fe-119">Task 6: Verify that the Domain-Based Attribute is Created using Master Data Manager</span></span>](../../2014/tutorials/task-6-verify-domain-based-attribute-master-data-manager.md)  
  
  
