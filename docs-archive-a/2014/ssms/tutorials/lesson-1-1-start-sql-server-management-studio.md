---
title: 啟動 SQL Server Management Studio | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: 25ffaea6-0eee-4169-8dd0-1da417c28fc6
author: stevestein
ms.author: sstein
ms.openlocfilehash: a8fc9de4884da9a4c372eecdeb6fde12cf3c507e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686724"
---
# <a name="start-sql-server-management-studio"></a><span data-ttu-id="4fb47-102">啟動 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="4fb47-102">Start SQL Server Management Studio</span></span>
  <span data-ttu-id="4fb47-103">在開始這個教學課程之前，我們先看一下 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="4fb47-103">To begin this tutorial, let's take a look at [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
## <a name="opening-sql-server-management-studio"></a><span data-ttu-id="4fb47-104">開啟 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="4fb47-104">Opening SQL Server Management Studio</span></span>  
  
#### <a name="to-open-sql-server-management-studio"></a><span data-ttu-id="4fb47-105">開啟 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="4fb47-105">To open SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="4fb47-106">在 [**開始**] 功能表上，依序指向 [**所有程式**] 和 [] [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)] ，然後按一下 [ **SQL Server Management Studio**]。</span><span class="sxs-lookup"><span data-stu-id="4fb47-106">On the **Start** menu, point to **All Programs**, point to [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], and then click **SQL Server Management Studio**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4fb47-107">預設不會安裝 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="4fb47-107">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] is not installed by default.</span></span> <span data-ttu-id="4fb47-108">如果沒有 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]，請執行安裝程式來安裝它。</span><span class="sxs-lookup"><span data-stu-id="4fb47-108">If [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] is unavailable, install it by running Setup.</span></span> [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] <span data-ttu-id="4fb47-109">未提供 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="4fb47-109">is not available with [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)].</span></span> [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]<span data-ttu-id="4fb47-110">Express 可從[Microsoft 下載中心](https://www.microsoft.com/download/details.aspx?id=14630)免費下載，但其使用者介面與本教學課程中所述的不同。</span><span class="sxs-lookup"><span data-stu-id="4fb47-110">Express is available as a free download from the [Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=14630), but has a different user interface than is described in this tutorial.</span></span>  
  
2.  <span data-ttu-id="4fb47-111">在 [連接到伺服器]\*\*\*\* 對話方塊中，驗證預設值，然後按一下 [連接]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4fb47-111">In the **Connect to Server** dialog box, verify the default settings, and then click **Connect**.</span></span> <span data-ttu-id="4fb47-112">若要連接，[**伺服器名稱**] 方塊必須包含已安裝之電腦的名稱 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="4fb47-112">To connect, the **Server name** box must contain the name of the computer where [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is installed.</span></span> <span data-ttu-id="4fb47-113">如果 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 是已命名的實例，[**伺服器名稱**] 方塊也應該包含實例名稱，格式為 \<*computer_name*> \\ < *instance_name*>。</span><span class="sxs-lookup"><span data-stu-id="4fb47-113">If the [!INCLUDE[ssDE](../../includes/ssde-md.md)] is a named instance, the **Server name** box should also contain the instance name in the format \<*computer_name*>\\<*instance_name*>.</span></span>  
  
## <a name="management-studio-components"></a><span data-ttu-id="4fb47-114">Management Studio 元件</span><span class="sxs-lookup"><span data-stu-id="4fb47-114">Management Studio Components</span></span>  
 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] <span data-ttu-id="4fb47-115">在特定資訊類型專用的視窗中呈現資訊。</span><span class="sxs-lookup"><span data-stu-id="4fb47-115">presents information in windows dedicated to specific types of information.</span></span> <span data-ttu-id="4fb47-116">資料庫資訊是顯示在「物件總管」和文件視窗中。</span><span class="sxs-lookup"><span data-stu-id="4fb47-116">Database information is shown in Object Explorer and document windows.</span></span>  
  
-   <span data-ttu-id="4fb47-117">物件總管是含有伺服器中所有資料庫物件的樹狀檢視。</span><span class="sxs-lookup"><span data-stu-id="4fb47-117">Object Explorer is a tree view of all the database objects in a server.</span></span> <span data-ttu-id="4fb47-118">其中可包括 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]和 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]的資料庫。</span><span class="sxs-lookup"><span data-stu-id="4fb47-118">This can include the databases of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], and [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].</span></span> <span data-ttu-id="4fb47-119">物件總管含有它所連接的所有伺服器的資訊。</span><span class="sxs-lookup"><span data-stu-id="4fb47-119">Object Explorer includes information for all servers to which it is connected.</span></span> <span data-ttu-id="4fb47-120">當您開啟 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]時，系統會提示您將物件總管連接到上次使用的設定。</span><span class="sxs-lookup"><span data-stu-id="4fb47-120">When you open [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], you are prompted to connect Object Explorer to the settings that were last used.</span></span> <span data-ttu-id="4fb47-121">您可以在 [已註冊的伺服器] 元件中，按兩下任何伺服器來連接它，但您不需要註冊要連接的伺服器。</span><span class="sxs-lookup"><span data-stu-id="4fb47-121">You can double-click any server in the Registered Servers component to connect to it, but you do not have to register a server to connect.</span></span>  
  
-   <span data-ttu-id="4fb47-122">文件視窗是 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]最大的部分。</span><span class="sxs-lookup"><span data-stu-id="4fb47-122">The document window is the largest portion of [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span> <span data-ttu-id="4fb47-123">文件視窗可包含查詢編輯器和瀏覽器視窗。</span><span class="sxs-lookup"><span data-stu-id="4fb47-123">The document windows can contain query editors and browser windows.</span></span> <span data-ttu-id="4fb47-124">預設會顯示目前電腦中 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 執行個體所連接的 [摘要] 頁面。</span><span class="sxs-lookup"><span data-stu-id="4fb47-124">By default, the Summary page is displayed, connected to the instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)] on the current computer.</span></span>  
  
## <a name="showing-additional-windows"></a><span data-ttu-id="4fb47-125">顯示其他視窗</span><span class="sxs-lookup"><span data-stu-id="4fb47-125">Showing Additional Windows</span></span>  
  
#### <a name="to-show-the-registered-servers-window"></a><span data-ttu-id="4fb47-126">顯示 [已註冊的伺服器] 視窗</span><span class="sxs-lookup"><span data-stu-id="4fb47-126">To show the Registered Servers window</span></span>  
  
1.  <span data-ttu-id="4fb47-127">在 [檢視]\*\*\*\* 功能表上，按一下 [已註冊的伺服器]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4fb47-127">On the **View** menu, click **Registered Servers**.</span></span>  
  
     <span data-ttu-id="4fb47-128">[已註冊的伺服器] 視窗會出現在「物件總管」上方。</span><span class="sxs-lookup"><span data-stu-id="4fb47-128">The Registered Servers window appears above Object Explorer.</span></span> <span data-ttu-id="4fb47-129">[已註冊的伺服器] 會列出您經常管理的伺服器。</span><span class="sxs-lookup"><span data-stu-id="4fb47-129">Registered Servers lists servers which you manage frequently.</span></span> <span data-ttu-id="4fb47-130">您可以在這份清單中，新增和移除伺服器。</span><span class="sxs-lookup"><span data-stu-id="4fb47-130">You can add and remove servers from this list.</span></span> <span data-ttu-id="4fb47-131">列出的伺服器只包括您執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 之電腦中的 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="4fb47-131">The only servers listed are the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instances on the computer where you are running [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span>  
  
2.  <span data-ttu-id="4fb47-132">如果您的伺服器沒有出現，請在 [已註冊的伺服器] 中，以滑鼠右鍵按一下 [**資料庫引擎**]，然後按一下 [**更新本機伺服器註冊**]。</span><span class="sxs-lookup"><span data-stu-id="4fb47-132">If your server does not appear, in Registered Servers, right-click **Database Engine**, and then click **Update Local Server Registration**.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="4fb47-133">本課程的下一項工作</span><span class="sxs-lookup"><span data-stu-id="4fb47-133">Next Task in Lesson</span></span>  
 [<span data-ttu-id="4fb47-134">連接已註冊的伺服器和物件總管</span><span class="sxs-lookup"><span data-stu-id="4fb47-134">Connect with Registered Servers and Object Explorer</span></span>](../object/object-explorer.md)  
  
  
