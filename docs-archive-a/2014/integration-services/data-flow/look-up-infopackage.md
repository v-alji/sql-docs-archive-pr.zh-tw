---
title: 查閱 InfoPackage | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 7c0cb7a4-cd07-44cc-85cb-eb1ad91f85fd
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1e45477e8faeed07faa114850e10a3bc4bbcf170
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700075"
---
# <a name="look-up-infopackage"></a><span data-ttu-id="56e6a-102">查閱 InfoPackage</span><span class="sxs-lookup"><span data-stu-id="56e6a-102">Look Up InfoPackage</span></span>
  <span data-ttu-id="56e6a-103">使用 [查閱 InfoPackage]  對話方塊可以查閱 SAP Netweaver BW 系統中定義的 InfoPackage。</span><span class="sxs-lookup"><span data-stu-id="56e6a-103">Use the **Look Up InfoPackage** dialog box to look up an InfoPackage that is defined in the SAP Netweaver BW system.</span></span> <span data-ttu-id="56e6a-104">出現 InfoPackage 的清單時，請選取您要的 InfoPackage，然後目的地就會將必要的值填入相關聯的選項。</span><span class="sxs-lookup"><span data-stu-id="56e6a-104">When the list of InfoPackages appears, select the InfoPackage that you want, and the destination will populate the associated options with the required values.</span></span>  
  
 <span data-ttu-id="56e6a-105">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW 的 SAP BW 目的地會使用 [查閱 ProcessChain]  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="56e6a-105">The SAP BW destination of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW uses the **Look Up Process Chain** dialog box.</span></span> <span data-ttu-id="56e6a-106">若要深入了解 SAP BW 目的地，請參閱 [SAP BW Destination](sap-bw-destination.md)。</span><span class="sxs-lookup"><span data-stu-id="56e6a-106">To learn more about the SAP BW destination, see [SAP BW Destination](sap-bw-destination.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="56e6a-107">Microsoft Connector 1.1 for SAP BW 的文件集是假設使用者已熟悉 SAP Netweaver BW 環境。</span><span class="sxs-lookup"><span data-stu-id="56e6a-107">The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment.</span></span> <span data-ttu-id="56e6a-108">如需有關 SAP Netweaver BW 的詳細資訊，或有關如何設定 SAP Netweaver BW 物件與處理序的詳細資訊，請參閱 SAP 文件集。</span><span class="sxs-lookup"><span data-stu-id="56e6a-108">For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.</span></span>  
  
 <span data-ttu-id="56e6a-109">**若要開啟查閱 InfoPackage 對話方塊**</span><span class="sxs-lookup"><span data-stu-id="56e6a-109">**To open the Look Up InfoPackage dialog box**</span></span>  
  
1.  <span data-ttu-id="56e6a-110">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，開啟包含 SAP BW 目的地的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 套件。</span><span class="sxs-lookup"><span data-stu-id="56e6a-110">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that contains the SAP BW destination.</span></span>  
  
2.  <span data-ttu-id="56e6a-111">在 [資料流程]  索引標籤上，按兩下 SAP BW 目的地。</span><span class="sxs-lookup"><span data-stu-id="56e6a-111">On the **Data Flow** tab, double-click the SAP BW destination.</span></span>  
  
3.  <span data-ttu-id="56e6a-112">在 **[SAP BW 目的地編輯器]** 中，按一下 **[連接管理員]** 開啟編輯器的 **[連接管理員]** 頁面。</span><span class="sxs-lookup"><span data-stu-id="56e6a-112">In the **SAP BW Destination Editor**, click **Connection Manager** to open the **Connection Manager** page of the editor.</span></span>  
  
4.  <span data-ttu-id="56e6a-113">在 [連線管理員]  頁面的 [InfoPackage/InfoSource]  群組方塊中，按一下 [查閱]  顯示 [查閱 InfoPackage]  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="56e6a-113">On the **Connection Manager** page, in the **InfoPackage/InfoSource** group box, click **Look up** to display the **Look Up InfoPackage** dialog box.</span></span>  
  
## <a name="lookup-options"></a><span data-ttu-id="56e6a-114">查閱選項</span><span class="sxs-lookup"><span data-stu-id="56e6a-114">Lookup Options</span></span>  
 <span data-ttu-id="56e6a-115">在查閱欄位中，您可以使用星號萬用字元 (\*) 或結合星號萬用字元使用部分字串來篩選結果。</span><span class="sxs-lookup"><span data-stu-id="56e6a-115">In the lookup fields, you can filter results by using the asterisk wildcard character (\*), or by using a partial string in combination with the asterisk wildcard character.</span></span> <span data-ttu-id="56e6a-116">不過，如果您將查閱欄位保留空白，查閱作業就只會比對該欄位中的空白字串。</span><span class="sxs-lookup"><span data-stu-id="56e6a-116">However, if you leave a lookup field empty, the lookup operation will only match empty strings in that field.</span></span>  
  
 <span data-ttu-id="56e6a-117">**InfoPackage**</span><span class="sxs-lookup"><span data-stu-id="56e6a-117">**InfoPackage**</span></span>  
 <span data-ttu-id="56e6a-118">輸入您想要查閱的 InfoPackage 名稱，或是包含星號萬用字元 (\*) 的部分名稱。</span><span class="sxs-lookup"><span data-stu-id="56e6a-118">Enter the name of the InfoPackage that you want to look up, or a partial name with the asterisk wildcard character (\*).</span></span> <span data-ttu-id="56e6a-119">或者，單獨使用星號萬用字元來包含所有 InfoPackage。</span><span class="sxs-lookup"><span data-stu-id="56e6a-119">Or, use the asterisk wildcard character alone to include all InfoPackages.</span></span>  
  
 <span data-ttu-id="56e6a-120">**InfoSource**</span><span class="sxs-lookup"><span data-stu-id="56e6a-120">**InfoSource**</span></span>  
 <span data-ttu-id="56e6a-121">輸入 InfoSource 的名稱，或是包含星號萬用字元 (\*) 的部分名稱。</span><span class="sxs-lookup"><span data-stu-id="56e6a-121">Enter the name of the InfoSource, or a partial name with the asterisk wildcard character (\*).</span></span> <span data-ttu-id="56e6a-122">或者，單獨使用星號萬用字元來包含所有 InfoPackage (不論 InfoSource 為何)。</span><span class="sxs-lookup"><span data-stu-id="56e6a-122">Or, use the asterisk wildcard character alone to include all InfoPackages regardless of InfoSource.</span></span>  
  
 <span data-ttu-id="56e6a-123">**來源系統**</span><span class="sxs-lookup"><span data-stu-id="56e6a-123">**Source system**</span></span>  
 <span data-ttu-id="56e6a-124">輸入來源系統的名稱，或是包含星號萬用字元 (\*) 的部分名稱。</span><span class="sxs-lookup"><span data-stu-id="56e6a-124">Enter the name of the source system, or a partial name with the asterisk wildcard character (\*).</span></span> <span data-ttu-id="56e6a-125">或者，單獨使用星號萬用字元來包含所有 InfoPackage (不論來源系統為何)。</span><span class="sxs-lookup"><span data-stu-id="56e6a-125">Or, use the asterisk wildcard character alone to include all InfoPackages regardless of source systems.</span></span>  
  
 <span data-ttu-id="56e6a-126">**查閱**</span><span class="sxs-lookup"><span data-stu-id="56e6a-126">**Look up**</span></span>  
 <span data-ttu-id="56e6a-127">查閱 SAP Netweaver BW 系統中定義的相符 InfoPackage。</span><span class="sxs-lookup"><span data-stu-id="56e6a-127">Look up matching InfoPackages that are defined in the SAP Netweaver BW system.</span></span>  
  
## <a name="lookup-results"></a><span data-ttu-id="56e6a-128">查閱結果</span><span class="sxs-lookup"><span data-stu-id="56e6a-128">Lookup Results</span></span>  
 <span data-ttu-id="56e6a-129">在您按一下 [查閱] 按鈕之後，SAP Netweaver BW 系統中的 InfoPackage 清單就會顯示在包含下列資料行標題的資料表中。</span><span class="sxs-lookup"><span data-stu-id="56e6a-129">After you click the Look up button, a list of the InfoPackages in the SAP Netweaver BW system appears in a table with the following column headings.</span></span>  
  
 <span data-ttu-id="56e6a-130">**InfoPackage**</span><span class="sxs-lookup"><span data-stu-id="56e6a-130">**InfoPackage**</span></span>  
 <span data-ttu-id="56e6a-131">顯示 SAP Netweaver BW 系統中定義的 InfoPackage 名稱。</span><span class="sxs-lookup"><span data-stu-id="56e6a-131">Displays the name of the InfoPackage that is defined in the SAP Netweaver BW system.</span></span>  
  
 <span data-ttu-id="56e6a-132">**型別**</span><span class="sxs-lookup"><span data-stu-id="56e6a-132">**Type**</span></span>  
 <span data-ttu-id="56e6a-133">顯示 InfoPackage 的類型。</span><span class="sxs-lookup"><span data-stu-id="56e6a-133">Displays the type of the InfoPackage.</span></span> <span data-ttu-id="56e6a-134">下表列出類型的可能值。</span><span class="sxs-lookup"><span data-stu-id="56e6a-134">The following table lists the possible values for the type.</span></span>  
  
|<span data-ttu-id="56e6a-135">值</span><span class="sxs-lookup"><span data-stu-id="56e6a-135">Value</span></span>|<span data-ttu-id="56e6a-136">描述</span><span class="sxs-lookup"><span data-stu-id="56e6a-136">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="56e6a-137">Trans.</span><span class="sxs-lookup"><span data-stu-id="56e6a-137">Trans.</span></span>|<span data-ttu-id="56e6a-138">交易資料。</span><span class="sxs-lookup"><span data-stu-id="56e6a-138">Transaction data.</span></span>|  
|<span data-ttu-id="56e6a-139">Attr.</span><span class="sxs-lookup"><span data-stu-id="56e6a-139">Attr.</span></span>|<span data-ttu-id="56e6a-140">屬性資料。</span><span class="sxs-lookup"><span data-stu-id="56e6a-140">Attribute data.</span></span>|  
|<span data-ttu-id="56e6a-141">文字</span><span class="sxs-lookup"><span data-stu-id="56e6a-141">Texts</span></span>|<span data-ttu-id="56e6a-142">文字。</span><span class="sxs-lookup"><span data-stu-id="56e6a-142">Texts.</span></span>|  
  
 <span data-ttu-id="56e6a-143">**說明**</span><span class="sxs-lookup"><span data-stu-id="56e6a-143">**Description**</span></span>  
 <span data-ttu-id="56e6a-144">顯示 InfoPackage 的描述。</span><span class="sxs-lookup"><span data-stu-id="56e6a-144">Displays the description of the InfoPackage.</span></span>  
  
 <span data-ttu-id="56e6a-145">**InfoSource**</span><span class="sxs-lookup"><span data-stu-id="56e6a-145">**InfoSource**</span></span>  
 <span data-ttu-id="56e6a-146">顯示與 InfoPackage 相關聯的 InfoSource 名稱 (如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="56e6a-146">Displays the name of the InfoSource, if any, that is associated with the InfoPackage.</span></span>  
  
 <span data-ttu-id="56e6a-147">**Source System**</span><span class="sxs-lookup"><span data-stu-id="56e6a-147">**Source System**</span></span>  
 <span data-ttu-id="56e6a-148">顯示來源系統的名稱。</span><span class="sxs-lookup"><span data-stu-id="56e6a-148">Displays the name of the source system.</span></span>  
  
 <span data-ttu-id="56e6a-149">出現 InfoPackage 的清單時，請選取您要的 InfoPackage，然後目的地就會將必要的值填入相關聯的選項。</span><span class="sxs-lookup"><span data-stu-id="56e6a-149">When the list of InfoPackages appears, select the InfoPackage that you want, and the destination will populate the associated options with the required values.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56e6a-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="56e6a-150">See Also</span></span>  
 <span data-ttu-id="56e6a-151">[SAP BW 目的地編輯器 &#40;連線管理員頁面&#41;](sap-bw-destination-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="56e6a-151">[SAP BW Destination Editor &#40;Connection Manager Page&#41;](sap-bw-destination-editor-connection-manager-page.md) </span></span>  
 [<span data-ttu-id="56e6a-152">Microsoft Connector 1.1 for SAP BW F1 說明</span><span class="sxs-lookup"><span data-stu-id="56e6a-152">Microsoft Connector 1.1 for SAP BW F1 Help</span></span>](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  
