---
title: 判斷是否已安裝及啟動資料庫引擎 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- SQL Server, determining if installed
- verifying Database Engine installation
- viewing Database Engine installation
- installed Database Engine verification [SQL Server]
ms.assetid: babb02e4-3521-4b75-b5df-e09205594375
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 0a912cf4a89f208543605cc84f480b63955214ab
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707854"
---
# <a name="determine-whether-the-database-engine-is-installed-and-started"></a><span data-ttu-id="017cf-102">判斷是否已安裝及啟動 Database Engine</span><span class="sxs-lookup"><span data-stu-id="017cf-102">Determine Whether the Database Engine Is Installed and Started</span></span>
  <span data-ttu-id="017cf-103">只要成功安裝 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] ，就會將檔案安裝至檔案系統、在登錄中建立項目並安裝許多工具。</span><span class="sxs-lookup"><span data-stu-id="017cf-103">A successful installation of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] installs files to the file system, creates entries in the registry, and installs several tools.</span></span> <span data-ttu-id="017cf-104">此主題描述如何使用 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 組態管理員，在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中確認 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 是否已安裝並啟動。</span><span class="sxs-lookup"><span data-stu-id="017cf-104">This topic describes how to determine whether the [!INCLUDE[ssDE](../../includes/ssde-md.md)] is installed and started in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager.</span></span>  
  
##  <a name="using-sql-server-configuration-manager"></a><a name="SSMSProcedure"></a> <span data-ttu-id="017cf-105">使用 SQL Server 組態管理員</span><span class="sxs-lookup"><span data-stu-id="017cf-105">Using SQL Server Configuration Manager</span></span>  
  
#### <a name="how-to-view-and-start-the-database-engine-by-using-sql-server-configuration-manager"></a><span data-ttu-id="017cf-106">如何使用 SQL Server 組態管理員來檢視並啟動 Database Engine</span><span class="sxs-lookup"><span data-stu-id="017cf-106">How to view and start the Database Engine by using SQL Server Configuration Manager</span></span>  
  
1.  <span data-ttu-id="017cf-107">按一下 [開始]，依序指向 [所有程式]、[Microsoft SQL Server] 和 [組態工具]，然後按一下 [SQL Server 組態管理員]。</span><span class="sxs-lookup"><span data-stu-id="017cf-107">Click **Start**, point to **All Programs**, point to **Microsoft SQL Server**, point to **Configuration Tools**, and then click **SQL Server Configuration Manager**.</span></span>  
  
     <span data-ttu-id="017cf-108">如果您在 [開始] 功能表上找不到這些項目，就表示未正確安裝 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="017cf-108">If you do not have these entries on the **Start** menu, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is not correctly installed.</span></span> <span data-ttu-id="017cf-109">請執行安裝程式來安裝 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="017cf-109">Run Setup to install the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].</span></span>  
  
2.  <span data-ttu-id="017cf-110">在 [SQL Server 組態管理員] 中，按一下左窗格中的 [SQL Server 服務]。</span><span class="sxs-lookup"><span data-stu-id="017cf-110">In **SQL Server Configuration Manager**, on the left pane, click **SQL Server Services**.</span></span> <span data-ttu-id="017cf-111">右窗格會列出與 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 相關的許多服務。</span><span class="sxs-lookup"><span data-stu-id="017cf-111">The right pane lists several services that are related to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="017cf-112">若已安裝 [!INCLUDE[ssDE](../../includes/ssde-md.md)]，[!INCLUDE[ssDE](../../includes/ssde-md.md)] 服務就會列為 [SQL Server (MSSQLSERVER)] (如果其為預設執行個體的話) 或 [SQL Server (\<*instance_name*>)]  (如果 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 是安裝為具名執行個體的話)。</span><span class="sxs-lookup"><span data-stu-id="017cf-112">If the [!INCLUDE[ssDE](../../includes/ssde-md.md)] is installed, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] service is listed as **SQL Server (MSSQLSERVER)** if it is the default instance; or **SQL Server (**\<*instance_name*>**)**, if the [!INCLUDE[ssDE](../../includes/ssde-md.md)] is installed as a named instance.</span></span> <span data-ttu-id="017cf-113">除非執行個體名稱已變更，否則 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] 會安裝為 **SQLEXPRESS** 名稱的具名執行個體。</span><span class="sxs-lookup"><span data-stu-id="017cf-113">Unless the instance name is changed, [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] installs as a named instance with the name **SQLEXPRESS**.</span></span> <span data-ttu-id="017cf-114">綠色的三角形圖示是表示 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 正在執行。</span><span class="sxs-lookup"><span data-stu-id="017cf-114">A green triangle icon indicates that the [!INCLUDE[ssDE](../../includes/ssde-md.md)] is running.</span></span> <span data-ttu-id="017cf-115">紅色的正方形圖示則表示 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 已停止。</span><span class="sxs-lookup"><span data-stu-id="017cf-115">A red square icon indicates that the [!INCLUDE[ssDE](../../includes/ssde-md.md)] is stopped.</span></span>  
  
3.  <span data-ttu-id="017cf-116">若要啟動 [!INCLUDE[ssDE](../../includes/ssde-md.md)]，請以滑鼠右鍵按一下右窗格中的 [!INCLUDE[ssDE](../../includes/ssde-md.md)]，然後按一下 [啟動]。</span><span class="sxs-lookup"><span data-stu-id="017cf-116">To start the [!INCLUDE[ssDE](../../includes/ssde-md.md)], in the right pane, right-click the [!INCLUDE[ssDE](../../includes/ssde-md.md)], and then click **Start**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="017cf-117">在安裝過程中，使用者可以選取要用來安裝程式檔案和資料庫檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="017cf-117">During setup, the user can select a location in which to install the program files and the database files.</span></span> <span data-ttu-id="017cf-118">如果使用者接受預設位置，這些檔案就會安裝至 [!INCLUDE[ssInstallPath](../../includes/ssinstallpath-md.md)] 和 C:\Program Files\Microsoft SQL Server\MSSQL.*x*，其中 *x* 是數字。</span><span class="sxs-lookup"><span data-stu-id="017cf-118">If the user accepts the default location, the files are installed to [!INCLUDE[ssInstallPath](../../includes/ssinstallpath-md.md)] and C:\Program Files\Microsoft SQL Server\MSSQL.*x*, where *x* is a number.</span></span>  
  
  
