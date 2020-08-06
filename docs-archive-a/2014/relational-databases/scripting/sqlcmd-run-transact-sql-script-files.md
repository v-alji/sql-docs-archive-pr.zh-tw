---
title: 使用 sqlcmd 執行 Transact-SQL 指令碼檔案
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- transact sql scripts
ms.assetid: 90067eb8-ca3e-44e8-bb1a-bf7d1a359423
author: rothja
ms.author: jroth
ms.openlocfilehash: cd34b089fc4e971cac9e5713cbe303192a7a48c1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592588"
---
# <a name="run-transact-sql-script-files-using-sqlcmd"></a><span data-ttu-id="e63e6-102">使用 sqlcmd 執行 Transact-SQL 指令碼檔案</span><span class="sxs-lookup"><span data-stu-id="e63e6-102">Run Transact-SQL Script Files Using sqlcmd</span></span>
  <span data-ttu-id="e63e6-103">您可以使用 `sqlcmd` 來執行 [!INCLUDE[tsql](../../includes/tsql-md.md)] 指令碼檔案。</span><span class="sxs-lookup"><span data-stu-id="e63e6-103">You can use `sqlcmd` to run a [!INCLUDE[tsql](../../includes/tsql-md.md)] script file.</span></span> <span data-ttu-id="e63e6-104">[!INCLUDE[tsql](../../includes/tsql-md.md)] 指令碼檔案是一個文字檔，可以包含 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式、`sqlcmd` 命令和指令碼變數的組合。</span><span class="sxs-lookup"><span data-stu-id="e63e6-104">A [!INCLUDE[tsql](../../includes/tsql-md.md)] script file is a text file that can contain a combination of [!INCLUDE[tsql](../../includes/tsql-md.md)] statements, `sqlcmd` commands, and scripting variables.</span></span>  
  
 <span data-ttu-id="e63e6-105">若要使用「記事本」建立簡單的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 指令碼檔案，請遵循下列步驟：</span><span class="sxs-lookup"><span data-stu-id="e63e6-105">To create a simple [!INCLUDE[tsql](../../includes/tsql-md.md)] script file by using Notepad, follow these steps:</span></span>  
  
1.  <span data-ttu-id="e63e6-106">按一下 [開始]\*\*\*\*，依序指向 [所有程式]\*\*\*\* 和 [附屬應用程式]\*\*\*\*，然後按一下 [記事本]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e63e6-106">Click **Start**, point to **All Programs**, point to **Accessories**, and then click **Notepad**.</span></span>  
  
2.  <span data-ttu-id="e63e6-107">將下列 [!INCLUDE[tsql](../../includes/tsql-md.md)] 程式碼複製並貼到 [記事本] 中：</span><span class="sxs-lookup"><span data-stu-id="e63e6-107">Copy and paste the following [!INCLUDE[tsql](../../includes/tsql-md.md)] code into Notepad:</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT p.FirstName + ' ' + p.LastName AS 'Employee Name',  
    a.AddressLine1, a.AddressLine2 , a.City, a.PostalCode   
    FROM Person.Person AS p   
       INNER JOIN HumanResources.Employee AS e   
            ON p.BusinessEntityID = e.BusinessEntityID  
        INNER JOIN Person.BusinessEntityAddress bea   
            ON bea.BusinessEntityID = e.BusinessEntityID  
        INNER JOIN Person.Address AS a   
            ON a.AddressID = bea.AddressID;  
    GO  
    ```  
  
3.  <span data-ttu-id="e63e6-108">將檔案儲存成 C 磁碟機中的 **myScript.sql** 。</span><span class="sxs-lookup"><span data-stu-id="e63e6-108">Save the file as **myScript.sql** in the C drive.</span></span>  
  
### <a name="to-run-the-script-file"></a><span data-ttu-id="e63e6-109">執行指令碼檔案</span><span class="sxs-lookup"><span data-stu-id="e63e6-109">To run the script file</span></span>  
  
1.  <span data-ttu-id="e63e6-110">開啟命令提示字元視窗。</span><span class="sxs-lookup"><span data-stu-id="e63e6-110">Open a command prompt window.</span></span>  
  
2.  <span data-ttu-id="e63e6-111">在 [命令提示字元] 視窗中輸入：`sqlcmd -S myServer\instanceName -i C:\myScript.sql`</span><span class="sxs-lookup"><span data-stu-id="e63e6-111">In the Command Prompt window, type: `sqlcmd -S myServer\instanceName -i C:\myScript.sql`</span></span>  
  
3.  <span data-ttu-id="e63e6-112">按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="e63e6-112">Press ENTER.</span></span>  
  
 <span data-ttu-id="e63e6-113">此時會在命令提示字元視窗中，顯示一份 [!INCLUDE[ssSampleDBCoShort](../../includes/sssampledbcoshort-md.md)] 員工姓名和地址的清單。</span><span class="sxs-lookup"><span data-stu-id="e63e6-113">A list of [!INCLUDE[ssSampleDBCoShort](../../includes/sssampledbcoshort-md.md)] employee names and addresses is written to the command prompt window.</span></span>  
  
### <a name="to-save-this-output-to-a-text-file"></a><span data-ttu-id="e63e6-114">將這份輸出儲存在文字檔中</span><span class="sxs-lookup"><span data-stu-id="e63e6-114">To save this output to a text file</span></span>  
  
1.  <span data-ttu-id="e63e6-115">開啟命令提示字元視窗。</span><span class="sxs-lookup"><span data-stu-id="e63e6-115">Open a command prompt window.</span></span>  
  
2.  <span data-ttu-id="e63e6-116">在 [命令提示字元] 視窗中輸入：`sqlcmd -S myServer\instanceName -i C:\myScript.sql -o C:\EmpAdds.txt`</span><span class="sxs-lookup"><span data-stu-id="e63e6-116">In the Command Prompt window, type: `sqlcmd -S myServer\instanceName -i C:\myScript.sql -o C:\EmpAdds.txt`</span></span>  
  
3.  <span data-ttu-id="e63e6-117">按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="e63e6-117">Press ENTER.</span></span>  
  
 <span data-ttu-id="e63e6-118">此時在命令提示字元視窗中不會傳回任何輸出。</span><span class="sxs-lookup"><span data-stu-id="e63e6-118">No output is returned in the Command Prompt window.</span></span> <span data-ttu-id="e63e6-119">而是會將輸出送往 EmpAdds.txt 檔。</span><span class="sxs-lookup"><span data-stu-id="e63e6-119">Instead, the output is sent to the EmpAdds.txt file.</span></span> <span data-ttu-id="e63e6-120">您可以開啟 EmpAdds.txt 檔來確認這份輸出。</span><span class="sxs-lookup"><span data-stu-id="e63e6-120">You can verify this output by opening the EmpAdds.txt file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e63e6-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e63e6-121">See Also</span></span>  
 <span data-ttu-id="e63e6-122">[啟動 sqlcmd 公用程式](sqlcmd-start-the-utility.md) </span><span class="sxs-lookup"><span data-stu-id="e63e6-122">[Start the sqlcmd Utility](sqlcmd-start-the-utility.md) </span></span>  
 [<span data-ttu-id="e63e6-123">sqlcmd 公用程式</span><span class="sxs-lookup"><span data-stu-id="e63e6-123">sqlcmd Utility</span></span>](../../tools/sqlcmd-utility.md)  
  
  
