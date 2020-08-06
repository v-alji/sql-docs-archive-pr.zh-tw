---
title: 連接到伺服器 (連接屬性頁面) Analysis Services | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.connecttoas.connectionproperties.f1
ms.assetid: 26cf53e3-3bcb-4697-8a88-53e93bc68b56
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 04706671ea8b0a50f2bf72cd7b73db88dce34d89
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686475"
---
# <a name="connect-to-server-connection-properties-page-analysis-services"></a><span data-ttu-id="67757-102">連接到伺服器 (連接屬性頁面) Analysis Service</span><span class="sxs-lookup"><span data-stu-id="67757-102">Connect to Server (Connection Properties Page) Analysis Services</span></span>
  <span data-ttu-id="67757-103">連接到 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 或在 [已註冊的伺服器]\*\*\*\* 中註冊 [!INCLUDE[ssAS](../includes/ssas-md.md)] 時，請使用這個索引標籤來檢視或指定選項。</span><span class="sxs-lookup"><span data-stu-id="67757-103">Use this tab to view or specify options when connecting to [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] or registering [!INCLUDE[ssAS](../includes/ssas-md.md)] in **Registered Servers**.</span></span> <span data-ttu-id="67757-104">連接時，[連接]\*\*\*\* 和 [選項]\*\*\*\* 才會出現在這個對話方塊中。</span><span class="sxs-lookup"><span data-stu-id="67757-104">**Connect** and **Options** only appear in this dialog box when connecting.</span></span> <span data-ttu-id="67757-105">註冊 [!INCLUDE[ssAS](../includes/ssas-md.md)] 時，[測試]\*\*\*\* 和 [儲存]\*\*\*\* 才會出現在這個對話方塊中。</span><span class="sxs-lookup"><span data-stu-id="67757-105">**Test** and **Save** only appear in this dialog box when registering [!INCLUDE[ssAS](../includes/ssas-md.md)].</span></span>  
  
## <a name="options"></a><span data-ttu-id="67757-106">選項</span><span class="sxs-lookup"><span data-stu-id="67757-106">Options</span></span>  
 <span data-ttu-id="67757-107">**連線到資料庫**</span><span class="sxs-lookup"><span data-stu-id="67757-107">**Connect to database**</span></span>  
 <span data-ttu-id="67757-108">從清單中選取要連接的資料庫。</span><span class="sxs-lookup"><span data-stu-id="67757-108">Select a database to connect to from the list.</span></span> <span data-ttu-id="67757-109">如果您選取 **\<default>** ，您將會連接到伺服器的預設資料庫。</span><span class="sxs-lookup"><span data-stu-id="67757-109">If you select **\<default>**, you will be connected to the default database for the server.</span></span> <span data-ttu-id="67757-110">如果您選取 **\<Browse server>** ，您可以流覽伺服器，尋找您想要連接的資料庫。</span><span class="sxs-lookup"><span data-stu-id="67757-110">If you select **\<Browse server>**, you can browse the server for the database you would like to connect to.</span></span>  
  
 <span data-ttu-id="67757-111">**連接逾時**</span><span class="sxs-lookup"><span data-stu-id="67757-111">**Connection timeout**</span></span>  
 <span data-ttu-id="67757-112">輸入在超時之前，等候連線建立的秒數。預設值為15秒。</span><span class="sxs-lookup"><span data-stu-id="67757-112">Enter the number of seconds to wait for a connection to be established before timing out. The default value is 15 seconds.</span></span>  
  
 <span data-ttu-id="67757-113">**執行超時**</span><span class="sxs-lookup"><span data-stu-id="67757-113">**Execution timeout**</span></span>  
 <span data-ttu-id="67757-114">輸入在伺服器上執行的工作完成之前，所要等候的時間 (以秒為單位)。</span><span class="sxs-lookup"><span data-stu-id="67757-114">Enter the amount of time in seconds to wait before execution of a task is completed on the server.</span></span> <span data-ttu-id="67757-115">預設值為零秒，此值會指出沒有逾時。</span><span class="sxs-lookup"><span data-stu-id="67757-115">The default value is zero seconds, which indicates there is no time-out.</span></span>  
  
 <span data-ttu-id="67757-116">**加密連線**</span><span class="sxs-lookup"><span data-stu-id="67757-116">**Encrypt connection**</span></span>  
 <span data-ttu-id="67757-117">強制連接的加密。</span><span class="sxs-lookup"><span data-stu-id="67757-117">Forces encryption of the connection.</span></span>  
  
 <span data-ttu-id="67757-118">**全部重設**</span><span class="sxs-lookup"><span data-stu-id="67757-118">**Reset All**</span></span>  
 <span data-ttu-id="67757-119">將所有手動輸入的連接屬性值取代成預設值。</span><span class="sxs-lookup"><span data-stu-id="67757-119">Replace all manually entered connection property values with the default values.</span></span>  
  
 <span data-ttu-id="67757-120">**[連接]**</span><span class="sxs-lookup"><span data-stu-id="67757-120">**Connect**</span></span>  
 <span data-ttu-id="67757-121">使用列出的值嘗試進行連接。</span><span class="sxs-lookup"><span data-stu-id="67757-121">Attempt a connection using the listed values.</span></span>  
  
 <span data-ttu-id="67757-122">**選項**</span><span class="sxs-lookup"><span data-stu-id="67757-122">**Options**</span></span>  
 <span data-ttu-id="67757-123">按一下即可變更對話方塊，並隱藏其他伺服器連接選項，例如記住密碼。</span><span class="sxs-lookup"><span data-stu-id="67757-123">Click to change the dialog and hide the additional server connection options, such as remembering the password.</span></span>  
  
 <span data-ttu-id="67757-124">**Test**</span><span class="sxs-lookup"><span data-stu-id="67757-124">**Test**</span></span>  
 <span data-ttu-id="67757-125">在 [已註冊的伺服器]\*\*\*\* 中註冊 [!INCLUDE[ssAS](../includes/ssas-md.md)] 時，請按一下以測試連接。</span><span class="sxs-lookup"><span data-stu-id="67757-125">When registering [!INCLUDE[ssAS](../includes/ssas-md.md)] in **Registered Servers**, click to test the connection.</span></span>  
  
 <span data-ttu-id="67757-126">**儲存**</span><span class="sxs-lookup"><span data-stu-id="67757-126">**Save**</span></span>  
 <span data-ttu-id="67757-127">儲存 [已註冊的伺服器]\*\*\*\* 中的設定。</span><span class="sxs-lookup"><span data-stu-id="67757-127">Saves the settings in **Registered Servers**.</span></span>  
  
  
