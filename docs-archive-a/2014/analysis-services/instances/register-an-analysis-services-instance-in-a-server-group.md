---
title: 在伺服器群組中註冊 Analysis Services 實例 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 5fd3826b-8f75-48eb-910c-bf784163e53b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 277f905e7d234ec9136ecc5b658cb4ef6675ae4c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702085"
---
# <a name="register-an-analysis-services-instance-in-a-server-group"></a><span data-ttu-id="9ce63-102">註冊伺服器群組中的 Analysis Services 執行個體</span><span class="sxs-lookup"><span data-stu-id="9ce63-102">Register an Analysis Services Instance in a Server Group</span></span>
  <span data-ttu-id="9ce63-103">如果您有大量 Analysis Services 伺服器執行個體，可以在 Management Studio 建立伺服器群組，讓伺服器管理變得更輕鬆。</span><span class="sxs-lookup"><span data-stu-id="9ce63-103">If you have a large number of Analysis Services server instances, you can create server groups in Management Studio to make server administration easier.</span></span> <span data-ttu-id="9ce63-104">伺服器群組的目的是在管理工作空間內提供一組相關伺服器之間的接近性。</span><span class="sxs-lookup"><span data-stu-id="9ce63-104">The purpose of a server group is to provide proximity among a group of related servers within the administrative workspace.</span></span> <span data-ttu-id="9ce63-105">例如，假設您負責管理十個不同的 Analysis Services 執行個體。</span><span class="sxs-lookup"><span data-stu-id="9ce63-105">For example, suppose you are tasked with managing ten separate instances of Analysis Services.</span></span> <span data-ttu-id="9ce63-106">依伺服器模式、開機時間準則，或依部門或地區的伺服器群組方式，可讓檢視及連接到共用相同特性的執行個體更輕鬆。</span><span class="sxs-lookup"><span data-stu-id="9ce63-106">Grouping them by server mode, up-time criteria, or by department or region would allow you to view and connect to instances that share the same characteristics more easily.</span></span> <span data-ttu-id="9ce63-107">您還可以加入有助於記住伺服器用法的描述性資訊。</span><span class="sxs-lookup"><span data-stu-id="9ce63-107">You can also add descriptive information that helps you remember how the server is used.</span></span>

 <span data-ttu-id="9ce63-108">![具有成員伺服器之已註冊的伺服器窗格](../media/ssas-ssms-registerserver.gif "具有成員伺服器之已註冊的伺服器窗格")</span><span class="sxs-lookup"><span data-stu-id="9ce63-108">![Registered Server pane with member servers](../media/ssas-ssms-registerserver.gif "Registered Server pane with member servers")</span></span>

 <span data-ttu-id="9ce63-109">可以用階層式結構來建立伺服器群組。</span><span class="sxs-lookup"><span data-stu-id="9ce63-109">Server groups can be created in a hierarchical structure.</span></span> <span data-ttu-id="9ce63-110">[本機伺服器群組] 是根節點，</span><span class="sxs-lookup"><span data-stu-id="9ce63-110">Local Server Group is the root node.</span></span> <span data-ttu-id="9ce63-111">它永遠包含本機電腦上執行的 Analysis Services 執行個體。</span><span class="sxs-lookup"><span data-stu-id="9ce63-111">It always contains instances of Analysis Services that run on the local computer.</span></span> <span data-ttu-id="9ce63-112">您可以將遠端伺服器加入至任何群組，包括本機群組。</span><span class="sxs-lookup"><span data-stu-id="9ce63-112">You can add remote servers to any group, including the local group.</span></span>

 <span data-ttu-id="9ce63-113">在建立伺服器群組之後，您必須使用 [已註冊的伺服器] 窗格來檢視及連接到成員伺服器。</span><span class="sxs-lookup"><span data-stu-id="9ce63-113">After you create a server group, you must use the Registered Servers pane to view and connect to the member servers.</span></span> <span data-ttu-id="9ce63-114">此窗格依伺服器類型 (Database Engine、Analysis Services、Reporting Services 和 Integration Services) 來篩選 SQL Server 執行個體。</span><span class="sxs-lookup"><span data-stu-id="9ce63-114">The pane filters SQL Server instances by server type (Database Engine, Analysis Services, Reporting Services, and Integration Services).</span></span> <span data-ttu-id="9ce63-115">按一下伺服器類型，即可檢視為此類型建立的伺服器群組。</span><span class="sxs-lookup"><span data-stu-id="9ce63-115">You click a server type to view the server groups created for it.</span></span> <span data-ttu-id="9ce63-116">若要連接到群組中的特定伺服器，您可以按兩下群組中的伺服器。</span><span class="sxs-lookup"><span data-stu-id="9ce63-116">To connect to a specific server within group, you double-click a server in the group.</span></span>

 <span data-ttu-id="9ce63-117">為伺服器所定義的連接資訊 (包括伺服器名稱) 會隨著伺服器註冊保存。</span><span class="sxs-lookup"><span data-stu-id="9ce63-117">The connection information that is defined for the server, including the server name, is persisted with server registration.</span></span> <span data-ttu-id="9ce63-118">您不能修改連接資訊，或在透過其他工具連接到伺服器時使用已註冊的名稱。</span><span class="sxs-lookup"><span data-stu-id="9ce63-118">You cannot modify the connection information, or use the registered name when connecting to the server using other tools.</span></span>

## <a name="create-a-server-group-and-add-registered-servers"></a><span data-ttu-id="9ce63-119">建立伺服器群組及加入已註冊的伺服器</span><span class="sxs-lookup"><span data-stu-id="9ce63-119">Create a Server Group and Add Registered Servers</span></span>

1.  <span data-ttu-id="9ce63-120">在 Management Studio 中，按一下 [檢視] 功能表上的 [已註冊的伺服器]，在工作空間中開啟 [已註冊的伺服器] 窗格。</span><span class="sxs-lookup"><span data-stu-id="9ce63-120">In Management Studio, click Registered Servers on the View menu to open the Registered Servers pane in the workspace.</span></span> <span data-ttu-id="9ce63-121">根據預設，本機伺服器群組已建立。</span><span class="sxs-lookup"><span data-stu-id="9ce63-121">By default, a local Server Group is already created.</span></span> <span data-ttu-id="9ce63-122">在本機伺服器上執行的所有 Analysis Services 執行個體都是成員。</span><span class="sxs-lookup"><span data-stu-id="9ce63-122">All instances of Analysis Services that are running on the local server are members.</span></span>

2.  <span data-ttu-id="9ce63-123">以滑鼠右鍵按一下 [本機伺服器群組]，選取 [新增伺服器群組]，並提供群組名稱。</span><span class="sxs-lookup"><span data-stu-id="9ce63-123">Right-click Local Server Group, select New Server Group, and give the group a name.</span></span>

3.  <span data-ttu-id="9ce63-124">以滑鼠右鍵按一下伺服器群組，然後選取 [新增伺服器註冊]。</span><span class="sxs-lookup"><span data-stu-id="9ce63-124">Right-click the server group and select New Server Registration.</span></span> <span data-ttu-id="9ce63-125">如果伺服器安裝為具名執行個體，請輸入本機或遠端伺服器的網路名稱，包括執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="9ce63-125">Enter the network name of a local or remote server, including the instance name if the server was installed as a named instance.</span></span> <span data-ttu-id="9ce63-126">或者，您也可以提供出現在 [已註冊的伺服器] 中的已註冊伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="9ce63-126">Optionally, you can provide a registered server name that appears in Registered Servers.</span></span> <span data-ttu-id="9ce63-127">此名稱只在 [已註冊的伺服器] 中使用。</span><span class="sxs-lookup"><span data-stu-id="9ce63-127">This name is used in Registered Servers only.</span></span> <span data-ttu-id="9ce63-128">您不能使用它來重新命名伺服器，也不能在連接字串中使用它。</span><span class="sxs-lookup"><span data-stu-id="9ce63-128">You cannot use it to rename a server, nor can you use it in a connection string.</span></span> <span data-ttu-id="9ce63-129">已註冊的伺服器名稱可以比實際伺服器名稱更具描述性，或包含有助於區別伺服器的識別特性。</span><span class="sxs-lookup"><span data-stu-id="9ce63-129">A registered server name can be more descriptive than the actual server name or include other identifying characteristics that help you distinguish this server from other servers.</span></span>


