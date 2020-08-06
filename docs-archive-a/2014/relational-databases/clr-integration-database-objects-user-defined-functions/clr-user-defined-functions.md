---
title: CLR 使用者定義函數 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- building database objects [CLR integration], user-defined functions
- functions [CLR integration]
- common language runtime [SQL Server], user-defined functions
- database objects [CLR integration], user-defined functions
- user-defined functions [CLR integration]
ms.assetid: 6f7491f1-9a46-4146-ae09-056248634de2
author: rothja
ms.author: jroth
ms.openlocfilehash: ba7a4a983ec0cb36ef0fd79df44491f7f23f7648
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598451"
---
# <a name="clr-user-defined-functions"></a><span data-ttu-id="f2dcf-102">CLR 使用者定義函式</span><span class="sxs-lookup"><span data-stu-id="f2dcf-102">CLR User-Defined Functions</span></span>
  <span data-ttu-id="f2dcf-103">使用者定義函數是可以使用參數、執行計算或其他動作，並傳回結果的常式。</span><span class="sxs-lookup"><span data-stu-id="f2dcf-103">User-defined functions are routines that can take parameters, perform calculations or other actions, and return a result.</span></span> <span data-ttu-id="f2dcf-104">從 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 開始，您可以使用任何 [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework 程式設計語言 (例如，[!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic .NET 或 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C#) 撰寫使用者定義函數。</span><span class="sxs-lookup"><span data-stu-id="f2dcf-104">Beginning with [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], you can write user-defined functions in any [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework programming language, such as [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic .NET or [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C#.</span></span>  
  
 <span data-ttu-id="f2dcf-105">函數有兩種類型：傳回單一值的純量值函式，以及傳回一組資料列的資料表值函式。</span><span class="sxs-lookup"><span data-stu-id="f2dcf-105">There are two types of functions: scalar, which returns a single value, and table-valued, which returns a set of rows.</span></span>  
  
 <span data-ttu-id="f2dcf-106">下表列出本節的主題。</span><span class="sxs-lookup"><span data-stu-id="f2dcf-106">The following table lists the topics in this section.</span></span>  
  
 [<span data-ttu-id="f2dcf-107">CLR 純量值函式</span><span class="sxs-lookup"><span data-stu-id="f2dcf-107">CLR Scalar-Valued Functions</span></span>](clr-scalar-valued-functions.md)  
 <span data-ttu-id="f2dcf-108">涵蓋純量值函式的實作需求與範例。</span><span class="sxs-lookup"><span data-stu-id="f2dcf-108">Covers implementation requirements and examples of scalar-valued functions.</span></span>  
  
 [<span data-ttu-id="f2dcf-109">CLR 資料表值函式</span><span class="sxs-lookup"><span data-stu-id="f2dcf-109">CLR Table-Valued Functions</span></span>](clr-table-valued-functions.md)  
 <span data-ttu-id="f2dcf-110">討論如何實作與使用資料表值函式 (TVF)，以及 [!INCLUDE[tsql](../../includes/tsql-md.md)] 和 Common Language Runtime (CLR) TVF 之間的差異。</span><span class="sxs-lookup"><span data-stu-id="f2dcf-110">Discusses how to implement and use table-valued functions (TVFs), as well as differences between [!INCLUDE[tsql](../../includes/tsql-md.md)] and common language runtime (CLR) TVFs.</span></span>  
  
 [<span data-ttu-id="f2dcf-111">CLR 使用者定義彙總</span><span class="sxs-lookup"><span data-stu-id="f2dcf-111">CLR User-Defined Aggregates</span></span>](clr-user-defined-aggregates.md)  
 <span data-ttu-id="f2dcf-112">描述如何實作及使用使用者定義彙總。</span><span class="sxs-lookup"><span data-stu-id="f2dcf-112">Describes how to implement and use user-defined aggregates.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2dcf-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f2dcf-113">See Also</span></span>  
 [<span data-ttu-id="f2dcf-114">使用者定義的函式</span><span class="sxs-lookup"><span data-stu-id="f2dcf-114">User-Defined Functions</span></span>](../user-defined-functions/user-defined-functions.md)  
  
  
