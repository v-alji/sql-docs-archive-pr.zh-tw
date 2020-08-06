---
title: 上傳檔案或報表 (報表管理員) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- publishing reports [Reporting Services], uploading files
- reports [Reporting Services], publishing
- uploading reports [Reporting Services]
- uploading files [Reporting Services]
- files [Reporting Services], uploading
ms.assetid: 79027e11-f4ba-4bfd-bd8c-d334e3da02a1
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 119e2b22976dc227e017b81a59b698cf9eb7457f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593284"
---
# <a name="upload-a-file-or-report-report-manager"></a><span data-ttu-id="e3e6d-102">上傳檔案或報表 (報表管理員)</span><span class="sxs-lookup"><span data-stu-id="e3e6d-102">Upload a File or Report (Report Manager)</span></span>
  <span data-ttu-id="e3e6d-103">報表管理員會提供一項上傳功能，讓您可以將報表、模型和其他檔案加入至報表伺服器，而不需要從用戶端應用程式發行這些項目。</span><span class="sxs-lookup"><span data-stu-id="e3e6d-103">Report Manager provides an upload feature so that you can add reports, models, and other files to a report server without having to publish those items from a client application.</span></span> <span data-ttu-id="e3e6d-104">您從檔案系統上傳的檔案會當做項目儲存在報表伺服器上。</span><span class="sxs-lookup"><span data-stu-id="e3e6d-104">Files that you upload from the file system are stored as items on the report server.</span></span> <span data-ttu-id="e3e6d-105">您所上傳的檔案類型會決定其儲存方式：</span><span class="sxs-lookup"><span data-stu-id="e3e6d-105">The type of file you upload determines how it is stored:</span></span>  
  
-   <span data-ttu-id="e3e6d-106">.rdl 檔案會儲存成報表。</span><span class="sxs-lookup"><span data-stu-id="e3e6d-106">.rdl files are stored as reports.</span></span>  
  
-   <span data-ttu-id="e3e6d-107">.smdl 檔案會儲存成報表模型。</span><span class="sxs-lookup"><span data-stu-id="e3e6d-107">.smdl files are stored as report models.</span></span>  
  
-   <span data-ttu-id="e3e6d-108">所有其他檔案 (包括共用資料來源 (.rds) 檔案) 則會當做資源上傳。</span><span class="sxs-lookup"><span data-stu-id="e3e6d-108">All other files, including shared data source (.rds) files, are uploaded as resources.</span></span> <span data-ttu-id="e3e6d-109">雖然報表伺服器不會處理資源，但是如果報表伺服器支援檔案的 MIME 類型，您就可以在報表管理員中檢視資源。</span><span class="sxs-lookup"><span data-stu-id="e3e6d-109">Resources are not processed by a report server, but can be viewed in Report Manager if the report server supports the MIME type of the file.</span></span>  
  
### <a name="to-upload-a-file-or-report"></a><span data-ttu-id="e3e6d-110">若要上傳檔案或報表</span><span class="sxs-lookup"><span data-stu-id="e3e6d-110">To upload a file or report</span></span>  
  
1.  <span data-ttu-id="e3e6d-111">啟動 [報表管理員 &#40;SSRS 原生模式&#41;](../report-manager-ssrs-native-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="e3e6d-111">Start [Report Manager  &#40;SSRS Native Mode&#41;](../report-manager-ssrs-native-mode.md).</span></span>  
  
2.  <span data-ttu-id="e3e6d-112">在報表管理員中，導覽至 **[內容]** 頁面。</span><span class="sxs-lookup"><span data-stu-id="e3e6d-112">In Report Manager, navigate to the **Contents** page.</span></span> <span data-ttu-id="e3e6d-113">導覽至您要加入項目的資料夾。</span><span class="sxs-lookup"><span data-stu-id="e3e6d-113">Navigate to the folder to which you want to add an item.</span></span>  
  
3.  <span data-ttu-id="e3e6d-114">按一下 [上傳檔案]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e3e6d-114">Click **Upload File**.</span></span>  
  
4.  <span data-ttu-id="e3e6d-115">按一下 [瀏覽]\*\*\*\* 選取要上傳的檔案。</span><span class="sxs-lookup"><span data-stu-id="e3e6d-115">Click **Browse** to select a file to upload.</span></span> <span data-ttu-id="e3e6d-116">您可以上傳報表定義檔案、影像、文件，或要在報表伺服器上提供使用的任何檔案。</span><span class="sxs-lookup"><span data-stu-id="e3e6d-116">You can upload a report definition file, an image, a document, or any file that you want to make available on the report server.</span></span>  
  
5.  <span data-ttu-id="e3e6d-117">輸入新項目的名稱。</span><span class="sxs-lookup"><span data-stu-id="e3e6d-117">Type a name for the new item.</span></span> <span data-ttu-id="e3e6d-118">項目名稱可以包含空格，但是不能包含保留字元：; ?</span><span class="sxs-lookup"><span data-stu-id="e3e6d-118">An item name can include spaces, but cannot include the reserved characters: ; ?</span></span> <span data-ttu-id="e3e6d-119">： \@ & = +，$/\* \< > |。</span><span class="sxs-lookup"><span data-stu-id="e3e6d-119">: \@ & = + , $ / \* \< > |.</span></span>  
  
6.  <span data-ttu-id="e3e6d-120">如果您要以新項目取代現有的項目，請選取 [如果項目存在則覆寫]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e3e6d-120">If you want to replace an existing item with the new item, select **Overwrite item if it exists**.</span></span>  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e3e6d-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e3e6d-121">See Also</span></span>  
 <span data-ttu-id="e3e6d-122">[建立、刪除或修改共用資料來源 &#40;報表管理員&#41;](../create-delete-or-modify-a-shared-data-source-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="e3e6d-122">[Create, Delete, or Modify a Shared Data Source &#40;Report Manager&#41;](../create-delete-or-modify-a-shared-data-source-report-manager.md) </span></span>  
 <span data-ttu-id="e3e6d-123">[[內容] 頁面 &#40;報表管理員&#41;](../contents-page-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="e3e6d-123">[Contents Page &#40;Report Manager&#41;](../contents-page-report-manager.md) </span></span>  
 <span data-ttu-id="e3e6d-124">[上傳檔案頁面 &#40;報表管理員&#41;](../upload-file-page-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="e3e6d-124">[Upload File Page &#40;Report Manager&#41;](../upload-file-page-report-manager.md) </span></span>  
 [<span data-ttu-id="e3e6d-125">上傳檔案到資料夾</span><span class="sxs-lookup"><span data-stu-id="e3e6d-125">Upload Files to a Folder</span></span>](../report-server/upload-files-to-a-folder.md)  
  
  
