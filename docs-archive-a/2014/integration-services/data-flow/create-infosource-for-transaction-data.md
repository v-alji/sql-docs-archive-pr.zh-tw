---
title: 建立交易資料的 InfoSource | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: ab5f23e2-cd4e-4507-83d9-ac5ef721c171
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 3e3a60bb93da17e79087982473e92c35fa0856d3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687084"
---
# <a name="create-infosource-for-transaction-data"></a><span data-ttu-id="01c9a-102">建立交易資料的 InfoSource</span><span class="sxs-lookup"><span data-stu-id="01c9a-102">Create InfoSource for Transaction Data</span></span>
  <span data-ttu-id="01c9a-103">使用 [建立交易資料的 InfoSource]  對話方塊可以在 SAP Netweaver BW 系統中建立交易資料的新 InfoSource。</span><span class="sxs-lookup"><span data-stu-id="01c9a-103">Use the **Create InfoSource for Transaction Data** dialog box to create a new InfoSource for transaction data in the SAP Netweaver BW system.</span></span>  
  
 <span data-ttu-id="01c9a-104">您可以從 [SAP BW 目的地編輯器]  的 [連線管理員]  頁面開啟 [建立交易資料的 InfoSource]  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="01c9a-104">You can open the **Create InfoSource for Transaction Data** dialog box from the **Connection Manager** page of the **SAP BW Destination Editor**.</span></span> <span data-ttu-id="01c9a-105">若要深入了解 SAP BW 目的地，請參閱 [SAP BW Destination](sap-bw-destination.md)。</span><span class="sxs-lookup"><span data-stu-id="01c9a-105">To learn more about the SAP BW destination, see [SAP BW Destination](sap-bw-destination.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="01c9a-106">Microsoft Connector 1.1 for SAP BW 的文件集是假設使用者已熟悉 SAP Netweaver BW 環境。</span><span class="sxs-lookup"><span data-stu-id="01c9a-106">The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment.</span></span> <span data-ttu-id="01c9a-107">如需有關 SAP Netweaver BW 的詳細資訊，或有關如何設定 SAP Netweaver BW 物件與處理序的詳細資訊，請參閱 SAP 文件集。</span><span class="sxs-lookup"><span data-stu-id="01c9a-107">For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.</span></span>  
  
 <span data-ttu-id="01c9a-108">**若要開啟建立交易資料的 InfoSource 對話方塊**</span><span class="sxs-lookup"><span data-stu-id="01c9a-108">**To open the Create InfoSource for Transaction Data dialog box**</span></span>  
  
1.  <span data-ttu-id="01c9a-109">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，開啟包含 SAP BW 目的地的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 套件。</span><span class="sxs-lookup"><span data-stu-id="01c9a-109">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that contains the SAP BW destination.</span></span>  
  
2.  <span data-ttu-id="01c9a-110">在 [資料流程]  索引標籤上，按兩下 SAP BW 目的地。</span><span class="sxs-lookup"><span data-stu-id="01c9a-110">On the **Data Flow** tab, double-click the SAP BW destination.</span></span>  
  
3.  <span data-ttu-id="01c9a-111">在 **[SAP BW 目的地編輯器]** 中，按一下 **[連接管理員]** 開啟編輯器的 **[連接管理員]** 頁面。</span><span class="sxs-lookup"><span data-stu-id="01c9a-111">In the **SAP BW Destination Editor**, click **Connection Manager** to open the **Connection Manager** page of the editor.</span></span>  
  
4.  <span data-ttu-id="01c9a-112">在 [連線管理員]  頁面的 [建立 SAP BW 物件]  群組方塊中，選取 [InfoSource]  ，然後按一下 [建立]  。</span><span class="sxs-lookup"><span data-stu-id="01c9a-112">On the **Connection Manager** page, in the **Create SAP BW Objects** group box, select **InfoSource**, and then click **Create**.</span></span>  
  
5.  <span data-ttu-id="01c9a-113">在 [建立 InfoSource]  對話方塊中，選取 [交易資料]  ，然後按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="01c9a-113">In the **Create InfoSource** dialog box, select **Transaction data**, and then click **OK**.</span></span>  
  
## <a name="general-options"></a><span data-ttu-id="01c9a-114">一般選項</span><span class="sxs-lookup"><span data-stu-id="01c9a-114">General Options</span></span>  
 <span data-ttu-id="01c9a-115">**InfoSource 名稱**</span><span class="sxs-lookup"><span data-stu-id="01c9a-115">**InfoSource name**</span></span>  
 <span data-ttu-id="01c9a-116">輸入新 InfoSource 的名稱。</span><span class="sxs-lookup"><span data-stu-id="01c9a-116">Enter a name for the new InfoSource.</span></span>  
  
 <span data-ttu-id="01c9a-117">**簡短描述**</span><span class="sxs-lookup"><span data-stu-id="01c9a-117">**Short description**</span></span>  
 <span data-ttu-id="01c9a-118">輸入新 InfoSource 的簡短描述。</span><span class="sxs-lookup"><span data-stu-id="01c9a-118">Enter a short description for the new InfoSource.</span></span>  
  
 <span data-ttu-id="01c9a-119">**詳細描述**</span><span class="sxs-lookup"><span data-stu-id="01c9a-119">**Long description**</span></span>  
 <span data-ttu-id="01c9a-120">輸入新 InfoSource 的詳細描述。</span><span class="sxs-lookup"><span data-stu-id="01c9a-120">Enter a long description for the new InfoSource.</span></span>  
  
 <span data-ttu-id="01c9a-121">**來源系統**</span><span class="sxs-lookup"><span data-stu-id="01c9a-121">**Source system**</span></span>  
 <span data-ttu-id="01c9a-122">選取與 InfoSource 相關聯的來源系統。</span><span class="sxs-lookup"><span data-stu-id="01c9a-122">Select the source system associated with the InfoSource.</span></span>  
  
 <span data-ttu-id="01c9a-123">**儲存並啟用**</span><span class="sxs-lookup"><span data-stu-id="01c9a-123">**Save & Activate**</span></span>  
 <span data-ttu-id="01c9a-124">儲存並啟用新的 InfoSource。</span><span class="sxs-lookup"><span data-stu-id="01c9a-124">Save and activate the new InfoSource.</span></span>  
  
## <a name="infosource-transfer-structure-options"></a><span data-ttu-id="01c9a-125">InfoSource 傳送結構選項</span><span class="sxs-lookup"><span data-stu-id="01c9a-125">InfoSource Transfer Structure Options</span></span>  
 <span data-ttu-id="01c9a-126">InfoSource 傳送結構可讓您將資料流程資料行與 InfoSource 建立關聯。</span><span class="sxs-lookup"><span data-stu-id="01c9a-126">The InfoSource transfer structure lets you associate data flow columns to InfoSources.</span></span>  
  
 <span data-ttu-id="01c9a-127">**PipelineElement**</span><span class="sxs-lookup"><span data-stu-id="01c9a-127">**PipelineElement**</span></span>  
 <span data-ttu-id="01c9a-128">在連接到 SAP BW 目的地之資料流程的輸出中顯示資料行。</span><span class="sxs-lookup"><span data-stu-id="01c9a-128">Displays the column in the output of the data flow that is connected to the SAP BW destination.</span></span>  
  
 <span data-ttu-id="01c9a-129">**PipelineDataType**</span><span class="sxs-lookup"><span data-stu-id="01c9a-129">**PipelineDataType**</span></span>  
 <span data-ttu-id="01c9a-130">顯示資料流程資料行的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 資料類型。</span><span class="sxs-lookup"><span data-stu-id="01c9a-130">Displays the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] data type of the data flow column.</span></span>  
  
 <span data-ttu-id="01c9a-131">**Iobject - 搜尋**</span><span class="sxs-lookup"><span data-stu-id="01c9a-131">**Iobject - Search**</span></span>  
 <span data-ttu-id="01c9a-132">將現有的 InfoObject 與目前資料列中的資料流程資料行建立關聯。</span><span class="sxs-lookup"><span data-stu-id="01c9a-132">Associate an existing InfoObject to the data flow column in the current row.</span></span> <span data-ttu-id="01c9a-133">若要建立此關聯，請按一下 [搜尋]  ，然後使用 [查閱 InfoObject]  對話方塊來選取現有的 InfoObject。</span><span class="sxs-lookup"><span data-stu-id="01c9a-133">To make this association, click **Search**, and then use the **Look Up InfoObject** dialog box to select the existing InfoObject.</span></span> <span data-ttu-id="01c9a-134">如需有關此對話方塊的詳細資訊，請參閱＜ [Look Up InfoObject](look-up-infoobject.md)＞。</span><span class="sxs-lookup"><span data-stu-id="01c9a-134">For more information about this dialog box, see [Look Up InfoObject](look-up-infoobject.md).</span></span>  
  
 <span data-ttu-id="01c9a-135">在您選取現有的 InfoObject 之後，此元件就會將選取的值填入 [InfoObject]  和 [類型]  資料行。</span><span class="sxs-lookup"><span data-stu-id="01c9a-135">After you select an existing InfoObject, the component populates the **InfoObject** and **Type** columns with the selected values.</span></span>  
  
 <span data-ttu-id="01c9a-136">**Iobject - 新增**</span><span class="sxs-lookup"><span data-stu-id="01c9a-136">**Iobject - New**</span></span>  
 <span data-ttu-id="01c9a-137">建立新的 InfoObject 並將這個新的 InfoObject 與目前資料列中的資料流程資料行建立關聯。</span><span class="sxs-lookup"><span data-stu-id="01c9a-137">Create a new InfoObject and associate this new InfoObect to the data flow column in the current row.</span></span> <span data-ttu-id="01c9a-138">若要建立新的 InfoObject，請按一下 [新增]  ，然後使用 [建立新的 InfoObject]  對話方塊來建立 InfoObject。</span><span class="sxs-lookup"><span data-stu-id="01c9a-138">To create the new InfoObject, click **New**, and then use the **Create New InfoObject** dialog box to create the InfoObject.</span></span> <span data-ttu-id="01c9a-139">如需有關此對話方塊的詳細資訊，請參閱＜ [Create New InfoObject](create-new-infoobject.md)＞。</span><span class="sxs-lookup"><span data-stu-id="01c9a-139">For more information about this dialog box, see [Create New InfoObject](create-new-infoobject.md).</span></span>  
  
 <span data-ttu-id="01c9a-140">在您建立新的 InfoObject 之後，此元件就會將新的值填入 [InfoObject]  和 [類型]  資料行。</span><span class="sxs-lookup"><span data-stu-id="01c9a-140">After you create a new InfoObject, the component populates the **InfoObject** and **Type** columns with the new values.</span></span>  
  
 <span data-ttu-id="01c9a-141">**Iobject - 移除**</span><span class="sxs-lookup"><span data-stu-id="01c9a-141">**Iobject - Remove**</span></span>  
 <span data-ttu-id="01c9a-142">移除 InfoObject 與目前資料列的資料流程資料行之間的關聯。</span><span class="sxs-lookup"><span data-stu-id="01c9a-142">Remove the association between the InfoObject and the data flow column for the current row.</span></span> <span data-ttu-id="01c9a-143">若要移除此關聯，請按一下 [移除]  。</span><span class="sxs-lookup"><span data-stu-id="01c9a-143">To remove this association, click **Remove**.</span></span>  
  
 <span data-ttu-id="01c9a-144">**InfoObject**</span><span class="sxs-lookup"><span data-stu-id="01c9a-144">**InfoObject**</span></span>  
 <span data-ttu-id="01c9a-145">顯示與資料流程資料行相關聯的 InfoObject 名稱。</span><span class="sxs-lookup"><span data-stu-id="01c9a-145">Displays the name of the InfoObject that is associated with the data flow column.</span></span>  
  
 <span data-ttu-id="01c9a-146">**型別**</span><span class="sxs-lookup"><span data-stu-id="01c9a-146">**Type**</span></span>  
 <span data-ttu-id="01c9a-147">顯示與資料流程資料行相關聯的 InfoObject 類型。</span><span class="sxs-lookup"><span data-stu-id="01c9a-147">Displays the type of the InfoObject that is associated with the data flow column.</span></span> <span data-ttu-id="01c9a-148">下表列出類型的可能值。</span><span class="sxs-lookup"><span data-stu-id="01c9a-148">The following table lists the possible values for the type.</span></span>  
  
|<span data-ttu-id="01c9a-149">值</span><span class="sxs-lookup"><span data-stu-id="01c9a-149">Value</span></span>|<span data-ttu-id="01c9a-150">描述</span><span class="sxs-lookup"><span data-stu-id="01c9a-150">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="01c9a-151">CHA</span><span class="sxs-lookup"><span data-stu-id="01c9a-151">CHA</span></span>|<span data-ttu-id="01c9a-152">特性</span><span class="sxs-lookup"><span data-stu-id="01c9a-152">Characteristics</span></span>|  
|<span data-ttu-id="01c9a-153">UNI</span><span class="sxs-lookup"><span data-stu-id="01c9a-153">UNI</span></span>|<span data-ttu-id="01c9a-154">單位</span><span class="sxs-lookup"><span data-stu-id="01c9a-154">Units</span></span>|  
|<span data-ttu-id="01c9a-155">KYF</span><span class="sxs-lookup"><span data-stu-id="01c9a-155">KYF</span></span>|<span data-ttu-id="01c9a-156">關鍵數據</span><span class="sxs-lookup"><span data-stu-id="01c9a-156">Key figures</span></span>|  
|<span data-ttu-id="01c9a-157">TIM</span><span class="sxs-lookup"><span data-stu-id="01c9a-157">TIM</span></span>|<span data-ttu-id="01c9a-158">時間特性</span><span class="sxs-lookup"><span data-stu-id="01c9a-158">Time characteristics</span></span>|  
  
 <span data-ttu-id="01c9a-159">**單位欄位**</span><span class="sxs-lookup"><span data-stu-id="01c9a-159">**Unit Field**</span></span>  
 <span data-ttu-id="01c9a-160">指定 InfoObject 將使用的單位。</span><span class="sxs-lookup"><span data-stu-id="01c9a-160">Specify the units that the InfoObject will use.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01c9a-161">另請參閱</span><span class="sxs-lookup"><span data-stu-id="01c9a-161">See Also</span></span>  
 <span data-ttu-id="01c9a-162">[建立 InfoSource](create-infosource.md) </span><span class="sxs-lookup"><span data-stu-id="01c9a-162">[Create InfoSource](create-infosource.md) </span></span>  
 [<span data-ttu-id="01c9a-163">Microsoft Connector 1.1 for SAP BW F1 說明</span><span class="sxs-lookup"><span data-stu-id="01c9a-163">Microsoft Connector 1.1 for SAP BW F1 Help</span></span>](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  
