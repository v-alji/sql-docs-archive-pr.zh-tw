---
title: 使用原則式管理 Facets | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- viewing Policy-Based Management facets
- facets [Policy-Based Management], copying
- facets [Policy-Based Management], viewing
- copying Policy-Based Management facets
ms.assetid: 88d025c4-07c2-4e4d-8634-204249a8c82c
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 5a356550796cc682b2292defffd6565b7fea0783
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593976"
---
# <a name="working-with-policy-based-management-facets"></a><span data-ttu-id="8bb9d-102">使用原則式管理 Facet</span><span class="sxs-lookup"><span data-stu-id="8bb9d-102">Working with Policy-Based Management Facets</span></span>
  <span data-ttu-id="8bb9d-103">原則式管理 Facet 是一組與所需管理區域相關的邏輯屬性。</span><span class="sxs-lookup"><span data-stu-id="8bb9d-103">A Policy-Based Management facet is a set of logical properties that are related to an area of management interest.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="8bb9d-104">包含數個預先定義的 Facet。</span><span class="sxs-lookup"><span data-stu-id="8bb9d-104">includes several predefined facets.</span></span> <span data-ttu-id="8bb9d-105">例如，介面區組態 Facet 會將預設關閉的功能定義成屬性。</span><span class="sxs-lookup"><span data-stu-id="8bb9d-105">For example, the Surface Area Configuration facet defines, as properties, the features that are off by default.</span></span>  
  
 <span data-ttu-id="8bb9d-106">當您管理許多相似的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 環境時，可以在其中一個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體內設定 Facet、將此 Facet 的狀態複製到檔案，然後將該檔案當作原則匯入到另一個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體中。</span><span class="sxs-lookup"><span data-stu-id="8bb9d-106">When you manage many similar [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] environments, you can configure a facet in one instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], copy the state of the facet to a file, and then import that file into another instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] as a policy.</span></span> <span data-ttu-id="8bb9d-107">當此狀態已經轉換成原則時，該原則就可以套用至 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的其他執行個體、執行個體物件、資料庫或資料庫物件。</span><span class="sxs-lookup"><span data-stu-id="8bb9d-107">When the state has been converted to a policy, the policy can be applied to other instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], instance objects, databases, or database objects.</span></span>  
  
 <span data-ttu-id="8bb9d-108">此主題描述如何將 Facet 的狀態複製到 XML 檔。</span><span class="sxs-lookup"><span data-stu-id="8bb9d-108">This topic describes how to copy the state of a facet to an XML file.</span></span>  
  
##  <a name="permissions"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="8bb9d-109">權限</span><span class="sxs-lookup"><span data-stu-id="8bb9d-109">Permissions</span></span>  
 <span data-ttu-id="8bb9d-110">本主題中的程序需要 msdb 資料庫的 PolicyAdministratorRole 角色成員資格。</span><span class="sxs-lookup"><span data-stu-id="8bb9d-110">The procedures in this topic require membership in the PolicyAdministratorRole role in the msdb database.</span></span>  
  
## <a name="viewing-and-copying-facet-states"></a><span data-ttu-id="8bb9d-111">檢視和複製 Facet 狀態</span><span class="sxs-lookup"><span data-stu-id="8bb9d-111">Viewing and Copying Facet States</span></span>  
 [<span data-ttu-id="8bb9d-112">檢視 SQL Server 物件的原則式管理 Facet</span><span class="sxs-lookup"><span data-stu-id="8bb9d-112">View the Policy-Based Management Facets on a SQL Server Object</span></span>](view-the-policy-based-management-facets-on-a-sql-server-object.md)  
  
 [<span data-ttu-id="8bb9d-113">將原則式管理 Facet 狀態複製到 XML 檔案</span><span class="sxs-lookup"><span data-stu-id="8bb9d-113">Copy a Policy-Based Management Facet State to an XML File</span></span>](copy-a-policy-based-management-facet-state-to-an-xml-file.md)  
  
## <a name="see-also"></a><span data-ttu-id="8bb9d-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8bb9d-114">See Also</span></span>  
 [<span data-ttu-id="8bb9d-115">使用原則式管理來管理伺服器</span><span class="sxs-lookup"><span data-stu-id="8bb9d-115">Administer Servers by Using Policy-Based Management</span></span>](administer-servers-by-using-policy-based-management.md)  
  
  
