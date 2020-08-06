---
title: SQL Server 公用程式) 的公用程式管理 (|Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: 3e5a00c3-8905-40f0-9ddc-d924df9c2f0d
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: fca4ea655ffdcf8471d1340016d16f2c5b9c352a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700174"
---
# <a name="utility-administration-sql-server-utility"></a><span data-ttu-id="ae51b-102">公用程式管理 (SQL Server 公用程式)</span><span class="sxs-lookup"><span data-stu-id="ae51b-102">Utility Administration (SQL Server Utility)</span></span>
  <span data-ttu-id="ae51b-103">您可以使用 [公用程式管理] 索引標籤來管理 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 公用程式的原則、安全性和資料倉儲設定。</span><span class="sxs-lookup"><span data-stu-id="ae51b-103">Use the Utility Administration tabs to manage policy, security, and data warehouse settings for a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Utility.</span></span> <span data-ttu-id="ae51b-104">如需 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 公用程式概念的詳細資訊，請參閱 [SQL Server 公用程式的功能與工作](../relational-databases/manage/sql-server-utility-features-and-tasks.md)。</span><span class="sxs-lookup"><span data-stu-id="ae51b-104">For more information about [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Utility concepts, see [SQL Server Utility Features and Tasks](../relational-databases/manage/sql-server-utility-features-and-tasks.md).</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="ae51b-105">UI 元素清單</span><span class="sxs-lookup"><span data-stu-id="ae51b-105">UI element list</span></span>  
 <span data-ttu-id="ae51b-106">原則索引標籤 - 使用 [原則] 索引標籤來檢視或指定全域監視原則。</span><span class="sxs-lookup"><span data-stu-id="ae51b-106">Policy tab - Use the policy tab to view or specify global monitoring policies.</span></span>  
  
 <span data-ttu-id="ae51b-107">設定全域資料層應用程式監視原則。</span><span class="sxs-lookup"><span data-stu-id="ae51b-107">Set global data-tier application monitoring policies.</span></span> <span data-ttu-id="ae51b-108">若要展開這個選項的值清單，請按一下原則名稱旁的箭頭，或是按一下原則標題。</span><span class="sxs-lookup"><span data-stu-id="ae51b-108">To expand the list of values for this option, click on the arrow next to the policy name, or click on the policy title.</span></span>  
 <span data-ttu-id="ae51b-109">應用程式何時用完處理器容量？</span><span class="sxs-lookup"><span data-stu-id="ae51b-109">When is an application running out of processor capacity?</span></span> <span data-ttu-id="ae51b-110">若要變更這個原則，請使用原則描述右邊的控制項，然後按一下 **[套用]** 。</span><span class="sxs-lookup"><span data-stu-id="ae51b-110">To change this policy, use the control to the right of the policy description, then click **Apply**.</span></span> <span data-ttu-id="ae51b-111">您也可以使用顯示畫面底部的按鈕來還原預設值或捨棄變更。</span><span class="sxs-lookup"><span data-stu-id="ae51b-111">You can also restore default values or discard changes using buttons at the bottom of the display.</span></span>  
  
-   <span data-ttu-id="ae51b-112">處理器使用量的預設最大值為 70%。</span><span class="sxs-lookup"><span data-stu-id="ae51b-112">The default maximum value for processor utilization is 70%.</span></span>  
  
-   <span data-ttu-id="ae51b-113">處理器使用量的預設最小值為 0%。</span><span class="sxs-lookup"><span data-stu-id="ae51b-113">The default minimum value for processor utilization is 0%.</span></span>  
  
 <span data-ttu-id="ae51b-114">應用程式何時用完檔案空間？</span><span class="sxs-lookup"><span data-stu-id="ae51b-114">When is an application running out of file space?</span></span> <span data-ttu-id="ae51b-115">若要變更資料檔或記錄檔空間使用量的原則，請使用原則描述右邊的控制項，然後按一下 [套用] 。</span><span class="sxs-lookup"><span data-stu-id="ae51b-115">To change the policy for data file or log file space utilization, use the control to the right of the policy description, then click **Apply**.</span></span> <span data-ttu-id="ae51b-116">您也可以使用顯示畫面底部的按鈕來還原預設值或捨棄變更。</span><span class="sxs-lookup"><span data-stu-id="ae51b-116">You can also restore default values or discard changes using buttons at the bottom of the display.</span></span>  
  
-   <span data-ttu-id="ae51b-117">檔案空間使用量的預設最大值為 70%。</span><span class="sxs-lookup"><span data-stu-id="ae51b-117">The default maximum value for file space utilization is 70%.</span></span>  
  
-   <span data-ttu-id="ae51b-118">檔案空間使用量的預設最小值為 0%。</span><span class="sxs-lookup"><span data-stu-id="ae51b-118">The default minimum value for file space utilization is 0%.</span></span>  
  
 <span data-ttu-id="ae51b-119">設定 SQL Server Managed 執行個體的全域應用程式監視原則。</span><span class="sxs-lookup"><span data-stu-id="ae51b-119">Set global SQL Server managed instance application monitoring policies.</span></span> <span data-ttu-id="ae51b-120">若要展開這個選項的值清單，請按一下原則名稱旁的箭頭，或是按一下原則標題。</span><span class="sxs-lookup"><span data-stu-id="ae51b-120">To expand the list of values for this option, click on the arrow next to the policy name, or click on the policy title.</span></span>  
 <span data-ttu-id="ae51b-121">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的 Managed 執行個體何時用完處理器容量？</span><span class="sxs-lookup"><span data-stu-id="ae51b-121">When is a managed instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] running out of processor capacity?</span></span> <span data-ttu-id="ae51b-122">若要變更這個原則，請使用原則描述右邊的控制項，然後按一下 **[套用]** 。</span><span class="sxs-lookup"><span data-stu-id="ae51b-122">To change this policy, use the control to the right of the policy description, then click **Apply**.</span></span> <span data-ttu-id="ae51b-123">您也可以使用顯示畫面底部的按鈕來還原預設值或捨棄變更。</span><span class="sxs-lookup"><span data-stu-id="ae51b-123">You can also restore default values or discard changes using buttons at the bottom of the display.</span></span>  
  
-   <span data-ttu-id="ae51b-124">執行個體處理器使用量的預設最大值為 70%。</span><span class="sxs-lookup"><span data-stu-id="ae51b-124">The default maximum value for instance processor utilization is 70%.</span></span>  
  
-   <span data-ttu-id="ae51b-125">執行個體處理器使用量的預設最小值為 0%。</span><span class="sxs-lookup"><span data-stu-id="ae51b-125">The default minimum value for instance processor utilization is 0%.</span></span>  
  
 <span data-ttu-id="ae51b-126">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 電腦的 Managed 執行個體何時用完處理器容量？</span><span class="sxs-lookup"><span data-stu-id="ae51b-126">When is a managed instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] computer running out of processor capacity?</span></span> <span data-ttu-id="ae51b-127">若要變更這個原則，請使用原則描述右邊的控制項，然後按一下 **[套用]** 。</span><span class="sxs-lookup"><span data-stu-id="ae51b-127">To change this policy, use the control to the right of the policy description, then click **Apply**.</span></span> <span data-ttu-id="ae51b-128">您也可以使用顯示畫面底部的按鈕來還原預設值或捨棄變更。</span><span class="sxs-lookup"><span data-stu-id="ae51b-128">You can also restore default values or discard changes using buttons at the bottom of the display.</span></span>  
  
-   <span data-ttu-id="ae51b-129">電腦處理器使用量的預設最大值為 70%。</span><span class="sxs-lookup"><span data-stu-id="ae51b-129">The default maximum value for computer processor utilization is 70%.</span></span>  
  
-   <span data-ttu-id="ae51b-130">電腦處理器使用量的預設最小值為 0%。</span><span class="sxs-lookup"><span data-stu-id="ae51b-130">The default minimum value for computer processor utilization is 0%.</span></span>  
  
 <span data-ttu-id="ae51b-131">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的 Managed 執行個體何時用完檔案空間？</span><span class="sxs-lookup"><span data-stu-id="ae51b-131">When is a managed instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] running out of file space?</span></span> <span data-ttu-id="ae51b-132">若要變更資料檔或記錄檔空間使用量的原則，請使用原則描述右邊的控制項，然後按一下 **[套用]** 。</span><span class="sxs-lookup"><span data-stu-id="ae51b-132">To change the policy for data file or log file space utilization , use the control to the right of the policy description, then click **Apply**.</span></span> <span data-ttu-id="ae51b-133">您也可以使用顯示畫面底部的按鈕來還原預設值或捨棄變更。</span><span class="sxs-lookup"><span data-stu-id="ae51b-133">You can also restore default values or discard changes using buttons at the bottom of the display.</span></span>  
  
-   <span data-ttu-id="ae51b-134">檔案空間使用量的預設最大值為 70%。</span><span class="sxs-lookup"><span data-stu-id="ae51b-134">The default maximum value for file space utilization is 70%.</span></span>  
  
-   <span data-ttu-id="ae51b-135">檔案空間使用量的預設最小值為 0%。</span><span class="sxs-lookup"><span data-stu-id="ae51b-135">The default minimum value for file space utilization is 0%.</span></span>  
  
 <span data-ttu-id="ae51b-136">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 電腦的 Managed 執行個體何時用完存放磁碟區空間？</span><span class="sxs-lookup"><span data-stu-id="ae51b-136">When is a managed instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] computer running out of storage volume space?</span></span> <span data-ttu-id="ae51b-137">若要變更這個原則，請使用原則描述右邊的控制項，然後按一下 **[套用]** 。</span><span class="sxs-lookup"><span data-stu-id="ae51b-137">To change this policy, use the control to the right of the policy description, then click **Apply**.</span></span> <span data-ttu-id="ae51b-138">您也可以使用顯示畫面底部的按鈕來還原預設值或捨棄變更。</span><span class="sxs-lookup"><span data-stu-id="ae51b-138">You can also restore default values or discard changes using buttons at the bottom of the display.</span></span>  
  
-   <span data-ttu-id="ae51b-139">電腦磁碟區空間使用量的預設最大值為 70%。</span><span class="sxs-lookup"><span data-stu-id="ae51b-139">The default maximum value for computer volume space utilization is 70%.</span></span>  
  
-   <span data-ttu-id="ae51b-140">電腦磁碟區空間使用量的預設最小值為 0%。</span><span class="sxs-lookup"><span data-stu-id="ae51b-140">The default minimum value for computer volume space utilization is 0%.</span></span>  
  
 <span data-ttu-id="ae51b-141">從高動態的資源中減少原則違規雜訊。</span><span class="sxs-lookup"><span data-stu-id="ae51b-141">Reducing policy violation noise from highly volatile resources.</span></span> <span data-ttu-id="ae51b-142">若要展開這項功能的控制項，請按一下顯示畫面右邊的向下箭頭。</span><span class="sxs-lookup"><span data-stu-id="ae51b-142">To expand the controls for this feature, click on the down-arrow on the right side of the display.</span></span>  
 <span data-ttu-id="ae51b-143">如需詳細資訊，請參閱[降低 CPU 使用量原則的雜訊 &#40;SQL Server Utility&#41;](../relational-databases/manage/reduce-noise-in-cpu-utilization-policies-sql-server-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="ae51b-143">For more information, see [Reduce Noise in CPU Utilization Policies &#40;SQL Server Utility&#41;](../relational-databases/manage/reduce-noise-in-cpu-utilization-policies-sql-server-utility.md)</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="ae51b-144">UI 元素清單</span><span class="sxs-lookup"><span data-stu-id="ae51b-144">UI element list</span></span>  
 <span data-ttu-id="ae51b-145">安全性索引標籤 - 顯示有權從 UCP 管理或讀取的登入名稱。</span><span class="sxs-lookup"><span data-stu-id="ae51b-145">Security tab - Displays login names with permissions to administer or read from the UCP.</span></span>  
  
 <span data-ttu-id="ae51b-146">從 UCP 選取將會加入至公用程式讀取者角色的登入。</span><span class="sxs-lookup"><span data-stu-id="ae51b-146">Select the logins from the UCP that will be added to the Utility Reader role.</span></span>  
 <span data-ttu-id="ae51b-147">公用程式讀取者權限可讓使用者帳戶：</span><span class="sxs-lookup"><span data-stu-id="ae51b-147">The Utility Reader privilege allows the user account to:</span></span>  
  
-   <span data-ttu-id="ae51b-148">連接到 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 公用程式。</span><span class="sxs-lookup"><span data-stu-id="ae51b-148">Connect to the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Utility.</span></span>  
  
-   <span data-ttu-id="ae51b-149">請參閱 SSMS 中公用程式總管內的所有視點。</span><span class="sxs-lookup"><span data-stu-id="ae51b-149">See all viewpoints in the Utility Explorer in SSMS.</span></span>  
  
-   <span data-ttu-id="ae51b-150">請參閱 SSMS 中公用程式總管內 [公用程式管理] 節點上的設定。</span><span class="sxs-lookup"><span data-stu-id="ae51b-150">See settings on the Utility Administration node in Utility Explorer in SSMS.</span></span>  
  
 <span data-ttu-id="ae51b-151">公用程式管理員可以將 SQL Server 執行個體註冊到 SQL Server 公用程式，並從 SQL Server 公用程式中移除 SQL Server 執行個體，也可以修改 Managed 執行個體的原則及修改 UCP 上的管理設定。</span><span class="sxs-lookup"><span data-stu-id="ae51b-151">Utility administrators can enroll instances of SQL Server into and remove instances of SQL Server from a SQL Server Utility, as well as modify policies on managed instances and modify administration settings on the UCP.</span></span>  
  
 <span data-ttu-id="ae51b-152">若要成為公用程式管理員，您必須擁有 SQL Server 執行個體的系統管理員 (sysadmin) 權限。</span><span class="sxs-lookup"><span data-stu-id="ae51b-152">To be a Utility administrator, you must have sysadmin privileges on the instance of SQL Server.</span></span> <span data-ttu-id="ae51b-153">若要加入或變更 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] UCP 的使用者帳戶，請在 SSMS 中使用物件總管，將使用者加入至 SQL Server UCP 執行個體的伺服器登入。</span><span class="sxs-lookup"><span data-stu-id="ae51b-153">To add or change user accounts for the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] UCP, use Object Explorer in SSMS to add the user to the server logins of the UCP instance of SQL Server.</span></span> <span data-ttu-id="ae51b-154">如需詳細資訊，請參閱 [sp_addlogin &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addlogin-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="ae51b-154">For more information, see [sp_addlogin &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addlogin-transact-sql).</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="ae51b-155">UI 元素清單</span><span class="sxs-lookup"><span data-stu-id="ae51b-155">UI element list</span></span>  
 <span data-ttu-id="ae51b-156">資料倉儲索引標籤 - 顯示公用程式管理資料倉儲的組態詳細資料。</span><span class="sxs-lookup"><span data-stu-id="ae51b-156">Data Warehouse tab - Displays configuration details for the utility management data warehouse.</span></span>  
  
 <span data-ttu-id="ae51b-157">資料保留</span><span class="sxs-lookup"><span data-stu-id="ae51b-157">Data Retention</span></span>  
 <span data-ttu-id="ae51b-158">指定針對 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]Managed 執行個體所收集之使用量資訊的資料保留週期。</span><span class="sxs-lookup"><span data-stu-id="ae51b-158">Specify the data retention period for utilization information collected for managed instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="ae51b-159">預設期間為 1 年。</span><span class="sxs-lookup"><span data-stu-id="ae51b-159">The default time period is 1 year.</span></span> <span data-ttu-id="ae51b-160">最小值是 1 個月。</span><span class="sxs-lookup"><span data-stu-id="ae51b-160">The minimum value is 1 month.</span></span> <span data-ttu-id="ae51b-161">最長的支援期間為 2 年。</span><span class="sxs-lookup"><span data-stu-id="ae51b-161">The longest supported value is 2 years.</span></span>  
  
 <span data-ttu-id="ae51b-162">公用程式資料倉儲組態資訊</span><span class="sxs-lookup"><span data-stu-id="ae51b-162">Utility Data Warehouse Configuration Information</span></span>  
 <span data-ttu-id="ae51b-163">這一版的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]無法設定下列組態設定：</span><span class="sxs-lookup"><span data-stu-id="ae51b-163">The following configuration settings are not configurable in this release of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="ae51b-164">UMDW 名稱：Sysutility_mdw_\<GUID>_DATA。</span><span class="sxs-lookup"><span data-stu-id="ae51b-164">UMDW name: Sysutility_mdw_\<GUID>_DATA.</span></span>  
  
-   <span data-ttu-id="ae51b-165">收集組上傳頻率：每隔 15 分鐘。</span><span class="sxs-lookup"><span data-stu-id="ae51b-165">Collection set upload frequency: Every 15 minutes.</span></span>  
  
 <span data-ttu-id="ae51b-166">UMDW 目錄是可設定的：\<System drive>:\Program Files\Microsoft SQL Server\MSSQL10_50.<UCP_Name>\MSSQL\Data\\，其中 \<System drive> 通常是 C:\ 磁碟機。</span><span class="sxs-lookup"><span data-stu-id="ae51b-166">The UMDW directory is configurable: \<System drive>:\Program Files\Microsoft SQL Server\MSSQL10_50.<UCP_Name>\MSSQL\Data\\, where \<System drive> is normally the C:\ drive.</span></span> <span data-ttu-id="ae51b-167">記錄檔 UMDW_\<GUID>_LOG 位於相同的目錄中。</span><span class="sxs-lookup"><span data-stu-id="ae51b-167">The log file, UMDW_\<GUID>_LOG, is located in the same directory.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ae51b-168">可以使用卸離/附加或 ALTER DATABASE 來變更 UMDW (sysutility_mdw) 檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="ae51b-168">The UMDW (sysutility_mdw) file location can be changed using detach/attach or ALTER DATABASE.</span></span> <span data-ttu-id="ae51b-169">我們建議使用 ALTER DATABASE。</span><span class="sxs-lookup"><span data-stu-id="ae51b-169">We recommend the use of ALTER DATABASE.</span></span> <span data-ttu-id="ae51b-170">如需詳細資訊，請參閱 [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="ae51b-170">For more information, see [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql).</span></span>  
  
 <span data-ttu-id="ae51b-171">回到原廠的預設值</span><span class="sxs-lookup"><span data-stu-id="ae51b-171">Go back to out-of-the-box defaults</span></span>  
 <span data-ttu-id="ae51b-172">若要將此索引標籤上的設定重設為預設值，請按一下 [還原預設值] 按鈕，然後按一下 [套用]。</span><span class="sxs-lookup"><span data-stu-id="ae51b-172">To reset settings on this tab to default values, click the **Restore Defaults** button, then click **Apply**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae51b-173">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ae51b-173">See Also</span></span>  
 <span data-ttu-id="ae51b-174">[公用程式儀表板 &#40;SQL Server 公用程式&#41;](../../2014/database-engine/utility-dashboard-sql-server-utility.md) </span><span class="sxs-lookup"><span data-stu-id="ae51b-174">[Utility Dashboard &#40;SQL Server Utility&#41;](../../2014/database-engine/utility-dashboard-sql-server-utility.md) </span></span>  
 <span data-ttu-id="ae51b-175">[部署的資料層應用程式詳細資料 &#40;SQL Server 公用程式&#41;](../../2014/database-engine/deployed-data-tier-application-details-sql-server-utility.md) </span><span class="sxs-lookup"><span data-stu-id="ae51b-175">[Deployed Data-tier Application Details &#40;SQL Server Utility&#41;](../../2014/database-engine/deployed-data-tier-application-details-sql-server-utility.md) </span></span>  
 <span data-ttu-id="ae51b-176">[受管理的執行個體詳細資料 &#40;SQL Server 公用程式&#41;](../../2014/database-engine/managed-instance-details-sql-server-utility.md) </span><span class="sxs-lookup"><span data-stu-id="ae51b-176">[Managed Instance Details &#40;SQL Server Utility&#41;](../../2014/database-engine/managed-instance-details-sql-server-utility.md) </span></span>  
 [<span data-ttu-id="ae51b-177">監視 SQL Server 公用程式中的 SQL Server 執行個體</span><span class="sxs-lookup"><span data-stu-id="ae51b-177">Monitor Instances of SQL Server in the SQL Server Utility</span></span>](../relational-databases/manage/monitor-instances-of-sql-server-in-the-sql-server-utility.md)  
  
  
