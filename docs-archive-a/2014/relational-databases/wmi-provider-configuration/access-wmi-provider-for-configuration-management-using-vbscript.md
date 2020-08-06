---
title: 使用 VBScript 修改 SQL Server 服務的 Advanced 屬性 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- VBScript [WMI]
- modifying SQL Server Service properties
- WMI Provider for Configuration Management, VBScript
ms.assetid: f3c5d981-eaa3-4d34-9b91-37e42636aa81
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 2cf722b00a31723b77624c33fef81a82ff0cb926
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606659"
---
# <a name="modify-sql-server-service-advanced-properties-using-vbscript"></a><span data-ttu-id="3f1dc-102">使用 VBScript 修改 SQL Server 服務進階屬性</span><span class="sxs-lookup"><span data-stu-id="3f1dc-102">Modify SQL Server Service Advanced Properties using VBScript</span></span>
  <span data-ttu-id="3f1dc-103">本節說明如何建立 VBScript 程式，以列出在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 電腦上執行之已安裝實例的版本 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="3f1dc-103">This section describes how to create a VBScript program that lists the version of installed instances of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that are running on a computer.</span></span>  
  
 <span data-ttu-id="3f1dc-104">此程式碼範例會列出在電腦上執行的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體和它的版本。</span><span class="sxs-lookup"><span data-stu-id="3f1dc-104">The code example lists the instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] running on the computer and its version.</span></span>  
  
### <a name="listing-name-and-version-of-installed-instances-of-sql-server"></a><span data-ttu-id="3f1dc-105">列出已安裝之 SQL Server 執行個體的名稱和版本</span><span class="sxs-lookup"><span data-stu-id="3f1dc-105">Listing name and version of installed instances of SQL Server</span></span>  
  
1.  <span data-ttu-id="3f1dc-106">在文字編輯器中開啟新的文件，例如 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 記事本。</span><span class="sxs-lookup"><span data-stu-id="3f1dc-106">Open a new document in a text editor, such as [!INCLUDE[msCoName](../../includes/msconame-md.md)] Notepad.</span></span> <span data-ttu-id="3f1dc-107">複製這個程序之後的程式碼，然後使用 .vbs 副檔名來儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="3f1dc-107">Copy the code that follows this procedure and save the file with a .vbs extension.</span></span> <span data-ttu-id="3f1dc-108">此範例稱為 test.vbs。</span><span class="sxs-lookup"><span data-stu-id="3f1dc-108">This example is called test.vbs.</span></span>  
  
2.  <span data-ttu-id="3f1dc-109">使用 VBScript `GetObject` 函數連接到電腦管理的 WMI 提供者執行個體。</span><span class="sxs-lookup"><span data-stu-id="3f1dc-109">Connect to an instance of the WMI Provider for Computer Management with the VBScript `GetObject` function.</span></span> <span data-ttu-id="3f1dc-110">此範例會連接到名為 mpc 的遠端電腦，但是會省略電腦名稱來連接本機電腦：winmgmts:root\Microsoft\SqlServer\ComputerManagement。</span><span class="sxs-lookup"><span data-stu-id="3f1dc-110">This example connects to a remote computer named mpc, but omit the computer name to connect to the local computer: winmgmts:root\Microsoft\SqlServer\ComputerManagement.</span></span> <span data-ttu-id="3f1dc-111">如需有關 `GetObject` 函數的詳細資訊，請參閱 VBScript 參考資料。</span><span class="sxs-lookup"><span data-stu-id="3f1dc-111">For more information about the `GetObject` function, see the VBScript reference.</span></span>  
  
3.  <span data-ttu-id="3f1dc-112">使用 `InstancesOf` 方法來列舉服務的清單。</span><span class="sxs-lookup"><span data-stu-id="3f1dc-112">Use the `InstancesOf` method to enumerate a list of the services.</span></span> <span data-ttu-id="3f1dc-113">也可以使用簡單 WQL 查詢和 `ExecQuery` 方法 (而不是 `InstancesOf` 方法) 來列舉此服務。</span><span class="sxs-lookup"><span data-stu-id="3f1dc-113">The services can also be enumerated by using a simple WQL query and an `ExecQuery` method instead of the `InstancesOf` method.</span></span>  
  
4.  <span data-ttu-id="3f1dc-114">使用 `ExecQuery` 方法和 WQL 查詢來擷取已安裝之 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體的名稱和版本。</span><span class="sxs-lookup"><span data-stu-id="3f1dc-114">Use the `ExecQuery` method and a WQL query to retrieve the name and version of the installed instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
5.  <span data-ttu-id="3f1dc-115">儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="3f1dc-115">Save the file.</span></span>  
  
6.  <span data-ttu-id="3f1dc-116">在命令提示字元中輸入，以執行腳本 `cscript test.vbs` 。</span><span class="sxs-lookup"><span data-stu-id="3f1dc-116">Run the script by typing `cscript test.vbs` at the command prompt.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3f1dc-117">範例</span><span class="sxs-lookup"><span data-stu-id="3f1dc-117">Example</span></span>  
  
```  
set wmi = GetObject("WINMGMTS:\\.\root\Microsoft\SqlServer\ComputerManagement12")  
for each prop in wmi.ExecQuery("select * from SqlServiceAdvancedProperty where SQLServiceType = 1 AND PropertyName = 'VERSION'")  
WScript.Echo prop.ServiceName & " " & prop.PropertyName & ": " & prop.PropertyStrValue  
next  
```  
  
  
