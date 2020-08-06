---
title: SQL Server Compact Edition 連線管理員 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Compact, connection manager
- connections [Integration Services], SQL Server Compact
- connection managers [Integration Services], SQL Server Compact
ms.assetid: ba627d4d-41f4-49fc-a921-f534cde67770
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5d4feb001cc7c0fd0bd8b6e60d5ab22b33ad2eb9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708546"
---
# <a name="sql-server-compact-edition-connection-manager"></a><span data-ttu-id="2de4a-102">SQL Server Compact Edition 連接管理員</span><span class="sxs-lookup"><span data-stu-id="2de4a-102">SQL Server Compact Edition Connection Manager</span></span>
  <span data-ttu-id="2de4a-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact 連線管理員可讓封裝連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact 資料庫。</span><span class="sxs-lookup"><span data-stu-id="2de4a-103">A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact connection manager enables a package to connect to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact database.</span></span> <span data-ttu-id="2de4a-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 包含的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Compact 目的地使用此連線管理員將資料載入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact 資料庫中的資料表。</span><span class="sxs-lookup"><span data-stu-id="2de4a-104">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact destination that [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] includes uses this connection manager to load data into a table in a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact database.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2de4a-105">在 64 位元電腦上，您必須以 32 位元模式執行連接至 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact 資料來源的封裝。</span><span class="sxs-lookup"><span data-stu-id="2de4a-105">On a 64-bit computer, you must run packages that connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact data sources in 32-bit mode.</span></span> <span data-ttu-id="2de4a-106">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 用來連接到 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Compact 資料來源的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact 提供者只有提供 32 位元版本。</span><span class="sxs-lookup"><span data-stu-id="2de4a-106">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact provider that [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] uses to connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact data sources is available only in a 32-bit version.</span></span>  
  
## <a name="configuration-the-sql-server-compact-edition-connection-manager"></a><span data-ttu-id="2de4a-107">SQL Server Compact Edition 連接管理員的組態</span><span class="sxs-lookup"><span data-stu-id="2de4a-107">Configuration the SQL Server Compact Edition Connection Manager</span></span>  
 <span data-ttu-id="2de4a-108">當您將 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact 連線管理員加入封裝時， [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 會建立在執行時間解析為 Compact 連接的連線管理員 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、設定連線管理員屬性，並將連線管理員加入 `Connections` 封裝上的集合。</span><span class="sxs-lookup"><span data-stu-id="2de4a-108">When you add a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact connection manager to a package, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] creates a connection manager that will resolve to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact connection at run time, sets the connection manager properties, and adds the connection manager to the `Connections` collection on the package.</span></span>  
  
 <span data-ttu-id="2de4a-109">連接管理員的 `ConnectionManagerType` 屬性會設為 `SQLMOBILE`。</span><span class="sxs-lookup"><span data-stu-id="2de4a-109">The `ConnectionManagerType` property of the connection manager is set to `SQLMOBILE`.</span></span>  
  
 <span data-ttu-id="2de4a-110">您可以利用下列方式設定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact 連線管理員：</span><span class="sxs-lookup"><span data-stu-id="2de4a-110">You can configure the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact connection manager in the following ways:</span></span>  
  
-   <span data-ttu-id="2de4a-111">提供指定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact 資料庫位置的連接字串。</span><span class="sxs-lookup"><span data-stu-id="2de4a-111">Provide a connection string that specifies the location of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact database.</span></span>  
  
-   <span data-ttu-id="2de4a-112">提供有密碼保護之資料庫的密碼。</span><span class="sxs-lookup"><span data-stu-id="2de4a-112">Provide a password for a password-protected database.</span></span>  
  
-   <span data-ttu-id="2de4a-113">指定儲存資料庫的伺服器。</span><span class="sxs-lookup"><span data-stu-id="2de4a-113">Specify the server on which the database is stored.</span></span>  
  
-   <span data-ttu-id="2de4a-114">指示是否在執行階段保留從連接管理員建立的連接。</span><span class="sxs-lookup"><span data-stu-id="2de4a-114">Indicate whether the connection that is created from the connection manager is retained at run time.</span></span>  
  
 <span data-ttu-id="2de4a-115">您可以透過 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師或以程式設計方式設定屬性。</span><span class="sxs-lookup"><span data-stu-id="2de4a-115">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="2de4a-116">如需有關可以在「 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師」中設定之屬性的詳細資訊，請按下列其中一個主題：</span><span class="sxs-lookup"><span data-stu-id="2de4a-116">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="2de4a-117">SQL Server Compact Edition 連線管理員編輯器 &#40;連接頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="2de4a-117">SQL Server Compact Edition Connection Manager Editor &#40;Connection Page&#41;</span></span>](../sql-server-compact-edition-connection-manager-editor-connection-page.md)  
  
-   [<span data-ttu-id="2de4a-118">SQL Server Compact Edition 連線管理員編輯器 &#40;全部頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="2de4a-118">SQL Server Compact Edition Connection Manager Editor &#40;All Page&#41;</span></span>](../sql-server-compact-edition-connection-manager-editor-all-page.md)  
  
 <span data-ttu-id="2de4a-119">如需以程式設計方式設定連線管理員的資訊，請參閱 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 和 [以程式設計方式加入連接](../building-packages-programmatically/adding-connections-programmatically.md)。</span><span class="sxs-lookup"><span data-stu-id="2de4a-119">For information about configuring a connection manager programmatically, see <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> and [Adding Connections Programmatically](../building-packages-programmatically/adding-connections-programmatically.md).</span></span>  
  
  
