---
title: 登入 SQL Server 的執行個體 (命令提示字元) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- logins [SQL Server], named instance of SQL Server
- log ins [SQL Server]
- logins [SQL Server], default instance of SQL Server
- command prompt [SQL Server], logins
- logging in [SQL Server]
ms.assetid: f67c11e3-c519-40c9-82c1-07efa9d9985e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 32028a30786117f2cafa76150867a0e726b07cda
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585584"
---
# <a name="log-in-to-an-instance-of-sql-server-command-prompt"></a><span data-ttu-id="99bfd-102">登入 SQL Server 的執行個體 (命令提示字元)</span><span class="sxs-lookup"><span data-stu-id="99bfd-102">Log In to an Instance of SQL Server (Command Prompt)</span></span>
  <span data-ttu-id="99bfd-103">本主題描述如何使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]sqlcmd **公用程式測試** 執行個體的連線。</span><span class="sxs-lookup"><span data-stu-id="99bfd-103">This topic describes how to test connectivity to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], use the **sqlcmd** utility.</span></span>  
  
##  <a name="SSMSProcedure"></a>  
  
#### <a name="to-log-in-to-the-default-instance-of-sql-server"></a><span data-ttu-id="99bfd-104">若要登入 SQL Server 的預設執行個體</span><span class="sxs-lookup"><span data-stu-id="99bfd-104">To log in to the default instance of SQL Server</span></span>  
  
1.  <span data-ttu-id="99bfd-105">在命令提示字元中，輸入下列命令即可使用 [Windows 驗證] 進行連接：</span><span class="sxs-lookup"><span data-stu-id="99bfd-105">From a command prompt, enter the following command to connect by using Windows Authentication:</span></span>  
  
    ```  
    sqlcmd [ /E ] [ /S servername ]  
  
    ```  
  
#### <a name="to-log-in-to-a-named-instance-of-sql-server"></a><span data-ttu-id="99bfd-106">若要登入 SQL Server 的具名執行個體</span><span class="sxs-lookup"><span data-stu-id="99bfd-106">To log in to a named instance of SQL Server</span></span>  
  
1.  <span data-ttu-id="99bfd-107">在命令提示字元中，輸入下列命令即可使用 [Windows 驗證] 進行連接：</span><span class="sxs-lookup"><span data-stu-id="99bfd-107">From a command prompt, enter the following command to connect by using Windows Authentication:</span></span>  
  
    ```  
    sqlcmd [ /E ] /S servername\instancename  
  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="99bfd-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="99bfd-108">See Also</span></span>  
 <span data-ttu-id="99bfd-109">[sqlcmd 公用程式](../../tools/sqlcmd-utility.md) </span><span class="sxs-lookup"><span data-stu-id="99bfd-109">[sqlcmd Utility](../../tools/sqlcmd-utility.md) </span></span>  
 [<span data-ttu-id="99bfd-110">osql 公用程式</span><span class="sxs-lookup"><span data-stu-id="99bfd-110">osql Utility</span></span>](../../tools/osql-utility.md)  
  
  
