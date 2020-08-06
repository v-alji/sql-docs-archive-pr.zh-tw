---
title: 快照集資料夾 | Microsoft 文件
ms.custom: ''
ms.date: 06/30/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.replicationutilities.specifysnapshotfolder.f1
ms.assetid: 3eb1b73f-ddb3-4d09-be6e-811c414698e9
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 48b490c65662edf65018e98dd1bc3339f6aae6b6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606739"
---
# <a name="snapshot-folder"></a><span data-ttu-id="6bfaa-102">快照集資料夾</span><span class="sxs-lookup"><span data-stu-id="6bfaa-102">Snapshot Folder</span></span>
  <span data-ttu-id="6bfaa-103">**[快照集資料夾]** 頁面會出現在設定散發精靈和新增發行集精靈中。</span><span class="sxs-lookup"><span data-stu-id="6bfaa-103">The **Snapshot Folder** page appears in the Configure Distribution Wizard and in the New Publication Wizard.</span></span> <span data-ttu-id="6bfaa-104">您為快照集資料夾指定的位置會作為此精靈中已啟用之所有發行者的預設值 (稍後使用 **[散發者屬性]** 對話方塊啟用的發行者並不會套用此預設快照集資料夾)。</span><span class="sxs-lookup"><span data-stu-id="6bfaa-104">The location you specify for the snapshot folder will be used as the default for all Publishers enabled in this wizard (the default snapshot folder does not apply to Publishers that are later enabled using the **Distributor Properties** dialog box).</span></span> <span data-ttu-id="6bfaa-105">針對設定散發精靈或 **[散發者屬性]** 對話方塊之 **[發行者]** 頁面上的任何發行者，您可以覆寫此預設值。</span><span class="sxs-lookup"><span data-stu-id="6bfaa-105">You can override this default for any Publisher on the **Publishers** page of the Configure Distribution Wizard or the **Distributor Properties** dialog box.</span></span>  
  
 <span data-ttu-id="6bfaa-106">快照集資料夾只是指定為共用的目錄；讀取並寫入此資料夾的代理程式必須具有足夠的權限才能對其進行存取。</span><span class="sxs-lookup"><span data-stu-id="6bfaa-106">The snapshot folder is simply a directory that you have designated as a share; agents that read from and write to this folder must have sufficient permissions to access it.</span></span> <span data-ttu-id="6bfaa-107">如需適當地保護資料夾的詳細資訊，請參閱[保護快照集資料夾](security/secure-the-snapshot-folder.md)。</span><span class="sxs-lookup"><span data-stu-id="6bfaa-107">For more information about securing the folder appropriately, see [Secure the Snapshot Folder](security/secure-the-snapshot-folder.md).</span></span> <span data-ttu-id="6bfaa-108">在實作複寫之前，請先測試確認複寫代理程式能夠連接到快照集資料夾。</span><span class="sxs-lookup"><span data-stu-id="6bfaa-108">Prior to implementing replication, test that the replication agents will be able to connect to the snapshot folder.</span></span> <span data-ttu-id="6bfaa-109">在每個代理程式都會使用到的帳戶之下登入，然後嘗試存取快照集資料夾。</span><span class="sxs-lookup"><span data-stu-id="6bfaa-109">Log on under the account that will be used by each agent and then attempt to access the snapshot folder.</span></span>  
  
## <a name="options"></a><span data-ttu-id="6bfaa-110">選項</span><span class="sxs-lookup"><span data-stu-id="6bfaa-110">Options</span></span>  
 <span data-ttu-id="6bfaa-111">**快照集資料夾**</span><span class="sxs-lookup"><span data-stu-id="6bfaa-111">**Snapshot folder**</span></span>  
 <span data-ttu-id="6bfaa-112">輸入要在其中儲存快照集檔案之資料夾的路徑。</span><span class="sxs-lookup"><span data-stu-id="6bfaa-112">Enter the path for the folder where you want snapshot files stored.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="6bfaa-113">建議您使用網路共用作為快照集資料夾的位置。</span><span class="sxs-lookup"><span data-stu-id="6bfaa-113">recommends that you use a network share as a snapshot folder location.</span></span> <span data-ttu-id="6bfaa-114">其他電腦上的代理程式無法存取本機路徑 (以磁碟機代號開頭的路徑，例如 C:\\)。</span><span class="sxs-lookup"><span data-stu-id="6bfaa-114">Local paths (those starting with a drive letter, such as C:\\) are not accessible to agents on other computers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bfaa-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6bfaa-115">See Also</span></span>  
 <span data-ttu-id="6bfaa-116">[替代快照集資料夾位置](alternate-snapshot-folder-locations.md) </span><span class="sxs-lookup"><span data-stu-id="6bfaa-116">[Alternate Snapshot Folder Locations](alternate-snapshot-folder-locations.md) </span></span>  
 <span data-ttu-id="6bfaa-117">[[設定散發]](configure-distribution.md) </span><span class="sxs-lookup"><span data-stu-id="6bfaa-117">[Configure Distribution](configure-distribution.md) </span></span>  
 <span data-ttu-id="6bfaa-118">[設定發行和散發](configure-publishing-and-distribution.md) </span><span class="sxs-lookup"><span data-stu-id="6bfaa-118">[Configure Publishing and Distribution](configure-publishing-and-distribution.md) </span></span>  
 <span data-ttu-id="6bfaa-119">[檢視及修改散發者和發行者屬性](view-and-modify-distributor-and-publisher-properties.md) </span><span class="sxs-lookup"><span data-stu-id="6bfaa-119">[View and Modify Distributor and Publisher Properties](view-and-modify-distributor-and-publisher-properties.md) </span></span>  
 [<span data-ttu-id="6bfaa-120">使用快照集初始化訂閱</span><span class="sxs-lookup"><span data-stu-id="6bfaa-120">Initialize a Subscription with a Snapshot</span></span>](initialize-a-subscription-with-a-snapshot.md)  
  
  
