---
title: SQL Server Agent 屬性 (連接頁面) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.agent.connection.f1
ms.assetid: d6a677ff-60ad-47ba-a0cb-df4193b165e0
author: stevestein
ms.author: sstein
ms.openlocfilehash: ec9ae575f1ced510d95256d6827435e5b6ad89d1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599310"
---
# <a name="sql-server-agent-properties-connection-page"></a><span data-ttu-id="28954-102">SQL Server Agent 屬性 (連接頁面)</span><span class="sxs-lookup"><span data-stu-id="28954-102">SQL Server Agent Properties (Connection Page)</span></span>
  <span data-ttu-id="28954-103">使用此頁面來查看和修改從 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 服務到連接的設定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="28954-103">Use this page to view and modify the settings for the connection from the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="options"></a><span data-ttu-id="28954-104">選項</span><span class="sxs-lookup"><span data-stu-id="28954-104">Options</span></span>  
 <span data-ttu-id="28954-105">**別名本機主機伺服器**</span><span class="sxs-lookup"><span data-stu-id="28954-105">**Alias local host server**</span></span>  
 <span data-ttu-id="28954-106">指定用來連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]之本機執行個體的別名。</span><span class="sxs-lookup"><span data-stu-id="28954-106">Specifies the alias to use to connect to the local instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="28954-107">如果您無法使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 的預設連接選項，請為執行個體定義別名，並在此處指定該別名。</span><span class="sxs-lookup"><span data-stu-id="28954-107">If you cannot use the default connection options for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent, define an alias for the instance and specify the alias here.</span></span>  
  
 <span data-ttu-id="28954-108">**[使用 Windows 驗證]**</span><span class="sxs-lookup"><span data-stu-id="28954-108">**Use Windows Authentication**</span></span>  
 <span data-ttu-id="28954-109">將 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 驗證設定為連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體的驗證方法。</span><span class="sxs-lookup"><span data-stu-id="28954-109">Sets [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Authentication as the authentication method used to connect to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="28954-110">Agent 會以 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 服務執行身分帳戶連線。</span><span class="sxs-lookup"><span data-stu-id="28954-110">Agent connects as the account that the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service runs as.</span></span>  
  
 <span data-ttu-id="28954-111">**[使用 SQL Server 驗證]**</span><span class="sxs-lookup"><span data-stu-id="28954-111">**Use SQL Server Authentication**</span></span>  
 <span data-ttu-id="28954-112">設定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證為連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體的驗證方法。</span><span class="sxs-lookup"><span data-stu-id="28954-112">Sets [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication as the authentication method used to connect to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span>  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="28954-113">提供驗證的目的在提供回溯相容性。</span><span class="sxs-lookup"><span data-stu-id="28954-113">Authentication is provided for backward compatibility.</span></span> <span data-ttu-id="28954-114">為了提升安全性，如果可能的話請使用 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="28954-114">For improved security, use Windows Authentication if possible.</span></span>  
  
 <span data-ttu-id="28954-115">**登入**</span><span class="sxs-lookup"><span data-stu-id="28954-115">**Login**</span></span>  
 <span data-ttu-id="28954-116">指定用來連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的登入名稱。</span><span class="sxs-lookup"><span data-stu-id="28954-116">Specifies the login name to use to connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="28954-117">**密碼**</span><span class="sxs-lookup"><span data-stu-id="28954-117">**Password**</span></span>  
 <span data-ttu-id="28954-118">指定用來連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的密碼。</span><span class="sxs-lookup"><span data-stu-id="28954-118">Specifies the password to use to connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
  
