---
title: 在新增或修改可用性複本時指定端點 URL (SQL Server) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- endpoints [SQL Server], AlwaysOn Availability Groups
- Availability Groups [SQL Server], configuring
- Availability Groups [SQL Server], endpoint
- Endpoint URLs (HADR)
ms.assetid: d7520c13-a8ee-4ddc-9e9a-54cd3d27ef1c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: da1eb2bacd4d5a2f7d0b2a623343f62b5e89597d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708658"
---
# <a name="specify-the-endpoint-url-when-adding-or-modifying-an-availability-replica-sql-server"></a><span data-ttu-id="08f90-102">在加入或修改可用性複本時指定端點 URL (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="08f90-102">Specify the Endpoint URL When Adding or Modifying an Availability Replica (SQL Server)</span></span>
  <span data-ttu-id="08f90-103">若要裝載可用性群組的可用性複本，伺服器執行個體必須擁有資料庫鏡像端點。</span><span class="sxs-lookup"><span data-stu-id="08f90-103">To host an availability replica for an availability group, a server instance must possess a database mirroring endpoint.</span></span> <span data-ttu-id="08f90-104">伺服器執行個體使用此端點接聽來自其他伺服器執行個體所裝載之可用性複本的 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 訊息。</span><span class="sxs-lookup"><span data-stu-id="08f90-104">The server instance uses this endpoint to listen for [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] messages from availability replicas hosted by other server instances.</span></span> <span data-ttu-id="08f90-105">若要定義可用性群組的可用性複本，您必須指定將要裝載此複本之伺服器執行個體的端點 URL。</span><span class="sxs-lookup"><span data-stu-id="08f90-105">To define an availability replica for an availability group, you must specify the endpoint URL of the server instance that will host the replica.</span></span> <span data-ttu-id="08f90-106">「端點 URL」會識別資料庫鏡像端點的傳輸通訊協定 (TCP)、伺服器執行個體的系統位址，以及與端點相關聯的連接埠號碼。</span><span class="sxs-lookup"><span data-stu-id="08f90-106">The *endpoint URL* identifies the transport protocol of the database mirroring endpoint-TCP, the system address of the server instance, and the port number associated with the endpoint.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="08f90-107">「端點 URL」一詞是資料庫鏡像使用者介面和文件集所用「伺服器網路位址」一詞的同義詞。</span><span class="sxs-lookup"><span data-stu-id="08f90-107">The term "endpoint URL" is synonymous with the term "server network address" used by the database mirroring user interface and documentation.</span></span>  
  
-   [<span data-ttu-id="08f90-108">端點 URL 的語法</span><span class="sxs-lookup"><span data-stu-id="08f90-108">Syntax for an Endpoint URL</span></span>](#SyntaxOfURL)  
  
-   [<span data-ttu-id="08f90-109">尋找系統的完整功能變數名稱</span><span class="sxs-lookup"><span data-stu-id="08f90-109">Finding the Fully Qualified Domain Name of A System</span></span>](#Finding_FQDN)  
  
-   [<span data-ttu-id="08f90-110">相關工作</span><span class="sxs-lookup"><span data-stu-id="08f90-110">Related Tasks</span></span>](#RelatedTasks)  
  
-   [<span data-ttu-id="08f90-111">相關內容</span><span class="sxs-lookup"><span data-stu-id="08f90-111">Related Content</span></span>](#RelatedContent)  
  
##  <a name="syntax-for-an-endpoint-url"></a><a name="SyntaxOfURL"></a> <span data-ttu-id="08f90-112">端點 URL 的語法</span><span class="sxs-lookup"><span data-stu-id="08f90-112">Syntax for an Endpoint URL</span></span>  
 <span data-ttu-id="08f90-113">端點 URL 的語法採用以下格式：</span><span class="sxs-lookup"><span data-stu-id="08f90-113">The syntax for an endpoint URL is of the form:</span></span>  
  
 <span data-ttu-id="08f90-114">TCP<strong>://</strong> *\<system-address>* <strong>:</strong> *\<port>*</span><span class="sxs-lookup"><span data-stu-id="08f90-114">TCP<strong>://</strong>*\<system-address>*<strong>:</strong>*\<port>*</span></span>  
  
 <span data-ttu-id="08f90-115">其中</span><span class="sxs-lookup"><span data-stu-id="08f90-115">where</span></span>  
  
-   <span data-ttu-id="08f90-116">*\<system-address>* 是可明確識別目標電腦系統的字串。</span><span class="sxs-lookup"><span data-stu-id="08f90-116">*\<system-address>* is a string that unambiguously identifies the target computer system.</span></span> <span data-ttu-id="08f90-117">伺服器位址通常是系統名稱 (如果系統位於同一個網域內)、完整網域名稱或 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="08f90-117">Typically, the server address is a system name (if the systems are in the same domain), a fully qualified domain name, or an IP address:</span></span>  
  
    -   <span data-ttu-id="08f90-118">因為 Windows Server 容錯移轉叢集 (WSFC) 叢集的節點都是在相同網域中，您可以使用電腦系統的名稱，例如 `SYSTEM46`。</span><span class="sxs-lookup"><span data-stu-id="08f90-118">Because the nodes of Windows Server Failover Clustering (WSFC) cluster are the same domain, you can use the name of the computer system; for example, `SYSTEM46`.</span></span>  
  
    -   <span data-ttu-id="08f90-119">若要使用 IP 位址，則它在您的環境中必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="08f90-119">To use an IP address, it must be unique in your environment.</span></span> <span data-ttu-id="08f90-120">建議您只使用靜態的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="08f90-120">We recommend that you use an IP address only if it is static.</span></span> <span data-ttu-id="08f90-121">此 IP 位址可以是 IP 第 4 版 (IPv4) 或 IP 第 6 版 (IPv6)。</span><span class="sxs-lookup"><span data-stu-id="08f90-121">The IP address can be IP Version 4 (IPv4) or IP Version 6 (IPv6).</span></span> <span data-ttu-id="08f90-122">IPv6 位址必須使用方括弧括住，例如： **[** <IPv6 位址> **]** 。</span><span class="sxs-lookup"><span data-stu-id="08f90-122">An IPv6 address must be enclosed within square brackets, for example: **[**_<IPv6_address>_**]**.</span></span>  
  
         <span data-ttu-id="08f90-123">若要取得系統的 IP 位址，請在 Windows 命令提示字元下，輸入 **ipconfig** 命令。</span><span class="sxs-lookup"><span data-stu-id="08f90-123">To learn the IP address of a system, at the Windows command prompt, enter the **ipconfig** command.</span></span>  
  
    -   <span data-ttu-id="08f90-124">完整網域名稱保證可以運作。</span><span class="sxs-lookup"><span data-stu-id="08f90-124">The fully qualified domain name is guaranteed to work.</span></span> <span data-ttu-id="08f90-125">這是在不同位置會採用不同格式的本機定義位址字串。</span><span class="sxs-lookup"><span data-stu-id="08f90-125">This is a locally defined address string that takes different forms in different places.</span></span> <span data-ttu-id="08f90-126">完整網域名稱通常 (但不一定) 都是複合名稱，包含電腦名稱及一系列以句號分隔的網域區段，並採用下列格式：</span><span class="sxs-lookup"><span data-stu-id="08f90-126">Often, but not always, a fully qualified domain name is a compound name that includes the computer name and a series of period-separated domain segments of the form:</span></span>  
  
         <span data-ttu-id="08f90-127">_電腦名稱_ **.**</span><span class="sxs-lookup"><span data-stu-id="08f90-127">_computer_name_ **.**</span></span> <span data-ttu-id="08f90-128">_網域區段_[... **.** _網域區段_]</span><span class="sxs-lookup"><span data-stu-id="08f90-128">_domain_segment_[...**.**_domain_segment_]</span></span>  
  
         <span data-ttu-id="08f90-129">其中 *電腦名稱*是執行伺服器執行個體之電腦的網路名稱，而 *網域區段*[... **.** _網域區段_] 則是伺服器的其餘網域資訊；例如： `localinfo.corp.Adventure-Works.com`。</span><span class="sxs-lookup"><span data-stu-id="08f90-129">where *computer_name i*s the network name of the computer running the server instance, and *domain_segment*[...**.**_domain_segment_] is the remaining domain information of the server; for example: `localinfo.corp.Adventure-Works.com`.</span></span>  
  
         <span data-ttu-id="08f90-130">網域區段的內容和數目是在公司或組織的內部決定的。</span><span class="sxs-lookup"><span data-stu-id="08f90-130">The content and number of domain segments are determined within the company or organization.</span></span> <span data-ttu-id="08f90-131">如需詳細資訊，請參閱本主題後面的＜ [尋找完整網域名稱](#Finding_FQDN)＞。</span><span class="sxs-lookup"><span data-stu-id="08f90-131">For more information, see [Finding the Fully Qualified Domain Name](#Finding_FQDN), later in this topic.</span></span>  
  
-   <span data-ttu-id="08f90-132">*\<port>* 是夥伴伺服器執行個體的鏡像端點所使用的連接埠號碼。</span><span class="sxs-lookup"><span data-stu-id="08f90-132">*\<port>* is the port number used by the mirroring endpoint of the partner server instance.</span></span>  
  
     <span data-ttu-id="08f90-133">資料庫鏡像端點可以使用電腦系統上任何可用的通訊埠。</span><span class="sxs-lookup"><span data-stu-id="08f90-133">A database mirroring endpoint can use any available port on the computer system.</span></span> <span data-ttu-id="08f90-134">每個通訊埠編號必須只與一個端點產生關聯，而且每個端點會與單一伺服器執行個體產生關聯，因此相同伺服器上的不同伺服器執行個體會在具有不同通訊埠的不同端點上接聽。</span><span class="sxs-lookup"><span data-stu-id="08f90-134">Each port number must be associated with only one endpoint, and each endpoint is associated with a single server instance; thus, different server instances on the same server listen on different endpoints with different ports.</span></span> <span data-ttu-id="08f90-135">因此，當您指定可用性複本時，在端點 URL 中指定的通訊埠，會永遠把內送訊息導向到端點與該通訊埠產生關聯的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="08f90-135">Therefore, the port you specify in the endpoint URL when you specify an availability replica will always direct incoming messages to the server instance whose endpoint is associated with that port.</span></span>  
  
     <span data-ttu-id="08f90-136">在端點 URL 中，只有通訊埠編號會識別與目標電腦上的鏡像端點相關聯的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="08f90-136">IIn the endpoint URL, only the number of the port identifies the server instance that is associated with the mirroring endpoint on the target computer.</span></span> <span data-ttu-id="08f90-137">下圖說明單一電腦上兩個伺服器執行個體的端點 URL。</span><span class="sxs-lookup"><span data-stu-id="08f90-137">The following figure illustrates the endpoint URLs of two server instances on a single computer.</span></span> <span data-ttu-id="08f90-138">預設的執行個體會使用通訊埠 `7022` ，而具名執行個體則使用通訊埠 `7033`。</span><span class="sxs-lookup"><span data-stu-id="08f90-138">The default instance uses port `7022` and the named instance uses port `7033`.</span></span> <span data-ttu-id="08f90-139">這兩個伺服器執行個體的端點 URL 分別為： `TCP://MYSYSTEM.Adventure-works.MyDomain.com:7022` 和 `TCP://MYSYSTEM.Adventure-works.MyDomain.com:7033`。</span><span class="sxs-lookup"><span data-stu-id="08f90-139">The endpoint URL for these two server instances are, respectively: `TCP://MYSYSTEM.Adventure-works.MyDomain.com:7022` and `TCP://MYSYSTEM.Adventure-works.MyDomain.com:7033`.</span></span> <span data-ttu-id="08f90-140">請注意，位址不包含伺服器執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="08f90-140">Note that the address does not contain the name of the server instance.</span></span>  
  
     <span data-ttu-id="08f90-141">![預設執行個體的伺服器網路位址](../../media/dbm-2-instances-ports-1-system.gif "預設執行個體的伺服器網路位址")</span><span class="sxs-lookup"><span data-stu-id="08f90-141">![Server network addresses of a default instance](../../media/dbm-2-instances-ports-1-system.gif "Server network addresses of a default instance")</span></span>  
  
     <span data-ttu-id="08f90-142">若要識別目前關聯於伺服器執行個體之資料庫鏡像端點的通訊埠，請使用下列 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 陳述式：</span><span class="sxs-lookup"><span data-stu-id="08f90-142">To identify the port currently associated with database mirroring endpoint of a server instance, use the following [!INCLUDE[tsql](../../../includes/tsql-md.md)] statement:</span></span>  
  
    ```sql
    SELECT type_desc, port FROM sys.TCP_endpoints  
    ```  
  
     <span data-ttu-id="08f90-143">尋找 **type_desc** 值是 "DATABASE_MIRRORING" 的資料列，並使用對應通訊埠編號。</span><span class="sxs-lookup"><span data-stu-id="08f90-143">Find the row whose **type_desc** value is "DATABASE_MIRRORING," and use the corresponding port number.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="08f90-144">範例</span><span class="sxs-lookup"><span data-stu-id="08f90-144">Examples</span></span>  
  
#### <a name="a-using-a-system-name"></a><span data-ttu-id="08f90-145">A.</span><span class="sxs-lookup"><span data-stu-id="08f90-145">A.</span></span> <span data-ttu-id="08f90-146">使用系統名稱</span><span class="sxs-lookup"><span data-stu-id="08f90-146">Using a system name</span></span>  
 <span data-ttu-id="08f90-147">下列端點 URL 會指定一個系統名稱 `SYSTEM46`和通訊埠 `7022`。</span><span class="sxs-lookup"><span data-stu-id="08f90-147">The following endpoint URL specifies a system name, `SYSTEM46`, and port `7022`.</span></span>  
  
 `TCP://SYSTEM46:7022`  
  
#### <a name="b-using-a-fully-qualified-domain-name"></a><span data-ttu-id="08f90-148">B.</span><span class="sxs-lookup"><span data-stu-id="08f90-148">B.</span></span> <span data-ttu-id="08f90-149">使用完整網域名稱</span><span class="sxs-lookup"><span data-stu-id="08f90-149">Using a fully qualified domain name</span></span>  
 <span data-ttu-id="08f90-150">下列端點 URL 會指定一個完整網域名稱 `DBSERVER8.manufacturing.Adventure-Works.com`和通訊埠 `7024`。</span><span class="sxs-lookup"><span data-stu-id="08f90-150">The following endpoint URL specifies a fully qualified domain name, `DBSERVER8.manufacturing.Adventure-Works.com`, and port `7024`.</span></span>  
  
 `TCP://DBSERVER8.manufacturing.Adventure-Works.com:7024`  
  
#### <a name="c-using-ipv4"></a><span data-ttu-id="08f90-151">C.</span><span class="sxs-lookup"><span data-stu-id="08f90-151">C.</span></span> <span data-ttu-id="08f90-152">使用 IPv4</span><span class="sxs-lookup"><span data-stu-id="08f90-152">Using IPv4</span></span>  
 <span data-ttu-id="08f90-153">下列端點 URL 會指定一個 IPv4 位址 `10.193.9.134`和通訊埠 `7023`。</span><span class="sxs-lookup"><span data-stu-id="08f90-153">The following endpoint URL specifies an IPv4 address, `10.193.9.134`, and port `7023`.</span></span>  
  
 `TCP://10.193.9.134:7023`  
  
#### <a name="d-using-ipv6"></a><span data-ttu-id="08f90-154">D.</span><span class="sxs-lookup"><span data-stu-id="08f90-154">D.</span></span> <span data-ttu-id="08f90-155">使用 IPv6</span><span class="sxs-lookup"><span data-stu-id="08f90-155">Using IPv6</span></span>  
 <span data-ttu-id="08f90-156">下列端點 URL 會包含一個 IPv6 位址 `2001:4898:23:1002:20f:1fff:feff:b3a3`和通訊埠 `7022`。</span><span class="sxs-lookup"><span data-stu-id="08f90-156">The following endpoint URL contains an IPv6 address, `2001:4898:23:1002:20f:1fff:feff:b3a3`, and port `7022`.</span></span>  
  
 `TCP://[2001:4898:23:1002:20f:1fff:feff:b3a3]:7022`  
  
##  <a name="finding-the-fully-qualified-domain-name-of-a-system"></a><a name="Finding_FQDN"></a> <span data-ttu-id="08f90-157">尋找系統的完整網域名稱</span><span class="sxs-lookup"><span data-stu-id="08f90-157">Finding the Fully Qualified Domain Name of A System</span></span>  
 <span data-ttu-id="08f90-158">若要尋找系統的完整網域名稱，請在該系統的 Windows 命令提示字元下，輸入：</span><span class="sxs-lookup"><span data-stu-id="08f90-158">To find the fully qualified domain name of a system, at the Windows command prompt on that system, enter:</span></span>  
  
 <span data-ttu-id="08f90-159">**IPCONFIG /ALL**</span><span class="sxs-lookup"><span data-stu-id="08f90-159">**IPCONFIG /ALL**</span></span>  
  
 <span data-ttu-id="08f90-160">若要形成完整的網域名稱，請串連 <主機名稱> 和 <主要 DNS 尾碼> 的值，如下所示：</span><span class="sxs-lookup"><span data-stu-id="08f90-160">To form the fully qualified domain name, concatenate the values of *<host_name>* and *<Primary_Dns_Suffix>* as follows:</span></span>  
  
 <span data-ttu-id="08f90-161">_<主機名稱>_ **.**</span><span class="sxs-lookup"><span data-stu-id="08f90-161">_<host_name>_ **.**</span></span> <span data-ttu-id="08f90-162">_<主要 DNS 尾碼>_</span><span class="sxs-lookup"><span data-stu-id="08f90-162">_<Primary_Dns_Suffix>_</span></span>  
  
 <span data-ttu-id="08f90-163">例如，IP 組態</span><span class="sxs-lookup"><span data-stu-id="08f90-163">For example, the IP configuration</span></span>  
  
 `Host Name  .  .  .  .  .  .  : MYSERVER`  
  
 `Primary Dns Suffix  .  .  .  : mydomain.Adventure-Works.com`  
  
 <span data-ttu-id="08f90-164">等於下列完整的網域名稱：</span><span class="sxs-lookup"><span data-stu-id="08f90-164">equates to the following fully qualified domain name:</span></span>  
  
 `MYSERVER.mydomain.Adventure-Works.com`  
  
> [!NOTE]  
>  <span data-ttu-id="08f90-165">如果您需要有關完整網域名稱的詳細資訊，請洽詢您的系統管理員。</span><span class="sxs-lookup"><span data-stu-id="08f90-165">If you need more information about a fully qualified domain name, see your system administrator.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="08f90-166">相關工作</span><span class="sxs-lookup"><span data-stu-id="08f90-166">Related Tasks</span></span>  
 <span data-ttu-id="08f90-167">**若要設定資料庫鏡像端點**</span><span class="sxs-lookup"><span data-stu-id="08f90-167">**To Configure a Database Mirroring Endpoint**</span></span>  
  
-   [<span data-ttu-id="08f90-168">建立 AlwaysOn 可用性群組 &#40;SQL Server PowerShell 的資料庫鏡像端點&#41;</span><span class="sxs-lookup"><span data-stu-id="08f90-168">Create a Database Mirroring Endpoint for AlwaysOn Availability Groups &#40;SQL Server PowerShell&#41;</span></span>](database-mirroring-always-on-availability-groups-powershell.md)  
  
-   [<span data-ttu-id="08f90-169">建立 Windows 驗證的資料庫鏡像端點 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="08f90-169">Create a Database Mirroring Endpoint for Windows Authentication &#40;Transact-SQL&#41;</span></span>](../../database-mirroring/create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)  
  
-   [<span data-ttu-id="08f90-170">使用資料庫鏡像端點憑證 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="08f90-170">Use Certificates for a Database Mirroring Endpoint &#40;Transact-SQL&#41;</span></span>](../../database-mirroring/use-certificates-for-a-database-mirroring-endpoint-transact-sql.md)  
  
    -   [<span data-ttu-id="08f90-171">允許資料庫鏡像端點使用輸出連線的憑證 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="08f90-171">Allow a Database Mirroring Endpoint to Use Certificates for Outbound Connections &#40;Transact-SQL&#41;</span></span>](../../database-mirroring/database-mirroring-use-certificates-for-outbound-connections.md)  
  
    -   [<span data-ttu-id="08f90-172">允許資料庫鏡像端點使用輸入連線的憑證 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="08f90-172">Allow a Database Mirroring Endpoint to Use Certificates for Inbound Connections &#40;Transact-SQL&#41;</span></span>](../../database-mirroring/database-mirroring-use-certificates-for-inbound-connections.md)  
  
-   [<span data-ttu-id="08f90-173">指定伺服器網路位址 &#40;資料庫鏡像&#41;</span><span class="sxs-lookup"><span data-stu-id="08f90-173">Specify a Server Network Address &#40;Database Mirroring&#41;</span></span>](../../database-mirroring/specify-a-server-network-address-database-mirroring.md)  
  
-   [<span data-ttu-id="08f90-174">針對 AlwaysOn 可用性群組 Configuration &#40;SQL Server&#41;已刪除進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="08f90-174">Troubleshoot AlwaysOn Availability Groups Configuration &#40;SQL Server&#41;deleted</span></span>](troubleshoot-always-on-availability-groups-configuration-sql-server.md)  
  
 <span data-ttu-id="08f90-175">**若要檢視有關資料庫鏡像端點的資訊**</span><span class="sxs-lookup"><span data-stu-id="08f90-175">**To View Information About the Database Mirroring Endpoint**</span></span>  
  
-   [<span data-ttu-id="08f90-176">sys.database_mirroring_endpoints &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="08f90-176">sys.database_mirroring_endpoints &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql)  
  
 <span data-ttu-id="08f90-177">**若要加入可用性複本**</span><span class="sxs-lookup"><span data-stu-id="08f90-177">**To add an availability replica**</span></span>  
  
-   [<span data-ttu-id="08f90-178">將次要複本加入至可用性群組 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="08f90-178">Add a Secondary Replica to an Availability Group &#40;SQL Server&#41;</span></span>](add-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="08f90-179">將次要複本聯結至可用性群組 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="08f90-179">Join a Secondary Replica to an Availability Group &#40;SQL Server&#41;</span></span>](join-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="08f90-180">相關內容</span><span class="sxs-lookup"><span data-stu-id="08f90-180">Related Content</span></span>  
  
-   [<span data-ttu-id="08f90-181">Microsoft SQL Server AlwaysOn 高可用性和災害復原方案指南</span><span class="sxs-lookup"><span data-stu-id="08f90-181">Microsoft SQL Server AlwaysOn Solutions Guide for High Availability and Disaster Recovery</span></span>](https://go.microsoft.com/fwlink/?LinkId=227600)  
  
## <a name="see-also"></a><span data-ttu-id="08f90-182">另請參閱</span><span class="sxs-lookup"><span data-stu-id="08f90-182">See Also</span></span>  
 <span data-ttu-id="08f90-183">[建立及設定可用性群組 &#40;SQL Server&#41;](creation-and-configuration-of-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="08f90-183">[Creation and Configuration of Availability Groups &#40;SQL Server&#41;](creation-and-configuration-of-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="08f90-184">[AlwaysOn 可用性群組 &#40;SQL Server 的總覽&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="08f90-184">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="08f90-185">CREATE ENDPOINT &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="08f90-185">CREATE ENDPOINT &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-endpoint-transact-sql)  
