---
title: 建立交易資料的 InfoCube | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 673cea01-a260-4fce-a1a0-f73839289805
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a20fe051cfdd3e6afe285279996fcf696a83c21b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687092"
---
# <a name="create-infocube-for-transaction-data"></a><span data-ttu-id="96581-102">建立交易資料的 InfoCube</span><span class="sxs-lookup"><span data-stu-id="96581-102">Create InfoCube for Transaction Data</span></span>
  <span data-ttu-id="96581-103">使用 [建立交易資料的 InfoCube]  對話方塊可以在 SAP Netweaver BW 系統中建立交易資料的新 InfoCube。</span><span class="sxs-lookup"><span data-stu-id="96581-103">Use the **Create InfoCube for Transaction Data** dialog box to create a new InfoCube for transaction data in the SAP Netweaver BW system.</span></span>  
  
 <span data-ttu-id="96581-104">您可以從 [SAP BW 目的地編輯器] 的 [連線管理員] 頁面開啟 [建立交易資料的 InfoCube] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="96581-104">You can open the **Create InfoCube for Transaction Data** dialog box from the **Connection Manager** page of the **SAP BW Destination Editor**.</span></span> <span data-ttu-id="96581-105">若要深入了解 SAP BW 目的地，請參閱 [SAP BW Destination](sap-bw-destination.md)。</span><span class="sxs-lookup"><span data-stu-id="96581-105">To learn more about the SAP BW destination, see [SAP BW Destination](sap-bw-destination.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="96581-106">Microsoft Connector 1.1 for SAP BW 的文件集是假設使用者已熟悉 SAP Netweaver BW 環境。</span><span class="sxs-lookup"><span data-stu-id="96581-106">The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment.</span></span> <span data-ttu-id="96581-107">如需有關 SAP Netweaver BW 的詳細資訊，或有關如何設定 SAP Netweaver BW 物件與處理序的詳細資訊，請參閱 SAP 文件集。</span><span class="sxs-lookup"><span data-stu-id="96581-107">For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.</span></span>  
  
 <span data-ttu-id="96581-108">**若要開啟建立交易資料的 InfoCube 對話方塊**</span><span class="sxs-lookup"><span data-stu-id="96581-108">**To open the Create InfoCube for Transaction Data dialog box**</span></span>  
  
1.  <span data-ttu-id="96581-109">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，開啟包含 SAP BW 目的地的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 套件。</span><span class="sxs-lookup"><span data-stu-id="96581-109">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that contains the SAP BW destination.</span></span>  
  
2.  <span data-ttu-id="96581-110">在 [資料流程]  索引標籤上，按兩下 SAP BW 目的地。</span><span class="sxs-lookup"><span data-stu-id="96581-110">On the **Data Flow** tab, double-click the SAP BW destination.</span></span>  
  
3.  <span data-ttu-id="96581-111">在 **[SAP BW 目的地編輯器]** 中，按一下 **[連接管理員]** 開啟編輯器的 **[連接管理員]** 頁面。</span><span class="sxs-lookup"><span data-stu-id="96581-111">In the **SAP BW Destination Editor**, click **Connection Manager** to open the **Connection Manager** page of the editor.</span></span>  
  
4.  <span data-ttu-id="96581-112">在 [連線管理員]  頁面的 [建立 SAP BW 物件]  群組方塊中，選取 [InfoCube]  ，然後按一下 [建立]  。</span><span class="sxs-lookup"><span data-stu-id="96581-112">On the **Connection Manager** page, in the **Create SAP BW Objects** group box, select **InfoCube**, and then click **Create**.</span></span>  
  
## <a name="general-options"></a><span data-ttu-id="96581-113">一般選項</span><span class="sxs-lookup"><span data-stu-id="96581-113">General Options</span></span>  
 <span data-ttu-id="96581-114">**InfoCube 名稱**</span><span class="sxs-lookup"><span data-stu-id="96581-114">**InfoCube name**</span></span>  
 <span data-ttu-id="96581-115">輸入新 InfoCube 的名稱。</span><span class="sxs-lookup"><span data-stu-id="96581-115">Enter a name for the new InfoCube.</span></span>  
  
 <span data-ttu-id="96581-116">**詳細描述**</span><span class="sxs-lookup"><span data-stu-id="96581-116">**Long description**</span></span>  
 <span data-ttu-id="96581-117">輸入新 InfoCube 的描述。</span><span class="sxs-lookup"><span data-stu-id="96581-117">Enter a description for the new InfoCube.</span></span>  
  
 <span data-ttu-id="96581-118">**儲存並啟用**</span><span class="sxs-lookup"><span data-stu-id="96581-118">**Save & Activate**</span></span>  
 <span data-ttu-id="96581-119">儲存並啟用新的 InfoCube。</span><span class="sxs-lookup"><span data-stu-id="96581-119">Save and activate the new InfoCube.</span></span>  
  
## <a name="infocube-transfer-structure-options"></a><span data-ttu-id="96581-120">InfoCube 傳送結構選項</span><span class="sxs-lookup"><span data-stu-id="96581-120">InfoCube Transfer Structure Options</span></span>  
 <span data-ttu-id="96581-121">InfoCube 傳送結構區段可讓您將資料流程資料行與 InfoObject 建立關聯。</span><span class="sxs-lookup"><span data-stu-id="96581-121">The InfoCube transfer structure section lets you associate data flow columns to InfoObjects.</span></span>  
  
 <span data-ttu-id="96581-122">**PipelineElement**</span><span class="sxs-lookup"><span data-stu-id="96581-122">**PipelineElement**</span></span>  
 <span data-ttu-id="96581-123">在連接到 SAP BW 目的地之資料流程的輸出中顯示資料行。</span><span class="sxs-lookup"><span data-stu-id="96581-123">Displays the column in the output of the data flow that is connected to the SAP BW destination.</span></span>  
  
 <span data-ttu-id="96581-124">**PipelineDataType**</span><span class="sxs-lookup"><span data-stu-id="96581-124">**PipelineDataType**</span></span>  
 <span data-ttu-id="96581-125">顯示資料流程資料行的資料類型。</span><span class="sxs-lookup"><span data-stu-id="96581-125">Displays the data type of the data flow column.</span></span>  
  
 <span data-ttu-id="96581-126">**InfoObject**</span><span class="sxs-lookup"><span data-stu-id="96581-126">**InfoObject**</span></span>  
 <span data-ttu-id="96581-127">顯示與資料流程資料行相關聯的 InfoObject 名稱。</span><span class="sxs-lookup"><span data-stu-id="96581-127">Displays the name of the InfoObject that is associated with the data flow column.</span></span>  
  
 <span data-ttu-id="96581-128">**型別**</span><span class="sxs-lookup"><span data-stu-id="96581-128">**Type**</span></span>  
 <span data-ttu-id="96581-129">顯示與資料流程資料行相關聯的 InfoObject 類型。</span><span class="sxs-lookup"><span data-stu-id="96581-129">Displays the type of the InfoObject that is associated with the data flow column.</span></span> <span data-ttu-id="96581-130">下表列出類型的可能值。</span><span class="sxs-lookup"><span data-stu-id="96581-130">The following table lists the possible values for the type.</span></span>  
  
|<span data-ttu-id="96581-131">值</span><span class="sxs-lookup"><span data-stu-id="96581-131">Value</span></span>|<span data-ttu-id="96581-132">描述</span><span class="sxs-lookup"><span data-stu-id="96581-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="96581-133">CHA</span><span class="sxs-lookup"><span data-stu-id="96581-133">CHA</span></span>|<span data-ttu-id="96581-134">特性</span><span class="sxs-lookup"><span data-stu-id="96581-134">Characteristics</span></span>|  
|<span data-ttu-id="96581-135">UNI</span><span class="sxs-lookup"><span data-stu-id="96581-135">UNI</span></span>|<span data-ttu-id="96581-136">單位</span><span class="sxs-lookup"><span data-stu-id="96581-136">Units</span></span>|  
|<span data-ttu-id="96581-137">KYF</span><span class="sxs-lookup"><span data-stu-id="96581-137">KYF</span></span>|<span data-ttu-id="96581-138">關鍵數據</span><span class="sxs-lookup"><span data-stu-id="96581-138">Key figures</span></span>|  
|<span data-ttu-id="96581-139">TIM</span><span class="sxs-lookup"><span data-stu-id="96581-139">TIM</span></span>|<span data-ttu-id="96581-140">時間特性</span><span class="sxs-lookup"><span data-stu-id="96581-140">Time characteristics</span></span>|  
  
 <span data-ttu-id="96581-141">**Iobject - 搜尋**</span><span class="sxs-lookup"><span data-stu-id="96581-141">**Iobject - Search**</span></span>  
 <span data-ttu-id="96581-142">將現有的 InfoObject 與目前資料列的資料流程資料行建立關聯。</span><span class="sxs-lookup"><span data-stu-id="96581-142">Associate an existing InfoObject to the data flow column for the current row.</span></span> <span data-ttu-id="96581-143">若要建立此關聯，請按一下 [搜尋]  ，然後使用 [查閱 InfoObject]  對話方塊來選取現有的 InfoObject。</span><span class="sxs-lookup"><span data-stu-id="96581-143">To make this association, click **Search**, and then use the **Look Up InfoObject** dialog box to select the existing InfoObject.</span></span> <span data-ttu-id="96581-144">如需有關此對話方塊的詳細資訊，請參閱＜ [Look Up InfoObject](look-up-infoobject.md)＞。</span><span class="sxs-lookup"><span data-stu-id="96581-144">For more information about this dialog box, see [Look Up InfoObject](look-up-infoobject.md).</span></span>  
  
 <span data-ttu-id="96581-145">在您選取現有的 InfoObject 之後，此元件就會將選取的值填入 [InfoObject]  和 [類型]  資料行。</span><span class="sxs-lookup"><span data-stu-id="96581-145">After you select an existing InfoObject, the component populates the **InfoObject** and **Type** columns with the selected values.</span></span>  
  
 <span data-ttu-id="96581-146">**Iobject - 新增**</span><span class="sxs-lookup"><span data-stu-id="96581-146">**Iobject - New**</span></span>  
 <span data-ttu-id="96581-147">建立新的 InfoObject 並將這個新的 InfoObject 與目前資料列中的資料流程資料行建立關聯。</span><span class="sxs-lookup"><span data-stu-id="96581-147">Create a new InfoObject and associate this new InfoObject to the data flow column in the current row.</span></span> <span data-ttu-id="96581-148">若要建立新的 InfoObject，請按一下 [新增]  ，然後使用 [建立新的 InfoObject]  對話方塊來建立 InfoObject。</span><span class="sxs-lookup"><span data-stu-id="96581-148">To create the new InfoObject, click **New**, and then use the **Create New InfoObject** dialog box to create the InfoObject.</span></span> <span data-ttu-id="96581-149">如需有關此對話方塊的詳細資訊，請參閱＜ [Create New InfoObject](create-new-infoobject.md)＞。</span><span class="sxs-lookup"><span data-stu-id="96581-149">For more information about this dialog box, see [Create New InfoObject](create-new-infoobject.md).</span></span>  
  
 <span data-ttu-id="96581-150">在您建立新的 InfoObject 之後，此元件就會將新的值填入 [InfoObject]  和 [類型]  資料行。</span><span class="sxs-lookup"><span data-stu-id="96581-150">After you create a new InfoObject, the component populates the **InfoObject** and **Type** columns with the new values.</span></span>  
  
 <span data-ttu-id="96581-151">**Iobject - 移除**</span><span class="sxs-lookup"><span data-stu-id="96581-151">**Iobject - Remove**</span></span>  
 <span data-ttu-id="96581-152">移除 InfoObject 與目前資料列的資料流程資料行之間的關聯。</span><span class="sxs-lookup"><span data-stu-id="96581-152">Remove the association between the InfoObject and the data flow column for the current row.</span></span> <span data-ttu-id="96581-153">若要移除此關聯，請按一下 [移除]  。</span><span class="sxs-lookup"><span data-stu-id="96581-153">To remove this association, click **Remove**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96581-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="96581-154">See Also</span></span>  
 [<span data-ttu-id="96581-155">Microsoft Connector 1.1 for SAP BW F1 說明</span><span class="sxs-lookup"><span data-stu-id="96581-155">Microsoft Connector 1.1 for SAP BW F1 Help</span></span>](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  
