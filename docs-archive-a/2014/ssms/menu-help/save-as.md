---
title: 另存新檔 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vs.saveas
helpviewer_keywords:
- Save As dialog box
ms.assetid: 61347757-f5a3-481d-8b05-1fed086629b6
author: stevestein
ms.author: sstein
ms.openlocfilehash: e47d9c37371283fc6fba2754896d77b51d26cef0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607202"
---
# <a name="save-as"></a><span data-ttu-id="223e1-102">另存新檔</span><span class="sxs-lookup"><span data-stu-id="223e1-102">Save As</span></span>
  <span data-ttu-id="223e1-103">使用此對話方塊，即可以指定的檔案格式將目前項目的執行個體儲存在指定的位置。</span><span class="sxs-lookup"><span data-stu-id="223e1-103">Use this dialog box to save an instance of the current item at a specified location in a specified file format.</span></span> <span data-ttu-id="223e1-104">若要顯示此對話方塊，請按一下 [檔案] 功能表上的 [**另存** *\<file>* **As**新檔] (其中**File** *\<file>* 是目前專案的名稱) ，或是在程式碼編輯器中按下 ALT + F。</span><span class="sxs-lookup"><span data-stu-id="223e1-104">To display this dialog box, click **Save** *\<file>* **As** on the **File** menu (where *\<file>* is the name of the current item), or press ALT+F, A in the Code Editor.</span></span>  
  
## <a name="central-panel"></a><span data-ttu-id="223e1-105">中央面板</span><span class="sxs-lookup"><span data-stu-id="223e1-105">Central Panel</span></span>  
 <span data-ttu-id="223e1-106">**儲存於**</span><span class="sxs-lookup"><span data-stu-id="223e1-106">**Save in**</span></span>  
 <span data-ttu-id="223e1-107">從這個下拉式功能表找出現有的專案資料夾。</span><span class="sxs-lookup"><span data-stu-id="223e1-107">Locate the existing project folder from this drop-down menu.</span></span> <span data-ttu-id="223e1-108">從此清單中選取資料夾會在下方的窗格中顯示資料夾的內容。</span><span class="sxs-lookup"><span data-stu-id="223e1-108">Selecting a folder from this list displays the contents of the folder in the primary pane below.</span></span>  
  
 <span data-ttu-id="223e1-109">**檔案名稱**</span><span class="sxs-lookup"><span data-stu-id="223e1-109">**File name**</span></span>  
 <span data-ttu-id="223e1-110">使用此選項來檢視目前的檔案名稱、變更檔案名稱，或篩選顯示的檔案和資料夾。</span><span class="sxs-lookup"><span data-stu-id="223e1-110">Use this option to view the current file name, change the file name, or filter the files and folders that are displayed.</span></span> <span data-ttu-id="223e1-111">若要篩選顯示的檔案和資料夾，請輸入要篩選的完整或部份的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="223e1-111">To filter the files and folders that are displayed, enter a full or partial file name on which to filter.</span></span> <span data-ttu-id="223e1-112">您可以使用星號 (`*`) 作為萬用字元。</span><span class="sxs-lookup"><span data-stu-id="223e1-112">You can use the asterisk (`*`) as a wildcard.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="223e1-113">若要顯示位於網路及網路位置上的檔案，請在 [檔案名稱]  方塊中輸入 URL 或網路路徑。</span><span class="sxs-lookup"><span data-stu-id="223e1-113">To display files on Web and network locations, enter a URL or network path in the **File name** box.</span></span> <span data-ttu-id="223e1-114">例如，"<http://mywebsite>" 會顯示在 "mywebsite" Web 位置上的可用檔案，而 "\\\myserver\myshare" 則會顯示在 "myserver" 的 "myshare" 位置上的可用檔案。</span><span class="sxs-lookup"><span data-stu-id="223e1-114">For example, "<http://mywebsite>" displays the files available at the "mywebsite" Web location and "\\\myserver\myshare" displays the files available at the "myshare" location on "myserver".</span></span>  
  
 <span data-ttu-id="223e1-115">**存檔類型**</span><span class="sxs-lookup"><span data-stu-id="223e1-115">**Save as type**</span></span>  
 <span data-ttu-id="223e1-116">使用此選項為所選項目選取新的檔案類型。</span><span class="sxs-lookup"><span data-stu-id="223e1-116">Use this option to select a new file type for the selected item.</span></span> <span data-ttu-id="223e1-117">顯示的檔案類型都是適用於所選取項目進行轉換的可用檔案類型。</span><span class="sxs-lookup"><span data-stu-id="223e1-117">The file types displayed include all available file types to which the selected item can be converted.</span></span>  
  
 <span data-ttu-id="223e1-118">**進階儲存選項**</span><span class="sxs-lookup"><span data-stu-id="223e1-118">**Advanced Save Options**</span></span>  
 <span data-ttu-id="223e1-119">若要存取 [進階儲存選項]  對話方塊，請選取 [儲存]  按鈕右方的小矩形，然後按一下 [使用編碼方式儲存]  。</span><span class="sxs-lookup"><span data-stu-id="223e1-119">To access the **Advanced Save Options Dialog Box**, select the small rectangle at the right of the **Save** button and then click **Save with Encoding**.</span></span> <span data-ttu-id="223e1-120">使用此對話方塊來指定檔案的編碼方式和用於行尾的字元。</span><span class="sxs-lookup"><span data-stu-id="223e1-120">Use this dialog box to specify an encoding for the file and the characters to use at Line endings.</span></span>  
  
## <a name="left-panel"></a><span data-ttu-id="223e1-121">左面板</span><span class="sxs-lookup"><span data-stu-id="223e1-121">Left Panel</span></span>  
 <span data-ttu-id="223e1-122">**桌面**</span><span class="sxs-lookup"><span data-stu-id="223e1-122">**Desktop**</span></span>  
 <span data-ttu-id="223e1-123">顯示位於桌面上的任何檔案和資料夾。</span><span class="sxs-lookup"><span data-stu-id="223e1-123">Displays any files and folders located on the desktop.</span></span>  
  
 <span data-ttu-id="223e1-124">**我的專案**</span><span class="sxs-lookup"><span data-stu-id="223e1-124">**My Projects**</span></span>  
 <span data-ttu-id="223e1-125">顯示位於 **我的專案** 或最近瀏覽位置上的檔案及資料夾。</span><span class="sxs-lookup"><span data-stu-id="223e1-125">Displays files and folders at the **My Projects** or the most recently visited location.</span></span>  
  
 <span data-ttu-id="223e1-126">**我的電腦**</span><span class="sxs-lookup"><span data-stu-id="223e1-126">**My Computer**</span></span>  
 <span data-ttu-id="223e1-127">顯示您電腦上的 **的電腦** 位置。</span><span class="sxs-lookup"><span data-stu-id="223e1-127">Displays the **My Computer** location on your computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="223e1-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="223e1-128">See Also</span></span>  
 <span data-ttu-id="223e1-129">[Advanced Save 選項](advanced-save-options.md) </span><span class="sxs-lookup"><span data-stu-id="223e1-129">[Advanced Save Options](advanced-save-options.md) </span></span>  
 [<span data-ttu-id="223e1-130">利用編碼管理檔案</span><span class="sxs-lookup"><span data-stu-id="223e1-130">Manage Files with Encoding</span></span>](../solution/manage-files-with-encoding.md)  
  
  
