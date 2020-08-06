---
title: 步驟 5：加入和設定一般檔案來源 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 5c95ce51-e0fe-4fc5-95eb-2945929f2b13
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 504cfb4bc722627eb8ee70ec1f2c562cef8f1f0f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596130"
---
# <a name="step-5-adding-and-configuring-the-flat-file-source"></a><span data-ttu-id="902bb-102">步驟 5：新增和設定一般檔案來源</span><span class="sxs-lookup"><span data-stu-id="902bb-102">Step 5: Adding and Configuring the Flat File Source</span></span>
  <span data-ttu-id="902bb-103">在這項工作中，您會在封裝中加入和設定一般檔案來源。</span><span class="sxs-lookup"><span data-stu-id="902bb-103">In this task, you will add and configure a Flat File source to your package.</span></span> <span data-ttu-id="902bb-104">一般檔案來源是一個資料流程元件，它使用一般檔案連接管理員所定義的中繼資料，來指定轉換處理序要從一般檔案擷取之資料的格式和結構。</span><span class="sxs-lookup"><span data-stu-id="902bb-104">A Flat File source is a data flow component that uses metadata defined by a Flat File connection manager to specify the format and structure of the data to be extracted from the flat file by a transform process.</span></span> <span data-ttu-id="902bb-105">一般檔案來源可設定為使用一般檔案連接管理員提供的檔案格式定義，從單個一般檔案擷取資料。</span><span class="sxs-lookup"><span data-stu-id="902bb-105">The Flat File source can be configured to extract data from a single flat file by using the file format definition provided by the Flat File connection manager.</span></span>  
  
 <span data-ttu-id="902bb-106">在本教學課程中，您會將一般檔案來源設定為使用 `Sample Flat File Source Data` 您先前建立的連接管理員。</span><span class="sxs-lookup"><span data-stu-id="902bb-106">For this tutorial, you will configure the Flat File source to use the `Sample Flat File Source Data` connection manager that you previously created.</span></span>  
  
### <a name="to-add-a-flat-file-source-component"></a><span data-ttu-id="902bb-107">若要加入一般檔案來源元件</span><span class="sxs-lookup"><span data-stu-id="902bb-107">To add a Flat File Source component</span></span>  
  
1.  <span data-ttu-id="902bb-108">按兩下 [**資料流程**] 工作， `Extract Sample Currency Data` 或按一下 [**資料流程]** 索引標籤，以開啟 [資料流程設計師]。</span><span class="sxs-lookup"><span data-stu-id="902bb-108">Open the **Data Flow** designer, either by double-clicking the `Extract Sample Currency Data` data flow task or by clicking the **Data Flow tab**.</span></span>  
  
2.  <span data-ttu-id="902bb-109">在 [SSIS 工具箱]\*\*\*\* 中，展開 [其他來源]\*\*\*\*，然後將 [一般檔案來源]\*\*\*\* 拖曳至 [資料流程]\*\*\*\* 索引標籤的設計介面中。</span><span class="sxs-lookup"><span data-stu-id="902bb-109">In the **SSIS Toolbox**, expand **OtherSources**, and then drag a **Flat File Source** onto the design surface of the **Data Flow** tab.</span></span>  
  
3.  <span data-ttu-id="902bb-110">在 [**資料流程] 設計介面**上，以滑鼠右鍵按一下新加入的 [一般檔案**來源**]，按一下 [**重新命名**]，然後將名稱變更為 `Extract Sample Currency Data` 。</span><span class="sxs-lookup"><span data-stu-id="902bb-110">On the **Data Flow** design surface, right-click the newly added **Flat File Source**, click **Rename**, and change the name to `Extract Sample Currency Data`.</span></span>  
  
4.  <span data-ttu-id="902bb-111">按兩下一般檔案來源，來開啟 [一般檔案來源編輯器] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="902bb-111">Double-click the Flat File source to open the Flat File Source Editor dialog box.</span></span>  
  
5.  <span data-ttu-id="902bb-112">在 [一般檔案**連接管理員**] 方塊中，選取 [] `Sample Flat File Source Data` 。</span><span class="sxs-lookup"><span data-stu-id="902bb-112">In the **Flat file connection manager** box, select `Sample Flat File Source Data`.</span></span>  
  
6.  <span data-ttu-id="902bb-113">按一下 **[資料行]** 並確認資料行的名稱正確無誤。</span><span class="sxs-lookup"><span data-stu-id="902bb-113">Click **Columns** and verify that the names of the columns are correct.</span></span>  
  
7.  <span data-ttu-id="902bb-114">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="902bb-114">Click **OK**.</span></span>  
  
8.  <span data-ttu-id="902bb-115">以滑鼠右鍵按一下一般檔案來源，然後按一下 **[屬性]**。</span><span class="sxs-lookup"><span data-stu-id="902bb-115">Right-click the Flat File source and click **Properties**.</span></span>  
  
9. <span data-ttu-id="902bb-116">在 [屬性視窗中，確認 `LocaleID` 屬性已設為 [\*\*英文] ([美國]) \*\*。</span><span class="sxs-lookup"><span data-stu-id="902bb-116">In the Properties window, verify that the `LocaleID` property is set to **English (United States)**.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="902bb-117">本課程的下一項工作</span><span class="sxs-lookup"><span data-stu-id="902bb-117">Next Task in Lesson</span></span>  
 [<span data-ttu-id="902bb-118">步驟 6：新增和設定查閱轉換</span><span class="sxs-lookup"><span data-stu-id="902bb-118">Step 6: Adding and Configuring the Lookup Transformations</span></span>](lesson-1-6-adding-and-configuring-the-lookup-transformations.md)  
  
## <a name="see-also"></a><span data-ttu-id="902bb-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="902bb-119">See Also</span></span>  
 <span data-ttu-id="902bb-120">[一般檔案來源](data-flow/flat-file-source.md) </span><span class="sxs-lookup"><span data-stu-id="902bb-120">[Flat File Source](data-flow/flat-file-source.md) </span></span>  
 [<span data-ttu-id="902bb-121">一般檔案連線管理員編輯器 &#40;一般頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="902bb-121">Flat File Connection Manager Editor &#40;General Page&#41;</span></span>](general-page-of-integration-services-designers-options.md)  
  
  
