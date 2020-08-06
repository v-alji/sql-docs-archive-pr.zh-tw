---
title: 工作9：設定參考資料服務 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: d0535fce-2bf5-4f6d-b517-ffe6fa13738d
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 1e7c685de13a2f5c495482f816818ff6b838fc7e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710005"
---
# <a name="task-9-configuring-a-reference-data-service"></a><span data-ttu-id="26ea4-102">工作 9：設定參考資料服務</span><span class="sxs-lookup"><span data-stu-id="26ea4-102">Task 9: Configuring a Reference Data Service</span></span>
  <span data-ttu-id="26ea4-103">在這項工作中，您會設定 DQS 在 Azure Marketplace 上使用參考資料服務。</span><span class="sxs-lookup"><span data-stu-id="26ea4-103">In this task, you configure DQS to use a Reference Data Service on Azure Marketplace.</span></span> <span data-ttu-id="26ea4-104">在下一項工作中，您會將**位址驗證**網域設定為使用此服務。</span><span class="sxs-lookup"><span data-stu-id="26ea4-104">In the next task, you will configure the **Address Validation** domain to use this service.</span></span> <span data-ttu-id="26ea4-105">在執行時間，在清理活動期間，DQS 會將**位址驗證**定義域中的定義域值傳遞給服務以進行清理。</span><span class="sxs-lookup"><span data-stu-id="26ea4-105">At runtime, during cleansing activity, DQS passes the values of domains in the **Address Validation** domain to the service for cleansing.</span></span> <span data-ttu-id="26ea4-106">如需詳細資訊，請參閱[設定 DQS 使用參考資料](https://msdn.microsoft.com/library/hh213070.aspx)。</span><span class="sxs-lookup"><span data-stu-id="26ea4-106">See [Configure DQS to Use Reference Data](https://msdn.microsoft.com/library/hh213070.aspx) for more details.</span></span>  
  
1.  <span data-ttu-id="26ea4-107">在**DQS 用戶端**的主頁面中 **，按一下 [** 系統**管理**] 窗格中的 [設定]。</span><span class="sxs-lookup"><span data-stu-id="26ea4-107">In the main page of **DQS Client**, in the **Administration** pane, click **Configuration**.</span></span>  
  
2.  <span data-ttu-id="26ea4-108">確定 [**參考資料**] 索引標籤為作用中狀態。</span><span class="sxs-lookup"><span data-stu-id="26ea4-108">Ensure that **Reference Data** tab is active.</span></span>  
  
3.  <span data-ttu-id="26ea4-109">如果您需要使用 proxy 伺服器連線到網際網路，請在 [**網路設定**] 區域中，于 [ **proxy 伺服器**] 和 [**埠**] 欄位中輸入適當的值。</span><span class="sxs-lookup"><span data-stu-id="26ea4-109">In the **Network Settings** area, type appropriate values in the **Proxy Server** and **Port** fields if you need to use a proxy server to connect to Internet.</span></span>  
  
4.  <span data-ttu-id="26ea4-110">輸入 [ **DataMarket 帳戶識別碼**] 欄位的**Azure Marketplace 帳戶金鑰**。</span><span class="sxs-lookup"><span data-stu-id="26ea4-110">Type your **Azure Marketplace Account Key** for the **DataMarket Account ID** field.</span></span>  
  
     <span data-ttu-id="26ea4-111">![Azure DataMarket 參考資料服務帳戶](../../2014/tutorials/media/et-configuringareferencedataservice.jpg "Azure DataMarket 參考資料服務帳戶")</span><span class="sxs-lookup"><span data-stu-id="26ea4-111">![Azure Data Market Reference Data Service Account](../../2014/tutorials/media/et-configuringareferencedataservice.jpg "Azure Data Market Reference Data Service Account")</span></span>  
  
5.  <span data-ttu-id="26ea4-112">按一下文字方塊旁的 [**驗證**] 按鈕，以驗證帳戶識別碼。</span><span class="sxs-lookup"><span data-stu-id="26ea4-112">Click **Validate** button next to the text box to validate the account ID.</span></span>  
  
6.  <span data-ttu-id="26ea4-113">在訊息方塊上按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="26ea4-113">Click **OK** on the message box.</span></span>  
  
7.  <span data-ttu-id="26ea4-114">按一下頁面底部的 [**關閉**]，切換到 DQS 用戶端的主頁面。</span><span class="sxs-lookup"><span data-stu-id="26ea4-114">Click **Close** at the bottom of the page to switch to the main page of DQS Client.</span></span>  
  
## <a name="next-task"></a><span data-ttu-id="26ea4-115">下一項工作</span><span class="sxs-lookup"><span data-stu-id="26ea4-115">Next Task</span></span>  
 [<span data-ttu-id="26ea4-116">工作 10：設定複合定義域使用參考資料服務</span><span class="sxs-lookup"><span data-stu-id="26ea4-116">Task 10: Configuring Composite Domain to Use Reference Data Service</span></span>](../../2014/tutorials/task-10-configuring-composite-domain-to-use-reference-data-service.md)  
  
  
