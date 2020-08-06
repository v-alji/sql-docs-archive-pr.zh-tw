---
title: " (ODBC) 執行交易 |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, transactions
- transactions [ODBC]
- ODBC, transactions
ms.assetid: f431191a-5762-4f0b-85bb-ac99aff29724
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 8abc09c9395225dd653a072fd6c25dadce0849b2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708597"
---
# <a name="performing-transactions-odbc"></a><span data-ttu-id="7f8e3-102">執行交易 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="7f8e3-102">Performing Transactions (ODBC)</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="7f8e3-103">和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 驅動程式可支援 ODBC API 交易管理函數。</span><span class="sxs-lookup"><span data-stu-id="7f8e3-103">and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver support the ODBC API transaction management functions.</span></span> [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="7f8e3-104">針對個別伺服器上的本機交易提供了完整的支援。</span><span class="sxs-lookup"><span data-stu-id="7f8e3-104">offers full support for local transactions on an individual server.</span></span> <span data-ttu-id="7f8e3-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 驅動程式會使用這些功能來支援可管理交易的 ODBC API 函數。</span><span class="sxs-lookup"><span data-stu-id="7f8e3-105">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver uses these features to support the ODBC API functions that manage transactions.</span></span>  
  
 <span data-ttu-id="7f8e3-106">透過 Microsoft 分散式交易協調器 (MS DTC) 的使用，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 驅動程式可以參與跨越多部伺服器的分散式交易。</span><span class="sxs-lookup"><span data-stu-id="7f8e3-106">Through the use of the Microsoft Distributed Transaction Coordinator (MS DTC), the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver can participate in distributed transactions spanning multiple servers.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7f8e3-107">本節內容</span><span class="sxs-lookup"><span data-stu-id="7f8e3-107">In This Section</span></span>  
  
-   [<span data-ttu-id="7f8e3-108">ODBC 中的交易</span><span class="sxs-lookup"><span data-stu-id="7f8e3-108">Transactions in ODBC</span></span>](../../relational-databases/native-client/odbc/performing-transactions-in-odbc.md)  
  
-   [<span data-ttu-id="7f8e3-109">執行分散式交易</span><span class="sxs-lookup"><span data-stu-id="7f8e3-109">Performing Distributed Transactions</span></span>](../../relational-databases/native-client-ole-db-transactions/transactions.md)  
  
  
