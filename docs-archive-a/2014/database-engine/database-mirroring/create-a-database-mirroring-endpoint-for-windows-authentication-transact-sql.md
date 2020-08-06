---
title: 建立 Windows 驗證的資料庫鏡像端點 (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- database mirroring [SQL Server], deployment
- database mirroring [SQL Server], endpoint
- endpoints [SQL Server], database mirroring
- Windows authentication [SQL Server]
- database mirroring [SQL Server], security
ms.assetid: baf1a4b1-6790-4275-b261-490bca33bdb9
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 5558bc5684f2eb9053c935543db0c05d6225daf7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593576"
---
# <a name="create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql"></a><span data-ttu-id="85052-102">建立 Windows 驗證的資料庫鏡像端點 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="85052-102">Create a Database Mirroring Endpoint for Windows Authentication (Transact-SQL)</span></span>
  <span data-ttu-id="85052-103">此主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中建立使用 Windows 驗證的資料庫鏡像端點。</span><span class="sxs-lookup"><span data-stu-id="85052-103">This topic describes how to create a database mirroring endpoint that uses Windows Authentication in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="85052-104">若要支援資料庫鏡像或 [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] ， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的每個執行個體都需要一個資料庫鏡像端點。</span><span class="sxs-lookup"><span data-stu-id="85052-104">To support database mirroring or [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] each instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] requires a database mirroring endpoint.</span></span> <span data-ttu-id="85052-105">伺服器執行個體只可有一個資料庫鏡像端點，而這個端點具有單一通訊埠。</span><span class="sxs-lookup"><span data-stu-id="85052-105">A server instance can have only one database mirroring endpoint, which has a single port.</span></span> <span data-ttu-id="85052-106">建立資料庫鏡像端點後，該資料庫鏡像端點即可使用本機系統上的任何可用通訊埠。</span><span class="sxs-lookup"><span data-stu-id="85052-106">A database mirroring endpoint can use any port that is available on the local system when the endpoint is created.</span></span> <span data-ttu-id="85052-107">伺服器執行個體上的所有資料庫鏡像工作階段都會接聽該通訊埠，且資料庫鏡像的所有內送連接也都會使用該通訊埠。</span><span class="sxs-lookup"><span data-stu-id="85052-107">All database mirroring sessions on a server instance listen on that port, and all incoming connections for database mirroring use that port.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="85052-108">若資料庫鏡像端點存在且已在使用中，我們建議您使用該端點。</span><span class="sxs-lookup"><span data-stu-id="85052-108">If a database mirroring endpoint exists and is already in use, we recommend that you use that endpoint.</span></span> <span data-ttu-id="85052-109">卸除使用中端點會中斷現有工作階段。</span><span class="sxs-lookup"><span data-stu-id="85052-109">Dropping an in-use endpoint disrupts existing sessions.</span></span>  
  
 <span data-ttu-id="85052-110">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="85052-110">**In This Topic**</span></span>  
  
-   <span data-ttu-id="85052-111">**開始之前：** [安全性](#Security)</span><span class="sxs-lookup"><span data-stu-id="85052-111">**Before you begin:**  [Security](#Security)</span></span>  
  
-   <span data-ttu-id="85052-112">**使用下列項目建立資料庫鏡像端點：** [Transact-SQL](#TsqlProcedure)</span><span class="sxs-lookup"><span data-stu-id="85052-112">**To create a database mirroring endpoint, using:**  [Transact-SQL](#TsqlProcedure)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="85052-113">開始之前</span><span class="sxs-lookup"><span data-stu-id="85052-113">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="85052-114">Security</span><span class="sxs-lookup"><span data-stu-id="85052-114">Security</span></span>  
 <span data-ttu-id="85052-115">伺服器執行個體的驗證及加密方法是由系統管理員所建立。</span><span class="sxs-lookup"><span data-stu-id="85052-115">The authentication and encryption methods of the server instance are established by the system administrator.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="85052-116">RC4 演算法已被取代。</span><span class="sxs-lookup"><span data-stu-id="85052-116">The RC4 algorithm is deprecated.</span></span> [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="85052-117">我們建議您改用 AES。</span><span class="sxs-lookup"><span data-stu-id="85052-117">We recommend that you use AES.</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="85052-118">權限</span><span class="sxs-lookup"><span data-stu-id="85052-118">Permissions</span></span>  
 <span data-ttu-id="85052-119">需要 CREATE ENDPOINT 權限或系統管理員 (sysadmin) 固定伺服器角色的成員資格。</span><span class="sxs-lookup"><span data-stu-id="85052-119">Requires CREATE ENDPOINT permission, or membership in the sysadmin fixed server role.</span></span> <span data-ttu-id="85052-120">如需詳細資訊，請參閱 [GRANT 端點權限 &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-endpoint-permissions-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="85052-120">For more information, see [GRANT Endpoint Permissions &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-endpoint-permissions-transact-sql).</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="85052-121">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="85052-121">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-database-mirroring-endpoint-that-uses-windows-authentication"></a><span data-ttu-id="85052-122">建立使用 Windows 驗證的資料庫鏡像端點</span><span class="sxs-lookup"><span data-stu-id="85052-122">To Create a Database Mirroring Endpoint That Uses Windows Authentication</span></span>  
  
1.  <span data-ttu-id="85052-123">連結至您要建立資料庫鏡像端點的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="85052-123">Connect to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on which you want to create a database mirroring endpoint.</span></span>  
  
2.  <span data-ttu-id="85052-124">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="85052-124">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="85052-125">使用下列陳述式決定資料庫鏡像端點是否已經存在。</span><span class="sxs-lookup"><span data-stu-id="85052-125">Determine if a database mirroring endpoint already exists by using the following statement:</span></span>  
  
    ```sql
    SELECT name, role_desc, state_desc FROM sys.database_mirroring_endpoints;
    ```  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="85052-126">如果伺服器執行個體已經有資料庫鏡像端點，則在您於伺服器執行個體上建立的其他任何工作階段，都會使用該端點。</span><span class="sxs-lookup"><span data-stu-id="85052-126">If a database mirroring endpoint already exists for the server instance, use that endpoint for any other sessions you establish on the server instance.</span></span>  
  
4.  <span data-ttu-id="85052-127">若要以 Transact-SQL 來建立使用 Windows 驗證的端點，請使用 CREATE ENDPOINT 陳述式。</span><span class="sxs-lookup"><span data-stu-id="85052-127">To use Transact-SQL to create an endpoint to use with Windows Authentication, use a CREATE ENDPOINT statement.</span></span> <span data-ttu-id="85052-128">陳述式會採用下列一般形式：</span><span class="sxs-lookup"><span data-stu-id="85052-128">The statement takes the following general form:</span></span>  
  
     <span data-ttu-id="85052-129">CREATE ENDPOINT *\<endpointName>*</span><span class="sxs-lookup"><span data-stu-id="85052-129">CREATE ENDPOINT *\<endpointName>*</span></span>  
  
     <span data-ttu-id="85052-130">STATE=STARTED</span><span class="sxs-lookup"><span data-stu-id="85052-130">STATE=STARTED</span></span>  
  
     <span data-ttu-id="85052-131">AS TCP (LISTENER_PORT = *\<listenerPortList>* )</span><span class="sxs-lookup"><span data-stu-id="85052-131">AS TCP ( LISTENER_PORT = *\<listenerPortList>* )</span></span>  
  
     <span data-ttu-id="85052-132">FOR DATABASE_MIRRORING</span><span class="sxs-lookup"><span data-stu-id="85052-132">FOR DATABASE_MIRRORING</span></span>  
  
     <span data-ttu-id="85052-133">(</span><span class="sxs-lookup"><span data-stu-id="85052-133">(</span></span>  
  
     <span data-ttu-id="85052-134">[AUTHENTICATION = **WINDOWS** [ *\<authorizationMethod>* ]</span><span class="sxs-lookup"><span data-stu-id="85052-134">[ AUTHENTICATION = **WINDOWS** [ *\<authorizationMethod>* ]</span></span>  
  
     <span data-ttu-id="85052-135">]</span><span class="sxs-lookup"><span data-stu-id="85052-135">]</span></span>  
  
     <span data-ttu-id="85052-136">[ [ **,** ] ENCRYPTION = **REQUIRED**</span><span class="sxs-lookup"><span data-stu-id="85052-136">[ [**,**] ENCRYPTION = **REQUIRED**</span></span>  
  
     <span data-ttu-id="85052-137">[ALGORITHM { *\<algorithm>* }]</span><span class="sxs-lookup"><span data-stu-id="85052-137">[ ALGORITHM { *\<algorithm>* } ]</span></span>  
  
     <span data-ttu-id="85052-138">]</span><span class="sxs-lookup"><span data-stu-id="85052-138">]</span></span>  
  
     <span data-ttu-id="85052-139">[ **,** ] ROLE = *\<role>*</span><span class="sxs-lookup"><span data-stu-id="85052-139">[**,**] ROLE = *\<role>*</span></span>  
  
     <span data-ttu-id="85052-140">)</span><span class="sxs-lookup"><span data-stu-id="85052-140">)</span></span>  
  
     <span data-ttu-id="85052-141">其中</span><span class="sxs-lookup"><span data-stu-id="85052-141">where</span></span>  
  
    -   <span data-ttu-id="85052-142">*\<endpointName>* 是伺服器執行個體的資料庫鏡像端點唯一名稱。</span><span class="sxs-lookup"><span data-stu-id="85052-142">*\<endpointName>* is a unique name for the database mirroring endpoint of the server instance.</span></span>  
  
    -   <span data-ttu-id="85052-143">STARTED 指定要啟動及要開始接聽連接的端點。</span><span class="sxs-lookup"><span data-stu-id="85052-143">STARTED specifies that the endpoint is to be started and to begin listening for connections.</span></span> <span data-ttu-id="85052-144">資料庫鏡像端點通常是在 STARTED 狀態下建立。</span><span class="sxs-lookup"><span data-stu-id="85052-144">A database mirroring endpoint typically is created in the STARTED state.</span></span> <span data-ttu-id="85052-145">您也可以在 STOPPED 狀態 (預設值) 或 DISABLED 狀態下啟動工作階段。</span><span class="sxs-lookup"><span data-stu-id="85052-145">Alternatively, you can start a session in a STOPPED state (the default) or DISABLED state.</span></span>  
  
    -   <span data-ttu-id="85052-146">*\<listenerPortList>* 是想要伺服器用來接聽資料庫鏡像訊息的單一連接埠號碼 (*nnnn*)。</span><span class="sxs-lookup"><span data-stu-id="85052-146">*\<listenerPortList>* is a single port number (*nnnn*) on which you want the server to listen for database mirroring messages.</span></span> <span data-ttu-id="85052-147">只允許 TCP；指定任何其他通訊協定將造成錯誤。</span><span class="sxs-lookup"><span data-stu-id="85052-147">Only TCP is allowed; specifying any other protocol causes an error.</span></span>  
  
         <span data-ttu-id="85052-148">每個電腦系統僅能使用某個通訊埠編號一次。</span><span class="sxs-lookup"><span data-stu-id="85052-148">A port number can be used only once per computer system.</span></span> <span data-ttu-id="85052-149">建立資料庫鏡像端點後，該資料庫鏡像端點即可使用本機系統上的任何可用通訊埠。</span><span class="sxs-lookup"><span data-stu-id="85052-149">A database mirroring endpoint can use any port that is available on the local system when the endpoint is created.</span></span> <span data-ttu-id="85052-150">若要識別系統上 TCP 端點目前使用的通訊埠，請使用下列 Transact-SQL 陳述式：</span><span class="sxs-lookup"><span data-stu-id="85052-150">To identify the ports currently being used by TCP endpoints on the system, use the following Transact-SQL statement:</span></span>  
  
        ```  
        SELECT name, port FROM sys.tcp_endpoints;  
        ```  
  
        > [!IMPORTANT]  
        >  <span data-ttu-id="85052-151">每個伺服器執行個體都需要一個且唯一的接聽程式通訊埠。</span><span class="sxs-lookup"><span data-stu-id="85052-151">Each server instance requires one and only one unique listener port.</span></span>  
  
    -   <span data-ttu-id="85052-152">若為 Windows 驗證，除非您想要端點只使用 NTLM 或 Kerberos 來驗證連接，否則 AUTHENTICATION 是選擇性選項。</span><span class="sxs-lookup"><span data-stu-id="85052-152">For Windows Authentication, the AUTHENTICATION option is optional, unless you want the endpoint to use only NTLM or Kerberos to authenticate connections.</span></span> <span data-ttu-id="85052-153">*\<authorizationMethod>* 會指定下列任一方法以用於驗證連線：NTLM、KERBEROS 或 NEGOTIATE。</span><span class="sxs-lookup"><span data-stu-id="85052-153">*\<authorizationMethod>* specifies the method used to authenticate connections as one of the following: NTLM, KERBEROS, or NEGOTIATE.</span></span> <span data-ttu-id="85052-154">預設值 NEGOTIATE，將導致端點使用 Windows 交涉通訊協定來選擇 NTLM 或 Kerberos。</span><span class="sxs-lookup"><span data-stu-id="85052-154">The default, NEGOTIATE, causes the endpoint to use the Windows negotiation protocol to choose either NTLM or Kerberos.</span></span> <span data-ttu-id="85052-155">視相對端點的驗證層級而定，交涉可讓連接需要或不需要驗證。</span><span class="sxs-lookup"><span data-stu-id="85052-155">Negotiation enables connections with or without authentication, depending on the authentication level of the opposite endpoint.</span></span>  
  
    -   <span data-ttu-id="85052-156">依預設，ENCRYPTION 是設定為 REQUIRED。</span><span class="sxs-lookup"><span data-stu-id="85052-156">ENCRYPTION is set to REQUIRED by default.</span></span> <span data-ttu-id="85052-157">這表示此端點的所有連接都必須使用加密。</span><span class="sxs-lookup"><span data-stu-id="85052-157">This means that all connections to this endpoint must use encryption.</span></span> <span data-ttu-id="85052-158">不過，您可以停用加密或使其在端點上為選擇性的。</span><span class="sxs-lookup"><span data-stu-id="85052-158">However, you can disable encryption or make it optional on an endpoint.</span></span> <span data-ttu-id="85052-159">替代方案如下所示：</span><span class="sxs-lookup"><span data-stu-id="85052-159">The alternatives are as follows:</span></span>  
  
        |<span data-ttu-id="85052-160">值</span><span class="sxs-lookup"><span data-stu-id="85052-160">Value</span></span>|<span data-ttu-id="85052-161">定義</span><span class="sxs-lookup"><span data-stu-id="85052-161">Definition</span></span>|  
        |-----------|----------------|  
        |<span data-ttu-id="85052-162">DISABLED</span><span class="sxs-lookup"><span data-stu-id="85052-162">DISABLED</span></span>|<span data-ttu-id="85052-163">指定透過連接傳送的資料不加密。</span><span class="sxs-lookup"><span data-stu-id="85052-163">Specifies that data sent over a connection is not encrypted.</span></span>|  
        |<span data-ttu-id="85052-164">SUPPORTED</span><span class="sxs-lookup"><span data-stu-id="85052-164">SUPPORTED</span></span>|<span data-ttu-id="85052-165">指定只有在相對端點指定為 SUPPORTED 或 REQUIRED 時才加密資料。</span><span class="sxs-lookup"><span data-stu-id="85052-165">Specifies that the data is encrypted only if the opposite endpoint specifies either SUPPORTED or REQUIRED.</span></span>|  
        |<span data-ttu-id="85052-166">REQUIRED</span><span class="sxs-lookup"><span data-stu-id="85052-166">REQUIRED</span></span>|<span data-ttu-id="85052-167">指定透過連接所傳送的資料必須加密。</span><span class="sxs-lookup"><span data-stu-id="85052-167">Specifies that data sent over a connection must be encrypted.</span></span>|  
  
         <span data-ttu-id="85052-168">如果端點需要加密，其他的端點必須將 ENCRYPTION 設定為 SUPPORTED 或 REQUIRED。</span><span class="sxs-lookup"><span data-stu-id="85052-168">If an endpoint requires encryption, the other endpoint must have ENCRYPTION set to either SUPPORTED or REQUIRED.</span></span>  
  
    -   <span data-ttu-id="85052-169">*\<algorithm>* 提供用於指定端點加密標準的選項。</span><span class="sxs-lookup"><span data-stu-id="85052-169">*\<algorithm>* provides the option of specifying the encryption standards for the endpoint.</span></span> <span data-ttu-id="85052-170">*\<algorithm>* 值可為下列任一演算法或演算法的組合：RC4、AES、AES RC4 或 RC4 AES。</span><span class="sxs-lookup"><span data-stu-id="85052-170">The value of *\<algorithm>* can be one following algorithms or combinations of algorithms: RC4, AES, AES RC4, or RC4 AES.</span></span>  
  
         <span data-ttu-id="85052-171">AES RC4 指定此端點將交涉加密演算法，將優先權指定給 AES 演算法。</span><span class="sxs-lookup"><span data-stu-id="85052-171">AES RC4 specifies that this endpoint will negotiate for the encryption algorithm, giving preference to the AES algorithm.</span></span> <span data-ttu-id="85052-172">RC4 AES 指定此端點將交涉加密演算法，將優先權指定給 RC4 演算法。</span><span class="sxs-lookup"><span data-stu-id="85052-172">RC4 AES specifies that this endpoint will negotiate for the encryption algorithm, giving preference to the RC4 algorithm.</span></span> <span data-ttu-id="85052-173">如果這兩個端點都指定了這兩種演算法 (但指定順序不同)，則以接受連接的端點為準。</span><span class="sxs-lookup"><span data-stu-id="85052-173">If both endpoints specify both algorithms but in different orders, the endpoint accepting the connection wins.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="85052-174">RC4 演算法已被取代。</span><span class="sxs-lookup"><span data-stu-id="85052-174">The RC4 algorithm is deprecated.</span></span> [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="85052-175">我們建議您改用 AES。</span><span class="sxs-lookup"><span data-stu-id="85052-175">We recommend that you use AES.</span></span>  
  
    -   <span data-ttu-id="85052-176">*\<role>* 定義伺服器可執行的一或多個角色。</span><span class="sxs-lookup"><span data-stu-id="85052-176">*\<role>* defines the role or roles that the server can perform.</span></span> <span data-ttu-id="85052-177">指定所需的 ROLE。</span><span class="sxs-lookup"><span data-stu-id="85052-177">Specifying ROLE is required.</span></span> <span data-ttu-id="85052-178">然而，端點的角色只與資料庫鏡像有關。</span><span class="sxs-lookup"><span data-stu-id="85052-178">However, the role of the endpoint is relevant only for database mirroring.</span></span> <span data-ttu-id="85052-179">對於 [!INCLUDE[ssHADR](../../includes/sshadr-md.md)]，端點的角色會被忽略。</span><span class="sxs-lookup"><span data-stu-id="85052-179">For [!INCLUDE[ssHADR](../../includes/sshadr-md.md)], the role of the endpoint is ignored.</span></span>  
  
         <span data-ttu-id="85052-180">若要允許伺服器執行個體做為一個資料庫鏡像工作階段的一個角色，並做為另一個工作階段的其他角色，請指定 ROLE=ALL。</span><span class="sxs-lookup"><span data-stu-id="85052-180">To allow a server instance to serve as one role for one database mirroring session and different role for another session, specify ROLE=ALL.</span></span> <span data-ttu-id="85052-181">若要限制伺服器執行個體做為夥伴或見證伺服器，請分別指定 ROLE=PARTNER 或 ROLE=WITNESS。</span><span class="sxs-lookup"><span data-stu-id="85052-181">To restrict a server instance to being either a partner or a witness, specify ROLE=PARTNER or ROLE=WITNESS, respectively.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="85052-182">如需不同版本之資料庫鏡像選項的詳細資訊 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，請參閱[SQL Server 2014 版本所支援的功能](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)。</span><span class="sxs-lookup"><span data-stu-id="85052-182">For more information about Database Mirroring options for different editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
     <span data-ttu-id="85052-183">如需 CREATE ENDPOINT 語法的完整說明，請參閱 [CREATE ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-endpoint-transact-sql)中建立使用 Windows 驗證的資料庫鏡像端點。</span><span class="sxs-lookup"><span data-stu-id="85052-183">For a complete description of the CREATE ENDPOINT syntax, see [CREATE ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-endpoint-transact-sql).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="85052-184">若要變更現有的端點，請使用 [ALTER ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-endpoint-transact-sql)中建立使用 Windows 驗證的資料庫鏡像端點。</span><span class="sxs-lookup"><span data-stu-id="85052-184">To change an existing endpoint, use [ALTER ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-endpoint-transact-sql).</span></span>  
  
###  <a name="example-creating-endpoints-to-support-for-database-mirroring-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="85052-185">範例：建立端點以支援資料庫鏡像 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="85052-185">Example: Creating Endpoints to Support for Database Mirroring (Transact-SQL)</span></span>  
 <span data-ttu-id="85052-186">下列範例會在三部不同的電腦系統上建立預設伺服器執行個體的資料庫鏡像端點：</span><span class="sxs-lookup"><span data-stu-id="85052-186">The following example creates database mirroring endpoints for the default server instances on three separate computer systems:</span></span>  
  
|<span data-ttu-id="85052-187">伺服器執行個體的角色</span><span class="sxs-lookup"><span data-stu-id="85052-187">Role of server instance</span></span>|<span data-ttu-id="85052-188">主機電腦的名稱</span><span class="sxs-lookup"><span data-stu-id="85052-188">Name of host computer</span></span>|  
|-----------------------------|---------------------------|  
|<span data-ttu-id="85052-189">夥伴 (一開始為主體角色)</span><span class="sxs-lookup"><span data-stu-id="85052-189">Partner (initially in the principal role)</span></span>|`SQLHOST01\.`|  
|<span data-ttu-id="85052-190">夥伴 (一開始為鏡像角色)</span><span class="sxs-lookup"><span data-stu-id="85052-190">Partner (initially in the mirror role)</span></span>|`SQLHOST02\.`|  
|<span data-ttu-id="85052-191">見證</span><span class="sxs-lookup"><span data-stu-id="85052-191">Witness</span></span>|`SQLHOST03\.`|  
  
 <span data-ttu-id="85052-192">在此範例中，雖然任何可用的通訊埠編號都可以使用，不過三個終止點都會使用通訊埠編號 7022。</span><span class="sxs-lookup"><span data-stu-id="85052-192">In this example, all three endpoints use port number 7022, though any available port number would work.</span></span> <span data-ttu-id="85052-193">AUTHENTICATION 選項是不必要的，因為終止點會使用預設類型「Windows 驗證」。</span><span class="sxs-lookup"><span data-stu-id="85052-193">The AUTHENTICATION option is unnecessary, because the endpoints use the default type, Windows Authentication.</span></span> <span data-ttu-id="85052-194">ENCRYPTION 選項也沒有必要，因為終止點隨時會交涉連線的驗證方法，這是「Windows 驗證」的預設行為。</span><span class="sxs-lookup"><span data-stu-id="85052-194">The ENCRYPTION option is also unnecessary, because the endpoints are all intended to negotiate the authentication method for a connection, which is the default behavior for Windows Authentication.</span></span> <span data-ttu-id="85052-195">另外，所有終止點都需要加密，這也是預設行為。</span><span class="sxs-lookup"><span data-stu-id="85052-195">Also, all of the endpoints require the encryption, which is the default behavior.</span></span>  
  
 <span data-ttu-id="85052-196">每個伺服器執行個體都限制為擔任夥伴或見證，每個伺服器的終止點都會明確地指定其角色 (ROLE=PARTNER 或 ROLE=WITNESS)。</span><span class="sxs-lookup"><span data-stu-id="85052-196">Each server instance is limited to serving as either a partner or a witness, and the endpoint of each server expressly specifies which role (ROLE=PARTNER or ROLE=WITNESS).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="85052-197">每個伺服器執行個體都僅能有一個終止點。</span><span class="sxs-lookup"><span data-stu-id="85052-197">Each server instance can have only one endpoint.</span></span> <span data-ttu-id="85052-198">因此，如果您要伺服器執行個體成為某些工作階段中的夥伴，而其他的為見證，請指定 ROLE=ALL。</span><span class="sxs-lookup"><span data-stu-id="85052-198">Therefore, if you want a server instance to be a partner in some sessions and the witness in others, specify ROLE=ALL.</span></span>  
  
```sql
--Endpoint for initial principal server instance, which  
--is the only server instance running on SQLHOST01.  
CREATE ENDPOINT endpoint_mirroring  
    STATE = STARTED  
    AS TCP ( LISTENER_PORT = 7022 )  
    FOR DATABASE_MIRRORING (ROLE=PARTNER);  
GO  
--Endpoint for initial mirror server instance, which  
--is the only server instance running on SQLHOST02.  
CREATE ENDPOINT endpoint_mirroring  
    STATE = STARTED  
    AS TCP ( LISTENER_PORT = 7022 )  
    FOR DATABASE_MIRRORING (ROLE=PARTNER);  
GO  
--Endpoint for witness server instance, which  
--is the only server instance running on SQLHOST03.  
CREATE ENDPOINT endpoint_mirroring  
    STATE = STARTED  
    AS TCP ( LISTENER_PORT = 7022 )  
    FOR DATABASE_MIRRORING (ROLE=WITNESS);  
GO  
```  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="85052-199">相關工作</span><span class="sxs-lookup"><span data-stu-id="85052-199">Related Tasks</span></span>  

### <a name="to-configure-a-database-mirroring-endpoint"></a><span data-ttu-id="85052-200">若要設定資料庫鏡像端點</span><span class="sxs-lookup"><span data-stu-id="85052-200">To Configure a Database Mirroring Endpoint</span></span>
  
-   [<span data-ttu-id="85052-201">建立 AlwaysOn 可用性群組 &#40;SQL Server PowerShell 的資料庫鏡像端點&#41;</span><span class="sxs-lookup"><span data-stu-id="85052-201">Create a Database Mirroring Endpoint for AlwaysOn Availability Groups &#40;SQL Server PowerShell&#41;</span></span>](../availability-groups/windows/database-mirroring-always-on-availability-groups-powershell.md)  
  
-   [<span data-ttu-id="85052-202">使用資料庫鏡像端點憑證 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="85052-202">Use Certificates for a Database Mirroring Endpoint &#40;Transact-SQL&#41;</span></span>](use-certificates-for-a-database-mirroring-endpoint-transact-sql.md)  
  
    -   [<span data-ttu-id="85052-203">允許資料庫鏡像端點使用輸出連線的憑證 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="85052-203">Allow a Database Mirroring Endpoint to Use Certificates for Outbound Connections &#40;Transact-SQL&#41;</span></span>](database-mirroring-use-certificates-for-outbound-connections.md)  
  
    -   [<span data-ttu-id="85052-204">允許資料庫鏡像端點使用輸入連線的憑證 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="85052-204">Allow a Database Mirroring Endpoint to Use Certificates for Inbound Connections &#40;Transact-SQL&#41;</span></span>](database-mirroring-use-certificates-for-inbound-connections.md)  
  
-   [<span data-ttu-id="85052-205">指定伺服器網路位址 &#40;資料庫鏡像&#41;</span><span class="sxs-lookup"><span data-stu-id="85052-205">Specify a Server Network Address &#40;Database Mirroring&#41;</span></span>](specify-a-server-network-address-database-mirroring.md)  
  
-   [<span data-ttu-id="85052-206">在新增或修改可用性複本時指定端點 URL &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="85052-206">Specify the Endpoint URL When Adding or Modifying an Availability Replica &#40;SQL Server&#41;</span></span>](../availability-groups/windows/specify-endpoint-url-adding-or-modifying-availability-replica.md)  
  
 <span data-ttu-id="85052-207">**若要檢視有關資料庫鏡像端點的資訊**</span><span class="sxs-lookup"><span data-stu-id="85052-207">**To View Information About the Database Mirroring Endpoint**</span></span>  
  
-   [<span data-ttu-id="85052-208">sys.database_mirroring_endpoints &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="85052-208">sys.database_mirroring_endpoints &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql)  
  
## <a name="see-also"></a><span data-ttu-id="85052-209">另請參閱</span><span class="sxs-lookup"><span data-stu-id="85052-209">See Also</span></span>  
 <span data-ttu-id="85052-210">[ALTER ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-endpoint-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="85052-210">[ALTER ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-endpoint-transact-sql) </span></span>  
 <span data-ttu-id="85052-211">[選擇加密演算法](../../relational-databases/security/encryption/choose-an-encryption-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="85052-211">[Choose an Encryption Algorithm](../../relational-databases/security/encryption/choose-an-encryption-algorithm.md) </span></span>  
 <span data-ttu-id="85052-212">[CREATE ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-endpoint-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="85052-212">[CREATE ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-endpoint-transact-sql) </span></span>  
 <span data-ttu-id="85052-213">[指定伺服器網路位址 &#40;資料庫鏡像&#41;](specify-a-server-network-address-database-mirroring.md) </span><span class="sxs-lookup"><span data-stu-id="85052-213">[Specify a Server Network Address &#40;Database Mirroring&#41;](specify-a-server-network-address-database-mirroring.md) </span></span>  
 <span data-ttu-id="85052-214">[範例：使用 Windows 驗證設定資料庫鏡像 &#40;Transact-SQL&#41;](example-setting-up-database-mirroring-using-windows-authentication-transact-sql.md) </span><span class="sxs-lookup"><span data-stu-id="85052-214">[Example: Setting Up Database Mirroring Using Windows Authentication &#40;Transact-SQL&#41;](example-setting-up-database-mirroring-using-windows-authentication-transact-sql.md) </span></span>  
 [<span data-ttu-id="85052-215">資料庫鏡像端點 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="85052-215">The Database Mirroring Endpoint &#40;SQL Server&#41;</span></span>](the-database-mirroring-endpoint-sql-server.md)  
