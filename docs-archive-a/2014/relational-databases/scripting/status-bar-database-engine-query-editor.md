---
title: 狀態列 (Database Engine 查詢編輯器)
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: e7f2d6f4-bb94-4cf5-a096-c34397e679af
author: rothja
ms.author: jroth
ms.openlocfilehash: 743ae0a4152daee19aa67f85337ae4077a3ed7f6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598806"
---
# <a name="status-bar-database-engine-query-editor"></a><span data-ttu-id="e0d39-102">狀態列 (Database Engine 查詢編輯器)</span><span class="sxs-lookup"><span data-stu-id="e0d39-102">Status Bar (Database Engine Query Editor)</span></span>
  <span data-ttu-id="e0d39-103">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 查詢編輯器視窗的狀態列可能利用彩色編碼，以便表示每個視窗所連接的 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="e0d39-103">The status bar of [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor windows can be color coded to indicate which instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] each window is connected to.</span></span>  
  
1.  <span data-ttu-id="e0d39-104">**開始之前：** [狀態列色彩](#StatusBarColors)</span><span class="sxs-lookup"><span data-stu-id="e0d39-104">**Before you begin:**  [Status Bar Colors](#StatusBarColors)</span></span>  
  
2.  <span data-ttu-id="e0d39-105">**在以下項目中設定伺服器狀態色彩：** [物件總管](#SetOEServerColor)、[已註冊的伺服器](#SetRegServerColor)</span><span class="sxs-lookup"><span data-stu-id="e0d39-105">**To set a server status color in:**  [Object Explorer](#SetOEServerColor), [Registered Server](#SetRegServerColor)</span></span>  
  
3.  <span data-ttu-id="e0d39-106">**使用狀態色彩：** [使用伺服器色彩開啟查詢編輯器](#OpenServerColor)、[指定狀態色彩並開啟查詢編輯器](#OpenSpecColor)</span><span class="sxs-lookup"><span data-stu-id="e0d39-106">**To use a status color:**  [Open Query Editor Using a Server Color](#OpenServerColor), [Open a Query Editor Specifying a Status Color](#OpenSpecColor)</span></span>  
  
##  <a name="status-bar-colors"></a><a name="StatusBarColors"></a> <span data-ttu-id="e0d39-107">狀態列色彩</span><span class="sxs-lookup"><span data-stu-id="e0d39-107">Status Bar Colors</span></span>  
 <span data-ttu-id="e0d39-108">您可在 **[物件總管]** 或 **[已註冊的伺服器]** 中讓狀態列色彩與特定伺服器節點產生關聯。</span><span class="sxs-lookup"><span data-stu-id="e0d39-108">You can associate a status bar color with a specific server node in either **Object Explorer** or **Registered Servers**.</span></span> <span data-ttu-id="e0d39-109">您僅能指定連接至 [!INCLUDE[ssDE](../../includes/ssde-md.md)]執行個體的伺服器節點之色彩，而不能指定其他 SQL Server 技術的伺服器節點色彩。</span><span class="sxs-lookup"><span data-stu-id="e0d39-109">The colors can only be specified for server nodes connected to an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)], not server nodes for other SQL Server technologies.</span></span> <span data-ttu-id="e0d39-110">每當您將新的 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 查詢編輯器視窗連接至 [!INCLUDE[ssDE](../../includes/ssde-md.md)]執行個體時，便可自訂狀態列色彩。</span><span class="sxs-lookup"><span data-stu-id="e0d39-110">You can also specify a custom status bar color each time you connect a new [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor window to an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span> <span data-ttu-id="e0d39-111">接著您可以使用為伺服器節點所定義的狀態色彩，開啟查詢編輯器視窗；或為該編輯器視窗指定獨特的色彩。</span><span class="sxs-lookup"><span data-stu-id="e0d39-111">You can then open a query editor window using either the status color defined for the server node, or specify a unique color for that editor window.</span></span>  
  
 <span data-ttu-id="e0d39-112">為 [物件總管] 中伺服器節點設定自訂狀態列色彩的作業，必須在進行連接時完成。</span><span class="sxs-lookup"><span data-stu-id="e0d39-112">Setting a custom status bar color for a server node in Object Explorer must be done when making the connection.</span></span> <span data-ttu-id="e0d39-113">若要變更現有伺服器節點的色彩，您必須中斷連接後重新連接，然後再指定新的色彩。</span><span class="sxs-lookup"><span data-stu-id="e0d39-113">To change the color associated with an existing server node, you must disconnect and then reconnect specifying the new color.</span></span>  
  
##  <a name="set-the-status-color-for-a-server-in-object-explorer"></a><a name="SetOEServerColor"></a> <span data-ttu-id="e0d39-114">為 [物件總管] 中的伺服器設定狀態色彩</span><span class="sxs-lookup"><span data-stu-id="e0d39-114">Set the Status Color for a Server in Object Explorer</span></span>  
 <span data-ttu-id="e0d39-115">**設定 [物件總管] 中的伺服器狀態色彩**</span><span class="sxs-lookup"><span data-stu-id="e0d39-115">**To set a server status color in Object Explorer**</span></span>  
  
1.  <span data-ttu-id="e0d39-116">在 [物件總管]  中，選取 [連接]  按鈕，然後選取 [資料庫引擎…]  。</span><span class="sxs-lookup"><span data-stu-id="e0d39-116">In **Object Explorer**, select the **Connect** button and then select **Database Engine...**.</span></span>  
  
2.  <span data-ttu-id="e0d39-117">在 [連接到伺服器]  對話方塊中選取 [選項 >>]  。</span><span class="sxs-lookup"><span data-stu-id="e0d39-117">On the **Connect to Server** dialog, select **Options >>**.</span></span>  
  
3.  <span data-ttu-id="e0d39-118">選取 **[使用自訂色彩]** 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="e0d39-118">Select the **Use custom color** check box.</span></span>  
  
4.  <span data-ttu-id="e0d39-119">選取 [選取...]  按鈕，可選取色彩。</span><span class="sxs-lookup"><span data-stu-id="e0d39-119">To select the color, select the **Select...** button.</span></span>  
  
5.  <span data-ttu-id="e0d39-120">選取基本色彩或自訂色彩，然後選取 [確定]。</span><span class="sxs-lookup"><span data-stu-id="e0d39-120">Select either a basic or custom color, then select OK.</span></span>  
  
6.  <span data-ttu-id="e0d39-121">填入其餘的連接資訊，然後選取 **[連接]** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="e0d39-121">Fill in the rest of the connection information, and then select the **Connect** button.</span></span>  
  
##  <a name="set-the-status-color-for-a-registered-server"></a><a name="SetRegServerColor"></a> <span data-ttu-id="e0d39-122">為已註冊的伺服器設定狀態色彩</span><span class="sxs-lookup"><span data-stu-id="e0d39-122">Set the Status Color For a Registered Server</span></span>  
 <span data-ttu-id="e0d39-123">**為已註冊的伺服器設定伺服器色彩**</span><span class="sxs-lookup"><span data-stu-id="e0d39-123">**To set a server color For a Registered Server**</span></span>  
  
1.  <span data-ttu-id="e0d39-124">在 [已註冊的伺服器]  中，以滑鼠右鍵按一下伺服器節點，然後選取 [屬性…]  。</span><span class="sxs-lookup"><span data-stu-id="e0d39-124">In **Registered Servers**, right click the server node and then select **Properties...**.</span></span>  
  
2.  <span data-ttu-id="e0d39-125">在 **[編輯伺服器註冊屬性]** 對話方塊上，選取 **[連接屬性]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="e0d39-125">On the **Edit Server Registration Properties** dialog, select the **Connection Properties** tab.</span></span>  
  
3.  <span data-ttu-id="e0d39-126">選取 **[使用自訂色彩]** 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="e0d39-126">Select the **Use custom color** check box.</span></span>  
  
4.  <span data-ttu-id="e0d39-127">選取 [選取...]  按鈕，可選取色彩。</span><span class="sxs-lookup"><span data-stu-id="e0d39-127">To select the color, select the **Select...** button.</span></span>  
  
5.  <span data-ttu-id="e0d39-128">選取基本色彩或自訂色彩，然後選取 [確定]。</span><span class="sxs-lookup"><span data-stu-id="e0d39-128">Select either a basic or custom color, then select OK.</span></span>  
  
6.  <span data-ttu-id="e0d39-129">選取 **[編輯伺服器註冊屬性]** 對話方塊上的 **[儲存]** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="e0d39-129">Select the **Save** button on the **Edit Server Registration Properties** dialog.</span></span>  
  
##  <a name="open-an-editor-using-a-server-color"></a><a name="OpenServerColor"></a> <span data-ttu-id="e0d39-130">使用伺服器色彩開啟編輯器</span><span class="sxs-lookup"><span data-stu-id="e0d39-130">Open An Editor Using a Server Color</span></span>  
 <span data-ttu-id="e0d39-131">**使用伺服器色彩開啟編輯器視窗**</span><span class="sxs-lookup"><span data-stu-id="e0d39-131">**To open an editor window using a server color**</span></span>  
  
-   <span data-ttu-id="e0d39-132">在 [物件總管]  或 [已註冊的伺服器]  中，以滑鼠右鍵按一下伺服器節點，然後選取 [新增查詢]  。</span><span class="sxs-lookup"><span data-stu-id="e0d39-132">Right-click a server node in either **Object Explorer** or **Registered Servers**, and select **New Query**.</span></span>  
  
-   <span data-ttu-id="e0d39-133">或者，反白顯示伺服器節點，然後選取 **[新增查詢]** 工具列按鈕。</span><span class="sxs-lookup"><span data-stu-id="e0d39-133">Alternatively, highlight a server node, and then select the **New Query** toolbar button.</span></span>  
  
-   <span data-ttu-id="e0d39-134">編輯器視窗中的狀態列將會使用為相對應之伺服器定義的色彩。</span><span class="sxs-lookup"><span data-stu-id="e0d39-134">The status bar in the editor window will use the color defined for the associated server.</span></span>  
  
##  <a name="open-an-editor-specifying-a-status-color"></a><a name="OpenSpecColor"></a> <span data-ttu-id="e0d39-135">開啟指定狀態色彩的編輯器</span><span class="sxs-lookup"><span data-stu-id="e0d39-135">Open an Editor Specifying a Status Color</span></span>  
 <span data-ttu-id="e0d39-136">**開啟指定狀態色彩的編輯器視窗**</span><span class="sxs-lookup"><span data-stu-id="e0d39-136">**To open an editor window specifying a status color**</span></span>  
  
-   <span data-ttu-id="e0d39-137">在 **[檔案]** 功能表上，選取 **[開新檔案]** ，再選取 **[Database Engine 查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="e0d39-137">Open the **File** menu, select **New**, and then select **Database Engine Query**.</span></span>  
  
-   <span data-ttu-id="e0d39-138">在 [連接到伺服器]  對話方塊中選取 [選項 >>]  。</span><span class="sxs-lookup"><span data-stu-id="e0d39-138">On the **Connect to Server** dialog, select **Options >>**.</span></span>  
  
-   <span data-ttu-id="e0d39-139">選取 **[使用自訂色彩]** 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="e0d39-139">Select the **Use custom color** check box.</span></span>  
  
-   <span data-ttu-id="e0d39-140">選取 [選取...]  按鈕，可選取色彩。</span><span class="sxs-lookup"><span data-stu-id="e0d39-140">To select the color, select the **Select...** button.</span></span>  
  
-   <span data-ttu-id="e0d39-141">選取基本色彩或自訂色彩，然後選取 [確定]。</span><span class="sxs-lookup"><span data-stu-id="e0d39-141">Select either a basic or custom color, then select OK.</span></span>  
  
-   <span data-ttu-id="e0d39-142">填入其餘的連接資訊，然後選取 **[連接]** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="e0d39-142">Fill in the rest of the connection information, and then select the **Connect** button.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0d39-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e0d39-143">See Also</span></span>  
 [<span data-ttu-id="e0d39-144">查詢與文字編輯器 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="e0d39-144">Query and Text Editors &#40;SQL Server Management Studio&#41;</span></span>](../scripting/query-and-text-editors-sql-server-management-studio.md)  
  
  
