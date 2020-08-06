---
title: 一般與內容連接 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- context connections [CLR integration]
- regular connections [CLR integration]
ms.assetid: a1dead02-be88-4b16-8cb2-db1284856764
author: rothja
ms.author: jroth
ms.openlocfilehash: ce531129099a8f4908bdc4b29920696d4ba3c505
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606906"
---
# <a name="regular-vs-context-connections"></a><span data-ttu-id="8c4eb-102">一般連線與內容連接</span><span class="sxs-lookup"><span data-stu-id="8c4eb-102">Regular vs. Context Connections</span></span>
  <span data-ttu-id="8c4eb-103">如果您要連接到遠端伺服器，請務必使用正常連接而非內容連接。</span><span class="sxs-lookup"><span data-stu-id="8c4eb-103">If you are connecting to a remote server, always use regular connections rather than context connections.</span></span> <span data-ttu-id="8c4eb-104">如果您需要連接到執行預存程序或函數的相同伺服器，在大部分的情況下，請使用內容連接。</span><span class="sxs-lookup"><span data-stu-id="8c4eb-104">If you need to connect to the same server on which the stored procedure or function is running, use the context connection in most cases.</span></span> <span data-ttu-id="8c4eb-105">其優點包含可在相同的交易空間執行，以及不必重新驗證等等。</span><span class="sxs-lookup"><span data-stu-id="8c4eb-105">This has benefits such as running in the same transaction space and not having to reauthenticate.</span></span>  
  
 <span data-ttu-id="8c4eb-106">此外，使用內容連接通常會使效能更好，而且資源的使用量更少。</span><span class="sxs-lookup"><span data-stu-id="8c4eb-106">Additionally, using the context connection typically results in better performance and less resource usage.</span></span> <span data-ttu-id="8c4eb-107">內容連線是一個同進程的連線，因此它可以藉由略過網路通訊協定和傳輸層來傳送 Transact-sql 語句並接收結果，以「直接」連線到伺服器。</span><span class="sxs-lookup"><span data-stu-id="8c4eb-107">The context connection is an in-process-only connection, so it can contact the server "directly" by bypassing the network protocol and transport layers to send Transact-SQL statements and receive results.</span></span> <span data-ttu-id="8c4eb-108">系統也會略過驗證處理序。</span><span class="sxs-lookup"><span data-stu-id="8c4eb-108">The authentication process is bypassed, as well.</span></span> <span data-ttu-id="8c4eb-109">下圖顯示 `SqlClient` Managed 提供者的主要元件，以及使用正常連接或內容連接時，不同的元件分別如何與彼此互動。</span><span class="sxs-lookup"><span data-stu-id="8c4eb-109">The following figure shows the primary components of the `SqlClient` managed provider, as well as how the different components interact with each other when using a regular connection, and when using the context connection.</span></span>  
  
 <span data-ttu-id="8c4eb-110">![內容和一般連接的程式碼路徑。](../../../database-engine/dev-guide/media/clrintdataaccess.gif "內容和一般連接的程式碼路徑。")</span><span class="sxs-lookup"><span data-stu-id="8c4eb-110">![Code paths of a context and a regular connnection.](../../../database-engine/dev-guide/media/clrintdataaccess.gif "Code paths of a context and a regular connnection.")</span></span>  
  
 <span data-ttu-id="8c4eb-111">內容連接會遵循較短的程式碼路徑，並涉及較少的元件，因此，您可以預期會比在正常連接下，來回伺服器之要求和結果的速度還要快。</span><span class="sxs-lookup"><span data-stu-id="8c4eb-111">The context connection follows a shorter code path and involves fewer components, so you can expect requests and results to get to and from the server faster than in a regular connection.</span></span> <span data-ttu-id="8c4eb-112">對於內容連接和正常連接，在伺服器上的查詢執行時間是相同的。</span><span class="sxs-lookup"><span data-stu-id="8c4eb-112">Query execution time on the server is the same for context and regular connections.</span></span>  
  
 <span data-ttu-id="8c4eb-113">您有時候可能需要針對相同的伺服器開啟個別的正常連接。</span><span class="sxs-lookup"><span data-stu-id="8c4eb-113">There are some cases in which you may need to open a separate regular connection to the same server.</span></span> <span data-ttu-id="8c4eb-114">例如，使用內容連接有一些限制，如[一般和內容連接的限制](context-connections-and-regular-connections-restrictions.md)中所述。</span><span class="sxs-lookup"><span data-stu-id="8c4eb-114">For example, there are certain restrictions on using the context connection, described in [Restrictions on Regular and Context Connections](context-connections-and-regular-connections-restrictions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c4eb-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8c4eb-115">See Also</span></span>  
 [<span data-ttu-id="8c4eb-116">內容連接</span><span class="sxs-lookup"><span data-stu-id="8c4eb-116">Context Connection</span></span>](context-connection.md)  
  
  
