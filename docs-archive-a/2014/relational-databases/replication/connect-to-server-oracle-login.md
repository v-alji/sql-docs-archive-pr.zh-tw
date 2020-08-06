---
title: 連接到伺服器 (Oracle)，登入 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.oracleconnection.login.f1
helpviewer_keywords:
- Connect to Server dialog box, replication
ms.assetid: 86ed91a1-a07c-46f2-a913-67317ef2255e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 23f5b515fcb1e80416d860e2ff3a2e6be5431819
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585318"
---
# <a name="connect-to-server-oracle-login"></a><span data-ttu-id="875d6-102">連接到伺服器 (Oracle)，登入</span><span class="sxs-lookup"><span data-stu-id="875d6-102">Connect to Server (Oracle), Login</span></span>
  <span data-ttu-id="875d6-103">使用 [連線到伺服器]  對話方塊的 [登入]  索引標籤，即可指定從 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 散發者連線到 Oracle 發行者的帳戶。</span><span class="sxs-lookup"><span data-stu-id="875d6-103">Use the **Login** tab of the **Connect to Server** dialog box to specify the account under which connections are made from the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributor to the Oracle Publisher.</span></span> <span data-ttu-id="875d6-104">您必須使用在發行者組態期間，為複寫管理的使用者結構描述指定之相同帳戶。</span><span class="sxs-lookup"><span data-stu-id="875d6-104">You must use the same account as the one specified for the replication administrative user schema during configuration of the Publisher.</span></span> <span data-ttu-id="875d6-105">如需詳細資訊，請參閱[設定 Oracle 發行者](non-sql/configure-an-oracle-publisher.md)。</span><span class="sxs-lookup"><span data-stu-id="875d6-105">For more information, see [Configure an Oracle Publisher](non-sql/configure-an-oracle-publisher.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="875d6-106">選項。</span><span class="sxs-lookup"><span data-stu-id="875d6-106">Options</span></span>  
 <span data-ttu-id="875d6-107">**伺服器執行個體**</span><span class="sxs-lookup"><span data-stu-id="875d6-107">**Server instance**</span></span>  
 <span data-ttu-id="875d6-108">Oracle 發行者的透明網路基質 (Transparent Network Substrate，TNS) 名稱，是安裝在散發者上的 Oracle 用戶端軟體於組態期間指定的。</span><span class="sxs-lookup"><span data-stu-id="875d6-108">The Transparent Network Substrate (TNS) name of the Oracle Publisher, which is specified during configuration of the Oracle client software installed on the Distributor.</span></span>  
  
 <span data-ttu-id="875d6-109">**驗證**</span><span class="sxs-lookup"><span data-stu-id="875d6-109">**Authentication**</span></span>  
 <span data-ttu-id="875d6-110">選取 **[Oracle 標準驗證]** (建議選項) 或 **[Windows 驗證]** 。</span><span class="sxs-lookup"><span data-stu-id="875d6-110">Select **Oracle Standard Authentication** (recommended) or **Windows Authentication**.</span></span> <span data-ttu-id="875d6-111">如果您選取 **[Windows 驗證]** ：</span><span class="sxs-lookup"><span data-stu-id="875d6-111">If you select **Windows Authentication**:</span></span>  
  
-   <span data-ttu-id="875d6-112">Oracle 伺服器必須設定為允許使用 Windows 認證進行連接。</span><span class="sxs-lookup"><span data-stu-id="875d6-112">The Oracle server must be configured to allow connections using Windows credentials.</span></span> <span data-ttu-id="875d6-113">如需詳細資訊，請參閱 Oracle 文件集。</span><span class="sxs-lookup"><span data-stu-id="875d6-113">For more information, see the Oracle documentation.</span></span>  
  
-   <span data-ttu-id="875d6-114">您目前必須是使用與複寫管理的使用者結構描述所指定的相同 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 帳戶登入的。</span><span class="sxs-lookup"><span data-stu-id="875d6-114">You must be currently logged in with the same [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows account you specified for the replication administrative user schema.</span></span>  
  
 <span data-ttu-id="875d6-115">**[登入]** 和 **[密碼]**</span><span class="sxs-lookup"><span data-stu-id="875d6-115">**Login** and **Password**</span></span>  
 <span data-ttu-id="875d6-116">如果您在 **[驗證]** 選項選取了 **[Oracle 標準驗證]** ，請指定要使用的登入和密碼，這必須與複寫管理的使用者結構描述指定之登入和密碼相同。</span><span class="sxs-lookup"><span data-stu-id="875d6-116">If you selected **Oracle Standard Authentication** for the **Authentication** option, specify the login and password to use, which must be the same as those specified for the replication administrative user schema.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="875d6-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="875d6-117">See Also</span></span>  
 [<span data-ttu-id="875d6-118">Oracle 發行相關術語字彙</span><span class="sxs-lookup"><span data-stu-id="875d6-118">Glossary of Terms for Oracle Publishing</span></span>](non-sql/glossary-of-terms-for-oracle-publishing.md)  
  
  
