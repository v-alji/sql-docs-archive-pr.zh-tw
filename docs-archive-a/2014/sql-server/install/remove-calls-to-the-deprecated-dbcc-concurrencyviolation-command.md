---
title: 移除對已被取代之 DBCC CONCURRENCYVIOLATION 命令的呼叫 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 2cc9f6ff-de36-4e94-bd04-59f5c45c4911
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: cde04ebfc2ea9996d1c9ed233123e5b66f6e81fa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705938"
---
# <a name="remove-calls-to-the-deprecated-dbcc-concurrencyviolation-command"></a><span data-ttu-id="3179b-102">移除已被取代之 DBCC CONCURRENCYVIOLATION 命令的呼叫</span><span class="sxs-lookup"><span data-stu-id="3179b-102">Remove calls to the deprecated DBCC CONCURRENCYVIOLATION command</span></span>
  <span data-ttu-id="3179b-103">Upgrade Advisor 偵測到您使用了 DBCC CONCURRENCYVIOLATION 命令。</span><span class="sxs-lookup"><span data-stu-id="3179b-103">Upgrade Advisor detected the use of the DBCC CONCURRENCYVIOLATION command.</span></span> <span data-ttu-id="3179b-104">無法再使用這個命令。</span><span class="sxs-lookup"><span data-stu-id="3179b-104">This command is no longer available.</span></span> <span data-ttu-id="3179b-105">執行這個命令會傳回錯誤 2526。</span><span class="sxs-lookup"><span data-stu-id="3179b-105">Executing this command returns error 2526.</span></span>  
  
## <a name="component"></a><span data-ttu-id="3179b-106">元件</span><span class="sxs-lookup"><span data-stu-id="3179b-106">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a><span data-ttu-id="3179b-107">描述</span><span class="sxs-lookup"><span data-stu-id="3179b-107">Description</span></span>  
 <span data-ttu-id="3179b-108">由於沒有任何 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的最新版本包含工作負載管理員，因此這個命令已經移除了。</span><span class="sxs-lookup"><span data-stu-id="3179b-108">No recent version of edition of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] includes a workload governor; therefore the command has been removed.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="3179b-109">更正動作</span><span class="sxs-lookup"><span data-stu-id="3179b-109">Corrective Action</span></span>  
 <span data-ttu-id="3179b-110">請更新應用程式和指令碼，以便移除這個已被取代之命令的參考。</span><span class="sxs-lookup"><span data-stu-id="3179b-110">Update applications and scripts to remove references to this deprecated command.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="3179b-111">外部資源</span><span class="sxs-lookup"><span data-stu-id="3179b-111">External Resources</span></span>  
  
