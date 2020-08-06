---
title: INFORMATION_SCHEMA。架構會傳回資料庫中的架構名稱，而不是實例中的資料庫 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- INFORMATION_SCHEMA.SCHEMATA view
ms.assetid: 4337b643-910d-47d7-bea8-f4052066b9a2
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: cb2a34a59bf6257c188210fc7bf2aeacb70f6b7f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606031"
---
# <a name="information_schemaschemata-returns-schema-names-in-a-database-not-databases-in-an-instance"></a><span data-ttu-id="a262b-102">INFORMATION_SCHEMA.SCHEMATA 會傳回資料庫 (非執行個體中的資料庫) 中的結構描述名稱</span><span class="sxs-lookup"><span data-stu-id="a262b-102">INFORMATION_SCHEMA.SCHEMATA returns schema names in a database, not databases in an instance</span></span>
  <span data-ttu-id="a262b-103">Upgrade Advisor 偵測到參考 INFORMATION_SCHEMA.SCHEMATA 檢視的陳述式。</span><span class="sxs-lookup"><span data-stu-id="a262b-103">Upgrade Advisor detected statements that reference the INFORMATION_SCHEMA.SCHEMATA view.</span></span> <span data-ttu-id="a262b-104">在舊版 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中，此檢視會傳回 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體中的所有資料庫。</span><span class="sxs-lookup"><span data-stu-id="a262b-104">In earlier versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], this view returned all databases in an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="a262b-105">在 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 和更新版本中，此檢視會傳回資料庫中的所有結構描述。</span><span class="sxs-lookup"><span data-stu-id="a262b-105">In [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later, the view returns all schemas in a database.</span></span>  
  
## <a name="component"></a><span data-ttu-id="a262b-106">元件</span><span class="sxs-lookup"><span data-stu-id="a262b-106">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a><span data-ttu-id="a262b-107">描述</span><span class="sxs-lookup"><span data-stu-id="a262b-107">Description</span></span>  
 <span data-ttu-id="a262b-108">在舊版 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中，INFORMATION_SCHEMA.SCHEMATA 檢視會傳回 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體中的所有資料庫。</span><span class="sxs-lookup"><span data-stu-id="a262b-108">In earlier versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the INFORMATION_SCHEMA.SCHEMATA view returned all databases in an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="a262b-109">現在，該檢視會傳回符合「SQL 標準」之資料庫中的所有結構描述。</span><span class="sxs-lookup"><span data-stu-id="a262b-109">Now, the view returns all schemas in a database, which complies with the SQL Standard.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="a262b-110">更正動作</span><span class="sxs-lookup"><span data-stu-id="a262b-110">Corrective Action</span></span>  
 <span data-ttu-id="a262b-111">將您的應用程式修改為參考**sys.databases**目錄檢視，以傳回實例中的所有資料庫 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="a262b-111">Modify your application to reference the **sys.databases** catalog view to return all databases in an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a262b-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a262b-112">See Also</span></span>  
 <span data-ttu-id="a262b-113">[資料庫引擎升級問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="a262b-113">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="a262b-114">SQL Server 2014 Upgrade Advisor &#91;新的&#93;</span><span class="sxs-lookup"><span data-stu-id="a262b-114">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
