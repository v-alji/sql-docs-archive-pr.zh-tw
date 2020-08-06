---
title: 啟用記憶體選項中的鎖定頁面 (Windows) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- Lock Pages in Memory option
ms.assetid: cd581fbc-4747-439e-87f9-2f18e39c5bb9
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 13290940c3a94a7ba79582d892a5e28670f24b29
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596275"
---
# <a name="enable-the-lock-pages-in-memory-option-windows"></a><span data-ttu-id="7960b-102">啟用鎖定記憶體分頁選項 (Windows)</span><span class="sxs-lookup"><span data-stu-id="7960b-102">Enable the Lock Pages in Memory Option (Windows)</span></span>
  <span data-ttu-id="7960b-103">此 Windows 原則決定哪些帳戶可以使用處理序將資料保留在實體記憶體中，以防止系統將資料傳送到磁碟上的虛擬記憶體。</span><span class="sxs-lookup"><span data-stu-id="7960b-103">This Windows policy determines which accounts can use a process to keep data in physical memory, preventing the system from paging the data to virtual memory on disk.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7960b-104">在預期到磁碟的分頁記憶體時，在記憶體中鎖定分頁可能會提升效能。</span><span class="sxs-lookup"><span data-stu-id="7960b-104">Locking pages in memory may boost performance when paging memory to disk is expected.</span></span>  
  
 <span data-ttu-id="7960b-105">請使用 Windows 群組原則工具 (gpedit.msc)，以針對 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]所使用的帳戶啟用這個原則。</span><span class="sxs-lookup"><span data-stu-id="7960b-105">Use the Windows Group Policy tool (gpedit.msc) to enable this policy for the account used by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="7960b-106">您必須是系統管理員，才可變更這個原則。</span><span class="sxs-lookup"><span data-stu-id="7960b-106">You must be a system administrator to change this policy.</span></span>  
  
### <a name="to-enable-the-lock-pages-in-memory-option"></a><span data-ttu-id="7960b-107">若要啟用鎖定記憶體分頁選項</span><span class="sxs-lookup"><span data-stu-id="7960b-107">To enable the lock pages in memory option</span></span>  
  
1.  <span data-ttu-id="7960b-108">在 **[開始]** 功能表上，按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="7960b-108">On the **Start** menu, click **Run**.</span></span> <span data-ttu-id="7960b-109">在 [**開啟**] 方塊中，輸入 `gpedit.msc` 。</span><span class="sxs-lookup"><span data-stu-id="7960b-109">In the **Open** box, type `gpedit.msc`.</span></span>  
  
2.  <span data-ttu-id="7960b-110">在 [本機群組原則編輯器] 主控台中，依序展開 [電腦設定] 和 [Windows 設定]。</span><span class="sxs-lookup"><span data-stu-id="7960b-110">On the **Local Group Policy Editor** console, expand **Computer Configuration**, and then expand **Windows Settings**.</span></span>  
  
3.  <span data-ttu-id="7960b-111">展開 [安全性設定]，然後展開 [本機原則]。</span><span class="sxs-lookup"><span data-stu-id="7960b-111">Expand **Security Settings**, and then expand **Local Policies**.</span></span>  
  
4.  <span data-ttu-id="7960b-112">選取 [使用者權限指派] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="7960b-112">Select the **User Rights Assignment** folder.</span></span>  
  
     <span data-ttu-id="7960b-113">這些原則會顯示在詳細資料窗格中。</span><span class="sxs-lookup"><span data-stu-id="7960b-113">The policies will be displayed in the details pane.</span></span>  
  
5.  <span data-ttu-id="7960b-114">在窗格中按兩下 [鎖定記憶體中的分頁]。</span><span class="sxs-lookup"><span data-stu-id="7960b-114">In the pane, double-click **Lock pages in memory**.</span></span>  
  
6.  <span data-ttu-id="7960b-115">在 [本機安全性設定 - 鎖定記憶體中的分頁] 對話方塊中，按一下 [新增使用者或群組]。</span><span class="sxs-lookup"><span data-stu-id="7960b-115">In the **Local Security Setting - Lock pages in memory** dialog box, click **Add User or Group**.</span></span>  
  
7.  <span data-ttu-id="7960b-116">在 [選取使用者、服務帳戶或群組]\*\*\*\* 對話方塊中，加入具有執行 sqlservr.exe 權限的帳戶。</span><span class="sxs-lookup"><span data-stu-id="7960b-116">In the **Select Users, Service Accounts, or Groups** dialog box, add an account with privileges to run sqlservr.exe.</span></span>  
  
8.  <span data-ttu-id="7960b-117">登出後再重新登入以使這項變更生效。</span><span class="sxs-lookup"><span data-stu-id="7960b-117">Log out and then log back in for this change to take effect.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7960b-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7960b-118">See Also</span></span>  
 [<span data-ttu-id="7960b-119">伺服器記憶體伺服器組態選項</span><span class="sxs-lookup"><span data-stu-id="7960b-119">Server Memory Server Configuration Options</span></span>](server-memory-server-configuration-options.md)  
  
  
