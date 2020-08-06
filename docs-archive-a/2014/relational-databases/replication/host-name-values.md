---
title: HOST_NAME 值 | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newsubwizard.hostnamevalue.f1
ms.assetid: 21548f08-2910-4a55-baac-b911ba9afaf1
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 67d01df05c8d56fd435eb0ee1b42ba2da6a312ce
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585830"
---
# <a name="host_name-values"></a><span data-ttu-id="a1f1f-102">HOST_NAME 值</span><span class="sxs-lookup"><span data-stu-id="a1f1f-102">HOST_NAME Values</span></span>
  <span data-ttu-id="a1f1f-103">具有參數化篩選的合併式發行集，會使用 SUSER_SNAME() 函數及/或 HOST_NAME() 函數來篩選資料。</span><span class="sxs-lookup"><span data-stu-id="a1f1f-103">Merge publications with parameterized filters use the SUSER_SNAME() function and/or the HOST_NAME() function to filter data.</span></span> <span data-ttu-id="a1f1f-104">函數是在新增發行集精靈或 **[發行集屬性]** 對話方塊中指定。</span><span class="sxs-lookup"><span data-stu-id="a1f1f-104">The function is specified in the New Publication Wizard or the **Publication Properties** dialog box.</span></span>  
  
 <span data-ttu-id="a1f1f-105">依預設，HOST_NAME() 函數會傳回連接到發行者的電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="a1f1f-105">By default, the HOST_NAME() function returns the name of the computer connecting to the Publisher.</span></span> <span data-ttu-id="a1f1f-106">使用參數化篩選時，通常會在精靈的這個頁面上提供一個值，來覆寫此值。</span><span class="sxs-lookup"><span data-stu-id="a1f1f-106">When using parameterized filters, it is common to override this value by supplying a value on this page of the wizard.</span></span> <span data-ttu-id="a1f1f-107">HOST_NAME() 函數就會傳回您指定的值，而非電腦的名稱。</span><span class="sxs-lookup"><span data-stu-id="a1f1f-107">The HOST_NAME() function then returns the value you specify rather than the name of the computer.</span></span> <span data-ttu-id="a1f1f-108">如需詳細資訊，請參閱[參數化資料列篩選](merge/parameterized-filters-parameterized-row-filters.md)的＜覆寫 HOST_NAME() 值＞一節。</span><span class="sxs-lookup"><span data-stu-id="a1f1f-108">For more information, see the "Overriding the HOST_NAME() Value" section of [Parameterized Row Filters](merge/parameterized-filters-parameterized-row-filters.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a1f1f-109">如果您覆寫 HOST_NAME()，則所有對 HOST_NAME() 函數的呼叫均會傳回您指定的值。</span><span class="sxs-lookup"><span data-stu-id="a1f1f-109">If you override HOST_NAME(), all calls to the HOST_NAME() function will return the value you specify.</span></span> <span data-ttu-id="a1f1f-110">請確定其他應用程式不會相依於由 HOST_NAME() 傳回電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="a1f1f-110">Ensure that other applications are not depending on HOST_NAME() returning the computer name.</span></span>  
  
## <a name="options"></a><span data-ttu-id="a1f1f-111">選項。</span><span class="sxs-lookup"><span data-stu-id="a1f1f-111">Options</span></span>  
 <span data-ttu-id="a1f1f-112">**訂閱屬性**</span><span class="sxs-lookup"><span data-stu-id="a1f1f-112">**Subscription properties**</span></span>  
 <span data-ttu-id="a1f1f-113">在 **[HOST_NAME 值]** 資料行中，輸入每一個訂閱者的值，或接受預設值 (訂閱者電腦的名稱)。</span><span class="sxs-lookup"><span data-stu-id="a1f1f-113">Enter a value for each Subscriber in the **HOST_NAME Value** column or accept the default, which is the name of the Subscriber computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1f1f-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a1f1f-114">See Also</span></span>  
 <span data-ttu-id="a1f1f-115">[Create a Pull Subscription](create-a-pull-subscription.md) </span><span class="sxs-lookup"><span data-stu-id="a1f1f-115">[Create a Pull Subscription](create-a-pull-subscription.md) </span></span>  
 <span data-ttu-id="a1f1f-116">[Create a Push Subscription](create-a-push-subscription.md) </span><span class="sxs-lookup"><span data-stu-id="a1f1f-116">[Create a Push Subscription](create-a-push-subscription.md) </span></span>  
 <span data-ttu-id="a1f1f-117">[檢視及修改提取訂閱屬性](view-and-modify-pull-subscription-properties.md) </span><span class="sxs-lookup"><span data-stu-id="a1f1f-117">[View and Modify Pull Subscription Properties](view-and-modify-pull-subscription-properties.md) </span></span>  
 <span data-ttu-id="a1f1f-118">[檢視及修改發送訂閱屬性](view-and-modify-push-subscription-properties.md) </span><span class="sxs-lookup"><span data-stu-id="a1f1f-118">[View and Modify Push Subscription Properties](view-and-modify-push-subscription-properties.md) </span></span>  
 <span data-ttu-id="a1f1f-119">[HOST_NAME &#40;Transact-SQL&#41;](/sql/t-sql/functions/host-name-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a1f1f-119">[HOST_NAME &#40;Transact-SQL&#41;](/sql/t-sql/functions/host-name-transact-sql) </span></span>  
 [<span data-ttu-id="a1f1f-120">訂閱發行集</span><span class="sxs-lookup"><span data-stu-id="a1f1f-120">Subscribe to Publications</span></span>](subscribe-to-publications.md)  
  
  
