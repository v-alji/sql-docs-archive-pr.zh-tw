---
title: 教學課程：離線建立快速圖表報表 (報表產生器) | Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- reports, creating
- tutorials, getting started
- creating reports
ms.assetid: 6b1db67a-cf75-494c-b70c-09f1e6a8d414
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 51a9e648550a0108f47e3d93d75267ab0c1c24f7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593823"
---
# <a name="tutorial-create-a-quick-chart-report-offline-report-builder"></a><span data-ttu-id="4ad39-102">教學課程：離線建立快速圖表報表 (報表產生器)</span><span class="sxs-lookup"><span data-stu-id="4ad39-102">Tutorial: Create a Quick Chart Report Offline (Report Builder)</span></span>
  <span data-ttu-id="4ad39-103">在此教學課程中，您將使用精靈來建立圓形圖，然後稍微進行修改，以便了解可行的作業。</span><span class="sxs-lookup"><span data-stu-id="4ad39-103">In this tutorial, you'll create a pie chart by using a wizard, and then you'll modify it a little, just to get an idea of what's possible.</span></span> <span data-ttu-id="4ad39-104">您可以採用兩種不同的方式進行此教學課程。</span><span class="sxs-lookup"><span data-stu-id="4ad39-104">You can do this tutorial two different ways.</span></span> <span data-ttu-id="4ad39-105">這兩種方法的結果都相同，如下圖所示的圓形圖：</span><span class="sxs-lookup"><span data-stu-id="4ad39-105">Both methods have the same outcome-a pie chart like the one in the following illustration:</span></span>

 <span data-ttu-id="4ad39-106">![[執行] 檢視中的「我的第一個圓形圖」](../media/rs-my1stpierunview.gif "[執行視圖] 中的第一個圓形圖")</span><span class="sxs-lookup"><span data-stu-id="4ad39-106">!["My First Pie Chart" in Run view](../media/rs-my1stpierunview.gif "My First Pie Chart in Run view")</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4ad39-107">先決條件</span><span class="sxs-lookup"><span data-stu-id="4ad39-107">Prerequisites</span></span>
 <span data-ttu-id="4ad39-108">不論您使用的是 XML 資料或 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 查詢，都需要具備 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 報表產生器的存取權。</span><span class="sxs-lookup"><span data-stu-id="4ad39-108">Whether you use XML data or a [!INCLUDE[tsql](../../../includes/tsql-md.md)] query, you need to have access to [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] Report Builder.</span></span> <span data-ttu-id="4ad39-109">您可以執行單機版，或者報表管理員或 SharePoint 網站提供的 ClickOnce 版本。</span><span class="sxs-lookup"><span data-stu-id="4ad39-109">You can run the stand-alone version or the ClickOnce version available from Report Manager or a SharePoint site.</span></span> <span data-ttu-id="4ad39-110">只有第一個步驟「如何開啟報表產生器」與 ClickOnce 版本不同。</span><span class="sxs-lookup"><span data-stu-id="4ad39-110">Only the first step, how to open Report Builder, is different for ClickOnce versions.</span></span> <span data-ttu-id="4ad39-111">如需詳細資訊，請參閱[安裝、卸載和報表產生器支援](../install-uninstall-and-report-builder-support.md)。</span><span class="sxs-lookup"><span data-stu-id="4ad39-111">For more information, see [Install, Uninstall, and Report Builder Support](../install-uninstall-and-report-builder-support.md).</span></span>

##  <a name="two-ways-to-do-this-tutorial"></a><a name="TwoWays"></a> <span data-ttu-id="4ad39-112">進行此教學課程的兩種方式</span><span class="sxs-lookup"><span data-stu-id="4ad39-112">Two Ways To Do This Tutorial</span></span>

-   [<span data-ttu-id="4ad39-113">使用 XML 資料建立圓形圖</span><span class="sxs-lookup"><span data-stu-id="4ad39-113">Create the pie chart with XML data</span></span>](#CreatePieChartXML)

-   [<span data-ttu-id="4ad39-114">建立含資料之 Transact-SQL 查詢的圓形圖</span><span class="sxs-lookup"><span data-stu-id="4ad39-114">Create the pie chart with a Transact-SQL query that contains data</span></span>](#CreatePieQueryData)

### <a name="using-xml-data-for-this-tutorial"></a><span data-ttu-id="4ad39-115">在此教學課程中使用 XML 資料</span><span class="sxs-lookup"><span data-stu-id="4ad39-115">Using XML data for this tutorial</span></span>
 <span data-ttu-id="4ad39-116">您可以使用從本主題複製的 XML 資料，並將它貼入精靈中。</span><span class="sxs-lookup"><span data-stu-id="4ad39-116">You can use XML data that you copy from this topic and paste into the wizard.</span></span> <span data-ttu-id="4ad39-117">您不需要連接至報表伺服器或是 SharePoint 整合模式中的報表伺服器，也不需要存取 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="4ad39-117">You don't need to be connected to a report server or a report server in SharePoint integrated mode, and you don't need access to an instance of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span>

 [<span data-ttu-id="4ad39-118">使用 XML 資料建立圓形圖</span><span class="sxs-lookup"><span data-stu-id="4ad39-118">Create the pie chart with XML data</span></span>](#CreatePieChartXML)

### <a name="using-a-transact-sql-query-that-contains-data-for-this-tutorial"></a><span data-ttu-id="4ad39-119">在此教學課程中使用包含資料的 Transact-SQL 查詢</span><span class="sxs-lookup"><span data-stu-id="4ad39-119">Using a Transact-SQL query that contains data for this tutorial</span></span>
 <span data-ttu-id="4ad39-120">您可以從本主題複製包含資料的查詢，並將它貼入精靈中。</span><span class="sxs-lookup"><span data-stu-id="4ad39-120">You can copy a query with data included in it from this topic and paste it into the wizard.</span></span> <span data-ttu-id="4ad39-121">您將需要 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 執行個體的名稱，以及能夠以唯讀方式存取任何資料庫的認證。</span><span class="sxs-lookup"><span data-stu-id="4ad39-121">You will need the name of an instance of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] and credentials sufficient for read-only access to any database.</span></span> <span data-ttu-id="4ad39-122">教學課程中的資料集查詢會使用常值資料，但是查詢必須經過 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 執行個體處理，才能傳回報表資料集所需的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="4ad39-122">The dataset query in the tutorial uses literal data, but the query must be processed by an instance of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] to return the metadata that is required for a report dataset.</span></span>

 <span data-ttu-id="4ad39-123">使用 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 查詢的優點在於，所有其他報表產生器教學課程都使用相同的方法，因此當您進行其他教學課程時，已經知道要執行哪些作業。</span><span class="sxs-lookup"><span data-stu-id="4ad39-123">The advantage of using the [!INCLUDE[tsql](../../../includes/tsql-md.md)] query is that all the other Report Builder tutorials use the same method, so when you do the other tutorials, you will already know what to do.</span></span>

 <span data-ttu-id="4ad39-124">[!INCLUDE[tsql](../../../includes/tsql-md.md)] 查詢需要其他幾項必要條件。</span><span class="sxs-lookup"><span data-stu-id="4ad39-124">The [!INCLUDE[tsql](../../../includes/tsql-md.md)] query does require a few other prerequisites.</span></span> <span data-ttu-id="4ad39-125">如需詳細資訊，請參閱[教學課程的必要條件 &#40;報表產生器&#41;](../report-builder-tutorials.md)。</span><span class="sxs-lookup"><span data-stu-id="4ad39-125">For more information, see [Prerequisites for Tutorials &#40;Report Builder&#41;](../report-builder-tutorials.md).</span></span>

 [<span data-ttu-id="4ad39-126">建立含資料之 Transact-SQL 查詢的圓形圖</span><span class="sxs-lookup"><span data-stu-id="4ad39-126">Create the pie chart with a Transact-SQL query that contains data</span></span>](#CreatePieQueryData)

## <a name="also-in-this-article"></a><span data-ttu-id="4ad39-127">本文相關內容</span><span class="sxs-lookup"><span data-stu-id="4ad39-127">Also in This Article</span></span>
 [<span data-ttu-id="4ad39-128">執行嚮導之後</span><span class="sxs-lookup"><span data-stu-id="4ad39-128">After You Run the Wizard</span></span>](#AfterWizard)

 [<span data-ttu-id="4ad39-129">下一步</span><span class="sxs-lookup"><span data-stu-id="4ad39-129">What's Next</span></span>](#WhatsNext)

##  <a name="creating-the-pie-chart-with-xml-data"></a><a name="CreatePieChartXML"></a><span data-ttu-id="4ad39-130">使用 XML 資料建立圓形圖</span><span class="sxs-lookup"><span data-stu-id="4ad39-130">Creating the pie chart with XML data</span></span>

#### <a name="to-create-the-pie-chart-with-xml-data"></a><span data-ttu-id="4ad39-131">建立含 XML 資料的圓形圖</span><span class="sxs-lookup"><span data-stu-id="4ad39-131">To create the pie chart with XML data</span></span>

1.  <span data-ttu-id="4ad39-132">按一下 **[開始]**、依序指向 **[程式集]** 和 **[Microsoft SQL Server 2012 報表產生器]**，然後按一下 **[報表產生器]**。</span><span class="sxs-lookup"><span data-stu-id="4ad39-132">Click **Start**, point to **Programs**, point to **Microsoft SQL Server 2012 Report Builder**, and then click **Report Builder**.</span></span>

     <span data-ttu-id="4ad39-133">[**消費者入門**] 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="4ad39-133">The **Getting Started** dialog box appears.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="4ad39-134"> 如果 **[使用者入門]** 對話方塊沒有出現，請在 **[報表產生器]** 按鈕中按一下 **[新增]**。</span><span class="sxs-lookup"><span data-stu-id="4ad39-134">If the **Getting Started** dialog box does not appear, from the **Report Builder** button, click **New**.</span></span>

2.  <span data-ttu-id="4ad39-135">在左窗格中，確認已選取 **[報表]** 。</span><span class="sxs-lookup"><span data-stu-id="4ad39-135">In the left pane, verify that **Report** is selected.</span></span>

3.  <span data-ttu-id="4ad39-136">在右窗格中按一下 [圖表精靈]  ，然後按一下 [建立]  。</span><span class="sxs-lookup"><span data-stu-id="4ad39-136">In the right pane, click **Chart Wizard**, and then click **Create**.</span></span>

4.  <span data-ttu-id="4ad39-137">在 [選擇資料集]  頁面中按一下 [建立資料集]  ，然後按一下 [下一步]  。</span><span class="sxs-lookup"><span data-stu-id="4ad39-137">In the **Choose a dataset** page, click **Create a dataset**, and then click **Next**.</span></span>

5.  <span data-ttu-id="4ad39-138">在 [選擇與資料來源的連線]  頁面中，按一下 [新增]  。</span><span class="sxs-lookup"><span data-stu-id="4ad39-138">In the **Choose a connection to a data source** page, click **New**.</span></span>

     <span data-ttu-id="4ad39-139">**[資料來源屬性]** 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="4ad39-139">The **Data Source Properties** dialog box opens.</span></span>

6.  <span data-ttu-id="4ad39-140">您可以將資料來源命名為任何想要的名稱。</span><span class="sxs-lookup"><span data-stu-id="4ad39-140">You can name a data source anything you want.</span></span> <span data-ttu-id="4ad39-141">在 [名稱]  方塊中，鍵入 **MyPieChart**。</span><span class="sxs-lookup"><span data-stu-id="4ad39-141">In the **Name** box, type **MyPieChart**.</span></span>

7.  <span data-ttu-id="4ad39-142">在 [**選取連線類型**] 方塊中，按一下 [ **XML]。**</span><span class="sxs-lookup"><span data-stu-id="4ad39-142">In the **Select connection type** box, click **XML.**</span></span>

8.  <span data-ttu-id="4ad39-143">按一下 [**認證**] 索引標籤，選取 [**使用目前的 Windows 使用者]。可能需要 Kerberos 委派**，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="4ad39-143">Click the **Credentials** tab, select **Use current Windows user. Kerberos delegation may be required**, and then click **OK**.</span></span>

9. <span data-ttu-id="4ad39-144">在 [選擇與資料來源的連線]  頁面中，按一下 [MyPieChart]  ，然後按一下 [下一步]  。</span><span class="sxs-lookup"><span data-stu-id="4ad39-144">In the **Choose a connection to a data source** page, click **MyPieChart**, and then click **Next**.</span></span>

10. <span data-ttu-id="4ad39-145">複製下列文字，並將它貼入 [**設計查詢**] 頁面中央的大型方塊中。</span><span class="sxs-lookup"><span data-stu-id="4ad39-145">Copy the following text and paste it in the large box in the center of the **Design a query** page.</span></span>

    ```
    <Query>
    <ElementPath>Root /S  {@Sales (Integer)} /C {@FullName} </ElementPath>
    <XmlData>
    <Root>
    <S Sales="150">
      <C FullName="Jae Pak" />
    </S>
    <S Sales="350">
      <C FullName="Jillian  Carson" />
    </S>
    <S Sales="250">
      <C FullName="Linda C Mitchell" />
    </S>
    <S Sales="500">
      <C FullName="Michael Blythe" />
    </S>
    <S Sales="450">
      <C FullName="Ranjit Varkey" />
    </S>
    </Root>
    </XmlData>
    </Query>
    ```

11. <span data-ttu-id="4ad39-146">(選擇性) 按一下 [執行] 按鈕 (**!**) 來查看您報表所依據的資料。</span><span class="sxs-lookup"><span data-stu-id="4ad39-146">(Optional) Click the Run button (**!**) to see the data your chart will be based on.</span></span>

12. <span data-ttu-id="4ad39-147">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="4ad39-147">Click **Next**.</span></span>

13. <span data-ttu-id="4ad39-148">在 [選擇圖表類型]\*\*\*\* 頁面中，按一下 [圓形圖]\*\*\*\*，然後按一下 [下一步]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4ad39-148">In the **Choose a chart type** page, click **Pie**, and then click **Next**.</span></span>

14. <span data-ttu-id="4ad39-149">在 [排列圖表欄位]\*\*\*\* 頁面中，按兩下 [可用的欄位]\*\*\*\* 方塊中的 **Sales** 欄位。</span><span class="sxs-lookup"><span data-stu-id="4ad39-149">In the **Arrange chart fields** page, double-click the **Sales** field in the **Available fields** box.</span></span>

     <span data-ttu-id="4ad39-150">請注意，它會自動移至 [值]\*\*\*\* 方塊，因為它是數值。</span><span class="sxs-lookup"><span data-stu-id="4ad39-150">Note that it automatically moves to the **Values** box, because it is a numerical value.</span></span>

15. <span data-ttu-id="4ad39-151">將 **FullName** 欄位從 [可用的欄位]\*\*\*\* 方塊拖曳至 [類別目錄]\*\*\*\* 方塊中 (或是按兩下該欄位，就會移至 [類別目錄]\*\*\*\* 方塊)，然後按一下 [下一步]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4ad39-151">Drag the **FullName** field from the **Available fields** box to the **Categories** box (or double-click it; it will go to the **Categories** box), and then click **Next**.</span></span>

16. <span data-ttu-id="4ad39-152">在 [**選擇樣式**] 頁面中，預設會選取 [**海洋**]。</span><span class="sxs-lookup"><span data-stu-id="4ad39-152">In the **Choose a style** page, **Ocean** is selected by default.</span></span> <span data-ttu-id="4ad39-153">按一下其他樣式來查看其外觀。</span><span class="sxs-lookup"><span data-stu-id="4ad39-153">Click the other styles to see what they look like.</span></span>

17. <span data-ttu-id="4ad39-154">按一下 [完成] 。</span><span class="sxs-lookup"><span data-stu-id="4ad39-154">Click **Finish**.</span></span>

     <span data-ttu-id="4ad39-155">您現在就會在設計介面上看見新的圓形圖報表。</span><span class="sxs-lookup"><span data-stu-id="4ad39-155">You're now looking at your new pie chart report on the design surface.</span></span> <span data-ttu-id="4ad39-156">您所看見的內容是代表性內容。</span><span class="sxs-lookup"><span data-stu-id="4ad39-156">What you see is representational.</span></span> <span data-ttu-id="4ad39-157">圖例會顯示成 Full Name 1、Full Name 2，以此類推，而非銷售人員的名稱，而且圓形圖配量的大小也不正確。</span><span class="sxs-lookup"><span data-stu-id="4ad39-157">The legend reads Full Name 1, Full Name 2, etc., rather than the salespeople's names, and the size of the slices of pie are not accurate.</span></span> <span data-ttu-id="4ad39-158">這只是要讓您了解報表即將呈現的外觀而已。</span><span class="sxs-lookup"><span data-stu-id="4ad39-158">This is just to give you an idea of what your report will look like.</span></span>

18. <span data-ttu-id="4ad39-159">若要查看實際的圓形圖，請在功能區的 [主資料夾]\*\*\*\* 索引標籤上，按一下 [執行]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4ad39-159">To see your actual pie chart, click **Run** on the **Home** tab of the Ribbon.</span></span>

 <span data-ttu-id="4ad39-160">搭配 [![回到頁首] 連結使用的箭號圖示](../../2014-toc/media/uparrow16x16.gif "與 [回到頁首] 連結搭配使用的箭頭圖示")[回到頁首](#TwoWays)</span><span class="sxs-lookup"><span data-stu-id="4ad39-160">![Arrow icon used with Back to Top link](../../2014-toc/media/uparrow16x16.gif "Arrow icon used with Back to Top link") [Back to Top](#TwoWays)</span></span>

##  <a name="creating-the-pie-chart-with-a-tsql-query"></a><a name="CreatePieQueryData"></a> <span data-ttu-id="4ad39-161">使用 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 查詢建立圓形圖</span><span class="sxs-lookup"><span data-stu-id="4ad39-161">Creating the pie chart with a [!INCLUDE[tsql](../../../includes/tsql-md.md)] query</span></span>

#### <a name="to-create-the-pie-chart-with-a-tsql-query-that-contains-data"></a><span data-ttu-id="4ad39-162">若要建立含資料之 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 查詢的圓形圖</span><span class="sxs-lookup"><span data-stu-id="4ad39-162">To create the pie chart with a [!INCLUDE[tsql](../../../includes/tsql-md.md)] query that contains data</span></span>

1.  <span data-ttu-id="4ad39-163">按一下 **[開始]**、依序指向 **[程式集]** 和 **[Microsoft SQL Server 2012 報表產生器]**，然後按一下 **[報表產生器]**。</span><span class="sxs-lookup"><span data-stu-id="4ad39-163">Click **Start**, point to **Programs**, point to **Microsoft SQL Server 2012 Report Builder**, and then click **Report Builder**.</span></span>

2.  <span data-ttu-id="4ad39-164">在 [**新增報表或資料集**] 對話方塊中，確認已在左窗格中選取 [**報表**]。</span><span class="sxs-lookup"><span data-stu-id="4ad39-164">In the **New report or dataset** dialog box, verify that **Report** is selected in the left pane.</span></span>

3.  <span data-ttu-id="4ad39-165">在右窗格中按一下 [圖表精靈]\*\*\*\*，然後按一下 [建立]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4ad39-165">In the right pane, click **Chart Wizard**, and then click **Create**.</span></span>

4.  <span data-ttu-id="4ad39-166">在 [選擇資料集]\*\*\*\* 頁面中按一下 [建立資料集]\*\*\*\*，然後按一下 [下一步]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4ad39-166">In the **Choose a dataset** page, click **Create a dataset**, and then click **Next**.</span></span>

5.  <span data-ttu-id="4ad39-167">在 [選擇與資料來源的連線]\*\*\*\* 頁面中，選取現有的資料來源，或瀏覽至報表伺服器並選取資料來源，然後按一下 [下一步]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4ad39-167">In the **Choose a connection to a data source** page, select an existing data source or browse to the report server and select a data source, and then click **Next**.</span></span> <span data-ttu-id="4ad39-168">您可能需要輸入使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="4ad39-168">You may need to enter a user name and password.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="4ad39-169">只要您有適當的權限，選擇哪一種資料來源都無關緊要。</span><span class="sxs-lookup"><span data-stu-id="4ad39-169">The data source you choose is unimportant, as long as you have adequate permissions.</span></span> <span data-ttu-id="4ad39-170">因為您不會從資料來源取得資料。</span><span class="sxs-lookup"><span data-stu-id="4ad39-170">You will not be getting data from the data source.</span></span> <span data-ttu-id="4ad39-171">如需詳細資訊，請參閱[教學課程的必要條件 &#40;報表產生器&#41;](../report-builder-tutorials.md)。</span><span class="sxs-lookup"><span data-stu-id="4ad39-171">For more information, see [Prerequisites for Tutorials &#40;Report Builder&#41;](../report-builder-tutorials.md).</span></span>

6.  <span data-ttu-id="4ad39-172">在 [**設計查詢**] 頁面上，按一下 [當做**文字編輯**]。</span><span class="sxs-lookup"><span data-stu-id="4ad39-172">On the **Design a Query** page, click **Edit as Text**.</span></span>

7.  <span data-ttu-id="4ad39-173">將下列查詢貼入查詢窗格中：</span><span class="sxs-lookup"><span data-stu-id="4ad39-173">Paste the following query into the query pane:</span></span>

    ```
    SELECT 150 AS Sales, 'Jae Pak' AS FullName 
    UNION SELECT 350 AS Sales, 'Jillian Carson' AS FullName 
    UNION SELECT 250 AS Sales, 'Linda C Mitchell' AS FullName 
    UNION SELECT 500 AS Sales, 'Michael Blythe' AS FullName 
    UNION SELECT 450 AS Sales, 'Ranjit Varkey' AS FullName 
    ```

8.  <span data-ttu-id="4ad39-174">(選擇性) 按一下 [執行] 按鈕 (**!**) 來查看您報表所依據的資料。</span><span class="sxs-lookup"><span data-stu-id="4ad39-174">(Optional) Click the Run button (**!**) to see the data your chart will be based on.</span></span>

9. <span data-ttu-id="4ad39-175">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="4ad39-175">Click **Next**.</span></span>

10. <span data-ttu-id="4ad39-176">在 [選擇圖表類型]\*\*\*\* 頁面中，按一下 [圓形圖]\*\*\*\*，然後按一下 [下一步]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4ad39-176">In the **Choose a chart type** page, click **Pie**, and then click **Next**.</span></span>

11. <span data-ttu-id="4ad39-177">在 [排列圖表欄位]\*\*\*\* 頁面中，按兩下 [可用的欄位]\*\*\*\* 方塊中的 **Sales** 欄位。</span><span class="sxs-lookup"><span data-stu-id="4ad39-177">In the **Arrange chart fields** page, double-click the **Sales** field in the **Available fields** box.</span></span>

     <span data-ttu-id="4ad39-178">請注意，它會自動移至 [值]\*\*\*\* 方塊，因為它是數值。</span><span class="sxs-lookup"><span data-stu-id="4ad39-178">Note that it automatically moves to the **Values** box, because it's a numerical value.</span></span>

12. <span data-ttu-id="4ad39-179">將 **FullName** 欄位從 [可用的欄位]\*\*\*\* 方塊拖曳至 [類別目錄]\*\*\*\* 方塊中 (或是按兩下該欄位，就會移至 [類別目錄]\*\*\*\* 方塊)，然後按一下 [下一步]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4ad39-179">Drag the **FullName** field from the **Available fields** box to the **Categories** box (or double-click it; it will go to the **Categories** box), and then click **Next**.</span></span>

13. <span data-ttu-id="4ad39-180">在 [**選擇樣式**] 頁面中，預設會選取 [海洋]。</span><span class="sxs-lookup"><span data-stu-id="4ad39-180">In the **Choose a style** page, Ocean is selected by default.</span></span> <span data-ttu-id="4ad39-181">按一下其他樣式來查看其外觀。</span><span class="sxs-lookup"><span data-stu-id="4ad39-181">Click the other styles to see what they look like.</span></span>

14. <span data-ttu-id="4ad39-182">按一下 [完成] 。</span><span class="sxs-lookup"><span data-stu-id="4ad39-182">Click **Finish**.</span></span>

     <span data-ttu-id="4ad39-183">您現在就會在設計介面上看見新的圓形圖報表。</span><span class="sxs-lookup"><span data-stu-id="4ad39-183">You're now looking at your new pie chart report on the design surface.</span></span> <span data-ttu-id="4ad39-184">您所看見的內容是代表性內容。</span><span class="sxs-lookup"><span data-stu-id="4ad39-184">What you see is representational.</span></span> <span data-ttu-id="4ad39-185">圖例會顯示成 Full Name 1、Full Name 2，以此類推，而非銷售人員的名稱，而且圓形圖配量的大小也不正確。</span><span class="sxs-lookup"><span data-stu-id="4ad39-185">The legend reads Full Name 1, Full Name 2, etc., rather than the salespeople's names, and the size of the slices of pie are not accurate.</span></span> <span data-ttu-id="4ad39-186">這只是要讓您了解報表即將呈現的外觀而已。</span><span class="sxs-lookup"><span data-stu-id="4ad39-186">This is just to give you an idea of what your report will look like.</span></span>

15. <span data-ttu-id="4ad39-187">若要查看實際的圓形圖，請在功能區的 [主資料夾]\*\*\*\* 索引標籤上，按一下 [執行]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4ad39-187">To see your actual pie chart, click **Run** on the **Home** tab of the Ribbon.</span></span>

 <span data-ttu-id="4ad39-188">搭配 [![回到頁首] 連結使用的箭號圖示](../../2014-toc/media/uparrow16x16.gif "與 [回到頁首] 連結搭配使用的箭頭圖示")[回到頁首](#TwoWays)</span><span class="sxs-lookup"><span data-stu-id="4ad39-188">![Arrow icon used with Back to Top link](../../2014-toc/media/uparrow16x16.gif "Arrow icon used with Back to Top link") [Back to Top](#TwoWays)</span></span>

##  <a name="after-you-run-the-wizard"></a><a name="AfterWizard"></a> <span data-ttu-id="4ad39-189">執行精靈之後</span><span class="sxs-lookup"><span data-stu-id="4ad39-189">After You Run the Wizard</span></span>
 <span data-ttu-id="4ad39-190">既然您已經擁有圓形圖報表，就可以開始處理它。</span><span class="sxs-lookup"><span data-stu-id="4ad39-190">Now that you have your pie chart report, you can play with it.</span></span> <span data-ttu-id="4ad39-191">在 [功能區] 的 [執行]\*\*\*\* 索引標籤上，按一下 [設計]\*\*\*\*，即可繼續修改。</span><span class="sxs-lookup"><span data-stu-id="4ad39-191">On the **Run** tab of the Ribbon, click **Design**, so you can continue modifying it.</span></span>

### <a name="make-the-chart-bigger"></a><span data-ttu-id="4ad39-192">讓圖表變大</span><span class="sxs-lookup"><span data-stu-id="4ad39-192">Make the chart bigger</span></span>
 <span data-ttu-id="4ad39-193">您可能想要讓圓形圖變大。</span><span class="sxs-lookup"><span data-stu-id="4ad39-193">You may want the pie chart to be bigger.</span></span> <span data-ttu-id="4ad39-194">按一下以選取圖表 (而非圖表中的任何元素)，然後拖曳右下角調整其大小。</span><span class="sxs-lookup"><span data-stu-id="4ad39-194">Click the chart, but not on any element in the chart, to select it and drag the lower-right corner to resize it.</span></span>

### <a name="add-a-report-title"></a><span data-ttu-id="4ad39-195">加入報表標題</span><span class="sxs-lookup"><span data-stu-id="4ad39-195">Add a report title</span></span>
 <span data-ttu-id="4ad39-196">選取圖表頂端的 [圖表標題]\*\*\*\* 這幾個字，然後輸入標題，例如**銷售圓形圖**。</span><span class="sxs-lookup"><span data-stu-id="4ad39-196">Select the words **Chart title** at the top of the chart, and then type a title, such as **Sales Pie Chart**.</span></span>

### <a name="add-percentages"></a><span data-ttu-id="4ad39-197">加入百分比</span><span class="sxs-lookup"><span data-stu-id="4ad39-197">Add percentages</span></span>

##### <a name="to-display-percentage-values-as-labels-on-a-pie-chart"></a><span data-ttu-id="4ad39-198">將百分比值顯示為圓形圖的標籤</span><span class="sxs-lookup"><span data-stu-id="4ad39-198">To display percentage values as labels on a pie chart</span></span>

1.  <span data-ttu-id="4ad39-199">以滑鼠右鍵按一下圓形圖，然後選取 [**顯示資料標籤**]。</span><span class="sxs-lookup"><span data-stu-id="4ad39-199">Right-click on the pie chart and select **Show Data Labels**.</span></span> <span data-ttu-id="4ad39-200">資料標籤會顯示在圓形圖的每個扇區內。</span><span class="sxs-lookup"><span data-stu-id="4ad39-200">The data labels should appear within each slice on the pie chart.</span></span>

2.  <span data-ttu-id="4ad39-201">以滑鼠右鍵按一下標籤，然後選取 [**數列標籤屬性**]。</span><span class="sxs-lookup"><span data-stu-id="4ad39-201">Right-click on the labels and select **Series Label Properties**.</span></span> <span data-ttu-id="4ad39-202">[數列標籤屬性]\*\*\*\* 對話方塊便會出現。</span><span class="sxs-lookup"><span data-stu-id="4ad39-202">The **Series Label Properties** dialog box appears.</span></span>

3.  <span data-ttu-id="4ad39-203">`#PERCENT{P0}`針對 [**標籤資料**] 選項輸入。</span><span class="sxs-lookup"><span data-stu-id="4ad39-203">Type `#PERCENT{P0}` for the **Label data** option.</span></span>

     <span data-ttu-id="4ad39-204">`{P0}` 提供您沒有小數位數的百分比。</span><span class="sxs-lookup"><span data-stu-id="4ad39-204">The `{P0}` gives you the percentage without decimal places.</span></span> <span data-ttu-id="4ad39-205">如果您只輸入 `#PERCENT`，數字會有兩個小數位數。</span><span class="sxs-lookup"><span data-stu-id="4ad39-205">If you type just `#PERCENT`, your numbers will have two decimal places.</span></span> <span data-ttu-id="4ad39-206">`#PERCENT` 是為您執行計算或函數的關鍵字，還有其他關鍵字可以使用。</span><span class="sxs-lookup"><span data-stu-id="4ad39-206">`#PERCENT` is a keyword that performs a calculation or function for you; there are many others.</span></span>

 <span data-ttu-id="4ad39-207">如需自訂圖表標籤和圖例的詳細資訊，請參閱 [在圓形圖上顯示百分比值 &#40;報表產生器及 SSRS&#41;](../report-design/display-percentage-values-on-a-pie-chart-report-builder-and-ssrs.md) 和[變更圖例項目的文字 &#40;報表產生器及 SSRS&#41;](../report-design/chart-legend-change-item-text-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="4ad39-207">For more information about customizing chart labels and legends, see [Display Percentage Values on a Pie Chart &#40;Report Builder and SSRS&#41;](../report-design/display-percentage-values-on-a-pie-chart-report-builder-and-ssrs.md) and [Change the Text of a Legend Item &#40;Report Builder and SSRS&#41;](../report-design/chart-legend-change-item-text-report-builder.md).</span></span>

 <span data-ttu-id="4ad39-208">搭配 [![回到頁首] 連結使用的箭號圖示](../../2014-toc/media/uparrow16x16.gif "與 [回到頁首] 連結搭配使用的箭頭圖示")[回到頁首](#TwoWays)</span><span class="sxs-lookup"><span data-stu-id="4ad39-208">![Arrow icon used with Back to Top link](../../2014-toc/media/uparrow16x16.gif "Arrow icon used with Back to Top link") [Back to Top](#TwoWays)</span></span>

##  <a name="whats-next"></a><a name="WhatsNext"></a><span data-ttu-id="4ad39-209">下一步是什麼？</span><span class="sxs-lookup"><span data-stu-id="4ad39-209">What's Next?</span></span>
 <span data-ttu-id="4ad39-210">既然您已經在報表產生器中建立第一份報表，可以準備嘗試進行其他教學課程，並且根據自己的資料開始建立報表。</span><span class="sxs-lookup"><span data-stu-id="4ad39-210">Now that you have created your first report in Report Builder, you are ready to try the other tutorials and to start creating reports from your own data.</span></span> <span data-ttu-id="4ad39-211">若要執行報表產生器，您需要使用*連接字串*來存取資料來源（例如資料庫）的許可權，這會實際將您連接至資料來源。</span><span class="sxs-lookup"><span data-stu-id="4ad39-211">To run Report Builder, you need permission to access your data sources, such as databases, with a *connection string*, which actually connects you to the data source.</span></span> <span data-ttu-id="4ad39-212">系統管理員會提供這項資訊而且可能會為您設定。</span><span class="sxs-lookup"><span data-stu-id="4ad39-212">Your system administrator will have this information and can set you up.</span></span>

 <span data-ttu-id="4ad39-213">若要進行其他教學課程，您需要 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 執行個體的名稱，以及能夠以唯讀方式存取任何資料庫的認證。</span><span class="sxs-lookup"><span data-stu-id="4ad39-213">To work through the other tutorials, you need the name of an instance of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] and credentials sufficient for read-only access to any database.</span></span> <span data-ttu-id="4ad39-214">系統管理員可能也會為您進行該設定。</span><span class="sxs-lookup"><span data-stu-id="4ad39-214">Your system administrator can also set that up for you.</span></span>

 <span data-ttu-id="4ad39-215">最後，若要將報表儲存至報表伺服器或與報表伺服器整合的 SharePoint 網站，您將需要 URL 和權限。</span><span class="sxs-lookup"><span data-stu-id="4ad39-215">Finally, to save your reports to a report server or a SharePoint site that is integrated with a report server, you need the URL and permissions.</span></span> <span data-ttu-id="4ad39-216">雖然您可以直接從電腦執行任何已建立的報表，不過從報表伺服器或 SharePoint 網站執行時，報表會提供更多功能。</span><span class="sxs-lookup"><span data-stu-id="4ad39-216">You can run any report you create directly from your computer, but reports have more functionality when run from the report server or SharePoint site.</span></span> <span data-ttu-id="4ad39-217">您需要權限才能從發行報表的報表伺服器或 SharePoint 網站執行您的報表或其他報表。</span><span class="sxs-lookup"><span data-stu-id="4ad39-217">You need permissions to run your reports or others from the report server or SharePoint site where they are published.</span></span> <span data-ttu-id="4ad39-218">請連絡系統管理員以取得存取權。</span><span class="sxs-lookup"><span data-stu-id="4ad39-218">Talk to your system administrator to obtain access.</span></span>

 <span data-ttu-id="4ad39-219">開始之前，閱讀一些概念和詞彙的相關資訊可能會有所協助。</span><span class="sxs-lookup"><span data-stu-id="4ad39-219">It may help to read about some of the concepts and terms before you get started.</span></span> <span data-ttu-id="4ad39-220">如需詳細資訊，請參閱[報表產生器和 SSRS&#41;的報表撰寫概念 &#40;](../report-design/report-authoring-concepts-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="4ad39-220">For more information, see [Report Authoring Concepts &#40;Report Builder and SSRS&#41;](../report-design/report-authoring-concepts-report-builder-and-ssrs.md).</span></span> <span data-ttu-id="4ad39-221">此外，在您建立第一份報表之前，請花點時間規劃一下。</span><span class="sxs-lookup"><span data-stu-id="4ad39-221">Also, spend some time planning, before you create your first report.</span></span> <span data-ttu-id="4ad39-222">這是值得花費的時間。</span><span class="sxs-lookup"><span data-stu-id="4ad39-222">It will be time well spent.</span></span> <span data-ttu-id="4ad39-223">如需詳細資訊，請參閱[規劃報表 &#40;報表產生器&#41;](../report-design/planning-a-report-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="4ad39-223">For more information, see [Planning a Report &#40;Report Builder&#41;](../report-design/planning-a-report-report-builder.md).</span></span>

 <span data-ttu-id="4ad39-224">搭配 [![回到頁首] 連結使用的箭號圖示](../../2014-toc/media/uparrow16x16.gif "與 [回到頁首] 連結搭配使用的箭頭圖示")[回到頁首](#TwoWays)</span><span class="sxs-lookup"><span data-stu-id="4ad39-224">![Arrow icon used with Back to Top link](../../2014-toc/media/uparrow16x16.gif "Arrow icon used with Back to Top link") [Back to Top](#TwoWays)</span></span>

## <a name="see-also"></a><span data-ttu-id="4ad39-225">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4ad39-225">See Also</span></span>
 <span data-ttu-id="4ad39-226">[SQL Server 2014 中的](report-builder-in-sql-server-2016.md)[教學課程 &#40;報表產生器&#41;](../report-builder-tutorials.md)報表產生器</span><span class="sxs-lookup"><span data-stu-id="4ad39-226">[Tutorials &#40;Report Builder&#41;](../report-builder-tutorials.md) [Report Builder in SQL Server 2014](report-builder-in-sql-server-2016.md)</span></span>


