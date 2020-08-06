---
title: 連接到伺服器 (Analysis Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.connection.login.analysisserver.f1
ms.assetid: 7e277d22-8d4b-422e-8882-7c5dd7a6d915
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: b3530f38534e09ef19e77293880129274dfc211b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686477"
---
# <a name="connect-to-server-analysis-services"></a><span data-ttu-id="2eee7-102">連接到伺服器 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="2eee7-102">Connect to Server (Analysis Services)</span></span>
  <span data-ttu-id="2eee7-103">連接到 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 時，使用此對話方塊來檢視或指定選項。</span><span class="sxs-lookup"><span data-stu-id="2eee7-103">Use this dialog to view or specify options when connecting to [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span>  
  
## <a name="options"></a><span data-ttu-id="2eee7-104">選項。</span><span class="sxs-lookup"><span data-stu-id="2eee7-104">Options</span></span>  
 <span data-ttu-id="2eee7-105">**伺服器類型**</span><span class="sxs-lookup"><span data-stu-id="2eee7-105">**Server type**</span></span>  
 <span data-ttu-id="2eee7-106">從 [物件總管] 註冊伺服器時，選取要連接的伺服器類型： [!INCLUDE[ssDE](../includes/ssde-md.md)]、Analysis Services、Reporting Services 或 Integration Services。</span><span class="sxs-lookup"><span data-stu-id="2eee7-106">When registering a server from Object Explorer, select the type of server to connect to: [!INCLUDE[ssDE](../includes/ssde-md.md)], Analysis Services, Reporting Services, or Integration Services.</span></span> <span data-ttu-id="2eee7-107">對話方塊的其他部分僅會顯示適用於所選取伺服器類型的選項。</span><span class="sxs-lookup"><span data-stu-id="2eee7-107">The rest of the dialog shows only the options that apply to the selected server type.</span></span> <span data-ttu-id="2eee7-108">從 [已註冊的伺服器] 註冊伺服器時，[伺服器類型]  方塊是唯讀的，且會與 [已註冊的伺服器] 元件中所顯示的伺服器類型相符。</span><span class="sxs-lookup"><span data-stu-id="2eee7-108">When registering a server from Registered Servers, the **Server type** box is read-only, and matches the type of server displayed in the Registered Servers component.</span></span> <span data-ttu-id="2eee7-109">若要註冊不同類型的伺服器，請先從 [已註冊的伺服器] 工具列中選取 [[!INCLUDE[ssDE](../includes/ssde-md.md)]]、[Analysis Services]、[Reporting Services] 或 [Integration Services]，再開始註冊新的伺服器。</span><span class="sxs-lookup"><span data-stu-id="2eee7-109">To register a different type of server, select [!INCLUDE[ssDE](../includes/ssde-md.md)], Analysis Services, Reporting Services, or Integration Services from the Registered Servers toolbar before starting to register a new server.</span></span>  
  
 <span data-ttu-id="2eee7-110">**伺服器名稱**</span><span class="sxs-lookup"><span data-stu-id="2eee7-110">**Server name**</span></span>  
 <span data-ttu-id="2eee7-111">選取要連接的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="2eee7-111">Select the server instance to connect to.</span></span> <span data-ttu-id="2eee7-112">預設會顯示上次連接的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="2eee7-112">The server instance last connected to is displayed by default.</span></span>  
  
 <span data-ttu-id="2eee7-113">**驗證**</span><span class="sxs-lookup"><span data-stu-id="2eee7-113">**Authentication**</span></span>  
 <span data-ttu-id="2eee7-114">當連接到 Analysis Services 的執行個體時，支援下列驗證模式： [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="2eee7-114">The following authentication modes are supported when connecting to an instance of Analysis Services: [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows Authentication.</span></span>  
  
 <span data-ttu-id="2eee7-115">**Windows 驗證模式 (Windows 驗證)**</span><span class="sxs-lookup"><span data-stu-id="2eee7-115">**Windows Authentication Mode (Windows Authentication)**</span></span>  
 <span data-ttu-id="2eee7-116">**Windows 驗證**模式允許使用者透過 windows 使用者帳戶連接。</span><span class="sxs-lookup"><span data-stu-id="2eee7-116">**Windows Authentication** mode allows a user to connect through a Windows user account.</span></span>  
  
 <span data-ttu-id="2eee7-117">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="2eee7-117">**User name**</span></span>  
 <span data-ttu-id="2eee7-118">這個選項在此版本中無法使用。</span><span class="sxs-lookup"><span data-stu-id="2eee7-118">This option is not available in this release.</span></span> <span data-ttu-id="2eee7-119">輸入要用來連接的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="2eee7-119">Enter the user name to connect with.</span></span> <span data-ttu-id="2eee7-120">只有在您選取使用 **Windows 驗證**連接時，才能使用此選項。</span><span class="sxs-lookup"><span data-stu-id="2eee7-120">This option is only available if you have selected to connect using **Windows Authentication**.</span></span>  
  
 <span data-ttu-id="2eee7-121">**密碼**</span><span class="sxs-lookup"><span data-stu-id="2eee7-121">**Password**</span></span>  
 <span data-ttu-id="2eee7-122">這個選項在此版本中無法使用。</span><span class="sxs-lookup"><span data-stu-id="2eee7-122">This option is not available in this release.</span></span> <span data-ttu-id="2eee7-123">輸入登入的密碼。</span><span class="sxs-lookup"><span data-stu-id="2eee7-123">Enter the password for the login.</span></span> <span data-ttu-id="2eee7-124">只有在您選取使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 驗證連接時，才能編輯此選項。</span><span class="sxs-lookup"><span data-stu-id="2eee7-124">This option is only editable if you have selected to connect using [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
 <span data-ttu-id="2eee7-125">**[連接]**</span><span class="sxs-lookup"><span data-stu-id="2eee7-125">**Connect**</span></span>  
 <span data-ttu-id="2eee7-126">按一下即可連接到上列所選的伺服器。</span><span class="sxs-lookup"><span data-stu-id="2eee7-126">Click to connect to the server selected above.</span></span>  
  
 <span data-ttu-id="2eee7-127">**選項**</span><span class="sxs-lookup"><span data-stu-id="2eee7-127">**Options**</span></span>  
 <span data-ttu-id="2eee7-128">按一下即可顯示其他伺服器連接選項，例如，註冊伺服器與記住密碼。</span><span class="sxs-lookup"><span data-stu-id="2eee7-128">Click to display additional server connection options, such as registering a server and remembering the password.</span></span>  
  
  
