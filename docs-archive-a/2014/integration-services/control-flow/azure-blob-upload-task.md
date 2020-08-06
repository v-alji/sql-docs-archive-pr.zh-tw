---
title: Azure Blob 上傳工作 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.afpblobuptask.f1
- sql11.dts.designer.afpblobuptask.f1
ms.assetid: 6ea068b0-4cd8-45b5-b89d-09b8f25040c0
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0ca15c5a77a2694293981121f4e5927be8ec0e1c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688114"
---
# <a name="azure-blob-upload-task"></a><span data-ttu-id="03f0e-102">Azure Blob 上傳工作</span><span class="sxs-lookup"><span data-stu-id="03f0e-102">Azure Blob Upload Task</span></span>
  <span data-ttu-id="03f0e-103">Azure Blob 上傳工作可讓 SSIS 封裝將檔案上傳到 Azure Blob 儲存體。</span><span class="sxs-lookup"><span data-stu-id="03f0e-103">The Azure Blob Upload Task enables an SSIS package to upload files to an Azure blob storage.</span></span>   
<span data-ttu-id="03f0e-104">若要加入 **Azure Blob 上傳工作**，請將其拖放至 SSIS 設計工具，然後按兩下或在其上按一下滑鼠右鍵，再按一下 [編輯]  ，即可看到以下 [Azure Blob 上傳工作編輯器]  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="03f0e-104">To add an **Azure Blob Upload Task**, drag-drop it to the SSIS Designer, and double-click or right-click and click **Edit** to see the following **Azure Blob Upload Task Editor** dialog box.</span></span>  
  
 <span data-ttu-id="03f0e-105">下表提供此對話方塊中欄位的描述。</span><span class="sxs-lookup"><span data-stu-id="03f0e-105">The following table provides descriptions for the fields in this dialog box.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="03f0e-106">**欄位**</span><span class="sxs-lookup"><span data-stu-id="03f0e-106">**Field**</span></span>|<span data-ttu-id="03f0e-107">**說明**</span><span class="sxs-lookup"><span data-stu-id="03f0e-107">**Description**</span></span>|  
|<span data-ttu-id="03f0e-108">AzureStorageConnection</span><span class="sxs-lookup"><span data-stu-id="03f0e-108">AzureStorageConnection</span></span>|<span data-ttu-id="03f0e-109">指定現有的 Azure 儲存體連線管理員，或建立參考 Azure 儲存體帳戶的新連線管理員，而該儲存體帳戶指向裝載 Blob 檔案之處。</span><span class="sxs-lookup"><span data-stu-id="03f0e-109">Specify an existing Azure Storage Connection Manager or create a new one that refers to an Azure Storage Account, which points to where the blob files are hosted.</span></span>|  
|<span data-ttu-id="03f0e-110">BlobContainer</span><span class="sxs-lookup"><span data-stu-id="03f0e-110">BlobContainer</span></span>|<span data-ttu-id="03f0e-111">指定以 Blob 形式保存上傳之檔案的 Blob 容器名稱。</span><span class="sxs-lookup"><span data-stu-id="03f0e-111">Specifies the name of the blob container that will hold the uploaded files as blobs.</span></span>|  
|<span data-ttu-id="03f0e-112">BlobDirectory</span><span class="sxs-lookup"><span data-stu-id="03f0e-112">BlobDirectory</span></span>|<span data-ttu-id="03f0e-113">指定以區塊 Blob 形式儲存上傳之檔案的 Blob 目錄。</span><span class="sxs-lookup"><span data-stu-id="03f0e-113">Specifies the blob directory where the uploaded file will be stored as a block blob.</span></span> <span data-ttu-id="03f0e-114">Blob 目錄是虛擬的階層式結構。</span><span class="sxs-lookup"><span data-stu-id="03f0e-114">The blob directory is a virtual hierarchical structure.</span></span> <span data-ttu-id="03f0e-115">如果在 Blob 已存在，將會遭到取代。</span><span class="sxs-lookup"><span data-stu-id="03f0e-115">If the blob already exists, it will be replaced.</span></span>|  
|<span data-ttu-id="03f0e-116">LocalDirectory</span><span class="sxs-lookup"><span data-stu-id="03f0e-116">LocalDirectory</span></span>|<span data-ttu-id="03f0e-117">指定含有要上傳之檔案的本機目錄。</span><span class="sxs-lookup"><span data-stu-id="03f0e-117">Specify the local directory that contains the files to be uploaded.</span></span>|  
|<span data-ttu-id="03f0e-118">FileName</span><span class="sxs-lookup"><span data-stu-id="03f0e-118">FileName</span></span>|<span data-ttu-id="03f0e-119">指定名稱篩選器以選取採用指定名稱模式的檔案。</span><span class="sxs-lookup"><span data-stu-id="03f0e-119">Specifies a name filter to select files with the specified name pattern.</span></span> <span data-ttu-id="03f0e-120">例如</span><span class="sxs-lookup"><span data-stu-id="03f0e-120">E.g.</span></span> <span data-ttu-id="03f0e-121">MySheet\*.xls\* 包含 MySheet001.xls 及 MySheetABC.xlsx 等檔案。</span><span class="sxs-lookup"><span data-stu-id="03f0e-121">MySheet\*.xls\* includes files such as MySheet001.xls and MySheetABC.xlsx.</span></span>|  
|<span data-ttu-id="03f0e-122">TimeRangeFrom/TimeRangeTo</span><span class="sxs-lookup"><span data-stu-id="03f0e-122">TimeRangeFrom/TimeRangeTo</span></span>|<span data-ttu-id="03f0e-123">指定時間範圍篩選器。</span><span class="sxs-lookup"><span data-stu-id="03f0e-123">Specifies a time range filter.</span></span> <span data-ttu-id="03f0e-124">將會包含在 **TimeRangeFrom** 之後且 **TimeRangeTo** 之前所修改的檔案。</span><span class="sxs-lookup"><span data-stu-id="03f0e-124">Files modified after **TimeRangeFrom** and before **TimeRangeTo** will be included.</span></span>|  
  
  
