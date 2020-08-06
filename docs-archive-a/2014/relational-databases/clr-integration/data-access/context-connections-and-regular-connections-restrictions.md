---
title: 一般和內容連接的限制 |Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- context connections [CLR integration]
- regular connections [CLR integration]
ms.assetid: 0c6fe4cb-d846-40b5-8884-35a9c770f5e8
author: rothja
ms.author: jroth
ms.openlocfilehash: 52f50347a27cdaffe83b252d86c56382b5ef4f31
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597168"
---
# <a name="restrictions-on-regular-and-context-connections"></a><span data-ttu-id="1bcdc-102">一般和內容連接的限制</span><span class="sxs-lookup"><span data-stu-id="1bcdc-102">Restrictions on Regular and Context Connections</span></span>
  <span data-ttu-id="1bcdc-103">本主題討論 [!INCLUDE[msCoName](../../../includes/ssnoversion-md.md)] 透過內容和一般連接在進程中執行之程式碼的相關限制。</span><span class="sxs-lookup"><span data-stu-id="1bcdc-103">This topic discusses the restrictions associated with code executing in the [!INCLUDE[msCoName](../../../includes/ssnoversion-md.md)] process through context and regular connections.</span></span>  
  
## <a name="restrictions-on-context-connections"></a><span data-ttu-id="1bcdc-104">內容連接的限制</span><span class="sxs-lookup"><span data-stu-id="1bcdc-104">Restrictions on Context Connections</span></span>  
 <span data-ttu-id="1bcdc-105">開發應用程式時，請考慮下列適用於內容連接的限制：</span><span class="sxs-lookup"><span data-stu-id="1bcdc-105">When developing your application, take into account the following restrictions that apply to context connections:</span></span>  
  
-   <span data-ttu-id="1bcdc-106">在給定連接的給定時間內，您只能開啟一個內容連接。</span><span class="sxs-lookup"><span data-stu-id="1bcdc-106">You can have only one context connection open at a given time for a given connection.</span></span> <span data-ttu-id="1bcdc-107">如果您同時在不同的連接中執行多個陳述式，其中每個陳述式可能會取得自己的內容連接。</span><span class="sxs-lookup"><span data-stu-id="1bcdc-107">If you have multiple statements running concurrently in separate connections, each one of them can get their own context connection.</span></span> <span data-ttu-id="1bcdc-108">這項限制不會影響來自不同連接的並行要求，只會影響給定連接的給定要求。</span><span class="sxs-lookup"><span data-stu-id="1bcdc-108">The restriction does not affect concurrent requests from different connections; it only affects a given request on a given connection.</span></span>  
  
-   <span data-ttu-id="1bcdc-109">內容連接不支援 Multiple Active Result Sets (MARS)。</span><span class="sxs-lookup"><span data-stu-id="1bcdc-109">Multiple Active Result Sets (MARS) is not supported in a context connection.</span></span>  
  
-   <span data-ttu-id="1bcdc-110">`SqlBulkCopy` 類別無法在內容連接中運作。</span><span class="sxs-lookup"><span data-stu-id="1bcdc-110">The `SqlBulkCopy` class does not operate in a context connection.</span></span>  
  
-   <span data-ttu-id="1bcdc-111">不支援在內容連接中更新批次。</span><span class="sxs-lookup"><span data-stu-id="1bcdc-111">Update batching in a context connection is not supported</span></span>  
  
-   <span data-ttu-id="1bcdc-112">`SqlNotificationRequest` 無法搭配針對內容連接執行的命令使用。</span><span class="sxs-lookup"><span data-stu-id="1bcdc-112">`SqlNotificationRequest` cannot be used with commands that execute against a context connection.</span></span>  
  
-   <span data-ttu-id="1bcdc-113">不支援取消針對內容連接執行的命令。</span><span class="sxs-lookup"><span data-stu-id="1bcdc-113">Canceling commands that are running against the context connection is not supported.</span></span> <span data-ttu-id="1bcdc-114">`SqlCommand.Cancel` 方法會以無訊息的方式忽略此要求。</span><span class="sxs-lookup"><span data-stu-id="1bcdc-114">The `SqlCommand.Cancel` method silently ignores the request.</span></span>  
  
-   <span data-ttu-id="1bcdc-115">當您使用 "context connection=true" 時，無法使用其他連接字串關鍵字。</span><span class="sxs-lookup"><span data-stu-id="1bcdc-115">No other connection string keywords can be used when you use "context connection=true".</span></span>  
  
-   <span data-ttu-id="1bcdc-116">如果 `SqlConnection.DataSource` 的連接字串為 "context connection=true"，`SqlConnection` 屬性就會傳回 Null，而非 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="1bcdc-116">The `SqlConnection.DataSource` property returns null if the connection string for the `SqlConnection` is "context connection=true", instead of the name of the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="1bcdc-117">針對內容連接執行命令時，設定 `SqlCommand.CommandTimeout` 屬性就沒有任何作用。</span><span class="sxs-lookup"><span data-stu-id="1bcdc-117">Setting the `SqlCommand.CommandTimeout` property has no effect when the command is executed against a context connection.</span></span>  
  
## <a name="restrictions-on-regular-connections"></a><span data-ttu-id="1bcdc-118">一般連接的限制</span><span class="sxs-lookup"><span data-stu-id="1bcdc-118">Restrictions on Regular Connections</span></span>  
 <span data-ttu-id="1bcdc-119">開發應用程式時，請考慮下列適用於一般連接的限制：</span><span class="sxs-lookup"><span data-stu-id="1bcdc-119">When developing your application, take into account the following restrictions that apply to regular connections:</span></span>  
  
-   <span data-ttu-id="1bcdc-120">不支援針對內部伺服器執行非同步命令。</span><span class="sxs-lookup"><span data-stu-id="1bcdc-120">Asynchronous command execution against internal servers is not supported.</span></span> <span data-ttu-id="1bcdc-121">如果您在命令的連接字串中包含 "async=true"，然後執行此命令，就會導致系統擲回 `System.NotSupportedException`。</span><span class="sxs-lookup"><span data-stu-id="1bcdc-121">Including "async=true" in the connection string of a command, and then executing the command, results in `System.NotSupportedException` being thrown.</span></span> <span data-ttu-id="1bcdc-122">此訊息會顯示：「在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 處理序內部執行時，不支援非同步處理」。</span><span class="sxs-lookup"><span data-stu-id="1bcdc-122">This message appears: "Asynchronous processing is not supported when running inside the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] process."</span></span>  
  
-   <span data-ttu-id="1bcdc-123">不支援 `SqlDependency` 物件。</span><span class="sxs-lookup"><span data-stu-id="1bcdc-123">`SqlDependency` object is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bcdc-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1bcdc-124">See Also</span></span>  
 [<span data-ttu-id="1bcdc-125">內容連接</span><span class="sxs-lookup"><span data-stu-id="1bcdc-125">Context Connection</span></span>](context-connection.md)  
  
  
