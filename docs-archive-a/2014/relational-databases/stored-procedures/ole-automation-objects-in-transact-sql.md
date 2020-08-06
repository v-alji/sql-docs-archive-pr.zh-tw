---
title: Transact-SQL 中的 OLE Automation 物件 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: conceptual
helpviewer_keywords:
- triggers [SQL Server], OLE Automation
- batches [SQL Server], OLE Automation
- OLE Automation [SQL Server]
- OLE Automation [SQL Server], about OLE Automation
ms.assetid: a887d956-4cd0-400a-aa96-00d7abd7c44b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1f36846565bb60fbf875e9babdabbb6d1667f5ea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607368"
---
# <a name="ole-automation-objects-in-transact-sql"></a><span data-ttu-id="83684-102">Transact-SQL 中的 OLE Automation 物件</span><span class="sxs-lookup"><span data-stu-id="83684-102">OLE Automation Objects in Transact-SQL</span></span>
  [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="83684-103">包含多個系統預存程序，可讓您在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 批次、預存程序與觸發程序中參考 OLE Automation 物件。</span><span class="sxs-lookup"><span data-stu-id="83684-103">includes several system stored procedures that allow OLE Automation objects to be referenced in [!INCLUDE[tsql](../../includes/tsql-md.md)] batches, stored procedures, and triggers.</span></span> <span data-ttu-id="83684-104">這些系統預存程序以擴充預存程序來執行，而透過預存程序執行的 OLE Automation 物件在 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 執行個體的位址空間內的執行方式與擴充預存程序的執行方式相同。</span><span class="sxs-lookup"><span data-stu-id="83684-104">These system stored procedures run as extended stored procedures, and the OLE Automation objects that are executed through the stored procedures run in the address space of an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] in the same way that an extended stored procedure runs.</span></span>  
  
 <span data-ttu-id="83684-105">OLE Automation 預存程序可讓 [!INCLUDE[tsql](../../includes/tsql-md.md)] 批次參考 SQL-DMO 物件和自訂 OLE Automation 物件，例如公開 **IDispatch** 介面的物件。</span><span class="sxs-lookup"><span data-stu-id="83684-105">The OLE Automation stored procedures enable [!INCLUDE[tsql](../../includes/tsql-md.md)] batches to reference SQL-DMO objects and custom OLE Automation objects, such as objects that expose the **IDispatch** interface.</span></span> <span data-ttu-id="83684-106">使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 所建立的自訂、內含式 OLE 伺服器必須具有 **Class_Initialize** 和 **Class_Terminate** 副程式的錯誤處理常式 (請使用 **On Error GoTo** 陳述式來指定此錯誤處理常式)。</span><span class="sxs-lookup"><span data-stu-id="83684-106">A custom in-process OLE server that is created by using [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] must have an error handler (specified with the **On Error GoTo** statement) for the **Class_Initialize** and **Class_Terminate** subroutines.</span></span> <span data-ttu-id="83684-107">**Class_Initialize** 與 **Class_Terminate** 副程式中的未處理錯誤將導致未預期的錯誤，例如 [!INCLUDE[ssDE](../../includes/ssde-md.md)]執行個體中的存取違規。</span><span class="sxs-lookup"><span data-stu-id="83684-107">Unhandled errors in the **Class_Initialize** and **Class_Terminate** subroutines can cause unpredictable errors, such as an access violation in an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span> <span data-ttu-id="83684-108">對於其他的副程式，我們也建議您使用錯誤處理常式。</span><span class="sxs-lookup"><span data-stu-id="83684-108">Error handlers for other subroutines are also recommended.</span></span>  
  
 <span data-ttu-id="83684-109">在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 中使用 OLE Automation 物件的第一個步驟是呼叫 **sp_OACreate** 系統預存程序，以便在 [!INCLUDE[ssDE](../../includes/ssde-md.md)]執行個體的位址空間中建立物件的執行個體。</span><span class="sxs-lookup"><span data-stu-id="83684-109">The first step when using an OLE Automation object in [!INCLUDE[tsql](../../includes/tsql-md.md)] is to call the **sp_OACreate** system stored procedure to create an instance of the object in the address space of the instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
 <span data-ttu-id="83684-110">在建立物件的執行個體之後，請呼叫下列預存程序來使用物件的相關屬性、方法與錯誤資訊：</span><span class="sxs-lookup"><span data-stu-id="83684-110">After an instance of the object has been created, call the following stored procedures to work with the properties, methods, and error information related to the object:</span></span>  
  
-   <span data-ttu-id="83684-111">**sp_OAGetProperty** 取得屬性的值。</span><span class="sxs-lookup"><span data-stu-id="83684-111">**sp_OAGetProperty** obtains the value of a property.</span></span>  
  
-   <span data-ttu-id="83684-112">**sp_OASetProperty** 設定屬性的值。</span><span class="sxs-lookup"><span data-stu-id="83684-112">**sp_OASetProperty** sets the value of a property.</span></span>  
  
-   <span data-ttu-id="83684-113">**sp_OAMethod** 呼叫一個方法。</span><span class="sxs-lookup"><span data-stu-id="83684-113">**sp_OAMethod** calls a method.</span></span>  
  
-   <span data-ttu-id="83684-114">**sp_OAGetErrorInfo** 取得最近的錯誤資訊。</span><span class="sxs-lookup"><span data-stu-id="83684-114">**sp_OAGetErrorInfo** obtains the most recent error information.</span></span>  
  
 <span data-ttu-id="83684-115">當您不再需要物件時，可呼叫 **sp_OADestroy** 來將使用 **sp_OACreate**所建立的物件執行個體取消配置。</span><span class="sxs-lookup"><span data-stu-id="83684-115">When there is no more need for the object, call **sp_OADestroy** to deallocate the instance of the object created by using **sp_OACreate**.</span></span>  
  
 <span data-ttu-id="83684-116">OLE Automation 物件會透過屬性值和方法傳回資料。</span><span class="sxs-lookup"><span data-stu-id="83684-116">OLE Automation objects return data through property values and methods.</span></span> <span data-ttu-id="83684-117">**sp_OAGetProperty** 和 **sp_OAMethod** 會以結果集形式傳回這些資料值。</span><span class="sxs-lookup"><span data-stu-id="83684-117">**sp_OAGetProperty** and **sp_OAMethod** return these data values in the form of a result set.</span></span>  
  
 <span data-ttu-id="83684-118">OLE Automation 物件的範圍是一個批次。</span><span class="sxs-lookup"><span data-stu-id="83684-118">The scope of an OLE Automation object is a batch.</span></span> <span data-ttu-id="83684-119">該物件的所有參考都必須包含於一個批次、預存程序或觸發程序內。</span><span class="sxs-lookup"><span data-stu-id="83684-119">All references to the object must be contained in a single batch, stored procedure, or trigger.</span></span>  
  
 <span data-ttu-id="83684-120">在參考物件時， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] OLE Automation 物件支援將參考的物件跨越它所包含的其他物件。</span><span class="sxs-lookup"><span data-stu-id="83684-120">When it references objects, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] OLE Automation objects support traversing the referenced object to other objects that it contains.</span></span> <span data-ttu-id="83684-121">例如，在使用 SQL-DMO **SQLServer** 物件時，您可參考至該伺服器所包含的資料庫與資料表。</span><span class="sxs-lookup"><span data-stu-id="83684-121">For example, when using the SQL-DMO **SQLServer** object, references can be made to databases and tables contained on that server.</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="83684-122">相關內容</span><span class="sxs-lookup"><span data-stu-id="83684-122">Related Content</span></span>  
 [<span data-ttu-id="83684-123">物件階層語法 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="83684-123">Object Hierarchy Syntax &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/object-hierarchy-syntax-transact-sql)  
  
 [<span data-ttu-id="83684-124">介面區組態</span><span class="sxs-lookup"><span data-stu-id="83684-124">Surface Area Configuration</span></span>](../security/surface-area-configuration.md)  
  
 [<span data-ttu-id="83684-125">OLE Automation 程序伺服器組態選項</span><span class="sxs-lookup"><span data-stu-id="83684-125">Ole Automation Procedures Server Configuration Option</span></span>](../../database-engine/configure-windows/ole-automation-procedures-server-configuration-option.md)  
  
 [<span data-ttu-id="83684-126">sp_OACreate &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="83684-126">sp_OACreate &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-oacreate-transact-sql)  
  
 [<span data-ttu-id="83684-127">sp_OAGetProperty &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="83684-127">sp_OAGetProperty &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-oagetproperty-transact-sql)  
  
 [<span data-ttu-id="83684-128">sp_OASetProperty &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="83684-128">sp_OASetProperty &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-oasetproperty-transact-sql)  
  
 [<span data-ttu-id="83684-129">sp_OAMethod &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="83684-129">sp_OAMethod &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-oamethod-transact-sql)  
  
 [<span data-ttu-id="83684-130">sp_OAGetErrorInfo &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="83684-130">sp_OAGetErrorInfo &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-oageterrorinfo-transact-sql)  
  
 [<span data-ttu-id="83684-131">sp_OADestroy &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="83684-131">sp_OADestroy &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-oadestroy-transact-sql)  
  
  
