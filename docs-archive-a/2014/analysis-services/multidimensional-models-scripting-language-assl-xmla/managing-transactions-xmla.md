---
title: 管理 (XMLA) 的交易 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- XML for Analysis, transactions
- XMLA, transactions
- explicit transactions [XMLA]
- implicit transactions
- transactions [XML for Analysis]
- rolling back transactions, XMLA
- reference counts [XML for Analysis]
- committing transactions
- starting transactions
ms.assetid: f5112e01-82f8-4870-bfb7-caa00182c999
author: minewiskan
ms.author: owend
ms.openlocfilehash: bff1c60addd25b222905e33bc33e77dd85e88803
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87605919"
---
# <a name="managing-transactions-xmla"></a><span data-ttu-id="6f36f-102">管理交易 (XMLA)</span><span class="sxs-lookup"><span data-stu-id="6f36f-102">Managing Transactions (XMLA)</span></span>
  <span data-ttu-id="6f36f-103">傳送至實例的每個 XML for Analysis (XMLA) 命令都會在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 目前隱含或明確會話的交易內容中執行。</span><span class="sxs-lookup"><span data-stu-id="6f36f-103">Every XML for Analysis (XMLA) command sent to an instance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] runs within the context of a transaction on the current implicit or explicit session.</span></span> <span data-ttu-id="6f36f-104">若要管理這些交易，您可以使用[BeginTransaction](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/begintransaction-element-xmla)、 [CommitTransaction](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/committransaction-element-xmla)和[RollbackTransaction](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/rollbacktransaction-element-xmla)命令。</span><span class="sxs-lookup"><span data-stu-id="6f36f-104">To manage each of these transactions, you use the [BeginTransaction](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/begintransaction-element-xmla), [CommitTransaction](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/committransaction-element-xmla), and [RollbackTransaction](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/rollbacktransaction-element-xmla) commands.</span></span> <span data-ttu-id="6f36f-105">透過使用這些命令，您可以建立隱含或是明確的交易、變更交易參考計數，以及開始、認可或是回復交易。</span><span class="sxs-lookup"><span data-stu-id="6f36f-105">By using these commands, you can create implicit or explicit transactions, change the transaction reference count, as well as start, commit, or roll back transactions.</span></span>  
  
## <a name="implicit-and-explicit-transactions"></a><span data-ttu-id="6f36f-106">隱含與明確交易。</span><span class="sxs-lookup"><span data-stu-id="6f36f-106">Implicit and Explicit Transactions</span></span>  
 <span data-ttu-id="6f36f-107">交易是隱含或明確的：</span><span class="sxs-lookup"><span data-stu-id="6f36f-107">A transaction is either implicit or explicit:</span></span>  
  
 <span data-ttu-id="6f36f-108">**隱含交易**</span><span class="sxs-lookup"><span data-stu-id="6f36f-108">**Implicit transaction**</span></span>  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]<span data-ttu-id="6f36f-109">如果*implicit* `BeginTransaction` 命令未指定交易的開頭，則會建立 XMLA 命令的隱含交易。</span><span class="sxs-lookup"><span data-stu-id="6f36f-109">creates an *implicit* transaction for an XMLA command if the `BeginTransaction` command does not specify the start of a transaction.</span></span> <span data-ttu-id="6f36f-110">如果命令成功，[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 永遠都會認可隱含交易。而如果命令失敗，則會回復隱含交易。</span><span class="sxs-lookup"><span data-stu-id="6f36f-110">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] always commits an implicit transaction if the command succeeds, and rolls back an implicit transaction if the command fails.</span></span>  
  
 <span data-ttu-id="6f36f-111">**明確交易**</span><span class="sxs-lookup"><span data-stu-id="6f36f-111">**Explicit transaction**</span></span>  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]<span data-ttu-id="6f36f-112">如果命令開始交易，則建立*明確*的交易 `BeginTransaction` 。</span><span class="sxs-lookup"><span data-stu-id="6f36f-112">creates an *explicit* transaction if the `BeginTransaction` command starts of a transaction.</span></span> <span data-ttu-id="6f36f-113">不過，如果傳送的是 `CommitTransaction` 命令，[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 只會認可明確交易。而如果傳送的是 `RollbackTransaction` 命令，則會回復明確交易。</span><span class="sxs-lookup"><span data-stu-id="6f36f-113">However, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] only commits an explicit transaction if a `CommitTransaction` command is sent, and rolls back an explicit transaction if a `RollbackTransaction` command is sent.</span></span>  
  
 <span data-ttu-id="6f36f-114">此外，如果目前的工作階段在使用中交易完成之前就結束了目前的工作階段，[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 則會回復隱含交易和明確交易。</span><span class="sxs-lookup"><span data-stu-id="6f36f-114">In addition, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] rolls back both implicit and explicit transactions if the current session ends before the active transaction completes.</span></span>  
  
## <a name="transactions-and-reference-counts"></a><span data-ttu-id="6f36f-115">交易和參考計數</span><span class="sxs-lookup"><span data-stu-id="6f36f-115">Transactions and Reference Counts</span></span>  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="6f36f-116">會為每個工作階段維護一個交易參考計數。</span><span class="sxs-lookup"><span data-stu-id="6f36f-116">maintains a transaction reference count for each session.</span></span> <span data-ttu-id="6f36f-117">不過，[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 並不支援巢狀交易，因為每個工作階段都只會維護一個使用中交易。</span><span class="sxs-lookup"><span data-stu-id="6f36f-117">However, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] does not support nested transactions in that only one active transaction is maintained per session.</span></span> <span data-ttu-id="6f36f-118">如果目前的工作階段沒有使用中交易，則會將交易參考計數設定為 0。</span><span class="sxs-lookup"><span data-stu-id="6f36f-118">If the current session does not have an active transaction, the transaction reference count is set to zero.</span></span>  
  
 <span data-ttu-id="6f36f-119">換句話說，每個 `BeginTransaction` 命令都會以一為單位遞增參考計數，而每個 `CommitTransaction` 命令則會以一為單位遞減參考計數。</span><span class="sxs-lookup"><span data-stu-id="6f36f-119">In other words, each `BeginTransaction` command increments the reference count by one, while each `CommitTransaction` command decrements the reference count by one.</span></span> <span data-ttu-id="6f36f-120">如果 `CommitTransaction` 命令將交易計數設定為零，則 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 會認可交易。</span><span class="sxs-lookup"><span data-stu-id="6f36f-120">If a `CommitTransaction` command sets the transaction count to zero, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] commits the transaction.</span></span>  
  
 <span data-ttu-id="6f36f-121">不過，`RollbackTransaction` 命令會回復使用中交易，不論交易參考計數目前的值為何。</span><span class="sxs-lookup"><span data-stu-id="6f36f-121">However, the `RollbackTransaction` command rolls back the active transaction regardless of the current value of the transaction reference count.</span></span> <span data-ttu-id="6f36f-122">換句話說，單一 `RollbackTransaction` 命令會回復使用中交易，不論傳送了多少 `BeginTransaction` 命令或是 `CommitTransaction` 命令，並將交易參考計數設定為零。</span><span class="sxs-lookup"><span data-stu-id="6f36f-122">In other words, a single `RollbackTransaction` command rolls back the active transaction, no matter how many `BeginTransaction` commands or `CommitTransaction` commands were sent, and sets the transaction reference count to zero.</span></span>  
  
## <a name="beginning-a-transaction"></a><span data-ttu-id="6f36f-123">開始交易</span><span class="sxs-lookup"><span data-stu-id="6f36f-123">Beginning a Transaction</span></span>  
 <span data-ttu-id="6f36f-124">`BeginTransaction` 命令會在目前的工作階段上開始明確交易，並以一為單位為目前的工作階段遞增交易參考計數。</span><span class="sxs-lookup"><span data-stu-id="6f36f-124">The `BeginTransaction` command begins an explicit transaction on the current session and increments the transaction reference count for the current session by one.</span></span> <span data-ttu-id="6f36f-125">所有後續的命令都會視為在使用中交易內，直到已傳送足夠的 `CommitTransaction` 命令認可使用中交易，或是傳送單一 `RollbackTransaction` 命令來回復使用中交易為止。</span><span class="sxs-lookup"><span data-stu-id="6f36f-125">All subsequent commands are considered to be within the active transaction, until either enough `CommitTransaction` commands are sent to commit the active transaction or a single `RollbackTransaction` command is sent to roll back the active transaction.</span></span>  
  
## <a name="committing-a-transaction"></a><span data-ttu-id="6f36f-126">認可交易</span><span class="sxs-lookup"><span data-stu-id="6f36f-126">Committing a Transaction</span></span>  
 <span data-ttu-id="6f36f-127">`CommitTransaction` 命令會認可在目前的工作階段上執行 `BeginTransaction` 命令之後所執行的命令結果。</span><span class="sxs-lookup"><span data-stu-id="6f36f-127">The `CommitTransaction` command commits the results of commands that are run after the `BeginTransaction` command was run on the current session.</span></span> <span data-ttu-id="6f36f-128">每個 `CommitTransaction` 命令會為工作階段上的使用中交易遞減參考計數。</span><span class="sxs-lookup"><span data-stu-id="6f36f-128">Each `CommitTransaction` command decrements the reference count for active transactions on a session.</span></span> <span data-ttu-id="6f36f-129">如果 `CommitTransaction` 命令將參考計數設定為零，則 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 會認可使用中交易。</span><span class="sxs-lookup"><span data-stu-id="6f36f-129">If a `CommitTransaction` command sets the reference count to zero, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] commits the active transaction.</span></span> <span data-ttu-id="6f36f-130">如果沒有使用中交易 (換句話說，目前工作階段的交易參考計數已經設定為零)，則 `CommitTransaction` 命令會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="6f36f-130">If there is no active transaction (in other words, the transaction reference count for the current session is already set to zero), a `CommitTransaction` command results in an error.</span></span>  
  
## <a name="rolling-back-a-transaction"></a><span data-ttu-id="6f36f-131">回復交易</span><span class="sxs-lookup"><span data-stu-id="6f36f-131">Rolling Back a Transaction</span></span>  
 <span data-ttu-id="6f36f-132">`RollbackTransaction` 命令會回復在目前的工作階段上執行 `BeginTransaction` 命令之後所執行的命令結果。</span><span class="sxs-lookup"><span data-stu-id="6f36f-132">The `RollbackTransaction` command rolls back the results of commands that are run after the `BeginTransaction` command was run on the current session.</span></span> <span data-ttu-id="6f36f-133">不論目前交易參考計數為何，`RollbackTransaction` 命令都會回復使用中交易，並將交易參考計數設定為零。</span><span class="sxs-lookup"><span data-stu-id="6f36f-133">The `RollbackTransaction` command rolls back the active transaction, regardless of the current transaction reference count, and sets the transaction reference count to zero.</span></span> <span data-ttu-id="6f36f-134">如果沒有使用中交易 (換句話說，目前工作階段的交易參考計數已經設定為零)，則 `RollbackTransaction` 命令會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="6f36f-134">If there is no active transaction (in other words, the transaction reference count for the current session is already set to zero), a `RollbackTransaction` command results in an error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f36f-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6f36f-135">See Also</span></span>  
 [<span data-ttu-id="6f36f-136">在 Analysis Services 中使用 XMLA 進行開發</span><span class="sxs-lookup"><span data-stu-id="6f36f-136">Developing with XMLA in Analysis Services</span></span>](developing-with-xmla-in-analysis-services.md)  
  
  
