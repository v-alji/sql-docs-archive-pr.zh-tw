---
title: IBM DB2 訂閱者 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- non-SQL Server Subscribers, IBM DB2
- data types [SQL Server replication], non-SQL Server Subscribers
- IBM DB2 Subscribers
- mapping data types [SQL Server replication]
- heterogeneous Subscribers, IBM DB2
ms.assetid: a1a27b1e-45dd-4d7d-b6c0-2b608ed175f6
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 54263e75c0f4c7da7c6d9c24ea499c202372aa64
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702782"
---
# <a name="ibm-db2-subscribers"></a><span data-ttu-id="c3156-102">IBM DB2 訂閱者</span><span class="sxs-lookup"><span data-stu-id="c3156-102">IBM DB2 Subscribers</span></span>
  <span data-ttu-id="c3156-103">透過[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Host Integration Server 所含的 OLE DB 提供者， [!INCLUDE[msCoName](../../../includes/msconame-md.md)] 支援向 IBM DB2/AS 400、DB2/MVS 和 DB2/Universal Database 的提取訂閱。</span><span class="sxs-lookup"><span data-stu-id="c3156-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] supports push subscriptions to IBM DB2/AS 400, DB2/MVS, and DB2/Universal Database through the OLE DB providers that are included with [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Host Integration Server.</span></span>  
  
## <a name="configuring-an-ibm-db2-subscriber"></a><span data-ttu-id="c3156-104">設定 IBM DB2 訂閱者</span><span class="sxs-lookup"><span data-stu-id="c3156-104">Configuring an IBM DB2 Subscriber</span></span>  
 <span data-ttu-id="c3156-105">若要設定「IBM DB2 訂閱者」，請遵循下列步驟：</span><span class="sxs-lookup"><span data-stu-id="c3156-105">To configure an IBM DB2 Subscriber, follow these steps:</span></span>  
  
1.  <span data-ttu-id="c3156-106">在散發者上安裝 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] OLE DB Provider for DB2 的最新版本：</span><span class="sxs-lookup"><span data-stu-id="c3156-106">Install the latest version of the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] OLE DB Provider for DB2 on the Distributor:</span></span>  
  
    -   <span data-ttu-id="c3156-107">如果您使用的是 [!INCLUDE[ssEnterpriseEd11](../../../includes/ssenterpriseed11-md.md)]，請在 [SQL Server 2008 下載](https://go.microsoft.com/fwlink/?LinkId=149256) 網頁的 **[Related Downloads] (相關下載)** 區段中，按一下最新版 Microsoft SQL Server 2008 功能套件的連結。</span><span class="sxs-lookup"><span data-stu-id="c3156-107">If you are using [!INCLUDE[ssEnterpriseEd11](../../../includes/ssenterpriseed11-md.md)], on the [SQL Server 2008 Downloads](https://go.microsoft.com/fwlink/?LinkId=149256) Web page, in the **Related Downloads** section, click the link to the latest version of the Microsoft SQL Server 2008 Feature Pack.</span></span> <span data-ttu-id="c3156-108">在 **[Microsoft SQL Server 2008 Feature Pack]** 網頁上，搜尋 **[Microsoft OLE DB Provider for DB2]**。</span><span class="sxs-lookup"><span data-stu-id="c3156-108">On the **Microsoft SQL Server 2008 Feature Pack** Web page, search for **Microsoft OLE DB Provider for DB2**.</span></span>  
  
    -   <span data-ttu-id="c3156-109">如果您使用的是 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] Standard，請安裝 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Host [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] (HIS) 伺服器的最新版本，其中就包含此提供者。</span><span class="sxs-lookup"><span data-stu-id="c3156-109">If you are using [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] Standard, install the latest version of the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Host [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] (HIS) server, which includes the provider.</span></span>  
  
     <span data-ttu-id="c3156-110">除了安裝提供者外，建議您同時安裝「資料存取工具」，該工具將在下一步中用到 (依預設，它會隨 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] Enterprise 的下載一起安裝)。</span><span class="sxs-lookup"><span data-stu-id="c3156-110">In addition to installing the provider, we recommend that you install the Data Access Tool, which is used in the next step (it is installed by default with the download for [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] Enterprise).</span></span> <span data-ttu-id="c3156-111">如需有關安裝和使用「資料存取工具」的詳細資料，請參閱提供者文件集或 HIS 文件集。</span><span class="sxs-lookup"><span data-stu-id="c3156-111">For more information about installing and using the Data Access Tool, see the provider documentation or the HIS documentation.</span></span>  
  
2.  <span data-ttu-id="c3156-112">為「訂閱者」建立連接字串。</span><span class="sxs-lookup"><span data-stu-id="c3156-112">Create a connection string for the Subscriber.</span></span> <span data-ttu-id="c3156-113">在任何文字編輯器中都可建立連接字串，但建議您使用「資料存取工具」。</span><span class="sxs-lookup"><span data-stu-id="c3156-113">The connection string can be created in any text editor, but we recommend that you use the Data Access Tool.</span></span> <span data-ttu-id="c3156-114">若要在「資料存取工具」中建立字串：</span><span class="sxs-lookup"><span data-stu-id="c3156-114">To create the string in the Data Access Tool:</span></span>  
  
    1.  <span data-ttu-id="c3156-115">依序按一下 **[開始]** 、 **[程式集]** 和 **[DB2 的 Microsoft OLE DB 提供者]** ，然後再按 **[資料存取工具]** 。</span><span class="sxs-lookup"><span data-stu-id="c3156-115">Click **Start**, **Programs**, **Microsoft OLE DB Provider for DB2**, and then **Data Access Tool**.</span></span>  
  
    2.  <span data-ttu-id="c3156-116">遵循 **[資料存取工具]** 中的步驟提供有關 DB2 伺服器的資訊。</span><span class="sxs-lookup"><span data-stu-id="c3156-116">In the **Data Access Tool**, follow the steps to provide information about the DB2 server.</span></span> <span data-ttu-id="c3156-117">完成工具後，將建立通用資料連結 (UDL) 和相關聯的連接字串 (複寫實際不會使用 UDL，但會用到連接字串)。</span><span class="sxs-lookup"><span data-stu-id="c3156-117">When you complete the tool, a universal data link (UDL) is created with an associated connection string (the UDL is not actually used by replication, but the connection string is).</span></span>  
  
    3.  <span data-ttu-id="c3156-118">存取連接字串：以滑鼠右鍵按一下「資料存取工具」中的 UDL，然後選取 **[顯示連接字串]** 。</span><span class="sxs-lookup"><span data-stu-id="c3156-118">Access the connection string: right-click the UDL in the Data Access Tool and select **Display Connection String**.</span></span>  
  
     <span data-ttu-id="c3156-119">連接字串類似於 (使用分行符號是為提高可讀性)：</span><span class="sxs-lookup"><span data-stu-id="c3156-119">The connection string will be similar to (line breaks are for readability):</span></span>  
  
    ```  
    Provider=DB2OLEDB;Initial Catalog=MY_SUBSCRIBER_DB;Network Transport Library=TCP;Host CCSID=1252;  
    PC Code Page=1252;Network Address=MY_SUBSCRIBER;Network Port=50000;Package Collection=MY_PKGCOL;  
    Default Schema=MY_SCHEMA;Process Binary as Character=False;Units of Work=RUW;DBMS Platform=DB2/NT;  
    Persist Security Info=False;Connection Pooling=True;  
    ```  
  
     <span data-ttu-id="c3156-120">字串中的大多數選項是您設定之 DB2 伺服器的專用選項，但 `Process Binary as Character` 選項，應一律設定為 `False`。</span><span class="sxs-lookup"><span data-stu-id="c3156-120">Most of the options in the string are specific to the DB2 server you are configuring, but the `Process Binary as Character` option should always be set to `False`.</span></span> <span data-ttu-id="c3156-121">需要為 `Initial Catalog` 選項指定值，以便識別訂閱資料庫。</span><span class="sxs-lookup"><span data-stu-id="c3156-121">A value is required for the `Initial Catalog` option to identify the subscription database.</span></span> <span data-ttu-id="c3156-122">在您建立訂閱時，將在「新增訂閱精靈」中輸入連接字串。</span><span class="sxs-lookup"><span data-stu-id="c3156-122">The connection string will be entered in the New Subscription Wizard when you create the subscription.</span></span>  
  
3.  <span data-ttu-id="c3156-123">建立快照集或交易式發行集，並為非[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 訂閱者啟用，然後再為訂閱者建立發送訂閱。</span><span class="sxs-lookup"><span data-stu-id="c3156-123">Create a snapshot or transactional publication, enable it for non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Subscribers, and then create a push subscription for the Subscriber.</span></span> <span data-ttu-id="c3156-124">如需相關資訊，請參閱 [為非 SQL Server 訂閱者建立訂閱](../create-a-subscription-for-a-non-sql-server-subscriber.md)。</span><span class="sxs-lookup"><span data-stu-id="c3156-124">For more information, see [Create a Subscription for a Non-SQL Server Subscriber](../create-a-subscription-for-a-non-sql-server-subscriber.md).</span></span>  
  
4.  <span data-ttu-id="c3156-125">可以選擇為一或多個發行項指定自訂建立指令碼。</span><span class="sxs-lookup"><span data-stu-id="c3156-125">Optionally, specify a custom creation script for one or more articles.</span></span> <span data-ttu-id="c3156-126">發行資料表時，將為該資料表建立一個 CREATE TABLE 指令碼。</span><span class="sxs-lookup"><span data-stu-id="c3156-126">When a table is published, a CREATE TABLE script is created for that table.</span></span> <span data-ttu-id="c3156-127">對於非[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 訂閱者，指令碼將以 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 用語建立，然後在套用到訂閱者端之前，透過散發代理程式將其翻譯為比較一般的 SQL 用語。</span><span class="sxs-lookup"><span data-stu-id="c3156-127">For non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Subscribers, the script is created in the [!INCLUDE[tsql](../../../includes/tsql-md.md)] dialect, and it is then translated to a more generic SQL dialect by the Distribution Agent before being applied at the Subscriber.</span></span> <span data-ttu-id="c3156-128">若要指定自訂的建立指令碼，請修改現有的 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 指令碼或建立使用 DB2 SQL 用語的完整指令碼；如果已建立 DB2 指令碼，請使用 **bypass_translation** 指示詞，好讓散發代理程式無需進行翻譯便可在訂閱者端套用指令碼。</span><span class="sxs-lookup"><span data-stu-id="c3156-128">To specify a custom creation script, either modify the existing [!INCLUDE[tsql](../../../includes/tsql-md.md)] script or create a complete script that uses the DB2 SQL dialect; if a DB2 script is created, use the **bypass_translation** directive so that the Distribution Agent will apply the script at the Subscriber without translation.</span></span>  
  
     <span data-ttu-id="c3156-129">有多種情況下會需要修改指令碼，但最常見的原因是改變資料類型對應。</span><span class="sxs-lookup"><span data-stu-id="c3156-129">Scripts can be modified for a number of reasons, but the most common reason is to alter data type mappings.</span></span> <span data-ttu-id="c3156-130">如需詳細資訊，請參閱本主題中的＜資料類型對應考量＞一節。</span><span class="sxs-lookup"><span data-stu-id="c3156-130">For more information, see the "Data Type Mapping Considerations" section in this topic.</span></span> <span data-ttu-id="c3156-131">如果您修改 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 指令碼，請將變更限制為資料類型對應變更 (且指令碼不應包含任何註解)。</span><span class="sxs-lookup"><span data-stu-id="c3156-131">If you modify the [!INCLUDE[tsql](../../../includes/tsql-md.md)] script, changes should be restricted to data type mapping changes (and the script should not contain any comments).</span></span> <span data-ttu-id="c3156-132">如果需要作大量變更，請建立 DB2 指令碼。</span><span class="sxs-lookup"><span data-stu-id="c3156-132">If more substantial changes are required, create a DB2 script.</span></span>  
  
     <span data-ttu-id="c3156-133">**若要修改發行項指令碼並做為自訂建立指令碼提供**</span><span class="sxs-lookup"><span data-stu-id="c3156-133">**To modify an article script and supply it as a custom creation script**</span></span>  
  
    1.  <span data-ttu-id="c3156-134">為發行集產生快照集後，瀏覽至發行集的快照集資料夾。</span><span class="sxs-lookup"><span data-stu-id="c3156-134">After the snapshot has been generated for the publication, navigate to the snapshot folder for the publication.</span></span>  
  
    2.  <span data-ttu-id="c3156-135">找到與發行項名稱相同的 .sch 檔案，例如 MyArticle.sch。</span><span class="sxs-lookup"><span data-stu-id="c3156-135">Locate the .sch file with the same name as the article, such as MyArticle.sch.</span></span>  
  
    3.  <span data-ttu-id="c3156-136">使用 [記事本] 或其他文字編輯器開啟此檔案。</span><span class="sxs-lookup"><span data-stu-id="c3156-136">Open this file using Notepad or another text editor.</span></span>  
  
    4.  <span data-ttu-id="c3156-137">修改檔案並將其儲存至其他目錄。</span><span class="sxs-lookup"><span data-stu-id="c3156-137">Modify the file and save it to a different directory.</span></span>  
  
    5.  <span data-ttu-id="c3156-138">執行 sp_changearticle，並指定 *creation_script* 屬性的檔案路徑與名稱。</span><span class="sxs-lookup"><span data-stu-id="c3156-138">Execute sp_changearticle, specifying the file path and name for the *creation_script* property.</span></span> <span data-ttu-id="c3156-139">如需詳細資訊，請參閱 [sp_changearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changearticle-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="c3156-139">For more information, see [sp_changearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changearticle-transact-sql).</span></span>  
  
     <span data-ttu-id="c3156-140">**若要建立發行項指令碼並做為自訂建立指令碼提供**</span><span class="sxs-lookup"><span data-stu-id="c3156-140">**To create an article script and supply it as a custom creation script**</span></span>  
  
    1.  <span data-ttu-id="c3156-141">使用 DB2 SQL 用語建立發行項指令碼。</span><span class="sxs-lookup"><span data-stu-id="c3156-141">Create an article script using the DB2 SQL dialect.</span></span> <span data-ttu-id="c3156-142">確定檔案的第一行為 **bypass_translation**，且該行上除此之外無其他內容。</span><span class="sxs-lookup"><span data-stu-id="c3156-142">Ensure the first line of the file is **bypass_translation**, with nothing else on the line.</span></span>  
  
    2.  <span data-ttu-id="c3156-143">執行 sp_changearticle，並指定 *creation_script* 屬性的檔案路徑與名稱。</span><span class="sxs-lookup"><span data-stu-id="c3156-143">Execute sp_changearticle, specifying the file path and name for the *creation_script* property.</span></span>  
  
## <a name="considerations-for-ibm-db2-subscribers"></a><span data-ttu-id="c3156-144">IBM DB2 訂閱者考量</span><span class="sxs-lookup"><span data-stu-id="c3156-144">Considerations for IBM DB2 Subscribers</span></span>  
 <span data-ttu-id="c3156-145">複寫至「DB2 訂閱者」時，除了＜ [Non-SQL Server Subscribers](non-sql-server-subscribers.md)＞主題中涵蓋的考量外，還需考慮以下幾個問題：</span><span class="sxs-lookup"><span data-stu-id="c3156-145">In addition to the considerations covered in the topic [Non-SQL Server Subscribers](non-sql-server-subscribers.md), consider the following issues when replicating to DB2 Subscribers:</span></span>  
  
-   <span data-ttu-id="c3156-146">每個已複寫資料表的資料與索引將指定給 DB2 資料表空間。</span><span class="sxs-lookup"><span data-stu-id="c3156-146">The data and indexes for each replicated table are assigned to a DB2 tablespace.</span></span> <span data-ttu-id="c3156-147">DB2 資料表空間的頁面大小，控制資料表空間所屬資料表的最大資料行行數以及最大資料列大小。</span><span class="sxs-lookup"><span data-stu-id="c3156-147">The page size of a DB2 tablespace controls the maximum number of columns and the maximum row size of the tables belonging to the tablespace.</span></span> <span data-ttu-id="c3156-148">根據複寫的資料行數與資料表的最大資料列大小，確定與複寫資料表相關聯的資料表空間是否適當。</span><span class="sxs-lookup"><span data-stu-id="c3156-148">Ensure that the tablespace associated with replicated tables is appropriate based on the number of replicated columns and the maximum row size of the tables.</span></span>  
  
-   <span data-ttu-id="c3156-149">如果資料表中一或多個主索引鍵資料行的資料類型為 DECIMAL(32-38, 0-38) 或 NUMERIC(32-38, 0-38)，則不要使用異動複寫將資料表發行至「DB2 訂閱者」。</span><span class="sxs-lookup"><span data-stu-id="c3156-149">Do not publish tables to DB2 Subscribers using transactional replication if one or more primary key columns in the table is of data type DECIMAL(32-38, 0-38) or NUMERIC(32-38, 0-38).</span></span> <span data-ttu-id="c3156-150">異動複寫使用主索引鍵識別資料列；這可能會導致失敗，因為這些資料類型對應至「訂閱者」端的 VARCHAR(41)。</span><span class="sxs-lookup"><span data-stu-id="c3156-150">Transactional replication identifies rows using the primary key; this can result in failures because these data types are mapped to VARCHAR(41) at the Subscriber.</span></span> <span data-ttu-id="c3156-151">含有可使用這些資料類型之主索引鍵的資料表可以使用快照式複寫加以發行。</span><span class="sxs-lookup"><span data-stu-id="c3156-151">Tables with primary keys that use these data types can be published using snapshot replication.</span></span>  
  
-   <span data-ttu-id="c3156-152">如果您要在「訂閱者」端預先建立資料表，請不要由複寫來建立，而是使用僅支援複寫選項。</span><span class="sxs-lookup"><span data-stu-id="c3156-152">If you want to pre-create tables at the Subscriber, rather than having replication create them, use the replication support only option.</span></span> <span data-ttu-id="c3156-153">如需詳細資訊，請參閱 [不使用快照集初始化交易式訂閱](../initialize-a-transactional-subscription-without-a-snapshot.md)中手動初始化訂閱。</span><span class="sxs-lookup"><span data-stu-id="c3156-153">For more information, see [Initialize a Transactional Subscription Without a Snapshot](../initialize-a-transactional-subscription-without-a-snapshot.md).</span></span>  
  
-   <span data-ttu-id="c3156-154">相對於 DB2，[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 允許使用更長的資料表名稱和資料行名稱：</span><span class="sxs-lookup"><span data-stu-id="c3156-154">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] allows longer table names and column names than DB2:</span></span>  
  
    -   <span data-ttu-id="c3156-155">如果發行集資料庫中的資料表名稱比「訂閱者」端 DB2 版本支援的資料表名稱長，請為 destination_table 發行項屬性指定替代名稱。</span><span class="sxs-lookup"><span data-stu-id="c3156-155">If the publication database includes tables with names longer than those supported on the DB2 version at the Subscriber, specify an alternative name for the destination_table article property.</span></span> <span data-ttu-id="c3156-156">如需在建立發行集時設定屬性的詳細資訊，請參閱[建立發行集](../publish/create-a-publication.md)和[定義發行項](../publish/define-an-article.md)。</span><span class="sxs-lookup"><span data-stu-id="c3156-156">For more information about setting properties when creating a publication, see [Create a Publication](../publish/create-a-publication.md) and [Define an Article](../publish/define-an-article.md).</span></span>  
  
    -   <span data-ttu-id="c3156-157">不可能指定替代資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="c3156-157">It is not possible to specify alternative column names.</span></span> <span data-ttu-id="c3156-158">您必須確定已發行資料表中的資料行名稱比「訂閱者」端 DB2 版本支援的那些資料行名稱短。</span><span class="sxs-lookup"><span data-stu-id="c3156-158">You must ensure that published tables do not include column names longer than those supported on the DB2 version at the Subscriber.</span></span>  
  
## <a name="mapping-data-types-from-sql-server-to-ibm-db2"></a><span data-ttu-id="c3156-159">從 SQL Server 到 IBM DB2 的資料類型對應</span><span class="sxs-lookup"><span data-stu-id="c3156-159">Mapping Data Types from SQL Server to IBM DB2</span></span>  
 <span data-ttu-id="c3156-160">下表顯示了將資料複寫到執行 IBM DB2 的「訂閱者」時所使用的資料類型對應。</span><span class="sxs-lookup"><span data-stu-id="c3156-160">The following table shows the data type mappings that are used when data is replicated to a Subscriber running IBM DB2.</span></span>  
  
|<span data-ttu-id="c3156-161">SQL Server 資料類型</span><span class="sxs-lookup"><span data-stu-id="c3156-161">SQL Server data type</span></span>|<span data-ttu-id="c3156-162">IBM DB2 資料類型</span><span class="sxs-lookup"><span data-stu-id="c3156-162">IBM DB2 data type</span></span>|  
|--------------------------|-----------------------|  
|`bigint`|<span data-ttu-id="c3156-163">DECIMAL(19,0)</span><span class="sxs-lookup"><span data-stu-id="c3156-163">DECIMAL(19,0)</span></span>|  
|`binary(1-254)`|<span data-ttu-id="c3156-164">CHAR(1-254) FOR BIT DATA</span><span class="sxs-lookup"><span data-stu-id="c3156-164">CHAR(1-254) FOR BIT DATA</span></span>|  
|`binary(255-8000)`|<span data-ttu-id="c3156-165">VARCHAR(255-8000) FOR BIT DATA</span><span class="sxs-lookup"><span data-stu-id="c3156-165">VARCHAR(255-8000) FOR BIT DATA</span></span>|  
|`bit`|<span data-ttu-id="c3156-166">SMALLINT</span><span class="sxs-lookup"><span data-stu-id="c3156-166">SMALLINT</span></span>|  
|`char(1-254)`|<span data-ttu-id="c3156-167">CHAR(1-254)</span><span class="sxs-lookup"><span data-stu-id="c3156-167">CHAR(1-254)</span></span>|  
|`char(255-8000)`|<span data-ttu-id="c3156-168">VARCHAR(255-8000)</span><span class="sxs-lookup"><span data-stu-id="c3156-168">VARCHAR(255-8000)</span></span>|  
|`date`|<span data-ttu-id="c3156-169">日期</span><span class="sxs-lookup"><span data-stu-id="c3156-169">DATE</span></span>|  
|`datetime`|<span data-ttu-id="c3156-170">timestamp</span><span class="sxs-lookup"><span data-stu-id="c3156-170">TIMESTAMP</span></span>|  
|`datetime2(0-7)`|<span data-ttu-id="c3156-171">VARCHAR(27)</span><span class="sxs-lookup"><span data-stu-id="c3156-171">VARCHAR(27)</span></span>|  
|`datetimeoffset(0-7)`|<span data-ttu-id="c3156-172">VARCHAR(34)</span><span class="sxs-lookup"><span data-stu-id="c3156-172">VARCHAR(34)</span></span>|  
|`decimal(1-31, 0-31)`|<span data-ttu-id="c3156-173">DECIMAL(1-31, 0-31)</span><span class="sxs-lookup"><span data-stu-id="c3156-173">DECIMAL(1-31, 0-31)</span></span>|  
|`decimal(32-38, 0-38)`|<span data-ttu-id="c3156-174">VARCHAR(41)</span><span class="sxs-lookup"><span data-stu-id="c3156-174">VARCHAR(41)</span></span>|  
|`float(53)`|<span data-ttu-id="c3156-175">DOUBLE</span><span class="sxs-lookup"><span data-stu-id="c3156-175">DOUBLE</span></span>|  
|`float`|<span data-ttu-id="c3156-176">FLOAT</span><span class="sxs-lookup"><span data-stu-id="c3156-176">FLOAT</span></span>|  
|`geography`|<span data-ttu-id="c3156-177">影像</span><span class="sxs-lookup"><span data-stu-id="c3156-177">IMAGE</span></span>|  
|`geometry`|<span data-ttu-id="c3156-178">影像</span><span class="sxs-lookup"><span data-stu-id="c3156-178">IMAGE</span></span>|  
|`hierarchyid`|<span data-ttu-id="c3156-179">影像</span><span class="sxs-lookup"><span data-stu-id="c3156-179">IMAGE</span></span>|  
|`image`|<span data-ttu-id="c3156-180">位資料的 VARCHAR (0) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="c3156-180">VARCHAR(0) FOR BIT DATA<sup>1</sup></span></span>|  
|`into`|<span data-ttu-id="c3156-181">INT</span><span class="sxs-lookup"><span data-stu-id="c3156-181">INT</span></span>|  
|`money`|<span data-ttu-id="c3156-182">DECIMAL(19,4)</span><span class="sxs-lookup"><span data-stu-id="c3156-182">DECIMAL(19,4)</span></span>|  
|`nchar(1-4000)`|<span data-ttu-id="c3156-183">VARCHAR(1-4000)</span><span class="sxs-lookup"><span data-stu-id="c3156-183">VARCHAR(1-4000)</span></span>|  
|`ntext`|<span data-ttu-id="c3156-184">VARCHAR (0) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="c3156-184">VARCHAR(0)<sup>1</sup></span></span>|  
|`numeric(1-31, 0-31)`|<span data-ttu-id="c3156-185">DECIMAL(1-31,0-31)</span><span class="sxs-lookup"><span data-stu-id="c3156-185">DECIMAL(1-31,0-31)</span></span>|  
|`numeric(32-38, 0-38)`|<span data-ttu-id="c3156-186">VARCHAR(41)</span><span class="sxs-lookup"><span data-stu-id="c3156-186">VARCHAR(41)</span></span>|  
|`nvarchar(1-4000)`|<span data-ttu-id="c3156-187">VARCHAR(1-4000)</span><span class="sxs-lookup"><span data-stu-id="c3156-187">VARCHAR(1-4000)</span></span>|  
|`nvarchar(max)`|<span data-ttu-id="c3156-188">VARCHAR (0) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="c3156-188">VARCHAR(0)<sup>1</sup></span></span>|  
|`real`|<span data-ttu-id="c3156-189">REAL</span><span class="sxs-lookup"><span data-stu-id="c3156-189">REAL</span></span>|  
|`smalldatetime`|<span data-ttu-id="c3156-190">timestamp</span><span class="sxs-lookup"><span data-stu-id="c3156-190">TIMESTAMP</span></span>|  
|`smallint`|<span data-ttu-id="c3156-191">SMALLINT</span><span class="sxs-lookup"><span data-stu-id="c3156-191">SMALLINT</span></span>|  
|`smallmoney`|<span data-ttu-id="c3156-192">DECIMAL(10,4)</span><span class="sxs-lookup"><span data-stu-id="c3156-192">DECIMAL(10,4)</span></span>|  
|`sql_variant`|<span data-ttu-id="c3156-193">N/A</span><span class="sxs-lookup"><span data-stu-id="c3156-193">N/A</span></span>|  
|`sysname`|<span data-ttu-id="c3156-194">VARCHAR(128)</span><span class="sxs-lookup"><span data-stu-id="c3156-194">VARCHAR(128)</span></span>|  
|`text`|<span data-ttu-id="c3156-195">VARCHAR (0) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="c3156-195">VARCHAR(0)<sup>1</sup></span></span>|  
|`time(0-7)`|<span data-ttu-id="c3156-196">VARCHAR(16)</span><span class="sxs-lookup"><span data-stu-id="c3156-196">VARCHAR(16)</span></span>|  
|`timestamp`|<span data-ttu-id="c3156-197">CHAR(8) FOR BIT DATA</span><span class="sxs-lookup"><span data-stu-id="c3156-197">CHAR(8) FOR BIT DATA</span></span>|  
|`tinyint`|<span data-ttu-id="c3156-198">SMALLINT</span><span class="sxs-lookup"><span data-stu-id="c3156-198">SMALLINT</span></span>|  
|`uniqueidentifier`|<span data-ttu-id="c3156-199">CHAR(38)</span><span class="sxs-lookup"><span data-stu-id="c3156-199">CHAR(38)</span></span>|  
|`varbinary(1-8000)`|<span data-ttu-id="c3156-200">VARCHAR(1-8000) FOR BIT DATA</span><span class="sxs-lookup"><span data-stu-id="c3156-200">VARCHAR(1-8000) FOR BIT DATA</span></span>|  
|`varchar(1-8000)`|<span data-ttu-id="c3156-201">VARCHAR(1-8000)</span><span class="sxs-lookup"><span data-stu-id="c3156-201">VARCHAR(1-8000)</span></span>|  
|`varbinary(max)`|<span data-ttu-id="c3156-202">位資料的 VARCHAR (0) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="c3156-202">VARCHAR(0) FOR BIT DATA<sup>1</sup></span></span>|  
|`varchar(max)`|<span data-ttu-id="c3156-203">VARCHAR (0) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="c3156-203">VARCHAR(0)<sup>1</sup></span></span>|  
|`xml`|<span data-ttu-id="c3156-204">VARCHAR (0) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="c3156-204">VARCHAR(0)<sup>1</sup></span></span>|  
  
 <span data-ttu-id="c3156-205"><sup>1</sup>如需有關 VARCHAR 的對應詳細資訊 (0) ，請參閱下一節。</span><span class="sxs-lookup"><span data-stu-id="c3156-205"><sup>1</sup> See the next section for more information about mappings to VARCHAR(0).</span></span>  
  
### <a name="data-type-mapping-considerations"></a><span data-ttu-id="c3156-206">資料類型對應考量</span><span class="sxs-lookup"><span data-stu-id="c3156-206">Data Type Mapping Considerations</span></span>  
 <span data-ttu-id="c3156-207">複寫至「DB2 訂閱者」時，請考慮下列資料類型對應問題：</span><span class="sxs-lookup"><span data-stu-id="c3156-207">Consider the following data type mapping issues when replicating to DB2 Subscribers:</span></span>  
  
-   <span data-ttu-id="c3156-208">將 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] `char` 、 `varchar` `binary` 和分別對應 `varbinary` 至 db2 CHAR、Varchar、CHAR for bit data 及 Varchar for bit data 時，複寫會將 db2 資料類型的長度設定為與 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 類型相同。</span><span class="sxs-lookup"><span data-stu-id="c3156-208">When mapping [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] `char`, `varchar`, `binary` and `varbinary` to DB2 CHAR, VARCHAR, CHAR FOR BIT DATA, and VARCHAR FOR BIT DATA, respectively, replication sets the length of the DB2 data type to be the same as that of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] type.</span></span>  
  
     <span data-ttu-id="c3156-209">這可使產生的資料表在「訂閱者」端成功建立，只要 DB2 頁面大小條件約束足以容納資料列的大小上限。</span><span class="sxs-lookup"><span data-stu-id="c3156-209">This allows the generated table to be successfully created at the Subscriber, as long as the DB2 page size constraint is large enough to accommodate the maximum size of the row.</span></span> <span data-ttu-id="c3156-210">確定用於存取 DB2 資料庫的登入，有權限存取擁有足夠大小以容納正複寫至 DB2 之資料表的資料表空間。</span><span class="sxs-lookup"><span data-stu-id="c3156-210">Ensure that the login used to access the DB2 database has permissions to access table spaces of a sufficient size for the tables being replicated to DB2.</span></span>  
  
-   <span data-ttu-id="c3156-211">DB2 可以支援最大 32 千位元組 (KB) 的 VARCHAR 資料行，因此可以將某些 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 大型物件資料行正確對應至 DB2 VARCHAR 資料行。</span><span class="sxs-lookup"><span data-stu-id="c3156-211">DB2 can support VARCHAR columns as large as 32 kilobytes (KB); therefore it is possible that some [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] large object columns can be appropriately mapped to DB2 VARCHAR columns.</span></span> <span data-ttu-id="c3156-212">但是，複寫用於 DB2 的 OLE DB 提供者不支援將 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 大型物件對應至 DB2 大型物件。</span><span class="sxs-lookup"><span data-stu-id="c3156-212">However, the OLE DB provider that replication uses for DB2 does not support mapping [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] large objects to DB2 large objects.</span></span> <span data-ttu-id="c3156-213">基於這個理由，、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] `text` `varchar(max)` 、和資料行會 `ntext` `nvarchar(max)` 對應至產生的建立腳本中的 VARCHAR (0) 。</span><span class="sxs-lookup"><span data-stu-id="c3156-213">For this reason, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] `text`, `varchar(max)`, `ntext`, and `nvarchar(max)` columns are mapped to VARCHAR(0) in the generated create scripts.</span></span> <span data-ttu-id="c3156-214">長度值 0 必須在將指令碼套用至「訂閱者」之前變更為適當值。</span><span class="sxs-lookup"><span data-stu-id="c3156-214">The length value of 0 must be changed to an appropriate value prior to applying the script to the Subscriber.</span></span> <span data-ttu-id="c3156-215">如果資料類型長度未變更，則嘗試在「DB2 訂閱者」端建立資料表時，DB2 將產生錯誤 604 (表示資料類型的有效位數或長度屬性無效)。</span><span class="sxs-lookup"><span data-stu-id="c3156-215">If the data type length is not changed, DB2 will raise error 604 when the table create is attempted at the DB2 Subscriber (error 604 indicates that the precision or length attribute of a data type is not valid).</span></span>  
  
     <span data-ttu-id="c3156-216">根據您對要複寫之來源資料表的了解，判斷是否適合將 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 大型物件對應至可變長度的 DB2 項目，並在自訂建立指令碼中指定適當的最大長度。</span><span class="sxs-lookup"><span data-stu-id="c3156-216">Based upon your knowledge of the source table that you are replicating, determine whether it is appropriate to map a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] large object to a variable length DB2 item, and specify an appropriate maximum length in a custom creation script.</span></span> <span data-ttu-id="c3156-217">如需有關指定自訂建立指令碼的資訊，請參閱本主題中＜設定 IBM DB2 訂閱者＞一節中的步驟 5。</span><span class="sxs-lookup"><span data-stu-id="c3156-217">For information about specifying a custom creation script, see step 5 in the section "Configuring an IBM DB2 Subscriber" in this topic.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c3156-218">指定的 DB2 類型長度與其他資料行長度的組合，不得超過由資料表資料指派到的 DB2 資料表空間確定之最大資料列大小。</span><span class="sxs-lookup"><span data-stu-id="c3156-218">The specified length for the DB2 type, when combined with other column lengths, cannot exceed the maximum row size based upon the DB2 table space that the table data is assigned to.</span></span>  
  
     <span data-ttu-id="c3156-219">如果大型物件資料行沒有適當的對應，請考慮在發行項上使用資料行篩選，以便不複寫資料行。</span><span class="sxs-lookup"><span data-stu-id="c3156-219">If there is no appropriate mapping for a large object column, consider using column filtering on the article so that the column is not replicated.</span></span> <span data-ttu-id="c3156-220">如需詳細資訊，請參閱[篩選發行的資料](../publish/filter-published-data.md)。</span><span class="sxs-lookup"><span data-stu-id="c3156-220">For more information, see [Filter Published Data](../publish/filter-published-data.md).</span></span>  
  
-   <span data-ttu-id="c3156-221">當複寫 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] `nchar` 和 `nvarchar` 至 DB2 CHAR 和 VARCHAR 時，複寫會針對 db2 類型使用與類型相同的長度規範 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="c3156-221">When replicating [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] `nchar` and `nvarchar` to DB2 CHAR and VARCHAR, replication uses the same length-specifier for the DB2 type as for the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] type.</span></span> <span data-ttu-id="c3156-222">但是，資料類型長度對於產生的 DB2 資料表可能太小。</span><span class="sxs-lookup"><span data-stu-id="c3156-222">However, the data type length might too small for the generated DB2 table.</span></span>  
  
     <span data-ttu-id="c3156-223">在某些 DB2 環境中， [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] `char` 資料項目不限於單一位元組字元; CHAR 或 VARCHAR 專案的長度必須將此納入考慮。</span><span class="sxs-lookup"><span data-stu-id="c3156-223">In some DB2 environments, a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] `char` data item is not restricted to single-byte characters; the length of a CHAR or VARCHAR item must take this into account.</span></span> <span data-ttu-id="c3156-224">如果需要 *shift in* 和 *shift out* 字元，您還必須考慮到它們。</span><span class="sxs-lookup"><span data-stu-id="c3156-224">You must also take into account *shift in* and *shift out* characters if they are needed.</span></span> <span data-ttu-id="c3156-225">如果您要複寫具有和資料行的資料表 `nchar` `nvarchar` ，您可能需要在自訂建立腳本中為資料類型指定較大的最大長度。</span><span class="sxs-lookup"><span data-stu-id="c3156-225">If you are replicating tables with `nchar` and `nvarchar` columns, you might need to specify a larger maximum length for the data type in a custom creation script.</span></span> <span data-ttu-id="c3156-226">如需有關指定自訂建立指令碼的資訊，請參閱本主題中＜設定 IBM DB2 訂閱者＞一節中的步驟 5。</span><span class="sxs-lookup"><span data-stu-id="c3156-226">For information about specifying a custom creation script, see step 5 in the section "Configuring an IBM DB2 Subscriber" in this topic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3156-227">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c3156-227">See Also</span></span>  
 <span data-ttu-id="c3156-228">[Non-SQL Server Subscribers](non-sql-server-subscribers.md) </span><span class="sxs-lookup"><span data-stu-id="c3156-228">[Non-SQL Server Subscribers](non-sql-server-subscribers.md) </span></span>  
 [<span data-ttu-id="c3156-229">訂閱發行集</span><span class="sxs-lookup"><span data-stu-id="c3156-229">Subscribe to Publications</span></span>](../subscribe-to-publications.md)  
  
  
