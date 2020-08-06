---
title: " (查詢結果和相依性服務頁面的選項) |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.QueryResults.DependencyServicesGeneral
ms.assetid: dd7f6c31-7d7f-4972-854a-1419a2826dca
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 356714ee933fb40eda7038f4088309b6187f3ed8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599178"
---
# <a name="options-query-results-and-dependency-services-page"></a><span data-ttu-id="e6874-102">選項 (查詢結果和相依性服務頁面)</span><span class="sxs-lookup"><span data-stu-id="e6874-102">Options (Query Results and Dependency Services Page)</span></span>
  <span data-ttu-id="e6874-103">使用此頁面可指定要針對相依性服務連接的伺服器。</span><span class="sxs-lookup"><span data-stu-id="e6874-103">Use this page to specify the server to connect for Dependency Services.</span></span> <span data-ttu-id="e6874-104">相依性服務可讓您擷取在不同伺服器上儲存的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 和 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 物件之間的相依性資訊。</span><span class="sxs-lookup"><span data-stu-id="e6874-104">Dependency Services enables you to extract information about dependencies between [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] and [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] objects stored on different servers.</span></span> <span data-ttu-id="e6874-105">您可以使用中的 [**物件**相依性] 對話方塊來查看物件相依性 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="e6874-105">You view object dependencies by using the **Object Dependencies** dialog box in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)].</span></span>  
  
 <span data-ttu-id="e6874-106">**您想要做什麼事？**</span><span class="sxs-lookup"><span data-stu-id="e6874-106">**What do you want to do?**</span></span>  
  
1.  [<span data-ttu-id="e6874-107">開啟選項 (查詢結果/相依性服務頁面) 對話方塊</span><span class="sxs-lookup"><span data-stu-id="e6874-107">Open the Options (Query Results/Dependency Services Page) Dialog Box</span></span>](#open_dialog)  
  
2.  [<span data-ttu-id="e6874-108">設定選項</span><span class="sxs-lookup"><span data-stu-id="e6874-108">Configure the Options</span></span>](#options)  
  
##  <a name="open-the-options-query-resultsdependency-services-page-dialog-box"></a><a name="open_dialog"></a><span data-ttu-id="e6874-109">開啟 (查詢結果/相依性服務頁面) 對話方塊中的選項</span><span class="sxs-lookup"><span data-stu-id="e6874-109">Open the Options (Query Results/Dependency Services Page) Dialog Box</span></span>  
  
1.  <span data-ttu-id="e6874-110">在中 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] ，按一下 [**工具**] 功能表上的 [**選項**]。</span><span class="sxs-lookup"><span data-stu-id="e6874-110">In [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)], click **Options** on the **Tools** menu.</span></span>  
  
2.  <span data-ttu-id="e6874-111">展開 [查詢結果]\*\*\*\*，然後按一下 [相依性服務]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e6874-111">Expand **Query Results**, and then click **Dependency Services**.</span></span>  
  
##  <a name="configure-the-options"></a><a name="options"></a> <span data-ttu-id="e6874-112">設定選項</span><span class="sxs-lookup"><span data-stu-id="e6874-112">Configure the Options</span></span>  
  
### <a name="options"></a><span data-ttu-id="e6874-113">選項。</span><span class="sxs-lookup"><span data-stu-id="e6874-113">Options</span></span>  
 <span data-ttu-id="e6874-114">**相依性服務伺服器**</span><span class="sxs-lookup"><span data-stu-id="e6874-114">**Dependency Services server**</span></span>  
 <span data-ttu-id="e6874-115">指定安裝相依性服務的伺服器。</span><span class="sxs-lookup"><span data-stu-id="e6874-115">Specify the server that Dependency Services is installed on.</span></span>  
  
 <span data-ttu-id="e6874-116">**驗證**</span><span class="sxs-lookup"><span data-stu-id="e6874-116">**Authentication**</span></span>  
 <span data-ttu-id="e6874-117">選取 Windows 驗證來以 Microsoft Windows 使用者帳戶登入，或是選取 SQL Server 驗證。</span><span class="sxs-lookup"><span data-stu-id="e6874-117">Select Windows Authentication to log on using a Microsoft Windows user account, or select SQL Server Authentication.</span></span>  
  
 <span data-ttu-id="e6874-118">當使用者透過不信任連接並指定登入名稱和密碼進行連接時，SQL Server 本身會執行驗證，檢查是否已建立 SQL Server 登入帳戶，而且指定的密碼是否符合先前記錄的密碼。</span><span class="sxs-lookup"><span data-stu-id="e6874-118">When a user connects with a specified login name and password from a non-trusted connection, SQL Server performs the authentication by checking to see if a SQL Server login account has been set up and if the specified password matches the one previously recorded.</span></span> <span data-ttu-id="e6874-119">如果 SQL Server 找不到登入帳戶，驗證將會失敗，而且使用者會收到錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="e6874-119">If SQL Server cannot find the login account, authentication fails, and the user receives an error message.</span></span>  
  
 <span data-ttu-id="e6874-120">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="e6874-120">**User name**</span></span>  
 <span data-ttu-id="e6874-121">如果使用 SQL Server 驗證，請提供使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="e6874-121">If using SQL Server Authentication, provide a user name.</span></span>  
  
 <span data-ttu-id="e6874-122">**密碼**</span><span class="sxs-lookup"><span data-stu-id="e6874-122">**Password**</span></span>  
 <span data-ttu-id="e6874-123">如果使用 SQL Server 驗證，請提供密碼。</span><span class="sxs-lookup"><span data-stu-id="e6874-123">If using SQL Server Authentication, provide a password.</span></span>  
  
 <span data-ttu-id="e6874-124">**Test**</span><span class="sxs-lookup"><span data-stu-id="e6874-124">**Test**</span></span>  
 <span data-ttu-id="e6874-125">按一下來測試連接。</span><span class="sxs-lookup"><span data-stu-id="e6874-125">Click to test the connection.</span></span>