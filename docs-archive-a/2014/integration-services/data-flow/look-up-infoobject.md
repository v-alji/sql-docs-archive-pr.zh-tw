---
title: 查閱 InfoObject | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: e7f4c132-a5ec-49d8-a964-45775432731f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1616b4fcb368afc9e3f1157a3fc2511d4a7e8cce
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700078"
---
# <a name="look-up-infoobject"></a><span data-ttu-id="cf82d-102">查閱 InfoObject</span><span class="sxs-lookup"><span data-stu-id="cf82d-102">Look Up InfoObject</span></span>
  <span data-ttu-id="cf82d-103">使用 [查閱 InfoObject]  對話方塊可以查閱 SAP Netweaver BW 系統中定義的 InfoObject。</span><span class="sxs-lookup"><span data-stu-id="cf82d-103">Use the **Look Up InfoObject** dialog box to look up an InfoObject that is defined in the SAP Netweaver BW system.</span></span> <span data-ttu-id="cf82d-104">出現可用的 InfoObject 清單時，請選取您要的 InfoObject，然後 SAP BW 目的地就會將必要的值填入相關聯的選項。</span><span class="sxs-lookup"><span data-stu-id="cf82d-104">When the list of available InfoObjects appears, select the InfoObject that you want, and the SAP BW destination will populate the associated options with the required values.</span></span>  
  
 <span data-ttu-id="cf82d-105">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW 的 SAP BW 目的地會使用 [查閱 InfoObject]  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="cf82d-105">The SAP BW destination of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW uses the **Look Up InfoObject** dialog box.</span></span> <span data-ttu-id="cf82d-106">若要深入了解 SAP BW 目的地，請參閱 [SAP BW Destination](sap-bw-destination.md)。</span><span class="sxs-lookup"><span data-stu-id="cf82d-106">To learn more about the SAP BW destination, see [SAP BW Destination](sap-bw-destination.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="cf82d-107">Microsoft Connector 1.1 for SAP BW 的文件集是假設使用者已熟悉 SAP Netweaver BW 環境。</span><span class="sxs-lookup"><span data-stu-id="cf82d-107">The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment.</span></span> <span data-ttu-id="cf82d-108">如需有關 SAP Netweaver BW 的詳細資訊，或有關如何設定 SAP Netweaver BW 物件與處理序的詳細資訊，請參閱 SAP 文件集。</span><span class="sxs-lookup"><span data-stu-id="cf82d-108">For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.</span></span>  
  
 <span data-ttu-id="cf82d-109">**若要開啟查閱 InfoObject 對話方塊**</span><span class="sxs-lookup"><span data-stu-id="cf82d-109">**To open the Look Up InfoObject dialog box**</span></span>  
  
1.  <span data-ttu-id="cf82d-110">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，開啟包含 SAP BW 目的地的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 套件。</span><span class="sxs-lookup"><span data-stu-id="cf82d-110">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that contains the SAP BW destination.</span></span>  
  
2.  <span data-ttu-id="cf82d-111">在 [資料流程]  索引標籤上，按兩下 SAP BW 目的地。</span><span class="sxs-lookup"><span data-stu-id="cf82d-111">On the **Data Flow** tab, double-click the SAP BW destination.</span></span>  
  
3.  <span data-ttu-id="cf82d-112">在 **[SAP BW 目的地編輯器]** 中，按一下 **[連接管理員]** 開啟編輯器的 **[連接管理員]** 頁面。</span><span class="sxs-lookup"><span data-stu-id="cf82d-112">In the **SAP BW Destination Editor**, click **Connection Manager** to open the **Connection Manager** page of the editor.</span></span>  
  
4.  <span data-ttu-id="cf82d-113">在 [連線管理員]  頁面的 [建立 SAP BW 物件]  群組方塊中，選取下列其中一個選項：</span><span class="sxs-lookup"><span data-stu-id="cf82d-113">On the **Connection Manager** page, in the **Create SAP BW Objects** group box, select one of the following options:</span></span>  
  
    1.  <span data-ttu-id="cf82d-114">選取 [InfoCube]  。</span><span class="sxs-lookup"><span data-stu-id="cf82d-114">Select **InfoCube**.</span></span> <span data-ttu-id="cf82d-115">然後按一下 [ **建立**]。</span><span class="sxs-lookup"><span data-stu-id="cf82d-115">Then, click **Create**.</span></span> <span data-ttu-id="cf82d-116">在 [建立交易資料的 InfoCube] 對話方塊中，於清單內其中一個資料列的 [IObject] 資料行中，按一下 [搜尋]。</span><span class="sxs-lookup"><span data-stu-id="cf82d-116">In the **Create InfoCube for Transaction Data** dialog box, click **Search** in the **IObject** column for one of the rows in the list.</span></span> <span data-ttu-id="cf82d-117">每個資料列都代表封裝之資料流程中的資料行。</span><span class="sxs-lookup"><span data-stu-id="cf82d-117">Each row represents a column in the data flow of the package.</span></span>  
  
    2.  <span data-ttu-id="cf82d-118">選取 [InfoSource]  。</span><span class="sxs-lookup"><span data-stu-id="cf82d-118">Select **InfoSource**.</span></span> <span data-ttu-id="cf82d-119">接著，按一下 [建立]  。</span><span class="sxs-lookup"><span data-stu-id="cf82d-119">Then click **Create**.</span></span> <span data-ttu-id="cf82d-120">在 [建立 InfoSource]  對話方塊中，選取 [交易資料]  。</span><span class="sxs-lookup"><span data-stu-id="cf82d-120">In the **Create InfoSource** dialog box, select **Transaction data**.</span></span> <span data-ttu-id="cf82d-121">在 [建立交易資料的 InfoSource] 對話方塊中，於清單內其中一個資料列的 [IObject] 資料行中，按一下 [搜尋]。</span><span class="sxs-lookup"><span data-stu-id="cf82d-121">In the **Create InfoSource for Transaction Data** dialog box, click **Search** in the **IObject** column for one of the rows in the list.</span></span> <span data-ttu-id="cf82d-122">每個資料列都代表封裝之資料流程中的資料行。</span><span class="sxs-lookup"><span data-stu-id="cf82d-122">Each row represents a column in the data flow of the package.</span></span>  
  
    3.  <span data-ttu-id="cf82d-123">選取 [InfoSource]  。</span><span class="sxs-lookup"><span data-stu-id="cf82d-123">Select **InfoSource**.</span></span> <span data-ttu-id="cf82d-124">接著，按一下 [建立]  。</span><span class="sxs-lookup"><span data-stu-id="cf82d-124">Then click **Create**.</span></span> <span data-ttu-id="cf82d-125">在 [建立 InfoSource]  對話方塊中，選取 [主要資料]  。</span><span class="sxs-lookup"><span data-stu-id="cf82d-125">In the **Create InfoSource** dialog box, select **Master data**.</span></span> <span data-ttu-id="cf82d-126">在 [建立主要資料的 InfoSource]  對話方塊中，按一下 [查閱]  。</span><span class="sxs-lookup"><span data-stu-id="cf82d-126">In the **Create InfoSource for Master Data** dialog box, click **Look up**.</span></span>  
  
 <span data-ttu-id="cf82d-127">您也可以在 [建立新的 InfoObject] 對話方塊的 [屬性] 區段中按一下 [加入]，藉以開啟 [查閱 InfoObject] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="cf82d-127">You can also open the **Look Up InfoObject** dialog box by clicking **Add** in the **Attributes** section of the **Create New InfoObject** dialog box.</span></span>  
  
## <a name="lookup-options"></a><span data-ttu-id="cf82d-128">查閱選項</span><span class="sxs-lookup"><span data-stu-id="cf82d-128">Lookup Options</span></span>  
 <span data-ttu-id="cf82d-129">在查閱欄位文字方塊中，您可以使用星號萬用字元 (\*) 或結合星號萬用字元使用部分字串來篩選結果。</span><span class="sxs-lookup"><span data-stu-id="cf82d-129">In the lookup field text boxes, you can filter results by using the asterisk wildcard character (\*), or by using a partial string in combination with the asterisk wildcard character.</span></span> <span data-ttu-id="cf82d-130">不過，如果您將查閱欄位保留空白，查閱處理序就只會比對該欄位中的空白字串。</span><span class="sxs-lookup"><span data-stu-id="cf82d-130">However, if you leave a lookup field empty, the lookup process will only match empty strings in that field.</span></span>  
  
 <span data-ttu-id="cf82d-131">**特性**</span><span class="sxs-lookup"><span data-stu-id="cf82d-131">**Characteristics**</span></span>  
 <span data-ttu-id="cf82d-132">查閱代表特性的 InfoObject。</span><span class="sxs-lookup"><span data-stu-id="cf82d-132">Look up InfoObjects that represent characteristics.</span></span>  
  
 <span data-ttu-id="cf82d-133">**單位**</span><span class="sxs-lookup"><span data-stu-id="cf82d-133">**Units**</span></span>  
 <span data-ttu-id="cf82d-134">查閱代表單位的 InfoObject。</span><span class="sxs-lookup"><span data-stu-id="cf82d-134">Look up InfoObjects that represent units.</span></span>  
  
 <span data-ttu-id="cf82d-135">**關鍵數據**</span><span class="sxs-lookup"><span data-stu-id="cf82d-135">**Key figures**</span></span>  
 <span data-ttu-id="cf82d-136">查閱代表關鍵數據的 InfoObject。</span><span class="sxs-lookup"><span data-stu-id="cf82d-136">Look up InfoObjects that represent key figures.</span></span>  
  
 <span data-ttu-id="cf82d-137">**時間特性**</span><span class="sxs-lookup"><span data-stu-id="cf82d-137">**Time characteristics**</span></span>  
 <span data-ttu-id="cf82d-138">查閱代表時間特性的 InfoObject。</span><span class="sxs-lookup"><span data-stu-id="cf82d-138">Look up InfoObjects that represent time characteristics.</span></span>  
  
 <span data-ttu-id="cf82d-139">**名稱**</span><span class="sxs-lookup"><span data-stu-id="cf82d-139">**Name**</span></span>  
 <span data-ttu-id="cf82d-140">輸入您想要查閱的 InfoObject 名稱，或是包含星號萬用字元 (\*) 的部分名稱。</span><span class="sxs-lookup"><span data-stu-id="cf82d-140">Enter the name of the InfoObject that you want to look up, or a partial name with the asterisk wildcard character (\*).</span></span> <span data-ttu-id="cf82d-141">或者，單獨使用星號萬用字元來包含所有 InfoObject。</span><span class="sxs-lookup"><span data-stu-id="cf82d-141">Or, use the asterisk wildcard character alone to include all InfoObjects.</span></span>  
  
 <span data-ttu-id="cf82d-142">**說明**</span><span class="sxs-lookup"><span data-stu-id="cf82d-142">**Description**</span></span>  
 <span data-ttu-id="cf82d-143">輸入描述，或是包含星號萬用字元 (\*) 的部分描述。</span><span class="sxs-lookup"><span data-stu-id="cf82d-143">Enter the description, or a partial description with the asterisk wildcard character (\*).</span></span> <span data-ttu-id="cf82d-144">或者，單獨使用星號萬用字元來包含所有 InfoObject (不論描述為何)。</span><span class="sxs-lookup"><span data-stu-id="cf82d-144">Or, use the asterisk wildcard character alone to include all InfoObjects regardless of description.</span></span>  
  
 <span data-ttu-id="cf82d-145">**查閱**</span><span class="sxs-lookup"><span data-stu-id="cf82d-145">**Look up**</span></span>  
 <span data-ttu-id="cf82d-146">查閱 SAP Netweaver BW 系統中定義的相符 InfoObject。</span><span class="sxs-lookup"><span data-stu-id="cf82d-146">Look up matching InfoObjects that are defined in the SAP Netweaver BW system.</span></span>  
  
## <a name="lookup-results"></a><span data-ttu-id="cf82d-147">查閱結果</span><span class="sxs-lookup"><span data-stu-id="cf82d-147">Lookup Results</span></span>  
 <span data-ttu-id="cf82d-148">在您按一下 [查閱] 按鈕之後，SAP Netweaver BW 系統中的 InfoObject 清單就會顯示在包含下列資料行標題的資料表中。</span><span class="sxs-lookup"><span data-stu-id="cf82d-148">After you click the Look up button, a list of the InfoObjects in the SAP Netweaver BW system appears in a table with the following column headings.</span></span>  
  
 <span data-ttu-id="cf82d-149">**InfoObject**</span><span class="sxs-lookup"><span data-stu-id="cf82d-149">**InfoObject**</span></span>  
 <span data-ttu-id="cf82d-150">顯示 SAP Netweaver BW 系統中定義的 InfoObject 名稱。</span><span class="sxs-lookup"><span data-stu-id="cf82d-150">Displays the name of the InfoObject that is defined in the SAP Netweaver BW system.</span></span>  
  
 <span data-ttu-id="cf82d-151">**文字 (短)**</span><span class="sxs-lookup"><span data-stu-id="cf82d-151">**Text (short)**</span></span>  
 <span data-ttu-id="cf82d-152">顯示與 InfoObject 相關聯的簡短文字。</span><span class="sxs-lookup"><span data-stu-id="cf82d-152">Displays the short text that is associated with the InfoObject.</span></span>  
  
 <span data-ttu-id="cf82d-153">出現可用的 InfoObject 清單時，請選取您要的 InfoObject，然後目的地就會將必要的值填入相關聯的選項。</span><span class="sxs-lookup"><span data-stu-id="cf82d-153">When the list of available InfoObjects appears, select the InfoObject that you want, and the destination will populate the associated options with the required values.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf82d-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cf82d-154">See Also</span></span>  
 <span data-ttu-id="cf82d-155">[建立交易資料的 InfoCube](create-infocube-for-transaction-data.md) </span><span class="sxs-lookup"><span data-stu-id="cf82d-155">[Create InfoCube for Transaction Data](create-infocube-for-transaction-data.md) </span></span>  
 <span data-ttu-id="cf82d-156">[建立 InfoSource](create-infosource.md) </span><span class="sxs-lookup"><span data-stu-id="cf82d-156">[Create InfoSource](create-infosource.md) </span></span>  
 <span data-ttu-id="cf82d-157">[建立交易資料的 InfoSource](create-infosource-for-transaction-data.md) </span><span class="sxs-lookup"><span data-stu-id="cf82d-157">[Create InfoSource for Transaction Data](create-infosource-for-transaction-data.md) </span></span>  
 <span data-ttu-id="cf82d-158">[建立主要資料的 InfoSource](create-infosource-for-master-data.md) </span><span class="sxs-lookup"><span data-stu-id="cf82d-158">[Create InfoSource for Master Data](create-infosource-for-master-data.md) </span></span>  
 <span data-ttu-id="cf82d-159">[建立新的 InfoObject](create-new-infoobject.md) </span><span class="sxs-lookup"><span data-stu-id="cf82d-159">[Create New InfoObject](create-new-infoobject.md) </span></span>  
 <span data-ttu-id="cf82d-160">[SAP BW 目的地編輯器 &#40;連線管理員頁面&#41;](sap-bw-destination-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="cf82d-160">[SAP BW Destination Editor &#40;Connection Manager Page&#41;](sap-bw-destination-editor-connection-manager-page.md) </span></span>  
 [<span data-ttu-id="cf82d-161">Microsoft Connector 1.1 for SAP BW F1 說明</span><span class="sxs-lookup"><span data-stu-id="cf82d-161">Microsoft Connector 1.1 for SAP BW F1 Help</span></span>](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  
