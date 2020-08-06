---
title: MSSQLSERVER_17832 | Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 17828 (Database Engine error)
- maxtokensize
- 17832 (Database Engine error)
- login packet (bad)
ms.assetid: bd56ffe4-0855-4ada-8aca-251fbc6ff2ce
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: dba214e2cce04ff2583e12ae7cee9b54373390a6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687945"
---
# <a name="mssqlserver_17832"></a><span data-ttu-id="712d2-102">MSSQLSERVER_17832</span><span class="sxs-lookup"><span data-stu-id="712d2-102">MSSQLSERVER_17832</span></span>
    
## <a name="details"></a><span data-ttu-id="712d2-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="712d2-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="712d2-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="712d2-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="712d2-105">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="712d2-105">Event ID</span></span>|<span data-ttu-id="712d2-106">17832</span><span class="sxs-lookup"><span data-stu-id="712d2-106">17832</span></span>|  
|<span data-ttu-id="712d2-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="712d2-107">Event Source</span></span>|<span data-ttu-id="712d2-108">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="712d2-108">MSSQLSERVER</span></span>|  
|<span data-ttu-id="712d2-109">元件</span><span class="sxs-lookup"><span data-stu-id="712d2-109">Component</span></span>|<span data-ttu-id="712d2-110">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="712d2-110">SQLEngine</span></span>|  
|<span data-ttu-id="712d2-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="712d2-111">Symbolic Name</span></span>|<span data-ttu-id="712d2-112">SRV_BAD_LOGIN_PKT</span><span class="sxs-lookup"><span data-stu-id="712d2-112">SRV_BAD_LOGIN_PKT</span></span>|  
|<span data-ttu-id="712d2-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="712d2-113">Message Text</span></span>|<span data-ttu-id="712d2-114">用來開啟連接的登入封包的結構無效; 此連接已經關閉。</span><span class="sxs-lookup"><span data-stu-id="712d2-114">The login packet used to open the connection is structurally invalid; the connection has been closed.</span></span> <span data-ttu-id="712d2-115">請聯繫用戶端程式庫的供應商。%.\*ls</span><span class="sxs-lookup"><span data-stu-id="712d2-115">Please contact the vendor of the client library.%.\*ls</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="712d2-116">說明</span><span class="sxs-lookup"><span data-stu-id="712d2-116">Explanation</span></span>  
 <span data-ttu-id="712d2-117">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 電腦無法處理用戶端登入封包。</span><span class="sxs-lookup"><span data-stu-id="712d2-117">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] computer was unable to process the client login packet.</span></span> <span data-ttu-id="712d2-118">這可能是因為封包的建立方式不正確，或者封包在傳輸期間已損毀。</span><span class="sxs-lookup"><span data-stu-id="712d2-118">This may be because the packet was created improperly or because the packet was damaged during transmission.</span></span> <span data-ttu-id="712d2-119">此外，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 電腦的組態也可能會造成這個錯誤。</span><span class="sxs-lookup"><span data-stu-id="712d2-119">It can also be caused by the configuration of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] computer.</span></span> <span data-ttu-id="712d2-120">所列出的 IP 位址就是用戶端電腦的位址。</span><span class="sxs-lookup"><span data-stu-id="712d2-120">The IP address listed is the address of the client computer.</span></span>  
  
### <a name="more-information"></a><span data-ttu-id="712d2-121">相關資訊</span><span class="sxs-lookup"><span data-stu-id="712d2-121">More Information</span></span>  
 <span data-ttu-id="712d2-122">在 Kerberos 環境中使用 Windows 驗證時，用戶端就會接收包含專用權屬性憑證 (PAC) 的 Kerberos Ticket。</span><span class="sxs-lookup"><span data-stu-id="712d2-122">When using Windows Authentication in a Kerberos environment, a client receives a Kerberos ticket that contains a Privilege Attribute Certificate (PAC).</span></span> <span data-ttu-id="712d2-123">此 PAC 包含各種類型的授權資料，包括使用者為所屬成員的群組、使用者擁有的權限，以及哪些原則會套用至使用者。</span><span class="sxs-lookup"><span data-stu-id="712d2-123">The PAC contains various types of authorization data including groups that the user is a member of, rights the user has, and what policies apply to the user.</span></span> <span data-ttu-id="712d2-124">當此用戶端接收 Kerberos Ticket 時，PAC 中所包含的資訊就會用來產生使用者的存取 Token。</span><span class="sxs-lookup"><span data-stu-id="712d2-124">When the client receives the Kerberos ticket, the information contained in the PAC is used to generate the user's access token.</span></span> <span data-ttu-id="712d2-125">此用戶端會將 Token 呈現給 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 電腦，當做登入封包的一部分。</span><span class="sxs-lookup"><span data-stu-id="712d2-125">The client presents the token to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] computer as part of the login packet.</span></span>  
  
 <span data-ttu-id="712d2-126">如果此 Token 的建立方式不正確或者在傳輸期間已損毀，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 就無法提供有關問題的其他資訊。</span><span class="sxs-lookup"><span data-stu-id="712d2-126">If the token was improperly created or damaged during transmission, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cannot offer additional information about the problem.</span></span>  
  
 <span data-ttu-id="712d2-127">當使用者是屬於許多群組的成員或者具有許多原則時，此 Token 的大小可能會超過一般大小才能列出所有項目。</span><span class="sxs-lookup"><span data-stu-id="712d2-127">When the user is a member of many groups or has many policies, the token may grow larger than normal to list them all.</span></span> <span data-ttu-id="712d2-128">如果此 Token 的大小超過伺服器電腦的 **MaxTokenSize** 值，用戶端就會因為一般網路錯誤 (GNE) 而無法連線，而且可能會發生錯誤 17832。</span><span class="sxs-lookup"><span data-stu-id="712d2-128">If the token grows larger than the **MaxTokenSize** value of the server computer, the client fails to connect with a General Network Error (GNE) and error 17832 can occur.</span></span> <span data-ttu-id="712d2-129">這個問題可能只會影響某些使用者：具有許多群組或原則的使用者。</span><span class="sxs-lookup"><span data-stu-id="712d2-129">This problem may affect only some users: users with many groups or policies.</span></span> <span data-ttu-id="712d2-130">當此問題是伺服器電腦的 **MaxTokenSize** 值時，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 錯誤記錄檔中的錯誤 17832 將會伴隨狀態 9 的錯誤一起出現。</span><span class="sxs-lookup"><span data-stu-id="712d2-130">When the problem is the **MaxTokenSize** value of the server computer, error 17832 in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log will be accompanied by an error with state 9.</span></span> <span data-ttu-id="712d2-131">如需 Kerberos 和 **MaxTokenSize** 的其他詳細資料，請參閱 [KB327825](https://support.microsoft.com/kb/327825)。</span><span class="sxs-lookup"><span data-stu-id="712d2-131">For additional details about the Kerberos and **MaxTokenSize**, see [KB327825](https://support.microsoft.com/kb/327825).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="712d2-132">使用者動作</span><span class="sxs-lookup"><span data-stu-id="712d2-132">User Action</span></span>  
 <span data-ttu-id="712d2-133">若要解決這個問題，請將伺服器電腦的 **MaxTokenSize** 值增加到足以包含組織內任何使用者之最大 Token 的大小。</span><span class="sxs-lookup"><span data-stu-id="712d2-133">To resolve this problem, increase the **MaxTokenSize** value of the server computer, to a size large enough to contain the largest token of any user in your organization.</span></span> <span data-ttu-id="712d2-134">若要針對組織研究正確的 Token 大小，請考慮使用 **Tokensz** 應用程式。</span><span class="sxs-lookup"><span data-stu-id="712d2-134">To research the correct token size for your organization, consider using the **Tokensz** application.</span></span>   
  
> [!CAUTION]  
>  [!INCLUDE[ssNoteRegistry](../../includes/ssnoteregistry-md.md)]  
  
 <span data-ttu-id="712d2-135">**變更伺服器電腦上的 MaxTokenSize**</span><span class="sxs-lookup"><span data-stu-id="712d2-135">**To change the MaxTokenSize  on the server computer**</span></span>  
  
1.  <span data-ttu-id="712d2-136">在 **[開始]** 功能表上，按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="712d2-136">On the **Start** menu, click **Run**.</span></span>  
  
2.  <span data-ttu-id="712d2-137">輸入 `regedit` ，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="712d2-137">Type `regedit`, and then click **OK**.</span></span> <span data-ttu-id="712d2-138">(如果出現 [使用者帳戶控制] 對話方塊，請按一下 [繼續])。</span><span class="sxs-lookup"><span data-stu-id="712d2-138">(If the **User Account Control** dialog box appears, click **Continue**.)</span></span>  
  
3.  <span data-ttu-id="712d2-139">巡覽至 **HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\Lsa\Kerberos\Parameters**。</span><span class="sxs-lookup"><span data-stu-id="712d2-139">Navigate to **HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\Lsa\Kerberos\Parameters**.</span></span>  
  
4.  <span data-ttu-id="712d2-140">如果 **MaxTokenSize** 參數不存在，請以滑鼠右鍵按一下 [參數]，並指向 [新增]，然後按一下 [DWORD (32-位元) 值]。</span><span class="sxs-lookup"><span data-stu-id="712d2-140">If the **MaxTokenSize** parameter is not present, right-click **Parameters**, point to **New**, and then click **DWORD (32-bit)** Value.</span></span> <span data-ttu-id="712d2-141">將此登錄項目命名為 **MaxTokenSize**。</span><span class="sxs-lookup"><span data-stu-id="712d2-141">Name the registry entry **MaxTokenSize**.</span></span>  
  
5.  <span data-ttu-id="712d2-142">以滑鼠右鍵按一下 **MaxTokenSize**，然後按一下 [修改]。</span><span class="sxs-lookup"><span data-stu-id="712d2-142">Right-click **MaxTokenSize**, and then click **Modify**.</span></span>  
  
6.  <span data-ttu-id="712d2-143">在 [數值資料] 方塊中，輸入所需的 **MaxTokenSize** 值。</span><span class="sxs-lookup"><span data-stu-id="712d2-143">In the **Value data** box type the desired **MaxTokenSize** value.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="712d2-144">十六進位值 ffff (十進位值 65535) 是最大的建議 Token 大小。</span><span class="sxs-lookup"><span data-stu-id="712d2-144">Hexadecimal value ffff (decimal value 65535) is the maximum recommended token size.</span></span> <span data-ttu-id="712d2-145">雖然提供這個值可能會解決此問題，但是卻可能會對效能造成整部電腦的不良影響。</span><span class="sxs-lookup"><span data-stu-id="712d2-145">Providing this value would probably solve the problem, but could have negative computer-wide effects with regard to performance.</span></span> <span data-ttu-id="712d2-146">我們建議您建立允許組織內任何使用者之最大 Token 的最小 **MaxTokenSize** 值並且輸入該值。</span><span class="sxs-lookup"><span data-stu-id="712d2-146">We recommend that you establish the minimum **MaxTokenSize** value that allows for the largest token of any user in your organization and enter that value.</span></span>  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
8.  <span data-ttu-id="712d2-147">關閉 [登錄編輯程式]。</span><span class="sxs-lookup"><span data-stu-id="712d2-147">Close **Registry Editor**.</span></span>  
  
9. <span data-ttu-id="712d2-148">重新啟動電腦。</span><span class="sxs-lookup"><span data-stu-id="712d2-148">Restart the computer.</span></span>  
  
  
