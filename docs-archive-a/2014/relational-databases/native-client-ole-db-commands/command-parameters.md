---
title: 命令參數 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- parameters [SQL Server Native Client]
- SQL Server Native Client OLE DB provider, parameters
- SQL Server Native Client OLE DB provider, commands
- parameters [SQL Server Native Client], OLE DB
- commands [OLE DB]
ms.assetid: 072ead49-ebaf-41eb-9a0f-613e9d990f26
author: rothja
ms.author: jroth
ms.openlocfilehash: 6c00250bac3504ffb06b37aeb8c4e7eaf583c987
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607387"
---
# <a name="command-parameters"></a><span data-ttu-id="051ad-102">命令參數</span><span class="sxs-lookup"><span data-stu-id="051ad-102">Command Parameters</span></span>
  <span data-ttu-id="051ad-103">在命令文字中，參數會以問號字元來標示。</span><span class="sxs-lookup"><span data-stu-id="051ad-103">Parameters are marked in command text with the question mark character.</span></span> <span data-ttu-id="051ad-104">例如，下列 SQL 陳述式是針對單一輸入參數標示：</span><span class="sxs-lookup"><span data-stu-id="051ad-104">For example, the following SQL statement is marked for a single input parameter:</span></span>  
  
```  
{call SalesByCategory('Produce', ?)}  
```  
  
 <span data-ttu-id="051ad-105">為了藉由減少網路流量來改善效能， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 除非在執行命令之前呼叫了**ICommandWithParameters：： GetParameterInfo**或**ICommandPrepare：:P 準備**，否則 Native Client OLE DB 提供者不會自動衍生參數資訊。</span><span class="sxs-lookup"><span data-stu-id="051ad-105">To improve performance by reducing network traffic, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider does not automatically derive parameter information unless **ICommandWithParameters::GetParameterInfo** or **ICommandPrepare::Prepare** is called before executing a command.</span></span> <span data-ttu-id="051ad-106">這表示 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者不會自動執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="051ad-106">This means that the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider does not automatically:</span></span>  
  
-   <span data-ttu-id="051ad-107">確認使用 **ICommandWithParameters::SetParameterInfo** 所指定之資料類型的正確性。</span><span class="sxs-lookup"><span data-stu-id="051ad-107">Verify the correctness of the data type specified with **ICommandWithParameters::SetParameterInfo**.</span></span>  
  
-   <span data-ttu-id="051ad-108">從存取子繫結資訊中指定的 DBTYPE 對應至參數的正確 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料類型。</span><span class="sxs-lookup"><span data-stu-id="051ad-108">Map from the DBTYPE specified in the accessor binding information to the correct [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type for the parameter.</span></span>  
  
 <span data-ttu-id="051ad-109">如果應用程式指定了與參數之 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料類型不相容的資料類型，它們將在使用其中一種方法時收到可能的錯誤或遺失有效位數。</span><span class="sxs-lookup"><span data-stu-id="051ad-109">Applications will receive possible errors or loss of precision with either of these methods if they specify data types that are not compatible with the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type of the parameter.</span></span>  
  
 <span data-ttu-id="051ad-110">若要確保不會發生這種情況，應用程式應該：</span><span class="sxs-lookup"><span data-stu-id="051ad-110">To ensure this does not happen, the application should:</span></span>  
  
-   <span data-ttu-id="051ad-111">確定 *pwszDataSourceType* 符合參數的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料類型 (如果寫入 **ICommandWithParameters::SetParameterInfo** 程式碼的話)。</span><span class="sxs-lookup"><span data-stu-id="051ad-111">Ensure that *pwszDataSourceType* matches the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type for the parameter if hard-coding **ICommandWithParameters::SetParameterInfo**.</span></span>  
  
-   <span data-ttu-id="051ad-112">確定繫結至參數的 DBTYPE 值與參數的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料類型具有相同的類型 (如果寫入存取子程式碼的話)。</span><span class="sxs-lookup"><span data-stu-id="051ad-112">Ensure that the DBTYPE value being bound to the parameter is of the same type as the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type for the parameter if hard-coding an accessor.</span></span>  
  
-   <span data-ttu-id="051ad-113">將應用程式編碼成呼叫 **ICommandWithParameters::GetParameterInfo**，如此提供者就可以用動態方式取得參數的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料類型。</span><span class="sxs-lookup"><span data-stu-id="051ad-113">Code the application to call **ICommandWithParameters::GetParameterInfo** so that the provider can obtain the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data types of the parameters dynamically.</span></span> <span data-ttu-id="051ad-114">請注意，這可能會導致與伺服器之間的額外網路往返。</span><span class="sxs-lookup"><span data-stu-id="051ad-114">Note that this causes an extra network round trip to the server.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="051ad-115">在下列情況下，提供者不支援呼叫 **ICommandWithParameters::GetParameterInfo**：包含 FROM 子句的任何 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] UPDATE 或 DELETE 陳述式、相依於包含參數之子查詢的任何 SQL 陳述式、在比較 (like) 或定量述詞的運算式中都包含參數標記的 SQL 陳述式，或是其中一個參數為函式參數的任何查詢。</span><span class="sxs-lookup"><span data-stu-id="051ad-115">The provider does not support calling **ICommandWithParameters::GetParameterInfo** for any [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] UPDATE or DELETE statement containing a FROM clause; for any SQL statement depending on a subquery containing parameters; for SQL statements containing parameter markers in both expressions of a comparison, like, or quantified predicate; or queries where one of the parameters is a parameter to a function.</span></span> <span data-ttu-id="051ad-116">在處理 SQL 陳述式批次時，提供者也不支援針對批次內第一個陳述式之後的陳述式中的參數標記呼叫 **ICommandWithParameters::GetParameterInfo**。</span><span class="sxs-lookup"><span data-stu-id="051ad-116">When processing a batch of SQL statements, the provider also does not support calling **ICommandWithParameters::GetParameterInfo** for parameter markers in statements after the first statement in the batch.</span></span> <span data-ttu-id="051ad-117">不允許在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 命令中使用註解 (/\* \*/)。</span><span class="sxs-lookup"><span data-stu-id="051ad-117">Comments (/\* \*/) are not allowed in the [!INCLUDE[tsql](../../includes/tsql-md.md)] command.</span></span>  
  
 <span data-ttu-id="051ad-118">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供者支援 SQL 語句命令中的輸入參數。</span><span class="sxs-lookup"><span data-stu-id="051ad-118">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider supports input parameters in SQL statement commands.</span></span> <span data-ttu-id="051ad-119">在程序呼叫命令中， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者支援輸入、輸出和輸入/輸出參數。</span><span class="sxs-lookup"><span data-stu-id="051ad-119">On procedure-call commands, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider supports input, output, and input/output parameters.</span></span> <span data-ttu-id="051ad-120">在執行 (只有在沒有傳回任何資料列集時) 或應用程式已用盡所有傳回的資料列集時，輸出參數值就會傳回應用程式。</span><span class="sxs-lookup"><span data-stu-id="051ad-120">Output parameter values are returned to the application either on execution (only if there are no rowsets returned) or when all returned rowsets are exhausted by the application.</span></span> <span data-ttu-id="051ad-121">若要確保傳回的值有效，請使用 **IMultipleResults** 來強制資料列集取用。</span><span class="sxs-lookup"><span data-stu-id="051ad-121">To ensure that returned values are valid, use **IMultipleResults** to force rowset consumption.</span></span>  
  
 <span data-ttu-id="051ad-122">您不需要在 DBPARAMBINDINFO 結構中指定預存程序參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="051ad-122">The names of stored procedure parameters need not be specified in a DBPARAMBINDINFO structure.</span></span> <span data-ttu-id="051ad-123">請使用 Null 作為*pwszName*成員的值，以指出 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者應該忽略參數名稱，並只使用**ICommandWithParameters：： SetParameterInfo**的*rgParamOrdinals*成員中指定的序數。</span><span class="sxs-lookup"><span data-stu-id="051ad-123">Use NULL for the value of the *pwszName* member to indicate that the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider should ignore the parameter name and use only the ordinal specified in the *rgParamOrdinals* member of **ICommandWithParameters::SetParameterInfo**.</span></span> <span data-ttu-id="051ad-124">如果命令文字同時包含已命名和未命名的參數，您就必須在任何已命名的參數前面指定所有未命名的參數。</span><span class="sxs-lookup"><span data-stu-id="051ad-124">If the command text contains both named and unnamed parameters, all of the unnamed parameters must be specified before any named parameters.</span></span>  
  
 <span data-ttu-id="051ad-125">如果指定了預存程式參數的名稱， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者會檢查名稱，以確保它是有效的。</span><span class="sxs-lookup"><span data-stu-id="051ad-125">If the name of a stored procedure parameter is specified, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider checks the name to ensure that it is valid.</span></span> <span data-ttu-id="051ad-126">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供者從取用者收到錯誤的參數名稱時，會傳回錯誤。</span><span class="sxs-lookup"><span data-stu-id="051ad-126">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider returns an error when it receives an erroneous parameter name from the consumer.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="051ad-127">為了公開 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] XML 和使用者定義型別 (UDT) 的支援， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者會執行新的[ISSCommandWithParameters](../native-client-ole-db-interfaces/isscommandwithparameters-ole-db.md)介面。</span><span class="sxs-lookup"><span data-stu-id="051ad-127">To expose support for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] XML and user-defined types (UDT), the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider implements a new [ISSCommandWithParameters](../native-client-ole-db-interfaces/isscommandwithparameters-ole-db.md) interface.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="051ad-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="051ad-128">See Also</span></span>  
 [<span data-ttu-id="051ad-129">命令</span><span class="sxs-lookup"><span data-stu-id="051ad-129">Commands</span></span>](commands.md)  
  
  
