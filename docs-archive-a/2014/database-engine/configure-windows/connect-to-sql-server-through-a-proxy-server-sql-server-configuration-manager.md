---
title: 透過 Proxy 伺服器連接到 SQL Server (SQL Server 組態管理員) |Microsoft Docs
ms.custom: ''
ms.date: 06/22/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- Remote WinSock
- RWS
- LATs
- proxy servers [SQL Server]
- connections [SQL Server], proxy server
- Microsoft Proxy Server [SQL Server]
- local address tables [SQL Server]
ms.assetid: 39714de0-2a1f-4179-9091-5c3fa4612545
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: de22ad6043c509f08471a6bea40c0efa18d76842
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597328"
---
# <a name="connect-to-sql-server-through-a-proxy-server-sql-server-configuration-manager"></a><span data-ttu-id="e6b9e-102">經由 Proxy 伺服器連接至 SQL Server (SQL Server 組態管理員)</span><span class="sxs-lookup"><span data-stu-id="e6b9e-102">Connect to SQL Server Through a Proxy Server (SQL Server Configuration Manager)</span></span>
  <span data-ttu-id="e6b9e-103">此主題描述如何使用 SQL Server 組態管理員，在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中透過 Proxy 伺服器連接到 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="e6b9e-103">This topic describes how to connect to SQL Server through a proxy server in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using SQL Server Configuration Manager.</span></span> <span data-ttu-id="e6b9e-104">若要使用遠端 WinSock (RWS) 的方法進行遠端接聽，請定義 Proxy Server 的本機位址資料表 (LAT)，使接聽節點位址在 LAT 項目範圍之外。</span><span class="sxs-lookup"><span data-stu-id="e6b9e-104">To listen remotely by way of Remote WinSock (RWS), define the local address table (LAT) for the proxy server so that the listening node address is outside the range of LAT entries.</span></span>  
  
##  <a name="using-sql-server-configuration-manager"></a><a name="SSMSProcedure"></a> <span data-ttu-id="e6b9e-105">使用 SQL Server 組態管理員</span><span class="sxs-lookup"><span data-stu-id="e6b9e-105">Using SQL Server Configuration Manager</span></span>  
  
#### <a name="to-enable-connections-to-sql-server-through-microsoft-proxy-server"></a><span data-ttu-id="e6b9e-106">若要透過 Microsoft Proxy Server 連接到 SQL Server</span><span class="sxs-lookup"><span data-stu-id="e6b9e-106">To enable connections to SQL Server through Microsoft Proxy Server</span></span>  
  
1.  <span data-ttu-id="e6b9e-107">請遵循[設定伺服器接聽特定 TCP 通訊埠 &#40;SQL Server 組態管理員&#41;](configure-a-server-to-listen-on-a-specific-tcp-port.md) 中的步驟，來判斷 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 所使用的 TCP/IP 通訊埠為何，或是將 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 設定為使用指定的通訊埠。</span><span class="sxs-lookup"><span data-stu-id="e6b9e-107">Follow the steps in [Configure a Server to Listen on a Specific TCP Port &#40;SQL Server Configuration Manager&#41;](configure-a-server-to-listen-on-a-specific-tcp-port.md) to determine which TCP/IP ports are used by the [!INCLUDE[ssDE](../../includes/ssde-md.md)], or to configure the [!INCLUDE[ssDE](../../includes/ssde-md.md)] to use a desired port.</span></span>  
  
2.  <span data-ttu-id="e6b9e-108">在您的 Proxy 伺服器中，定義 Proxy 伺服器的本機位址資料表 (LAT)，使接聽節點位址不在 LAT 項目的範圍內。</span><span class="sxs-lookup"><span data-stu-id="e6b9e-108">In your proxy server define the local address table (LAT) for the proxy server so that the listening node address is outside the range of LAT entries.</span></span> <span data-ttu-id="e6b9e-109">如需詳細資訊，請參閱您的 Proxy 伺服器文件集。</span><span class="sxs-lookup"><span data-stu-id="e6b9e-109">For more information, see your proxy server documentation.</span></span>  
  
  
