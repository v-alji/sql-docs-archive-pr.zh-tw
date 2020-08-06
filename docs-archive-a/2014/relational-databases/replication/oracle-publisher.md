---
title: Oracle 發行者 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newpubwizard.selectoraclepublisher.f1
ms.assetid: 019b7c49-dcca-445d-8969-5982a8ccbc1a
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: db52b93b3d260ff58a151e7238bbbe065bc47bc0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585296"
---
# <a name="oracle-publisher"></a><span data-ttu-id="f4d1e-102">Oracle 發行者</span><span class="sxs-lookup"><span data-stu-id="f4d1e-102">Oracle Publisher</span></span>
  <span data-ttu-id="f4d1e-103">從 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 開始，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 可讓您使用快照式和異動複寫來發佈 Oracle 資料庫的資料。</span><span class="sxs-lookup"><span data-stu-id="f4d1e-103">Beginning with [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] allows you to publish data from an Oracle database using snapshot and transactional replication.</span></span> <span data-ttu-id="f4d1e-104">如需詳細資訊，請參閱 [Oracle 發行概觀](non-sql/oracle-publishing-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="f4d1e-104">For more information, see [Oracle Publishing Overview](non-sql/oracle-publishing-overview.md).</span></span>  
  
 <span data-ttu-id="f4d1e-105">Oracle 發行者必須使用遠端 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 散發者；在安裝和測試必要的 Oracle 網路軟體之後，必須在此伺服器上執行此精靈。</span><span class="sxs-lookup"><span data-stu-id="f4d1e-105">The Oracle Publisher must use a remote [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributor; this wizard must be run on that server after the necessary Oracle networking software has been installed and tested.</span></span> <span data-ttu-id="f4d1e-106">如需詳細資訊，請參閱[設定 Oracle 發行者](non-sql/configure-an-oracle-publisher.md)。</span><span class="sxs-lookup"><span data-stu-id="f4d1e-106">For more information, see [Configure an Oracle Publisher](non-sql/configure-an-oracle-publisher.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="f4d1e-107">如果另一位管理員將 Oracle 資料庫設定為發行者，則在按 **[下一步]** 之後，將提示您輸入用來連接 Oracle 資料庫進行複寫之登入的密碼。</span><span class="sxs-lookup"><span data-stu-id="f4d1e-107">If another administrator configured the Oracle database as a Publisher, after clicking **Next** you will be prompted to enter the password for the replication login used to connect to the Oracle database.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="f4d1e-108">就會在您的登入和 Oracle 資料庫的連結伺服器連接之間建立對應。</span><span class="sxs-lookup"><span data-stu-id="f4d1e-108">will then create a mapping between your login and the linked server connection to the Oracle database.</span></span> <span data-ttu-id="f4d1e-109">對於後續的 Oracle 資料庫連接，您就不必再輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="f4d1e-109">You will not be required to enter a password for subsequent connections to the Oracle database.</span></span>  
  
## <a name="options"></a><span data-ttu-id="f4d1e-110">選項。</span><span class="sxs-lookup"><span data-stu-id="f4d1e-110">Options</span></span>  
 <span data-ttu-id="f4d1e-111">**Oracle 發行者**</span><span class="sxs-lookup"><span data-stu-id="f4d1e-111">**Oracle Publishers**</span></span>  
 <span data-ttu-id="f4d1e-112">從清單中選取 Oracle 發行者。</span><span class="sxs-lookup"><span data-stu-id="f4d1e-112">Select an Oracle Publisher from the list.</span></span> <span data-ttu-id="f4d1e-113">此清單包含先前已設定執行此精靈之伺服器為其散發者的 Oracle 發行者。</span><span class="sxs-lookup"><span data-stu-id="f4d1e-113">This list contains Oracle Publishers that have previously been configured to use the server against which the wizard is running as their Distributor.</span></span> <span data-ttu-id="f4d1e-114">如果清單是空的，或您要使用的 Oracle 發行者不在清單中，請按一下 **[加入 Oracle 發行者]** 。</span><span class="sxs-lookup"><span data-stu-id="f4d1e-114">If the list is empty, or the Oracle Publisher you want to use is not in the list, click **Add Oracle Publisher**.</span></span>  
  
 <span data-ttu-id="f4d1e-115">**[加入 Oracle 發行者]**</span><span class="sxs-lookup"><span data-stu-id="f4d1e-115">**Add Oracle Publisher**</span></span>  
 <span data-ttu-id="f4d1e-116">按一下以啟動 **[散發者屬性]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="f4d1e-116">Click to launch the **Distributor Properties** dialog box.</span></span> <span data-ttu-id="f4d1e-117">在此對話方塊中，按一下 **[加入]** ，然後按一下 **[加入 Oracle 發行者]** 。</span><span class="sxs-lookup"><span data-stu-id="f4d1e-117">In this dialog box, click **Add**, and then click **Add Oracle Publisher**.</span></span> <span data-ttu-id="f4d1e-118">在 **[連接到伺服器]** 對話方塊中，指定 Oracle 伺服器名稱，以及複寫管理的使用者結構描述之登入和密碼。</span><span class="sxs-lookup"><span data-stu-id="f4d1e-118">In the **Connect to Server** dialog box, specify the Oracle server name, and the login and password for the replication administrative user schema.</span></span> <span data-ttu-id="f4d1e-119">如需詳細資訊，請參閱[連線到伺服器 &#40;Oracle&#41;，登入](connect-to-server-oracle-login.md)。</span><span class="sxs-lookup"><span data-stu-id="f4d1e-119">For more information, see [Connect to Server &#40;Oracle&#41;, Login](connect-to-server-oracle-login.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f4d1e-120">如果執行精靈的伺服器尚未設定為散發者，則會提示您立即設定。</span><span class="sxs-lookup"><span data-stu-id="f4d1e-120">If the server against which the wizard is running has not yet been configured as a Distributor, you are prompted to configure it now.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4d1e-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f4d1e-121">See Also</span></span>  
 [<span data-ttu-id="f4d1e-122">從 Oracle 資料庫建立發行集</span><span class="sxs-lookup"><span data-stu-id="f4d1e-122">Create a Publication from an Oracle Database</span></span>](publish/create-a-publication-from-an-oracle-database.md)   

  
  
