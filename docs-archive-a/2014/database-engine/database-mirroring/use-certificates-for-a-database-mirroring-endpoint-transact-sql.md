---
title: 使用資料庫鏡像端點憑證 (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- database mirroring [SQL Server], deployment
- certificates [SQL Server], database mirroring
- authentication [SQL Server], database mirroring
- database mirroring [SQL Server], security
ms.assetid: f7c23cc2-48dc-4b78-b441-89ca29a0bd9e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: c159e66e798524c41bf6e653283c299cc8393be5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594680"
---
# <a name="use-certificates-for-a-database-mirroring-endpoint-transact-sql"></a><span data-ttu-id="4bf90-102">使用資料庫鏡像端點憑證 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="4bf90-102">Use Certificates for a Database Mirroring Endpoint (Transact-SQL)</span></span>
  <span data-ttu-id="4bf90-103">若要啟用某伺服器執行個體上資料庫鏡像的憑證驗證，系統管理員必須設定每一個伺服器執行個體，才能同時在傳出和傳入的連接使用憑證。</span><span class="sxs-lookup"><span data-stu-id="4bf90-103">To enable certificate authentication for database mirroring on a given server instance, the system administrator must configure each server instance to use certificates on both outbound and inbound connections.</span></span> <span data-ttu-id="4bf90-104">您必須先設定傳出連接。</span><span class="sxs-lookup"><span data-stu-id="4bf90-104">Outbound connections must be configured first.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4bf90-105">伺服器執行個體上的所有鏡像連接都使用單一資料庫鏡像端點，而您必須在建立端點時指定伺服器執行個體的驗證方法。</span><span class="sxs-lookup"><span data-stu-id="4bf90-105">All mirroring connections on a server instance use a single database mirroring endpoint, and you must specify the authentication method of the server instance when you create the endpoint.</span></span> <span data-ttu-id="4bf90-106">因此，您可以在每一個伺服器執行個體只使用一個驗證形式進行資料庫鏡像。</span><span class="sxs-lookup"><span data-stu-id="4bf90-106">Therefore, you can use only one form of authentication per server instance for database mirroring.</span></span>  
  
## <a name="configuring-outbound-connections"></a><span data-ttu-id="4bf90-107">設定傳出連接</span><span class="sxs-lookup"><span data-stu-id="4bf90-107">Configuring Outbound Connections</span></span>  
 <span data-ttu-id="4bf90-108">在每一個您要設定資料庫鏡像的伺服器執行個體上依照下列步驟進行：</span><span class="sxs-lookup"><span data-stu-id="4bf90-108">Follow these steps on each server instance that you are configuring for database mirroring:</span></span>  
  
1.  <span data-ttu-id="4bf90-109">在 **master** 資料庫中，建立資料庫主要金鑰。</span><span class="sxs-lookup"><span data-stu-id="4bf90-109">In the **master** database, create a database master key.</span></span>  
  
2.  <span data-ttu-id="4bf90-110">在 **master** 資料庫中，建立伺服器執行個體的加密憑證。</span><span class="sxs-lookup"><span data-stu-id="4bf90-110">In the **master** database, create an encrypted certificate on the server instance.</span></span>  
  
3.  <span data-ttu-id="4bf90-111">使用伺服器執行個體的憑證來建立其端點。</span><span class="sxs-lookup"><span data-stu-id="4bf90-111">Create an endpoint for the server instance using its certificate.</span></span>  
  
4.  <span data-ttu-id="4bf90-112">將憑證備份至檔案中，並以安全的方式將其複製到其他一或多個系統。</span><span class="sxs-lookup"><span data-stu-id="4bf90-112">Back up the certificate to a file and securely copy it to the other system or systems.</span></span>  
  
 <span data-ttu-id="4bf90-113">您必須為每一個夥伴或見證 (如果有的話) 完成上述步驟。</span><span class="sxs-lookup"><span data-stu-id="4bf90-113">You must complete these steps for each partner and the witness, if there is one.</span></span>  
  
 <span data-ttu-id="4bf90-114">如需詳細資訊，請參閱 [允許資料庫鏡像端點使用輸出連線的憑證 &#40;Transact-SQL&#41;](database-mirroring-use-certificates-for-outbound-connections.md)。</span><span class="sxs-lookup"><span data-stu-id="4bf90-114">For more information, see [Allow a Database Mirroring Endpoint to Use Certificates for Outbound Connections &#40;Transact-SQL&#41;](database-mirroring-use-certificates-for-outbound-connections.md).</span></span>  
  
## <a name="configuring-inbound-connections"></a><span data-ttu-id="4bf90-115">設定傳入連接</span><span class="sxs-lookup"><span data-stu-id="4bf90-115">Configuring Inbound Connections</span></span>  
 <span data-ttu-id="4bf90-116">接著，在每一個您要設定資料庫鏡像的夥伴上依照下列步驟進行。</span><span class="sxs-lookup"><span data-stu-id="4bf90-116">Next, follow these steps for each partner that you are configuring for database mirroring.</span></span> <span data-ttu-id="4bf90-117">在 **master** 資料庫中：</span><span class="sxs-lookup"><span data-stu-id="4bf90-117">In the **master** database:</span></span>  
  
1.  <span data-ttu-id="4bf90-118">為其他系統建立登入。</span><span class="sxs-lookup"><span data-stu-id="4bf90-118">Create a login for the other system.</span></span>  
  
2.  <span data-ttu-id="4bf90-119">為該登入建立使用者。</span><span class="sxs-lookup"><span data-stu-id="4bf90-119">Create a user for that login.</span></span>  
  
3.  <span data-ttu-id="4bf90-120">取得另一個伺服器執行個體的鏡像端點的憑證。</span><span class="sxs-lookup"><span data-stu-id="4bf90-120">Obtain the certificate for the mirroring endpoint of the other server instance.</span></span>  
  
4.  <span data-ttu-id="4bf90-121">使憑證與步驟 2 所建立的使用者產生關聯。</span><span class="sxs-lookup"><span data-stu-id="4bf90-121">Associate the certificate with the user created in step 2.</span></span>  
  
5.  <span data-ttu-id="4bf90-122">將 CONNECT 權限授與登入，以連接該鏡像端點。</span><span class="sxs-lookup"><span data-stu-id="4bf90-122">Grant CONNECT permission on the login for that mirroring endpoint.</span></span>  
  
 <span data-ttu-id="4bf90-123">如果有見證，您也必須為它設定傳入連接。</span><span class="sxs-lookup"><span data-stu-id="4bf90-123">If there is a witness, you must also set up inbound connections for it.</span></span> <span data-ttu-id="4bf90-124">這需要在兩個夥伴上設定見證的登入、使用者和憑證，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="4bf90-124">This requires setting up logins, users, and certificates for the witness on both of the partners, and vice versa.</span></span>  
  
 <span data-ttu-id="4bf90-125">如需詳細資訊，請參閱 [允許資料庫鏡像端點使用輸入連線的憑證 &#40;Transact-SQL&#41;](database-mirroring-use-certificates-for-inbound-connections.md)。</span><span class="sxs-lookup"><span data-stu-id="4bf90-125">For more information, see [Allow a Database Mirroring Endpoint to Use Certificates for Inbound Connections &#40;Transact-SQL&#41;](database-mirroring-use-certificates-for-inbound-connections.md).</span></span>  
  
## <a name="security"></a><span data-ttu-id="4bf90-126">安全性</span><span class="sxs-lookup"><span data-stu-id="4bf90-126">Security</span></span>  
 <span data-ttu-id="4bf90-127">除非您可保證網路的安全無虞，否則建議您對資料庫鏡像連接使用加密。</span><span class="sxs-lookup"><span data-stu-id="4bf90-127">Unless you can guarantee that your network is secure, we recommend that you use encryption for database mirroring connections.</span></span> <span data-ttu-id="4bf90-128">如需詳細資訊，請參閱 [資料庫鏡像端點 &#40;SQL Server&#41;](the-database-mirroring-endpoint-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="4bf90-128">For more information, see [The Database Mirroring Endpoint &#40;SQL Server&#41;](the-database-mirroring-endpoint-sql-server.md).</span></span>  
  
 <span data-ttu-id="4bf90-129">將憑證複製到另一個系統時，請使用安全複製方法。</span><span class="sxs-lookup"><span data-stu-id="4bf90-129">When copying a certificate to another system, use a secure copy method.</span></span> <span data-ttu-id="4bf90-130">務必將您所有的憑證小心保管。</span><span class="sxs-lookup"><span data-stu-id="4bf90-130">Be extremely careful to keep all of your certificates secure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4bf90-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4bf90-131">See Also</span></span>  
 <span data-ttu-id="4bf90-132">[建立資料庫主要金鑰](../../relational-databases/security/encryption/create-a-database-master-key.md) </span><span class="sxs-lookup"><span data-stu-id="4bf90-132">[Create a Database Master Key](../../relational-databases/security/encryption/create-a-database-master-key.md) </span></span>  
 <span data-ttu-id="4bf90-133">[CREATE MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-master-key-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="4bf90-133">[CREATE MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-master-key-transact-sql) </span></span>  
 <span data-ttu-id="4bf90-134">[資料庫鏡像和 AlwaysOn 可用性群組的傳輸安全性 &#40;SQL Server&#41;](transport-security-database-mirroring-always-on-availability.md) </span><span class="sxs-lookup"><span data-stu-id="4bf90-134">[Transport Security for Database Mirroring and AlwaysOn Availability Groups &#40;SQL Server&#41;](transport-security-database-mirroring-always-on-availability.md) </span></span>  
 <span data-ttu-id="4bf90-135">[SQL Server Database Engine 和 Azure SQL Database 的資訊安全中心](../../relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database.md) </span><span class="sxs-lookup"><span data-stu-id="4bf90-135">[Security Center for SQL Server Database Engine and Azure SQL Database](../../relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database.md) </span></span>  
 [<span data-ttu-id="4bf90-136">資料庫鏡像端點 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="4bf90-136">The Database Mirroring Endpoint &#40;SQL Server&#41;</span></span>](the-database-mirroring-endpoint-sql-server.md)  
  
  
