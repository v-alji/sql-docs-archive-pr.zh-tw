---
title: 目的地資料庫檔案 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transferdatabasetask.destdbfiles.f1
ms.assetid: f6f90417-86fb-4b8c-a790-0b215c344ef6
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0d0ab2c0ff39fc728afc17b59f0d4bae076e4022
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599609"
---
# <a name="destination-database-files"></a><span data-ttu-id="f63e0-102">目的地資料庫檔案</span><span class="sxs-lookup"><span data-stu-id="f63e0-102">Destination Database Files</span></span>
  <span data-ttu-id="f63e0-103">使用 **[目的地資料庫檔案]** 對話方塊，即可檢視或變更目的地伺服器上的資料庫檔案名稱和位置，或是指定傳送資料庫工作的網路檔案位置。</span><span class="sxs-lookup"><span data-stu-id="f63e0-103">Use the **Destination Database Files** dialog box to view or change the database file names and locations on the destination server, or to specify a network file location for the Transfer Database task.</span></span> <span data-ttu-id="f63e0-104">如需這項工作的詳細資訊，請參閱 [傳送資料庫工作](control-flow/transfer-database-task.md)。</span><span class="sxs-lookup"><span data-stu-id="f63e0-104">For more information about this task, see [Transfer Database Task](control-flow/transfer-database-task.md).</span></span>  
  
 <span data-ttu-id="f63e0-105">若要使用來源伺服器上的資料庫檔案名稱和位置，來自動擴展此對話方塊，請先在 **[傳送資料庫工作編輯器]** 對話方塊的 **[資料庫]** 頁面中，指定 **[SourceConnection]** 、 **[SourceDatabaseName]** 和 **[SourceDatabaseFiles]** 。</span><span class="sxs-lookup"><span data-stu-id="f63e0-105">To automatically populate this dialog box with the database file names and locations on the source server, specify the **SourceConnection**, **SourceDatabaseName**, and **SourceDatabaseFiles** first in the **Databases** page of the **Transfer Database Task Editor** dialog box.</span></span>  
  
## <a name="options"></a><span data-ttu-id="f63e0-106">選項。</span><span class="sxs-lookup"><span data-stu-id="f63e0-106">Options</span></span>  
 <span data-ttu-id="f63e0-107">**目的地檔案**</span><span class="sxs-lookup"><span data-stu-id="f63e0-107">**Destination File**</span></span>  
 <span data-ttu-id="f63e0-108">目的地伺服器上已傳送資料庫檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="f63e0-108">Names of the transferred database files on the destination server.</span></span>  
  
 <span data-ttu-id="f63e0-109">輸入檔案名稱，或是按一下檔案名稱來編輯它。</span><span class="sxs-lookup"><span data-stu-id="f63e0-109">Enter the file name, or click the file name to edit it.</span></span>  
  
 <span data-ttu-id="f63e0-110">**目的資料夾**</span><span class="sxs-lookup"><span data-stu-id="f63e0-110">**Destination Folder**</span></span>  
 <span data-ttu-id="f63e0-111">目的地伺服器上的資料夾，用於存放將傳送的資料庫檔案。</span><span class="sxs-lookup"><span data-stu-id="f63e0-111">Folder on the destination server where the database files will be transferred to.</span></span>  
  
 <span data-ttu-id="f63e0-112">輸入資料夾路徑，按一下該資料夾路徑來編輯它，或是按一下瀏覽來找出在目的地伺服器上的資料夾，以存放要傳送的資料庫檔案。</span><span class="sxs-lookup"><span data-stu-id="f63e0-112">Enter the folder path, click the folder path to edit it, or click browse to locate the folder where you want to transfer the database files on the destination server.</span></span>  
  
 <span data-ttu-id="f63e0-113">**網路檔案共用**</span><span class="sxs-lookup"><span data-stu-id="f63e0-113">**Network File Share**</span></span>  
 <span data-ttu-id="f63e0-114">在目的地伺服器上的網路共用資料夾，其中存放要傳送的資料庫檔案。</span><span class="sxs-lookup"><span data-stu-id="f63e0-114">Network shared folder on the destination server where the database files will be transferred to.</span></span> <span data-ttu-id="f63e0-115">當您在 **[傳送資料庫工作編輯器]** 對話方塊的 **[資料庫]** 頁面中，將 **[方法]** 指定為 **[DatabaseOffline]** ，以離線模式傳送資料庫時，請使用 **[網路檔案共用]** 。</span><span class="sxs-lookup"><span data-stu-id="f63e0-115">Use **Network file share** when you transfer a database in offline mode by specifying **DatabaseOffline** for **Method** in the **Databases** page of the **Transfer Database Task Editor** dialog box.</span></span>  
  
 <span data-ttu-id="f63e0-116">輸入網路檔案共用位置，或是按一下瀏覽來找出網路檔案共用位置。</span><span class="sxs-lookup"><span data-stu-id="f63e0-116">Enter the network file share location, or click browse to locate the network file share location.</span></span>  
  
 <span data-ttu-id="f63e0-117">當您以離線模式傳送資料庫時，在將資料庫檔案傳送到 **[目的資料夾]** 位置之前，會將其複製到 **[網路檔案共用]** 位置。</span><span class="sxs-lookup"><span data-stu-id="f63e0-117">When you transfer a database in offline mode, the database files are copied to the **Network file share** location before they are transferred to the **Destination folder** location.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f63e0-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f63e0-118">See Also</span></span>  
 <span data-ttu-id="f63e0-119">[Integration Services 錯誤和訊息參考](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="f63e0-119">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="f63e0-120">[[傳送資料庫工作編輯器] &#40;一般頁面&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="f63e0-120">[Transfer Database Task Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 [<span data-ttu-id="f63e0-121">傳送資料庫工作編輯器 &#40;資料庫頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="f63e0-121">Transfer Database Task Editor &#40;Databases Page&#41;</span></span>](../../2014/integration-services/transfer-database-task-editor-databases-page.md)  
  
  
