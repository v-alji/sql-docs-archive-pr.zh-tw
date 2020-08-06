---
title: 使用目的地輔助程式新增目的地 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 747a0de0-3c2f-4d31-a692-7111fc0911d8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: cd36828a7bab7fb33b86765f9f064b6406a17a9a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592821"
---
# <a name="add-a-destination-using-destination-assistant"></a><span data-ttu-id="5348e-102">使用目的地小幫手來加入目的地</span><span class="sxs-lookup"><span data-stu-id="5348e-102">Add a Destination using Destination Assistant</span></span>
  <span data-ttu-id="5348e-103">本主題提供使用目的地小幫手來加入新目的地的步驟，也會列出可在 [加入新目的地]  對話方塊上使用的選項。當您將目的地小幫手拖放至 SSIS 設計師時，即會顯示此對話方塊。</span><span class="sxs-lookup"><span data-stu-id="5348e-103">This topic provides steps to add a new destination using the Destination Assistant and also lists the options that are available on the **Add New Destination** dialog, which you will see when you drag-drop the Destination Assistant to the SSIS Designer.</span></span>  
  
### <a name="to-use-destination-assistant-to-add-a-destination"></a><span data-ttu-id="5348e-104">使用目的地小幫手加入目的地</span><span class="sxs-lookup"><span data-stu-id="5348e-104">To use Destination Assistant to add a destination</span></span>  
  
1.  <span data-ttu-id="5348e-105">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 中，開啟要加入目的地元件的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 封裝。</span><span class="sxs-lookup"><span data-stu-id="5348e-105">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package that you want to add a destination component to.</span></span>  
  
2.  <span data-ttu-id="5348e-106">將 [目的地小幫手]  元件從 SSIS 工具箱拖曳至 [資料流程]  索引標籤。[加入新目的地]  對話方塊應會隨即出現。</span><span class="sxs-lookup"><span data-stu-id="5348e-106">Drag the **Destination Assistant** component from the SSIS Toolbox to the **Data Flow** tab. You should see the **Add New Destination** dialog box.</span></span> <span data-ttu-id="5348e-107">下一節提供可以在對話方塊中使用之選項的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="5348e-107">The next section provides you details about the options available in the dialog box.</span></span>  
  
3.  <span data-ttu-id="5348e-108">在 [類型]  清單中選取目的地的類型。</span><span class="sxs-lookup"><span data-stu-id="5348e-108">Select the type of the destination in the **Types** list.</span></span>  
  
4.  <span data-ttu-id="5348e-109">在 [連線管理員] 清單中選取現有的連線管理員，或選取 **\<New>** ，以建立新的連線管理員。</span><span class="sxs-lookup"><span data-stu-id="5348e-109">Select an existing connection manager in the **Connection Managers** list or select **\<New>** to create a new connection manager.</span></span>  
  
5.  <span data-ttu-id="5348e-110">如果您選取現有的連線管理員，請按一下 [確定]  ，以關閉 [加入新目的地]  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="5348e-110">If you select an existing connection manager, click **OK** to close the **Add New Destination** dialog box.</span></span> <span data-ttu-id="5348e-111">您應該會看到目的地和連線管理員已加入資料流程。</span><span class="sxs-lookup"><span data-stu-id="5348e-111">You should see the destination and connection managers added to the data flow.</span></span>  
  
6.  <span data-ttu-id="5348e-112">如果按一下 **\<New>** 來建立新的連線管理員，則應會顯示 [連線管理員] 對話方塊，其可供指定連線參數。</span><span class="sxs-lookup"><span data-stu-id="5348e-112">If you click **\<New>** to create a new connection manager, you should see a **Connection Manager** dialog box, which lets you specify parameters for the connection.</span></span> <span data-ttu-id="5348e-113">完成建立新的連接管理員之後，您會在 SSIS 設計師中看到目的地和連接管理員。</span><span class="sxs-lookup"><span data-stu-id="5348e-113">After you are done with creating the new connection manager, you will see the destination and the connection manager in SSIS Designer.</span></span>  
  
  
