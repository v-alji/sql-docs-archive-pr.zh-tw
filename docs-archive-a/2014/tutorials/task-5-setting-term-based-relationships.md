---
title: 工作5：設定以詞彙為基礎的關聯性 |Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 6569d512-637d-4f7b-82e1-1e8582278b37
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 1589ec5843053baa6c42a0b9b0dec019c887da9c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704410"
---
# <a name="task-5-setting-term-based-relationships"></a><span data-ttu-id="1368b-102">工作 5：設定以詞彙為主的關聯</span><span class="sxs-lookup"><span data-stu-id="1368b-102">Task 5: Setting Term Based Relationships</span></span>
  <span data-ttu-id="1368b-103">在這項工作中，您會針對**供應商名稱**網域的值定義幾個以詞彙為主的關聯。</span><span class="sxs-lookup"><span data-stu-id="1368b-103">In this task, you define a few term-based relations for values for the **Supplier Name** domain.</span></span> <span data-ttu-id="1368b-104">以詞彙為主的關聯可讓您針對屬於定義域值的詞彙進行更正。</span><span class="sxs-lookup"><span data-stu-id="1368b-104">A term-based relation enables you to make a correction to a term that is part of a value in a domain.</span></span> <span data-ttu-id="1368b-105">它會啟用多個值，這些值除了被視為相同同義字的共同部分拼字以外，都是相同的。</span><span class="sxs-lookup"><span data-stu-id="1368b-105">It enables multiple values that are identical except for the spelling of a common part of them to be considered identical synonyms.</span></span> <span data-ttu-id="1368b-106">例如， **inc.** 可以更正為已**納入**。</span><span class="sxs-lookup"><span data-stu-id="1368b-106">For example, **Inc.** can be corrected to **Incorporated**.</span></span> <span data-ttu-id="1368b-107">DQS 會在知識探索、清理或比對程序中使用這些關聯。</span><span class="sxs-lookup"><span data-stu-id="1368b-107">DQS uses these relations in the knowledge discovery, cleansing, or matching processes.</span></span> <span data-ttu-id="1368b-108">如需詳細資訊，請參閱[建立以詞彙為基礎](https://msdn.microsoft.com/library/hh510404.aspx)的關聯。</span><span class="sxs-lookup"><span data-stu-id="1368b-108">See [Create Term-based Relations](https://msdn.microsoft.com/library/hh510404.aspx) for more details.</span></span>  
  
1.  <span data-ttu-id="1368b-109">在 [**網域] 清單**中選取 [**供應商名稱**]。</span><span class="sxs-lookup"><span data-stu-id="1368b-109">Select **Supplier Name** in the **Domain list**.</span></span>  
  
2.  <span data-ttu-id="1368b-110">切換至右窗格中的 [以**詞彙為基礎的關聯**性] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="1368b-110">Switch to the **Term-Based Relationships** tab in the right pane.</span></span>  
  
3.  <span data-ttu-id="1368b-111">按一下工具列上的 [**加入新關聯**] 按鈕，以加入資料表的關聯性。</span><span class="sxs-lookup"><span data-stu-id="1368b-111">Click **Add new relation** button on the toolbar to add a relation to the table.</span></span>  
  
4.  <span data-ttu-id="1368b-112">針對 [**值**欄位] 和 [**公司**] 輸入 [ **Co** ] 作為 [**更正為**] 欄位。</span><span class="sxs-lookup"><span data-stu-id="1368b-112">Type **Co.** for the **Value** field and **Company** for the **Correct To** field.</span></span>  
  
5.  <span data-ttu-id="1368b-113">針對以下的值重複上述兩個步驟：</span><span class="sxs-lookup"><span data-stu-id="1368b-113">Repeat the previous two steps for the following values:</span></span>  
  
    |<span data-ttu-id="1368b-114">值</span><span class="sxs-lookup"><span data-stu-id="1368b-114">Value</span></span>|<span data-ttu-id="1368b-115">更正為</span><span class="sxs-lookup"><span data-stu-id="1368b-115">Correct To</span></span>|  
    |-----------|----------------|  
    |<span data-ttu-id="1368b-116">Corp.</span><span class="sxs-lookup"><span data-stu-id="1368b-116">Corp.</span></span>|<span data-ttu-id="1368b-117">Corporation</span><span class="sxs-lookup"><span data-stu-id="1368b-117">Corporation</span></span>|  
    |<span data-ttu-id="1368b-118">Inc.</span><span class="sxs-lookup"><span data-stu-id="1368b-118">Inc.</span></span>|<span data-ttu-id="1368b-119">Incorporated</span><span class="sxs-lookup"><span data-stu-id="1368b-119">Incorporated</span></span>|  
  
     <span data-ttu-id="1368b-120">![以詞彙為主的關聯](../../2014/tutorials/media/et-settingtermbasedrelations.jpg "以詞彙為主的關聯")</span><span class="sxs-lookup"><span data-stu-id="1368b-120">![Term Based Relations](../../2014/tutorials/media/et-settingtermbasedrelations.jpg "Term Based Relations")</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="1368b-121">後續步驟</span><span class="sxs-lookup"><span data-stu-id="1368b-121">Next Step</span></span>  
 [<span data-ttu-id="1368b-122">工作 6：設定同義字</span><span class="sxs-lookup"><span data-stu-id="1368b-122">Task 6: Setting Synonyms</span></span>](../../2014/tutorials/task-6-setting-synonyms.md)  
  
  
