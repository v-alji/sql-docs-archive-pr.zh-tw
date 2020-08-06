---
title: 初始化訂閱 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- snapshot replication [SQL Server], initializing subscriptions
- transactional replication, initializing subscriptions
- initializing subscriptions [SQL Server replication]
- subscriptions [SQL Server replication], initializing
- initializing subscriptions [SQL Server replication], about initializing subscriptions
- merge replication [SQL Server replication], initializing subscriptions
ms.assetid: d6013845-cb7a-4203-8e21-edce32f1d330
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1f024d360fdeab477ace09970b4f140a97696c2c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585826"
---
# <a name="initialize-a-subscription"></a><span data-ttu-id="85370-102">初始化訂閱</span><span class="sxs-lookup"><span data-stu-id="85370-102">Initialize a Subscription</span></span>
  <span data-ttu-id="85370-103">複寫拓撲中的訂閱者必須初始化，使得它們具有已訂閱發行集中各發行項之結構描述副本和所有需要的複寫物件，例如預存程序、觸發程序和中繼資料表。</span><span class="sxs-lookup"><span data-stu-id="85370-103">Subscribers in a replication topology must be initialized, so that they have a copy of the schema from each article in the publication they have subscribed to and any replication objects that are required, such as stored procedures, triggers, and metadata tables.</span></span> <span data-ttu-id="85370-104">另外，「訂閱者」通常會接收初始資料集。</span><span class="sxs-lookup"><span data-stu-id="85370-104">In addition, the Subscriber typically receives an initial dataset.</span></span> <span data-ttu-id="85370-105">預設初始化方法會使用包含結構描述、複寫物件和資料的完整快照集，但是沒有完整的快照集也可以初始化發行集。</span><span class="sxs-lookup"><span data-stu-id="85370-105">The default initialization method uses a full snapshot that includes schema, replication objects, and data, but publications can also be initialized without a full snapshot.</span></span>  
  
 <span data-ttu-id="85370-106">如需相關資訊，請參閱 [Initialize a Subscription with a Snapshot](initialize-a-subscription-with-a-snapshot.md) 及 [Initialize a Transactional Subscription Without a Snapshot](initialize-a-transactional-subscription-without-a-snapshot.md)。</span><span class="sxs-lookup"><span data-stu-id="85370-106">For more information, see [Initialize a Subscription with a Snapshot](initialize-a-subscription-with-a-snapshot.md) and [Initialize a Transactional Subscription Without a Snapshot](initialize-a-transactional-subscription-without-a-snapshot.md).</span></span>  
  
  
