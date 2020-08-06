---
title: 複寫加密資料行中的資料 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- encryption [SQL Server], replicating data
- encryption [SQL Server replication]
- publishing [SQL Server replication], encrypted columns
ms.assetid: d1f8f586-e5a3-4a71-9391-11198d42bfa3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2e1528d81faa352fdcdf37abe9ad93fda190445c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701038"
---
# <a name="replicate-data-in-encrypted-columns-sql-server-management-studio"></a><span data-ttu-id="70c1c-102">複寫加密資料行中的資料 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="70c1c-102">Replicate Data in Encrypted Columns (SQL Server Management Studio)</span></span>
  <span data-ttu-id="70c1c-103">複寫讓您可以發行加密的資料行資料。</span><span class="sxs-lookup"><span data-stu-id="70c1c-103">Replication enables you to publish encrypted column data.</span></span> <span data-ttu-id="70c1c-104">若要在訂閱者端解密及使用此資料，於發行者端用來加密資料的金鑰也必須存在訂閱者端。</span><span class="sxs-lookup"><span data-stu-id="70c1c-104">To decrypt and use this data at the Subscriber, the key that was used to encrypt the data at the Publisher must also be present on the Subscriber.</span></span> <span data-ttu-id="70c1c-105">複寫並不會提供用於傳輸加密金鑰的安全機制。</span><span class="sxs-lookup"><span data-stu-id="70c1c-105">Replication does not provide a secure mechanism to transport encryption keys.</span></span> <span data-ttu-id="70c1c-106">您必須以手動方式於訂閱者端重新建立加密金鑰。</span><span class="sxs-lookup"><span data-stu-id="70c1c-106">You must manually re-create the encryption key at the Subscriber.</span></span> <span data-ttu-id="70c1c-107">本主題示範如何於發行者端加密資料行，並確定訂閱者端可使用加密金鑰。</span><span class="sxs-lookup"><span data-stu-id="70c1c-107">This topic shows you how to encrypt a column at the Publisher and make sure that the encryption key is available at the Subscriber.</span></span>  
  
 <span data-ttu-id="70c1c-108">基本步驟如下：</span><span class="sxs-lookup"><span data-stu-id="70c1c-108">The basic steps are as follows:</span></span>  
  
1.  <span data-ttu-id="70c1c-109">於發行者端建立對稱金鑰。</span><span class="sxs-lookup"><span data-stu-id="70c1c-109">Create the symmetric key at the Publisher.</span></span>  
  
2.  <span data-ttu-id="70c1c-110">使用對稱金鑰加密資料行資料。</span><span class="sxs-lookup"><span data-stu-id="70c1c-110">Encrypt column data with the symmetric key.</span></span>  
  
3.  <span data-ttu-id="70c1c-111">發行包含加密資料行的資料表。</span><span class="sxs-lookup"><span data-stu-id="70c1c-111">Publish the table with the encrypted column.</span></span>  
  
4.  <span data-ttu-id="70c1c-112">訂閱發行集。</span><span class="sxs-lookup"><span data-stu-id="70c1c-112">Subscribe to the publication.</span></span>  
  
5.  <span data-ttu-id="70c1c-113">初始化訂閱。</span><span class="sxs-lookup"><span data-stu-id="70c1c-113">Initialize the subscription.</span></span>  
  
6.  <span data-ttu-id="70c1c-114">使用與步驟 1 相同的 ALGORITHM、KEY_SOURCE 和 IDENTITY_VALUE 值，於訂閱者端重新建立對稱金鑰。</span><span class="sxs-lookup"><span data-stu-id="70c1c-114">Recreate the symmetric key at the Subscriber using same values for ALGORITHM, KEY_SOURCE, and IDENTITY_VALUE as in step 1.</span></span>  
  
7.  <span data-ttu-id="70c1c-115">存取加密的資料行資料。</span><span class="sxs-lookup"><span data-stu-id="70c1c-115">Access the encrypted column data.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="70c1c-116">您應該使用對稱金鑰來加密資料行資料。</span><span class="sxs-lookup"><span data-stu-id="70c1c-116">You should use a symmetric key to encrypt column data.</span></span> <span data-ttu-id="70c1c-117">在發行者端和訂閱者端可以用不同方式維護對稱金鑰本身的安全性。</span><span class="sxs-lookup"><span data-stu-id="70c1c-117">The symmetric key itself can be secured by different means at the Publisher and Subscriber.</span></span>  
  
### <a name="to-create-and-replicate-encrypted-column-data"></a><span data-ttu-id="70c1c-118">建立和複寫加密的資料行資料</span><span class="sxs-lookup"><span data-stu-id="70c1c-118">To create and replicate encrypted column data</span></span>  
  
1.  <span data-ttu-id="70c1c-119">於發行者端，執行 [CREATE SYMMETRIC KEY](/sql/t-sql/statements/create-symmetric-key-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="70c1c-119">At the Publisher, execute [CREATE SYMMETRIC KEY](/sql/t-sql/statements/create-symmetric-key-transact-sql).</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="70c1c-120">KEY_SOURCE 的值是重要的資料，可用於重新建立對稱金鑰和解密資料，</span><span class="sxs-lookup"><span data-stu-id="70c1c-120">The value of KEY_SOURCE is valuable data that can be used to re-create the symmetric key and decrypt data.</span></span> <span data-ttu-id="70c1c-121">所以務必安全地存放和傳輸 KEY_SOURCE。</span><span class="sxs-lookup"><span data-stu-id="70c1c-121">KEY_SOURCE must always be stored and transported securely.</span></span>  
  
2.  <span data-ttu-id="70c1c-122">執行 [OPEN SYMMETRIC KEY](/sql/t-sql/statements/open-symmetric-key-transact-sql) 開啟新的金鑰。</span><span class="sxs-lookup"><span data-stu-id="70c1c-122">Execute [OPEN SYMMETRIC KEY](/sql/t-sql/statements/open-symmetric-key-transact-sql) to open the new key.</span></span>  
  
3.  <span data-ttu-id="70c1c-123">使用 [EncryptByKey](/sql/t-sql/functions/encryptbykey-transact-sql) 函數於發行者端加密資料行資料。</span><span class="sxs-lookup"><span data-stu-id="70c1c-123">Use the [EncryptByKey](/sql/t-sql/functions/encryptbykey-transact-sql) function to encrypt column data at the Publisher.</span></span>  
  
4.  <span data-ttu-id="70c1c-124">執行 [CLOSE SYMMETRIC KEY](/sql/t-sql/statements/close-symmetric-key-transact-sql) 關閉金鑰。</span><span class="sxs-lookup"><span data-stu-id="70c1c-124">Execute [CLOSE SYMMETRIC KEY](/sql/t-sql/statements/close-symmetric-key-transact-sql) to close the key.</span></span>  
  
5.  <span data-ttu-id="70c1c-125">發行包含加密資料行的資料表。</span><span class="sxs-lookup"><span data-stu-id="70c1c-125">Publish the table that contains the encrypted column.</span></span> <span data-ttu-id="70c1c-126">如需詳細資訊，請參閱[建立發行集](../publish/create-a-publication.md)。</span><span class="sxs-lookup"><span data-stu-id="70c1c-126">For more information, see [Create a Publication](../publish/create-a-publication.md).</span></span>  
  
6.  <span data-ttu-id="70c1c-127">訂閱發行集。</span><span class="sxs-lookup"><span data-stu-id="70c1c-127">Subscribe to the publication.</span></span> <span data-ttu-id="70c1c-128">如需詳細資訊，請參閱[建立提取訂閱](../create-a-pull-subscription.md)或[建立發送訂閱](../create-a-push-subscription.md)。</span><span class="sxs-lookup"><span data-stu-id="70c1c-128">For more information, see [Create a Pull Subscription](../create-a-pull-subscription.md) or [Create a Push Subscription](../create-a-push-subscription.md).</span></span>  
  
7.  <span data-ttu-id="70c1c-129">初始化訂閱。</span><span class="sxs-lookup"><span data-stu-id="70c1c-129">Initialize the subscription.</span></span> <span data-ttu-id="70c1c-130">如需詳細資訊，請參閱 [建立和套用初始快照集](../create-and-apply-the-initial-snapshot.md)。</span><span class="sxs-lookup"><span data-stu-id="70c1c-130">For more information, see [Create and Apply the Initial Snapshot](../create-and-apply-the-initial-snapshot.md).</span></span>  
  
8.  <span data-ttu-id="70c1c-131">在訂閱者端，使用與步驟 1 相同的 ALGORITHM、KEY_SOURCE 和 IDENTITY_VALUE 值來執行 [CREATE SYMMETRIC KEY](/sql/t-sql/statements/create-symmetric-key-transact-sql) 。</span><span class="sxs-lookup"><span data-stu-id="70c1c-131">At the Subscriber, execute [CREATE SYMMETRIC KEY](/sql/t-sql/statements/create-symmetric-key-transact-sql) using the same values for ALGORITHM, KEY_SOURCE, and IDENTITY_VALUE as in step 1.</span></span> <span data-ttu-id="70c1c-132">您可以針對 ENCRYPTION BY 指定不同的值。</span><span class="sxs-lookup"><span data-stu-id="70c1c-132">You can specify a different value for ENCRYPTION BY.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="70c1c-133">KEY_SOURCE 的值是重要的資料，可用於重新建立對稱金鑰和解密資料，</span><span class="sxs-lookup"><span data-stu-id="70c1c-133">The value of KEY_SOURCE is valuable data that can be used to re-create the symmetric key and decrypt data.</span></span> <span data-ttu-id="70c1c-134">所以務必安全地存放和傳輸 KEY_SOURCE。</span><span class="sxs-lookup"><span data-stu-id="70c1c-134">KEY_SOURCE must always be stored and transported securely.</span></span>  
  
9. <span data-ttu-id="70c1c-135">執行 [OPEN SYMMETRIC KEY](/sql/t-sql/statements/open-symmetric-key-transact-sql) 開啟新的金鑰。</span><span class="sxs-lookup"><span data-stu-id="70c1c-135">Execute [OPEN SYMMETRIC KEY](/sql/t-sql/statements/open-symmetric-key-transact-sql) to open the new key.</span></span>  
  
10. <span data-ttu-id="70c1c-136">使用 [DecryptByKey](/sql/t-sql/functions/decryptbykey-transact-sql) 函數於訂閱者端解密複寫的資料。</span><span class="sxs-lookup"><span data-stu-id="70c1c-136">Use the [DecryptByKey](/sql/t-sql/functions/decryptbykey-transact-sql) function to decrypt replicated data at the Subscriber.</span></span>  
  
11. <span data-ttu-id="70c1c-137">執行 [CLOSE SYMMETRIC KEY](/sql/t-sql/statements/close-symmetric-key-transact-sql) 關閉金鑰。</span><span class="sxs-lookup"><span data-stu-id="70c1c-137">Execute [CLOSE SYMMETRIC KEY](/sql/t-sql/statements/close-symmetric-key-transact-sql) to close the key.</span></span>  
  
## <a name="example"></a><span data-ttu-id="70c1c-138">範例</span><span class="sxs-lookup"><span data-stu-id="70c1c-138">Example</span></span>  
 <span data-ttu-id="70c1c-139">此範例會建立對稱金鑰、用來協助維護對稱金鑰安全性的憑證和主要金鑰。</span><span class="sxs-lookup"><span data-stu-id="70c1c-139">This example creates a symmetric key, a certificate that is used to help secure the symmetric key, and a master key.</span></span> <span data-ttu-id="70c1c-140">這些金鑰建立在複寫資料庫中，</span><span class="sxs-lookup"><span data-stu-id="70c1c-140">These keys are created in the publication database.</span></span> <span data-ttu-id="70c1c-141">然後用來在 `SalesOrderHeader` 資料表中建立加密資料行 (EncryptedCreditCardApprovalCode)。</span><span class="sxs-lookup"><span data-stu-id="70c1c-141">They are then used to create an encrypted column (EncryptedCreditCardApprovalCode) in the `SalesOrderHeader` table.</span></span> <span data-ttu-id="70c1c-142">這個資料行會發行在 AdvWorksSalesOrdersMerge 發行集中，取代未加密的 CreditCardApprovalCode 資料行。</span><span class="sxs-lookup"><span data-stu-id="70c1c-142">This column is published in the AdvWorksSalesOrdersMerge publication instead of the unencrypted CreditCardApprovalCode column.</span></span> <span data-ttu-id="70c1c-143">可能的話，會在執行階段提示使用者輸入安全性認證。</span><span class="sxs-lookup"><span data-stu-id="70c1c-143">When possible, prompt users to enter security credentials at runtime.</span></span> <span data-ttu-id="70c1c-144">如果您必須將認證儲存在指令碼檔案中，則必須維護這個檔案的安全性，使他人無法在未獲授權的情況下擅自存取。</span><span class="sxs-lookup"><span data-stu-id="70c1c-144">If you must store credentials in a script file, you must secure the file to prevent unauthorized access.</span></span>  
  
 [!code-sql[HowTo#sp_PublishEncryptedColumn](../../../snippets/tsql/SQL15/replication/howto/tsql/publishencryptedcolumn.sql#sp_publishencryptedcolumn)]  
  
 [!code-sql[HowTo#sp_AddMergeArticle](../../../snippets/tsql/SQL15/replication/howto/tsql/createmergepub.sql#sp_addmergearticle)]  
  
## <a name="example"></a><span data-ttu-id="70c1c-145">範例</span><span class="sxs-lookup"><span data-stu-id="70c1c-145">Example</span></span>  
 <span data-ttu-id="70c1c-146">本範例會使用與第一個範例相同的 ALGORITHM、KEY_SOURCE 和 IDENTITY_VALUE 值，在訂閱資料庫中重新建立相同的對稱金鑰。</span><span class="sxs-lookup"><span data-stu-id="70c1c-146">This example recreates the same symmetric key in the subscription database using the same values for ALGORITHM, KEY_SOURCE, and IDENTITY_VALUE from the first example.</span></span> <span data-ttu-id="70c1c-147">本範例假設您已經初始化訂閱 AdvWorksSalesOrdersMerge 發行集，以複寫加密資料行。</span><span class="sxs-lookup"><span data-stu-id="70c1c-147">This example assumes that you have already initialized a subscription to the AdvWorksSalesOrdersMerge publication to replicate the encrypted column.</span></span> <span data-ttu-id="70c1c-148">可能的話，會在執行階段提示使用者輸入安全性認證。</span><span class="sxs-lookup"><span data-stu-id="70c1c-148">When possible, prompt users to enter security credentials at runtime.</span></span> <span data-ttu-id="70c1c-149">如果您必須將認證儲存在指令碼檔案中，則必須維護這個檔案在儲存和傳輸時的安全性，使他人無法在未獲授權的情況下擅自存取。</span><span class="sxs-lookup"><span data-stu-id="70c1c-149">If you must store credentials in a script file, you must secure the file during storage and transport to prevent unauthorized access.</span></span>  
  
 [!code-sql[HowTo#sp_SubscriberEncryptedColumn](../../../snippets/tsql/SQL15/replication/howto/tsql/subscriberencryptedcolumn.sql#sp_subscriberencryptedcolumn)]  
  
## <a name="see-also"></a><span data-ttu-id="70c1c-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="70c1c-150">See Also</span></span>  
 <span data-ttu-id="70c1c-151">[SQL Server 複寫安全性](view-and-modify-replication-security-settings.md) </span><span class="sxs-lookup"><span data-stu-id="70c1c-151">[SQL Server Replication Security](view-and-modify-replication-security-settings.md) </span></span>  
 [<span data-ttu-id="70c1c-152">在兩部伺服器上建立相同的對稱金鑰</span><span class="sxs-lookup"><span data-stu-id="70c1c-152">Create Identical Symmetric Keys on Two Servers</span></span>](../../security/encryption/create-identical-symmetric-keys-on-two-servers.md)  
  
  
