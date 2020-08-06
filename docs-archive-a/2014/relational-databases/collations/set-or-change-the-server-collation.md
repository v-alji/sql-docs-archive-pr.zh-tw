---
title: 設定或變更伺服器定序 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- server collations [SQL Server]
- collations [SQL Server], server
ms.assetid: 3242deef-6f5f-4051-a121-36b3b4da851d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 35e7be051c8cf63a272f2bf42fb54b1c45ed4160
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606895"
---
# <a name="set-or-change-the-server-collation"></a><span data-ttu-id="a6ac5-102">設定或變更伺服器定序</span><span class="sxs-lookup"><span data-stu-id="a6ac5-102">Set or Change the Server Collation</span></span>
  <span data-ttu-id="a6ac5-103">對於與 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體一起安裝的所有系統資料庫，以及任何新建的使用者資料庫而言，伺服器定序會當做預設定序。</span><span class="sxs-lookup"><span data-stu-id="a6ac5-103">The server collation acts as the default collation for all system databases that are installed with the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], and also any newly created user databases.</span></span> <span data-ttu-id="a6ac5-104">伺服器定序是在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝期間指定。</span><span class="sxs-lookup"><span data-stu-id="a6ac5-104">The server collation is specified during [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installation.</span></span> <span data-ttu-id="a6ac5-105">如需詳細資訊，請參閱 [Collation and Unicode Support](collation-and-unicode-support.md)。</span><span class="sxs-lookup"><span data-stu-id="a6ac5-105">For more information, see [Collation and Unicode Support](collation-and-unicode-support.md).</span></span>  
  
## <a name="changing-the-server-collation"></a><span data-ttu-id="a6ac5-106">變更伺服器定序</span><span class="sxs-lookup"><span data-stu-id="a6ac5-106">Changing the Server Collation</span></span>  
 <span data-ttu-id="a6ac5-107">變更 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體的預設定序是相當複雜的作業，需要執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="a6ac5-107">Changing the default collation for an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] can be a complex operation and involves the following steps:</span></span>  
  
-   <span data-ttu-id="a6ac5-108">確定已備妥重新建立使用者資料庫以及所有內含物件所需的所有資訊或指令碼。</span><span class="sxs-lookup"><span data-stu-id="a6ac5-108">Make sure you have all the information or scripts needed to re-create your user databases and all the objects in them.</span></span>  
  
-   <span data-ttu-id="a6ac5-109">使用 [bcp Utility](../../tools/bcp-utility.md)這類工具來匯出所有資料。</span><span class="sxs-lookup"><span data-stu-id="a6ac5-109">Export all your data using a tool such as the [bcp Utility](../../tools/bcp-utility.md).</span></span> <span data-ttu-id="a6ac5-110">如需詳細資訊，請參閱[資料的大量匯入及匯出 &#40;SQL Server&#41;](../import-export/bulk-import-and-export-of-data-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="a6ac5-110">For more information, see [Bulk Import and Export of Data &#40;SQL Server&#41;](../import-export/bulk-import-and-export-of-data-sql-server.md).</span></span>  
  
-   <span data-ttu-id="a6ac5-111">卸除所有使用者資料庫。</span><span class="sxs-lookup"><span data-stu-id="a6ac5-111">Drop all the user databases.</span></span>  
  
-   <span data-ttu-id="a6ac5-112">重建 master 資料庫，以使用 **setup** 命令的 SQLCOLLATION 屬性來指定新定序。</span><span class="sxs-lookup"><span data-stu-id="a6ac5-112">Rebuild the master database specifying the new collation in the SQLCOLLATION property of the **setup** command.</span></span> <span data-ttu-id="a6ac5-113">例如：</span><span class="sxs-lookup"><span data-stu-id="a6ac5-113">For example:</span></span>  
  
    ```  
    Setup /QUIET /ACTION=REBUILDDATABASE /INSTANCENAME=InstanceName   
    /SQLSYSADMINACCOUNTS=accounts /[ SAPWD= StrongPassword ]   
    /SQLCOLLATION=CollationName  
    ```  
  
     <span data-ttu-id="a6ac5-114">如需詳細資訊，請參閱 [重建系統資料庫](../databases/system-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="a6ac5-114">For more information, see [Rebuild System Databases](../databases/system-databases.md).</span></span>  
  
-   <span data-ttu-id="a6ac5-115">建立所有資料庫以及所有內含物件。</span><span class="sxs-lookup"><span data-stu-id="a6ac5-115">Create all the databases and all the objects in them.</span></span>  
  
-   <span data-ttu-id="a6ac5-116">匯入所有資料。</span><span class="sxs-lookup"><span data-stu-id="a6ac5-116">Import all your data.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a6ac5-117">您可以不變更 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體的預設定序，而是針對每個建立的新資料庫指定預設定序。</span><span class="sxs-lookup"><span data-stu-id="a6ac5-117">Instead of changing the default collation of an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you can specify a default collation for each new database you create.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6ac5-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a6ac5-118">See Also</span></span>  
 <span data-ttu-id="a6ac5-119">[定序與 Unicode 支援](collation-and-unicode-support.md) </span><span class="sxs-lookup"><span data-stu-id="a6ac5-119">[Collation and Unicode Support](collation-and-unicode-support.md) </span></span>  
 <span data-ttu-id="a6ac5-120">[設定或變更資料庫定序](set-or-change-the-database-collation.md) </span><span class="sxs-lookup"><span data-stu-id="a6ac5-120">[Set or Change the Database Collation](set-or-change-the-database-collation.md) </span></span>  
 <span data-ttu-id="a6ac5-121">[設定或變更資料行定序](set-or-change-the-column-collation.md) </span><span class="sxs-lookup"><span data-stu-id="a6ac5-121">[Set or Change the Column Collation](set-or-change-the-column-collation.md) </span></span>  
 [<span data-ttu-id="a6ac5-122">重建系統資料庫</span><span class="sxs-lookup"><span data-stu-id="a6ac5-122">Rebuild System Databases</span></span>](../databases/system-databases.md)  
  
  
