---
title: 加密資料行 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- encryption [SQL Server], columns
- cryptography [SQL Server], columns
ms.assetid: 38e9bf58-10c6-46ed-83cb-e2d76cda0adc
author: jaszymas
ms.author: jaszymas
ms.openlocfilehash: 00f8b06296b3407ac070cd40378f3ff1039a0b93
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709065"
---
# <a name="encrypt-a-column-of-data"></a><span data-ttu-id="0bc31-102">加密資料行</span><span class="sxs-lookup"><span data-stu-id="0bc31-102">Encrypt a Column of Data</span></span>
  <span data-ttu-id="0bc31-103">此主題描述如何使用 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] ，在 [!INCLUDE[tsql](../../../includes/tsql-md.md)]中透過對稱加密來加密資料行。</span><span class="sxs-lookup"><span data-stu-id="0bc31-103">This topic describes how to encrypt a column of data by using symmetric encryption in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] using [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="0bc31-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="0bc31-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="0bc31-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="0bc31-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="0bc31-106">安全性</span><span class="sxs-lookup"><span data-stu-id="0bc31-106">Security</span></span>](#Security)  
  
-   [<span data-ttu-id="0bc31-107">若要使用 Transact-SQL 來加密資料行</span><span class="sxs-lookup"><span data-stu-id="0bc31-107">To encrypt a column of data, using Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="0bc31-108">開始之前</span><span class="sxs-lookup"><span data-stu-id="0bc31-108">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="0bc31-109">Security</span><span class="sxs-lookup"><span data-stu-id="0bc31-109">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="0bc31-110">權限</span><span class="sxs-lookup"><span data-stu-id="0bc31-110">Permissions</span></span>  
 <span data-ttu-id="0bc31-111">需要下列權限，才能執行以下步驟：</span><span class="sxs-lookup"><span data-stu-id="0bc31-111">The following permissions are necessary to perform the steps below:</span></span>  
  
-   <span data-ttu-id="0bc31-112">資料庫的 CONTROL 權限。</span><span class="sxs-lookup"><span data-stu-id="0bc31-112">CONTROL permission on the database.</span></span>  
  
-   <span data-ttu-id="0bc31-113">資料庫的 CREATE CERTIFICATE 權限。</span><span class="sxs-lookup"><span data-stu-id="0bc31-113">CREATE CERTIFICATE permission on the database.</span></span> <span data-ttu-id="0bc31-114">只有 Windows 登入、SQL Server 登入，以及應用程式角色可以擁有憑證。</span><span class="sxs-lookup"><span data-stu-id="0bc31-114">Only Windows logins, SQL Server logins, and application roles can own certificates.</span></span> <span data-ttu-id="0bc31-115">群組和角色無法擁有憑證。</span><span class="sxs-lookup"><span data-stu-id="0bc31-115">Groups and roles cannot own certificates.</span></span>  
  
-   <span data-ttu-id="0bc31-116">資料表的 ALTER 權限。</span><span class="sxs-lookup"><span data-stu-id="0bc31-116">ALTER permission on the table.</span></span>  
  
-   <span data-ttu-id="0bc31-117">金鑰的某種權限，而且絕不能被拒絕 VIEW DEFINITION 權限。</span><span class="sxs-lookup"><span data-stu-id="0bc31-117">Some permission on the key and must not have been denied VIEW DEFINITION permission.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="0bc31-118">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="0bc31-118">Using Transact-SQL</span></span>  
  
#### <a name="to-encrypt-a-column-of-data-using-a-simple-symmetric-encryption"></a><span data-ttu-id="0bc31-119">若要使用簡單的對稱加密來加密資料行</span><span class="sxs-lookup"><span data-stu-id="0bc31-119">To encrypt a column of data using a simple symmetric encryption</span></span>  
  
1.  <span data-ttu-id="0bc31-120">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="0bc31-120">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="0bc31-121">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="0bc31-121">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="0bc31-122">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="0bc31-122">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    --If there is no master key, create one now.   
    IF NOT EXISTS   
        (SELECT * FROM sys.symmetric_keys WHERE symmetric_key_id = 101)  
        CREATE MASTER KEY ENCRYPTION BY   
        PASSWORD = '23987hxJKL95QYV4369#ghf0%lekjg5k3fd117r$$#1946kcj$n44ncjhdlj'  
    GO  
  
    CREATE CERTIFICATE Sales09  
       WITH SUBJECT = 'Customer Credit Card Numbers';  
    GO  
  
    CREATE SYMMETRIC KEY CreditCards_Key11  
        WITH ALGORITHM = AES_256  
        ENCRYPTION BY CERTIFICATE Sales09;  
    GO  
  
    -- Create a column in which to store the encrypted data.  
    ALTER TABLE Sales.CreditCard   
        ADD CardNumber_Encrypted varbinary(128);   
    GO  
  
    -- Open the symmetric key with which to encrypt the data.  
    OPEN SYMMETRIC KEY CreditCards_Key11  
       DECRYPTION BY CERTIFICATE Sales09;  
  
    -- Encrypt the value in column CardNumber using the  
    -- symmetric key CreditCards_Key11.  
    -- Save the result in column CardNumber_Encrypted.    
    UPDATE Sales.CreditCard  
    SET CardNumber_Encrypted = EncryptByKey(Key_GUID('CreditCards_Key11')  
        , CardNumber, 1, HashBytes('SHA1', CONVERT( varbinary  
        , CreditCardID)));  
    GO  
  
    -- Verify the encryption.  
    -- First, open the symmetric key with which to decrypt the data.  
  
    OPEN SYMMETRIC KEY CreditCards_Key11  
       DECRYPTION BY CERTIFICATE Sales09;  
    GO  
  
    -- Now list the original card number, the encrypted card number,  
    -- and the decrypted ciphertext. If the decryption worked,  
    -- the original number will match the decrypted number.  
  
    SELECT CardNumber, CardNumber_Encrypted   
        AS 'Encrypted card number', CONVERT(nvarchar,  
        DecryptByKey(CardNumber_Encrypted, 1 ,   
        HashBytes('SHA1', CONVERT(varbinary, CreditCardID))))  
        AS 'Decrypted card number' FROM Sales.CreditCard;  
    GO  
    ```  
  
#### <a name="to-encrypt-a-column-of-data-using-symmetric-encryption-that-includes-an-authenticator"></a><span data-ttu-id="0bc31-123">若要使用包含驗證器的對稱加密來加密資料行</span><span class="sxs-lookup"><span data-stu-id="0bc31-123">To encrypt a column of data using symmetric encryption that includes an authenticator</span></span>  
  
1.  <span data-ttu-id="0bc31-124">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="0bc31-124">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="0bc31-125">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="0bc31-125">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="0bc31-126">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="0bc31-126">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
  
    --If there is no master key, create one now.   
    IF NOT EXISTS   
        (SELECT * FROM sys.symmetric_keys WHERE symmetric_key_id = 101)  
        CREATE MASTER KEY ENCRYPTION BY   
        PASSWORD = '23987hxJKL969#ghf0%94467GRkjg5k3fd117r$$#1946kcj$n44nhdlj'  
    GO  
  
    CREATE CERTIFICATE HumanResources037  
       WITH SUBJECT = 'Employee Social Security Numbers';  
    GO  
  
    CREATE SYMMETRIC KEY SSN_Key_01  
        WITH ALGORITHM = AES_256  
        ENCRYPTION BY CERTIFICATE HumanResources037;  
    GO  
  
    USE [AdventureWorks2012];  
    GO  
  
    -- Create a column in which to store the encrypted data.  
    ALTER TABLE HumanResources.Employee  
        ADD EncryptedNationalIDNumber varbinary(128);   
    GO  
  
    -- Open the symmetric key with which to encrypt the data.  
    OPEN SYMMETRIC KEY SSN_Key_01  
       DECRYPTION BY CERTIFICATE HumanResources037;  
  
    -- Encrypt the value in column NationalIDNumber with symmetric   
    -- key SSN_Key_01. Save the result in column EncryptedNationalIDNumber.  
    UPDATE HumanResources.Employee  
    SET EncryptedNationalIDNumber = EncryptByKey(Key_GUID('SSN_Key_01'), NationalIDNumber);  
    GO  
  
    -- Verify the encryption.  
    -- First, open the symmetric key with which to decrypt the data.  
    OPEN SYMMETRIC KEY SSN_Key_01  
       DECRYPTION BY CERTIFICATE HumanResources037;  
    GO  
  
    -- Now list the original ID, the encrypted ID, and the   
    -- decrypted ciphertext. If the decryption worked, the original  
    -- and the decrypted ID will match.  
    SELECT NationalIDNumber, EncryptedNationalIDNumber   
        AS 'Encrypted ID Number',  
        CONVERT(nvarchar, DecryptByKey(EncryptedNationalIDNumber))   
        AS 'Decrypted ID Number'  
        FROM HumanResources.Employee;  
    GO  
    ```  
  
 <span data-ttu-id="0bc31-127">如需詳細資訊，請參閱下列：</span><span class="sxs-lookup"><span data-stu-id="0bc31-127">For more information, see the following:</span></span>  
  
-   [<span data-ttu-id="0bc31-128">CREATE CERTIFICATE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="0bc31-128">CREATE CERTIFICATE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-certificate-transact-sql)  
  
-   [<span data-ttu-id="0bc31-129">CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="0bc31-129">CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-symmetric-key-transact-sql)  
  
-   [<span data-ttu-id="0bc31-130">ALTER TABLE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="0bc31-130">ALTER TABLE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-table-transact-sql)  
  
-   [<span data-ttu-id="0bc31-131">OPEN SYMMETRIC KEY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="0bc31-131">OPEN SYMMETRIC KEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/open-symmetric-key-transact-sql)  
  
  
