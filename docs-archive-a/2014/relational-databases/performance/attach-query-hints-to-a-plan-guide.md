---
title: 將查詢提示附加至計畫指南 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: 2131f796-6359-4f9e-9047-da0b3d4dedaf
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 074c69ffefd2b5a7b2ef445f941f97b7130b0732
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597791"
---
# <a name="attach-query-hints-to-a-plan-guide"></a><span data-ttu-id="18a59-102">將查詢提示附加至計畫指南</span><span class="sxs-lookup"><span data-stu-id="18a59-102">Attach Query Hints to a Plan Guide</span></span>
  <span data-ttu-id="18a59-103">在計畫指南中所使用的有效查詢提示組合。</span><span class="sxs-lookup"><span data-stu-id="18a59-103">Any combination of valid query hints can be used in a plan guide.</span></span> <span data-ttu-id="18a59-104">當計畫指南能配合查詢時，系統會先將計畫指南之提示子句中指定的 OPTION 子句加入查詢中，然後再編譯和最佳化查詢。</span><span class="sxs-lookup"><span data-stu-id="18a59-104">When a plan guide matches a query, the OPTION clause specified in the hints clause of a plan guide is added to the query before it compiles and optimizes.</span></span> <span data-ttu-id="18a59-105">如果配合計畫指南的查詢已經有 OPTION 子句，在計畫指南中所指定的查詢提示將會取代查詢中的提示。</span><span class="sxs-lookup"><span data-stu-id="18a59-105">If a query that is matched to a plan guide already has an OPTION clause, the query hints specified in the plan guide replace those in the query.</span></span> <span data-ttu-id="18a59-106">不過，若要讓計畫指南配合已經有 OPTION 子句的查詢，您必須在指定查詢文字以符合 sp_create_plan_guide 陳述式時，包含查詢的 OPTION 子句。</span><span class="sxs-lookup"><span data-stu-id="18a59-106">However, for a plan guide to match a query that already has an OPTION clause, you must include the OPTION clause of the query when you specify the text of the query to match in the sp_create_plan_guide statement.</span></span> <span data-ttu-id="18a59-107">如果您要將計畫指南中所指定的提示加入查詢中已存在的提示，您不應該取代它們，而是必須在計畫指南的 OPTION 子句中同時指定原始提示和其他提示。</span><span class="sxs-lookup"><span data-stu-id="18a59-107">If you want the hints specified in the plan guide to be added to the hints that already exist on the query, instead of replacing them, you must specify both the original hints and the additional hints in the OPTION clause of the plan guide.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="18a59-108">不當使用查詢提示的計畫指南可能會造成編譯、執行或效能上的問題。</span><span class="sxs-lookup"><span data-stu-id="18a59-108">Plan guides that misuse query hints can cause compilation, execution, or performance problems.</span></span> <span data-ttu-id="18a59-109">計畫指南應該只能由資深的開發人員與資料庫管理員使用。</span><span class="sxs-lookup"><span data-stu-id="18a59-109">Plan guides should be used only by experienced developers and database administrators.</span></span>  
  
## <a name="common-query-hints-used-in-plan-guides"></a><span data-ttu-id="18a59-110">計畫指南中常用的查詢提示</span><span class="sxs-lookup"><span data-stu-id="18a59-110">Common Query Hints Used in Plan Guides</span></span>  
 <span data-ttu-id="18a59-111">可從計畫指南獲益的查詢通常是以參數為基礎，而且有可能執行的效果很差，因為它們使用快取的查詢計畫，這些參數值並不代表最糟榚的情況值或最具代表性的狀況值。</span><span class="sxs-lookup"><span data-stu-id="18a59-111">Queries that can benefit from plan guides are generally parameter-based, and may be performing poorly because they use cached query plans whose parameter values do not represent a worst-case or most representative scenario.</span></span> <span data-ttu-id="18a59-112">OPTIMIZE FOR 與 RECOMPILE 查詢提示可用以處理此問題。</span><span class="sxs-lookup"><span data-stu-id="18a59-112">The OPTIMIZE FOR and RECOMPILE query hints can be used to address this problem.</span></span> <span data-ttu-id="18a59-113">OPTIMIZE FOR 指示 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 在最佳化查詢時使用參數的特定值。</span><span class="sxs-lookup"><span data-stu-id="18a59-113">OPTIMIZE FOR instructs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to use a particular value for a parameter when the query is optimized.</span></span> <span data-ttu-id="18a59-114">RECOMPILE 指示伺服器在執行後捨棄查詢計畫，以強制查詢最佳化工具在下次執行相同的查詢時，重新編譯新的查詢計畫。</span><span class="sxs-lookup"><span data-stu-id="18a59-114">RECOMPILE instructs the server to discard a query plan after execution, forcing the query optimizer to recompile a new query plan the next time that the same query is executed.</span></span> <span data-ttu-id="18a59-115">如需範例，請參閱 [計畫指南](plan-guides.md)。</span><span class="sxs-lookup"><span data-stu-id="18a59-115">For an example, see [Plan Guides](plan-guides.md).</span></span>  
  
 <span data-ttu-id="18a59-116">此外，您可以指定 INDEX、FORCESCAN 和 FORCESEEK 資料表提示做為查詢提示。</span><span class="sxs-lookup"><span data-stu-id="18a59-116">In addition, you can specify the table hints INDEX, FORCESCAN, and FORCESEEK as query hints.</span></span> <span data-ttu-id="18a59-117">將這些提示指定為查詢提示時，其行為模式就與內嵌資料表或檢視提示相同。</span><span class="sxs-lookup"><span data-stu-id="18a59-117">When specified as query hints, these hints behave like an inline table or view hint.</span></span> <span data-ttu-id="18a59-118">INDEX 提示會強制查詢最佳化工具只使用指定的索引來存取參考之資料表或檢視內的資料。</span><span class="sxs-lookup"><span data-stu-id="18a59-118">The INDEX hint forces the query optimizer to use only the specified indexes to access the data in the referenced table or view.</span></span> <span data-ttu-id="18a59-119">FORCESEEK 提示會強制最佳化工具只使用索引搜尋作業，以存取參考之資料表或檢視內的資料。</span><span class="sxs-lookup"><span data-stu-id="18a59-119">The FORCESEEK hint forces the optimizer to use only an index seek operation to access the data in the referenced table or view.</span></span> <span data-ttu-id="18a59-120">這些提示提供額外的計畫指南功能，並讓您對於使用此計畫指南的查詢最佳化有更大的影響。</span><span class="sxs-lookup"><span data-stu-id="18a59-120">These hints provide additional plan guide functionality and allow you to have more influence over the optimization of queries that use the plan guide.</span></span>  
  
  
