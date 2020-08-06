---
title: Azure Data Lake Store 檔案系統工作 | Microsoft Docs
ms.custom: ''
ms.date: 01/09/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- SQL12.DTS.DESIGNER.AFPADLSTASK.F1
- SQL11.DTS.DESIGNER.AFPADLSTASK.F1
ms.assetid: 02b9edd7-6ef9-463e-abbf-e1830bcae875
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1bc37e774c5346190635e50259deb47f2f22a054
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597298"
---
# <a name="azure-data-lake-store-file-system-task"></a><span data-ttu-id="159cc-102">Azure Data Lake Store 檔案系統工作</span><span class="sxs-lookup"><span data-stu-id="159cc-102">Azure Data Lake Store File System Task</span></span>

<span data-ttu-id="159cc-103">**Azure Data Lake 儲存區檔案系統**工作可讓使用者在 Azure Data Lake 存放區上執行各種檔案系統作業， [ (ADLS) ](https://azure.microsoft.com/services/data-lake-store/)。</span><span class="sxs-lookup"><span data-stu-id="159cc-103">The **Azure Data Lake Store File System Task** enables users to perform various file system operations on [Azure Data Lake Store (ADLS)](https://azure.microsoft.com/services/data-lake-store/).</span></span>

<span data-ttu-id="159cc-104">若要將 Azure Data Lake Store 檔案系統工作新增至套件，請將它從 SSIS 工具箱拖曳至設計工具畫布。</span><span class="sxs-lookup"><span data-stu-id="159cc-104">To add an Azure Data Lake Store File System Task to a package, drag it from SSIS Toolbox to the designer canvas.</span></span> <span data-ttu-id="159cc-105">然後按兩下該工作，或以滑鼠右鍵按一下工作並選取 [**編輯**]，以開啟 [工作編輯器] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="159cc-105">Then double-click the task, or right-click the task and select **Edit**, to open the task editor dialog box.</span></span>

<span data-ttu-id="159cc-106">**Operation** 屬性會指定要執行的檔案系統作業。</span><span class="sxs-lookup"><span data-stu-id="159cc-106">The **Operation** property specifies the file system operation to perform.</span></span> <span data-ttu-id="159cc-107">支援下列作業。</span><span class="sxs-lookup"><span data-stu-id="159cc-107">The following operations are supported.</span></span>

* <span data-ttu-id="159cc-108">**CopyToADLS：** 將檔案上傳至 ADLS。</span><span class="sxs-lookup"><span data-stu-id="159cc-108">**CopyToADLS:** Upload files to ADLS.</span></span>
* <span data-ttu-id="159cc-109">**CopyFromADLS：** 從 ADLS 下載檔案。</span><span class="sxs-lookup"><span data-stu-id="159cc-109">**CopyFromADLS:** Download files from ADLS.</span></span>

<span data-ttu-id="159cc-110">任何作業都必須指定 Azure Data Lake 連線管理員。</span><span class="sxs-lookup"><span data-stu-id="159cc-110">For any operation, you have to specify an Azure Data Lake connection manager.</span></span>

<span data-ttu-id="159cc-111">以下是每個作業特定屬性的描述。</span><span class="sxs-lookup"><span data-stu-id="159cc-111">Here are the descriptions of the properties specific to each operation.</span></span>

## <a name="copytoadls"></a><span data-ttu-id="159cc-112">CopyToADLS</span><span class="sxs-lookup"><span data-stu-id="159cc-112">CopyToADLS</span></span>

* <span data-ttu-id="159cc-113">**LocalDirectory：** 指定包含要上傳之檔案的來原始目錄。</span><span class="sxs-lookup"><span data-stu-id="159cc-113">**LocalDirectory:** Specifies the source directory which contains files to upload.</span></span>
* <span data-ttu-id="159cc-114">**FileNamePattern：** 指定來源檔案的檔案名稱篩選。</span><span class="sxs-lookup"><span data-stu-id="159cc-114">**FileNamePattern:** Specifies a file name filter for source files.</span></span> <span data-ttu-id="159cc-115">只會上傳名稱符合指定模式的檔案。</span><span class="sxs-lookup"><span data-stu-id="159cc-115">Only files whose name matches the specified pattern will be uploaded.</span></span> <span data-ttu-id="159cc-116">支援萬用字元 `*` 和 `?`。</span><span class="sxs-lookup"><span data-stu-id="159cc-116">Wildcards `*` and `?` are supported.</span></span>
* <span data-ttu-id="159cc-117">**SearchRecursively：** 指定是否以遞迴方式在要上傳檔案的來源目錄中搜尋。</span><span class="sxs-lookup"><span data-stu-id="159cc-117">**SearchRecursively:** Specifies whether to search recursively within the source directory for files to upload.</span></span>
* <span data-ttu-id="159cc-118">**AzureDataLakeDirectory：** 指定檔案上傳位置的 ADLS 目的地目錄。</span><span class="sxs-lookup"><span data-stu-id="159cc-118">**AzureDataLakeDirectory:** Specifies the ADLS destination directory to upload files to.</span></span>
* <span data-ttu-id="159cc-119">**FileExpiry：** 指定要上傳至 ADLS 之檔案的到期日期和時間，或將此屬性保留空白，表示檔案永不過期。</span><span class="sxs-lookup"><span data-stu-id="159cc-119">**FileExpiry:** Specifies an expiration date and time for the files uploaded to ADLS, or leave this property blank to indicate that the files never expire.</span></span>

## <a name="copyfromadls"></a><span data-ttu-id="159cc-120">CopyFromADLS</span><span class="sxs-lookup"><span data-stu-id="159cc-120">CopyFromADLS</span></span>

* <span data-ttu-id="159cc-121">**AzureDataLakeDirectory：** 指定包含要下載檔案的 ADLS 來源目錄。</span><span class="sxs-lookup"><span data-stu-id="159cc-121">**AzureDataLakeDirectory:** Specifies the ADLS source directory which contains the files to download.</span></span>
* <span data-ttu-id="159cc-122">**SearchRecursively：** 指定是否以遞迴方式在要下載檔案的來源目錄中搜尋。</span><span class="sxs-lookup"><span data-stu-id="159cc-122">**SearchRecursively:** Specifies whether to search recursively within the source directory for files to download.</span></span>
* <span data-ttu-id="159cc-123">**LocalDirectory：** 指定儲存下載檔案的目的地目錄。</span><span class="sxs-lookup"><span data-stu-id="159cc-123">**LocalDirectory:** Specifies the destination directory to store downloaded files.</span></span>
