---
title: 建立新的 InfoObject | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 3587a633-1c0b-4d63-a22a-6b2b93923c3a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 022f2d1e3fe10ae037ea379a02a18845b3a36107
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599615"
---
# <a name="create-new-infoobject"></a><span data-ttu-id="9ca6b-102">建立新的 InfoObject</span><span class="sxs-lookup"><span data-stu-id="9ca6b-102">Create New InfoObject</span></span>
  <span data-ttu-id="9ca6b-103">使用 **[建立新的 InfoObject]** 對話方塊可以在 SAP Netweaver BW 系統中建立新的 InfoObject。</span><span class="sxs-lookup"><span data-stu-id="9ca6b-103">Use the **Create New InfoObject** dialog box to create a new InfoObject in the SAP Netweaver BW system.</span></span>  
  
 <span data-ttu-id="9ca6b-104">您可以從 **[SAP BW 目的地編輯器]** 的 **[連接管理員]** 頁面開啟 **[建立 InfoObject]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="9ca6b-104">You can open the **Create InfoObject** dialog box from the **Connection Manager** page of the **SAP BW Destination Editor**.</span></span> <span data-ttu-id="9ca6b-105">若要深入了解 SAP BW 目的地，請參閱 [SAP BW Destination](sap-bw-destination.md)。</span><span class="sxs-lookup"><span data-stu-id="9ca6b-105">To learn more about the SAP BW destination, see [SAP BW Destination](sap-bw-destination.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="9ca6b-106">Microsoft Connector 1.1 for SAP BW 的文件集是假設使用者已熟悉 SAP Netweaver BW 環境。</span><span class="sxs-lookup"><span data-stu-id="9ca6b-106">The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment.</span></span> <span data-ttu-id="9ca6b-107">如需有關 SAP Netweaver BW 的詳細資訊，或有關如何設定 SAP Netweaver BW 物件與處理序的詳細資訊，請參閱 SAP 文件集。</span><span class="sxs-lookup"><span data-stu-id="9ca6b-107">For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.</span></span>  
  
 <span data-ttu-id="9ca6b-108">**若要開啟建立新的 InfoObject 對話方塊**</span><span class="sxs-lookup"><span data-stu-id="9ca6b-108">**To open the Create New InfoObject dialog box**</span></span>  
  
1.  <span data-ttu-id="9ca6b-109">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，開啟包含 SAP BW 目的地的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 套件。</span><span class="sxs-lookup"><span data-stu-id="9ca6b-109">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that contains the SAP BW destination.</span></span>  
  
2.  <span data-ttu-id="9ca6b-110">在 [資料流程]  索引標籤上，按兩下 SAP BW 目的地。</span><span class="sxs-lookup"><span data-stu-id="9ca6b-110">On the **Data Flow** tab, double-click the SAP BW destination.</span></span>  
  
3.  <span data-ttu-id="9ca6b-111">在 **[SAP BW 目的地編輯器]** 中，按一下 **[連接管理員]** 開啟編輯器的 **[連接管理員]** 頁面。</span><span class="sxs-lookup"><span data-stu-id="9ca6b-111">In the **SAP BW Destination Editor**, click **Connection Manager** to open the **Connection Manager** page of the editor.</span></span>  
  
4.  <span data-ttu-id="9ca6b-112">在 **[連接管理員]** 頁面的 **[建立 SAP BW 物件]** 群組方塊中，執行下列其中一個步驟以建立 InfoObject：</span><span class="sxs-lookup"><span data-stu-id="9ca6b-112">On the **Connection Manager** page, in the **Create SAP BW Objects** group box, do one of the following steps to create an InfoObject:</span></span>  
  
    1.  <span data-ttu-id="9ca6b-113">若要直接建立 InfoObject，請選取 **[InfoObject]** ，然後按一下 **[建立]** 開啟 **[建立新的 InfoObject]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="9ca6b-113">To create an InfoObject directly, select **InfoObject**, and then click **Create** to open the **Create New InfoObject** dialog box.</span></span>  
  
    2.  <span data-ttu-id="9ca6b-114">若要在建立 InfoCube 時建立 InfoObject，請選取 **[InfoCube]** ，然後按一下 **[建立]** 。</span><span class="sxs-lookup"><span data-stu-id="9ca6b-114">To create an InfoObject while creating an InfoCube, select **InfoCube**, and then click **Create**.</span></span> <span data-ttu-id="9ca6b-115">在 **[建立交易資料的 InfoCube]** 對話方塊中，於清單內其中一個資料列的 **[IObject]** 資料行中，選取 **[建立]** 開啟 **[建立新的 InfoObject]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="9ca6b-115">In the **Create InfoCube for Transaction Data** dialog box, in the **IObject** column for one of the rows in the list, select **Create** to open the **Create New InfoObject** dialog box.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="9ca6b-116">資料表中的每個資料列都代表封裝之資料流程中的資料行。</span><span class="sxs-lookup"><span data-stu-id="9ca6b-116">Each row in the table represents a column in the data flow of the package.</span></span>  
  
    3.  <span data-ttu-id="9ca6b-117">若要在建立交易資料的 InfoSource 時建立 InfoObject，請選取 **[InfoSource]** ，然後按一下 **[建立]** 。</span><span class="sxs-lookup"><span data-stu-id="9ca6b-117">To create an InfoObject while creating an InfoSouce for transactional data, select **InfoSource**, and then click **Create**.</span></span> <span data-ttu-id="9ca6b-118">在 **[建立 InfoSource]** 對話方塊中，選取 **[交易資料]** ，然後按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="9ca6b-118">In the **Create InfoSource** dialog box, select **Transaction Data**, and then click **OK**.</span></span> <span data-ttu-id="9ca6b-119">在 **[建立交易資料的 InfoSource]** 對話方塊中，於清單內其中一個資料列的 **[IObject]** 資料行中，選取 **[建立]** 開啟 **[建立新的 InfoObject]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="9ca6b-119">In the **Create InfoSource for Transaction Data** dialog box, in the **IObject** column for one of the rows in the list, select **Create** to open the **Create New InfoObject** dialog box.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="9ca6b-120">資料表中的每個資料列都代表封裝之資料流程中的資料行。</span><span class="sxs-lookup"><span data-stu-id="9ca6b-120">Each row in the table represents a column in the data flow of the package.</span></span>  
  
    4.  <span data-ttu-id="9ca6b-121">若要在建立主要資料的 InfoSource 時建立 InfoObject，請選取 **[InfoSource]** ，然後按一下 **[建立]** 。</span><span class="sxs-lookup"><span data-stu-id="9ca6b-121">To create an InfoObject while creating an InfoSource for master data, select **InfoSource**, and then click **Create**.</span></span> <span data-ttu-id="9ca6b-122">在 **[建立 InfoSource]** 對話方塊中，選取 **[主要資料]** ，然後按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="9ca6b-122">In the **Create InfoSource** dialog box, select **Master Data**, and then click **OK**.</span></span> <span data-ttu-id="9ca6b-123">在 **[建立主要資料的 InfoSource]** 對話方塊中，按一下 **[新增]** 開啟 **[建立新的 InfoObject]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="9ca6b-123">In the **Create InfoSource for Master Data** dialog box, click **New** to open the **Create New InfoObject** dialog box.</span></span>  
  
 <span data-ttu-id="9ca6b-124">您也可以在 **[建立新的 InfoObject]** 對話方塊的 **[屬性]** 區段中按一下 **[新增]** ，藉以開啟 **[建立新的 InfoObject]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="9ca6b-124">You can also open the **Create New InfoObject** dialog box by clicking **New** in the **Attributes** section of the **Create New InfoObject** dialog box.</span></span>  
  
## <a name="general-options"></a><span data-ttu-id="9ca6b-125">一般選項</span><span class="sxs-lookup"><span data-stu-id="9ca6b-125">General Options</span></span>  
 <span data-ttu-id="9ca6b-126">**特性**</span><span class="sxs-lookup"><span data-stu-id="9ca6b-126">**Characteristic**</span></span>  
 <span data-ttu-id="9ca6b-127">建立代表維度資料的 InfoObject。</span><span class="sxs-lookup"><span data-stu-id="9ca6b-127">Create an InfoObject that represents dimension data.</span></span>  
  
 <span data-ttu-id="9ca6b-128">**關鍵數據**</span><span class="sxs-lookup"><span data-stu-id="9ca6b-128">**Key figure**</span></span>  
 <span data-ttu-id="9ca6b-129">建立代表事實資料的 InfoObject。</span><span class="sxs-lookup"><span data-stu-id="9ca6b-129">Create an InfoObject that represents fact data.</span></span>  
  
 <span data-ttu-id="9ca6b-130">**InfoObject 名稱**</span><span class="sxs-lookup"><span data-stu-id="9ca6b-130">**InfoObject name**</span></span>  
 <span data-ttu-id="9ca6b-131">輸入 InfoObject 的名稱。</span><span class="sxs-lookup"><span data-stu-id="9ca6b-131">Enter a name for the InfoObject.</span></span>  
  
 <span data-ttu-id="9ca6b-132">**簡短描述**</span><span class="sxs-lookup"><span data-stu-id="9ca6b-132">**Short description**</span></span>  
 <span data-ttu-id="9ca6b-133">輸入 InfoObject 的簡短描述。</span><span class="sxs-lookup"><span data-stu-id="9ca6b-133">Enter a short description for the InfoObject.</span></span>  
  
 <span data-ttu-id="9ca6b-134">**詳細描述**</span><span class="sxs-lookup"><span data-stu-id="9ca6b-134">**Long description**</span></span>  
 <span data-ttu-id="9ca6b-135">輸入 InfoObject 的詳細描述。</span><span class="sxs-lookup"><span data-stu-id="9ca6b-135">Enter a long description for the InfoObject.</span></span>  
  
 <span data-ttu-id="9ca6b-136">**具有主要資料**</span><span class="sxs-lookup"><span data-stu-id="9ca6b-136">**Has master data**</span></span>  
 <span data-ttu-id="9ca6b-137">表示 InfoObject 包含屬性、文字或階層形式的主要資料。</span><span class="sxs-lookup"><span data-stu-id="9ca6b-137">Indicate that the InfoObject contains master data in the form of attributes, texts, or hierarchies.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9ca6b-138">如果 InfoObject 代表維度資料，而且您已選取 [特性]  選項，請選取此選項。</span><span class="sxs-lookup"><span data-stu-id="9ca6b-138">Select this option if the InfoObject represents dimensional data and you have selected the **Characteristic** option.</span></span>  
  
 <span data-ttu-id="9ca6b-139">**允許小寫字元**</span><span class="sxs-lookup"><span data-stu-id="9ca6b-139">**Allow lower-case characters**</span></span>  
 <span data-ttu-id="9ca6b-140">允許在 InfoObject 資料中使用小寫字元。</span><span class="sxs-lookup"><span data-stu-id="9ca6b-140">Allow lower-case characters in the InfoObject data.</span></span>  
  
 <span data-ttu-id="9ca6b-141">**儲存並啟用**</span><span class="sxs-lookup"><span data-stu-id="9ca6b-141">**Save & Activate**</span></span>  
 <span data-ttu-id="9ca6b-142">儲存並啟用新的 InfoObject。</span><span class="sxs-lookup"><span data-stu-id="9ca6b-142">Save and active the new InfoObject.</span></span>  
  
## <a name="data-type-options"></a><span data-ttu-id="9ca6b-143">資料類型選項</span><span class="sxs-lookup"><span data-stu-id="9ca6b-143">Data Type Options</span></span>  
 <span data-ttu-id="9ca6b-144">**CHAR - 字元字串**</span><span class="sxs-lookup"><span data-stu-id="9ca6b-144">**CHAR - Character String**</span></span>  
 <span data-ttu-id="9ca6b-145">表示 InfoObject 包含字元資料。</span><span class="sxs-lookup"><span data-stu-id="9ca6b-145">Indicates that the InfoObject contains character data.</span></span>  
  
 <span data-ttu-id="9ca6b-146">**NUMC - 數值字串**</span><span class="sxs-lookup"><span data-stu-id="9ca6b-146">**NUMC - Numeric String**</span></span>  
 <span data-ttu-id="9ca6b-147">表示 InfoObject 包含數值資料。</span><span class="sxs-lookup"><span data-stu-id="9ca6b-147">Indicates that the InfoObject contains numeric data.</span></span>  
  
 <span data-ttu-id="9ca6b-148">**DATS - 日期 (YYYYMMDD)**</span><span class="sxs-lookup"><span data-stu-id="9ca6b-148">**DATS - Date (YYYYMMDD)**</span></span>  
 <span data-ttu-id="9ca6b-149">表示 InfoObject 包含日期資料。</span><span class="sxs-lookup"><span data-stu-id="9ca6b-149">Indicates that the InfoObject contains date data.</span></span>  
  
 <span data-ttu-id="9ca6b-150">**TIMS - 時間 (HHMMSS)**</span><span class="sxs-lookup"><span data-stu-id="9ca6b-150">**TIMS - Time (HHMMSS)**</span></span>  
 <span data-ttu-id="9ca6b-151">表示 InfoObject 包含時間資料。</span><span class="sxs-lookup"><span data-stu-id="9ca6b-151">Indicates that the InfoObject contains time data.</span></span>  
  
 <span data-ttu-id="9ca6b-152">**長度**</span><span class="sxs-lookup"><span data-stu-id="9ca6b-152">**Length**</span></span>  
 <span data-ttu-id="9ca6b-153">輸入資料的長度。</span><span class="sxs-lookup"><span data-stu-id="9ca6b-153">Enter the length of the data.</span></span>  
  
## <a name="text-options"></a><span data-ttu-id="9ca6b-154">文字選項</span><span class="sxs-lookup"><span data-stu-id="9ca6b-154">Text Options</span></span>  
 <span data-ttu-id="9ca6b-155">**具有文字**</span><span class="sxs-lookup"><span data-stu-id="9ca6b-155">**With Texts**</span></span>  
 <span data-ttu-id="9ca6b-156">表示 InfoObject 包含文字。</span><span class="sxs-lookup"><span data-stu-id="9ca6b-156">Indicate that the InfoObject contains texts.</span></span>  
  
 <span data-ttu-id="9ca6b-157">**短文字**</span><span class="sxs-lookup"><span data-stu-id="9ca6b-157">**Short Text**</span></span>  
 <span data-ttu-id="9ca6b-158">表示 InfoObject 包含短文字。</span><span class="sxs-lookup"><span data-stu-id="9ca6b-158">Indicates that the InfoObject contains short texts.</span></span>  
  
 <span data-ttu-id="9ca6b-159">**中長文字**</span><span class="sxs-lookup"><span data-stu-id="9ca6b-159">**Medium Text**</span></span>  
 <span data-ttu-id="9ca6b-160">表示 InfoObject 包含中長文字。</span><span class="sxs-lookup"><span data-stu-id="9ca6b-160">Indicates that the InfoObject contains medium texts.</span></span>  
  
 <span data-ttu-id="9ca6b-161">**長文字**</span><span class="sxs-lookup"><span data-stu-id="9ca6b-161">**Long Text**</span></span>  
 <span data-ttu-id="9ca6b-162">表示 InfoObject 包含長文字。</span><span class="sxs-lookup"><span data-stu-id="9ca6b-162">Indicates that the InfoObject contains long texts.</span></span>  
  
 <span data-ttu-id="9ca6b-163">**與文字語言相依**</span><span class="sxs-lookup"><span data-stu-id="9ca6b-163">**Text Language-Dependent**</span></span>  
 <span data-ttu-id="9ca6b-164">表示文字具有語言相依性。</span><span class="sxs-lookup"><span data-stu-id="9ca6b-164">Indicates that the texts are language-dependent.</span></span>  
  
 <span data-ttu-id="9ca6b-165">**與文字時間相依**</span><span class="sxs-lookup"><span data-stu-id="9ca6b-165">**Text Time-Dependent**</span></span>  
 <span data-ttu-id="9ca6b-166">表示文字具有時間相依性。</span><span class="sxs-lookup"><span data-stu-id="9ca6b-166">Indicates that the texts are time-dependent.</span></span>  
  
## <a name="attributes-section"></a><span data-ttu-id="9ca6b-167">屬性區段</span><span class="sxs-lookup"><span data-stu-id="9ca6b-167">Attributes Section</span></span>  
 <span data-ttu-id="9ca6b-168">**[屬性]** 區段包含 InfoObject 的屬性清單，以及可讓您在清單中加入和移除屬性的選項。</span><span class="sxs-lookup"><span data-stu-id="9ca6b-168">The **Attributes** section consists of a list of attributes for the InfoObject, and the options that let you add and remove attributes from the list.</span></span>  
  
### <a name="attributes-list"></a><span data-ttu-id="9ca6b-169">屬性清單</span><span class="sxs-lookup"><span data-stu-id="9ca6b-169">Attributes List</span></span>  
 <span data-ttu-id="9ca6b-170">**[屬性]** 清單會顯示您所建立之 InfoObject 的屬性。</span><span class="sxs-lookup"><span data-stu-id="9ca6b-170">The **Attributes** list displays the attributes of the InfoObject that you are creating.</span></span> <span data-ttu-id="9ca6b-171">**[屬性]** 清單具有下列資料行標題：</span><span class="sxs-lookup"><span data-stu-id="9ca6b-171">The **Attributes** list has the following column headings:</span></span>  
  
 <span data-ttu-id="9ca6b-172">**InfoObject**</span><span class="sxs-lookup"><span data-stu-id="9ca6b-172">**InfoObject**</span></span>  
 <span data-ttu-id="9ca6b-173">檢視 InfoObject 的名稱。</span><span class="sxs-lookup"><span data-stu-id="9ca6b-173">View the name of the InfoObject.</span></span>  
  
 <span data-ttu-id="9ca6b-174">**說明**</span><span class="sxs-lookup"><span data-stu-id="9ca6b-174">**Description**</span></span>  
 <span data-ttu-id="9ca6b-175">檢視 InfoObject 的描述。</span><span class="sxs-lookup"><span data-stu-id="9ca6b-175">View the description of the InfoObject.</span></span>  
  
 <span data-ttu-id="9ca6b-176">**InfoObject 類型**</span><span class="sxs-lookup"><span data-stu-id="9ca6b-176">**InfoObject Type**</span></span>  
 <span data-ttu-id="9ca6b-177">檢視 InfoObject 的類型。</span><span class="sxs-lookup"><span data-stu-id="9ca6b-177">View the type of the InfoObject.</span></span> <span data-ttu-id="9ca6b-178">下表列出類型的可能值。</span><span class="sxs-lookup"><span data-stu-id="9ca6b-178">The following table lists the possible values for the type.</span></span>  
  
|<span data-ttu-id="9ca6b-179">值</span><span class="sxs-lookup"><span data-stu-id="9ca6b-179">Value</span></span>|<span data-ttu-id="9ca6b-180">描述</span><span class="sxs-lookup"><span data-stu-id="9ca6b-180">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="9ca6b-181">CHA</span><span class="sxs-lookup"><span data-stu-id="9ca6b-181">CHA</span></span>|<span data-ttu-id="9ca6b-182">特性</span><span class="sxs-lookup"><span data-stu-id="9ca6b-182">Characteristics</span></span>|  
|<span data-ttu-id="9ca6b-183">KYF</span><span class="sxs-lookup"><span data-stu-id="9ca6b-183">KYF</span></span>|<span data-ttu-id="9ca6b-184">關鍵數據</span><span class="sxs-lookup"><span data-stu-id="9ca6b-184">Key figures</span></span>|  
|<span data-ttu-id="9ca6b-185">UNI</span><span class="sxs-lookup"><span data-stu-id="9ca6b-185">UNI</span></span>|<span data-ttu-id="9ca6b-186">單位</span><span class="sxs-lookup"><span data-stu-id="9ca6b-186">Units</span></span>|  
|<span data-ttu-id="9ca6b-187">TIM</span><span class="sxs-lookup"><span data-stu-id="9ca6b-187">TIM</span></span>|<span data-ttu-id="9ca6b-188">時間特性</span><span class="sxs-lookup"><span data-stu-id="9ca6b-188">Time characteristics</span></span>|  
  
### <a name="attributes-options"></a><span data-ttu-id="9ca6b-189">屬性選項</span><span class="sxs-lookup"><span data-stu-id="9ca6b-189">Attributes Options</span></span>  
 <span data-ttu-id="9ca6b-190">使用下列選項可以針對您所建立的 InfoObject 加入和移除屬性：</span><span class="sxs-lookup"><span data-stu-id="9ca6b-190">Use the following options to add and remove attributes for the InfoObject that you are creating:</span></span>  
  
 <span data-ttu-id="9ca6b-191">**加入**</span><span class="sxs-lookup"><span data-stu-id="9ca6b-191">**Add**</span></span>  
 <span data-ttu-id="9ca6b-192">加入現有的 InfoObject 做為屬性。</span><span class="sxs-lookup"><span data-stu-id="9ca6b-192">Add an existing InfoObject as an attribute.</span></span>  
  
 <span data-ttu-id="9ca6b-193">若要加入現有的 InfoObject，請按一下 [加入]，然後使用 **[查閱 InfoObject]** 對話方塊來尋找 InfoObject。</span><span class="sxs-lookup"><span data-stu-id="9ca6b-193">To add an existing InfoObject, click Add, and then use the **Look Up InfoObject** dialog box to find the InfoObject.</span></span> <span data-ttu-id="9ca6b-194">如需有關此對話方塊的詳細資訊，請參閱＜ [Look Up InfoObject](look-up-infoobject.md)＞。</span><span class="sxs-lookup"><span data-stu-id="9ca6b-194">For more information about this dialog box, see [Look Up InfoObject](look-up-infoobject.md).</span></span>  
  
 <span data-ttu-id="9ca6b-195">**新增**</span><span class="sxs-lookup"><span data-stu-id="9ca6b-195">**New**</span></span>  
 <span data-ttu-id="9ca6b-196">加入新的 InfoObject 做為屬性。</span><span class="sxs-lookup"><span data-stu-id="9ca6b-196">Add a new InfoObject as an attribute.</span></span>  
  
 <span data-ttu-id="9ca6b-197">若要建立並加入新的 InfoObject，請按一下 [新增]，然後使用 **[建立新的 InfoObject]** 對話方塊的新執行個體來建立新的 InfoObject。</span><span class="sxs-lookup"><span data-stu-id="9ca6b-197">To create and add a new InfoObject, click New, and then use a new instance of the **Create New InfoObject** dialog box to create the new InfoObject.</span></span>  
  
 <span data-ttu-id="9ca6b-198">**移除**</span><span class="sxs-lookup"><span data-stu-id="9ca6b-198">**Remove**</span></span>  
 <span data-ttu-id="9ca6b-199">從 [屬性]  清單中移除選取的 InfoObject。</span><span class="sxs-lookup"><span data-stu-id="9ca6b-199">Remove the selected InfoObject from the **Attributes** list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ca6b-200">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9ca6b-200">See Also</span></span>  
 <span data-ttu-id="9ca6b-201">[建立交易資料的 InfoCube](create-infocube-for-transaction-data.md) </span><span class="sxs-lookup"><span data-stu-id="9ca6b-201">[Create InfoCube for Transaction Data](create-infocube-for-transaction-data.md) </span></span>  
 <span data-ttu-id="9ca6b-202">[建立 InfoSource](create-infosource.md) </span><span class="sxs-lookup"><span data-stu-id="9ca6b-202">[Create InfoSource](create-infosource.md) </span></span>  
 <span data-ttu-id="9ca6b-203">[建立交易資料的 InfoSource](create-infosource-for-transaction-data.md) </span><span class="sxs-lookup"><span data-stu-id="9ca6b-203">[Create InfoSource for Transaction Data](create-infosource-for-transaction-data.md) </span></span>  
 <span data-ttu-id="9ca6b-204">[建立主要資料的 InfoSource](create-infosource-for-master-data.md) </span><span class="sxs-lookup"><span data-stu-id="9ca6b-204">[Create InfoSource for Master Data](create-infosource-for-master-data.md) </span></span>  
 [<span data-ttu-id="9ca6b-205">Microsoft Connector 1.1 for SAP BW F1 說明</span><span class="sxs-lookup"><span data-stu-id="9ca6b-205">Microsoft Connector 1.1 for SAP BW F1 Help</span></span>](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  
