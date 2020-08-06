---
title: 使用數位憑證來簽署封裝 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- digital signatures [Integration Services]
- signing packages [Integration Services]
- signatures [Integration Services]
ms.assetid: 182b115e-0fe2-4717-8dff-183f9eb6e397
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 6bd0f73d609623f882e474c96a01cd3bc0274b6b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709718"
---
# <a name="sign-a-package-by-using-a-digital-certificate"></a><span data-ttu-id="a17e5-102">使用數位憑證來簽署封裝</span><span class="sxs-lookup"><span data-stu-id="a17e5-102">Sign a Package by Using a Digital Certificate</span></span>
  <span data-ttu-id="a17e5-103">此主題描述如何使用數位憑證來簽署 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 封裝。</span><span class="sxs-lookup"><span data-stu-id="a17e5-103">This topic describes how to sign an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package with a digital certificate.</span></span> <span data-ttu-id="a17e5-104">您可以使用數位簽章搭配其他設定，防止無效的封裝載入並執行。</span><span class="sxs-lookup"><span data-stu-id="a17e5-104">You can use a digital signature, together with other settings, to prevent a package that is not valid from loading and running.</span></span>  
  
 <span data-ttu-id="a17e5-105">簽署 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 封裝之前，您必須執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="a17e5-105">Before you can sign an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package, you must do the following tasks:</span></span>  
  
-   <span data-ttu-id="a17e5-106">建立或取得要與憑證建立關聯的私密金鑰，然後將此私密金鑰儲存在本機電腦上。</span><span class="sxs-lookup"><span data-stu-id="a17e5-106">Create or obtain a private key to associate with the certificate, and store this private key on the local computer.</span></span>  
  
-   <span data-ttu-id="a17e5-107">向信任的憑證授權單位取得用於程式碼簽署的憑證。</span><span class="sxs-lookup"><span data-stu-id="a17e5-107">Obtain a certificate for the purpose of code signing from a trusted certification authority.</span></span> <span data-ttu-id="a17e5-108">您可以使用下列其中一種方法來取得或建立憑證：</span><span class="sxs-lookup"><span data-stu-id="a17e5-108">You can use one of the following methods to obtain or create a certificate:</span></span>  
  
    -   <span data-ttu-id="a17e5-109">向發行憑證的公開商業憑證授權單位取得憑證。</span><span class="sxs-lookup"><span data-stu-id="a17e5-109">Obtain a certificate from a public, commercial certification authority that issues certificates.</span></span>  
  
    -   <span data-ttu-id="a17e5-110">從可以讓組織在內部發行憑證的憑證伺服器取得憑證。</span><span class="sxs-lookup"><span data-stu-id="a17e5-110">Obtain a certificate from a certificate server, that enables an organization to internally issue certificates.</span></span> <span data-ttu-id="a17e5-111">您必須將用來簽署憑證的根憑證加入至 **[信任根憑證授權單位]** 存放區。</span><span class="sxs-lookup"><span data-stu-id="a17e5-111">You have to add the root certificate that is used to sign the certificate to the **Trusted Root Certification Authorities** store.</span></span> <span data-ttu-id="a17e5-112">若要加入根憑證，您可以使用 [!INCLUDE[msCoName](../includes/msconame-md.md)] Management Console (MMC) 的「憑證」嵌入式管理單元。</span><span class="sxs-lookup"><span data-stu-id="a17e5-112">To add the root certificate, you can use the Certificates snap-in for the [!INCLUDE[msCoName](../includes/msconame-md.md)] Management Console (MMC).</span></span> <span data-ttu-id="a17e5-113">如需詳細資訊，請參閱 MSDN Library 中的＜[憑證服務](https://go.microsoft.com/fwlink/?LinkId=100755)＞(英文) 主題。</span><span class="sxs-lookup"><span data-stu-id="a17e5-113">For more information, see the topic, "[Certificate Services](https://go.microsoft.com/fwlink/?LinkId=100755)," in the MSDN library.</span></span>  
  
    -   <span data-ttu-id="a17e5-114">建立僅供測試用途的自訂憑證。</span><span class="sxs-lookup"><span data-stu-id="a17e5-114">Create your own certificate for testing purposes only.</span></span> <span data-ttu-id="a17e5-115">憑證建立工具 (Makecert.exe) 會產生供測試用途的 X.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="a17e5-115">The Certificate Creation Tool (Makecert.exe) generates X.509 certificates for testing purposes.</span></span> <span data-ttu-id="a17e5-116">如需詳細資訊，請參閱 MSDN Library 中的＜[憑證建立工具 (Makecert.exe)](https://go.microsoft.com/fwlink/?LinkId=100756)＞主題。</span><span class="sxs-lookup"><span data-stu-id="a17e5-116">For more information, see the topic, "[Certificate Creation Tool (Makecert.exe)](https://go.microsoft.com/fwlink/?LinkId=100756)," in the MSDN Library.</span></span>  
  
     <span data-ttu-id="a17e5-117">如需有關憑證的詳細資訊，請參閱「憑證」嵌入式管理單元的線上說明。</span><span class="sxs-lookup"><span data-stu-id="a17e5-117">For more information about certificates, see the online Help for the Certificates snap-in.</span></span> <span data-ttu-id="a17e5-118">如需有關如何簽署數位資產的詳細資訊，請參閱 MSDN Library 中的[使用 Authenticode 簽署與檢查程式碼](https://go.microsoft.com/fwlink/?LinkId=78100)主題。</span><span class="sxs-lookup"><span data-stu-id="a17e5-118">For more information about how to sign digital assets, see the topic, "[Signing and Checking Code with Authenticode](https://go.microsoft.com/fwlink/?LinkId=78100)," in the MSDN Library.</span></span>  
  
-   <span data-ttu-id="a17e5-119">確定憑證已經啟用程式碼簽署。</span><span class="sxs-lookup"><span data-stu-id="a17e5-119">Make sure that the certificate has been enabled for code signing.</span></span> <span data-ttu-id="a17e5-120">若要判斷憑證是否已啟用程式碼簽署，請在「憑證」嵌入式管理單元中檢閱憑證的屬性。</span><span class="sxs-lookup"><span data-stu-id="a17e5-120">To determine whether a certificate is enabled for code signing, review the properties of the certificate in the Certificates snap-in.</span></span>  
  
-   <span data-ttu-id="a17e5-121">將憑證儲存在個人存放區中。</span><span class="sxs-lookup"><span data-stu-id="a17e5-121">Store the certificate in the Personal store.</span></span>  
  
 <span data-ttu-id="a17e5-122">當您已完成上述工作之後，就可以使用下列程序來簽署封裝。</span><span class="sxs-lookup"><span data-stu-id="a17e5-122">After you have completed the previous tasks, you can use the following procedure to sign a package.</span></span>  
  
### <a name="to-sign-a-package"></a><span data-ttu-id="a17e5-123">若要簽署封裝</span><span class="sxs-lookup"><span data-stu-id="a17e5-123">To sign a package</span></span>  
  
1.  <span data-ttu-id="a17e5-124">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，開啟包含要簽署之封裝的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="a17e5-124">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package to be signed.</span></span>  
  
2.  <span data-ttu-id="a17e5-125">在 [方案總管] 中，按兩下封裝將其開啟。</span><span class="sxs-lookup"><span data-stu-id="a17e5-125">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="a17e5-126">在 [ [!INCLUDE[ssIS](../includes/ssis-md.md)] 設計師] 的 **[SSIS]** 功能表上，按一下 **[數位簽章]** 。</span><span class="sxs-lookup"><span data-stu-id="a17e5-126">In [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer, on the **SSIS** menu, click **Digital Signing**.</span></span>  
  
4.  <span data-ttu-id="a17e5-127">在 **[數位簽章]** 對話方塊中，按一下 **[簽署]** 。</span><span class="sxs-lookup"><span data-stu-id="a17e5-127">In the **Digital Signing** dialog box, click **Sign**.</span></span>  
  
5.  <span data-ttu-id="a17e5-128">在 **[選取憑證]** 對話方塊中，選取憑證。</span><span class="sxs-lookup"><span data-stu-id="a17e5-128">In the **Select a Certificate** dialog box, select a certificate.</span></span>  
  
6.  <span data-ttu-id="a17e5-129">(選擇性) 按一下 [檢視憑證]  檢視憑證資訊。</span><span class="sxs-lookup"><span data-stu-id="a17e5-129">(Optional) Click **View Certificat**e to view certificate information.</span></span>  
  
7.  <span data-ttu-id="a17e5-130">按一下 **[確定]** 關閉 **[選取憑證]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="a17e5-130">Click **OK** to close the **Select a Certificate** dialog box.</span></span>  
  
8.  <span data-ttu-id="a17e5-131">按一下 **[確定]** 關閉 **[數位簽章]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="a17e5-131">Click **OK** to close the **Digital Signing** dialog box.</span></span>  
  
9. <span data-ttu-id="a17e5-132">若要儲存已更新的封裝，請在 **[檔案]** 功能表上，按一下 **[儲存選取項目]** 。</span><span class="sxs-lookup"><span data-stu-id="a17e5-132">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
     <span data-ttu-id="a17e5-133">雖然封裝已經簽署，但是您現在必須設定 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] ，以便檢查或確認數位簽章，然後再載入封裝。</span><span class="sxs-lookup"><span data-stu-id="a17e5-133">Although the package has been signed, you must now configure [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] to check or verify the digital signature before loading the package.</span></span> <span data-ttu-id="a17e5-134">如需詳細資訊，請參閱 [Identify the Source of Packages with Digital Signatures](security/identify-the-source-of-packages-with-digital-signatures.md)(使用數位簽章識別封裝來源)。</span><span class="sxs-lookup"><span data-stu-id="a17e5-134">For more information, see [Identify the Source of Packages with Digital Signatures](security/identify-the-source-of-packages-with-digital-signatures.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a17e5-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a17e5-135">See Also</span></span>  
 [<span data-ttu-id="a17e5-136">安全性概觀 (Integration Services)</span><span class="sxs-lookup"><span data-stu-id="a17e5-136">Security Overview &#40;Integration Services&#41;</span></span>](security/security-overview-integration-services.md)  
  
  
