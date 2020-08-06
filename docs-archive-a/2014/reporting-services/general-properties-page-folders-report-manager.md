---
title: 一般屬性頁面、資料夾 (報表管理員) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 31d99d9b-2303-4bae-9466-fb67b97cf11a
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: fb1c3fbf2e9020ac5d1fe5ebbd1e9ed48b45adb9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606095"
---
# <a name="general-properties-page-folders-report-manager"></a><span data-ttu-id="f9f9c-102">一般屬性頁面，資料夾 (報表管理員)</span><span class="sxs-lookup"><span data-stu-id="f9f9c-102">General Properties Page, Folders (Report Manager)</span></span>
  <span data-ttu-id="f9f9c-103">使用資料夾的 [一般] 屬性頁面來檢視和設定您建立之資料夾的屬性。</span><span class="sxs-lookup"><span data-stu-id="f9f9c-103">Use the General properties page for folders to view and set properties for the folders that you create.</span></span> <span data-ttu-id="f9f9c-104">有關誰建立和修改資料夾及何時修改資料夾的資訊顯示會在 [一般] 屬性頁面上方。</span><span class="sxs-lookup"><span data-stu-id="f9f9c-104">Information about who created or modified the folder and when the folder was modified appear at the top of the General properties page.</span></span>  
  
 <span data-ttu-id="f9f9c-105">資料夾屬性也包含安全性設定。</span><span class="sxs-lookup"><span data-stu-id="f9f9c-105">Folder properties also include security settings.</span></span> <span data-ttu-id="f9f9c-106">如需有關資料夾安全性的詳細資訊，請參閱[保護資料夾](security/secure-folders.md)。</span><span class="sxs-lookup"><span data-stu-id="f9f9c-106">For more information about folder security, see [Secure Folders](security/secure-folders.md).</span></span>  
  
 <span data-ttu-id="f9f9c-107">不可以在報表伺服器命名空間內重新命名或移動特殊用途的資料夾 (例如，[主資料夾]、[我的報表] 和 [使用者] 資料夾)。</span><span class="sxs-lookup"><span data-stu-id="f9f9c-107">Special-purpose folders such as Home, My Reports, and Users folders cannot be renamed or moved within the report server namespace.</span></span> <span data-ttu-id="f9f9c-108">[一般] 屬性頁不適用於這些資料夾中。</span><span class="sxs-lookup"><span data-stu-id="f9f9c-108">The General properties page is not available for these folders.</span></span>  
  
## <a name="navigation"></a><span data-ttu-id="f9f9c-109">導覽</span><span class="sxs-lookup"><span data-stu-id="f9f9c-109">Navigation</span></span>  
 <span data-ttu-id="f9f9c-110">您可以使用下列程序，在使用者介面 (UI) 中導覽至這個位置。</span><span class="sxs-lookup"><span data-stu-id="f9f9c-110">Use the following procedure to navigate to this location in the user interface (UI).</span></span>  
  
###### <a name="to-open-the-general-properties-page-for-a-folder"></a><span data-ttu-id="f9f9c-111">若要開啟資料夾的一般屬性頁面</span><span class="sxs-lookup"><span data-stu-id="f9f9c-111">To open the General properties page for a folder</span></span>  
  
1.  <span data-ttu-id="f9f9c-112">開啟報表管理員，然後開啟您想要檢視或設定屬性的資料夾。</span><span class="sxs-lookup"><span data-stu-id="f9f9c-112">Open Report Manager, and open the folder for which you want to view or configure properties.</span></span>  
  
2.  <span data-ttu-id="f9f9c-113">在資料夾橫幅底下的工具列中，按一下 **[資料夾設定]**。</span><span class="sxs-lookup"><span data-stu-id="f9f9c-113">Under the folder banner, in the toolbar, click **Folder Settings**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="f9f9c-114">選項。</span><span class="sxs-lookup"><span data-stu-id="f9f9c-114">Options</span></span>  
 <span data-ttu-id="f9f9c-115">**名稱**</span><span class="sxs-lookup"><span data-stu-id="f9f9c-115">**Name**</span></span>  
 <span data-ttu-id="f9f9c-116">指定資料夾的名稱。</span><span class="sxs-lookup"><span data-stu-id="f9f9c-116">Specify a name for the folder.</span></span> <span data-ttu-id="f9f9c-117">名稱必須至少包含一個英數字元。</span><span class="sxs-lookup"><span data-stu-id="f9f9c-117">A name must contain at least one alphanumeric character.</span></span> <span data-ttu-id="f9f9c-118">它也可以包含空格和某些符號。</span><span class="sxs-lookup"><span data-stu-id="f9f9c-118">It can also include spaces and some symbols.</span></span> <span data-ttu-id="f9f9c-119">請勿使用 ; ?</span><span class="sxs-lookup"><span data-stu-id="f9f9c-119">Do not use the characters ; ?</span></span> <span data-ttu-id="f9f9c-120">： \@ & = +，$ \* \< > |"或/指定名稱時。</span><span class="sxs-lookup"><span data-stu-id="f9f9c-120">: \@ & = + , $ \* \< > | " or / when specifying a name.</span></span>  
  
 <span data-ttu-id="f9f9c-121">**說明**</span><span class="sxs-lookup"><span data-stu-id="f9f9c-121">**Description**</span></span>  
 <span data-ttu-id="f9f9c-122">輸入資料夾內容的描述。</span><span class="sxs-lookup"><span data-stu-id="f9f9c-122">Type a description of the folder contents.</span></span> <span data-ttu-id="f9f9c-123">此描述會出現在有權存取此資料夾之使用者的 [內容] 頁面上。</span><span class="sxs-lookup"><span data-stu-id="f9f9c-123">This description appears on the Contents page for users who have permission to access the folder.</span></span>  
  
 <span data-ttu-id="f9f9c-124">**在清單檢視中隱藏**</span><span class="sxs-lookup"><span data-stu-id="f9f9c-124">**Hide in list view**</span></span>  
 <span data-ttu-id="f9f9c-125">選取這個選項可以對正在「報表管理員」中使用清單檢視模式的使用者隱藏資料夾。</span><span class="sxs-lookup"><span data-stu-id="f9f9c-125">Select this option to hide the folder from users who are using list view mode in Report Manager.</span></span> <span data-ttu-id="f9f9c-126">清單檢視模式是瀏覽報表伺服器資料夾階層時的預設檢視格式。</span><span class="sxs-lookup"><span data-stu-id="f9f9c-126">List view mode is the default view format when browsing the report server folder hierarchy.</span></span> <span data-ttu-id="f9f9c-127">在清單檢視中，項目名稱和描述會跨頁排列。</span><span class="sxs-lookup"><span data-stu-id="f9f9c-127">In list view, item names and descriptions flow across the page.</span></span> <span data-ttu-id="f9f9c-128">替代格式是詳細資料檢視。</span><span class="sxs-lookup"><span data-stu-id="f9f9c-128">The alternate format is details view.</span></span> <span data-ttu-id="f9f9c-129">詳細資料檢視會省略描述，但會包括項目的其他相關資訊。</span><span class="sxs-lookup"><span data-stu-id="f9f9c-129">Details view omits descriptions, but includes other information about the item.</span></span> <span data-ttu-id="f9f9c-130">雖然在清單檢視中可以隱藏項目，但在詳細資料檢視中則不行。</span><span class="sxs-lookup"><span data-stu-id="f9f9c-130">Although you can hide an item in list view, you cannot hide an item in details view.</span></span> <span data-ttu-id="f9f9c-131">如果想要限制項目的存取，您必須建立角色指派。</span><span class="sxs-lookup"><span data-stu-id="f9f9c-131">If you want to restrict access to an item, you must create a role assignment.</span></span>  
  
 <span data-ttu-id="f9f9c-132">**套用**</span><span class="sxs-lookup"><span data-stu-id="f9f9c-132">**Apply**</span></span>  
 <span data-ttu-id="f9f9c-133">按一下即可儲存您的變更。</span><span class="sxs-lookup"><span data-stu-id="f9f9c-133">Click to save your changes.</span></span>  
  
 <span data-ttu-id="f9f9c-134">**刪除**</span><span class="sxs-lookup"><span data-stu-id="f9f9c-134">**Delete**</span></span>  
 <span data-ttu-id="f9f9c-135">按一下即可移除資料夾及其內容。</span><span class="sxs-lookup"><span data-stu-id="f9f9c-135">Click to remove the folder and its contents.</span></span>  
  
 <span data-ttu-id="f9f9c-136">**移動**</span><span class="sxs-lookup"><span data-stu-id="f9f9c-136">**Move**</span></span>  
 <span data-ttu-id="f9f9c-137">按一下即可在報表伺服器命名空間中重新定位報表或資料夾。</span><span class="sxs-lookup"><span data-stu-id="f9f9c-137">Click to relocate a report or folder within the report server namespace.</span></span> <span data-ttu-id="f9f9c-138">按一下此按鈕會開啟 [移動項目] 頁面，您可在此瀏覽資料夾的新位置。</span><span class="sxs-lookup"><span data-stu-id="f9f9c-138">Clicking this button opens the Move Items page that allows you to browse folders for a new folder location.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9f9c-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f9f9c-139">See Also</span></span>  
 <span data-ttu-id="f9f9c-140">[報表管理員 &#40;SSRS 原生模式&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="f9f9c-140">[Report Manager  &#40;SSRS Native Mode&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span></span>  
 [<span data-ttu-id="f9f9c-141">報表管理員 F1 說明</span><span class="sxs-lookup"><span data-stu-id="f9f9c-141">Report Manager F1 Help</span></span>](../../2014/reporting-services/report-manager-f1-help.md)  
  
  
