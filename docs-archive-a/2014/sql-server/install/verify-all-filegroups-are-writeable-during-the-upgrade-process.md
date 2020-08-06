---
title: 驗證升級程式期間，所有檔案群組都是可寫入的 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- filegroups [SQL Server], writeable
- writeable filegroups [SQL Server]
ms.assetid: 2985efc1-4b14-46c3-abbd-a656b159f23c
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 8146efb876bf97c36c549a2b58d104592df611e9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710109"
---
# <a name="verify-all-filegroups-are-writeable-during-the-upgrade-process"></a><span data-ttu-id="8d513-102">在升級過程中，確認所有檔案群組都是可寫入的</span><span class="sxs-lookup"><span data-stu-id="8d513-102">Verify all filegroups are writeable during the upgrade process</span></span>
  <span data-ttu-id="8d513-103">Upgrade Advisor 偵測到具有一或多個唯讀檔案群組的資料庫。</span><span class="sxs-lookup"><span data-stu-id="8d513-103">Upgrade Advisor detected a database that has one or more read-only filegroups.</span></span> <span data-ttu-id="8d513-104">在升級之前，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體中的所有資料庫都必須將檔案群組設為 READ_WRITE。</span><span class="sxs-lookup"><span data-stu-id="8d513-104">All databases in the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] must have filegroups set to READ_WRITE before upgrading.</span></span>  
  
## <a name="component"></a><span data-ttu-id="8d513-105">元件</span><span class="sxs-lookup"><span data-stu-id="8d513-105">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a><span data-ttu-id="8d513-106">更正動作</span><span class="sxs-lookup"><span data-stu-id="8d513-106">Corrective Action</span></span>  
 <span data-ttu-id="8d513-107">請使用 ALTER DATABASE 將檔案群組設定為 READ_WRITE。</span><span class="sxs-lookup"><span data-stu-id="8d513-107">Use ALTER DATABASE to set the filegroup to READ_WRITE.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d513-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8d513-108">See Also</span></span>  
 <span data-ttu-id="8d513-109">[資料庫引擎升級問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="8d513-109">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="8d513-110">SQL Server 2014 Upgrade Advisor &#91;新的&#93;</span><span class="sxs-lookup"><span data-stu-id="8d513-110">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
