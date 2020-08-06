---
title: 工作 2 (選擇性) ：使用主資料管理員建立 MDS 訂閱視圖 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: f3da8219-e0cb-4848-95ca-285a76ec1ba9
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 998436734ba5c3cf09cfe88f266a0908c0550abc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704430"
---
# <a name="task-2-optional-creating-a-mds-subscription-view-using-master-data-manager"></a><span data-ttu-id="ecd42-102">工作 2 (選擇性)：使用主資料管理員建立 MDS 訂閱檢視</span><span class="sxs-lookup"><span data-stu-id="ecd42-102">Task 2 (Optional): Creating a MDS Subscription View using Master Data Manager</span></span>
  <span data-ttu-id="ecd42-103">在這項工作中，您會建立訂閱視圖，將**供應商**模型中的**供應商**實體公開給其他應用程式。</span><span class="sxs-lookup"><span data-stu-id="ecd42-103">In this task, you create a subscription view to expose the **Supplier** entity in the **Suppliers** model to other applications.</span></span> <span data-ttu-id="ecd42-104">您不會在目前的教學課程版本中使用這個檢視。</span><span class="sxs-lookup"><span data-stu-id="ecd42-104">You do not consume this view in the current version of the tutorial.</span></span>  
  
1.  <span data-ttu-id="ecd42-105">按一下頂端的 [ **Master Data Manager** `http://localhost/MDS` **SQL Server 2012 Master Data Services** ]，切換至主資料管理員 () 的主頁面。</span><span class="sxs-lookup"><span data-stu-id="ecd42-105">Switch to the main page of **Master Data Manager** (`http://localhost/MDS`) by clicking **SQL Server 2012 Master Data Services** at the top.</span></span>  
  
2.  <span data-ttu-id="ecd42-106">按一下 [**整合管理**]。</span><span class="sxs-lookup"><span data-stu-id="ecd42-106">Click **Integration Management**.</span></span>  
  
3.  <span data-ttu-id="ecd42-107">按一下功能表列上的 [**建立視圖**]。</span><span class="sxs-lookup"><span data-stu-id="ecd42-107">Click **Create Views** on the menu bar.</span></span>  
  
     <span data-ttu-id="ecd42-108">![[加入新的訂閱檢視] 按鈕](../../2014/tutorials/media/et-creatingamdssubscriptionviewusingmdm-01.jpg "[加入新的訂閱檢視] 按鈕")</span><span class="sxs-lookup"><span data-stu-id="ecd42-108">![Add a New Subscription View Button](../../2014/tutorials/media/et-creatingamdssubscriptionviewusingmdm-01.jpg "Add a New Subscription View Button")</span></span>  
  
4.  <span data-ttu-id="ecd42-109">按一下工具列上的 [ \*\*+ (加) \*\* ] 圖示，以建立訂用帳戶視圖。</span><span class="sxs-lookup"><span data-stu-id="ecd42-109">Click **+ (Plus)** icon on the toolbar to create a subscription view.</span></span>  
  
5.  <span data-ttu-id="ecd42-110">在 [**建立訂**用帳戶] 視圖窗格中，輸入**供應商**的**訂閱視圖名稱**。</span><span class="sxs-lookup"><span data-stu-id="ecd42-110">In the **Create Subscription View** pane, type **Suppliers** for **Subscription view name**.</span></span>  
  
6.  <span data-ttu-id="ecd42-111">選取 [適用于**模型**的**供應商**]。</span><span class="sxs-lookup"><span data-stu-id="ecd42-111">Select **Suppliers** for **Model**.</span></span>  
  
7.  <span data-ttu-id="ecd42-112">針對 [**版本**] 選取 [ **VERSION_1** ]。</span><span class="sxs-lookup"><span data-stu-id="ecd42-112">Select **VERSION_1** for **Version**.</span></span>  
  
8.  <span data-ttu-id="ecd42-113">選取 [**實體**的**供應商**]。</span><span class="sxs-lookup"><span data-stu-id="ecd42-113">Select **Supplier** for **Entity**.</span></span>  
  
9. <span data-ttu-id="ecd42-114">選取 [分**葉成員**] 做為 [**格式**]。</span><span class="sxs-lookup"><span data-stu-id="ecd42-114">Select **Leaf members** for **Format**.</span></span>  
  
     <span data-ttu-id="ecd42-115">![[儲存訂閱檢視] 按鈕](../../2014/tutorials/media/et-creatingamdssubscriptionviewusingmdm-02.jpg "[儲存訂閱檢視] 按鈕")</span><span class="sxs-lookup"><span data-stu-id="ecd42-115">![Save Subscription View Button](../../2014/tutorials/media/et-creatingamdssubscriptionviewusingmdm-02.jpg "Save Subscription View Button")</span></span>  
  
10. <span data-ttu-id="ecd42-116">按一下工具列上的 [**儲存**] 來儲存訂閱視圖。</span><span class="sxs-lookup"><span data-stu-id="ecd42-116">Click **Save** on the toolbar to save the subscription view.</span></span> <span data-ttu-id="ecd42-117">此動作會在名為**供應商**的 SQL Server 中建立一個視圖。</span><span class="sxs-lookup"><span data-stu-id="ecd42-117">This action creates a view in SQL Server named **Suppliers**.</span></span> <span data-ttu-id="ecd42-118">您可以使用 SQL Server Management Studio (SSMS) 來驗證。</span><span class="sxs-lookup"><span data-stu-id="ecd42-118">You can verify this using SQL Server Management Studio (SSMS).</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="ecd42-119">後續步驟</span><span class="sxs-lookup"><span data-stu-id="ecd42-119">Next Step</span></span>  
 [<span data-ttu-id="ecd42-120">工作 3 &#40;選擇性&#41;：審查訂閱視圖</span><span class="sxs-lookup"><span data-stu-id="ecd42-120">Task 3 &#40;Optional&#41;: Reviewing the Subscription Views</span></span>](task-3-optional-reviewing-the-subscription-views.md)  
  
  
