---
title: 複製資料行轉換編輯器 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.copymaptransformation.f1
helpviewer_keywords:
- Copy Column Transformation Editor
ms.assetid: d8e70541-d563-4ce4-bf66-bc888a0d3026
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7647d25891b37e5f09356d427072e84b45882e4c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596838"
---
# <a name="copy-column-transformation-editor"></a><span data-ttu-id="7066d-102">複製資料行轉換編輯器</span><span class="sxs-lookup"><span data-stu-id="7066d-102">Copy Column Transformation Editor</span></span>
  <span data-ttu-id="7066d-103">使用 **[複製資料行轉換編輯器]** 對話方塊，即可選取要複製的資料行，並為新的輸出資料行指派名稱。</span><span class="sxs-lookup"><span data-stu-id="7066d-103">Use the **Copy Column Transformation Editor** dialog box to select columns to copy and to assign names for the new output columns.</span></span>  
  
 <span data-ttu-id="7066d-104">若要深入了解複製資料行轉換，請參閱＜ [Copy Column Transformation](data-flow/transformations/copy-column-transformation.md)＞。</span><span class="sxs-lookup"><span data-stu-id="7066d-104">To learn more about the Copy Column transformation, see [Copy Column Transformation](data-flow/transformations/copy-column-transformation.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7066d-105">如果只是將所有的來源資料複製到目的地時，就可能不需要使用複製資料行轉換。</span><span class="sxs-lookup"><span data-stu-id="7066d-105">When you are simply copying all of your source data to a destination, it may not be necessary to use the Copy Column transformation.</span></span> <span data-ttu-id="7066d-106">在某些不需要進行資料轉換的狀況下，可以將來源直接連接到目的地。</span><span class="sxs-lookup"><span data-stu-id="7066d-106">In some scenarios, you can connect a source directly to a destination, when no data transformation is required.</span></span> <span data-ttu-id="7066d-107">在這些狀況下，最好使用「SQL Server 匯入和匯出精靈」為您建立封裝。</span><span class="sxs-lookup"><span data-stu-id="7066d-107">In these circumstances it is often preferable to use the SQL Server Import and Export Wizard to create your package for you.</span></span> <span data-ttu-id="7066d-108">稍後可依需要來增強和重新設定封裝。</span><span class="sxs-lookup"><span data-stu-id="7066d-108">Later you can enhance and reconfigure the package as needed.</span></span> <span data-ttu-id="7066d-109">如需詳細資訊，請參閱＜ [SQL Server Import and Export Wizard](import-export-data/import-and-export-data-with-the-sql-server-import-and-export-wizard.md)＞。</span><span class="sxs-lookup"><span data-stu-id="7066d-109">For more information, see [SQL Server Import and Export Wizard](import-export-data/import-and-export-data-with-the-sql-server-import-and-export-wizard.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="7066d-110">選項。</span><span class="sxs-lookup"><span data-stu-id="7066d-110">Options</span></span>  
 <span data-ttu-id="7066d-111">**可用的輸入資料行**</span><span class="sxs-lookup"><span data-stu-id="7066d-111">**Available Input Columns**</span></span>  
 <span data-ttu-id="7066d-112">使用核取方塊來選取要複製的資料行。</span><span class="sxs-lookup"><span data-stu-id="7066d-112">Select columns to copy by using the check boxes.</span></span> <span data-ttu-id="7066d-113">您的選取範圍會將輸入資料行加入下列資料表中。</span><span class="sxs-lookup"><span data-stu-id="7066d-113">Your selections add input columns to the table below.</span></span>  
  
 <span data-ttu-id="7066d-114">**輸入資料行**</span><span class="sxs-lookup"><span data-stu-id="7066d-114">**Input Column**</span></span>  
 <span data-ttu-id="7066d-115">從可用輸入資料行的清單中選取要複製的資料行。</span><span class="sxs-lookup"><span data-stu-id="7066d-115">Select columns to copy from the list of available input columns.</span></span> <span data-ttu-id="7066d-116">您的選擇會反映在 **[可用的輸入資料行]** 資料表的核取方塊選擇中。</span><span class="sxs-lookup"><span data-stu-id="7066d-116">Your selections are reflected in the check box selections in the **Available Input Columns** table.</span></span>  
  
 <span data-ttu-id="7066d-117">**輸出別名**</span><span class="sxs-lookup"><span data-stu-id="7066d-117">**Output Alias**</span></span>  
 <span data-ttu-id="7066d-118">輸入每個新輸出資料行的別名。</span><span class="sxs-lookup"><span data-stu-id="7066d-118">Type an alias for each new output column.</span></span> <span data-ttu-id="7066d-119">預設為 **[的副本]**，後面緊接著輸入資料行的名稱，但是您也可以選擇任何唯一的描述性名稱。</span><span class="sxs-lookup"><span data-stu-id="7066d-119">The default is **Copy of**, followed by the name of the input column; however, you can choose any unique, descriptive name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7066d-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7066d-120">See Also</span></span>  
 [<span data-ttu-id="7066d-121">Integration Services 錯誤和訊息參考</span><span class="sxs-lookup"><span data-stu-id="7066d-121">Integration Services Error and Message Reference</span></span>](../../2014/integration-services/integration-services-error-and-message-reference.md)  
  
  
