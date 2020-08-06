---
title: SQL Server 安裝的新增功能 | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- installing SQL Server, what's new
- SQL Server, what's new
- SQL Server, installing
ms.assetid: c8642a96-3a09-4ec7-a9c3-c539147e6330
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d34085e320cd8ca0b82d382d6d49eaa303086114
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595390"
---
# <a name="what39s-new-in-sql-server-installation"></a><span data-ttu-id="4b019-102">SQL Server 安裝的新增功能</span><span class="sxs-lookup"><span data-stu-id="4b019-102">What&#39;s New in SQL Server Installation</span></span>
  <span data-ttu-id="4b019-103">Windows Vista 不是 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 支援的作業系統。</span><span class="sxs-lookup"><span data-stu-id="4b019-103">Windows Vista is not a supported operating system for [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)].</span></span> <span data-ttu-id="4b019-104">Service Pack 1 會保留 [!INCLUDE[win7](../../includes/win7-md.md)] 和 [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] 作業系統的最低需求。</span><span class="sxs-lookup"><span data-stu-id="4b019-104">Service Pack 1 remains as the minimum requirement for [!INCLUDE[win7](../../includes/win7-md.md)] and [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] operating systems.</span></span> <span data-ttu-id="4b019-105">如需作業系統需求的詳細資訊，請參閱[安裝 SQL Server 2014 的硬體和軟體需求](hardware-and-software-requirements-for-installing-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="4b019-105">For more information on operating system requirements, see [Hardware and Software Requirements for Installing SQL Server 2014](hardware-and-software-requirements-for-installing-sql-server.md).</span></span>  
  
 <span data-ttu-id="4b019-106">[!INCLUDE[ssExpCurrent](../../includes/ssexpcurrent-md.md)] 的安裝會提示您指定目錄，用來儲存所擷取的封裝。</span><span class="sxs-lookup"><span data-stu-id="4b019-106">Installation of [!INCLUDE[ssExpCurrent](../../includes/ssexpcurrent-md.md)] will prompt you to specify the directory to save the extracted package.</span></span> <span data-ttu-id="4b019-107">如果沒有輸入位置，[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 會預設為電腦的系統磁碟機。</span><span class="sxs-lookup"><span data-stu-id="4b019-107">If no location is entered, [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] will default to the computer's system drive.</span></span> <span data-ttu-id="4b019-108">在 [!INCLUDE[ssExpCurrent](../../includes/ssexpcurrent-md.md)] 安裝完成之後，仍會保留所擷取的檔案。</span><span class="sxs-lookup"><span data-stu-id="4b019-108">The extracted files will remain after [!INCLUDE[ssExpCurrent](../../includes/ssexpcurrent-md.md)] installation is complete.</span></span>  
  
 <span data-ttu-id="4b019-109">在 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 中，所有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝都支援 SysPrep。</span><span class="sxs-lookup"><span data-stu-id="4b019-109">In [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)], SysPrep is supported for all installations of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="4b019-110">SysPrep 現在支援容錯移轉叢集安裝。</span><span class="sxs-lookup"><span data-stu-id="4b019-110">SysPrep now supports failover cluster installations.</span></span> <span data-ttu-id="4b019-111">如需詳細資訊，請參閱[使用 Sysprep 安裝 SQL Server 的考慮](../../database-engine/install-windows/considerations-for-installing-sql-server-using-sysprep.md)和[使用 sysprep 安裝 SQL Server 2014](../../database-engine/install-windows/install-sql-server-using-sysprep.md)。</span><span class="sxs-lookup"><span data-stu-id="4b019-111">For more information, see [Considerations for Installing SQL Server Using SysPrep](../../database-engine/install-windows/considerations-for-installing-sql-server-using-sysprep.md) and [Install SQL Server 2014 Using SysPrep](../../database-engine/install-windows/install-sql-server-using-sysprep.md).</span></span>  
  
 <span data-ttu-id="4b019-112">支援從 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 升級，但不支援並存。</span><span class="sxs-lookup"><span data-stu-id="4b019-112">Upgrade from [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] is supported, but side-by-side is not supported.</span></span> <span data-ttu-id="4b019-113">如需 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)][!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]支援的詳細資訊，請參閱 [支援的版本與版本升級](../../database-engine/install-windows/supported-version-and-edition-upgrades.md)。</span><span class="sxs-lookup"><span data-stu-id="4b019-113">For more information about [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] support in [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)], see [Supported Version and Edition Upgrades](../../database-engine/install-windows/supported-version-and-edition-upgrades.md).</span></span>  
  
 <span data-ttu-id="4b019-114">從 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 開始，Standard 版中的資料庫引擎具有 128 GB 的記憶體容量。</span><span class="sxs-lookup"><span data-stu-id="4b019-114">Beginning in [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)], the database engine in the Standard edition has a memory capacity of 128 GB.</span></span> <span data-ttu-id="4b019-115">在中 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] ，Standard edition 中的資料庫引擎具有 64 GB 的記憶體容量。</span><span class="sxs-lookup"><span data-stu-id="4b019-115">In [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], the database engine in the Standard edition had a memory capacity of 64 GB.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b019-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4b019-116">See Also</span></span>  
 <span data-ttu-id="4b019-117">[2014 SQL Server 的新功能](../what-s-new-in-sql-server-2016.md) </span><span class="sxs-lookup"><span data-stu-id="4b019-117">[What's New in SQL Server 2014](../what-s-new-in-sql-server-2016.md) </span></span>  
 <span data-ttu-id="4b019-118">[SQL Server 2014 的產品規格](../../../2014/getting-started/sql-server-2014-product-specifications.md) </span><span class="sxs-lookup"><span data-stu-id="4b019-118">[Product Specifications for SQL Server 2014](../../../2014/getting-started/sql-server-2014-product-specifications.md) </span></span>  
 <span data-ttu-id="4b019-119">[規劃 SQL Server 安裝](../../../2014/sql-server/install/planning-a-sql-server-installation.md) </span><span class="sxs-lookup"><span data-stu-id="4b019-119">[Planning a SQL Server Installation](../../../2014/sql-server/install/planning-a-sql-server-installation.md) </span></span>  
 [<span data-ttu-id="4b019-120">安裝 SQL Server 2014 的硬體與軟體需求</span><span class="sxs-lookup"><span data-stu-id="4b019-120">Hardware and Software Requirements for Installing SQL Server 2014</span></span>](hardware-and-software-requirements-for-installing-sql-server.md)  
  
  
