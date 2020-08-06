---
title: 註冊已連線的伺服器
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.swb.registerserver.f1
helpviewer_keywords:
- Registered Servers [SQL Server], register connected servers
- connected server registrations [SQL Server]
ms.assetid: 77deb5f5-0f80-484f-8b8b-29afa67ec18f
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 1d337d2da7d305165307745fb02526e37b53bbd3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594316"
---
# <a name="register-a-connected-server-sql-server-management-studio"></a><span data-ttu-id="85a0b-102">註冊連接的伺服器 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="85a0b-102">Register a Connected Server (SQL Server Management Studio)</span></span>
  <span data-ttu-id="85a0b-103">此主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ，在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中註冊伺服器。</span><span class="sxs-lookup"><span data-stu-id="85a0b-103">This topic describes how to register servers in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="85a0b-104">透過註冊伺服器，您可以儲存經常存取之伺服器的連接資訊。</span><span class="sxs-lookup"><span data-stu-id="85a0b-104">By registering the server, you can save the connection information for servers that you access frequently.</span></span> <span data-ttu-id="85a0b-105">您可以在連接之前或連接時從 [物件總管] 註冊伺服器。</span><span class="sxs-lookup"><span data-stu-id="85a0b-105">A server can be registered before connecting, or at the time of connection from Object Explorer.</span></span>  
  
 <span data-ttu-id="85a0b-106">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="85a0b-106">**In This Topic**</span></span>  
  
-   <span data-ttu-id="85a0b-107">**若要使用下列項目註冊伺服器：**</span><span class="sxs-lookup"><span data-stu-id="85a0b-107">**To register a server, using:**</span></span>  
  
     [<span data-ttu-id="85a0b-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="85a0b-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="85a0b-109">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="85a0b-109">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-register-a-connected-server"></a><span data-ttu-id="85a0b-110">若要註冊連接的伺服器</span><span class="sxs-lookup"><span data-stu-id="85a0b-110">To register a connected server</span></span>  
  
1.  <span data-ttu-id="85a0b-111">在物件總管中，以滑鼠右鍵按一下已連接的伺服器，然後按一下 [註冊]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="85a0b-111">In Object Explorer, right-click a server to which you already are connected, and then click **Register**.</span></span>  
  
     <span data-ttu-id="85a0b-112">**伺服器名稱**</span><span class="sxs-lookup"><span data-stu-id="85a0b-112">**Server name**</span></span>  
     <span data-ttu-id="85a0b-113">輸入您要用於已註冊之伺服器的名稱。</span><span class="sxs-lookup"><span data-stu-id="85a0b-113">Enter the name you want to use for the registered server.</span></span> <span data-ttu-id="85a0b-114">使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 註冊本機或遠端伺服器，可以讓您儲存伺服器連接資訊供未來連接使用。</span><span class="sxs-lookup"><span data-stu-id="85a0b-114">Registering a local or remote server using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] lets you store the server connection information for future connections.</span></span> <span data-ttu-id="85a0b-115">此欄位的預設值為您連接到伺服器時所輸入的伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="85a0b-115">This field defaults to the server name entered when you were connecting to the server.</span></span> <span data-ttu-id="85a0b-116">您可以保留此伺服器名稱，或輸入伺服器的另一個易用名稱。</span><span class="sxs-lookup"><span data-stu-id="85a0b-116">You can retain this server name or enter another easy-to-use name for the server.</span></span>  
  
     <span data-ttu-id="85a0b-117">**伺服器描述**</span><span class="sxs-lookup"><span data-stu-id="85a0b-117">**Server description**</span></span>  
     <span data-ttu-id="85a0b-118">輸入伺服器的選擇性描述。</span><span class="sxs-lookup"><span data-stu-id="85a0b-118">Enter an optional description of the server.</span></span> <span data-ttu-id="85a0b-119">允許的最大字元數為 250。</span><span class="sxs-lookup"><span data-stu-id="85a0b-119">The maximum number of characters allowed is 250.</span></span>  
  
     <span data-ttu-id="85a0b-120">**選取伺服器群組**</span><span class="sxs-lookup"><span data-stu-id="85a0b-120">**Select a server group**</span></span>  
     <span data-ttu-id="85a0b-121">選取您要儲存伺服器註冊的伺服器群組。</span><span class="sxs-lookup"><span data-stu-id="85a0b-121">Select the server group where you want to save the server registration.</span></span>  
  
     <span data-ttu-id="85a0b-122">**新增群組**</span><span class="sxs-lookup"><span data-stu-id="85a0b-122">**New Group**</span></span>  
     <span data-ttu-id="85a0b-123">按一下即可啟動 [新增群組]\*\*\*\* 對話方塊，您可以在此為已註冊的伺服器建立新的伺服器群組。</span><span class="sxs-lookup"><span data-stu-id="85a0b-123">Click to launch the **New Group** dialog box, where you can create a new server group for the registered server.</span></span>  
  
     <span data-ttu-id="85a0b-124">**儲存**</span><span class="sxs-lookup"><span data-stu-id="85a0b-124">**Save**</span></span>  
     <span data-ttu-id="85a0b-125">按一下即可儲存您所輸入的資訊，然後建立已註冊的伺服器。</span><span class="sxs-lookup"><span data-stu-id="85a0b-125">Click to save the information you have entered and create a registered server.</span></span>  
  
  
