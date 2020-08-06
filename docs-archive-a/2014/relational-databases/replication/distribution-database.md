---
title: 散發資料庫 | Microsoft Docs
ms.custom: ''
ms.date: 06/30/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.configuredistributionwizard.distributiondatabase.f1
ms.assetid: 5b42a083-7a11-41d8-9e3f-320c7c907237
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d98a80be52ae77cbdaf1581a5b3397f9d11af4fb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585868"
---
# <a name="distribution-database"></a><span data-ttu-id="2b52a-102">散發資料庫</span><span class="sxs-lookup"><span data-stu-id="2b52a-102">Distribution Database</span></span>
  <span data-ttu-id="2b52a-103">散發資料庫會儲存所有複寫類型的中繼資料和記錄資料，以及異動複寫的交易。</span><span class="sxs-lookup"><span data-stu-id="2b52a-103">The distribution database stores metadata and history data for all types of replication, and transactions for transactional replication.</span></span>  
  
 <span data-ttu-id="2b52a-104">在許多情況下，單一散發資料庫即已足夠。</span><span class="sxs-lookup"><span data-stu-id="2b52a-104">In many cases, a single distribution database is sufficient.</span></span> <span data-ttu-id="2b52a-105">不過，如果多個發行者使用單一散發者，請考慮為每個發行者建立一個散發資料庫。</span><span class="sxs-lookup"><span data-stu-id="2b52a-105">However, if multiple Publishers use a single Distributor, consider creating a distribution database for each Publisher.</span></span> <span data-ttu-id="2b52a-106">這樣可以確保流經每個散發資料庫的資料都不同。</span><span class="sxs-lookup"><span data-stu-id="2b52a-106">Doing so ensures that the data flowing through each distribution database is distinct.</span></span> <span data-ttu-id="2b52a-107">您可以為使用設定散發精靈的散發者指定一個散發資料庫。</span><span class="sxs-lookup"><span data-stu-id="2b52a-107">You can specify one distribution database for the Distributor using the Configure Distribution Wizard.</span></span> <span data-ttu-id="2b52a-108">如有需要，請在 **[散發者屬性]** 對話方塊中指定其他散發資料庫。</span><span class="sxs-lookup"><span data-stu-id="2b52a-108">If necessary, specify additional distribution databases in the **Distributor Properties** dialog box.</span></span>  
  
## <a name="options"></a><span data-ttu-id="2b52a-109">選項。</span><span class="sxs-lookup"><span data-stu-id="2b52a-109">Options</span></span>  
 <span data-ttu-id="2b52a-110">**散發資料庫名稱**</span><span class="sxs-lookup"><span data-stu-id="2b52a-110">**Distribution database name**</span></span>  
 <span data-ttu-id="2b52a-111">輸入散發資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="2b52a-111">Enter a name for the distribution database.</span></span> <span data-ttu-id="2b52a-112">散發資料庫的預設名稱為「distribution」。</span><span class="sxs-lookup"><span data-stu-id="2b52a-112">The default name for the distribution database is 'distribution'.</span></span> <span data-ttu-id="2b52a-113">如果您指定名稱，則名稱最多為 128 個字元、在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體中必須為唯一，且必須符合識別碼的規則。</span><span class="sxs-lookup"><span data-stu-id="2b52a-113">If you specify a name, the name can be a maximum of 128 characters, must be unique within an instance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], and must conform to the rules for identifiers.</span></span> <span data-ttu-id="2b52a-114">如需詳細資訊，請參閱＜ [Database Identifiers](../databases/database-identifiers.md)＞。</span><span class="sxs-lookup"><span data-stu-id="2b52a-114">For more information, see [Database Identifiers](../databases/database-identifiers.md).</span></span>  
  
 <span data-ttu-id="2b52a-115">**[散發資料庫檔案的資料夾]** 和 **[散發資料庫記錄檔的資料夾]**</span><span class="sxs-lookup"><span data-stu-id="2b52a-115">**Folder for the distribution database file** and **Folder for the distribution database log file**</span></span>  
 <span data-ttu-id="2b52a-116">輸入散發資料庫和記錄檔的路徑。</span><span class="sxs-lookup"><span data-stu-id="2b52a-116">Enter the path for the distribution database and log files.</span></span> <span data-ttu-id="2b52a-117">路徑必須參考對散發者而言是本機的磁碟機，而且以本機磁碟機代號開始，然後是冒號 (例如，C:)。</span><span class="sxs-lookup"><span data-stu-id="2b52a-117">Paths must refer to disks that are local to the Distributor and begin with a local drive letter and colon (for example, C:).</span></span> <span data-ttu-id="2b52a-118">對應的磁碟機代號和網路路徑無效。</span><span class="sxs-lookup"><span data-stu-id="2b52a-118">Mapped drive letters and network paths are not valid.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2b52a-119">您可以藉由將散發資料庫記錄放置在散發資料庫的個別磁碟機上，來減少寫入交易的時間和改進複寫的效能。</span><span class="sxs-lookup"><span data-stu-id="2b52a-119">You can decrease the time it takes to write transactions and improve the performance of replication by placing the distribution database log on a separate disk drive from the distribution database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b52a-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2b52a-120">See Also</span></span>  
 <span data-ttu-id="2b52a-121">[[設定散發]](configure-distribution.md) </span><span class="sxs-lookup"><span data-stu-id="2b52a-121">[Configure Distribution](configure-distribution.md) </span></span>  
 <span data-ttu-id="2b52a-122">[設定發行和散發](configure-publishing-and-distribution.md) </span><span class="sxs-lookup"><span data-stu-id="2b52a-122">[Configure Publishing and Distribution](configure-publishing-and-distribution.md) </span></span>  
 [<span data-ttu-id="2b52a-123">檢視及修改散發者和發行者屬性</span><span class="sxs-lookup"><span data-stu-id="2b52a-123">View and Modify Distributor and Publisher Properties</span></span>](view-and-modify-distributor-and-publisher-properties.md)  
  
  
