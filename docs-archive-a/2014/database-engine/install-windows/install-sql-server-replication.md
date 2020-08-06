---
title: 安裝 SQL Server 複寫 | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- components [SQL Server replication]
- command line installations [SQL Server replication]
- installing replication
- replication [SQL Server], installing
- command prompt [SQL Server replication]
ms.assetid: c50ad078-060b-4a8d-ad45-9e31a8d85729
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ba941fda1d463e7bb4a26bd2fbb45d2a82ca27b3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688162"
---
# <a name="install-sql-server-replication"></a><span data-ttu-id="d85a6-102">安裝 SQL Server 複寫</span><span class="sxs-lookup"><span data-stu-id="d85a6-102">Install SQL Server Replication</span></span>
  <span data-ttu-id="d85a6-103">您可以使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝精靈或命令提示字元來安裝複寫元件。</span><span class="sxs-lookup"><span data-stu-id="d85a6-103">Replication components can be installed by using the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Installation Wizard or at a command prompt.</span></span> <span data-ttu-id="d85a6-104">請在安裝 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]或修改現有的執行個體時安裝複寫。</span><span class="sxs-lookup"><span data-stu-id="d85a6-104">Install replication when you install [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], or when you modify an existing instance.</span></span>  
  
 <span data-ttu-id="d85a6-105">安裝複寫元件之後，您必須先設定伺服器，才能使用複寫。</span><span class="sxs-lookup"><span data-stu-id="d85a6-105">After replication components are installed, you must configure the server before you can use replication.</span></span> <span data-ttu-id="d85a6-106">如需詳細資訊，請參閱《 [線上叢書》的](../../relational-databases/replication/configure-distribution.md) 設定散發 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="d85a6-106">For more information, see [Configure Distribution](../../relational-databases/replication/configure-distribution.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="d85a6-107">如果在修改現有的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體時安裝複寫元件，則必須在安裝完成之後停止並重新啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent。</span><span class="sxs-lookup"><span data-stu-id="d85a6-107">If you install replication components when you modify an existing instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you must stop and restart [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent after the installation is completed.</span></span> <span data-ttu-id="d85a6-108">這個動作有助於確保 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 能夠辨識複寫代理程式子系統，而且可以從作業步驟呼叫複寫代理程式。</span><span class="sxs-lookup"><span data-stu-id="d85a6-108">This action helps ensure that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent recognizes the replication agent subsystems and can call replication agents from job steps.</span></span>  
  
## <a name="installing-replication-by-using-setup"></a><span data-ttu-id="d85a6-109">使用安裝程式安裝複寫</span><span class="sxs-lookup"><span data-stu-id="d85a6-109">Installing Replication by Using Setup</span></span>  
 <span data-ttu-id="d85a6-110">**在安裝新執行個體時安裝複寫 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**</span><span class="sxs-lookup"><span data-stu-id="d85a6-110">**To install replication when installing a new instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**</span></span>  
  
-   <span data-ttu-id="d85a6-111">若要安裝複寫元件 (包括 Replication Management Objects (RMO))，請在安裝精靈的 [特徵選取] 頁面上選取 [SQL Server 複寫]。</span><span class="sxs-lookup"><span data-stu-id="d85a6-111">To install replication components, including Replication Management Objects (RMO), select **SQL Server Replication** on the **Feature Selection** page of the Installation Wizard.</span></span>  
  
## <a name="installing-replication-from-the-command-prompt"></a><span data-ttu-id="d85a6-112">從命令提示字元安裝複寫</span><span class="sxs-lookup"><span data-stu-id="d85a6-112">Installing Replication from the Command Prompt</span></span>  
 <span data-ttu-id="d85a6-113">**在安裝新執行個體時安裝複寫 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**</span><span class="sxs-lookup"><span data-stu-id="d85a6-113">**To install replication when installing a new instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**</span></span>  
  
-   <span data-ttu-id="d85a6-114">請參閱[從命令提示字元安裝 SQL Server 2014](install-sql-server-from-the-command-prompt.md)。</span><span class="sxs-lookup"><span data-stu-id="d85a6-114">See [Install SQL Server 2014 from the Command Prompt](install-sql-server-from-the-command-prompt.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d85a6-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d85a6-115">See Also</span></span>  
 <span data-ttu-id="d85a6-116">[安裝 SQL Server 2014](install-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="d85a6-116">[Install SQL Server 2014](install-sql-server.md) </span></span>  
 <span data-ttu-id="d85a6-117">[從命令提示字元安裝 SQL Server 2014](install-sql-server-from-the-command-prompt.md) </span><span class="sxs-lookup"><span data-stu-id="d85a6-117">[Install SQL Server 2014 from the Command Prompt](install-sql-server-from-the-command-prompt.md) </span></span>  
 [<span data-ttu-id="d85a6-118">SQL Server 2014 各版本所支援的功能</span><span class="sxs-lookup"><span data-stu-id="d85a6-118">Features Supported by the Editions of SQL Server 2014</span></span>](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)  
  
  
