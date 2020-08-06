---
title: 連接到伺服器 (Oracle)，連接屬性 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.oracleconnection.connectionprops.f1
helpviewer_keywords:
- Connect to Server dialog box, replication
ms.assetid: 1bb7396f-cbb2-4f88-b82b-543287ed4172
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 4c76a3058283a098357701a44de48efff917acd7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585321"
---
# <a name="connect-to-server-oracle-connection-properties"></a><span data-ttu-id="f16e8-102">連接到伺服器 (Oracle)，連接屬性</span><span class="sxs-lookup"><span data-stu-id="f16e8-102">Connect to Server (Oracle), Connection Properties</span></span>
  <span data-ttu-id="f16e8-103">使用 **[連接到伺服器]** 對話方塊的 **[連接屬性]** 索引標籤，即可指定 **[閘道]** 或 **[完整]** 發行選項。</span><span class="sxs-lookup"><span data-stu-id="f16e8-103">Use the **Connection Properties** tab of the **Connect to Server** dialog box to specify a publishing option of **Gateway** or **Complete**.</span></span> <span data-ttu-id="f16e8-104">識別發行者之後，除非卸除並重新設定發行者，否則無法變更此選項。</span><span class="sxs-lookup"><span data-stu-id="f16e8-104">After a Publisher is identified, this option cannot be changed without dropping and reconfiguring the Publisher.</span></span> <span data-ttu-id="f16e8-105">如需詳細資訊，請參閱[設定 Oracle 發行者](non-sql/configure-an-oracle-publisher.md)。</span><span class="sxs-lookup"><span data-stu-id="f16e8-105">For more information, see [Configure an Oracle Publisher](non-sql/configure-an-oracle-publisher.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="f16e8-106">選項。</span><span class="sxs-lookup"><span data-stu-id="f16e8-106">Options</span></span>  
 <span data-ttu-id="f16e8-107">**發行者類型**</span><span class="sxs-lookup"><span data-stu-id="f16e8-107">**Publisher type**</span></span>  
 <span data-ttu-id="f16e8-108">選取 **[閘道]** 或 **[完整]** 。</span><span class="sxs-lookup"><span data-stu-id="f16e8-108">Select **Gateway** or **Complete**.</span></span> <span data-ttu-id="f16e8-109">**[完整]** 選項可以為 Oracle 發行提供具有完整支援功能的快照式和交易式發行集。</span><span class="sxs-lookup"><span data-stu-id="f16e8-109">The **Complete** option is designed to provide snapshot and transactional publications with the complete set of supported features for Oracle publishing.</span></span> <span data-ttu-id="f16e8-110">**[閘道]** 選項可以在複寫作為系統之間的閘道時，提供特定的設計最佳化以提升效能。</span><span class="sxs-lookup"><span data-stu-id="f16e8-110">The **Gateway** option provides specific design optimizations to improve performance for cases where replication serves as a gateway between systems.</span></span> <span data-ttu-id="f16e8-111">如果您計畫在多個交易式發行集內發行相同的資料表，就無法使用 **[閘道]** 選項。</span><span class="sxs-lookup"><span data-stu-id="f16e8-111">The **Gateway** option cannot be used if you plan to publish the same table in multiple transactional publications.</span></span> <span data-ttu-id="f16e8-112">如果您選取 **[閘道]** ，則資料表最多只能在一個交易式發行集裡出現，但可以在任意數目的快照式發行集裡出現。</span><span class="sxs-lookup"><span data-stu-id="f16e8-112">A table can appear in at most one transactional publication and any number of snapshot publications if you select **Gateway**.</span></span>  
  
 <span data-ttu-id="f16e8-113">**逾時**</span><span class="sxs-lookup"><span data-stu-id="f16e8-113">**Timeouts**</span></span>  
 <span data-ttu-id="f16e8-114">指定 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 散發者要嘗試連線 Oracle 發行者多久之後，才發生逾時錯誤。</span><span class="sxs-lookup"><span data-stu-id="f16e8-114">Specify how long the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributor should attempt to connect to the Oracle Publisher before a timeout error occurs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f16e8-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f16e8-115">See Also</span></span>  
 <span data-ttu-id="f16e8-116">[Oracle 發行相關術語字彙](non-sql/glossary-of-terms-for-oracle-publishing.md) </span><span class="sxs-lookup"><span data-stu-id="f16e8-116">[Glossary of Terms for Oracle Publishing](non-sql/glossary-of-terms-for-oracle-publishing.md) </span></span>  
 [<span data-ttu-id="f16e8-117">Oracle 發行者的效能微調</span><span class="sxs-lookup"><span data-stu-id="f16e8-117">Performance Tuning for Oracle Publishers</span></span>](non-sql/performance-tuning-for-oracle-publishers.md)  
  
  
