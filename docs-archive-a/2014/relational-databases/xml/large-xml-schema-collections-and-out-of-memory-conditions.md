---
title: 大型的 XML 結構描述集合與記憶體不足的情況 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- out-of-memory conditions
- XML schema collections [SQL Server], large
ms.assetid: 29b9d839-aaaf-48fb-be17-840c751f36f1
author: rothja
ms.author: jroth
ms.openlocfilehash: 8443207bbbdff5db7e54d61fcebabe70e34cc540
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710409"
---
# <a name="large-xml-schema-collections-and-out-of-memory-conditions"></a><span data-ttu-id="ab8b9-102">大型的 XML 結構描述集合與記憶體不足的情況</span><span class="sxs-lookup"><span data-stu-id="ab8b9-102">Large XML Schema Collections and Out-of-Memory Conditions</span></span>
  <span data-ttu-id="ab8b9-103">在大型的 XML 結構描述集合中呼叫內建 XML_SCHEMA_NAMESPACE() 函數時，或是當您嘗試卸除大型 XML 結構描述集合時，就可能會發生記憶體不足的情況。</span><span class="sxs-lookup"><span data-stu-id="ab8b9-103">During a call to the built-in XML_SCHEMA_NAMESPACE() function on a large XML schema collection, or when you try to drop large XML schema collections, an out-of-memory condition may occur.</span></span> <span data-ttu-id="ab8b9-104">下列是您可用來處理此情形的解決方案：</span><span class="sxs-lookup"><span data-stu-id="ab8b9-104">The following are solutions you can use to handle this:</span></span>  
  
-   <span data-ttu-id="ab8b9-105">當系統負載很輕時，使用 DROP_XML_SCHEMA_COLLECTION 命令。</span><span class="sxs-lookup"><span data-stu-id="ab8b9-105">When the system load is light, use the DROP_XML_SCHEMA_COLLECTION command.</span></span> <span data-ttu-id="ab8b9-106">如果這個命令失敗，請使用 ALTER DATABASE 陳述式和再次嘗試 DROP XML SCHEMA COLLECTION，以便將資料庫切換到單一使用者模式中。</span><span class="sxs-lookup"><span data-stu-id="ab8b9-106">If this fails, put the database in single-user mode by using the ALTER DATABASE statement and trying DROP XML SCHEMA COLLECTION again.</span></span> <span data-ttu-id="ab8b9-107">如果 XML 結構描述集合存在於 **master**、 **model**或 **tempdb**中，則單一使用者模式將需要重新啟動伺服器。</span><span class="sxs-lookup"><span data-stu-id="ab8b9-107">If the XML schema collection exists in **master**, **model**, or **tempdb**, a server restart is required for single-user mode.</span></span>  
  
-   <span data-ttu-id="ab8b9-108">當您呼叫 XML_SCHEMA_NAMESPACE 時，可以嘗試擷取單一 XML 結構描述命名空間、可以在系統負載較輕時嘗試呼叫，也可以在單一使用者模式中嘗試呼叫。</span><span class="sxs-lookup"><span data-stu-id="ab8b9-108">When you call the XML_SCHEMA_NAMESPACE, you can try to retrieve a single XML schema namespace, you can try the call when the system load is lighter, or you can try the call in single-user mode.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab8b9-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ab8b9-109">See Also</span></span>  
 [<span data-ttu-id="ab8b9-110">伺服器上 XML 結構描述集合的需求與限制</span><span class="sxs-lookup"><span data-stu-id="ab8b9-110">Requirements and Limitations for XML Schema Collections on the Server</span></span>](requirements-and-limitations-for-xml-schema-collections-on-the-server.md)  
  
  
