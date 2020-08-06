---
title: 使用 SQL Server Native Client 的時機 |Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, about SQL Server Native Client ODBC driver
- SQLNCLI, about SQL Server Native Client
- data access [SQL Server Native Client], about SQL Server Native Client
ms.assetid: 08f18b36-209d-4cf7-9623-ebc61859a91d
author: rothja
ms.author: jroth
ms.openlocfilehash: f8aeb34525bbe5c1b003e8fd95e7a414025965a8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594510"
---
# <a name="when-to-use-sql-server-native-client"></a><span data-ttu-id="b2e43-102">使用 SQL Server Native Client 的時機</span><span class="sxs-lookup"><span data-stu-id="b2e43-102">When to Use SQL Server Native Client</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="b2e43-103">Native Client 是用來存取 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫資料的一種技術。</span><span class="sxs-lookup"><span data-stu-id="b2e43-103">Native Client is one technology that you can use to access data in a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database.</span></span>  <span data-ttu-id="b2e43-104">如需不同資料存取技術的討論內容，請參閱 [Data Access Technologies Road Map](https://go.microsoft.com/fwlink/?LinkID=179186) (資料存取技術藍圖)</span><span class="sxs-lookup"><span data-stu-id="b2e43-104">For a discussion of the different data-access technologies, see [Data Access Technologies Road Map](https://go.microsoft.com/fwlink/?LinkID=179186)</span></span>  
  
 <span data-ttu-id="b2e43-105">決定是否要使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 當做應用程式的資料存取技術時，您應該考慮許多因素。</span><span class="sxs-lookup"><span data-stu-id="b2e43-105">When deciding whether to use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client as the data access technology of your application, you should consider several factors.</span></span>  
  
 <span data-ttu-id="b2e43-106">對於新的應用程式而言，如果您正在使用 Microsoft Visual C# 或 Visual Basic 等 Managed 程式語言，而且需要存取 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中的新功能，則應該使用 .NET Framework Data Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (屬於 .NET Framework 的一部分)。</span><span class="sxs-lookup"><span data-stu-id="b2e43-106">For new applications, if you're using a managed programming language such as Microsoft Visual C# or Visual Basic, and you need to access the new features in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you should use the .NET Framework Data Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], which is part of the .NET Framework.</span></span>  
  
 <span data-ttu-id="b2e43-107">如果您正在開發以 COM 為基礎的應用程式，而且需要存取 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 所導入的新功能，則應該使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client。</span><span class="sxs-lookup"><span data-stu-id="b2e43-107">If you are developing a COM-based application and need to access the new features introduced in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you should use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.</span></span> <span data-ttu-id="b2e43-108">如果您不需要存取 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的新功能，可以繼續使用 Windows Data Access Components (WDAC)。</span><span class="sxs-lookup"><span data-stu-id="b2e43-108">If you don't need access to the new features of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you can continue to use Windows Data Access Components (WDAC).</span></span>  
  
 <span data-ttu-id="b2e43-109">對於現有的 OLE DB 和 ODBC 應用程式而言，主要的問題在於您是否需要存取 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的新功能。</span><span class="sxs-lookup"><span data-stu-id="b2e43-109">For existing OLE DB and ODBC applications, the primary issue is whether you need to access the new features of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="b2e43-110">如果您有一個不需要 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 之新功能的完整應用程式，就可以繼續使用 WDAC。</span><span class="sxs-lookup"><span data-stu-id="b2e43-110">If you have a mature application that does not need the new features of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you can continue to use WDAC.</span></span> <span data-ttu-id="b2e43-111">但是，如果您需要存取這些新功能（例如[xml 資料類型](/sql/t-sql/xml/xml-transact-sql)），您應該使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client。</span><span class="sxs-lookup"><span data-stu-id="b2e43-111">But if you do need to access those new features, such as the [xml data type](/sql/t-sql/xml/xml-transact-sql), you should use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.</span></span>  
  
 <span data-ttu-id="b2e43-112">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 和 MDAC 都可使用資料列版本設定來支援讀取認可的交易隔離，但是只有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 可支援快照集交易隔離 </span><span class="sxs-lookup"><span data-stu-id="b2e43-112">Both [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client and MDAC support read committed transaction isolation using row versioning, but only [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client supports snapshot transaction isolation.</span></span> <span data-ttu-id="b2e43-113">(在程式設計的詞彙中，含有資料列版本設定的讀取認可交易隔離與讀取認可的交易相同)。</span><span class="sxs-lookup"><span data-stu-id="b2e43-113">(In programming terms, read committed transaction isolation with row versioning is the same as Read-Committed transaction.)</span></span>  
  
 <span data-ttu-id="b2e43-114">如需 Native Client 與 MDAC 之間差異的詳細資訊 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，請參閱將[應用程式更新為從 MDAC SQL Server Native Client](../../relational-databases/native-client/applications/updating-an-application-to-sql-server-native-client-from-mdac.md)。</span><span class="sxs-lookup"><span data-stu-id="b2e43-114">For information about the differences between [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client and MDAC, see [Updating an Application to SQL Server Native Client from MDAC](../../relational-databases/native-client/applications/updating-an-application-to-sql-server-native-client-from-mdac.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2e43-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b2e43-115">See Also</span></span>  
 <span data-ttu-id="b2e43-116">[SQL Server Native Client 程式設計](../../relational-databases/native-client/sql-server-native-client-programming.md) </span><span class="sxs-lookup"><span data-stu-id="b2e43-116">[SQL Server Native Client Programming](../../relational-databases/native-client/sql-server-native-client-programming.md) </span></span>  
 <span data-ttu-id="b2e43-117">[ODBC 的使用說明主題](../native-client-odbc-how-to/odbc-how-to-topics.md) </span><span class="sxs-lookup"><span data-stu-id="b2e43-117">[ODBC How-to Topics](../native-client-odbc-how-to/odbc-how-to-topics.md) </span></span>  
 [<span data-ttu-id="b2e43-118">OLE DB 的使用說明主題</span><span class="sxs-lookup"><span data-stu-id="b2e43-118">OLE DB How-to Topics</span></span>](../native-client-ole-db-how-to/ole-db-how-to-topics.md)  
  
  
