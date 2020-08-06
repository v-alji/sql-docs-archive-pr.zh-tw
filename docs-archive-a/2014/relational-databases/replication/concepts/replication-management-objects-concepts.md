---
title: 複寫管理物件概念 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- replication [SQL Server], RMO
- programming interfaces [SQL Server replication]
- replication [SQL Server], how-to topics
- RMO [SQL Server]
- Replication Management Objects
- programming [SQL Server replication], RMO
ms.assetid: 37476d50-fb47-49e3-9504-3b163ac381d8
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0dc41416e0fb585db376c6b72f28f7c30cfff052
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595921"
---
# <a name="replication-management-objects-concepts"></a><span data-ttu-id="0c02d-102">Replication Management Objects Concepts</span><span class="sxs-lookup"><span data-stu-id="0c02d-102">Replication Management Objects Concepts</span></span>
  <span data-ttu-id="0c02d-103">Replication Management Objects (RMO) 是一種 Managed 程式碼組件，用以封裝 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的複寫功能。</span><span class="sxs-lookup"><span data-stu-id="0c02d-103">Replication Management Objects (RMO) is a managed code assembly that encapsulates replication functionalities for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="0c02d-104">RMO 是由 <xref:Microsoft.SqlServer.Replication> 命名空間實作。</span><span class="sxs-lookup"><span data-stu-id="0c02d-104">RMO is implemented by the <xref:Microsoft.SqlServer.Replication> namespace.</span></span>  
  
 <span data-ttu-id="0c02d-105">下列章節中的主題將說明如何使用 RMO 屬性，以程式設計方式控制複寫工作。</span><span class="sxs-lookup"><span data-stu-id="0c02d-105">The topics in the following sections describe how you can use RMO to programmatically control replication tasks:</span></span>  
  
 [<span data-ttu-id="0c02d-106">設定散發</span><span class="sxs-lookup"><span data-stu-id="0c02d-106">Configure Distribution</span></span>](../configure-distribution.md)  
 <span data-ttu-id="0c02d-107">本節中的主題示範如何使用 RMO 來設定發行與散發。</span><span class="sxs-lookup"><span data-stu-id="0c02d-107">Topics in this section show how to use RMO to configure publishing and distribution.</span></span>  
  
 [<span data-ttu-id="0c02d-108">建立發行集</span><span class="sxs-lookup"><span data-stu-id="0c02d-108">Create a Publication</span></span>](../publish/create-a-publication.md)  
 <span data-ttu-id="0c02d-109">本章節中的主題示範如何使用 RMO 來建立、刪除和修改發行集與發行項。</span><span class="sxs-lookup"><span data-stu-id="0c02d-109">Topics in this section show how to use RMO to create, delete, and modify publications and articles.</span></span>  
  
 [<span data-ttu-id="0c02d-110">訂閱發行集</span><span class="sxs-lookup"><span data-stu-id="0c02d-110">Subscribe to Publications</span></span>](../subscribe-to-publications.md)  
 <span data-ttu-id="0c02d-111">本章節中的主題示範如何使用 RMO 來建立、刪除和修改訂閱。</span><span class="sxs-lookup"><span data-stu-id="0c02d-111">Topics in this section show how to use RMO to create, delete, and modify subscriptions.</span></span>  
  
 [<span data-ttu-id="0c02d-112">保護複寫拓撲</span><span class="sxs-lookup"><span data-stu-id="0c02d-112">Secure a Replication Topology</span></span>](../security/view-and-modify-replication-security-settings.md)  
 <span data-ttu-id="0c02d-113">本章節中的主題示範如何使用 RMO 來檢視和修改安全性設定。</span><span class="sxs-lookup"><span data-stu-id="0c02d-113">Topics in this section show how to use RMO to view and modify security settings.</span></span>  
  
 [<span data-ttu-id="0c02d-114">同步處理訂閱 &#40;複寫&#41;</span><span class="sxs-lookup"><span data-stu-id="0c02d-114">Synchronize Subscriptions &#40;Replication&#41;</span></span>](../synchronize-data.md)  
 <span data-ttu-id="0c02d-115">本章節中的主題示範如何同步處理訂閱。</span><span class="sxs-lookup"><span data-stu-id="0c02d-115">Topics in this section show how to synchronize subscriptions.</span></span>  
  
 [<span data-ttu-id="0c02d-116">監視複寫</span><span class="sxs-lookup"><span data-stu-id="0c02d-116">Monitoring Replication</span></span>](../monitoring-replication.md)  
 <span data-ttu-id="0c02d-117">本章節中的主題示範如何以程式設計方式監視複寫拓撲。</span><span class="sxs-lookup"><span data-stu-id="0c02d-117">Topics in this section show how to programmatically monitor a replication topology.</span></span>  
  
## <a name="introduction-to-rmo-programming"></a><span data-ttu-id="0c02d-118">RMO 程式設計簡介</span><span class="sxs-lookup"><span data-stu-id="0c02d-118">Introduction to RMO Programming</span></span>  
 <span data-ttu-id="0c02d-119">RMO 是針對程式設計 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 複寫的所有層面所設計。</span><span class="sxs-lookup"><span data-stu-id="0c02d-119">RMO is designed for programming all aspects of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] replication.</span></span> <span data-ttu-id="0c02d-120">RMO 命名空間是 <xref:Microsoft.SqlServer.Replication>，而且它是 Microsoft.SqlServer.Rmo.dll 所實作，這個檔案是 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework 組件。</span><span class="sxs-lookup"><span data-stu-id="0c02d-120">The RMO namespace is <xref:Microsoft.SqlServer.Replication>, and it is implemented by the Microsoft.SqlServer.Rmo.dll, which is a [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework assembly.</span></span> <span data-ttu-id="0c02d-121">同時也屬於 <xref:Microsoft.SqlServer.Replication> 命名空間的 Microsoft.SqlServer.Replication.dll 組件，會實作 Managed 程式碼介面，以設計各種複寫代理程式的程式 (快照集代理程式、散發代理程式以及合併代理程式)。</span><span class="sxs-lookup"><span data-stu-id="0c02d-121">The Microsoft.SqlServer.Replication.dll assembly, which also belongs to the <xref:Microsoft.SqlServer.Replication> namespace, implements a managed code interface for programming the various replication agents (Snapshot Agent, Distribution Agent, and Merge Agent).</span></span> <span data-ttu-id="0c02d-122">可從 RMO 存取其類別以同步處理訂閱。</span><span class="sxs-lookup"><span data-stu-id="0c02d-122">Its classes can be accessed from RMO to synchronize subscriptions.</span></span> <span data-ttu-id="0c02d-123">在由 Microsoft.SqlServer.Replication.BusinessLogicSupport.dll 組件所實作的 <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport> 命名空間中的類別，是用以為合併式複寫建立自訂商務邏輯。</span><span class="sxs-lookup"><span data-stu-id="0c02d-123">Classes in the <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport> namespace, implemented by the Microsoft.SqlServer.Replication.BusinessLogicSupport.dll assembly, are used to create custom business logic for merge replication.</span></span> <span data-ttu-id="0c02d-124">這個組件與 RMO 無關。</span><span class="sxs-lookup"><span data-stu-id="0c02d-124">This assembly is independent from RMO.</span></span>  
  
## <a name="deploying-applications-based-on-rmo"></a><span data-ttu-id="0c02d-125">根據 RMO 部署應用程式</span><span class="sxs-lookup"><span data-stu-id="0c02d-125">Deploying Applications Based on RMO</span></span>  
 <span data-ttu-id="0c02d-126">RMO 相依於隨附在所有版本的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (但 SQL Server Compact 除外) 中之複寫元件與用戶端連線元件。</span><span class="sxs-lookup"><span data-stu-id="0c02d-126">RMO depends on the replication components and client connectivity components that are included with all versions of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] except SQL Server Compact.</span></span> <span data-ttu-id="0c02d-127">若要根據 RMO 部署應用程式，您必須在應用程式將執行的電腦上，安裝含有複寫元件與用戶端連線元件的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 版本。</span><span class="sxs-lookup"><span data-stu-id="0c02d-127">To deploy an application based on RMO, you must install a version of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that includes replication components and client connectivity components on the computer on which the application will run.</span></span>  
  
## <a name="getting-started-with-rmo"></a><span data-ttu-id="0c02d-128">RMO 使用者入門</span><span class="sxs-lookup"><span data-stu-id="0c02d-128">Getting Started with RMO</span></span>  
 <span data-ttu-id="0c02d-129">本章節描述如何使用 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Studio 啟動簡單的 RMO 專案。</span><span class="sxs-lookup"><span data-stu-id="0c02d-129">This section describes how to start a simple RMO project using [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Studio.</span></span>  
  
#### <a name="to-create-a-new-microsoft-visual-c-project"></a><span data-ttu-id="0c02d-130">若要建立新的 Microsoft Visual C# 專案</span><span class="sxs-lookup"><span data-stu-id="0c02d-130">To create a new Microsoft Visual C# project</span></span>  
  
1.  <span data-ttu-id="0c02d-131">啟動 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="0c02d-131">Start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="0c02d-132">在 [檔案]  功能表上，按一下 [新增專案]  。</span><span class="sxs-lookup"><span data-stu-id="0c02d-132">On the **File** menu, click **NewProject.**</span></span> <span data-ttu-id="0c02d-133">[新增專案]  對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="0c02d-133">The **New Project** dialog box appears.</span></span>  
  
3.  <span data-ttu-id="0c02d-134">在 [專案類型]  對話方塊中，選取 [Visual C# 專案]  。</span><span class="sxs-lookup"><span data-stu-id="0c02d-134">In the **Project Types** dialog box, select **Visual C# Projects**.</span></span> <span data-ttu-id="0c02d-135">在 [範本]  窗格中，選取 [Windows 應用程式]  。</span><span class="sxs-lookup"><span data-stu-id="0c02d-135">In the **Templates** pane, select **Windows Application**.</span></span>  
  
4.  <span data-ttu-id="0c02d-136">(選擇性) 在 [名稱]  中，鍵入新應用程式的名稱。</span><span class="sxs-lookup"><span data-stu-id="0c02d-136">(Optional) In **Name**, type the name of the new application.</span></span>  
  
5.  <span data-ttu-id="0c02d-137">按一下 [確定]  ，載入 Visual C# Windows 範本。</span><span class="sxs-lookup"><span data-stu-id="0c02d-137">Click **OK** to load the Visual C# Windows template.</span></span>  
  
6.  <span data-ttu-id="0c02d-138">在 [專案]  功能表上，選取 [新增參考]  項目。</span><span class="sxs-lookup"><span data-stu-id="0c02d-138">On the **Project** menu, select **Add Reference** item.</span></span> <span data-ttu-id="0c02d-139">[新增參考]  對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="0c02d-139">The **Add Reference** dialog box appears.</span></span>  
  
7.  <span data-ttu-id="0c02d-140">從 [.NET]  索引標籤的清單中選取下列組件，然後按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="0c02d-140">Select the following assemblies from the list on the **.NET** tab, and then click **OK**.</span></span>  
  
    -   <span data-ttu-id="0c02d-141">Microsoft.SqlServer.Replication .NET 程式設計介面</span><span class="sxs-lookup"><span data-stu-id="0c02d-141">Microsoft.SqlServer.Replication .NET Programming Interface</span></span>  
  
    -   <span data-ttu-id="0c02d-142">Microsoft.SqlServer.ConnectionInfo</span><span class="sxs-lookup"><span data-stu-id="0c02d-142">Microsoft.SqlServer.ConnectionInfo</span></span>  
  
    -   <span data-ttu-id="0c02d-143">複寫代理程式程式庫</span><span class="sxs-lookup"><span data-stu-id="0c02d-143">Replication Agent Library</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="0c02d-144">使用 CTRL 鍵以選取一個以上的檔案。</span><span class="sxs-lookup"><span data-stu-id="0c02d-144">Use the CTRL key to select more than one file.</span></span>  
  
8.  <span data-ttu-id="0c02d-145">(選擇性) 重複步驟 6。</span><span class="sxs-lookup"><span data-stu-id="0c02d-145">(Optional) Repeat step 6.</span></span> <span data-ttu-id="0c02d-146">按一下 [瀏覽]  索引標籤，導覽至 [!INCLUDE[ssInstallPath](../../../includes/ssinstallpath-md.md)]COM，選取 Microsoft.SqlServer.Replication.BusinessLogicSupport.dll，然後按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="0c02d-146">Click the **Browse** tab, navigate to [!INCLUDE[ssInstallPath](../../../includes/ssinstallpath-md.md)]COM, select Microsoft.SqlServer.Replication.BusinessLogicSupport.dll, and then click **OK**.</span></span>  
  
9. <span data-ttu-id="0c02d-147">在 [檢視]  功能表中，按一下 [程式碼]  。</span><span class="sxs-lookup"><span data-stu-id="0c02d-147">On the **View** menu, click **Code**.</span></span>  
  
10. <span data-ttu-id="0c02d-148">在程式碼中的命名空間陳述式前面，輸入下列 `using` 陳述式來限定 RMO 命名空間中的類型：</span><span class="sxs-lookup"><span data-stu-id="0c02d-148">In the code, before the namespace statement, type the following `using` statements to qualify the types in the RMO namespaces:</span></span>  
  
    ```  
    // These namespaces are required.  
    using Microsoft.SqlServer.Replication;  
    using Microsoft.SqlServer.Management.Common;  
    // This namespace is only used when creating custom business  
    // logic for merge replication.  
    using Microsoft.SqlServer.Replication.BusinessLogicSupport;   
    ```  
  
#### <a name="to-create-a-new-microsoft-visual-basic-net-project"></a><span data-ttu-id="0c02d-149">建立新的 Microsoft Visual Basic .NET 專案</span><span class="sxs-lookup"><span data-stu-id="0c02d-149">To create a new Microsoft Visual Basic .NET project</span></span>  
  
1.  <span data-ttu-id="0c02d-150">啟動 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="0c02d-150">Start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="0c02d-151">在 [檔案]  功能表上，選取 [新增專案]  。</span><span class="sxs-lookup"><span data-stu-id="0c02d-151">On the **File** menu, select **New Project**.</span></span> <span data-ttu-id="0c02d-152">[新增專案]  對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="0c02d-152">The **New Project** dialog box appears.</span></span>  
  
3.  <span data-ttu-id="0c02d-153">在 [專案類型] 窗格中，選取 [Visual Basic]  。</span><span class="sxs-lookup"><span data-stu-id="0c02d-153">In the Project Types pane, select **Visual Basic**.</span></span> <span data-ttu-id="0c02d-154">在 [範本] 窗格中，選取 [Windows 應用程式]  。</span><span class="sxs-lookup"><span data-stu-id="0c02d-154">In the Templates pane, select **Windows Application**.</span></span>  
  
4.  <span data-ttu-id="0c02d-155">(選擇性) 在 [名稱]  方塊中，鍵入新應用程式的名稱。</span><span class="sxs-lookup"><span data-stu-id="0c02d-155">(Optional) In the **Name** box, type the name of the new application.</span></span>  
  
5.  <span data-ttu-id="0c02d-156">按一下 [確定]  ，載入 Visual Basic Windows 範本。</span><span class="sxs-lookup"><span data-stu-id="0c02d-156">Click **OK** to load the Visual Basic Windows template.</span></span>  
  
6.  <span data-ttu-id="0c02d-157">在 [專案]  功能表上，選取 [新增參考]  。</span><span class="sxs-lookup"><span data-stu-id="0c02d-157">On the **Project** menu, select **Add Reference**.</span></span> <span data-ttu-id="0c02d-158">[新增參考]  對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="0c02d-158">The **Add Reference** dialog box appears.</span></span>  
  
7.  <span data-ttu-id="0c02d-159">從 [.NET]  索引標籤的清單中選取下列組件，然後按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="0c02d-159">Select the following assemblies from the list on the **.NET** tab, and then click **OK**.</span></span>  
  
    -   <span data-ttu-id="0c02d-160">Microsoft.SqlServer.Replication .NET 程式設計介面</span><span class="sxs-lookup"><span data-stu-id="0c02d-160">Microsoft.SqlServer.Replication .NET Programming Interface</span></span>  
  
    -   <span data-ttu-id="0c02d-161">Microsoft.SqlServer.ConnectionInfo</span><span class="sxs-lookup"><span data-stu-id="0c02d-161">Microsoft.SqlServer.ConnectionInfo</span></span>  
  
    -   <span data-ttu-id="0c02d-162">複寫代理程式程式庫</span><span class="sxs-lookup"><span data-stu-id="0c02d-162">Replication Agent Library</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="0c02d-163">使用 CTRL 鍵以選取一個以上的檔案。</span><span class="sxs-lookup"><span data-stu-id="0c02d-163">Use the CTRL key to select more than one file.</span></span>  
  
8.  <span data-ttu-id="0c02d-164">(選擇性) 重複步驟 6。</span><span class="sxs-lookup"><span data-stu-id="0c02d-164">(Optional) Repeat step 6.</span></span> <span data-ttu-id="0c02d-165">按一下 [瀏覽]  索引標籤，導覽至 [!INCLUDE[ssInstallPath](../../../includes/ssinstallpath-md.md)]COM，選取 Microsoft.SqlServer.Replication.BusinessLogicSupport.dll，然後按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="0c02d-165">Click the **Browse** tab, navigate to [!INCLUDE[ssInstallPath](../../../includes/ssinstallpath-md.md)]COM, select Microsoft.SqlServer.Replication.BusinessLogicSupport.dll, and then click **OK**.</span></span>  
  
9. <span data-ttu-id="0c02d-166">在 [檢視]  功能表中，按一下 [程式碼]  。</span><span class="sxs-lookup"><span data-stu-id="0c02d-166">On the **View** menu, click **Code**.</span></span>  
  
10. <span data-ttu-id="0c02d-167">在程式碼的任何宣告前面，輸入下列 `Imports` 陳述式，以限定 RMO 命名空間中的類型。</span><span class="sxs-lookup"><span data-stu-id="0c02d-167">In the code, before any declarations, type the following `Imports` statements to qualify the types in the RMO namespaces.</span></span>  
  
    ```  
    ' These namespaces are required.  
    Imports Microsoft.SqlServer.Replication  
    Imports Microsoft.SqlServer.Management.Common  
    ' This namespace is only used when creating custom business  
    ' logic for merge replication.  
    Imports Microsoft.SqlServer.Replication.BusinessLogicSupport   
    ```  
  
## <a name="connecting-to-a-replication-server"></a><span data-ttu-id="0c02d-168">連接至複寫伺服器</span><span class="sxs-lookup"><span data-stu-id="0c02d-168">Connecting to a Replication Server</span></span>  
 <span data-ttu-id="0c02d-169">RMO 程式設計物件需要使用 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 類別的執行個體，來建立 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體的連接。</span><span class="sxs-lookup"><span data-stu-id="0c02d-169">RMO programming objects require that a connection to an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] is made by using an instance of the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span> <span data-ttu-id="0c02d-170">這個伺服器連接會獨立於任何 RMO 程式設計物件之外建立。</span><span class="sxs-lookup"><span data-stu-id="0c02d-170">This connection to the server is made independently of any RMO programming objects.</span></span> <span data-ttu-id="0c02d-171">接著會在執行個體建立期間將它傳遞到 RMO 物件，或是將它指派到物件的 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="0c02d-171">It is then passed to the RMO object either during instance creation or by assignment to the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property of the object.</span></span> <span data-ttu-id="0c02d-172">以此方式，就可以個別建立和管理 RMO 程式設計物件與連接物件執行個體，而且多個 RMO 程式設計物件可以重複使用單一連接物件。</span><span class="sxs-lookup"><span data-stu-id="0c02d-172">In this manner, an RMO programming object and the connection object instances can be created and managed separately, and a single connection object can be reused with multiple RMO programming objects.</span></span> <span data-ttu-id="0c02d-173">下列規則適用於應用程式伺服器的連接：</span><span class="sxs-lookup"><span data-stu-id="0c02d-173">The following rules apply for connections to a replication server:</span></span>  
  
-   <span data-ttu-id="0c02d-174">連接的所有屬性是針對指定的 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 物件所定義。</span><span class="sxs-lookup"><span data-stu-id="0c02d-174">All properties for the connection are defined for a given <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object.</span></span>  
  
-   <span data-ttu-id="0c02d-175">每個 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體的連接都必須有它自己的 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 物件。</span><span class="sxs-lookup"><span data-stu-id="0c02d-175">A connection to each instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] must have its own <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object.</span></span>  
  
-   <span data-ttu-id="0c02d-176">會將 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 物件指派到要在伺服器上建立或存取的 RMO 程式設計物件之 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="0c02d-176">The <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object is assigned to the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property of the RMO programming object being created or accessed on the server.</span></span>  
  
-   <span data-ttu-id="0c02d-177"><xref:Microsoft.SqlServer.Management.Common.ConnectionManager.Connect%2A> 方法會開啟伺服器的連接。</span><span class="sxs-lookup"><span data-stu-id="0c02d-177">The <xref:Microsoft.SqlServer.Management.Common.ConnectionManager.Connect%2A> method opens the connection to the server.</span></span> <span data-ttu-id="0c02d-178">必須先呼叫這個方法，才能呼叫在使用此連接的任何 RMO 程式設計物件上存取伺服器之任何方法。</span><span class="sxs-lookup"><span data-stu-id="0c02d-178">This method must be called before calling any methods that access the server on any RMO programming objects using the connection.</span></span>  
  
-   <span data-ttu-id="0c02d-179">因為 RMO 與 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 管理物件 (SMO) 都使用 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 類別連接至 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]，所以 RMO 與 SMO 物件都可以使用相同的連接。</span><span class="sxs-lookup"><span data-stu-id="0c02d-179">Because RMO and [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Management Objects (SMO) both use the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class for connections to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], the same connection can be used by both RMO and SMO objects.</span></span> <span data-ttu-id="0c02d-180">如需詳細資訊，請參閱[連線到 SQL Server 的執行個體](../../server-management-objects-smo/create-program/connecting-to-an-instance-of-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="0c02d-180">For more information, see [Connecting to an Instance of SQL Server](../../server-management-objects-smo/create-program/connecting-to-an-instance-of-sql-server.md).</span></span>  
  
-   <span data-ttu-id="0c02d-181">在 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 物件中，會提供所有建立連接及成功登入伺服器的驗證資訊。</span><span class="sxs-lookup"><span data-stu-id="0c02d-181">All authentication information to make the connection and successfully log on to the server is supplied in the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object.</span></span>  
  
-   <span data-ttu-id="0c02d-182">Windows 驗證是預設值。</span><span class="sxs-lookup"><span data-stu-id="0c02d-182">Windows Authentication is the default.</span></span> <span data-ttu-id="0c02d-183">若要使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 驗證，必須將 <xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.LoginSecure%2A> 設定為 `false` 與 <xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.Login%2A>，而且 <xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.Password%2A> 必須設定為有效的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 登入與密碼。</span><span class="sxs-lookup"><span data-stu-id="0c02d-183">To use [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication, <xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.LoginSecure%2A> must be set to `false` and <xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.Login%2A> and <xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.Password%2A> must be set to a valid [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] logon and password.</span></span> <span data-ttu-id="0c02d-184">安全性認證必須以安全方式儲存和處理，而且每當有需要時必須在執行階段提供。</span><span class="sxs-lookup"><span data-stu-id="0c02d-184">Security credentials must always be stored and handled securely, and supplied at run-time whenever possible.</span></span>  
  
-   <span data-ttu-id="0c02d-185">對於多執行緒應用程式，應該在每個執行緒中使用個別的 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 物件。</span><span class="sxs-lookup"><span data-stu-id="0c02d-185">For multithreaded applications, a separate <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object should be used in each thread.</span></span>  
  
 <span data-ttu-id="0c02d-186">在 <xref:Microsoft.SqlServer.Management.Common.ConnectionManager.Disconnect%2A> 物件上呼叫 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 方法，以關閉 RMO 物件所使用的使用中伺服器連接。</span><span class="sxs-lookup"><span data-stu-id="0c02d-186">Call the <xref:Microsoft.SqlServer.Management.Common.ConnectionManager.Disconnect%2A> method on the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object to close active server connections used by RMO objects.</span></span>  
  
## <a name="setting-rmo-properties"></a><span data-ttu-id="0c02d-187">設定 RMO 屬性</span><span class="sxs-lookup"><span data-stu-id="0c02d-187">Setting RMO Properties</span></span>  
 <span data-ttu-id="0c02d-188">RMO 程式設計物件的屬性代表在伺服器這些複寫物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="0c02d-188">The properties of RMO programming objects represent the properties of these replication objects at the server.</span></span> <span data-ttu-id="0c02d-189">在伺服器建立新複寫物件時，會使用 RMO 屬性來定義這些物件。</span><span class="sxs-lookup"><span data-stu-id="0c02d-189">When creating new replication objects at the server, RMO properties are used to define these objects.</span></span> <span data-ttu-id="0c02d-190">對於現有的物件，RMO 屬性代表現有物件的屬性，只能修改可寫入或是可設定的屬性。</span><span class="sxs-lookup"><span data-stu-id="0c02d-190">For existing objects, the RMO properties represent the existing object's properties, which can be modified only for properties that are writable or settable.</span></span> <span data-ttu-id="0c02d-191">屬性可以在新物件或是現有物件上設定。</span><span class="sxs-lookup"><span data-stu-id="0c02d-191">Properties can be set on new objects or existing objects.</span></span>  
  
### <a name="setting-properties-for-new-replication-objects"></a><span data-ttu-id="0c02d-192">設定新複寫物件的屬性</span><span class="sxs-lookup"><span data-stu-id="0c02d-192">Setting Properties for New Replication Objects</span></span>  
 <span data-ttu-id="0c02d-193">在伺服器建立新複寫物件時，您必須先指定所有必要的屬性，才能呼叫物件的 `Create` 方法。</span><span class="sxs-lookup"><span data-stu-id="0c02d-193">When creating a new replication object at the server, you must specify all required properties before calling the `Create` method of the object.</span></span> <span data-ttu-id="0c02d-194">如需為新複寫物件設定屬性的詳細資訊，請參閱[設定發行和散發](../configure-publishing-and-distribution.md)。</span><span class="sxs-lookup"><span data-stu-id="0c02d-194">For more information about setting properties for a new replication object, see [Configure Publishing and Distribution](../configure-publishing-and-distribution.md).</span></span>  
  
### <a name="setting-properties-for-existing-replication-objects"></a><span data-ttu-id="0c02d-195">設定現有複寫物件的屬性</span><span class="sxs-lookup"><span data-stu-id="0c02d-195">Setting Properties for Existing Replication Objects</span></span>  
 <span data-ttu-id="0c02d-196">對於存在於伺服器上的複寫物件，視物件而定，RMO 可能支援變更某些或是所有其屬性的能力。</span><span class="sxs-lookup"><span data-stu-id="0c02d-196">For replication objects that exist at the server, depending on the object, RMO might support the ability to change some or all of its properties.</span></span> <span data-ttu-id="0c02d-197">只可以變更可寫入的或可設定的屬性。</span><span class="sxs-lookup"><span data-stu-id="0c02d-197">Only writable or settable properties can be changed.</span></span> <span data-ttu-id="0c02d-198">在變更屬性之前，必須先呼叫 `Load` 或 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> 方法，從伺服器取得目前的屬性。</span><span class="sxs-lookup"><span data-stu-id="0c02d-198">Before properties can be changed, either the `Load` or the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method must be called to get the current properties from the server.</span></span> <span data-ttu-id="0c02d-199">呼叫這些方法表示要修改現有的物件。</span><span class="sxs-lookup"><span data-stu-id="0c02d-199">Calling these methods indicates that an existing object is being modified.</span></span>  
  
 <span data-ttu-id="0c02d-200">依預設，當變更物件屬性時，RMO 會根據要使用的 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 之執行模式，將這些變更認可到伺服器。</span><span class="sxs-lookup"><span data-stu-id="0c02d-200">By default, when changing object properties, RMO commits these changes to the server based on the execution mode of the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> being used.</span></span> <span data-ttu-id="0c02d-201"><xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> 方法可用以在嘗試擷取或是變更其屬性之前，先驗證存在於伺服器的物件。</span><span class="sxs-lookup"><span data-stu-id="0c02d-201">The <xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> method can be used to verify that an object exists at the server before attempting to retrieve or change its properties.</span></span> <span data-ttu-id="0c02d-202">如需變更複寫物件屬性的詳細資訊，請參閱[檢視及修改散發者和發行者屬性](../view-and-modify-distributor-and-publisher-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="0c02d-202">For more information about changing the properties of a replication object, see [View and Modify Distributor and Publisher Properties](../view-and-modify-distributor-and-publisher-properties.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0c02d-203">當有多個 RMO 用戶端或是多個 RMO 程式設計物件的執行個體，在伺服器上存取相同複寫物件時，可以呼叫 RMO 物件的 `Refresh` 方法，以便根據伺服器上物件目前的狀態來更新屬性。</span><span class="sxs-lookup"><span data-stu-id="0c02d-203">When multiple RMO clients or multiple instances of an RMO programming object are accessing the same replication object at the server, the `Refresh` method of the RMO object can be called to update the properties based on the current state of the object at the server.</span></span>  
  
### <a name="caching-property-changes"></a><span data-ttu-id="0c02d-204">快取屬性變更</span><span class="sxs-lookup"><span data-stu-id="0c02d-204">Caching Property Changes</span></span>  
 <span data-ttu-id="0c02d-205">當將 <xref:Microsoft.SqlServer.Management.Common.SqlExecutionModes> 屬性設定為 <xref:Microsoft.SqlServer.Management.Common.SqlExecutionModes.CaptureSql> 時，會擷取 RMO 產生的所有 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 陳述式，這樣就可以使用其中一個執行方法，以單一批次手動執行它們。</span><span class="sxs-lookup"><span data-stu-id="0c02d-205">When the <xref:Microsoft.SqlServer.Management.Common.SqlExecutionModes> property is set to <xref:Microsoft.SqlServer.Management.Common.SqlExecutionModes.CaptureSql> all [!INCLUDE[tsql](../../../includes/tsql-md.md)] statements generated by RMO are captured so that they can be executed manually in a single batch by using one of the execution methods.</span></span> <span data-ttu-id="0c02d-206">RMO 可讓您使用物件的 <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> 方法，以擷取屬性變更並在單一批次中一起認可它們。</span><span class="sxs-lookup"><span data-stu-id="0c02d-206">RMO lets you cache property changes and commit them together in a single batch by using the <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> method of the object.</span></span> <span data-ttu-id="0c02d-207">若要快取屬性變更，必須將物件的 <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> 屬性設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="0c02d-207">To cache property changes, the <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> property of the object must be set to `true`.</span></span> <span data-ttu-id="0c02d-208">在快取 RMO 中的屬性變更時，<xref:Microsoft.SqlServer.Management.Common.ServerConnection> 物件仍然會控制何時將變更傳送到伺服器。</span><span class="sxs-lookup"><span data-stu-id="0c02d-208">When caching property changes in RMO, the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object still controls when changes are sent to the server.</span></span> <span data-ttu-id="0c02d-209">如需快取複寫物件之屬性變更的詳細資訊，請參閱[檢視及修改散發者和發行者屬性](../view-and-modify-distributor-and-publisher-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="0c02d-209">For more information about caching property changes for a replication object, see [View and Modify Distributor and Publisher Properties](../view-and-modify-distributor-and-publisher-properties.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="0c02d-210">雖然 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 類別支援在設定屬性時宣告明確的交易，不過，這樣的交易可能會平擾內部複寫交易、可能會產生非預期的結果，而且不應該與 RMO 搭配使用。</span><span class="sxs-lookup"><span data-stu-id="0c02d-210">Although the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class supports declaring explicit transactions when setting properties, such transactions may interfere with internal replication transactions, can produce unanticipated results, and should not be used with RMO.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0c02d-211">範例</span><span class="sxs-lookup"><span data-stu-id="0c02d-211">Example</span></span>  
 <span data-ttu-id="0c02d-212">這個範例會示範屬性變更的快取。</span><span class="sxs-lookup"><span data-stu-id="0c02d-212">This example demonstrates the caching of property changes.</span></span> <span data-ttu-id="0c02d-213">會快取對於交易式發行集屬性所做的變更，直到將它們明確地傳送到伺服器為止。</span><span class="sxs-lookup"><span data-stu-id="0c02d-213">Changes made to the attributes of a transactional publication are cached until they are explicitly sent to the server.</span></span>  
  
 [!code-csharp[HowTo#rmo_ChangeTranPub_cached](../../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_ChangeTranPub_cached)]  
  
## <a name="see-also"></a><span data-ttu-id="0c02d-214">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0c02d-214">See Also</span></span>  
 <span data-ttu-id="0c02d-215">[Replication System Stored Procedures Concepts](replication-system-stored-procedures-concepts.md) </span><span class="sxs-lookup"><span data-stu-id="0c02d-215">[Replication System Stored Procedures Concepts](replication-system-stored-procedures-concepts.md) </span></span>  
 [<span data-ttu-id="0c02d-216">複寫程式設計概念</span><span class="sxs-lookup"><span data-stu-id="0c02d-216">Replication Programming Concepts</span></span>](replication-programming-concepts.md)  
  
  
