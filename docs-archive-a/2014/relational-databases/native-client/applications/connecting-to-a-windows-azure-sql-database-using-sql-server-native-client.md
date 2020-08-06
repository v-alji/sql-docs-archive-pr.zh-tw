---
title: 使用 SQL Server Native Client 連接到 Azure SQL Database |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: 0dc20bb6-b142-4259-b87b-427d2ba798af
author: rothja
ms.author: jroth
ms.openlocfilehash: 177c655f97e32f2044460e87c6cd775cdf8fcde9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597077"
---
# <a name="connecting-to-an-azure-sql-database-using-sql-server-native-client"></a><span data-ttu-id="b0dfc-102">使用 SQL Server Native Client 連線到 Azure SQL Database</span><span class="sxs-lookup"><span data-stu-id="b0dfc-102">Connecting to an Azure SQL Database Using SQL Server Native Client</span></span>
  <span data-ttu-id="b0dfc-103">如需示範如何使用 Native Client 連接至的 [!INCLUDE[ssSDSfull](../../../includes/sssdsfull-md.md)] 範例 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ，請參閱[開發： how to 主題 (Azure SQL Database) ](https://msdn.microsoft.com/library/ee621787.aspx)。</span><span class="sxs-lookup"><span data-stu-id="b0dfc-103">For a sample that shows how to connect to a [!INCLUDE[ssSDSfull](../../../includes/sssdsfull-md.md)] using [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, see [Development: How-to Topics (Azure SQL Database)](https://msdn.microsoft.com/library/ee621787.aspx).</span></span>  
  
## <a name="known-issues-when-connecting-to-a-sql-database"></a><span data-ttu-id="b0dfc-104">連接至 SQL 資料庫時的已知問題</span><span class="sxs-lookup"><span data-stu-id="b0dfc-104">Known Issues When Connecting to a SQL Database</span></span>  
 <span data-ttu-id="b0dfc-105">以下是使用 [!INCLUDE[ssSDS](../../../includes/sssds-md.md)] Native Client 連接至 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 時的已知問題：</span><span class="sxs-lookup"><span data-stu-id="b0dfc-105">The following are known issues when connecting to a [!INCLUDE[ssSDS](../../../includes/sssds-md.md)] using [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client:</span></span>  
  
-   <span data-ttu-id="b0dfc-106">如果在階段中使用 `SQLBrowseConnect`，可能會拒絕與 `SQLBrowseConnect` 建立的連接。</span><span class="sxs-lookup"><span data-stu-id="b0dfc-106">A connection made with `SQLBrowseConnect` may be rejected if `SQLBrowseConnect` is used in stages.</span></span>  <span data-ttu-id="b0dfc-107">例如，如果在第一次呼叫中傳送驅動程式名稱，在第二次呼叫中傳送伺服器和認證 (使用者和密碼)，然後建立連接，再於第三次呼叫中傳送資料庫名稱和語言，</span><span class="sxs-lookup"><span data-stu-id="b0dfc-107">For example, if the driver name is sent in the first call, server and credentials (user and password) sent in the second call, establishing the connection, and a database name and a language in the third call.</span></span>  <span data-ttu-id="b0dfc-108">則第三次呼叫會導致 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 發出 USE 陳述式以變更資料庫。</span><span class="sxs-lookup"><span data-stu-id="b0dfc-108">The third call will cause [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client to issue a USE statement to change databases.</span></span> <span data-ttu-id="b0dfc-109">但是，[!INCLUDE[ssSDS](../../../includes/sssds-md.md)] 不支援 USE 陳述式，因此產生下列錯誤：</span><span class="sxs-lookup"><span data-stu-id="b0dfc-109">However, the USE statement is not supported in [!INCLUDE[ssSDS](../../../includes/sssds-md.md)], generating the following error:</span></span>  
  
    ```  
    [Microsoft][SQL Server Native Client 11.0][SQL Server]USE statement is not supported to switch between databases. Use a new connection to connect to a different Database.  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="b0dfc-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b0dfc-110">See Also</span></span>  
 [<span data-ttu-id="b0dfc-111">使用 SQL Server Native Client 建置應用程式</span><span class="sxs-lookup"><span data-stu-id="b0dfc-111">Building Applications with SQL Server Native Client</span></span>](building-applications-with-sql-server-native-client.md)  
  
  
