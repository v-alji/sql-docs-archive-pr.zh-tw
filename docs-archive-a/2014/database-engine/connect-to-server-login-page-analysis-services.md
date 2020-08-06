---
title: 連接到伺服器 (登入頁面) Analysis Services | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.connecttoas.login.f1
ms.assetid: fb012bc8-5105-438a-afcc-74264ebae035
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 0cdbb890693c6f00d8515194804b96b6483cb956
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707821"
---
# <a name="connect-to-server-login-page-analysis-services"></a><span data-ttu-id="c0338-102">連接到伺服器 (登入頁面) Analysis Services</span><span class="sxs-lookup"><span data-stu-id="c0338-102">Connect to Server (Login Page) Analysis Services</span></span>
  <span data-ttu-id="c0338-103">連接到時，使用此索引標籤來查看或指定下列選項 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="c0338-103">Use this tab to view or specify the following options when connecting to [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span>  
  
## <a name="options"></a><span data-ttu-id="c0338-104">選項。</span><span class="sxs-lookup"><span data-stu-id="c0338-104">Options</span></span>  
 <span data-ttu-id="c0338-105">**伺服器類型**</span><span class="sxs-lookup"><span data-stu-id="c0338-105">**Server type**</span></span>  
 <span data-ttu-id="c0338-106">從 [物件總管] 註冊伺服器時，選取要連接的伺服器類型： [!INCLUDE[ssDE](../includes/ssde-md.md)]、Analysis Services、Reporting Services 或 Integration Services。</span><span class="sxs-lookup"><span data-stu-id="c0338-106">When registering a server from Object Explorer, select the type of server to connect to: [!INCLUDE[ssDE](../includes/ssde-md.md)], Analysis Services, Reporting Services, or Integration Services.</span></span> <span data-ttu-id="c0338-107">對話方塊的其他部分僅會顯示適用於所選取伺服器類型的選項。</span><span class="sxs-lookup"><span data-stu-id="c0338-107">The rest of the dialog shows only the options that apply to the selected server type.</span></span> <span data-ttu-id="c0338-108">從 [已註冊的伺服器] 註冊伺服器時，[伺服器類型]  方塊是唯讀的，且會與 [已註冊的伺服器] 元件中所顯示的伺服器類型相符。</span><span class="sxs-lookup"><span data-stu-id="c0338-108">When registering a server from Registered Servers, the **Server type** box is read-only, and matches the type of server displayed in the Registered Servers component.</span></span> <span data-ttu-id="c0338-109">若要註冊不同類型的伺服器，請先從 [已註冊的伺服器] 工具列中選取 [[!INCLUDE[ssDE](../includes/ssde-md.md)]]、[Analysis Services]、[Reporting Services] 或 [Integration Services]，再開始註冊新的伺服器。</span><span class="sxs-lookup"><span data-stu-id="c0338-109">To register a different type of server, select [!INCLUDE[ssDE](../includes/ssde-md.md)], Analysis Services, Reporting Services, or Integration Services from the Registered Servers toolbar before starting to register a new server.</span></span>  
  
 <span data-ttu-id="c0338-110">**伺服器名稱**</span><span class="sxs-lookup"><span data-stu-id="c0338-110">**Server name**</span></span>  
 <span data-ttu-id="c0338-111">選取要連接的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="c0338-111">Select the server instance to connect to.</span></span> <span data-ttu-id="c0338-112">預設會顯示上次連接的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="c0338-112">The server instance last connected to is displayed by default.</span></span>  
  
 <span data-ttu-id="c0338-113">**驗證**</span><span class="sxs-lookup"><span data-stu-id="c0338-113">**Authentication**</span></span>  
 <span data-ttu-id="c0338-114">當連接到 Analysis Services 的執行個體時，支援下列驗證模式： [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="c0338-114">The following authentication modes are supported when connecting to an instance of Analysis Services: [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows Authentication.</span></span>  
  
 <span data-ttu-id="c0338-115">**Windows 驗證模式 (Windows 驗證)**</span><span class="sxs-lookup"><span data-stu-id="c0338-115">**Windows Authentication Mode (Windows Authentication)**</span></span>  
 <span data-ttu-id="c0338-116">Windows 驗證模式允許使用者透過 Windows 使用者帳戶連接。</span><span class="sxs-lookup"><span data-stu-id="c0338-116">Windows Authentication mode allows a user to connect through a Windows user account.</span></span>  
  
 <span data-ttu-id="c0338-117">**[連接]**</span><span class="sxs-lookup"><span data-stu-id="c0338-117">**Connect**</span></span>  
 <span data-ttu-id="c0338-118">連接到上列所選的伺服器。</span><span class="sxs-lookup"><span data-stu-id="c0338-118">Connect to the server selected above.</span></span>  
  
 <span data-ttu-id="c0338-119">**選項**</span><span class="sxs-lookup"><span data-stu-id="c0338-119">**Options**</span></span>  
 <span data-ttu-id="c0338-120">按一下即可變更對話方塊，並隱藏其他伺服器連接選項，例如記住密碼。</span><span class="sxs-lookup"><span data-stu-id="c0338-120">Click to change the dialog and hide the additional server connection options, such as remembering the password.</span></span>  
  
  
