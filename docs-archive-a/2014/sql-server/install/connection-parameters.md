---
title: 連接參數 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Upgrade Advisor [SQL Server], connections
- authentication [Upgrade Advisor]
- SQL Server Upgrade Advisor, connections
- connections [Upgrade Advisor]
- server instances [Upgrade Advisor]
- default server instances
- analyzing system [Upgrade Advisor], connections
ms.assetid: f754d038-637a-4d8e-85b0-b242e6499d26
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 27eb69dfd2c41710a47861e0992486267f692a3a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593785"
---
# <a name="connection-parameters"></a><span data-ttu-id="40fbb-102">連線參數</span><span class="sxs-lookup"><span data-stu-id="40fbb-102">Connection Parameters</span></span>
  <span data-ttu-id="40fbb-103">若要分析特定伺服器類型 (例如 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)])，您必須選取 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的特定執行個體。</span><span class="sxs-lookup"><span data-stu-id="40fbb-103">To analyze certain server types, such as the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], you must select a specific instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="40fbb-104">系統會自動選取 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的預設執行個體。</span><span class="sxs-lookup"><span data-stu-id="40fbb-104">The default instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is automatically selected.</span></span> <span data-ttu-id="40fbb-105">您可以變更此選擇，但一次只能選取一個執行個體供 Upgrade Advisor 分析。</span><span class="sxs-lookup"><span data-stu-id="40fbb-105">You can change this selection, but you can select only one instance at a time for analysis by Upgrade Advisor.</span></span> <span data-ttu-id="40fbb-106">如果您已加入需要驗證的伺服器類型，就必須輸入驗證模式和認證。</span><span class="sxs-lookup"><span data-stu-id="40fbb-106">If you have included a server type that requires authentication, you must enter the authentication mode and credentials.</span></span>  
  
## <a name="options"></a><span data-ttu-id="40fbb-107">選項。</span><span class="sxs-lookup"><span data-stu-id="40fbb-107">Options</span></span>  
 <span data-ttu-id="40fbb-108">**伺服器名稱**</span><span class="sxs-lookup"><span data-stu-id="40fbb-108">**Server name**</span></span>  
 <span data-ttu-id="40fbb-109">預先填入您在 [[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 元件] 窗格中輸入的電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="40fbb-109">Pre-populated with the computer name that you entered in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Components pane.</span></span>  
  
 <span data-ttu-id="40fbb-110">**執行個體名稱**</span><span class="sxs-lookup"><span data-stu-id="40fbb-110">**Instance name**</span></span>  
 <span data-ttu-id="40fbb-111">從電腦上可用的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體中選取。</span><span class="sxs-lookup"><span data-stu-id="40fbb-111">Select from the instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that are available on the computer.</span></span> <span data-ttu-id="40fbb-112">如果您沒有看見執行個體的清單，請使用 MSSQLSERVER 來掃描預設執行個體。</span><span class="sxs-lookup"><span data-stu-id="40fbb-112">If you do not see a list of instances, use MSSQLSERVER to scan the default instance.</span></span> <span data-ttu-id="40fbb-113">這與遠端電腦尤其有關。</span><span class="sxs-lookup"><span data-stu-id="40fbb-113">This is especially relevant for remote computers.</span></span> <span data-ttu-id="40fbb-114">此外，您也可以使用 "default" 一詞來掃描預設執行個體。</span><span class="sxs-lookup"><span data-stu-id="40fbb-114">You can also use the word "default" to scan the default instance.</span></span>  
  
 <span data-ttu-id="40fbb-115">**驗證**</span><span class="sxs-lookup"><span data-stu-id="40fbb-115">**Authentication**</span></span>  
 <span data-ttu-id="40fbb-116">從這部電腦上可用的驗證模式清單中選取。</span><span class="sxs-lookup"><span data-stu-id="40fbb-116">Select from the list of available authentication modes on this computer.</span></span> <span data-ttu-id="40fbb-117">根據預設，驗證模式是 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="40fbb-117">By default, the authentication mode is Windows Authentication.</span></span>  
  
 <span data-ttu-id="40fbb-118">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="40fbb-118">**User name**</span></span>  
 <span data-ttu-id="40fbb-119">如果您要使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證，請在此方塊中輸入使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="40fbb-119">If using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication, enter a user name in the box.</span></span> <span data-ttu-id="40fbb-120">我們建議使用者名稱擁有這部電腦的管理認證。</span><span class="sxs-lookup"><span data-stu-id="40fbb-120">We recommend that the user name have administrative credentials on the computer.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="40fbb-121">如果您選取 [Windows 驗證]，則會在 [**使用者名稱**] 文字方塊中填入目前登入之使用者的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="40fbb-121">If you select Windows Authentication, the user name of the currently logged-on user is populated in the **User name** text box.</span></span>  
  
 <span data-ttu-id="40fbb-122">**密碼**</span><span class="sxs-lookup"><span data-stu-id="40fbb-122">**Password**</span></span>  
 <span data-ttu-id="40fbb-123">請輸入指定之使用者的密碼。</span><span class="sxs-lookup"><span data-stu-id="40fbb-123">Enter the password for the specified user.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40fbb-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="40fbb-124">See Also</span></span>  
 <span data-ttu-id="40fbb-125">[使用 Upgrade Advisor](../../../2014/sql-server/install/working-with-upgrade-advisor.md) </span><span class="sxs-lookup"><span data-stu-id="40fbb-125">[Working with Upgrade Advisor](../../../2014/sql-server/install/working-with-upgrade-advisor.md) </span></span>  
 [<span data-ttu-id="40fbb-126">Upgrade Advisor 使用者介面參考</span><span class="sxs-lookup"><span data-stu-id="40fbb-126">Upgrade Advisor User Interface Reference</span></span>](../../../2014/sql-server/install/upgrade-advisor-user-interface-reference.md)  
  
  
