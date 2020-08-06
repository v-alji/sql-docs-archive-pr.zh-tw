---
title: 步驟 3：加入和設定 OLE DB 連線管理員 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: e7b74cba-a0e5-4478-af12-3f81b9484e9e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 3bc4c885ce6c39c72031dd3b528a769cd47ac8f0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596144"
---
# <a name="step-3-adding-and-configuring-an-ole-db-connection-manager"></a><span data-ttu-id="f6b32-102">步驟 3：新增和設定 OLE DB 連線管理員</span><span class="sxs-lookup"><span data-stu-id="f6b32-102">Step 3: Adding and Configuring an OLE DB Connection Manager</span></span>
  <span data-ttu-id="f6b32-103">在加入一般檔案連接管理員來連接到資料來源之後，下一項工作是加入 OLE DB 連接管理員來連接到目的地。</span><span class="sxs-lookup"><span data-stu-id="f6b32-103">After you have added a Flat File connection manager to connect to the data source, the next task is to add an OLE DB connection manager to connect to the destination.</span></span> <span data-ttu-id="f6b32-104">OLE DB 連接管理員可讓封裝從任何 OLE DB 相容資料來源擷取資料或載入資料至該處。</span><span class="sxs-lookup"><span data-stu-id="f6b32-104">An OLE DB connection manager enables a package to extract data from or load data into any OLE DB-compliant data source.</span></span> <span data-ttu-id="f6b32-105">使用 OLE DB 連接管理員，您可以指定連接的伺服器、驗證方法和預設資料庫。</span><span class="sxs-lookup"><span data-stu-id="f6b32-105">Using the OLE DB Connection manager, you can specify the server, the authentication method, and the default database for the connection.</span></span>  
  
 <span data-ttu-id="f6b32-106">在這一課，您將建立 OLE DB 連接管理員，以便使用 Windows 驗證連接到 **AdventureWorksDB2012**的本機執行個體。</span><span class="sxs-lookup"><span data-stu-id="f6b32-106">In this lesson, you will create an OLE DB connection manager that uses Windows Authentication to connect to the local instance of **AdventureWorksDB2012**.</span></span> <span data-ttu-id="f6b32-107">您建立的 OLE DB 連接管理員，也會供您在這個教學課程後面建立的其他元件所參考，例如查閱轉換和 OLE DB 目的地。</span><span class="sxs-lookup"><span data-stu-id="f6b32-107">The OLE DB connection manager that you create will also be referenced by other components that you will create later in this tutorial, such as the Lookup transformation and the OLE DB destination.</span></span>  
  
### <a name="to-add-and-configure-an-ole-db-connection-manager-to-the-ssis-package"></a><span data-ttu-id="f6b32-108">若要將 OLE DB 連接管理員加入至 SSIS 封裝並進行設定</span><span class="sxs-lookup"><span data-stu-id="f6b32-108">To add and configure an OLE DB Connection Manager to the SSIS package</span></span>  
  
1.  <span data-ttu-id="f6b32-109">以滑鼠右鍵按一下 **[連接管理員]** 區域的任何位置，然後按一下 **[新增 OLE DB 連接]**。</span><span class="sxs-lookup"><span data-stu-id="f6b32-109">Right-click anywhere in the **Connection Managers** area, and then click **New OLE DB Connection**.</span></span>  
  
2.  <span data-ttu-id="f6b32-110">在 **[設定 OLE DB 連接管理員]** 對話方塊中，按一下 **[新增]**。</span><span class="sxs-lookup"><span data-stu-id="f6b32-110">In the **Configure OLE DB Connection Manager** dialog box, click **New**.</span></span>  
  
3.  <span data-ttu-id="f6b32-111">對於 **[伺服器名稱]**，輸入 **localhost**。</span><span class="sxs-lookup"><span data-stu-id="f6b32-111">For **Server name**, enter **localhost**.</span></span>  
  
     <span data-ttu-id="f6b32-112">當您指定 localhost 做為伺服器名稱時，連接管理員會連接到本機電腦上 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的預設執行個體。</span><span class="sxs-lookup"><span data-stu-id="f6b32-112">When you specify localhost as the server name, the connection manager connects to the default instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] on the local computer.</span></span> <span data-ttu-id="f6b32-113">若要使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]的遠端執行個體，請將 localhost 取代成您要連接的伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="f6b32-113">To use a remote instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], replace localhost with the name of the server to which you want to connect.</span></span>  
  
4.  <span data-ttu-id="f6b32-114">在 **[登入伺服器]** 群組中，確認已選取 **[使用 Windows 驗證]** 。</span><span class="sxs-lookup"><span data-stu-id="f6b32-114">In the **Log on to the server** group, verify that **Use Windows Authentication** is selected.</span></span>  
  
5.  <span data-ttu-id="f6b32-115">在 [**連接到資料庫]** 群組的 [**選取或輸入資料庫名稱**] 方塊中，輸入或選取 `AdventureWorksDW2012` 。</span><span class="sxs-lookup"><span data-stu-id="f6b32-115">In the **Connect to a database** group, in the **Select or enter a database name** box, type or select `AdventureWorksDW2012`.</span></span>  
  
6.  <span data-ttu-id="f6b32-116">按一下 **[測試連接]** 以確認您指定的連接設定有效。</span><span class="sxs-lookup"><span data-stu-id="f6b32-116">Click **Test Connection** to verify that the connection settings you have specified are valid.</span></span>  
  
7.  <span data-ttu-id="f6b32-117">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="f6b32-117">Click **OK**.</span></span>  
  
8.  <span data-ttu-id="f6b32-118">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="f6b32-118">Click **OK**.</span></span>  
  
9. <span data-ttu-id="f6b32-119">在 **[設定 OLE DB 連接管理員]** 對話方塊的 **[資料連接]** 窗格中，確認已選取 **localhost.AdventureWorksDW2012** 。</span><span class="sxs-lookup"><span data-stu-id="f6b32-119">In the **Data Connections** pane of the **Configure OLE DB Connection Manager** dialog box, verify that **localhost.AdventureWorksDW2012** is selected.</span></span>  
  
10. <span data-ttu-id="f6b32-120">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="f6b32-120">Click **OK**.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="f6b32-121">本課程的下一項工作</span><span class="sxs-lookup"><span data-stu-id="f6b32-121">Next Task in Lesson</span></span>  
 [<span data-ttu-id="f6b32-122">步驟 4：將資料流程工作新增至封裝</span><span class="sxs-lookup"><span data-stu-id="f6b32-122">Step 4: Adding a Data Flow Task to the Package</span></span>](lesson-1-4-adding-a-data-flow-task-to-the-package.md)  
  
## <a name="see-also"></a><span data-ttu-id="f6b32-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f6b32-123">See Also</span></span>  
 [<span data-ttu-id="f6b32-124">OLE DB 連線管理員</span><span class="sxs-lookup"><span data-stu-id="f6b32-124">OLE DB Connection Manager</span></span>](connection-manager/ole-db-connection-manager.md)  
  
  
