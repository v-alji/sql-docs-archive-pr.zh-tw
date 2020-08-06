---
title: SQL Server 屬性 (啟動參數] 索引標籤) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: 16942624-5374-446c-8de4-ee6ed34d6e94
author: stevestein
ms.author: sstein
ms.openlocfilehash: 66c4b71433face008ba78af93579cf175fb4bed4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595335"
---
# <a name="sql-server-properties-startup-parameters-tab"></a><span data-ttu-id="dab7d-102">SQL Server 屬性 (啟動參數索引標籤)</span><span class="sxs-lookup"><span data-stu-id="dab7d-102">SQL Server Properties (Startup Parameters Tab)</span></span>
  <span data-ttu-id="dab7d-103">您可以使用這個對話方塊來加入或移除 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的啟動參數。</span><span class="sxs-lookup"><span data-stu-id="dab7d-103">Use this dialog box to add or remove startup parameters for the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span> <span data-ttu-id="dab7d-104">啟動參數可能會對 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 效能產生很大的影響。</span><span class="sxs-lookup"><span data-stu-id="dab7d-104">Startup parameters can have a large effect on the [!INCLUDE[ssDE](../../includes/ssde-md.md)] performance.</span></span> <span data-ttu-id="dab7d-105">加入或變更啟動參數之前，請先參閱《 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 線上叢書》中的＜使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務啟動選項＞主題。</span><span class="sxs-lookup"><span data-stu-id="dab7d-105">Before adding or changing startup parameters, see the topic "Using the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Service Startup Options" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="options"></a><span data-ttu-id="dab7d-106">選項。</span><span class="sxs-lookup"><span data-stu-id="dab7d-106">Options</span></span>  
 <span data-ttu-id="dab7d-107">**指定啟動參數**</span><span class="sxs-lookup"><span data-stu-id="dab7d-107">**Specify a startup parameter**</span></span>  
 <span data-ttu-id="dab7d-108">若要加入參數，請輸入參數，然後按一下 [加入]  。</span><span class="sxs-lookup"><span data-stu-id="dab7d-108">To add a parameter, type the parameter, and then click **Add**.</span></span>  
  
 <span data-ttu-id="dab7d-109">若要修改其中一個必要參數，請在 **[現有參數]** 方塊中選取參數、在 **[指定啟動參數]** 方塊中變更其值，然後按一下 **[更新]** 。</span><span class="sxs-lookup"><span data-stu-id="dab7d-109">To modify one of the required parameters, select the parameter in the **Existing parameters** box, change the values in the **Specify a startup parameter** box, and then click **Update**.</span></span>  
  
 <span data-ttu-id="dab7d-110">**[現有參數]**</span><span class="sxs-lookup"><span data-stu-id="dab7d-110">**Existing parameters**</span></span>  
 <span data-ttu-id="dab7d-111">若要移除參數，請選取參數，然後按一下 [移除]  。</span><span class="sxs-lookup"><span data-stu-id="dab7d-111">To remove a parameter, select a parameter, and then click **Remove**.</span></span>  
  
## <a name="parameter-format"></a><span data-ttu-id="dab7d-112">參數格式</span><span class="sxs-lookup"><span data-stu-id="dab7d-112">Parameter Format</span></span>  
 <span data-ttu-id="dab7d-113">請勿在參數之間輸入分隔符號。</span><span class="sxs-lookup"><span data-stu-id="dab7d-113">Do not enter a separator between parameters.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="dab7d-114">組態管理員會自動加入分隔符號。</span><span class="sxs-lookup"><span data-stu-id="dab7d-114">Configuration Manager automatically adds the separator.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="dab7d-115">組態管理員會強制執行下列參數需求。</span><span class="sxs-lookup"><span data-stu-id="dab7d-115">Configuration Manager enforces the following parameter requirements.</span></span>  
  
-   <span data-ttu-id="dab7d-116">修剪任何啟動參數中的開頭和尾端空白。</span><span class="sxs-lookup"><span data-stu-id="dab7d-116">Leading and trailing spaces are trimmed from any startup parameter.</span></span>  
  
-   <span data-ttu-id="dab7d-117">所有啟動參數的開頭都是 - (虛線) 而第二個值是字母。</span><span class="sxs-lookup"><span data-stu-id="dab7d-117">All startup parameters start with a - (dash) and the second value is a letter.</span></span>  
  
## <a name="required-parameters"></a><span data-ttu-id="dab7d-118">必要參數</span><span class="sxs-lookup"><span data-stu-id="dab7d-118">Required Parameters</span></span>  
 <span data-ttu-id="dab7d-119">下列參數為必要參數。</span><span class="sxs-lookup"><span data-stu-id="dab7d-119">The following parameters are required.</span></span> <span data-ttu-id="dab7d-120">您可以變更但無法移除這些參數。</span><span class="sxs-lookup"><span data-stu-id="dab7d-120">They can be changed but not removed.</span></span>  
  
-   <span data-ttu-id="dab7d-121">-d 是 **master.mdf** 檔案 (master 資料庫資料檔) 的路徑。</span><span class="sxs-lookup"><span data-stu-id="dab7d-121">-d is the path of the **master.mdf** file (the master database data file).</span></span>  
  
-   <span data-ttu-id="dab7d-122">-l 是 **master.ldf** 檔案 (master 資料庫記錄檔) 的路徑。</span><span class="sxs-lookup"><span data-stu-id="dab7d-122">-l is the path of the **master.ldf** file (the master database log file).</span></span>  
  
-   <span data-ttu-id="dab7d-123">-e 是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 錯誤記錄檔的路徑。</span><span class="sxs-lookup"><span data-stu-id="dab7d-123">-e is the path of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log files.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="dab7d-124">如果檔案路徑不正確， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 可能無法啟動。</span><span class="sxs-lookup"><span data-stu-id="dab7d-124">If the file path parameters are incorrect [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] might not start.</span></span>  
  
 <span data-ttu-id="dab7d-125">如需有關如何移動 master 資料庫的詳細資訊，請參閱《 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 線上叢書》中的＜移動系統資料庫＞主題。</span><span class="sxs-lookup"><span data-stu-id="dab7d-125">For more information about how to move the master database, see the topic "Moving System Databases" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="optional-parameters"></a><span data-ttu-id="dab7d-126">選擇性參數</span><span class="sxs-lookup"><span data-stu-id="dab7d-126">Optional Parameters</span></span>  
 <span data-ttu-id="dab7d-127">《 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 線上叢書》中的＜使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務啟動選項＞主題描述了所有支援的啟動參數。</span><span class="sxs-lookup"><span data-stu-id="dab7d-127">All of the supported startup parameters are described in the topic "Using the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Service Startup Options," in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span> <span data-ttu-id="dab7d-128">啟動參數 -T*trace#* 表示 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體應該使用作用中的指定追蹤旗標 (*trace#* ) 來啟動。</span><span class="sxs-lookup"><span data-stu-id="dab7d-128">A startup parameter of -T*trace#* indicates that an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] should be started with a specified trace flag (*trace#*) in effect.</span></span> <span data-ttu-id="dab7d-129">追蹤旗標用來啟動具有非標準行為的伺服器。</span><span class="sxs-lookup"><span data-stu-id="dab7d-129">Trace flags are used to start the server with nonstandard behavior.</span></span> <span data-ttu-id="dab7d-130">如需追蹤旗標的詳細資訊，請參閱《[!INCLUDE[tsql](../../includes/tsql-md.md)]線上叢書》中的＜追蹤旗標 ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] )＞主題。</span><span class="sxs-lookup"><span data-stu-id="dab7d-130">For more information about trace flags, see the topic "Trace Flags ([!INCLUDE[tsql](../../includes/tsql-md.md)])" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="dab7d-131">您可能會在網際網路上看到其他未記載的啟動參數和追蹤旗標描述。</span><span class="sxs-lookup"><span data-stu-id="dab7d-131">You might see additional undocumented startup parameters and trace flags described on the Internet.</span></span> <span data-ttu-id="dab7d-132">未記載的啟動參數和追蹤旗標是用來處理不常見的問題或強制執行測試所需的特定條件。</span><span class="sxs-lookup"><span data-stu-id="dab7d-132">Undocumented startup parameters and trace flags are created to address uncommon problems or to force certain conditions required for testing.</span></span> <span data-ttu-id="dab7d-133">使用未記載的啟動參數可能會產生非預期的結果。</span><span class="sxs-lookup"><span data-stu-id="dab7d-133">Using undocumented startup parameters can have unexpected results.</span></span> <span data-ttu-id="dab7d-134">除非 Microsoft 客戶支援服務建議使用未記載的參數，否則請勿使用這些參數。</span><span class="sxs-lookup"><span data-stu-id="dab7d-134">Do not use undocumented parameters unless directed by Microsoft Customer Support Services.</span></span>  
  
 <span data-ttu-id="dab7d-135">下列清單描述的是一些常見的選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="dab7d-135">The following list describes some common optional parameters.</span></span>  
  
|<span data-ttu-id="dab7d-136">參數</span><span class="sxs-lookup"><span data-stu-id="dab7d-136">Parameter</span></span>|<span data-ttu-id="dab7d-137">簡短描述</span><span class="sxs-lookup"><span data-stu-id="dab7d-137">Short description</span></span>|  
|---------------|-----------------------|  
|<span data-ttu-id="dab7d-138">-M</span><span class="sxs-lookup"><span data-stu-id="dab7d-138">-m</span></span>|<span data-ttu-id="dab7d-139">在單一使用者模式中啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="dab7d-139">Starts an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in single-user mode.</span></span>|  
|<span data-ttu-id="dab7d-140">-T1204</span><span class="sxs-lookup"><span data-stu-id="dab7d-140">-T1204</span></span>|<span data-ttu-id="dab7d-141">傳回參與死結之鎖定的資源和類型，以及目前受影響的命令。</span><span class="sxs-lookup"><span data-stu-id="dab7d-141">Returns the resources and types of locks participating in a deadlock and also the current command affected.</span></span>|  
|<span data-ttu-id="dab7d-142">-T1224</span><span class="sxs-lookup"><span data-stu-id="dab7d-142">-T1224</span></span>|<span data-ttu-id="dab7d-143">停用以鎖定個數為基礎的鎖定擴大。</span><span class="sxs-lookup"><span data-stu-id="dab7d-143">Disables lock escalation based on the number of locks.</span></span>|  
|<span data-ttu-id="dab7d-144">-T3608</span><span class="sxs-lookup"><span data-stu-id="dab7d-144">-T3608</span></span>|<span data-ttu-id="dab7d-145">防止 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 自動啟動並復原任何資料庫，但 master 資料庫除外。</span><span class="sxs-lookup"><span data-stu-id="dab7d-145">Prevents [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from automatically starting and recovering any database except the master database.</span></span>|  
|<span data-ttu-id="dab7d-146">-T7806</span><span class="sxs-lookup"><span data-stu-id="dab7d-146">-T7806</span></span>|<span data-ttu-id="dab7d-147">在 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]上啟用專用管理員連接 (DAC)。</span><span class="sxs-lookup"><span data-stu-id="dab7d-147">Enables a dedicated administrator connection (DAC) on [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)].</span></span>|  
  
> [!CAUTION]  
>  <span data-ttu-id="dab7d-148">某些選擇性參數可能會變更伺服器行為，而且可能會影響效能。</span><span class="sxs-lookup"><span data-stu-id="dab7d-148">Some optional parameters can change server behavior and may affect performance.</span></span>  
  
## <a name="permissions"></a><span data-ttu-id="dab7d-149">權限</span><span class="sxs-lookup"><span data-stu-id="dab7d-149">Permissions</span></span>  
 <span data-ttu-id="dab7d-150">只有能夠在登錄中變更相關項目的使用者才能使用這個頁面，</span><span class="sxs-lookup"><span data-stu-id="dab7d-150">Use of this page is restricted to users who can change the related entries in the registry.</span></span> <span data-ttu-id="dab7d-151">包括下列使用者。</span><span class="sxs-lookup"><span data-stu-id="dab7d-151">This includes the following users.</span></span>  
  
-   <span data-ttu-id="dab7d-152">本機 Administrators 群組的成員。</span><span class="sxs-lookup"><span data-stu-id="dab7d-152">Members of the local administrators group.</span></span>  
  
-   <span data-ttu-id="dab7d-153">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]所使用的網域帳戶 (如果 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 設定為使用網域帳戶來執行的話)。</span><span class="sxs-lookup"><span data-stu-id="dab7d-153">The domain account that is used by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], if the [!INCLUDE[ssDE](../../includes/ssde-md.md)] is configured to run under a domain account.</span></span>  
  
## <a name="books-online-references"></a><span data-ttu-id="dab7d-154">線上叢書參考</span><span class="sxs-lookup"><span data-stu-id="dab7d-154">Books Online References</span></span>  
 <span data-ttu-id="dab7d-155">如需 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 啟動參數的其他資訊，請參閱《[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 線上叢書》中的＜如何：設定伺服器啟動選項 ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 組態管理員)＞。</span><span class="sxs-lookup"><span data-stu-id="dab7d-155">For additional information about [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] startup parameters, see "How to: Configure Server Startup Options ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager)" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
  
