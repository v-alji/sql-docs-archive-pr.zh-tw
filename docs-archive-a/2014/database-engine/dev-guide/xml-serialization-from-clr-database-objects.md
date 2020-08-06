---
title: 從 CLR 資料庫物件進行 XML 序列化 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
helpviewer_keywords:
- serialization
- XML serialization [CLR integration]
- common language runtime [SQL Server], XML serialization
- XmlSerializer class
ms.assetid: ac84339b-9384-4710-bebc-01607864a344
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: ee93ee4b7bf9cba3f11b329244d4523636cb7704
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701650"
---
# <a name="xml-serialization-from-clr-database-objects"></a><span data-ttu-id="e3343-102">從 CLR 資料庫物件進行 XML 序列化</span><span class="sxs-lookup"><span data-stu-id="e3343-102">XML Serialization from CLR Database Objects</span></span>
  <span data-ttu-id="e3343-103">XML 序列化是下列兩種狀況所需的作業：</span><span class="sxs-lookup"><span data-stu-id="e3343-103">XML serialization is required for two scenarios:</span></span>  
  
-   <span data-ttu-id="e3343-104">從 Common Language Runtime (CLR) 物件叫用 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="e3343-104">Invoking Web Services from common language runtime (CLR) objects.</span></span>  
  
-   <span data-ttu-id="e3343-105">將使用者定義型別 (UDT) 轉換成 XML。</span><span class="sxs-lookup"><span data-stu-id="e3343-105">Converting a user-defined type (UDT) to XML.</span></span>  
  
 <span data-ttu-id="e3343-106">叫用 `XmlSerializer` 類別來執行 XML 序列化通常會產生額外的序列化組件，而且此組件會多載進入含有來源組件的專案中。</span><span class="sxs-lookup"><span data-stu-id="e3343-106">Performing XML serialization by invoking the `XmlSerializer` class normally generates an additional serialization assembly that is overloaded into the project with the source assembly.</span></span> <span data-ttu-id="e3343-107">不過，基於安全性考量，這個多載在 CLR 中已停用。</span><span class="sxs-lookup"><span data-stu-id="e3343-107">However, for security purposes, this overload is disabled in the CLR.</span></span> <span data-ttu-id="e3343-108">因此，若要在內部呼叫 web 服務或執行從 UDT 到 XML [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的轉換，則必須使用稱為**Sgen.exe**的工具，以產生必要序列化元件的 .NET Framework 來手動建立元件。</span><span class="sxs-lookup"><span data-stu-id="e3343-108">Therefore, to call a web service or perform conversion from UDT to XML inside [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the assembly must be created manually using a tool called **Sgen.exe** provided with the .NET Framework that generates the necessary serialization assemblies.</span></span> <span data-ttu-id="e3343-109">叫用 `XmlSerializer` 時，您必須遵循下列步驟，手動建立序列化組件：</span><span class="sxs-lookup"><span data-stu-id="e3343-109">When invoking `XmlSerializer`, the serialization assembly must be created manually by following these steps:</span></span>  
  
1.  <span data-ttu-id="e3343-110">執行 .NET Framework SDK 所提供的**Sgen.exe**工具，以建立包含來源元件之 XML 序列化程式的元件。</span><span class="sxs-lookup"><span data-stu-id="e3343-110">Run the **Sgen.exe** tool that is provided with the .NET Framework SDK to create the assembly containing the XML serializers for the source assembly.</span></span>  
  
2.  <span data-ttu-id="e3343-111">使用 `CREATE ASSEMBLY` 陳述式，在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中註冊已產生的組件。</span><span class="sxs-lookup"><span data-stu-id="e3343-111">Register the generated assembly in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using the `CREATE ASSEMBLY` statement.</span></span>  
  
 <span data-ttu-id="e3343-112">如需執行 XML 序列化時可能會收到之錯誤的相關資訊，請參閱下列 Microsoft 支援服務文章：「[無法載入動態產生的序列化元件](https://support.microsoft.com/kb/913668)」。</span><span class="sxs-lookup"><span data-stu-id="e3343-112">For information about errors that you may receive when performing XML serialization, see the following Microsoft Support article: ["Cannot load dynamically generated serialization assembly"](https://support.microsoft.com/kb/913668).</span></span>  
  
 <span data-ttu-id="e3343-113">如需有關 XMLSerializer 不支援之資料類型的詳細資訊，請參閱 .NET Framework 文件集中的＜.NET Framework 中的 XML 結構描述繫結支援＞。</span><span class="sxs-lookup"><span data-stu-id="e3343-113">For information on data types that are not supported by XMLSerializer, see XML Schema Binding Support in the .NET Framework in the .NET Framework documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3343-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e3343-114">See Also</span></span>  
 <span data-ttu-id="e3343-115">[從 CLR 資料庫物件進行資料存取](../../relational-databases/clr-integration/data-access/data-access-from-clr-database-objects.md) </span><span class="sxs-lookup"><span data-stu-id="e3343-115">[Data Access from CLR Database Objects](../../relational-databases/clr-integration/data-access/data-access-from-clr-database-objects.md) </span></span>  
 [<span data-ttu-id="e3343-116">CREATE ASSEMBLY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="e3343-116">CREATE ASSEMBLY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-assembly-transact-sql)  
  
  
