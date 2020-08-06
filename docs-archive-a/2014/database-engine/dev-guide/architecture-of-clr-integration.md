---
title: CLR 整合的架構 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
helpviewer_keywords:
- common language runtime [SQL Server], architecture
- architecture [CLR integration]
ms.assetid: 05e4b872-3d21-46de-b4d5-739b5f2a0cf9
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: bb32e2c7f5eb2079146a2fee64af2e2dbc1d3356
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593548"
---
# <a name="architecture-of-clr-integration"></a><span data-ttu-id="837fc-102">CLR 整合的架構</span><span class="sxs-lookup"><span data-stu-id="837fc-102">Architecture of CLR Integration</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="837fc-103">與 .NET Framework Common Language Runtime (CLR) 整合可讓資料庫程式設計人員使用 Visual C#、Visual Basic .NET 和 Visual C++ 等語言。</span><span class="sxs-lookup"><span data-stu-id="837fc-103">integration with the .NET Framework common language runtime (CLR) enables database programmers to use languages such as Visual C#, Visual Basic .NET, and Visual C++.</span></span> <span data-ttu-id="837fc-104">程式設計人員可以使用這些語言所撰寫的商務邏輯種類包括函數、預存程序、觸發程序、資料類型和彙總。</span><span class="sxs-lookup"><span data-stu-id="837fc-104">Functions, stored procedures, triggers, data types, and aggregates are among the kinds of business logic that programmers can write with these languages.</span></span>  
  
 <span data-ttu-id="837fc-105">本節將描述 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 內部的 CLR 整合架構，以及這個架構如何提供安全、可擴充、可靠且有效率的環境來執行使用者程式碼。</span><span class="sxs-lookup"><span data-stu-id="837fc-105">This section describes the architecture of CLR integration inside [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and how this architecture provides a safe, scalable, secure, and efficient environment to run user code.</span></span>  
  
 <span data-ttu-id="837fc-106">下表列出本節的主題。</span><span class="sxs-lookup"><span data-stu-id="837fc-106">The following table lists the topics in this section.</span></span>  
  
 [<span data-ttu-id="837fc-107">CLR 主控環境</span><span class="sxs-lookup"><span data-stu-id="837fc-107">CLR Hosted Environment</span></span>](../../relational-databases/clr-integration/clr-integration-architecture-clr-hosted-environment.md)  
 <span data-ttu-id="837fc-108">描述 CLR 整合的架構設計目標、機制和優點。</span><span class="sxs-lookup"><span data-stu-id="837fc-108">Discusses architectural design goals, mechanisms, and benefits of CLR integration.</span></span>  
  
 [<span data-ttu-id="837fc-109">CLR 整合的效能</span><span class="sxs-lookup"><span data-stu-id="837fc-109">Performance of CLR Integration</span></span>](../../relational-databases/clr-integration/clr-integration-architecture-performance.md)  
 <span data-ttu-id="837fc-110">涵蓋 CLR 整合架構的效能考量。</span><span class="sxs-lookup"><span data-stu-id="837fc-110">Covers performance considerations of the CLR integration architecture.</span></span>  
  
  
