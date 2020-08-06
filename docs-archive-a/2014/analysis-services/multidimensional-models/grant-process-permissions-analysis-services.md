---
title: 授與處理許可權 (Analysis Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- permissions [Analysis Services], process
- process permissions [Analysis Services]
ms.assetid: c1531c23-6b46-46a8-9ba3-b6d3f2016443
author: minewiskan
ms.author: owend
ms.openlocfilehash: 4e41e8710bc167ef53eb2aad2cbf678019b96e0c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703337"
---
# <a name="grant-process-permissions-analysis-services"></a><span data-ttu-id="51b33-102">授與處理權限 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="51b33-102">Grant process permissions (Analysis Services)</span></span>
  <span data-ttu-id="51b33-103">身為管理員，您可以建立專用於 Analysis Services 處理作業的角色，讓您能夠將該特殊工作委派給其他使用者，或委派給用於自動排程處理的應用程式。</span><span class="sxs-lookup"><span data-stu-id="51b33-103">As an administrator, you can create a role dedicated to Analysis Services processing operations, allowing you to delegate that particular task to other users, or to applications used for unattended scheduled processing.</span></span> <span data-ttu-id="51b33-104">處理權限可在資料庫、Cube、維度和採礦結構層級上授與。</span><span class="sxs-lookup"><span data-stu-id="51b33-104">Process permissions can be granted at the database, cube, dimension, and mining structure levels.</span></span> <span data-ttu-id="51b33-105">除非您正在使用一個非常大的 Cube 或表格式資料庫，否則建議在資料層級授與處理權限，內含所有物件，包含彼此間具有相依性的物件。</span><span class="sxs-lookup"><span data-stu-id="51b33-105">Unless you are working with a very large cube or tabular database, we recommend granting processing rights at the database level, inclusive of all objects, including those having dependencies on each other.</span></span>  
  
 <span data-ttu-id="51b33-106">權限是透過將物件與權限和 Windows 使用者或群組帳戶關聯的角色來授與。</span><span class="sxs-lookup"><span data-stu-id="51b33-106">Permissions are granted through roles that associate objects with permissions and Windows user or group accounts.</span></span> <span data-ttu-id="51b33-107">請記住，權限是加總的。</span><span class="sxs-lookup"><span data-stu-id="51b33-107">Remember that permissions are additive.</span></span> <span data-ttu-id="51b33-108">如果某個角色會授與處理 Cube 的權限，第二個角色則提供處理維度的相同使用者權限時，在兩個不同角色的權限結合之後，使用者即擁有處理 Cube 及處理該資料庫內之指定維度的權限。</span><span class="sxs-lookup"><span data-stu-id="51b33-108">If one role grants permission to process a cube, while a second role gives the same user permission to process a dimension, the permissions from the two different roles combine to give the user permission to both process the cube and process the specified dimension within that database.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="51b33-109">角色僅擁有 [處理] 權限的使用者將無法使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 或 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 連接到 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 及處理物件。</span><span class="sxs-lookup"><span data-stu-id="51b33-109">A user whose role only has Process permissions will be unable to use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] to connect to [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] and process objects.</span></span> <span data-ttu-id="51b33-110">這些工具需要有 `Read Definition` 權限來存取物件中繼資料。</span><span class="sxs-lookup"><span data-stu-id="51b33-110">These tools require the `Read Definition` permission to access object metadata.</span></span> <span data-ttu-id="51b33-111">如果無法使用這些工具，就必須使用 XMLA 指令碼來執行處理作業。</span><span class="sxs-lookup"><span data-stu-id="51b33-111">Without the ability to use either tool, XMLA script must be used to execute a processing operation.</span></span>  
>   
>  <span data-ttu-id="51b33-112">建議您基於測試目的同時授與 `Read Definition` 權限。</span><span class="sxs-lookup"><span data-stu-id="51b33-112">We suggest you also grant `Read Definition` permissions for testing purposes.</span></span> <span data-ttu-id="51b33-113">擁有 `Read Definition` 和 `Process Database` 權限的使用者可以透過互動方式處理 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中的物件。</span><span class="sxs-lookup"><span data-stu-id="51b33-113">A user having both `Read Definition` and `Process Database` permissions can process objects in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], interactively.</span></span> <span data-ttu-id="51b33-114">如需詳細資訊，請參閱 [授與物件中繼資料的讀取定義權限 &#40;Analysis Services&#41;](grant-read-definition-permissions-on-object-metadata-analysis-services.md) 。</span><span class="sxs-lookup"><span data-stu-id="51b33-114">See [Grant read definition permissions on object metadata &#40;Analysis Services&#41;](grant-read-definition-permissions-on-object-metadata-analysis-services.md) for details.</span></span>  
  
## <a name="set-processing-permissions-at-the-database-level"></a><span data-ttu-id="51b33-115">設定資料庫層級的處理權限</span><span class="sxs-lookup"><span data-stu-id="51b33-115">Set processing permissions at the database level</span></span>  
 <span data-ttu-id="51b33-116">本節說明如何針對資料庫中的所有 Cube、維度、採礦結構及採礦模型，由非管理員的使用者來啟用處理。</span><span class="sxs-lookup"><span data-stu-id="51b33-116">This section explains how to enable processing by non-administrators, for all cubes, dimensions, mining structures, and mining models in the database.</span></span>  
  
1.  <span data-ttu-id="51b33-117">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，連接到 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]的執行個體、開啟 [資料庫] 資料夾，然後選取資料庫。</span><span class="sxs-lookup"><span data-stu-id="51b33-117">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to the instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], open the Databases folder, and select a database.</span></span>  
  
2.  <span data-ttu-id="51b33-118">以滑鼠右鍵按一下 [**角色**] [  |  **新增角色**]。</span><span class="sxs-lookup"><span data-stu-id="51b33-118">Right-click **Roles** | **New Role**.</span></span> <span data-ttu-id="51b33-119">輸入名稱和描述。</span><span class="sxs-lookup"><span data-stu-id="51b33-119">Enter a name and description.</span></span>  
  
3.  <span data-ttu-id="51b33-120">在 [**一般**] 窗格中，選取 `Process Database` 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="51b33-120">In the **General** pane, select the `Process Database` check box.</span></span> <span data-ttu-id="51b33-121">此外，選取 `Read Definition` 也可以透過其中一個 SQL Server 工具（例如）啟用互動式處理 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="51b33-121">Additionally, select `Read Definition` to also enable interactive processing through one of the SQL Server tools, such as [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
4.  <span data-ttu-id="51b33-122">在 [成員資格]\*\*\*\* 窗格中，新增擁有可處理這個資料庫中任何物件之權限的 Windows 使用者和群組帳戶。</span><span class="sxs-lookup"><span data-stu-id="51b33-122">In the **Membership** pane, add the Windows user and group accounts having permission to process any object in this database.</span></span>  
  
5.  <span data-ttu-id="51b33-123">按一下 [確定]\*\*\*\* 以完成角色定義。</span><span class="sxs-lookup"><span data-stu-id="51b33-123">Click **OK** to complete the role definition.</span></span>  
  
## <a name="set-processing-permissions-on-individual-objects"></a><span data-ttu-id="51b33-124">設定個別物件的處理權限</span><span class="sxs-lookup"><span data-stu-id="51b33-124">Set processing permissions on individual objects</span></span>  
 <span data-ttu-id="51b33-125">您可以設定個別 Cube、維度、資料採礦結構或模型的處理權限。</span><span class="sxs-lookup"><span data-stu-id="51b33-125">You can set processing permissions on individual cubes, dimensions, data mining structures or models.</span></span>  
  
 <span data-ttu-id="51b33-126">如果您不小心排除了需要一起處理的物件 (例如，如果您啟用 Cube 上的處理，但未啟用其相關維度上的處理)，則處理會失敗。</span><span class="sxs-lookup"><span data-stu-id="51b33-126">Processing can fail if you inadvertently exclude objects that need to be processed together (for example, if you enable processing on a cube, but not on its related dimensions).</span></span> <span data-ttu-id="51b33-127">因為很容易遺失物件相依性，因此，在設定個別物件的處理權限時，徹底測試是必要的。</span><span class="sxs-lookup"><span data-stu-id="51b33-127">Because it can be easy to miss object dependencies, thorough testing is essential when setting processing permissions on individual objects.</span></span>  
  
1.  <span data-ttu-id="51b33-128">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，連接到 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]的執行個體、開啟 [資料庫] 資料夾，然後選取資料庫。</span><span class="sxs-lookup"><span data-stu-id="51b33-128">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to the instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], open the Databases folder, and select a database.</span></span>  
  
2.  <span data-ttu-id="51b33-129">以滑鼠右鍵按一下 [**角色**] [  |  **新增角色**]。</span><span class="sxs-lookup"><span data-stu-id="51b33-129">Right-click **Roles** | **New Role**.</span></span> <span data-ttu-id="51b33-130">輸入名稱和描述。</span><span class="sxs-lookup"><span data-stu-id="51b33-130">Enter a name and description.</span></span>  
  
3.  <span data-ttu-id="51b33-131">在 [**一般**] 窗格中，清除 `Process Database` 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="51b33-131">In the **General** pane, clear the `Process Database` check box.</span></span> <span data-ttu-id="51b33-132">資料庫權限會藉由將角色選項變成灰色或無法選取狀態，來覆寫設定較低層級物件之權限的能力。</span><span class="sxs-lookup"><span data-stu-id="51b33-132">Database permissions override the ability to set permissions on lower-level objects by making role options grayed out or un-selectable.</span></span>  
  
     <span data-ttu-id="51b33-133">技術上來說，專屬的處理角色不需要任何資料庫權限。</span><span class="sxs-lookup"><span data-stu-id="51b33-133">Technically, no database permissions are needed for dedicated processing roles.</span></span> <span data-ttu-id="51b33-134">但是， `Read Definition` 如果沒有資料庫層級，您就無法在中查看資料庫 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，讓測試變得更棘手。</span><span class="sxs-lookup"><span data-stu-id="51b33-134">But without `Read Definition` at the database level, you cannot view the database in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], making testing more difficult.</span></span>  
  
4.  <span data-ttu-id="51b33-135">選取要處理的個別物件：</span><span class="sxs-lookup"><span data-stu-id="51b33-135">Select individual objects to process:</span></span>  
  
    -   <span data-ttu-id="51b33-136">在 [Cube]\*\*\*\* 窗格中，選取每個 Cube 的 [處理]\*\*\*\* 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="51b33-136">In the **Cubes** pane, select the **Process** check box for each cube.</span></span>  
  
    -   <span data-ttu-id="51b33-137">在 [維度]\*\*\*\* 窗格中，選取 [所有資料庫維度]\*\*\*\*，然後選取每個維度的 [處理]\*\*\*\* 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="51b33-137">In the **Dimensions** pane, select **All database dimensions**, and then **Process** check box for each dimension.</span></span> <span data-ttu-id="51b33-138">或者，選取所有資料列，然後使用 Shift + 滑鼠左鍵來切換核取方塊選取項目。</span><span class="sxs-lookup"><span data-stu-id="51b33-138">Or, select all rows, then use shift-click to toggle the check box selections.</span></span>  
  
5.  <span data-ttu-id="51b33-139">在 [成員資格]\*\*\*\* 窗格中，新增擁有權限可處理這些物件的 Windows 使用者和群組帳戶。</span><span class="sxs-lookup"><span data-stu-id="51b33-139">In the **Membership** pane, add the Windows user and group accounts having permission to process these objects.</span></span>  
  
6.  <span data-ttu-id="51b33-140">按一下 [確定]\*\*\*\* 以完成角色定義。</span><span class="sxs-lookup"><span data-stu-id="51b33-140">Click **OK** to complete the role definition.</span></span>  
  
## <a name="test-processing"></a><span data-ttu-id="51b33-141">測試處理</span><span class="sxs-lookup"><span data-stu-id="51b33-141">Test processing</span></span>  
  
1.  <span data-ttu-id="51b33-142">按住 Shift 鍵並使用滑鼠右鍵按一下 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、選取 [以不同的使用者身分執行]\*\*\*\*，然後使用指派給您正在測試之角色的 Windows 帳戶連接到 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="51b33-142">Hold down the shift-key and right-click [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], select **Run as a different user** and connect to the instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] using a Windows account assigned to the role you are testing.</span></span>  
  
2.  <span data-ttu-id="51b33-143">開啟 [資料庫] 資料夾，然後選取資料庫。</span><span class="sxs-lookup"><span data-stu-id="51b33-143">Open the Databases folder, and select a database.</span></span> <span data-ttu-id="51b33-144">您將只會看見您的帳戶具有成員資格之角色可看見的資料庫。</span><span class="sxs-lookup"><span data-stu-id="51b33-144">You will only see the databases that are visible to the roles for which your account has membership.</span></span>  
  
3.  <span data-ttu-id="51b33-145">使用滑鼠右鍵按一下 Cube 或維度，然後選取 [處理]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="51b33-145">Right-click a cube or dimension and select **Process**.</span></span> <span data-ttu-id="51b33-146">選擇處理選項。</span><span class="sxs-lookup"><span data-stu-id="51b33-146">Choose a processing option.</span></span> <span data-ttu-id="51b33-147">針對所有物件組合，測試所有選項。</span><span class="sxs-lookup"><span data-stu-id="51b33-147">Test all of the options, for all combinations of objects.</span></span> <span data-ttu-id="51b33-148">如果因為遺漏物件而發生錯誤，請將物件新增到角色。</span><span class="sxs-lookup"><span data-stu-id="51b33-148">If errors occur due to missing objects, add the objects to the role.</span></span>  
  
## <a name="set-processing-permissions-on-a-data-mining-structure"></a><span data-ttu-id="51b33-149">設定資料採礦結構的處理權限</span><span class="sxs-lookup"><span data-stu-id="51b33-149">Set processing permissions on a data mining structure</span></span>  
 <span data-ttu-id="51b33-150">您可以建立角色，授與權限來處理資料採礦結構。</span><span class="sxs-lookup"><span data-stu-id="51b33-150">You can create a role granting permission to process data mining structures.</span></span> <span data-ttu-id="51b33-151">其中包括處理所有採礦模型。</span><span class="sxs-lookup"><span data-stu-id="51b33-151">This includes the processing of all mining models.</span></span>  
  
 <span data-ttu-id="51b33-152">導覽和結構的流覽和許可權是不可部分**完成**的，而且 `Read Definition` 可以加入至相同的角色，或分成不同的角色。</span><span class="sxs-lookup"><span data-stu-id="51b33-152">**Drill Through** and `Read Definition` permissions used for browsing a mining model and structure are atomic and can be added to the same role, or separated out into a different role.</span></span>  
  
1.  <span data-ttu-id="51b33-153">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，連接到 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]的執行個體、開啟 [資料庫] 資料夾，然後選取資料庫。</span><span class="sxs-lookup"><span data-stu-id="51b33-153">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to the instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], open the Databases folder, and select a database.</span></span>  
  
2.  <span data-ttu-id="51b33-154">以滑鼠右鍵按一下 [**角色**] [  |  **新增角色**]。</span><span class="sxs-lookup"><span data-stu-id="51b33-154">Right-click **Roles** | **New Role**.</span></span> <span data-ttu-id="51b33-155">輸入名稱和描述。</span><span class="sxs-lookup"><span data-stu-id="51b33-155">Enter a name and description.</span></span> <span data-ttu-id="51b33-156">在 [一般]\*\*\*\* 窗格中，確定已取消選取資料庫權限核取方塊。</span><span class="sxs-lookup"><span data-stu-id="51b33-156">In the **General** pane, make sure that the database permission check boxes are clear.</span></span> <span data-ttu-id="51b33-157">資料庫權限將會藉由將角色選項變成灰色或無法選取狀態，來覆寫設定較低層級物件之權限的能力。</span><span class="sxs-lookup"><span data-stu-id="51b33-157">Database permissions will override the ability to set permissions on lower-level objects by making role options grayed out or un-selectable.</span></span>  
  
3.  <span data-ttu-id="51b33-158">在 [採礦結構]\*\*\*\* 窗格中，選取每個採礦結構的 [處理]\*\*\*\* 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="51b33-158">In the **Mining Structures** pane, select the **Process** check box for each mining structure.</span></span>  
  
4.  <span data-ttu-id="51b33-159">在 [成員資格]\*\*\*\* 窗格中，新增擁有可處理這個資料庫中任何物件之權限的 Windows 使用者和群組帳戶。</span><span class="sxs-lookup"><span data-stu-id="51b33-159">In the **Membership** pane, add the Windows user and group accounts having permission to process any object in this database.</span></span>  
  
5.  <span data-ttu-id="51b33-160">按一下 [確定]\*\*\*\* 以完成角色定義。</span><span class="sxs-lookup"><span data-stu-id="51b33-160">Click **OK** to complete the role definition.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51b33-161">另請參閱</span><span class="sxs-lookup"><span data-stu-id="51b33-161">See Also</span></span>  
 <span data-ttu-id="51b33-162">[處理資料庫、資料表或資料分割](../tabular-models/process-database-table-or-partition-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="51b33-162">[Process Database, Table, or Partition](../tabular-models/process-database-table-or-partition-analysis-services.md) </span></span>  
 <span data-ttu-id="51b33-163">[多維度模型物件處理](processing-a-multidimensional-model-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="51b33-163">[Multidimensional Model Object Processing](processing-a-multidimensional-model-analysis-services.md) </span></span>  
 <span data-ttu-id="51b33-164">[授與資料庫許可權 &#40;Analysis Services&#41;](grant-database-permissions-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="51b33-164">[Grant database permissions &#40;Analysis Services&#41;](grant-database-permissions-analysis-services.md) </span></span>  
 [<span data-ttu-id="51b33-165">授與物件中繼資料的讀取定義權限 &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="51b33-165">Grant read definition permissions on object metadata &#40;Analysis Services&#41;</span></span>](grant-read-definition-permissions-on-object-metadata-analysis-services.md)  
  
  
