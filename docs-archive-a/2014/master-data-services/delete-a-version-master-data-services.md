---
title: 刪除版本 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- versions [Master Data Services], deleting
- deleting versions [Master Data Services]
ms.assetid: 2a4eeffe-8379-4744-ad44-c27d8c8ac9a8
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: f83a3bc396b2a13ac7ac03ef653b16a0d556189a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606390"
---
# <a name="delete-a-version-master-data-services"></a><span data-ttu-id="d2c44-102">刪除版本 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="d2c44-102">Delete a Version (Master Data Services)</span></span>
  <span data-ttu-id="d2c44-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，當您確定不再需要與某個版本有關的主要資料時，可刪除此版本。</span><span class="sxs-lookup"><span data-stu-id="d2c44-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], delete a version when you are sure you no longer need the master data associated with the version.</span></span> <span data-ttu-id="d2c44-104">當您刪除版本之後，就無法擷取關聯的主要資料。</span><span class="sxs-lookup"><span data-stu-id="d2c44-104">After you delete a version, you cannot retrieve the associated master data.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="d2c44-105">如果模型只有一個版本而且您將它刪除，此模型就無法使用。</span><span class="sxs-lookup"><span data-stu-id="d2c44-105">If a model has only one version and you delete it, the model becomes unusable.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="d2c44-106">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="d2c44-106">Prerequisites</span></span>  
 <span data-ttu-id="d2c44-107">若要執行此程序：</span><span class="sxs-lookup"><span data-stu-id="d2c44-107">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="d2c44-108">您在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 資料庫中，必須擁有檢視 mdm.viw_SYSTEM_SCHEMA_VERSION 檢視表的權限以及執行 mds.udpVersionDelete 預存程序的權限。</span><span class="sxs-lookup"><span data-stu-id="d2c44-108">You must have permission to view the mdm.viw_SYSTEM_SCHEMA_VERSION view and to execute the mds.udpVersionDelete stored procedure in the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database.</span></span> <span data-ttu-id="d2c44-109">如需詳細資訊，請參閱[資料庫物件安全性 &#40;Master Data Services&#41;](database-object-security-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="d2c44-109">For more information, see [Database Object Security &#40;Master Data Services&#41;](database-object-security-master-data-services.md).</span></span>  
  
### <a name="to-delete-a-version"></a><span data-ttu-id="d2c44-110">若要刪除版本</span><span class="sxs-lookup"><span data-stu-id="d2c44-110">To delete a version</span></span>  
  
1.  <span data-ttu-id="d2c44-111">開啟 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 並且連接到 [!INCLUDE[ssDE](../includes/ssde-md.md)] 資料庫的 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="d2c44-111">Open [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] and connect to the [!INCLUDE[ssDE](../includes/ssde-md.md)] instance for your [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database.</span></span>  
  
2.  <span data-ttu-id="d2c44-112">開啟 mdm.viw_SYSTEM_SCHEMA_VERSION 檢視表。</span><span class="sxs-lookup"><span data-stu-id="d2c44-112">Open the mdm.viw_SYSTEM_SCHEMA_VERSION view.</span></span>  
  
3.  <span data-ttu-id="d2c44-113">尋找您想要刪除之模型的版本，然後將值複製到 **[識別碼]** 欄位。</span><span class="sxs-lookup"><span data-stu-id="d2c44-113">Find the version of the model you want to delete and copy the value in the **ID** field.</span></span>  
  
4.  <span data-ttu-id="d2c44-114">建立新的查詢。</span><span class="sxs-lookup"><span data-stu-id="d2c44-114">Create a new query.</span></span>  
  
5.  <span data-ttu-id="d2c44-115">輸入下列文字，使用您在步驟 2 複製的值取代 *version_ID* 。</span><span class="sxs-lookup"><span data-stu-id="d2c44-115">Type the following text, replacing *version_ID* with the value you copied in step 2.</span></span>  
  
    ```  
    EXEC [mdm].[udpVersionDelete] @Version_ID='version_ID'  
    ```  
  
6.  <span data-ttu-id="d2c44-116">執行查詢。</span><span class="sxs-lookup"><span data-stu-id="d2c44-116">Run the query.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d2c44-117">您可能需要等候幾分鐘，Web 應用程式才會反映變更。</span><span class="sxs-lookup"><span data-stu-id="d2c44-117">You may have to wait a few minutes before the Web application reflects the change.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2c44-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d2c44-118">See Also</span></span>  
 <span data-ttu-id="d2c44-119">[版本 &#40;Master Data Services&#41;](../../2014/master-data-services/versions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="d2c44-119">[Versions &#40;Master Data Services&#41;](../../2014/master-data-services/versions-master-data-services.md) </span></span>  
 [<span data-ttu-id="d2c44-120">複製版本 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="d2c44-120">Copy a Version &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/copy-a-version-master-data-services.md)  
  
  
