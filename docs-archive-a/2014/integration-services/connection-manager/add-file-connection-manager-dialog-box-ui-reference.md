---
title: 新增檔案連線管理員對話方塊 UI 參考 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.fileconnection.f1
helpviewer_keywords:
- Add File Connection Manager
ms.assetid: 9370bfb5-5993-4ad8-a9cd-2de53f320f34
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 044d8e2eaae9db17d7155cb354f8d009750f44d6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706629"
---
# <a name="add-file-connection-manager-dialog-box-ui-reference"></a><span data-ttu-id="6b4b7-102">加入檔案連接管理員對話方塊 UI 參考</span><span class="sxs-lookup"><span data-stu-id="6b4b7-102">Add File Connection Manager Dialog Box UI Reference</span></span>
  <span data-ttu-id="6b4b7-103">使用 **[加入檔案連接管理員]** 對話方塊來定義一組檔案或資料夾的連接。</span><span class="sxs-lookup"><span data-stu-id="6b4b7-103">Use the **Add File Connection Manager** dialog box to define a connection to a group of files or folders.</span></span>  
  
 <span data-ttu-id="6b4b7-104">若要深入了解多個檔案連接管理員，請參閱＜ [Multiple Files Connection Manager](multiple-files-connection-manager.md)＞。</span><span class="sxs-lookup"><span data-stu-id="6b4b7-104">To learn more about the Multiple Files connection manager, see [Multiple Files Connection Manager](multiple-files-connection-manager.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6b4b7-105">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 中的內建工作和資料流程元件不會使用「多個檔案」連接管理員。</span><span class="sxs-lookup"><span data-stu-id="6b4b7-105">The built-in tasks and data flow components in [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] do not use the Multiple Files connection manager.</span></span> <span data-ttu-id="6b4b7-106">但是，您可以在指令碼工作或指令碼元件中使用這個連接管理員。</span><span class="sxs-lookup"><span data-stu-id="6b4b7-106">However, you can use this connection manager in the Script task or Script component.</span></span>  
  
## <a name="options"></a><span data-ttu-id="6b4b7-107">選項。</span><span class="sxs-lookup"><span data-stu-id="6b4b7-107">Options</span></span>  
 <span data-ttu-id="6b4b7-108">**使用類型**</span><span class="sxs-lookup"><span data-stu-id="6b4b7-108">**Usage type**</span></span>  
 <span data-ttu-id="6b4b7-109">指定用於多個檔案連接管理員的檔案類型。</span><span class="sxs-lookup"><span data-stu-id="6b4b7-109">Specify the type of files to use for the multiple files connection manager.</span></span>  
  
|<span data-ttu-id="6b4b7-110">值</span><span class="sxs-lookup"><span data-stu-id="6b4b7-110">Value</span></span>|<span data-ttu-id="6b4b7-111">描述</span><span class="sxs-lookup"><span data-stu-id="6b4b7-111">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6b4b7-112">**建立檔案**</span><span class="sxs-lookup"><span data-stu-id="6b4b7-112">**Create files**</span></span>|<span data-ttu-id="6b4b7-113">連接管理員將建立檔案。</span><span class="sxs-lookup"><span data-stu-id="6b4b7-113">The connection manager will create the files.</span></span>|  
|<span data-ttu-id="6b4b7-114">**現有的檔案**</span><span class="sxs-lookup"><span data-stu-id="6b4b7-114">**Existing files**</span></span>|<span data-ttu-id="6b4b7-115">連接管理員將使用現有的檔案。</span><span class="sxs-lookup"><span data-stu-id="6b4b7-115">The connection manager will use existing files.</span></span>|  
|<span data-ttu-id="6b4b7-116">**建立資料夾**</span><span class="sxs-lookup"><span data-stu-id="6b4b7-116">**Create folders**</span></span>|<span data-ttu-id="6b4b7-117">連接管理員將建立資料夾。</span><span class="sxs-lookup"><span data-stu-id="6b4b7-117">The connection manager will create the folders.</span></span>|  
|<span data-ttu-id="6b4b7-118">**現有的資料夾**</span><span class="sxs-lookup"><span data-stu-id="6b4b7-118">**Existing folders**</span></span>|<span data-ttu-id="6b4b7-119">連接管理員將使用現有的資料夾。</span><span class="sxs-lookup"><span data-stu-id="6b4b7-119">The connection manager will use existing folders.</span></span>|  
  
 <span data-ttu-id="6b4b7-120">**檔案 / 資料夾**</span><span class="sxs-lookup"><span data-stu-id="6b4b7-120">**Files / Folders**</span></span>  
 <span data-ttu-id="6b4b7-121">檢視已經使用如下所述的按鈕加入的檔案或資料夾。</span><span class="sxs-lookup"><span data-stu-id="6b4b7-121">View the files or folders that you have added by using the buttons described as follows.</span></span>  
  
 <span data-ttu-id="6b4b7-122">**加入**</span><span class="sxs-lookup"><span data-stu-id="6b4b7-122">**Add**</span></span>  
 <span data-ttu-id="6b4b7-123">使用 [選取檔案]  對話方塊來加入檔案，或使用 [瀏覽資料夾]  對話方塊來加入資料夾。</span><span class="sxs-lookup"><span data-stu-id="6b4b7-123">Add a file by using the **Select Files** dialog box, or add a folder by using the **Browse for Folder** dialog box.</span></span>  
  
 <span data-ttu-id="6b4b7-124">**編輯**</span><span class="sxs-lookup"><span data-stu-id="6b4b7-124">**Edit**</span></span>  
 <span data-ttu-id="6b4b7-125">選取檔案或資料夾，然後使用 [選取檔案]  或 [瀏覽資料夾]  對話方塊以不同的檔案或資料夾來取代。</span><span class="sxs-lookup"><span data-stu-id="6b4b7-125">Select a file or folder, and then replace it with a different file or folder by using the **Select Files** or **Browse for Folder** dialog box.</span></span>  
  
 <span data-ttu-id="6b4b7-126">**移除**</span><span class="sxs-lookup"><span data-stu-id="6b4b7-126">**Remove**</span></span>  
 <span data-ttu-id="6b4b7-127">選取檔案或資料夾，然後使用 [移除]  按鈕將它從清單中移除。</span><span class="sxs-lookup"><span data-stu-id="6b4b7-127">Select a file or folder, and then remove it from the list by using the **Remove** button.</span></span>  
  
 <span data-ttu-id="6b4b7-128">**箭頭按鈕**</span><span class="sxs-lookup"><span data-stu-id="6b4b7-128">**Arrow buttons**</span></span>  
 <span data-ttu-id="6b4b7-129">選取檔案或資料夾，然後使用箭頭按鈕上移或下移來指定存取順序。</span><span class="sxs-lookup"><span data-stu-id="6b4b7-129">Select a file or folder, and then use the arrow buttons to move it up or down to specify the sequence of access.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b4b7-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6b4b7-130">See Also</span></span>  
 [<span data-ttu-id="6b4b7-131">Integration Services 錯誤和訊息參考</span><span class="sxs-lookup"><span data-stu-id="6b4b7-131">Integration Services Error and Message Reference</span></span>](../integration-services-error-and-message-reference.md)  
  
  
