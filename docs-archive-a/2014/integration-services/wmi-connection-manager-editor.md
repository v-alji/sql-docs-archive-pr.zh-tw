---
title: WMI 連線管理員編輯器 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.wmiconnection.f1
helpviewer_keywords:
- WMI Connection Manager Editor
ms.assetid: 0ef2c913-0779-4a07-989e-3361cd83170b
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e85cdd2157c8ebe4cb9e6b53f8c3b47ff102a7b4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599555"
---
# <a name="wmi-connection-manager-editor"></a><span data-ttu-id="17944-102">WMI 連接管理員編輯器</span><span class="sxs-lookup"><span data-stu-id="17944-102">WMI Connection Manager Editor</span></span>
  <span data-ttu-id="17944-103">使用 [WMI 連線管理員]\*\*\*\* 對話方塊，以指定 Microsoft Windows Management Instrumentation (WMI) 與伺服器的連線。</span><span class="sxs-lookup"><span data-stu-id="17944-103">Use the **WMI Connection Manager** dialog box to specify a Microsoft Windows Management Instrumentation (WMI) connection to a server.</span></span>  
  
 <span data-ttu-id="17944-104">若要深入了解 WMI 連接管理員，請參閱＜ [WMI Connection Manager](connection-manager/wmi-connection-manager.md)＞。</span><span class="sxs-lookup"><span data-stu-id="17944-104">To learn more about the WMI connection manager, see [WMI Connection Manager](connection-manager/wmi-connection-manager.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="17944-105">選項。</span><span class="sxs-lookup"><span data-stu-id="17944-105">Options</span></span>  
 <span data-ttu-id="17944-106">**名稱**</span><span class="sxs-lookup"><span data-stu-id="17944-106">**Name**</span></span>  
 <span data-ttu-id="17944-107">提供唯一的名稱給連接管理員。</span><span class="sxs-lookup"><span data-stu-id="17944-107">Provide a unique name for the connection manager.</span></span>  
  
 <span data-ttu-id="17944-108">**說明**</span><span class="sxs-lookup"><span data-stu-id="17944-108">**Description**</span></span>  
 <span data-ttu-id="17944-109">描述連接管理員。</span><span class="sxs-lookup"><span data-stu-id="17944-109">Describe the connection manager.</span></span> <span data-ttu-id="17944-110">最佳作法是以其用途描述連接管理員，使封裝可以自我記錄並易於維護。</span><span class="sxs-lookup"><span data-stu-id="17944-110">As a best practice, describe the connection manager in terms of its purpose, to make packages self-documenting and easier to maintain.</span></span>  
  
 <span data-ttu-id="17944-111">**伺服器名稱**</span><span class="sxs-lookup"><span data-stu-id="17944-111">**Server name**</span></span>  
 <span data-ttu-id="17944-112">提供您要 WMI 連接的伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="17944-112">Provide the name of the server to which you want to make the WMI connection.</span></span>  
  
 <span data-ttu-id="17944-113">**Namespace**</span><span class="sxs-lookup"><span data-stu-id="17944-113">**Namespace**</span></span>  
 <span data-ttu-id="17944-114">指定 WMI 命名空間。</span><span class="sxs-lookup"><span data-stu-id="17944-114">Specify the WMI namespace.</span></span>  
  
 <span data-ttu-id="17944-115">**使用 Windows 驗證**</span><span class="sxs-lookup"><span data-stu-id="17944-115">**Use Windows authentication**</span></span>  
 <span data-ttu-id="17944-116">選取以使用 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="17944-116">Select to use Windows Authentication.</span></span> <span data-ttu-id="17944-117">如果您使用 Windows 驗證，就不需要提供連接的使用者名稱或密碼。</span><span class="sxs-lookup"><span data-stu-id="17944-117">If you use Windows Authentication, you do not need to provide a user name or password for the connection.</span></span>  
  
 <span data-ttu-id="17944-118">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="17944-118">**User name**</span></span>  
 <span data-ttu-id="17944-119">如果您並未使用 Windows 驗證，則必須提供連接的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="17944-119">If you do not use Windows Authentication, you must provide a user name for the connection.</span></span>  
  
 <span data-ttu-id="17944-120">**密碼**</span><span class="sxs-lookup"><span data-stu-id="17944-120">**Password**</span></span>  
 <span data-ttu-id="17944-121">如果您並未使用 Windows 驗證，則必須提供連接的密碼。</span><span class="sxs-lookup"><span data-stu-id="17944-121">If you do not use Windows Authentication, you must provide the password for the connection.</span></span>  
  
 <span data-ttu-id="17944-122">**Test**</span><span class="sxs-lookup"><span data-stu-id="17944-122">**Test**</span></span>  
 <span data-ttu-id="17944-123">測試連接管理員設定。</span><span class="sxs-lookup"><span data-stu-id="17944-123">Test the connection manager settings.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17944-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="17944-124">See Also</span></span>  
 <span data-ttu-id="17944-125">[Integration Services 錯誤和訊息參考](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="17944-125">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="17944-126">[設定管理概念的 WMI 提供者](../relational-databases/wmi-provider-configuration/wmi-provider-for-configuration-management.md) </span><span class="sxs-lookup"><span data-stu-id="17944-126">[WMI Provider for Configuration Management Concepts](../relational-databases/wmi-provider-configuration/wmi-provider-for-configuration-management.md) </span></span>  
 [<span data-ttu-id="17944-127">伺服器事件的 WMI 提供者概念</span><span class="sxs-lookup"><span data-stu-id="17944-127">WMI Provider for Server Events Concepts</span></span>](../relational-databases/wmi-provider-server-events/wmi-provider-for-server-events-concepts.md)  
  
  
