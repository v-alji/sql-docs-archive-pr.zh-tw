---
title: " (查詢結果的選項-SQL Server-多伺服器) |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.swb.sqleditors.multiserverresultssettings
- VS.ToolsOptionsPages.QueryResults.SqlServer.SQLMultiServerResults
ms.assetid: d6768bd8-9cb5-4606-a726-a33a1df9e1bb
author: rothja
ms.author: jroth
ms.openlocfilehash: 8273ad5edc65dd7351533209e9fa670c49f75f7a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705406"
---
# <a name="options-query-results-sql-server-multi-server"></a><span data-ttu-id="d18c2-102">選項 (查詢結果-SQL Server-多伺服器)</span><span class="sxs-lookup"><span data-stu-id="d18c2-102">Options (Query Results-SQL Server-Multi-Server)</span></span>
  <span data-ttu-id="d18c2-103">當您同時查詢多部伺服器時，使用這個頁面可指定用來顯示結果集的選項。</span><span class="sxs-lookup"><span data-stu-id="d18c2-103">When you are querying multiple servers at the same time, use this page to specify the options for displaying result sets.</span></span> <span data-ttu-id="d18c2-104">合併結果會將所有伺服器的結果集結合到單一結果集內。</span><span class="sxs-lookup"><span data-stu-id="d18c2-104">Merge results combines the result sets from all servers into a single result set.</span></span> <span data-ttu-id="d18c2-105">合併結果時，要回應的第一部伺服器會設定結果集的結構描述。</span><span class="sxs-lookup"><span data-stu-id="d18c2-105">When merging results, the first server to respond sets the schema for the result set.</span></span> <span data-ttu-id="d18c2-106">若要合併結果集，此查詢必須傳回每一部伺服器中具有相同資料行名稱的相同資料行數。</span><span class="sxs-lookup"><span data-stu-id="d18c2-106">To merge the result sets, the query must return the same number of columns with the same column names from each server.</span></span> <span data-ttu-id="d18c2-107">當合併結果時，會針對不符合結構描述 (資料行計數和資料行名稱) 的每一部伺服器顯示一則訊息 (該結構描述是由第一部傳回結果的伺服器所傳回)。</span><span class="sxs-lookup"><span data-stu-id="d18c2-107">When merging results, a message is displayed for each server that does not match the schema (column count and column names) that is returned by the first server to return results.</span></span>  
  
 <span data-ttu-id="d18c2-108">當您不要合併結果時，第一部伺服器中的結果集將會顯示在它自己的方格中，而且有它自己的結構描述。</span><span class="sxs-lookup"><span data-stu-id="d18c2-108">When you do not merge results, the result set from each server will be displayed in its own grid with its own schema.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="d18c2-109">UI 元素清單</span><span class="sxs-lookup"><span data-stu-id="d18c2-109">UI element list</span></span>  
 <span data-ttu-id="d18c2-110">**合併結果**</span><span class="sxs-lookup"><span data-stu-id="d18c2-110">**Merge results**</span></span>  
 <span data-ttu-id="d18c2-111">選取此核取方塊可將幾部伺服器中的結果集結合到相同方格內。</span><span class="sxs-lookup"><span data-stu-id="d18c2-111">Select this check box to combine the result sets from several servers into the same grid.</span></span>  
  
 <span data-ttu-id="d18c2-112">**將伺服器名稱加入結果**</span><span class="sxs-lookup"><span data-stu-id="d18c2-112">**Add server name to the results**</span></span>  
 <span data-ttu-id="d18c2-113">選取此核取方塊可包含另一個資料行，此資料行會提供產生每一個資料列的伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="d18c2-113">Select this check box to include an additional column that provides the name of the server that produced each row.</span></span>  
  
 <span data-ttu-id="d18c2-114">**將登入名稱加入結果**</span><span class="sxs-lookup"><span data-stu-id="d18c2-114">**Add login name to the results**</span></span>  
 <span data-ttu-id="d18c2-115">選取此核取方塊可包含另一個資料行，此資料行所提供的登入是用來連接提供每一個資料列的伺服器。</span><span class="sxs-lookup"><span data-stu-id="d18c2-115">Select this check box to include an additional column that provides the login that was used to connect to the server that provided each row.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d18c2-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d18c2-116">See Also</span></span>  
 <span data-ttu-id="d18c2-117">[建立中央管理伺服器和伺服器群組 &#40;SQL Server Management Studio&#41;](../ssms/register-servers/create-a-central-management-server-and-server-group.md) </span><span class="sxs-lookup"><span data-stu-id="d18c2-117">[Create a Central Management Server and Server Group &#40;SQL Server Management Studio&#41;](../ssms/register-servers/create-a-central-management-server-and-server-group.md) </span></span>  
 [<span data-ttu-id="d18c2-118">同時針對多部伺服器執行陳述式 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="d18c2-118">Execute Statements Against Multiple Servers Simultaneously &#40;SQL Server Management Studio&#41;</span></span>](../ssms/register-servers/execute-statements-against-multiple-servers-simultaneously.md)  
  
  
