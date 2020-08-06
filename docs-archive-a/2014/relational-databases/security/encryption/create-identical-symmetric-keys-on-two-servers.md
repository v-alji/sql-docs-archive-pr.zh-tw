---
title: 在兩部伺服器上建立相同的對稱金鑰 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- symmetric keys [SQL Server], creating
ms.assetid: a13d0b21-a43b-43c0-9c22-7ba8f3d15e80
author: jaszymas
ms.author: jaszymas
ms.openlocfilehash: 38eaccffff89b0be7e59f628fcfb9b6e772a02b1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709078"
---
# <a name="create-identical-symmetric-keys-on-two-servers"></a><span data-ttu-id="43083-102">在兩部伺服器上建立相同的對稱金鑰</span><span class="sxs-lookup"><span data-stu-id="43083-102">Create Identical Symmetric Keys on Two Servers</span></span>
  <span data-ttu-id="43083-103">此主題描述如何使用 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] ，在 [!INCLUDE[tsql](../../../includes/tsql-md.md)]中於兩部不同的伺服器上建立相同的對稱金鑰</span><span class="sxs-lookup"><span data-stu-id="43083-103">This topic describes how to create identical symmetric keys on two different servers in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="43083-104">若要解密加密文字，您就需要用來加密的金鑰。</span><span class="sxs-lookup"><span data-stu-id="43083-104">In order to decrypt ciphertext, you need the key that was used to encrypt it.</span></span> <span data-ttu-id="43083-105">在單一資料庫中同時進行加密和解密時，此金鑰會儲存在資料庫中，然後根據權限提供金鑰，以便進行加密和解密。</span><span class="sxs-lookup"><span data-stu-id="43083-105">When both encryption and decryption occur in a single database, the key is stored in the database and it is available, depending on permissions, for both encryption and decryption.</span></span> <span data-ttu-id="43083-106">但是，在不同的資料庫或不同的伺服器上進行加密和解密時，儲存在某個資料庫中的金鑰將無法在第二個資料庫上使用。</span><span class="sxs-lookup"><span data-stu-id="43083-106">But when encryption and decryption occur in separate databases or on separate servers, the key stored in one database is not available for use on the second database</span></span>  
  
 <span data-ttu-id="43083-107">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="43083-107">**In This Topic**</span></span>  
  
-   <span data-ttu-id="43083-108">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="43083-108">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="43083-109">限制事項</span><span class="sxs-lookup"><span data-stu-id="43083-109">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="43083-110">安全性</span><span class="sxs-lookup"><span data-stu-id="43083-110">Security</span></span>](#Security)  
  
-   [<span data-ttu-id="43083-111">若要使用 Transact-SQL 在兩部不同的伺服器上建立相同的對稱金鑰</span><span class="sxs-lookup"><span data-stu-id="43083-111">To create identical symmetric keys on two different servers, using Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="43083-112">開始之前</span><span class="sxs-lookup"><span data-stu-id="43083-112">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="43083-113">限制事項</span><span class="sxs-lookup"><span data-stu-id="43083-113">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="43083-114">當建立對稱金鑰時，至少必須利用下列一項來加密對稱金鑰：憑證、密碼、對稱金鑰、非對稱金鑰或 PROVIDER。</span><span class="sxs-lookup"><span data-stu-id="43083-114">When a symmetric key is created, the symmetric key must be encrypted by using at least one of the following: certificate, password, symmetric key, asymmetric key, or PROVIDER.</span></span> <span data-ttu-id="43083-115">針對每一種類型，金鑰都可以有多個加密。</span><span class="sxs-lookup"><span data-stu-id="43083-115">The key can have more than one encryption of each type.</span></span> <span data-ttu-id="43083-116">換句話說，可以同時利用多個憑證、密碼、對稱金鑰及非對稱金鑰來加密單一對稱金鑰。</span><span class="sxs-lookup"><span data-stu-id="43083-116">In other words, a single symmetric key can be encrypted by using multiple certificates, passwords, symmetric keys, and asymmetric keys at the same time.</span></span>  
  
-   <span data-ttu-id="43083-117">如果是利用密碼 (而不是利用資料庫主要金鑰的公開金鑰) 來加密對稱金鑰，則會使用 TRIPLE DES 加密演算法。</span><span class="sxs-lookup"><span data-stu-id="43083-117">When a symmetric key is encrypted with a password instead of the public key of the database master key, the TRIPLE DES encryption algorithm is used.</span></span> <span data-ttu-id="43083-118">因此，利用強式加密演算法 (如 AES) 建立的金鑰，其本身的安全是由較弱的演算法來維護的。</span><span class="sxs-lookup"><span data-stu-id="43083-118">Because of this, keys that are created with a strong encryption algorithm, such as AES, are themselves secured by a weaker algorithm.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="43083-119">Security</span><span class="sxs-lookup"><span data-stu-id="43083-119">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="43083-120">權限</span><span class="sxs-lookup"><span data-stu-id="43083-120">Permissions</span></span>  
 <span data-ttu-id="43083-121">需要資料庫的 ALTER ANY SYMMETRIC KEY 權限。</span><span class="sxs-lookup"><span data-stu-id="43083-121">Requires ALTER ANY SYMMETRIC KEY permission on the database.</span></span> <span data-ttu-id="43083-122">如果指定了 AUTHORIZATION，則需要資料庫使用者的 IMPERSONATE 權限或應用程式角色的 ALTER 權限。</span><span class="sxs-lookup"><span data-stu-id="43083-122">If AUTHORIZATION is specified, requires IMPERSONATE permission on the database user or ALTER permission on the application role.</span></span> <span data-ttu-id="43083-123">如果是利用憑證或非對稱金鑰來加密，則需要憑證或非對稱金鑰的 VIEW DEFINITION 權限。</span><span class="sxs-lookup"><span data-stu-id="43083-123">If encryption is by certificate or asymmetric key, requires VIEW DEFINITION permission on the certificate or asymmetric key.</span></span> <span data-ttu-id="43083-124">只有 Windows 登入、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 登入，以及應用程式角色可以擁有對稱金鑰。</span><span class="sxs-lookup"><span data-stu-id="43083-124">Only Windows logins, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] logins, and application roles can own symmetric keys.</span></span> <span data-ttu-id="43083-125">群組和角色無法擁有對稱金鑰。</span><span class="sxs-lookup"><span data-stu-id="43083-125">Groups and roles cannot own symmetric keys.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="43083-126">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="43083-126">Using Transact-SQL</span></span>  
  
#### <a name="to-create-identical-symmetric-keys-on-two-different-servers"></a><span data-ttu-id="43083-127">若要在兩部不同的伺服器上建立相同的對稱金鑰</span><span class="sxs-lookup"><span data-stu-id="43083-127">To create identical symmetric keys on two different servers</span></span>  
  
1.  <span data-ttu-id="43083-128">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="43083-128">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="43083-129">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="43083-129">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="43083-130">執行下列 CREATE MASTER KEY、CREATE CERTIFICATE 和 CREATE SYMMETRIC KEY 陳述式，建立金鑰。</span><span class="sxs-lookup"><span data-stu-id="43083-130">Create a key by running the following CREATE MASTER KEY, CREATE CERTIFICATE, and CREATE SYMMETRIC KEY statements.</span></span>  
  
    ```  
    CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'My p@55w0Rd';  
    GO  
    CREATE CERTIFICATE [cert_keyProtection] WITH SUBJECT = 'Key Protection';  
    GO  
    CREATE SYMMETRIC KEY [key_DataShare] WITH  
        KEY_SOURCE = 'My key generation bits. This is a shared secret!',  
        ALGORITHM = AES_256,   
        IDENTITY_VALUE = 'Key Identity generation bits. Also a shared secret'  
        ENCRYPTION BY CERTIFICATE [cert_keyProtection];  
    GO  
    ```  
  
4.  <span data-ttu-id="43083-131">連接到另一個伺服器執行個體，開啟不同的查詢視窗，然後執行以上 SQL 陳述式，在第二部伺服器上建立相同的金鑰。</span><span class="sxs-lookup"><span data-stu-id="43083-131">Connect to a separate server instance, open a different Query Window, and run the SQL statements above to create the same key on the second server.</span></span>  
  
5.  <span data-ttu-id="43083-132">先在第一部伺服器上執行以下 OPEN SYMMETRIC KEY 陳述式和 SELECT 陳述式，藉以測試金鑰。</span><span class="sxs-lookup"><span data-stu-id="43083-132">Test the keys by first running the OPEN SYMMETRIC KEY statement and the SELECT statement below on the first server.</span></span>  
  
    ```  
    OPEN SYMMETRIC KEY [key_DataShare]   
        DECRYPTION BY CERTIFICATE cert_keyProtection;  
    GO  
    SELECT encryptbykey(key_guid('key_DataShare'), 'MyData' )  
    GO  
    -- For example, the output might look like this: 0x2152F8DA8A500A9EDC2FAE26D15C302DA70D25563DAE7D5D1102E3056CE9EF95CA3E7289F7F4D0523ED0376B155FE9C3  
    ```  
  
6.  <span data-ttu-id="43083-133">在第二部伺服器上，將之前 SELECT 陳述式的結果貼入下列程式碼，做為 `@blob` 的值，然後執行下列程式碼來確認重複金鑰可以解密加密文字。</span><span class="sxs-lookup"><span data-stu-id="43083-133">On the second server, paste the result of the previous SELECT statement into the following code as the value of `@blob` and run the following code to verify that the duplicate key can decrypt the ciphertext.</span></span>  
  
    ```  
    OPEN SYMMETRIC KEY [key_DataShare]   
        DECRYPTION BY CERTIFICATE cert_keyProtection;  
    GO  
    DECLARE @blob varbinary(8000);  
    SET @blob = SELECT CONVERT(varchar(8000), decryptbykey(@blob));  
    GO  
    ```  
  
7.  <span data-ttu-id="43083-134">關閉兩部伺服器上的對稱金鑰。</span><span class="sxs-lookup"><span data-stu-id="43083-134">Close the symmetric key on both servers.</span></span>  
  
    ```  
    CLOSE SYMMETRIC KEY [key_DataShare];  
    GO  
    ```  
  
 <span data-ttu-id="43083-135">如需詳細資訊，請參閱下列：</span><span class="sxs-lookup"><span data-stu-id="43083-135">For more information, see the following:</span></span>  
  
-   [<span data-ttu-id="43083-136">CREATE MASTER KEY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="43083-136">CREATE MASTER KEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-master-key-transact-sql)  
  
-   [<span data-ttu-id="43083-137">CREATE CERTIFICATE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="43083-137">CREATE CERTIFICATE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-certificate-transact-sql)  
  
-   [<span data-ttu-id="43083-138">CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="43083-138">CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-symmetric-key-transact-sql)  
  
-   [<span data-ttu-id="43083-139">ENCRYPTBYKEY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="43083-139">ENCRYPTBYKEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/encryptbykey-transact-sql)  
  
-   [<span data-ttu-id="43083-140">DECRYPTBYKEY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="43083-140">DECRYPTBYKEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/decryptbykey-transact-sql)  
  
-   [<span data-ttu-id="43083-141">OPEN SYMMETRIC KEY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="43083-141">OPEN SYMMETRIC KEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/open-symmetric-key-transact-sql)  
  
  
