---
title: 匯入已註冊的伺服器資訊
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.swb.importregisteredservers.f1
helpviewer_keywords:
- transferring registered server information
- Registered Servers [SQL Server], importing
- importing registered server information
ms.assetid: cc497a14-1360-4887-b70c-002f042823b6
author: markingmyname
ms.author: maghan
ms.openlocfilehash: f2eddb3b83f73253e977316767f2b930bc8ab9ff
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705845"
---
# <a name="import-registered-server-information-sql-server-management-studio"></a><span data-ttu-id="aee03-102">匯入已註冊的伺服器資訊 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="aee03-102">Import Registered Server Information (SQL Server Management Studio)</span></span>
  <span data-ttu-id="aee03-103">本主題描述如何在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]中匯入儲存的已註冊伺服器資訊。</span><span class="sxs-lookup"><span data-stu-id="aee03-103">This topic describes how to import saved registered server information in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="aee03-104">先匯出然後再匯入已註冊的伺服器檔案，可以讓您輕鬆地在 [已註冊的伺服器] 中，使用相同的伺服器設定數部電腦。</span><span class="sxs-lookup"><span data-stu-id="aee03-104">Exporting and then importing registered server files lets you easily configure several computers with the same servers in Registered Servers.</span></span> <span data-ttu-id="aee03-105">從各地的電腦管理大量的伺服器時，或要為較沒有經驗的使用者設定基本連接設定時，這個作法非常有用。</span><span class="sxs-lookup"><span data-stu-id="aee03-105">This is useful when managing a large number of servers from computers in several locations, or when you want to configure basic connection settings for a less-experienced user.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="aee03-106">您無法從舊版 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 將已註冊的伺服器資訊匯入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中。</span><span class="sxs-lookup"><span data-stu-id="aee03-106">You cannot import registered server information into [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] from earlier versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
##  <a name="SSMSProcedure"></a>  
  
#### <a name="to-import-registered-server-information"></a><span data-ttu-id="aee03-107">匯入已註冊的伺服器資訊</span><span class="sxs-lookup"><span data-stu-id="aee03-107">To import registered server information</span></span>  
  
1.  <span data-ttu-id="aee03-108">在 [已註冊的伺服器] 中，按一下 [已註冊的伺服器] 工具列上的伺服器類型。</span><span class="sxs-lookup"><span data-stu-id="aee03-108">In Registered Servers, click the server type on the Registered Servers toolbar.</span></span> <span data-ttu-id="aee03-109">伺服器類型必須和已註冊伺服器的匯出檔案同類型。</span><span class="sxs-lookup"><span data-stu-id="aee03-109">The server type must be the same as the registered server export file type.</span></span> <span data-ttu-id="aee03-110">例如，如果您已匯出 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 已註冊的伺服器資訊，則必須在 [已註冊的伺服器] 工具列上按一下 **[SQL Server]** 。</span><span class="sxs-lookup"><span data-stu-id="aee03-110">For example, if you have exported [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] registered server information, you must click **SQL Server** on the Registered Servers toolbar.</span></span>  
  
2.  <span data-ttu-id="aee03-111">以滑鼠右鍵按一下伺服器群組，並選取 [匯入]  。</span><span class="sxs-lookup"><span data-stu-id="aee03-111">Right-click a server group, and select **Import**.</span></span>  
  
3.  <span data-ttu-id="aee03-112">在 **[匯入已註冊的伺服器]** 對話方塊中，選取要匯入的已註冊伺服器檔案，然後按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="aee03-112">In the **Import Registered Servers** dialog box, select the registered servers file to import, and then click **OK**.</span></span>  
  
     <span data-ttu-id="aee03-113">**匯入檔案**</span><span class="sxs-lookup"><span data-stu-id="aee03-113">**Import file**</span></span>  
     <span data-ttu-id="aee03-114">在文字方塊中鍵入匯入檔案的名稱，或按一下瀏覽按鈕 ( **...** ) 以找出用戶端電腦上的匯入檔案。</span><span class="sxs-lookup"><span data-stu-id="aee03-114">Type the name of the import file in the text box, or click the Browse button (**...**) to locate the import file on the client computer.</span></span> <span data-ttu-id="aee03-115">如果您選取現有的檔案，則已註冊的伺服器資訊會附加至該檔案。</span><span class="sxs-lookup"><span data-stu-id="aee03-115">If you select an existing file, the registered server information is appended to the file.</span></span> <span data-ttu-id="aee03-116">匯入檔案僅可為先前匯出之已註冊的伺服器檔案。</span><span class="sxs-lookup"><span data-stu-id="aee03-116">The import file can only be a previously exported registered server file.</span></span> <span data-ttu-id="aee03-117">已註冊的伺服器檔案的副檔名為 .regsrvr。</span><span class="sxs-lookup"><span data-stu-id="aee03-117">Registered server files have a .regsrvr extension.</span></span>  
  
     <span data-ttu-id="aee03-118">**選取要匯入的伺服器群組**</span><span class="sxs-lookup"><span data-stu-id="aee03-118">**Select the server group to import to**</span></span>  
     <span data-ttu-id="aee03-119">選取檔案中已註冊的伺服器項目將要匯入的根節點或特定伺服器群組。</span><span class="sxs-lookup"><span data-stu-id="aee03-119">Select the root node or a particular server group to which the registered server entries in the file will be imported.</span></span> <span data-ttu-id="aee03-120">您可以將所有已註冊的伺服器、特定伺服器群組中已註冊的伺服器或單一已註冊的伺服器匯入至匯出檔案。</span><span class="sxs-lookup"><span data-stu-id="aee03-120">You can import all registered servers, registered servers in a particular server group, or a single registered server to the export file.</span></span> <span data-ttu-id="aee03-121">匯入功能是遞迴的；例如，如果伺服器群組 A 包含伺服器群組 B，而伺服器群組 B 包含伺服器群組 C 和 D，則匯入伺服器群組 A 會匯出 A、B、C 以及 D 中的所有項目。</span><span class="sxs-lookup"><span data-stu-id="aee03-121">The import functionality is recursive; for example, if server group A contains server group B, and server group B contains server groups C and D, importing server group A exports all entries in A, B, C, and D.</span></span>  
  
     <span data-ttu-id="aee03-122">伺服器群組僅會顯示目前已註冊的伺服器樹狀目錄的伺服器群組。</span><span class="sxs-lookup"><span data-stu-id="aee03-122">The server group displays only the server groups of the current registered server tree.</span></span>  
  
     <span data-ttu-id="aee03-123">如果選取匯入現有的伺服器群組或伺服器，就會出現訊息，確認您想要覆寫現有的伺服器或伺服器群組。</span><span class="sxs-lookup"><span data-stu-id="aee03-123">If you select to import an existing server group or server, a message confirms that you want to overwrite the existing server or server group.</span></span>  
  
 <span data-ttu-id="aee03-124">使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證的伺服器註冊會以每位使用者的方式儲存密碼。</span><span class="sxs-lookup"><span data-stu-id="aee03-124">Server registrations that use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication store passwords on a per-user basis.</span></span> <span data-ttu-id="aee03-125">匯入伺服器註冊後，使用者第一次連接到每個伺服器時都必須輸入密碼，將密碼儲存在他們的已註冊的伺服器清單中。</span><span class="sxs-lookup"><span data-stu-id="aee03-125">After importing the server registrations, users must enter the password for each server the first time they connect, storing the passwords in their lists of registered servers.</span></span> <span data-ttu-id="aee03-126">透過 Windows 驗證註冊的伺服器則不需如此。</span><span class="sxs-lookup"><span data-stu-id="aee03-126">This is not necessary for servers registered through Windows Authentication.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aee03-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aee03-127">See Also</span></span>  
 <span data-ttu-id="aee03-128">[變更伺服器的註冊 &#40;SQL Server Management Studio&#41;](change-a-server-s-registration-sql-server-management-studio.md) [匯出已註冊的伺服器資訊 &#40;SQL Server Management Studio&#41;](export-registered-server-information-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="aee03-128">[Change a Server's Registration &#40;SQL Server Management Studio&#41;](change-a-server-s-registration-sql-server-management-studio.md) [Export Registered Server Information &#40;SQL Server Management Studio&#41;](export-registered-server-information-sql-server-management-studio.md) </span></span>  
 [<span data-ttu-id="aee03-129">建立新的已註冊伺服器 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="aee03-129">Create a New Registered Server &#40;SQL Server Management Studio&#41;</span></span>](create-a-new-registered-server-sql-server-management-studio.md)  
  
  
