---
title: CLR 整合自訂屬性的總覽 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
helpviewer_keywords:
- custom attributes [CLR integration]
- attributes [CLR integration]
- common language runtime [SQL Server], attributes
- database objects [CLR integration], custom attributes
- building database objects [CLR integration], custom attributes
ms.assetid: ecf5c097-0972-48e2-a9c0-b695b7dd2820
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: aa0bf94ee27fd89a6aa690e0ff2f8e3295648946
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585575"
---
# <a name="overview-of-clr-integration-custom-attributes"></a><span data-ttu-id="b2b81-102">CLR 整合自訂屬性的概觀</span><span class="sxs-lookup"><span data-stu-id="b2b81-102">Overview of CLR Integration Custom Attributes</span></span>
  <span data-ttu-id="b2b81-103">[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 的 Common Language Runtime (CLR) 允許使用描述性的關鍵字 (稱為屬性)。</span><span class="sxs-lookup"><span data-stu-id="b2b81-103">The common language runtime (CLR) of the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] allows the use of descriptive keywords, called attributes.</span></span> <span data-ttu-id="b2b81-104">這些屬性會針對許多元素 (如方法和類別) 提供其他資訊。</span><span class="sxs-lookup"><span data-stu-id="b2b81-104">These attributes provide additional information for many elements, such as methods and classes.</span></span> <span data-ttu-id="b2b81-105">屬性會隨著物件的中繼資料儲存在組件中，而且可用來將程式碼描述給其他開發工具知道，或是影響 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 內的執行階段行為。</span><span class="sxs-lookup"><span data-stu-id="b2b81-105">The attributes are saved in the assembly with the metadata of the object, and can be used to describe your code to other development tools or to affect runtime behavior inside [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="b2b81-106">當您向 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 註冊 CLR 常式時，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會衍生一組有關此常式的屬性。</span><span class="sxs-lookup"><span data-stu-id="b2b81-106">When you register a CLR routine with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] derives a set of properties about the routine.</span></span> <span data-ttu-id="b2b81-107">這些常式屬性會決定該常式的功能，包括是否可以為此常式建立索引。</span><span class="sxs-lookup"><span data-stu-id="b2b81-107">These routine properties determine the capabilities of the routine, including whether the routine can be indexed.</span></span> <span data-ttu-id="b2b81-108">例如，將 `DataAccess` 屬性設定為 `DataAccessKind.Read` 可讓您從 CLR 函數內的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用者資料表存取資料。</span><span class="sxs-lookup"><span data-stu-id="b2b81-108">For example, setting the `DataAccess` property to `DataAccessKind.Read` lets you access data from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] user tables inside a CLR function.</span></span> <span data-ttu-id="b2b81-109">下列範例顯示一個簡單的案例，其中 `DataAccess` 屬性設定為有助於從使用者資料表**table1**進行資料存取。</span><span class="sxs-lookup"><span data-stu-id="b2b81-109">The following example shows a simple case in which the `DataAccess` property is set to facilitate data access from a user table **table1**.</span></span>  
  
```csharp  
using System;  
using System.Data;  
using System.Data.Sql;  
using System.Data.SqlTypes;  
using Microsoft.SqlServer.Server;  
using System.Data.SqlClient;  
  
public partial class UserDefinedFunctions  
{  
    [SqlFunction(DataAccess = DataAccessKind.Read)]  
    public static string func1()  
    {  
        // Open a connection and create a command  
        SqlConnection conn = new SqlConnection("context connection = true");  
        conn.Open();  
        SqlCommand cmd = conn.CreateCommand();  
        cmd.CommandText = "SELECT str_val FROM table1 WHERE int_val = 10";  
        // where table1 is a user table  
        // Execute this command   
        SqlDataReader rd = cmd.ExecuteReader();  
        // Set string ret_val to str_val returned from the query  
        string ret_val = rd.GetValue(0).ToString();  
        rd.Close();  
        return ret_val;  
    }  
}  
```  
  
```vb  
Imports System  
Imports System.Data  
Imports System.Data.Sql  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
Imports System.Data.SqlClient  
  
Public partial Class UserDefinedFunctions  
    <SqlFunction(DataAccess = DataAccessKind.Read)> _   
    Public Shared Function func1() As String  
        ' Open a connection and create a command  
        Dim conn As SqlConnection = New SqlConnection("context connection = true")   
        conn.Open()  
        Dim cmd As SqlCommand =  conn.CreateCommand()   
        cmd.CommandText = "SELECT str_val FROM table1 WHERE int_val = 10"  
        ' where table1 is a user table  
        ' Execute this command   
        Dim rd As SqlDataReader =  cmd.ExecuteReader()   
        ' Set string ret_val to str_val returned from the query  
        Dim ret_val As String =  rd.GetValue(0).ToString()   
        rd.Close()  
        Return ret_val  
    End Function  
End Class  
```  
  
 <span data-ttu-id="b2b81-110">如果是 [!INCLUDE[tsql](../../includes/tsql-md.md)] 常式，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會直接從常式定義衍生常式屬性。</span><span class="sxs-lookup"><span data-stu-id="b2b81-110">For [!INCLUDE[tsql](../../includes/tsql-md.md)] routines, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] derives routine properties directly from the routine definition.</span></span> <span data-ttu-id="b2b81-111">如果是 CLR 常式，伺服器不會分析常式的主體來衍生這些屬性。</span><span class="sxs-lookup"><span data-stu-id="b2b81-111">For CLR routines, the server does not analyze the body of the routine to derive these properties.</span></span> <span data-ttu-id="b2b81-112">您可以改為將自訂屬性用於使用 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 語言實作的類別和類別成員。</span><span class="sxs-lookup"><span data-stu-id="b2b81-112">Instead, you can use custom attributes for classes and class members implemented in a [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] language.</span></span>  
  
 <span data-ttu-id="b2b81-113">CLR 常式、使用者定義型別和彙總所需的自訂屬性會定義在 `Microsoft.SqlServer.Server` 命名空間內。</span><span class="sxs-lookup"><span data-stu-id="b2b81-113">The custom attributes needed for CLR routines, user-defined types, and aggregates are defined in the `Microsoft.SqlServer.Server` namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2b81-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b2b81-114">See Also</span></span>  
 [<span data-ttu-id="b2b81-115">CLR 常式的自訂屬性</span><span class="sxs-lookup"><span data-stu-id="b2b81-115">Custom Attributes for CLR Routines</span></span>](../../relational-databases/clr-integration/database-objects/clr-integration-custom-attributes-for-clr-routines.md)  
  
  
