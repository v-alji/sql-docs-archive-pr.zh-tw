---
title: 資料收集器程式設計 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
helpviewer_keywords:
- data collector [SQL Server], programming
ms.assetid: 53b4752b-055d-4716-b2bc-75b4cce84101
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 9f4da839f25da8f8aab3e21fa98547eff72d2140
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709901"
---
# <a name="data-collector-programming"></a><span data-ttu-id="ddc16-102">資料收集器程式設計</span><span class="sxs-lookup"><span data-stu-id="ddc16-102">Data Collector Programming</span></span>
  <span data-ttu-id="ddc16-103"><xref:Microsoft.SqlServer.Management.Collector> 中的資料收集器 API 可透過物件模型，以程式設計的方式控制所有的組態作業。</span><span class="sxs-lookup"><span data-stu-id="ddc16-103">The data collector API, in <xref:Microsoft.SqlServer.Management.Collector>, allows programmatic control of all configuration operations through the object model.</span></span> <span data-ttu-id="ddc16-104">此外，許多使用 API 的資料收集作業都會實作為安裝在伺服器上的預存程序。</span><span class="sxs-lookup"><span data-stu-id="ddc16-104">In addition, many of the data collection operations that use the API are implemented as stored procedures that are installed on the server.</span></span>

 <span data-ttu-id="ddc16-105">下圖顯示資料收集器物件模型的重要元素。</span><span class="sxs-lookup"><span data-stu-id="ddc16-105">The following illustration shows key elements of the data collector object model.</span></span>

 <span data-ttu-id="ddc16-106">![資料收集器物件模型](../../../2014/database-engine/dev-guide/media/dc-objectmodel.gif "資料收集器物件模型")</span><span class="sxs-lookup"><span data-stu-id="ddc16-106">![The Data Collector Object Model](../../../2014/database-engine/dev-guide/media/dc-objectmodel.gif "The Data Collector Object Model")</span></span>


