---
title: ICommandWithParameters | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: 66644c70-def7-46d8-8c47-b883292a0288
author: rothja
ms.author: jroth
ms.openlocfilehash: df3103181b3cad772e7d1c73068b8864bf591b73
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599494"
---
# <a name="icommandwithparameters"></a><span data-ttu-id="65d92-102">ICommandWithParameters</span><span class="sxs-lookup"><span data-stu-id="65d92-102">ICommandWithParameters</span></span>
  <span data-ttu-id="65d92-103">從 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 開始，資料庫引擎的改進功能就允許 ICommandWithParameters::GetParameterInfo 針對預期的結果取得更精確的描述。</span><span class="sxs-lookup"><span data-stu-id="65d92-103">Improvements in the database engine beginning with [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] allow ICommandWithParameters::GetParameterInfo to obtain more accurate descriptions of the expected results.</span></span> <span data-ttu-id="65d92-104">這些更精確的結果可能與舊版 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中 CommandWithParameters::GetParameterInfo 所傳回的值不同。</span><span class="sxs-lookup"><span data-stu-id="65d92-104">These more accurate results may differ from the values returned by CommandWithParameters::GetParameterInfo in previous versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="65d92-105">如需詳細資訊，請參閱[中繼資料探索](../native-client/features/metadata-discovery.md)。</span><span class="sxs-lookup"><span data-stu-id="65d92-105">For more information, see [Metadata Discovery](../native-client/features/metadata-discovery.md).</span></span>  
  
 <span data-ttu-id="65d92-106">此外，從 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 開始，當您呼叫 ICommandWithParameters::SetParameterInfo 時，傳遞給 *pwszName* 參數的值必須是有效的識別碼。</span><span class="sxs-lookup"><span data-stu-id="65d92-106">Also beginning in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], when calling ICommandWithParameters::SetParameterInfo, the value passed to the *pwszName* parameter must be a valid identifier.</span></span> <span data-ttu-id="65d92-107">如需詳細資訊，請參閱＜ [Database Identifiers](../databases/database-identifiers.md)＞。</span><span class="sxs-lookup"><span data-stu-id="65d92-107">For more information, see [Database Identifiers](../databases/database-identifiers.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65d92-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="65d92-108">See Also</span></span>  
 [<span data-ttu-id="65d92-109">介面 &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="65d92-109">Interfaces &#40;OLE DB&#41;</span></span>](../../database-engine/dev-guide/interfaces-ole-db.md)  
  
  
