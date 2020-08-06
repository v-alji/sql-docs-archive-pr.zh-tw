---
title: ODBC 連線管理員 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- connections [Integration Services], ODBC
- ODBC connection manager
- data sources [Integration Services], connections
- connection managers [Integration Services], ODBC
ms.assetid: e8c77aa7-6772-485e-918e-cef9eeb18c58
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e1069e31f3f8ffaf14dde091d913ff6d9f8fa7cc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594633"
---
# <a name="odbc-connection-manager"></a><span data-ttu-id="c99ae-102">ODBC 連接管理員</span><span class="sxs-lookup"><span data-stu-id="c99ae-102">ODBC Connection Manager</span></span>
  <span data-ttu-id="c99ae-103">ODBC 連接管理員可使用「開放式資料庫連接 (ODBC)」規格，讓封裝連接到各種資料庫管理系統。</span><span class="sxs-lookup"><span data-stu-id="c99ae-103">An ODBC connection manager enables a package to connect to a variety of database management systems using the Open Database Connectivity specification (ODBC).</span></span>  
  
 <span data-ttu-id="c99ae-104">當您將 ODBC 連接加入封裝並設定連線管理員屬性時，會建立連線管理員， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 並將連線管理員加入 `Connections` 封裝的集合。</span><span class="sxs-lookup"><span data-stu-id="c99ae-104">When you add an ODBC connection to a package and set the connection manager properties, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] creates a connection manager and adds the connection manager to the `Connections` collection of the package.</span></span> <span data-ttu-id="c99ae-105">在執行階段，連接管理員會解析為實體 ODBC 連接。</span><span class="sxs-lookup"><span data-stu-id="c99ae-105">At run time the connection manager is resolved as a physical ODBC connection.</span></span>  
  
 <span data-ttu-id="c99ae-106">連接管理員的 `ConnectionManagerType` 屬性會設為 `ODBC`。</span><span class="sxs-lookup"><span data-stu-id="c99ae-106">The `ConnectionManagerType` property of the connection manager is set to `ODBC`.</span></span>  
  
 <span data-ttu-id="c99ae-107">您可以利用下列方式設定 ODBC 連接管理員：</span><span class="sxs-lookup"><span data-stu-id="c99ae-107">You can configure the ODBC connection manager in the following ways:</span></span>  
  
-   <span data-ttu-id="c99ae-108">提供參考使用者或系統資料來源名稱的連接字串。</span><span class="sxs-lookup"><span data-stu-id="c99ae-108">Provide a connection string that references a user or system data source name.</span></span>  
  
-   <span data-ttu-id="c99ae-109">指定要連接的伺服器。</span><span class="sxs-lookup"><span data-stu-id="c99ae-109">Specify the server to connect to.</span></span>  
  
-   <span data-ttu-id="c99ae-110">指示在執行階段是否保留連接。</span><span class="sxs-lookup"><span data-stu-id="c99ae-110">Indicate whether the connection is retained at run time.</span></span>  
  
## <a name="configuration-of-the-odbc-connection-manager"></a><span data-ttu-id="c99ae-111">設定 ODBC 連接管理員</span><span class="sxs-lookup"><span data-stu-id="c99ae-111">Configuration of the ODBC Connection Manager</span></span>  
 <span data-ttu-id="c99ae-112">您可以透過 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師或以程式設計方式設定屬性。</span><span class="sxs-lookup"><span data-stu-id="c99ae-112">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="c99ae-113">如需可在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師中設定之屬性的詳細資訊，請按下列其中一個主題：</span><span class="sxs-lookup"><span data-stu-id="c99ae-113">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click one of the following topic:</span></span>  
  
-   [<span data-ttu-id="c99ae-114">ODBC 連線管理員 UI 參考</span><span class="sxs-lookup"><span data-stu-id="c99ae-114">ODBC Connection Manager UI Reference</span></span>](../odbc-connection-manager-ui-reference.md)  
  
 <span data-ttu-id="c99ae-115">如需以程式設計方式設定連線管理員的資訊，請參閱 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 和 [以程式設計方式加入連接](../building-packages-programmatically/adding-connections-programmatically.md)。</span><span class="sxs-lookup"><span data-stu-id="c99ae-115">For information about configuring a connection manager programmatically, see <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> and [Adding Connections Programmatically](../building-packages-programmatically/adding-connections-programmatically.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c99ae-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c99ae-116">See Also</span></span>  
 [<span data-ttu-id="c99ae-117">Integration Services &#40;SSIS&#41; 連接</span><span class="sxs-lookup"><span data-stu-id="c99ae-117">Integration Services &#40;SSIS&#41; Connections</span></span>](integration-services-ssis-connections.md)  
  
  
