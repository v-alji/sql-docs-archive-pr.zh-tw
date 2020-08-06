---
title: 備份資料庫主要金鑰 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- database master key [SQL Server], exporting
ms.assetid: 7ad9a0a0-6e4f-4f7b-8801-8c1b9d49c4d8
author: jaszymas
ms.author: jaszymas
ms.openlocfilehash: 9a66d28fea8289719d3efb2351409e0f14379ec9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709086"
---
# <a name="back-up-a-database-master-key"></a><span data-ttu-id="d8085-102">備份資料庫主要金鑰</span><span class="sxs-lookup"><span data-stu-id="d8085-102">Back Up a Database Master Key</span></span>
  <span data-ttu-id="d8085-103">此主題描述如何使用 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] ，備份 [!INCLUDE[tsql](../../../includes/tsql-md.md)]中的資料庫主要金鑰。</span><span class="sxs-lookup"><span data-stu-id="d8085-103">This topic describes how to back up a database master key in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="d8085-104">資料庫主要金鑰可用來加密資料庫內部的其他金鑰和憑證。</span><span class="sxs-lookup"><span data-stu-id="d8085-104">The database master key is used to encrypt other keys and certificates inside a database.</span></span> <span data-ttu-id="d8085-105">如果遭到刪除或損毀， [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 可能就無法解密那些金鑰，而使用這些金鑰加密的資料實際上等於遺失了。</span><span class="sxs-lookup"><span data-stu-id="d8085-105">If it is deleted or corrupted, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] may be unable to decrypt those keys, and the data encrypted using them will be effectively lost.</span></span> <span data-ttu-id="d8085-106">因此，您應該備份資料庫主要金鑰，並將該備份存放在安全且位於異地的位置。</span><span class="sxs-lookup"><span data-stu-id="d8085-106">For this reason, you should back up the database master key and store the backup in a secure off-site location.</span></span>  
  
 <span data-ttu-id="d8085-107">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="d8085-107">**In This Topic**</span></span>  
  
-   <span data-ttu-id="d8085-108">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="d8085-108">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="d8085-109">限制事項</span><span class="sxs-lookup"><span data-stu-id="d8085-109">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="d8085-110">安全性</span><span class="sxs-lookup"><span data-stu-id="d8085-110">Security</span></span>](#Security)  
  
-   [<span data-ttu-id="d8085-111">若要使用 Transact-SQL 備份資料庫主要金鑰</span><span class="sxs-lookup"><span data-stu-id="d8085-111">To back up a database master key using Transact-SQL</span></span>](#Procedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="d8085-112">開始之前</span><span class="sxs-lookup"><span data-stu-id="d8085-112">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="d8085-113">限制事項</span><span class="sxs-lookup"><span data-stu-id="d8085-113">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="d8085-114">主要金鑰必須開啟，因此，將它備份之前必須先將它解密。</span><span class="sxs-lookup"><span data-stu-id="d8085-114">The master key must be open and, therefore, decrypted before it is backed up.</span></span> <span data-ttu-id="d8085-115">如果是利用服務主要金鑰來加密主要金鑰，則不必明確開啟主要金鑰。</span><span class="sxs-lookup"><span data-stu-id="d8085-115">If it is encrypted with the service master key, the master key does not have to be explicitly opened.</span></span> <span data-ttu-id="d8085-116">不過，如果只利用密碼加密主要金鑰，則必須明確開啟主要金鑰。</span><span class="sxs-lookup"><span data-stu-id="d8085-116">But if the master key is encrypted only with a password, it must be explicitly opened.</span></span>  
  
-   <span data-ttu-id="d8085-117">我們建議您在建立主要金鑰後立即將它備份，然後將該備份儲存在安全的離站位置。</span><span class="sxs-lookup"><span data-stu-id="d8085-117">We recommend that you back up the master key as soon as it is created, and store the backup in a secure, off-site location.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="d8085-118">Security</span><span class="sxs-lookup"><span data-stu-id="d8085-118">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="d8085-119">權限</span><span class="sxs-lookup"><span data-stu-id="d8085-119">Permissions</span></span>  
 <span data-ttu-id="d8085-120">需要資料庫的 CONTROL 權限。</span><span class="sxs-lookup"><span data-stu-id="d8085-120">Requires CONTROL permission on the database.</span></span>  
  
##  <a name="using-sql-server-management-studio-with-transact-sql"></a><a name="Procedure"></a><span data-ttu-id="d8085-121">搭配 Transact-sql 使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="d8085-121">Using SQL Server Management Studio with Transact-SQL</span></span>  
  
#### <a name="to-back-up-the-database-master-key"></a><span data-ttu-id="d8085-122">若要備份資料庫主要金鑰</span><span class="sxs-lookup"><span data-stu-id="d8085-122">To back-up the database master key</span></span>  
  
1.  <span data-ttu-id="d8085-123">在 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]中，連接到包含要備份之資料庫主要金鑰的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="d8085-123">In [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], connect to the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance containing the database master key you wish to back up.</span></span>  
  
2.  <span data-ttu-id="d8085-124">選擇要在備份媒體上用於加密資料庫主要金鑰的密碼。</span><span class="sxs-lookup"><span data-stu-id="d8085-124">Choose a password that will be used to encrypt the database master key on the backup medium.</span></span> <span data-ttu-id="d8085-125">這個密碼必須遵守複雜性檢查。</span><span class="sxs-lookup"><span data-stu-id="d8085-125">This password is subject to complexity checks.</span></span>  
  
3.  <span data-ttu-id="d8085-126">取得抽取式備份媒體以便儲存備份金鑰的副本。</span><span class="sxs-lookup"><span data-stu-id="d8085-126">Obtain a removable backup medium for storing a copy of the backed-up key.</span></span>  
  
4.  <span data-ttu-id="d8085-127">識別要在其中建立金鑰備份的 NTFS 目錄。</span><span class="sxs-lookup"><span data-stu-id="d8085-127">Identify an NTFS directory in which to create the backup of the key.</span></span> <span data-ttu-id="d8085-128">這是建立下個步驟指定之檔案所在的位置。</span><span class="sxs-lookup"><span data-stu-id="d8085-128">This is where you will create the file specified in the next step.</span></span> <span data-ttu-id="d8085-129">這個目錄應該使用具有高度限制性的存取控制清單 (ACL) 加以保護。</span><span class="sxs-lookup"><span data-stu-id="d8085-129">The directory should be protected with highly restrictive access control lists (ACLs).</span></span>  
  
5.  <span data-ttu-id="d8085-130">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="d8085-130">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
6.  <span data-ttu-id="d8085-131">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="d8085-131">On the Standard bar, click **New Query**.</span></span>  
  
7.  <span data-ttu-id="d8085-132">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="d8085-132">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- Creates a backup of the "AdventureWorks2012" master key. Because this master key is not encrypted by the service master key, a password must be specified when it is opened.  
    USE AdventureWorks2012;   
    GO  
    OPEN MASTER KEY DECRYPTION BY PASSWORD = 'sfj5300osdVdgwdfkli7';   
  
    BACKUP MASTER KEY TO FILE = 'c:\temp\exportedmasterkey'   
        ENCRYPTION BY PASSWORD = 'sd092735kjn$&adsg';   
    GO  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="d8085-133">金鑰的檔案路徑和金鑰的密碼 (如果有) 不同於上方指示。</span><span class="sxs-lookup"><span data-stu-id="d8085-133">The file path to the key and the key's password (if it exists) will be different than what is indicated above.</span></span> <span data-ttu-id="d8085-134">請確定兩者都是您伺服器和金鑰設定專用的。</span><span class="sxs-lookup"><span data-stu-id="d8085-134">Please make sure that both are specific to your server and key set-up.</span></span>  
  
8.  <span data-ttu-id="d8085-135">將檔案複製到備份媒體，並確認複製後的副本。</span><span class="sxs-lookup"><span data-stu-id="d8085-135">Copy the file to the backup medium and verify the copy.</span></span>  
  
9. <span data-ttu-id="d8085-136">將備份存放在安全且位於異地的位置。</span><span class="sxs-lookup"><span data-stu-id="d8085-136">Store the backup in a secure, off-site location.</span></span>  
  
 <span data-ttu-id="d8085-137">如需詳細資訊，請參閱 [OPEN MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/open-master-key-transact-sql) (開啟主要金鑰 (Transact-SQL)) 和 [BACKUP MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-master-key-transact-sql) (備份主要金鑰 (Transact-SQL))。</span><span class="sxs-lookup"><span data-stu-id="d8085-137">For more information, see [OPEN MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/open-master-key-transact-sql) and [BACKUP MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-master-key-transact-sql).</span></span>  
  
  
