---
title: rskeymgmt 公用程式 (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- report servers [Reporting Services], encryption
- joining report server instances [SQL Server]
- report server scale-out deployments [Reporting Services]
- cryptography [Reporting Services]
- multiple report server instances
- command prompt utilities [Reporting Services]
- report servers [Reporting Services], scale-out deployments
- encryption [Reporting Services]
- rskeymgmt utility
- scale-out deployments [Reporting Services]
ms.assetid: 53f1318d-bd2d-4c08-b19f-c8b698b5b3d3
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ae4bdd6656cf5b29f8fd40fcf730f49a6de8f32e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704821"
---
# <a name="rskeymgmt-utility-ssrs"></a><span data-ttu-id="b1baf-102">rskeymgmt 公用程式 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="b1baf-102">rskeymgmt Utility (SSRS)</span></span>
  <span data-ttu-id="b1baf-103">擷取、還原、建立和刪除「用來保護機密報表伺服器資料，以免遭到未獲授權的存取」之對稱金鑰。</span><span class="sxs-lookup"><span data-stu-id="b1baf-103">Extracts, restores, creates, and deletes the symmetric key used to protect sensitive report server data against unauthorized access.</span></span> <span data-ttu-id="b1baf-104">另外，這個公用程式也用來將報表伺服器執行個體聯結在向外延展部署中。</span><span class="sxs-lookup"><span data-stu-id="b1baf-104">This utility is also used to join report server instances in a scale-out deployment.</span></span> <span data-ttu-id="b1baf-105">「報表伺服器向外延展部署」  是指共用單一報表伺服器資料庫的多個報表伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="b1baf-105">A *report server scale-out deployment* refers to multiple report server instances that share a single report server database.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1baf-106">語法</span><span class="sxs-lookup"><span data-stu-id="b1baf-106">Syntax</span></span>  
  
```  
  
      rskeymgmt {-?}  
{-eextract}  
{-aapply}  
{-ddeleteall}  
{-srecreatekey}  
{-rremoveinstancekey}  
{-jjoinfarm}  
{-iinstance}  
{-ffile}  
{-pencryptionpassword}  
{-mremotecomputer}  
{-ninstancenameofremotecomputer}  
{-uadministratoruseraccount}  
{-vadministratorpassword}  
{-ttrace}  
```  
  
## <a name="arguments"></a><span data-ttu-id="b1baf-107">引數</span><span class="sxs-lookup"><span data-stu-id="b1baf-107">Arguments</span></span>  
 <span data-ttu-id="b1baf-108">**-?**</span><span class="sxs-lookup"><span data-stu-id="b1baf-108">**-?**</span></span>  
 <span data-ttu-id="b1baf-109">顯示 **rskeymgmt** 引數的語法。</span><span class="sxs-lookup"><span data-stu-id="b1baf-109">Displays the syntax of **rskeymgmt** arguments.</span></span>  
  
 <span data-ttu-id="b1baf-110">**-e**</span><span class="sxs-lookup"><span data-stu-id="b1baf-110">**-e**</span></span>  
 <span data-ttu-id="b1baf-111">擷取「用來加密和解密報表伺服器執行個體的資料，以便將它複製到檔案中」之對稱金鑰。</span><span class="sxs-lookup"><span data-stu-id="b1baf-111">Extracts the symmetric key used to encrypt and decrypt data for the report server instance so that you can copy it to a file.</span></span>  
  
 <span data-ttu-id="b1baf-112">此引數沒有取得值。</span><span class="sxs-lookup"><span data-stu-id="b1baf-112">This argument does not take a value.</span></span> <span data-ttu-id="b1baf-113">不過，命令列必須包括其他引數，才能完成擷取作業。</span><span class="sxs-lookup"><span data-stu-id="b1baf-113">However, you must include additional arguments on the command line to complete the extraction.</span></span> <span data-ttu-id="b1baf-114">您必須指定的引數包括 `-f` 和 `-p`。</span><span class="sxs-lookup"><span data-stu-id="b1baf-114">The arguments that you must specify include `-f` and`-p`.</span></span>  
  
 <span data-ttu-id="b1baf-115">**-a**</span><span class="sxs-lookup"><span data-stu-id="b1baf-115">**-a**</span></span>  
 <span data-ttu-id="b1baf-116">利用密碼保護的備份檔所提供之副本來取代現有的對稱金鑰。</span><span class="sxs-lookup"><span data-stu-id="b1baf-116">Replaces an existing symmetric key with a copy that you provide in a password protected backup file.</span></span> <span data-ttu-id="b1baf-117">這會更新對稱金鑰的所有執行個體。</span><span class="sxs-lookup"><span data-stu-id="b1baf-117">All instances of the symmetric key are updated.</span></span>  
  
 <span data-ttu-id="b1baf-118">此引數沒有取得值。</span><span class="sxs-lookup"><span data-stu-id="b1baf-118">This argument does not take a value.</span></span> <span data-ttu-id="b1baf-119">不過，命令列必須包括其他引數，才能選取要套用的金鑰所在的檔案。</span><span class="sxs-lookup"><span data-stu-id="b1baf-119">However, you must include additional arguments on the command line to select the file that contains the key to be applied.</span></span> <span data-ttu-id="b1baf-120">您可以指定的引數包括 `-f` 和 `-p`。</span><span class="sxs-lookup"><span data-stu-id="b1baf-120">The arguments that you can specify include `-f` and`-p`.</span></span>  
  
 <span data-ttu-id="b1baf-121">**-d**</span><span class="sxs-lookup"><span data-stu-id="b1baf-121">**-d**</span></span>  
 <span data-ttu-id="b1baf-122">刪除所有對稱金鑰執行個體及報表伺服器資庫中所有已加密的資料。</span><span class="sxs-lookup"><span data-stu-id="b1baf-122">Deletes all symmetric key instances and all encrypted data in a report server database.</span></span> <span data-ttu-id="b1baf-123">此引數沒有取得值。</span><span class="sxs-lookup"><span data-stu-id="b1baf-123">This argument does not take a value.</span></span>  
  
 `-s`  
 <span data-ttu-id="b1baf-124">產生新的對稱金鑰，以及利用新的金鑰來重新加密所有已加密的內容。</span><span class="sxs-lookup"><span data-stu-id="b1baf-124">Generates a new symmetric key and re-encrypts all encrypted content using the new key.</span></span> <span data-ttu-id="b1baf-125">這會重新產生對稱金鑰的所有執行個體。</span><span class="sxs-lookup"><span data-stu-id="b1baf-125">All instances of the symmetric key are regenerated.</span></span>  
  
 `-j`  
 <span data-ttu-id="b1baf-126">設定遠端報表伺服器執行個體來共用本機報表伺服器執行個體所用的報表伺服器資料庫。</span><span class="sxs-lookup"><span data-stu-id="b1baf-126">Configures a remote report server instance to share the report server database that is used by the local report server instance.</span></span>  
  
 <span data-ttu-id="b1baf-127">**-r**  *installationID*</span><span class="sxs-lookup"><span data-stu-id="b1baf-127">**-r**  *installationID*</span></span>  
 <span data-ttu-id="b1baf-128">移除特定報表伺服器執行個體的對稱金鑰資訊，因而從向外延展部署中移除報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="b1baf-128">Removes the symmetric key information for a specific report server instance, thereby removing the report server from a scale-out deployment.</span></span> <span data-ttu-id="b1baf-129"><安裝識別碼>\*\* 是一個 GUID 值，可在 RSReportserver.config 檔中找到它。</span><span class="sxs-lookup"><span data-stu-id="b1baf-129">The *installationID* is a GUID value that can be found in the RSReportserver.config file.</span></span>  
  
 <span data-ttu-id="b1baf-130">`-f`  *文字檔*</span><span class="sxs-lookup"><span data-stu-id="b1baf-130">`-f`  *file*</span></span>  
 <span data-ttu-id="b1baf-131">指定儲存了對稱金鑰備份副本之檔案的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="b1baf-131">Specifies a fully qualified path to the file that stores a backup copy of the symmetric keys.</span></span>  
  
 <span data-ttu-id="b1baf-132">若為 **rskeymgmt -e**，對稱金鑰會寫入您指定的檔案中。</span><span class="sxs-lookup"><span data-stu-id="b1baf-132">For **rskeymgmt -e**, the symmetric key is written to the file you specify.</span></span>  
  
 <span data-ttu-id="b1baf-133">若為 **rskeymgmt -a**，便會將檔案中所儲存的對稱金鑰值套用在報表伺服器執行個體上。</span><span class="sxs-lookup"><span data-stu-id="b1baf-133">For **rskeymgmt -a**, the symmetric key value stored in the file is applied to the report server instance.</span></span>  
  
 <span data-ttu-id="b1baf-134">`-p`  *許可權*</span><span class="sxs-lookup"><span data-stu-id="b1baf-134">`-p`  *password*</span></span>  
 <span data-ttu-id="b1baf-135">(`-f` 需要這個引數) 指定用來備份或套用對稱金鑰的密碼。</span><span class="sxs-lookup"><span data-stu-id="b1baf-135">(Required for `-f`) Specifies the password used to back up or apply a symmetric key.</span></span> <span data-ttu-id="b1baf-136">這個值不能空白。</span><span class="sxs-lookup"><span data-stu-id="b1baf-136">This value cannot be empty.</span></span>  
  
 `-i`  
 <span data-ttu-id="b1baf-137">指定本機報表伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="b1baf-137">Specifies a local report server instance.</span></span> <span data-ttu-id="b1baf-138">如果您將報表伺服器安裝在預設的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體上，這個引數就是選擇性的 (`-i` 的預設值是 MSSQLSERVER)。</span><span class="sxs-lookup"><span data-stu-id="b1baf-138">This argument is optional if you installed the report server on the default [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance (the default value for `-i` is MSSQLSERVER).</span></span> <span data-ttu-id="b1baf-139">若您將報表伺服器安裝成具名執行個體，就需要 `-i`。</span><span class="sxs-lookup"><span data-stu-id="b1baf-139">If you installed the report server as a named instance, `-i` is required.</span></span>  
  
 `-m`  
 <span data-ttu-id="b1baf-140">指定要聯結至報表伺服器向外延展部署中，主控報表伺服器執行個體的遠端電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="b1baf-140">Specifies the name of the remote computer that hosts the report server instance you are joining to the report server scale-out deployment.</span></span> <span data-ttu-id="b1baf-141">請使用在網路中用來識別這部電腦的名稱。</span><span class="sxs-lookup"><span data-stu-id="b1baf-141">Use the name of the computer that identifies it on your network.</span></span>  
  
 `-n`  
 <span data-ttu-id="b1baf-142">指定遠端電腦中之報表伺服器執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="b1baf-142">Specifies the name of the report server instance on a remote computer.</span></span> <span data-ttu-id="b1baf-143">如果您將報表伺服器安裝在預設的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體上，這個引數就是選擇性的 (`-n` 的預設值是 MSSQLSERVER)。</span><span class="sxs-lookup"><span data-stu-id="b1baf-143">This argument is optional if you installed the report server on the default [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance (the default value for `-n` is MSSQLSERVER).</span></span> <span data-ttu-id="b1baf-144">若您將報表伺服器安裝成具名執行個體，就需要 `-n`。</span><span class="sxs-lookup"><span data-stu-id="b1baf-144">If you installed the report server as a named instance, `-n` is required.</span></span>  
  
 <span data-ttu-id="b1baf-145">`-u`  *useraccount*</span><span class="sxs-lookup"><span data-stu-id="b1baf-145">`-u`  *useraccount*</span></span>  
 <span data-ttu-id="b1baf-146">指定要聯結至向外延展部署中之遠端電腦的管理員帳戶。</span><span class="sxs-lookup"><span data-stu-id="b1baf-146">Specifies the administrator account on the remote computer that you are joining to the scale-out deployment.</span></span> <span data-ttu-id="b1baf-147">如果未指定帳戶，就會使用目前使用者的認證。</span><span class="sxs-lookup"><span data-stu-id="b1baf-147">If an account is not specified, the credentials of the current user are used.</span></span>  
  
 <span data-ttu-id="b1baf-148">`-v`  *許可權*</span><span class="sxs-lookup"><span data-stu-id="b1baf-148">`-v`  *password*</span></span>  
 <span data-ttu-id="b1baf-149">(`-u` 需要這個引數) 指定要聯結至向外延展部署中之遠端電腦的管理員帳戶密碼。</span><span class="sxs-lookup"><span data-stu-id="b1baf-149">(Required for `-u`) Specifies the password of an administrator account on the remote computer that you want to join to the scale-out deployment.</span></span>  
  
 <span data-ttu-id="b1baf-150">**-t**  *追蹤*</span><span class="sxs-lookup"><span data-stu-id="b1baf-150">**-t**  *trace*</span></span>  
 <span data-ttu-id="b1baf-151">在追蹤記錄中，輸出錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="b1baf-151">Outputs error messages to the trace log.</span></span> <span data-ttu-id="b1baf-152">此引數沒有取得值。</span><span class="sxs-lookup"><span data-stu-id="b1baf-152">This argument does not take a value.</span></span> <span data-ttu-id="b1baf-153">如需詳細資訊，請參閱 [Report Server Service Trace Log](../report-server/report-server-service-trace-log.md)。</span><span class="sxs-lookup"><span data-stu-id="b1baf-153">For more information, see [Report Server Service Trace Log](../report-server/report-server-service-trace-log.md).</span></span>  
  
## <a name="permissions"></a><span data-ttu-id="b1baf-154">權限</span><span class="sxs-lookup"><span data-stu-id="b1baf-154">Permissions</span></span>  
 <span data-ttu-id="b1baf-155">您必須是執行這套工具的本機管理員，且您必須在主控報表伺服器之電腦的本機環境中執行它。</span><span class="sxs-lookup"><span data-stu-id="b1baf-155">You must be a local administrator to run the tool, and you must run it locally on the computer that hosts the report server.</span></span> <span data-ttu-id="b1baf-156">rskeymgmt 公用程式會使用本機報表伺服器 Windows 執行個體 (這個公用程式無法連接報表伺服器 Windows 服務的遠端執行個體，因此，您無法利用它來管理遠端報表伺服器執行個體的加密金鑰)。</span><span class="sxs-lookup"><span data-stu-id="b1baf-156">The rskeymgmt utility works with the local Report Server Windows instance (the utility cannot connect to remote instances of the Report Server Windows service so it cannot be used to manage the encryption keys of a remote report server instance).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b1baf-157">如果您使用 `-u` 和 `-v` 引數，請務必指定對遠端電腦具有管理員權限的帳戶。</span><span class="sxs-lookup"><span data-stu-id="b1baf-157">If you are using the `-u` and `-v` arguments, be sure to specify an account that has administrator permissions on the remote computer.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="b1baf-158">範例</span><span class="sxs-lookup"><span data-stu-id="b1baf-158">Examples</span></span>  
 <span data-ttu-id="b1baf-159">下列範例說明 **rskeymgmt**的使用方式。</span><span class="sxs-lookup"><span data-stu-id="b1baf-159">The following examples illustrate ways of using **rskeymgmt**.</span></span> <span data-ttu-id="b1baf-160">下列範例會顯示如何擷取、還原和刪除加密金鑰，以及如何設定報表伺服器的向外延展部署。</span><span class="sxs-lookup"><span data-stu-id="b1baf-160">The following examples show how to extract, restore, and delete encryption keys, and how to configure a report server scale-out deployment.</span></span>  
  
#### <a name="extracting-encryption-keys"></a><span data-ttu-id="b1baf-161">擷取加密金鑰</span><span class="sxs-lookup"><span data-stu-id="b1baf-161">Extracting Encryption Keys</span></span>  
 <span data-ttu-id="b1baf-162">這個範例會顯示如何建立加密金鑰的備份副本，以及將它儲存在磁碟片的密碼保護檔案中。</span><span class="sxs-lookup"><span data-stu-id="b1baf-162">This example shows how to create a backup copy of the encryption key and save it to a password-protected file on a floppy disk.</span></span> <span data-ttu-id="b1baf-163">如果報表伺服器安裝成具名執行個體，請加入 `-i` 引數。</span><span class="sxs-lookup"><span data-stu-id="b1baf-163">If the report server is installed as a named instance, add the `-i` argument.</span></span>  
  
```  
rskeymgmt -e -f a:\backupkey\keys -p <password>  
```  
  
#### <a name="restoring-encryption-keys"></a><span data-ttu-id="b1baf-164">還原加密金鑰</span><span class="sxs-lookup"><span data-stu-id="b1baf-164">Restoring Encryption Keys</span></span>  
 <span data-ttu-id="b1baf-165">這個範例會顯示如何取代加密金鑰。</span><span class="sxs-lookup"><span data-stu-id="b1baf-165">This example shows how to replace the encryption key.</span></span> <span data-ttu-id="b1baf-166">您必須指定金鑰備份副本的位置以及將檔案解除鎖定的密碼。</span><span class="sxs-lookup"><span data-stu-id="b1baf-166">You must specify the location of the backup copy of the key and the password that unlocks the file.</span></span>  
  
```  
rskeymgmt -a -f a:\backupkey\keys -p <password>  
```  
  
#### <a name="deleting-encryption-keys-and-encrypted-content"></a><span data-ttu-id="b1baf-167">刪除加密金鑰和加密內容</span><span class="sxs-lookup"><span data-stu-id="b1baf-167">Deleting Encryption Keys and Encrypted Content</span></span>  
 <span data-ttu-id="b1baf-168">這個範例會顯示如何刪除報表伺服器所儲存的所有加密金鑰。</span><span class="sxs-lookup"><span data-stu-id="b1baf-168">This example shows how to delete all encryption keys stored in a report server.</span></span> <span data-ttu-id="b1baf-169">如果您的安裝架構是一項報表伺服器向外延展部署，便會刪除部署所包含的所有報表伺服器執行個體的加密金鑰。</span><span class="sxs-lookup"><span data-stu-id="b1baf-169">If your installation is a report server scale-out deployment, the encryption keys for all report server instances that are included in the deployment will be deleted.</span></span> <span data-ttu-id="b1baf-170">刪除加密金鑰也會刪除報表伺服器資料庫中任何現有的加密值。</span><span class="sxs-lookup"><span data-stu-id="b1baf-170">Deleting an encryption key also deletes any existing encrypted values in the report server database.</span></span> <span data-ttu-id="b1baf-171">如需加密內容的詳細資訊，請參閱[儲存加密的報表伺服器資料 &#40;SSRS 設定管理員&#41;](../install-windows/ssrs-encryption-keys-store-encrypted-report-server-data.md)。</span><span class="sxs-lookup"><span data-stu-id="b1baf-171">For more information about encrypted content, see [Store Encrypted Report Server Data &#40;SSRS Configuration Manager&#41;](../install-windows/ssrs-encryption-keys-store-encrypted-report-server-data.md).</span></span>  
  
```  
rskeymgmt -d  
```  
  
#### <a name="joining-a-remote-report-server-named-instance-to-a-scale-out-deployment"></a><span data-ttu-id="b1baf-172">將遠端報表伺服器具名執行個體聯結至向外延展部署中</span><span class="sxs-lookup"><span data-stu-id="b1baf-172">Joining a Remote Report Server Named Instance to a Scale-out Deployment</span></span>  
 <span data-ttu-id="b1baf-173">這個範例會顯示如何將遠端電腦所安裝的報表伺服器執行個體加入報表伺服器向外延展部署中。</span><span class="sxs-lookup"><span data-stu-id="b1baf-173">This example shows how to add a report server instance that is installed on a remote computer to a report server scale-out deployment.</span></span> <span data-ttu-id="b1baf-174">您必須在已設定成要使用共用資料庫的其中一部電腦中執行這個命令。</span><span class="sxs-lookup"><span data-stu-id="b1baf-174">You must run the command on one of the computers that is already configured to use the shared database.</span></span> <span data-ttu-id="b1baf-175">命令引數會指定要聯結至向外延展部署中的遠端報表伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="b1baf-175">The command arguments specify the remote report server instance you want to join to the scale-out deployment.</span></span>  
  
```  
rskeymgmt -j -m <remotecomputer> -n <namedreportserverinstance> -u <administratoraccount> -v <administratorpassword>  
```  
  
> [!NOTE]  
>  <span data-ttu-id="b1baf-176">報表伺服器向外延展部署是指多個報表伺服器執行個體共用相同報表伺服器資料庫的部署模型。</span><span class="sxs-lookup"><span data-stu-id="b1baf-176">A report server scale-out deployment refers to a deployment model where multiple report server instances share the same report server database.</span></span> <span data-ttu-id="b1baf-177">對稱金鑰儲存在報表伺服器資料庫中的任何報表伺服器執行個體，都可以使用報表伺服器資料庫。</span><span class="sxs-lookup"><span data-stu-id="b1baf-177">A report server database can be used by any report server instance that stores its symmetric keys in the database.</span></span> <span data-ttu-id="b1baf-178">例如，如果報表伺服器資料庫包含三個報表伺服器執行個體的金鑰資訊，這三個執行個體都會被視為相同向外延展部署的成員。</span><span class="sxs-lookup"><span data-stu-id="b1baf-178">For example, if a report server database contains key information for three report server instances, all three instances are considered to members of the same scale-out deployment.</span></span>  
  
#### <a name="joining-report-server-instances-on-the-same-computer"></a><span data-ttu-id="b1baf-179">在相同電腦上聯結報表伺服器執行個體</span><span class="sxs-lookup"><span data-stu-id="b1baf-179">Joining Report Server Instances on the Same Computer</span></span>  
 <span data-ttu-id="b1baf-180">您可以從安裝在相同電腦上的多個報表伺服器執行個體中建立向外延展部署。</span><span class="sxs-lookup"><span data-stu-id="b1baf-180">You can create a scale-out deployment from multiple report server instances that are installed on the same computer.</span></span> <span data-ttu-id="b1baf-181">如果您要聯結的報表伺服器執行個體是安裝在本機，請不要設定 `-u` 和 `-v` 引數。</span><span class="sxs-lookup"><span data-stu-id="b1baf-181">Do not set the `-u` and `-v` arguments if you are joining report server instances that are installed locally.</span></span> <span data-ttu-id="b1baf-182">只有當您從遠端電腦聯結執行個體時，才要使用 `-u` 和 `-v` 引數。</span><span class="sxs-lookup"><span data-stu-id="b1baf-182">The `-u` and `-v` arguments are used only when you are joining an instance from a remote computer.</span></span> <span data-ttu-id="b1baf-183">如果您指定這些引數，會出現下列錯誤：「使用者認證無法用於本機連接。」</span><span class="sxs-lookup"><span data-stu-id="b1baf-183">If you specify the arguments, you will get the following error: "User credentials cannot be used for local connections."</span></span>  
  
 <span data-ttu-id="b1baf-184">下列範例說明使用多個本機執行個體建立向外延展部署的語法。</span><span class="sxs-lookup"><span data-stu-id="b1baf-184">The following example illustrates the syntax for creating a scale-out deployment using multiple local instances.</span></span> <span data-ttu-id="b1baf-185">在此範例中，<`initializedinstance`> 是已初始化來使用報表伺服器資料庫的實例名稱，而 <`newinstance`> 是您想要加入至部署之實例的名稱：</span><span class="sxs-lookup"><span data-stu-id="b1baf-185">In this example, <`initializedinstance`> is the name of an instance that is already initialized to use the report server database, and <`newinstance`> is the name of the instance that you want to add to the deployment:</span></span>  
  
```  
rskeymgmt -j -i <initializedinstance> -m <computer name> -n <newinstance>  
```  
  
#### <a name="removing-encryption-keys-for-a-single-report-server-in-a-scale-out-deployment"></a><span data-ttu-id="b1baf-186">移除向外延展部署中之單一報表伺服器的加密金鑰</span><span class="sxs-lookup"><span data-stu-id="b1baf-186">Removing Encryption Keys for a Single Report Server in a Scale-out Deployment</span></span>  
 <span data-ttu-id="b1baf-187">這個範例會顯示如何在報表伺服器的向外延展部署中，移除單一報表伺服器的加密金鑰。</span><span class="sxs-lookup"><span data-stu-id="b1baf-187">This example shows how to remove the encryption keys for a single report server in a report server scale-out deployment.</span></span> <span data-ttu-id="b1baf-188">這些金鑰會從報表伺服器資料庫中移除。</span><span class="sxs-lookup"><span data-stu-id="b1baf-188">The keys are removed from the report server database.</span></span> <span data-ttu-id="b1baf-189">移除報表伺服器執行個體的金鑰之後，這個報表伺服器執行個體就無法存取資料庫中的加密資料，此時便從這項向外延展部署中將它有效地移除。</span><span class="sxs-lookup"><span data-stu-id="b1baf-189">Once the keys for that report server instance are removed, that report server instance can no longer access encrypted data in the database, effectively removing it from the scale-out deployment.</span></span>  
  
 <span data-ttu-id="b1baf-190">您必須指定安裝識別碼，才能從向外延展部署中移除報表伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="b1baf-190">Removing a report server instance from a scale-out deployment requires you to specify an installation ID.</span></span> <span data-ttu-id="b1baf-191">安裝識別碼是在您想要移除加密金鑰之報表伺服器執行個體的 RSReportserver.config 檔中儲存的 GUID。</span><span class="sxs-lookup"><span data-stu-id="b1baf-191">The installation ID is a GUID stored in the RSReportserver.config file of the report server instance for which you want to remove encryption keys.</span></span> <span data-ttu-id="b1baf-192">您必須在要從向外延展部署中移除的電腦上執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="b1baf-192">You must run the following command on the computer that you want to remove from the scale-out deployment.</span></span> <span data-ttu-id="b1baf-193">如果報表伺服器安裝成具名執行個體，請利用 `-i` 引數來指定執行個體。</span><span class="sxs-lookup"><span data-stu-id="b1baf-193">If the report server is installed as a named instance, use the `-i` argument to specify the instance.</span></span> <span data-ttu-id="b1baf-194">如需詳細資訊，請參閱 [RSReportServer Configuration File](../report-server/rsreportserver-config-configuration-file.md)。</span><span class="sxs-lookup"><span data-stu-id="b1baf-194">For more information, see [RSReportServer Configuration File](../report-server/rsreportserver-config-configuration-file.md).</span></span>  
  
```  
rskeymgmt -r <installationID>  
```  
  
## <a name="file-location"></a><span data-ttu-id="b1baf-195">檔案位置</span><span class="sxs-lookup"><span data-stu-id="b1baf-195">File Location</span></span>  
 <span data-ttu-id="b1baf-196">Rskeymgmt.exe 位於\*\* \<*drive*> ： \PROGRAM Files\Microsoft sql Server\110\Tools\Binn**或 At \*\* \<*drive*> ： \Program FILES (x86) \microsoft sql Server\110\Tools\Binn**。</span><span class="sxs-lookup"><span data-stu-id="b1baf-196">Rskeymgmt.exe is located at **\<*drive*>:\Program Files\Microsoft SQL Server\110\Tools\Binn** or at **\<*drive*>:\Program Files (x86)\Microsoft SQL Server\110\Tools\Binn**.</span></span> <span data-ttu-id="b1baf-197">您可以從檔案系統上的任何資料夾執行此公用程式。</span><span class="sxs-lookup"><span data-stu-id="b1baf-197">You can run the utility from any folder on your file system.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b1baf-198">備註</span><span class="sxs-lookup"><span data-stu-id="b1baf-198">Remarks</span></span>  
 <span data-ttu-id="b1baf-199">報表伺服器會加密預存的認證和連接資訊。</span><span class="sxs-lookup"><span data-stu-id="b1baf-199">A report server encrypts stored credentials and connection information.</span></span> <span data-ttu-id="b1baf-200">資料的加密使用公開金鑰和對稱金鑰。</span><span class="sxs-lookup"><span data-stu-id="b1baf-200">A public key and a symmetric key are used to encrypt data.</span></span> <span data-ttu-id="b1baf-201">報表伺服器資料庫必須具備有效的金鑰，報表伺服器才能夠執行。</span><span class="sxs-lookup"><span data-stu-id="b1baf-201">A report server database must have valid keys in order for the report server to run.</span></span> <span data-ttu-id="b1baf-202">您可以使用 **rskeymgmt** 來備份、刪除或還原金鑰。</span><span class="sxs-lookup"><span data-stu-id="b1baf-202">You can use **rskeymgmt** to back up, delete, or restore the keys.</span></span> <span data-ttu-id="b1baf-203">如果金鑰無法還原，這個工具可用來刪除已無法使用的加密內容。</span><span class="sxs-lookup"><span data-stu-id="b1baf-203">If the keys cannot be restored, this tool provides a way to delete encrypted content that can no longer be used.</span></span>  
  
 <span data-ttu-id="b1baf-204">**rskeymgmt** 公用程式用來管理安裝期間或初始化期間所定義的金鑰組。</span><span class="sxs-lookup"><span data-stu-id="b1baf-204">The **rskeymgmt** utility is used to manage the key set that is defined during Setup or during initialization.</span></span> <span data-ttu-id="b1baf-205">它利用遠端程序呼叫 (RPC) 端點來連接本機報表伺服器 Windows 服務。</span><span class="sxs-lookup"><span data-stu-id="b1baf-205">It connects to the local Report Server Windows service through a Remote Procedure Call (RPC) endpoint.</span></span> <span data-ttu-id="b1baf-206">報表伺服器 Windows 服務必須在執行中，這個公用程式才能運作。</span><span class="sxs-lookup"><span data-stu-id="b1baf-206">The Report Server Windows service must be running in order for this utility to work.</span></span>  
  
 <span data-ttu-id="b1baf-207">如需加密金鑰的詳細資訊，請參閱[設定和管理加密金鑰 &#40;SSRS 設定管理員&#41;](../install-windows/ssrs-encryption-keys-manage-encryption-keys.md) 和[初始化報表伺服器 &#40;SSRS 設定管理員&#41;](../install-windows/ssrs-encryption-keys-initialize-a-report-server.md)。</span><span class="sxs-lookup"><span data-stu-id="b1baf-207">For more information about the encryption keys, see [Configure and Manage Encryption Keys &#40;SSRS Configuration Manager&#41;](../install-windows/ssrs-encryption-keys-manage-encryption-keys.md) and [Initialize a Report Server &#40;SSRS Configuration Manager&#41;](../install-windows/ssrs-encryption-keys-initialize-a-report-server.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1baf-208">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b1baf-208">See Also</span></span>  
 <span data-ttu-id="b1baf-209">[設定原生模式報表伺服器向外延展部署 &#40;SSRS Configuration Manager&#41;](../install-windows/configure-a-native-mode-report-server-scale-out-deployment.md) </span><span class="sxs-lookup"><span data-stu-id="b1baf-209">[Configure a Native Mode Report Server Scale-Out Deployment &#40;SSRS Configuration Manager&#41;](../install-windows/configure-a-native-mode-report-server-scale-out-deployment.md) </span></span>  
 <span data-ttu-id="b1baf-210">[Reporting Services 報表伺服器 &#40;原生模式&#41;](../report-server/reporting-services-report-server-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="b1baf-210">[Reporting Services Report Server &#40;Native Mode&#41;](../report-server/reporting-services-report-server-native-mode.md) </span></span>  
 <span data-ttu-id="b1baf-211">[&#40;SSRS&#41;的報表伺服器命令提示字元公用程式](report-server-command-prompt-utilities-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="b1baf-211">[Report Server Command Prompt Utilities &#40;SSRS&#41;](report-server-command-prompt-utilities-ssrs.md) </span></span>  
 [<span data-ttu-id="b1baf-212">設定和管理加密金鑰 &#40;SSRS 組態管理員&#41;</span><span class="sxs-lookup"><span data-stu-id="b1baf-212">Configure and Manage Encryption Keys &#40;SSRS Configuration Manager&#41;</span></span>](../install-windows/ssrs-encryption-keys-manage-encryption-keys.md)  
  
  
