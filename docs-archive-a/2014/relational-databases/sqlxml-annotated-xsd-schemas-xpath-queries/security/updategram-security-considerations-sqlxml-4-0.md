---
title: Updategram (SQLXML 4.0) 的安全性考慮 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- SQLXML, updategrams
- security [SQLXML], updategrams
- updategrams [SQLXML], security
ms.assetid: 00dc6cf4-a2e8-4cca-bdd6-d5122102a82d
author: rothja
ms.author: jroth
ms.openlocfilehash: eb0319285e6e8cf6e8b3e70f3eb6b9923de06f55
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598775"
---
# <a name="updategram-security-considerations-sqlxml-40"></a><span data-ttu-id="626a8-102">Updategram 安全性考量 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="626a8-102">Updategram Security Considerations (SQLXML 4.0)</span></span>
  <span data-ttu-id="626a8-103">下面是使用 Updategram 的安全性指導方針：</span><span class="sxs-lookup"><span data-stu-id="626a8-103">The following are security guidelines for using updategrams:</span></span>  
  
-   <span data-ttu-id="626a8-104">當您使用 Updategram 來更新資料時，請避免使用預設對應。</span><span class="sxs-lookup"><span data-stu-id="626a8-104">Avoid using default mapping when you use updategrams to update data.</span></span> <span data-ttu-id="626a8-105">當您使用預設對應時，Updategram 中的元素名稱會對應至資料表名稱，而且屬性名稱會對應至資料行。</span><span class="sxs-lookup"><span data-stu-id="626a8-105">When you use default mapping, an element name in an updategram maps to a table name, and an attribute name maps to a column.</span></span> <span data-ttu-id="626a8-106">這樣會公開資料庫中的資料庫資料表和資料行資訊，因而可能產生安全性風險。</span><span class="sxs-lookup"><span data-stu-id="626a8-106">This exposes the database table and column information in the database, which can be a potential security risk.</span></span> <span data-ttu-id="626a8-107">不過，如果您指定不同的對應結構描述 (將 Updategram 中的元素和屬性對應至資料庫資料表和資料行)，您的 Updategram 元素和屬性名稱可能就是任意的，而且此結構描述會針對這些名稱與資料庫資料表和資料行進行必要的對應。</span><span class="sxs-lookup"><span data-stu-id="626a8-107">Instead, if you specify a separate mapping schema that maps the elements and attributes in an updategram to the database tables and columns, your updategram element and attribute names can be arbitrary, and the schema does necessary mapping of these names to the database tables and columns.</span></span> <span data-ttu-id="626a8-108">因此，資料庫資訊就不會在 Updategram 中公開。</span><span class="sxs-lookup"><span data-stu-id="626a8-108">Thus, the database information is not exposed in an updategram.</span></span>  
  
-   <span data-ttu-id="626a8-109">請勿允許使用者建立和執行其 Updategram。</span><span class="sxs-lookup"><span data-stu-id="626a8-109">Do not allow users to create and execute their updategrams.</span></span> <span data-ttu-id="626a8-110">建議您將 Updategram 放置於伺服器上成為範本，而非以動態方式在 ASP 類型的應用程式中建立它們，因為這樣會讓資料庫中的資料面臨風險。</span><span class="sxs-lookup"><span data-stu-id="626a8-110">It is recommended having updategrams reside as templates on a server rather than creating them dynamically in ASP-type applications, which could put the data in the database at risk.</span></span> <span data-ttu-id="626a8-111">僅允許使用者透過當做範本提供的 Updategram 來存取資料可以降低這項風險。</span><span class="sxs-lookup"><span data-stu-id="626a8-111">Allowing users to access the data only through the updategrams provided as templates, can eliminate this risk.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="626a8-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="626a8-112">See Also</span></span>  
 [<span data-ttu-id="626a8-113">使用 Updategram 來修改 SQLXML 4.0 中的資料</span><span class="sxs-lookup"><span data-stu-id="626a8-113">Using Updategrams to Modify Data in SQLXML 4.0</span></span>](../updategrams/using-updategrams-to-modify-data-in-sqlxml-4-0.md)  
  
  
