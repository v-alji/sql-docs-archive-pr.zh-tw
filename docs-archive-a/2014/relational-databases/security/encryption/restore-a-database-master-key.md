---
title: 還原資料庫主要金鑰 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- database master key [SQL Server], importing
ms.assetid: 16897cc5-db8f-43bb-a38e-6855c82647cf
author: jaszymas
ms.author: jaszymas
ms.openlocfilehash: 614ba8bdc494ae7e7e5b3ed7b62390721ef642a3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710525"
---
# <a name="restore-a-database-master-key"></a><span data-ttu-id="94353-102">還原資料庫主要金鑰</span><span class="sxs-lookup"><span data-stu-id="94353-102">Restore a Database Master Key</span></span>
  <span data-ttu-id="94353-103">此主題描述如何使用 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] ，還原 [!INCLUDE[tsql](../../../includes/tsql-md.md)]中的資料庫主要金鑰。</span><span class="sxs-lookup"><span data-stu-id="94353-103">This topic describes how to restore the database master key in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="94353-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="94353-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="94353-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="94353-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="94353-106">限制事項</span><span class="sxs-lookup"><span data-stu-id="94353-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="94353-107">安全性</span><span class="sxs-lookup"><span data-stu-id="94353-107">Security</span></span>](#Security)  
  
-   [<span data-ttu-id="94353-108">若要使用 Transact-SQL 還原資料庫主要金鑰</span><span class="sxs-lookup"><span data-stu-id="94353-108">To restore the database master key using Transact-SQL</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="94353-109">開始之前</span><span class="sxs-lookup"><span data-stu-id="94353-109">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="94353-110">限制事項</span><span class="sxs-lookup"><span data-stu-id="94353-110">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="94353-111">當主要金鑰還原時， [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 會解密所有利用目前作用中主要金鑰加密的金鑰，然後利用還原的主要金鑰加密這些金鑰。</span><span class="sxs-lookup"><span data-stu-id="94353-111">When the master key is restored, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] decrypts all the keys that are encrypted with the currently active master key, and then encrypts these keys with the restored master key.</span></span> <span data-ttu-id="94353-112">這項需要大量資源的作業應該安排在低需求時進行。</span><span class="sxs-lookup"><span data-stu-id="94353-112">This resource-intensive operation should be scheduled during a period of low demand.</span></span> <span data-ttu-id="94353-113">如果目前資料庫主要金鑰未開啟或無法開啟，或者，如果利用該金鑰加密的任何金鑰無法解密，還原作業便會失敗。</span><span class="sxs-lookup"><span data-stu-id="94353-113">If the current database master key is not open or cannot be opened, or if any of the keys that are encrypted by it cannot be decrypted, the restore operation fails.</span></span>  
  
-   <span data-ttu-id="94353-114">如果任何一項解密失敗，還原便會失敗。</span><span class="sxs-lookup"><span data-stu-id="94353-114">If any one of the decryptions fails, the restore will fail.</span></span> <span data-ttu-id="94353-115">您可以利用 FORCE 選項來省略錯誤，但這個選項會使所有無法解密的資料遺失。</span><span class="sxs-lookup"><span data-stu-id="94353-115">You can use the FORCE option to ignore errors, but this option will cause the loss of any data that cannot be decrypted.</span></span>  
  
-   <span data-ttu-id="94353-116">如果先前是由服務主要金鑰加密主要金鑰，則還原的主要金鑰也會由服務主要金鑰來加密。</span><span class="sxs-lookup"><span data-stu-id="94353-116">If the master key was encrypted by the service master key, the restored master key will also be encrypted by the service master key.</span></span>  
  
-   <span data-ttu-id="94353-117">如果目前資料庫中沒有主要金鑰，RESTORE MASTER KEY 會建立主要金鑰。</span><span class="sxs-lookup"><span data-stu-id="94353-117">If there is no master key in the current database, RESTORE MASTER KEY creates a master key.</span></span> <span data-ttu-id="94353-118">不會自動利用服務主要金鑰來加密新的主要金鑰。</span><span class="sxs-lookup"><span data-stu-id="94353-118">The new master key will not be automatically encrypted with the service master key.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="94353-119">Security</span><span class="sxs-lookup"><span data-stu-id="94353-119">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="94353-120">權限</span><span class="sxs-lookup"><span data-stu-id="94353-120">Permissions</span></span>  
 <span data-ttu-id="94353-121">需要資料庫的 CONTROL 權限。</span><span class="sxs-lookup"><span data-stu-id="94353-121">Requires CONTROL permission on the database.</span></span>  
  
##  <a name="using-sql-server-management-studio-with-transact-sql"></a><a name="SSMSProcedure"></a><span data-ttu-id="94353-122">搭配 Transact-sql 使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="94353-122">Using SQL Server Management Studio with Transact-SQL</span></span>  
  
#### <a name="to-restore-the-database-master-key"></a><span data-ttu-id="94353-123">若要還原資料庫主要金鑰</span><span class="sxs-lookup"><span data-stu-id="94353-123">To restore the database master key</span></span>  
  
1.  <span data-ttu-id="94353-124">從實體備份媒體或本機檔案系統上的目錄，擷取已備份的資料庫主要金鑰副本。</span><span class="sxs-lookup"><span data-stu-id="94353-124">Retrieve a copy of the backed-up database master key, either from a physical backup medium or a directory on the local file system.</span></span>  
  
2.  <span data-ttu-id="94353-125">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="94353-125">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
3.  <span data-ttu-id="94353-126">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="94353-126">On the Standard bar, click **New Query**.</span></span>  
  
4.  <span data-ttu-id="94353-127">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="94353-127">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- Restores the database master key of the AdventureWorks2012 database.  
    USE AdventureWorks2012;  
    GO  
    RESTORE MASTER KEY   
        FROM FILE = 'c:\backups\keys\AdventureWorks2012_master_key'   
        DECRYPTION BY PASSWORD = '3dH85Hhk003#GHkf02597gheij04'   
        ENCRYPTION BY PASSWORD = '259087M#MyjkFkjhywiyedfgGDFD';  
    GO  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="94353-128">金鑰的檔案路徑和金鑰的密碼 (如果有) 不同於上方指示。</span><span class="sxs-lookup"><span data-stu-id="94353-128">The file path to the key and the key's password (if it exists) will be different than what is indicated above.</span></span> <span data-ttu-id="94353-129">請確定兩者都是您伺服器和金鑰設定專用的。</span><span class="sxs-lookup"><span data-stu-id="94353-129">Please make sure that both are specific to your server and key set-up.</span></span>  
  
 <span data-ttu-id="94353-130">如需詳細資訊，請參閱 [RESTORE MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-master-key-transact-sql)</span><span class="sxs-lookup"><span data-stu-id="94353-130">For more information, see [RESTORE MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-master-key-transact-sql)</span></span>  
  
  
