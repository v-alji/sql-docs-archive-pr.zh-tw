---
title: Filestream 存取層級伺服器組態選項 | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- FILESTREAM [SQL Server], access level
- filestream access level
ms.assetid: b88f6ff2-795e-4730-bfb8-dbc6a958f2ad
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: dfa43b8e6e1762e87dd9c2abbdf7a583963e196e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606449"
---
# <a name="filestream-access-level-server-configuration-option"></a><span data-ttu-id="71a11-102">檔案資料流存取層級伺服器組態選項</span><span class="sxs-lookup"><span data-stu-id="71a11-102">filestream access level Server Configuration Option</span></span>
  <span data-ttu-id="71a11-103">您可以使用 filestream_access_level 選項來變更這個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體的 FILESTREAM 存取層級。</span><span class="sxs-lookup"><span data-stu-id="71a11-103">Use the filestream_access_level option to change the FILESTREAM access level for this instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="71a11-104">您必須先針對 FILESTREAM 啟用 Windows 管理設定，然後這個選項才會生效。</span><span class="sxs-lookup"><span data-stu-id="71a11-104">Before this option has any effect, the Windows administration settings for FILESTREAM must be enabled.</span></span> <span data-ttu-id="71a11-105">當您安裝 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 或使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 組態管理員時，可以啟用這些設定。</span><span class="sxs-lookup"><span data-stu-id="71a11-105">You can enable these settings when you install [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or by using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager.</span></span>  
  
|<span data-ttu-id="71a11-106">值</span><span class="sxs-lookup"><span data-stu-id="71a11-106">Value</span></span>|<span data-ttu-id="71a11-107">定義</span><span class="sxs-lookup"><span data-stu-id="71a11-107">Definition</span></span>|  
|-----------|----------------|  
|<span data-ttu-id="71a11-108">0</span><span class="sxs-lookup"><span data-stu-id="71a11-108">0</span></span>|<span data-ttu-id="71a11-109">針對這個執行個體停用 FILESTREAM 支援。</span><span class="sxs-lookup"><span data-stu-id="71a11-109">Disables FILESTREAM support for this instance.</span></span>|  
|<span data-ttu-id="71a11-110">1</span><span class="sxs-lookup"><span data-stu-id="71a11-110">1</span></span>|<span data-ttu-id="71a11-111">針對 [!INCLUDE[tsql](../../includes/tsql-md.md)] 存取啟用 FILESTREAM。</span><span class="sxs-lookup"><span data-stu-id="71a11-111">Enables FILESTREAM for [!INCLUDE[tsql](../../includes/tsql-md.md)] access.</span></span>|  
|<span data-ttu-id="71a11-112">2</span><span class="sxs-lookup"><span data-stu-id="71a11-112">2</span></span>|<span data-ttu-id="71a11-113">針對 [!INCLUDE[tsql](../../includes/tsql-md.md)] 和 Win32 資料流存取啟用 FILESTREAM。</span><span class="sxs-lookup"><span data-stu-id="71a11-113">Enables FILESTREAM for [!INCLUDE[tsql](../../includes/tsql-md.md)] and Win32 streaming access.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="71a11-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="71a11-114">See Also</span></span>  
 <span data-ttu-id="71a11-115">[Database Engine 組態 - Filestream](../../sql-server/install/database-engine-configuration-filestream.md) </span><span class="sxs-lookup"><span data-stu-id="71a11-115">[Database Engine Configuration - Filestream](../../sql-server/install/database-engine-configuration-filestream.md) </span></span>  
 [<span data-ttu-id="71a11-116">啟用及設定 FILESTREAM</span><span class="sxs-lookup"><span data-stu-id="71a11-116">Enable and Configure FILESTREAM</span></span>](../../relational-databases/blob/enable-and-configure-filestream.md)  
  
  
