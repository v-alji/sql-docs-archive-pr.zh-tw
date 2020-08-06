---
title: SMO 連線管理員 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- connections [Integration Services], SMO
- SMO connection manager
- connection managers [Integration Services], SMO
ms.assetid: d273f1fb-a6a8-4f2f-a5ff-55c2e3de4723
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 988eef214608399bc3ec483d9976c2f5d52acb2a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708550"
---
# <a name="smo-connection-manager"></a><span data-ttu-id="496ac-102">SMO 連線管理員</span><span class="sxs-lookup"><span data-stu-id="496ac-102">SMO Connection Manager</span></span>
  <span data-ttu-id="496ac-103">SMO 連接管理員可讓封裝連接到 SQL Management Object (SMO) 伺服器。</span><span class="sxs-lookup"><span data-stu-id="496ac-103">An SMO connection manager enables a package to connect to a SQL Management Object (SMO) server.</span></span> <span data-ttu-id="496ac-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包含的傳送工作會使用 SMO 連線管理員。</span><span class="sxs-lookup"><span data-stu-id="496ac-104">The transfer tasks that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] includes use an SMO connection manager.</span></span> <span data-ttu-id="496ac-105">例如，傳送 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入的「傳送登入」工作便使用 SMO 連線管理員。</span><span class="sxs-lookup"><span data-stu-id="496ac-105">For example, the Transfer Logins task that transfers [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] logins uses an SMO connection manager.</span></span>  
  
 <span data-ttu-id="496ac-106">當您將 SMO 連接管理員加入封裝時，[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 會建立在執行階段解析為 SMO 連接的連接管理員、設定連接管理員屬性，並將連接管理員加入封裝上的 `Connections` 集合。</span><span class="sxs-lookup"><span data-stu-id="496ac-106">When you add an SMO connection manager to a package, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] creates a connection manager that will resolve to an SMO connection at run time, sets the connection manager properties, and adds the connection manager to the `Connections` collection on the package.</span></span> <span data-ttu-id="496ac-107">連接管理員的 `ConnectionManagerType` 屬性會設為 `SMOServer`。</span><span class="sxs-lookup"><span data-stu-id="496ac-107">The `ConnectionManagerType` property of the connection manager is set to `SMOServer`.</span></span>  
  
 <span data-ttu-id="496ac-108">您可以利用下列方式設定 SMO 連接管理員：</span><span class="sxs-lookup"><span data-stu-id="496ac-108">You can configure an SMO connection manager in the following ways:</span></span>  
  
-   <span data-ttu-id="496ac-109">指定已安裝 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 之伺服器的名稱。</span><span class="sxs-lookup"><span data-stu-id="496ac-109">Specify the name of a server on which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is installed.</span></span>  
  
-   <span data-ttu-id="496ac-110">選取驗證模式以連接到伺服器。</span><span class="sxs-lookup"><span data-stu-id="496ac-110">Select the authentication mode for connecting to the server.</span></span>  
  
## <a name="configuration-of-the-smo-connection-manager"></a><span data-ttu-id="496ac-111">設定 SMO 連接管理員</span><span class="sxs-lookup"><span data-stu-id="496ac-111">Configuration of the SMO Connection Manager</span></span>  
 <span data-ttu-id="496ac-112">您可以透過 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師或以程式設計方式設定屬性。</span><span class="sxs-lookup"><span data-stu-id="496ac-112">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="496ac-113">如需可在 [ [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師] 中設定之屬性的詳細資訊，請參閱 [SMO 連線管理員編輯器](../smo-connection-manager-editor.md)。</span><span class="sxs-lookup"><span data-stu-id="496ac-113">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, see [SMO Connection Manager Editor](../smo-connection-manager-editor.md).</span></span>  
  
 <span data-ttu-id="496ac-114">如需以程式設計方式設定連線管理員的資訊，請參閱 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 和 [以程式設計方式加入連接](../building-packages-programmatically/adding-connections-programmatically.md)。</span><span class="sxs-lookup"><span data-stu-id="496ac-114">For information about configuring a connection manager programmatically, see <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> and [Adding Connections Programmatically](../building-packages-programmatically/adding-connections-programmatically.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="496ac-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="496ac-115">See Also</span></span>  
 [<span data-ttu-id="496ac-116">Integration Services &#40;SSIS&#41; 連接</span><span class="sxs-lookup"><span data-stu-id="496ac-116">Integration Services &#40;SSIS&#41; Connections</span></span>](integration-services-ssis-connections.md)  
  
  
