---
title: 執行預存程序 (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- stored procedures [OLE DB], executing
- OLE DB, stored procedures
- SQL Server Native Client OLE DB provider, stored procedures
ms.assetid: c77d9be9-2176-4438-8c7a-04b63ebece08
author: rothja
ms.author: jroth
ms.openlocfilehash: 2e6ce951f343002feea5aa793d0cc2092422b819
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706374"
---
# <a name="running-stored-procedures-ole-db"></a><span data-ttu-id="43ea1-102">執行預存程序 (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="43ea1-102">Running Stored Procedures (OLE DB)</span></span>
  <span data-ttu-id="43ea1-103">執行陳述式時，在資料來源上呼叫預存程序 (而非直接在用戶端應用程式中執行或準備陳述式) 可以提供：</span><span class="sxs-lookup"><span data-stu-id="43ea1-103">When executing statements, calling a stored procedure on the data source (instead of executing or preparing a statement in the client application directly) can provide:</span></span>  
  
-   <span data-ttu-id="43ea1-104">較高的效能。</span><span class="sxs-lookup"><span data-stu-id="43ea1-104">Higher performance.</span></span>  
  
-   <span data-ttu-id="43ea1-105">降低的網路負擔。</span><span class="sxs-lookup"><span data-stu-id="43ea1-105">Reduced network overhead.</span></span>  
  
-   <span data-ttu-id="43ea1-106">更好的一致性。</span><span class="sxs-lookup"><span data-stu-id="43ea1-106">Better consistency.</span></span>  
  
-   <span data-ttu-id="43ea1-107">更好的精確度。</span><span class="sxs-lookup"><span data-stu-id="43ea1-107">Better accuracy.</span></span>  
  
-   <span data-ttu-id="43ea1-108">增加的功能。</span><span class="sxs-lookup"><span data-stu-id="43ea1-108">Added functionality.</span></span>  
  
 <span data-ttu-id="43ea1-109">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client OLE DB 提供者支援 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 預存程式用來傳回資料的三種機制：</span><span class="sxs-lookup"><span data-stu-id="43ea1-109">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider supports three of the mechanisms that [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] stored procedures use to return data:</span></span>  
  
-   <span data-ttu-id="43ea1-110">程序中的每個 SELECT 陳述式都會產生一個結果集。</span><span class="sxs-lookup"><span data-stu-id="43ea1-110">Every SELECT statement in the procedure generates a result set.</span></span>  
  
-   <span data-ttu-id="43ea1-111">程序可以透過輸出參數傳回資料。</span><span class="sxs-lookup"><span data-stu-id="43ea1-111">The procedure can return data through output parameters.</span></span>  
  
-   <span data-ttu-id="43ea1-112">程序可以有一個整數的傳回碼。</span><span class="sxs-lookup"><span data-stu-id="43ea1-112">The procedure can have an integer return code.</span></span>  
  
 <span data-ttu-id="43ea1-113">應用程式必須能夠處理預存程序中的所有這些輸出。</span><span class="sxs-lookup"><span data-stu-id="43ea1-113">The application must be able to handle all of these outputs from stored procedures.</span></span>  
  
 <span data-ttu-id="43ea1-114">不同的 OLE DB 提供者在結果處理期間，會在不同時間傳回輸出參數和傳回值。</span><span class="sxs-lookup"><span data-stu-id="43ea1-114">Different OLE DB providers return output parameters and return values at different times during result processing.</span></span> <span data-ttu-id="43ea1-115">如果是 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者，在取用者抓取或取消預存程式所傳回的結果集之前，不會提供輸出參數和傳回碼。</span><span class="sxs-lookup"><span data-stu-id="43ea1-115">In case of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider, the output parameters and return codes are not supplied until after the consumer has retrieved or canceled the result sets returned by the stored procedure.</span></span> <span data-ttu-id="43ea1-116">傳回碼和輸出參數會由來自伺服器的最後一個 TDS 封包傳回。</span><span class="sxs-lookup"><span data-stu-id="43ea1-116">The return codes and the output parameters are returned in the last TDS packet from the server.</span></span>  
  
 <span data-ttu-id="43ea1-117">當它傳回輸出參數和傳回碼時，提供者會使用 DBPROP_OUTPUTPARAMETERAVAILABILITY 屬性來報告。</span><span class="sxs-lookup"><span data-stu-id="43ea1-117">Providers use the DBPROP_OUTPUTPARAMETERAVAILABILITY property to report when it returns output parameters and return values.</span></span> <span data-ttu-id="43ea1-118">這個屬性位於 DBPROPSET_DATASOURCEINFO 屬性集中。</span><span class="sxs-lookup"><span data-stu-id="43ea1-118">This property is in the DBPROPSET_DATASOURCEINFO property set.</span></span>  
  
 <span data-ttu-id="43ea1-119">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client OLE DB 提供者會將 DBPROP_OUTPUTPARAMETERAVAILABILITY 屬性設定為 DBPROPVAL_OA_ATROWRELEASE，以指出在處理或釋放結果集之前，不會傳回傳回碼和輸出參數。</span><span class="sxs-lookup"><span data-stu-id="43ea1-119">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider sets the DBPROP_OUTPUTPARAMETERAVAILABILITY property to DBPROPVAL_OA_ATROWRELEASE to indicate that return codes and output parameters are not returned until the result set is processed or released.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43ea1-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="43ea1-120">See Also</span></span>  
 [<span data-ttu-id="43ea1-121">預存程式</span><span class="sxs-lookup"><span data-stu-id="43ea1-121">Stored Procedures</span></span>](stored-procedures.md)  
  
  
