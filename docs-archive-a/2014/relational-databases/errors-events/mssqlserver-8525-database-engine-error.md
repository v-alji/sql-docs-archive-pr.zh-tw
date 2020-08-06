---
title: MSSQLSERVER_8525 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- "8525"
helpviewer_keywords:
- 8525 (Database Engine error)
ms.assetid: 297867c1-691e-4d6b-a3be-a7575015ecfa
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 36db48ca2a9afd08dadcd12abc13b9978e227b00
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597863"
---
# <a name="mssqlserver_8525"></a><span data-ttu-id="c85eb-102">MSSQLSERVER_8525</span><span class="sxs-lookup"><span data-stu-id="c85eb-102">MSSQLSERVER_8525</span></span>
    
## <a name="details"></a><span data-ttu-id="c85eb-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="c85eb-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c85eb-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="c85eb-104">Product Name</span></span>|<span data-ttu-id="c85eb-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="c85eb-105">SQL Server</span></span>|  
|<span data-ttu-id="c85eb-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="c85eb-106">Event ID</span></span>|<span data-ttu-id="c85eb-107">8525</span><span class="sxs-lookup"><span data-stu-id="c85eb-107">8525</span></span>|  
|<span data-ttu-id="c85eb-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="c85eb-108">Event Source</span></span>|<span data-ttu-id="c85eb-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="c85eb-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="c85eb-110">元件</span><span class="sxs-lookup"><span data-stu-id="c85eb-110">Component</span></span>|<span data-ttu-id="c85eb-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="c85eb-111">SQLEngine</span></span>|  
|<span data-ttu-id="c85eb-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="c85eb-112">Symbolic Name</span></span>||  
|<span data-ttu-id="c85eb-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="c85eb-113">Message Text</span></span>|<span data-ttu-id="c85eb-114">分散式交易完成。</span><span class="sxs-lookup"><span data-stu-id="c85eb-114">Distributed transaction completed.</span></span> <span data-ttu-id="c85eb-115">請在新的交易或是 NULL 交易中編列這個工作階段。</span><span class="sxs-lookup"><span data-stu-id="c85eb-115">Either enlist this session in a new transaction or the NULL transaction.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="c85eb-116">說明</span><span class="sxs-lookup"><span data-stu-id="c85eb-116">Explanation</span></span>  
 <span data-ttu-id="c85eb-117">在將分散式交易協調器搭配 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 一起使用的程式設計模型中，應用程式必須明確編列至分散式交易，並從分散式交易脫離。</span><span class="sxs-lookup"><span data-stu-id="c85eb-117">The programming model for using the Distributed Transaction Coordinator with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] requires applications to explicitly enlist to and defect from a distributed transaction.</span></span>  
  
 <span data-ttu-id="c85eb-118">當符合下列四個條件時，就會發生此錯誤：</span><span class="sxs-lookup"><span data-stu-id="c85eb-118">This error occurs when the following four conditions are met:</span></span>  
  
-   <span data-ttu-id="c85eb-119">應用程式已編列到分散式交易中。</span><span class="sxs-lookup"><span data-stu-id="c85eb-119">The application has enlisted into a distributed transaction.</span></span>  
  
-   <span data-ttu-id="c85eb-120">因為某種原因，交易已結束 (已認可或已回復)。</span><span class="sxs-lookup"><span data-stu-id="c85eb-120">The transaction has ended, either committed or rolled back, for any reason.</span></span>  
  
-   <span data-ttu-id="c85eb-121">使用者應用程式尚未明確脫離分散式交易，或尚未明確編列到新的分散式交易中。</span><span class="sxs-lookup"><span data-stu-id="c85eb-121">The user application has not explicitly defected from a distributed transaction or explicitly enlisted into a new distributed transaction.</span></span>  
  
-   <span data-ttu-id="c85eb-122">應用程式嘗試進行脫離現有分散式交易或編列到新的分散式交易以外的其他任何作業，例如發出查詢或啟動本機交易。</span><span class="sxs-lookup"><span data-stu-id="c85eb-122">The application tries to do any transactional operation other than defecting from existing distributed transaction or enlisting to a new distributed transaction, such as issuing a query or starting a local transaction.</span></span>  
  
 <span data-ttu-id="c85eb-123">當應用程式執行建立本機交易的作業時，會使用錯誤狀態 1，而當應用程式嘗試編列到繫結工作階段時，則會使用狀態 2。</span><span class="sxs-lookup"><span data-stu-id="c85eb-123">Error state 1 is used when the application performs an operation that creates local transactions, and state 2 is used when application tries to enlist to a bound session.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="c85eb-124">使用者動作</span><span class="sxs-lookup"><span data-stu-id="c85eb-124">User Action</span></span>  
 <span data-ttu-id="c85eb-125">在應用程式編列到分散式交易之後，應用程式必須明確脫離該分散式交易或編列到另一個分散式交易。</span><span class="sxs-lookup"><span data-stu-id="c85eb-125">After an application has enlisted into a distributed transaction, the application must explicitly defect from the distributed transaction or enlist to another distributed transaction.</span></span> <span data-ttu-id="c85eb-126">這個動作會隱含脫離先前編列的交易。</span><span class="sxs-lookup"><span data-stu-id="c85eb-126">This will implicitly defect from a previous enlisted transaction.</span></span> <span data-ttu-id="c85eb-127">如需脫離或編列到分散式交易的正確語法，請參閱應用程式的程式設計介面手冊。</span><span class="sxs-lookup"><span data-stu-id="c85eb-127">For the exact syntax to defect from or enlist to a distributed transaction, see the programming interface manual for the application.</span></span>  
  
  
