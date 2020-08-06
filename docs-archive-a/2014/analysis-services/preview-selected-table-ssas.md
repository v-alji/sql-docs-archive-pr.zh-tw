---
title: 預覽選取的資料表 (SSAS) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.previewselecttable.f1
ms.assetid: b6b34b5a-43b3-4a75-9f3b-b2ad1084b1b6
author: minewiskan
ms.author: owend
ms.openlocfilehash: 25eb4d4424223449052ab1f65b41cf270da81fb0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708737"
---
# <a name="preview-selected-table-ssas"></a><span data-ttu-id="b47cd-102">預覽選取的資料表 (SSAS)</span><span class="sxs-lookup"><span data-stu-id="b47cd-102">Preview Selected Table (SSAS)</span></span>
  <span data-ttu-id="b47cd-103">**[資料表匯入精靈]** 的這個頁面可讓您預覽選定資料表中的資料、選取要併入資料匯入的資料行，以及在選取的資料行中篩選資料。</span><span class="sxs-lookup"><span data-stu-id="b47cd-103">This page of the **Table Import Wizard** enables you to preview the data in the selected table, to select the columns to include in the data import, and to filter data in the selected columns.</span></span> <span data-ttu-id="b47cd-104">若要從 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]存取精靈，請按一下 **[模型]** 功能表上的 **[從資料來源匯入]**。</span><span class="sxs-lookup"><span data-stu-id="b47cd-104">To access the wizard from the [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], on the **Model** menu, click **Import from Data Source**.</span></span>  
  
 <span data-ttu-id="b47cd-105">並非資料表中的所有資料列都會顯示。</span><span class="sxs-lookup"><span data-stu-id="b47cd-105">Not all the rows in the table are displayed.</span></span> <span data-ttu-id="b47cd-106">但是，您設定的篩選將會在匯入期間套用至資料表中的所有資料。</span><span class="sxs-lookup"><span data-stu-id="b47cd-106">However, the filters that you set will be applied to all of the data in the table during import.</span></span>  
  
 <span data-ttu-id="b47cd-107">針對使用 Windows 驗證的資料來源，目前使用者的認證會用來提取顯示在 [預覽和篩選] 對話方塊中的資料。</span><span class="sxs-lookup"><span data-stu-id="b47cd-107">For data sources using Windows authentication, the credentials of the current user are used to fetch the data displayed in the Preview and Filter dialog.</span></span> <span data-ttu-id="b47cd-108">至於其他資料來源，連接字串中提供的認證則用來提取資料。</span><span class="sxs-lookup"><span data-stu-id="b47cd-108">For other data sources, the credentials supplied in the connection string are used to fetch the data.</span></span>  
  
 <span data-ttu-id="b47cd-109">此頁面之資料的外觀不保證匯入將會成功。</span><span class="sxs-lookup"><span data-stu-id="b47cd-109">The appearance of data on this page does not guarantee import will succeed.</span></span> <span data-ttu-id="b47cd-110">如果在 [模擬資訊] 頁面中指定的使用者名稱未具備從所選資料庫讀取的權限，則匯入將會失敗。</span><span class="sxs-lookup"><span data-stu-id="b47cd-110">If the user name specified in the Impersonation Information page does not have sufficient privileges to read from the selected database, import will fail.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="b47cd-111">UI 元素清單</span><span class="sxs-lookup"><span data-stu-id="b47cd-111">UI element list</span></span>  
 <span data-ttu-id="b47cd-112">**資料行標頭中的核取方塊**</span><span class="sxs-lookup"><span data-stu-id="b47cd-112">**Checkbox in the column header**</span></span>  
 <span data-ttu-id="b47cd-113">選取核取方塊可將資料行納入資料匯入作業。</span><span class="sxs-lookup"><span data-stu-id="b47cd-113">Select the checkbox to include the column in the data import.</span></span> <span data-ttu-id="b47cd-114">清除核取方塊可從資料匯入作業排除資料行。</span><span class="sxs-lookup"><span data-stu-id="b47cd-114">Clear the checkbox to remove the column from the data import.</span></span>  
  
 <span data-ttu-id="b47cd-115">**資料行標頭中的向下箭號按鈕**</span><span class="sxs-lookup"><span data-stu-id="b47cd-115">**Down-arrow button in the column header**</span></span>  
 <span data-ttu-id="b47cd-116">篩選資料行中的資料。</span><span class="sxs-lookup"><span data-stu-id="b47cd-116">Filter data in the column.</span></span>  
  
 <span data-ttu-id="b47cd-117">**清除資料列篩選**</span><span class="sxs-lookup"><span data-stu-id="b47cd-117">**Clear Row Filters**</span></span>  
 <span data-ttu-id="b47cd-118">移除已經套用到資料行中資料的所有篩選。</span><span class="sxs-lookup"><span data-stu-id="b47cd-118">Remove all filters that were applied to the data in the columns.</span></span>  
  
  
