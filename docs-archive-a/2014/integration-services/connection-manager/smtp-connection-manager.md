---
title: SMTP 連線管理員 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- connections [Integration Services], SMTP
- SMTP connection manager [Integration Services]
- connection managers [Integration Services], SMTP
ms.assetid: 3795d442-714b-4bbb-9acd-75bf277a468a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f3c090ab672790901baae01ae86f8d22e008b4ac
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708549"
---
# <a name="smtp-connection-manager"></a><span data-ttu-id="a1d3c-102">SMTP 連接管理員</span><span class="sxs-lookup"><span data-stu-id="a1d3c-102">SMTP Connection Manager</span></span>
  <span data-ttu-id="a1d3c-103">SMTP 連接管理員可讓封裝連接到 Simple Mail Transfer Protocol (SMTP) 伺服器。</span><span class="sxs-lookup"><span data-stu-id="a1d3c-103">An SMTP connection manager enables a package to connect to a Simple Mail Transfer Protocol (SMTP) server.</span></span> <span data-ttu-id="a1d3c-104">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包含的「傳送郵件」工作會使用 SMTP 連線管理員。</span><span class="sxs-lookup"><span data-stu-id="a1d3c-104">The Send Mail task that [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] includes uses an SMTP connection manager.</span></span>  
  
 <span data-ttu-id="a1d3c-105">將 Microsoft Exchange 用作 SMTP 伺服器時，您可能需要設定 SMTP 連接管理員使用「Windows 驗證」。</span><span class="sxs-lookup"><span data-stu-id="a1d3c-105">When using Microsoft Exchange as the SMTP server, you may need to configure the SMTP connection manager to use Windows Authentication.</span></span> <span data-ttu-id="a1d3c-106">Exchange 伺服器可以設定成不允許未驗證的 SMTP 連接。</span><span class="sxs-lookup"><span data-stu-id="a1d3c-106">Exchange servers may be configured to not allow unauthenticated SMTP connections.</span></span>  
  
## <a name="configuration-the-smtp-connection-manager"></a><span data-ttu-id="a1d3c-107">設定 SMTP 連接管理員</span><span class="sxs-lookup"><span data-stu-id="a1d3c-107">Configuration the SMTP Connection Manager</span></span>  
 <span data-ttu-id="a1d3c-108">當您將 SMTP 連接管理員加入封裝時，[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 會建立在執行階段解析為 SMTP 連接的連接管理員、設定連接管理員屬性，並將連接管理員加入封裝上的 `Connections` 集合。</span><span class="sxs-lookup"><span data-stu-id="a1d3c-108">When you add an SMTP connection manager to a package, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] creates a connection manager that will resolve to an SMTP connection at run time, sets the connection manager properties, and adds the connection manager to the `Connections` collection on the package.</span></span> <span data-ttu-id="a1d3c-109">連接管理員的 `ConnectionManagerType` 屬性會設為 `SMTP`。</span><span class="sxs-lookup"><span data-stu-id="a1d3c-109">The `ConnectionManagerType` property of the connection manager is set to `SMTP`.</span></span>  
  
 <span data-ttu-id="a1d3c-110">您可以利用下列方式設定 SMTP 連接管理員：</span><span class="sxs-lookup"><span data-stu-id="a1d3c-110">You can configure an SMTP connection manager in the following ways:</span></span>  
  
-   <span data-ttu-id="a1d3c-111">提供連接字串。</span><span class="sxs-lookup"><span data-stu-id="a1d3c-111">Provide a connection string.</span></span>  
  
-   <span data-ttu-id="a1d3c-112">指定 SMTP 伺服器的名稱。</span><span class="sxs-lookup"><span data-stu-id="a1d3c-112">Specify the name of an SMTP server.</span></span>  
  
-   <span data-ttu-id="a1d3c-113">指定要使用的驗證方法。</span><span class="sxs-lookup"><span data-stu-id="a1d3c-113">Specify the authentication method to use.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="a1d3c-114">SMTP 連接管理員僅支援匿名驗證和 Windows 驗證，</span><span class="sxs-lookup"><span data-stu-id="a1d3c-114">The SMTP connection manager supports only anonymous authentication and Windows Authentication.</span></span> <span data-ttu-id="a1d3c-115">而不支援基本驗證。</span><span class="sxs-lookup"><span data-stu-id="a1d3c-115">It does not support basic authentication.</span></span>  
  
-   <span data-ttu-id="a1d3c-116">指定在傳送電子郵件訊息時，是否使用「安全通訊端層 (SSL)」加密通訊。</span><span class="sxs-lookup"><span data-stu-id="a1d3c-116">Specify whether to encrypt communication using Secure Sockets Layer (SSL) when sending e-mail messages.</span></span>  
  
 <span data-ttu-id="a1d3c-117">您可以透過 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師或以程式設計方式設定屬性。</span><span class="sxs-lookup"><span data-stu-id="a1d3c-117">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="a1d3c-118">如需可在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師中設定之屬性的詳細資訊，請參閱 [SMTP 連線管理員編輯器](../smtp-connection-manager-editor.md)。</span><span class="sxs-lookup"><span data-stu-id="a1d3c-118">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, see [SMTP Connection Manager Editor](../smtp-connection-manager-editor.md).</span></span>  
  
 <span data-ttu-id="a1d3c-119">如需以程式設計方式設定連線管理員的資訊，請參閱 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 和 [以程式設計方式加入連接](../building-packages-programmatically/adding-connections-programmatically.md)。</span><span class="sxs-lookup"><span data-stu-id="a1d3c-119">For information about configuring a connection manager programmatically, see <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> and [Adding Connections Programmatically](../building-packages-programmatically/adding-connections-programmatically.md).</span></span>  
  
  
