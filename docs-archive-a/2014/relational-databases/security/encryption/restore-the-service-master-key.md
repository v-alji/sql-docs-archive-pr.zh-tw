---
title: 還原服務主要金鑰 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- service master key [SQL Server], importing
- service master key [SQL Server], restoring
ms.assetid: 14bdbbbe-d384-4692-b670-4243d2466fe1
author: jaszymas
ms.author: jaszymas
ms.openlocfilehash: 2ad99fc9baa518d50678ddd6e6db1ec554658823
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710526"
---
# <a name="restore-the-service-master-key"></a><span data-ttu-id="63532-102">還原服務主要金鑰</span><span class="sxs-lookup"><span data-stu-id="63532-102">Restore the Service Master Key</span></span>
  <span data-ttu-id="63532-103">此主題描述如何使用 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] ，還原 [!INCLUDE[tsql](../../../includes/tsql-md.md)]中的服務主要金鑰。</span><span class="sxs-lookup"><span data-stu-id="63532-103">This topic describes how to restore the service master key in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="63532-104">需要還原服務主要金鑰的情況不太可能發生在您身上。</span><span class="sxs-lookup"><span data-stu-id="63532-104">It is unlikely that you will ever need to restore the service master key.</span></span> <span data-ttu-id="63532-105">萬一真的碰到了，就應該非常小心地進行。</span><span class="sxs-lookup"><span data-stu-id="63532-105">If you do, you should proceed with extreme caution.</span></span> <span data-ttu-id="63532-106">如需詳細資訊，請參閱 [Back Up the Service Master Key](service-master-key.md)。</span><span class="sxs-lookup"><span data-stu-id="63532-106">For more information, see [Back Up the Service Master Key](service-master-key.md).</span></span>  
  
 <span data-ttu-id="63532-107">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="63532-107">**In This Topic**</span></span>  
  
-   <span data-ttu-id="63532-108">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="63532-108">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="63532-109">限制事項</span><span class="sxs-lookup"><span data-stu-id="63532-109">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="63532-110">安全性</span><span class="sxs-lookup"><span data-stu-id="63532-110">Security</span></span>](#Security)  
  
-   [<span data-ttu-id="63532-111">若要使用 Transact-SQL 還原服務主要金鑰</span><span class="sxs-lookup"><span data-stu-id="63532-111">To restore the service master key using Transact-SQL</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="63532-112">開始之前</span><span class="sxs-lookup"><span data-stu-id="63532-112">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="63532-113">限制事項</span><span class="sxs-lookup"><span data-stu-id="63532-113">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="63532-114">當還原服務主要金鑰時， [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 會解密所有已利用目前的服務主要金鑰來加密的金鑰和秘密，然後利用從備份檔案載入的服務主要金鑰來加密它們。</span><span class="sxs-lookup"><span data-stu-id="63532-114">When the service master key is restored, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] decrypts all the keys and secrets that have been encrypted with the current service master key, and then encrypts them with the service master key loaded from the backup file.</span></span>  
  
-   <span data-ttu-id="63532-115">如果任何一項解密失敗，還原便會失敗。</span><span class="sxs-lookup"><span data-stu-id="63532-115">If any one of the decryptions fails, the restore will fail.</span></span> <span data-ttu-id="63532-116">您可以利用 FORCE 選項來省略錯誤，但這個選項會使所有無法解密的資料遺失。</span><span class="sxs-lookup"><span data-stu-id="63532-116">You can use the FORCE option to ignore errors, but this option will cause the loss of any data that cannot be decrypted.</span></span>  
  
-   <span data-ttu-id="63532-117">重新產生加密階層是一項需要大量資源的作業。</span><span class="sxs-lookup"><span data-stu-id="63532-117">Regenerating the encryption hierarchy is a resource-intensive operation.</span></span> <span data-ttu-id="63532-118">您應該將這項作業安排在低需求時進行。</span><span class="sxs-lookup"><span data-stu-id="63532-118">You should schedule this during a period of low demand.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="63532-119">服務主要金鑰是 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 加密階層的根。</span><span class="sxs-lookup"><span data-stu-id="63532-119">The service master key is the root of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] encryption hierarchy.</span></span> <span data-ttu-id="63532-120">服務主要金鑰會直接或間接維護樹狀結構中之所有其他金鑰的安全。</span><span class="sxs-lookup"><span data-stu-id="63532-120">The service master key directly or indirectly secures all other keys in the tree.</span></span> <span data-ttu-id="63532-121">如果在強制還原作業進行期間某相依金鑰無法解密，由該金鑰維護其安全的資料便會遺失。</span><span class="sxs-lookup"><span data-stu-id="63532-121">If a dependent key cannot be decrypted during a forced restore, data that is secured by that key will be lost.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="63532-122">Security</span><span class="sxs-lookup"><span data-stu-id="63532-122">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="63532-123">權限</span><span class="sxs-lookup"><span data-stu-id="63532-123">Permissions</span></span>  
 <span data-ttu-id="63532-124">需要伺服器的 CONTROL SERVER 權限。</span><span class="sxs-lookup"><span data-stu-id="63532-124">Requires CONTROL SERVER permission on the server.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="SSMSProcedure"></a> <span data-ttu-id="63532-125">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="63532-125">Using Transact-SQL</span></span>  
  
#### <a name="to-restore-the-service-master-key"></a><span data-ttu-id="63532-126">若要還原服務主要金鑰</span><span class="sxs-lookup"><span data-stu-id="63532-126">To restore the service master key</span></span>  
  
1.  <span data-ttu-id="63532-127">從實體備份媒體或本機檔案系統上的目錄，擷取已備份的服務主要金鑰副本。</span><span class="sxs-lookup"><span data-stu-id="63532-127">Retrieve a copy of the backed-up service master key, either from a physical backup medium or a directory on the local file system.</span></span>  
  
2.  <span data-ttu-id="63532-128">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="63532-128">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
3.  <span data-ttu-id="63532-129">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="63532-129">On the Standard bar, click **New Query**.</span></span>  
  
4.  <span data-ttu-id="63532-130">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="63532-130">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- Restores the service master key from a backup file.  
    RESTORE SERVICE MASTER KEY   
        FROM FILE = 'c:\temp_backups\keys\service_master_key'   
        DECRYPTION BY PASSWORD = '3dH85Hhk003GHk2597gheij4';  
    GO  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="63532-131">金鑰的檔案路徑和金鑰的密碼 (如果有) 不同於上方指示。</span><span class="sxs-lookup"><span data-stu-id="63532-131">The file path to the key and the key's password (if it exists) will be different than what is indicated above.</span></span> <span data-ttu-id="63532-132">請確定兩者都是您伺服器和金鑰設定專用的。</span><span class="sxs-lookup"><span data-stu-id="63532-132">Please make sure that both are specific to your server and key set-up.</span></span>  
  
  
