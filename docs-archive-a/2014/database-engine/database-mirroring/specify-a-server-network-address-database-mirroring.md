---
title: 指定伺服器網路位址 (資料庫鏡像) | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- database mirroring [SQL Server], deployment
- database mirroring [SQL Server], endpoint
- endpoints [SQL Server], database mirroring
- server network addresses [SQL Server]
ms.assetid: a64d4b6b-9016-4f1e-a310-b1df181dd0c6
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 5c7db7ee6d321229205248059ce09a86f1da101f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596882"
---
# <a name="specify-a-server-network-address-database-mirroring"></a><span data-ttu-id="a772d-102">指定伺服器網路位址 (資料庫鏡像)</span><span class="sxs-lookup"><span data-stu-id="a772d-102">Specify a Server Network Address (Database Mirroring)</span></span>
  <span data-ttu-id="a772d-103">設定資料庫鏡像工作階段時，需要有每一個伺服器執行個體的伺服器網路位址。</span><span class="sxs-lookup"><span data-stu-id="a772d-103">Setting up a database mirroring session requires a server network address for each of the server instances.</span></span> <span data-ttu-id="a772d-104">伺服器執行個體的伺服器網路位址必須透過提供系統位址和執行個體所接聽的通訊埠編號，以明確識別該執行個體。</span><span class="sxs-lookup"><span data-stu-id="a772d-104">The server network address of a server instance must unambiguously identify the instance by providing a system address and the number of the port on which the instance is listening.</span></span>  
  
 <span data-ttu-id="a772d-105">伺服器執行個體上必須有資料庫鏡像端點，您才能在伺服器網路位址中指定通訊埠。</span><span class="sxs-lookup"><span data-stu-id="a772d-105">Before you can specify a port in a server network address, the database mirroring endpoint must exist on the server instance.</span></span> <span data-ttu-id="a772d-106">如需詳細資訊，請參閱[建立 Windows 驗證的資料庫鏡像端點 &#40;Transact-SQL&#41;](create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="a772d-106">For more information, see [Create a Database Mirroring Endpoint for Windows Authentication &#40;Transact-SQL&#41;](create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md).</span></span>  
  
  
  
##  <a name="syntax-for-a-server-network-address"></a><a name="Syntax"></a> <span data-ttu-id="a772d-107">伺服器網路位址的語法</span><span class="sxs-lookup"><span data-stu-id="a772d-107">Syntax for a Server Network Address</span></span>  
 <span data-ttu-id="a772d-108">伺服器網路位址的語法採用下列格式：</span><span class="sxs-lookup"><span data-stu-id="a772d-108">The syntax for a server network address is of the form:</span></span>  
  
 <span data-ttu-id="a772d-109">TCP：<strong>//</strong> *\<system-address>* <strong> ：<strong>*\<port>*</span><span class="sxs-lookup"><span data-stu-id="a772d-109">TCP<strong>://</strong>*\<system-address>*<strong>:<strong>*\<port>*</span></span> 
  
 <span data-ttu-id="a772d-110">其中</span><span class="sxs-lookup"><span data-stu-id="a772d-110">where</span></span>  
  
-   <span data-ttu-id="a772d-111">*\<system-address>* 是可明確識別目的地電腦系統的字串。</span><span class="sxs-lookup"><span data-stu-id="a772d-111">*\<system-address>* is a string that unambiguously identifies the destination computer system.</span></span> <span data-ttu-id="a772d-112">伺服器位址通常是系統名稱 (如果系統位於同一個網域內)、完整網域名稱或 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="a772d-112">Typically, the server address is a system name (if the systems are in the same domain), a fully qualified domain name, or an IP address:</span></span>  
  
    -   <span data-ttu-id="a772d-113">如果系統位於同一個網域，您可以使用電腦系統的名稱，例如 `SYSTEM46`。</span><span class="sxs-lookup"><span data-stu-id="a772d-113">If the systems are the same domain, you can use the name of the computer system; for example, `SYSTEM46`.</span></span>  
  
    -   <span data-ttu-id="a772d-114">若要使用 IP 位址，則它在您的環境中必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="a772d-114">To use an IP address, it must be unique in your environment.</span></span> <span data-ttu-id="a772d-115">建議您只使用靜態的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="a772d-115">We recommend that you use an IP address only if it is static.</span></span> <span data-ttu-id="a772d-116">此 IP 位址可以是 IP 第 4 版 (IPv4) 或 IP 第 6 版 (IPv6)。</span><span class="sxs-lookup"><span data-stu-id="a772d-116">The IP address can be IP Version 4 (IPv4) or IP Version 6 (IPv6).</span></span> <span data-ttu-id="a772d-117">IPv6 位址必須使用方括弧括住，例如： **[** <IPv6 位址> **]** 。</span><span class="sxs-lookup"><span data-stu-id="a772d-117">An IPv6 address must be enclosed within square brackets, for example: **[**_<IPv6_address>_**]**.</span></span>  
  
         <span data-ttu-id="a772d-118">若要取得系統的 IP 位址，請在 Windows 命令提示字元下，輸入 **ipconfig** 命令。</span><span class="sxs-lookup"><span data-stu-id="a772d-118">To learn the IP address of a system, at the Windows command prompt, enter the **ipconfig** command.</span></span>  
  
    -   <span data-ttu-id="a772d-119">完整網域名稱保證可以運作。</span><span class="sxs-lookup"><span data-stu-id="a772d-119">The fully qualified domain name is guaranteed to work.</span></span> <span data-ttu-id="a772d-120">這是在不同位置會有不同格式的本機定義位址字串。</span><span class="sxs-lookup"><span data-stu-id="a772d-120">This is a locally defined address string that different forms in different places.</span></span> <span data-ttu-id="a772d-121">完整網域名稱通常 (但不一定) 都是複合名稱，包含電腦名稱及一系列以句號分隔的網域區段，並採用下列格式：</span><span class="sxs-lookup"><span data-stu-id="a772d-121">Often, but not always, a fully qualified domain name is a compound name that includes the computer name and a series of period-separated domain segments of the form:</span></span>  
  
         <span data-ttu-id="a772d-122">_電腦名稱_ **.**</span><span class="sxs-lookup"><span data-stu-id="a772d-122">_computer_name_ **.**</span></span> <span data-ttu-id="a772d-123">_網域區段_[... **.** _網域區段_]</span><span class="sxs-lookup"><span data-stu-id="a772d-123">_domain_segment_[...**.**_domain_segment_]</span></span>  
  
         <span data-ttu-id="a772d-124">其中 *電腦名稱*是執行伺服器執行個體之電腦的網路名稱，而 *網域區段*[... **.** _網域區段_] 則是伺服器的其餘網域資訊；例如： `localinfo.corp.Adventure-Works.com`。</span><span class="sxs-lookup"><span data-stu-id="a772d-124">where *computer_name i*s the network name of the computer running the server instance, and *domain_segment*[...**.**_domain_segment_] is the remaining domain information of the server; for example: `localinfo.corp.Adventure-Works.com`.</span></span>  
  
         <span data-ttu-id="a772d-125">網域區段的內容和數目是在公司或組織的內部決定的。</span><span class="sxs-lookup"><span data-stu-id="a772d-125">The content and number of domain segments are determined within the company or organization.</span></span> <span data-ttu-id="a772d-126">如果您不知道伺服器的完整網域名稱，請洽詢您的系統管理員。</span><span class="sxs-lookup"><span data-stu-id="a772d-126">If you do not know the fully qualified domain name for your server, see your system administrator.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="a772d-127">如需有關如何尋找完整網域名稱的詳細資訊，請參閱本主題稍後的「尋找完整網域名稱」。</span><span class="sxs-lookup"><span data-stu-id="a772d-127">For information about how to find a fully qualified domain name, see "Finding the Fully Qualified Domain Name," later in this topic.</span></span>  
  
-   <span data-ttu-id="a772d-128">*\<port>* 是夥伴伺服器執行個體鏡像端點所使用的連接埠號碼。</span><span class="sxs-lookup"><span data-stu-id="a772d-128">*\<port>* is the port number used by the mirroring endpoint of the partner server instance.</span></span> <span data-ttu-id="a772d-129">如需指定端點的資訊，請參閱 [建立 Windows 驗證的資料庫鏡像端點 &#40;Transact-SQL&#41;](create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="a772d-129">For information about specifying an endpoint, see [Create a Database Mirroring Endpoint for Windows Authentication &#40;Transact-SQL&#41;](create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md).</span></span>  
  
     <span data-ttu-id="a772d-130">資料庫鏡像端點可以使用電腦系統上任何可用的通訊埠。</span><span class="sxs-lookup"><span data-stu-id="a772d-130">A database mirroring endpoint can use any available port on the computer system.</span></span> <span data-ttu-id="a772d-131">電腦系統上的每個通訊埠編號必須只與一個端點產生關聯，而且每個端點會與單一伺服器執行個體產生關聯，因此相同伺服器上的不同伺服器執行個體會利用不同通訊埠接聽不同端點。</span><span class="sxs-lookup"><span data-stu-id="a772d-131">Each port number on a computer system must be associated with only one endpoint, and each endpoint is associated with a single server instance; thus, different server instances on the same server listen on different endpoints with different ports.</span></span> <span data-ttu-id="a772d-132">因此，當您設定資料庫鏡像工作階段時，在伺服器網路位址中指定的通訊埠，會永遠把工作階段導向到端點與該通訊埠產生關聯的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="a772d-132">Therefore, the port you specify in the server network address when you set up a database mirroring session will always direct the session to the server instance whose endpoint is associated with that port.</span></span>  
  
     <span data-ttu-id="a772d-133">在伺服器執行個體的伺服器網路位址中，只有與鏡像端點產生關聯的通訊埠編號，會從電腦上的任何其他執行個體中區分該執行個體。</span><span class="sxs-lookup"><span data-stu-id="a772d-133">In the server network address of a server instance, only the number of the port associated with its mirroring endpoint distinguishes that instance from any other instances on the computer.</span></span> <span data-ttu-id="a772d-134">下圖說明單一電腦上兩個伺服器執行個體的伺服器網路位址。</span><span class="sxs-lookup"><span data-stu-id="a772d-134">The following figure illustrates the server network addresses of two server instances on a single computer.</span></span> <span data-ttu-id="a772d-135">預設的執行個體會使用通訊埠 `7022` ，而具名執行個體則使用通訊埠 `7033`。</span><span class="sxs-lookup"><span data-stu-id="a772d-135">The default instance uses port `7022` and the named instance uses port `7033`.</span></span> <span data-ttu-id="a772d-136">這兩個伺服器執行個體的伺服器網路位址分別為： `TCP://MYSYSTEM.Adventure-works.MyDomain.com:7022` 和 `TCP://MYSYSTEM.Adventure-works.MyDomain.com:7033`。</span><span class="sxs-lookup"><span data-stu-id="a772d-136">The server network address for these two server instances are, respectively: `TCP://MYSYSTEM.Adventure-works.MyDomain.com:7022` and `TCP://MYSYSTEM.Adventure-works.MyDomain.com:7033`.</span></span> <span data-ttu-id="a772d-137">請注意，位址不包含伺服器執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="a772d-137">Note that the address does not contain the name of the server instance.</span></span>  
  
     <span data-ttu-id="a772d-138">![預設執行個體的伺服器網路位址](../media/dbm-2-instances-ports-1-system.gif "預設執行個體的伺服器網路位址")</span><span class="sxs-lookup"><span data-stu-id="a772d-138">![Server network addresses of a default instance](../media/dbm-2-instances-ports-1-system.gif "Server network addresses of a default instance")</span></span>  
  
     <span data-ttu-id="a772d-139">若要識別目前關聯於伺服器執行個體之資料庫鏡像端點的通訊埠，請使用下列 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式：</span><span class="sxs-lookup"><span data-stu-id="a772d-139">To identify the port currently associated with database mirroring endpoint of a server instance, use the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement:</span></span>  
  
    ```  
    SELECT type_desc, port FROM sys.tcp_endpoints  
    ```  
  
     <span data-ttu-id="a772d-140">尋找 **type_desc** 值是 "DATABASE_MIRRORING" 的資料列，並使用對應通訊埠編號。</span><span class="sxs-lookup"><span data-stu-id="a772d-140">Find the row whose **type_desc** value is "DATABASE_MIRRORING," and use the corresponding port number.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="a772d-141">範例</span><span class="sxs-lookup"><span data-stu-id="a772d-141">Examples</span></span>  
  
#### <a name="a-using-a-system-name"></a><span data-ttu-id="a772d-142">A.</span><span class="sxs-lookup"><span data-stu-id="a772d-142">A.</span></span> <span data-ttu-id="a772d-143">使用系統名稱</span><span class="sxs-lookup"><span data-stu-id="a772d-143">Using a system name</span></span>  
 <span data-ttu-id="a772d-144">下列伺服器網路位址會指定一個系統名稱 `SYSTEM46`和通訊埠 `7022`。</span><span class="sxs-lookup"><span data-stu-id="a772d-144">The following server network address specifies a system name, `SYSTEM46`, and port `7022`.</span></span>  
  
```  
ALTER DATABASE AdventureWorks SET PARTNER ='tcp://SYSTEM46:7022';  
```  
  
#### <a name="b-using-a-fully-qualified-domain-name"></a><span data-ttu-id="a772d-145">B.</span><span class="sxs-lookup"><span data-stu-id="a772d-145">B.</span></span> <span data-ttu-id="a772d-146">使用完整網域名稱</span><span class="sxs-lookup"><span data-stu-id="a772d-146">Using a fully qualified domain name</span></span>  
 <span data-ttu-id="a772d-147">下列伺服器網路位址會指定一個完整網域名稱 `DBSERVER8.manufacturing.Adventure-Works.com`和通訊埠 `7024`。</span><span class="sxs-lookup"><span data-stu-id="a772d-147">The following server network address specifies a fully qualified domain name, `DBSERVER8.manufacturing.Adventure-Works.com`, and port `7024`.</span></span>  
  
```  
ALTER DATABASE AdventureWorks SET PARTNER ='tcp://DBSERVER8.manufacturing.Adventure-Works.com:7024';  
```  
  
#### <a name="c-using-ipv4"></a><span data-ttu-id="a772d-148">C.</span><span class="sxs-lookup"><span data-stu-id="a772d-148">C.</span></span> <span data-ttu-id="a772d-149">使用 IPv4</span><span class="sxs-lookup"><span data-stu-id="a772d-149">Using IPv4</span></span>  
 <span data-ttu-id="a772d-150">下列伺服器網路位址會指定一個 IPv4 位址 `10.193.9.134`和通訊埠 `7023`。</span><span class="sxs-lookup"><span data-stu-id="a772d-150">The following server network address specifies an IPv4 address, `10.193.9.134`, and port `7023`.</span></span>  
  
```  
ALTER DATABASE AdventureWorks SET PARTNER ='tcp://10.193.9.134:7023';  
```  
  
#### <a name="d-using-ipv6"></a><span data-ttu-id="a772d-151">D.</span><span class="sxs-lookup"><span data-stu-id="a772d-151">D.</span></span> <span data-ttu-id="a772d-152">使用 IPv6</span><span class="sxs-lookup"><span data-stu-id="a772d-152">Using IPv6</span></span>  
 <span data-ttu-id="a772d-153">下列伺服器網路位址會包含一個 IPv6 位址 `2001:4898:23:1002:20f:1fff:feff:b3a3`和通訊埠 `7022`。</span><span class="sxs-lookup"><span data-stu-id="a772d-153">The following server network address contains an IPv6 address, `2001:4898:23:1002:20f:1fff:feff:b3a3`, and port `7022`.</span></span>  
  
```  
ALTER DATABASE AdventureWorks SET PARTNER ='tcp://[2001:4898:23:1002:20f:1fff:feff:b3a3]:7022';  
```  
  
## <a name="finding-the-fully-qualified-domain-name"></a><span data-ttu-id="a772d-154">尋找完整網域名稱</span><span class="sxs-lookup"><span data-stu-id="a772d-154">Finding the Fully Qualified Domain Name</span></span>  
 <span data-ttu-id="a772d-155">若要尋找系統的完整網域名稱，請在該系統的 Windows 命令提示字元下，輸入：</span><span class="sxs-lookup"><span data-stu-id="a772d-155">To find the fully qualified domain name of a system, at the Windows command prompt on that system, enter:</span></span>  
  
 <span data-ttu-id="a772d-156">**IPCONFIG /ALL**</span><span class="sxs-lookup"><span data-stu-id="a772d-156">**IPCONFIG /ALL**</span></span>  
  
 <span data-ttu-id="a772d-157">若要形成完整的網域名稱，請串連 <主機名稱> 和 <主要 DNS 尾碼> 的值，如下所示：</span><span class="sxs-lookup"><span data-stu-id="a772d-157">To form the fully qualified domain name, concatenate the values of *<host_name>* and *<Primary_Dns_Suffix>* as follows:</span></span>  
  
 <span data-ttu-id="a772d-158">_<主機名稱>_ **.**</span><span class="sxs-lookup"><span data-stu-id="a772d-158">_<host_name>_ **.**</span></span> <span data-ttu-id="a772d-159">_<主要 DNS 尾碼>_</span><span class="sxs-lookup"><span data-stu-id="a772d-159">_<Primary_Dns_Suffix>_</span></span>  
  
 <span data-ttu-id="a772d-160">例如，IP 組態</span><span class="sxs-lookup"><span data-stu-id="a772d-160">For example, the IP configuration</span></span>  
  
 `Host Name  .  .  .  .  .  .  : MYSERVER`  
  
 `Primary Dns Suffix  .  .  .  : mydomain.Adventure-Works.com`  
  
 <span data-ttu-id="a772d-161">等於下列完整的網域名稱：</span><span class="sxs-lookup"><span data-stu-id="a772d-161">equates to the following fully qualified domain name:</span></span>  
  
 `MYSERVER.mydomain.Adventure-Works.com`  
  
##  <a name="examples"></a><a name="Examples"></a> <span data-ttu-id="a772d-162">範例</span><span class="sxs-lookup"><span data-stu-id="a772d-162">Examples</span></span>  
 <span data-ttu-id="a772d-163">下列範例會顯示另一個網域中名為 `REMOTESYSTEM3` 之電腦系統上伺服器執行個體的伺服器網路位址。</span><span class="sxs-lookup"><span data-stu-id="a772d-163">The following example shows the server network address for a server instance on a computer system named `REMOTESYSTEM3` in another domain.</span></span> <span data-ttu-id="a772d-164">網域資訊為 `NORTHWEST.ADVENTURE-WORKS.COM`，而且資料庫鏡像端點的通訊埠為 `7025`。</span><span class="sxs-lookup"><span data-stu-id="a772d-164">The domain information is `NORTHWEST.ADVENTURE-WORKS.COM`, and the port of the database mirroring endpoint is `7025`.</span></span> <span data-ttu-id="a772d-165">如果有這些範例元件，伺服器網路位址就是：</span><span class="sxs-lookup"><span data-stu-id="a772d-165">Given these example components, the server network address is.</span></span>  
  
 `TCP://REMOTESYSTEM3.NORTHWEST.ADVENTURE-WORKS.COM:7025`  
  
 <span data-ttu-id="a772d-166">下列範例會顯示名為 `DBSERVER1`之電腦系統上伺服器執行個體的伺服器網路位址。</span><span class="sxs-lookup"><span data-stu-id="a772d-166">The following example shows the server network address for a server instance on a computer system named `DBSERVER1`.</span></span> <span data-ttu-id="a772d-167">此系統位於本機網域，並由其系統名稱明確識別。</span><span class="sxs-lookup"><span data-stu-id="a772d-167">This system is in the local domain and is unambiguously identified by its system name.</span></span> <span data-ttu-id="a772d-168">資料庫鏡像端點的通訊埠為 `7022`。</span><span class="sxs-lookup"><span data-stu-id="a772d-168">The port of the database mirroring endpoint is `7022`.</span></span>  
  
 `TCP://DBSERVER1:7022`  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="a772d-169">相關工作</span><span class="sxs-lookup"><span data-stu-id="a772d-169">Related Tasks</span></span>  
  
-   [<span data-ttu-id="a772d-170">建立 Windows 驗證的資料庫鏡像端點 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a772d-170">Create a Database Mirroring Endpoint for Windows Authentication &#40;Transact-SQL&#41;</span></span>](create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)  
  
## <a name="see-also"></a><span data-ttu-id="a772d-171">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a772d-171">See Also</span></span>  
 <span data-ttu-id="a772d-172">[資料庫鏡像 &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="a772d-172">[Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span></span>  
 [<span data-ttu-id="a772d-173">資料庫鏡像端點 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a772d-173">The Database Mirroring Endpoint &#40;SQL Server&#41;</span></span>](the-database-mirroring-endpoint-sql-server.md)  
  
  
