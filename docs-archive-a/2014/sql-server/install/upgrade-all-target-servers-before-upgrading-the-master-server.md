---
title: 在升級主伺服器之前，請先升級所有目標伺服器 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- TSX [SQL Server Agent]
- target servers [SQL Server Agent]
- MSX [SQL Server Agent]
- master servers [SQL Server Agent]
ms.assetid: 2c231793-3878-4a5e-a425-1fa0d787ba84
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 031fedc4af4b058704cef1da8df846397b235305
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585764"
---
# <a name="upgrade-all-target-servers-before-upgrading-the-master-server"></a><span data-ttu-id="7da41-102">先升級所有目標伺服器後再升級主要伺服器</span><span class="sxs-lookup"><span data-stu-id="7da41-102">Upgrade all target servers before upgrading the master server</span></span>
  <span data-ttu-id="7da41-103">升級主要伺服器之前，請先升級所有設定為目標伺服器的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 電腦。</span><span class="sxs-lookup"><span data-stu-id="7da41-103">Before you upgrade the master server, upgrade all computers that are running [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that are configured as target servers.</span></span>  
  
## <a name="component"></a><span data-ttu-id="7da41-104">元件</span><span class="sxs-lookup"><span data-stu-id="7da41-104">Component</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="7da41-105">Agent</span><span class="sxs-lookup"><span data-stu-id="7da41-105">Agent</span></span>  
  
## <a name="description"></a><span data-ttu-id="7da41-106">描述</span><span class="sxs-lookup"><span data-stu-id="7da41-106">Description</span></span>  
 <span data-ttu-id="7da41-107">若要在多伺服器環境中自動化管理，您至少必須有一個主要伺服器和一個目標伺服器。</span><span class="sxs-lookup"><span data-stu-id="7da41-107">To automate administration in multiserver environments, you must have at least one master server and at least one target server.</span></span> <span data-ttu-id="7da41-108">主要伺服器會將作業散發到目標伺服器，並接收目標伺服器傳回的事件。</span><span class="sxs-lookup"><span data-stu-id="7da41-108">A master server distributes jobs to, and receives events from, target servers.</span></span> <span data-ttu-id="7da41-109">對於目標伺服器上執行的作業，主要伺服器也會儲存其作業定義的集中副本。</span><span class="sxs-lookup"><span data-stu-id="7da41-109">A master server also stores the central copy of job definitions for jobs that are run on target servers.</span></span>  
  
 <span data-ttu-id="7da41-110">如果目前的伺服器設定為主要伺服器，請先升級所有目標伺服器，然後再升級主要伺服器。</span><span class="sxs-lookup"><span data-stu-id="7da41-110">If the current server is configured as a master server, upgrade all of your target servers first before you upgrade the master server.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="7da41-111">更正動作</span><span class="sxs-lookup"><span data-stu-id="7da41-111">Corrective Action</span></span>  
 <span data-ttu-id="7da41-112">如果您無法在升級主要伺服器之前升級所有目標伺服器，就必須在升級之後，脫離所有目標伺服器並重新編列它們。</span><span class="sxs-lookup"><span data-stu-id="7da41-112">If you cannot upgrade all target servers before you upgrade the master server, you must defect all target servers and reenlist them after you upgrade.</span></span>  
  
 <span data-ttu-id="7da41-113">如需詳細資訊，請參閱《[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 線上叢書》中的＜將整個企業的管理自動化＞、＜如何：使目標伺服器脫離主要伺服器＞和＜如何：將目標伺服器編列至主要伺服器＞。</span><span class="sxs-lookup"><span data-stu-id="7da41-113">For more information, see the topics "Automating Administration across an Enterprise," "How to: Defect a Target Server from a Master Server," and "How to: Enlist a Target Server to a Master" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7da41-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7da41-114">See Also</span></span>  
 <span data-ttu-id="7da41-115">[SQL Server Agent 升級問題](../../../2014/sql-server/install/sql-server-agent-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="7da41-115">[SQL Server Agent Upgrade Issues](../../../2014/sql-server/install/sql-server-agent-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="7da41-116">SQL Server Agent 升級問題</span><span class="sxs-lookup"><span data-stu-id="7da41-116">SQL Server Agent Upgrade Issues</span></span>](../../../2014/sql-server/install/sql-server-agent-upgrade-issues.md)  
  
  
