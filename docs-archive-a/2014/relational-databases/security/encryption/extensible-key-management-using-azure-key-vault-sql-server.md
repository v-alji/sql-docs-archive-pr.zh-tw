---
title: 使用 Azure Key Vault 進行可延伸金鑰管理 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- EKM, with key vault
- TDE, EKM and key vault
- Extensible Key Management with key vault
- Key Management with key vault
- Transparent Data Encryption, using EKM and key vault
ms.assetid: 3efdc48a-8064-4ea6-a828-3fbf758ef97c
author: jaszymas
ms.author: jaszymas
ms.openlocfilehash: 0e4bbc4f0c371c927988e6b91fdbf47307ad9d3f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710533"
---
# <a name="extensible-key-management-using-azure-key-vault-sql-server"></a><span data-ttu-id="6ef30-102">使用 Azure Key Vault 進行可延伸金鑰管理 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="6ef30-102">Extensible Key Management Using Azure Key Vault (SQL Server)</span></span>
  <span data-ttu-id="6ef30-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]適用于 Azure Key Vault 的連接器 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] 可讓 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 加密利用 Azure Key Vault 服務作為可延伸[金鑰管理 &#40;EKM&#41;](extensible-key-management-ekm.md)提供者，以保護其加密金鑰。</span><span class="sxs-lookup"><span data-stu-id="6ef30-103">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Connector for [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Azure Key Vault enables [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] encryption to leverage the Azure Key Vault service as an [Extensible Key Management &#40;EKM&#41;](extensible-key-management-ekm.md) provider to protect its encryption keys.</span></span>

 <span data-ttu-id="6ef30-104">本主題內容：</span><span class="sxs-lookup"><span data-stu-id="6ef30-104">Included in this topic:</span></span>

-   [<span data-ttu-id="6ef30-105">EKM 的使用方式</span><span class="sxs-lookup"><span data-stu-id="6ef30-105">Uses of EKM</span></span>](#Uses)

-   [<span data-ttu-id="6ef30-106">步驟 1：設定金鑰保存庫以供 SQL Server 使用</span><span class="sxs-lookup"><span data-stu-id="6ef30-106">Step 1: Setting up the Key Vault for use by SQL Server</span></span>](#Step1)

-   [<span data-ttu-id="6ef30-107">步驟 2：安裝 SQL Server Connector</span><span class="sxs-lookup"><span data-stu-id="6ef30-107">Step 2: Installing the SQL Server Connector</span></span>](#Step2)

-   [<span data-ttu-id="6ef30-108">步驟 3：設定 SQL Server 對金鑰保存庫使用 EKM 提供者</span><span class="sxs-lookup"><span data-stu-id="6ef30-108">Step 3: Configure SQL Server to use an EKM provider for the Key Vault</span></span>](#Step3)

-   [<span data-ttu-id="6ef30-109">範例 A：使用金鑰保存庫中的非對稱金鑰進行透明資料加密</span><span class="sxs-lookup"><span data-stu-id="6ef30-109">Example A: Transparent Data Encryption by Using an Asymmetric Key from the Key Vault</span></span>](#ExampleA)

-   [<span data-ttu-id="6ef30-110">範例 B：使用金鑰保存庫中的非對稱金鑰進行備份加密</span><span class="sxs-lookup"><span data-stu-id="6ef30-110">Example B: Encrypting Backups by Using an Asymmetric Key from the Key Vault</span></span>](#ExampleB)

-   [<span data-ttu-id="6ef30-111">範例 C：使用金鑰保存庫中的非對稱金鑰進行資料行層級加密</span><span class="sxs-lookup"><span data-stu-id="6ef30-111">Example C: Column Level Encryption by Using an Asymmetric Key from the Key Vault</span></span>](#ExampleC)

##  <a name="uses-of-ekm"></a><a name="Uses"></a><span data-ttu-id="6ef30-112">EKM 的使用</span><span class="sxs-lookup"><span data-stu-id="6ef30-112">Uses of EKM</span></span>
 <span data-ttu-id="6ef30-113">組織可以使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 加密來保護機密資料。</span><span class="sxs-lookup"><span data-stu-id="6ef30-113">An organization can use [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] encryption to protect sensitive data.</span></span> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]<span data-ttu-id="6ef30-114">加密包含[透明資料加密 &#40;TDE&#41;](transparent-data-encryption.md)、資料[行層級加密](/sql/t-sql/functions/cryptographic-functions-transact-sql) (CLE) 和[備份加密](../../backup-restore/backup-encryption.md)。</span><span class="sxs-lookup"><span data-stu-id="6ef30-114">encryption includes [Transparent Data Encryption &#40;TDE&#41;](transparent-data-encryption.md), [Column Level Encryption](/sql/t-sql/functions/cryptographic-functions-transact-sql) (CLE), and [Backup Encryption](../../backup-restore/backup-encryption.md).</span></span> <span data-ttu-id="6ef30-115">在上述所有情況下，資料會使用對稱資料加密金鑰來加密。</span><span class="sxs-lookup"><span data-stu-id="6ef30-115">In all of these cases the data is encrypted using a symmetric data encryption key.</span></span> <span data-ttu-id="6ef30-116">對稱資料加密金鑰會以儲存在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]中的金鑰階層加密，受到更進一步的保護。</span><span class="sxs-lookup"><span data-stu-id="6ef30-116">The symmetric data encryption key is further protected by encrypting it with a hierarchy of keys stored in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="6ef30-117">或者，EKM 提供者架構可讓 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 透過儲存在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 之外部密碼編譯提供者中的非對稱金鑰，來保護資料加密金鑰。</span><span class="sxs-lookup"><span data-stu-id="6ef30-117">Alternatively, the EKM provider architecture enables [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] to protect the data encryption keys by using an asymmetric key stored outside of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in an external cryptographic provider.</span></span> <span data-ttu-id="6ef30-118">使用 EKM 提供者架構會多增加一層安全性，讓組織得以分開管理金鑰和資料。</span><span class="sxs-lookup"><span data-stu-id="6ef30-118">Using EKM provider architecture adds an additional layer of security and allows organizations to separate the management of keys and data.</span></span>

 <span data-ttu-id="6ef30-119">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Connector for Azure Key Vault 可讓 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 運用可擴充、高效能和高可用性的金鑰保存庫服務，做為加密金鑰保護的 EKM 提供者。</span><span class="sxs-lookup"><span data-stu-id="6ef30-119">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Connector for Azure Key Vault lets [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] leverage the scalable, high performance, and highly available key vault service as an EKM provider for encryption key protection.</span></span> <span data-ttu-id="6ef30-120">金鑰保存庫服務可以與 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Azure 虛擬機器上的 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] 安裝和內部部署伺服器搭配使用。</span><span class="sxs-lookup"><span data-stu-id="6ef30-120">The key vault service can be used with [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] installations on [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Azure Virtual Machines and for on-premises servers.</span></span> <span data-ttu-id="6ef30-121">金鑰保存庫服務也提供選項，以使用受到緊密控制和監視的硬體安全性模組 (HSM)，對非對稱加密金鑰提供更高等級的保護。</span><span class="sxs-lookup"><span data-stu-id="6ef30-121">The key vault service also provides the option to use tightly controlled and monitored Hardware Security Modules (HSMs) for a higher level of protection for asymmetric encryption keys.</span></span> <span data-ttu-id="6ef30-122">如需金鑰保存庫的詳細資訊，請參閱 [Azure 金鑰保存庫](https://go.microsoft.com/fwlink/?LinkId=521401)。</span><span class="sxs-lookup"><span data-stu-id="6ef30-122">For more information about the key vault, see [Azure Key Vault](https://go.microsoft.com/fwlink/?LinkId=521401).</span></span>

 <span data-ttu-id="6ef30-123">下列影像摘要說明使用金鑰保存庫的 EKM 處理流程。</span><span class="sxs-lookup"><span data-stu-id="6ef30-123">The following image summarizes the process flow of EKM using the key vault.</span></span> <span data-ttu-id="6ef30-124">影像中的程序步驟數字並非用以比對遵循影像的安裝步驟數字。</span><span class="sxs-lookup"><span data-stu-id="6ef30-124">The process step numbers in the image are not meant to match the setup step numbers that follow the image.</span></span>

 <span data-ttu-id="6ef30-125">![使用 Azure Key Vault 的 SQL Server EKM](../../../database-engine/media/ekm-using-azure-key-vault.png "使用 Azure Key Vault 的 SQL Server EKM")</span><span class="sxs-lookup"><span data-stu-id="6ef30-125">![SQL Server EKM using the Azure Key Vault](../../../database-engine/media/ekm-using-azure-key-vault.png "SQL Server EKM using the Azure Key Vault")</span></span>

##  <a name="step-1-set-up-the-key-vault-for-use-by-sql-server"></a><a name="Step1"></a><span data-ttu-id="6ef30-126">步驟1：設定要供 SQL Server 使用的 Key Vault</span><span class="sxs-lookup"><span data-stu-id="6ef30-126">Step 1: Set up the Key Vault for use by SQL Server</span></span>
 <span data-ttu-id="6ef30-127">下列步驟可用來設定金鑰保存庫，以搭配 [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)] 提供加密金鑰保護。</span><span class="sxs-lookup"><span data-stu-id="6ef30-127">Use the following steps to set up a key vault for use with the [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)] for encryption key protection.</span></span> <span data-ttu-id="6ef30-128">組織中可能已使用保存庫。</span><span class="sxs-lookup"><span data-stu-id="6ef30-128">A vault may already be in use for the organization.</span></span> <span data-ttu-id="6ef30-129">當保存庫不存在時，可由組織中指定來管理加密金鑰的 Azure 系統管理員建立保存庫、在保存庫中產生非對稱金鑰，然後再授權 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 使用金鑰。</span><span class="sxs-lookup"><span data-stu-id="6ef30-129">When a vault does not exist, the Azure Administrator in your organization that is designated to manage encryption keys can create a vault, generate an asymmetric key in the vault, and then authorize [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] to use the key.</span></span> <span data-ttu-id="6ef30-130">透過檢閱 [開始使用 Azure Key Vault](https://go.microsoft.com/fwlink/?LinkId=521402)及 PowerShell [Azure Key Vault Cmdlet](https://docs.microsoft.com/powershell/module/azurerm.keyvault) 參考，讓自己熟悉如何使用金鑰保存庫服務。</span><span class="sxs-lookup"><span data-stu-id="6ef30-130">To familiarize yourself with the key vault service review [Get Started with Azure Key Vault](https://go.microsoft.com/fwlink/?LinkId=521402), and the PowerShell [Azure Key Vault Cmdlets](https://docs.microsoft.com/powershell/module/azurerm.keyvault) reference.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="6ef30-131">如果您有多個 Azure 訂用帳戶，則必須使用包含 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]的訂用帳戶。</span><span class="sxs-lookup"><span data-stu-id="6ef30-131">If you have multiple Azure subscriptions, you must use the subscription that contains [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>

1.  <span data-ttu-id="6ef30-132">**建立保存庫：** 透過 **開始使用 Azure 金鑰保存庫** 中 [建立金鑰保存庫](https://go.microsoft.com/fwlink/?LinkId=521402)一節中的指示，來建立保存庫。</span><span class="sxs-lookup"><span data-stu-id="6ef30-132">**Create a vault:** Create a vault by using the instructions in the **Create a key vault** section of [Get Started with Azure Key Vault](https://go.microsoft.com/fwlink/?LinkId=521402).</span></span> <span data-ttu-id="6ef30-133">記錄保存庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="6ef30-133">Record the name of the vault.</span></span> <span data-ttu-id="6ef30-134">本主題使用 **ContosoKeyVault** 做為金鑰保存庫名稱。</span><span class="sxs-lookup"><span data-stu-id="6ef30-134">This topic uses **ContosoKeyVault** as the key vault name.</span></span>

2.  <span data-ttu-id="6ef30-135">**在保存庫中產生非對稱金鑰：** 金鑰保存庫中的非對稱金鑰可用來保護 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 加密金鑰。</span><span class="sxs-lookup"><span data-stu-id="6ef30-135">**Generate an asymmetric key in the vault:** The asymmetric key in the key vault is used to protect [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] encryption keys.</span></span> <span data-ttu-id="6ef30-136">只有非對稱金鑰的公開部分可離開保存庫，保存庫絕不會匯出私用部分。</span><span class="sxs-lookup"><span data-stu-id="6ef30-136">Only the public portion of the asymmetric key ever leaves the vault, the private portion is never exported by the vault.</span></span> <span data-ttu-id="6ef30-137">使用非對稱金鑰的所有密碼編譯作業會委派給 Azure Key Vault，並受到金鑰保存庫安全性的保護。</span><span class="sxs-lookup"><span data-stu-id="6ef30-137">All cryptographic operations using the asymmetric key are delegated to the Azure Key Vault, and are protected by the key vault security.</span></span>

     <span data-ttu-id="6ef30-138">您可以使用數種方式來產生非對稱金鑰，並將它儲存在保存庫。</span><span class="sxs-lookup"><span data-stu-id="6ef30-138">There are several ways that you can generate an asymmetric key and store it in the vault.</span></span> <span data-ttu-id="6ef30-139">您可以在外部產生金鑰，並將金鑰以 .pfx 檔案形式匯入到保存庫。</span><span class="sxs-lookup"><span data-stu-id="6ef30-139">You can externally generate a key, and import the key into the vault as a .pfx file.</span></span> <span data-ttu-id="6ef30-140">或使用金鑰保存庫 API 直接在保存庫中建立金鑰。</span><span class="sxs-lookup"><span data-stu-id="6ef30-140">Or create the key directly in the vault by using the key vault APIs.</span></span>

     <span data-ttu-id="6ef30-141">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Connector 需要使用 2048 位元 RSA 的非對稱金鑰，且金鑰名稱只能使用字元 "a-z"、"A-Z"、"0-9" 和 "-"。</span><span class="sxs-lookup"><span data-stu-id="6ef30-141">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Connector requires the asymmetric keys to be 2048-bit RSA, and the key name can only use the characters "a-z", "A-Z", "0-9", and "-".</span></span> <span data-ttu-id="6ef30-142">在本文件中，非對稱金鑰的名稱會是 **ContosoMasterKey**。</span><span class="sxs-lookup"><span data-stu-id="6ef30-142">In this document the name of the asymmetric key is referred to as **ContosoMasterKey**.</span></span> <span data-ttu-id="6ef30-143">請以您用於金鑰的唯一名稱來取代這個名稱。</span><span class="sxs-lookup"><span data-stu-id="6ef30-143">Replace this with the unique name you use for the key.</span></span>

    > [!IMPORTANT]
    >  <span data-ttu-id="6ef30-144">強烈建議在生產案例中匯入非對稱金鑰，因為這樣做可讓系統管理員在金鑰委付系統中委付金鑰。</span><span class="sxs-lookup"><span data-stu-id="6ef30-144">Importing the asymmetric key is highly recommended for production scenarios because it allows the administrator to escrow the key in a key escrow system.</span></span> <span data-ttu-id="6ef30-145">如果非對稱金鑰是在保存庫中建立，由於私密金鑰永遠不會離開保存庫，因此無法委付金鑰。</span><span class="sxs-lookup"><span data-stu-id="6ef30-145">If the asymmetric key is created in the vault, it cannot be escrowed because the private key can never leave the vault.</span></span> <span data-ttu-id="6ef30-146">您應該委付用來保護重要資料的金鑰。</span><span class="sxs-lookup"><span data-stu-id="6ef30-146">Keys used to protect critical data should be escrowed.</span></span> <span data-ttu-id="6ef30-147">遺失非對稱金鑰會導致資料永久無法復原。</span><span class="sxs-lookup"><span data-stu-id="6ef30-147">The loss of an asymmetric key will result in permanently unrecoverable data.</span></span>

    > [!IMPORTANT]
    >  <span data-ttu-id="6ef30-148">金鑰保存庫支援多種版本的相同指定金鑰。</span><span class="sxs-lookup"><span data-stu-id="6ef30-148">The key vault supports multiple versions of the same named key.</span></span> <span data-ttu-id="6ef30-149">您不應該對 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Connector 所使用的金鑰建立版本或進行復原。</span><span class="sxs-lookup"><span data-stu-id="6ef30-149">Keys to be used by [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Connector should not be versioned or rolled.</span></span> <span data-ttu-id="6ef30-150">如果系統管理員想要復原 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 加密所使用的金鑰，應該在保存庫中建立不同名稱的新金鑰，用來加密 DEK。</span><span class="sxs-lookup"><span data-stu-id="6ef30-150">If the administrator wants to roll the key used for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] encryption, a new key with a different name should be created in the vault and used to encrypt the DEK.</span></span>

     <span data-ttu-id="6ef30-151">如需如何將金鑰匯入金鑰保存庫或在金鑰保存庫中建立金鑰 (生產環境不建議使用) 的詳細資訊，請參閱 **開始使用 Azure Key Vault**[中的將金鑰或密碼加入金鑰保存庫](https://go.microsoft.com/fwlink/?LinkId=521402)一節。</span><span class="sxs-lookup"><span data-stu-id="6ef30-151">For more information on how to import a key into the key vault or to create a key in the key vault (not recommended for a production environment), see the **Add a key or secret to the key vault** section in [Get Started with Azure Key Vault](https://go.microsoft.com/fwlink/?LinkId=521402).</span></span>

3.  <span data-ttu-id="6ef30-152">**取得要用於 SQL Server 的 Azure Active Directory 服務主體：** 當組織註冊 Microsoft 雲端服務時，它會取得 Azure Active Directory。</span><span class="sxs-lookup"><span data-stu-id="6ef30-152">**Get Azure Active Directory Service Principals to use for SQL Server:** When the organization signs up for a Microsoft cloud service, it gets an Azure Active Directory.</span></span> <span data-ttu-id="6ef30-153">在 Azure Active Directory 中建立 **服務主體** ，以供 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 在存取金鑰保存庫時使用 (以向 Azure Active Directory 驗證自己)。</span><span class="sxs-lookup"><span data-stu-id="6ef30-153">Create **Service Principals** in the Azure Active Directory for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] to use (to authenticate itself to Azure Active Directory) while accessing the key vault.</span></span>

    -   <span data-ttu-id="6ef30-154">\*\*\*\* 系統管理員若要在設定 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 使用加密時存取保存庫，需要一個服務主體 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="6ef30-154">One **Service Principal** will be needed by a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] administrator to access the vault while configuring [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] to use encryption.</span></span>

    -   <span data-ttu-id="6ef30-155">\*\*\*\* 若要存取保存庫，以解除包裝 [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)] 加密所使用的金鑰，則需要另一個服務主體 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="6ef30-155">Another **Service Principal** will be needed by the [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)] to access the vault for unwrapping keys used in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] encryption.</span></span>

     <span data-ttu-id="6ef30-156">如需如何註冊應用程式及產生服務主體的詳細資訊，請參閱 **開始使用 Azure Key Vault** 中的 [使用 Azure Active Directory 註冊應用程式](https://go.microsoft.com/fwlink/?LinkId=521402)一節。</span><span class="sxs-lookup"><span data-stu-id="6ef30-156">For more information about how to register an application and generate a service principal, see the **Register an Application with Azure Active Directory** section in [Get Started with Azure Key Vault](https://go.microsoft.com/fwlink/?LinkId=521402).</span></span> <span data-ttu-id="6ef30-157">註冊程序會針對每個 Azure Active Directory **服務主體** ，傳回 **應用程式識別碼**(又稱為 **用戶端識別碼** ) 和 **驗證金鑰**(又稱為 **密碼**)。</span><span class="sxs-lookup"><span data-stu-id="6ef30-157">The registration process returns an **Application ID** (also known as a **CLIENT ID**) and a **Authentication Key** (also known as a **Secret**) for each Azure Active Directory **Service Principal**.</span></span> <span data-ttu-id="6ef30-158">在語句中使用時 `CREATE CREDENTIAL` ，必須從**用戶端識別碼**移除連字號。</span><span class="sxs-lookup"><span data-stu-id="6ef30-158">When used in the `CREATE CREDENTIAL` statement, the hyphen must be removed from the **CLIENT ID**.</span></span> <span data-ttu-id="6ef30-159">請記錄這些項目，以用於下列指令碼：</span><span class="sxs-lookup"><span data-stu-id="6ef30-159">Record these for use in the scripts below:</span></span>

    -   <span data-ttu-id="6ef30-160">**sysadmin** 登入的 **服務主體** ： **CLIENTID_sysadmin_login** 和 **SECRET_sysadmin_login**</span><span class="sxs-lookup"><span data-stu-id="6ef30-160">**Service Principal** for a **sysadmin** login: **CLIENTID_sysadmin_login** and **SECRET_sysadmin_login**</span></span>

    -   <span data-ttu-id="6ef30-161">**的** 服務主體 [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)]： **CLIENTID_DBEngine** 和 **SECRET_DBEngine**。</span><span class="sxs-lookup"><span data-stu-id="6ef30-161">**Service Principal** for the [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)]: **CLIENTID_DBEngine** and **SECRET_DBEngine**.</span></span>

4.  <span data-ttu-id="6ef30-162">**授與服務主體存取金鑰保存庫的權限：** 和 **和\*\*\*\*服務主體** 都需要金鑰保存庫中的 **get**, **list**, **wrapKey**,  **unwrapKey** 權限。</span><span class="sxs-lookup"><span data-stu-id="6ef30-162">**Grant Permission for the Service Principals to access the Key Vault:** Both the **CLIENTID_sysadmin_login** and **CLIENTID_DBEngineService Principals** require the **get**, **list**, **wrapKey**, and **unwrapKey** permissions in the key vault.</span></span> <span data-ttu-id="6ef30-163">如果您想要透過 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 建立金鑰，還必須授與金鑰保存庫的 **create** 權限。</span><span class="sxs-lookup"><span data-stu-id="6ef30-163">If you intend to create keys through [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] you also need to grant the **create** permission in key vault.</span></span>

    > [!IMPORTANT]
    >  <span data-ttu-id="6ef30-164">使用者必須至少具有這個金鑰保存庫的 **wrapKey** 和 **unwrapKey** 作業。</span><span class="sxs-lookup"><span data-stu-id="6ef30-164">Users must have at least the **wrapKey** and **unwrapKey** operations for the key vault.</span></span>

     <span data-ttu-id="6ef30-165">如需授與保存庫權限的詳細資訊，請參閱 **開始使用 Azure Key Vault**[中的授權應用程式使用金鑰或密碼](https://go.microsoft.com/fwlink/?LinkId=521402)一節。</span><span class="sxs-lookup"><span data-stu-id="6ef30-165">For more information about granting permissions to the vault, see the **Authorize the application to use the key or secret** section in [Get Started with Azure Key Vault](https://go.microsoft.com/fwlink/?LinkId=521402).</span></span>

     <span data-ttu-id="6ef30-166">Azure Key Vault 文件的連結</span><span class="sxs-lookup"><span data-stu-id="6ef30-166">Links to Azure Key Vault documentation</span></span>

    -   [<span data-ttu-id="6ef30-167">什麼是 Azure 金鑰保存庫？</span><span class="sxs-lookup"><span data-stu-id="6ef30-167">What is Azure Key Vault?</span></span>](https://go.microsoft.com/fwlink/?LinkId=521401)

    -   [<span data-ttu-id="6ef30-168">開始使用 Azure Key Vault</span><span class="sxs-lookup"><span data-stu-id="6ef30-168">Get Started with Azure Key Vault</span></span>](https://go.microsoft.com/fwlink/?LinkId=521402)

    -   <span data-ttu-id="6ef30-169">PowerShell [Azure 金鑰保存庫 Cmdlet](https://docs.microsoft.com/powershell/module/azurerm.keyvault) 參考</span><span class="sxs-lookup"><span data-stu-id="6ef30-169">PowerShell [Azure Key Vault Cmdlets](https://docs.microsoft.com/powershell/module/azurerm.keyvault) reference</span></span>

##  <a name="step-2-install-the-sql-server-connector"></a><a name="Step2"></a><span data-ttu-id="6ef30-170">步驟2：安裝 SQL Server 連接器</span><span class="sxs-lookup"><span data-stu-id="6ef30-170">Step 2: Install the SQL Server Connector</span></span>
 <span data-ttu-id="6ef30-171">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Connector 是由 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 電腦的系統管理員所下載及安裝。</span><span class="sxs-lookup"><span data-stu-id="6ef30-171">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Connector is downloaded and installed by the administrator of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] computer.</span></span> <span data-ttu-id="6ef30-172">您可以從 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Microsoft 下載中心 [下載](https://go.microsoft.com/fwlink/p/?LinkId=521700)Connector。</span><span class="sxs-lookup"><span data-stu-id="6ef30-172">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Connector is available as a download from the [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=521700).</span></span>  <span data-ttu-id="6ef30-173">搜尋 **SQL Server Connector for Microsoft Azure Key Vault**，檢閱詳細資料、系統需求和安裝指示，然後選擇下載連接器並使用 [執行] \*\*\*\* 開始安裝。</span><span class="sxs-lookup"><span data-stu-id="6ef30-173">Search for **SQL Server Connector for Microsoft Azure Key Vault**, review the details, system requirements and install instructions and choose to download the connector and start the installation using **Run**.</span></span> <span data-ttu-id="6ef30-174">檢閱授權，然後接受授權並繼續。</span><span class="sxs-lookup"><span data-stu-id="6ef30-174">Review the license and accept the license and continue.</span></span>

 <span data-ttu-id="6ef30-175">根據預設，連接器會安裝在**C:\Program Files\SQL Server connector for Microsoft Azure Key Vault**。</span><span class="sxs-lookup"><span data-stu-id="6ef30-175">By default the connector is installed at **C:\Program Files\SQL Server Connector for Microsoft Azure Key Vault**.</span></span> <span data-ttu-id="6ef30-176">這個位置可以在安裝期間變更。</span><span class="sxs-lookup"><span data-stu-id="6ef30-176">This location can be changed during setup.</span></span> <span data-ttu-id="6ef30-177">(如果變更，請調整下列指令碼)。</span><span class="sxs-lookup"><span data-stu-id="6ef30-177">(If changed, adjust the scripts below.)</span></span>

 <span data-ttu-id="6ef30-178">完成安裝時，電腦上會安裝下列項目：</span><span class="sxs-lookup"><span data-stu-id="6ef30-178">On completing the install, the following are installed on the machine:</span></span>

-   <span data-ttu-id="6ef30-179">**Microsoft.AzureKeyVaultService.EKM.dll**：這是密碼編譯的 EKM 提供者 DLL，需要向 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 或使用 CREATE CRYPTOGRAPHIC PROVIDER 陳述式註冊。</span><span class="sxs-lookup"><span data-stu-id="6ef30-179">**Microsoft.AzureKeyVaultService.EKM.dll**: This is the cryptographic EKM provider DLL that needs to be registered with [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] by using the CREATE CRYPTOGRAPHIC PROVIDER statement.</span></span>

-   <span data-ttu-id="6ef30-180">**Azure Key Vault SQL Server Connector**：這是 Windows 服務，可讓密碼編譯的 EKM 提供者與金鑰保存庫通訊。</span><span class="sxs-lookup"><span data-stu-id="6ef30-180">**Azure Key Vault SQL Server Connector**: This is a Windows service that enables the cryptographic EKM provider to communicate with the key vault.</span></span>

 <span data-ttu-id="6ef30-181">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Connector 安裝也可讓您選擇性地下載 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 加密的範例指令碼。</span><span class="sxs-lookup"><span data-stu-id="6ef30-181">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Connector installation also allows you to optionally download sample scripts for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] encryption.</span></span>

##  <a name="step-3-configure-sql-server-to-use-an-ekm-provider-for-the-key-vault"></a><a name="Step3"></a><span data-ttu-id="6ef30-182">步驟3：設定 SQL Server 使用 Key Vault 的 EKM 提供者</span><span class="sxs-lookup"><span data-stu-id="6ef30-182">Step 3: Configure SQL Server to use an EKM provider for the Key Vault</span></span>

###  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="6ef30-183">權限</span><span class="sxs-lookup"><span data-stu-id="6ef30-183">Permissions</span></span>
 <span data-ttu-id="6ef30-184">若要完成這整個程序，需要 CONTROL SERVER 權限或 **sysadmin** 固定伺服器角色中的成員資格。</span><span class="sxs-lookup"><span data-stu-id="6ef30-184">To complete this entire process requires CONTROL SERVER permission or membership in the **sysadmin** fixed server role.</span></span> <span data-ttu-id="6ef30-185">特定動作需要下列權限：</span><span class="sxs-lookup"><span data-stu-id="6ef30-185">Specific actions require the following permissions:</span></span>

-   <span data-ttu-id="6ef30-186">若要建立密碼編譯提供者，需要 CONTROL SERVER 權限或 **sysadmin** 固定伺服器角色中的成員資格。</span><span class="sxs-lookup"><span data-stu-id="6ef30-186">To create a cryptographic provider, requires CONTROL SERVER permission or membership in the **sysadmin** fixed server role.</span></span>

-   <span data-ttu-id="6ef30-187">若要變更組態選項及執行 RECONFIGURE 陳述式，您必須取得 ALTER SETTINGS 伺服器層級的權限。</span><span class="sxs-lookup"><span data-stu-id="6ef30-187">To change a configuration option and run the RECONFIGURE statement, you must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="6ef30-188">**系統管理員 (sysadmin)** 及 **serveradmin** 固定伺服器角色會隱含 ALTER SETTINGS 權限。</span><span class="sxs-lookup"><span data-stu-id="6ef30-188">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>

-   <span data-ttu-id="6ef30-189">若要建立認證，需要 ALTER ANY CREDENTIAL 權限。</span><span class="sxs-lookup"><span data-stu-id="6ef30-189">To create a credential, requires ALTER ANY CREDENTIAL permission.</span></span>

-   <span data-ttu-id="6ef30-190">若要將認證加入登入，需要 ALTER ANY LOGIN 權限。</span><span class="sxs-lookup"><span data-stu-id="6ef30-190">To add a credential to a login, requires ALTER ANY LOGIN permission.</span></span>

-   <span data-ttu-id="6ef30-191">若要建立非對稱金鑰，需要 CREATE ASYMMETRIC KEY 權限。</span><span class="sxs-lookup"><span data-stu-id="6ef30-191">To create an asymmetric key, requires CREATE ASYMMETRIC KEY permission.</span></span>

###  <a name="to-configure-sql-server-to-use-a-cryptographic-provider"></a><a name="TsqlProcedure"></a><span data-ttu-id="6ef30-192">設定 SQL Server 使用密碼編譯提供者</span><span class="sxs-lookup"><span data-stu-id="6ef30-192">To configure SQL Server to use a cryptographic provider</span></span>

1.  <span data-ttu-id="6ef30-193">設定 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] 使用 EKM，並向 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]註冊 (建立) 密碼編譯提供者。</span><span class="sxs-lookup"><span data-stu-id="6ef30-193">Configure the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] to use EKM, and register (create) the cryptographic provider with [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>

    ```sql
    -- Enable advanced options.
    USE master;
    GO

    sp_configure 'show advanced options', 1 ;
    GO
    RECONFIGURE ;
    GO
    -- Enable EKM provider
    sp_configure 'EKM provider enabled', 1 ;
    GO
    RECONFIGURE ;
    GO

    -- Create a cryptographic provider, using the SQL Server Connector
    -- which is an EKM provider for the Azure Key Vault. This example uses 
    -- the name AzureKeyVault_EKM_Prov.

    CREATE CRYPTOGRAPHIC PROVIDER AzureKeyVault_EKM_Prov 
    FROM FILE = 'C:\Program Files\SQL Server Connector for Microsoft Azure Key Vault\Microsoft.AzureKeyVaultService.EKM.dll';
    GO
    ```

2.  <span data-ttu-id="6ef30-194">設定 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 系統管理員登入的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 認證使用金鑰保存庫，以便設定及管理 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 加密案例。</span><span class="sxs-lookup"><span data-stu-id="6ef30-194">Setup a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] credential for a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] administrator login to use the key vault in order to setup and manage [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] encryption scenarios.</span></span>

    > [!IMPORTANT]
    >  <span data-ttu-id="6ef30-195">的身分**識別**引數 `CREATE CREDENTIAL` 需要金鑰保存庫名稱。</span><span class="sxs-lookup"><span data-stu-id="6ef30-195">The **IDENTITY** argument of `CREATE CREDENTIAL` requires the key vault name.</span></span> <span data-ttu-id="6ef30-196">的**SECRET**引數 `CREATE CREDENTIAL` 需要 *\<Client ID>* 沒有連字號) 的 (，並在兩者 *\<Secret>* 之間一起傳遞而不會有空格。</span><span class="sxs-lookup"><span data-stu-id="6ef30-196">The **SECRET** argument of `CREATE CREDENTIAL` requires the *\<Client ID>* (without hyphens) and *\<Secret>* to be passed together without a space between them.</span></span>

     <span data-ttu-id="6ef30-197">在下列範例中，**用戶端識別碼** (`EF5C8E09-4D2A-4A76-9998-D93440D8115D`) 會移除連字號並以字串輸入 `EF5C8E094D2A4A769998D93440D8115D` ，而**密碼**會以字串*SECRET_sysadmin_login*表示。</span><span class="sxs-lookup"><span data-stu-id="6ef30-197">In the following example, the **Client ID** (`EF5C8E09-4D2A-4A76-9998-D93440D8115D`) is stripped of the hyphens and entered as the string `EF5C8E094D2A4A769998D93440D8115D` and the **Secret** is represented by the string *SECRET_sysadmin_login*.</span></span>

    ```sql
    USE master;
    CREATE CREDENTIAL sysadmin_ekm_cred 
        WITH IDENTITY = 'ContosoKeyVault', 
        SECRET = 'EF5C8E094D2A4A769998D93440D8115DSECRET_sysadmin_login' 
    FOR CRYPTOGRAPHIC PROVIDER AzureKeyVault_EKM_Prov ;

    -- Add the credential to the SQL Server administrators domain login 
    ALTER LOGIN [<domain>/<login>]
    ADD CREDENTIAL sysadmin_ekm_cred;
    ```

     <span data-ttu-id="6ef30-198">如需使用引數的變數 `CREATE CREDENTIAL` ，並以程式設計方式從用戶端識別碼移除連字號的範例，請參閱[CREATE CREDENTIAL &#40;transact-sql&#41;](/sql/t-sql/statements/create-credential-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="6ef30-198">For an example of using variables for the `CREATE CREDENTIAL` arguments and programmatically removing the hyphens from the Client ID, see [CREATE CREDENTIAL &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-credential-transact-sql).</span></span>

3.  <span data-ttu-id="6ef30-199">如果您已如第 3 節步驟 1 所述匯入非對稱金鑰，請在下列範例中提供您的金鑰名稱，以開啟金鑰。</span><span class="sxs-lookup"><span data-stu-id="6ef30-199">If you imported an asymmetric key as described earlier in step 1, section 3, open the key by providing your key name in the following example.</span></span>

    ```sql
    CREATE ASYMMETRIC KEY CONTOSO_KEY 
    FROM PROVIDER [AzureKeyVault_EKM_Prov]
    WITH PROVIDER_KEY_NAME = 'ContosoMasterKey',
    CREATION_DISPOSITION = OPEN_EXISTING;
    ```

     <span data-ttu-id="6ef30-200">雖然生產環境不建議使用 (因為無法匯出金鑰)，但是您可以從 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]直接在保存庫中建立非對稱金鑰。</span><span class="sxs-lookup"><span data-stu-id="6ef30-200">Though not recommended for production (because the key cannot be exported), it is possible to create an asymmetric key directly in the vault from [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="6ef30-201">如果您之前沒有匯入金鑰，則可以使用下列指令碼，在金鑰保存庫中建立非對稱金鑰進行測試。</span><span class="sxs-lookup"><span data-stu-id="6ef30-201">If you did not import a key earlier, then create an asymmetric key in the key vault for testing by using the following script.</span></span> <span data-ttu-id="6ef30-202">使用 **sysadmin_ekm_cred** 認證提供的登入來執行指令碼。</span><span class="sxs-lookup"><span data-stu-id="6ef30-202">Execute the script, using a login provisioned with the **sysadmin_ekm_cred** credential.</span></span>

    ```sql
    CREATE ASYMMETRIC KEY CONTOSO_KEY 
    FROM PROVIDER [AzureKeyVault_EKM_Prov]
    WITH ALGORITHM = RSA_2048,
    PROVIDER_KEY_NAME = 'ContosoMasterKey';
    ```

> [!TIP]
>  <span data-ttu-id="6ef30-203">使用者收到錯誤： **無法從提供者匯出公開金鑰。：提供者錯誤碼：2053。**</span><span class="sxs-lookup"><span data-stu-id="6ef30-203">Users receiving the error **Cannot export public key from the provider. Provider error code: 2053.**</span></span> <span data-ttu-id="6ef30-204">應該檢查其金鑰保存庫中的 **get**、 **list**、 **wrapKey**、 and **unwrapKey** 權限。</span><span class="sxs-lookup"><span data-stu-id="6ef30-204">should check their **get**, **list**, **wrapKey**, and **unwrapKey** permissions in the key vault.</span></span>

 <span data-ttu-id="6ef30-205">如需詳細資訊，請參閱下列：</span><span class="sxs-lookup"><span data-stu-id="6ef30-205">For more information, see the following:</span></span>

-   [<span data-ttu-id="6ef30-206">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="6ef30-206">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)

-   [<span data-ttu-id="6ef30-207">CREATE CRYPTOGRAPHIC PROVIDER &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="6ef30-207">CREATE CRYPTOGRAPHIC PROVIDER &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-cryptographic-provider-transact-sql)

-   [<span data-ttu-id="6ef30-208">CREATE CREDENTIAL &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="6ef30-208">CREATE CREDENTIAL &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-credential-transact-sql)

-   [<span data-ttu-id="6ef30-209">CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="6ef30-209">CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-asymmetric-key-transact-sql)

-   [<span data-ttu-id="6ef30-210">CREATE LOGIN &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="6ef30-210">CREATE LOGIN &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-login-transact-sql)

-   [<span data-ttu-id="6ef30-211">ALTER LOGIN &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="6ef30-211">ALTER LOGIN &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-login-transact-sql)

## <a name="examples"></a><span data-ttu-id="6ef30-212">範例</span><span class="sxs-lookup"><span data-stu-id="6ef30-212">Examples</span></span>

###  <a name="example-a-transparent-data-encryption-by-using-an-asymmetric-key-from-the-key-vault"></a><a name="ExampleA"></a><span data-ttu-id="6ef30-213">範例 A：使用來自 Key Vault 的非對稱金鑰透明資料加密</span><span class="sxs-lookup"><span data-stu-id="6ef30-213">Example A: Transparent Data Encryption by Using an Asymmetric Key from the Key Vault</span></span>
 <span data-ttu-id="6ef30-214">完成上述步驟之後，請建立認證和登入，並建立受到金鑰保存庫中非對稱金鑰保護的資料庫加密金鑰。</span><span class="sxs-lookup"><span data-stu-id="6ef30-214">After completing the steps above, create a credential and a login, create a database encryption key protected by the asymmetric key in the key vault.</span></span> <span data-ttu-id="6ef30-215">請使用資料庫加密金鑰透過 TDE 來加密資料庫。</span><span class="sxs-lookup"><span data-stu-id="6ef30-215">Use the database encryption key to encrypt a database with TDE.</span></span>

 <span data-ttu-id="6ef30-216">若要加密資料庫，需要資料庫的 CONTROL 權限。</span><span class="sxs-lookup"><span data-stu-id="6ef30-216">To encrypt a database requires CONTROL permission on the database.</span></span>

##### <a name="to-enable-tde-using-ekm-and-the-key-vault"></a><span data-ttu-id="6ef30-217">使用 EKM 和金鑰保存庫啟用 TDE</span><span class="sxs-lookup"><span data-stu-id="6ef30-217">To enable TDE using EKM and the Key Vault</span></span>

1.  <span data-ttu-id="6ef30-218">建立 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 認證，以供 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] 在資料庫載入期間用於存取金鑰保存庫 EKM。</span><span class="sxs-lookup"><span data-stu-id="6ef30-218">Create a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] credential for the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] to use when accessing the key vault EKM during database load.</span></span>

    > [!IMPORTANT]
    >  <span data-ttu-id="6ef30-219">的身分**識別**引數 `CREATE CREDENTIAL` 需要金鑰保存庫名稱。</span><span class="sxs-lookup"><span data-stu-id="6ef30-219">The **IDENTITY** argument of `CREATE CREDENTIAL` requires the key vault name.</span></span> <span data-ttu-id="6ef30-220">的**SECRET**引數 `CREATE CREDENTIAL` 需要 *\<Client ID>* 沒有連字號) 的 (，並在兩者 *\<Secret>* 之間一起傳遞而不會有空格。</span><span class="sxs-lookup"><span data-stu-id="6ef30-220">The **SECRET** argument of `CREATE CREDENTIAL` requires the *\<Client ID>* (without hyphens) and *\<Secret>* to be passed together without a space between them.</span></span>

     <span data-ttu-id="6ef30-221">在下列範例中， **用戶端識別碼** (`EF5C8E09-4D2A-4A76-9998-D93440D8115D`) 已移除連字號並以字串 `EF5C8E094D2A4A769998D93440D8115D` 輸入，而 **密碼** 會以字串 *SECRET_DBEngine*來表示。</span><span class="sxs-lookup"><span data-stu-id="6ef30-221">In the following example, the **Client ID** (`EF5C8E09-4D2A-4A76-9998-D93440D8115D`) is stripped of the hyphens and entered as the string `EF5C8E094D2A4A769998D93440D8115D` and the **Secret** is represented by the string *SECRET_DBEngine*.</span></span>

    ```sql
    USE master;
    CREATE CREDENTIAL Azure_EKM_TDE_cred 
        WITH IDENTITY = 'ContosoKeyVault', 
        SECRET = 'EF5C8E094D2A4A769998D93440D8115DSECRET_DBEngine' 
        FOR CRYPTOGRAPHIC PROVIDER AzureKeyVault_EKM_Prov ;
    ```

2.  <span data-ttu-id="6ef30-222">建立 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 要用於 TDE 的 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] 登入，然後加入認證。</span><span class="sxs-lookup"><span data-stu-id="6ef30-222">Create a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] login to be used by the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] for TDE, and add the credential to it.</span></span> <span data-ttu-id="6ef30-223">這個範例使用儲存在金鑰保存庫中的 CONTOSO_KEY 非對稱金鑰，這是稍早針對 master 資料庫匯入或建立的金鑰，如上面的 [第 3 節步驟 3](#Step3) 所述。</span><span class="sxs-lookup"><span data-stu-id="6ef30-223">This example uses the CONTOSO_KEY asymmetric key stored in the key vault, which was imported or created earlier for the master database, as described in [Step 3, section 3](#Step3) above.</span></span>

    ```sql
    USE master;
    -- Create a SQL Server login associated with the asymmetric key 
    -- for the Database engine to use when it loads a database 
    -- encrypted by TDE.
    CREATE LOGIN TDE_Login 
    FROM ASYMMETRIC KEY CONTOSO_KEY;
    GO 

    -- Alter the TDE Login to add the credential for use by the 
    -- Database Engine to access the key vault
    ALTER LOGIN TDE_Login 
    ADD CREDENTIAL Azure_EKM_TDE_cred ;
    GO
    ```

3.  <span data-ttu-id="6ef30-224">建立要用於 TDE 的資料庫加密金鑰 (DEK)。</span><span class="sxs-lookup"><span data-stu-id="6ef30-224">Create the database encryption key (DEK) that will be used for TDE.</span></span> <span data-ttu-id="6ef30-225">DEK 可使用 SQL Server 支援的任何演算法或金鑰長度來建立。</span><span class="sxs-lookup"><span data-stu-id="6ef30-225">The DEK can be created using any SQL Server supported algorithm or key length.</span></span> <span data-ttu-id="6ef30-226">DEK 受到金鑰保存庫中非對稱金鑰的保護。</span><span class="sxs-lookup"><span data-stu-id="6ef30-226">The DEK will be protected by the asymmetric key in the key vault.</span></span>

     <span data-ttu-id="6ef30-227">這個範例使用儲存在金鑰保存庫中的 CONTOSO_KEY 非對稱金鑰，這是稍早匯入或建立的金鑰，如上面的 [第 3 節步驟 3](#Step3) 所述。</span><span class="sxs-lookup"><span data-stu-id="6ef30-227">This example uses the CONTOSO_KEY asymmetric key stored in the key vault, which was imported or created earlier, as described in [Step 3, section 3](#Step3) above.</span></span>

    ```sql
    USE ContosoDatabase;
    GO

    CREATE DATABASE ENCRYPTION KEY 
    WITH ALGORITHM = AES_128 
    ENCRYPTION BY SERVER ASYMMETRIC KEY CONTOSO_KEY;
    GO

    -- Alter the database to enable transparent data encryption.
    ALTER DATABASE ContosoDatabase 
    SET ENCRYPTION ON ;
    GO
    ```

     <span data-ttu-id="6ef30-228">如需詳細資訊，請參閱下列：</span><span class="sxs-lookup"><span data-stu-id="6ef30-228">For more information, see the following:</span></span>

    -   [<span data-ttu-id="6ef30-229">CREATE DATABASE ENCRYPTION KEY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="6ef30-229">CREATE DATABASE ENCRYPTION KEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-database-encryption-key-transact-sql)

    -   [<span data-ttu-id="6ef30-230">ALTER DATABASE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="6ef30-230">ALTER DATABASE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-database-transact-sql)

###  <a name="example-b-encrypting-backups-by-using-an-asymmetric-key-from-the-key-vault"></a><a name="ExampleB"></a><span data-ttu-id="6ef30-231">範例 B：使用 Key Vault 中的非對稱金鑰來加密備份</span><span class="sxs-lookup"><span data-stu-id="6ef30-231">Example B: Encrypting Backups by Using an Asymmetric Key from the Key Vault</span></span>
 <span data-ttu-id="6ef30-232">自 [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)]開始，支援加密備份。</span><span class="sxs-lookup"><span data-stu-id="6ef30-232">Encrypted backups are supported starting with [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)].</span></span> <span data-ttu-id="6ef30-233">下列範例如何建立及還原以資料加密金鑰加密的備份，這個資料加密金鑰受到金鑰保存庫中非對稱金鑰的保護。</span><span class="sxs-lookup"><span data-stu-id="6ef30-233">The following example creates and restores a backup encrypted a data encryption key protected by the asymmetric key in the key vault.</span></span>

```sql
USE master;
BACKUP DATABASE [DATABASE_TO_BACKUP]
TO DISK = N'[PATH TO BACKUP FILE]' 
WITH FORMAT, INIT, SKIP, NOREWIND, NOUNLOAD, 
ENCRYPTION(ALGORITHM = AES_256, SERVER ASYMMETRIC KEY = [CONTOSO_KEY]);
GO
```

 <span data-ttu-id="6ef30-234">範例還原程式碼。</span><span class="sxs-lookup"><span data-stu-id="6ef30-234">Sample restore code.</span></span>

```sql
RESTORE DATABASE [DATABASE_TO_BACKUP]
FROM DISK = N'[PATH TO BACKUP FILE]' WITH FILE = 1, NOUNLOAD, REPLACE;
GO
```

 <span data-ttu-id="6ef30-235">如需備份選項的詳細資訊，請參閱[backup &#40;transact-sql&#41;](/sql/t-sql/statements/backup-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="6ef30-235">For more information about backup options, see [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql).</span></span>

###  <a name="example-c-column-level-encryption-by-using-an-asymmetric-key-from-the-key-vault"></a><a name="ExampleC"></a><span data-ttu-id="6ef30-236">範例 C：使用 Key Vault 中的非對稱金鑰進行資料行層級加密</span><span class="sxs-lookup"><span data-stu-id="6ef30-236">Example C: Column Level Encryption by Using an Asymmetric Key from the Key Vault</span></span>
 <span data-ttu-id="6ef30-237">下列範例會建立受到金鑰保存庫中非對稱金鑰保護的對稱金鑰。</span><span class="sxs-lookup"><span data-stu-id="6ef30-237">The following example creates a symmetric key protected by the asymmetric key in the key vault.</span></span> <span data-ttu-id="6ef30-238">然後使用對稱金鑰加密資料庫中的資料。</span><span class="sxs-lookup"><span data-stu-id="6ef30-238">Then the symmetric key is used to encrypt data in the database.</span></span>

 <span data-ttu-id="6ef30-239">這個範例使用儲存在金鑰保存庫中的 CONTOSO_KEY 非對稱金鑰，這是稍早匯入或建立的金鑰，如上面的 [第 3 節步驟 3](#Step3) 所述。</span><span class="sxs-lookup"><span data-stu-id="6ef30-239">This example uses the CONTOSO_KEY asymmetric key stored in the key vault, which was imported or created earlier, as described in [Step 3, section 3](#Step3) above.</span></span> <span data-ttu-id="6ef30-240">若要在 `ContosoDatabase` 資料庫中使用這個非對稱金鑰，您必須再執行一次 CREATE ASYMMETRIC KEY 陳述式，以提供參考這個金鑰的 `ContosoDatabase` 資料庫。</span><span class="sxs-lookup"><span data-stu-id="6ef30-240">To use this asymmetric key in the `ContosoDatabase` database, you must execute the CREATE ASYMMETRIC KEY statement again, to provide the `ContosoDatabase` database with a reference to the key.</span></span>

```sql
USE [ContosoDatabase];
GO

-- Create a reference to the key in the key vault
CREATE ASYMMETRIC KEY CONTOSO_KEY 
FROM PROVIDER [AzureKeyVault_EKM_Prov]
WITH PROVIDER_KEY_NAME = 'ContosoMasterKey',
CREATION_DISPOSITION = OPEN_EXISTING;

-- Create the data encryption key.
-- The data encryption key can be created using any SQL Server 
-- supported algorithm or key length.
-- The DEK will be protected by the asymmetric key in the key vault

CREATE SYMMETRIC KEY DATA_ENCRYPTION_KEY
    WITH ALGORITHM=AES_256
    ENCRYPTION BY ASYMMETRIC KEY CONTOSO_KEY;

DECLARE @DATA VARBINARY(MAX);

--Open the symmetric key for use in this session
OPEN SYMMETRIC KEY DATA_ENCRYPTION_KEY 
DECRYPTION BY ASYMMETRIC KEY CONTOSO_KEY;

--Encrypt syntax
SELECT @DATA = ENCRYPTBYKEY(KEY_GUID('DATA_ENCRYPTION_KEY'), CONVERT(VARBINARY,'Plain text data to encrypt'));

-- Decrypt syntax
SELECT CONVERT(VARCHAR, DECRYPTBYKEY(@DATA));

--Close the symmetric key
CLOSE SYMMETRIC KEY DATA_ENCRYPTION_KEY;
```

## <a name="see-also"></a><span data-ttu-id="6ef30-241">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6ef30-241">See Also</span></span>
 <span data-ttu-id="6ef30-242">[建立密碼編譯提供者 &#40;transact-sql&#41;](/sql/t-sql/statements/create-cryptographic-provider-transact-sql) [建立認證 &#40;TRANSACT-SQL&#41;](/sql/t-sql/statements/create-credential-transact-sql) [建立非對稱金鑰 &#40;transact-sql&#41;](/sql/t-sql/statements/create-asymmetric-key-transact-sql) [建立對稱金鑰 &#40;TRANSACT-SQL](/sql/t-sql/statements/create-symmetric-key-transact-sql)&#41;可延伸[金鑰管理 &#40;EKM&#41;](extensible-key-management-ekm.md) [使用 ekm 備份加密來啟用 TDE](enable-tde-on-sql-server-using-ekm.md) [Backup Encryption](../../backup-restore/backup-encryption.md) [建立加密備份](../../backup-restore/create-an-encrypted-backup.md)</span><span class="sxs-lookup"><span data-stu-id="6ef30-242">[CREATE CRYPTOGRAPHIC PROVIDER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-cryptographic-provider-transact-sql) [CREATE CREDENTIAL &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-credential-transact-sql) [CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-asymmetric-key-transact-sql) [CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-symmetric-key-transact-sql) [Extensible Key Management &#40;EKM&#41;](extensible-key-management-ekm.md) [Enable TDE Using EKM](enable-tde-on-sql-server-using-ekm.md) [Backup Encryption](../../backup-restore/backup-encryption.md) [Create an Encrypted Backup](../../backup-restore/create-an-encrypted-backup.md)</span></span>
