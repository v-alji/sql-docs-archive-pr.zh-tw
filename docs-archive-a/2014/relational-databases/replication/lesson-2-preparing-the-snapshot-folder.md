---
title: 第 2 課：準備快照集資料夾 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], tutorials
ms.assetid: f286cde9-c0d0-43ef-b7ba-53c3cbb8906c
author: rothja
ms.author: jroth
ms.openlocfilehash: 5d98c7433d0bd50504f20f7f576fcf0b20154c81
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707382"
---
# <a name="lesson-2-preparing-the-snapshot-folder"></a><span data-ttu-id="d3ab1-102">第 2 課：準備快照集資料夾</span><span class="sxs-lookup"><span data-stu-id="d3ab1-102">Lesson 2: Preparing the Snapshot Folder</span></span>
  <span data-ttu-id="d3ab1-103">在這一課，您將學習設定用於建立及儲存發行集快照集的快照集資料夾。</span><span class="sxs-lookup"><span data-stu-id="d3ab1-103">In this lesson, you will learn to configure the snapshot folder that is used to create and store the publication snapshot.</span></span>  
  
### <a name="to-create-a-share-for-the-snapshot-folder-and-assign-permissions"></a><span data-ttu-id="d3ab1-104">建立快照集資料夾的共用並指定權限</span><span class="sxs-lookup"><span data-stu-id="d3ab1-104">To create a share for the snapshot folder and assign permissions</span></span>  
  
1.  <span data-ttu-id="d3ab1-105">在 [Windows 檔案總管] 中，導覽到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料的資料夾。</span><span class="sxs-lookup"><span data-stu-id="d3ab1-105">In Windows Explorer, navigate to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data folder.</span></span> <span data-ttu-id="d3ab1-106">預設位置是 C:\Program Files\Microsoft SQL Server\MSSQL.X\MSSQL\Data。</span><span class="sxs-lookup"><span data-stu-id="d3ab1-106">The default location is C:\Program Files\Microsoft SQL Server\MSSQL.X\MSSQL\Data.</span></span>  
  
2.  <span data-ttu-id="d3ab1-107">建立名為 **repldata**的新資料夾。</span><span class="sxs-lookup"><span data-stu-id="d3ab1-107">Create a new folder named **repldata**.</span></span>  
  
3.  <span data-ttu-id="d3ab1-108">以滑鼠右鍵按一下該資料夾，然後按一下 [內容]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d3ab1-108">Right-click this folder and click **Properties**.</span></span>  
  
4.  <span data-ttu-id="d3ab1-109">在 [repldata 內容]\*\*\*\* 對話方塊的 [共用]\*\*\*\* 索引標籤上，按一下 [共用]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d3ab1-109">On the **Sharing** tab in the **repldata Properties** dialog box, click **Share**.</span></span>  
  
5.  <span data-ttu-id="d3ab1-110">在 [檔案共用]\*\*\*\* 對話方塊中，按一下 [共用]\*\*\*\*，然後按一下 [完成]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d3ab1-110">In the **File Sharing** dialog box, click **Share**, and then click **Done**.</span></span>  
  
6.  <span data-ttu-id="d3ab1-111">在 **[安全性]** 索引標籤上，按一下 **[編輯]** 。</span><span class="sxs-lookup"><span data-stu-id="d3ab1-111">On the **Security** tab, click **Edit**.</span></span>  
  
7.  <span data-ttu-id="d3ab1-112">在 [權限]\*\*\*\* 對話方塊中，按一下 [新增]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d3ab1-112">In the **Permissions** dialog box, click **Add.**</span></span> <span data-ttu-id="d3ab1-113">在 [**選取使用者、電腦、服務帳戶或群組**] 文字方塊中，輸入第1課所建立快照集代理程式帳戶的名稱，例如 \<_Machine_Name> _**\ repl_snapshot**，其中 \<*Machine_Name> \* 是發行者的名稱。</span><span class="sxs-lookup"><span data-stu-id="d3ab1-113">In the **Select User, Computers, Service Account, or Groups** text box, type the name of the Snapshot Agent account created in Lesson 1, as \<_Machine_Name>_**\repl_snapshot**, where \<*Machine_Name>\* is the name of the Publisher.</span></span> <span data-ttu-id="d3ab1-114">按一下 [檢查名稱]\*\*\*\*，然後按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d3ab1-114">Click **Check Names**, and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="d3ab1-115">重複上一個步驟，將散發代理程式的許可權、 \<_Machine_Name> _ **\ repl_distribution**，以及合併代理程式 \<_Machine_Name> _的**\ repl_merge**。</span><span class="sxs-lookup"><span data-stu-id="d3ab1-115">Repeat the previous step to add permissions for the Distribution Agent, as \<_Machine_Name>_**\repl_distribution**, and for the Merge Agent as \<_Machine_Name>_**\repl_merge**.</span></span>  
  
9. <span data-ttu-id="d3ab1-116">確認允許下列權限；</span><span class="sxs-lookup"><span data-stu-id="d3ab1-116">Verify the following permissions are allowed:</span></span>  
  
    -   <span data-ttu-id="d3ab1-117">repl_snapshot - Full Control</span><span class="sxs-lookup"><span data-stu-id="d3ab1-117">repl_snapshot - Full Control</span></span>  
  
    -   <span data-ttu-id="d3ab1-118">repl_distribution - Read</span><span class="sxs-lookup"><span data-stu-id="d3ab1-118">repl_distribution - Read</span></span>  
  
    -   <span data-ttu-id="d3ab1-119">repl_merge - Read</span><span class="sxs-lookup"><span data-stu-id="d3ab1-119">repl_merge - Read</span></span>  
  
10. <span data-ttu-id="d3ab1-120">按一下 [確定]\*\*\*\* 關閉 [repldata 屬性]\*\*\*\* 對話方塊，並建立 repldata 共用。</span><span class="sxs-lookup"><span data-stu-id="d3ab1-120">Click **OK** to close the **repldata Properties** dialog box and create the repldata share.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="d3ab1-121">後續步驟</span><span class="sxs-lookup"><span data-stu-id="d3ab1-121">Next Steps</span></span>  
 <span data-ttu-id="d3ab1-122">您已順利設定快照集資料夾的共用。</span><span class="sxs-lookup"><span data-stu-id="d3ab1-122">You have successfully configured the share for the snapshot folder.</span></span> <span data-ttu-id="d3ab1-123">下一步，您將設定散發。</span><span class="sxs-lookup"><span data-stu-id="d3ab1-123">Next, you will configure distribution.</span></span> <span data-ttu-id="d3ab1-124">請參閱 [第 3 課：設定散發](lesson-3-configuring-distribution.md)。</span><span class="sxs-lookup"><span data-stu-id="d3ab1-124">See [Lesson 3: Configuring Distribution](lesson-3-configuring-distribution.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3ab1-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d3ab1-125">See Also</span></span>  
 [<span data-ttu-id="d3ab1-126">保護快照集資料夾</span><span class="sxs-lookup"><span data-stu-id="d3ab1-126">Secure the Snapshot Folder</span></span>](security/secure-the-snapshot-folder.md)  
  
  
