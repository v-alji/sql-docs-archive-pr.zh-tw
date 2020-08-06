---
title: 檔案連線管理員編輯器 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.fileconnectionmanager.f1
helpviewer_keywords:
- File Connection Manager Editor
ms.assetid: 051c48e5-3d86-49af-b554-ff62e3de3622
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 2f3261b836d4800787fc078b05b15e469d3c200d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599060"
---
# <a name="file-connection-manager-editor"></a><span data-ttu-id="0a1ff-102">檔案連接管理員編輯器</span><span class="sxs-lookup"><span data-stu-id="0a1ff-102">File Connection Manager Editor</span></span>
  <span data-ttu-id="0a1ff-103">使用 **[檔案連接管理員編輯器]** 對話方塊，以指定用來連接到檔案或資料夾的屬性。</span><span class="sxs-lookup"><span data-stu-id="0a1ff-103">Use the **File Connection Manager Editor** dialog box to specify the properties used to connect to a file or a folder.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0a1ff-104">您可以針對檔案連線管理員來設定 ConnectionString 屬性，其方式是在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]的 [屬性] 視窗中指定運算式。</span><span class="sxs-lookup"><span data-stu-id="0a1ff-104">You can set the ConnectionString property for the File connection manager by specifying an expression in the Properties window of [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="0a1ff-105">但是，若您在使用運算式來指定檔案或資料夾時想要避免驗證錯誤，請在 **檔案連線管理員編輯器**中針對 **檔案/資料夾**，加入檔案或資料夾的路徑。</span><span class="sxs-lookup"><span data-stu-id="0a1ff-105">However, to avoid a validation error when you use an expression to specify the file or folder, in the **File Connection Manager Editor**, for **File/Folder**, add a file or folder path.</span></span>  
  
 <span data-ttu-id="0a1ff-106">若要深入了解檔案連接管理員，請參閱＜ [File Connection Manager](connection-manager/file-connection-manager.md)＞。</span><span class="sxs-lookup"><span data-stu-id="0a1ff-106">To learn more about the File connection manager, see [File Connection Manager](connection-manager/file-connection-manager.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="0a1ff-107">選項</span><span class="sxs-lookup"><span data-stu-id="0a1ff-107">Options</span></span>  
 <span data-ttu-id="0a1ff-108">**使用類型**</span><span class="sxs-lookup"><span data-stu-id="0a1ff-108">**Usage Type**</span></span>  
 <span data-ttu-id="0a1ff-109">指定 [檔案連線管理員]\*\*\*\* 是否連接到現有的檔案或資料夾，或者建立新檔案或資料夾。</span><span class="sxs-lookup"><span data-stu-id="0a1ff-109">Specify whether the **File Connection Manager** connects to an existing file or folder or creates a new file or folder.</span></span>  
  
|<span data-ttu-id="0a1ff-110">值</span><span class="sxs-lookup"><span data-stu-id="0a1ff-110">Value</span></span>|<span data-ttu-id="0a1ff-111">描述</span><span class="sxs-lookup"><span data-stu-id="0a1ff-111">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0a1ff-112">建立檔案</span><span class="sxs-lookup"><span data-stu-id="0a1ff-112">Create file</span></span>|<span data-ttu-id="0a1ff-113">在執行階段建立新檔案。</span><span class="sxs-lookup"><span data-stu-id="0a1ff-113">Create a new file at run time.</span></span>|  
|<span data-ttu-id="0a1ff-114">現有的檔案</span><span class="sxs-lookup"><span data-stu-id="0a1ff-114">Existing file</span></span>|<span data-ttu-id="0a1ff-115">使用現有的檔案</span><span class="sxs-lookup"><span data-stu-id="0a1ff-115">Use an existing file.</span></span>|  
|<span data-ttu-id="0a1ff-116">建立資料夾</span><span class="sxs-lookup"><span data-stu-id="0a1ff-116">Create folder</span></span>|<span data-ttu-id="0a1ff-117">在執行階段建立新資料夾。</span><span class="sxs-lookup"><span data-stu-id="0a1ff-117">Create a new folder at run time.</span></span>|  
|<span data-ttu-id="0a1ff-118">現有的資料夾</span><span class="sxs-lookup"><span data-stu-id="0a1ff-118">Existing folder</span></span>|<span data-ttu-id="0a1ff-119">使用現有的資料夾。</span><span class="sxs-lookup"><span data-stu-id="0a1ff-119">Use an existing folder.</span></span>|  
  
 <span data-ttu-id="0a1ff-120">**檔案 / 資料夾**</span><span class="sxs-lookup"><span data-stu-id="0a1ff-120">**File / Folder**</span></span>  
 <span data-ttu-id="0a1ff-121">若為 [檔案]\*\*\*\*，請指定要使用的檔案。</span><span class="sxs-lookup"><span data-stu-id="0a1ff-121">If **File**, specify the file to use.</span></span>  
  
 <span data-ttu-id="0a1ff-122">若為 **[資料夾]**，請指定要使用的資料夾。</span><span class="sxs-lookup"><span data-stu-id="0a1ff-122">If **Folder**, specify the folder to use.</span></span>  
  
 <span data-ttu-id="0a1ff-123">**瀏覽**</span><span class="sxs-lookup"><span data-stu-id="0a1ff-123">**Browse**</span></span>  
 <span data-ttu-id="0a1ff-124">使用 [選取檔案]\*\*\*\* 或 [瀏覽資料夾]\*\*\*\* 對話方塊，來選取檔案或資料夾。</span><span class="sxs-lookup"><span data-stu-id="0a1ff-124">Select the file or folder by using the **Select File** or **Browse for Folder** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a1ff-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0a1ff-125">See Also</span></span>  
 [<span data-ttu-id="0a1ff-126">Integration Services 錯誤和訊息參考</span><span class="sxs-lookup"><span data-stu-id="0a1ff-126">Integration Services Error and Message Reference</span></span>](../../2014/integration-services/integration-services-error-and-message-reference.md)  
  
  
