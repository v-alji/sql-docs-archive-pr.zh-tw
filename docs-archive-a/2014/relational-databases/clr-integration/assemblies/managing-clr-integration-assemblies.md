---
title: 管理 CLR 整合元件 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
dev_langs:
- TSQL
helpviewer_keywords:
- database objects [CLR integration], assemblies
- common language runtime [SQL Server], assemblies
- assemblies [CLR integration], managing
ms.assetid: bdbbf325-14f6-460e-a35a-d3861d3c961e
author: rothja
ms.author: jroth
ms.openlocfilehash: 191ccd73ca42ef4c26291e6de88f5f2b0cf565ef
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704157"
---
# <a name="managing-clr-integration-assemblies"></a><span data-ttu-id="d67bd-102">管理 CLR 整合組件</span><span class="sxs-lookup"><span data-stu-id="d67bd-102">Managing CLR Integration Assemblies</span></span>
  <span data-ttu-id="d67bd-103">Managed 程式碼會經過編譯，然後以稱為組件的單位進行部署。</span><span class="sxs-lookup"><span data-stu-id="d67bd-103">Managed code is compiled and then deployed in units called an assembly.</span></span> <span data-ttu-id="d67bd-104">組件會封裝為 DLL 或可執行檔 (.exe)。</span><span class="sxs-lookup"><span data-stu-id="d67bd-104">An assembly is packaged as a DLL or executable (.exe) file.</span></span> <span data-ttu-id="d67bd-105">可執行檔可以自行執行，而 DLL 則必須裝載在現有的應用程式中。</span><span class="sxs-lookup"><span data-stu-id="d67bd-105">While an executable file can run on its own, a DLL must be hosted in an existing application.</span></span> <span data-ttu-id="d67bd-106">Managed DLL 元件可以載入並由裝載 [!INCLUDE[msCoName](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="d67bd-106">Managed DLL assemblies can be loaded into and hosted by [!INCLUDE[msCoName](../../../includes/ssnoversion-md.md)].</span></span> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]<span data-ttu-id="d67bd-107">使用 CREATE ASSEMBLY 語句的資料庫，然後才可以在進程中載入並使用它。</span><span class="sxs-lookup"><span data-stu-id="d67bd-107">database using the CREATE ASSEMBLY statement, before it can be loaded in the process and used.</span></span> <span data-ttu-id="d67bd-108">這些組件也可以使用 ALTER ASSEMBLY 陳述式，從比較新的版本升級，或者使用 DROP ASSEMBLY 陳述式，從 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 移除。</span><span class="sxs-lookup"><span data-stu-id="d67bd-108">Assemblies can also be updated from a more recent version using the ALTER ASSEMBLY statement, or removed from [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] using the DROP ASSEMBLY statement.</span></span>  
  
 <span data-ttu-id="d67bd-109">組件資訊會儲存在安裝該組件所在資料庫的 `sys.assembly_files` 資料表中。</span><span class="sxs-lookup"><span data-stu-id="d67bd-109">Assembly information is stored in the `sys.assembly_files` table in the database where the assembly has been installed.</span></span> <span data-ttu-id="d67bd-110">`sys.assembly_files` 資料表包含下列資料行。</span><span class="sxs-lookup"><span data-stu-id="d67bd-110">The `sys.assembly_files` table contains the following columns.</span></span>  
  
|<span data-ttu-id="d67bd-111">資料行</span><span class="sxs-lookup"><span data-stu-id="d67bd-111">Column</span></span>|<span data-ttu-id="d67bd-112">描述</span><span class="sxs-lookup"><span data-stu-id="d67bd-112">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="d67bd-113">assembly_id</span><span class="sxs-lookup"><span data-stu-id="d67bd-113">assembly_id</span></span>|<span data-ttu-id="d67bd-114">為組件定義的識別項。</span><span class="sxs-lookup"><span data-stu-id="d67bd-114">The identifier defined for the assembly.</span></span> <span data-ttu-id="d67bd-115">此號碼會指派給與同一組件相關的所有物件。</span><span class="sxs-lookup"><span data-stu-id="d67bd-115">This number is assigned to all objects relating to the same assembly.</span></span>|  
|<span data-ttu-id="d67bd-116">NAME</span><span class="sxs-lookup"><span data-stu-id="d67bd-116">name</span></span>|<span data-ttu-id="d67bd-117">物件的名稱。</span><span class="sxs-lookup"><span data-stu-id="d67bd-117">The name of the object.</span></span>|  
|<span data-ttu-id="d67bd-118">file_id</span><span class="sxs-lookup"><span data-stu-id="d67bd-118">file_id</span></span>|<span data-ttu-id="d67bd-119">識別每個物件的數字，其中會將 1 的值指派給與給定 `assembly_id` 相關聯的第一個物件。</span><span class="sxs-lookup"><span data-stu-id="d67bd-119">A number identifying each object, with the first object associated with a given `assembly_id` being given the value of 1.</span></span> <span data-ttu-id="d67bd-120">如果有多個物件與相同的 `assembly_id` 相關聯，則每個後續的 `file_id` 值都會以 1 遞增。</span><span class="sxs-lookup"><span data-stu-id="d67bd-120">If multiple objects are associated with the same `assembly_id`, then each subsequent `file_id` value is incremented by 1.</span></span>|  
|<span data-ttu-id="d67bd-121">內容</span><span class="sxs-lookup"><span data-stu-id="d67bd-121">content</span></span>|<span data-ttu-id="d67bd-122">組件或檔案的十六進位表示法。</span><span class="sxs-lookup"><span data-stu-id="d67bd-122">The hexadecimal representation of the assembly or file.</span></span>|  
  
## <a name="in-this-section"></a><span data-ttu-id="d67bd-123">本節內容</span><span class="sxs-lookup"><span data-stu-id="d67bd-123">In This Section</span></span>  
 [<span data-ttu-id="d67bd-124">建立組件</span><span class="sxs-lookup"><span data-stu-id="d67bd-124">Creating an Assembly</span></span>](creating-an-assembly.md)  
 <span data-ttu-id="d67bd-125">討論如何在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中建立 SAFE、EXTERNAL_ACCESS 與 UNSAFE CLR 組件。</span><span class="sxs-lookup"><span data-stu-id="d67bd-125">Discusses creating SAFE, EXTERNAL_ACCESS, and UNSAFE CLR assemblies in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="d67bd-126">變更組件</span><span class="sxs-lookup"><span data-stu-id="d67bd-126">Altering an Assembly</span></span>](altering-an-assembly.md)  
 <span data-ttu-id="d67bd-127">描述如何在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中更新 CLR 組件。</span><span class="sxs-lookup"><span data-stu-id="d67bd-127">Describes updating CLR assemblies in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="d67bd-128">卸除組件</span><span class="sxs-lookup"><span data-stu-id="d67bd-128">Dropping an Assembly</span></span>](dropping-an-assembly.md)  
 <span data-ttu-id="d67bd-129">討論如何從 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 卸除 CLR 組件。</span><span class="sxs-lookup"><span data-stu-id="d67bd-129">Discusses dropping CLR assemblies from [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d67bd-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d67bd-130">See Also</span></span>  
 <span data-ttu-id="d67bd-131">[CLR 整合安全性](../security/clr-integration-security.md) </span><span class="sxs-lookup"><span data-stu-id="d67bd-131">[CLR Integration Security](../security/clr-integration-security.md) </span></span>  
 [<span data-ttu-id="d67bd-132">CLR 整合程式碼存取安全性</span><span class="sxs-lookup"><span data-stu-id="d67bd-132">CLR Integration Code Access Security</span></span>](../security/clr-integration-code-access-security.md)  
  
  
