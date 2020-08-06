---
title: 如何檢視 CDC 執行個體屬性 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 4bce9b82-7bbd-41df-b3f4-4b40b8bad474
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 86fa298b0e02a16ddbaea220ef7f3d9f6172bf85
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701509"
---
# <a name="how-to-view-the-cdc-instance-properties"></a><span data-ttu-id="cad04-102">如何檢視 CDC 執行個體屬性</span><span class="sxs-lookup"><span data-stu-id="cad04-102">How to View the CDC Instance Properties</span></span>
  <span data-ttu-id="cad04-103">這個程序描述如何使用 CDC 設計工具主控台來檢視有關執行個體的資訊，您建立這些資訊是為了管理執行個體的操作。</span><span class="sxs-lookup"><span data-stu-id="cad04-103">This procedure describes how to use the CDC Designer Console to view information about the instances that you create to help manage the operation of the instances.</span></span>  
  
### <a name="to-view-information-about-a-specific-instance"></a><span data-ttu-id="cad04-104">若要檢視有關特定執行個體的資訊</span><span class="sxs-lookup"><span data-stu-id="cad04-104">To view information about a specific instance</span></span>  
  
1.  <span data-ttu-id="cad04-105">從 **[開始]** 功能表選取 **[CDC 設計工具主控台]** 。</span><span class="sxs-lookup"><span data-stu-id="cad04-105">From the **Start** menu, select the **CDC Designer Console**.</span></span>  
  
2.  <span data-ttu-id="cad04-106">在左窗格中展開 **[異動資料擷取]** ，然後展開包含您要檢視之執行個體的服務。</span><span class="sxs-lookup"><span data-stu-id="cad04-106">In the left pane, expand **Change Data Capture** then expand the service that contains the instance you want to view.</span></span>  
  
3.  <span data-ttu-id="cad04-107">選取您要使用的執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="cad04-107">Select the name of an instance you want to work with.</span></span>  
  
     <span data-ttu-id="cad04-108">有關執行個體的資訊會顯示在 CDC 設計工具主控台的中央。</span><span class="sxs-lookup"><span data-stu-id="cad04-108">The information about the instance is displayed in the center part of the CDC Designer Console.</span></span> <span data-ttu-id="cad04-109">它分為四個索引標籤。</span><span class="sxs-lookup"><span data-stu-id="cad04-109">It is divided into four tabs.</span></span> <span data-ttu-id="cad04-110">所有索引標籤都是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="cad04-110">All of the tabs are read only.</span></span>  
  
     <span data-ttu-id="cad04-111">**狀態**</span><span class="sxs-lookup"><span data-stu-id="cad04-111">**Status**</span></span>  
     <span data-ttu-id="cad04-112">這個索引標籤會顯示有關此執行個體之目前異動資料擷取狀態的資訊。</span><span class="sxs-lookup"><span data-stu-id="cad04-112">This tab displays the information about the current status of the change data capture for the instance.</span></span> <span data-ttu-id="cad04-113">如需有關此索引標籤顯示之內容的詳細資訊，請參閱＜ **Manage a CDC Instance** ＞中的 [[檢視器索引標籤]](manage-a-cdc-instance.md)一節。</span><span class="sxs-lookup"><span data-stu-id="cad04-113">For information about what is displayed in this tab, see the **Viewer Tabs** section in [Manage a CDC Instance](manage-a-cdc-instance.md).</span></span>  
  
     <span data-ttu-id="cad04-114">**Oracle**</span><span class="sxs-lookup"><span data-stu-id="cad04-114">**Oracle**</span></span>  
     <span data-ttu-id="cad04-115">此索引標籤會顯示有關 CDC 執行個體和 Oracle 來源資料庫的一般資訊。</span><span class="sxs-lookup"><span data-stu-id="cad04-115">This tab displays general information about the CDC instance and the Oracle source database.</span></span> <span data-ttu-id="cad04-116">如需有關此索引標籤顯示之內容的詳細資訊，請參閱＜ [Edit the Oracle Database Properties](edit-the-oracle-database-properties.md)＞。</span><span class="sxs-lookup"><span data-stu-id="cad04-116">For information about what is displayed in this tab, see [Edit the Oracle Database Properties](edit-the-oracle-database-properties.md).</span></span>  
  
     <span data-ttu-id="cad04-117">**資料表**</span><span class="sxs-lookup"><span data-stu-id="cad04-117">**Tables**</span></span>  
     <span data-ttu-id="cad04-118">這個索引標籤會顯示有關異動資料擷取中所包含之資料表的資訊。</span><span class="sxs-lookup"><span data-stu-id="cad04-118">This tab displays information about the tables included in the change data capture.</span></span> <span data-ttu-id="cad04-119">也會列出擷取的資料行。</span><span class="sxs-lookup"><span data-stu-id="cad04-119">It also lists the columns that are captured.</span></span> <span data-ttu-id="cad04-120">如需有關此索引標籤顯示之內容的詳細資訊，請參閱＜ [Edit Tables](edit-tables.md)＞。</span><span class="sxs-lookup"><span data-stu-id="cad04-120">For information about what is displayed in this tab, see [Edit Tables](edit-tables.md).</span></span>  
  
     <span data-ttu-id="cad04-121">**進階**</span><span class="sxs-lookup"><span data-stu-id="cad04-121">**Advanced**</span></span>  
     <span data-ttu-id="cad04-122">此索引標籤會顯示您在屬性編輯器中所定義的進階屬性清單。</span><span class="sxs-lookup"><span data-stu-id="cad04-122">This tab displays a list of advanced properties that you define in the properties editor.</span></span> <span data-ttu-id="cad04-123">如需有關此索引標籤顯示之內容的詳細資訊，請參閱＜ [Edit the Advanced Properties](edit-the-advanced-properties.md)＞。</span><span class="sxs-lookup"><span data-stu-id="cad04-123">For information about what is displayed in this tab, see [Edit the Advanced Properties](edit-the-advanced-properties.md).</span></span>  
  
  
