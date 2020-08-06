---
title: 新增資料夾頁面 (報表管理員) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 9212fc68-f0a6-4f79-83c1-84baf4d1957e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 27c6a82c4911ba42215d4ab7dcafd666ddce5d54
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598242"
---
# <a name="new-folder-page-report-manager"></a><span data-ttu-id="a97d2-102">新增資料夾頁面 (報表管理員)</span><span class="sxs-lookup"><span data-stu-id="a97d2-102">New Folder Page (Report Manager)</span></span>
  <span data-ttu-id="a97d2-103">使用 [新增資料夾] 頁面，即可在報表伺服器資料夾階層中建立新的資料夾。</span><span class="sxs-lookup"><span data-stu-id="a97d2-103">Use the New Folder page to create a new folder in the report server folder hierarchy.</span></span> <span data-ttu-id="a97d2-104">您建立的資料夾是儲存在報表伺服器資料庫中的虛擬資料夾。</span><span class="sxs-lookup"><span data-stu-id="a97d2-104">The folder that you create is a virtual folder that is stored in a report server database.</span></span> <span data-ttu-id="a97d2-105">這個資料夾並不是在電腦的檔案系統中建立的。</span><span class="sxs-lookup"><span data-stu-id="a97d2-105">The folder is not created in the file system of your computer.</span></span>  
  
 <span data-ttu-id="a97d2-106">資料夾將就地建立，作為目前選取的資料夾的子資料夾。</span><span class="sxs-lookup"><span data-stu-id="a97d2-106">A folder is created in-place, as a subfolder of the folder that is currently selected.</span></span> <span data-ttu-id="a97d2-107">在建立資料夾之前，您應該瀏覽想要建立資料夾的位置。</span><span class="sxs-lookup"><span data-stu-id="a97d2-107">Before creating a folder, you should navigate to the location where you want to create the folder.</span></span>  
  
 <span data-ttu-id="a97d2-108">在建立資料夾之後，可以透過資料夾的 [一般] 屬性頁來修改其名稱和描述。</span><span class="sxs-lookup"><span data-stu-id="a97d2-108">After you create a folder, you can modify its name and description through the General properties page of the folder.</span></span>  
  
## <a name="navigation"></a><span data-ttu-id="a97d2-109">導覽</span><span class="sxs-lookup"><span data-stu-id="a97d2-109">Navigation</span></span>  
 <span data-ttu-id="a97d2-110">您可以使用下列程序，在使用者介面 (UI) 中導覽至這個位置。</span><span class="sxs-lookup"><span data-stu-id="a97d2-110">Use the following procedure to navigate to this location in the user interface (UI).</span></span>  
  
###### <a name="to-open-the-new-folder-page"></a><span data-ttu-id="a97d2-111">若要開啟新增資料夾頁面</span><span class="sxs-lookup"><span data-stu-id="a97d2-111">To open the New Folder page</span></span>  
  
1.  <span data-ttu-id="a97d2-112">開啟報表管理員中，然後導覽至您想要在其中建立新資料夾的資料夾。</span><span class="sxs-lookup"><span data-stu-id="a97d2-112">Open Report Manager, and navigate to the folder in which you want to create a new folder.</span></span>  
  
2.  <span data-ttu-id="a97d2-113">在工具列中，按一下 **[新增資料夾]**。</span><span class="sxs-lookup"><span data-stu-id="a97d2-113">In the toolbar, click **New Folder**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="a97d2-114">選項。</span><span class="sxs-lookup"><span data-stu-id="a97d2-114">Options</span></span>  
 <span data-ttu-id="a97d2-115">**名稱**</span><span class="sxs-lookup"><span data-stu-id="a97d2-115">**Name**</span></span>  
 <span data-ttu-id="a97d2-116">指定資料夾的名稱。</span><span class="sxs-lookup"><span data-stu-id="a97d2-116">Specify the name of the folder.</span></span> <span data-ttu-id="a97d2-117">名稱必須至少包含一個英數字元。</span><span class="sxs-lookup"><span data-stu-id="a97d2-117">A name must contain at least one alphanumeric character.</span></span> <span data-ttu-id="a97d2-118">也可以包含空格和特定符號。</span><span class="sxs-lookup"><span data-stu-id="a97d2-118">It can also include spaces and certain symbols.</span></span> <span data-ttu-id="a97d2-119">請勿使用 ; ?</span><span class="sxs-lookup"><span data-stu-id="a97d2-119">Do not use the characters ; ?</span></span> <span data-ttu-id="a97d2-120">： \@ & = +，$/\* \< > |"或/指定名稱時。</span><span class="sxs-lookup"><span data-stu-id="a97d2-120">: \@ & = + , $ / \* \< > | " or / when specifying a name.</span></span>  
  
 <span data-ttu-id="a97d2-121">**說明**</span><span class="sxs-lookup"><span data-stu-id="a97d2-121">**Description**</span></span>  
 <span data-ttu-id="a97d2-122">輸入資料夾內容的描述。</span><span class="sxs-lookup"><span data-stu-id="a97d2-122">Type a description of folder contents.</span></span> <span data-ttu-id="a97d2-123">此描述會顯示在有權存取此資料夾之使用者的 [內容] 頁面中。</span><span class="sxs-lookup"><span data-stu-id="a97d2-123">This description appears in the Contents page to users who have permission to access the folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a97d2-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a97d2-124">See Also</span></span>  
 <span data-ttu-id="a97d2-125">[建立、刪除或修改資料夾 &#40;報表管理員&#41;](report-server/create-delete-or-modify-a-folder-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="a97d2-125">[Create, Delete, or Modify a Folder &#40;Report Manager&#41;](report-server/create-delete-or-modify-a-folder-report-manager.md) </span></span>  
 <span data-ttu-id="a97d2-126">[一般屬性頁面、資料夾 &#40;報表管理員&#41;](../../2014/reporting-services/general-properties-page-folders-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="a97d2-126">[General Properties Page, Folders &#40;Report Manager&#41;](../../2014/reporting-services/general-properties-page-folders-report-manager.md) </span></span>  
 <span data-ttu-id="a97d2-127">[報表管理員 &#40;SSRS 原生模式&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="a97d2-127">[Report Manager  &#40;SSRS Native Mode&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span></span>  
 <span data-ttu-id="a97d2-128">[[內容] 頁面 &#40;報表管理員&#41;](../../2014/reporting-services/contents-page-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="a97d2-128">[Contents Page &#40;Report Manager&#41;](../../2014/reporting-services/contents-page-report-manager.md) </span></span>  
 <span data-ttu-id="a97d2-129">[報表管理員 F1 說明](../../2014/reporting-services/report-manager-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="a97d2-129">[Report Manager F1 Help](../../2014/reporting-services/report-manager-f1-help.md) </span></span>  
 [<span data-ttu-id="a97d2-130">一般屬性頁面、資料夾 &#40;報表管理員&#41;</span><span class="sxs-lookup"><span data-stu-id="a97d2-130">General Properties Page, Folders &#40;Report Manager&#41;</span></span>](../../2014/reporting-services/general-properties-page-folders-report-manager.md)  
  
  
