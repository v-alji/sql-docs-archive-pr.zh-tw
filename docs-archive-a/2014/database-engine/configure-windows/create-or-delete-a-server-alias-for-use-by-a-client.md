---
title: 建立或刪除伺服器別名，以供用戶端 (SQL Server 組態管理員) 使用 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- server alias
helpviewer_keywords:
- aliases [SQL Server], deleting
- aliases [SQL Server], creating
ms.assetid: b687e376-ee33-470d-b65a-87246bfefe6f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: bead257b40c33e3640b18890a7d109d774131123
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596906"
---
# <a name="create-or-delete-a-server-alias-for-use-by-a-client-sql-server-configuration-manager"></a><span data-ttu-id="84ee1-102">建立或刪除用戶端使用的伺服器別名 (SQL Server 組態管理員)</span><span class="sxs-lookup"><span data-stu-id="84ee1-102">Create or Delete a Server Alias for Use by a Client (SQL Server Configuration Manager)</span></span>
  <span data-ttu-id="84ee1-103">此主題描述如何使用 SQL Server 組態管理員，在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中建立或刪除伺服器別名。</span><span class="sxs-lookup"><span data-stu-id="84ee1-103">This topic describes how to create or delete a server alias in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using SQL Server Configuration Manager.</span></span> <span data-ttu-id="84ee1-104">別名是可用於進行連接的替代名稱。</span><span class="sxs-lookup"><span data-stu-id="84ee1-104">An alias is an alternate name that can be used to make a connection.</span></span> <span data-ttu-id="84ee1-105">別名會封裝連接字串的必要元素，並以使用者選擇的名稱來公開這些元素。</span><span class="sxs-lookup"><span data-stu-id="84ee1-105">The alias encapsulates the required elements of a connection string, and exposes them with a name chosen by the user.</span></span> <span data-ttu-id="84ee1-106">別名可用於任何用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="84ee1-106">Aliases can be used with any client application.</span></span> <span data-ttu-id="84ee1-107">藉由建立伺服器別名，用戶端電腦可使用不同網路通訊協定來連接到多個伺服器，而不必指定每一個伺服器的通訊協定和連接詳細資料。</span><span class="sxs-lookup"><span data-stu-id="84ee1-107">By creating server aliases, your client computer can connect to multiple servers using different network protocols, without having to specify the protocol and connection details for each one.</span></span> <span data-ttu-id="84ee1-108">此外，您也可以一直啟用不同的網路通訊協定，即使您只需要偶而使用它們。</span><span class="sxs-lookup"><span data-stu-id="84ee1-108">In addition, you can also have different network protocols enabled all the time, even if you only need to use them occasionally.</span></span> <span data-ttu-id="84ee1-109">若您已設定伺服器在非預設通訊埠編號或具名管道上接聽，且您已停用 SQL Server Browser 服務，請建立指定新通訊埠編號或具名管道的別名。</span><span class="sxs-lookup"><span data-stu-id="84ee1-109">If you have configured the server to listen on a non-default port number or named pipe, and you have disabled the SQL Server Browser service, create an alias that specifies the new port number or named pipe.</span></span>  
  
##  <a name="using-sql-server-configuration-manager"></a><a name="SSMSProcedure"></a> <span data-ttu-id="84ee1-110">使用 SQL Server 組態管理員</span><span class="sxs-lookup"><span data-stu-id="84ee1-110">Using SQL Server Configuration Manager</span></span>  
  
#### <a name="to-create-an-alias"></a><span data-ttu-id="84ee1-111">若要建立別名</span><span class="sxs-lookup"><span data-stu-id="84ee1-111">To create an alias</span></span>  
  
1.  <span data-ttu-id="84ee1-112">在 SQL Server 組態管理員中，展開 [SQL Server Native Client Configuration (SQL Server Native Client 組態)]，並以滑鼠右鍵按一下 [別名]，然後按一下 [新增別名]。</span><span class="sxs-lookup"><span data-stu-id="84ee1-112">In SQL Server Configuration Manager, expand **SQL Server Native Client Configuration**, right-click **Aliases**, and then click **New Alias**.</span></span>  
  
2.  <span data-ttu-id="84ee1-113">在 [別名名稱] 方塊中，輸入別名的名稱。</span><span class="sxs-lookup"><span data-stu-id="84ee1-113">In the **Alias Name** box, type the name of the alias.</span></span> <span data-ttu-id="84ee1-114">當用戶端應用程式連接時使用此名稱。</span><span class="sxs-lookup"><span data-stu-id="84ee1-114">Client applications use this name when they connect.</span></span>  
  
3.  <span data-ttu-id="84ee1-115">在 [伺服器] 方塊中，輸入伺服器的名稱或 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="84ee1-115">In the **Server** box, type the name or IP address of a server.</span></span> <span data-ttu-id="84ee1-116">針對具名執行個體，請附加執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="84ee1-116">For a named instance append the instance name.</span></span>  
  
4.  <span data-ttu-id="84ee1-117">在 [通訊協定] 方塊中，選取用於此別名的通訊協定。</span><span class="sxs-lookup"><span data-stu-id="84ee1-117">In the **Protocol** box, select the protocol used for this alias.</span></span> <span data-ttu-id="84ee1-118">選取通訊協定，將選用屬性方塊的標題變更為「通訊埠編號」、「管道名稱」或「連接字串」。</span><span class="sxs-lookup"><span data-stu-id="84ee1-118">Selecting a protocol, changes the title of the optional properties box to Port No, Pipe Name, or Connection String.</span></span>  
  
 <span data-ttu-id="84ee1-119">＜[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 組態管理員說明＞中描述的連接字串，對於建立自己連接字串的程式設計人員會很有幫助。</span><span class="sxs-lookup"><span data-stu-id="84ee1-119">The connection strings described in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager Help can be useful for programmers who create their own connection strings.</span></span> <span data-ttu-id="84ee1-120">若要存取此資訊，在 [新增別名] 對話方塊，按 F1，或按一下 [說明]。</span><span class="sxs-lookup"><span data-stu-id="84ee1-120">To access this information, in the **New Alias** dialog box, press F1, or click **Help**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="84ee1-121">如果已設定的別名連接到錯誤的伺服器或執行個體，請停用再重新啟用相關的網路通訊協定。</span><span class="sxs-lookup"><span data-stu-id="84ee1-121">If a configured alias is connecting to the wrong server or instance, disable and then reenable the associated network protocol.</span></span> <span data-ttu-id="84ee1-122">這麼做可清除任何快取的連接資訊，讓用戶端能夠正確連接。</span><span class="sxs-lookup"><span data-stu-id="84ee1-122">Doing this clears any cached connection information and allows the client to connect correctly.</span></span>  
  
#### <a name="to-delete-an-alias"></a><span data-ttu-id="84ee1-123">若要刪除別名</span><span class="sxs-lookup"><span data-stu-id="84ee1-123">To delete an alias</span></span>  
  
1.  <span data-ttu-id="84ee1-124">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 組態管理員中，展開 [SQL Server Native Client Configuration (SQL Server Native Client 組態)]，再按一下 [別名]。</span><span class="sxs-lookup"><span data-stu-id="84ee1-124">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, expand **SQL Server Native Client Configuration**, and then click **Aliases**.</span></span>  
  
2.  <span data-ttu-id="84ee1-125">在詳細資料窗格中，以滑鼠右鍵按一下要刪除的別名，然後按一下 [刪除]。</span><span class="sxs-lookup"><span data-stu-id="84ee1-125">In the details pane, right-click the alias that you want to delete, and then click **Delete**.</span></span>  
  
  
