---
title: SMO 中的回溯相容性 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
ms.assetid: 2f986436-aaf2-4eaf-9809-df849d97d4fb
author: stevestein
ms.author: sstein
ms.openlocfilehash: 73b6f4eebccf23850ccf08ec95ccb59dbc5c6293
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595918"
---
# <a name="backward-compatibility-in-smo"></a><span data-ttu-id="7871c-102">SMO 中的回溯相容性</span><span class="sxs-lookup"><span data-stu-id="7871c-102">Backward Compatibility in SMO</span></span>
  <span data-ttu-id="7871c-103">以舊版 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 撰寫的 SMO 應用程式可以使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中的 SMO 重新編譯。</span><span class="sxs-lookup"><span data-stu-id="7871c-103">SMO applications that were written using previous versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] can be recompiled by using SMO in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
## <a name="migrating-smo-applications"></a><span data-ttu-id="7871c-104">移轉 SMO 應用程式</span><span class="sxs-lookup"><span data-stu-id="7871c-104">Migrating SMO Applications</span></span>  
 <span data-ttu-id="7871c-105">您必須移除舊版 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 之 SMO dll 的參考，並納入 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 所提供之新 SMO dll 的參考。</span><span class="sxs-lookup"><span data-stu-id="7871c-105">References to SMO dlls in older versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] must be removed, and references to the new SMO dlls that are provided with [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] must be included.</span></span>  
  
 <span data-ttu-id="7871c-106">下列是您應該要參考的基本項目：</span><span class="sxs-lookup"><span data-stu-id="7871c-106">Minimally, you would reference the following:</span></span>  
  
-   <span data-ttu-id="7871c-107">Microsoft.SqlServer.ConnectionInfo</span><span class="sxs-lookup"><span data-stu-id="7871c-107">Microsoft.SqlServer.ConnectionInfo</span></span>  
  
-   <span data-ttu-id="7871c-108">Microsoft.SqlServer.Smo</span><span class="sxs-lookup"><span data-stu-id="7871c-108">Microsoft.SqlServer.Smo</span></span>  
  
-   <span data-ttu-id="7871c-109">Microsoft.SqlServer.Management.Sdk.Sfc</span><span class="sxs-lookup"><span data-stu-id="7871c-109">Microsoft.SqlServer.Management.Sdk.Sfc</span></span>  
  
 <span data-ttu-id="7871c-110">對於連接類別、SMO 公用程式類別和基礎類別而言，這些檔案是必須的。</span><span class="sxs-lookup"><span data-stu-id="7871c-110">These files are required for connection classes, SMO utility classes, and foundation classes.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7871c-111">由於 SmoEnum.dll 已經移除，因此所有指向它的參考也必須從 SMO [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 專案中移除。</span><span class="sxs-lookup"><span data-stu-id="7871c-111">SmoEnum.dll has been removed so references to it must be removed from the SMO [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] project.</span></span>  
  
 <span data-ttu-id="7871c-112">命名空間也已變更，因此您可以使用下列的命名空間：</span><span class="sxs-lookup"><span data-stu-id="7871c-112">The namespaces have also changed, so you can use the following:</span></span>  
  
##### <a name="for-visual-c"></a><span data-ttu-id="7871c-113">For Visual C#</span><span class="sxs-lookup"><span data-stu-id="7871c-113">For Visual C#</span></span>  
  
```  
using Microsoft.SqlServer.Management.Smo;  
using Microsoft.SqlServer.Management.Common;  
```  
  
##### <a name="for-visual-basic"></a><span data-ttu-id="7871c-114">For Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7871c-114">For Visual Basic</span></span>  
  
```  
Imports Microsoft.SqlServer.Management.Smo  
Imports Microsoft.SqlServer.Management.Common  
```  
  
 <span data-ttu-id="7871c-115">如果您的程式碼使用了 Urn 功能，例如 `Server.GetSqlSmoObject(Urn)`，則必須連結到 Microsoft.SqlServer.Management.Sdk.Sfc 命名空間。</span><span class="sxs-lookup"><span data-stu-id="7871c-115">If your code uses Urn functionality, such as `Server.GetSqlSmoObject(Urn)`, you must link to the Microsoft.SqlServer.Management.Sdk.Sfc namespace.</span></span>  
  
 <span data-ttu-id="7871c-116">如果您的程式碼直接使用了傳送物件，則必須連結到 Microsoft.SqlServer.Management.SmoExtended 命名空間。</span><span class="sxs-lookup"><span data-stu-id="7871c-116">If your code uses the Transfer object directly, you will have to link to the Microsoft.SqlServer.Management.SmoExtended namespace.</span></span>  
  
 <span data-ttu-id="7871c-117">當您在移轉程式碼時，可能需要修改程式碼。</span><span class="sxs-lookup"><span data-stu-id="7871c-117">When you migrate code, you might have to modify the code.</span></span> <span data-ttu-id="7871c-118">這是因為有多個 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 和 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 功能都已被 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中的功能取代了。</span><span class="sxs-lookup"><span data-stu-id="7871c-118">This is because several [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] features have been deprecated in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="7871c-119">如需已被取代之功能的詳細資訊，請參閱《線上叢書》中[SQL Server 2014 的已淘汰資料庫引擎功能](../../database-engine/deprecated-database-engine-features-in-sql-server-2016.md) [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="7871c-119">For more information about deprecated features, see [Deprecated Database Engine Features in SQL Server 2014](../../database-engine/deprecated-database-engine-features-in-sql-server-2016.md) in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Books Online.</span></span>  
  
  
