---
title: 資料庫引擎設定-Filestream |Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- FILESTREAM [SQL Server], about FILESTREAM
ms.assetid: 641a10a1-ae52-4d26-8f1c-a032a4aeff02
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: ab12b507246a3e13ac59be213813604d531d9a28
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704738"
---
# <a name="database-engine-configuration---filestream"></a><span data-ttu-id="ce8b2-102">Database Engine 組態 - Filestream</span><span class="sxs-lookup"><span data-stu-id="ce8b2-102">Database Engine Configuration - Filestream</span></span>
  <span data-ttu-id="ce8b2-103">您可以使用這個頁面，針對這個 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 安裝啟用 FILESTREAM。</span><span class="sxs-lookup"><span data-stu-id="ce8b2-103">Use this page to enable FILESTREAM for this installation of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="ce8b2-104">FILESTREAM 將 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 與 NTFS 檔案系統整合，方法是 `varbinary(max)` 將二進位大型物件 (BLOB) 資料儲存為檔案系統上的檔案。</span><span class="sxs-lookup"><span data-stu-id="ce8b2-104">FILESTREAM integrates the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] with an NTFS file system by storing `varbinary(max)` binary large object (BLOB) data as files on the file system.</span></span> [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="ce8b2-105">陳述式可以插入、更新、查詢、搜尋和備份 FILESTREAM 資料。</span><span class="sxs-lookup"><span data-stu-id="ce8b2-105">statements can insert, update, query, search, and back up FILESTREAM data.</span></span> <span data-ttu-id="ce8b2-106">Win32 檔案系統介面提供了資料的資料流方式存取。</span><span class="sxs-lookup"><span data-stu-id="ce8b2-106">Win32 file system interfaces provide streaming access to the data.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="ce8b2-107">UI 元素清單</span><span class="sxs-lookup"><span data-stu-id="ce8b2-107">UI element list</span></span>  
 <span data-ttu-id="ce8b2-108">**對 Transact-SQL 存取啟用 FILESTREAM**</span><span class="sxs-lookup"><span data-stu-id="ce8b2-108">**Enable FILESTREAM for Transact-SQL access**</span></span>  
 <span data-ttu-id="ce8b2-109">選取此選項即可針對 [!INCLUDE[tsql](../../includes/tsql-md.md)] 存取啟用 FILESTREAM。</span><span class="sxs-lookup"><span data-stu-id="ce8b2-109">Select to enable FILESTREAM for [!INCLUDE[tsql](../../includes/tsql-md.md)] access.</span></span> <span data-ttu-id="ce8b2-110">您必須先核取這個控制項，然後才能使用其他控制選項。</span><span class="sxs-lookup"><span data-stu-id="ce8b2-110">This control must be checked before the other control options will be available.</span></span>  
  
 <span data-ttu-id="ce8b2-111">**對檔案 I/O 資料流存取啟用 FILESTREAM**</span><span class="sxs-lookup"><span data-stu-id="ce8b2-111">**Enable FILESTREAM for file I/O streaming access**</span></span>  
 <span data-ttu-id="ce8b2-112">選取此選項即可針對 Win32 資料流存取啟用 FILESTREAM。</span><span class="sxs-lookup"><span data-stu-id="ce8b2-112">Select to enable Win32 streaming access for FILESTREAM.</span></span>  
  
 <span data-ttu-id="ce8b2-113">**Windows 共用名稱**</span><span class="sxs-lookup"><span data-stu-id="ce8b2-113">**Windows share name**</span></span>  
 <span data-ttu-id="ce8b2-114">使用這個控制項即可輸入即將儲存 FILESTREAM 資料之 Windows 共用的名稱。</span><span class="sxs-lookup"><span data-stu-id="ce8b2-114">Use this control to enter the name of the Windows share in which the FILESTREAM data will be stored.</span></span>  
  
 <span data-ttu-id="ce8b2-115">**允許遠端用戶端具有 FILESTREAM 資料的資料流存取權**</span><span class="sxs-lookup"><span data-stu-id="ce8b2-115">**Allow remote clients to have streaming access to FILESTREAM data**</span></span>  
 <span data-ttu-id="ce8b2-116">選取這個控制項即可允許遠端用戶端在此伺服器上存取這項 FILESTREAM 資料。</span><span class="sxs-lookup"><span data-stu-id="ce8b2-116">Select this control to allow remote clients to access this FILESTREAM data on this server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce8b2-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ce8b2-117">See Also</span></span>  
 <span data-ttu-id="ce8b2-118">[啟用及設定 FILESTREAM](../../relational-databases/blob/enable-and-configure-filestream.md) </span><span class="sxs-lookup"><span data-stu-id="ce8b2-118">[Enable and Configure FILESTREAM](../../relational-databases/blob/enable-and-configure-filestream.md) </span></span>  
 [<span data-ttu-id="ce8b2-119">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="ce8b2-119">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
