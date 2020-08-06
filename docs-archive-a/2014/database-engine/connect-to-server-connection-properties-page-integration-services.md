---
title: 連接到伺服器 (連線屬性頁面) Integration Services |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.connecttodts.connectionproperties.f1
- sql12.ssiseditserverregistration.connectionproperties.f1
ms.assetid: c2513dab-8415-4e0c-9475-6d4ab97fea7c
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 05f3d370a3f3a299bb90df53538b3fa3e90e28c4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707826"
---
# <a name="connect-to-server-connection-properties-page-integration-services"></a><span data-ttu-id="355f4-102">連接到伺服器 (連接屬性頁面) Integration Services</span><span class="sxs-lookup"><span data-stu-id="355f4-102">Connect to Server (Connection Properties Page) Integration Services</span></span>
  <span data-ttu-id="355f4-103">連接到 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 或在 [已註冊的伺服器]\*\*\*\* 中註冊 [!INCLUDE[ssIS](../includes/ssis-md.md)] 時，請使用這個索引標籤來檢視或指定選項。</span><span class="sxs-lookup"><span data-stu-id="355f4-103">Use this tab to view or specify options when connecting to [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] or registering [!INCLUDE[ssIS](../includes/ssis-md.md)] in **Registered Servers**.</span></span> <span data-ttu-id="355f4-104">連接時，[連接]\*\*\*\* 和 [選項]\*\*\*\* 才會出現在這個對話方塊中。</span><span class="sxs-lookup"><span data-stu-id="355f4-104">**Connect** and **Options** only appear in this dialog box when connecting.</span></span> <span data-ttu-id="355f4-105">註冊 [!INCLUDE[ssIS](../includes/ssis-md.md)] 時，[測試]\*\*\*\* 和 [儲存]\*\*\*\* 才會出現在這個對話方塊中。</span><span class="sxs-lookup"><span data-stu-id="355f4-105">**Test** and **Save** only appear in this dialog box when registering [!INCLUDE[ssIS](../includes/ssis-md.md)].</span></span>  
  
## <a name="options"></a><span data-ttu-id="355f4-106">選項</span><span class="sxs-lookup"><span data-stu-id="355f4-106">Options</span></span>  
 <span data-ttu-id="355f4-107">**連接埠號碼**</span><span class="sxs-lookup"><span data-stu-id="355f4-107">**Port number**</span></span>  
 <span data-ttu-id="355f4-108">輸入 [!INCLUDE[ssIS](../includes/ssis-md.md)]所使用的通訊埠編號。</span><span class="sxs-lookup"><span data-stu-id="355f4-108">Enter the port number used by [!INCLUDE[ssIS](../includes/ssis-md.md)].</span></span>  
  
 <span data-ttu-id="355f4-109">**連接逾時**</span><span class="sxs-lookup"><span data-stu-id="355f4-109">**Connection time-out**</span></span>  
 <span data-ttu-id="355f4-110">輸入在超時之前，等候連線建立的秒數。預設值為15秒。</span><span class="sxs-lookup"><span data-stu-id="355f4-110">Enter the number of seconds to wait for a connection to be established before timing out. The default value is 15 seconds.</span></span>  
  
 <span data-ttu-id="355f4-111">**執行逾時**</span><span class="sxs-lookup"><span data-stu-id="355f4-111">**Execution time-out**</span></span>  
 <span data-ttu-id="355f4-112">輸入在伺服器上執行的工作完成之前，所要等候的時間 (以秒為單位)。</span><span class="sxs-lookup"><span data-stu-id="355f4-112">Enter the amount of time in seconds to wait before execution of a task is completed on the server.</span></span> <span data-ttu-id="355f4-113">預設值為零秒，此值會指出沒有逾時。</span><span class="sxs-lookup"><span data-stu-id="355f4-113">The default value is zero seconds, which indicates there is no time-out.</span></span>  
  
 <span data-ttu-id="355f4-114">**全部重設**</span><span class="sxs-lookup"><span data-stu-id="355f4-114">**Reset All**</span></span>  
 <span data-ttu-id="355f4-115">將所有手動輸入的連接屬性值取代成預設值。</span><span class="sxs-lookup"><span data-stu-id="355f4-115">Replace all manually entered connection property values with the default values.</span></span>  
  
 <span data-ttu-id="355f4-116">**[連接]**</span><span class="sxs-lookup"><span data-stu-id="355f4-116">**Connect**</span></span>  
 <span data-ttu-id="355f4-117">使用列出的值嘗試進行連接。</span><span class="sxs-lookup"><span data-stu-id="355f4-117">Attempt a connection using the listed values.</span></span>  
  
 <span data-ttu-id="355f4-118">**選項**</span><span class="sxs-lookup"><span data-stu-id="355f4-118">**Options**</span></span>  
 <span data-ttu-id="355f4-119">按一下即可變更對話方塊，並隱藏其他伺服器連接選項，例如記住密碼。</span><span class="sxs-lookup"><span data-stu-id="355f4-119">Click to change the dialog and hide the additional server connection options, such as remembering the password.</span></span>  
  
 <span data-ttu-id="355f4-120">**Test**</span><span class="sxs-lookup"><span data-stu-id="355f4-120">**Test**</span></span>  
 <span data-ttu-id="355f4-121">在 [已註冊的伺服器]\*\*\*\* 中註冊 [!INCLUDE[ssIS](../includes/ssis-md.md)] 時，請按一下以測試連接。</span><span class="sxs-lookup"><span data-stu-id="355f4-121">When registering [!INCLUDE[ssIS](../includes/ssis-md.md)] in **Registered Servers**, click to test the connection.</span></span>  
  
 <span data-ttu-id="355f4-122">**儲存**</span><span class="sxs-lookup"><span data-stu-id="355f4-122">**Save**</span></span>  
 <span data-ttu-id="355f4-123">儲存 [已註冊的伺服器]\*\*\*\* 中的設定。</span><span class="sxs-lookup"><span data-stu-id="355f4-123">Saves the settings in **Registered Servers**.</span></span>  
  
  
