---
title: 建立 Analysis Services 作業步驟 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- job steps [Analysis Services]
ms.assetid: 03d4bb86-514b-4a55-97b9-c2c0fa08b428
author: stevestein
ms.author: sstein
ms.openlocfilehash: ed0e63c22d4cad270bcb544b03decba269e4f43a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699262"
---
# <a name="create-an-analysis-services-job-step"></a><span data-ttu-id="25c6a-102">Create an Analysis Services Job Step</span><span class="sxs-lookup"><span data-stu-id="25c6a-102">Create an Analysis Services Job Step</span></span>
  <span data-ttu-id="25c6a-103">此主題描述如何使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 SQL Server 管理物件，在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中建立和定義執行 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]Analysis Services 命令與查詢的 [!INCLUDE[tsql](../../includes/tsql-md.md)] Agent 作業步驟。</span><span class="sxs-lookup"><span data-stu-id="25c6a-103">This topic describes how to create and define [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job steps in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] that execute [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Analysis Services commands and queries by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)] or SQL Server Management Objects.</span></span>  
  
-   <span data-ttu-id="25c6a-104">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="25c6a-104">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="25c6a-105">限制事項</span><span class="sxs-lookup"><span data-stu-id="25c6a-105">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="25c6a-106">安全性</span><span class="sxs-lookup"><span data-stu-id="25c6a-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="25c6a-107">**若要透過下列項目，建立使用 Analysis Services 命令和/或查詢的 SQL Server 作業步驟：**</span><span class="sxs-lookup"><span data-stu-id="25c6a-107">**To create a SQL Server job steps using Analysis Services commands and/or queries, with:**</span></span>  
  
     [<span data-ttu-id="25c6a-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="25c6a-108">SQL Server Management Studio</span></span>](#SSMS)  
  
     [<span data-ttu-id="25c6a-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="25c6a-109">Transact-SQL</span></span>](#TSQL)  
  
     [<span data-ttu-id="25c6a-110">SQL Server 管理物件</span><span class="sxs-lookup"><span data-stu-id="25c6a-110">SQL Server Management Objects</span></span>](#SMO)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="25c6a-111">開始之前</span><span class="sxs-lookup"><span data-stu-id="25c6a-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="25c6a-112">限制事項</span><span class="sxs-lookup"><span data-stu-id="25c6a-112">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="25c6a-113">如果作業步驟使用 Analysis Services 命令，命令陳述式必須是 XML for Analysis Services **Execute** 方法。</span><span class="sxs-lookup"><span data-stu-id="25c6a-113">If the job step uses an Analysis Services command, the command statement must be an XML for Analysis Services **Execute** method.</span></span> <span data-ttu-id="25c6a-114">此陳述式可能不包含完整的簡易物件存取通訊協定 (SOAP) Envelope 或 XML for Analysis **Discover** 方法。</span><span class="sxs-lookup"><span data-stu-id="25c6a-114">The statement may not contain a complete Simple Object Access Protocol (SOAP) envelope or an XML for Analysis **Discover** method.</span></span> <span data-ttu-id="25c6a-115">雖然 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 支援完整的 SOAP Envelope 與 **Discover** 方法，但是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 作業步驟則不支援。</span><span class="sxs-lookup"><span data-stu-id="25c6a-115">While [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] supports complete SOAP envelopes and the **Discover** method, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job steps do not.</span></span> <span data-ttu-id="25c6a-116">如需有關 XML for Analysis Services 的詳細資訊，請參閱 [XML for Analysis 概觀 (XMLA)](https://msdn.microsoft.com/library/ms187190.aspx)。</span><span class="sxs-lookup"><span data-stu-id="25c6a-116">For more information about XML for Analysis Services, see [XML for Analysis Overview (XMLA)](https://msdn.microsoft.com/library/ms187190.aspx).</span></span>  
  
-   <span data-ttu-id="25c6a-117">如果作業步驟使用 Analysis Services 查詢，查詢陳述式必須是多維度運算式 (MDX) 查詢。</span><span class="sxs-lookup"><span data-stu-id="25c6a-117">If the job step uses an Analysis Services query, the query statement must be a multidimensional expressions (MDX) query.</span></span> <span data-ttu-id="25c6a-118">如需 MDX 的詳細資訊，請參閱[Mdx 查詢基本概念 &#40;Analysis Services&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/mdx/mdx-query-fundamentals-analysis-services)。</span><span class="sxs-lookup"><span data-stu-id="25c6a-118">For more information about MDX, see [MDX Query Fundamentals &#40;Analysis Services&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/mdx/mdx-query-fundamentals-analysis-services).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="25c6a-119">Security</span><span class="sxs-lookup"><span data-stu-id="25c6a-119">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="25c6a-120">權限</span><span class="sxs-lookup"><span data-stu-id="25c6a-120">Permissions</span></span>  
  
-   <span data-ttu-id="25c6a-121">若要執行使用 Analysis Services 子系統的作業步驟，使用者必須是 **系統管理員 (sysadmin)** 固定伺服器角色的成員，或具有已定義能使用此子系統之有效 Proxy 帳戶的存取權。</span><span class="sxs-lookup"><span data-stu-id="25c6a-121">To run a job step that uses the Analysis Services subsystem, a user must be a member of the **sysadmin** fixed server role or have access to a valid proxy account defined to use this subsystem.</span></span> <span data-ttu-id="25c6a-122">此外， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 服務帳戶或 Proxy 必須是 Analysis Services 管理員，且必須是有效的 Windows 網域帳戶。</span><span class="sxs-lookup"><span data-stu-id="25c6a-122">In addition, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service account or the proxy must be an Analysis Services administrator and a valid Windows domain account.</span></span>  
  
-   <span data-ttu-id="25c6a-123">只有 **系統管理員 (sysadmin)** 固定伺服器角色的成員可以將作業步驟輸出寫入檔案。</span><span class="sxs-lookup"><span data-stu-id="25c6a-123">Only members of the **sysadmin** fixed server role can write job step output to a file.</span></span> <span data-ttu-id="25c6a-124">若作業步驟是由屬於 **msdb** 資料庫之 **SQLAgentUserRole** 資料庫角色 的使用者執行，則輸出只能寫入一個資料表。</span><span class="sxs-lookup"><span data-stu-id="25c6a-124">If the job step is run by users who are members of the **SQLAgentUserRole** database role in the **msdb** database, then the output can be written only to a table.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="25c6a-125">Agent 會將作業步驟輸出寫入**msdb**資料庫中的**sysjobstepslog**資料表。</span><span class="sxs-lookup"><span data-stu-id="25c6a-125">Agent writes job step output to the **sysjobstepslog** table in the **msdb** database.</span></span>  
  
-   <span data-ttu-id="25c6a-126">如需詳細資訊，請參閱＜ [實作 SQL Server Agent 安全性](implement-sql-server-agent-security.md)＞。</span><span class="sxs-lookup"><span data-stu-id="25c6a-126">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="25c6a-127">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="25c6a-127">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-an-analysis-services-command-job-step"></a><span data-ttu-id="25c6a-128">若要建立 Analysis Services 命令作業步驟</span><span class="sxs-lookup"><span data-stu-id="25c6a-128">To create an Analysis Services command job step</span></span>  
  
1.  <span data-ttu-id="25c6a-129">在**物件總管中，** 連接到的實例 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] ，然後展開該實例。</span><span class="sxs-lookup"><span data-stu-id="25c6a-129">In **Object Explorer,** connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="25c6a-130">展開 **SQL Server Agent**，建立新作業或以滑鼠右鍵按一下現有作業，然後按一下 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="25c6a-130">Expand **SQL Server Agent**, create a new job or right-click an existing job, and then click **Properties**.</span></span> <span data-ttu-id="25c6a-131">如需建立作業的詳細資訊，請參閱 [建立作業](create-jobs.md)。</span><span class="sxs-lookup"><span data-stu-id="25c6a-131">For more information on creating a job, see [Create Jobs](create-jobs.md).</span></span>  
  
3.  <span data-ttu-id="25c6a-132">在 **[作業屬性]** 對話方塊中，按一下 **[步驟]** 頁面，然後按一下 **[新增]**。</span><span class="sxs-lookup"><span data-stu-id="25c6a-132">In the **Job Properties** dialog box, click the **Steps** page, and then click **New**.</span></span>  
  
4.  <span data-ttu-id="25c6a-133">在 **[新增作業步驟]** 對話方塊中，輸入作業 **步驟名稱**。</span><span class="sxs-lookup"><span data-stu-id="25c6a-133">In the **New Job Step** dialog box, type a job **Step name**.</span></span>  
  
5.  <span data-ttu-id="25c6a-134">在 **[類型]** 清單中，按一下 **[SQL Server Analysis Services 命令]**。</span><span class="sxs-lookup"><span data-stu-id="25c6a-134">In the **Type** list, click **SQL Server Analysis Services Command**.</span></span>  
  
6.  <span data-ttu-id="25c6a-135">在 **[執行身分]** 清單中，選取已定義為使用「Analysis Services 命令」子系統的 Proxy。</span><span class="sxs-lookup"><span data-stu-id="25c6a-135">In the **Run as** list, select a proxy that has been defined to use the Analysis Services Command subsystem.</span></span> <span data-ttu-id="25c6a-136">身為 **系統管理員 (sysadmin)** 固定伺服器角色成員的使用者，也可以選取 **[SQL 代理程式服務帳戶]** 來執行這個作業步驟。</span><span class="sxs-lookup"><span data-stu-id="25c6a-136">A user who is a member of the **sysadmin** fixed server role can also select **SQL Agent Service Account** to run this job step.</span></span>  
  
7.  <span data-ttu-id="25c6a-137">選取將執行作業步驟的 **伺服器** ，或輸入伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="25c6a-137">Select the **Server** where the job step will run, or type the server name.</span></span>  
  
8.  <span data-ttu-id="25c6a-138">在 **[命令]** 方塊中，輸入要執行的陳述式，或按一下 **[開啟]** 選取陳述式。</span><span class="sxs-lookup"><span data-stu-id="25c6a-138">In the **Command** box, type the statement to execute, or click **Open** to select a statement.</span></span>  
  
9. <span data-ttu-id="25c6a-139">按一下 **[進階]** 頁面以定義這個作業步驟的選項，例如在作業步驟成功或失敗時， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 所該採取的行動、應該嘗試作業步驟多少次，以及應該在何處寫入作業步驟輸出。</span><span class="sxs-lookup"><span data-stu-id="25c6a-139">Click the **Advanced** page to define options for this job step, such as what action [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent should take if the job step succeeds or fails, how many times the job step should be attempted, and where the job step output should be written.</span></span>  
  
#### <a name="to-create-an-analysis-services-query-job-step"></a><span data-ttu-id="25c6a-140">若要建立 Analysis Services 查詢作業步驟</span><span class="sxs-lookup"><span data-stu-id="25c6a-140">To create an Analysis Services query job step</span></span>  
  
1.  <span data-ttu-id="25c6a-141">在**物件總管中，** 連接到的實例 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] ，然後展開該實例。</span><span class="sxs-lookup"><span data-stu-id="25c6a-141">In **Object Explorer,** connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="25c6a-142">展開 **SQL Server Agent**，建立新作業或以滑鼠右鍵按一下現有作業，然後按一下 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="25c6a-142">Expand **SQL Server Agent**, create a new job or right-click an existing job, and then click **Properties**.</span></span> <span data-ttu-id="25c6a-143">如需建立作業的詳細資訊，請參閱 [建立作業](create-jobs.md)。</span><span class="sxs-lookup"><span data-stu-id="25c6a-143">For more information on creating a job, see [Create Jobs](create-jobs.md).</span></span>  
  
3.  <span data-ttu-id="25c6a-144">在 **[作業屬性]** 方塊中，按一下 **[步驟]** 頁面，然後按一下 **[新增]**。</span><span class="sxs-lookup"><span data-stu-id="25c6a-144">In the **Job Properties** dialog, click the **Steps** page, and then click **New**.</span></span>  
  
4.  <span data-ttu-id="25c6a-145">在 **[新增作業步驟]** 對話方塊中，輸入一個作業 **步驟名稱**。</span><span class="sxs-lookup"><span data-stu-id="25c6a-145">In the **New Job Step** dialog, type a job **Step name**.</span></span>  
  
5.  <span data-ttu-id="25c6a-146">在 **[類型]** 清單中，按一下 **[SQL Server Analysis Services 查詢]**。</span><span class="sxs-lookup"><span data-stu-id="25c6a-146">In the **Type** list, click **SQL Server Analysis Services Query**.</span></span>  
  
6.  <span data-ttu-id="25c6a-147">在 **[執行身分]** 清單中，選取已定義為使用「Analysis Services 查詢」子系統的 Proxy。</span><span class="sxs-lookup"><span data-stu-id="25c6a-147">In the **Run as** list, select a proxy that has been defined to use the Analysis Services Query subsystem.</span></span> <span data-ttu-id="25c6a-148">身為 **系統管理員 (sysadmin)** 固定伺服器角色成員的使用者，也可以選取 **[SQL 代理程式服務帳戶]** 來執行這個作業步驟。</span><span class="sxs-lookup"><span data-stu-id="25c6a-148">A user who is a member of the **sysadmin** fixed server role can also select **SQL Agent Service Account** to run this job step.</span></span>  
  
7.  <span data-ttu-id="25c6a-149">選取將執行作業步驟的 **伺服器** 與 **資料庫** ，或輸入伺服器或資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="25c6a-149">Select the **Server** and the **Database** where the job step will run, or type the server or database name.</span></span>  
  
8.  <span data-ttu-id="25c6a-150">在 **[命令]** 方塊中，輸入要執行的陳述式，或按一下 **[開啟]** 選取陳述式。</span><span class="sxs-lookup"><span data-stu-id="25c6a-150">In the **Command** box, type the statement to execute, or click **Open** to select a statement.</span></span>  
  
9. <span data-ttu-id="25c6a-151">按一下 **[進階]** 頁面以定義這個作業步驟的選項，例如在作業步驟成功或失敗時， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 所該採取的行動、應該嘗試作業步驟多少次，以及應該在何處寫入作業步驟輸出。</span><span class="sxs-lookup"><span data-stu-id="25c6a-151">Click the **Advanced** page to define options for this job step, such as what action [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent should take if the job step succeeds or fails, how many times the job step should be attempted, and where the job step output should be written.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> <span data-ttu-id="25c6a-152">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="25c6a-152">Using Transact-SQL</span></span>  
  
#### <a name="to-create-an-analysis-services-command-job-step"></a><span data-ttu-id="25c6a-153">若要建立 Analysis Services 命令作業步驟</span><span class="sxs-lookup"><span data-stu-id="25c6a-153">To create an Analysis Services command job step</span></span>  
  
1.  <span data-ttu-id="25c6a-154">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="25c6a-154">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="25c6a-155">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="25c6a-155">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="25c6a-156">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="25c6a-156">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```sql
    -- Creates a job step that uses XMLA to create a relational data source that references the AdventureWorks2012 Microsoft SQL Server database  
    USE msdb;  
    GO  
    EXEC sp_add_jobstep  
        @job_name = N'Weekly Sales Data Backup',  
        @step_name = N'Create a relational data source that references the AdventureWorks2012 Microsoft SQL Server database ',  
        @subsystem = N'ANALYSISCOMMAND',  
        @command = N' <Create xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">  
        <ParentObject>  
            <DatabaseID>AdventureWorks2012</DatabaseID>  
        </ParentObject>  
        <ObjectDefinition>  
            <DataSource xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:type="RelationalDataSource">  
                <ID>AdventureWorks2012</ID>  
                <Name>Adventure Works 2012</Name>  
                <ConnectionString>Data Source=localhost;Initial Catalog=AdventureWorks2012;Integrated Security=True</ConnectionString>  
                <ImpersonationInfo>  
                    <ImpersonationMode>ImpersonateServiceAccount</ImpersonationMode>  
                </ImpersonationInfo>  
                <ManagedProvider>System.Data.SqlClient</ManagedProvider>  
                <Timeout>PT0S</Timeout>  
            </DataSource>  
        </ObjectDefinition>  
    </Create>', ;  
    GO  
    ```  
  
 <span data-ttu-id="25c6a-157">如需詳細資訊，請參閱[sp_add_jobstep &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="25c6a-157">For more information, see [sp_add_jobstep &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql).</span></span>  
  
#### <a name="to-create-an-analysis-services-query-job-step"></a><span data-ttu-id="25c6a-158">若要建立 Analysis Services 查詢作業步驟</span><span class="sxs-lookup"><span data-stu-id="25c6a-158">To create an Analysis Services query job step</span></span>  
  
1.  <span data-ttu-id="25c6a-159">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="25c6a-159">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="25c6a-160">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="25c6a-160">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="25c6a-161">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="25c6a-161">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```sql
    -- Creates a job step that uses MDX to return data  
    USE msdb;  
    GO  
    EXEC sp_add_jobstep  
        @job_name = N'Weekly Sales Data Backup',  
        @step_name = N'Returns the Internet sales amount by state',  
        @subsystem = N'ANALYSISQUERY',  
        @command = N' SELECT  
       [Measures].[Internet Sales Amount] ON COLUMNS,  
       [Customer].[State-Province].Members ON ROWS  
    FROM [AdventureWorks2012]',   
        @retry_attempts = 5,  
        @retry_interval = 5 ;  
    GO  
    ```  
  
 <span data-ttu-id="25c6a-162">如需詳細資訊，請參閱[sp_add_jobstep &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="25c6a-162">For more information, see [sp_add_jobstep &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql).</span></span>  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a><span data-ttu-id="25c6a-163">使用 SQL Server 管理物件</span><span class="sxs-lookup"><span data-stu-id="25c6a-163">Using SQL Server Management Objects</span></span>  
 <span data-ttu-id="25c6a-164">**建立 PowerShell 指令碼作業步驟**</span><span class="sxs-lookup"><span data-stu-id="25c6a-164">**To create a PowerShell Script job step**</span></span>  
  
 <span data-ttu-id="25c6a-165">透過所選的程式語言，例如 XMLA 或 MDX，使用 `JobStep` 類別。</span><span class="sxs-lookup"><span data-stu-id="25c6a-165">Use the `JobStep` class by using a programming language that you choose, such as XMLA or MDX.</span></span> <span data-ttu-id="25c6a-166">如需詳細資訊，請參閱 [SQL Server 管理物件 (SMO)](https://msdn.microsoft.com/library/ms162169.aspx)。</span><span class="sxs-lookup"><span data-stu-id="25c6a-166">For more information, see [SQL Server Management Objects (SMO)](https://msdn.microsoft.com/library/ms162169.aspx).</span></span>  
