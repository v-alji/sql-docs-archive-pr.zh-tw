---
title: 新別名 (別名索引標籤) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: 785eb6fb-f67e-449d-b1c8-c38dfbb95ef6
author: stevestein
ms.author: sstein
ms.openlocfilehash: 90742e5de3da0cac83c8b18eebba242ddb9a865d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595337"
---
# <a name="new-alias-alias-tab"></a><span data-ttu-id="e7f2e-102">新增別名 (別名索引標籤)</span><span class="sxs-lookup"><span data-stu-id="e7f2e-102">New Alias (Alias Tab)</span></span>
  <span data-ttu-id="e7f2e-103">別名是可用於進行連接的替代名稱。</span><span class="sxs-lookup"><span data-stu-id="e7f2e-103">An alias is an alternate name that can be used to make a connection.</span></span> <span data-ttu-id="e7f2e-104">別名會封裝連接字串的必要元素，並以使用者選擇的名稱來公開這些元素。</span><span class="sxs-lookup"><span data-stu-id="e7f2e-104">The alias encapsulates the required elements of a connection string, and exposes them with a name chosen by the user.</span></span> <span data-ttu-id="e7f2e-105">您可以使用 [別名 - 新增] 對話方塊的 [別名] 頁面來指定別名的連接字串元素。</span><span class="sxs-lookup"><span data-stu-id="e7f2e-105">Use the **Alias** page on the **Alias - New** dialog box to specify the elements of the connection string for an alias.</span></span> <span data-ttu-id="e7f2e-106">若要變更現有別名的連接字串，請參閱 [&#60;Alias&#62; 屬性 &#40;別名索引標籤&#41;](../../../2014/tools/configuration-manager/alias-properties-alias-tab.md)。</span><span class="sxs-lookup"><span data-stu-id="e7f2e-106">To change the connection string of an existing alias, see [&#60;Alias&#62; Properties &#40;Alias Tab&#41;](../../../2014/tools/configuration-manager/alias-properties-alias-tab.md).</span></span>  
  
 <span data-ttu-id="e7f2e-107">您不必填滿所有 **[內容]** 方格內的值。</span><span class="sxs-lookup"><span data-stu-id="e7f2e-107">All values in the **Properties** grid do not have to be completed.</span></span> <span data-ttu-id="e7f2e-108">有效的組合視選取的通訊協定而異。</span><span class="sxs-lookup"><span data-stu-id="e7f2e-108">Valid combinations vary depending on the protocol selected.</span></span> <span data-ttu-id="e7f2e-109">如需有效組合的範例，請參閱下列主題。</span><span class="sxs-lookup"><span data-stu-id="e7f2e-109">See the topics listed below for examples of valid combinations.</span></span>  
  
 <span data-ttu-id="e7f2e-110">**別名名稱**</span><span class="sxs-lookup"><span data-stu-id="e7f2e-110">**Alias Name**</span></span>  
 <span data-ttu-id="e7f2e-111">您想要用來代表這個連接的名稱 (別名)。</span><span class="sxs-lookup"><span data-stu-id="e7f2e-111">The name (alias) that you want to use to refer to this connection.</span></span>  
  
 <span data-ttu-id="e7f2e-112">**管道名稱** / **連接埠號碼**</span><span class="sxs-lookup"><span data-stu-id="e7f2e-112">**Pipe Name** / **Port No**</span></span>  
 <span data-ttu-id="e7f2e-113">連接字串的其他元素。</span><span class="sxs-lookup"><span data-stu-id="e7f2e-113">Additional elements of the connection string.</span></span> <span data-ttu-id="e7f2e-114">這個方塊的名稱會隨著選取的通訊協定變化。</span><span class="sxs-lookup"><span data-stu-id="e7f2e-114">The name of this box varies with the selected protocol.</span></span>  
  
 <span data-ttu-id="e7f2e-115">**通訊協定**</span><span class="sxs-lookup"><span data-stu-id="e7f2e-115">**Protocol**</span></span>  
 <span data-ttu-id="e7f2e-116">用於連接的通訊協定。</span><span class="sxs-lookup"><span data-stu-id="e7f2e-116">The protocol used for the connection.</span></span>  
  
 <span data-ttu-id="e7f2e-117">**Server**</span><span class="sxs-lookup"><span data-stu-id="e7f2e-117">**Server**</span></span>  
 <span data-ttu-id="e7f2e-118">要連接的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="e7f2e-118">The name of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance being connected to.</span></span>  
  
## <a name="when-to-use-an-alias"></a><span data-ttu-id="e7f2e-119">使用別名的時機</span><span class="sxs-lookup"><span data-stu-id="e7f2e-119">When to Use an Alias</span></span>  
 <span data-ttu-id="e7f2e-120">依預設， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 共用記憶體 **通訊協定來連接到** 的本機執行個體；使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] TCP/IP **或** 具名管道 **來連接到其他電腦上的**執行個體。</span><span class="sxs-lookup"><span data-stu-id="e7f2e-120">By default, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connects to a local instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using the **Shared Memory** protocol, and to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on another computer using either **TCP/IP** or **Named Pipes**.</span></span> <span data-ttu-id="e7f2e-121">當您想要使用 TCP/IP 或具名管道，並且想要提供自訂連接字串，或當您想要使用其他名稱 (而不使用伺服器名稱) 來進行連接時，請建立別名。</span><span class="sxs-lookup"><span data-stu-id="e7f2e-121">Create an alias when you are using TCP/IP or named pipes, and you want to provide a customized connection string, or when you want to use a name other than the server name for the connection.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="e7f2e-122">範例</span><span class="sxs-lookup"><span data-stu-id="e7f2e-122">Examples</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="e7f2e-123">並非接聽預設 TCP/IP 通訊埠 1433，因此您必須為連接字串提供其他連接埠號碼。</span><span class="sxs-lookup"><span data-stu-id="e7f2e-123">is not listening on the default TCP/IP port of 1433 so you want to provide a connection string with a different port number.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="e7f2e-124">並非接聽預設具名管道，因此您必須為連接字串提供其他管道名稱。</span><span class="sxs-lookup"><span data-stu-id="e7f2e-124">is not listening on the default named pipe so you want to provide a connection string with a different pipe name.</span></span>  
  
-   <span data-ttu-id="e7f2e-125">應用程式想要連接到伺服器上的 `ACCT`資料庫，但該資料庫已被合併為 `ACCT` 伺服器上的 `CENTRAL`執行個體。</span><span class="sxs-lookup"><span data-stu-id="e7f2e-125">An application expects to connect to a database on the server named `ACCT`, but that database has been consolidated as an instance named `ACCT` on a server named `CENTRAL`.</span></span> <span data-ttu-id="e7f2e-126">該應用程式無法輕易修改。</span><span class="sxs-lookup"><span data-stu-id="e7f2e-126">The application cannot easily be changed.</span></span> <span data-ttu-id="e7f2e-127">您可以建立名為 `ACCT`的別名，其連接字串指向 `CENTRAL\ACCT`。</span><span class="sxs-lookup"><span data-stu-id="e7f2e-127">Create an alias named `ACCT`, with a connection string pointing to `CENTRAL\ACCT`.</span></span>  
  
## <a name="creating-a-valid-connection-string"></a><span data-ttu-id="e7f2e-128">建立有效的連接字串</span><span class="sxs-lookup"><span data-stu-id="e7f2e-128">Creating a Valid Connection String</span></span>  
 <span data-ttu-id="e7f2e-129">如需有效別名屬性組合的範例描述，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="e7f2e-129">See the following topics for a description and examples of valid combinations of alias properties:</span></span>  
  
-   [<span data-ttu-id="e7f2e-130">使用共用記憶體通訊協定建立有效的連接字串</span><span class="sxs-lookup"><span data-stu-id="e7f2e-130">Creating a Valid Connection String Using Shared Memory Protocol</span></span>](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-shared-memory-protocol.md)  
  
-   [<span data-ttu-id="e7f2e-131">使用 TCP IP 建立有效的連接字串</span><span class="sxs-lookup"><span data-stu-id="e7f2e-131">Creating a Valid Connection String Using TCP IP</span></span>](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-tcp-ip.md)  
  
-   [<span data-ttu-id="e7f2e-132">使用具名管道建立有效的連接字串</span><span class="sxs-lookup"><span data-stu-id="e7f2e-132">Creating a Valid Connection String Using Named Pipes</span></span>](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-named-pipes.md)  
  
  
