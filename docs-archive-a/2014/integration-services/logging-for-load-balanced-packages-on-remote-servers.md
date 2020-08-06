---
title: 遠端伺服器上負載平衡封裝的記錄 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- logs [Integration Services], remote packages
ms.assetid: fd571567-b625-4f9a-8b7e-42c5c588b11b
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b45fa6607d6edc1559d8ebcbbbc7598e11eac408
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596108"
---
# <a name="logging-for-load-balanced-packages-on-remote-servers"></a><span data-ttu-id="b8e78-102">遠端伺服器上負載平衡封裝的記錄</span><span class="sxs-lookup"><span data-stu-id="b8e78-102">Logging for Load Balanced Packages on Remote Servers</span></span>
  <span data-ttu-id="b8e78-103">當所有子封裝都使用相同的記錄提供者，而且全部寫入同一個目的地時，可以讓管理員較容易管理各種伺服器上執行之所有子封裝的記錄檔。</span><span class="sxs-lookup"><span data-stu-id="b8e78-103">It is easier for an administrator to manage the logs for all the child packages that are running on various servers when all the child packages use the same log provider and they all write to the same destination.</span></span> <span data-ttu-id="b8e78-104">為所有子封裝建立共用記錄檔的其中一個方法，就是透過設定子封裝，使它們將事件記錄到 SQL Server 記錄提供者。</span><span class="sxs-lookup"><span data-stu-id="b8e78-104">One way that you can create a common log file for all child packages is to configure the child packages to log their events to a SQL Server log provider.</span></span> <span data-ttu-id="b8e78-105">您可以將所有封裝設定成使用同一個資料庫、同一部伺服器，以及伺服器的同一個執行個體。</span><span class="sxs-lookup"><span data-stu-id="b8e78-105">You can configure all the packages to use the same database, the same server, and the same instance of the server.</span></span>  
  
 <span data-ttu-id="b8e78-106">若要檢視記錄檔，管理員只需登入單一伺服器即可檢視所有子封裝的記錄檔。</span><span class="sxs-lookup"><span data-stu-id="b8e78-106">To view the log files, the administrator only has to log on to a single server to view the log files for all child packages.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="b8e78-107">相關工作</span><span class="sxs-lookup"><span data-stu-id="b8e78-107">Related Tasks</span></span>  
 <span data-ttu-id="b8e78-108">如需如何啟用封裝中記錄的資訊，請參閱 [在 SQL Server Data Tools 中啟用封裝記錄功能](../../2014/integration-services/enable-package-logging-in-sql-server-data-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="b8e78-108">For information about how to enable logging in a package, see [Enable Package Logging in SQL Server Data Tools](../../2014/integration-services/enable-package-logging-in-sql-server-data-tools.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8e78-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b8e78-109">See Also</span></span>  
 [<span data-ttu-id="b8e78-110">Integration Services &#40;SSIS&#41; 記錄</span><span class="sxs-lookup"><span data-stu-id="b8e78-110">Integration Services &#40;SSIS&#41; Logging</span></span>](performance/integration-services-ssis-logging.md)  
  
  
