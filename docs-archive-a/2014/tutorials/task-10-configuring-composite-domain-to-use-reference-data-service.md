---
title: 工作10：設定複合定義域使用參考資料服務 |Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 752eefde-8b87-4f54-878e-9963ccbadc8e
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: d70966b4cde110540bf5008eda4e3151fe32f28d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710066"
---
# <a name="task-10-configuring-composite-domain-to-use-reference-data-service"></a><span data-ttu-id="6a952-102">工作 10：設定複合定義域使用參考資料服務</span><span class="sxs-lookup"><span data-stu-id="6a952-102">Task 10: Configuring Composite Domain to Use Reference Data Service</span></span>
  <span data-ttu-id="6a952-103">在這項工作中，您會設定**位址驗證**複合定義域，以使用**Melissa 的資料位址檢查**服務。</span><span class="sxs-lookup"><span data-stu-id="6a952-103">In this task, you configure the **Address Validation** composite domain to use the **Melissa Data - Address Check** service.</span></span> <span data-ttu-id="6a952-104">在執行階段的清理活動期間，DQS 會將地址驗證定義域中的定義域值傳遞給服務以進行清理。</span><span class="sxs-lookup"><span data-stu-id="6a952-104">At runtime, during cleansing activity, DQS passes the values of domains in the Address Validation domain to the service for cleansing.</span></span> <span data-ttu-id="6a952-105">如需詳細資訊，請參閱[將定義域/複合定義域對應至參考資料](https://msdn.microsoft.com/library/hh213030.aspx)。</span><span class="sxs-lookup"><span data-stu-id="6a952-105">See [Map Domain/Composite Domain to Reference Data](https://msdn.microsoft.com/library/hh213030.aspx) for more details.</span></span>  
  
1.  <span data-ttu-id="6a952-106">在**DQS 用戶端**的主頁面中，按一下 [**最近使用的知識庫**] 底下的 [**供應商 (網域管理]) \*\* ，啟動 [**定義域管理\*\*] 頁面。</span><span class="sxs-lookup"><span data-stu-id="6a952-106">In the main page of **DQS Client**, click **Suppliers (Domain Management)** under **Recent Knowledge Bases** to launch the **Domain Management** page.</span></span>  
  
2.  <span data-ttu-id="6a952-107">在**定義域清單**中選取 [**位址驗證**] 複合定義域。</span><span class="sxs-lookup"><span data-stu-id="6a952-107">Select the **Address Validation** composite domain in the **list of domains**.</span></span>  
  
3.  <span data-ttu-id="6a952-108">在右窗格中，切換至 [**參考資料**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="6a952-108">In the right pane, switch to the **Reference Data** tab.</span></span>  
  
     <span data-ttu-id="6a952-109">![[參考資料] 索引標籤](../../2014/tutorials/media/et-configuringcdtouserds-01.jpg "[參考資料] 索引標籤")</span><span class="sxs-lookup"><span data-stu-id="6a952-109">![Reference Data Tab](../../2014/tutorials/media/et-configuringcdtouserds-01.jpg "Reference Data Tab")</span></span>  
  
4.  <span data-ttu-id="6a952-110">按一下工具列上的 **[流覽]** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="6a952-110">Click **Browse** button on the toolbar.</span></span>  
  
5.  <span data-ttu-id="6a952-111">在 [**線上參考資料提供者目錄**] 對話方塊中，選取 [ **Melissa 資料-位址檢查**] 旁的**核取方塊**。</span><span class="sxs-lookup"><span data-stu-id="6a952-111">On the **Online Reference Data Providers Catalog** dialog box, select **check box** next to **Melissa Data - Address Check**.</span></span>  
  
     <span data-ttu-id="6a952-112">![選取 [Melissa Data – 地址檢查]](../../2014/tutorials/media/et-configuringcdtouserds-02.jpg "選取 [Melissa Data – 地址檢查]")</span><span class="sxs-lookup"><span data-stu-id="6a952-112">![Select Melissa Data - Address Check](../../2014/tutorials/media/et-configuringcdtouserds-02.jpg "Select Melissa Data - Address Check")</span></span>  
  
6.  <span data-ttu-id="6a952-113">在右窗格的 [**架構**] 區段中，使用下拉式清單將 [**位址行**] 定義域對應至\*\*位址行 (M) \*\*架構專案。</span><span class="sxs-lookup"><span data-stu-id="6a952-113">In the right pane, in the **Schema** section, map **Address Line** domain to the **Address Line (M)** schema item by using the drop-down list.</span></span>  
  
     <span data-ttu-id="6a952-114">![將 RDS 結構描述項目對應至定義域](../../2014/tutorials/media/et-configuringcdtouserds-03.jpg "將 RDS 結構描述項目對應至定義域")</span><span class="sxs-lookup"><span data-stu-id="6a952-114">![Map RDS Schema Item to Domain](../../2014/tutorials/media/et-configuringcdtouserds-03.jpg "Map RDS Schema Item to Domain")</span></span>  
  
7.  <span data-ttu-id="6a952-115">按一下工具列上的 [\*\*加入架構專案] (+) \*\* ] 按鈕，以在清單中建立專案。</span><span class="sxs-lookup"><span data-stu-id="6a952-115">Click **Add Schema Entry (+)** button on the toolbar to create an entry in the list.</span></span>  
  
     <span data-ttu-id="6a952-116">![[加入架構專案] 工具列按鈕](../../2014/tutorials/media/et-configuringcdtouserds-04.jpg "[加入架構專案] 工具列按鈕")</span><span class="sxs-lookup"><span data-stu-id="6a952-116">![Add Schema Entry Toolbar Button](../../2014/tutorials/media/et-configuringcdtouserds-04.jpg "Add Schema Entry Toolbar Button")</span></span>  
  
8.  <span data-ttu-id="6a952-117">使用下拉式清單對應以下 DQS 定義域，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="6a952-117">Map the following DQS domains by using the drop-down lists as shown in the following picture.</span></span>  
  
     <span data-ttu-id="6a952-118">![將 RDS 結構描述項目對應至定義域](../../2014/tutorials/media/et-configuringcdtouserds-05.jpg "將 RDS 結構描述項目對應至定義域")</span><span class="sxs-lookup"><span data-stu-id="6a952-118">![Map RDS Schema Items to Domains](../../2014/tutorials/media/et-configuringcdtouserds-05.jpg "Map RDS Schema Items to Domains")</span></span>  
  
9. <span data-ttu-id="6a952-119">按一下 **[確定]** ，關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="6a952-119">Click **OK** to close the dialog box.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="6a952-120">後續步驟</span><span class="sxs-lookup"><span data-stu-id="6a952-120">Next Step</span></span>  
 [<span data-ttu-id="6a952-121">工作 11：發行知識庫</span><span class="sxs-lookup"><span data-stu-id="6a952-121">Task 11: Publishing the Knowledge Base</span></span>](../../2014/tutorials/task-11-publishing-the-knowledge-base.md)  
  
  
