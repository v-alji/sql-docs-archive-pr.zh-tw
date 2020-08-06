---
title: 建立 RSExecRole | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- RSExecRole
ms.assetid: 7ac17341-df7e-4401-870e-652caa2859c0
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 0037ef0c4d7a949b5a30bb45356613f6114db130
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699289"
---
# <a name="create-the-rsexecrole"></a><span data-ttu-id="04c06-102">建立 RSExecRole</span><span class="sxs-lookup"><span data-stu-id="04c06-102">Create the RSExecRole</span></span>
  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] <span data-ttu-id="04c06-103">會使用稱為 `RSExecRole` 之預先定義的資料庫角色，授與報表伺服器對於報表伺服器資料庫的權限。</span><span class="sxs-lookup"><span data-stu-id="04c06-103">uses a predefined database role called `RSExecRole` to grant report server permissions to the report server database.</span></span> <span data-ttu-id="04c06-104">`RSExecRole` 角色會自動與報表伺服器資料庫一起建立。</span><span class="sxs-lookup"><span data-stu-id="04c06-104">The `RSExecRole` role is created automatically with the report server database.</span></span> <span data-ttu-id="04c06-105">您絕對不能修改它或是將其他使用者指派給這個角色，這是一般的規則。</span><span class="sxs-lookup"><span data-stu-id="04c06-105">As a rule, you should never modify it or assign other users to the role.</span></span> <span data-ttu-id="04c06-106">不過，當您將報表伺服器資料庫移至新的或不同的時 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../../includes/ssde-md.md)] ，必須在 MASTER 和 MSDB 系統資料庫中重新建立該角色。</span><span class="sxs-lookup"><span data-stu-id="04c06-106">However, when you move a report server database to a new or different [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../../includes/ssde-md.md)], must re-create the role in the Master and MSDB system databases.</span></span>

 <span data-ttu-id="04c06-107">使用下列指示執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="04c06-107">Using the following instructions, you will perform the following steps:</span></span>

-   <span data-ttu-id="04c06-108">在 Master 系統資料庫中建立及提供 `RSExecRole`。</span><span class="sxs-lookup"><span data-stu-id="04c06-108">Create and provision the `RSExecRole` in the Master system database.</span></span>

-   <span data-ttu-id="04c06-109">在 MSDB 系統資料庫中建立及提供 `RSExecRole`。</span><span class="sxs-lookup"><span data-stu-id="04c06-109">Create and provision the `RSExecRole` in the MSDB system database.</span></span>

> [!NOTE]
>  <span data-ttu-id="04c06-110">本主題的指示適用於不想要執行指令碼或撰寫 WMI 程式碼來提供報表伺服器資料庫的使用者。</span><span class="sxs-lookup"><span data-stu-id="04c06-110">The instructions in this topic are intended for users who do not want to run a script or write WMI code to provision the report server database.</span></span> <span data-ttu-id="04c06-111">如果您管理大型部署，而且平常都會移動資料庫，您應該撰寫指令碼，讓這些步驟自動化。</span><span class="sxs-lookup"><span data-stu-id="04c06-111">If you manage a large deployment and will be moving databases routinely, you should write a script to automate these steps.</span></span> <span data-ttu-id="04c06-112">如需詳細資訊，請參閱 [存取 Reporting Services WMI 提供者](../tools/access-the-reporting-services-wmi-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="04c06-112">For more information, see [Access the Reporting Services WMI Provider](../tools/access-the-reporting-services-wmi-provider.md).</span></span>

## <a name="before-you-start"></a><span data-ttu-id="04c06-113">開始之前</span><span class="sxs-lookup"><span data-stu-id="04c06-113">Before you start</span></span>

-   <span data-ttu-id="04c06-114">請備份加密金鑰，好讓您可以在移動資料庫之後還原這些金鑰。</span><span class="sxs-lookup"><span data-stu-id="04c06-114">Back up the encryption keys so that you can restore them after the database is moved.</span></span> <span data-ttu-id="04c06-115">這個步驟不會直接影響您建立及提供 `RSExecRole` 的能力，但是您必須擁有金鑰的備份，才能夠確認您的工作。</span><span class="sxs-lookup"><span data-stu-id="04c06-115">This is step does not directly affect your ability to create and provision the `RSExecRole`, but you must have a backup of the keys in order to verify your work.</span></span> <span data-ttu-id="04c06-116">如需詳細資訊，請參閱 [備份與還原 Reporting Services 加密金鑰](../install-windows/ssrs-encryption-keys-back-up-and-restore-encryption-keys.md)。</span><span class="sxs-lookup"><span data-stu-id="04c06-116">For more information, see [Back Up and Restore Reporting Services Encryption Keys](../install-windows/ssrs-encryption-keys-back-up-and-restore-encryption-keys.md).</span></span>

-   <span data-ttu-id="04c06-117">請確認您已經使用具有 `sysadmin` 執行個體上 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 權限的使用者帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="04c06-117">Verify you are logged on as a user account that has `sysadmin` permissions on the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance.</span></span>

-   <span data-ttu-id="04c06-118">請確認在您打算使用的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體上已安裝及執行 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] Agent 服務。</span><span class="sxs-lookup"><span data-stu-id="04c06-118">Verify [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent service is installed and running on the instance of the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] instance that you plan to use.</span></span>

-   <span data-ttu-id="04c06-119">附加 reportservertempdb 和 reportserver 資料庫。</span><span class="sxs-lookup"><span data-stu-id="04c06-119">Attach the reportservertempdb and reportserver databases.</span></span> <span data-ttu-id="04c06-120">您不需要附加這些資料庫也可以建立實際角色，但是在您測試工作以前，必須要附加這些資料庫。</span><span class="sxs-lookup"><span data-stu-id="04c06-120">You are not required to attach the databases to create the actual role, but they must be attached before you can test your work.</span></span>

 <span data-ttu-id="04c06-121">手動建立 `RSExecRole` 的指示是要用於移轉報表伺服器安裝的環境。</span><span class="sxs-lookup"><span data-stu-id="04c06-121">The instructions for manually creating the `RSExecRole` are intended to be used within the context of migrating a report server installation.</span></span> <span data-ttu-id="04c06-122">本主題不會說明類似備份及移動報表伺服器資料庫等重要工作，這些工作記載於 Database Engine 文件集內。</span><span class="sxs-lookup"><span data-stu-id="04c06-122">Important tasks such as backing up and moving the report server database are not addressed in this topic, but are documented in the Database Engine documentation.</span></span>

## <a name="create-rsexecrole-in-master"></a><span data-ttu-id="04c06-123">在 Master 資料庫中建立 RSExecRole</span><span class="sxs-lookup"><span data-stu-id="04c06-123">Create RSExecRole in Master</span></span>
 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] <span data-ttu-id="04c06-124">會使用適用於 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent 服務的擴充預存程序來支援排程作業。</span><span class="sxs-lookup"><span data-stu-id="04c06-124">uses extended stored procedures for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent service to support scheduled operations.</span></span> <span data-ttu-id="04c06-125">下列步驟說明如何將這些程序的 Execute 權限授與給 `RSExecRole` 角色。</span><span class="sxs-lookup"><span data-stu-id="04c06-125">The following steps explain how to grant Execute permissions for the procedures to the `RSExecRole` role.</span></span>

#### <a name="to-create-rsexecrole-in-the-master-system-database-using-management-studio"></a><span data-ttu-id="04c06-126">使用 Management Studio 在 Master 系統資料庫中建立 RSExecRole</span><span class="sxs-lookup"><span data-stu-id="04c06-126">To create RSExecRole in the Master system database using Management Studio</span></span>

1.  <span data-ttu-id="04c06-127">啟動 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 並連線到主控報表伺服器資料庫的 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="04c06-127">Start [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] and connect to the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] instance that hosts the report server database.</span></span>

2.  <span data-ttu-id="04c06-128">開啟 **[資料庫]** 。</span><span class="sxs-lookup"><span data-stu-id="04c06-128">Open **Databases**.</span></span>

3.  <span data-ttu-id="04c06-129">開啟 **[系統資料庫]** 。</span><span class="sxs-lookup"><span data-stu-id="04c06-129">Open **System Databases**.</span></span>

4.  <span data-ttu-id="04c06-130">開啟 `Master`。</span><span class="sxs-lookup"><span data-stu-id="04c06-130">Open `Master`.</span></span>

5.  <span data-ttu-id="04c06-131">開啟 **[安全性]** 。</span><span class="sxs-lookup"><span data-stu-id="04c06-131">Open **Security**.</span></span>

6.  <span data-ttu-id="04c06-132">開啟 **[角色]** 。</span><span class="sxs-lookup"><span data-stu-id="04c06-132">Open **Roles**.</span></span>

7.  <span data-ttu-id="04c06-133">以滑鼠右鍵按一下 **[資料庫角色]** ，然後選取 **[新增資料庫角色]** 。</span><span class="sxs-lookup"><span data-stu-id="04c06-133">Right-click **Database Roles**, and select **New Database Role**.</span></span> <span data-ttu-id="04c06-134">[一般] 頁面隨即出現。</span><span class="sxs-lookup"><span data-stu-id="04c06-134">The General page appears.</span></span>

8.  <span data-ttu-id="04c06-135">在 [**角色名稱**] 中，輸入 `RSExecRole` 。</span><span class="sxs-lookup"><span data-stu-id="04c06-135">In **Role name**, type `RSExecRole`.</span></span>

9. <span data-ttu-id="04c06-136">在 **[擁有者]** 中輸入 **DBO**。</span><span class="sxs-lookup"><span data-stu-id="04c06-136">In **Owner**, type **DBO**.</span></span>

10. <span data-ttu-id="04c06-137">按一下 **[安全性實體]**。</span><span class="sxs-lookup"><span data-stu-id="04c06-137">Click **Securables**.</span></span>

11. <span data-ttu-id="04c06-138">按一下 **[搜尋]** 。</span><span class="sxs-lookup"><span data-stu-id="04c06-138">Click **Search**.</span></span> <span data-ttu-id="04c06-139">**[加入物件]** 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="04c06-139">The **Add Objects** dialog box appears.</span></span> <span data-ttu-id="04c06-140">預設會選取 **[特定物件]** 選項。</span><span class="sxs-lookup"><span data-stu-id="04c06-140">The **Specific Objects** option is selected by default.</span></span>

12. <span data-ttu-id="04c06-141">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="04c06-141">Click **OK**.</span></span> <span data-ttu-id="04c06-142">**[選取物件]** 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="04c06-142">The **Select Objects** dialog box appears.</span></span>

13. <span data-ttu-id="04c06-143">按一下 **[物件類型]** 。</span><span class="sxs-lookup"><span data-stu-id="04c06-143">Click **Object Types**.</span></span>

14. <span data-ttu-id="04c06-144">按一下 **[擴充預存程序]** 。</span><span class="sxs-lookup"><span data-stu-id="04c06-144">Click **Extended Stored Procedures**.</span></span>

15. <span data-ttu-id="04c06-145">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="04c06-145">Click **OK**.</span></span>

16. <span data-ttu-id="04c06-146">按一下 **[瀏覽]** 。</span><span class="sxs-lookup"><span data-stu-id="04c06-146">Click **Browse**.</span></span>

17. <span data-ttu-id="04c06-147">向下捲動擴充預存程序的清單，並選取以下項目：</span><span class="sxs-lookup"><span data-stu-id="04c06-147">Scroll down the list of extended stored procedures and select the following:</span></span>

    1.  <span data-ttu-id="04c06-148">xp_sqlagent_enum_jobs</span><span class="sxs-lookup"><span data-stu-id="04c06-148">xp_sqlagent_enum_jobs</span></span>

    2.  <span data-ttu-id="04c06-149">xp_sqlagent_is_starting</span><span class="sxs-lookup"><span data-stu-id="04c06-149">xp_sqlagent_is_starting</span></span>

    3.  <span data-ttu-id="04c06-150">xp_sqlagent_notify</span><span class="sxs-lookup"><span data-stu-id="04c06-150">xp_sqlagent_notify</span></span>

18. <span data-ttu-id="04c06-151">按一下 **[確定]** ，再按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="04c06-151">Click **OK**, and the click **OK** again.</span></span>

19. <span data-ttu-id="04c06-152">在 **[Execute]** 資料列中，按一下 **[授與]** 資料行內的核取方塊，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="04c06-152">In the **Execute** row, in the **Grant** column, click the check box, and then click **OK**.</span></span>

20. <span data-ttu-id="04c06-153">針對每個剩餘的預存程序重複此步驟。</span><span class="sxs-lookup"><span data-stu-id="04c06-153">Repeat for each of the remaining stored procedures.</span></span> <span data-ttu-id="04c06-154">`RSExecRole` 必須針對所有三個預存程序授與「執行」權限。</span><span class="sxs-lookup"><span data-stu-id="04c06-154">`RSExecRole` must be granted Execute permissions for all three stored procedures.</span></span>

 <span data-ttu-id="04c06-155">![[資料庫角色屬性] 頁面](../media/rsexecroledbproperties.gif "[資料庫角色屬性] 頁面")</span><span class="sxs-lookup"><span data-stu-id="04c06-155">![Database Role Properties page](../media/rsexecroledbproperties.gif "Database Role Properties page")</span></span>

## <a name="create-rsexecrole-in-msdb"></a><span data-ttu-id="04c06-156">在 MSDB 資料庫中建立 RSExecRole</span><span class="sxs-lookup"><span data-stu-id="04c06-156">Create RSExecRole in MSDB</span></span>
 <span data-ttu-id="04c06-157">Reporting Services 會使用適用於 SQL Server Agent 服務的預存程序，並從系統資料表擷取作業資訊來支援排程作業。</span><span class="sxs-lookup"><span data-stu-id="04c06-157">Reporting Services uses stored procedures for SQL Server Agent service and retrieves job information from system tables to support scheduled operations.</span></span> <span data-ttu-id="04c06-158">下列步驟說明如何將這些程序的 Execute 權限及資料表的 Select 權限授與給 RSExecRole。</span><span class="sxs-lookup"><span data-stu-id="04c06-158">The following steps explain how to grant Execute permissions for the procedures and Select permissions on the tables to the RSExecRole.</span></span>

#### <a name="to-create-rsexecrole-in-the-msdb-system-database"></a><span data-ttu-id="04c06-159">在 MSDB 系統資料庫中建立 RSExecRole</span><span class="sxs-lookup"><span data-stu-id="04c06-159">To create RSExecRole in the MSDB system database</span></span>

1.  <span data-ttu-id="04c06-160">重複類似的步驟來授與 MSDB 中預存程序和資料表的權限。</span><span class="sxs-lookup"><span data-stu-id="04c06-160">Repeat similar steps for granting permissions to stored procedures and tables in MSDB.</span></span> <span data-ttu-id="04c06-161">為了簡化步驟，您將會個別提供預存程序和資料表。</span><span class="sxs-lookup"><span data-stu-id="04c06-161">To simplify the steps, you will provision the stored procedures and tables separately.</span></span>

2.  <span data-ttu-id="04c06-162">開啟 `MSDB`。</span><span class="sxs-lookup"><span data-stu-id="04c06-162">Open `MSDB`.</span></span>

3.  <span data-ttu-id="04c06-163">開啟 **[安全性]**。</span><span class="sxs-lookup"><span data-stu-id="04c06-163">Open **Security**.</span></span>

4.  <span data-ttu-id="04c06-164">開啟 **[角色]**。</span><span class="sxs-lookup"><span data-stu-id="04c06-164">Open **Roles**.</span></span>

5.  <span data-ttu-id="04c06-165">以滑鼠右鍵按一下 **[資料庫角色]**，然後選取 **[新增資料庫角色]**。</span><span class="sxs-lookup"><span data-stu-id="04c06-165">Right-click **Database Roles**, and select **New Database Role**.</span></span> <span data-ttu-id="04c06-166">[一般] 頁面隨即出現。</span><span class="sxs-lookup"><span data-stu-id="04c06-166">The General page appears.</span></span>

6.  <span data-ttu-id="04c06-167">在 [角色名稱] 中，輸入 `RSExecRole` 。</span><span class="sxs-lookup"><span data-stu-id="04c06-167">In Role name, type `RSExecRole`.</span></span>

7.  <span data-ttu-id="04c06-168">在 [擁有者] 中輸入**DBO**。</span><span class="sxs-lookup"><span data-stu-id="04c06-168">In Owner, type **DBO**.</span></span>

8.  <span data-ttu-id="04c06-169">按一下 **[安全性實體]**。</span><span class="sxs-lookup"><span data-stu-id="04c06-169">Click **Securables**.</span></span>

9. <span data-ttu-id="04c06-170">按一下 [新增] 。</span><span class="sxs-lookup"><span data-stu-id="04c06-170">Click **Add**.</span></span> <span data-ttu-id="04c06-171">**[加入物件]** 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="04c06-171">The **Add Objects** dialog box appears.</span></span> <span data-ttu-id="04c06-172">預設會選取 **[指定物件]** 選項。</span><span class="sxs-lookup"><span data-stu-id="04c06-172">The **Specify Objects** option is selected by default.</span></span>

10. <span data-ttu-id="04c06-173">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="04c06-173">Click **OK**.</span></span>

11. <span data-ttu-id="04c06-174">按一下 **[物件類型]**。</span><span class="sxs-lookup"><span data-stu-id="04c06-174">Click **Object Types**.</span></span>

12. <span data-ttu-id="04c06-175">按一下 **[預存程序]**。</span><span class="sxs-lookup"><span data-stu-id="04c06-175">Click **Stored Procedures.**</span></span>

13. <span data-ttu-id="04c06-176">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="04c06-176">Click **OK**.</span></span>

14. <span data-ttu-id="04c06-177">按一下 **[瀏覽]** 。</span><span class="sxs-lookup"><span data-stu-id="04c06-177">Click **Browse**.</span></span>

15. <span data-ttu-id="04c06-178">向下捲動項目的清單，並選取以下項目：</span><span class="sxs-lookup"><span data-stu-id="04c06-178">Scroll down the list of items and select the following:</span></span>

    1.  <span data-ttu-id="04c06-179">sp_add_category</span><span class="sxs-lookup"><span data-stu-id="04c06-179">sp_add_category</span></span>

    2.  <span data-ttu-id="04c06-180">sp_add_job</span><span class="sxs-lookup"><span data-stu-id="04c06-180">sp_add_job</span></span>

    3.  <span data-ttu-id="04c06-181">sp_add_jobschedule</span><span class="sxs-lookup"><span data-stu-id="04c06-181">sp_add_jobschedule</span></span>

    4.  <span data-ttu-id="04c06-182">sp_add_jobserver</span><span class="sxs-lookup"><span data-stu-id="04c06-182">sp_add_jobserver</span></span>

    5.  <span data-ttu-id="04c06-183">sp_add_jobstep</span><span class="sxs-lookup"><span data-stu-id="04c06-183">sp_add_jobstep</span></span>

    6.  <span data-ttu-id="04c06-184">sp_delete_job</span><span class="sxs-lookup"><span data-stu-id="04c06-184">sp_delete_job</span></span>

    7.  <span data-ttu-id="04c06-185">sp_help_category</span><span class="sxs-lookup"><span data-stu-id="04c06-185">sp_help_category</span></span>

    8.  <span data-ttu-id="04c06-186">sp_help_job</span><span class="sxs-lookup"><span data-stu-id="04c06-186">sp_help_job</span></span>

    9. <span data-ttu-id="04c06-187">sp_help_jobschedule</span><span class="sxs-lookup"><span data-stu-id="04c06-187">sp_help_jobschedule</span></span>

    10. <span data-ttu-id="04c06-188">sp_verify_job_identifiers</span><span class="sxs-lookup"><span data-stu-id="04c06-188">sp_verify_job_identifiers</span></span>

16. <span data-ttu-id="04c06-189">按一下 **[確定]**，再按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="04c06-189">Click **OK**, and the click **OK** again.</span></span>

17. <span data-ttu-id="04c06-190">選取第一個預存程序：sp_add_category。</span><span class="sxs-lookup"><span data-stu-id="04c06-190">Select the first stored procedure: sp_add_category.</span></span>

18. <span data-ttu-id="04c06-191">在 **[Execute]** 資料列中，按一下 **[授與]** 資料行內的核取方塊，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="04c06-191">In the **Execute** row, in the **Grant** column, click the checkbox, and then click **OK**.</span></span>

19. <span data-ttu-id="04c06-192">針對每個剩餘的預存程序重複此步驟。</span><span class="sxs-lookup"><span data-stu-id="04c06-192">Repeat for each of the remaining stored procedures.</span></span> <span data-ttu-id="04c06-193">必須針對所有的十個預存程序為 RSExecRole 授與 Execute 權限。</span><span class="sxs-lookup"><span data-stu-id="04c06-193">RSExecRole must be granted Execute permissions for all ten stored procedures.</span></span>

20. <span data-ttu-id="04c06-194">在 [安全性實體] 索引標籤上，再次按一下 **[加入]** 。</span><span class="sxs-lookup"><span data-stu-id="04c06-194">On the Securables tab, and click **Add** again.</span></span> <span data-ttu-id="04c06-195">**[加入物件]** 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="04c06-195">The **Add Objects** dialog box appears.</span></span> <span data-ttu-id="04c06-196">預設會選取 **[指定物件]** 選項。</span><span class="sxs-lookup"><span data-stu-id="04c06-196">The **Specify Objects** option is selected by default.</span></span>

21. <span data-ttu-id="04c06-197">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="04c06-197">Click **OK**.</span></span>

22. <span data-ttu-id="04c06-198">按一下 **[物件類型]**。</span><span class="sxs-lookup"><span data-stu-id="04c06-198">Click **Object Types**.</span></span>

23. <span data-ttu-id="04c06-199">按一下 **[資料表]**。</span><span class="sxs-lookup"><span data-stu-id="04c06-199">Click **Tables.**</span></span>

24. <span data-ttu-id="04c06-200">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="04c06-200">Click **OK**.</span></span>

25. <span data-ttu-id="04c06-201">按一下 **[瀏覽]** 。</span><span class="sxs-lookup"><span data-stu-id="04c06-201">Click **Browse**.</span></span>

26. <span data-ttu-id="04c06-202">向下捲動項目的清單，並選取以下項目：</span><span class="sxs-lookup"><span data-stu-id="04c06-202">Scroll down the list of items and select the following:</span></span>

    1.  <span data-ttu-id="04c06-203">syscategories</span><span class="sxs-lookup"><span data-stu-id="04c06-203">syscategories</span></span>

    2.  <span data-ttu-id="04c06-204">sysjobs</span><span class="sxs-lookup"><span data-stu-id="04c06-204">sysjobs</span></span>

27. <span data-ttu-id="04c06-205">按一下 **[確定]**，再按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="04c06-205">Click **OK**, and the click **OK** again.</span></span>

28. <span data-ttu-id="04c06-206">選取第一個資料表：syscategories。</span><span class="sxs-lookup"><span data-stu-id="04c06-206">Select the first table: syscategories.</span></span>

29. <span data-ttu-id="04c06-207">在 **[Select]** 資料列中，按一下 **[授與]** 資料行內的核取方塊，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="04c06-207">In the **Select** row, in the **Grant** column, click the checkbox, and then click **OK**.</span></span>

30. <span data-ttu-id="04c06-208">針對 sysjobs 資料表重複此步驟。</span><span class="sxs-lookup"><span data-stu-id="04c06-208">Repeat for the sysjobs table.</span></span> <span data-ttu-id="04c06-209">必須針對這兩個資料表為 RSExecRole 授與 Select 權限。</span><span class="sxs-lookup"><span data-stu-id="04c06-209">RSExecRole must be granted Select permissions for both tables.</span></span>

## <a name="move-the-report-server-database"></a><span data-ttu-id="04c06-210">移動報表伺服器資料庫</span><span class="sxs-lookup"><span data-stu-id="04c06-210">Move the Report Server Database</span></span>
 <span data-ttu-id="04c06-211">在建立角色之後，您可以將報表伺服器資料庫移到新的 SQL Server 執行個體。</span><span class="sxs-lookup"><span data-stu-id="04c06-211">After you create the roles, you can move the report server database to new SQL Server instance.</span></span> <span data-ttu-id="04c06-212">如需詳細資訊，請參閱 [將報表伺服器資料庫移至其他電腦 &#40;SSRS 原生模式&#41;](../report-server/moving-the-report-server-databases-to-another-computer-ssrs-native-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="04c06-212">For more information, see [Moving the Report Server Databases to Another Computer &#40;SSRS Native Mode&#41;](../report-server/moving-the-report-server-databases-to-another-computer-ssrs-native-mode.md).</span></span>

 <span data-ttu-id="04c06-213">如果您要將 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] 升級到 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]，您可以在移動資料庫之前或之後來升級。</span><span class="sxs-lookup"><span data-stu-id="04c06-213">If you are upgrading the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] to [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], you can upgrade it before or after moving the database.</span></span>

 <span data-ttu-id="04c06-214">當報表伺服器連接到報表伺服器資料庫時，報表伺服器資料庫將會自動升級到 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="04c06-214">The report server database will be upgraded to the [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] automatically when the report server connects to it.</span></span> <span data-ttu-id="04c06-215">升級此資料庫不需要任何特定步驟。</span><span class="sxs-lookup"><span data-stu-id="04c06-215">There are no specific steps required for upgrading the database.</span></span>

## <a name="restore-encryption-keys-and-verify-your-work"></a><span data-ttu-id="04c06-216">還原加密金鑰及確認工作</span><span class="sxs-lookup"><span data-stu-id="04c06-216">Restore Encryption Keys and Verify Your Work</span></span>
 <span data-ttu-id="04c06-217">如果您已經附加報表伺服器資料庫，您現在應該能夠完成以下步驟來確認您的工作。</span><span class="sxs-lookup"><span data-stu-id="04c06-217">If you have attached the report server databases, you should now be able to complete the following steps to verify your work.</span></span>

#### <a name="to-verify-report-server-operability-after-a-database-move"></a><span data-ttu-id="04c06-218">在移動資料庫之後確認報表伺服器是否可操作</span><span class="sxs-lookup"><span data-stu-id="04c06-218">To verify report server operability after a database move</span></span>

1.  <span data-ttu-id="04c06-219">啟動 Reporting Services 組態工具，並連接到報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="04c06-219">Start the Reporting Services Configuration tool and connect to the report server.</span></span>

2.  <span data-ttu-id="04c06-220">按一下 **[資料庫]**。</span><span class="sxs-lookup"><span data-stu-id="04c06-220">Click **Database**.</span></span>

3.  <span data-ttu-id="04c06-221">按一下 **[變更資料庫]**。</span><span class="sxs-lookup"><span data-stu-id="04c06-221">Click **Change Database**.</span></span>

4.  <span data-ttu-id="04c06-222">按一下 **[選擇現有報表伺服器資料庫]**。</span><span class="sxs-lookup"><span data-stu-id="04c06-222">Click **Choose an existing report server database**.</span></span>

5.  <span data-ttu-id="04c06-223">輸入 Database Engine 的伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="04c06-223">Enter the server name of the Database Engine.</span></span> <span data-ttu-id="04c06-224">如果您將報表伺服器資料庫附加至已命名的實例，則必須以下列格式輸入實例名稱： \<servername> \\<instancename \> 。</span><span class="sxs-lookup"><span data-stu-id="04c06-224">If you attached the report server databases to a named instance, you must type the instance name in this format: \<servername>\\<instancename\>.</span></span>

6.  <span data-ttu-id="04c06-225">按一下 **[測試連接]** 。</span><span class="sxs-lookup"><span data-stu-id="04c06-225">Click **Test Connection**.</span></span>

7.  <span data-ttu-id="04c06-226">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="04c06-226">Click **Next**.</span></span>

8.  <span data-ttu-id="04c06-227">在 [資料庫] 上，選取報表伺服器資料庫。</span><span class="sxs-lookup"><span data-stu-id="04c06-227">On the Database, select the report server database.</span></span>

9. <span data-ttu-id="04c06-228">按 [下一步]  ，並且完成精靈。</span><span class="sxs-lookup"><span data-stu-id="04c06-228">Click **Next** and complete the wizard.</span></span>

10. <span data-ttu-id="04c06-229">按一下 **[加密金鑰]**。</span><span class="sxs-lookup"><span data-stu-id="04c06-229">Click **Encryption Keys**.</span></span>

11. <span data-ttu-id="04c06-230">按一下 [**還原**]。</span><span class="sxs-lookup"><span data-stu-id="04c06-230">Click **Restore**.</span></span>

12. <span data-ttu-id="04c06-231">選取具有對稱金鑰之備份副本 (用來解密預存認證) 及報表伺服器資料庫中之連接資訊的強式檔案 (.snk)。</span><span class="sxs-lookup"><span data-stu-id="04c06-231">Select the strong file (.snk) that has the backup copy of the symmetric key used to decrypt stored credentials and connection information in the report server database.</span></span>

13. <span data-ttu-id="04c06-232">輸入密碼，並按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="04c06-232">Enter the password and click **OK**.</span></span>

14. <span data-ttu-id="04c06-233">按一下 **[報表管理員 URL]**。</span><span class="sxs-lookup"><span data-stu-id="04c06-233">Click **Report Manager URL**.</span></span>

15. <span data-ttu-id="04c06-234">按一下此連結，開啟報表管理員。</span><span class="sxs-lookup"><span data-stu-id="04c06-234">Click the link to open Report Manager.</span></span> <span data-ttu-id="04c06-235">您應該可從報表伺服器資料庫中看到報表伺服器項目。</span><span class="sxs-lookup"><span data-stu-id="04c06-235">You should see the report server items from the report server database.</span></span>

## <a name="see-also"></a><span data-ttu-id="04c06-236">另請參閱</span><span class="sxs-lookup"><span data-stu-id="04c06-236">See Also</span></span>
 <span data-ttu-id="04c06-237">將[報表伺服器資料庫移至另一部電腦 &#40;SSRS 原生模式&#41;](../report-server/moving-the-report-server-databases-to-another-computer-ssrs-native-mode.md) [Reporting Services 組態管理員 &#40;原生模式&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md) [建立原生模式報表伺服器資料庫 &#40;SSRS Configuration Manager&#41;](../install-windows/ssrs-report-server-create-a-native-mode-report-server-database.md) [備份和還原 Reporting Services 加密金鑰](../install-windows/ssrs-encryption-keys-back-up-and-restore-encryption-keys.md)</span><span class="sxs-lookup"><span data-stu-id="04c06-237">[Moving the Report Server Databases to Another Computer &#40;SSRS Native Mode&#41;](../report-server/moving-the-report-server-databases-to-another-computer-ssrs-native-mode.md) [Reporting Services Configuration Manager &#40;Native Mode&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md) [Create a Native Mode Report Server Database  &#40;SSRS Configuration Manager&#41;](../install-windows/ssrs-report-server-create-a-native-mode-report-server-database.md) [Back Up and Restore Reporting Services Encryption Keys](../install-windows/ssrs-encryption-keys-back-up-and-restore-encryption-keys.md)</span></span>


