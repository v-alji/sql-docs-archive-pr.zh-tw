---
title: 工作8：建立複合定義域規則 |Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: cff3b662-7876-4445-9bdd-96be35b3ca0c
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 4766a1206eb09e98bb20d3712a63762126b682b7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598689"
---
# <a name="task-8-creating-a-composite-domain-rule"></a><span data-ttu-id="ed8b2-102">工作 8：建立複合定義域規則</span><span class="sxs-lookup"><span data-stu-id="ed8b2-102">Task 8: Creating a Composite Domain Rule</span></span>
  <span data-ttu-id="ed8b2-103">在這項工作中，您會建立**位址驗證**複合定義域的規則。</span><span class="sxs-lookup"><span data-stu-id="ed8b2-103">In this task, you create a rule for the **Address Validation** composite domain.</span></span> <span data-ttu-id="ed8b2-104">您會定義跨定義域規則：如果**city**是**洛杉磯**，則**state**必須是**CA** ，其中**City**和**State**是兩個網域。</span><span class="sxs-lookup"><span data-stu-id="ed8b2-104">You define a cross-domain rule: if **City** is **Los Angeles**, **State** must be **CA** where **City** and **State** are two domains.</span></span>  
  
1.  <span data-ttu-id="ed8b2-105">在右窗格中，切換至 [ **CD 規則**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="ed8b2-105">In the right pane, switch to the **CD Rules** tab.</span></span>  
  
2.  <span data-ttu-id="ed8b2-106">按一下工具列中的 [**加入新的定義域規則**]。</span><span class="sxs-lookup"><span data-stu-id="ed8b2-106">Click **Add a new domain rule** from the toolbar.</span></span>  
  
3.  <span data-ttu-id="ed8b2-107">輸入「**城市-州**」的**名稱**規則，然後按**enter**鍵。</span><span class="sxs-lookup"><span data-stu-id="ed8b2-107">Type **City-State Rule** for **Name** and press **ENTER**.</span></span>  
  
4.  <span data-ttu-id="ed8b2-108">在 [**建立規則**] 窗格中，選取 [定義域] 清單中的 [ **City** ]，然後選取 [條件**值等於**]，並輸入**洛杉磯**作為值。</span><span class="sxs-lookup"><span data-stu-id="ed8b2-108">In the **Build a Rule** pane, select **City** in the domain list, and select condition **Value is equal to** and type **Los Angeles** for the value.</span></span>  
  
5.  <span data-ttu-id="ed8b2-109">在 [ **Then** ] 窗格中，選取 [定義域] 清單中的 [**狀態**]，然後選取 [**值等於**]，輸入**CA**作為值，然後按**tab**鍵。</span><span class="sxs-lookup"><span data-stu-id="ed8b2-109">In the **Then** pane, select **State** in the domain list, and select **Value is equal to**, type **CA** for the value, and press **TAB**.</span></span>  
  
     <span data-ttu-id="ed8b2-110">![複合定義域規則](../../2014/tutorials/media/et-creatingacompositedomainrule.jpg "複合定義域規則")</span><span class="sxs-lookup"><span data-stu-id="ed8b2-110">![Composite Domain Rule](../../2014/tutorials/media/et-creatingacompositedomainrule.jpg "Composite Domain Rule")</span></span>  
  
6.  <span data-ttu-id="ed8b2-111">按一下頁面底部的 [**關閉**] 按鈕，切換到 DQS 用戶端的主頁面。</span><span class="sxs-lookup"><span data-stu-id="ed8b2-111">Click **Close** button at the bottom of the page to switch to the main page of DQS Client.</span></span> <span data-ttu-id="ed8b2-112">您將會在下一課發行知識庫。</span><span class="sxs-lookup"><span data-stu-id="ed8b2-112">You will publish the knowledge base in the next lesson.</span></span> <span data-ttu-id="ed8b2-113">請注意，知識庫處於鎖定狀態 (鎖定圖示)。</span><span class="sxs-lookup"><span data-stu-id="ed8b2-113">Notice that the knowledge base is in locked state (lock icon).</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="ed8b2-114">後續步驟</span><span class="sxs-lookup"><span data-stu-id="ed8b2-114">Next Step</span></span>  
 [<span data-ttu-id="ed8b2-115">工作 9：設定參考資料服務</span><span class="sxs-lookup"><span data-stu-id="ed8b2-115">Task 9: Configuring a Reference Data Service</span></span>](../../2014/tutorials/task-9-configuring-a-reference-data-service.md)  
  
  
