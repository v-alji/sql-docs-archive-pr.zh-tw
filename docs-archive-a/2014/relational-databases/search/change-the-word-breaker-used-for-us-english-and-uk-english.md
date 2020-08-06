---
title: 變更用於美式英文與英式英文的斷詞工具 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
ms.assetid: 6b5d2177-db98-47f5-b32e-4b80a2f74ffe
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 3b759b90ec834dcb666f7862bfba3857f2fea0d2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596621"
---
# <a name="change-the-word-breaker-used-for-us-english-and-uk-english"></a><span data-ttu-id="fc6c5-102">Change the Word Breaker Used for US English and UK English</span><span class="sxs-lookup"><span data-stu-id="fc6c5-102">Change the Word Breaker Used for US English and UK English</span></span>
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="fc6c5-103">會安裝適用於英文的新版 (14.0.4999.1038 版) 斷詞工具和字幹分析器，並取代這些舊版元件 (12.0.6828.0 版)。</span><span class="sxs-lookup"><span data-stu-id="fc6c5-103">installs a new version (version 14.0.4999.1038) of the word breaker and stemmer for the English language, replacing the previous version of these components (version 12.0.6828.0).</span></span> <span data-ttu-id="fc6c5-104">如需新元件行為變更的詳細資訊，請參閱 [全文檢索搜尋的行為變更](full-text-search.md)。</span><span class="sxs-lookup"><span data-stu-id="fc6c5-104">For information about the changed behavior of the new components, see [Behavior Changes to Full-Text Search](full-text-search.md).</span></span> <span data-ttu-id="fc6c5-105">本主題描述的是如何從新版元件切換成舊版，或從舊版切換回新版。</span><span class="sxs-lookup"><span data-stu-id="fc6c5-105">This topic describes how to switch from the new version of these components to the previous version, or to switch back from the previous version to the new version.</span></span> <span data-ttu-id="fc6c5-106">若為叢集安裝，就應該在所有主要和被動節點上進行這些變更。</span><span class="sxs-lookup"><span data-stu-id="fc6c5-106">For cluster installations, these changes should be made on all the primary and passive nodes.</span></span>  
  
 <span data-ttu-id="fc6c5-107">舊版 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用了由美式英文 (LCID 1033) 和英式英文 (LCID 2057) 之不同 CLSID 所代表的不同斷詞工具。</span><span class="sxs-lookup"><span data-stu-id="fc6c5-107">Previous versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] used different word breakers represented by different CLSIDs for US English (LCID 1033) and UK English (LCID 2057).</span></span> <span data-ttu-id="fc6c5-108">在這個版本中，這兩個 LCID 都使用具有相同 CLSID 的相同元件，如下表所示：</span><span class="sxs-lookup"><span data-stu-id="fc6c5-108">In this release, both LCIDs use the same components with the same CLSIDs, as shown in the following table:</span></span>  
  
|<span data-ttu-id="fc6c5-109">LCID</span><span class="sxs-lookup"><span data-stu-id="fc6c5-109">LCID</span></span>|<span data-ttu-id="fc6c5-110">舊版所安裝的斷詞工具</span><span class="sxs-lookup"><span data-stu-id="fc6c5-110">Word breaker installed by previous versions</span></span><br /><br /> <span data-ttu-id="fc6c5-111">12.0.6828.0 版</span><span class="sxs-lookup"><span data-stu-id="fc6c5-111">version 12.0.6828.0</span></span>|<span data-ttu-id="fc6c5-112">舊版所安裝的字幹分析器</span><span class="sxs-lookup"><span data-stu-id="fc6c5-112">Stemmer installed by previous versions</span></span>|<span data-ttu-id="fc6c5-113">這個版本所安裝的斷詞工具</span><span class="sxs-lookup"><span data-stu-id="fc6c5-113">Word breaker installed by this version</span></span><br /><br /> <span data-ttu-id="fc6c5-114">14.0.4999.1038 版</span><span class="sxs-lookup"><span data-stu-id="fc6c5-114">version 14.0.4999.1038</span></span>|<span data-ttu-id="fc6c5-115">這個版本所安裝的字幹分析器</span><span class="sxs-lookup"><span data-stu-id="fc6c5-115">Stemmer installed by this version</span></span>|  
|----------|-------------------------------------------------------------------------|--------------------------------------------|-----------------------------------------------------------------------|---------------------------------------|  
|<span data-ttu-id="fc6c5-116">1033</span><span class="sxs-lookup"><span data-stu-id="fc6c5-116">1033</span></span><br /><span data-ttu-id="fc6c5-117">(美式英文)</span><span class="sxs-lookup"><span data-stu-id="fc6c5-117">(US English)</span></span>|<span data-ttu-id="fc6c5-118">188D6CC5-CB03-4C01-912E-47D21295D77E</span><span class="sxs-lookup"><span data-stu-id="fc6c5-118">188D6CC5-CB03-4C01-912E-47D21295D77E</span></span>|<span data-ttu-id="fc6c5-119">EEED4C20-7F1B-11CE-BE57-00AA0051FE20</span><span class="sxs-lookup"><span data-stu-id="fc6c5-119">EEED4C20-7F1B-11CE-BE57-00AA0051FE20</span></span>|<span data-ttu-id="fc6c5-120">9faed859-0b30-4434-ae65-412e14a16fb8</span><span class="sxs-lookup"><span data-stu-id="fc6c5-120">9faed859-0b30-4434-ae65-412e14a16fb8</span></span>|<span data-ttu-id="fc6c5-121">e1e5ef84-c4a6-4e50-8188-99aef3de2659</span><span class="sxs-lookup"><span data-stu-id="fc6c5-121">e1e5ef84-c4a6-4e50-8188-99aef3de2659</span></span>|  
|<span data-ttu-id="fc6c5-122">2057</span><span class="sxs-lookup"><span data-stu-id="fc6c5-122">2057</span></span><br /><span data-ttu-id="fc6c5-123">(英式英文)</span><span class="sxs-lookup"><span data-stu-id="fc6c5-123">(UK English)</span></span>|<span data-ttu-id="fc6c5-124">173C97E2-AEBE-437C-9445-01B237ABF2F6</span><span class="sxs-lookup"><span data-stu-id="fc6c5-124">173C97E2-AEBE-437C-9445-01B237ABF2F6</span></span>|<span data-ttu-id="fc6c5-125">D99F7670-7F1A-11CE-BE57-00AA0051FE20</span><span class="sxs-lookup"><span data-stu-id="fc6c5-125">D99F7670-7F1A-11CE-BE57-00AA0051FE20</span></span>|<span data-ttu-id="fc6c5-126">9faed859-0b30-4434-ae65-412e14a16fb8</span><span class="sxs-lookup"><span data-stu-id="fc6c5-126">9faed859-0b30-4434-ae65-412e14a16fb8</span></span>|<span data-ttu-id="fc6c5-127">e1e5ef84-c4a6-4e50-8188-99aef3de2659</span><span class="sxs-lookup"><span data-stu-id="fc6c5-127">e1e5ef84-c4a6-4e50-8188-99aef3de2659</span></span>|  
  
 <span data-ttu-id="fc6c5-128">本主題所描述的元件是安裝在 `MSSQL\Binn` 執行個體之 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料夾中的 DLL 檔案。</span><span class="sxs-lookup"><span data-stu-id="fc6c5-128">The components described in this topic are DLL files that are installed in the `MSSQL\Binn` folder for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="fc6c5-129">完整路徑通常是 `C:\Program Files\Microsoft SQL Server\<instance>\MSSQL\Binn`。</span><span class="sxs-lookup"><span data-stu-id="fc6c5-129">The full path is typically `C:\Program Files\Microsoft SQL Server\<instance>\MSSQL\Binn`.</span></span>  
  
 <span data-ttu-id="fc6c5-130">如需斷詞工具與字幹分析器的詳細資訊，請參閱 [設定及管理搜尋的斷詞工具與字幹分析器](configure-and-manage-word-breakers-and-stemmers-for-search.md)。</span><span class="sxs-lookup"><span data-stu-id="fc6c5-130">For more information about word breakers and stemmers, see [Configure and Manage Word Breakers and Stemmers for Search](configure-and-manage-word-breakers-and-stemmers-for-search.md).</span></span>  
  
## <a name="switching-from-the-current-english-word-breaker-to-the-previous-english-word-breakers"></a><span data-ttu-id="fc6c5-131">從目前的英文斷詞工具切換成先前的英文斷詞工具</span><span class="sxs-lookup"><span data-stu-id="fc6c5-131">Switching from the current English word breaker to the previous English word breakers</span></span>  
  
#### <a name="to-switch-from-the-current-version-of-the-us-english-word-breaker-to-the-previous-version"></a><span data-ttu-id="fc6c5-132">若要從目前版本的美式英文斷詞工具切換成舊版</span><span class="sxs-lookup"><span data-stu-id="fc6c5-132">To switch from the current version of the US English word breaker to the previous version</span></span>  
  
1.  <span data-ttu-id="fc6c5-133">在登錄中，巡覽至下列節點：**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<執行個體根目錄\>\MSSearch\CLSID**。</span><span class="sxs-lookup"><span data-stu-id="fc6c5-133">In the registry, navigate to the following node: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<InstanceRoot\>\MSSearch\CLSID**.</span></span>  
  
2.  <span data-ttu-id="fc6c5-134">使用下列步驟，針對 LCID 1033 的舊版美式英文斷詞工具和字幹分析器介面加入 COM ClassID 的新機碼：</span><span class="sxs-lookup"><span data-stu-id="fc6c5-134">Use the following steps to add new keyS for the COM ClassIDs for the previous US English word breaker and stemmer interfaces for LCID 1033:</span></span>  
  
    1.  <span data-ttu-id="fc6c5-135">針對先前的斷詞工具，加入含有 **{188D6CC5-CB03-4C01-912E-47D21295D77E}** 值的新機碼。</span><span class="sxs-lookup"><span data-stu-id="fc6c5-135">Add a new key with the value **{188D6CC5-CB03-4C01-912E-47D21295D77E}** for the previous word breaker.</span></span>  
  
    2.  <span data-ttu-id="fc6c5-136">將該機碼值的 (預設) 資料更新為 **langwrbk.dll**。</span><span class="sxs-lookup"><span data-stu-id="fc6c5-136">Update the (Default) data of that key value to **langwrbk.dll**.</span></span>  
  
    3.  <span data-ttu-id="fc6c5-137">針對先前的字幹分析器，加入含有 **{EEED4C20-7F1B-11CE-BE57-00AA0051FE20}** 值的新機碼。</span><span class="sxs-lookup"><span data-stu-id="fc6c5-137">Add a new key with the value **{EEED4C20-7F1B-11CE-BE57-00AA0051FE20}** for the previous stemmer.</span></span>  
  
    4.  <span data-ttu-id="fc6c5-138">將該機碼值的 (預設) 資料更新為 **infosoft.dll**。</span><span class="sxs-lookup"><span data-stu-id="fc6c5-138">Update the (Default) data of that key value to **infosoft.dll**.</span></span>  
  
3.  <span data-ttu-id="fc6c5-139">在登錄中，巡覽至下列節點：**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<執行個體根目錄\>\MSSearch\Language\enu**。</span><span class="sxs-lookup"><span data-stu-id="fc6c5-139">In the registry, navigate to the following node: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<InstanceRoot\>\MSSearch\Language\enu**.</span></span>  
  
4.  <span data-ttu-id="fc6c5-140">將 **WBreakerClass** 機碼值更新為 **{188D6CC5-CB03-4C01-912E-47D21295D77E}** 。</span><span class="sxs-lookup"><span data-stu-id="fc6c5-140">Update the **WBreakerClass** key value to **{188D6CC5-CB03-4C01-912E-47D21295D77E}**.</span></span>  
  
5.  <span data-ttu-id="fc6c5-141">將 **StemmerClass** 機碼值更新為 **{EEED4C20-7F1B-11CE-BE57-00AA0051FE20}** 。</span><span class="sxs-lookup"><span data-stu-id="fc6c5-141">Update the **StemmerClass** key value to **{EEED4C20-7F1B-11CE-BE57-00AA0051FE20}**.</span></span>  
  
6.  <span data-ttu-id="fc6c5-142">重新啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="fc6c5-142">Restart [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
#### <a name="to-switch-from-the-current-version-of-the-uk-english-word-breaker-to-the-previous-version"></a><span data-ttu-id="fc6c5-143">若要從目前版本的英式英文斷詞工具切換成舊版</span><span class="sxs-lookup"><span data-stu-id="fc6c5-143">To switch from the current version of the UK English word breaker to the previous version</span></span>  
  
1.  <span data-ttu-id="fc6c5-144">在登錄中，巡覽至下列節點：**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<執行個體根目錄\>\MSSearch\CLSID**。</span><span class="sxs-lookup"><span data-stu-id="fc6c5-144">In the registry, navigate to the following node: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<InstanceRoot\>\MSSearch\CLSID**.</span></span>  
  
2.  <span data-ttu-id="fc6c5-145">使用下列步驟，針對 LCID 2057 的先前英式英文斷詞工具和字幹分析器介面加入 COM ClassID 的新機碼：</span><span class="sxs-lookup"><span data-stu-id="fc6c5-145">Use the following steps to add a new key for the COM ClassIDs for the previous UK English word breaker and stemmer interfaces for LCID 2057:</span></span>  
  
    1.  <span data-ttu-id="fc6c5-146">針對先前的斷詞工具，加入含有 **{173C97E2-AEBE-437C-9445-01B237ABF2F6}** 值的新機碼。</span><span class="sxs-lookup"><span data-stu-id="fc6c5-146">Add a new key with the value **{173C97E2-AEBE-437C-9445-01B237ABF2F6}** for the previous word breaker.</span></span>  
  
    2.  <span data-ttu-id="fc6c5-147">將該機碼值的 (預設) 資料更新為 **langwrbk.dll**。</span><span class="sxs-lookup"><span data-stu-id="fc6c5-147">Update the (Default) data of that key value to **langwrbk.dll**.</span></span>  
  
    3.  <span data-ttu-id="fc6c5-148">針對先前的字幹分析器，加入含有 **{D99F7670-7F1A-11CE-BE57-00AA0051FE20}** 值的新機碼。</span><span class="sxs-lookup"><span data-stu-id="fc6c5-148">Add a new key with the value **{D99F7670-7F1A-11CE-BE57-00AA0051FE20}** for the previous stemmer.</span></span>  
  
    4.  <span data-ttu-id="fc6c5-149">將該機碼值的 (預設) 資料更新為 **infosoft.dll**。</span><span class="sxs-lookup"><span data-stu-id="fc6c5-149">Update the (Default) data of that key value to **infosoft.dll**.</span></span>  
  
3.  <span data-ttu-id="fc6c5-150">在登錄中，巡覽至下列節點：**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<執行個體根目錄\>\MSSearch\Language\eng**。</span><span class="sxs-lookup"><span data-stu-id="fc6c5-150">In the registry, navigate to the following node: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<InstanceRoot\>\MSSearch\Language\eng**.</span></span>  
  
4.  <span data-ttu-id="fc6c5-151">將 **WBreakerClass** 機碼值更新為 **{173C97E2-AEBE-437C-9445-01B237ABF2F6}** 。</span><span class="sxs-lookup"><span data-stu-id="fc6c5-151">Update the **WBreakerClass** key value to **{173C97E2-AEBE-437C-9445-01B237ABF2F6}**.</span></span>  
  
5.  <span data-ttu-id="fc6c5-152">將 **StemmerClass** 機碼值更新為 **{D99F7670-7F1A-11CE-BE57-00AA0051FE20}** 。</span><span class="sxs-lookup"><span data-stu-id="fc6c5-152">Update the **StemmerClass** key value to **{D99F7670-7F1A-11CE-BE57-00AA0051FE20}**.</span></span>  
  
6.  <span data-ttu-id="fc6c5-153">重新啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="fc6c5-153">Restart [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="switching-back-from-the-previous-english-word-breakers-to-the-current-english-word-breaker"></a><span data-ttu-id="fc6c5-154">從先前的英文斷詞工具切換回目前的英文斷詞工具</span><span class="sxs-lookup"><span data-stu-id="fc6c5-154">Switching back from the previous English word breakers to the current English word breaker</span></span>  
  
#### <a name="to-switch-back-from-the-previous-version-of-the-us-english-word-breaker-to-the-current-version"></a><span data-ttu-id="fc6c5-155">若要從舊版的美式英文斷詞工具切換回目前版本</span><span class="sxs-lookup"><span data-stu-id="fc6c5-155">To switch back from the previous version of the US English word breaker to the current version</span></span>  
  
1.  <span data-ttu-id="fc6c5-156">在登錄中，巡覽至下列節點：**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<執行個體根目錄\>\MSSearch\CLSID**。</span><span class="sxs-lookup"><span data-stu-id="fc6c5-156">In the registry, navigate to the following node: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<InstanceRoot\>\MSSearch\CLSID**.</span></span>  
  
2.  <span data-ttu-id="fc6c5-157">如果下列機碼不存在，請使用下列步驟，針對 LCID 1033 的目前美式英文斷詞工具和字幹分析器介面加入 COM ClassID 的新機碼：</span><span class="sxs-lookup"><span data-stu-id="fc6c5-157">If the following keys do not exist, then use the following steps to add a new key for the COM ClassIDs for the current US English word breaker and stemmer interfaces for LCID 1033:</span></span>  
  
    1.  <span data-ttu-id="fc6c5-158">針對目前的斷詞工具，加入含有 **{9faed859-0b30-4434-ae65-412e14a16fb8}** 值的新機碼。</span><span class="sxs-lookup"><span data-stu-id="fc6c5-158">Add a new key with the value **{9faed859-0b30-4434-ae65-412e14a16fb8}** for the current word breaker.</span></span>  
  
    2.  <span data-ttu-id="fc6c5-159">將該機碼值的 (預設) 資料更新為 **MsWb7.dll**。</span><span class="sxs-lookup"><span data-stu-id="fc6c5-159">Update the (Default) data of that key value to **MsWb7.dll**.</span></span>  
  
    3.  <span data-ttu-id="fc6c5-160">針對目前的字幹分析器，加入含有 **{e1e5ef84-c4a6-4e50-8188-99aef3de2659}** 值的新機碼。</span><span class="sxs-lookup"><span data-stu-id="fc6c5-160">Add a new key with the value **{e1e5ef84-c4a6-4e50-8188-99aef3de2659}** for the current stemmer.</span></span>  
  
    4.  <span data-ttu-id="fc6c5-161">將該機碼值的 (預設) 資料更新為 **MsWb7.dll**。</span><span class="sxs-lookup"><span data-stu-id="fc6c5-161">Update the (Default) data of that key value to **MsWb7.dll**.</span></span>  
  
3.  <span data-ttu-id="fc6c5-162">在登錄中，巡覽至下列節點：**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<執行個體根目錄\>\MSSearch\Language\eng**。</span><span class="sxs-lookup"><span data-stu-id="fc6c5-162">In the registry, navigate to the following node: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<InstanceRoot\>\MSSearch\Language\eng**.</span></span>  
  
4.  <span data-ttu-id="fc6c5-163">將 **WBreakerClass** 機碼值更新為 **{9faed859-0b30-4434-ae65-412e14a16fb8}** 。</span><span class="sxs-lookup"><span data-stu-id="fc6c5-163">Update the **WBreakerClass** key value to **{9faed859-0b30-4434-ae65-412e14a16fb8}**.</span></span>  
  
5.  <span data-ttu-id="fc6c5-164">將 **StemmerClass** 機碼值更新為 **{e1e5ef84-c4a6-4e50-8188-99aef3de2659}** 。</span><span class="sxs-lookup"><span data-stu-id="fc6c5-164">Update the **StemmerClass** key value to **{e1e5ef84-c4a6-4e50-8188-99aef3de2659}**.</span></span>  
  
6.  <span data-ttu-id="fc6c5-165">重新啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="fc6c5-165">Restart [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
#### <a name="to-switch-back-from-the-previous-version-of-the-uk-english-word-breaker-to-the-current-version"></a><span data-ttu-id="fc6c5-166">若要從舊版的英式英文斷詞工具切換回目前版本</span><span class="sxs-lookup"><span data-stu-id="fc6c5-166">To switch back from the previous version of the UK English word breaker to the current version</span></span>  
  
1.  <span data-ttu-id="fc6c5-167">在登錄中，巡覽至下列節點：**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<執行個體根目錄\>\MSSearch\CLSID**。</span><span class="sxs-lookup"><span data-stu-id="fc6c5-167">In the registry, navigate to the following node: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<InstanceRoot\>\MSSearch\CLSID**.</span></span>  
  
2.  <span data-ttu-id="fc6c5-168">如果下列機碼不存在，請使用下列步驟，針對 LCID 2057 的目前英式英文斷詞工具和字幹分析器介面加入 COM ClassID 的新機碼：</span><span class="sxs-lookup"><span data-stu-id="fc6c5-168">If the following keys do not exist, then use the following steps to add a new key for the COM ClassIDs for the current UK English word breaker and stemmer interfaces for LCID 2057:</span></span>  
  
    1.  <span data-ttu-id="fc6c5-169">針對目前的斷詞工具，加入含有 **{9faed859-0b30-4434-ae65-412e14a16fb8}** 值的新機碼。</span><span class="sxs-lookup"><span data-stu-id="fc6c5-169">Add a new key with the value **{9faed859-0b30-4434-ae65-412e14a16fb8}** for the current word breaker.</span></span>  
  
    2.  <span data-ttu-id="fc6c5-170">將該機碼值的 (預設) 資料更新為 **MsWb7.dll**。</span><span class="sxs-lookup"><span data-stu-id="fc6c5-170">Update the (Default) data of that key value to **MsWb7.dll**.</span></span>  
  
    3.  <span data-ttu-id="fc6c5-171">針對目前的字幹分析器，加入含有 **{e1e5ef84-c4a6-4e50-8188-99aef3de2659}** 值的新機碼。</span><span class="sxs-lookup"><span data-stu-id="fc6c5-171">Add a new key with the value **{e1e5ef84-c4a6-4e50-8188-99aef3de2659}** for the current stemmer.</span></span>  
  
    4.  <span data-ttu-id="fc6c5-172">將該機碼值的 (預設) 資料更新為 **MsWb7.dll**。</span><span class="sxs-lookup"><span data-stu-id="fc6c5-172">Update the (Default) data of that key value to **MsWb7.dll**.</span></span>  
  
3.  <span data-ttu-id="fc6c5-173">在登錄中，巡覽至下列節點：**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<執行個體根目錄\>\MSSearch\Language\eng**。</span><span class="sxs-lookup"><span data-stu-id="fc6c5-173">In the registry, navigate to the following node: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<InstanceRoot\>\MSSearch\Language\eng**.</span></span>  
  
4.  <span data-ttu-id="fc6c5-174">將 **WBreakerClass** 機碼值更新為 **{9faed859-0b30-4434-ae65-412e14a16fb8}** 。</span><span class="sxs-lookup"><span data-stu-id="fc6c5-174">Update the **WBreakerClass** key value to **{9faed859-0b30-4434-ae65-412e14a16fb8}**.</span></span>  
  
5.  <span data-ttu-id="fc6c5-175">將 **StemmerClass** 機碼值更新為 **{e1e5ef84-c4a6-4e50-8188-99aef3de2659}** 。</span><span class="sxs-lookup"><span data-stu-id="fc6c5-175">Update the **StemmerClass** key value to **{e1e5ef84-c4a6-4e50-8188-99aef3de2659}**.</span></span>  
  
6.  <span data-ttu-id="fc6c5-176">重新啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="fc6c5-176">Restart [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc6c5-177">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fc6c5-177">See Also</span></span>  
 <span data-ttu-id="fc6c5-178">[將搜索所使用的斷詞工具還原為舊版](revert-the-word-breakers-used-by-search-to-the-previous-version.md) </span><span class="sxs-lookup"><span data-stu-id="fc6c5-178">[Revert the Word Breakers Used by Search to the Previous Version](revert-the-word-breakers-used-by-search-to-the-previous-version.md) </span></span>  
 [<span data-ttu-id="fc6c5-179">全文檢索搜尋的行為變更</span><span class="sxs-lookup"><span data-stu-id="fc6c5-179">Behavior Changes to Full-Text Search</span></span>](full-text-search.md)  
  
  
