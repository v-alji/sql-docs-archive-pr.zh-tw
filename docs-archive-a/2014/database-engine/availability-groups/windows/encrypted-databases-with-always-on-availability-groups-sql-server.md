---
title: 具有 AlwaysOn 可用性群組 (SQL Server) 的加密資料庫 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Transparent Data Encryption, AlwaysOn Availability Groups
- TDE, AlwaysOn Availability Groups
- Availability Groups [SQL Server], interoperability
ms.assetid: 09eb6ebc-3051-4fff-86a5-93524507b1fc
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 91e717a896634a7df5a96253c51207831f142cff
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592249"
---
# <a name="encrypted-databases-with-alwayson-availability-groups-sql-server"></a><span data-ttu-id="9fa57-102">加密的資料庫與 AlwaysOn 可用性群組 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="9fa57-102">Encrypted Databases with AlwaysOn Availability Groups (SQL Server)</span></span>
  <span data-ttu-id="9fa57-103">本主題包含在 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 中使用目前加密或最近解密之資料庫搭配 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="9fa57-103">This topic contains information about the using currently encrypted or recently decrypted databases with [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span>  
  
 <span data-ttu-id="9fa57-104">**本主題內容：**</span><span class="sxs-lookup"><span data-stu-id="9fa57-104">**In this Topic:**</span></span>  
  
-   [<span data-ttu-id="9fa57-105">限制事項</span><span class="sxs-lookup"><span data-stu-id="9fa57-105">Limitations and Restrictions</span></span>](#Restrictions)  
  
-   [<span data-ttu-id="9fa57-106">相關工作</span><span class="sxs-lookup"><span data-stu-id="9fa57-106">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="9fa57-107">限制事項</span><span class="sxs-lookup"><span data-stu-id="9fa57-107">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="9fa57-108">如果資料庫已加密，甚至包含資料庫加密金鑰 (DEK)，您就無法使用 [!INCLUDE[ssAoNewAgWiz](../../../includes/ssaonewagwiz-md.md)] 或 [!INCLUDE[ssAoAddDbWiz](../../../includes/ssaoadddbwiz-md.md)] ，將資料庫加入至可用性群組。</span><span class="sxs-lookup"><span data-stu-id="9fa57-108">If a database is encrypted or even contains a Database Encryption Key (DEK), you cannot use the [!INCLUDE[ssAoNewAgWiz](../../../includes/ssaonewagwiz-md.md)] or [!INCLUDE[ssAoAddDbWiz](../../../includes/ssaoadddbwiz-md.md)] to add the database to an availability group.</span></span> <span data-ttu-id="9fa57-109">即使加密的資料庫已經解密，其記錄備份可能包含加密資料。</span><span class="sxs-lookup"><span data-stu-id="9fa57-109">Even if an encrypted database has been decrypted, its log backups might contain encrypted data.</span></span> <span data-ttu-id="9fa57-110">在此情況中，資料庫的完整初始資料同步處理可能會失敗。</span><span class="sxs-lookup"><span data-stu-id="9fa57-110">In this case, full initial data synchronization could fail on the database.</span></span> <span data-ttu-id="9fa57-111">這是因為還原記錄作業可能需要資料庫加密金鑰 (DEK) 所使用的憑證，而該憑證可能無法使用。</span><span class="sxs-lookup"><span data-stu-id="9fa57-111">This is because the restore log operation might require the certificate that was used by the database encryption keys (DEKs), and that certificate might be unavailable.</span></span>  
  
     <span data-ttu-id="9fa57-112">若要讓解密的資料庫能夠透過精靈加入至可用性群組：</span><span class="sxs-lookup"><span data-stu-id="9fa57-112">To make a decrypted database eligible to add to an availability group using the wizard:</span></span>  
  
    1.  <span data-ttu-id="9fa57-113">建立主要資料庫的記錄備份。</span><span class="sxs-lookup"><span data-stu-id="9fa57-113">Create a log backup of the primary database.</span></span>  
  
    2.  <span data-ttu-id="9fa57-114">建立主要資料庫的完整資料庫備份。</span><span class="sxs-lookup"><span data-stu-id="9fa57-114">Create a full database backup of the primary database.</span></span>  
  
    3.  <span data-ttu-id="9fa57-115">在裝載次要複本的伺服器執行個體上還原資料庫備份。</span><span class="sxs-lookup"><span data-stu-id="9fa57-115">Restore the database backup on the server instance that hosts the secondary replica.</span></span>  
  
    4.  <span data-ttu-id="9fa57-116">從主要資料庫建立新的記錄備份。</span><span class="sxs-lookup"><span data-stu-id="9fa57-116">Create a new log backup from primary database.</span></span>  
  
    5.  <span data-ttu-id="9fa57-117">在次要資料庫上還原這個記錄備份。</span><span class="sxs-lookup"><span data-stu-id="9fa57-117">Restore this log backup on the secondary database.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="9fa57-118">相關工作</span><span class="sxs-lookup"><span data-stu-id="9fa57-118">Related Tasks</span></span>  
  
-   [<span data-ttu-id="9fa57-119">針對可用性群組手動準備次要資料庫 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="9fa57-119">Manually Prepare a Secondary Database for an Availability Group &#40;SQL Server&#41;</span></span>](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="9fa57-120">使用可用性群組精靈 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="9fa57-120">Use the Availability Group Wizard &#40;SQL Server Management Studio&#41;</span></span>](use-the-availability-group-wizard-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="9fa57-121">使用將資料庫加入至可用性群組精靈 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="9fa57-121">Use the Add Database to Availability Group Wizard &#40;SQL Server Management Studio&#41;</span></span>](availability-group-add-database-to-group-wizard.md)  
  
## <a name="see-also"></a><span data-ttu-id="9fa57-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9fa57-122">See Also</span></span>  
 <span data-ttu-id="9fa57-123">[AlwaysOn 可用性群組 &#40;SQL Server 的總覽&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="9fa57-123">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="9fa57-124">透明資料加密 &#40;TDE&#41;</span><span class="sxs-lookup"><span data-stu-id="9fa57-124">Transparent Data Encryption &#40;TDE&#41;</span></span>](../../../relational-databases/security/encryption/transparent-data-encryption.md)  
  
  
