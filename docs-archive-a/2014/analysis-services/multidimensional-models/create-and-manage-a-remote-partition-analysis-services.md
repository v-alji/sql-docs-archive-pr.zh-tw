---
title: 建立和管理遠端資料分割 (Analysis Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- partitions [Analysis Services], remote
- remote partitions [Analysis Services]
ms.assetid: 4322b5cb-af07-4e79-8ecb-59e1121a9eb8
author: minewiskan
ms.author: owend
ms.openlocfilehash: 0bd44775a579cc8f770f088594653bb65000407f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584762"
---
# <a name="create-and-manage-a-remote-partition-analysis-services"></a><span data-ttu-id="25335-102">建立及管理遠端分割區 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="25335-102">Create and Manage a Remote Partition (Analysis Services)</span></span>
  <span data-ttu-id="25335-103">分割量值群組時，您可以在遠端 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體上設定次要資料庫作為分割區儲存。</span><span class="sxs-lookup"><span data-stu-id="25335-103">When partitioning a measure group, you can configure a secondary database on a remote [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance as partition storage.</span></span>  
  
 <span data-ttu-id="25335-104">Cube (稱為 master 資料庫) 的遠端分割區，會儲存在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 遠端執行個體上的專用 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 資料庫 (稱為次要資料庫) 中。</span><span class="sxs-lookup"><span data-stu-id="25335-104">Remote partitions for a cube (called the master database) are stored in a dedicated [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database on the remote instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] (called the secondary database).</span></span>  
  
 <span data-ttu-id="25335-105">專用次要資料庫會針對唯一的 master 資料庫儲存遠端資料分割，但是 master 資料庫可以使用多個次要資料庫，只要所有次要資料庫都在相同的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]遠端執行個體上即可。</span><span class="sxs-lookup"><span data-stu-id="25335-105">A dedicated secondary database can store remote partitions for one and only one master database, but the master database can use multiple secondary databases, as long as all the secondary databases are on the same remote instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="25335-106">資料庫中專屬於遠端分割區的維度會建立為連結維度。</span><span class="sxs-lookup"><span data-stu-id="25335-106">Dimensions in a database dedicated to remote partitions are created as linked dimensions.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="25335-107">先決條件</span><span class="sxs-lookup"><span data-stu-id="25335-107">Prerequisites</span></span>  
 <span data-ttu-id="25335-108">建立遠端分割區之前，必須先符合下列條件：</span><span class="sxs-lookup"><span data-stu-id="25335-108">Before you create a remote partition, the following conditions must be met:</span></span>  
  
-   <span data-ttu-id="25335-109">您必須具有次要 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體和專用資料庫以儲存資料分割。</span><span class="sxs-lookup"><span data-stu-id="25335-109">You must have a second [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance and dedicated database to store the partitions.</span></span> <span data-ttu-id="25335-110">次要資料庫的用途只有一個，那就是為 master 資料庫提供遠端分割區儲存。</span><span class="sxs-lookup"><span data-stu-id="25335-110">The secondary database is single-purpose; it provides storage of remote partitions for a master database.</span></span>  
  
-   <span data-ttu-id="25335-111">這兩個伺服器執行個體的版本必須相同。</span><span class="sxs-lookup"><span data-stu-id="25335-111">Both server instances must be the same version.</span></span> <span data-ttu-id="25335-112">這兩個資料庫應該是相同的功能層級。</span><span class="sxs-lookup"><span data-stu-id="25335-112">Both databases should be the same functional level.</span></span>  
  
-   <span data-ttu-id="25335-113">這兩個執行個體必須設定 TCP 連接。</span><span class="sxs-lookup"><span data-stu-id="25335-113">Both instances must be configured for TCP connections.</span></span> [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="25335-114">不支援使用 HTTP 通訊協定建立遠端資料分割。</span><span class="sxs-lookup"><span data-stu-id="25335-114">does not support creation of remote partitions by using the HTTP protocol.</span></span>  
  
-   <span data-ttu-id="25335-115">這兩部電腦上的防火牆設定必須設為接受外部連接。</span><span class="sxs-lookup"><span data-stu-id="25335-115">Firewall settings on both computers must be set to accept outside connections.</span></span> <span data-ttu-id="25335-116">如需設定防火牆的資訊，請參閱 [設定 Windows 防火牆以允許 Analysis Services 存取](../instances/configure-the-windows-firewall-to-allow-analysis-services-access.md)。</span><span class="sxs-lookup"><span data-stu-id="25335-116">For information about setting the firewall, see [Configure the Windows Firewall to Allow Analysis Services Access](../instances/configure-the-windows-firewall-to-allow-analysis-services-access.md).</span></span>  
  
-   <span data-ttu-id="25335-117">執行 master 資料庫之執行個體的服務帳戶必須具有 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]遠端執行個體的管理存取權限。</span><span class="sxs-lookup"><span data-stu-id="25335-117">The service account for the instance running the master database must have administrative access to the remote instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="25335-118">如果服務帳戶變更，您必須更新伺服器和資料庫上的權限。</span><span class="sxs-lookup"><span data-stu-id="25335-118">If the service account changes, you must update permissions on both the server and database.</span></span>  
  
-   <span data-ttu-id="25335-119">您必須是兩部電腦的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 管理員。</span><span class="sxs-lookup"><span data-stu-id="25335-119">You must be an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] administrator on both computers.</span></span>  
  
-   <span data-ttu-id="25335-120">您必須確保災害復原計畫包含遠端分割區的備份與還原。</span><span class="sxs-lookup"><span data-stu-id="25335-120">You must ensure your disaster recovery plan accommodates backup and restore of the remote partitions.</span></span> <span data-ttu-id="25335-121">使用遠端分割區會讓備份與還原作業變得很複雜。</span><span class="sxs-lookup"><span data-stu-id="25335-121">Using remote partitions can complicate backup and restore operations.</span></span> <span data-ttu-id="25335-122">請務必針對您的計畫進行徹底的測試，確保能夠還原必要資料。</span><span class="sxs-lookup"><span data-stu-id="25335-122">Be sure to test your plan thoroughly to be sure you can restore the necessary data.</span></span>  
  
## <a name="configure-remote-partitions"></a><span data-ttu-id="25335-123">設定遠端分割區</span><span class="sxs-lookup"><span data-stu-id="25335-123">Configure remote partitions</span></span>  
 <span data-ttu-id="25335-124">執行實例的兩部不同電腦 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 都必須建立遠端分割區安排，將一部電腦指定為主伺服器，另一部電腦做為次級伺服器。</span><span class="sxs-lookup"><span data-stu-id="25335-124">Two separate computers that are running an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] are each required to create a remote partition arrangement that designates one computer as the master server and the other computer as the subordinate server.</span></span>  
  
 <span data-ttu-id="25335-125">下列程序假設您有兩個伺服器執行個體，其中 Cube 資料庫部署在主要伺服器上。</span><span class="sxs-lookup"><span data-stu-id="25335-125">The following procedure assumes that you have two server instances, with a cube database deployed on the master server.</span></span> <span data-ttu-id="25335-126">基於此程序的目的，Cube 資料庫稱為 db-master。</span><span class="sxs-lookup"><span data-stu-id="25335-126">For the purposes of this procedure, the cube database is referred to as db-master.</span></span> <span data-ttu-id="25335-127">包含遠端分割區的儲存資料庫稱為 db-storage。</span><span class="sxs-lookup"><span data-stu-id="25335-127">The storage database containing remote partitions is referred to as db-storage.</span></span>  
  
 <span data-ttu-id="25335-128">您將使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 和 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 完成此程序。</span><span class="sxs-lookup"><span data-stu-id="25335-128">You will use both [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] and [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] to complete this procedure.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="25335-129">遠端分割區只能與其他遠端分割區合併。</span><span class="sxs-lookup"><span data-stu-id="25335-129">Remote partitions can be merged only with other remote partitions.</span></span> <span data-ttu-id="25335-130">如果使用本機和遠端分割區的組合，替代方式是建立包含合併資料的新分割區，並刪除您不再使用的分割區。</span><span class="sxs-lookup"><span data-stu-id="25335-130">If you are using a combination of local and remote partitions, an alternative approach is to create new partitions that include the combined data, deleting the partitions you no longer use.</span></span>  
  
#### <a name="specify-valid-server-names-for-cube-deployment-in-ssdt"></a><span data-ttu-id="25335-131">為 Cube 部署指定有效的伺服器名稱 (在 SSDT 中)</span><span class="sxs-lookup"><span data-stu-id="25335-131">Specify valid server names for cube deployment (in SSDT)</span></span>  
  
1.  <span data-ttu-id="25335-132">在主要伺服器上：在方案總管中，以滑鼠右鍵按一下方案名稱，然後選取 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="25335-132">On the master server: In Solution Explorer, right-click the solution name and select **Properties**.</span></span> <span data-ttu-id="25335-133">在 [屬性]\*\*\*\* 對話方塊中，依序按一下 [組態屬性]\*\*\*\*、[部署]\*\*\*\* 及 [伺服器]\*\*\*\*，然後設定主要伺服器的名稱。</span><span class="sxs-lookup"><span data-stu-id="25335-133">In the **Properties** dialog box, click **Configuration Properties**, then click **Deployment**, and then click **Server** and set the master server's name.</span></span>  
  
2.  <span data-ttu-id="25335-134">在從屬伺服器上：在方案總管中，以滑鼠右鍵按一下方案名稱，然後選取 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="25335-134">On the subordinate server: In Solution Explorer, right-click the solution name and select **Properties**.</span></span> <span data-ttu-id="25335-135">在 [屬性]\*\*\*\* 對話方塊中，依序按一下 [組態屬性]\*\*\*\*、[部署]\*\*\*\* 及 [伺服器]\*\*\*\*，然後設定從屬伺服器的名稱。</span><span class="sxs-lookup"><span data-stu-id="25335-135">In the **Properties** dialog box, click **Configuration Properties**, then click **Deployment**, and then click **Server** and set the subordinate server's name.</span></span>  
  
#### <a name="create-and-deploy-a-secondary-database-in-ssdt"></a><span data-ttu-id="25335-136">建立及部署次要資料庫 (在 SSDT 中)</span><span class="sxs-lookup"><span data-stu-id="25335-136">Create and deploy a secondary database (in SSDT)</span></span>  
  
1.  <span data-ttu-id="25335-137">在從屬伺服器上：為儲存資料庫建立新的 Analysis Services 專案。</span><span class="sxs-lookup"><span data-stu-id="25335-137">On the subordinate server: Create a new Analysis Services project for the storage database.</span></span>  
  
2.  <span data-ttu-id="25335-138">在從屬伺服器上：在 [方案總管] 中，建立指向 Cube 資料庫 (db-master) 的新資料來源。</span><span class="sxs-lookup"><span data-stu-id="25335-138">On the subordinate server: In Solution Explorer, create a new data source pointing to the cube database, db-master.</span></span> <span data-ttu-id="25335-139">使用提供者 **Native OLE DB\Microsoft OLE DB Provider for Analysis Services 11.0**。</span><span class="sxs-lookup"><span data-stu-id="25335-139">Use the provider **Native OLE DB\Microsoft OLE DB Provider for Analysis Services 11.0**.</span></span>  
  
3.  <span data-ttu-id="25335-140">在從屬伺服器上：部署方案。</span><span class="sxs-lookup"><span data-stu-id="25335-140">On the subordinate server: Deploy the solution.</span></span>  
  
#### <a name="enable-features-in-ssms"></a><span data-ttu-id="25335-141">啟用功能 (在 SSMS 中)</span><span class="sxs-lookup"><span data-stu-id="25335-141">Enable features (in SSMS)</span></span>  
  
1.  <span data-ttu-id="25335-142">在從屬伺服器上：在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中，以滑鼠右鍵按一下物件總管中已連接的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體，然後選取 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="25335-142">On the subordinate server: In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], right-click your connected [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance in Object Explorer and select **Properties**.</span></span> <span data-ttu-id="25335-143">將 **Feature\LinkToOtherInstanceEnabled** 和 **Feature\LinkFromOtherInstanceEnabled** 設為 **True**。</span><span class="sxs-lookup"><span data-stu-id="25335-143">Set both **Feature\LinkToOtherInstanceEnabled** and **Feature\LinkFromOtherInstanceEnabled** to **True**.</span></span>  
  
2.  <span data-ttu-id="25335-144">在從屬伺服器上：以滑鼠右鍵按一下物件總管中的伺服器名稱，然後選取 [重新啟動]\*\*\*\* 以重新啟動伺服器。</span><span class="sxs-lookup"><span data-stu-id="25335-144">On the subordinate server: Restart the server by right-clicking the server name in Object Explorer and selecting **Restart**.</span></span>  
  
3.  <span data-ttu-id="25335-145">在主要伺服器上：在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中，以滑鼠右鍵按一下物件總管中已連接的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體，然後選取 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="25335-145">On the master server: In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], right-click your connected [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance in Object Explorer and select **Properties**.</span></span> <span data-ttu-id="25335-146">將 **Feature\LinkToOtherInstanceEnabled** 和 **Feature\LinkFromOtherInstanceEnabled** 設為 **True**。</span><span class="sxs-lookup"><span data-stu-id="25335-146">Set both **Feature\LinkToOtherInstanceEnabled** and **Feature\LinkFromOtherInstanceEnabled** to **True**.</span></span>  
  
4.  <span data-ttu-id="25335-147">在主要伺服器上：若要重新啟動伺服器，請以滑鼠右鍵按一下物件總管中的伺服器名稱，然後選取 [重新啟動]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="25335-147">On the master server: To restart the server, right-click the server name in Object Explorer and select **Restart**.</span></span>  
  
#### <a name="set-the-masterdatasourceid-database-property-on-the-remote-server-in-ssms"></a><span data-ttu-id="25335-148">設定遠端伺服器上的 MasterDataSourceID 資料庫屬性 (在 SSMS 中)</span><span class="sxs-lookup"><span data-stu-id="25335-148">Set the MasterDataSourceID database property on the remote server (in SSMS)</span></span>  
  
1.  <span data-ttu-id="25335-149">在從屬伺服器上：以滑鼠右鍵按一下儲存體資料庫 [資料庫-儲存體]，指向 [**編寫資料庫的腳本為**  |  **ALTER to**  |  **New 查詢編輯器] 視窗**。</span><span class="sxs-lookup"><span data-stu-id="25335-149">On the subordinate server: Right-click the storage database, db-storage, point to **Script Database as** | **ALTER To** | **New Query Editor Window**.</span></span>  
  
2.  <span data-ttu-id="25335-150">將 **MasterDataSourceID** 加入 XMLA 中，然後指定 Cube 資料庫 db-master 的識別碼作為其值。</span><span class="sxs-lookup"><span data-stu-id="25335-150">Add **MasterDataSourceID** to the XMLA, and then specify the cube database, db-master, ID as the value.</span></span> <span data-ttu-id="25335-151">XMLA 看起來應該類似如下。</span><span class="sxs-lookup"><span data-stu-id="25335-151">The XMLA should look similar to the following.</span></span>  
  
    ```  
    <Alter ObjectExpansion="ExpandFull" xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">  
    <Object>  
       <DatabaseID>DB-Storage</DatabaseID>  
    </Object>  
    <ObjectDefinition>  
       <Database xmlns:xsd="http://www.w3.org/2001/XMLSchema" 400"   
          <ID>DB-Storage</ID>  
          <Name>DB-StorageB</Name>  
          <ddl200:CompatibilityLevel>1100</ddl200:CompatibilityLevel>  
          <Language>1033</Language>  
          <Collation>Latin1_General_CI_AS</Collation>  
          <DataSourceImpersonationInfo>  
    <ImpersonationMode>ImpersonateAccount</ImpersonationMode>  
             <Account>*********</Account>  
          </DataSourceImpersonationInfo>  
          <MasterDataSourceID>DB-Master</MasterDataSourceID>  
       </Database>  
    </ObjectDefinition>  
    </Alter>  
    ```  
  
3.  <span data-ttu-id="25335-152">按 F5 執行指令碼。</span><span class="sxs-lookup"><span data-stu-id="25335-152">Press F5 to execute the script.</span></span>  
  
#### <a name="set-up-the-remote-partition-in-ssdt"></a><span data-ttu-id="25335-153">設定遠端分割區 (在 SSDT 中)</span><span class="sxs-lookup"><span data-stu-id="25335-153">Set up the remote partition (in SSDT)</span></span>  
  
1.  <span data-ttu-id="25335-154">在主伺服器上：在 Cube 設計師中開啟 cube，然後**按一下 [** 資料分割] 索引標籤。展開量值群組。</span><span class="sxs-lookup"><span data-stu-id="25335-154">On the master server: Open the cube in Cube Designer and click **Partitions** tab. Expand the measure group.</span></span> <span data-ttu-id="25335-155">如果為多個資料分割設定量值群組，請按一下 [新增資料分割]\*\*\*\*；否則在 [來源] 資料行中按一下瀏覽 (.</span><span class="sxs-lookup"><span data-stu-id="25335-155">Click **New Partition** if the measure group is already configured for multiple partitions, or click the browse (.</span></span> <span data-ttu-id="25335-156">.</span><span class="sxs-lookup"><span data-stu-id="25335-156">.</span></span> <span data-ttu-id="25335-157">) 按鈕，以編輯現有的分割區。</span><span class="sxs-lookup"><span data-stu-id="25335-157">) button in the Source column to edit the existing partition.</span></span>  
  
2.  <span data-ttu-id="25335-158">在 [資料分割精靈] 的 [指定來源資訊]\*\*\*\* 中，選取原始資料來源檢視和事實資料表。</span><span class="sxs-lookup"><span data-stu-id="25335-158">In the Partition Wizard, in **Specify Source Information**, select the original Data Source View and fact table.</span></span>  
  
3.  <span data-ttu-id="25335-159">如果使用查詢繫結，請為建立的新分割區提供分割資料的 WHERE 子句。</span><span class="sxs-lookup"><span data-stu-id="25335-159">If using a query binding, provide a WHERE clause that segments the data for the new partition you are creating.</span></span>  
  
4.  <span data-ttu-id="25335-160">在 [處理與儲存位置]\*\*\*\* 的 [處理位置]\*\*\*\* 下，選擇 [遠端 Analysis Services 資料來源]\*\*\*\*，然後按一下 [新增]\*\*\*\*，以建立指向從屬資料庫 db-storage 的新資料來源。</span><span class="sxs-lookup"><span data-stu-id="25335-160">In **Processing and Storage Locations**, under **Processing Location**, choose **Remote Analysis Services data source** and click **New** to create a new data source that points to your subordinate database, db-storage.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="25335-161">如果發生錯誤，指出集合中不存在此資料來源，您必須開啟儲存資料庫 db-storage 的專案，然後建立指向 master 資料庫 db-master 的資料來源。</span><span class="sxs-lookup"><span data-stu-id="25335-161">If you get an error indicating the data source does not exist in the collection, you must open the project of the storage database, db-storage, and create a data source that points to the master database, db-master.</span></span>  
  
5.  <span data-ttu-id="25335-162">在主要伺服器上：以滑鼠右鍵按一下方案總管中的 Cube 名稱，然後選取 [處理]\*\*\*\* 並完整處理 Cube。</span><span class="sxs-lookup"><span data-stu-id="25335-162">On the master server: Right-click the cube name in Solution Explorer, select **Process** and fully process the cube.</span></span>  
  
## <a name="administering-remote-partitions"></a><span data-ttu-id="25335-163">管理遠端分割區</span><span class="sxs-lookup"><span data-stu-id="25335-163">Administering remote partitions</span></span>  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="25335-164">支援遠端資料分割的平行和循序處理。</span><span class="sxs-lookup"><span data-stu-id="25335-164">supports both parallel and sequential processing of remote partitions.</span></span> <span data-ttu-id="25335-165">定義分割區的 master 資料庫會協調參與處理 Cube 之分割區所有執行個體之間的交易。</span><span class="sxs-lookup"><span data-stu-id="25335-165">The master database, where the partitions were defined, coordinates the transactions among all the instances that participate in processing the partitions of a cube.</span></span> <span data-ttu-id="25335-166">然後將處理報表傳送至處理分割區的所有執行個體。</span><span class="sxs-lookup"><span data-stu-id="25335-166">Processing reports are then sent to all instances that processed a partition.</span></span>  
  
 <span data-ttu-id="25335-167">您可以在單一 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]執行個體上同時管理內含遠端分割區的 Cube 及其分割區。</span><span class="sxs-lookup"><span data-stu-id="25335-167">A cube that contains remote partitions can be administered together with its partitions on a single instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="25335-168">但是，您只能在定義遠端分割區及其父 Cube 的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體上，檢視及更新分割區的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="25335-168">However, the metadata for the remote partition can be viewed and updated only on the instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] where the partition and its parent cube were defined.</span></span> <span data-ttu-id="25335-169">您無法在遠端 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]執行個體上，檢視或更新遠端資料分割。</span><span class="sxs-lookup"><span data-stu-id="25335-169">The remote partition cannot be viewed or updated on the remote instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="25335-170">雖然結構描述資料列集不會顯示專用於儲存遠端分割區的資料庫，但是使用分析管理物件 (AMO) 的應用程式仍可使用 XML for Analysis Discover 命令探索專用資料庫。</span><span class="sxs-lookup"><span data-stu-id="25335-170">Although databases dedicated to storage of remote partitions are not exposed to schema rowsets, applications that use Analysis Management Objects (AMO) can still discover a dedicated database by using the XML for Analysis Discover command.</span></span> <span data-ttu-id="25335-171">任何使用 TCP 或 HTTP 用戶端直接傳送至專用資料庫的 CREATE 或 DELETE 命令會成功完成，但是伺服器會傳回警告，指出這些動作可能會損毀此密切管理的資料庫。</span><span class="sxs-lookup"><span data-stu-id="25335-171">Any CREATE or DELETE command that is sent directly to a dedicated database by using a TCP or HTTP client will succeed, but the server will return a warning indicating that the action may damage this closely managed database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25335-172">另請參閱</span><span class="sxs-lookup"><span data-stu-id="25335-172">See Also</span></span>  
 [<span data-ttu-id="25335-173">資料分割 &#40;Analysis Services - 多維度資料&#41;</span><span class="sxs-lookup"><span data-stu-id="25335-173">Partitions &#40;Analysis Services - Multidimensional Data&#41;</span></span>](../multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data.md)  
  
  
