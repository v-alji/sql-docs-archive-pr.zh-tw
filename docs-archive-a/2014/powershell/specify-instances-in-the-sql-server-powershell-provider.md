---
title: 指定 SQL Server PowerShell 提供者中的執行個體 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: scripting
ms.topic: conceptual
ms.assetid: 9373de68-fd43-45f2-b9a6-149c96610aeb
author: stevestein
ms.author: sstein
ms.openlocfilehash: cc04bacc1ff36b0b5ce526a377fcdb750ad134a4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595144"
---
# <a name="specify-instances-in-the-sql-server-powershell-provider"></a><span data-ttu-id="7080a-102">指定 SQL Server PowerShell 提供者中的執行個體</span><span class="sxs-lookup"><span data-stu-id="7080a-102">Specify Instances in the SQL Server PowerShell Provider</span></span>
  <span data-ttu-id="7080a-103">針對 SQL Server PowerShell 提供者指定的路徑必須識別 [!INCLUDE[ssDE](../includes/ssde-md.md)] 的執行個體及其執行所在的電腦。</span><span class="sxs-lookup"><span data-stu-id="7080a-103">The paths specified for the SQL Server PowerShell provider must identify the instance of the [!INCLUDE[ssDE](../includes/ssde-md.md)] and the computer it is running on.</span></span> <span data-ttu-id="7080a-104">用來指定電腦和執行個體的語法必須符合 SQL Server 識別碼和 Windows PowerShell 路徑的規則。</span><span class="sxs-lookup"><span data-stu-id="7080a-104">The syntax for specifying the computer and the instance must comply with both the rules for SQL Server identifiers and Windows PowerShell paths.</span></span>  
  
1.  <span data-ttu-id="7080a-105">**開始之前：**  [限制事項](#LimitationsRestrictions)</span><span class="sxs-lookup"><span data-stu-id="7080a-105">**Before you begin:**  [Limitations and Restrictions](#LimitationsRestrictions)</span></span>  
  
2.  <span data-ttu-id="7080a-106">**若要指定執行個體：**  [範例](#Examples)</span><span class="sxs-lookup"><span data-stu-id="7080a-106">**To specify an instance:**  [Examples](#Examples)</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="7080a-107">開始之前</span><span class="sxs-lookup"><span data-stu-id="7080a-107">Before You Begin</span></span>  
 <span data-ttu-id="7080a-108">SQL Server 提供者路徑中接在 SQLSERVER:\SQL 後面的第一個節點是執行 [!INCLUDE[ssDE](../includes/ssde-md.md)]執行個體的電腦名稱。例如：</span><span class="sxs-lookup"><span data-stu-id="7080a-108">The first node following the SQLSERVER:\SQL in a SQL Server provider path is the name of the computer that is running the instance of the [!INCLUDE[ssDE](../includes/ssde-md.md)]; for example:</span></span>  
  
```  
SQLSERVER:\SQL\MyComputer  
```  
  
 <span data-ttu-id="7080a-109">如果您在與 [!INCLUDE[ssDE](../includes/ssde-md.md)]執行個體相同的電腦上執行 Windows PowerShell，就可以使用 localhost 或 (local) 來取代電腦的名稱。</span><span class="sxs-lookup"><span data-stu-id="7080a-109">If you are running Windows PowerShell on the same computer as the instance of the [!INCLUDE[ssDE](../includes/ssde-md.md)], you can use either localhost or (local) instead of the name of the computer.</span></span> <span data-ttu-id="7080a-110">使用 localhost 或 (local) 的指令碼可以在任何電腦上執行，而不需要變更成反映不同的電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="7080a-110">Scripts that use localhost or (local) can be run on any computer without having to be changed to reflect the different computer names.</span></span>  
  
 <span data-ttu-id="7080a-111">您可以在相同電腦上執行 [!INCLUDE[ssDE](../includes/ssde-md.md)] 可執行程式的多個執行個體。</span><span class="sxs-lookup"><span data-stu-id="7080a-111">You can run multiple instances of the [!INCLUDE[ssDE](../includes/ssde-md.md)] executable program on the same computer.</span></span> <span data-ttu-id="7080a-112">SQL Server 提供者路徑中接在電腦名稱後面的節點可識別執行個體。例如：</span><span class="sxs-lookup"><span data-stu-id="7080a-112">The node following the computer name in a SQL Server provider path identifies the instance; for example:</span></span>  
  
```  
SQLSERVER:\SQL\MyComputer\MyInstance  
```  
  
 <span data-ttu-id="7080a-113">每一部電腦都只能有一個預設 [!INCLUDE[ssDE](../includes/ssde-md.md)]執行個體。</span><span class="sxs-lookup"><span data-stu-id="7080a-113">Each computer can have one default instance of the [!INCLUDE[ssDE](../includes/ssde-md.md)].</span></span> <span data-ttu-id="7080a-114">當您安裝預設執行個體時，未指定它的名稱。</span><span class="sxs-lookup"><span data-stu-id="7080a-114">You do not specify a name for the default instance when you install it.</span></span> <span data-ttu-id="7080a-115">如果您在連接字串中只有指定電腦名稱，您會連接到該電腦上的預設執行個體。</span><span class="sxs-lookup"><span data-stu-id="7080a-115">If you specify only a computer name in a connection string, you are connected to the default instance on that computer.</span></span> <span data-ttu-id="7080a-116">此電腦上的所有其他執行個體都必須是具名執行個體。</span><span class="sxs-lookup"><span data-stu-id="7080a-116">All other instances on the computer must be named instances.</span></span> <span data-ttu-id="7080a-117">您可在安裝期間指定執行個體名稱，而且連接字串必須指定電腦名稱和執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="7080a-117">You specify the instance name during setup, and connection strings must specify both the computer name and the instance name.</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> <span data-ttu-id="7080a-118">限制事項</span><span class="sxs-lookup"><span data-stu-id="7080a-118">Limitations and Restrictions</span></span>  
 <span data-ttu-id="7080a-119">您無法使用句號 (.)，在 PowerShell 指令碼中指定本機電腦。</span><span class="sxs-lookup"><span data-stu-id="7080a-119">You cannot use a period (.) to specify the local computer in PowerShell scripts.</span></span> <span data-ttu-id="7080a-120">因為句號會被 PowerShell 解譯成命令，所以不支援句號。</span><span class="sxs-lookup"><span data-stu-id="7080a-120">The period is not supported because the period is interpreted as a command by PowerShell.</span></span>  
  
 <span data-ttu-id="7080a-121">(local) 中的括號字元通常會被 Windows PowerShell 視為命令。</span><span class="sxs-lookup"><span data-stu-id="7080a-121">The parenthesis characters in (local) are normally treated as commands by Windows PowerShell.</span></span> <span data-ttu-id="7080a-122">您必須將其編碼或逸出以在路徑中使用，或使用雙引號括住路徑。</span><span class="sxs-lookup"><span data-stu-id="7080a-122">You must either encode them or escape them for use in a path, or enclose the path in double-quotation marks.</span></span> <span data-ttu-id="7080a-123">如需詳細資訊，請參閱＜編碼及解碼 SQL Server 識別碼＞。</span><span class="sxs-lookup"><span data-stu-id="7080a-123">For more information, see Encode and Decode SQL Server Identifiers.</span></span>  
  
 <span data-ttu-id="7080a-124">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 提供者會要求您一定要指定執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="7080a-124">The [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] provider requires that you always specify an instance name.</span></span> <span data-ttu-id="7080a-125">如果是預設執行個體，您必須指定執行個體名稱 DEFAULT。</span><span class="sxs-lookup"><span data-stu-id="7080a-125">For default instances, you must specify an instance name of DEFAULT.</span></span>  
  
##  <a name="examples-computer-and-instance-names"></a><a name="Examples"></a><span data-ttu-id="7080a-126">典型電腦和實例名稱</span><span class="sxs-lookup"><span data-stu-id="7080a-126">Examples; Computer and Instance Names</span></span>  
 <span data-ttu-id="7080a-127">此範例使用 localhost 和 DEFAULT 指定本機電腦上的預設執行個體：</span><span class="sxs-lookup"><span data-stu-id="7080a-127">This example uses localhost and DEFAULT to specify the default instance on the local computer:</span></span>  
  
```powershell
Set-Location SQLSERVER:\SQL\localhost\DEFAULT
```  
  
 <span data-ttu-id="7080a-128">(local) 中的括號字元通常會被 Windows PowerShell 視為命令。</span><span class="sxs-lookup"><span data-stu-id="7080a-128">The parenthesis characters in (local) are normally treated as commands by Windows PowerShell.</span></span> <span data-ttu-id="7080a-129">因此，您必須：</span><span class="sxs-lookup"><span data-stu-id="7080a-129">You must either:</span></span>  
  
-   <span data-ttu-id="7080a-130">使用引號括住路徑字串：</span><span class="sxs-lookup"><span data-stu-id="7080a-130">Enclose the path string in quotes:</span></span>  
  
    ```powershell
    Set-Location "SQLSERVER:\SQL\(local)\DEFAULT"  
    ```  
  
-   <span data-ttu-id="7080a-131">使用反勾號字元 (\`) 來逸出括號：</span><span class="sxs-lookup"><span data-stu-id="7080a-131">Escape the parenthesis using the back tick character (\`):</span></span>  
  
    ```powershell
    Set-Location SQLSERVER:\SQL\`(local`)\DEFAULT  
    ```  
  
-   <span data-ttu-id="7080a-132">使用十六進位表示法來編碼括號：</span><span class="sxs-lookup"><span data-stu-id="7080a-132">Encode the parenthesis using their hexadecimal representation:</span></span>  
  
    ```powershell
    Set-Location SQLSERVER:\SQL\%28local%29\DEFAULT  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="7080a-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7080a-133">See Also</span></span>  
 <span data-ttu-id="7080a-134">[PowerShell 中的 SQL Server 識別碼](sql-server-identifiers-in-powershell.md) </span><span class="sxs-lookup"><span data-stu-id="7080a-134">[SQL Server Identifiers in PowerShell](sql-server-identifiers-in-powershell.md) </span></span>  
 <span data-ttu-id="7080a-135">[SQL Server PowerShell 提供者](sql-server-powershell-provider.md) </span><span class="sxs-lookup"><span data-stu-id="7080a-135">[SQL Server PowerShell Provider](sql-server-powershell-provider.md) </span></span>  
 [<span data-ttu-id="7080a-136">SQL Server PowerShell</span><span class="sxs-lookup"><span data-stu-id="7080a-136">SQL Server PowerShell</span></span>](sql-server-powershell.md)  
