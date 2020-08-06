---
title: 在散發者端啟用遠端發行者 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- remote Distributors [SQL Server replication]
- Publishers [SQL Server replication]
ms.assetid: 6f8e2831-5c45-4e39-8e51-d37e2813cf3d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 06c85924731b79e8b3c79cfbcc354b5bedf69b62
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585852"
---
# <a name="enable-a-remote-publisher-at-a-distributor-sql-server-management-studio"></a><span data-ttu-id="bcc45-102">在散發者端啟用遠端發行者 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="bcc45-102">Enable a Remote Publisher at a Distributor (SQL Server Management Studio)</span></span>
  <span data-ttu-id="bcc45-103">在 **[發行者]** 頁面中讓「發行者」使用遠端「散發者」。</span><span class="sxs-lookup"><span data-stu-id="bcc45-103">Enable a Publisher to use a remote Distributor on the **Publishers** page.</span></span> <span data-ttu-id="bcc45-104">此頁面會在 [設定散發] 精靈與 [散發者屬性 - \<Distributor>] 對話方塊中提供。</span><span class="sxs-lookup"><span data-stu-id="bcc45-104">This page is available in the Configure Distribution Wizard and the **Distributor Properties - \<Distributor>** dialog box.</span></span> <span data-ttu-id="bcc45-105">如需使用精靈以及存取對話方塊的詳細資訊，請參閱[設定發行和散發](configure-publishing-and-distribution.md)和[檢視和修改散發者和發行者屬性](view-and-modify-distributor-and-publisher-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="bcc45-105">For more information about using the wizard and accessing the dialog box, see [Configure Publishing and Distribution](configure-publishing-and-distribution.md) and [View and Modify Distributor and Publisher Properties](view-and-modify-distributor-and-publisher-properties.md).</span></span>  
  
### <a name="to-enable-a-publisher-in-the-configure-distribution-wizard"></a><span data-ttu-id="bcc45-106">若要在設定散發精靈中啟用發行者</span><span class="sxs-lookup"><span data-stu-id="bcc45-106">To enable a Publisher in the Configure Distribution Wizard</span></span>  
  
1.  <span data-ttu-id="bcc45-107">在「設定散發精靈」的 **[發行者]** 頁面中，按一下 **[加入]** 。</span><span class="sxs-lookup"><span data-stu-id="bcc45-107">On the **Publishers** page of the Configure Distribution Wizard, click **Add**.</span></span>  
  
2.  <span data-ttu-id="bcc45-108">按一下 **[加入 SQL Server 發行者]** 。</span><span class="sxs-lookup"><span data-stu-id="bcc45-108">Click **Add SQL Server Publisher**.</span></span> <span data-ttu-id="bcc45-109">如需有關啟用 Oracle 發行者以使用散發者的資訊，請參閱＜ [Create a Publication from an Oracle Database](publish/create-a-publication-from-an-oracle-database.md)＞。</span><span class="sxs-lookup"><span data-stu-id="bcc45-109">For information about enabling an Oracle Publisher to use a Distributor, see [Create a Publication from an Oracle Database](publish/create-a-publication-from-an-oracle-database.md).</span></span>  
  
3.  <span data-ttu-id="bcc45-110">在 **[連接到伺服器]** 對話方塊中，指定將使用遠端散發者的發行者連接資訊，然後按一下 **[連接]** 。</span><span class="sxs-lookup"><span data-stu-id="bcc45-110">In the **Connect to Server** dialog box, specify connection information for the Publisher that will use the remote Distributor, and then click **Connect**.</span></span>  
  
4.  <span data-ttu-id="bcc45-111">在 **[散發者密碼]** 頁面的 **[密碼]** 和 **[確認密碼]** 文字方塊中，為 **distributor_admin** 帳戶 (複寫將用其從「發行者」連接到「散發者」以執行管理工作) 指定增強式密碼。</span><span class="sxs-lookup"><span data-stu-id="bcc45-111">On the **Distributor Password** page, in the **Password** and **Confirm password** text boxes, specify a strong password for the **distributor_admin** account, which replication uses to connect from the Publisher to the Distributor to perform administrative tasks.</span></span>  
  
5.  <span data-ttu-id="bcc45-112">若要檢視和修改發行者的設定，請按一下屬性按鈕 ([...])。</span><span class="sxs-lookup"><span data-stu-id="bcc45-112">To view and modify settings for a Publisher, click the properties button (**...**).</span></span>  
  
6.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-enable-a-publisher-in-the-distributor-properties-dialog-box"></a><span data-ttu-id="bcc45-113">若要在散發者屬性對話方塊中啟用發行者</span><span class="sxs-lookup"><span data-stu-id="bcc45-113">To enable a Publisher in the Distributor Properties dialog box</span></span>  
  
1.  <span data-ttu-id="bcc45-114">在 [散發者屬性 - \<Distributor>] 對話方塊的 [發行者] 頁面上，按一下 [新增]。</span><span class="sxs-lookup"><span data-stu-id="bcc45-114">On the **Publishers** page of the **Distributor Properties - \<Distributor>** dialog box, click **Add**.</span></span>  
  
2.  <span data-ttu-id="bcc45-115">按一下 **[加入 SQL Server 發行者]** 。</span><span class="sxs-lookup"><span data-stu-id="bcc45-115">Click **Add SQL Server Publisher**.</span></span> <span data-ttu-id="bcc45-116">如需有關啟用 Oracle 發行者以使用散發者的資訊，請參閱＜ [Create a Publication from an Oracle Database](publish/create-a-publication-from-an-oracle-database.md)＞。</span><span class="sxs-lookup"><span data-stu-id="bcc45-116">For information about enabling an Oracle Publisher to use a Distributor, see [Create a Publication from an Oracle Database](publish/create-a-publication-from-an-oracle-database.md).</span></span>  
  
3.  <span data-ttu-id="bcc45-117">在 **[連接到伺服器]** 對話方塊中，指定將使用遠端散發者的發行者連接資訊，然後按一下 **[連接]** 。</span><span class="sxs-lookup"><span data-stu-id="bcc45-117">In the **Connect to Server** dialog box, specify connection information for the Publisher that will use the remote Distributor, and then click **Connect**.</span></span>  
  
4.  <span data-ttu-id="bcc45-118">在 **[發行者]** 頁面的 **[密碼]** 和 **[確認密碼]** 文字方塊中，為 **distributor_admin** 帳戶 (複寫將用其從「發行者」連接到「散發者」以執行管理工作) 指定增強式密碼。</span><span class="sxs-lookup"><span data-stu-id="bcc45-118">On the **Publishers** page, in the **Password** and **Confirm password** text boxes, specify a strong password for the **distributor_admin** account, which replication uses to connect from the Publisher to the Distributor to perform administrative tasks.</span></span>  
  
5.  <span data-ttu-id="bcc45-119">若要檢視和修改發行者的設定，請按一下屬性按鈕 ([...])。</span><span class="sxs-lookup"><span data-stu-id="bcc45-119">To view and modify settings for a Publisher, click the properties button (**...**).</span></span>  
  
6.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="bcc45-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bcc45-120">See Also</span></span>  
 <span data-ttu-id="bcc45-121">[設定發行和散發](configure-publishing-and-distribution.md) </span><span class="sxs-lookup"><span data-stu-id="bcc45-121">[Configure Publishing and Distribution](configure-publishing-and-distribution.md) </span></span>  
 <span data-ttu-id="bcc45-122">[[設定散發]](configure-distribution.md) </span><span class="sxs-lookup"><span data-stu-id="bcc45-122">[Configure Distribution](configure-distribution.md) </span></span>  
 [<span data-ttu-id="bcc45-123">保護散發者</span><span class="sxs-lookup"><span data-stu-id="bcc45-123">Secure the Distributor</span></span>](security/secure-the-distributor.md)  
  
  
