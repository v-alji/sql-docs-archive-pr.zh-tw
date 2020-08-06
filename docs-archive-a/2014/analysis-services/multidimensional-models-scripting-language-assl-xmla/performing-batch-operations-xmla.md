---
title: " (XMLA) 執行批次作業 |Microsoft Docs"
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- multiple projects
- XML for Analysis, batches
- parallel batch execution [XMLA]
- transactional batches
- serial batch execution [XMLA]
- XMLA, batches
- batches [XML for Analysis]
- nontransactional batches
ms.assetid: 731c70e5-ed51-46de-bb69-cbf5aea18dda
author: minewiskan
ms.author: owend
ms.openlocfilehash: 69899077cf534482879accbf10640f6295e3866a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592314"
---
# <a name="performing-batch-operations-xmla"></a><span data-ttu-id="77b17-102">執行批次作業 (XMLA)</span><span class="sxs-lookup"><span data-stu-id="77b17-102">Performing Batch Operations (XMLA)</span></span>
  <span data-ttu-id="77b17-103">您可以使用 XML for Analysis (XMLA) 中的[Batch](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/batch-element-xmla)命令，使用單一 xmla [Execute](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute)方法執行多個 xmla 命令。</span><span class="sxs-lookup"><span data-stu-id="77b17-103">You can use the [Batch](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/batch-element-xmla) command in XML for Analysis (XMLA) to run multiple XMLA commands using a single XMLA [Execute](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute) method.</span></span> <span data-ttu-id="77b17-104">您可以用單一交易或每個命令的個別交易，以序列或平行方式執行 `Batch` 命令中包含的多個命令。</span><span class="sxs-lookup"><span data-stu-id="77b17-104">You can run multiple commands contained in the `Batch` command either as a single transaction or in individual transactions for each command, in serial or in parallel.</span></span> <span data-ttu-id="77b17-105">您也可以在命令中指定非正規系結和其他屬性 `Batch` 來處理多個 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 物件。</span><span class="sxs-lookup"><span data-stu-id="77b17-105">You can also specify out-of-line bindings and other properties in the `Batch` command for processing multiple [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] objects.</span></span>  
  
## <a name="running-transactional-and-nontransactional-batch-commands"></a><span data-ttu-id="77b17-106">執行交易式與非交易式批次命令</span><span class="sxs-lookup"><span data-stu-id="77b17-106">Running Transactional and Nontransactional Batch Commands</span></span>  
 <span data-ttu-id="77b17-107">`Batch` 命令使用下列兩種方式之一來執行命令：</span><span class="sxs-lookup"><span data-stu-id="77b17-107">The `Batch` command executes commands in one of two ways:</span></span>  
  
 <span data-ttu-id="77b17-108">**異動**</span><span class="sxs-lookup"><span data-stu-id="77b17-108">**Transactional**</span></span>  
 <span data-ttu-id="77b17-109">如果 `Transaction` 命令的屬性 `Batch` 設定為 true，則命令會 `Batch` 在單一交易中執行命令所包含的所有命令 `Batch` -交易式批次。 *transactional*</span><span class="sxs-lookup"><span data-stu-id="77b17-109">If the `Transaction` attribute of the `Batch` command is set to true, the `Batch` command run commands all of the commands contained by the `Batch` command in a single transaction-a *transactional* batch.</span></span>  
  
 <span data-ttu-id="77b17-110">如果交易式批次中有任何命令失敗，則會 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 回復命令中執行失敗的命令之前的任何命令， `Batch` 而且命令會 `Batch` 立即結束。</span><span class="sxs-lookup"><span data-stu-id="77b17-110">If any command fails in a transactional batch, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] rolls back any command in the `Batch` command that ran before the command that failed and the `Batch` command immediately ends.</span></span> <span data-ttu-id="77b17-111">`Batch` 命令中尚未執行的任何命令都不會被執行。</span><span class="sxs-lookup"><span data-stu-id="77b17-111">Any commands in the `Batch` command that have not yet run are not executed.</span></span> <span data-ttu-id="77b17-112">在 `Batch` 命令結束之後，`Batch` 命令會報告因為失敗的命令而發生的任何錯誤。</span><span class="sxs-lookup"><span data-stu-id="77b17-112">After the `Batch` command ends, the `Batch` command reports any errors that occurred for the failed command.</span></span>  
  
 <span data-ttu-id="77b17-113">**非交易式**</span><span class="sxs-lookup"><span data-stu-id="77b17-113">**Nontransactional**</span></span>  
 <span data-ttu-id="77b17-114">如果 `Transaction` 屬性設定為 false，此命令會 `Batch` 在個別的交易中執行命令所包含的每個命令 `Batch` -*非*交易式批次。</span><span class="sxs-lookup"><span data-stu-id="77b17-114">If the `Transaction` attribute is set to false, the `Batch` command runs each command contained by the `Batch` command in a separate transaction-a *nontransactional* batch.</span></span> <span data-ttu-id="77b17-115">如果非交易式批次中有任何命令失敗，`Batch` 命令會繼續執行失敗命令之後的命令。</span><span class="sxs-lookup"><span data-stu-id="77b17-115">If any command fails in a nontransactional batch, the `Batch` command continues to run commands after the command which failed.</span></span> <span data-ttu-id="77b17-116">在 `Batch` 命令嘗試執行 `Batch` 命令包含的所有命令之後，`Batch` 命令會報告所發生的任何錯誤。</span><span class="sxs-lookup"><span data-stu-id="77b17-116">After the `Batch` command tries to run all the commands that the `Batch` command contains, the `Batch` command reports any errors that occurred.</span></span>  
  
 <span data-ttu-id="77b17-117">所有由包含在 `Batch` 命令中的命令傳回的結果，都會按照 `Batch` 命令所含命令的相同順序來傳回。</span><span class="sxs-lookup"><span data-stu-id="77b17-117">All results returned by commands contained in a `Batch` command are returned in the same order in which the commands are contained in the `Batch` command.</span></span> <span data-ttu-id="77b17-118">`Batch` 命令傳回的結果，會因 `Batch` 命令是交易式或非交易式而異。</span><span class="sxs-lookup"><span data-stu-id="77b17-118">The results returned by a `Batch` command vary based on whether the `Batch` command is transactional or nontransactional.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="77b17-119">如果 `Batch` 命令包含不會傳回輸出的命令（例如[Lock](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/lock-element-xmla)命令），且該命令已成功執行，則命令會在 `Batch` results 元素中傳回空的[根](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/root-element-xmla)元素。</span><span class="sxs-lookup"><span data-stu-id="77b17-119">If a `Batch` command contains a command that does not return output, such as the [Lock](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/lock-element-xmla) command, and that command successfully runs, the `Batch` command returns an empty [root](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/root-element-xmla) element within the results element.</span></span> <span data-ttu-id="77b17-120">空的 `root` 元素可確保 `Batch` 命令中所含的每個命令，可與該命令結果的適當 `root` 元素相符。</span><span class="sxs-lookup"><span data-stu-id="77b17-120">The empty `root` element ensures that each command contained in a `Batch` command can be matched with the appropriate `root` element for that command's results.</span></span>  
  
### <a name="returning-results-from-transactional-batch-results"></a><span data-ttu-id="77b17-121">從交易式批次結果傳回結果</span><span class="sxs-lookup"><span data-stu-id="77b17-121">Returning Results from Transactional Batch Results</span></span>  
 <span data-ttu-id="77b17-122">在交易式批次內執行的命令之結果，必須等到整個 `Batch` 命令完成後才會傳回。</span><span class="sxs-lookup"><span data-stu-id="77b17-122">Results from commands run within a transactional batch are not returned until the entire `Batch` command is completed.</span></span> <span data-ttu-id="77b17-123">不在每個命令執行後便傳回結果，是因為交易式批次中任何失敗的命令，都會造成回復整個 `Batch` 命令及所含的命令。</span><span class="sxs-lookup"><span data-stu-id="77b17-123">The results are not returned after each command runs because any command that fails within a transactional batch would cause the entire `Batch` command and all containing commands to be rolled back.</span></span> <span data-ttu-id="77b17-124">如果所有命令都啟動並順利執行，則命令的方法所傳回之[ExecuteResponse](https://docs.microsoft.com/bi-reference/xmla/xml-elements-objects-executeresponse)元素的[return](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/return-element-xmla)元素會 `Execute` `Batch` 包含一個[results](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/results-element-xmla)元素，而此專案會 `root` 針對命令中包含的每個成功執行命令，各包含一個元素 `Batch` 。</span><span class="sxs-lookup"><span data-stu-id="77b17-124">If all commands start and run successfully, the [return](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/return-element-xmla) element of the [ExecuteResponse](https://docs.microsoft.com/bi-reference/xmla/xml-elements-objects-executeresponse) element returned by the `Execute` method for the `Batch` command contains one [results](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/results-element-xmla) element, which in turn contains one `root` element for each successfully run command contained in the `Batch` command.</span></span> <span data-ttu-id="77b17-125">如果 `Batch` 命令中有任何命令無法啟動或是無法完成，`Execute` 方法會傳回 `Batch` 命令的 SOAP 錯誤，其中包含失敗命令的錯誤。</span><span class="sxs-lookup"><span data-stu-id="77b17-125">If any command in the `Batch` command cannot be started or fails to complete, the `Execute` method returns a SOAP fault for the `Batch` command that contains the error of the command that failed.</span></span>  
  
### <a name="returning-results-from-nontransactional-batch-results"></a><span data-ttu-id="77b17-126">從非交易式批次結果傳回結果</span><span class="sxs-lookup"><span data-stu-id="77b17-126">Returning Results from Nontransactional Batch Results</span></span>  
 <span data-ttu-id="77b17-127">在非交易式批次內執行的命令之結果，會在每個命令傳回結果時，按照 `Batch` 命令中所含的命令順序來傳回。</span><span class="sxs-lookup"><span data-stu-id="77b17-127">Results from commands run within a nontransactional batch are returned in the order in which the commands are contained within the `Batch` command and as they are returned by each command.</span></span> <span data-ttu-id="77b17-128">如果無法成功啟動 `Batch` 命令中所含的任何命令，`Execute` 方法會傳回 SOAP 錯誤，其中包含 `Batch` 命令的錯誤。</span><span class="sxs-lookup"><span data-stu-id="77b17-128">If no command contained in the `Batch` command can be successfully started, the `Execute` method returns a SOAP fault that contains an error for the `Batch` command.</span></span> <span data-ttu-id="77b17-129">如果至少成功啟動一個命令，則 `return` 命令的 `ExecuteResponse` 方法所傳回之 `Execute` 元素的 `Batch` 元素，會包含一個 `results` 元素，而其中會為 `root` 命令所含的每個命令，各包含一個 `Batch` 元素。</span><span class="sxs-lookup"><span data-stu-id="77b17-129">If at least one command is successfully started, the `return` element of the `ExecuteResponse` element returned by the `Execute` method for the `Batch` command contains one `results` element, which in turn contains one `root` element for each command contained in the `Batch` command.</span></span> <span data-ttu-id="77b17-130">如果非交易式批次中的一個或多個命令無法啟動或無法完成，則 `root` 該失敗命令的元素會包含描述錯誤的[錯誤](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/error-element-xmla)元素。</span><span class="sxs-lookup"><span data-stu-id="77b17-130">If one or more commands in a nontransactional batch cannot be started or fails to complete, the `root` element for that failed command contains an [error](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/error-element-xmla) element describing the error.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="77b17-131">只要在非交易式批次中至少有一個命令可以啟動，便會將非交易式批次視為已成功執行，即使在非交易式批次中所含的每個命令，都在 `Batch` 命令的結果中傳回錯誤，亦然。</span><span class="sxs-lookup"><span data-stu-id="77b17-131">As long as at least one command in a nontransactional batch can be started, the nontransactional batch is considered to have successfully run, even if every command contained in the nontransactional batch returns an error in the results of the `Batch` command.</span></span>  
  
## <a name="using-serial-and-parallel-execution"></a><span data-ttu-id="77b17-132">使用序列和平行執行</span><span class="sxs-lookup"><span data-stu-id="77b17-132">Using Serial and Parallel Execution</span></span>  
 <span data-ttu-id="77b17-133">您可以使用 `Batch` 命令，以序列或平行方式，執行包含的命令。</span><span class="sxs-lookup"><span data-stu-id="77b17-133">You can use the `Batch` command to run included commands in serial or in parallel.</span></span> <span data-ttu-id="77b17-134">以序列方式執行命令時，`Batch` 命令中所含的下一個命令必須等到 `Batch` 命令中目前執行的命令完成時才能啟動。</span><span class="sxs-lookup"><span data-stu-id="77b17-134">When the commands are run in serial, the next command included in the `Batch` command cannot start until the currently running command in the `Batch` command is completed.</span></span> <span data-ttu-id="77b17-135">以平行方式執行命令時，`Batch` 命令可以同時執行多個命令。</span><span class="sxs-lookup"><span data-stu-id="77b17-135">When the commands are run in parallel, multiple commands can be executed simultaneously by the `Batch` command.</span></span>  
  
 <span data-ttu-id="77b17-136">若要以平行方式執行命令，請將要平行執行的命令加入至命令的[parallel](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/parallel-element-xmla)屬性 `Batch` 。</span><span class="sxs-lookup"><span data-stu-id="77b17-136">To run commands in parallel, you add the commands to be run in parallel to the [Parallel](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/parallel-element-xmla) property of the `Batch` command.</span></span> <span data-ttu-id="77b17-137">目前， [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 只能平行執行連續的連續[進程](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/process-element-xmla)命令。</span><span class="sxs-lookup"><span data-stu-id="77b17-137">Currently, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] can run only contiguous, sequential [Process](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/process-element-xmla) commands in parallel.</span></span> <span data-ttu-id="77b17-138">包含在屬性中的任何其他 XMLA 命令（例如[Create](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/create-element-xmla)或[Alter](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/alter-element-xmla)） `Parallel` 都會以序列循序執行。</span><span class="sxs-lookup"><span data-stu-id="77b17-138">Any other XMLA command, such as [Create](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/create-element-xmla) or [Alter](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/alter-element-xmla), included in the `Parallel` property is run serially.</span></span>  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="77b17-139">會嘗試平行執行所有包含在 `Process` 屬性中的 `Parallel` 命令，但是無法保證所有包含的 `Process` 命令都可以平行執行。</span><span class="sxs-lookup"><span data-stu-id="77b17-139">tries to run all `Process` commands included in the `Parallel` property in parallel, but cannot guarantee that all included `Process` commands can be run in parallel.</span></span> <span data-ttu-id="77b17-140">執行個體會分析每個 `Process` 命令，而且如果執行個體判斷無法平行執行命令，就會序列執行 `Process` 命令。</span><span class="sxs-lookup"><span data-stu-id="77b17-140">The instance analyzes each `Process` command and, if the instance determines that the command cannot be run in parallel, the `Process` command is run in serial.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="77b17-141">若要平行執行命令，必須將 `Transaction` 命令的 `Batch` 屬性設定成 True，因為 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 僅支援每個連接有一個使用中交易，而且非交易式批次會在個別交易中執行每個命令。</span><span class="sxs-lookup"><span data-stu-id="77b17-141">To run commands in parallel, the `Transaction` attribute of the `Batch` command must be set to true because [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] supports only one active transaction per connection and nontransactional batches run each command in a separate transaction.</span></span> <span data-ttu-id="77b17-142">如果您在非交易式批次中包含 `Parallel` 屬性，就會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="77b17-142">If you include the `Parallel` property in a nontransactional batch, an error occurs.</span></span>  
  
### <a name="limiting-parallel-execution"></a><span data-ttu-id="77b17-143">限制平行執行</span><span class="sxs-lookup"><span data-stu-id="77b17-143">Limiting Parallel Execution</span></span>  
 <span data-ttu-id="77b17-144">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體會嘗試盡量平行執行 `Process` 命令，最多可達執行個體執行的電腦限制。</span><span class="sxs-lookup"><span data-stu-id="77b17-144">An [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance tries to run as many `Process` commands in parallel as possible, up to the limits of the computer on which the instance runs.</span></span> <span data-ttu-id="77b17-145">您可以將 `Process` 屬性 (Property) 的 `maxParallel` 屬性 (Attribute)，設定為可以平行執行之 `Parallel` 命令的上限，以限制並行執行的 `Process` 命令數目。</span><span class="sxs-lookup"><span data-stu-id="77b17-145">You can limit the number of concurrently executing `Process` commands by setting the `maxParallel` attribute of the `Parallel` property to a value indicating the maximum number of `Process` commands that can be run in parallel.</span></span>  
  
 <span data-ttu-id="77b17-146">例如，`Parallel` 屬性依序包含下列命令：</span><span class="sxs-lookup"><span data-stu-id="77b17-146">For example, a `Parallel` property contains the following commands in the sequence listed:</span></span>  
  
1.  `Create`  
  
2.  `Process`  
  
3.  `Alter`  
  
4.  `Process`  
  
5.  `Process`  
  
6.  `Process`  
  
7.  `Delete`  
  
8.  `Process`  
  
9. `Process`  
  
 <span data-ttu-id="77b17-147">此 `maxParalle` 屬性 (Property) 的 `Parallel`l 屬性 (Attribute) 是設定為 2。</span><span class="sxs-lookup"><span data-stu-id="77b17-147">The `maxParalle`l attribute of this `Parallel` property is set to 2.</span></span> <span data-ttu-id="77b17-148">因此，執行個體會依照下列清單執行上列命令：</span><span class="sxs-lookup"><span data-stu-id="77b17-148">Therefore, the instance runs the previous lists of commands as described in the following list:</span></span>  
  
-   <span data-ttu-id="77b17-149">命令 1 會序列執行，因為命令 1 是 `Create` 命令，而且只有 `Process` 命令可以平行執行。</span><span class="sxs-lookup"><span data-stu-id="77b17-149">Command 1 runs serially because command 1 is a `Create` command and only `Process` commands can be run in parallel.</span></span>  
  
-   <span data-ttu-id="77b17-150">命令2會在命令1完成後循序執行。</span><span class="sxs-lookup"><span data-stu-id="77b17-150">Command 2 runs serially after command 1 is completed.</span></span>  
  
-   <span data-ttu-id="77b17-151">命令3會在命令2完成後循序執行。</span><span class="sxs-lookup"><span data-stu-id="77b17-151">Command 3 runs serially after command 2 is completed.</span></span>  
  
-   <span data-ttu-id="77b17-152">命令4和5會在命令3完成後平行執行。</span><span class="sxs-lookup"><span data-stu-id="77b17-152">Commands 4 and 5 run in parallel after command 3 is completed.</span></span> <span data-ttu-id="77b17-153">雖然命令 6 也是 `Process` 命令，不過，命令 6 無法與命令 4 和 5 一起平行執行，因為 `maxParallel` 屬性是設定為 2。</span><span class="sxs-lookup"><span data-stu-id="77b17-153">Although command 6 is also a `Process` command, command 6 cannot run in parallel with commands 4 and 5 because the `maxParallel` property is set to 2.</span></span>  
  
-   <span data-ttu-id="77b17-154">命令 6 會在命令 4 和 5 完成之後序列執行。</span><span class="sxs-lookup"><span data-stu-id="77b17-154">Command 6 runs serially after both commands 4 and 5 are completed.</span></span>  
  
-   <span data-ttu-id="77b17-155">命令 7 會在命令 6 完成之後序列執行。</span><span class="sxs-lookup"><span data-stu-id="77b17-155">Command 7 runs serially after command 6 is completed.</span></span>  
  
-   <span data-ttu-id="77b17-156">命令 8 與 9 會在命令 7 完成之後平行執行。</span><span class="sxs-lookup"><span data-stu-id="77b17-156">Commands 8 and 9 run in parallel after command 7 is completed.</span></span>  
  
## <a name="using-the-batch-command-to-process-objects"></a><span data-ttu-id="77b17-157">使用 Batch 命令處理物件</span><span class="sxs-lookup"><span data-stu-id="77b17-157">Using the Batch Command to Process Objects</span></span>  
 <span data-ttu-id="77b17-158">`Batch` 命令特別包含一些選擇性的屬性 (Property) 與屬性 (Attribute)，以支援處理多個 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 專案：</span><span class="sxs-lookup"><span data-stu-id="77b17-158">The `Batch` command contains several optional properties and attributes specifically included to support processing multiple [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] projects:</span></span>  
  
-   <span data-ttu-id="77b17-159">`ProcessAffectedObjects` 命令的 `Batch` 屬性指出執行個體是否要在 `Process` 命令中的 `Batch` 命令處理指定的物件之後，也處理需要重新處理的物件。</span><span class="sxs-lookup"><span data-stu-id="77b17-159">The `ProcessAffectedObjects` attribute of the `Batch` command indicates whether the instance should also process any object that requires reprocessing as a result of a `Process` command included in the `Batch` command processing a specified object.</span></span>  
  
-   <span data-ttu-id="77b17-160">[系結[] 屬性包含](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/bindings-element-xmla)命令中所有命令所使用之非正規系結的集合 `Process` `Batch` 。</span><span class="sxs-lookup"><span data-stu-id="77b17-160">The [Bindings](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/bindings-element-xmla) property contains a collection of out-of-line bindings used by all of the `Process` commands in the `Batch` command.</span></span>  
  
-   <span data-ttu-id="77b17-161">[DataSource](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/source-element-xmla)屬性包含命令中所有命令所使用之資料來源的非正規系結 `Process` `Batch` 。</span><span class="sxs-lookup"><span data-stu-id="77b17-161">The [DataSource](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/source-element-xmla) property contains an out-of-line binding for a data source used by all of the `Process` commands in the `Batch` command.</span></span>  
  
-   <span data-ttu-id="77b17-162">[DataSourceView](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/datasourceview-element-xmla)屬性包含命令中所有命令所使用之資料來源視圖的非正規系結 `Process` `Batch` 。</span><span class="sxs-lookup"><span data-stu-id="77b17-162">The [DataSourceView](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/datasourceview-element-xmla) property contains an out-of-line binding for a data source view used by all of the `Process` commands in the `Batch` command.</span></span>  
  
-   <span data-ttu-id="77b17-163">[ErrorConfiguration](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/errorconfiguration-element-xmla)屬性會指定 `Batch` 命令處理 `Process` 命令中包含的所有命令所遇到之錯誤的方式 `Batch` 。</span><span class="sxs-lookup"><span data-stu-id="77b17-163">The [ErrorConfiguration](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/errorconfiguration-element-xmla) property specifies the way in which the `Batch` command handles errors encountered by all `Process` commands contained in the `Batch` command.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="77b17-164">如果 `Process` 命令是包含在 `Bindings` 命令中，則 `DataSource` 命令無法包括 `DataSourceView`、`ErrorConfiguration`、`Process` 或 `Batch` 屬性。</span><span class="sxs-lookup"><span data-stu-id="77b17-164">A `Process` command cannot include the `Bindings`, `DataSource`, `DataSourceView`, or `ErrorConfiguration` properties, if the `Process` command is contained in a `Batch` command.</span></span> <span data-ttu-id="77b17-165">如果您必須為 `Process` 命令指定這些屬性，請在包含 `Batch` 命令的 `Process` 命令的對應屬性中提供必要的資訊。</span><span class="sxs-lookup"><span data-stu-id="77b17-165">If you must specify these properties for a `Process` command, provide the necessary information in the corresponding properties of the `Batch` command that contains the `Process` command.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77b17-166">另請參閱</span><span class="sxs-lookup"><span data-stu-id="77b17-166">See Also</span></span>  
 <span data-ttu-id="77b17-167">[&#40;XMLA&#41;的批次元素](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/batch-element-xmla) </span><span class="sxs-lookup"><span data-stu-id="77b17-167">[Batch Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/batch-element-xmla) </span></span>  
 <span data-ttu-id="77b17-168">[XMLA&#41;的 Process 元素 &#40;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/process-element-xmla) </span><span class="sxs-lookup"><span data-stu-id="77b17-168">[Process Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/process-element-xmla) </span></span>  
 <span data-ttu-id="77b17-169">[多維度模型物件處理](../multidimensional-models/processing-a-multidimensional-model-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="77b17-169">[Multidimensional Model Object Processing](../multidimensional-models/processing-a-multidimensional-model-analysis-services.md) </span></span>  
 [<span data-ttu-id="77b17-170">在 Analysis Services 中使用 XMLA 進行開發</span><span class="sxs-lookup"><span data-stu-id="77b17-170">Developing with XMLA in Analysis Services</span></span>](developing-with-xmla-in-analysis-services.md)  
  
  
