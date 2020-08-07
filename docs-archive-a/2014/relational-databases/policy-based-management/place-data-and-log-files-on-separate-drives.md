---
title: 將資料檔和記錄檔放在不同的磁碟機上 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 6cbedc27-4d77-44ad-bed2-c23b628475a7
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d3f972ea29322a046c09657e2ed2499655c82aed
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597770"
---
# <a name="place-data-and-log-files-on-separate-drives"></a><span data-ttu-id="c2591-102">將資料檔和記錄檔放在不同的磁碟機上</span><span class="sxs-lookup"><span data-stu-id="c2591-102">Place Data and Log Files on Separate Drives</span></span>
  <span data-ttu-id="c2591-103">此規則會檢查資料檔和記錄檔是否放在不同的邏輯磁碟機上。</span><span class="sxs-lookup"><span data-stu-id="c2591-103">This rule checks whether data and log files are placed on separate logical drives.</span></span> <span data-ttu-id="c2591-104">將資料檔和記錄檔放在相同的裝置上可能會造成該裝置的競爭情況，並產生效能不佳的情況。</span><span class="sxs-lookup"><span data-stu-id="c2591-104">Placing both data and log files on the same device can cause contention for that device and result in poor performance.</span></span> <span data-ttu-id="c2591-105">將這些檔案放在不同的磁碟機上可允許同時針對資料檔和記錄檔發生 I/O 活動。</span><span class="sxs-lookup"><span data-stu-id="c2591-105">Placing the files on separate drives allows the I/O activity to occur at the same time for both the data and log files.</span></span>  
  
## <a name="best-practices-recommendations"></a><span data-ttu-id="c2591-106">最佳做法建議</span><span class="sxs-lookup"><span data-stu-id="c2591-106">Best Practices Recommendations</span></span>  
 <span data-ttu-id="c2591-107">當您建立新的資料庫時，請針對資料和記錄指定個別的磁碟機。</span><span class="sxs-lookup"><span data-stu-id="c2591-107">When you create a new database, specify separate drives for the data and log.</span></span> <span data-ttu-id="c2591-108">若要在建立資料庫之後移動檔案，必須讓該資料庫離線。</span><span class="sxs-lookup"><span data-stu-id="c2591-108">To move files after the database is created, the database must be taken offline.</span></span> <span data-ttu-id="c2591-109">請使用下列其中一種方法來移動檔案：</span><span class="sxs-lookup"><span data-stu-id="c2591-109">Move the files by using one of the following methods:</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c2591-110">這個原則無法透過掛接點偵測個別的實體裝置</span><span class="sxs-lookup"><span data-stu-id="c2591-110">This policy cannot detect separate physical devices through mount points</span></span>  
  
-   <span data-ttu-id="c2591-111">使用具有 WITH MOVE 選項的 RESTORE DATABASE 陳述式從備份還原資料庫。</span><span class="sxs-lookup"><span data-stu-id="c2591-111">Restore the database from backup by using the RESTORE DATABASE statement with the WITH MOVE option.</span></span>  
  
-   <span data-ttu-id="c2591-112">卸離然後附加資料庫，為資料和記錄裝置指定不同的位置。</span><span class="sxs-lookup"><span data-stu-id="c2591-112">Detach and then attach the database specifying separate locations for the data and log devices.</span></span>  
  
-   <span data-ttu-id="c2591-113">執行具有 MODIFY FILE 選項的 ALTER DATABASE 陳述式然後重新啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體，以指定新的位置。</span><span class="sxs-lookup"><span data-stu-id="c2591-113">Specify a new location by running the ALTER DATABASE statement with the MODIFY FILE option, and then restarting the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="for-more-information"></a><span data-ttu-id="c2591-114">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="c2591-114">For More Information</span></span>  
 [<span data-ttu-id="c2591-115">移動資料庫檔案</span><span class="sxs-lookup"><span data-stu-id="c2591-115">Move Database Files</span></span>](../databases/move-database-files.md)  
  
 [<span data-ttu-id="c2591-116">移動使用者資料庫</span><span class="sxs-lookup"><span data-stu-id="c2591-116">Move User Databases</span></span>](../databases/move-user-databases.md)  
  
 [<span data-ttu-id="c2591-117">資料庫卸離與附加 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="c2591-117">Database Detach and Attach &#40;SQL Server&#41;</span></span>](../databases/database-detach-and-attach-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="c2591-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c2591-118">See Also</span></span>  
 [<span data-ttu-id="c2591-119">使用原則式管理來監視和強制最佳做法</span><span class="sxs-lookup"><span data-stu-id="c2591-119">Monitor and Enforce Best Practices by Using Policy-Based Management</span></span>](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
