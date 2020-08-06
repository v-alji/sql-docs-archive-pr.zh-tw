---
title: 存取 ADO.NET 中的使用者定義類型 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- ADO.NET [CLR integration]
- UDTs [CLR integration], ADO.NET
- user-defined types [CLR integration], ADO.NET
ms.assetid: 4b0d876c-8066-490e-8e18-327c0e942b19
author: rothja
ms.author: jroth
ms.openlocfilehash: a94e333ad743ed07dff6b973ebfe227312a1cab2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598447"
---
# <a name="accessing-user-defined-types-in-adonet"></a><span data-ttu-id="0889c-102">存取 ADO.NET 中的使用者定義型別</span><span class="sxs-lookup"><span data-stu-id="0889c-102">Accessing User-Defined Types in ADO.NET</span></span>
  <span data-ttu-id="0889c-103"> (Udt) 的使用者定義型別是使用 .NET Framework common language runtime 所支援的任何語言所撰寫， [!INCLUDE[msCoName](../../includes/msconame-md.md)] (CLR) 會產生可驗證的程式碼。</span><span class="sxs-lookup"><span data-stu-id="0889c-103">User-defined types (UDTs) are written using any of the languages supported by the [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework common language runtime (CLR) that produce verifiable code.</span></span> <span data-ttu-id="0889c-104">這包含 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C# 和 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic。</span><span class="sxs-lookup"><span data-stu-id="0889c-104">This includes [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C# and [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic.</span></span> <span data-ttu-id="0889c-105">UDT 允許在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫中儲存物件及自訂資料結構。</span><span class="sxs-lookup"><span data-stu-id="0889c-105">UDTs allow objects and custom data structures to be stored in a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database.</span></span> <span data-ttu-id="0889c-106">資料會做為 .NET Framework 類別或結構的公用成員而公開，行為可使用類別或結構的方法來定義。</span><span class="sxs-lookup"><span data-stu-id="0889c-106">The data is exposed as public members of a .NET Framework class or structure, and behaviors are defined by methods of the class or structure.</span></span> <span data-ttu-id="0889c-107">UDT 可用作資料表的資料行定義、[!INCLUDE[tsql](../../includes/tsql-md.md)] 批次中的變數，或是 [!INCLUDE[tsql](../../includes/tsql-md.md)] 函式或預存程序的引數。</span><span class="sxs-lookup"><span data-stu-id="0889c-107">A UDT can be used as the column definition of a table, as a variable in a [!INCLUDE[tsql](../../includes/tsql-md.md)] batch, or as an argument of a [!INCLUDE[tsql](../../includes/tsql-md.md)] function or stored procedure.</span></span>  
  
 <span data-ttu-id="0889c-108">在 ADO.NET 中，`System.Data.SqlClient` 提供者以下列方式公開 UDT：</span><span class="sxs-lookup"><span data-stu-id="0889c-108">In ADO.NET, the `System.Data.SqlClient` provider exposes UDTs in the following ways:</span></span>  
  
-   <span data-ttu-id="0889c-109">做為物件透過 `System.Data.SqlClient.SqlDataReader`。</span><span class="sxs-lookup"><span data-stu-id="0889c-109">Through the `System.Data.SqlClient.SqlDataReader` as an object.</span></span>  
  
-   <span data-ttu-id="0889c-110">做為未經處理位元組透過 `SqlDataReader`。</span><span class="sxs-lookup"><span data-stu-id="0889c-110">Through the `SqlDataReader` as raw bytes.</span></span>  
  
-   <span data-ttu-id="0889c-111">做為 `System.Data.SqlClient.SqlParameter` 物件的參數。</span><span class="sxs-lookup"><span data-stu-id="0889c-111">As a parameter of a `System.Data.SqlClient.SqlParameter` object.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0889c-112">本節內容</span><span class="sxs-lookup"><span data-stu-id="0889c-112">In This Section</span></span>  
 [<span data-ttu-id="0889c-113">擷取 UDT 資料</span><span class="sxs-lookup"><span data-stu-id="0889c-113">Retrieving UDT Data</span></span>](accessing-user-defined-types-retrieving-udt-data.md)  
 <span data-ttu-id="0889c-114">說明如何擷取 UDT 資料及如何指定參數。</span><span class="sxs-lookup"><span data-stu-id="0889c-114">Describes how to retrieve UDT data and how to specify parameters.</span></span>  
  
 [<span data-ttu-id="0889c-115">以 DataAdapter 更新 UDT 資料行</span><span class="sxs-lookup"><span data-stu-id="0889c-115">Updating UDT Columns with DataAdapters</span></span>](accessing-user-defined-types-updating-udt-columns-with-dataadapters.md)  
 <span data-ttu-id="0889c-116">說明如何在 `DataSets` 中使用 UDT，以及如何使用 `DataAdapters` 更新 UDT 資料。</span><span class="sxs-lookup"><span data-stu-id="0889c-116">Describes how to work with UDTs in `DataSets` and how to update UDT data using `DataAdapters`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0889c-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0889c-117">See Also</span></span>  
 [<span data-ttu-id="0889c-118">CLR 使用者定義類型</span><span class="sxs-lookup"><span data-stu-id="0889c-118">CLR User-Defined Types</span></span>](clr-user-defined-types.md)  
  
  
