---
title: 實例設定 |Microsoft Docs
ms.custom: ''
ms.date: 05/04/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
f1_keywords:
- instance configuration, Setup
helpviewer_keywords:
- Instance Name page [SQL Server Installation Wizard]
- SQL Server Installation Wizard, Instance Name page
ms.assetid: 5bf822fc-6dec-4806-a153-e200af28e9a5
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 86a9538e81881a3b42b95447f4264200e2fe9d4c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598154"
---
# <a name="instance-configuration"></a><span data-ttu-id="22142-102">執行個體組態</span><span class="sxs-lookup"><span data-stu-id="22142-102">Instance Configuration</span></span>
  <span data-ttu-id="22142-103">請使用 **安裝精靈的** [執行個體組態] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 頁面，指定要建立 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的預設執行個體還是具名執行個體。</span><span class="sxs-lookup"><span data-stu-id="22142-103">Use the **Instance Configuration** page of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Installation Wizard to specify whether to create a default instance or a named instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="22142-104">如果尚未安裝 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的執行個體，則除非您指定具名執行個體，否則將會建立預設執行個體。</span><span class="sxs-lookup"><span data-stu-id="22142-104">If an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is not already installed, a default instance will be created unless you specify a named instance.</span></span>  
  
 <span data-ttu-id="22142-105">每個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體都包含一組不同的服務，而這些服務對於定序和其他選項具有特定設定。</span><span class="sxs-lookup"><span data-stu-id="22142-105">Each instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] consists of a distinct set of services that have specific settings for collations and other options.</span></span> <span data-ttu-id="22142-106">目錄結構、登錄結構和服務名稱都反映出在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝期間建立的執行個體名稱和特定的執行個體識別碼。</span><span class="sxs-lookup"><span data-stu-id="22142-106">The directory structure, registry structure, and service names all reflect the instance name and a specific instance ID created during [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup.</span></span>  
  
 <span data-ttu-id="22142-107">執行個體是預設執行個體或具名執行個體。</span><span class="sxs-lookup"><span data-stu-id="22142-107">An instance is either the default instance or a named instance.</span></span> <span data-ttu-id="22142-108">預設執行個體名稱是 MSSQLSERVER。</span><span class="sxs-lookup"><span data-stu-id="22142-108">The default instance name is MSSQLSERVER.</span></span> <span data-ttu-id="22142-109">它不需要用戶端指定執行個體名稱來進行連接。</span><span class="sxs-lookup"><span data-stu-id="22142-109">It does not require a client to specify the name of the instance to make a connection.</span></span> <span data-ttu-id="22142-110">具名執行個體由使用者在安裝期間決定。</span><span class="sxs-lookup"><span data-stu-id="22142-110">A named instance is determined by the user during Setup.</span></span> <span data-ttu-id="22142-111">您可以將 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝為具名執行個體，而不需要先安裝預設執行個體。</span><span class="sxs-lookup"><span data-stu-id="22142-111">You can install [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] as a named instance without installing the default instance first.</span></span> <span data-ttu-id="22142-112">一次只有一個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝 (不論版本為何) 可以是預設執行個體。</span><span class="sxs-lookup"><span data-stu-id="22142-112">Only one installation of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], regardless of version, can be the default instance at one time.</span></span>  
  
 <span data-ttu-id="22142-113">**消息!**</span><span class="sxs-lookup"><span data-stu-id="22142-113">**Alert!**</span></span> <span data-ttu-id="22142-114">透過 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SysPrep，當您完成備妥的執行個體時，就可以在 [執行個體組態]\*\*\*\* 頁面上指定執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="22142-114">With [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SysPrep, you can specify the instance name when you complete a prepared instance on the **Instance Configuration** page.</span></span> <span data-ttu-id="22142-115">如果電腦上沒有任何現有的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 預設執行個體，您就可以選擇將所完成的備妥執行個體設定為預設執行個體。</span><span class="sxs-lookup"><span data-stu-id="22142-115">You can choose to configure the prepared instance you are completing as a default instance if there is no existing default instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on the machine.</span></span>  
  
## <a name="multiple-instances"></a><span data-ttu-id="22142-116">多個執行個體</span><span class="sxs-lookup"><span data-stu-id="22142-116">Multiple Instances</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="22142-117">支援單一伺服器或處理器上的多個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體，但是只有一個執行個體可以是預設執行個體；</span><span class="sxs-lookup"><span data-stu-id="22142-117">supports multiple instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on a single server or processor, but only one instance can be the default instance.</span></span> <span data-ttu-id="22142-118">其他所有的執行個體都必須是具名執行個體。</span><span class="sxs-lookup"><span data-stu-id="22142-118">All others must be named instances.</span></span> <span data-ttu-id="22142-119">電腦可同時執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的多個執行個體，每一個執行個體的執行與其他執行個體無關。</span><span class="sxs-lookup"><span data-stu-id="22142-119">A computer can run multiple instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] concurrently, and each instance runs independently of other instances.</span></span>  
  
 <span data-ttu-id="22142-120">如需詳細資訊，請參閱[SQL Server 的最大容量規格](../maximum-capacity-specifications-for-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="22142-120">For more information, see [Maximum Capacity Specifications for SQL Server](../maximum-capacity-specifications-for-sql-server.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="22142-121">選項</span><span class="sxs-lookup"><span data-stu-id="22142-121">Options</span></span>  
 <span data-ttu-id="22142-122">僅限容錯移轉叢集執行個體 - 指定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 容錯移轉叢集網路名稱。</span><span class="sxs-lookup"><span data-stu-id="22142-122">Failover cluster instances only - Specify the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster network name.</span></span> <span data-ttu-id="22142-123">這個名稱會在網路上識別容錯移轉叢集執行個體。</span><span class="sxs-lookup"><span data-stu-id="22142-123">This name identifies the failover cluster instance on the network.</span></span>  
  
 <span data-ttu-id="22142-124">預設或具名執行個體 - 在決定要安裝 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的預設執行個體還是具名執行個體時，請考量以下資訊：</span><span class="sxs-lookup"><span data-stu-id="22142-124">Default or Named instance - Consider the following information when you decide whether to install a default or named instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="22142-125">如果您計劃在資料庫伺服器上安裝單一 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體，它應該是預設執行個體。</span><span class="sxs-lookup"><span data-stu-id="22142-125">If you plan to install a single instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on a database server, it should be a default instance.</span></span>  
  
-   <span data-ttu-id="22142-126">當您打算在相同電腦上擁有多個執行個體時，請使用具名執行個體。</span><span class="sxs-lookup"><span data-stu-id="22142-126">Use a named instance for situations where you plan to have multiple instances on the same computer.</span></span> <span data-ttu-id="22142-127">一個伺服器只能主控一個預設執行個體。</span><span class="sxs-lookup"><span data-stu-id="22142-127">A server can host only one default instance.</span></span>  
  
-   <span data-ttu-id="22142-128">安裝 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] 的任何應用程式都應該將它安裝為具名執行個體。</span><span class="sxs-lookup"><span data-stu-id="22142-128">Any application that installs [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] should install it as a named instance.</span></span> <span data-ttu-id="22142-129">這種作法可以減少將多個應用程式安裝在相同電腦時所造成的衝突。</span><span class="sxs-lookup"><span data-stu-id="22142-129">This will minimizes conflict when multiple applications are installed on the same computer.</span></span>  
  
 <span data-ttu-id="22142-130">**預設執行個體**</span><span class="sxs-lookup"><span data-stu-id="22142-130">**Default instance**</span></span>  
 <span data-ttu-id="22142-131">選取這個選項可安裝 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的預設執行個體。</span><span class="sxs-lookup"><span data-stu-id="22142-131">Select this option to install a default instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="22142-132">電腦只能主控一個預設執行個體；所有其他執行個體都必須加以命名。</span><span class="sxs-lookup"><span data-stu-id="22142-132">A computer can host only one default instance; all other instances must be named.</span></span> <span data-ttu-id="22142-133">不過，如果您已安裝 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的預設執行個體，您可將 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 的預設執行個體加入相同電腦中。</span><span class="sxs-lookup"><span data-stu-id="22142-133">However, if you have a default instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installed, you can add a default instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] to the same computer.</span></span>  
  
 <span data-ttu-id="22142-134">**具名執行個體**</span><span class="sxs-lookup"><span data-stu-id="22142-134">**Named instance**</span></span>  
 <span data-ttu-id="22142-135">選取這個選項可建立新的具名執行個體。</span><span class="sxs-lookup"><span data-stu-id="22142-135">Select this option to create a new named instance.</span></span> <span data-ttu-id="22142-136">當您為 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的執行個體命名時，請注意以下事項：</span><span class="sxs-lookup"><span data-stu-id="22142-136">Be aware of the following when you name an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="22142-137">執行個體名稱不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="22142-137">Instance names are not case sensitive.</span></span>  
  
-   <span data-ttu-id="22142-138">執行個體名稱不能以底線 (_) 開始或結束。</span><span class="sxs-lookup"><span data-stu-id="22142-138">Instance names cannot start or end with an underscore (_).</span></span>  
  
-   <span data-ttu-id="22142-139">執行個體名稱不得包含 "Default" 一詞或其他保留關鍵字。</span><span class="sxs-lookup"><span data-stu-id="22142-139">Instance names cannot contain the term "Default" or other reserved keywords.</span></span> <span data-ttu-id="22142-140">如果在執行個體名稱中使用了保留關鍵字，會發生安裝程式錯誤。</span><span class="sxs-lookup"><span data-stu-id="22142-140">If a reserved keyword is used in an instance name, a Setup error will occur.</span></span> <span data-ttu-id="22142-141">如需詳細資訊，請參閱[&#40;transact-sql&#41;的保留關鍵字](/sql/t-sql/language-elements/reserved-keywords-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="22142-141">For more information, see [Reserved Keywords &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reserved-keywords-transact-sql).</span></span>  
  
-   <span data-ttu-id="22142-142">如果您為執行個體名稱指定 MSSQLServer，將會建立預設執行個體。</span><span class="sxs-lookup"><span data-stu-id="22142-142">If you specify MSSQLServer for the instance name, a default instance will be created.</span></span>  
  
-   <span data-ttu-id="22142-143">安裝 [!INCLUDE[ssGeminiLong](../../includes/ssgeminilong-md.md)] 時，一律會安裝成 'PowerPivot' 的具名執行個體。</span><span class="sxs-lookup"><span data-stu-id="22142-143">An installation of [!INCLUDE[ssGeminiLong](../../includes/ssgeminilong-md.md)] is always installed as a named instance of 'PowerPivot'.</span></span> <span data-ttu-id="22142-144">您無法針對這個功能角色指定不同的執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="22142-144">You cannot specify a different instance name for this feature role.</span></span>  
  
-   <span data-ttu-id="22142-145">執行個體名稱限制為 16 個字元。</span><span class="sxs-lookup"><span data-stu-id="22142-145">Instance names are limited to 16 characters.</span></span>  
  
-   <span data-ttu-id="22142-146">執行個體名稱中的第一個字元必須是字母。</span><span class="sxs-lookup"><span data-stu-id="22142-146">The first character in the instance name must be a letter.</span></span> <span data-ttu-id="22142-147">可接受的字母是由 Unicode Standard 2.0 所定義的字母。</span><span class="sxs-lookup"><span data-stu-id="22142-147">Acceptable letters are those defined by the Unicode Standard 2.0.</span></span> <span data-ttu-id="22142-148">這些包括拉丁字元 a-z、A-Z 及其他語言的字母字元。</span><span class="sxs-lookup"><span data-stu-id="22142-148">These include Latin characters a-z, A-Z, and letter characters from other languages.</span></span>  
  
-   <span data-ttu-id="22142-149">後續字元可以是 Unicode 標準 2.0 定義的字母、基本拉丁文或其他國家 (地區) 指令碼中的十進位數字、錢幣符號($) 或底線 (_)。</span><span class="sxs-lookup"><span data-stu-id="22142-149">Subsequent characters can be letters defined by the Unicode Standard 2.0, decimal numbers from Basic Latin or other national scripts, the dollar sign ($), or an underscore (_).</span></span>  
  
-   <span data-ttu-id="22142-150">執行個體名稱中不允許內嵌空格或其他特殊字元。</span><span class="sxs-lookup"><span data-stu-id="22142-150">Embedded spaces or other special characters are not allowed in instance names.</span></span> <span data-ttu-id="22142-151">此外，也不允許反斜線 (\\)、逗號 (,)、冒號 (:)、分號 (;)、單引號 (')、＆ 符號 (&)、連字號 (-) 和 At 符號 (@)。</span><span class="sxs-lookup"><span data-stu-id="22142-151">The backslash (\\), comma (,), colon (:), semi-colon (;), single quote ('), ampersand (&), hyphen (-), and at sign (@) are also not allowed.</span></span>  
  
-   <span data-ttu-id="22142-152">**只有在目前 Windows 字碼頁中有效的字元可以用於 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 實例名稱。如果使用不支援的 Unicode 字元，將會發生安裝程式錯誤。**</span><span class="sxs-lookup"><span data-stu-id="22142-152">**Only characters that are valid in the current Windows code page can be used in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance names. If an unsupported Unicode character is used, a Setup error will occur.**</span></span>  
  
 <span data-ttu-id="22142-153">**偵測到的實例和功能**</span><span class="sxs-lookup"><span data-stu-id="22142-153">**Detected instances and features**</span></span>  
 <span data-ttu-id="22142-154">在執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝程式的電腦上檢視已安裝的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體和元件的清單。</span><span class="sxs-lookup"><span data-stu-id="22142-154">View a list of installed [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instances and components on the computer where [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup is running.</span></span>  
  
 <span data-ttu-id="22142-155">**執行個體識別碼** ：依預設，此執行個體名稱會當作執行個體識別碼使用。</span><span class="sxs-lookup"><span data-stu-id="22142-155">**Instance ID** - By default, the instance name is used as the Instance ID.</span></span> <span data-ttu-id="22142-156">這是用來識別 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體的安裝目錄和登錄機碼。</span><span class="sxs-lookup"><span data-stu-id="22142-156">This is used to identify installation directories and registry keys for your instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="22142-157">這是預設執行個體和具名執行個體的狀況。</span><span class="sxs-lookup"><span data-stu-id="22142-157">This is the case for default instances and named instances.</span></span> <span data-ttu-id="22142-158">如果是預設執行個體，執行個體名稱和執行個體識別碼將會是 MSSQLSERVER。</span><span class="sxs-lookup"><span data-stu-id="22142-158">For a default instance, the instance name and instance ID would be MSSQLSERVER.</span></span> <span data-ttu-id="22142-159">若要使用非預設的實例識別碼，請在 [**實例識別碼**] 欄位中指定它。</span><span class="sxs-lookup"><span data-stu-id="22142-159">To use a non-default instance ID, specify it in the **Instance ID** field.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="22142-160">透過 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SysPrep，顯示在這個頁面上的執行個體識別碼就是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SysPrep 程序之準備映像步驟期間所指定的執行個體識別碼。</span><span class="sxs-lookup"><span data-stu-id="22142-160">With [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SysPrep, the Instance ID displayed on this page is the Instance ID specified during the prepare image step of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SysPrep process.</span></span> <span data-ttu-id="22142-161">您無法在完成映像步驟期間指定不同的執行個體識別碼。</span><span class="sxs-lookup"><span data-stu-id="22142-161">You will not be able to specify a different Instance ID during the complete image step.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="22142-162">不支援以底線 (_) 為開頭或是包含數字符號 (#) 或貨幣符號 ($) 的執行個體識別碼。</span><span class="sxs-lookup"><span data-stu-id="22142-162">Instance IDs that begin with an underscore (_) or that contain the number sign (#) or the dollar sign ($) are not supported.</span></span>  
  
 <span data-ttu-id="22142-163">如需目錄、檔案位置和實例識別碼命名的詳細資訊，請參閱[SQL Server 預設和命名實例的檔案位置](../../../2014/sql-server/install/file-locations-for-default-and-named-instances-of-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="22142-163">For more information about directories, file locations, and instance ID naming, see [File Locations for Default and Named Instances of SQL Server](../../../2014/sql-server/install/file-locations-for-default-and-named-instances-of-sql-server.md).</span></span>  
  
 <span data-ttu-id="22142-164">給定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體的所有元件都會當做一個單位來管理。</span><span class="sxs-lookup"><span data-stu-id="22142-164">All components of a given instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] are managed as a unit.</span></span> <span data-ttu-id="22142-165">所有的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Service Pack 和升級項目都會套用至 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體的每一個元件。</span><span class="sxs-lookup"><span data-stu-id="22142-165">All [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service packs and upgrades will apply to every component of an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="22142-166">所有共用相同執行個體名稱之 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的所有元件，都必須符合下列準則：</span><span class="sxs-lookup"><span data-stu-id="22142-166">All components of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that share the same instance name must meet the following criteria:</span></span>  
  
-   <span data-ttu-id="22142-167">**相同版本**</span><span class="sxs-lookup"><span data-stu-id="22142-167">**Same version**</span></span>  
  
-   <span data-ttu-id="22142-168">**相同修訂版**</span><span class="sxs-lookup"><span data-stu-id="22142-168">**Same edition**</span></span>  
  
-   <span data-ttu-id="22142-169">**相同語言設定**</span><span class="sxs-lookup"><span data-stu-id="22142-169">**Same language settings**</span></span>  
  
-   <span data-ttu-id="22142-170">**相同叢集狀態**</span><span class="sxs-lookup"><span data-stu-id="22142-170">**Same clustered state**</span></span>  
  
    > [!NOTE]  
    >  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="22142-171">無法識別叢集。</span><span class="sxs-lookup"><span data-stu-id="22142-171">is not cluster-aware.</span></span>  
  
-   <span data-ttu-id="22142-172">**相同作業系統**</span><span class="sxs-lookup"><span data-stu-id="22142-172">**Same operating system**</span></span>  
  
  
