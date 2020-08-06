---
title: ICommand (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ICommand [SQL Server Native Client]
ms.assetid: 5e24b3a0-0658-44fc-b653-f4c52f9eb328
author: rothja
ms.author: jroth
ms.openlocfilehash: 03bdccc83a04078210f2283d0b330f237ed02979
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599496"
---
# <a name="icommand-ole-db"></a><span data-ttu-id="efbea-102">ICommand (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="efbea-102">ICommand (OLE DB)</span></span>
  <span data-ttu-id="efbea-103">本主題討論 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 特有的 OLE DB 行為。</span><span class="sxs-lookup"><span data-stu-id="efbea-103">This topic discusses OLE DB behavior that is specific to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.</span></span>  
  
## <a name="icommandexecute"></a><span data-ttu-id="efbea-104">ICommand::Execute</span><span class="sxs-lookup"><span data-stu-id="efbea-104">ICommand::Execute</span></span>  
 <span data-ttu-id="efbea-105">插入大於資料行大小的資料通常會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="efbea-105">Inserting data that is greater than the size of a column typically results in an error.</span></span> <span data-ttu-id="efbea-106">不過，在一些狀況下會傳回 S_OK，但是會將 *dwStatus* 設定為 DBSTATUS_S_TRUNCATED。</span><span class="sxs-lookup"><span data-stu-id="efbea-106">However, there are situations where S_OK will be returned but the *dwStatus* will be set to DBSTATUS_S_TRUNCATED.</span></span> <span data-ttu-id="efbea-107">使用參數插入資料時，如果資料行不夠大，無法保存資料而且尚未呼叫 `ICommandWithParameters::SetParameterInfo`，通常會發生這種情況。</span><span class="sxs-lookup"><span data-stu-id="efbea-107">This generally occurs when inserting data with parameters, where the column is not large enough to hold the data, and `ICommandWithParameters::SetParameterInfo` has not been called.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="efbea-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="efbea-108">See Also</span></span>  
 [<span data-ttu-id="efbea-109">介面 &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="efbea-109">Interfaces &#40;OLE DB&#41;</span></span>](../../database-engine/dev-guide/interfaces-ole-db.md)  
  
  
