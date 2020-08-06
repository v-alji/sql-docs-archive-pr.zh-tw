---
title: 分割區 Wizard F1 說明 (Analysis Services-多維度資料) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Partition Wizard
ms.assetid: 3b6d7053-aeef-4d9e-af70-f5b40256e859
author: minewiskan
ms.author: owend
ms.openlocfilehash: fa8c0e94c2b18ffbd1228752bd7cb4ad4f684acb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593646"
---
# <a name="partition-wizard-f1-help-analysis-services---multidimensional-data"></a><span data-ttu-id="91604-102">資料分割精靈 F1 說明 (Analysis Services - 多維度資料)</span><span class="sxs-lookup"><span data-stu-id="91604-102">Partition Wizard F1 Help (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="91604-103">您可以使用資料分割精靈來定義 Cube 中之量值群組的資料分割。</span><span class="sxs-lookup"><span data-stu-id="91604-103">You can use the Partition Wizard to define partitions for a measure group in a cube.</span></span> <span data-ttu-id="91604-104">依預設，會為 Cube 中的每一個量值群組定義單一資料分割。</span><span class="sxs-lookup"><span data-stu-id="91604-104">By default, a single partition is defined for each measure group in a cube.</span></span> <span data-ttu-id="91604-105">但是，大型的資料分割會使存取和處理效能降低。</span><span class="sxs-lookup"><span data-stu-id="91604-105">Access and processing performance, however, can degrade for large partitions.</span></span> <span data-ttu-id="91604-106">藉由建立多個分割區，每一個分割區包含量值群組的一部份資料，這樣可以增進該量值群組的存取和處理效能。</span><span class="sxs-lookup"><span data-stu-id="91604-106">By creating multiple partitions, each containing a portion of the data for a measure group, you can improve the access and processing performance for that measure group.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="91604-107">建立的資料分割中，可能會因為 [指定來源資訊]\*\*\*\* 或 [限制資料列]\*\*\*\* 頁面中包含了重複的資料列，而含有不正確的資料。</span><span class="sxs-lookup"><span data-stu-id="91604-107">It is possible to create partitions that may contain incorrect data by including duplicate rows in the **Specify Source Information** or **Restrict Rows** pages.</span></span>  
  
 <span data-ttu-id="91604-108">分割區精靈會引導您完成下列步驟：</span><span class="sxs-lookup"><span data-stu-id="91604-108">The Partition Wizard guides you through the following steps:</span></span>  
  
-   <span data-ttu-id="91604-109">選取資料分割的資料來源檢視。</span><span class="sxs-lookup"><span data-stu-id="91604-109">Selecting the data source view for the partition.</span></span>  
  
-   <span data-ttu-id="91604-110">為包含在資料分割中的記錄建立篩選。</span><span class="sxs-lookup"><span data-stu-id="91604-110">Creating a filter for the records included in the partition.</span></span>  
  
-   <span data-ttu-id="91604-111">設定處理和儲存位置。</span><span class="sxs-lookup"><span data-stu-id="91604-111">Setting the processing and storage locations.</span></span>  
  
-   <span data-ttu-id="91604-112">命名和儲存資料分割。</span><span class="sxs-lookup"><span data-stu-id="91604-112">Naming and saving the partition.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="91604-113">本節內容</span><span class="sxs-lookup"><span data-stu-id="91604-113">In This Section</span></span>  
  
-   [<span data-ttu-id="91604-114">&#40;分割區 Wizard&#41;指定來源資訊</span><span class="sxs-lookup"><span data-stu-id="91604-114">Specify Source Information &#40;Partition Wizard&#41;</span></span>](specify-source-information-partition-wizard.md)  
  
-   [<span data-ttu-id="91604-115">限制資料列 &#40;分割區 Wizard&#41;</span><span class="sxs-lookup"><span data-stu-id="91604-115">Restrict Rows &#40;Partition Wizard&#41;</span></span>](restrict-rows-partition-wizard.md)  
  
-   [<span data-ttu-id="91604-116">&#40;分割區 Wizard&#41;的處理和儲存位置</span><span class="sxs-lookup"><span data-stu-id="91604-116">Processing and Storage Locations &#40;Partition Wizard&#41;</span></span>](processing-and-storage-locations-partition-wizard.md)  
  
-   [<span data-ttu-id="91604-117">正在完成 Wizard &#40;Partition Wizard&#41;</span><span class="sxs-lookup"><span data-stu-id="91604-117">Completing the Wizard &#40;Partition Wizard&#41;</span></span>](completing-the-wizard-partition-wizard.md)  
  
-   <span data-ttu-id="91604-118">[[流覽遠端資料夾] 對話方塊 &#40;Analysis Services-多維度資料&#41;](browse-for-remote-folder-dialog-box-analysis-services-multidimensional-data.md)</span><span class="sxs-lookup"><span data-stu-id="91604-118">[Browse for Remote Folder Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](browse-for-remote-folder-dialog-box-analysis-services-multidimensional-data.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91604-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="91604-119">See Also</span></span>  
 [<span data-ttu-id="91604-120">資料分割 &#40;Analysis Services - 多維度資料&#41;</span><span class="sxs-lookup"><span data-stu-id="91604-120">Partitions &#40;Analysis Services - Multidimensional Data&#41;</span></span>](multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data.md)  
  
  
