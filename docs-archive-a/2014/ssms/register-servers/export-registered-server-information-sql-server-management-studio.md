---
title: 匯出已註冊的伺服器資訊
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.swb.exportregisteredservers.f1
helpviewer_keywords:
- Registered Servers [SQL Server], exporting
- exporting registered server information
- transferring registered server information
ms.assetid: b65e168f-b6bf-489c-b8ad-3b8644acf0b6
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 03092de2d722e8f8b807dbb3d23c4b4e2b91f6f8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705842"
---
# <a name="export-registered-server-information-sql-server-management-studio"></a><span data-ttu-id="70892-102">匯出已註冊的伺服器資訊 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="70892-102">Export Registered Server Information (SQL Server Management Studio)</span></span>
  <span data-ttu-id="70892-103">本主題描述如何儲存並匯出 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]中已註冊伺服器的資訊，並將資訊散發給其他員工或伺服器。</span><span class="sxs-lookup"><span data-stu-id="70892-103">This topic describes how to save and export registered server information in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]and distribute it to other employees or servers.</span></span> <span data-ttu-id="70892-104">您可以使用此匯出功能，在多部電腦上顯示一致的使用者介面。</span><span class="sxs-lookup"><span data-stu-id="70892-104">You can use this export feature to present a consistent user interface on multiple computers.</span></span>  
  
 <span data-ttu-id="70892-105">先匯出然後再匯入已註冊的伺服器檔案，可以讓您輕鬆地在 [已註冊的伺服器] 中使用相同的伺服器設定數部電腦。</span><span class="sxs-lookup"><span data-stu-id="70892-105">Exporting and then importing Registered Server files lets you easily configure several computers with the same servers in Registered Servers.</span></span> <span data-ttu-id="70892-106">從各地的電腦管理大量的伺服器時，或要為較沒有經驗的使用者設定基本連接設定時，這個作法非常有用。</span><span class="sxs-lookup"><span data-stu-id="70892-106">This is useful when managing a large number of servers from computers in several locations, or when you want to configure a less experienced user with basic connection settings.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="70892-107">使用 SQL Server 驗證的伺服器註冊，會以每一使用者為基礎的方式來儲存密碼。</span><span class="sxs-lookup"><span data-stu-id="70892-107">Server registrations that use SQL Server Authentication store passwords on a per-user basis.</span></span> <span data-ttu-id="70892-108">先匯出然後匯入伺服器註冊後，使用者第一次連接到每個伺服器時都必須輸入密碼，將密碼儲存在他們的已註冊的伺服器清單中。</span><span class="sxs-lookup"><span data-stu-id="70892-108">After exporting and importing the server registrations, users must enter the password for each server the first time they connect, storing the passwords in their lists of registered servers.</span></span> <span data-ttu-id="70892-109">針對使用 Windows 驗證註冊的伺服器，則不需如此。</span><span class="sxs-lookup"><span data-stu-id="70892-109">This is not necessary for servers registered using Windows Authentication.</span></span>  
  
##  <a name="SSMSProcedure"></a>  
  
#### <a name="to-export-registered-server-information"></a><span data-ttu-id="70892-110">匯出已註冊的伺服器資訊</span><span class="sxs-lookup"><span data-stu-id="70892-110">To export registered server information</span></span>  
  
1.  <span data-ttu-id="70892-111">在 [已註冊的伺服器] 中，以滑鼠右鍵按一下伺服器群組，然後按一下 [匯出]  。</span><span class="sxs-lookup"><span data-stu-id="70892-111">In Registered Servers, right-click a server group, and then click **Export**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="70892-112">您可以匯出個別伺服器、整個已註冊的伺服器樹狀目錄，或已註冊的伺服器樹狀目錄之子集。</span><span class="sxs-lookup"><span data-stu-id="70892-112">You can export an individual server, all of the registered server tree, or a subset of the registered server tree.</span></span>  
  
2.  <span data-ttu-id="70892-113">在 **[匯出已註冊的伺服器]** 對話方塊中，進行下列選取。</span><span class="sxs-lookup"><span data-stu-id="70892-113">In the **Export Registered Servers** dialog box, make the following selections.</span></span>  
  
     <span data-ttu-id="70892-114">**伺服器群組**</span><span class="sxs-lookup"><span data-stu-id="70892-114">**Server group**</span></span>  
     <span data-ttu-id="70892-115">指定將要匯出的伺服器群組。</span><span class="sxs-lookup"><span data-stu-id="70892-115">Specify the server group which will be exported.</span></span> <span data-ttu-id="70892-116">將所有已註冊的伺服器、特定伺服器群組中已註冊的伺服器，或單一已註冊的伺服器匯出至匯出檔案。</span><span class="sxs-lookup"><span data-stu-id="70892-116">Export all registered servers, registered servers in a particular server group, or a single registered server to the export file.</span></span> <span data-ttu-id="70892-117">匯出功能是遞迴的；例如，如果伺服器群組 A 包含伺服器群組 B，而伺服器群組 B 包含伺服器群組 C 和 D，則匯出伺服器群組 A 會匯出 A、B、C 以及 D 中的所有項目。</span><span class="sxs-lookup"><span data-stu-id="70892-117">The export functionality is recursive; for example, if server group A contains server group B, and server group B contains server groups C and D, exporting server group A exports all entries in A, B, C, and D.</span></span>  
  
     <span data-ttu-id="70892-118">伺服器群組僅會顯示目前已註冊的伺服器樹狀目錄的伺服器群組。</span><span class="sxs-lookup"><span data-stu-id="70892-118">The server group displays only the server groups of the current registered server tree.</span></span>  
  
     <span data-ttu-id="70892-119">**匯出檔案**</span><span class="sxs-lookup"><span data-stu-id="70892-119">**Export file**</span></span>  
     <span data-ttu-id="70892-120">在文字方塊中鍵入匯出檔案的名稱，或使用瀏覽按鈕 ( **...** ) 以找出用戶端電腦上的匯出檔案。</span><span class="sxs-lookup"><span data-stu-id="70892-120">Type the name of the export file in the text box or use the Browse button (**...**) to locate an export file on the client computer.</span></span> <span data-ttu-id="70892-121">如果您選取現有的檔案，則已註冊的伺服器資訊會附加至該檔案。</span><span class="sxs-lookup"><span data-stu-id="70892-121">If you select an existing file, the registered server information is appended to the file.</span></span> <span data-ttu-id="70892-122">使用 .regsrvr 副檔名。</span><span class="sxs-lookup"><span data-stu-id="70892-122">Use the .regsrvr extension.</span></span> <span data-ttu-id="70892-123">如果您要提供已註冊的伺服器資訊給其他使用者或另一部電腦使用，您可以將檔案儲存在網路上。</span><span class="sxs-lookup"><span data-stu-id="70892-123">If you want your registered server information to be available to other users or another computer, you can save the file on the network.</span></span> <span data-ttu-id="70892-124">其他使用者就可以存取檔案，並匯入部分或全部已註冊的伺服器資訊。</span><span class="sxs-lookup"><span data-stu-id="70892-124">Other users can access the file and import part or all of the registered server information.</span></span> <span data-ttu-id="70892-125">如果您選取現有的檔案作為匯出檔案，則伺服器註冊資訊會覆寫該檔案的內容。</span><span class="sxs-lookup"><span data-stu-id="70892-125">If you select an existing file as your export file, the contents of the file are overwritten with the server registration information.</span></span>  
  
     <span data-ttu-id="70892-126">**不要在匯出檔案中包含使用者名稱與密碼**</span><span class="sxs-lookup"><span data-stu-id="70892-126">**Do not include user names and passwords in the export file**</span></span>  
     <span data-ttu-id="70892-127">匯出檔案時排除使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="70892-127">Exclude user names when exporting the file.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="70892-128">雖然匯出檔案已加密，但是如果使用者名稱與 SQL Server 驗證密碼均包含在檔案中，則要小心控制該檔案的存取權。</span><span class="sxs-lookup"><span data-stu-id="70892-128">Although the export files are encrypted, if user names and SQL Server Authentication passwords are included in the file, access to the file should be carefully controlled.</span></span> <span data-ttu-id="70892-129">因此，依預設使用者名稱與密碼會排除在匯出檔案之外。</span><span class="sxs-lookup"><span data-stu-id="70892-129">User names and passwords are therefore excluded from the export file by default.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70892-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="70892-130">See Also</span></span>  
 <span data-ttu-id="70892-131">匯[入已註冊的伺服器資訊 &#40;SQL Server Management Studio&#41;](import-registered-server-information-sql-server-management-studio.md) [建立新的已註冊伺服器 &#40;SQL Server Management Studio&#41;](create-a-new-registered-server-sql-server-management-studio.md)</span><span class="sxs-lookup"><span data-stu-id="70892-131">[Import Registered Server Information &#40;SQL Server Management Studio&#41;](import-registered-server-information-sql-server-management-studio.md) [Create a New Registered Server &#40;SQL Server Management Studio&#41;](create-a-new-registered-server-sql-server-management-studio.md)</span></span>  
  
  
