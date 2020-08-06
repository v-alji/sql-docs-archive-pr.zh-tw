---
title: 工作 3 (選擇性) ：審查訂閱視圖 |Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 3f1d3eb7-2baa-4215-b040-0b41e3d10740
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 35cf0c246ab778b46a2ceaa2b6ff6fad02d0b670
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592391"
---
# <a name="task-3-optional-reviewing-the-subscription-views"></a><span data-ttu-id="2e25f-102">工作 3 (選擇性)：檢閱訂閱檢視</span><span class="sxs-lookup"><span data-stu-id="2e25f-102">Task 3 (Optional): Reviewing the Subscription Views</span></span>
  <span data-ttu-id="2e25f-103">在這項工作中，您會確認已使用 SQL Server Management Studio 建立 SQL 檢視表。</span><span class="sxs-lookup"><span data-stu-id="2e25f-103">In this task, you confirm that the SQL views are created by using SQL Server Management Studio.</span></span>

1.  <span data-ttu-id="2e25f-104">啟動 [SQL Server Management Studio]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2e25f-104">Launch **SQL Server Management Studio**.</span></span> <span data-ttu-id="2e25f-105">依序按一下 [**開始**] 按鈕、[**所有程式**]、[ **Microsoft SQL Server 2012**]，然後按一下 [ **SQL Server Management Studio**]。</span><span class="sxs-lookup"><span data-stu-id="2e25f-105">Click the **Start** button, click **All Programs**, click **Microsoft SQL Server 2012**, and then click **SQL Server Management Studio**.</span></span>

2.  <span data-ttu-id="2e25f-106">在 [連線**到伺服器**] 視窗中，將 [**伺服器類型**] 設定為 [**資料庫引擎**]，輸入**伺服器名稱** (或選取 [ \*\* (本機) **]，然後選取適當的**驗證\*\*，再按一下 **[連接]**。</span><span class="sxs-lookup"><span data-stu-id="2e25f-106">In the **Connect to Server** window, set **Server Type** to **Database Engine**, type the **server name** (or select **(local)**, and select appropriate **authentication**, and click **Connect**.</span></span>

3.  <span data-ttu-id="2e25f-107">在 [**物件總管**] 窗格中，展開 [**資料庫**]，展開 [ **MDS**]，然後展開 [ **Views**]。</span><span class="sxs-lookup"><span data-stu-id="2e25f-107">In the **Object Explorer** pane, expand **Databases**, expand **MDS**, and then expand **Views**.</span></span>

4.  <span data-ttu-id="2e25f-108">確認您看到**mdm。** 清單中的供應商視圖。</span><span class="sxs-lookup"><span data-stu-id="2e25f-108">Confirm that you see the **mdm.Suppliers** view in the list.</span></span>

     <span data-ttu-id="2e25f-109">![SQL Server Management Studio - mdm.Suppliers 檢視](../../2014/tutorials/media/et-reviewingthesubscriptionviews.jpg "SQL Server Management Studio - mdm.Suppliers 檢視")</span><span class="sxs-lookup"><span data-stu-id="2e25f-109">![SQL Server Management Studio - mdm.Suppliers View](../../2014/tutorials/media/et-reviewingthesubscriptionviews.jpg "SQL Server Management Studio - mdm.Suppliers View")</span></span>

## <a name="next-step"></a><span data-ttu-id="2e25f-110">後續步驟</span><span class="sxs-lookup"><span data-stu-id="2e25f-110">Next Step</span></span>
 [<span data-ttu-id="2e25f-111">工作 4：使用 SQL Server Data Tools 建立 SSIS 專案</span><span class="sxs-lookup"><span data-stu-id="2e25f-111">Task 4: Creating an SSIS Project using SQL Server Data Tools</span></span>](../../2014/tutorials/task-4-creating-an-ssis-project-using-sql-server-data-tools.md)