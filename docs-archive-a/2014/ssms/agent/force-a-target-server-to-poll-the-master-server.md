---
title: 強制目標伺服器輪詢主要伺服器 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- forcing master server polling
- polling master servers [SQL Server]
- master servers [SQL Server], polling
- target servers [SQL Server], polling the master server
ms.assetid: f1189a47-5ac3-45e2-9c5f-847810672279
author: stevestein
ms.author: sstein
ms.openlocfilehash: b37bf19bfe8e8fb55c29c8d94c28a341d06df5da
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584962"
---
# <a name="force-a-target-server-to-poll-the-master-server"></a><span data-ttu-id="8a01b-102">強制目標伺服器輪詢主要伺服器</span><span class="sxs-lookup"><span data-stu-id="8a01b-102">Force a Target Server to Poll the Master Server</span></span>
  <span data-ttu-id="8a01b-103">此主題描述如何強制目標伺服器輪詢主要伺服器。</span><span class="sxs-lookup"><span data-stu-id="8a01b-103">This topic describes how to force a target server to poll the master server.</span></span> <span data-ttu-id="8a01b-104">目標伺服器必須是主要伺服器上已註冊的伺服器。</span><span class="sxs-lookup"><span data-stu-id="8a01b-104">The target server must be a registered server on the master server.</span></span>  
  
 <span data-ttu-id="8a01b-105">作業是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 執行的一系列指定動作。</span><span class="sxs-lookup"><span data-stu-id="8a01b-105">A job is a specified series of actions that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent performs.</span></span> <span data-ttu-id="8a01b-106">多重伺服器作業是一個主要伺服器執行於一或多個目標伺服器上的作業。</span><span class="sxs-lookup"><span data-stu-id="8a01b-106">A multiserver job is a job that a master server runs on one or more target servers.</span></span> <span data-ttu-id="8a01b-107">每一個目標伺服器可以同時執行相同作業的一個執行個體。</span><span class="sxs-lookup"><span data-stu-id="8a01b-107">Each target server can run one instance of the same job at the same time.</span></span> <span data-ttu-id="8a01b-108">每個目標伺服器會定期輪詢主要伺服器、下載任何指派到目標伺服器的新作業之副本，然後中斷連接。</span><span class="sxs-lookup"><span data-stu-id="8a01b-108">Each target server periodically polls the master server, downloads a copy of any new jobs assigned to the target server, and then disconnects.</span></span> <span data-ttu-id="8a01b-109">目標伺服器會先在本機執行作業，然後再重新連接到主要伺服器，以便上傳作業結果的狀態。</span><span class="sxs-lookup"><span data-stu-id="8a01b-109">The target server runs the job locally and then reconnects to the master server to upload the job outcome status.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8a01b-110">如果當目標伺服器嘗試上傳作業狀態時無法存取主要伺服器，作業狀態會被多工緩衝處理，直到可以存取主要伺服器為止。</span><span class="sxs-lookup"><span data-stu-id="8a01b-110">If the master server is inaccessible when the target server tries to upload job status, the job status is spooled until the master server can be accessed.</span></span>  
  
-   <span data-ttu-id="8a01b-111">**開始之前：** [限制事項](#Restrictions)、[安全性](#Security)</span><span class="sxs-lookup"><span data-stu-id="8a01b-111">**Before you begin:**  [Limitations and Restrictions](#Restrictions), [Security](#Security)</span></span>  
  
-   <span data-ttu-id="8a01b-112">**若要強制目標伺服器輪詢主要伺服器，請使用：**  [SQL Server Management Studio](#SSMS)</span><span class="sxs-lookup"><span data-stu-id="8a01b-112">**To force a target server to poll the master server, using:**  [SQL Server Management Studio](#SSMS)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="8a01b-113">開始之前</span><span class="sxs-lookup"><span data-stu-id="8a01b-113">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="8a01b-114">限制事項</span><span class="sxs-lookup"><span data-stu-id="8a01b-114">Limitations and Restrictions</span></span>  
 <span data-ttu-id="8a01b-115">目標伺服器必須是主要伺服器上已註冊的伺服器。</span><span class="sxs-lookup"><span data-stu-id="8a01b-115">The target server must be a registered server on the master server.</span></span> <span data-ttu-id="8a01b-116">您必須從主要伺服器執行本主題中提供的指示。</span><span class="sxs-lookup"><span data-stu-id="8a01b-116">You must run the instructions given in this topic from the master server.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="8a01b-117">Security</span><span class="sxs-lookup"><span data-stu-id="8a01b-117">Security</span></span>  
 <span data-ttu-id="8a01b-118">如需詳細資訊，請參閱＜ [Implement SQL Server Agent Security](implement-sql-server-agent-security.md) ＞和＜ [Choose the Right SQL Server Agent Service Account for Multiserver Environments](choose-the-right-sql-server-agent-service-account-for-multiserver-environments.md)＞。</span><span class="sxs-lookup"><span data-stu-id="8a01b-118">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md) and [Choose the Right SQL Server Agent Service Account for Multiserver Environments](choose-the-right-sql-server-agent-service-account-for-multiserver-environments.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="8a01b-119">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="8a01b-119">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="8a01b-120">**若要強制目標伺服器輪詢主要伺服器**</span><span class="sxs-lookup"><span data-stu-id="8a01b-120">**To force a target server to poll the master server**</span></span>  
  
1.  <span data-ttu-id="8a01b-121">在 **[物件總管]** 中展開主要伺服器。</span><span class="sxs-lookup"><span data-stu-id="8a01b-121">In **Object Explorer**, expand the master server.</span></span>  
  
2.  <span data-ttu-id="8a01b-122">以滑鼠右鍵按一下 [SQL Server Agent]\*\*\*\*，指向 [多重伺服器管理]\*\*\*\*，然後按一下 [管理目標伺服器]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8a01b-122">Right-click **SQL Server Agent**, point to **Multi Server Administration**, and then click **Manage Target Servers**.</span></span>  
  
3.  <span data-ttu-id="8a01b-123">按一下目標伺服器，然後按一下 **[強制輪詢]**。</span><span class="sxs-lookup"><span data-stu-id="8a01b-123">Click a target server, and then click **Force Poll**.</span></span>  
  
  
