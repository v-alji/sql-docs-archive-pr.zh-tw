---
title: Developer&#39;s 指南 (Replication) |Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: reference
helpviewer_keywords:
- developer's guide [SQL Server replication]
- programming [SQL Server replication]
- replication [SQL Server], development
ms.assetid: 7ee134ae-1cab-4a35-8017-8ac6d8fc64b6
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d9651aec1f02d19ea3494abf242f75049a4f33f8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705070"
---
# <a name="developer39s-guide-replication"></a><span data-ttu-id="dcb69-102">開發人員&#39;s 指南 (複寫) </span><span class="sxs-lookup"><span data-stu-id="dcb69-102">Developer&#39;s Guide (Replication)</span></span>
  <span data-ttu-id="dcb69-103">以程式設計的方式設定、維護和監視複寫拓撲的能力，可讓您同時簡化重複的複寫工作，並改善複寫為主的應用程式之使用者經驗。</span><span class="sxs-lookup"><span data-stu-id="dcb69-103">The ability to programmatically configure, maintain, and monitor a replication topology enables you to both simplify repeated replication tasks and improve the user experience for your replication-based applications.</span></span> <span data-ttu-id="dcb69-104">透過設計複寫的程式，一般使用者即可使用自訂的複寫功能，而不須熟悉複寫預存程序和複寫代理程式可執行檔，或是不須使用 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 實作的複寫使用者介面。</span><span class="sxs-lookup"><span data-stu-id="dcb69-104">By programming replication, your end-users can be provided with customized replication functionalities without having to be familiar with replication stored procedures and replication agent executables or having to using the replication user interface implemented by [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="dcb69-105">以下是您的應用程式可能從用程式存取複寫服務獲益的狀況：</span><span class="sxs-lookup"><span data-stu-id="dcb69-105">The following are scenarios in which your applications might benefit from programmatic access to replication services:</span></span>  
  
-   <span data-ttu-id="dcb69-106">將複寫功能加入現有一般使用者應用程式，例如在使用者按一下按鈕時，同步處埋提取訂閱。</span><span class="sxs-lookup"><span data-stu-id="dcb69-106">Adding replication functionalities to an existing end-user application, such as synchronizing a pull subscription when the user clicks a button.</span></span>   
-   <span data-ttu-id="dcb69-107">建立供遠端管理複寫使用的網路架構使用者介面。</span><span class="sxs-lookup"><span data-stu-id="dcb69-107">Creating a Web-based user interface for remotely administering replication.</span></span>    
-   <span data-ttu-id="dcb69-108">建立只公開管理功能子集的自訂使用者介面，可用以從單一位置遠端管理多個複寫拓撲，或是可結合管理與同步處理功能。</span><span class="sxs-lookup"><span data-stu-id="dcb69-108">Creating a custom user interface that exposes only a subset of administration functionality, can be used to remotely administer multiple replication topologies from a single location, or that combine administration and synchronization functionalities.</span></span>    
-   <span data-ttu-id="dcb69-109">透過加入監視發行集、訂閱或是在散發者端的狀態之能力，來改善現有的監視工具。</span><span class="sxs-lookup"><span data-stu-id="dcb69-109">Improving an existing monitoring tool by adding the ability to monitor the status of a publication, subscription, or at the Distributor.</span></span>    
-   <span data-ttu-id="dcb69-110">建立自訂應用程式以管理訂閱，或是將它們同步處理至 Oracle 發行者。</span><span class="sxs-lookup"><span data-stu-id="dcb69-110">Creating a custom application to administer or synchronize subscriptions to an Oracle publisher.</span></span>    
-   <span data-ttu-id="dcb69-111">當同步處理合併式訂閱時，會寫入執行的自訂商務邏輯規則。</span><span class="sxs-lookup"><span data-stu-id="dcb69-111">Writing customized business rules that are executed when a merge subscription is synchronized.</span></span>    
-   <span data-ttu-id="dcb69-112">在設定新的訂閱者時，會產生可重複執行的 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 指令碼。</span><span class="sxs-lookup"><span data-stu-id="dcb69-112">Generating [!INCLUDE[tsql](../../../includes/tsql-md.md)] scripts that can be run repeated when configuring new Subscribers.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="dcb69-113">可讓您以程式設計的方式控制複寫代理程式，並以程式設計的方式管理和監視複寫拓撲。</span><span class="sxs-lookup"><span data-stu-id="dcb69-113">enables you to programmatically control replication agents and to programmatically administer and monitor a replication topology.</span></span> <span data-ttu-id="dcb69-114">若要深入了解程式設計複寫，請參閱[複寫程式設計概念](replication-programming-concepts.md)。</span><span class="sxs-lookup"><span data-stu-id="dcb69-114">To learn more about programming replication, see [Replication Programming Concepts](replication-programming-concepts.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="dcb69-115">本節內容</span><span class="sxs-lookup"><span data-stu-id="dcb69-115">In This Section</span></span>  
 [<span data-ttu-id="dcb69-116">複寫程式設計概念</span><span class="sxs-lookup"><span data-stu-id="dcb69-116">Replication Programming Concepts</span></span>](replication-programming-concepts.md)  
 <span data-ttu-id="dcb69-117">描述開發使用複寫之應用程式的規劃步驟。</span><span class="sxs-lookup"><span data-stu-id="dcb69-117">Describes the planning steps to develop an application that uses replication.</span></span>  
  
 [<span data-ttu-id="dcb69-118">Replication System Stored Procedures Concepts</span><span class="sxs-lookup"><span data-stu-id="dcb69-118">Replication System Stored Procedures Concepts</span></span>](replication-system-stored-procedures-concepts.md)  
 <span data-ttu-id="dcb69-119">描述如何使用系統預存程序，在應用程式拓撲中提供程式存取。</span><span class="sxs-lookup"><span data-stu-id="dcb69-119">Describes how system stored procedures can be used to proivide programmatic access in a replication topology.</span></span>  
  
 [<span data-ttu-id="dcb69-120">複寫管理物件概念</span><span class="sxs-lookup"><span data-stu-id="dcb69-120">Replication Management Objects Concepts</span></span>](replication-management-objects-concepts.md)  
 <span data-ttu-id="dcb69-121">說明使用 Replication Management Objects (RMO) 的概念。</span><span class="sxs-lookup"><span data-stu-id="dcb69-121">Explains the concepts for using Replication Management Objects (RMO).</span></span> <span data-ttu-id="dcb69-122">這是一種 Managed 程式碼組件，用以封裝 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的複寫功能。</span><span class="sxs-lookup"><span data-stu-id="dcb69-122">This is a managed code assembly that encapsulates replication functionalities for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="dcb69-123">Replication Agent Executables Concepts</span><span class="sxs-lookup"><span data-stu-id="dcb69-123">Replication Agent Executables Concepts</span></span>](replication-agent-executables-concepts.md)  
 <span data-ttu-id="dcb69-124">描述複寫代理程式可執行檔的使用。</span><span class="sxs-lookup"><span data-stu-id="dcb69-124">Describes the use of Replication Agent Executable files.</span></span>  

  
  
