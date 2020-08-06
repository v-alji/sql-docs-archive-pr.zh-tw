---
title: 藉由設定登錄值來執行簽署原則 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- signing policies [Integration Services]
ms.assetid: 64f6966f-2292-401f-acb1-2ccb5aee484a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1e844b65df5b45f212554f7583f4e4b327b740e0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592124"
---
# <a name="implement-a-signing-policy-by-setting-a-registry-value"></a><span data-ttu-id="ef860-102">透過設定登錄值實作簽署原則</span><span class="sxs-lookup"><span data-stu-id="ef860-102">Implement a Signing Policy by Setting a Registry Value</span></span>
  <span data-ttu-id="ef860-103">您可以使用選擇性登錄值來管理載入已簽署或未簽署之封裝的組織原則。</span><span class="sxs-lookup"><span data-stu-id="ef860-103">You can use an optional registry value to manage an organization's policy for loading signed or unsigned packages.</span></span> <span data-ttu-id="ef860-104">如果您使用這個登錄值，就必須在即將執行 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 封裝而且想要強制執行此原則的每部電腦上建立這個登錄值。</span><span class="sxs-lookup"><span data-stu-id="ef860-104">If you use this registry value, you must create this registry value on each computer on which [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] packages will run and on which you want to enforce the policy.</span></span> <span data-ttu-id="ef860-105">設定此登錄值之後， [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 就會檢查或確認簽章，然後再載入封裝。</span><span class="sxs-lookup"><span data-stu-id="ef860-105">After the registry value has been set, [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] will check or verify the signatures before loading packages.</span></span>  
  
 <span data-ttu-id="ef860-106">本主題中的此程序說明如何將選擇性的 `BlockedSignatureStates` DWORD 值加入 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\100\SSIS 登錄機碼。</span><span class="sxs-lookup"><span data-stu-id="ef860-106">This procedure in this topic describes how to add the optional `BlockedSignatureStates` DWORD value to the HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\100\SSIS registry key.</span></span> <span data-ttu-id="ef860-107">`BlockedSignatureStates` 的資料值可指定當封裝包含不受信任的簽章、無效的簽章或未簽署時，是否應該加以封鎖。</span><span class="sxs-lookup"><span data-stu-id="ef860-107">The data value in `BlockedSignatureStates` determines whether a package should be blocked if it has an untrusted signature, has an invalid signature, or is unsigned.</span></span> <span data-ttu-id="ef860-108">對於用以簽署封裝的簽章狀態，`BlockedSignatureStates` 登錄值會使用下列定義：</span><span class="sxs-lookup"><span data-stu-id="ef860-108">With regard to the status of signatures used to sign packages, the `BlockedSignatureStates` registry value uses the following definitions:</span></span>  
  
-   <span data-ttu-id="ef860-109">「有效簽章」  是指可以成功讀取的簽章。</span><span class="sxs-lookup"><span data-stu-id="ef860-109">A *valid signature* is one that can be read successfully.</span></span>  
  
-   <span data-ttu-id="ef860-110">「無效簽章」  是指簽章的解密總和檢查碼 (由私密金鑰加密之封裝程式碼的單向雜湊) 與載入 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 封裝程序中導出的解密總和檢查碼不符。</span><span class="sxs-lookup"><span data-stu-id="ef860-110">An *invalid signature* is one for which the decrypted checksum (the one-way hash of the package code encrypted by a private key) does not match the decrypted checksum that is calculated as part of the process of loading [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] packages.</span></span>  
  
-   <span data-ttu-id="ef860-111">「信任簽章」  是指使用由信任根憑證授權單位簽署的數位憑證所建立的簽章。</span><span class="sxs-lookup"><span data-stu-id="ef860-111">A *trusted signature* is one that is created by using a digital certificate signed by a Trusted Root Certification Authority.</span></span> <span data-ttu-id="ef860-112">使用此設定時，簽署者不必出現在使用者的「受信任的發行者」清單中。</span><span class="sxs-lookup"><span data-stu-id="ef860-112">This setting does not require the signer to be found in the user's list of Trusted Publishers.</span></span>  
  
-   <span data-ttu-id="ef860-113">「不受信任的簽章」  是指無法確認為信任根憑證授權單位所發出的簽章，或不是目前的簽章。</span><span class="sxs-lookup"><span data-stu-id="ef860-113">An *untrusted signature* is one that cannot be verified as issued by a Trusted Root Certification Authority, or a signature that is not current.</span></span>  
  
 <span data-ttu-id="ef860-114">下表列出 DWORD 資料的有效值及其相關聯的原則。</span><span class="sxs-lookup"><span data-stu-id="ef860-114">The following table lists the valid values of the DWORD data and their associated policy.</span></span>  
  
|<span data-ttu-id="ef860-115">值</span><span class="sxs-lookup"><span data-stu-id="ef860-115">Value</span></span>|<span data-ttu-id="ef860-116">描述</span><span class="sxs-lookup"><span data-stu-id="ef860-116">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ef860-117">0</span><span class="sxs-lookup"><span data-stu-id="ef860-117">0</span></span>|<span data-ttu-id="ef860-118">沒有管理限制。</span><span class="sxs-lookup"><span data-stu-id="ef860-118">No administrative restriction.</span></span>|  
|<span data-ttu-id="ef860-119">1</span><span class="sxs-lookup"><span data-stu-id="ef860-119">1</span></span>|<span data-ttu-id="ef860-120">封鎖無效的簽章。</span><span class="sxs-lookup"><span data-stu-id="ef860-120">Block invalid signatures.</span></span><br /><br /> <span data-ttu-id="ef860-121">此設定不會封鎖未簽署的封裝。</span><span class="sxs-lookup"><span data-stu-id="ef860-121">This setting does not block unsigned packages.</span></span>|  
|<span data-ttu-id="ef860-122">2</span><span class="sxs-lookup"><span data-stu-id="ef860-122">2</span></span>|<span data-ttu-id="ef860-123">封鎖無效及不受信任的簽章。</span><span class="sxs-lookup"><span data-stu-id="ef860-123">Block invalid and untrusted signatures.</span></span><br /><br /> <span data-ttu-id="ef860-124">此設定不會封鎖未簽署的封裝，但是會封鎖自我產生的簽章。</span><span class="sxs-lookup"><span data-stu-id="ef860-124">This setting does not block unsigned packages, but blocks self-generated signatures.</span></span>|  
|<span data-ttu-id="ef860-125">3</span><span class="sxs-lookup"><span data-stu-id="ef860-125">3</span></span>|<span data-ttu-id="ef860-126">封鎖無效和不受信任的簽章以及未簽署的封裝</span><span class="sxs-lookup"><span data-stu-id="ef860-126">Block invalid and untrusted signatures and unsigned packages</span></span><br /><br /> <span data-ttu-id="ef860-127">此設定也會封鎖自我產生的簽章。</span><span class="sxs-lookup"><span data-stu-id="ef860-127">This setting also blocks self-generated signatures.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="ef860-128">`BlockedSignatureStates` 的建議設定為 3。</span><span class="sxs-lookup"><span data-stu-id="ef860-128">The recommended setting for `BlockedSignatureStates` is 3.</span></span> <span data-ttu-id="ef860-129">此設定會提供最大程度的保護，以防範無效或不受信任的未簽署封裝或簽章。</span><span class="sxs-lookup"><span data-stu-id="ef860-129">This setting provides the greatest protection against unsigned packages or signatures that are either not valid or untrusted.</span></span> <span data-ttu-id="ef860-130">但是，建議設定未必適合所有情況。</span><span class="sxs-lookup"><span data-stu-id="ef860-130">However, the recommended setting may not be appropriate in all circumstances.</span></span> <span data-ttu-id="ef860-131">如需簽署數位資產的詳細資訊，請參閱 MSDN Library 中的[Introduction to Code Signing](https://go.microsoft.com/fwlink/?LinkId=51414)(程式碼簽署簡介) 主題。</span><span class="sxs-lookup"><span data-stu-id="ef860-131">For more information about signing digital assets, see the topic, "[Introduction to Code Signing](https://go.microsoft.com/fwlink/?LinkId=51414)," in the MSDN Library.</span></span>  
  
### <a name="to-implement-a-signing-policy-for-packages"></a><span data-ttu-id="ef860-132">實作封裝的簽署原則</span><span class="sxs-lookup"><span data-stu-id="ef860-132">To implement a signing policy for packages</span></span>  
  
1.  <span data-ttu-id="ef860-133">在 **[開始]** 功能表上，按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="ef860-133">On the **Start** menu, click **Run**.</span></span>  
  
2.  <span data-ttu-id="ef860-134">在 [執行] 對話方塊中，輸入 `Regedit` ，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="ef860-134">In the Run dialog box, type `Regedit`, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="ef860-135">找出登錄機碼 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\100\SSIS。</span><span class="sxs-lookup"><span data-stu-id="ef860-135">Locate the registry key, HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\100\SSIS.</span></span>  
  
4.  <span data-ttu-id="ef860-136">以滑鼠右鍵按一下 [MSDTS]  ，指向 [新增]  ，然後按一下 [DWORD 值]  。</span><span class="sxs-lookup"><span data-stu-id="ef860-136">Right-click **MSDTS**, point to **New**, and then click **DWORD Value**.</span></span>  
  
5.  <span data-ttu-id="ef860-137">將新值的名稱更新為 `BlockedSignatureStates`。</span><span class="sxs-lookup"><span data-stu-id="ef860-137">Update the name of the new value to `BlockedSignatureStates`.</span></span>  
  
6.  <span data-ttu-id="ef860-138">按一下滑鼠右鍵 `BlockedSignatureStates` ，然後按一下 [**修改**]。</span><span class="sxs-lookup"><span data-stu-id="ef860-138">Right-click `BlockedSignatureStates` and click **Modify**.</span></span>  
  
7.  <span data-ttu-id="ef860-139">在 [編輯 DWORD 值]  對話方塊中，輸入值 0、1、2 或 3。</span><span class="sxs-lookup"><span data-stu-id="ef860-139">In the **Edit DWORD Value** dialog box, type the value 0, 1, 2, or 3.</span></span>  
  
8.  <span data-ttu-id="ef860-140">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="ef860-140">Click **OK**.</span></span>  
  
9. <span data-ttu-id="ef860-141">在 **[檔案]** 功能表上按一下 **[結束]** 。</span><span class="sxs-lookup"><span data-stu-id="ef860-141">On the **File** menu, click **Exit**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef860-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ef860-142">See Also</span></span>  
 <span data-ttu-id="ef860-143">[安全性總覽 &#40;Integration Services&#41;](security/security-overview-integration-services.md) </span><span class="sxs-lookup"><span data-stu-id="ef860-143">[Security Overview &#40;Integration Services&#41;](security/security-overview-integration-services.md) </span></span>  
 [<span data-ttu-id="ef860-144">使用數位簽章來識別封裝的來源</span><span class="sxs-lookup"><span data-stu-id="ef860-144">Identify the Source of Packages with Digital Signatures</span></span>](security/identify-the-source-of-packages-with-digital-signatures.md)  
  
  
