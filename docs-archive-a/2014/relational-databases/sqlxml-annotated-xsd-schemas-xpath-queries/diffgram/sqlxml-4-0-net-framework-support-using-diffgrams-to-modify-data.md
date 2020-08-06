---
title: 使用 Diffgram 來修改 SQLXML 4.0 中的資料 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- data deletions [SQLXML]
- updating data [SQLXML]
- DiffGrams [SQLXML]
- modifying data [SQLXML]
- .NET Framework [SQLXML], DiffGrams
- XML [SQLXML]
- database modifications [SQLXML]
- data updates [SQLXML]
- data modifications [SQLXML]
- record insertion [SQLXML]
- SQLXML, DiffGrams
- deleting data
- record updates [SQLXML]
- record deletions [SQLXML]
ms.assetid: 48b8a8f9-f3af-404f-8c84-f4c3703364d9
author: rothja
ms.author: jroth
ms.openlocfilehash: cc2e24304679a7648f18148eb45f33b9bf719a9f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596589"
---
# <a name="using-diffgrams-to-modify-data-in-sqlxml-40"></a><span data-ttu-id="17eb0-102">使用 DiffGram 來修改 SQLXML 4.0 中的資料</span><span class="sxs-lookup"><span data-stu-id="17eb0-102">Using DiffGrams to Modify Data in SQLXML 4.0</span></span>
  <span data-ttu-id="17eb0-103">DiffGram 格式是在 .NET Framework 的**資料集**元件中引進 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="17eb0-103">The DiffGram format is introduced in the **DataSet** component of the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework.</span></span> <span data-ttu-id="17eb0-104">您可以在 .NET Framework 內建立 DiffGram，並用其修改 Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 資料庫中資料表的資料。</span><span class="sxs-lookup"><span data-stu-id="17eb0-104">Within the .NET Framework, you can create DiffGrams and use them to modify data in tables in a Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="17eb0-105">本章節也提供 DiffGram 的簡介以及使用方法的範例。</span><span class="sxs-lookup"><span data-stu-id="17eb0-105">This section provides a brief introduction to DiffGrams and examples of how to use them.</span></span> <span data-ttu-id="17eb0-106">這裡假設您熟悉 .NET Framework 中的 DiffGram。</span><span class="sxs-lookup"><span data-stu-id="17eb0-106">It is assumed that you are familiar with DiffGrams in the .NET Framework.</span></span> <span data-ttu-id="17eb0-107">在此文件集中，主要焦點在於 SQLXML 特有的 DiffGram 問題。</span><span class="sxs-lookup"><span data-stu-id="17eb0-107">In this documentation, the primary focus is on DiffGram issues that are specific to SQLXML.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="17eb0-108">本節內容</span><span class="sxs-lookup"><span data-stu-id="17eb0-108">In This Section</span></span>  
 [<span data-ttu-id="17eb0-109">DiffGrams 的 SQLXML 4.0 簡介</span><span class="sxs-lookup"><span data-stu-id="17eb0-109">Introduction to DiffGrams in SQLXML 4.0</span></span>](introduction-to-diffgrams-in-sqlxml-4-0.md)  
 <span data-ttu-id="17eb0-110">提供有關 Diffgram 的基本資訊。</span><span class="sxs-lookup"><span data-stu-id="17eb0-110">Provides basic information about Diffgrams.</span></span>  
  
 [<span data-ttu-id="17eb0-111">&#40;SQLXML 4.0&#41;的 DiffGram 範例</span><span class="sxs-lookup"><span data-stu-id="17eb0-111">DiffGram Examples &#40;SQLXML 4.0&#41;</span></span>](diffgram-examples-sqlxml-4-0.md)  
 <span data-ttu-id="17eb0-112">提供使用 Diffgram 的範例。</span><span class="sxs-lookup"><span data-stu-id="17eb0-112">Provides examples of using Diffgrams.</span></span>  
  
 [<span data-ttu-id="17eb0-113">使用 ADO 執行 DiffGram &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="17eb0-113">Executing a DiffGram by Using ADO &#40;SQLXML 4.0&#41;</span></span>](executing-a-diffgram-by-using-ado-sqlxml-4-0.md)  
 <span data-ttu-id="17eb0-114">提供使用 ActiveX Data Objects (ADO) 執行 Diffgram 的範例。</span><span class="sxs-lookup"><span data-stu-id="17eb0-114">Provides an example of executing a Diffgram with ActiveX Data Objects (ADO).</span></span>  
  
 [<span data-ttu-id="17eb0-115">使用 SQLXML Managed 類別執行 DiffGram</span><span class="sxs-lookup"><span data-stu-id="17eb0-115">Executing a DiffGram by Using SQLXML Managed Classes</span></span>](../net-framework-classes/sqlxml-4-0-net-framework-support-managed-classes.md)  
 <span data-ttu-id="17eb0-116">提供使用 SQLXML Managed Classes 執行 Diffgram 的範例。</span><span class="sxs-lookup"><span data-stu-id="17eb0-116">Provides an example of executing a Diffgram with SQLXML Managed Classes.</span></span>  
  
  
