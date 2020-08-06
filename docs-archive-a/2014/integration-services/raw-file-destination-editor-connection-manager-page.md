---
title: 原始檔案目的地編輯器 (連線管理員頁面) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.rawfiledestinationconnectionmanager.f1
ms.assetid: a0ec9643-3b44-4467-b855-f45ae4794f7f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a693591921a5669eb9bc8160f0be076ab4d6869b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687994"
---
# <a name="raw-file-destination-editor-connection-manager-page"></a><span data-ttu-id="a656e-102">原始檔案目的地編輯器 (連接管理員頁面)</span><span class="sxs-lookup"><span data-stu-id="a656e-102">Raw File Destination Editor (Connection Manager Page)</span></span>
  <span data-ttu-id="a656e-103">使用原始檔案目的地編輯器設定原始檔案目的地將，以便將原始資料寫入至檔案。</span><span class="sxs-lookup"><span data-stu-id="a656e-103">Use the Raw File Destination Editor to configure the Raw File destination to write raw data to a file.</span></span>  
  
 <span data-ttu-id="a656e-104">**您想要做什麼事？**</span><span class="sxs-lookup"><span data-stu-id="a656e-104">**What do you want to do?**</span></span>  
  
-   [<span data-ttu-id="a656e-105">開啟原始檔案目的地編輯器</span><span class="sxs-lookup"><span data-stu-id="a656e-105">Open the Raw File Destination Editor</span></span>](#open)  
  
-   <span data-ttu-id="a656e-106">[設定 [連接管理員] 索引標籤上的選項](#connection)</span><span class="sxs-lookup"><span data-stu-id="a656e-106">[Set options on the Connection Manager tab](#connection)</span></span>  
  
-   [<span data-ttu-id="a656e-107">設定資料行索引標籤上的選項</span><span class="sxs-lookup"><span data-stu-id="a656e-107">Set options on the Columns tab</span></span>](#mapping)  
  
##  <a name="open-the-raw-file-destination-editor"></a><a name="open"></a> <span data-ttu-id="a656e-108">開啟原始檔案目的地編輯器</span><span class="sxs-lookup"><span data-stu-id="a656e-108">Open the Raw File Destination Editor</span></span>  
  
1.  <span data-ttu-id="a656e-109">將「原始檔案」目的地加入至 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 中的 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]封裝。</span><span class="sxs-lookup"><span data-stu-id="a656e-109">Add the Raw File destination to an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package, in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
2.  <span data-ttu-id="a656e-110">以滑鼠右鍵按一下此元件，然後按一下 **[編輯]**。</span><span class="sxs-lookup"><span data-stu-id="a656e-110">Right-click the component and then click **Edit**.</span></span>  
  
##  <a name="set-options-on-the-connection-manager-tab"></a><a name="connection"></a> <span data-ttu-id="a656e-111">設定連接管理員索引標籤上的選項</span><span class="sxs-lookup"><span data-stu-id="a656e-111">Set options on the Connection Manager tab</span></span>  
 <span data-ttu-id="a656e-112">**存取模式**</span><span class="sxs-lookup"><span data-stu-id="a656e-112">**Access mode**</span></span>  
 <span data-ttu-id="a656e-113">選取指定檔案名稱的方式。</span><span class="sxs-lookup"><span data-stu-id="a656e-113">Select how the file name is specified.</span></span> <span data-ttu-id="a656e-114">選取 **[檔案名稱]** 直接輸入檔案名稱和路徑，或是選取 **[來自變數的檔案名稱]** 指定包含檔案名稱的變數。</span><span class="sxs-lookup"><span data-stu-id="a656e-114">Select **File name** to enter the file name and path directly, of **File name from variable** to specify a variable that contains the file name.</span></span>  
  
 <span data-ttu-id="a656e-115">**[檔案名稱]** 或 **[變數名稱]**</span><span class="sxs-lookup"><span data-stu-id="a656e-115">**File name** or **Variable name**</span></span>  
 <span data-ttu-id="a656e-116">輸入原始檔案的名稱和路徑，或是選取包含檔案名稱的變數。</span><span class="sxs-lookup"><span data-stu-id="a656e-116">Enter the name and path of the raw file, or select the variable that contains the file name.</span></span>  
  
 <span data-ttu-id="a656e-117">**寫入選項**</span><span class="sxs-lookup"><span data-stu-id="a656e-117">**Write option**</span></span>  
 <span data-ttu-id="a656e-118">選取用來建立和寫入檔案的方法。</span><span class="sxs-lookup"><span data-stu-id="a656e-118">Select the method used to create and write to the file.</span></span>  
  
 <span data-ttu-id="a656e-119">**產生初始的原始檔案**</span><span class="sxs-lookup"><span data-stu-id="a656e-119">**Generate initial raw file**</span></span>  
 <span data-ttu-id="a656e-120">按一下此按鈕可以產生僅包含資料行 (僅中繼資料的檔案) 的空白原始檔案，而不必執行封裝。</span><span class="sxs-lookup"><span data-stu-id="a656e-120">Click the button to generate an empty raw file that contains only the columns (metadata-only file), without having to run the package.</span></span> <span data-ttu-id="a656e-121">此檔案包含您在 **[原始檔案目的地編輯器]** 之 **[資料行]** 頁面上選取的資料行。</span><span class="sxs-lookup"><span data-stu-id="a656e-121">The file contains the columns that you selected on the **Columns** page of the **Raw File Destination Editor**.</span></span> <span data-ttu-id="a656e-122">您可以將原始檔案來源指向這個僅中繼資料的檔案。</span><span class="sxs-lookup"><span data-stu-id="a656e-122">You can point the Raw File source to this metadata-only file.</span></span>  
  
 <span data-ttu-id="a656e-123">當您按一下 **[產生初始原始檔案]** 時，隨即顯示訊息方塊。</span><span class="sxs-lookup"><span data-stu-id="a656e-123">When you click **Generate initial raw file**, a message box appears.</span></span> <span data-ttu-id="a656e-124">按一下 **[確定]** ，繼續建立檔案。</span><span class="sxs-lookup"><span data-stu-id="a656e-124">Click **OK** to proceed with creating the file.</span></span> <span data-ttu-id="a656e-125">按一下 **[取消]** ，在 **[資料行]** 頁面上選取不同的資料行清單。</span><span class="sxs-lookup"><span data-stu-id="a656e-125">Click **Cancel** to select a different list of columns on the **Columns** page.</span></span>  
  
##  <a name="set-options-on-the-columns-tab"></a><a name="mapping"></a><span data-ttu-id="a656e-126">在 [資料行] 索引標籤上設定選項</span><span class="sxs-lookup"><span data-stu-id="a656e-126">Set options on the Columns tab</span></span>  
 <span data-ttu-id="a656e-127">**可用的輸入資料行**</span><span class="sxs-lookup"><span data-stu-id="a656e-127">**Available Input Columns**</span></span>  
 <span data-ttu-id="a656e-128">選取要寫入至原始檔案的一個或多個輸入資料行。</span><span class="sxs-lookup"><span data-stu-id="a656e-128">Select one or more input columns to write to the raw file.</span></span>  
  
 <span data-ttu-id="a656e-129">**輸入資料行**</span><span class="sxs-lookup"><span data-stu-id="a656e-129">**Input Column**</span></span>  
 <span data-ttu-id="a656e-130">當您在 **[可用的輸入資料行]** 底下選取資料表時，輸入資料行會自動加入此資料表中，或者您可以直接在此資料表中選取輸入資料行。</span><span class="sxs-lookup"><span data-stu-id="a656e-130">An input column is automatically added to this table when you select it under **Available Input Columns**, or you can select the input column directly in this table.</span></span>  
  
 <span data-ttu-id="a656e-131">**輸出別名**</span><span class="sxs-lookup"><span data-stu-id="a656e-131">**Output Alias**</span></span>  
 <span data-ttu-id="a656e-132">指定要做為輸出資料行使用的替代名稱。</span><span class="sxs-lookup"><span data-stu-id="a656e-132">Specify an alternate name to use for the output column.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a656e-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a656e-133">See Also</span></span>  
 [<span data-ttu-id="a656e-134">原始檔案目的地</span><span class="sxs-lookup"><span data-stu-id="a656e-134">Raw File Destination</span></span>](data-flow/raw-file-destination.md)  
  
  
