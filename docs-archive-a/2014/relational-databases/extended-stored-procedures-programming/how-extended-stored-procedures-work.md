---
title: 擴充預存程式的工作方式 |Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- extended stored procedures [SQL Server], about extended stored procedures
ms.assetid: 6e946d8c-3268-4b59-8a1c-1637909cd701
author: rothja
ms.author: jroth
ms.openlocfilehash: 75082fed6b70c214b4f55b85034ffa371824d24f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598395"
---
# <a name="how-extended-stored-procedures-work"></a><span data-ttu-id="45a86-102">擴充預存程序運作方式</span><span class="sxs-lookup"><span data-stu-id="45a86-102">How Extended Stored Procedures Work</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="45a86-103">請改用 CLR 整合。</span><span class="sxs-lookup"><span data-stu-id="45a86-103">Use CLR Integration instead.</span></span>  
  
 <span data-ttu-id="45a86-104">擴充預存程序藉以運作的程序為：</span><span class="sxs-lookup"><span data-stu-id="45a86-104">The process by which an extended stored procedure works is:</span></span>  
  
1.  <span data-ttu-id="45a86-105">當用戶端執行擴充預存程式時，會從用戶端應用程式 (TDS) 或簡單物件存取通訊協定 (SOAP) 格式，將要求傳送至表格式資料流程中 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="45a86-105">When a client executes an extended stored procedure, the request is transmitted in tabular data stream (TDS) or Simple Object Access Protocol (SOAP) format from the client application to [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
2.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="45a86-106">會搜尋與擴充預存程序相關聯的 DLL，並載入 DLL (如果尚未載入)。</span><span class="sxs-lookup"><span data-stu-id="45a86-106">searches for the DLL associated with the extended stored procedure, and loads the DLL if it is not already loaded.</span></span>  
  
3.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="45a86-107">會呼叫要求的擴充預存程序 (以 DLL 內部的函數實作)。</span><span class="sxs-lookup"><span data-stu-id="45a86-107">calls the requested extended stored procedure (implemented as a function inside the DLL).</span></span>  
  
4.  <span data-ttu-id="45a86-108">擴充預存程序會傳遞結果集，並透過擴充預存程序 API 將參數傳回至伺服器。</span><span class="sxs-lookup"><span data-stu-id="45a86-108">The extended stored procedure passes result sets and return parameters back to the server by through the Extended Stored Procedure API.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45a86-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="45a86-109">See Also</span></span>  
 [<span data-ttu-id="45a86-110">資料庫引擎擴充預存程序程式設計</span><span class="sxs-lookup"><span data-stu-id="45a86-110">Database Engine Extended Stored Procedure Programming</span></span>](../database-engine-extended-stored-procedure-programming.md)  
  
  
