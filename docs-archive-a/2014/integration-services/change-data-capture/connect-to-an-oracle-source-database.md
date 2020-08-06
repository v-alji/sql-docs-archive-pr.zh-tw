---
title: 連線到 Oracle 來源資料庫 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- oraDb
ms.assetid: 220cf555-0db2-443c-8f87-8e413f3ca731
author: chugugrace
ms.author: chugu
ms.openlocfilehash: fccba3d11adc67b3f5ef4f8648ec5d0de07a5648
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704353"
---
# <a name="connect-to-an-oracle-source-database"></a><span data-ttu-id="bdbf2-102">連接到 Oracle 來源資料庫</span><span class="sxs-lookup"><span data-stu-id="bdbf2-102">Connect to an Oracle Source Database</span></span>
  <span data-ttu-id="bdbf2-103">使用 [Oracle 來源] 頁面可提供連接至 Oracle 來源資料庫所需的資訊。</span><span class="sxs-lookup"><span data-stu-id="bdbf2-103">Use the Oracle Source page to provide the information necessary to connect to the Oracle source database.</span></span> <span data-ttu-id="bdbf2-104">此 CDC 執行個體將會讀取您所連接之 Oracle 資料庫的重做記錄。</span><span class="sxs-lookup"><span data-stu-id="bdbf2-104">The CDC instance will read the redo logs of the Oracle database you are connected to.</span></span>  
  
 <span data-ttu-id="bdbf2-105">**Oracle 連接字串**</span><span class="sxs-lookup"><span data-stu-id="bdbf2-105">**Oracle Connect String**</span></span>  
 <span data-ttu-id="bdbf2-106">輸入電腦與您使用之 Oracle 資料庫之間的 Oracle 連接字串。</span><span class="sxs-lookup"><span data-stu-id="bdbf2-106">Enter the Oracle connect string to the computer with the Oracle database you are using.</span></span> <span data-ttu-id="bdbf2-107">連接字串會以下列其中一種方式撰寫：</span><span class="sxs-lookup"><span data-stu-id="bdbf2-107">The connect string is written in one of the following ways:</span></span>  
  
 `host[:port][/service name]`  
  
 <span data-ttu-id="bdbf2-108">連接字串還可以指定 Oracle Net 連接描述項，例如， `(DESCRIPTION=(ADDRESS=(PROTOCOL=tcp) (HOST=erp.contoso.com) (PORT=1521)) (CONNECT_DATA=(SERVICE_NAME=orcl)))`</span><span class="sxs-lookup"><span data-stu-id="bdbf2-108">The connection string can also specify an Oracle Net connect descriptor, for example, `(DESCRIPTION=(ADDRESS=(PROTOCOL=tcp) (HOST=erp.contoso.com) (PORT=1521)) (CONNECT_DATA=(SERVICE_NAME=orcl)))`</span></span>  
  
 <span data-ttu-id="bdbf2-109">如果使用目錄伺服器或 tnsnames，則連接字串可以是連接的名稱。</span><span class="sxs-lookup"><span data-stu-id="bdbf2-109">If using a directory server or tnsnames, the connect string can be the name of the connection.</span></span>  
  
 <span data-ttu-id="bdbf2-110">**Oracle 記錄採礦驗證**</span><span class="sxs-lookup"><span data-stu-id="bdbf2-110">**Oracle Log Mining Authentication**</span></span>  
 <span data-ttu-id="bdbf2-111">若要輸入已被授權進行記錄採礦之 Oracle 資料庫使用者的認證，請選取下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="bdbf2-111">To enter the credentials for the Oracle database user that is authorized for log mining, select one of the following:</span></span>  
  
-   <span data-ttu-id="bdbf2-112">**Windows 驗證**：選取此選項可使用目前的 Windows 網域認證。</span><span class="sxs-lookup"><span data-stu-id="bdbf2-112">**Windows Authentication**: Select this to use the current Windows domain credentials.</span></span> <span data-ttu-id="bdbf2-113">只有當設定 Oracle 資料庫使用 Windows 驗證時，才可使用這個選項。</span><span class="sxs-lookup"><span data-stu-id="bdbf2-113">You can use this option only if the Oracle database is configured to work with Windows authentication.</span></span>  
  
-   <span data-ttu-id="bdbf2-114">**Oracle 驗證**：如果您選取這個選項，您必須在您所連接的 Oracle 資料庫中鍵入使用者的 [使用者名稱]  和 [密碼]  。</span><span class="sxs-lookup"><span data-stu-id="bdbf2-114">**Oracle Authentication**: If you select this option, you must type the **User Name** and **Password** for the user in the Oracle database you are connecting to.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bdbf2-115">使用者必須擁有 Oracle 資料庫中授與的以下權限，才能成為記錄採礦使用者。</span><span class="sxs-lookup"><span data-stu-id="bdbf2-115">A user must have the following privileges granted in the Oracle database to be a log-mining user.</span></span>  
> 
>  -   <span data-ttu-id="bdbf2-116">\<any-captured-table> 上的 SELECT</span><span class="sxs-lookup"><span data-stu-id="bdbf2-116">SELECT on \<any-captured-table></span></span>  
> -   <span data-ttu-id="bdbf2-117">SELECT ANY TRANSACTION</span><span class="sxs-lookup"><span data-stu-id="bdbf2-117">SELECT ANY TRANSACTION</span></span>  
> -   <span data-ttu-id="bdbf2-118">EXECUTE on DBMS LOGMNR</span><span class="sxs-lookup"><span data-stu-id="bdbf2-118">EXECUTE on DBMS LOGMNR</span></span>  
> -   <span data-ttu-id="bdbf2-119">SELECT on V$LOGMNR CONTENTS</span><span class="sxs-lookup"><span data-stu-id="bdbf2-119">SELECT on V$LOGMNR CONTENTS</span></span>  
> -   <span data-ttu-id="bdbf2-120">SELECT on V$ARCHIVED LOG</span><span class="sxs-lookup"><span data-stu-id="bdbf2-120">SELECT on V$ARCHIVED LOG</span></span>  
> -   <span data-ttu-id="bdbf2-121">SELECT on V$LOG</span><span class="sxs-lookup"><span data-stu-id="bdbf2-121">SELECT on V$LOG</span></span>  
> -   <span data-ttu-id="bdbf2-122">SELECT on V$LOGFILE</span><span class="sxs-lookup"><span data-stu-id="bdbf2-122">SELECT on V$LOGFILE</span></span>  
> -   <span data-ttu-id="bdbf2-123">SELECT on V$DATABASE</span><span class="sxs-lookup"><span data-stu-id="bdbf2-123">SELECT on V$DATABASE</span></span>  
> -   <span data-ttu-id="bdbf2-124">SELECT on V$THREAD</span><span class="sxs-lookup"><span data-stu-id="bdbf2-124">SELECT on V$THREAD</span></span>  
> -   <span data-ttu-id="bdbf2-125">SELECT on ALL INDEXES</span><span class="sxs-lookup"><span data-stu-id="bdbf2-125">SELECT on ALL INDEXES</span></span>  
> -   <span data-ttu-id="bdbf2-126">SELECT on ALL OBJECTS</span><span class="sxs-lookup"><span data-stu-id="bdbf2-126">SELECT on ALL OBJECTS</span></span>  
> -   <span data-ttu-id="bdbf2-127">SELECT on DBA OBJECTS</span><span class="sxs-lookup"><span data-stu-id="bdbf2-127">SELECT on DBA OBJECTS</span></span>  
> -   <span data-ttu-id="bdbf2-128">SELECT on ALL TABLES</span><span class="sxs-lookup"><span data-stu-id="bdbf2-128">SELECT on ALL TABLES</span></span>  
> 
>  <span data-ttu-id="bdbf2-129">如果有任何權限不能授與給 V$xxx，則將該權限授與給 V_S$xxx。</span><span class="sxs-lookup"><span data-stu-id="bdbf2-129">If any of these privileges cannot be granted to a V$xxx, then grant them to the V_S$xxx.</span></span>  
  
 <span data-ttu-id="bdbf2-130">**測試連接**</span><span class="sxs-lookup"><span data-stu-id="bdbf2-130">**Test Connection**</span></span>  
 <span data-ttu-id="bdbf2-131">按一下 [測試連接]  ，以判斷您是否已經與擁有 Oracle 資料庫的遠端電腦建立連接。</span><span class="sxs-lookup"><span data-stu-id="bdbf2-131">Click **Test Connection** to determine whether you established a connection with the remote computer that has the Oracle database.</span></span> <span data-ttu-id="bdbf2-132">隨即開啟對話方塊，通知您連接是否成功。</span><span class="sxs-lookup"><span data-stu-id="bdbf2-132">A dialog box opens to inform you whether the connection was successful.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="bdbf2-133">由於已知問題的緣故，如果未以系統管理員的身分執行 CDC 設計工具，則 Oracle 來源資料庫的連接可能會失敗。</span><span class="sxs-lookup"><span data-stu-id="bdbf2-133">Due to a known issue connection to the Oracle source database may fail if the CDC Designer is not run as an administrator.</span></span> <span data-ttu-id="bdbf2-134">如果連接失敗，請使用 **[以系統管理員身分執行]** 選項關閉 CDC 設計工具，然後重新啟動。</span><span class="sxs-lookup"><span data-stu-id="bdbf2-134">If connection fails, close and restart the CDC Designer using the **Run as administrator** option.</span></span>  
  
 <span data-ttu-id="bdbf2-135">當您在這個頁面上輸入資訊完畢後，請按 **[下一步]** [Select Oracle Tables and Columns](select-oracle-tables-and-columns.md)。</span><span class="sxs-lookup"><span data-stu-id="bdbf2-135">After you finish entering information on this page, click **Next** to [Select Oracle Tables and Columns](select-oracle-tables-and-columns.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bdbf2-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bdbf2-136">See Also</span></span>  
 <span data-ttu-id="bdbf2-137">[如何建立 SQL Server 變更資料庫執行個體](how-to-create-the-sql-server-change-database-instance.md) </span><span class="sxs-lookup"><span data-stu-id="bdbf2-137">[How to Create the SQL Server Change Database Instance](how-to-create-the-sql-server-change-database-instance.md) </span></span>  
 [<span data-ttu-id="bdbf2-138">編輯執行個體屬性</span><span class="sxs-lookup"><span data-stu-id="bdbf2-138">Edit Instance Properties</span></span>](edit-instance-properties.md)  
  
  
