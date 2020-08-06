---
title: 0xFFFF 字元不是有效的物件識別碼 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- 0xFFFF character [SQL Server]
ms.assetid: b2c9c8cf-9194-45e0-be6b-2d5ec52e8153
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 4594c1cca0fc183100d927842cc2b533694bf90e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595551"
---
# <a name="0xffff-character-is-not-valid-as-an-object-identifier"></a><span data-ttu-id="de68f-102">0xFFFF 字元不是有效的物件識別碼</span><span class="sxs-lookup"><span data-stu-id="de68f-102">0xFFFF character is not valid as an object identifier</span></span>
  <span data-ttu-id="de68f-103">Upgrade Advisor 在物件識別碼中偵測到 0xFFFF 字元。</span><span class="sxs-lookup"><span data-stu-id="de68f-103">Upgrade Advisor has detected the 0xFFFF character in an object identifier.</span></span> <span data-ttu-id="de68f-104">當資料庫相容性模式設定為 90 或之後時，[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 和更新版本無法參考或重新命名識別碼中包含此字元的物件 (例如資料庫、資料表或資料行)。</span><span class="sxs-lookup"><span data-stu-id="de68f-104">In [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later, objects such as databases, tables, and columns that contain this character in their identifiers cannot be referenced or renamed when the database compatibility mode is set to 90 or later.</span></span> <span data-ttu-id="de68f-105">當您升級為 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 時，使用者資料庫會維持其相容性模式。</span><span class="sxs-lookup"><span data-stu-id="de68f-105">When you upgrade to [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], user databases maintain their compatibility mode.</span></span> <span data-ttu-id="de68f-106">將資料庫相容性模式變更為 90 或之後以前，請重新命名包含 0xFFFF 字元的物件。</span><span class="sxs-lookup"><span data-stu-id="de68f-106">Before you change the database compatibility mode to 90 or later, rename the object that contains the 0xFFFF character.</span></span>  
  
 <span data-ttu-id="de68f-107">如需有關識別碼的詳細資訊，請參閱《[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 線上叢書》中的＜識別碼＞。</span><span class="sxs-lookup"><span data-stu-id="de68f-107">For more information about identifiers, see "Identifiers" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span> <span data-ttu-id="de68f-108">如需有關資料庫相容性模式的詳細資訊，請參閱《[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 線上叢書》中的＜sp_dbcmptlevel＞。</span><span class="sxs-lookup"><span data-stu-id="de68f-108">For more information about database compatibility modes, see "sp_dbcmptlevel" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="component"></a><span data-ttu-id="de68f-109">元件</span><span class="sxs-lookup"><span data-stu-id="de68f-109">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="de68f-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="de68f-110">See Also</span></span>  
 <span data-ttu-id="de68f-111">[資料庫引擎升級問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="de68f-111">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="de68f-112">SQL Server 2014 Upgrade Advisor &#91;新的&#93;</span><span class="sxs-lookup"><span data-stu-id="de68f-112">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
