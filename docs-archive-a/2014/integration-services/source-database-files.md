---
title: 源資料庫檔案 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transferdatabasetask.sourcedbfiles.f1
ms.assetid: 7dc6bfeb-37c1-45e8-a705-a87564922265
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 31f0c0e0c633ead0c093bdc8e1f20c9b8f23cc28
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709702"
---
# <a name="source-database-files"></a><span data-ttu-id="2f15f-102">來源資料庫檔案</span><span class="sxs-lookup"><span data-stu-id="2f15f-102">Source database files</span></span>
  <span data-ttu-id="2f15f-103">使用 **[來源資料庫檔案]** 對話方塊，即可檢視來源伺服器上的資料庫檔案名稱和位置，或指定傳送資料庫工作的網路檔案共用位置。</span><span class="sxs-lookup"><span data-stu-id="2f15f-103">Use the **Source Database Files** dialog box to view the database file names and locations on the source server, or to specify a network file share location for the Transfer Database task.</span></span> <span data-ttu-id="2f15f-104">如需這項工作的詳細資訊，請參閱 [傳送資料庫工作](control-flow/transfer-database-task.md)。</span><span class="sxs-lookup"><span data-stu-id="2f15f-104">For more information about this task, see [Transfer Database Task](control-flow/transfer-database-task.md).</span></span>  
  
 <span data-ttu-id="2f15f-105">若要以來源伺服器上的資料庫檔案名稱和位置來擴展此對話方塊，請在 **[傳送資料庫工作編輯器]** 對話方塊的 **[資料庫]** 頁面中，首先指定 **[SourceConnection]** 和 **[SourceDatabaseName]** 。</span><span class="sxs-lookup"><span data-stu-id="2f15f-105">To populate this dialog box with the database file names and locations on the source server, specify the **SourceConnection** and **SourceDatabaseName** first in the **Databases** page of the **Transfer Database Task Editor** dialog box.</span></span>  
  
## <a name="options"></a><span data-ttu-id="2f15f-106">選項。</span><span class="sxs-lookup"><span data-stu-id="2f15f-106">Options</span></span>  
 <span data-ttu-id="2f15f-107">**來源檔案**</span><span class="sxs-lookup"><span data-stu-id="2f15f-107">**Source File**</span></span>  
 <span data-ttu-id="2f15f-108">在來源伺服器上，將會被傳送的資料庫檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="2f15f-108">Database file names on the source server that will be transferred.</span></span> <span data-ttu-id="2f15f-109">**[來源檔案]** 是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="2f15f-109">**Source File** is read only.</span></span>  
  
 <span data-ttu-id="2f15f-110">**來源資料夾**</span><span class="sxs-lookup"><span data-stu-id="2f15f-110">**Source Folder**</span></span>  
 <span data-ttu-id="2f15f-111">在來源伺服器上，要傳送之資料庫檔案所在的資料夾。</span><span class="sxs-lookup"><span data-stu-id="2f15f-111">Folder on the source server where the database files to be transferred reside.</span></span> <span data-ttu-id="2f15f-112">**[來源資料夾]** 是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="2f15f-112">**Source Folder** is read only.</span></span>  
  
 <span data-ttu-id="2f15f-113">**網路檔案共用**</span><span class="sxs-lookup"><span data-stu-id="2f15f-113">**Network File Share**</span></span>  
 <span data-ttu-id="2f15f-114">在來源伺服器上，會從中傳送資料庫檔案的網路共用資料夾。</span><span class="sxs-lookup"><span data-stu-id="2f15f-114">Network shared folder on the source server from where the database files will be transferred.</span></span> <span data-ttu-id="2f15f-115">當您在 **[傳送資料庫工作編輯器]** 對話方塊的 **[資料庫]** 頁面中，將 **[方法]** 指定為 **[DatabaseOffline]** ，以離線模式傳送資料庫時，請使用 **[網路檔案共用]** 。</span><span class="sxs-lookup"><span data-stu-id="2f15f-115">Use **Network File Share** when you transfer a database in offline mode by specifying **DatabaseOffline** for **Method** in the **Databases** page of the **Transfer Database Task Editor** dialog box.</span></span>  
  
 <span data-ttu-id="2f15f-116">輸入網路檔案共用位置，或按一下瀏覽按鈕 **(...)** 以尋找網路檔案共用位置。</span><span class="sxs-lookup"><span data-stu-id="2f15f-116">Enter the network file share location, or click the browse button **(...)** to locate the network file share location.</span></span>  
  
 <span data-ttu-id="2f15f-117">在離線模式中傳送資料庫時，資料庫檔案會複製到來源伺服器上的 **[網路檔案共用]** 位置之後，才傳送到目的地伺服器。</span><span class="sxs-lookup"><span data-stu-id="2f15f-117">When you transfer a database in offline mode, the database files are copied to the **Network file share** location on the source server before they are transferred to the destination server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f15f-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2f15f-118">See Also</span></span>  
 <span data-ttu-id="2f15f-119">[Integration Services 錯誤和訊息參考](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="2f15f-119">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="2f15f-120">[[傳送資料庫工作編輯器] &#40;一般頁面&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="2f15f-120">[Transfer Database Task Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 [<span data-ttu-id="2f15f-121">傳送資料庫工作編輯器 &#40;資料庫頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="2f15f-121">Transfer Database Task Editor &#40;Databases Page&#41;</span></span>](../../2014/integration-services/transfer-database-task-editor-databases-page.md)  
  
  
