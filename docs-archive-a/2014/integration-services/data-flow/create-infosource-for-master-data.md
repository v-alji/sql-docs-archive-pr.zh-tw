---
title: 建立主要資料的 InfoSource | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: b52a9a89-8380-4a02-8a83-dcfb46ae860e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: bb90bc5cf27f37dc89df236b765db98088a5804a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687088"
---
# <a name="create-infosource-for-master-data"></a><span data-ttu-id="32992-102">[建立主要資料的 InfoSource]</span><span class="sxs-lookup"><span data-stu-id="32992-102">Create InfoSource for Master Data</span></span>
  <span data-ttu-id="32992-103">使用 [建立主要資料的 InfoSource]  對話方塊可以在 SAP Netweaver BW 系統中建立主要資料的新 InfoSource。</span><span class="sxs-lookup"><span data-stu-id="32992-103">Use the **Create InfoSource for Master Data** dialog box to create a new InfoSource for master data in the SAP Netweaver BW system.</span></span>  
  
 <span data-ttu-id="32992-104">您可以從 [SAP BW 目的地編輯器]  的 [連線管理員]  頁面開啟 [建立主要資料的 InfoSource]  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="32992-104">You can open the **Create InfoSource for Master Data** dialog box from the **Connection Manager** page of the **SAP BW Destination Editor**.</span></span> <span data-ttu-id="32992-105">若要深入了解 SAP BW 目的地，請參閱 [SAP BW Destination](sap-bw-destination.md)。</span><span class="sxs-lookup"><span data-stu-id="32992-105">To learn more about the SAP BW destination, see [SAP BW Destination](sap-bw-destination.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="32992-106">Microsoft Connector 1.1 for SAP BW 的文件集是假設使用者已熟悉 SAP Netweaver BW 環境。</span><span class="sxs-lookup"><span data-stu-id="32992-106">The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment.</span></span> <span data-ttu-id="32992-107">如需有關 SAP Netweaver BW 的詳細資訊，或有關如何設定 SAP Netweaver BW 物件與處理序的詳細資訊，請參閱 SAP 文件集。</span><span class="sxs-lookup"><span data-stu-id="32992-107">For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.</span></span>  
  
 <span data-ttu-id="32992-108">**若要開啟建立主要資料的 InfoSource 對話方塊**</span><span class="sxs-lookup"><span data-stu-id="32992-108">**To open the Create InfoSource for Master Data dialog box**</span></span>  
  
1.  <span data-ttu-id="32992-109">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，開啟包含 SAP BW 目的地的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 套件。</span><span class="sxs-lookup"><span data-stu-id="32992-109">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that contains the SAP BW destination.</span></span>  
  
2.  <span data-ttu-id="32992-110">在 [資料流程]  索引標籤上，按兩下 SAP BW 目的地。</span><span class="sxs-lookup"><span data-stu-id="32992-110">On the **Data Flow** tab, double-click the SAP BW destination.</span></span>  
  
3.  <span data-ttu-id="32992-111">在 **[SAP BW 目的地編輯器]** 中，按一下 **[連接管理員]** 開啟編輯器的 **[連接管理員]** 頁面。</span><span class="sxs-lookup"><span data-stu-id="32992-111">In the **SAP BW Destination Editor**, click **Connection Manager** to open the **Connection Manager** page of the editor.</span></span>  
  
4.  <span data-ttu-id="32992-112">在 [連線管理員]  頁面的 [建立 SAP BW 物件]  群組方塊中，選取 [InfoSource]  ，然後按一下 [建立]  。</span><span class="sxs-lookup"><span data-stu-id="32992-112">On the **Connection Manager** page, in the **Create SAP BW Objects** group box, select **InfoSource**, and then click **Create**.</span></span>  
  
5.  <span data-ttu-id="32992-113">在 [建立 InfoSource]  對話方塊中，選取 [主要資料]  ，然後按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="32992-113">In the **Create InfoSource** dialog box, select **Master data**, and then click **OK**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="32992-114">選項。</span><span class="sxs-lookup"><span data-stu-id="32992-114">Options</span></span>  
 <span data-ttu-id="32992-115">**InfoObject 名稱**</span><span class="sxs-lookup"><span data-stu-id="32992-115">**InfoObject name**</span></span>  
 <span data-ttu-id="32992-116">輸入新 InfoSource 應該依據的 InfoObject 名稱。</span><span class="sxs-lookup"><span data-stu-id="32992-116">Enter the name of the InfoObject on which the new InfoSource should be based.</span></span>  
  
 <span data-ttu-id="32992-117">**查閱**</span><span class="sxs-lookup"><span data-stu-id="32992-117">**Look up**</span></span>  
 <span data-ttu-id="32992-118">查閱 InfoObject。</span><span class="sxs-lookup"><span data-stu-id="32992-118">Look up the InfoObject.</span></span> <span data-ttu-id="32992-119">這個選項會開啟 [查閱 InfoObject]  對話方塊，讓您能夠選取 InfoObject。</span><span class="sxs-lookup"><span data-stu-id="32992-119">This option opens the **Look Up InfoObject** dialog box in which you can select the InfoObject.</span></span> <span data-ttu-id="32992-120">如需有關此對話方塊的詳細資訊，請參閱＜ [Look Up InfoObject](look-up-infoobject.md)＞。</span><span class="sxs-lookup"><span data-stu-id="32992-120">For more information about this dialog box, see [Look Up InfoObject](look-up-infoobject.md).</span></span>  
  
 <span data-ttu-id="32992-121">在您選取 InfoObject 之後，此元件就會將選取之 InfoObject 的名稱填入 [InfoObject 名稱]  文字方塊。</span><span class="sxs-lookup"><span data-stu-id="32992-121">After you select an InfoObject, the component populates the **InfoObject name** text box with the name of the selected InfoObject.</span></span>  
  
 <span data-ttu-id="32992-122">**新增**</span><span class="sxs-lookup"><span data-stu-id="32992-122">**New**</span></span>  
 <span data-ttu-id="32992-123">建立新的 InfoObject。</span><span class="sxs-lookup"><span data-stu-id="32992-123">Create a new InfoObject.</span></span> <span data-ttu-id="32992-124">這個選項會開啟 [建立新的 InfoObject]  對話方塊，讓您能夠建立新的 InfoObject。</span><span class="sxs-lookup"><span data-stu-id="32992-124">This option opens the **Create New InfoObject** dialog box in which you can create the new InfoObject.</span></span> <span data-ttu-id="32992-125">如需有關此對話方塊的詳細資訊，請參閱＜ [Create New InfoObject](create-new-infoobject.md)＞。</span><span class="sxs-lookup"><span data-stu-id="32992-125">For more information about this dialog box, see [Create New InfoObject](create-new-infoobject.md).</span></span>  
  
 <span data-ttu-id="32992-126">在您建立 InfoObject 之後，此元件就會將新 InfoObject 的名稱填入 [InfoObject 名稱]  文字方塊。</span><span class="sxs-lookup"><span data-stu-id="32992-126">After you create an InfoObject, the component populates the **InfoObject name** text box with the name of the new InfoObject.</span></span>  
  
 <span data-ttu-id="32992-127">**簡短描述**</span><span class="sxs-lookup"><span data-stu-id="32992-127">**Short description**</span></span>  
 <span data-ttu-id="32992-128">輸入新 InfoSource 的簡短描述。</span><span class="sxs-lookup"><span data-stu-id="32992-128">Enter a short description for the new InfoSource.</span></span>  
  
 <span data-ttu-id="32992-129">**詳細描述**</span><span class="sxs-lookup"><span data-stu-id="32992-129">**Long description**</span></span>  
 <span data-ttu-id="32992-130">輸入新 InfoSource 的詳細描述。</span><span class="sxs-lookup"><span data-stu-id="32992-130">Enter a long description for the new InfoSource.</span></span>  
  
 <span data-ttu-id="32992-131">**來源系統**</span><span class="sxs-lookup"><span data-stu-id="32992-131">**Source system**</span></span>  
 <span data-ttu-id="32992-132">選取要與新 InfoSource 相關聯的來源系統。</span><span class="sxs-lookup"><span data-stu-id="32992-132">Select the source system to be associated with the new InfoSource.</span></span>  
  
 <span data-ttu-id="32992-133">**應用程式**</span><span class="sxs-lookup"><span data-stu-id="32992-133">**Application**</span></span>  
 <span data-ttu-id="32992-134">輸入要與新 InfoSource 相關聯的應用程式名稱。</span><span class="sxs-lookup"><span data-stu-id="32992-134">Enter the name of the application to be associated with the new InfoSource.</span></span>  
  
 <span data-ttu-id="32992-135">**屬性**</span><span class="sxs-lookup"><span data-stu-id="32992-135">**Attributes**</span></span>  
 <span data-ttu-id="32992-136">表示主要資料包含屬性。</span><span class="sxs-lookup"><span data-stu-id="32992-136">Indicates that the master data consists of attributes.</span></span>  
  
 <span data-ttu-id="32992-137">**文字**</span><span class="sxs-lookup"><span data-stu-id="32992-137">**Texts**</span></span>  
 <span data-ttu-id="32992-138">表示主要資料包含屬性。</span><span class="sxs-lookup"><span data-stu-id="32992-138">Indicates that the master data consists of attributes.</span></span>  
  
 <span data-ttu-id="32992-139">**儲存並啟用**</span><span class="sxs-lookup"><span data-stu-id="32992-139">**Save & Activate**</span></span>  
 <span data-ttu-id="32992-140">儲存並啟用新的 InfoSource。</span><span class="sxs-lookup"><span data-stu-id="32992-140">Save and activate the new InfoSource.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32992-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="32992-141">See Also</span></span>  
 <span data-ttu-id="32992-142">[建立 InfoSource](create-infosource.md) </span><span class="sxs-lookup"><span data-stu-id="32992-142">[Create InfoSource](create-infosource.md) </span></span>  
 [<span data-ttu-id="32992-143">Microsoft Connector 1.1 for SAP BW F1 說明</span><span class="sxs-lookup"><span data-stu-id="32992-143">Microsoft Connector 1.1 for SAP BW F1 Help</span></span>](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  
