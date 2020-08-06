---
title: Azure Blob 下載工作 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.afpblobdltask.f1
- sql11.dts.designer.afpblobdltask.f1
ms.assetid: 8a63bf44-71be-456d-9a5c-be7c31aff065
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e2f61260b1fceaad3c27a0ce6ab6af28b15582bc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688117"
---
# <a name="azure-blob-download-task"></a><span data-ttu-id="91b11-102">Azure Blob 下載工作</span><span class="sxs-lookup"><span data-stu-id="91b11-102">Azure Blob Download Task</span></span>
  <span data-ttu-id="91b11-103">Azure Blob 下載工作可讓 SSIS 封裝能從 Azure Blob 儲存體下載檔案。</span><span class="sxs-lookup"><span data-stu-id="91b11-103">The Azure Blob Download Task enables an SSIS package to download files from an Azure blob storage.</span></span>   
<span data-ttu-id="91b11-104">若要加入 **Azure Blob 下載工作**，請將其拖放至 SSIS 設計工具，然後按兩下或按一下滑鼠右鍵，再按一下 [編輯]  ，即可看到以下 [Azure Blob 下載工作編輯器]  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="91b11-104">To add an **Azure Blob Download Task**, drag-drop it to the SSIS Designer, and double-click or right-click and click **Edit** to see the following **Azure Blob Download Task Editor** dialog box.</span></span>  
  
 <span data-ttu-id="91b11-105">下表提供此對話方塊中欄位的描述。</span><span class="sxs-lookup"><span data-stu-id="91b11-105">The following table provides description for the fields in this dialog box.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="91b11-106">**欄位**</span><span class="sxs-lookup"><span data-stu-id="91b11-106">**Field**</span></span>|<span data-ttu-id="91b11-107">**說明**</span><span class="sxs-lookup"><span data-stu-id="91b11-107">**Description**</span></span>|  
|<span data-ttu-id="91b11-108">AzureStorageConnection</span><span class="sxs-lookup"><span data-stu-id="91b11-108">AzureStorageConnection</span></span>|<span data-ttu-id="91b11-109">指定現有的 Azure 儲存體連線管理員，或建立參考 Azure 儲存體帳戶的新連線管理員，而該儲存體帳戶指向裝載 Blob 檔案之處。</span><span class="sxs-lookup"><span data-stu-id="91b11-109">Specify an existing Azure Storage Connection Manager or create a new one that refers to an Azure Storage Account, which points to where the blob files are hosted.</span></span>|  
|<span data-ttu-id="91b11-110">BlobContainer</span><span class="sxs-lookup"><span data-stu-id="91b11-110">BlobContainer</span></span>|<span data-ttu-id="91b11-111">指定包含要下載的 Blob 檔案之 Blob 容器的名稱。</span><span class="sxs-lookup"><span data-stu-id="91b11-111">Specifies the name of the blob container that contains the blob files to be downloaded.</span></span>|  
|<span data-ttu-id="91b11-112">BlobDirectory</span><span class="sxs-lookup"><span data-stu-id="91b11-112">BlobDirectory</span></span>|<span data-ttu-id="91b11-113">指定包含要下載之 Blob 檔案的 Blob 目錄。</span><span class="sxs-lookup"><span data-stu-id="91b11-113">Specifies the blob directory that contains the blob files to be downloaded.</span></span> <span data-ttu-id="91b11-114">Blob 目錄是虛擬的階層式結構。</span><span class="sxs-lookup"><span data-stu-id="91b11-114">The blob directory is a virtual hierarchical structure.</span></span>|  
|<span data-ttu-id="91b11-115">LocalDirectory</span><span class="sxs-lookup"><span data-stu-id="91b11-115">LocalDirectory</span></span>|<span data-ttu-id="91b11-116">指定將儲存已下載之 Blob 檔案的本機目錄。</span><span class="sxs-lookup"><span data-stu-id="91b11-116">Specifies the local directory where the downloaded blob files will be stored.</span></span>|  
|<span data-ttu-id="91b11-117">FileName</span><span class="sxs-lookup"><span data-stu-id="91b11-117">FileName</span></span>|<span data-ttu-id="91b11-118">指定名稱篩選器以選取採用指定名稱模式的檔案。</span><span class="sxs-lookup"><span data-stu-id="91b11-118">Specifies a name filter to select files with the specified name pattern.</span></span> <span data-ttu-id="91b11-119">例如</span><span class="sxs-lookup"><span data-stu-id="91b11-119">E.g.</span></span> <span data-ttu-id="91b11-120">MySheet\*.xls\* 包含 MySheet001.xls 及 MySheetABC.xlsx 等檔案。</span><span class="sxs-lookup"><span data-stu-id="91b11-120">MySheet\*.xls\* includes files such as MySheet001.xls and MySheetABC.xlsx.</span></span>|  
|<span data-ttu-id="91b11-121">TimeRangeFrom/TimeRangeTo</span><span class="sxs-lookup"><span data-stu-id="91b11-121">TimeRangeFrom/TimeRangeTo</span></span>|<span data-ttu-id="91b11-122">指定時間範圍篩選器。</span><span class="sxs-lookup"><span data-stu-id="91b11-122">Specifies a time range filter.</span></span> <span data-ttu-id="91b11-123">將會包含在 **TimeRangeFrom** 之後且 **TimeRangeTo** 之前所修改的檔案。</span><span class="sxs-lookup"><span data-stu-id="91b11-123">Files modified after **TimeRangeFrom** and before **TimeRangeTo** will be included.</span></span>|  
  
  
