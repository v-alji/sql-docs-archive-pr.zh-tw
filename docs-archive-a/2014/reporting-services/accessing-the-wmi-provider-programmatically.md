---
title: 以程式設計方式存取 WMI 提供者 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
ms.assetid: 67bd266b-1484-4863-8152-060a993420a9
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 6546d046fcd176eb5cc5fd462ea9a8a31c25b803
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597668"
---
# <a name="accessing-the-wmi-provider-programmatically"></a><span data-ttu-id="be394-102">以程式設計方式存取 WMI 提供者</span><span class="sxs-lookup"><span data-stu-id="be394-102">Accessing the WMI Provider Programmatically</span></span>
  <span data-ttu-id="be394-103">本主題尚在建構中。</span><span class="sxs-lookup"><span data-stu-id="be394-103">This topic is under construction.</span></span>  
  
## <a name="wmi-provider-overview"></a><span data-ttu-id="be394-104">WMI 提供者概觀</span><span class="sxs-lookup"><span data-stu-id="be394-104">WMI Provider Overview</span></span>  
 <span data-ttu-id="be394-105">本主題的程式碼範例中用來取得 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 相關資訊的命名空間為 **System.Management** 命名空間，其位於 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 中。</span><span class="sxs-lookup"><span data-stu-id="be394-105">The namespace used to obtain information about [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] in the code samples shown in this topic is the **System.Management** namespace, found in the [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="be394-106">**System.Management** 命名空間提供一組 Managed 程式碼類別，[!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 應用程式可以透過這些類別來存取和操作管理資訊。</span><span class="sxs-lookup"><span data-stu-id="be394-106">The **System.Management** namespace provides a set of managed code classes through which [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] applications can access and manipulate management information.</span></span> <span data-ttu-id="be394-107">如需使用 **System.Management** 命名空間以運用 Reporting Services WMI 類別的詳細資訊，請參閱 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] SDK 中的＜使用 System.Managment 存取管理資訊＞。</span><span class="sxs-lookup"><span data-stu-id="be394-107">For more information on using the Reporting Services WMI classes using the **System.Management** namespace, see "Accessing Management Information with System.Managment" in the [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] SDK.</span></span>  
  
## <a name="finding-a-report-server-instance"></a><span data-ttu-id="be394-108">尋找報表伺服器執行個體</span><span class="sxs-lookup"><span data-stu-id="be394-108">Finding a Report Server Instance</span></span>  
 <span data-ttu-id="be394-109">在報表伺服器安裝上尋找資訊的最好方法，就是列舉 WMI 執行個體集合。</span><span class="sxs-lookup"><span data-stu-id="be394-109">The preferred way of finding information on your report server installations is to enumerate through the WMI instance collection.</span></span> <span data-ttu-id="be394-110">以下範例顯示如何建立集合，以及對集合執行迴圈以顯示屬性，來尋找每個報表伺服器執行個體上的屬性。</span><span class="sxs-lookup"><span data-stu-id="be394-110">The example below shows how to find properties on every report server instance by creating a collection, and looping through the collection to display the properties.</span></span>  
  
```vb  
Imports System  
Imports System.Management  
Imports System.IO  
  
Module Module1  
    Sub Main()  
        Const WmiNamespace As String = "\\<ServerName>\root\Microsoft\SqlServer\ReportServer\<InstanceName>\v10\Admin"  
        Const WmiRSClass As String = _  
           "\\<ServerName>\root\Microsoft\SqlServer\ReportServer\<InstanceName>\v10\admin:MSReportServer_ConfigurationSetting"  
  
        Dim serverClass As ManagementClass  
        Dim scope As ManagementScope  
        scope = New ManagementScope(WmiNamespace)  
        'Connect to the Reporting Services namespace.  
        scope.Connect()  
  
        'Create the server class.  
        serverClass = New ManagementClass(WmiRSClass)  
        'Connect to the management object.  
        serverClass.Get()  
        If serverClass Is Nothing Then Throw New Exception("No class found")  
  
        'Loop through the instances of the server class.  
        Dim instances As ManagementObjectCollection = serverClass.GetInstances()  
        Dim instance As ManagementObject  
        For Each instance In instances  
            Console.Out.WriteLine("Instance Detected")  
            Dim instProps As PropertyDataCollection = instance.Properties  
            Dim prop As PropertyData  
            For Each prop In instProps  
                Dim name As String = prop.Name  
                Dim val As Object = prop.Value  
                Console.Out.Write("Property Name: " + name)  
                If val Is Nothing Then  
                    Console.Out.WriteLine("     Value: <null>")  
                Else  
                    Console.Out.WriteLine("     Value: " + val.ToString())  
                End If  
            Next  
        Next  
  
        Console.WriteLine("--- Press any key ---")  
        Console.ReadKey()  
  
    End Sub  
End Module  
```  
  
```csharp  
using System;  
using System.Management;  
using System.IO;  
[assembly: CLSCompliant(true)]  
  
class Class1  
{  
    [STAThread]  
    static void Main(string[] args)  
    {  
        const string WmiNamespace = @"\\<ServerName>\root\Microsoft\SqlServer\ReportServer\<InstanceName>\v10\Admin";  
        const string WmiRSClass =  
          @"\\<ServerName>\root\Microsoft\SqlServer\ReportServer\<InstanceName>\v10\admin:MSReportServer_ConfigurationSetting";  
        ManagementClass serverClass;  
        ManagementScope scope;  
        scope = new ManagementScope(WmiNamespace);  
  
        // Connect to the Reporting Services namespace.  
        scope.Connect();  
        // Create the server class.  
        serverClass = new ManagementClass(WmiRSClass);  
        // Connect to the management object.  
        serverClass.Get();  
        if (serverClass == null)  
            throw new Exception("No class found");  
  
        // Loop through the instances of the server class.  
        ManagementObjectCollection instances = serverClass.GetInstances();  
  
        foreach (ManagementObject instance in instances)  
        {  
            Console.Out.WriteLine("Instance Detected");  
            PropertyDataCollection instProps = instance.Properties;  
            foreach (PropertyData prop in instProps)  
            {  
                string name = prop.Name;  
                object val = prop.Value;  
                Console.Out.Write("Property Name: " + name);  
                if (val != null)  
                    Console.Out.WriteLine("     Value: " + val.ToString());  
                else  
                    Console.Out.WriteLine("     Value: <null>");  
            }  
        }  
        Console.WriteLine("\n--- Press any key ---");  
        Console.ReadKey();  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="be394-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="be394-111">See Also</span></span>  
 <span data-ttu-id="be394-112">[存取 Reporting Services WMI 提供者](tools/access-the-reporting-services-wmi-provider.md) </span><span class="sxs-lookup"><span data-stu-id="be394-112">[Access the Reporting Services WMI Provider](tools/access-the-reporting-services-wmi-provider.md) </span></span>  
 [<span data-ttu-id="be394-113">RSReportServer 設定檔</span><span class="sxs-lookup"><span data-stu-id="be394-113">RSReportServer Configuration File</span></span>](report-server/rsreportserver-config-configuration-file.md)  
  
  
