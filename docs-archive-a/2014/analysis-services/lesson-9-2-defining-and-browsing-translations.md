---
title: 定義和流覽翻譯 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 0e60be99-3768-499c-a22c-a4ec37e61887
author: minewiskan
ms.author: owend
ms.openlocfilehash: 351960375ce60825dfceccaa83856545c6b9208f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703361"
---
# <a name="defining-and-browsing-translations"></a><span data-ttu-id="63ba5-102">定義和瀏覽翻譯</span><span class="sxs-lookup"><span data-stu-id="63ba5-102">Defining and Browsing Translations</span></span>
  <span data-ttu-id="63ba5-103">翻譯是指採用特定語言之 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 物件名稱的表示。</span><span class="sxs-lookup"><span data-stu-id="63ba5-103">A translation is a representation of the names of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] objects in a specific language.</span></span> <span data-ttu-id="63ba5-104">這些物件包括量值群組、量值、維度、屬性、階層、KPI、動作和導出成員。</span><span class="sxs-lookup"><span data-stu-id="63ba5-104">Objects include measure groups, measures, dimensions, attributes, hierarchies, KPIs, actions, and calculated members.</span></span> <span data-ttu-id="63ba5-105">翻譯會針對可支援多種語言的用戶端應用程式，提供伺服器支援。</span><span class="sxs-lookup"><span data-stu-id="63ba5-105">Translations provide server support for client applications that can support multiple languages.</span></span> <span data-ttu-id="63ba5-106">透過使用這類用戶端，用戶端會將地區設定識別碼 (LCID) 傳遞給 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]的執行個體，然後當它提供 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 物件的中繼資料時，就會使用此 LCID 來決定要使用哪一組翻譯。</span><span class="sxs-lookup"><span data-stu-id="63ba5-106">By using such a client, the client passes the locale identifier (LCID) to the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], which uses the LCID to determine which set of translations to use when it provides metadata for [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] objects.</span></span> <span data-ttu-id="63ba5-107">如果 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 物件沒有包含該語言的翻譯，或者沒有包含指定之物件的翻譯，則在將物件中繼資料傳回到用戶端時會使用預設語言。</span><span class="sxs-lookup"><span data-stu-id="63ba5-107">If an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] object does not contain a translation for that language, or does not contain a translation for a specified object, the default language is used in returning the object metadata back to the client.</span></span> <span data-ttu-id="63ba5-108">例如，假設有一位法國的商務使用者從地區設定為法文的工作站中存取 Cube，若有法文翻譯的話，則該商務使用者會看到法文的成員標題及成員屬性值。</span><span class="sxs-lookup"><span data-stu-id="63ba5-108">For example, if a business user in France accesses a cube from a workstation that has a French locale setting, the business user will see the member captions and member property values in French if a French translation exists.</span></span> <span data-ttu-id="63ba5-109">不過，如果位於德國的商務使用者，從具有德文地區設定的工作站存取同一個 Cube，商務使用者就會看到德文的標題名稱以及成員屬性值。</span><span class="sxs-lookup"><span data-stu-id="63ba5-109">However, if a business user in Germany accesses the same cube from a workstation that has a German locale setting, the business user will see the captions names and member property values in German.</span></span> <span data-ttu-id="63ba5-110">如需詳細資訊，請參閱[維度翻譯](multidimensional-models-olap-logical-dimension-objects/dimension-translations.md)、 [Cube 翻譯](multidimensional-models-olap-logical-cube-objects/cube-translations.md)、[翻譯 &#40;Analysis Services&#41;](translations-analysis-services.md)。</span><span class="sxs-lookup"><span data-stu-id="63ba5-110">For more information, see [Dimension Translations](multidimensional-models-olap-logical-dimension-objects/dimension-translations.md), [Cube Translations](multidimensional-models-olap-logical-cube-objects/cube-translations.md), [Translations &#40;Analysis Services&#41;](translations-analysis-services.md).</span></span>  
  
 <span data-ttu-id="63ba5-111">在這個主題的工作中，您會在 [日期] 維度中，為一組有限的維度物件集定義中繼資料翻譯，以及在 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 教學課程 Cube 中，為 Cube 物件定義中繼資料翻譯。</span><span class="sxs-lookup"><span data-stu-id="63ba5-111">In the tasks in this topic, you define metadata translations for a limited set of dimension objects in the Date dimension and cube objects in the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube.</span></span> <span data-ttu-id="63ba5-112">您會瀏覽這些維度和 Cube 物件，來檢查中繼資料翻譯。</span><span class="sxs-lookup"><span data-stu-id="63ba5-112">You will then browse these dimension and cube objects to examine the metadata translations.</span></span>  
  
## <a name="specifying-translations-for-the-date-dimension-metadata"></a><span data-ttu-id="63ba5-113">指定日期維度中繼資料的翻譯</span><span class="sxs-lookup"><span data-stu-id="63ba5-113">Specifying Translations for the Date Dimension Metadata</span></span>  
  
1.  <span data-ttu-id="63ba5-114">開啟適用於 [日期]\*\*\*\* 維度的維度設計師，然後按一下 [翻譯]\*\*\*\* 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="63ba5-114">Open Dimension Designer for the **Date** dimension, and then click the **Translations** tab.</span></span>  
  
     <span data-ttu-id="63ba5-115">此時會出現每一個維度物件以預設語言表示的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="63ba5-115">The metadata in the default language for each dimension object appears.</span></span> <span data-ttu-id="63ba5-116">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 教學課程 Cube 的預設語言是英文。</span><span class="sxs-lookup"><span data-stu-id="63ba5-116">The default language in the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube is English.</span></span>  
  
2.  <span data-ttu-id="63ba5-117">在 [翻譯]\*\*\*\* 索引標籤的工具列上，按一下 [新增翻譯]\*\*\*\* 按鈕。</span><span class="sxs-lookup"><span data-stu-id="63ba5-117">On the toolbar of the **Translations** tab, click the **New Translation** button.</span></span>  
  
     <span data-ttu-id="63ba5-118">[選取語言]\*\*\*\* 對話方塊中會顯示一份語言清單。</span><span class="sxs-lookup"><span data-stu-id="63ba5-118">A list of languages appears in the **Select Language** dialog box.</span></span>  
  
3.  <span data-ttu-id="63ba5-119">按一下 [西班牙文 (西班牙)]\*\*\*\*，然後按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="63ba5-119">Click **Spanish (Spain)**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="63ba5-120">此時會出現新的資料行，讓您針對您要翻譯的中繼資料物件，定義西班牙文翻譯。</span><span class="sxs-lookup"><span data-stu-id="63ba5-120">A new column appears in which you will define the Spanish translations for the metadata objects you want to translate.</span></span> <span data-ttu-id="63ba5-121">在這個教學課程中，我們只會翻譯少量的物件來示範此程序。</span><span class="sxs-lookup"><span data-stu-id="63ba5-121">In this tutorial, we will only translate a few objects just to illustrate the process.</span></span>  
  
4.  <span data-ttu-id="63ba5-122">在 [翻譯]\*\*\*\* 索引標籤的工具列上，按一下 [新增翻譯]\*\*\*\* 按鈕，並在 [選取語言]\*\*\*\* 對話方塊中按一下 [法文 (法國)]\*\*\*\*，然後按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="63ba5-122">On the toolbar of the **Translations** tab, click the **New Translation** button, click **French (France)** in the **Select Language** dialog box, and then click **OK**.</span></span>  
  
     <span data-ttu-id="63ba5-123">此時會出現另一個語言資料行，讓您定義法文翻譯。</span><span class="sxs-lookup"><span data-stu-id="63ba5-123">Another language column appears in which you will define French translations.</span></span>  
  
5.  <span data-ttu-id="63ba5-124">在 [日期] 維度**標題**物件的**資料**列中，于 [西班牙文] ([法國) 翻譯] 資料行中輸入西班牙文 `Fecha` \*\* ([西班牙) \*\*翻譯] 欄位 `Temps` 。 \*\*French (France) \*\*</span><span class="sxs-lookup"><span data-stu-id="63ba5-124">In the row for the **Caption** object for the **Date** dimension, type `Fecha` in the **Spanish (Spain)** translation column and `Temps` in the **French (France)** translation column.</span></span>  
  
6.  <span data-ttu-id="63ba5-125">在 [ **Month Name** ] 屬性之**Caption**物件的資料列中，于 [西班牙文] ([法國) 翻譯] 資料行中輸入西班牙文 `Mes del Año` \*\* ([西班牙) \*\*翻譯] 資料行 `Mois d'Année` 。 \*\*French (France) \*\*</span><span class="sxs-lookup"><span data-stu-id="63ba5-125">In the row for the **Caption** object for the **Month Name** attribute, type `Mes del Año` in the **Spanish (Spain)** translation column and `Mois d'Année` in the **French (France)** translation column.</span></span>  
  
     <span data-ttu-id="63ba5-126">請注意，當您輸入這些翻譯時，會出現省略號 (**...**) 。</span><span class="sxs-lookup"><span data-stu-id="63ba5-126">Notice that when you enter these translations, an ellipsis (**...**) appears.</span></span> <span data-ttu-id="63ba5-127">按一下這個省略符號，可讓您在基礎資料表中指定一個資料行，以便提供屬性階層每個成員的翻譯。</span><span class="sxs-lookup"><span data-stu-id="63ba5-127">Clicking this ellipsis will enable you to specify a column in the underlying table that provides translations for each member of the attribute hierarchy.</span></span>  
  
7.  <span data-ttu-id="63ba5-128">針對 [**月份名稱**] 屬性，按一下西班牙文\*\* (西班牙) **轉譯的省略號 (**...\*\*) 。</span><span class="sxs-lookup"><span data-stu-id="63ba5-128">Click the ellipsis (**...**) for the **Spanish (Spain)** translation for the **Month Name** attribute.</span></span>  
  
     <span data-ttu-id="63ba5-129">此時會出現 [屬性資料翻譯]\*\*\*\* 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="63ba5-129">The **Attribute Data Translation** dialog box appears.</span></span>  
  
8.  <span data-ttu-id="63ba5-130">在 [翻譯資料行]\*\*\*\* 清單中選取 **SpanishMonthName**，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="63ba5-130">In the **Translation columns** list, select **SpanishMonthName**, as shown in the following image.</span></span>  
  
     <span data-ttu-id="63ba5-131">![屬性資料翻譯對話方塊](../../2014/tutorials/media/l9-translations-4.gif "屬性資料翻譯對話方塊")</span><span class="sxs-lookup"><span data-stu-id="63ba5-131">![Attribute Data Translation dialog box](../../2014/tutorials/media/l9-translations-4.gif "Attribute Data Translation dialog box")</span></span>  
  
9. <span data-ttu-id="63ba5-132">按一下 **[確定]**，然後按一下 [**月份名稱**] 屬性的 [**法文 (法國) **翻譯] 的省略號 (**...**) 。</span><span class="sxs-lookup"><span data-stu-id="63ba5-132">Click **OK**, and then click the ellipsis (**...**) for the **French (France)** translation for the **Month Name** attribute.</span></span>  
  
10. <span data-ttu-id="63ba5-133">在 [翻譯資料行\*\*\*\* 清單中選取 **FrenchMonthName**，然後按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="63ba5-133">In the **Translation columns** list, select **FrenchMonthName**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="63ba5-134">這個處理序的步驟，主要在示範如何定義維度物件和成員的中繼資料翻譯。</span><span class="sxs-lookup"><span data-stu-id="63ba5-134">The steps in this procedure illustrate the process of defining metadata translations for dimension objects and members.</span></span>  
  
## <a name="specifying-translations-for-the-analysis-services-tutorial-cube-metadata"></a><span data-ttu-id="63ba5-135">指定 Analysis Services 教學課程 Cube 中繼資料的翻譯</span><span class="sxs-lookup"><span data-stu-id="63ba5-135">Specifying Translations for the Analysis Services Tutorial Cube Metadata</span></span>  
  
1.  <span data-ttu-id="63ba5-136">切換到 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 教學課程 Cube 的 Cube 設計師，然後再切換到 [翻譯]\*\*\*\* 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="63ba5-136">Switch to Cube Designer for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube, and then switch to the **Translations** tab.</span></span>  
  
     <span data-ttu-id="63ba5-137">此時會出現每一個 Cube 物件以預設語言表示的中繼資料，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="63ba5-137">The metadata in the default language for each cube object appears, as shown in the following image.</span></span> <span data-ttu-id="63ba5-138">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 教學課程 Cube 的預設語言是英文。</span><span class="sxs-lookup"><span data-stu-id="63ba5-138">The default language in the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube is English.</span></span>  
  
     <span data-ttu-id="63ba5-139">![翻譯索引標籤中的預設語言](../../2014/tutorials/media/l9-translations-5.gif "翻譯索引標籤中的預設語言")</span><span class="sxs-lookup"><span data-stu-id="63ba5-139">![Default language in Translations tab](../../2014/tutorials/media/l9-translations-5.gif "Default language in Translations tab")</span></span>  
  
2.  <span data-ttu-id="63ba5-140">在 [翻譯]\*\*\*\* 索引標籤的工具列上，按一下 [新增翻譯]\*\*\*\* 按鈕。</span><span class="sxs-lookup"><span data-stu-id="63ba5-140">On the toolbar of the **Translations** tab, click the **New Translation** button.</span></span>  
  
     <span data-ttu-id="63ba5-141">[選取語言]\*\*\*\* 對話方塊中會顯示一份語言清單。</span><span class="sxs-lookup"><span data-stu-id="63ba5-141">A list of languages appears in the **Select Language** dialog box.</span></span>  
  
3.  <span data-ttu-id="63ba5-142">選取 [西班牙文 (西班牙)]\*\*\*\*，然後按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="63ba5-142">Select **Spanish (Spain)**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="63ba5-143">此時會出現新的資料行，讓您針對您要翻譯的中繼資料物件，定義西班牙文翻譯。</span><span class="sxs-lookup"><span data-stu-id="63ba5-143">A new column appears in which you will define the Spanish translations for the metadata objects you want to translate.</span></span> <span data-ttu-id="63ba5-144">在這個教學課程中，我們只會翻譯少量的物件來示範此程序。</span><span class="sxs-lookup"><span data-stu-id="63ba5-144">In this tutorial, we will only translate a few objects just to illustrate the process.</span></span>  
  
4.  <span data-ttu-id="63ba5-145">在 [翻譯]\*\*\*\* 索引標籤的工具列上，按一下 [新增翻譯]\*\*\*\* 按鈕，並選取 [選取語言]\*\*\*\* 對話方塊中的 [法文 (法國)]\*\*\*\*，然後按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="63ba5-145">On the toolbar of the **Translations** tab, click the **New Translation** button, select **French (France)** in the **Select Language** dialog box, and then click **OK**.</span></span>  
  
     <span data-ttu-id="63ba5-146">此時會出現另一個語言資料行，讓您定義法文翻譯。</span><span class="sxs-lookup"><span data-stu-id="63ba5-146">Another language column appears in which you will define French translations.</span></span>  
  
5.  <span data-ttu-id="63ba5-147">在 [日期] 維度**標題**物件的**資料**列中，于 [西班牙文] ([法國) 翻譯] 資料行中輸入西班牙文 `Fecha` \*\* ([西班牙) \*\*翻譯] 欄位 `Temps` 。 \*\*French (France) \*\*</span><span class="sxs-lookup"><span data-stu-id="63ba5-147">In the row for the **Caption** object for the **Date** dimension, type `Fecha` in the **Spanish (Spain)** translation column and `Temps` in the **French (France)** translation column.</span></span>  
  
6.  <span data-ttu-id="63ba5-148">在 [**網際網路銷售**] 量值群組之 [**標題**] 物件的資料列中，于 [西班牙文] ([法國) 翻譯] 資料行中輸入西班牙文 `Ventas del lnternet` \*\* ([西班牙) \*\*翻譯] 資料行 `Ventes D'Internet` 。 \*\*French (France) \*\*</span><span class="sxs-lookup"><span data-stu-id="63ba5-148">In the row for the **Caption** object for the **Internet Sales** measure group, type `Ventas del lnternet` in the **Spanish (Spain)** translation column and `Ventes D'Internet` in the **French (France)** translation column.</span></span>  
  
7.  <span data-ttu-id="63ba5-149">在 [網際網路銷售-銷售量] 量值的 [**標題**] 物件的資料列中，于 [西班牙文] ([法國) 翻譯] 資料行中輸入西班牙文 `Cantidad de las Ventas del Internet` \*\* ([西班牙) \*\*翻譯] 資料行 `Quantité de Ventes d'Internet` 。 \*\*French (France) \*\*</span><span class="sxs-lookup"><span data-stu-id="63ba5-149">In the row for the **Caption** object for the Internet Sales-Sales Amount measure, type `Cantidad de las Ventas del Internet` in the **Spanish (Spain)** translation column and `Quantité de Ventes d'Internet` in the **French (France)** translation column.</span></span>  
  
     <span data-ttu-id="63ba5-150">這個處理序的步驟，主要在示範如何定義 Cube 物件的中繼資料翻譯。</span><span class="sxs-lookup"><span data-stu-id="63ba5-150">The steps in this procedure illustrate the process of defining metadata translations for cube objects.</span></span>  
  
## <a name="browsing-the-cube-by-using-translations"></a><span data-ttu-id="63ba5-151">利用翻譯來瀏覽 Cube</span><span class="sxs-lookup"><span data-stu-id="63ba5-151">Browsing the Cube By Using Translations</span></span>  
  
1.  <span data-ttu-id="63ba5-152">在 [建立]\*\*\*\* 功能表上，按一下 [部署 Analysis Services 教學課程]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="63ba5-152">On the **Build** menu, click **Deploy Analysis Services Tutorial**.</span></span>  
  
2.  <span data-ttu-id="63ba5-153">順利完成部署之後，切換到 [瀏覽器]\*\*\*\* 索引標籤，然後按一下 [重新連接]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="63ba5-153">When deployment has successfully completed, switch to the **Browser** tab, and then click **Reconnect**.</span></span>  
  
3.  <span data-ttu-id="63ba5-154">從 [資料]\*\*\*\* 窗格中移除所有階層和量值，然後在 [檢視方塊]\*\*\*\* 清單中選取 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 教學課程。</span><span class="sxs-lookup"><span data-stu-id="63ba5-154">Remove all hierarchies and measures from the **Data** pane and select [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial in the **Perspectives** list.</span></span>  
  
4.  <span data-ttu-id="63ba5-155">在 [中繼資料] 窗格中，展開 [量值]\*\*\*\*，然後再展開 [網際網路銷售]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="63ba5-155">In the metadata pane, expand **Measures** and then expand **Internet Sales**.</span></span>  
  
     <span data-ttu-id="63ba5-156">請注意，[Internet Sales-Sales Amount (網際網路銷售 - 銷售量)]\*\*\*\* 量值會以英文出現在這個量值群組中。</span><span class="sxs-lookup"><span data-stu-id="63ba5-156">Notice that the **Internet Sales-Sales Amount** measure appears in English in this measure group.</span></span>  
  
5.  <span data-ttu-id="63ba5-157">在工具列上，選取 [語言]\*\*\*\* 清單中的 [西班牙文 (西班牙)]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="63ba5-157">On the toolbar, select **Spanish (Spain)** in the **Language** list.</span></span>  
  
     <span data-ttu-id="63ba5-158">請注意，[中繼資料] 窗格中的項目會重新擴展。</span><span class="sxs-lookup"><span data-stu-id="63ba5-158">Notice that the items in the metadata pane are repopulated.</span></span> <span data-ttu-id="63ba5-159">[中繼資料] 窗格中的項目重新擴展之後，請注意，[網際網路銷售 - 銷售量] 量值就不會出現在 [網際網路銷售] 顯示資料夾中了，</span><span class="sxs-lookup"><span data-stu-id="63ba5-159">After the items in the metadata pane are repopulated, notice that the Internet Sales-Sales Amount measure no longer appears in the Internet Sales display folder.</span></span> <span data-ttu-id="63ba5-160">相反地，它會在名為的新顯示資料夾中顯示為西班牙文 `Ventas del lnternet` ，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="63ba5-160">Instead, it appears in Spanish in a new display folder named `Ventas del lnternet`, as shown in the following image.</span></span>  
  
     <span data-ttu-id="63ba5-161">![重新擴展的中繼資料窗格](../../2014/tutorials/media/l9-translations-6.gif "重新擴展的中繼資料窗格")</span><span class="sxs-lookup"><span data-stu-id="63ba5-161">![Repopulated metadata pane](../../2014/tutorials/media/l9-translations-6.gif "Repopulated metadata pane")</span></span>  
  
6.  <span data-ttu-id="63ba5-162">在 [中繼資料] 窗格中，以滑鼠右鍵按一下， `Cantidad de las Ventas del Internet` 然後選取 [**加入至查詢**]。</span><span class="sxs-lookup"><span data-stu-id="63ba5-162">In the metadata pane, right-click `Cantidad de las Ventas del Internet` and then select **Add to Query**.</span></span>  
  
7.  <span data-ttu-id="63ba5-163">在 [中繼資料] 窗格中，依序展開、[Fecha] 和 [Fecha 日期]， `Fecha` 以滑鼠右鍵按一下 [ \*\* **]，然後選取 [**新增] 以進行篩選\*\*。 **Fecha.Calendar Date**</span><span class="sxs-lookup"><span data-stu-id="63ba5-163">In the metadata pane, expand `Fecha`, expand **Fecha.Calendar Date**, right-click **Fecha.Calendar Date**, and then select **Add to Filter**.</span></span>  
  
8.  <span data-ttu-id="63ba5-164">在 [篩選]\*\*\*\* 窗格中，選取 [CY 2007]\*\*\*\* 做為篩選運算式。</span><span class="sxs-lookup"><span data-stu-id="63ba5-164">In the **Filter** pane, select **CY 2007** as the filter expression.</span></span>  
  
9. <span data-ttu-id="63ba5-165">在 [中繼資料] 窗格中，以滑鼠右鍵按一下 [Mes del Ano]\*\*\*\*，然後選取[加入至查詢]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="63ba5-165">In the metadata pane, right-click **Mes del Ano** and select **Add to Query**.</span></span>  
  
     <span data-ttu-id="63ba5-166">請注意，月份是以西班牙文顯示，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="63ba5-166">Notice that the month names appear in Spanish, as shown in the following image.</span></span>  
  
     <span data-ttu-id="63ba5-167">![資料窗格中的西班牙文月份名稱](../../2014/tutorials/media/l9-translations-7.gif "資料窗格中的西班牙文月份名稱")</span><span class="sxs-lookup"><span data-stu-id="63ba5-167">![Month names in Spanish in data pane](../../2014/tutorials/media/l9-translations-7.gif "Month names in Spanish in data pane")</span></span>  
  
10. <span data-ttu-id="63ba5-168">在工具列上，選取 [語言]\*\*\*\* 清單中的 [法文 (法國)]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="63ba5-168">On the toolbar, select **French (France)** in the **Language** list.</span></span>  
  
     <span data-ttu-id="63ba5-169">請注意，現在月份會以法文顯示，與量值名稱一樣。</span><span class="sxs-lookup"><span data-stu-id="63ba5-169">Notice that the month names now appear in French and that the measure name now also appears in French.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="63ba5-170">下一課</span><span class="sxs-lookup"><span data-stu-id="63ba5-170">Next Lesson</span></span>  
 [<span data-ttu-id="63ba5-171">第10課：定義系統管理角色</span><span class="sxs-lookup"><span data-stu-id="63ba5-171">Lesson 10: Defining Administrative Roles</span></span>](lesson-10-defining-administrative-roles.md)  
  
## <a name="see-also"></a><span data-ttu-id="63ba5-172">另請參閱</span><span class="sxs-lookup"><span data-stu-id="63ba5-172">See Also</span></span>  
 <span data-ttu-id="63ba5-173">[維度翻譯](multidimensional-models-olap-logical-dimension-objects/dimension-translations.md) </span><span class="sxs-lookup"><span data-stu-id="63ba5-173">[Dimension Translations](multidimensional-models-olap-logical-dimension-objects/dimension-translations.md) </span></span>  
 <span data-ttu-id="63ba5-174">[Cube 翻譯](multidimensional-models-olap-logical-cube-objects/cube-translations.md) </span><span class="sxs-lookup"><span data-stu-id="63ba5-174">[Cube Translations](multidimensional-models-olap-logical-cube-objects/cube-translations.md) </span></span>  
 [<span data-ttu-id="63ba5-175">翻譯 &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="63ba5-175">Translations &#40;Analysis Services&#41;</span></span>](translations-analysis-services.md)  
  
  
