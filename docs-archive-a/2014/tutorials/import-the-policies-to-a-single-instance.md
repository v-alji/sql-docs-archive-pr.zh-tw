---
title: 將原則匯入至單一實例 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
ms.assetid: bc5bcd87-663f-41d9-bb7b-b3e083cd63df
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 0464bc6f4dcd6326a4b8f222cb4b3128f21561ca
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707981"
---
# <a name="import-the-policies-to-a-single-instance"></a><span data-ttu-id="cd7f7-102">將原則匯入至單一執行個體</span><span class="sxs-lookup"><span data-stu-id="cd7f7-102">Import the Policies to a Single Instance</span></span>
  <span data-ttu-id="cd7f7-103">在這項工作中，您將會針對 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的單一執行個體，匯入您要排程到以原則為基礎之管理的最佳作法原則。</span><span class="sxs-lookup"><span data-stu-id="cd7f7-103">In this task, you will import the best practices policies that you want to schedule into Policy-Based Management on a single instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="cd7f7-104">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="cd7f7-104">Prerequisites</span></span>  
 <span data-ttu-id="cd7f7-105">您必須在執行 [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] 或更新版本的伺服器上執行此程序。</span><span class="sxs-lookup"><span data-stu-id="cd7f7-105">You must perform this procedure on a server that is running [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] or a later version.</span></span>  
  
### <a name="import-the-best-practices-policies-for-the-database-engine"></a><span data-ttu-id="cd7f7-106">匯入 Database Engine 的最佳做法原則</span><span class="sxs-lookup"><span data-stu-id="cd7f7-106">Import the best practices policies for the Database Engine</span></span>  
  
1.  <span data-ttu-id="cd7f7-107">啟動 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]，然後連接至 [!INCLUDE[ssDE](../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="cd7f7-107">Start [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], and then connect to the [!INCLUDE[ssDE](../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="cd7f7-108">在物件總管中，展開 [**管理**]，然後展開 [**原則管理**]。</span><span class="sxs-lookup"><span data-stu-id="cd7f7-108">In Object Explorer, expand **Management**, and then expand **Policy Management**.</span></span>  
  
3.  <span data-ttu-id="cd7f7-109">以滑鼠右鍵按一下 [**原則**]，然後按一下 [匯**入原則**]。</span><span class="sxs-lookup"><span data-stu-id="cd7f7-109">Right-click **Policies**, and then click **Import Policy**.</span></span>  
  
4.  <span data-ttu-id="cd7f7-110">在 [匯**入**] 對話方塊中，按一下 [**要匯入**的檔案] 方塊旁的省略號 (**...**) ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="cd7f7-110">In the **Import** dialog box, next to the **Files to import** box, click the ellipsis (**...**) button.</span></span>  
  
5.  <span data-ttu-id="cd7f7-111">在 [**查詢**] 清單中，流覽至包含最佳作法原則的下列資料夾：</span><span class="sxs-lookup"><span data-stu-id="cd7f7-111">In the **Look in** list, browse to the following folder, which contains the best practices policies:</span></span>  
  
     <span data-ttu-id="cd7f7-112">**C:\Program Files (x86)\Microsoft SQL Server\110\Tools\Policies\DatabaseEngine\1033**</span><span class="sxs-lookup"><span data-stu-id="cd7f7-112">**C:\Program Files (x86)\Microsoft SQL Server\110\Tools\Policies\DatabaseEngine\1033**</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="cd7f7-113">檔案路徑可能會隨著您安裝 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 程式檔案的位置、執行 32 位元或 64 位元作業系統，以及語言識別碼而有所不同。</span><span class="sxs-lookup"><span data-stu-id="cd7f7-113">The file path may vary, depending on where you installed the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] program files, whether you are running a 32-bit or 64-bit operating system, and the language identifier.</span></span>  
  
6.  <span data-ttu-id="cd7f7-114">在 [**選取原則**] 對話方塊中，選取一或多個原則檔。</span><span class="sxs-lookup"><span data-stu-id="cd7f7-114">In the **Select Policy** dialog box, select one or more policy files.</span></span>  
  
     <span data-ttu-id="cd7f7-115">若要選取非相鄰的檔案，按一下某個檔案、按住 CTRL 鍵，然後按一下其他各個檔案。</span><span class="sxs-lookup"><span data-stu-id="cd7f7-115">To select nonadjacent files, click one file, hold down the CTRL key, and then click each additional file.</span></span> <span data-ttu-id="cd7f7-116">若要選取相鄰的檔案，按一下順序中的第一個檔案、按住 SHIFT 鍵，然後按一下最後一個檔案。</span><span class="sxs-lookup"><span data-stu-id="cd7f7-116">To select adjacent files, click the first file in the sequence, hold down the SHIFT key, and then click the last file.</span></span>  
  
7.  <span data-ttu-id="cd7f7-117">當您完成選取檔案時，請按一下 [**開啟**]。</span><span class="sxs-lookup"><span data-stu-id="cd7f7-117">When you are finished selecting files, click **Open**.</span></span>  
  
8.  <span data-ttu-id="cd7f7-118">在 [匯**入**] 對話方塊中，確認 [**原則狀態**] 清單已設定為 [匯**入時保留原則狀態**] (預設) ，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="cd7f7-118">In the **Import** dialog box, make sure that the **Policy state** list is set to **Preserve policy state on import** (the default), and then click **OK**.</span></span>  
  
     <span data-ttu-id="cd7f7-119">這些原則會匯入至 [**原則管理**] 底下的 [**原則**] 節點。</span><span class="sxs-lookup"><span data-stu-id="cd7f7-119">The policies are imported into the **Policies** node under **Policy Management**.</span></span> <span data-ttu-id="cd7f7-120">根據預設，匯入的原則會設為「視需要」評估模式。</span><span class="sxs-lookup"><span data-stu-id="cd7f7-120">By default, the imported policies are set to "On demand" evaluation mode.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="cd7f7-121">後續步驟</span><span class="sxs-lookup"><span data-stu-id="cd7f7-121">Next Steps</span></span>  
 [<span data-ttu-id="cd7f7-122">排程原則</span><span class="sxs-lookup"><span data-stu-id="cd7f7-122">Schedule the Policies</span></span>](../../2014/tutorials/schedule-the-policies.md)  
  
  
