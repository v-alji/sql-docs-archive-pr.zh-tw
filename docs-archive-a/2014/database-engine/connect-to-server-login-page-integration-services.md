---
title: 連接到伺服器 (登入頁面) Integration Services | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.connecttodtsserver.login.f1
- sql12.swb.connecttodts.login.f1
ms.assetid: 402c2de4-f4ea-40b0-909f-3ddf3bd59950
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 285518f4a1f3d9180d2c3c07a41bf75a00ea3593
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707818"
---
# <a name="connect-to-server-login-page-integration-services"></a><span data-ttu-id="b242a-102">連接到伺服器 (登入頁面) Integration Services</span><span class="sxs-lookup"><span data-stu-id="b242a-102">Connect to Server (Login Page) Integration Services</span></span>
  <span data-ttu-id="b242a-103">連接到時，使用此索引標籤來查看或指定下列選項 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="b242a-103">Use this tab to view or specify the following options when connecting to [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].</span></span>  
  
## <a name="options"></a><span data-ttu-id="b242a-104">選項。</span><span class="sxs-lookup"><span data-stu-id="b242a-104">Options</span></span>  
 <span data-ttu-id="b242a-105">**伺服器類型**</span><span class="sxs-lookup"><span data-stu-id="b242a-105">**Server type**</span></span>  
 <span data-ttu-id="b242a-106">從 [物件總管] 註冊伺服器時，選取要連接的伺服器類型： [!INCLUDE[ssDE](../includes/ssde-md.md)]、Analysis Services、Reporting Services 或 Integration Services。</span><span class="sxs-lookup"><span data-stu-id="b242a-106">When registering a server from Object Explorer, select the type of server to connect to: [!INCLUDE[ssDE](../includes/ssde-md.md)], Analysis Services, Reporting Services, or Integration Services.</span></span> <span data-ttu-id="b242a-107">對話方塊的其他部分僅會顯示適用於所選取伺服器類型的選項。</span><span class="sxs-lookup"><span data-stu-id="b242a-107">The rest of the dialog shows only the options that apply to the selected server type.</span></span> <span data-ttu-id="b242a-108">從 [已註冊的伺服器] 註冊伺服器時，[伺服器類型]  方塊是唯讀的，且會與 [已註冊的伺服器] 元件中所顯示的伺服器類型相符。</span><span class="sxs-lookup"><span data-stu-id="b242a-108">When registering a server from Registered Servers, the **Server type** box is read-only, and matches the type of server displayed in the Registered Servers component.</span></span> <span data-ttu-id="b242a-109">若要註冊不同類型的伺服器，請先從 [已註冊的伺服器] 工具列中選取 [[!INCLUDE[ssDE](../includes/ssde-md.md)]]、[Analysis Services]、[Reporting Services] 或 [Integration Services]，再開始註冊新的伺服器。</span><span class="sxs-lookup"><span data-stu-id="b242a-109">To register a different type of server, select [!INCLUDE[ssDE](../includes/ssde-md.md)], Analysis Services, Reporting Services, or Integration Services from the Registered Servers toolbar before starting to register a new server.</span></span>  
  
 <span data-ttu-id="b242a-110">**伺服器名稱**</span><span class="sxs-lookup"><span data-stu-id="b242a-110">**Server name**</span></span>  
 <span data-ttu-id="b242a-111">選取要連接的伺服器。</span><span class="sxs-lookup"><span data-stu-id="b242a-111">Select the server to connect to.</span></span> <span data-ttu-id="b242a-112">預設會顯示上次連接的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="b242a-112">The server instance last connected to is displayed by default.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b242a-113">請勿使用 *\<servername>* \\ *\<instancename>* ，因為不 [!INCLUDE[ssIS](../includes/ssis-md.md)] 支援在電腦上有多個實例。</span><span class="sxs-lookup"><span data-stu-id="b242a-113">Do not use *\<servername>*\\*\<instancename>*, because [!INCLUDE[ssIS](../includes/ssis-md.md)] does not support multiple instances on a computer.</span></span>  
  
 <span data-ttu-id="b242a-114">**驗證**</span><span class="sxs-lookup"><span data-stu-id="b242a-114">**Authentication**</span></span>  
 <span data-ttu-id="b242a-115">[!INCLUDE[msCoName](../includes/msconame-md.md)] 僅有 [!INCLUDE[ssIS](../includes/ssis-md.md)]Windows 驗證可用。</span><span class="sxs-lookup"><span data-stu-id="b242a-115">Only [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows Authentication is available for [!INCLUDE[ssIS](../includes/ssis-md.md)].</span></span> <span data-ttu-id="b242a-116">Windows 驗證模式允許使用者透過 Windows 使用者帳戶連接。</span><span class="sxs-lookup"><span data-stu-id="b242a-116">Windows Authentication mode allows a user to connect through a Windows user account.</span></span>  
  
 <span data-ttu-id="b242a-117">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="b242a-117">**User name**</span></span>  
 <span data-ttu-id="b242a-118">無法使用此選項，因為 [!INCLUDE[ssIS](../includes/ssis-md.md)]僅有 Windows 驗證可用。</span><span class="sxs-lookup"><span data-stu-id="b242a-118">This option is not available because only Windows Authentication is available for [!INCLUDE[ssIS](../includes/ssis-md.md)].</span></span>  
  
 <span data-ttu-id="b242a-119">**密碼**</span><span class="sxs-lookup"><span data-stu-id="b242a-119">**Password**</span></span>  
 <span data-ttu-id="b242a-120">無法使用此選項，因為 [!INCLUDE[ssIS](../includes/ssis-md.md)]僅有 Windows 驗證可用。</span><span class="sxs-lookup"><span data-stu-id="b242a-120">This option is not available because only Windows Authentication is available for [!INCLUDE[ssIS](../includes/ssis-md.md)].</span></span>  
  
 <span data-ttu-id="b242a-121">**記住密碼**</span><span class="sxs-lookup"><span data-stu-id="b242a-121">**Remember password**</span></span>  
 <span data-ttu-id="b242a-122">無法使用此選項，因為 [!INCLUDE[ssIS](../includes/ssis-md.md)]僅有 Windows 驗證可用。</span><span class="sxs-lookup"><span data-stu-id="b242a-122">This option is not available because only Windows Authentication is available for [!INCLUDE[ssIS](../includes/ssis-md.md)].</span></span>  
  
 <span data-ttu-id="b242a-123">**[連接]**</span><span class="sxs-lookup"><span data-stu-id="b242a-123">**Connect**</span></span>  
 <span data-ttu-id="b242a-124">連接到上列所選的伺服器。</span><span class="sxs-lookup"><span data-stu-id="b242a-124">Connect to the server selected above.</span></span>  
  
 <span data-ttu-id="b242a-125">**選項**</span><span class="sxs-lookup"><span data-stu-id="b242a-125">**Options**</span></span>  
 <span data-ttu-id="b242a-126">按一下即可變更對話方塊，並隱藏其他伺服器連接選項，例如記住密碼。</span><span class="sxs-lookup"><span data-stu-id="b242a-126">Click to change the dialog and hide the additional server connection options, such as remembering the password.</span></span>  
  
  
