---
title: 啟動 sqlcmd 公用程式
ms.custom: seo-lt-2019
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 00d57437-7a29-4da1-b639-ee990db055fb
author: rothja
ms.author: jroth
ms.openlocfilehash: d71e6f140238599b3f22850ee9b63a0ee25d900b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592579"
---
# <a name="start-the-sqlcmd-utility"></a><span data-ttu-id="2fdc3-102">啟動 sqlcmd 公用程式</span><span class="sxs-lookup"><span data-stu-id="2fdc3-102">Start the sqlcmd Utility</span></span>
  <span data-ttu-id="2fdc3-103">若要開始使用 `sqlcmd`，您必須先啟動該公用程式並連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="2fdc3-103">To begin using `sqlcmd`, you must first launch the utility and connect to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="2fdc3-104">您可以連接到預設或具名執行個體。</span><span class="sxs-lookup"><span data-stu-id="2fdc3-104">You can connect to either a default or named instance.</span></span> <span data-ttu-id="2fdc3-105">啟動 `sqlcmd` 公用程式是第一個步驟。</span><span class="sxs-lookup"><span data-stu-id="2fdc3-105">The first step is to start the `sqlcmd` utility.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2fdc3-106">`sqlcmd` 的預設驗證模式為 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="2fdc3-106">Windows Authentication is the default authentication mode for `sqlcmd`.</span></span> <span data-ttu-id="2fdc3-107">若要使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證，必須使用 **-U** 和 **-P** 選項來指定使用者名稱及密碼。</span><span class="sxs-lookup"><span data-stu-id="2fdc3-107">To use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication, you must specify a user name and password by using the **-U** and **-P** options.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2fdc3-108">根據預設， [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] 會安裝成具名執行個體 **sqlexpress**。</span><span class="sxs-lookup"><span data-stu-id="2fdc3-108">By default, [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] installs as the named instance **sqlexpress**.</span></span>  
  
 <span data-ttu-id="2fdc3-109">如果您從未連接過此 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 的執行個體，可能必須設定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 以接受連接。</span><span class="sxs-lookup"><span data-stu-id="2fdc3-109">If you have not connected to this instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] before, you may have to configure [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to accept connections.</span></span>  
  
### <a name="to-start-the-sqlcmd-utility-and-connect-to-a-default-instance-of-sql-server"></a><span data-ttu-id="2fdc3-110">啟動 sqlcmd 公用程式和連接 SQL Server 的預設執行個體</span><span class="sxs-lookup"><span data-stu-id="2fdc3-110">To start the sqlcmd utility and connect to a default instance of SQL Server</span></span>  
  
1.  <span data-ttu-id="2fdc3-111">在 [**開始**] 功能表上按一下 [**執行**]。</span><span class="sxs-lookup"><span data-stu-id="2fdc3-111">On the **Start** menu click **Run**.</span></span> <span data-ttu-id="2fdc3-112">在 [開啟]\*\*\*\* 方塊中，輸入 **cmd**，然後按一下 [確定]\*\*\*\* 開啟 [命令提示字元] 視窗。</span><span class="sxs-lookup"><span data-stu-id="2fdc3-112">In the **Open** box type **cmd**, and then click **OK** to open a Command Prompt window.</span></span>  
  
2.  <span data-ttu-id="2fdc3-113">在命令提示字元中，輸入 `sqlcmd`。</span><span class="sxs-lookup"><span data-stu-id="2fdc3-113">At the command prompt, type `sqlcmd`.</span></span>  
  
3.  <span data-ttu-id="2fdc3-114">按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="2fdc3-114">Press ENTER.</span></span>  
  
     <span data-ttu-id="2fdc3-115">現在，您已經有了信任連接，連接了電腦上所執行的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的預設執行個體。</span><span class="sxs-lookup"><span data-stu-id="2fdc3-115">You now have a trusted connection to the default instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that is running on your computer.</span></span>  
  
     <span data-ttu-id="2fdc3-116">**1>** 是 `sqlcmd` 指定行號的提示。</span><span class="sxs-lookup"><span data-stu-id="2fdc3-116">**1>** is the `sqlcmd` prompt that specifies the line number.</span></span> <span data-ttu-id="2fdc3-117">每按一次 ENTER 鍵，這個號碼就會增加 1。</span><span class="sxs-lookup"><span data-stu-id="2fdc3-117">Each time you press ENTER, the number increases by one.</span></span>  
  
4.  <span data-ttu-id="2fdc3-118">若要結束 `sqlcmd` 會話，請 `EXIT` 在提示字元中輸入 `sqlcmd` 。</span><span class="sxs-lookup"><span data-stu-id="2fdc3-118">To end the `sqlcmd` session, type `EXIT` at the `sqlcmd` prompt.</span></span>  
  
### <a name="to-start-the-sqlcmd-utility-and-connect-to-a-named-instance-of-sql-server"></a><span data-ttu-id="2fdc3-119">啟動 sqlcmd 公用程式並連接到 SQL Server 的具名執行個體</span><span class="sxs-lookup"><span data-stu-id="2fdc3-119">To start the sqlcmd utility and connect to a named instance of SQL Server</span></span>  
  
1.  <span data-ttu-id="2fdc3-120">開啟 [命令提示字元] 視窗，然後輸入 `sqlcmd -S` *myServer\instanceName*。</span><span class="sxs-lookup"><span data-stu-id="2fdc3-120">Open a Command Prompt window, and type `sqlcmd -S`*myServer\instanceName*.</span></span> <span data-ttu-id="2fdc3-121">以要連接的電腦名稱和 *的執行個體來取代* myServer\instanceName [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="2fdc3-121">Replace *myServer\instanceName* with the name of the computer and the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that you want to connect to.</span></span>  
  
2.  <span data-ttu-id="2fdc3-122">按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="2fdc3-122">Press ENTER.</span></span>  
  
     <span data-ttu-id="2fdc3-123">`sqlcmd`提示 (1>) 表示您已連接到指定的實例 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="2fdc3-123">The `sqlcmd` prompt (1>) indicates that you are connected to the specified instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2fdc3-124">輸入的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式會儲存在緩衝區。</span><span class="sxs-lookup"><span data-stu-id="2fdc3-124">Entered [!INCLUDE[tsql](../../includes/tsql-md.md)] statements are stored in a buffer.</span></span> <span data-ttu-id="2fdc3-125">當遇到 GO 命令時，這些陳述式會當做批次來執行。</span><span class="sxs-lookup"><span data-stu-id="2fdc3-125">They are executed as a batch when the GO command is encountered.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2fdc3-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2fdc3-126">See Also</span></span>  
 [<span data-ttu-id="2fdc3-127">使用 sqlcmd 執行 Transact-SQL 指令碼檔案</span><span class="sxs-lookup"><span data-stu-id="2fdc3-127">Run Transact-SQL Script Files Using sqlcmd</span></span>](sqlcmd-run-transact-sql-script-files.md)  
  
  
