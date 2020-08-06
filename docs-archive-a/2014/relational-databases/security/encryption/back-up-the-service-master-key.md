---
title: 備份服務主要金鑰 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- service master key [SQL Server], exporting
ms.assetid: f60b917c-6408-48be-b911-f93b05796904
author: jaszymas
ms.author: jaszymas
ms.openlocfilehash: b79212040df67c22ae7e34cd380a1a1f1bd10773
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709081"
---
# <a name="back-up-the-service-master-key"></a><span data-ttu-id="924a5-102">備份服務主要金鑰</span><span class="sxs-lookup"><span data-stu-id="924a5-102">Back Up the Service Master Key</span></span>
  <span data-ttu-id="924a5-103">此主題描述如何使用 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] ，備份 [!INCLUDE[tsql](../../../includes/tsql-md.md)]中的服務主要金鑰。</span><span class="sxs-lookup"><span data-stu-id="924a5-103">This topic describes how to back-up the Service Master key in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="924a5-104">服務主要金鑰是加密階層的根。</span><span class="sxs-lookup"><span data-stu-id="924a5-104">The service master key is the root of the encryption hierarchy.</span></span> <span data-ttu-id="924a5-105">應該將服務主要金鑰備份並儲存在安全且位於異地的位置。</span><span class="sxs-lookup"><span data-stu-id="924a5-105">It should be backed up and stored in a secure, off-site location.</span></span> <span data-ttu-id="924a5-106">建立這個備份，應該是必須在伺服器上執行的首要管理動作之一。</span><span class="sxs-lookup"><span data-stu-id="924a5-106">Creating this backup should be one of the first administrative actions performed on the server.</span></span>  
  
 <span data-ttu-id="924a5-107">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="924a5-107">**In This Topic**</span></span>  
  
-   <span data-ttu-id="924a5-108">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="924a5-108">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="924a5-109">限制事項</span><span class="sxs-lookup"><span data-stu-id="924a5-109">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="924a5-110">安全性</span><span class="sxs-lookup"><span data-stu-id="924a5-110">Security</span></span>](#Security)  
  
-   [<span data-ttu-id="924a5-111">若要備份服務主要金鑰</span><span class="sxs-lookup"><span data-stu-id="924a5-111">To back-up the Service Master key</span></span>](#Procedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="924a5-112">開始之前</span><span class="sxs-lookup"><span data-stu-id="924a5-112">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="924a5-113">限制事項</span><span class="sxs-lookup"><span data-stu-id="924a5-113">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="924a5-114">主要金鑰必須開啟，因此，將它備份之前必須先將它解密。</span><span class="sxs-lookup"><span data-stu-id="924a5-114">The master key must be open and, therefore, decrypted before it is backed up.</span></span> <span data-ttu-id="924a5-115">如果是利用服務主要金鑰來加密主要金鑰，則不必明確開啟主要金鑰；如果只利用密碼加密主要金鑰，則必須明確開啟主要金鑰。</span><span class="sxs-lookup"><span data-stu-id="924a5-115">If it is encrypted with the service master key, the master key does not have to be explicitly opened; however, if the master key is encrypted only with a password, it must be explicitly opened.</span></span>  
  
-   <span data-ttu-id="924a5-116">我們建議您在建立主要金鑰後立即將它備份，然後將該備份儲存在安全的離站位置。</span><span class="sxs-lookup"><span data-stu-id="924a5-116">We recommend that you back up the master key as soon as it is created, and store the backup in a secure, off-site location.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="924a5-117">Security</span><span class="sxs-lookup"><span data-stu-id="924a5-117">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="924a5-118">權限</span><span class="sxs-lookup"><span data-stu-id="924a5-118">Permissions</span></span>  
 <span data-ttu-id="924a5-119">需要資料庫的 CONTROL 權限。</span><span class="sxs-lookup"><span data-stu-id="924a5-119">Requires CONTROL permission on the database.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="Procedure"></a> <span data-ttu-id="924a5-120">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="924a5-120">Using Transact-SQL</span></span>  
  
#### <a name="to-back-up-the-service-master-key"></a><span data-ttu-id="924a5-121">若要備份服務主要金鑰</span><span class="sxs-lookup"><span data-stu-id="924a5-121">To back-up the Service Master key</span></span>  
  
1.  <span data-ttu-id="924a5-122">在 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]中，連接到含有您要備份的服務主要金鑰的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="924a5-122">In [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], connect to the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance containing the service master key you wish to back up.</span></span>  
  
2.  <span data-ttu-id="924a5-123">選擇要在備份媒體上用於加密服務主要金鑰的密碼。</span><span class="sxs-lookup"><span data-stu-id="924a5-123">Choose a password that will be used to encrypt the service master key on the backup medium.</span></span> <span data-ttu-id="924a5-124">這個密碼必須遵守複雜性檢查。</span><span class="sxs-lookup"><span data-stu-id="924a5-124">This password is subject to complexity checks.</span></span> <span data-ttu-id="924a5-125">如需詳細資訊，請參閱＜ [Password Policy](../password-policy.md)＞。</span><span class="sxs-lookup"><span data-stu-id="924a5-125">For more information, see [Password Policy](../password-policy.md).</span></span>  
  
3.  <span data-ttu-id="924a5-126">取得抽取式備份媒體以便儲存備份金鑰的副本。</span><span class="sxs-lookup"><span data-stu-id="924a5-126">Obtain a removable backup medium for storing a copy of the backed-up key.</span></span>  
  
4.  <span data-ttu-id="924a5-127">識別要在其中建立金鑰備份的 NTFS 目錄。</span><span class="sxs-lookup"><span data-stu-id="924a5-127">Identify an NTFS directory in which to create the backup of the key.</span></span> <span data-ttu-id="924a5-128">這是建立下個步驟指定之檔案所在的位置。</span><span class="sxs-lookup"><span data-stu-id="924a5-128">This is where you will create the file specified in the next step.</span></span> <span data-ttu-id="924a5-129">這個目錄應該使用具有高度限制性的存取控制清單 (ACL) 加以保護。</span><span class="sxs-lookup"><span data-stu-id="924a5-129">The directory should be protected with highly restrictive access control lists (ACLs).</span></span>  
  
5.  <span data-ttu-id="924a5-130">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="924a5-130">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
6.  <span data-ttu-id="924a5-131">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="924a5-131">On the Standard bar, click **New Query**.</span></span>  
  
7.  <span data-ttu-id="924a5-132">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="924a5-132">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- Creates a backup of the "AdventureWorks2012" master key.  
    -- Because this master key is not encrypted by the service master key, a password must be specified when it is opened.  
    USE AdventureWorks2012;  
    GO  
    BACKUP SERVICE MASTER KEY TO FILE = 'c:\temp_backups\keys\service_master_ key'   
        ENCRYPTION BY PASSWORD = '3dH85Hhk003GHk2597gheij4';  
    GO  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="924a5-133">金鑰的檔案路徑和金鑰的密碼 (如果有) 不同於上方指示。</span><span class="sxs-lookup"><span data-stu-id="924a5-133">The file path to the key and the key's password (if it exists) will be different than what is indicated above.</span></span> <span data-ttu-id="924a5-134">請確定兩者都是您伺服器和金鑰設定專用的。</span><span class="sxs-lookup"><span data-stu-id="924a5-134">Make sure that both are specific to your server and key set-up.</span></span>  
  
8.  <span data-ttu-id="924a5-135">將檔案複製到備份媒體，並確認複製後的副本。</span><span class="sxs-lookup"><span data-stu-id="924a5-135">Copy the file to the backup medium and verify the copy.</span></span>  
  
9. <span data-ttu-id="924a5-136">將備份存放在安全且位於異地的位置。</span><span class="sxs-lookup"><span data-stu-id="924a5-136">Store the backup in a secure, off-site location.</span></span>  
  
 <span data-ttu-id="924a5-137">如需詳細資訊，請參閱 [OPEN MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/open-master-key-transact-sql) (開啟主要金鑰 (Transact-SQL)) 和 [BACKUP MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-master-key-transact-sql) (備份主要金鑰 (Transact-SQL))。</span><span class="sxs-lookup"><span data-stu-id="924a5-137">For more information, see [OPEN MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/open-master-key-transact-sql) and [BACKUP MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-master-key-transact-sql).</span></span>  
  
  
