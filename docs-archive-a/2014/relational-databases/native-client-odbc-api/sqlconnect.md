---
title: SQLConnect |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQLConnect function
ms.assetid: 6da74e3a-4388-4907-81cb-987389bae467
author: rothja
ms.author: jroth
ms.openlocfilehash: 43b37ae16638e461e37edaead83cd9ceedc1c86d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595963"
---
# <a name="sqlconnect"></a><span data-ttu-id="73364-102">SQLConnect</span><span class="sxs-lookup"><span data-stu-id="73364-102">SQLConnect</span></span>
  <span data-ttu-id="73364-103">開啟連接時，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 會將 SQL_COPT_SS_MUTUALLY_AUTHENTICATED 和 SQL_COPT_SS_INTEGRATED_AUTHENTICATION_METHOD 設定為開啟連接所使用的驗證方法。</span><span class="sxs-lookup"><span data-stu-id="73364-103">When a connection is opened, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client sets SQL_COPT_SS_MUTUALLY_AUTHENTICATED and SQL_COPT_SS_INTEGRATED_AUTHENTICATION_METHOD to the authentication method used to open the connection.</span></span> <span data-ttu-id="73364-104">如需 Spn 的詳細資訊，請參閱[&#40;ODBC&#41;的用戶端連接中 &#40;spn&#41; 的服務主體名稱](../native-client/odbc/service-principal-names-spns-in-client-connections-odbc.md)。</span><span class="sxs-lookup"><span data-stu-id="73364-104">For more information about SPNs, see [Service Principal Names &#40;SPNs&#41; in Client Connections &#40;ODBC&#41;](../native-client/odbc/service-principal-names-spns-in-client-connections-odbc.md).</span></span>  
  
## <a name="sqlconnect-support-for-high-availability-disaster-recovery"></a><span data-ttu-id="73364-105">高可用性/災害復原的 SQLConnect 支援</span><span class="sxs-lookup"><span data-stu-id="73364-105">SQLConnect Support for High Availability, Disaster Recovery</span></span>  
 <span data-ttu-id="73364-106">如需使用**SQLConnect**連線到叢集的詳細資訊 [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] ，請參閱[高可用性和嚴重損壞修復 SQL Server Native Client 支援](../native-client/features/sql-server-native-client-support-for-high-availability-disaster-recovery.md)。</span><span class="sxs-lookup"><span data-stu-id="73364-106">For more information on using **SQLConnect** to connect to a [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] cluster, see [SQL Server Native Client Support for High Availability, Disaster Recovery](../native-client/features/sql-server-native-client-support-for-high-availability-disaster-recovery.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73364-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="73364-107">See Also</span></span>  
 <span data-ttu-id="73364-108">[SQLConnect 函式](https://go.microsoft.com/fwlink/?LinkId=101541) </span><span class="sxs-lookup"><span data-stu-id="73364-108">[SQLConnect Function](https://go.microsoft.com/fwlink/?LinkId=101541) </span></span>  
 [<span data-ttu-id="73364-109">ODBC API 實作詳細資料</span><span class="sxs-lookup"><span data-stu-id="73364-109">ODBC API Implementation Details</span></span>](odbc-api-implementation-details.md)  
  
  
