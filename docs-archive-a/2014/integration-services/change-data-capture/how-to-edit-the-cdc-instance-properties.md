---
title: 如何編輯 CDC 執行個體屬性 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 7a6c719a-3735-43b7-b3ab-dfadd325eca2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b02785a32fa1f64d5da0c3202acd7916da1e65ee
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687110"
---
# <a name="how-to-edit-the-cdc-instance-properties"></a><span data-ttu-id="110b1-102">如何編輯 CDC 執行個體屬性</span><span class="sxs-lookup"><span data-stu-id="110b1-102">How to Edit the CDC Instance Properties</span></span>
  <span data-ttu-id="110b1-103">此程序描述如何使用 CDC 設計工具主控台來編輯 CDC 執行個體的組態屬性。</span><span class="sxs-lookup"><span data-stu-id="110b1-103">This procedure describes how to use the CDC Designer Console to edit the configuration properties for a CDC instance.</span></span>  
  
### <a name="to-edit-the-cdc-instance-configuration-properties"></a><span data-ttu-id="110b1-104">若要編輯 CDC 執行個體組態屬性</span><span class="sxs-lookup"><span data-stu-id="110b1-104">To edit the CDC instance configuration properties</span></span>  
  
1.  <span data-ttu-id="110b1-105">從 **[開始]** 功能表選取 **[CDC 設計工具主控台]** 。</span><span class="sxs-lookup"><span data-stu-id="110b1-105">From the **Start** menu, select the **CDC Designer Console**.</span></span>  
  
2.  <span data-ttu-id="110b1-106">在左窗格中展開 **[異動資料擷取]** ，然後展開包含執行個體的服務，該執行個體包含您要編輯的屬性。</span><span class="sxs-lookup"><span data-stu-id="110b1-106">In the left pane, expand **Change Data Capture** then expand the service that contains the instance with the properties that you want to edit.</span></span>  
  
3.  <span data-ttu-id="110b1-107">選取您要編輯屬性的執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="110b1-107">Select the name of the instance where you want to edit the properties.</span></span>  
  
4.  <span data-ttu-id="110b1-108">從 CDC 設計工具主控台右側的 [動作] 窗格中，按一下 **[屬性]** 。</span><span class="sxs-lookup"><span data-stu-id="110b1-108">From the Actions pane on the right side of the CDC Designer Console, click **Properties**.</span></span>  
  
     <span data-ttu-id="110b1-109">您也可以用滑鼠右鍵按一下您要編輯屬性的執行個體，然後按一下 [屬性]  。</span><span class="sxs-lookup"><span data-stu-id="110b1-109">You can also right-click the instance where you want to edit the properties and click **Properties**.</span></span>  
  
5.  <span data-ttu-id="110b1-110">在屬性編輯器中，於下列索引標籤上編輯屬性：</span><span class="sxs-lookup"><span data-stu-id="110b1-110">In the Properties editor, edit the properties in the following tabs:</span></span>  
  
    -   <span data-ttu-id="110b1-111">**Oracle**：在屬性編輯器中使用 **[Oracle]** 索引標籤，以變更您在新增執行個體精靈中 [建立 CDC 資料庫] 頁面上提供的描述，以及變更 Oracle 記錄採礦資料庫連接資訊。</span><span class="sxs-lookup"><span data-stu-id="110b1-111">**Oracle**: Use the **Oracle** tab in the Properties editor to make changes to the description you provided in the Create CDC database page in the New Instance wizard and to make changes to the Oracle Log Mining database connection information.</span></span>  
  
         <span data-ttu-id="110b1-112">如需有關您可以在此索引標籤上編輯之內容的詳細資訊，請參閱＜ [Edit the Oracle Database Properties](edit-the-oracle-database-properties.md)＞。</span><span class="sxs-lookup"><span data-stu-id="110b1-112">For information about what you can edit in this tab, see [Edit the Oracle Database Properties](edit-the-oracle-database-properties.md).</span></span>  
  
    -   <span data-ttu-id="110b1-113">**資料表**：使用 **[資料表]** 索引標籤，以變更您從 Oracle 來源資料庫選取的資料表和資料行。</span><span class="sxs-lookup"><span data-stu-id="110b1-113">**Tables**: Use the **Tables** tab to make changes to the tables and columns that you selected from the Oracle source database.</span></span>  
  
         <span data-ttu-id="110b1-114">如需有關您可以在此索引標籤上編輯之內容的詳細資訊，請參閱＜ [Edit Tables](edit-tables.md)＞。</span><span class="sxs-lookup"><span data-stu-id="110b1-114">For information about what you can edit in this tab, see Edit [Edit Tables](edit-tables.md)</span></span>  
  
    -   <span data-ttu-id="110b1-115">**指令碼**：使用 [指令碼]  索引標籤可在即將設定補充記錄的 Oracle 來源資料庫上執行或重新執行指令碼。</span><span class="sxs-lookup"><span data-stu-id="110b1-115">**Scripts**: Use the **Scripts** tab to run or re-run a script on the Oracle source database that will set up supplemental logging.</span></span>  
  
         <span data-ttu-id="110b1-116">如需有關您可以在此索引標籤上執行之作業的詳細資訊，請參閱＜ [Review and Generate Supplemental Logging Scripts](review-and-generate-supplemental-logging-scripts.md)＞。</span><span class="sxs-lookup"><span data-stu-id="110b1-116">For information about what you can do in this tab, see [Review and Generate Supplemental Logging Scripts](review-and-generate-supplemental-logging-scripts.md).</span></span>  
  
    -   <span data-ttu-id="110b1-117">**進階**：使用 **[進階]** 索引標籤，將特殊屬性加入至 CDC 執行個體。</span><span class="sxs-lookup"><span data-stu-id="110b1-117">**Advanced**: Use the **Advanced** tab to add special properties to the CDC instance.</span></span>  
  
         <span data-ttu-id="110b1-118">如需有關您可以在此索引標籤上執行之作業的詳細資訊，請參閱＜ [Edit the Advanced Properties](edit-the-advanced-properties.md)＞。</span><span class="sxs-lookup"><span data-stu-id="110b1-118">For information about what you can do in this tab, see [Edit the Advanced Properties](edit-the-advanced-properties.md).</span></span>  
  
  
