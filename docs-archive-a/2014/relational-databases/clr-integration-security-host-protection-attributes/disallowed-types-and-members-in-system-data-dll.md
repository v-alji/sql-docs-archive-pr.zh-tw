---
title: System.Data.dll 中不允許的類型和成員 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- host protection attributes [CLR integration]
- common language runtime [SQL Server], host protection attributes
ms.assetid: ee5f55e9-fbef-401a-be18-a2e5873c8720
author: rothja
ms.author: jroth
ms.openlocfilehash: cd62f6f0a90bd167f20a33f8de749acc982f39b3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594107"
---
# <a name="disallowed-types-and-members-in-systemdatadll"></a><span data-ttu-id="d5490-102">在 System.Data.dll 中不允許的類型和成員</span><span class="sxs-lookup"><span data-stu-id="d5490-102">Disallowed Types and Members in System.Data.dll</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="d5490-103">通用語言整合 (CLR) 程式設計不允許使用具有的類型或成員，其 `HostProtectionAttribute` 指定的 `System.Security.Permissions.HostProtectionResource` 列舉值為、、、、、 `ExternalProcessMgmt` `ExternalThreading` `MayLeakOnAbort` `SecurityInfrastructure` `SelfAffectingProcessMgmnt` `SelfAffectingThreading` 、 **SharedState**、 `Synchronization` 或 `UI` 。</span><span class="sxs-lookup"><span data-stu-id="d5490-103">common language integration (CLR) programming disallows the use of a type or member that has a `HostProtectionAttribute` that specifies a `System.Security.Permissions.HostProtectionResource` enumeration with a value of `ExternalProcessMgmt`, `ExternalThreading`, `MayLeakOnAbort`, `SecurityInfrastructure`, `SelfAffectingProcessMgmnt`, `SelfAffectingThreading`, **SharedState**, `Synchronization`, or `UI`.</span></span> <span data-ttu-id="d5490-104">下表列出 System.Data.dll 組件的成員和類型，這些成員和類型的主機保護屬性 (HPA) 值不被允許。</span><span class="sxs-lookup"><span data-stu-id="d5490-104">The following table lists the members and types of the System.Data.dll assembly whose Host Protection Attribute (HPA) values are disallowed.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d5490-105">此清單是根據支援的組件產生的。</span><span class="sxs-lookup"><span data-stu-id="d5490-105">This list was generated from the supported assemblies.</span></span> <span data-ttu-id="d5490-106">如需詳細資訊，請參閱[支援的 .NET Framework 程式庫](../clr-integration/database-objects/supported-net-framework-libraries.md)。</span><span class="sxs-lookup"><span data-stu-id="d5490-106">For more information, see [Supported .NET Framework Libraries](../clr-integration/database-objects/supported-net-framework-libraries.md).</span></span>  
  
|<span data-ttu-id="d5490-107">類型或成員</span><span class="sxs-lookup"><span data-stu-id="d5490-107">Type or Member</span></span>|<span data-ttu-id="d5490-108">HPA 值</span><span class="sxs-lookup"><span data-stu-id="d5490-108">HPA Value(s)</span></span>|  
|--------------------|--------------------|  
|<span data-ttu-id="d5490-109">System.Data.SqlClient.SqlCommand.BeginExecuteNonQuery()</span><span class="sxs-lookup"><span data-stu-id="d5490-109">System.Data.SqlClient.SqlCommand.BeginExecuteNonQuery()</span></span>|<span data-ttu-id="d5490-110">ExternalThreading</span><span class="sxs-lookup"><span data-stu-id="d5490-110">ExternalThreading</span></span>|  
|<span data-ttu-id="d5490-111">System.Data.SqlClient.SqlCommand.BeginExecuteReader()</span><span class="sxs-lookup"><span data-stu-id="d5490-111">System.Data.SqlClient.SqlCommand.BeginExecuteReader()</span></span>|<span data-ttu-id="d5490-112">ExternalThreading</span><span class="sxs-lookup"><span data-stu-id="d5490-112">ExternalThreading</span></span>|  
|<span data-ttu-id="d5490-113">System.Data.SqlClient.SqlCommand.BeginExecuteXmlReader()</span><span class="sxs-lookup"><span data-stu-id="d5490-113">System.Data.SqlClient.SqlCommand.BeginExecuteXmlReader()</span></span>|<span data-ttu-id="d5490-114">ExternalThreading</span><span class="sxs-lookup"><span data-stu-id="d5490-114">ExternalThreading</span></span>|  
|<span data-ttu-id="d5490-115">System.Data.SqlClient.SqlDependency..ctor()</span><span class="sxs-lookup"><span data-stu-id="d5490-115">System.Data.SqlClient.SqlDependency..ctor()</span></span>|<span data-ttu-id="d5490-116">ExternalThreading</span><span class="sxs-lookup"><span data-stu-id="d5490-116">ExternalThreading</span></span>|  
|<span data-ttu-id="d5490-117">System.Data.SqlClient.SqlDependency.Start()</span><span class="sxs-lookup"><span data-stu-id="d5490-117">System.Data.SqlClient.SqlDependency.Start()</span></span>|<span data-ttu-id="d5490-118">ExternalThreading</span><span class="sxs-lookup"><span data-stu-id="d5490-118">ExternalThreading</span></span>|  
|<span data-ttu-id="d5490-119">System.Data.SqlClient.SqlDependency.Stop()</span><span class="sxs-lookup"><span data-stu-id="d5490-119">System.Data.SqlClient.SqlDependency.Stop()</span></span>|<span data-ttu-id="d5490-120">ExternalThreading</span><span class="sxs-lookup"><span data-stu-id="d5490-120">ExternalThreading</span></span>|  
|<span data-ttu-id="d5490-121">System.Data.TypedDataSetGenerator</span><span class="sxs-lookup"><span data-stu-id="d5490-121">System.Data.TypedDataSetGenerator</span></span>|<span data-ttu-id="d5490-122">SharedState、Synchronization</span><span class="sxs-lookup"><span data-stu-id="d5490-122">SharedState, Synchronization</span></span>|  
|<span data-ttu-id="d5490-123">System.Xml.XmlDataDocument</span><span class="sxs-lookup"><span data-stu-id="d5490-123">System.Xml.XmlDataDocument</span></span>|<span data-ttu-id="d5490-124">Synchronization</span><span class="sxs-lookup"><span data-stu-id="d5490-124">Synchronization</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d5490-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d5490-125">See Also</span></span>  
 <span data-ttu-id="d5490-126">[主機保護屬性和 CLR 整合程式設計](host-protection-attributes-and-clr-integration-programming.md) </span><span class="sxs-lookup"><span data-stu-id="d5490-126">[Host Protection Attributes and CLR Integration Programming](host-protection-attributes-and-clr-integration-programming.md) </span></span>  
 <span data-ttu-id="d5490-127">[Microsoft.VisualBasic.dll中不允許的類型和成員](disallowed-types-and-members-in-microsoft-visualbasic-dll.md) </span><span class="sxs-lookup"><span data-stu-id="d5490-127">[Disallowed Types and Members in Microsoft.VisualBasic.dll](disallowed-types-and-members-in-microsoft-visualbasic-dll.md) </span></span>  
 <span data-ttu-id="d5490-128">[mscorlib.dll中不允許的類型和成員](disallowed-types-and-members-in-mscorlib-dll.md) </span><span class="sxs-lookup"><span data-stu-id="d5490-128">[Disallowed Types and Members in mscorlib.dll](disallowed-types-and-members-in-mscorlib-dll.md) </span></span>  
 <span data-ttu-id="d5490-129">[System.dll中不允許的類型和成員](disallowed-types-and-members-in-system-dll.md) </span><span class="sxs-lookup"><span data-stu-id="d5490-129">[Disallowed Types and Members in System.dll](disallowed-types-and-members-in-system-dll.md) </span></span>  
 [<span data-ttu-id="d5490-130">System.Core.dll 中不允許的類型和成員</span><span class="sxs-lookup"><span data-stu-id="d5490-130">Disallowed Types and Members in System.Core.dll</span></span>](disallowed-types-and-members-in-system-core-dll.md)  
  
  
