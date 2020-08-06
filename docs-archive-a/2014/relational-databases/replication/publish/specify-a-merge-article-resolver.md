---
title: 指定合併發行項解析程式 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- articles [SQL Server replication], conflict resolution
- conflict resolution [SQL Server replication], merge replication
- merge replication conflict resolution [SQL Server replication], merge article resolvers
ms.assetid: a40083b3-4f7b-4a25-a5a3-6ef67bdff440
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ca32ef4936f31ca5c75dfc2df1eb965d17f7b039
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702710"
---
# <a name="specify-a-merge-article-resolver"></a><span data-ttu-id="cac0f-102">指定合併發行項解析程式</span><span class="sxs-lookup"><span data-stu-id="cac0f-102">Specify a Merge Article Resolver</span></span>
  <span data-ttu-id="cac0f-103">本主題描述如何使用 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../../includes/tsql-md.md)]中指定合併發行項解析程式。</span><span class="sxs-lookup"><span data-stu-id="cac0f-103">This topic describes how to specify a merge article resolver in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="cac0f-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="cac0f-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="cac0f-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="cac0f-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="cac0f-106">建議</span><span class="sxs-lookup"><span data-stu-id="cac0f-106">Recommendations</span></span>](#Recommendations)  
  
-   <span data-ttu-id="cac0f-107">**若要指定合併發行項解析程式，請使用：**</span><span class="sxs-lookup"><span data-stu-id="cac0f-107">**To specify a merge article resolver, using:**</span></span>  
  
     [<span data-ttu-id="cac0f-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="cac0f-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="cac0f-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="cac0f-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="cac0f-110">開始之前</span><span class="sxs-lookup"><span data-stu-id="cac0f-110">Before You Begin</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="cac0f-111">建議</span><span class="sxs-lookup"><span data-stu-id="cac0f-111">Recommendations</span></span>  
  
-   <span data-ttu-id="cac0f-112">合併式複寫允許下列類型的發行項解決器：</span><span class="sxs-lookup"><span data-stu-id="cac0f-112">Merge replication allows the following types of article resolvers:</span></span>  
  
    -   <span data-ttu-id="cac0f-113">預設解決器。</span><span class="sxs-lookup"><span data-stu-id="cac0f-113">The default resolver.</span></span> <span data-ttu-id="cac0f-114">預設解決器的行為視訂閱是客訂閱還是主訂閱而定。</span><span class="sxs-lookup"><span data-stu-id="cac0f-114">The behavior of the default resolver depends on whether the subscription is a client subscription or a server subscription.</span></span> <span data-ttu-id="cac0f-115">如需指定訂閱類型的詳細資訊，請參閱[指定合併訂閱類型和衝突解決方法優先權 &#40;SQL Server Management Studio&#41;](../specify-a-merge-subscription-type-and-conflict-resolution-priority.md)。</span><span class="sxs-lookup"><span data-stu-id="cac0f-115">For more information about specifying subscription type, see [Specify a Merge Subscription Type and Conflict Resolution Priority &#40;SQL Server Management Studio&#41;](../specify-a-merge-subscription-type-and-conflict-resolution-priority.md).</span></span>  
  
    -   <span data-ttu-id="cac0f-116">您撰寫的自訂解決器可以是商務邏輯處理常式 (以 Managed 程式碼撰寫) 或是以 COM 為基礎的自訂解決器。</span><span class="sxs-lookup"><span data-stu-id="cac0f-116">A custom resolver you have written, which can be a business logic handler (written in managed code) or a custom COM-based resolver.</span></span> <span data-ttu-id="cac0f-117">如需詳細資訊，請參閱 [進階合併式複寫衝突偵測與解決](../merge/advanced-merge-replication-conflict-detection-and-resolution.md)。</span><span class="sxs-lookup"><span data-stu-id="cac0f-117">For more information, see [Advanced Merge Replication Conflict Detection and Resolution](../merge/advanced-merge-replication-conflict-detection-and-resolution.md).</span></span> <span data-ttu-id="cac0f-118">如果您需要實作針對每一個複寫之資料列執行的自訂邏輯，而不只是針對衝突的資料列，請參閱＜ [為合併發行項實作商務邏輯處理常式](../implement-a-business-logic-handler-for-a-merge-article.md)中指定合併發行項解析程式。</span><span class="sxs-lookup"><span data-stu-id="cac0f-118">If you need to implement custom logic that is executed for each replicated row, not just for conflicting rows, see [Implement a Business Logic Handler for a Merge Article](../implement-a-business-logic-handler-for-a-merge-article.md).</span></span>  
  
    -   <span data-ttu-id="cac0f-119">以 COM 為基礎的標準解決器，包含在 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中。</span><span class="sxs-lookup"><span data-stu-id="cac0f-119">A standard COM-based resolver, which is included with [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="cac0f-120">若要使用預設解決器以外的其他解決器，您必須將解決器複製到執行「合併代理程式」的電腦，然後註冊它 (如果您使用的是商務邏輯處理常式，則還必須在「發行者」端對其進行註冊)。</span><span class="sxs-lookup"><span data-stu-id="cac0f-120">To use a resolver other than the default resolver, you must copy the resolver to the computer on which the Merge Agent runs and register it (if you are using a business logic handler, it must also be registered at the Publisher).</span></span> <span data-ttu-id="cac0f-121">「合併代理程式」在以下位置上執行：</span><span class="sxs-lookup"><span data-stu-id="cac0f-121">The Merge Agent runs at:</span></span>  
  
    -   <span data-ttu-id="cac0f-122">發送訂閱的「散發者」端</span><span class="sxs-lookup"><span data-stu-id="cac0f-122">The Distributor for a push subscription</span></span>  
  
    -   <span data-ttu-id="cac0f-123">提取訂閱的「訂閱者」端</span><span class="sxs-lookup"><span data-stu-id="cac0f-123">The Subscriber for a pull subscription</span></span>  
  
    -   <span data-ttu-id="cac0f-124">使用 Web 同步處理來提取訂閱的 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Internet Information Services (IIS)</span><span class="sxs-lookup"><span data-stu-id="cac0f-124">The [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Internet Information Services (IIS) server for a pull subscription that uses Web synchronization</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="cac0f-125">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="cac0f-125">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="cac0f-126">註冊解析程式之後，指定發行項應該使用 [發行項屬性 - \<Article>] 對話方塊的 [解析程式] 索引標籤上解析程式；此對話方塊可從 [新增發行集精靈] 與 [發行集屬性 - \<Publication>] 對話方塊中取得。</span><span class="sxs-lookup"><span data-stu-id="cac0f-126">After the resolver is registered, specify that an article should use the resolver on the **Resolver** tab of the **Article Properties - \<Article>** dialog box, which is available in the New Publication Wizard and the **Publication Properties - \<Publication>** dialog box.</span></span> <span data-ttu-id="cac0f-127">如需使用精靈及存取對話方塊的詳細資訊，請參閱[建立發行集](create-a-publication.md)和[檢視及修改發行集屬性](view-and-modify-publication-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="cac0f-127">For more information about using the wizard and accessing the dialog box, see [Create a Publication](create-a-publication.md) and [View and Modify Publication Properties](view-and-modify-publication-properties.md).</span></span>  
  
#### <a name="to-specify-a-resolver"></a><span data-ttu-id="cac0f-128">若要指定解決器</span><span class="sxs-lookup"><span data-stu-id="cac0f-128">To specify a resolver</span></span>  
  
1.  <span data-ttu-id="cac0f-129">在 [新增發行集精靈] 的 [發行項] 頁面上，或在 [發行集屬性 - \<Publication>] 對話方塊中，選取一個資料表。</span><span class="sxs-lookup"><span data-stu-id="cac0f-129">On the **Articles** page of the New Publication Wizard or the **Publication Properties - \<Publication>** dialog box, select a table.</span></span>  
  
2.  <span data-ttu-id="cac0f-130">按一下 **[發行項屬性]** ，然後按一下 **[設定反白顯示資料表發行項的屬性]** 。</span><span class="sxs-lookup"><span data-stu-id="cac0f-130">Click **Article Properties**, and then click **Set Properties of Highlighted Table Article**.</span></span>  
  
3.  <span data-ttu-id="cac0f-131">在 [發行項屬性 - \<Article>] 頁面上，按一下 [解析程式] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="cac0f-131">On the **Article Properties - \<Article>** page, click the **Resolver** tab.</span></span>  
  
4.  <span data-ttu-id="cac0f-132">選取 **[使用自訂解決器 (已在散發者註冊)]** ，然後在清單中按一下解決器。</span><span class="sxs-lookup"><span data-stu-id="cac0f-132">Select **Use a custom resolver (registered at the Distributor)**, and then in the list, click the resolver.</span></span>  
  
5.  <span data-ttu-id="cac0f-133">如果解決器需要輸入 (例如資料行名稱)，請在 **[輸入解決器所需的資訊]** 文字方塊中指定它。</span><span class="sxs-lookup"><span data-stu-id="cac0f-133">If the resolver requires input (such as a column name), specify it in the **Enter information needed by the resolver** text box.</span></span>  
  
6.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
7.  <span data-ttu-id="cac0f-134">對於每個需要解決器的發行項重複此處理。</span><span class="sxs-lookup"><span data-stu-id="cac0f-134">Repeat this process for each article that requires a resolver.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="cac0f-135">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="cac0f-135">Using Transact-SQL</span></span>  
  
#### <a name="to-register-a-custom-conflict-resolver"></a><span data-ttu-id="cac0f-136">註冊自訂衝突解決器</span><span class="sxs-lookup"><span data-stu-id="cac0f-136">To register a custom conflict resolver</span></span>  
  
1.  <span data-ttu-id="cac0f-137">如果您打算註冊您自己自訂的衝突解決器，請建立以下其中一種類型：</span><span class="sxs-lookup"><span data-stu-id="cac0f-137">If you plan to register your own custom conflict resolver, create one of the following types:</span></span>  
  
    -   <span data-ttu-id="cac0f-138">以 Managed 程式碼為基礎的解決器，當做商務邏輯處理常式。</span><span class="sxs-lookup"><span data-stu-id="cac0f-138">Managed code-based resolver as a business logic handler.</span></span> <span data-ttu-id="cac0f-139">如需詳細資訊，請參閱 [為合併發行項實作商務邏輯處理常式](../implement-a-business-logic-handler-for-a-merge-article.md)。</span><span class="sxs-lookup"><span data-stu-id="cac0f-139">For more information, see [Implement a Business Logic Handler for a Merge Article](../implement-a-business-logic-handler-for-a-merge-article.md).</span></span>  
  
    -   <span data-ttu-id="cac0f-140">以預存程序為基礎的解析程式以及以 COM 為基礎的解析程式。</span><span class="sxs-lookup"><span data-stu-id="cac0f-140">Stored procedure-based resolver and COM-based resolver.</span></span> <span data-ttu-id="cac0f-141">如需詳細資訊，請參閱 [針對合併發行項實作自訂衝突解析程式](../implement-a-custom-conflict-resolver-for-a-merge-article.md)。</span><span class="sxs-lookup"><span data-stu-id="cac0f-141">For more information, see [Implement a Custom Conflict Resolver for a Merge Article](../implement-a-custom-conflict-resolver-for-a-merge-article.md).</span></span>  
  
2.  <span data-ttu-id="cac0f-142">若要判斷是否已經註冊想要的解決程式，請在任何資料庫的發行者端執行 [sp_enumcustomresolvers &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="cac0f-142">To determine if the desired resolver is already registered, execute [sp_enumcustomresolvers &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql) at the Publisher on any database.</span></span> <span data-ttu-id="cac0f-143">這樣會顯示自訂解決器的描述以及在散發者上註冊之每一個以 COM 為基礎之解決器的類別識別碼 (CLSID)，或是在散發者上註冊之每一個商務邏輯處理常式的 Managed 組件相關資訊。</span><span class="sxs-lookup"><span data-stu-id="cac0f-143">This displays a description of the custom resolver as well as the class identifier (CLSID) for each COM-based resolver registered at the Distributor or information on the managed assembly for each business logic handler registered at the Distributor.</span></span>  
  
3.  <span data-ttu-id="cac0f-144">如果尚未註冊所要的自訂解析程式，請在散發者端執行 [sp_registercustomresolver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-registercustomresolver-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="cac0f-144">If the desired custom resolver is not already registered, execute [sp_registercustomresolver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-registercustomresolver-transact-sql) at the Distributor.</span></span> <span data-ttu-id="cac0f-145">指定解析程式的名稱; 如果 **@article_resolver** 是商務邏輯處理常式，這是元件的易記名稱。</span><span class="sxs-lookup"><span data-stu-id="cac0f-145">Specify a name for the resolver for **@article_resolver**; for a business logic handler, this is the friendly name of the assembly.</span></span> <span data-ttu-id="cac0f-146">如果是以 COM 為基礎的解析程式，請針對指定 DLL 的 CLSID， **@resolver_clsid** 針對商務邏輯處理常式，指定的值、的 `true` **@is_dotnet_assembly** 元件名稱 **@dotnet_assembly_name** ，以及覆寫之類別的完整名稱 <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> **@dotnet_class_name** 。</span><span class="sxs-lookup"><span data-stu-id="cac0f-146">For COM-based resolvers, specify the CLSID of the DLL for **@resolver_clsid**, and for a business logic handler, specify a value of `true` for **@is_dotnet_assembly**, the name of the assembly for **@dotnet_assembly_name**, and the fully-qualified name of the class that overrides <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> for **@dotnet_class_name**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="cac0f-147">如果商務邏輯處理常式元件未部署在與合併代理程式可執行檔相同的目錄中、與同步啟動合併代理程式之應用程式相同的目錄中，或在全域組件快取中 (GAC) ，您就必須使用的元件名稱來指定完整路徑 **@dotnet_assembly_name** 。</span><span class="sxs-lookup"><span data-stu-id="cac0f-147">If a business logic handler assembly is not deployed in the same directory as the Merge Agent executable, in the same directory as the application that synchronously starts the Merge Agent, or in the global assembly cache (GAC), you need to specify the full path with the assembly name for **@dotnet_assembly_name**.</span></span>  
  
4.  <span data-ttu-id="cac0f-148">如果此解決器是以 COM 為基礎的解決器：</span><span class="sxs-lookup"><span data-stu-id="cac0f-148">If the resolver is a COM-based resolver:</span></span>  
  
    -   <span data-ttu-id="cac0f-149">將自訂解決器 DLL 複製到發送訂閱的散發者上，或是提取訂閱的訂閱者上。</span><span class="sxs-lookup"><span data-stu-id="cac0f-149">Copy the custom resolver DLL to the Distributor for push subscriptions or to the Subscriber for pull subscriptions.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="cac0f-150">可以在[!INCLUDE[msCoName](../../../includes/msconame-md.md)] COM 目錄中找到 [!INCLUDE[ssInstallPath](../../../includes/ssinstallpath-md.md)]自訂解決器。</span><span class="sxs-lookup"><span data-stu-id="cac0f-150">[!INCLUDE[msCoName](../../../includes/msconame-md.md)] custom resolvers can be found in the [!INCLUDE[ssInstallPath](../../../includes/ssinstallpath-md.md)]COM directory.</span></span>  
  
    -   <span data-ttu-id="cac0f-151">使用 regsvr32.exe 向作業系統註冊自訂解決器 DLL。</span><span class="sxs-lookup"><span data-stu-id="cac0f-151">Use regsvr32.exe to register the custom resolver DLL with the operating system.</span></span> <span data-ttu-id="cac0f-152">例如，從命令提示字元執行以下命令可註冊 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Additive Conflict Resolver：</span><span class="sxs-lookup"><span data-stu-id="cac0f-152">For example, executing the following from the command prompt registers the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Additive Conflict Resolver:</span></span>  
  
        ```  
        regsvr32 ssradd.dll  
        ```  
  
5.  <span data-ttu-id="cac0f-153">如果解析程式是商務邏輯處理常式，請將元件部署在與合併代理程式可執行檔相同的資料夾中 ( # A0) 、與叫用合併代理程式的應用程式相同的資料夾中，或在步驟3中為參數指定的資料夾中 **@dotnet_assembly_name** 。</span><span class="sxs-lookup"><span data-stu-id="cac0f-153">If the resolver is a business logic handler, deploy the assembly in the same folder as the Merge Agent executable (replmerg.exe), in the same folder as an application that invokes the Merge Agent, or in the folder specified for the **@dotnet_assembly_name** parameter in step 3.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="cac0f-154">合併代理程式可執行檔的預設安裝位置為 [!INCLUDE[ssInstallPath](../../../includes/ssinstallpath-md.md)]COM。</span><span class="sxs-lookup"><span data-stu-id="cac0f-154">The default installation location of the Merge Agent executable is [!INCLUDE[ssInstallPath](../../../includes/ssinstallpath-md.md)]COM.</span></span>  
  
#### <a name="to-specify-a-custom-resolver-when-defining-a-merge-article"></a><span data-ttu-id="cac0f-155">在定義合併發行項時，指定自訂解決器</span><span class="sxs-lookup"><span data-stu-id="cac0f-155">To specify a custom resolver when defining a merge article</span></span>  
  
1.  <span data-ttu-id="cac0f-156">如果您打算使用自訂衝突解決器，請使用以上的程序建立及註冊解決器。</span><span class="sxs-lookup"><span data-stu-id="cac0f-156">If you plan to use a custom conflict resolver, create and register the resolver using the above procedure.</span></span>  
  
2.  <span data-ttu-id="cac0f-157">在發行者端，執行 [sp_enumcustomresolvers &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql)，並記下結果集中 [value] 欄位內所需的自訂解析程式名稱。</span><span class="sxs-lookup"><span data-stu-id="cac0f-157">At the Publisher, execute [sp_enumcustomresolvers &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql) and note the name of the desired custom resolver in the **value** field of result set.</span></span>  
  
3.  <span data-ttu-id="cac0f-158">在發行集資料庫的發行者端，執行 [sp_addmergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="cac0f-158">At the Publisher on the publication database, execute [sp_addmergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql).</span></span> <span data-ttu-id="cac0f-159">針對指定步驟2中的解決器名稱 **@article_resolver** ，並使用參數指定自訂解決器的任何必要輸入 **@resolver_info** 。</span><span class="sxs-lookup"><span data-stu-id="cac0f-159">Specify the name of the resolver from step 2 for **@article_resolver** and any required input to the custom resolver using the **@resolver_info** parameter.</span></span> <span data-ttu-id="cac0f-160">對於以預存程式為基礎的自訂解析程式， **@resolver_info** 是預存程式的名稱。</span><span class="sxs-lookup"><span data-stu-id="cac0f-160">For stored procedure-based custom resolvers, **@resolver_info** is the name of the stored procedure.</span></span> <span data-ttu-id="cac0f-161">如需 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] 提供之解析程式所需輸入的詳細資訊，請參閱 [Microsoft 以 COM 為基礎的解析程式](../merge/advanced-merge-replication-conflict-com-based-resolvers.md)。</span><span class="sxs-lookup"><span data-stu-id="cac0f-161">For more information about required input for resolvers supplied by [!INCLUDE[msCoName](../../../includes/msconame-md.md)], see [Microsoft COM-Based Resolvers](../merge/advanced-merge-replication-conflict-com-based-resolvers.md).</span></span>  
  
#### <a name="to-specify-or-change-a-custom-resolver-for-an-existing-merge-article"></a><span data-ttu-id="cac0f-162">針對現有的合併發行項指定或變更自訂解決器</span><span class="sxs-lookup"><span data-stu-id="cac0f-162">To specify or change a custom resolver for an existing merge article</span></span>  
  
1.  <span data-ttu-id="cac0f-163">若要判斷是否已針對發行項定義自訂解析程式，或是要取得解析程式的名稱，請執行 [sp_helpmergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpmergearticle-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="cac0f-163">To determine if a custom resolver has been defined for an article, or to get the name of the resolver, execute [sp_helpmergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpmergearticle-transact-sql).</span></span> <span data-ttu-id="cac0f-164">如果已針對發行項定義自訂解決器，它的名稱會顯示在 **article_resolver** 欄位中。</span><span class="sxs-lookup"><span data-stu-id="cac0f-164">If there is a custom resolver defined for the article, its name will be displayed in the **article_resolver** field.</span></span> <span data-ttu-id="cac0f-165">為解決器提供的任何輸入都會顯示在結果集的 **resolver_info** 欄位中。</span><span class="sxs-lookup"><span data-stu-id="cac0f-165">Any input supplied to the resolver will be displayed in the **resolver_info** field of the result set.</span></span>  
  
2.  <span data-ttu-id="cac0f-166">在發行者端，執行 [sp_enumcustomresolvers &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql)，並記下結果集中 [value] 欄位內所需的自訂解析程式名稱。</span><span class="sxs-lookup"><span data-stu-id="cac0f-166">At the Publisher, execute [sp_enumcustomresolvers &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql) and note the name of the desired custom resolver in the **value** field of the result set.</span></span>  
  
3.  <span data-ttu-id="cac0f-167">在發行集資料庫的發行者端，執行 [sp_changemergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="cac0f-167">At the Publisher on the publication database, execute [sp_changemergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql).</span></span> <span data-ttu-id="cac0f-168">針對 **article_resolver**指定 **@property**的值，包括商務邏輯處理常式的完整路徑，並針對 **@value**中指定合併發行項解析程式。</span><span class="sxs-lookup"><span data-stu-id="cac0f-168">Specify a value of **article_resolver**, including the full path for business logic handlers, for **@property**, and the name of the desired custom resolver from step 2 for **@value**.</span></span>  
  
4.  <span data-ttu-id="cac0f-169">若要變更自訂解析程式的任何必要輸入，請再次執行 [sp_changemergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="cac0f-169">To change any required input for the custom resolver, execute [sp_changemergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql) again.</span></span> <span data-ttu-id="cac0f-170">針對 **resolver_info** @is_dotnet_assembly **@property** 的值，並針對 **@value**中指定合併發行項解析程式。</span><span class="sxs-lookup"><span data-stu-id="cac0f-170">Specify a value of **resolver_info** for **@property** and any required input to the custom resolver for **@value**.</span></span> <span data-ttu-id="cac0f-171">對於以預存程式為基礎的自訂解析程式， **@resolver_info** 是預存程式的名稱。</span><span class="sxs-lookup"><span data-stu-id="cac0f-171">For stored procedure-based custom resolvers, **@resolver_info** is the name of the stored procedure.</span></span> <span data-ttu-id="cac0f-172">如需必要輸入的詳細資訊，請參閱 [Microsoft 以 COM 為基礎的解析程式](../merge/advanced-merge-replication-conflict-com-based-resolvers.md)。</span><span class="sxs-lookup"><span data-stu-id="cac0f-172">For more information about required input, see [Microsoft COM-Based Resolvers](../merge/advanced-merge-replication-conflict-com-based-resolvers.md).</span></span>  
  
#### <a name="to-unregister-a-custom-conflict-resolver"></a><span data-ttu-id="cac0f-173">取消註冊自訂衝突解決器</span><span class="sxs-lookup"><span data-stu-id="cac0f-173">To unregister a custom conflict resolver</span></span>  
  
1.  <span data-ttu-id="cac0f-174">在發行者端，執行 [sp_enumcustomresolvers &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql)，並記下結果集中 [value] 欄位內所需的自訂解析程式名稱。</span><span class="sxs-lookup"><span data-stu-id="cac0f-174">At the Publisher, execute [sp_enumcustomresolvers &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql) and note the name of the custom resolver to remove in the **value** field of the result set.</span></span>  
  
2.  <span data-ttu-id="cac0f-175">在散發者端，執行 [sp_unregistercustomresolver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-unregistercustomresolver-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="cac0f-175">Execute [sp_unregistercustomresolver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-unregistercustomresolver-transact-sql) at the Distributor.</span></span> <span data-ttu-id="cac0f-176">針對，指定步驟1中自訂解決器的完整名稱 **@article_resolver** 。</span><span class="sxs-lookup"><span data-stu-id="cac0f-176">Specify the full name of the custom resolver from step 1 for **@article_resolver**.</span></span>  
  
###  <a name="examples-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="cac0f-177">範例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="cac0f-177">Examples (Transact-SQL)</span></span>  
 <span data-ttu-id="cac0f-178">此範例會建立新的發行項，並指定在發生衝突時，應該使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Averaging Conflict Resolver 來計算 **UnitPrice** 資料行的平均值。</span><span class="sxs-lookup"><span data-stu-id="cac0f-178">This example creates a new article and specifies that the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Averaging Conflict Resolver be used to calculate the average of the **UnitPrice** column when conflicts occur.</span></span>  
  
 [!code-sql[HowTo#sp_addmerge_resolver](../../../snippets/tsql/SQL15/replication/howto/tsql/mergearticleresolvers.sql#sp_addmerge_resolver)]  
  
 <span data-ttu-id="cac0f-179">這個範例會變更要指定的發行項，其方式是在發生衝突時使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Additive Conflict Resolver 計算 **UnitsOnOrder** 資料行的總和。</span><span class="sxs-lookup"><span data-stu-id="cac0f-179">This example changes an article to specify using the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Additive Conflict Resolver to calculate the sum of the **UnitsOnOrder** column when conflicts occur.</span></span>  
  
 [!code-sql[HowTo#sp_changemerge_resolver](../../../snippets/tsql/SQL15/replication/howto/tsql/mergearticleresolvers.sql#sp_changemerge_resolver)]  
  
## <a name="see-also"></a><span data-ttu-id="cac0f-180">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cac0f-180">See Also</span></span>  
 <span data-ttu-id="cac0f-181">[進階合併式複寫衝突偵測與解決](../merge/advanced-merge-replication-conflict-detection-and-resolution.md) </span><span class="sxs-lookup"><span data-stu-id="cac0f-181">[Advanced Merge Replication Conflict Detection and Resolution](../merge/advanced-merge-replication-conflict-detection-and-resolution.md) </span></span>  
 [<span data-ttu-id="cac0f-182">為合併發行項實作商務邏輯處理常式</span><span class="sxs-lookup"><span data-stu-id="cac0f-182">Implement a Business Logic Handler for a Merge Article</span></span>](../implement-a-business-logic-handler-for-a-merge-article.md)  
  
  
