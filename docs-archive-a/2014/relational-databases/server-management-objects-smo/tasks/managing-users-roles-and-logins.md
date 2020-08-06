---
title: 管理使用者、角色和登入 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- logins [SMO]
- roles [SMO]
- users [SMO]
ms.assetid: 74e411fa-74ed-49ec-ab58-68c250f2280e
author: stevestein
ms.author: sstein
ms.openlocfilehash: bb53e7b4a5748e46c7cb147e1cda50652d8b8805
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598251"
---
# <a name="managing-users-roles-and-logins"></a><span data-ttu-id="29ee3-102">管理使用者、角色和登入</span><span class="sxs-lookup"><span data-stu-id="29ee3-102">Managing Users, Roles, and Logins</span></span>
  <span data-ttu-id="29ee3-103">在 SMO 中，登入是由 <xref:Microsoft.SqlServer.Management.Smo.Login> 物件表示。</span><span class="sxs-lookup"><span data-stu-id="29ee3-103">In SMO, logins are represented by the <xref:Microsoft.SqlServer.Management.Smo.Login> object.</span></span> <span data-ttu-id="29ee3-104">當登入存在於 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]時，可以加入至伺服器角色。</span><span class="sxs-lookup"><span data-stu-id="29ee3-104">When the logon exists in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], it can be added to a server role.</span></span> <span data-ttu-id="29ee3-105">伺服器角色是由 <xref:Microsoft.SqlServer.Management.Smo.ServerRole> 物件表示，</span><span class="sxs-lookup"><span data-stu-id="29ee3-105">The server role is represented by the <xref:Microsoft.SqlServer.Management.Smo.ServerRole> object.</span></span> <span data-ttu-id="29ee3-106">資料庫角色是由 <xref:Microsoft.SqlServer.Management.Smo.DatabaseRole> 物件表示，應用程式角色則是由 <xref:Microsoft.SqlServer.Management.Smo.ApplicationRole> 物件表示。</span><span class="sxs-lookup"><span data-stu-id="29ee3-106">The database role is represented by the <xref:Microsoft.SqlServer.Management.Smo.DatabaseRole> object and the application role is represented by the <xref:Microsoft.SqlServer.Management.Smo.ApplicationRole> object.</span></span>  
  
 <span data-ttu-id="29ee3-107">與伺服器層級相關聯的權限會列為 <xref:Microsoft.SqlServer.Management.Smo.ServerPermission> 物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="29ee3-107">Privileges associated with the server level are listed as properties of the <xref:Microsoft.SqlServer.Management.Smo.ServerPermission> object.</span></span> <span data-ttu-id="29ee3-108">伺服器層級權限可授與個別的登入帳戶，也可從這些帳戶拒絕或撤銷。</span><span class="sxs-lookup"><span data-stu-id="29ee3-108">The server level privileges can be granted to, denied to, or revoked from individual logon accounts.</span></span>  
  
 <span data-ttu-id="29ee3-109">每個 <xref:Microsoft.SqlServer.Management.Smo.Database> 物件都具有 <xref:Microsoft.SqlServer.Management.Smo.UserCollection> 物件，可指定資料庫中的所有使用者。</span><span class="sxs-lookup"><span data-stu-id="29ee3-109">Every <xref:Microsoft.SqlServer.Management.Smo.Database> object has a <xref:Microsoft.SqlServer.Management.Smo.UserCollection> object that specifies all users in the database.</span></span> <span data-ttu-id="29ee3-110">每個使用者都與一個登入相關聯。</span><span class="sxs-lookup"><span data-stu-id="29ee3-110">Each user is associated with a logon.</span></span> <span data-ttu-id="29ee3-111">單一的登入可以與一個以上資料庫中的使用者產生關聯。</span><span class="sxs-lookup"><span data-stu-id="29ee3-111">One logon can be associated with users in more than one database.</span></span> <span data-ttu-id="29ee3-112"><xref:Microsoft.SqlServer.Management.Smo.Login> 物件的 <xref:Microsoft.SqlServer.Management.Smo.Login.EnumDatabaseMappings%2A> 方法可用於列出每個資料庫中與該登入相關聯的所有使用者；</span><span class="sxs-lookup"><span data-stu-id="29ee3-112">The <xref:Microsoft.SqlServer.Management.Smo.Login> object's <xref:Microsoft.SqlServer.Management.Smo.Login.EnumDatabaseMappings%2A> method can be used to list all users in every database that is associated with the logon.</span></span> <span data-ttu-id="29ee3-113">或者，<xref:Microsoft.SqlServer.Management.Smo.User> 物件的 <xref:Microsoft.SqlServer.Management.Smo.Login> 屬性也可指定與該使用者相關的登入。</span><span class="sxs-lookup"><span data-stu-id="29ee3-113">Alternatively, the <xref:Microsoft.SqlServer.Management.Smo.User> object's <xref:Microsoft.SqlServer.Management.Smo.Login> property specifies the logon that is associated with the user.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="29ee3-114">資料庫也具有指定資料庫層級權限集的角色，這些權限可以讓使用者執行特定的工作。</span><span class="sxs-lookup"><span data-stu-id="29ee3-114">databases also have roles that specify a set of database level privileges that let a user perform specific tasks.</span></span> <span data-ttu-id="29ee3-115">與伺服器角色不同的是，資料庫角色不是固定的。</span><span class="sxs-lookup"><span data-stu-id="29ee3-115">Unlike server roles, database roles are not fixed.</span></span> <span data-ttu-id="29ee3-116">這些角色可以建立、修改和移除。</span><span class="sxs-lookup"><span data-stu-id="29ee3-116">They can be created, modified, and removed.</span></span> <span data-ttu-id="29ee3-117">若要進行大量管理，可以為資料庫角色指派權限和使用者。</span><span class="sxs-lookup"><span data-stu-id="29ee3-117">Privileges and users can be assigned to a database role for bulk administration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="29ee3-118">範例</span><span class="sxs-lookup"><span data-stu-id="29ee3-118">Example</span></span>  
 <span data-ttu-id="29ee3-119">在下列的程式碼範例中，您必須選取用於建立應用程式的程式設計環境、程式設計範本和程式設計語言。</span><span class="sxs-lookup"><span data-stu-id="29ee3-119">For the following code example, you will have to select the programming environment, programming template and the programming language to create your application.</span></span> <span data-ttu-id="29ee3-120">如需詳細資訊，請參閱[在 Visual Studio .net 中建立 VISUAL BASIC SMO 專案](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md)和[在 Visual Studio .Net 中建立 VISUAL C&#35; SMO 專案](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)。</span><span class="sxs-lookup"><span data-stu-id="29ee3-120">For more information, see [Create a Visual Basic SMO Project in Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) and [Create a Visual C&#35; SMO Project in Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).</span></span>  
  
## <a name="enumerating-logins-and-associated-users-in-visual-basic"></a><span data-ttu-id="29ee3-121">在 Visual Basic 中列舉登入和關聯的使用者</span><span class="sxs-lookup"><span data-stu-id="29ee3-121">Enumerating Logins and Associated Users in Visual Basic</span></span>  
 <span data-ttu-id="29ee3-122">資料庫中的每個使用者都與一個登入相關聯。</span><span class="sxs-lookup"><span data-stu-id="29ee3-122">Every user in a database is associated with a logon.</span></span> <span data-ttu-id="29ee3-123">此登入可以與一個以上資料庫中的使用者產生關聯。</span><span class="sxs-lookup"><span data-stu-id="29ee3-123">The logon can be associated with users in more than one database.</span></span> <span data-ttu-id="29ee3-124">此程式碼範例示範如何呼叫 <xref:Microsoft.SqlServer.Management.Smo.Login.EnumDatabaseMappings%2A> 物件的 <xref:Microsoft.SqlServer.Management.Smo.Login> 方法來列出與登入相關聯的所有資料庫使用者。</span><span class="sxs-lookup"><span data-stu-id="29ee3-124">The code example shows how to call the <xref:Microsoft.SqlServer.Management.Smo.Login.EnumDatabaseMappings%2A> method of the <xref:Microsoft.SqlServer.Management.Smo.Login> object to list all the database users who are associated with the logon.</span></span> <span data-ttu-id="29ee3-125">此範例會在 [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] 資料庫中建立登入和使用者，以確保有可以列舉的對應資訊。</span><span class="sxs-lookup"><span data-stu-id="29ee3-125">The example creates a logon and user in the [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] database to make sure there is mapping information to enumerate.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBLogins1](SMO How to#SMO_VBLogins1)]  -->  
  
## <a name="enumerating-logins-and-associated-users-in-visual-c"></a><span data-ttu-id="29ee3-126">在 Visual C# 中列舉登入和關聯的使用者</span><span class="sxs-lookup"><span data-stu-id="29ee3-126">Enumerating Logins and Associated Users in Visual C#</span></span>  
 <span data-ttu-id="29ee3-127">資料庫中的每個使用者都與一個登入相關聯。</span><span class="sxs-lookup"><span data-stu-id="29ee3-127">Every user in a database is associated with a logon.</span></span> <span data-ttu-id="29ee3-128">此登入可以與一個以上資料庫中的使用者產生關聯。</span><span class="sxs-lookup"><span data-stu-id="29ee3-128">The logon can be associated with users in more than one database.</span></span> <span data-ttu-id="29ee3-129">此程式碼範例示範如何呼叫 <xref:Microsoft.SqlServer.Management.Smo.Login.EnumDatabaseMappings%2A> 物件的 <xref:Microsoft.SqlServer.Management.Smo.Login> 方法來列出與登入相關聯的所有資料庫使用者。</span><span class="sxs-lookup"><span data-stu-id="29ee3-129">The code example shows how to call the <xref:Microsoft.SqlServer.Management.Smo.Login.EnumDatabaseMappings%2A> method of the <xref:Microsoft.SqlServer.Management.Smo.Login> object to list all the database users who are associated with the logon.</span></span> <span data-ttu-id="29ee3-130">此範例會在 [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] 資料庫中建立登入和使用者，以確保有可以列舉的對應資訊。</span><span class="sxs-lookup"><span data-stu-id="29ee3-130">The example creates a logon and user in the [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] database to make sure there is mapping information to enumerate.</span></span>  
  
```csharp
{   
Server srv = new Server();   
//Iterate through each database and display.   
  
foreach ( Database db in srv.Databases) {   
   Console.WriteLine("========");   
   Console.WriteLine("Login Mappings for the database: " + db.Name);   
   Console.WriteLine(" ");   
   //Run the EnumLoginMappings method and return details of database user-login mappings to a DataTable object variable.   
   DataTable d;  
   d = db.EnumLoginMappings();   
   //Display the mapping information.   
   foreach (DataRow r in d.Rows) {   
      foreach (DataColumn c in r.Table.Columns) {   
         Console.WriteLine(c.ColumnName + " = " + r[c]);   
      }   
      Console.WriteLine(" ");   
   }   
}   
}  
```  
  
## <a name="enumerating-logins-and-associated-users-in-powershell"></a><span data-ttu-id="29ee3-131">在 PowerShell 中列舉登入和相關聯的使用者</span><span class="sxs-lookup"><span data-stu-id="29ee3-131">Enumerating Logins and Associated Users in PowerShell</span></span>  
 <span data-ttu-id="29ee3-132">資料庫中的每個使用者都與一個登入相關聯。</span><span class="sxs-lookup"><span data-stu-id="29ee3-132">Every user in a database is associated with a logon.</span></span> <span data-ttu-id="29ee3-133">此登入可以與一個以上資料庫中的使用者產生關聯。</span><span class="sxs-lookup"><span data-stu-id="29ee3-133">The logon can be associated with users in more than one database.</span></span> <span data-ttu-id="29ee3-134">此程式碼範例示範如何呼叫 <xref:Microsoft.SqlServer.Management.Smo.Login.EnumDatabaseMappings%2A> 物件的 <xref:Microsoft.SqlServer.Management.Smo.Login> 方法來列出與登入相關聯的所有資料庫使用者。</span><span class="sxs-lookup"><span data-stu-id="29ee3-134">The code example shows how to call the <xref:Microsoft.SqlServer.Management.Smo.Login.EnumDatabaseMappings%2A> method of the <xref:Microsoft.SqlServer.Management.Smo.Login> object to list all the database users who are associated with the logon.</span></span> <span data-ttu-id="29ee3-135">此範例會在 [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] 資料庫中建立登入和使用者，以確保有可以列舉的對應資訊。</span><span class="sxs-lookup"><span data-stu-id="29ee3-135">The example creates a logon and user in the [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] database to make sure there is mapping information to enumerate.</span></span>  
  
```powershell
# Set the path context to the local, default instance of SQL Server.  
CD \sql\localhost\Default\Databases  
  
#Iterate through all databases  
 foreach ($db in Get-ChildItem)  
 {  
 "====="  
 "Login Mappings for the database: "+ $db.Name  
  
 #get the datatable containing the mapping from the smo database object  
 $dt = $db.EnumLoginMappings()  
  
 #display the results  
 foreach($row in $dt.Rows)  
     {  
        foreach($col in $row.Table.Columns)  
      {  
        $col.ColumnName + "=" + $row[$col]  
       }
     }  
 }  
```  
  
## <a name="managing-roles-and-users"></a><span data-ttu-id="29ee3-136">管理角色和使用者</span><span class="sxs-lookup"><span data-stu-id="29ee3-136">Managing Roles and Users</span></span>  
 <span data-ttu-id="29ee3-137">此範例示範如何管理角色和使用者。</span><span class="sxs-lookup"><span data-stu-id="29ee3-137">This sample demonstrates how to how to manage roles and users.</span></span> <span data-ttu-id="29ee3-138">第一個範例使用 C#，第二個範例使用 Visual Basic。</span><span class="sxs-lookup"><span data-stu-id="29ee3-138">The first sample uses C#, the second Visual Basic.</span></span> <span data-ttu-id="29ee3-139">這兩個範例需要參考下列組件：</span><span class="sxs-lookup"><span data-stu-id="29ee3-139">These samples need to reference the following assemblies:</span></span>  
  
-   <span data-ttu-id="29ee3-140">Microsoft.SqlServer.Smo.dll</span><span class="sxs-lookup"><span data-stu-id="29ee3-140">Microsoft.SqlServer.Smo.dll</span></span>  
  
-   <span data-ttu-id="29ee3-141">Microsoft.SqlServer.Management.Sdk.Sfc.dll</span><span class="sxs-lookup"><span data-stu-id="29ee3-141">Microsoft.SqlServer.Management.Sdk.Sfc.dll</span></span>  
  
-   <span data-ttu-id="29ee3-142">Microsoft.SqlServer.ConnectionInfo.dll</span><span class="sxs-lookup"><span data-stu-id="29ee3-142">Microsoft.SqlServer.ConnectionInfo.dll</span></span>  
  
-   <span data-ttu-id="29ee3-143">Microsoft.SqlServer.SqlEnum.dll</span><span class="sxs-lookup"><span data-stu-id="29ee3-143">Microsoft.SqlServer.SqlEnum.dll</span></span>  
  
```csharp
using Microsoft.SqlServer.Management.Smo;  
using System;  
  
public class A {  
   public static void Main() {  
      Server svr = new Server();  
      Database db = new Database(svr, "TESTDB");  
      db.Create();  
  
      // Creating Logins  
      Login login = new Login(svr, "Login1");  
      login.LoginType = LoginType.SqlLogin;  
      login.Create("password@1");  
  
      Login login2 = new Login(svr, "Login2");  
      login2.LoginType = LoginType.SqlLogin;  
      login2.Create("password@1");  
  
      // Creating Users in the database for the logins created  
      User user1 = new User(db, "User1");  
      user1.Login = "Login1";  
      user1.Create();  
  
      User user2 = new User(db, "User2");  
      user2.Login = "Login2";  
      user2.Create();  
  
      // Creating database permission Sets  
      DatabasePermissionSet dbPermSet = new DatabasePermissionSet(DatabasePermission.AlterAnySchema);  
      dbPermSet.Add(DatabasePermission.AlterAnyUser);  
  
      DatabasePermissionSet dbPermSet2 = new DatabasePermissionSet(DatabasePermission.CreateType);  
      dbPermSet2.Add(DatabasePermission.CreateSchema);  
      dbPermSet2.Add(DatabasePermission.CreateTable);  
  
      // Creating Database roles  
      DatabaseRole role1 = new DatabaseRole(db, "Role1");  
      role1.Create();  
  
      DatabaseRole role2 = new DatabaseRole(db, "Role2");  
      role2.Create();  
  
      // Granting Database Permission Sets to Roles  
      db.Grant(dbPermSet, role1.Name);  
      db.Grant(dbPermSet2, role2.Name);  
  
      // Adding members (Users / Roles) to Role  
      role1.AddMember("User1");  
  
      role2.AddMember("User2");  
  
      // Role1 becomes a member of Role2  
      role2.AddMember("Role1");  
  
      // Enumerating through explicit permissions granted to Role1  
      // enumerates all database permissions for the Grantee  
      DatabasePermissionInfo[] dbPermsRole1 = db.EnumDatabasePermissions("Role1");     
      foreach (DatabasePermissionInfo dbp in dbPermsRole1) {  
         Console.WriteLine(dbp.Grantee + " has " + dbp.PermissionType.ToString() + " permission.");  
      }  
      Console.WriteLine(" ");  
   }  
}  
```  
  
 <span data-ttu-id="29ee3-144">這是 Visual Basic 版本：</span><span class="sxs-lookup"><span data-stu-id="29ee3-144">This is the Visual Basic version:</span></span>  
  
```vb
Imports Microsoft.SqlServer.Management.Smo  
  
Public Class A  
   Public Shared Sub Main()  
      Dim svr As New Server()  
      Dim db As New Database(svr, "TESTDB")  
      db.Create()  
  
      ' Creating Logins  
      Dim login As New Login(svr, "Login1")  
      login.LoginType = LoginType.SqlLogin  
      login.Create("password@1")  
  
      Dim login2 As New Login(svr, "Login2")  
      login2.LoginType = LoginType.SqlLogin  
      login2.Create("password@1")  
  
      ' Creating Users in the database for the logins created  
      Dim user1 As New User(db, "User1")  
      user1.Login = "Login1"  
      user1.Create()  
  
      Dim user2 As New User(db, "User2")  
      user2.Login = "Login2"  
      user2.Create()  
  
      ' Creating database permission Sets  
      Dim dbPermSet As New DatabasePermissionSet(DatabasePermission.AlterAnySchema)  
      dbPermSet.Add(DatabasePermission.AlterAnyUser)  
  
      Dim dbPermSet2 As New DatabasePermissionSet(DatabasePermission.CreateType)  
      dbPermSet2.Add(DatabasePermission.CreateSchema)  
      dbPermSet2.Add(DatabasePermission.CreateTable)  
  
      ' Creating Database roles  
      Dim role1 As New DatabaseRole(db, "Role1")  
      role1.Create()  
  
      Dim role2 As New DatabaseRole(db, "Role2")  
      role2.Create()  
  
      ' Granting Database Permission Sets to Roles  
      db.Grant(dbPermSet, role1.Name)  
      db.Grant(dbPermSet2, role2.Name)  
  
      ' Adding members (Users / Roles) to Role  
      role1.AddMember("User1")  
  
      role2.AddMember("User2")  
  
      ' Role1 becomes a member of Role2  
      role2.AddMember("Role1")  
  
      ' Enumerating through explicit permissions granted to Role1  
      ' enumerates all database permissions for the Grantee  
      Dim dbPermsRole1 As DatabasePermissionInfo() = db.EnumDatabasePermissions("Role1")  
      For Each dbp As DatabasePermissionInfo In dbPermsRole1  
         Console.WriteLine(dbp.Grantee + " has " & dbp.PermissionType.ToString() & " permission.")  
      Next  
      Console.WriteLine(" ")  
   End Sub  
End Class  
```  
