---
title: 上傳檔案到資料夾 | Microsoft Docs
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
- files [Reporting Services]
- folders [Reporting Services], uploading files to
ms.assetid: 2f99a288-d4aa-4c64-b310-e457a2aef2c5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: cfb595ed6059436d17cb82262f5d1975a8397dbd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595617"
---
# <a name="upload-files-to-a-folder"></a><span data-ttu-id="4070a-102">上傳檔案到資料夾</span><span class="sxs-lookup"><span data-stu-id="4070a-102">Upload Files to a Folder</span></span>
  <span data-ttu-id="4070a-103">您可以從檔案系統上傳檔案，並將其當成 Managed 項目儲存在報表伺服器資料庫中。</span><span class="sxs-lookup"><span data-stu-id="4070a-103">You can upload files from the file system and store them as managed items in a report server database.</span></span> <span data-ttu-id="4070a-104">上傳檔案會有何狀況取決於檔案類型。</span><span class="sxs-lookup"><span data-stu-id="4070a-104">What happens when you upload a file depends on the file type.</span></span>

-   <span data-ttu-id="4070a-105">上傳 .rdl 檔案相當於發行報表。</span><span class="sxs-lookup"><span data-stu-id="4070a-105">Uploading an .rdl file is equivalent to publishing a report.</span></span>

-   <span data-ttu-id="4070a-106">上傳任何其他檔案，會將檔案當做單一的二進位物件加入到報表伺服器資料庫中。</span><span class="sxs-lookup"><span data-stu-id="4070a-106">Uploading any other file adds it to the report server database as a single binary object.</span></span> <span data-ttu-id="4070a-107">這些檔案會發行至報表伺服器做為資源。</span><span class="sxs-lookup"><span data-stu-id="4070a-107">These files are published to a report server as a resource.</span></span> <span data-ttu-id="4070a-108">資源可以是任何檔案類型。</span><span class="sxs-lookup"><span data-stu-id="4070a-108">Resources can be any file type.</span></span> <span data-ttu-id="4070a-109">如果副檔名符合已知的 MIME 類型，則會使用 MIME 類型的圖示來識別資源類型。</span><span class="sxs-lookup"><span data-stu-id="4070a-109">If the file extension matches a known MIME type, an icon for that MIME type is used to identify the resource type.</span></span> <span data-ttu-id="4070a-110">否則，會以一般檔案圖示表示資源。</span><span class="sxs-lookup"><span data-stu-id="4070a-110">Otherwise, a generic file icon indicates a resource.</span></span>

> [!NOTE]
>  <span data-ttu-id="4070a-111">您不能上傳報表資料來源 (.rds) 檔案，以建立共用資料來源。</span><span class="sxs-lookup"><span data-stu-id="4070a-111">You cannot upload a report data source (.rds) file to create a shared data source.</span></span> <span data-ttu-id="4070a-112">.rds 檔案只能在報表設計師中使用。</span><span class="sxs-lookup"><span data-stu-id="4070a-112">An .rds file is used only in Report Designer.</span></span> <span data-ttu-id="4070a-113">它無法提供您透過報表管理員定義與管理之共用資料來源項目的內容。</span><span class="sxs-lookup"><span data-stu-id="4070a-113">It cannot provide the content for a shared data source item that you define and manage through Report Manager.</span></span> <span data-ttu-id="4070a-114">上傳的替代方法，是撰寫指令碼來建立以 .rds 檔案為基礎的共用資料來源。</span><span class="sxs-lookup"><span data-stu-id="4070a-114">As an alternative to uploading, you can write a script that creates a shared data source based on a .rds file.</span></span>

 <span data-ttu-id="4070a-115">上傳項目的檔案大小上限是由 [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)]所決定。</span><span class="sxs-lookup"><span data-stu-id="4070a-115">The maximum file size for uploaded items is determined by [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)].</span></span> <span data-ttu-id="4070a-116">根據預設，大小上限是 4 MB。</span><span class="sxs-lookup"><span data-stu-id="4070a-116">By default, the maximum size is 4 megabytes (MB).</span></span>

 <span data-ttu-id="4070a-117">您上傳至報表伺服器資料庫的檔案，在資料夾階層中會使用下列圖示進行視覺化表示。</span><span class="sxs-lookup"><span data-stu-id="4070a-117">Visually, files that you upload to a report server database are represented in the folder hierarchy with the following icons.</span></span>

 <span data-ttu-id="4070a-118">![報表圖示](../media/hlp-16doc.gif "報表圖示")報表圖示</span><span class="sxs-lookup"><span data-stu-id="4070a-118">![Report icon](../media/hlp-16doc.gif "Report icon") report icon</span></span>

 <span data-ttu-id="4070a-119">![模型圖示](../media/model-icon.gif "模型圖示")報表模型圖示</span><span class="sxs-lookup"><span data-stu-id="4070a-119">![Model icon](../media/model-icon.gif "Model icon") report model icon</span></span>

 <span data-ttu-id="4070a-120">![一般資源圖示](../media/hlp-16file.gif "一般資源圖示")一般資源圖示</span><span class="sxs-lookup"><span data-stu-id="4070a-120">![generic resource icon](../media/hlp-16file.gif "generic resource icon") generic resource icon</span></span>

 <span data-ttu-id="4070a-121">上傳檔案時，檔案永遠會放在目前所選取的資料夾中。</span><span class="sxs-lookup"><span data-stu-id="4070a-121">When you upload a file, it is always placed in the folder that is currently selected.</span></span> <span data-ttu-id="4070a-122">您可以先導覽至要包含項目的資料夾，或是上傳檔案然後再移動到最終位置。</span><span class="sxs-lookup"><span data-stu-id="4070a-122">You can navigate to the folder that you want to contain the item first, or you can upload a file and then move it to a final location later.</span></span>

 <span data-ttu-id="4070a-123">若要上傳檔案，請使用報表管理員。</span><span class="sxs-lookup"><span data-stu-id="4070a-123">To upload a file, use Report Manager.</span></span> <span data-ttu-id="4070a-124">您是否能夠上傳檔案到報表伺服器，是依您角色指派中的工作而定。</span><span class="sxs-lookup"><span data-stu-id="4070a-124">Whether you can upload files to a report server depends on tasks that are part of your role assignment.</span></span> <span data-ttu-id="4070a-125">如果您使用預設安全性，本機管理員就可以將項目加入報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="4070a-125">If you are using default security, local administrators can add items to a report server.</span></span> <span data-ttu-id="4070a-126">如果已啟用我的報表，則只要是有 [我的報表] 資料夾的使用者，都有權將項目上傳至該資料夾。</span><span class="sxs-lookup"><span data-stu-id="4070a-126">If My Reports is enabled, any user who has a My Reports folder has permission to upload items to that folder.</span></span> <span data-ttu-id="4070a-127">如果您使用自訂角色指派，角色指派就必須包括支援資料夾管理的工作。</span><span class="sxs-lookup"><span data-stu-id="4070a-127">If you use custom role assignments, the role assignment must include tasks that support folder management.</span></span>

|<span data-ttu-id="4070a-128">作法</span><span class="sxs-lookup"><span data-stu-id="4070a-128">To do this</span></span>|<span data-ttu-id="4070a-129">包括下列工作</span><span class="sxs-lookup"><span data-stu-id="4070a-129">Include these tasks</span></span>|
|----------------|-------------------------|
|<span data-ttu-id="4070a-130">將 .rdl 檔案上傳至資料夾</span><span class="sxs-lookup"><span data-stu-id="4070a-130">Upload an .rdl file to a folder</span></span>|<span data-ttu-id="4070a-131">管理報表</span><span class="sxs-lookup"><span data-stu-id="4070a-131">Manage reports</span></span>|
|<span data-ttu-id="4070a-132">將任何檔案當成二進位物件上傳</span><span class="sxs-lookup"><span data-stu-id="4070a-132">Upload any file as a binary object</span></span>|<span data-ttu-id="4070a-133">管理資源</span><span class="sxs-lookup"><span data-stu-id="4070a-133">Manage resources</span></span>|
|<span data-ttu-id="4070a-134">檢視資料夾的內容</span><span class="sxs-lookup"><span data-stu-id="4070a-134">View the contents of a folder</span></span>|<span data-ttu-id="4070a-135">檢視資源、檢視報表</span><span class="sxs-lookup"><span data-stu-id="4070a-135">View resources, View reports</span></span>|

## <a name="see-also"></a><span data-ttu-id="4070a-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4070a-136">See Also</span></span>
 <span data-ttu-id="4070a-137">[報表管理員 &#40;SSRS 原生模式&#41;].。/report-manager-ssrs-native-mode.md) [在原生模式報表伺服器上](../security/granting-permissions-on-a-native-mode-report-server.md)授[與](../security/tasks-and-permissions.md)許可權[&#40;報表管理員上傳檔案或報表&#41;](../reports/upload-a-file-or-report-report-manager.md)</span><span class="sxs-lookup"><span data-stu-id="4070a-137">[Report Manager  &#40;SSRS Native Mode&#41;]../report-manager-ssrs-native-mode.md) [Granting Permissions on a Native Mode Report Server](../security/granting-permissions-on-a-native-mode-report-server.md) [Tasks and Permissions](../security/tasks-and-permissions.md) [Upload a File or Report &#40;Report Manager&#41;](../reports/upload-a-file-or-report-report-manager.md)</span></span>


