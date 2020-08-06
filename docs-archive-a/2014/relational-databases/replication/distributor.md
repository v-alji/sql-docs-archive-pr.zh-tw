---
title: 散發者 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.replicationutilities.selectdistributor.f1
ms.assetid: 787f0e9c-09dd-438a-bc04-5b8f99c127b8
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c601a540088b5cd9d7a2033510a5cf9b83c3170e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585856"
---
# <a name="distributor"></a><span data-ttu-id="5bda1-102">散發者</span><span class="sxs-lookup"><span data-stu-id="5bda1-102">Distributor</span></span>
  <span data-ttu-id="5bda1-103">**[散發者]** 頁面會出現在設定散發精靈和新增發行集精靈中。</span><span class="sxs-lookup"><span data-stu-id="5bda1-103">The **Distributor** page appears in the Configure Distribution Wizard and in the New Publication Wizard.</span></span> <span data-ttu-id="5bda1-104">散發者是包含散發資料庫的伺服器，而且會儲存所有類型之複寫的中繼資料和記錄資料。</span><span class="sxs-lookup"><span data-stu-id="5bda1-104">The Distributor is a server that contains the distribution database and stores metadata and history data for all types of replication.</span></span> <span data-ttu-id="5bda1-105">散發者也會儲存異動複寫的交易。</span><span class="sxs-lookup"><span data-stu-id="5bda1-105">The Distributor also stores transactions for transactional replication.</span></span> <span data-ttu-id="5bda1-106">散發者可以是與發行者相同的伺服器 (本機散發者)，也可以是與發行者不同的伺服器 (遠端散發者)。</span><span class="sxs-lookup"><span data-stu-id="5bda1-106">The Distributor can be the same server as the Publisher (a local Distributor) or it can be a separate server from the Publisher (a remote Distributor).</span></span> <span data-ttu-id="5bda1-107">散發者的角色會視您實作的複寫類型而定。</span><span class="sxs-lookup"><span data-stu-id="5bda1-107">The role of the Distributor varies, depending on which type of replication you implement.</span></span> <span data-ttu-id="5bda1-108">一般而言，它的角色用於異動複寫的機會，遠大於合併式複寫和快照式複寫。</span><span class="sxs-lookup"><span data-stu-id="5bda1-108">In general, its role is much greater for transactional replication than it is for merge replication and snapshot replication.</span></span> <span data-ttu-id="5bda1-109">合併式複寫和快照式複寫通常使用本機散發者，但在非常忙碌的電腦上進行異動複寫時，可以使用遠端散發者提高效益。</span><span class="sxs-lookup"><span data-stu-id="5bda1-109">Merge and snapshot replication typically use a local Distributor, but transactional replication on a very busy system can benefit from using a remote Distributor.</span></span>  
  
 <span data-ttu-id="5bda1-110">散發者會使用所在伺服器的下列額外資源：</span><span class="sxs-lookup"><span data-stu-id="5bda1-110">The Distributor uses these additional resources on the server where it is located:</span></span>  
  
-   <span data-ttu-id="5bda1-111">如果發行集的快照集檔案儲存於散發者時 (通常是如此)，則會使用額外的磁碟空間。</span><span class="sxs-lookup"><span data-stu-id="5bda1-111">Additional disk space if the snapshot files for the publication are stored on it (which they typically are).</span></span>  
  
-   <span data-ttu-id="5bda1-112">儲存散發資料庫的額外空間。</span><span class="sxs-lookup"><span data-stu-id="5bda1-112">Additional disk space to store the distribution database.</span></span>  
  
-   <span data-ttu-id="5bda1-113">針對在散發者上執行的發送訂閱，複寫代理程式會使用額外處理器資源。</span><span class="sxs-lookup"><span data-stu-id="5bda1-113">Additional processor usage by replication agents for push subscriptions running on the Distributor.</span></span>  
  
 <span data-ttu-id="5bda1-114">您選擇作為散發者的伺服器，應該具備足夠的磁碟空間及處理器動力，以便支援該伺服器的複寫及所有其他活動。</span><span class="sxs-lookup"><span data-stu-id="5bda1-114">The server you select as the Distributor should have adequate disk space and processor power to support replication and any other activities on that server.</span></span>  
  
## <a name="options"></a><span data-ttu-id="5bda1-115">選項。</span><span class="sxs-lookup"><span data-stu-id="5bda1-115">Options</span></span>  
 <span data-ttu-id="5bda1-116">**'\<ServerName>' 將扮演本身的散發者；SQL Server 將建立散發資料庫和記錄**</span><span class="sxs-lookup"><span data-stu-id="5bda1-116">**'\<ServerName>' will act as its own Distributor; SQL Server will create a distribution database and log**</span></span>  
 <span data-ttu-id="5bda1-117">選取此選項即可將您連接的伺服器設定為散發者。</span><span class="sxs-lookup"><span data-stu-id="5bda1-117">Select this option to configure the server you are connected to as a Distributor.</span></span>  
  
 <span data-ttu-id="5bda1-118">**使用下列伺服器做為散發者 (注意：您選取的伺服器必須已經設定為散發者)**</span><span class="sxs-lookup"><span data-stu-id="5bda1-118">**Use the following server as the Distributor (Note: the server you select must already be configured as a Distributor)**</span></span>  
 <span data-ttu-id="5bda1-119">選取此選項，然後按一下下面的伺服器名稱，即可將其他伺服器設定為散發者。</span><span class="sxs-lookup"><span data-stu-id="5bda1-119">Select this option and then click on the name of a server below to configure another server as the Distributor.</span></span>  
  
 <span data-ttu-id="5bda1-120">**加入**</span><span class="sxs-lookup"><span data-stu-id="5bda1-120">**Add**</span></span>  
 <span data-ttu-id="5bda1-121">如果沒有列出您要用來作為散發者的伺服器，請按一下 **[加入]** ，以識別該伺服器並將其加入清單。</span><span class="sxs-lookup"><span data-stu-id="5bda1-121">If the server you want to use as a Distributor is not listed, click **Add** to identify the server and add it to the list.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5bda1-122">若要使用遠端伺服器作為散發者，該遠端伺服器必須已經設定為散發者。</span><span class="sxs-lookup"><span data-stu-id="5bda1-122">To use a remote server as the Distributor, the remote server must already be configured as a Distributor.</span></span> <span data-ttu-id="5bda1-123">執行此精靈的伺服器，在該發行者上必須啟用為散發者。</span><span class="sxs-lookup"><span data-stu-id="5bda1-123">The server against which this wizard is running must be enabled as a Publisher on that Distributor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5bda1-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5bda1-124">See Also</span></span>  
 <span data-ttu-id="5bda1-125">[[設定散發]](configure-distribution.md) </span><span class="sxs-lookup"><span data-stu-id="5bda1-125">[Configure Distribution](configure-distribution.md) </span></span>  
 [<span data-ttu-id="5bda1-126">設定發行和散發</span><span class="sxs-lookup"><span data-stu-id="5bda1-126">Configure Publishing and Distribution</span></span>](configure-publishing-and-distribution.md)  
  
  
