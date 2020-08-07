---
title: 設定工具選項和版面配置 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Database Engine [SQL Server], tutorials
ms.assetid: 43e97ce0-97bc-4a27-9485-5bbeb7190b85
author: stevestein
ms.author: sstein
ms.openlocfilehash: 96d853a85b8ee4d451c55d7ea59af3755887be22
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703618"
---
# <a name="setting-tool-options-and-layout"></a><span data-ttu-id="0ed96-102">設定工具選項和配置</span><span class="sxs-lookup"><span data-stu-id="0ed96-102">Setting Tool Options and Layout</span></span>
  <span data-ttu-id="0ed96-103">您可以設定一些選項來設定 Database Engine Tuning Advisor 圖形化使用者介面 (GUI) 在啟動時所顯示的項目、它使用的字型，以及其他工具功能，以便對您使用它的方式，提供最好的支援。</span><span class="sxs-lookup"><span data-stu-id="0ed96-103">You can set options that configure what the Database Engine Tuning Advisor graphical user interface (GUI) displays on startup, the font it uses, and other tool functionality to best support how you use it.</span></span> <span data-ttu-id="0ed96-104">這一頁的練習可讓您熟悉您可以設定的選項及如何設定它們。</span><span class="sxs-lookup"><span data-stu-id="0ed96-104">The practices on this page familiarize you with the options you can set, and how to set them.</span></span>  
  
### <a name="set-the-tool-options"></a><span data-ttu-id="0ed96-105">設定工具選項</span><span class="sxs-lookup"><span data-stu-id="0ed96-105">Set the tool options</span></span>  
  
1.  <span data-ttu-id="0ed96-106">啟動 Database Engine Tuning Advisor。</span><span class="sxs-lookup"><span data-stu-id="0ed96-106">Start the Database Engine Tuning Advisor.</span></span> <span data-ttu-id="0ed96-107">在 Windows [開始]\*\*\*\* 功能表上，依序指向 [所有程式]\*\*\*\*、[[!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)]]、[效能工具]\*\*\*\*，然後按一下 [Database Engine Tuning Advisor]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0ed96-107">On the Windows **Start** menu, point to **All Programs**, point to [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], point to **Performance Tools**, and click **Database Engine Tuning Advisor**.</span></span>  
  
2.  <span data-ttu-id="0ed96-108">在 **[工具]** 功能表上，按一下 **[選項]** 。</span><span class="sxs-lookup"><span data-stu-id="0ed96-108">On the **Tools** menu, click **Options**.</span></span>  
  
3.  <span data-ttu-id="0ed96-109">在 [選項]\*\*\*\* 對話方塊中，檢視下列選項：</span><span class="sxs-lookup"><span data-stu-id="0ed96-109">In the **Options** dialog box, view the following options:</span></span>  
  
    -   <span data-ttu-id="0ed96-110">展開 [啟動時]\*\*\*\* 清單來檢視 Database Engine Tuning Advisor 啟動時所能顯示的項目。</span><span class="sxs-lookup"><span data-stu-id="0ed96-110">Expand the **On startup** list to view what Database Engine Tuning Advisor can display when it is started.</span></span> <span data-ttu-id="0ed96-111">依預設，會選取 [顯示新的工作階段]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0ed96-111">By default, **Show a new session** is selected.</span></span>  
  
    -   <span data-ttu-id="0ed96-112">按一下 [**變更字型**]，以查看您可以在 [**一般**] 索引標籤上，為資料庫和資料表清單選擇哪些字型。您為此選項選擇的字型也會在執行微調之後，用於 Database Engine Tuning Advisor 建議方格和報表中。</span><span class="sxs-lookup"><span data-stu-id="0ed96-112">Click **Change Font** to see what fonts you can choose for the lists of databases and tables on the **General** tab. The fonts you choose for this option also are used in Database Engine Tuning Advisor recommendation grids and reports after you have performed tuning.</span></span> <span data-ttu-id="0ed96-113">依預設，Database Engine Tuning Advisor 會使用系統字型。</span><span class="sxs-lookup"><span data-stu-id="0ed96-113">By default, Database Engine Tuning Advisor uses system fonts.</span></span>  
  
    -   <span data-ttu-id="0ed96-114">[最近使用清單中的項目數目]\*\*\*\* 的設定範圍在 **1** 和 **10** 之間。</span><span class="sxs-lookup"><span data-stu-id="0ed96-114">The **Number of items in most recently used lists** can be set between **1** and **10**.</span></span> <span data-ttu-id="0ed96-115">請在 [檔案]\*\*\*\* 功能表上，按一下 [最近使用的工作階段]\*\*\*\* 或 [最近使用的檔案]\*\*\*\* 來設定所顯示清單中的最大項目數。</span><span class="sxs-lookup"><span data-stu-id="0ed96-115">This sets the maximum number of items in the lists displayed by clicking **Recent Sessions** or **Recent Files** on the **File** menu.</span></span> <span data-ttu-id="0ed96-116">依預設，這個選項會設為 **4**。</span><span class="sxs-lookup"><span data-stu-id="0ed96-116">By default, this option is set to **4**.</span></span>  
  
    -   <span data-ttu-id="0ed96-117">當核取 [記住上次的微調選項]\*\*\*\* 時，依預設，Database Engine Tuning Advisor 會利用上一個微調工作階段所指定的微調選項來處理下一個微調工作階段。</span><span class="sxs-lookup"><span data-stu-id="0ed96-117">When **Remember my last tuning options** is checked, by default Database Engine Tuning Advisor uses the tuning options you specified for your last tuning session for the next tuning session.</span></span> <span data-ttu-id="0ed96-118">請清除這個核取方塊來使用 Database Engine Tuning Advisor 微調選項預設值。</span><span class="sxs-lookup"><span data-stu-id="0ed96-118">Clear this check box to use Database Engine Tuning Advisor tuning option defaults.</span></span> <span data-ttu-id="0ed96-119">預設會選取這個選項。</span><span class="sxs-lookup"><span data-stu-id="0ed96-119">By default, this option is selected.</span></span>  
  
    -   <span data-ttu-id="0ed96-120">依預設，會核取 [永久刪除工作階段之前先詢問]\*\*\*\* 來避免意外刪除微調工作階段。</span><span class="sxs-lookup"><span data-stu-id="0ed96-120">By default, **Ask before permanently deleting sessions** is checked to avoid accidentally deleting tuning sessions.</span></span>  
  
    -   <span data-ttu-id="0ed96-121">依預設，會核取 [停止工作階段分析之前先詢問]\*\*\*\*，以避免在 Database Engine Tuning Advisor 分析工作負載完成之前不慎停止微調工作階段。</span><span class="sxs-lookup"><span data-stu-id="0ed96-121">By default, **Ask before stopping session analysis** is checked to avoid accidentally stopping a tuning session before Database Engine Tuning Advisor has finished analyzing a workload.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="0ed96-122">下一課</span><span class="sxs-lookup"><span data-stu-id="0ed96-122">Next Lesson</span></span>  
 [<span data-ttu-id="0ed96-123">第 2 課：使用 Database Engine Tuning Advisor</span><span class="sxs-lookup"><span data-stu-id="0ed96-123">Lesson 2: Using Database Engine Tuning Advisor</span></span>](../../relational-databases/performance/database-engine-tuning-advisor.md)  
  
  
