---
title: Database Engine 擴充預存程序程式設計 | Microsoft 文件
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- extended stored procedures [SQL Server], programming
- stored procedures [SQL Server], extended
- Database Engine [SQL Server], stored procedures
- macros [SQL Server]
- Extended Stored Procedure API [SQL Server]
ms.assetid: 158a6765-0542-4e84-b5ab-f173d946ef5e
author: rothja
ms.author: jroth
ms.openlocfilehash: fecb8f996ddfcaede83cdb330e9c82bffdce5819
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606365"
---
# <a name="database-engine-extended-stored-procedure-programming"></a><span data-ttu-id="9514c-102">資料庫引擎擴充預存程序程式設計</span><span class="sxs-lookup"><span data-stu-id="9514c-102">Database Engine Extended Stored Procedure Programming</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="9514c-103">請改用 CLR 整合。</span><span class="sxs-lookup"><span data-stu-id="9514c-103">Use CLR Integration instead.</span></span> <span data-ttu-id="9514c-104">如需詳細資訊，請參閱 [Common Language Runtime &#40;CLR&#41; 整合程式設計概念](clr-integration/common-language-runtime-clr-integration-programming-concepts.md)。</span><span class="sxs-lookup"><span data-stu-id="9514c-104">For more information, see [Common Language Runtime &#40;CLR&#41; Integration Programming Concepts](clr-integration/common-language-runtime-clr-integration-programming-concepts.md).</span></span>  
  
 <span data-ttu-id="9514c-105">[!INCLUDE[msCoName](../includes/msconame-md.md)]擴充預存程式 API 會提供以伺服器為基礎的應用程式開發介面， (API) 以擴充 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 功能。</span><span class="sxs-lookup"><span data-stu-id="9514c-105">The [!INCLUDE[msCoName](../includes/msconame-md.md)] Extended Stored Procedure API provides a server-based application programming interface (API) for extending [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] functionality.</span></span> <span data-ttu-id="9514c-106">此 API 包含用來建置下列類別目錄中之應用程式的 C 和 C++ 函數和巨集：擴充預存程序和閘道應用程式。</span><span class="sxs-lookup"><span data-stu-id="9514c-106">The API consists of C and C++ functions and macros used to build applications in the following categories: extended stored procedures and gateway applications.</span></span>  
  
 <span data-ttu-id="9514c-107">擴充預存程序可讓您使用程式語言 (例如 C 語言) 來建立自己的外部常式。擴充預存程序對使用者而言就和一般的預存程序一樣，而且會以相同的方式執行。</span><span class="sxs-lookup"><span data-stu-id="9514c-107">Extended stored procedures allow you to create your own external routines in a programming language such as C. The extended stored procedures appear to users as typical stored procedures and are executed in the same way.</span></span> <span data-ttu-id="9514c-108">您可以將參數傳遞給擴充預存程序，而它們可以傳回結果及狀態。</span><span class="sxs-lookup"><span data-stu-id="9514c-108">Parameters can be passed to extended stored procedures, and they can return results and return status.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9514c-109">本節內容</span><span class="sxs-lookup"><span data-stu-id="9514c-109">In This Section</span></span>  
 [<span data-ttu-id="9514c-110">擴充預存程序程式設計</span><span class="sxs-lookup"><span data-stu-id="9514c-110">Programming Extended Stored Procedures</span></span>](extended-stored-procedures-programming/database-engine-extended-stored-procedures-programming.md)  
 <span data-ttu-id="9514c-111">說明如何建立、管理和使用擴充預存程序。</span><span class="sxs-lookup"><span data-stu-id="9514c-111">Explains how to create, manage, and use extended stored procedures.</span></span>  
  
 [<span data-ttu-id="9514c-112">擴充預存程序程式設計人員參考</span><span class="sxs-lookup"><span data-stu-id="9514c-112">Extended Stored Procedures Programmer's Reference</span></span>](extended-stored-procedures-reference/database-engine-extended-stored-procedures-reference.md)  
 <span data-ttu-id="9514c-113">包含擴充預存程序 API 的參考主題。</span><span class="sxs-lookup"><span data-stu-id="9514c-113">Contains reference topics for the Extended Stored Procedure API.</span></span>  
  
  
