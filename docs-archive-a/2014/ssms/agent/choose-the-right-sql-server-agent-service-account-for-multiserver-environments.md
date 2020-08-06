---
title: 為多伺服器環境選擇適當的 SQL Server Agent 服務帳戶 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, service accounts
- multiserver environments [SQL Server], SQL Server Agent service account behavior
ms.assetid: a07e2f38-281c-495b-965b-13fad03ba548
author: stevestein
ms.author: sstein
ms.openlocfilehash: 94ef890f5d2ef2b85d2f4d1023a93747e903a7f3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606584"
---
# <a name="choose-the-right-sql-server-agent-service-account-for-multiserver-environments"></a><span data-ttu-id="0f53e-102">為多伺服器環境選擇適當的 SQL Server Agent 服務帳戶</span><span class="sxs-lookup"><span data-stu-id="0f53e-102">Choose the Right SQL Server Agent Service Account for Multiserver Environments</span></span>
  <span data-ttu-id="0f53e-103">您為 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 服務所選擇的 Windows 帳戶會影響多伺服器環境的行為，如下所示：</span><span class="sxs-lookup"><span data-stu-id="0f53e-103">The Windows account you choose for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service can affect the behavior of a multiserver environment, as follows:</span></span>  
  
-   <span data-ttu-id="0f53e-104">如果您是以不是本機 Windows Administrators 群組成員的帳戶來執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 服務，則將目標伺服器編列至主要伺服器會失敗。</span><span class="sxs-lookup"><span data-stu-id="0f53e-104">If you run the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service under an account that is not a member of the local Windows Administrators group, enlisting target servers to master servers may fail.</span></span> <span data-ttu-id="0f53e-105">如果這麼做，則會傳回下列錯誤訊息：</span><span class="sxs-lookup"><span data-stu-id="0f53e-105">If it does, the following error message is returned:</span></span>  
  
     <span data-ttu-id="0f53e-106">「編列作業失敗。」</span><span class="sxs-lookup"><span data-stu-id="0f53e-106">"The enlistment operation failed."</span></span>  
  
     <span data-ttu-id="0f53e-107">重新啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 服務，以解決這個問題。</span><span class="sxs-lookup"><span data-stu-id="0f53e-107">Restart the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent services to resolve this issue.</span></span>  
  
-   <span data-ttu-id="0f53e-108">如果以本機系統帳戶執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 服務，則只有在主要伺服器和目標伺服器都位在相同電腦上時，才支援「主要伺服器-目標伺服器」作業。</span><span class="sxs-lookup"><span data-stu-id="0f53e-108">When the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service is run under the Local System account, master server-target server operations are supported only if both the master server and the target server reside on the same computer.</span></span> <span data-ttu-id="0f53e-109">如果您使用這個組態，則將目標伺服器編列至主要伺服器時，會傳回下列訊息：</span><span class="sxs-lookup"><span data-stu-id="0f53e-109">If you use this configuration, the following message is returned when you enlist target servers to a master server:</span></span>  
  
     <span data-ttu-id="0f53e-110">「請確定 <目標伺服器電腦名稱>\*\* 的代理程式啟動帳戶有權限以 targetServer 的身分登入」。</span><span class="sxs-lookup"><span data-stu-id="0f53e-110">"Ensure the agent start-up account for *<target_server_computer_name>* has rights to log on as targetServer."</span></span>  
  
     <span data-ttu-id="0f53e-111">您可以忽略此參考訊息。</span><span class="sxs-lookup"><span data-stu-id="0f53e-111">You can ignore this informational message.</span></span> <span data-ttu-id="0f53e-112">編列作業應該順利完成。</span><span class="sxs-lookup"><span data-stu-id="0f53e-112">The enlistment operation should complete successfully.</span></span>  
  
 <span data-ttu-id="0f53e-113">如需為 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 服務選擇帳戶的詳細資訊，請參閱 [選取 SQL Server Agent 服務的帳戶](select-an-account-for-the-sql-server-agent-service.md)。</span><span class="sxs-lookup"><span data-stu-id="0f53e-113">For more information about choosing an account for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service, see [Select an Account for the SQL Server Agent Service](select-an-account-for-the-sql-server-agent-service.md).</span></span>  
  
  
