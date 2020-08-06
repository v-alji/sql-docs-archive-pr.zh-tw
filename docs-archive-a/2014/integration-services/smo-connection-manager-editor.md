---
title: SMO 連線管理員編輯器 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.smoconnection.f1
helpviewer_keywords:
- SMO Connection Manager Editor
ms.assetid: bed52d80-ed2a-4bf4-bf7c-481b6e228ca4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 6b3d1ccea1a3a4e963c6b6f8c7dbd58a374b3de4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709714"
---
# <a name="smo-connection-manager-editor"></a><span data-ttu-id="314f6-102">SMO 連接管理員編輯器</span><span class="sxs-lookup"><span data-stu-id="314f6-102">SMO Connection Manager Editor</span></span>
  <span data-ttu-id="314f6-103">使用 [SMO 連線管理員編輯器]\*\*\*\* 來設定傳送 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 物件的各種工作所使用的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 連接。</span><span class="sxs-lookup"><span data-stu-id="314f6-103">Use the **SMO Connection Manager Editor** to configure a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] connection for use by the various tasks that transfer [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] objects.</span></span>  
  
 <span data-ttu-id="314f6-104">若要深入了解 SMO 連線管理員，請參閱 [SMO 連線管理員](connection-manager/smo-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="314f6-104">To learn more about the SMO connection manager, see [SMO Connection Manager](connection-manager/smo-connection-manager.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="314f6-105">選項。</span><span class="sxs-lookup"><span data-stu-id="314f6-105">Options</span></span>  
 <span data-ttu-id="314f6-106">**伺服器名稱**</span><span class="sxs-lookup"><span data-stu-id="314f6-106">**Server name**</span></span>  
 <span data-ttu-id="314f6-107">輸入 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 執行個體的名稱，或從清單中選取伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="314f6-107">Type the name of the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instance or select the server name from the list.</span></span>  
  
 <span data-ttu-id="314f6-108">**[重新整理]**</span><span class="sxs-lookup"><span data-stu-id="314f6-108">**Refresh**</span></span>  
 <span data-ttu-id="314f6-109">重新整理可以在網路上偵測到的可用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 執行個體的清單。</span><span class="sxs-lookup"><span data-stu-id="314f6-109">Refresh the list of available [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instances that can be detected on the network.</span></span>  
  
 <span data-ttu-id="314f6-110">**[使用 Windows 驗證]**</span><span class="sxs-lookup"><span data-stu-id="314f6-110">**Use Windows Authentication**</span></span>  
 <span data-ttu-id="314f6-111">使用 Windows 驗證連接到選取的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="314f6-111">Use Windows Authentication to connect to the selected [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instance.</span></span>  
  
 <span data-ttu-id="314f6-112">**[使用 SQL Server 驗證]**</span><span class="sxs-lookup"><span data-stu-id="314f6-112">**Use SQL Server Authentication**</span></span>  
 <span data-ttu-id="314f6-113">使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 驗證連接到選取的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="314f6-113">Use [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication to connect to the selected [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instance.</span></span>  
  
 <span data-ttu-id="314f6-114">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="314f6-114">**User name**</span></span>  
 <span data-ttu-id="314f6-115">如果您已經選取 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 驗證，請輸入 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="314f6-115">If you have selected [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] authentication, enter the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] user name.</span></span>  
  
 <span data-ttu-id="314f6-116">**密碼**</span><span class="sxs-lookup"><span data-stu-id="314f6-116">**Password**</span></span>  
 <span data-ttu-id="314f6-117">如果您已經選取 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 驗證，請輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="314f6-117">If you have selected [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] authentication, enter the password.</span></span>  
  
 <span data-ttu-id="314f6-118">**測試連接**</span><span class="sxs-lookup"><span data-stu-id="314f6-118">**Test Connection**</span></span>  
 <span data-ttu-id="314f6-119">以目前的設定測試連接。</span><span class="sxs-lookup"><span data-stu-id="314f6-119">Test the connection as configured.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="314f6-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="314f6-120">See Also</span></span>  
 [<span data-ttu-id="314f6-121">Integration Services 錯誤和訊息參考</span><span class="sxs-lookup"><span data-stu-id="314f6-121">Integration Services Error and Message Reference</span></span>](../../2014/integration-services/integration-services-error-and-message-reference.md)  
  
  
