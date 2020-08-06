---
title: 更新資源 (報表管理員) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- updating resources
- resources [Reporting Services], updating
ms.assetid: d21f7493-bcf7-4e9e-9886-55ebdc1f1037
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a0fca59e476c2820b715ff46729784edc562f74d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595618"
---
# <a name="update-a-resource-report-manager"></a><span data-ttu-id="58711-102">更新資源 (報表管理員)</span><span class="sxs-lookup"><span data-stu-id="58711-102">Update a Resource (Report Manager)</span></span>
  <span data-ttu-id="58711-103">您可以使用新版本來取代舊版本，以此方式更新資源。</span><span class="sxs-lookup"><span data-stu-id="58711-103">You can update a resource by replacing it with a newer version.</span></span> <span data-ttu-id="58711-104">資源是一些項目，儲存在包含您上傳之檔案中之內容的報表伺服器上。</span><span class="sxs-lookup"><span data-stu-id="58711-104">Resources are items stored on a report server that contain content from a file that you upload.</span></span> <span data-ttu-id="58711-105">您可以將新的或不同的檔案內容匯入現有的資源，以取代現有的資源。</span><span class="sxs-lookup"><span data-stu-id="58711-105">You can replace an existing resource by importing new or different file content into the existing resource.</span></span> <span data-ttu-id="58711-106">更新資源提供一種方式，可以更新內容，同時保留資源的現有屬性與安全性設定。</span><span class="sxs-lookup"><span data-stu-id="58711-106">Updating a resource provides a way to update content while preserving existing properties and security settings on the resource.</span></span>  
  
### <a name="to-update-a-resource"></a><span data-ttu-id="58711-107">若要更新資源</span><span class="sxs-lookup"><span data-stu-id="58711-107">To update a resource</span></span>  
  
1.  <span data-ttu-id="58711-108">啟動 [報表管理員 &#40;SSRS 原生模式&#41;](../report-manager-ssrs-native-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="58711-108">Start [Report Manager  &#40;SSRS Native Mode&#41;](../report-manager-ssrs-native-mode.md).</span></span>  
  
2.  <span data-ttu-id="58711-109">在報表管理員中，導覽至或搜尋您要更新的資源。</span><span class="sxs-lookup"><span data-stu-id="58711-109">In Report Manager, navigate to or search for the resource you want to update.</span></span>  
  
3.  <span data-ttu-id="58711-110">按一下資源，即可在 [檢視]\*\*\*\* 頁面中開啟資源。</span><span class="sxs-lookup"><span data-stu-id="58711-110">Click the resource to open it in the **View** page.</span></span>  
  
4.  <span data-ttu-id="58711-111">按一下 [屬性]\*\*\*\*，即可開啟 [一般]\*\*\*\* 屬性頁面。</span><span class="sxs-lookup"><span data-stu-id="58711-111">Click **Properties** to open the **General** properties page.</span></span>  
  
5.  <span data-ttu-id="58711-112">按一下 [取代]\*\*\*\*，即可開啟 [匯入資源]\*\*\*\* 頁面。</span><span class="sxs-lookup"><span data-stu-id="58711-112">Click **Replace** to open the **Import Resource** page.</span></span>  
  
6.  <span data-ttu-id="58711-113">按一下 **[瀏覽]** 。</span><span class="sxs-lookup"><span data-stu-id="58711-113">Click **Browse**.</span></span>  
  
7.  <span data-ttu-id="58711-114">選取您要用來取代目前資源的檔案。</span><span class="sxs-lookup"><span data-stu-id="58711-114">Select the file that you want to use to replace the current resource.</span></span> <span data-ttu-id="58711-115">您可以使用資源檔案的更新版本，或者指定不同名稱或檔案類型的檔案。</span><span class="sxs-lookup"><span data-stu-id="58711-115">You can use an updated version of the resource file, or specify a file with a different name or file type.</span></span>  
  
8.  <span data-ttu-id="58711-116">按一下 [確定]\*\*\*\*，即可上傳資源檔案，關閉 [匯入資源]\*\*\*\* 頁面，並將您的變更儲存到報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="58711-116">Click **OK** to upload the resource file, close the **Import Resource** page, and save your changes to the report server.</span></span>  
  
 <span data-ttu-id="58711-117">如果您更新的資源包含在報表中所使用的影像，您就需要重新整理報表才看得到更新的影像。</span><span class="sxs-lookup"><span data-stu-id="58711-117">If the resource you are updating contains an image that is used in a report, you need to refresh the report to see the updated image.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58711-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="58711-118">See Also</span></span>  
 <span data-ttu-id="58711-119">[[內容] 頁面 &#40;報表管理員&#41;](../contents-page-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="58711-119">[Contents Page &#40;Report Manager&#41;](../contents-page-report-manager.md) </span></span>  
 <span data-ttu-id="58711-120">[上傳檔案頁面 &#40;報表管理員&#41;](../upload-file-page-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="58711-120">[Upload File Page &#40;Report Manager&#41;](../upload-file-page-report-manager.md) </span></span>  
 <span data-ttu-id="58711-121">[將檔案上傳到資料夾](upload-files-to-a-folder.md) </span><span class="sxs-lookup"><span data-stu-id="58711-121">[Upload Files to a Folder](upload-files-to-a-folder.md) </span></span>  
 [<span data-ttu-id="58711-122">報表管理員 F1 說明</span><span class="sxs-lookup"><span data-stu-id="58711-122">Report Manager F1 Help</span></span>](../report-manager-f1-help.md)  
  
  
