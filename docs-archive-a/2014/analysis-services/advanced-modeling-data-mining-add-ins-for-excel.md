---
title: 適用于 Excel) 的 Advanced 模型 (資料採礦增益集 |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining structures, creating
ms.assetid: 042270a3-6ec7-4b52-b2ba-2adb6c4740d5
author: minewiskan
ms.author: owend
ms.openlocfilehash: 771eb6111765b558995ee3b0eb98196c63951567
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593239"
---
# <a name="advanced-modeling-data-mining-add-ins-for-excel"></a><span data-ttu-id="80d04-102">進階模型 (適用於 Excel 的資料採礦增益集)</span><span class="sxs-lookup"><span data-stu-id="80d04-102">Advanced Modeling (Data Mining Add-ins for Excel)</span></span>
  <span data-ttu-id="80d04-103">您可以使用 [ **先進** 的資料模型化] 選項來建立自訂資料採礦結構和模型，其參數與嚮導所建立的參數不同。</span><span class="sxs-lookup"><span data-stu-id="80d04-103">You can use the **Advanced** data modeling options to create custom data mining structures and models with parameters different from those created by the wizards.</span></span> <span data-ttu-id="80d04-104">本章節描述的兩個精靈可幫助您建立全新的資料採礦結構，以及要套用到現有資料採礦結構的新採礦模型。</span><span class="sxs-lookup"><span data-stu-id="80d04-104">The two wizards described in this section help you create a completely new data mining structure, and a new mining model to apply to an existing data mining structure.</span></span>  
  
## <a name="create-mining-structure"></a><span data-ttu-id="80d04-105">建立採礦結構</span><span class="sxs-lookup"><span data-stu-id="80d04-105">Create Mining Structure</span></span>  
 <span data-ttu-id="80d04-106">![資料採礦功能區中的建立採礦結構按鈕](media/dmc-createstruct.gif "資料採礦功能區中的建立採礦結構按鈕")</span><span class="sxs-lookup"><span data-stu-id="80d04-106">![Create Mining Structure button, Data Mining ribbon](media/dmc-createstruct.gif "Create Mining Structure button, Data Mining ribbon")</span></span>  
  
 <span data-ttu-id="80d04-107">[ **建立採礦結構] Wizard** 可協助您建立新的資料採礦結構。</span><span class="sxs-lookup"><span data-stu-id="80d04-107">The **Create Mining Structure Wizard** helps you build a new data mining structure.</span></span> <span data-ttu-id="80d04-108">結構就是擷取自指定之資料來源的資料集合。</span><span class="sxs-lookup"><span data-stu-id="80d04-108">A structure is a collection of data extracted from a specified data source.</span></span>  <span data-ttu-id="80d04-109">採礦結構可以使用來源的新資料來更新，但是當您建立採礦結構時，就會定義資料類型和名稱，而這些資訊會定義資料用於分析的方式。</span><span class="sxs-lookup"><span data-stu-id="80d04-109">A mining structure can be updated with new data at the source, but when you create the mining structure, you define data types and names that define how the data is used for analysis.</span></span>  
  
 <span data-ttu-id="80d04-110">您可以使用下列資料來源來建立結構：Excel 資料表、Excel 範圍，或是外部資料來源中已經定義為 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 資料來源檢視的任何資料。</span><span class="sxs-lookup"><span data-stu-id="80d04-110">You can use the following data sources to build your structure: an Excel table, an Excel range, or any data in an external data source that has already been defined as an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] data source view.</span></span>  
  
 <span data-ttu-id="80d04-111">對於每一個結構而言，您可以選擇將某些資料擱在一邊，以便將這些資料用於測試和驗證。</span><span class="sxs-lookup"><span data-stu-id="80d04-111">For each structure, you have the option of setting aside some of the data to use for testing and validation.</span></span> <span data-ttu-id="80d04-112">藉由在設定資料來源時建立此 *維持資料集* ，您可以確保以結構為基礎的所有模型都可以使用一致的資料集進行測試。</span><span class="sxs-lookup"><span data-stu-id="80d04-112">By creating this *holdout data set* when you set up your data sources, you can ensure that all models that are based on the structure are able to use a consistent data set for testing.</span></span>  
  
 <span data-ttu-id="80d04-113">在建立採礦結構之後，您可以加入多個模型以套用不同的分析方法。</span><span class="sxs-lookup"><span data-stu-id="80d04-113">After you have created a mining structure, you can add multiple models to apply different methods of analysis.</span></span>  
  
 <span data-ttu-id="80d04-114">如需有關如何使用 [ **建立採礦結構] Wizard**的詳細資訊，請參閱 [&#40;SQL Server 資料採礦增益集建立採礦結構&#41;](create-mining-structure-sql-server-data-mining-add-ins.md)。</span><span class="sxs-lookup"><span data-stu-id="80d04-114">For more information about how to use the **Create Mining Structure Wizard**, see [Create Mining Structure &#40;SQL Server Data Mining Add-ins&#41;](create-mining-structure-sql-server-data-mining-add-ins.md).</span></span>  
  
## <a name="add-model-to-structure"></a><span data-ttu-id="80d04-115">將模型加入結構</span><span class="sxs-lookup"><span data-stu-id="80d04-115">Add Model to Structure</span></span>  
 <span data-ttu-id="80d04-116">![將模型加入到結構按鈕中](media/dmc-addmodel.gif "將模型加入到結構按鈕中")</span><span class="sxs-lookup"><span data-stu-id="80d04-116">![Add Model to Structure button](media/dmc-addmodel.gif "Add Model to Structure button")</span></span>  
  
 <span data-ttu-id="80d04-117">當您將新模型加入結構時，可使用不同演算法或不同參數來分析資料。</span><span class="sxs-lookup"><span data-stu-id="80d04-117">When you add a new model to a structure, you analyze the data by using a different algorithm, or with different parameters.</span></span> <span data-ttu-id="80d04-118">如果您想要使用資料採礦用戶端工具中未公開的其中一種演算法來建立模型，這個選項就特別有用。</span><span class="sxs-lookup"><span data-stu-id="80d04-118">This option is particularly useful if you want to create a model using one of the algorithms not exposed in the Data Mining Client tools.</span></span>  
  
 <span data-ttu-id="80d04-119">例如，您可以使用 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 支援的任何演算法，包括：</span><span class="sxs-lookup"><span data-stu-id="80d04-119">For example, you can use any of the algorithms supported by [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], such as:</span></span>  
  
-   <span data-ttu-id="80d04-120">線性迴歸</span><span class="sxs-lookup"><span data-stu-id="80d04-120">Linear regression</span></span>  
  
-   <span data-ttu-id="80d04-121">時序群集</span><span class="sxs-lookup"><span data-stu-id="80d04-121">Sequence clustering</span></span>  
  
-   <span data-ttu-id="80d04-122">巢狀資料集的關聯分析</span><span class="sxs-lookup"><span data-stu-id="80d04-122">Association analysis on nested data sets</span></span>  
  
 <span data-ttu-id="80d04-123">若要查看有何種可用的採礦結構，您可以 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 按一下 [ **管理模型** ] 或 **[流覽]** 來流覽中儲存的模型和結構。</span><span class="sxs-lookup"><span data-stu-id="80d04-123">To see what kind of mining structures are available, you can browse the models and structures stored in [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] by clicking either **Manage Models** or **Browse**.</span></span>  
  
 <span data-ttu-id="80d04-124">但是，僅限於在目前工作階段期間建立的資料採礦結構，或是已儲存至 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 執行個體的採礦結構。</span><span class="sxs-lookup"><span data-stu-id="80d04-124">You are limited to data mining structures that were created during the current session, or mining structures that were saved to an instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="80d04-125">如需詳細資訊，請參閱 [將模型加入結構 &#40;適用于 Excel 的資料採礦增益集&#41;](add-model-to-structure-data-mining-add-ins-for-excel.md)。</span><span class="sxs-lookup"><span data-stu-id="80d04-125">For more information, see [Add Model to Structure &#40;Data Mining Add-ins for Excel&#41;](add-model-to-structure-data-mining-add-ins-for-excel.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80d04-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="80d04-126">See Also</span></span>  
 <span data-ttu-id="80d04-127">[&#40;SQL Server 資料採礦增益集來管理模型&#41;](manage-models-sql-server-data-mining-add-ins.md) </span><span class="sxs-lookup"><span data-stu-id="80d04-127">[Manage Models &#40;SQL Server Data Mining Add-ins&#41;](manage-models-sql-server-data-mining-add-ins.md) </span></span>  
 [<span data-ttu-id="80d04-128">在 Excel 中流覽模型 &#40;SQL Server 資料採礦增益集&#41;</span><span class="sxs-lookup"><span data-stu-id="80d04-128">Browsing Models in Excel &#40;SQL Server Data Mining Add-ins&#41;</span></span>](browsing-models-in-excel-sql-server-data-mining-add-ins.md)  
  
  
