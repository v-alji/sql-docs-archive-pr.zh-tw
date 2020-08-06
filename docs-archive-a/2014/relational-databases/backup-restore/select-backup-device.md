---
title: 選取備份裝置 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql12.swb.selectbackupdevice.f1
ms.assetid: 7887c9fd-15ce-4cc8-b069-845c1d09088c
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8a848f9188eec0ebb09931bca460b0389b9570ff
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705189"
---
# <a name="select-backup-device"></a><span data-ttu-id="02c9b-102">選取備份裝置</span><span class="sxs-lookup"><span data-stu-id="02c9b-102">Select Backup Device</span></span>
  <span data-ttu-id="02c9b-103">使用 **[選取備份裝置]** 對話方塊，可選取還原作業的邏輯備份裝置。</span><span class="sxs-lookup"><span data-stu-id="02c9b-103">Use the **Select Backup Device** dialog box to select a logical backup device for the restore operation.</span></span>  
  
 <span data-ttu-id="02c9b-104">邏輯備份裝置是使用者自訂的邏輯裝置，會對應至作業系統所提供的實體裝置 (磁帶機或磁碟機)。</span><span class="sxs-lookup"><span data-stu-id="02c9b-104">A logical backup device is a user-defined logical device that corresponds to a physical device, either a tape drive or a disk drive, that is provided by the operating system.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="02c9b-105">如果備份使用到多個備份裝置，則所有的備份裝置都必須對應至單一類型的裝置。</span><span class="sxs-lookup"><span data-stu-id="02c9b-105">If a backup uses multiple backup devices, they all must correspond to a single type of device.</span></span>  
  
 <span data-ttu-id="02c9b-106">**若要使用 SQL Server Management Studio 檢視備份裝置的內容**</span><span class="sxs-lookup"><span data-stu-id="02c9b-106">**To use SQL Server Management Studio to view the contents of a backup device**</span></span>  
  
-   [<span data-ttu-id="02c9b-107">檢視備份磁帶或檔案的內容 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="02c9b-107">View the Contents of a Backup Tape or File &#40;SQL Server&#41;</span></span>](view-the-contents-of-a-backup-tape-or-file-sql-server.md)  
  
-   [<span data-ttu-id="02c9b-108">檢視邏輯備份裝置的屬性和內容 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="02c9b-108">View the Properties and Contents of a Logical Backup Device &#40;SQL Server&#41;</span></span>](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)  
  
## <a name="options"></a><span data-ttu-id="02c9b-109">選項。</span><span class="sxs-lookup"><span data-stu-id="02c9b-109">Options</span></span>  
 <span data-ttu-id="02c9b-110">**備份裝置**</span><span class="sxs-lookup"><span data-stu-id="02c9b-110">**Backup device**</span></span>  
 <span data-ttu-id="02c9b-111">在清單方塊中，選取您要從中還原之邏輯備份裝置的名稱。</span><span class="sxs-lookup"><span data-stu-id="02c9b-111">In the list box, select the name of a logical backup device from which you want to restore.</span></span>  
  
 <span data-ttu-id="02c9b-112">如需如何檢視備份裝置內容的相關資訊，請參閱 [檢視邏輯備份裝置的屬性和內容 &#40;SQL Server&#41;](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="02c9b-112">For information about how to view the contents of a backup device, see [View the Properties and Contents of a Logical Backup Device &#40;SQL Server&#41;](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="02c9b-113">備註</span><span class="sxs-lookup"><span data-stu-id="02c9b-113">Remarks</span></span>  
 <span data-ttu-id="02c9b-114">如果您在清單中沒有看到包含您要搜尋之備份的邏輯備份裝置，則可能是已將備份直接寫入至一個或多個檔案或磁帶機。</span><span class="sxs-lookup"><span data-stu-id="02c9b-114">If you do not see a logical backup device that contains the backup you are seeking on the list, the backup might have been written directly to one or more files or tape drives.</span></span> <span data-ttu-id="02c9b-115">如果是這種情況，請取消 **[選取備份裝置]** 對話方塊，並且在 **[指定備份]** 對話方塊的 **[備份媒體]** 清單方塊中選取 **[檔案]** 或 **[磁帶]** 。</span><span class="sxs-lookup"><span data-stu-id="02c9b-115">If this is the case, cancel the **Select Backup Device** dialog box; and in the **Specify Backup** dialog box, select **File** or **Tape** in the **Backup media** list box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02c9b-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="02c9b-116">See Also</span></span>  
 [<span data-ttu-id="02c9b-117">備份裝置 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="02c9b-117">Backup Devices &#40;SQL Server&#41;</span></span>](backup-devices-sql-server.md)  
  
  
