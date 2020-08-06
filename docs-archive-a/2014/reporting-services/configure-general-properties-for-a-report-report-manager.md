---
title: 設定報表 (報表管理員) 的一般屬性 |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- reports [Reporting Services], properties
- properties [Reporting Services], general
ms.assetid: 10b941b2-28e6-4408-9ee4-acebc63c8496
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f30900158591afcd5997053dbb61cc22b495ed10
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707278"
---
# <a name="configure-general-properties-for-a-report-report-manager"></a><span data-ttu-id="2135a-102">設定報表的一般屬性 (報表管理員)</span><span class="sxs-lookup"><span data-stu-id="2135a-102">Configure General Properties for a Report (Report Manager)</span></span>
  
### <a name="to-configure-general-report-properties"></a><span data-ttu-id="2135a-103">若要設定一般報表屬性</span><span class="sxs-lookup"><span data-stu-id="2135a-103">To configure general report properties</span></span>

1.  <span data-ttu-id="2135a-104">啟動 [報表管理員 &#40;SSRS 原生模式&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="2135a-104">Start [Report Manager  &#40;SSRS Native Mode&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md).</span></span>

2.  <span data-ttu-id="2135a-105">在報表管理員中，導覽至 **[內容]** 頁面。</span><span class="sxs-lookup"><span data-stu-id="2135a-105">In Report Manager, navigate to the **Contents** page.</span></span> <span data-ttu-id="2135a-106">導覽到您要設定一般屬性的報表，並開啟該報表。</span><span class="sxs-lookup"><span data-stu-id="2135a-106">Navigate to the report that you want to configure general properties for and open it.</span></span>

3.  <span data-ttu-id="2135a-107">按一下 [屬性] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="2135a-107">Click the **Properties** tab.</span></span>

     <span data-ttu-id="2135a-108">或者，如果 [**內容**] 頁面是在詳細資料檢視中，請按一下 [屬性頁] 圖示：</span><span class="sxs-lookup"><span data-stu-id="2135a-108">Or, if the **Contents** page is in Details view, click the property page icon:</span></span>

     <span data-ttu-id="2135a-109">![屬性頁圖示](media/prop.gif "屬性頁面圖示")</span><span class="sxs-lookup"><span data-stu-id="2135a-109">![Property page icon](media/prop.gif "Property page icon")</span></span>

4.  <span data-ttu-id="2135a-110">[**一般**屬性] 頁面隨即顯示，而且您可以設定屬性，如下所示：</span><span class="sxs-lookup"><span data-stu-id="2135a-110">The **General** properties page is displayed, and you can configure properties as follows:</span></span>

    -   <span data-ttu-id="2135a-111">在 [**屬性**] 區段中，您可以修改報告名稱和描述。</span><span class="sxs-lookup"><span data-stu-id="2135a-111">In the **Properties** section, you can modify the report name and description.</span></span>

    -   <span data-ttu-id="2135a-112">您可以選取 [**在清單視圖中隱藏**] 核取方塊，以在預設頁面配置中開啟頁面時隱藏專案 (清單視圖]) 這會在頁面上上下排列專案。</span><span class="sxs-lookup"><span data-stu-id="2135a-112">You can select the **Hide in list view** checkbox to hide the item when the page is opened in the default page layout (list view) which arranges items across and down the page.</span></span>

    -   <span data-ttu-id="2135a-113">在 [**報表定義**] 區段中，按一下 [**編輯**]，將報表定義的複本解壓縮。</span><span class="sxs-lookup"><span data-stu-id="2135a-113">In the **Report Definition** section, click **Edit** to extract a copy of the report definition.</span></span> <span data-ttu-id="2135a-114">您在本機對報表定義所做的修改不會儲存在報表伺服器上。</span><span class="sxs-lookup"><span data-stu-id="2135a-114">Modifications that you make locally to the report definition are not saved on the report server.</span></span>

         <span data-ttu-id="2135a-115">或者，若要從 .rdl 檔案更新報表定義，請按一下 [**更新**]。</span><span class="sxs-lookup"><span data-stu-id="2135a-115">Or, to update the report definition from an .rdl file, click **Update**.</span></span>

        > [!NOTE]
        >  <span data-ttu-id="2135a-116">如果更新報表定義，必須在完成更新之後重設資料來源設定。</span><span class="sxs-lookup"><span data-stu-id="2135a-116">If you update a report definition, you must reset the data source settings after the update is completed.</span></span>

    -   <span data-ttu-id="2135a-117">使用 [**刪除**] 或 [**移動**] 按鈕來刪除或移動報表。</span><span class="sxs-lookup"><span data-stu-id="2135a-117">Use the **Delete** or **Move** buttons to delete or move the report.</span></span>

    -   <span data-ttu-id="2135a-118">您也可以建立連結報表。</span><span class="sxs-lookup"><span data-stu-id="2135a-118">You can also create a linked report.</span></span>

5.  <span data-ttu-id="2135a-119">當您完成設定報表的一般屬性時，**請按一下 [** 套用]。</span><span class="sxs-lookup"><span data-stu-id="2135a-119">When you have finished configuring general properties for the report, click **Apply**.</span></span>

## <a name="see-also"></a><span data-ttu-id="2135a-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2135a-120">See Also</span></span>
 <span data-ttu-id="2135a-121">[移動或刪除專案 &#40;報表管理員&#41;](report-server/move-or-delete-an-item-report-manager.md) [內容] 頁面 &#40;報表管理員](../../2014/reporting-services/contents-page-report-manager.md)&#41;[尋找、查看和管理報表 &#40;報表產生器和 SSRS &#41;](report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md) [一般屬性頁面、報表 &#40;報表管理員&#41;](../../2014/reporting-services/general-properties-page-reports-report-manager.md)</span><span class="sxs-lookup"><span data-stu-id="2135a-121">[Move or Delete an Item &#40;Report Manager&#41;](report-server/move-or-delete-an-item-report-manager.md) [Contents Page &#40;Report Manager&#41;](../../2014/reporting-services/contents-page-report-manager.md) [Finding, Viewing, and Managing Reports &#40;Report Builder and SSRS &#41;](report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md) [General Properties Page, Reports &#40;Report Manager&#41;](../../2014/reporting-services/general-properties-page-reports-report-manager.md)</span></span>


