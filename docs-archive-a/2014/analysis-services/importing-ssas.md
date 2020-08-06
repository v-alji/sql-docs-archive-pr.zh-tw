---
title: 匯入 (SSAS) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.importing.f1
ms.assetid: f1681be4-c543-4e77-875d-b13eeb75cf77
author: minewiskan
ms.author: owend
ms.openlocfilehash: 95ea60385014e5ca8b998b986a66c384f7151081
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87605922"
---
# <a name="importing-ssas"></a><span data-ttu-id="3c218-102">匯入 (SSAS)</span><span class="sxs-lookup"><span data-stu-id="3c218-102">Importing (SSAS)</span></span>
  <span data-ttu-id="3c218-103">[資料表匯入精靈]\*\*\*\* 的這個頁面可讓您檢視匯入作業的進度。</span><span class="sxs-lookup"><span data-stu-id="3c218-103">This page of the **Table Import Wizard** enables you to view the progress of the import operation.</span></span> <span data-ttu-id="3c218-104">若要從 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]存取精靈，請按一下 **[模型]** 功能表上的 **[從資料來源匯入]**。</span><span class="sxs-lookup"><span data-stu-id="3c218-104">To access the wizard from the [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], on the **Model** menu, click **Import from Data Source**.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="3c218-105">UI 元素清單</span><span class="sxs-lookup"><span data-stu-id="3c218-105">UI element list</span></span>  
 <span data-ttu-id="3c218-106">**詳細資料**</span><span class="sxs-lookup"><span data-stu-id="3c218-106">**Details**</span></span>  
 <span data-ttu-id="3c218-107">針對每一個資料匯入作業顯示以下資訊。</span><span class="sxs-lookup"><span data-stu-id="3c218-107">Displays the following information for each data import operation.</span></span>  
  
|<span data-ttu-id="3c218-108">資料行</span><span class="sxs-lookup"><span data-stu-id="3c218-108">Column</span></span>|<span data-ttu-id="3c218-109">描述</span><span class="sxs-lookup"><span data-stu-id="3c218-109">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="3c218-110">**工作專案**</span><span class="sxs-lookup"><span data-stu-id="3c218-110">**Work Item**</span></span>|<span data-ttu-id="3c218-111">顯示正在匯入之資料表或檢視表的名稱。</span><span class="sxs-lookup"><span data-stu-id="3c218-111">Displays the name of the table or view that is being imported.</span></span>|  
|<span data-ttu-id="3c218-112">**狀態**</span><span class="sxs-lookup"><span data-stu-id="3c218-112">**Status**</span></span>|<span data-ttu-id="3c218-113">指出是否已成功匯入資料表或檢視表以及匯入的資料列數目。</span><span class="sxs-lookup"><span data-stu-id="3c218-113">Indicates whether the table or view was successfully imported and the number of rows that were imported.</span></span>|  
|<span data-ttu-id="3c218-114">**Message**</span><span class="sxs-lookup"><span data-stu-id="3c218-114">**Message**</span></span>|<span data-ttu-id="3c218-115">如果資料表或檢視表匯入失敗，則會顯示詳細資訊的連結。</span><span class="sxs-lookup"><span data-stu-id="3c218-115">If the table or view import failed, displays a link to more information.</span></span> <span data-ttu-id="3c218-116">這項資訊會在 [詳細資料] 視窗中顯示。</span><span class="sxs-lookup"><span data-stu-id="3c218-116">This information is displayed in the Details window.</span></span><br /><br /> <span data-ttu-id="3c218-117">若要嘗試重新匯入資料表或檢視表，請結束精靈，然後重新執行。</span><span class="sxs-lookup"><span data-stu-id="3c218-117">To try again to import the table or view, exit the wizard and run it again.</span></span>|  
  
 <span data-ttu-id="3c218-118">**停止匯入**</span><span class="sxs-lookup"><span data-stu-id="3c218-118">**Stop Import**</span></span>  
 <span data-ttu-id="3c218-119">按一下即可在完成前停止匯入作業。</span><span class="sxs-lookup"><span data-stu-id="3c218-119">Click to stop the import operation before it is finished.</span></span> <span data-ttu-id="3c218-120">已匯入的資料表和檢視都會出現在 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] 設計工具中。</span><span class="sxs-lookup"><span data-stu-id="3c218-120">Tables and views that have already been imported will be displayed in the [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] designer.</span></span> <span data-ttu-id="3c218-121">尚未匯入的資料表與檢視則不會匯入。</span><span class="sxs-lookup"><span data-stu-id="3c218-121">Tables and views that have not been imported yet will not be imported.</span></span>  
  
  
