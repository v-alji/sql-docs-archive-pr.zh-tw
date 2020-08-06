---
title: SQL Server Native Client ODBC 資料來源 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC data sources, about data sources
- ODBC data sources, names
- data sources [SQL Server Native Client]
- names [ODBC]
- ODBC applications, data sources
- SQL Server Native Client ODBC driver, data sources
- ODBC data sources
ms.assetid: a6a50fd0-d439-43fd-b76f-16ec02f478c5
author: rothja
ms.author: jroth
ms.openlocfilehash: 6960118e13f0843640b18056bda655726cbbbd29
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595945"
---
# <a name="sql-server-native-client-odbc-data-sources"></a><span data-ttu-id="4aeea-102">SQL Server Native Client ODBC 資料來源</span><span class="sxs-lookup"><span data-stu-id="4aeea-102">SQL Server Native Client ODBC Data Sources</span></span>
  <span data-ttu-id="4aeea-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料來源名稱 (DSN) 會識別 ODBC 資料來源，其中包含 ODBC 應用程式需要連接到特定伺服器之 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫的所有資訊。</span><span class="sxs-lookup"><span data-stu-id="4aeea-103">A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data source name (DSN) identifies an ODBC data source containing all of the information that an ODBC application needs to connect to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database on a specific server.</span></span> <span data-ttu-id="4aeea-104">有兩個方式可以定義 ODBC 資料來源名稱：</span><span class="sxs-lookup"><span data-stu-id="4aeea-104">There are two ways you can define an ODBC data source name:</span></span>  
  
-   <span data-ttu-id="4aeea-105">在用戶端電腦上，開啟 [控制台] 中的 [系統管理工具]，然後按兩下 [\*\*資料來源] ([ODBC) \*\*]。</span><span class="sxs-lookup"><span data-stu-id="4aeea-105">On a client computer, open Administrative Tools in Control Panel, and double-click **Data Sources (ODBC)**.</span></span> <span data-ttu-id="4aeea-106">這樣會開啟「ODBC 資料來源管理員」來建立 DSN。</span><span class="sxs-lookup"><span data-stu-id="4aeea-106">This will open the ODBC Data Source Administrator, which you can use to create a DSN.</span></span>  
  
-   <span data-ttu-id="4aeea-107">在 ODBC 應用程式中，呼叫[SQLConfigDataSource](../native-client-odbc-api/sqlconfigdatasource.md)。</span><span class="sxs-lookup"><span data-stu-id="4aeea-107">In an ODBC application, call [SQLConfigDataSource](../native-client-odbc-api/sqlconfigdatasource.md).</span></span>  
  
 <span data-ttu-id="4aeea-108">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料來源包含：</span><span class="sxs-lookup"><span data-stu-id="4aeea-108">A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data source contains:</span></span>  
  
-   <span data-ttu-id="4aeea-109">資料來源的名稱。</span><span class="sxs-lookup"><span data-stu-id="4aeea-109">The name of the data source.</span></span>  
  
-   <span data-ttu-id="4aeea-110">連接到特定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體所需的任何資訊。</span><span class="sxs-lookup"><span data-stu-id="4aeea-110">Any information needed to connect to a specific instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="4aeea-111">在特定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體上所使用的預設資料庫 (選擇性)。</span><span class="sxs-lookup"><span data-stu-id="4aeea-111">The default database to use on a specific instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (optional).</span></span>  
  
-   <span data-ttu-id="4aeea-112">要使用哪些 ANSI 選項、是否要記錄效能統計資料等等的設定 (選擇性)。</span><span class="sxs-lookup"><span data-stu-id="4aeea-112">Settings such as which ANSI options to use, whether to log performance statistics, and so on (optional).</span></span>  
  
 <span data-ttu-id="4aeea-113">透過資料來源連接時，不需要 ODBC 應用程式。</span><span class="sxs-lookup"><span data-stu-id="4aeea-113">An ODBC application is not required to connect through a data source.</span></span> <span data-ttu-id="4aeea-114">不過，應用程式必須提供相同的連接資訊給驅動程式會在 DSN 中找到的 ODBC 連接函數。</span><span class="sxs-lookup"><span data-stu-id="4aeea-114">However, the application must provide the same connectivity information to an ODBC connect function that the driver would otherwise find in a DSN.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4aeea-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4aeea-115">See Also</span></span>  
 [<span data-ttu-id="4aeea-116">與 SQL Server &#40;ODBC&#41;通訊</span><span class="sxs-lookup"><span data-stu-id="4aeea-116">Communicating with SQL Server &#40;ODBC&#41;</span></span>](communicating-with-sql-server-odbc.md)  
  
  
