---
title: 連接到伺服器 (Integration Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.connection.login.dtsserver.f1
ms.assetid: 5be897bd-f36c-4c6a-a91a-13d0d016f8b6
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 8821018c45fdd77c4b3b896afc47b8f5b425af88
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707822"
---
# <a name="connect-to-server-integration-services"></a><span data-ttu-id="87236-102">連線到伺服器 (Integration Services)</span><span class="sxs-lookup"><span data-stu-id="87236-102">Connect to Server (Integration Services)</span></span>
  <span data-ttu-id="87236-103">連接到 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 時，使用此對話方塊來檢視或指定選項。</span><span class="sxs-lookup"><span data-stu-id="87236-103">Use this dialog to view or specify options when connecting to [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].</span></span>  
  
## <a name="options"></a><span data-ttu-id="87236-104">選項。</span><span class="sxs-lookup"><span data-stu-id="87236-104">Options</span></span>  
 <span data-ttu-id="87236-105">**伺服器類型**</span><span class="sxs-lookup"><span data-stu-id="87236-105">**Server type**</span></span>  
 <span data-ttu-id="87236-106">從 [物件總管] 註冊伺服器時，選取要連接的伺服器類型： [!INCLUDE[ssDE](../includes/ssde-md.md)]、Analysis Services、Reporting Services 或 Integration Services。</span><span class="sxs-lookup"><span data-stu-id="87236-106">When registering a server from Object Explorer, select the type of server to connect to: [!INCLUDE[ssDE](../includes/ssde-md.md)], Analysis Services, Reporting Services, or Integration Services.</span></span> <span data-ttu-id="87236-107">對話方塊的其他部分僅會顯示適用於所選取伺服器類型的選項。</span><span class="sxs-lookup"><span data-stu-id="87236-107">The rest of the dialog shows only the options that apply to the selected server type.</span></span> <span data-ttu-id="87236-108">從 [已註冊的伺服器] 註冊伺服器時，[伺服器類型] 方塊是唯讀的，且會與 [已註冊的伺服器] 元件中所顯示的伺服器類型相符。</span><span class="sxs-lookup"><span data-stu-id="87236-108">When registering a server from Registered Servers, the Server type box is read-only, and matches the type of server displayed in the Registered Servers component.</span></span> <span data-ttu-id="87236-109">若要註冊不同類型的伺服器，請先從 [已註冊的伺服器] 工具列中選取 [[!INCLUDE[ssDE](../includes/ssde-md.md)]]、[Analysis Services]、[Reporting Services] 或 [Integration Services]，再開始註冊新的伺服器。</span><span class="sxs-lookup"><span data-stu-id="87236-109">To register a different type of server, select [!INCLUDE[ssDE](../includes/ssde-md.md)], Analysis Services, Reporting Services, or Integration Services from the Registered Servers toolbar before starting to register a new server.</span></span>  
  
 <span data-ttu-id="87236-110">**伺服器名稱**</span><span class="sxs-lookup"><span data-stu-id="87236-110">**Server name**</span></span>  
 <span data-ttu-id="87236-111">選取要連接的伺服器。</span><span class="sxs-lookup"><span data-stu-id="87236-111">Select the server to connect to.</span></span> <span data-ttu-id="87236-112">預設會顯示上次連接的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="87236-112">The server instance last connected to is displayed by default.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="87236-113">請勿使用 *\<servername>* \\ *\<instancename>* ，因為不 [!INCLUDE[ssIS](../includes/ssis-md.md)] 支援在電腦上有多個實例。</span><span class="sxs-lookup"><span data-stu-id="87236-113">Do not use *\<servername>*\\*\<instancename>*, because [!INCLUDE[ssIS](../includes/ssis-md.md)] does not support multiple instances on a computer.</span></span>  
  
 <span data-ttu-id="87236-114">**驗證**</span><span class="sxs-lookup"><span data-stu-id="87236-114">**Authentication**</span></span>  
 <span data-ttu-id="87236-115">[!INCLUDE[msCoName](../includes/msconame-md.md)] 僅有 [!INCLUDE[ssIS](../includes/ssis-md.md)]Windows 驗證可用。</span><span class="sxs-lookup"><span data-stu-id="87236-115">Only [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows Authentication is available for [!INCLUDE[ssIS](../includes/ssis-md.md)].</span></span> <span data-ttu-id="87236-116">Windows 驗證模式允許使用者透過 Windows 使用者帳戶連接。</span><span class="sxs-lookup"><span data-stu-id="87236-116">Windows Authentication mode allows a user to connect through a Windows user account.</span></span>  
  
 <span data-ttu-id="87236-117">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="87236-117">**User name**</span></span>  
 <span data-ttu-id="87236-118">無法使用此選項，因為 [!INCLUDE[ssIS](../includes/ssis-md.md)]僅有 Windows 驗證可用。</span><span class="sxs-lookup"><span data-stu-id="87236-118">This option is not available because only Windows Authentication is available for [!INCLUDE[ssIS](../includes/ssis-md.md)].</span></span>  
  
 <span data-ttu-id="87236-119">**密碼**</span><span class="sxs-lookup"><span data-stu-id="87236-119">**Password**</span></span>  
 <span data-ttu-id="87236-120">無法使用此選項，因為 [!INCLUDE[ssIS](../includes/ssis-md.md)]僅有 Windows 驗證可用。</span><span class="sxs-lookup"><span data-stu-id="87236-120">This option is not available because only Windows Authentication is available for [!INCLUDE[ssIS](../includes/ssis-md.md)].</span></span>  
  
 <span data-ttu-id="87236-121">**[連接]**</span><span class="sxs-lookup"><span data-stu-id="87236-121">**Connect**</span></span>  
 <span data-ttu-id="87236-122">按一下即可連接到上列所選的伺服器。</span><span class="sxs-lookup"><span data-stu-id="87236-122">Click to connect to the server selected above.</span></span>  
  
 <span data-ttu-id="87236-123">**選項**</span><span class="sxs-lookup"><span data-stu-id="87236-123">**Options**</span></span>  
 <span data-ttu-id="87236-124">按一下即可顯示其他伺服器連接選項，例如，註冊伺服器與記住密碼。</span><span class="sxs-lookup"><span data-stu-id="87236-124">Click to display additional server connection options, such as registering a server and remembering the password.</span></span>  
  
  
