---
title: 原始檔案目的地編輯器 (資料行頁面) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.rawfiledestinationcolumns.f1
ms.assetid: 37f61d0b-1269-42ee-94ab-011cbaac63e9
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8a89d8ca46805a23fd03465ed40428081499dccb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687997"
---
# <a name="raw-file-destination-editor-columns-page"></a><span data-ttu-id="5aa38-102">原始檔案目的地編輯器 (資料行頁面)</span><span class="sxs-lookup"><span data-stu-id="5aa38-102">Raw File Destination Editor (Columns Page)</span></span>
  <span data-ttu-id="5aa38-103">使用原始檔案目的地編輯器設定原始檔案目的地將，以便將原始資料寫入至檔案。</span><span class="sxs-lookup"><span data-stu-id="5aa38-103">Use the Raw File Destination Editor to configure the Raw File destination to write raw data to a file.</span></span>  
  
 <span data-ttu-id="5aa38-104">**您想要做什麼事？**</span><span class="sxs-lookup"><span data-stu-id="5aa38-104">**What do you want to do?**</span></span>  
  
-   [<span data-ttu-id="5aa38-105">開啟原始檔案目的地編輯器</span><span class="sxs-lookup"><span data-stu-id="5aa38-105">Open the Raw File Destination Editor</span></span>](#open)  
  
-   <span data-ttu-id="5aa38-106">[設定 [連接管理員] 索引標籤上的選項](#connection)</span><span class="sxs-lookup"><span data-stu-id="5aa38-106">[Set options on the Connection Manager tab](#connection)</span></span>  
  
-   [<span data-ttu-id="5aa38-107">設定資料行索引標籤上的選項</span><span class="sxs-lookup"><span data-stu-id="5aa38-107">Set options on the Columns tab</span></span>](#mapping)  
  
##  <a name="open-the-raw-file-destination-editor"></a><a name="open"></a> <span data-ttu-id="5aa38-108">開啟原始檔案目的地編輯器</span><span class="sxs-lookup"><span data-stu-id="5aa38-108">Open the Raw File Destination Editor</span></span>  
  
1.  <span data-ttu-id="5aa38-109">將「原始檔案」目的地加入至 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 中的 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]封裝。</span><span class="sxs-lookup"><span data-stu-id="5aa38-109">Add the Raw File destination to an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package, in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
2.  <span data-ttu-id="5aa38-110">以滑鼠右鍵按一下此元件，然後按一下 **[編輯]**。</span><span class="sxs-lookup"><span data-stu-id="5aa38-110">Right-click the component and then click **Edit**.</span></span>  
  
##  <a name="set-options-on-the-connection-manager-tab"></a><a name="connection"></a> <span data-ttu-id="5aa38-111">設定連接管理員索引標籤上的選項</span><span class="sxs-lookup"><span data-stu-id="5aa38-111">Set options on the Connection Manager tab</span></span>  
 <span data-ttu-id="5aa38-112">**存取模式**</span><span class="sxs-lookup"><span data-stu-id="5aa38-112">**Access mode**</span></span>  
 <span data-ttu-id="5aa38-113">選取指定檔案名稱的方式。</span><span class="sxs-lookup"><span data-stu-id="5aa38-113">Select how the file name is specified.</span></span> <span data-ttu-id="5aa38-114">選取 **[檔案名稱]** 直接輸入檔案名稱和路徑，或是選取 **[來自變數的檔案名稱]** 指定包含檔案名稱的變數。</span><span class="sxs-lookup"><span data-stu-id="5aa38-114">Select **File name** to enter the file name and path directly, of **File name from variable** to specify a variable that contains the file name.</span></span>  
  
 <span data-ttu-id="5aa38-115">**[檔案名稱]** 或 **[變數名稱]**</span><span class="sxs-lookup"><span data-stu-id="5aa38-115">**File name** or **Variable name**</span></span>  
 <span data-ttu-id="5aa38-116">輸入原始檔案的名稱和路徑，或是選取包含檔案名稱的變數。</span><span class="sxs-lookup"><span data-stu-id="5aa38-116">Enter the name and path of the raw file, or select the variable that contains the file name.</span></span>  
  
 <span data-ttu-id="5aa38-117">**寫入選項**</span><span class="sxs-lookup"><span data-stu-id="5aa38-117">**Write option**</span></span>  
 <span data-ttu-id="5aa38-118">選取用來建立和寫入檔案的方法。</span><span class="sxs-lookup"><span data-stu-id="5aa38-118">Select the method used to create and write to the file.</span></span>  
  
 <span data-ttu-id="5aa38-119">**產生初始的原始檔案**</span><span class="sxs-lookup"><span data-stu-id="5aa38-119">**Generate initial raw file**</span></span>  
 <span data-ttu-id="5aa38-120">按一下此按鈕可以產生僅包含資料行 (僅中繼資料的檔案) 的空白原始檔案，而不必執行封裝。</span><span class="sxs-lookup"><span data-stu-id="5aa38-120">Click the button to generate an empty raw file that contains only the columns (metadata-only file), without having to run the package.</span></span> <span data-ttu-id="5aa38-121">您可以將原始檔案來源指向僅中繼資料的檔案。</span><span class="sxs-lookup"><span data-stu-id="5aa38-121">You can point the Raw File source to the metadata-only file.</span></span>  
  
 <span data-ttu-id="5aa38-122">當您按一下該按鈕時，資料行的清單便會出現。</span><span class="sxs-lookup"><span data-stu-id="5aa38-122">When you click the button, a list of the columns appears.</span></span> <span data-ttu-id="5aa38-123">您可以按一下 [取消]，然後修改資料行，或按一下 [確定]，以繼續建立該檔案。</span><span class="sxs-lookup"><span data-stu-id="5aa38-123">You can click cancel and modify the columns or click OK to proceed with creating the file.</span></span>  
  
##  <a name="set-options-on-the-columns-tab"></a><a name="mapping"></a><span data-ttu-id="5aa38-124">在 [資料行] 索引標籤上設定選項</span><span class="sxs-lookup"><span data-stu-id="5aa38-124">Set options on the Columns tab</span></span>  
 <span data-ttu-id="5aa38-125">**可用的輸入資料行**</span><span class="sxs-lookup"><span data-stu-id="5aa38-125">**Available Input Columns**</span></span>  
 <span data-ttu-id="5aa38-126">選取要寫入至原始檔案的一個或多個輸入資料行。</span><span class="sxs-lookup"><span data-stu-id="5aa38-126">Select one or more input columns to write to the raw file.</span></span>  
  
 <span data-ttu-id="5aa38-127">**輸入資料行**</span><span class="sxs-lookup"><span data-stu-id="5aa38-127">**Input Column**</span></span>  
 <span data-ttu-id="5aa38-128">當您在 **[可用的輸入資料行]** 底下選取資料表時，輸入資料行會自動加入此資料表中，或者您可以直接在此資料表中選取輸入資料行。</span><span class="sxs-lookup"><span data-stu-id="5aa38-128">An input column is automatically added to this table when you select it under **Available Input Columns**, or you can select the input column directly in this table.</span></span>  
  
 <span data-ttu-id="5aa38-129">**輸出別名**</span><span class="sxs-lookup"><span data-stu-id="5aa38-129">**Output Alias**</span></span>  
 <span data-ttu-id="5aa38-130">指定要做為輸出資料行使用的替代名稱。</span><span class="sxs-lookup"><span data-stu-id="5aa38-130">Specify an alternate name to use for the output column.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5aa38-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5aa38-131">See Also</span></span>  
 [<span data-ttu-id="5aa38-132">原始檔案目的地</span><span class="sxs-lookup"><span data-stu-id="5aa38-132">Raw File Destination</span></span>](data-flow/raw-file-destination.md)  
  
  
