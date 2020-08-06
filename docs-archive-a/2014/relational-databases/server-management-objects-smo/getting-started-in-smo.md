---
title: SMO 中的消費者入門 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Management Objects, about SQL Server Management Objects
- SMO [SQL Server], about SQL Server Management Objects
ms.assetid: ecc62702-c0d5-4180-b3c2-16ec5030caa7
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4d90911932b5f9bfc91368e70e66d2b227a3964f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597768"
---
# <a name="getting-started-in-smo"></a><span data-ttu-id="f56cb-102">SMO 使用者入門</span><span class="sxs-lookup"><span data-stu-id="f56cb-102">Getting Started in SMO</span></span>
  <span data-ttu-id="f56cb-103">本主題包含開始使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 管理物件 (SMO) 的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="f56cb-103">This topic contains information about getting started using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Objects (SMO).</span></span> <span data-ttu-id="f56cb-104">SMO 段落是針對開發人員所寫的。</span><span class="sxs-lookup"><span data-stu-id="f56cb-104">The SMO section is aimed at developers.</span></span> <span data-ttu-id="f56cb-105">下列清單將可幫助您尋找 SMO 物件階層、如何準備在 SMO 中撰寫程式、如何開始使用不同程式語言撰寫 SMO 程式以及一般和特定程式設計工作的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="f56cb-105">The following list will help you to locate information about the SMO object hierarchy, how to prepare for writing programs in SMO, how to start writing an SMO program in different programming languages, and general and specific programming tasks.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f56cb-106">**準備 SMO**</span><span class="sxs-lookup"><span data-stu-id="f56cb-106">**Preparing for SMO**</span></span><br /><br /> <span data-ttu-id="f56cb-107">-   [針對 SMO 進行準備](../../database-engine/dev-guide/preparing-to-use-smo.md)，會提供有關系統需求、安裝和 sql-dmo 比較的資訊。</span><span class="sxs-lookup"><span data-stu-id="f56cb-107">-   [Preparing for SMO](../../database-engine/dev-guide/preparing-to-use-smo.md) provides information about system requirements, installation, and comparisons with SQL-DMO.</span></span><br /><br /> <span data-ttu-id="f56cb-108">**物件模型**</span><span class="sxs-lookup"><span data-stu-id="f56cb-108">**Object Model**</span></span><br /><br /> <span data-ttu-id="f56cb-109">-[物件模型](smo-object-model.md)描述 SMO 物件階層，以及物件彼此之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="f56cb-109">-   The [Object Model](smo-object-model.md) describes the SMO object hierarchy and how the objects relate to one another.</span></span><br /><br /> <span data-ttu-id="f56cb-110">**程式設計語言**</span><span class="sxs-lookup"><span data-stu-id="f56cb-110">**Programming Languages**</span></span><br /><br /> <span data-ttu-id="f56cb-111">-   程式[設計語言](smo-programming-languages.md)描述程式設計環境，並包含以 c # 和 Visual Basic 開始撰寫 SMO 程式的詳細程式。</span><span class="sxs-lookup"><span data-stu-id="f56cb-111">-   [Programming Languages](smo-programming-languages.md) describes the programming environment and includes detailed procedures to start writing an SMO program in C# and Visual Basic.</span></span>|<span data-ttu-id="f56cb-112">**SMO 中的一般程式設計**</span><span class="sxs-lookup"><span data-stu-id="f56cb-112">**General Programming in SMO**</span></span><br /><br /> <span data-ttu-id="f56cb-113">-   [Smo 的一般程式設計](create-program/creating-smo-programs.md)是使用 smo 進行程式設計的簡介。</span><span class="sxs-lookup"><span data-stu-id="f56cb-113">-   [General Programming in SMO](create-program/creating-smo-programs.md) is an introduction to programming with SMO.</span></span> <span data-ttu-id="f56cb-114">本主題描述如何連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體，以及如何使用屬性、方法和集合。</span><span class="sxs-lookup"><span data-stu-id="f56cb-114">This topic describes how to connect to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], and how to use properties, methods, and collections.</span></span> <span data-ttu-id="f56cb-115">更進階的主題會描述資料類型、交易、設定擷取模式和事件以及例外狀況處理。</span><span class="sxs-lookup"><span data-stu-id="f56cb-115">More advanced topics describe data types, transactions, setting the capture mode, and event and exception handling.</span></span><br /><br /> <span data-ttu-id="f56cb-116">**程式設計特有的工作**</span><span class="sxs-lookup"><span data-stu-id="f56cb-116">**Programming Specific Tasks**</span></span><br /><br /> <span data-ttu-id="f56cb-117">-程式[設計特定](tasks/programming-specific-tasks.md)工作一節包含有關如何使用 SMO 來設計特定工作的概念和程式。</span><span class="sxs-lookup"><span data-stu-id="f56cb-117">-   The [Programming Specific Tasks](tasks/programming-specific-tasks.md) section contains concepts and procedures about how to program specific tasks by using SMO.</span></span> <span data-ttu-id="f56cb-118">此主題也描述 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的完整程式設計管理。</span><span class="sxs-lookup"><span data-stu-id="f56cb-118">The topic also describes complete programmatic management of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>|  
  
  
