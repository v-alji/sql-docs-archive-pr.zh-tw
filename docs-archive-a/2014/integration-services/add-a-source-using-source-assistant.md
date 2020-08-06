---
title: 使用來源助理新增來源 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 5e850b7c-4b89-42ad-b0a6-d63ac7cc9568
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1b58b10508765580e0cffe9bd62099f3e2d69863
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595263"
---
# <a name="add-a-source-using-source-assistant"></a><span data-ttu-id="c9b1b-102">使用來源小幫手加入來源</span><span class="sxs-lookup"><span data-stu-id="c9b1b-102">Add a Source using Source Assistant</span></span>
  <span data-ttu-id="c9b1b-103">本主題提供使用來源小幫手加入新來源的步驟，也會列出可以在 [加入新來源]\*\*\*\* 對話方塊上使用的選項。當您將來源小幫手拖放至 SSIS 設計師，即會顯示此對話方塊。</span><span class="sxs-lookup"><span data-stu-id="c9b1b-103">This topic provides steps to add a new source using the Source Assistant and also lists the options that are available on the **Add New Source** dialog, which you will see when you drag-drop the Source Assistant to the SSIS Designer.</span></span>  
  
### <a name="to-use-source-assistant-to-add-a-source"></a><span data-ttu-id="c9b1b-104">使用來源小幫手加入來源</span><span class="sxs-lookup"><span data-stu-id="c9b1b-104">To use Source Assistant to add a source</span></span>  
  
1.  <span data-ttu-id="c9b1b-105">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 中，開啟要加入來源元件的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 封裝。</span><span class="sxs-lookup"><span data-stu-id="c9b1b-105">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package that you want to add a source component to.</span></span>  
  
2.  <span data-ttu-id="c9b1b-106">將 [來源小幫手]  元件從 SSIS 工具箱拖曳至 [資料流程]  索引標籤。[加入新來源]  對話方塊應會隨即出現。</span><span class="sxs-lookup"><span data-stu-id="c9b1b-106">Drag the **Source Assistant** component from the SSIS Toolbox to the **Data Flow** tab. You should see the **Add New Source** dialog box.</span></span> <span data-ttu-id="c9b1b-107">下一節提供可以在對話方塊中使用之選項的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="c9b1b-107">The next section provides you details about the options available in the dialog box.</span></span>  
  
3.  <span data-ttu-id="c9b1b-108">在 [類型]  清單中選取目的地的類型。</span><span class="sxs-lookup"><span data-stu-id="c9b1b-108">Select the type of the destination in the **Types** list.</span></span>  
  
4.  <span data-ttu-id="c9b1b-109">在 [連線管理員] 清單中選取現有的連線管理員，或選取 **\<New>** ，以建立新的連線管理員。</span><span class="sxs-lookup"><span data-stu-id="c9b1b-109">Select an existing connection manager in the **Connection Managers** list or select **\<New>** to create a new connection manager.</span></span>  
  
5.  <span data-ttu-id="c9b1b-110">如果您選取現有的連線管理員，請按一下 [確定]  ，以關閉 [加入新目的地]  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="c9b1b-110">If you select an existing connection manager, click **OK** to close the **Add New Destination** dialog box.</span></span> <span data-ttu-id="c9b1b-111">您應該會看到目的地和連線管理員已加入資料流程。</span><span class="sxs-lookup"><span data-stu-id="c9b1b-111">You should see the destination and connection managers added to the data flow.</span></span>  
  
6.  <span data-ttu-id="c9b1b-112">如果按一下 **\<New>** 來建立新的連線管理員，則應會顯示 [連線管理員] 對話方塊，其可供指定連線參數。</span><span class="sxs-lookup"><span data-stu-id="c9b1b-112">If you click **\<New>** to create a new connection manager, you should see a **Connection Manager** dialog box, which lets you specify parameters for the connection.</span></span> <span data-ttu-id="c9b1b-113">完成建立新的連接管理員之後，您會在 SSIS 設計師中看到目的地和連接管理員。</span><span class="sxs-lookup"><span data-stu-id="c9b1b-113">After you are done with creating the new connection manager, you will see the destination and the connection manager in SSIS Designer.</span></span>  
  
  
