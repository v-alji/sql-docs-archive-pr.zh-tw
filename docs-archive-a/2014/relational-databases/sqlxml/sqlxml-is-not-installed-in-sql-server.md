---
title: SQL Server 中未安裝 SQLXML |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
ms.assetid: 3dbb4f65-41de-48b8-ad62-47c9d7932de3
author: rothja
ms.author: jroth
ms.openlocfilehash: ffa4cfd8b18dbfd9b4ba05599e2a973ac5f6e888
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597705"
---
# <a name="sqlxml-is-not-installed-in-sql-server"></a><span data-ttu-id="61ad2-102">SQLXML 不會安裝在 SQL Server 中</span><span class="sxs-lookup"><span data-stu-id="61ad2-102">SQLXML Is Not Installed in SQL Server</span></span>
  <span data-ttu-id="61ad2-103">在 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 之前，SQLXML 4.0 隨附於 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 而且是所有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 版本 ([!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] 除外) 之預設安裝的一部分。</span><span class="sxs-lookup"><span data-stu-id="61ad2-103">Before [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], SQLXML 4.0 was released with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and was part of the default installation of all [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] versions except for [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)].</span></span> <span data-ttu-id="61ad2-104">不過，從 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 開始，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 已不再包含最新版 SQLXML (SQLXML 4.0 SP1)。</span><span class="sxs-lookup"><span data-stu-id="61ad2-104">Starting with [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], the latest version of SQLXML (SQLXML 4.0 SP1) is no longer included in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="61ad2-105">若要安裝 SQLXML 4.0 SP1 （如果有的話），請從[SQLXML SP1 的安裝位置](https://www.microsoft.com/download/details.aspx?id=44272)下載。</span><span class="sxs-lookup"><span data-stu-id="61ad2-105">To install SQLXML 4.0 SP1 when it is available, download it from [Install Location for SQLXML SP1](https://www.microsoft.com/download/details.aspx?id=44272).</span></span>  
  
 <span data-ttu-id="61ad2-106">如果某個應用程式在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 上執行而且需要 SQLXML 4.0，但是電腦並沒有 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]，您就必須下載並安裝 SQLXML 4.0 SP1。</span><span class="sxs-lookup"><span data-stu-id="61ad2-106">If an application runs on [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and requires SQLXML 4.0, and if the computer does not have [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], you must download and install SQLXML 4.0 SP1.</span></span>  
  
## <a name="sqlxml-40-sp1-behavior-with-new-data-types-using-sqloledb-and-sql-server-native-client-ole-db-provider"></a><span data-ttu-id="61ad2-107">使用 SQLOLEDB 和 SQL Server Native Client OLE DB Provider 的 SQLXML 4.0 SP1 行為以及新的資料類型</span><span class="sxs-lookup"><span data-stu-id="61ad2-107">SQLXML 4.0 SP1 Behavior with New Data Types Using SQLOLEDB and SQL Server Native Client OLE DB Provider</span></span>  
 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] <span data-ttu-id="61ad2-108">導入了下列資料類型，而這些是使用 SQLXML 之開發人員可能會想要使用的資料類型：</span><span class="sxs-lookup"><span data-stu-id="61ad2-108">introduces the following data types, which developers using SQLXML might want to use:</span></span>  
  
-   `Date`  
  
-   `Time`  
  
-   `DateTime2`  
  
-   `DateTimeOffset`  
  
 <span data-ttu-id="61ad2-109">使用 SQLXML 4.0 SP1 搭配 SQLOLEDB (來自 Windows Data Access Components，之前稱為 Microsoft Data Access Components) 或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB (來自 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]) 時，這些新的類型將會針對開發人員顯示成字串。</span><span class="sxs-lookup"><span data-stu-id="61ad2-109">When using SQLXML 4.0 SP1 with either SQLOLEDB (from Windows Data Access Components, formerly Microsoft Data Access Components) or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB from [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], these new types will appear as strings to a developer.</span></span> <span data-ttu-id="61ad2-110">搭配 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者 11.0 使用時，SQLXML 4.0 SP1 會將這四個新的資料類型啟用成內建的純量類型。</span><span class="sxs-lookup"><span data-stu-id="61ad2-110">SQLXML 4.0 SP1 will enable these four new data types as built-in scalar types when used with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB Provider 11.0.</span></span> <span data-ttu-id="61ad2-111">在您下載 SQLXML 4.0 SP1 之前，將這些類型對應至非字串類型可能會導致某些資料遭截斷。</span><span class="sxs-lookup"><span data-stu-id="61ad2-111">Until you download SQLXML 4.0 SP1, mapping these types to non-string types might cause truncation of some data.</span></span> <span data-ttu-id="61ad2-112">例如，將對應 `DateTime2` 至 `xsd:date` 會導致資料截斷為 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] `DateTime` 3.33 毫秒的有效位數。</span><span class="sxs-lookup"><span data-stu-id="61ad2-112">For example, mapping `DateTime2` to `xsd:date` will cause data to be truncated to the [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] `DateTime` precision of 3.33 milliseconds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61ad2-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="61ad2-113">See Also</span></span>  
 [<span data-ttu-id="61ad2-114">SQLXML 4.0 程式設計概念</span><span class="sxs-lookup"><span data-stu-id="61ad2-114">SQLXML 4.0 Programming Concepts</span></span>](sqlxml-4-0-programming-concepts.md)  
  
  
