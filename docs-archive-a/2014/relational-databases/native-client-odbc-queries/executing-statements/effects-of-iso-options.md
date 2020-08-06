---
title: ISO 選項的效果 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ISO options (ODBC)
- ODBC applications, ISO options
- ODBC applications, statements
- SQL Server Native Client ODBC driver, ISO options
- statements [ODBC], ISO options
ms.assetid: 813f1397-fa0b-45ec-a718-e13fe2fb88ac
author: rothja
ms.author: jroth
ms.openlocfilehash: 79deff1d77f4020aa7484629bac78d360ed7691f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585358"
---
# <a name="effects-of-iso-options"></a><span data-ttu-id="ca2d3-102">ISO 選項的作用</span><span class="sxs-lookup"><span data-stu-id="ca2d3-102">Effects of ISO Options</span></span>
  <span data-ttu-id="ca2d3-103">ODBC 標準與 ISO 標準相當接近，而且 ODBC 應用程式應該是來自 ODBC 驅動程式的標準行為。</span><span class="sxs-lookup"><span data-stu-id="ca2d3-103">The ODBC standard is closely matched to the ISO standard, and ODBC applications expect standard behavior from an ODBC driver.</span></span> <span data-ttu-id="ca2d3-104">為了讓其行為與 ODBC standard 中定義的更緊密地進行比對， [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native CLIENT ODBC 驅動程式一律會使用所連接之 SQL Server 版本中提供的任何 ISO 選項。</span><span class="sxs-lookup"><span data-stu-id="ca2d3-104">To make its behavior conform more closely with that defined in the ODBC standard, the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver always uses any ISO options available in the version of SQL Server with which it connects.</span></span>  
  
 <span data-ttu-id="ca2d3-105">當 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native CLIENT odbc 驅動程式連接到的實例時 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ，伺服器會偵測到用戶端正在使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC 驅動程式，並在上設定數個選項。</span><span class="sxs-lookup"><span data-stu-id="ca2d3-105">When the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver connects to an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], the server detects that the client is using the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver and sets several options on.</span></span>  
  
 <span data-ttu-id="ca2d3-106">驅動程式本身會發出這些陳述式；ODBC 應用程式不用做任何事情就可以要求它們。</span><span class="sxs-lookup"><span data-stu-id="ca2d3-106">The driver issues these statements itself; the ODBC application does nothing to request them.</span></span> <span data-ttu-id="ca2d3-107">設定這些選項可以使用驅動程式，讓 ODBC 應用程式更容易攜帶，因為伺服器行為會符合 ISO 標準。</span><span class="sxs-lookup"><span data-stu-id="ca2d3-107">Setting these options allows ODBC applications using the driver to be more portable because the server behavior then matches the ISO standard.</span></span>  
  
 <span data-ttu-id="ca2d3-108">以 DB-Library 為基礎的應用程式一般不會開啟這些選項。</span><span class="sxs-lookup"><span data-stu-id="ca2d3-108">DB-Library-based applications generally do not turn these options on.</span></span> <span data-ttu-id="ca2d3-109">在執行相同的 SQL 語句時觀察 ODBC 或 DB-LIBRARY 用戶端間不同行為的網站，不應該假設這會指向 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native CLIENT ODBC 驅動程式的問題。</span><span class="sxs-lookup"><span data-stu-id="ca2d3-109">Sites observing different behavior between ODBC or DB-Library clients when running the same SQL statement should not assume this points to a problem with the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver.</span></span> <span data-ttu-id="ca2d3-110">它們應該先使用與 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native CLIENT ODBC 驅動程式所使用的相同 SET 選項，在 db-library 環境中重新執行語句。</span><span class="sxs-lookup"><span data-stu-id="ca2d3-110">They should first rerun the statement in the DB-Library environment with the same SET options as would be used by the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver.</span></span>  
  
 <span data-ttu-id="ca2d3-111">由於使用者和應用程式可以隨時開啟和關閉 SET 選項，因此，預存程序和觸發程序的開發人員也應該在開啟和關閉以上列出的 SET 選項時，小心測試其程序和觸發程序。</span><span class="sxs-lookup"><span data-stu-id="ca2d3-111">Because SET options can be turned on and off at any time by users and applications, developers of stored procedures and triggers should also take care to test their procedures and triggers with the SET options listed above turned both on and off.</span></span> <span data-ttu-id="ca2d3-112">無論特定連接叫用程序或觸發程序時已經設定哪些選項，這都可以確保程序和觸發程序能正常運作。</span><span class="sxs-lookup"><span data-stu-id="ca2d3-112">This ensures that the procedures and triggers work correctly regardless of which options a particular connection may have set on when they invoke the procedure or trigger.</span></span> <span data-ttu-id="ca2d3-113">對於需要為這些選項的其中之一進行特定設定的觸發程序或預存程序，應該在觸發程序或預存程序開始時發出 SET 陳述式。</span><span class="sxs-lookup"><span data-stu-id="ca2d3-113">Triggers or stored procedures that require a particular setting for one of these options should issue a SET statement at the start of the trigger or stored procedure.</span></span> <span data-ttu-id="ca2d3-114">此 SET 陳述式只有在執行觸發程序或預存程序時才有效，當程序或觸發程序結束時，就會還原原始的設定。</span><span class="sxs-lookup"><span data-stu-id="ca2d3-114">This SET statement remains in effect only for the execution of the trigger or stored procedure; when the procedure or trigger ends, the original setting is restored.</span></span>  
  
 <span data-ttu-id="ca2d3-115">連接到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的執行個體時，也會將第四個 SET 選項，也就是 CONCAT_NULL_YIELDS_NULL，設定為開啟。</span><span class="sxs-lookup"><span data-stu-id="ca2d3-115">When connected to an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], a fourth SET option, CONCAT_NULL_YIELDS_NULL, is also set on.</span></span> <span data-ttu-id="ca2d3-116">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]如果資料來源或[SQLDriverConnect](../../native-client-odbc-api/sqldriverconnect.md)或[SQLBrowseConnect](../../native-client-odbc-api/sqlbrowseconnect.md)中指定了 AnsiNPW = NO，Native Client ODBC 驅動程式就不會將這些選項設定為 on。</span><span class="sxs-lookup"><span data-stu-id="ca2d3-116">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver does not set these options on if AnsiNPW=NO is specified in the data source or on either [SQLDriverConnect](../../native-client-odbc-api/sqldriverconnect.md) or [SQLBrowseConnect](../../native-client-odbc-api/sqlbrowseconnect.md).</span></span>  
  
 <span data-ttu-id="ca2d3-117">如同稍早所述的 ISO 選項， [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native CLIENT ODBC 驅動程式不會在資料來源或**SQLDriverConnect**或**SQLBrowseConnect**中指定 QuotedID = NO 時，開啟 QUOTED_IDENTIFIER 選項。</span><span class="sxs-lookup"><span data-stu-id="ca2d3-117">Like the ISO options noted earlier, the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver does not turn the QUOTED_IDENTIFIER option on if QuotedID=NO is specified in the data source or on either **SQLDriverConnect** or **SQLBrowseConnect**.</span></span>  
  
 <span data-ttu-id="ca2d3-118">為了讓驅動程式知道 SET 選項的目前狀態，ODBC 應用程式應該不會使用 [!INCLUDE[tsql](../../../includes/tsql-md.md)] SET 陳述式來設定這些選項。</span><span class="sxs-lookup"><span data-stu-id="ca2d3-118">To allow the driver to know the current state of SET options, ODBC applications should not use the [!INCLUDE[tsql](../../../includes/tsql-md.md)] SET statement to set these options.</span></span> <span data-ttu-id="ca2d3-119">它們應該只會使用資料來源或連接選項設定這些選項。</span><span class="sxs-lookup"><span data-stu-id="ca2d3-119">They should only set these options using either the data source or the connection options.</span></span> <span data-ttu-id="ca2d3-120">如果應用程式發出 SET 陳述式，此驅動程式可能會產生不正確的 SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="ca2d3-120">If the application issues SET statements, the driver can generate incorrect SQL statements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca2d3-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ca2d3-121">See Also</span></span>  
 <span data-ttu-id="ca2d3-122">[&#40;ODBC&#41;執行語句](executing-statements-odbc.md) </span><span class="sxs-lookup"><span data-stu-id="ca2d3-122">[Executing Statements &#40;ODBC&#41;](executing-statements-odbc.md) </span></span>  
 <span data-ttu-id="ca2d3-123">[SQLDriverConnect](../../native-client-odbc-api/sqldriverconnect.md) </span><span class="sxs-lookup"><span data-stu-id="ca2d3-123">[SQLDriverConnect](../../native-client-odbc-api/sqldriverconnect.md) </span></span>  
 [<span data-ttu-id="ca2d3-124">SQLBrowseConnect</span><span class="sxs-lookup"><span data-stu-id="ca2d3-124">SQLBrowseConnect</span></span>](../../native-client-odbc-api/sqlbrowseconnect.md)  
  
  
