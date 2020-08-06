---
title: 建立 InfoPackage | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 9cd4a848-409f-4681-a390-1c49a2aadbd7
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 95f6ddce4e97c0c21d9f77c432231d414770dbce
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687090"
---
# <a name="create-infopackage"></a><span data-ttu-id="15bbc-102">建立 InfoPackage</span><span class="sxs-lookup"><span data-stu-id="15bbc-102">Create InfoPackage</span></span>
  <span data-ttu-id="15bbc-103">使用 [建立 InfoPackage]  對話方塊可以在 SAP Netweaver BW 系統中建立新的 InfoPackage。</span><span class="sxs-lookup"><span data-stu-id="15bbc-103">Use the **Create InfoPackage** dialog box to create a new InfoPackage in the SAP Netweaver BW system.</span></span>  
  
 <span data-ttu-id="15bbc-104">您可以從 [SAP BW 目的地編輯器] 的 [連線管理員] 頁面開啟 [建立 InfoPackage] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="15bbc-104">You can open the **Create InfoPackage** dialog box from the **Connection Manager** page of the **SAP BW Destination Editor**.</span></span> <span data-ttu-id="15bbc-105">若要深入了解 SAP BW 目的地，請參閱 [SAP BW Destination](sap-bw-destination.md)。</span><span class="sxs-lookup"><span data-stu-id="15bbc-105">To learn more about the SAP BW destination, see [SAP BW Destination](sap-bw-destination.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="15bbc-106">Microsoft Connector 1.1 for SAP BW 的文件集是假設使用者已熟悉 SAP Netweaver BW 環境。</span><span class="sxs-lookup"><span data-stu-id="15bbc-106">The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment.</span></span> <span data-ttu-id="15bbc-107">如需有關 SAP Netweaver BW 的詳細資訊，或有關如何設定 SAP Netweaver BW 物件與處理序的詳細資訊，請參閱 SAP 文件集。</span><span class="sxs-lookup"><span data-stu-id="15bbc-107">For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.</span></span>  
  
 <span data-ttu-id="15bbc-108">**若要開啟建立 InfoPackage 對話方塊**</span><span class="sxs-lookup"><span data-stu-id="15bbc-108">**To open the Create InfoPackage dialog box**</span></span>  
  
1.  <span data-ttu-id="15bbc-109">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，開啟包含 SAP BW 目的地的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 套件。</span><span class="sxs-lookup"><span data-stu-id="15bbc-109">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that contains the SAP BW destination.</span></span>  
  
2.  <span data-ttu-id="15bbc-110">在 [資料流程]  索引標籤上，按兩下 SAP BW 目的地。</span><span class="sxs-lookup"><span data-stu-id="15bbc-110">On the **Data Flow** tab, double-click the SAP BW destination.</span></span>  
  
3.  <span data-ttu-id="15bbc-111">在 **[SAP BW 目的地編輯器]** 中，按一下 **[連接管理員]** 開啟編輯器的 **[連接管理員]** 頁面。</span><span class="sxs-lookup"><span data-stu-id="15bbc-111">In the **SAP BW Destination Editor**, click **Connection Manager** to open the **Connection Manager** page of the editor.</span></span>  
  
4.  <span data-ttu-id="15bbc-112">在 [連線管理員]  頁面的 [建立 SAP BW 物件]  群組方塊中，選取 [InfoPackage]  ，然後按一下 [建立]  。</span><span class="sxs-lookup"><span data-stu-id="15bbc-112">On the **Connection Manager** page, in the **Create SAP BW Objects** group box, select **InfoPackage**, and then click **Create**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="15bbc-113">選項。</span><span class="sxs-lookup"><span data-stu-id="15bbc-113">Options</span></span>  
 <span data-ttu-id="15bbc-114">**InfoSource**</span><span class="sxs-lookup"><span data-stu-id="15bbc-114">**InfoSource**</span></span>  
 <span data-ttu-id="15bbc-115">輸入新 InfoPackage 應該依據的 InfoSource 名稱。</span><span class="sxs-lookup"><span data-stu-id="15bbc-115">Enter the name of the InfoSource on which the new InfoPackage should be based.</span></span>  
  
 <span data-ttu-id="15bbc-116">**簡短描述**</span><span class="sxs-lookup"><span data-stu-id="15bbc-116">**Short description**</span></span>  
 <span data-ttu-id="15bbc-117">輸入新 InfoPackage 的描述。</span><span class="sxs-lookup"><span data-stu-id="15bbc-117">Enter a description for the new InfoPackage.</span></span>  
  
 <span data-ttu-id="15bbc-118">**來源系統**</span><span class="sxs-lookup"><span data-stu-id="15bbc-118">**Source system**</span></span>  
 <span data-ttu-id="15bbc-119">選取應該與新 InfoPackage 相關聯的來源系統。</span><span class="sxs-lookup"><span data-stu-id="15bbc-119">Select the source system with which the new InfoPackage should be associated.</span></span>  
  
 <span data-ttu-id="15bbc-120">**屬性**</span><span class="sxs-lookup"><span data-stu-id="15bbc-120">**Attributes**</span></span>  
 <span data-ttu-id="15bbc-121">表示 InfoPackage 將會載入屬性資料。</span><span class="sxs-lookup"><span data-stu-id="15bbc-121">Indicates that the InfoPackage will load attribute data.</span></span>  
  
 <span data-ttu-id="15bbc-122">**文字**</span><span class="sxs-lookup"><span data-stu-id="15bbc-122">**Texts**</span></span>  
 <span data-ttu-id="15bbc-123">表示 InfoPackage 將會載入文字資料。</span><span class="sxs-lookup"><span data-stu-id="15bbc-123">Indicates that the InfoPackage will load text data.</span></span>  
  
 <span data-ttu-id="15bbc-124">**交易**</span><span class="sxs-lookup"><span data-stu-id="15bbc-124">**Transaction**</span></span>  
 <span data-ttu-id="15bbc-125">表示 InfoPackage 將會載入交易資料。</span><span class="sxs-lookup"><span data-stu-id="15bbc-125">Indicates that the InfoPackage will load transaction data.</span></span>  
  
 <span data-ttu-id="15bbc-126">**儲存並啟用**</span><span class="sxs-lookup"><span data-stu-id="15bbc-126">**Save & Activate**</span></span>  
 <span data-ttu-id="15bbc-127">儲存並啟用新的 InfoPackage。</span><span class="sxs-lookup"><span data-stu-id="15bbc-127">Save and activate the new InfoPackage.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15bbc-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="15bbc-128">See Also</span></span>  
 [<span data-ttu-id="15bbc-129">Microsoft Connector 1.1 for SAP BW F1 說明</span><span class="sxs-lookup"><span data-stu-id="15bbc-129">Microsoft Connector 1.1 for SAP BW F1 Help</span></span>](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  
