---
title: SQL Server Native Client 的元件 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, about SQL Server Native Client ODBC driver
- data access [SQL Server Native Client], components
- components [SQL Server Native Client]
- SQLNCLI, about SQL Server Native Client
ms.assetid: 65f932d5-daa1-4eff-b6df-ee633fcf2a7c
author: rothja
ms.author: jroth
ms.openlocfilehash: 32438b9fb5473d9251acd0aceddb46db373f3548
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597080"
---
# <a name="components-of-sql-server-native-client"></a><span data-ttu-id="f6e1d-102">SQL Server Native Client 的元件</span><span class="sxs-lookup"><span data-stu-id="f6e1d-102">Components of SQL Server Native Client</span></span>
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="f6e1d-103">Native Client 包含下列元件：</span><span class="sxs-lookup"><span data-stu-id="f6e1d-103">Native Client contains the following components:</span></span>  
  
|<span data-ttu-id="f6e1d-104">元件</span><span class="sxs-lookup"><span data-stu-id="f6e1d-104">Component</span></span>|<span data-ttu-id="f6e1d-105">描述</span><span class="sxs-lookup"><span data-stu-id="f6e1d-105">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f6e1d-106">sqlncli11.dll</span><span class="sxs-lookup"><span data-stu-id="f6e1d-106">sqlncli11.dll</span></span>|<span data-ttu-id="f6e1d-107">包含所有 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 功能的動態連結程式庫 (DLL) 檔案。</span><span class="sxs-lookup"><span data-stu-id="f6e1d-107">The dynamic-link library (DLL) file that contains all of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client functionality.</span></span> <span data-ttu-id="f6e1d-108">這包括 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者與 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC 驅動程式。</span><span class="sxs-lookup"><span data-stu-id="f6e1d-108">This includes the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider and the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver.</span></span>|  
|<span data-ttu-id="f6e1d-109">sqlnclir11.rll</span><span class="sxs-lookup"><span data-stu-id="f6e1d-109">sqlnclir11.rll</span></span>|<span data-ttu-id="f6e1d-110">隨附 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 程式庫的資源檔。</span><span class="sxs-lookup"><span data-stu-id="f6e1d-110">The accompanying resource file for the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client library.</span></span>|  
|<span data-ttu-id="f6e1d-111">s10ch_sqlncli.chm</span><span class="sxs-lookup"><span data-stu-id="f6e1d-111">s10ch_sqlncli.chm</span></span>|<span data-ttu-id="f6e1d-112">記載如何使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC 驅動程式或 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者建立 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 資料來源的資料來源精靈說明檔。</span><span class="sxs-lookup"><span data-stu-id="f6e1d-112">The Data Source Wizard help file that documents how to create a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] data source using the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver or the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider.</span></span>|  
|<span data-ttu-id="f6e1d-113">sqlncli.h</span><span class="sxs-lookup"><span data-stu-id="f6e1d-113">sqlncli.h</span></span>|<span data-ttu-id="f6e1d-114">包含使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 所需之所有新定義的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 標頭檔。</span><span class="sxs-lookup"><span data-stu-id="f6e1d-114">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client header file that contains all of the new definitions needed in order to use [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.</span></span> <span data-ttu-id="f6e1d-115">此標頭檔會同時取代 odbcss.h 和 sqloledb.h 標頭檔。</span><span class="sxs-lookup"><span data-stu-id="f6e1d-115">This header file replaces both the odbcss.h and the sqloledb.h header files.</span></span> <span data-ttu-id="f6e1d-116">**注意：** 您不能在相同的程式中參考 sqlncli 和 odbcss.h，但是只要先定義 sqloledb，就可以在同一個程式中參考 sqlncli 和 sqloledb。</span><span class="sxs-lookup"><span data-stu-id="f6e1d-116">**Note:**  You cannot reference sqlncli.h and odbcss.h in the same program, but you can reference sqlncli.h and sqloledb.h in same program as long as sqloledb.h is defined first.</span></span>|  
|<span data-ttu-id="f6e1d-117">sqlncli11.lib</span><span class="sxs-lookup"><span data-stu-id="f6e1d-117">sqlncli11.lib</span></span>|<span data-ttu-id="f6e1d-118">直接呼叫屬於**bcp** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC 驅動程式一部分之 bcp 公用程式函式所需的程式庫檔案。</span><span class="sxs-lookup"><span data-stu-id="f6e1d-118">The library file needed to directly call the **bcp** utility functions that are part of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver.</span></span> <span data-ttu-id="f6e1d-119">**注意：** 如果您在程式碼中參考 sqlncli11 檔案，您必須確定 sqlncli11.dll 檔案位於您的系統路徑中，以及使用您的應用程式之使用者的系統路徑中。</span><span class="sxs-lookup"><span data-stu-id="f6e1d-119">**Note:**  If you do reference the sqlncli11.lib file in your programming code, you need to make sure that the sqlncli11.dll file is in your system path, and in the system path of the users that make use of your application.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f6e1d-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f6e1d-120">See Also</span></span>  
 [<span data-ttu-id="f6e1d-121">使用 SQL Server Native Client 建置應用程式</span><span class="sxs-lookup"><span data-stu-id="f6e1d-121">Building Applications with SQL Server Native Client</span></span>](building-applications-with-sql-server-native-client.md)  
  
  
