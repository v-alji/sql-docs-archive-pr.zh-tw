---
title: sqlagent90 應用程式 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- starting SQL Server Agent
- sqlagent90 application
- SQL Server Agent, starting
- command prompt utilities [SQL Server], sqlagent90
ms.assetid: e8b80e8d-d0c9-4500-a868-0ce08233da08
author: stevestein
ms.author: sstein
ms.openlocfilehash: 290cb69f39aa3b08bb290c210b2d37977614a1ae
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593726"
---
# <a name="sqlagent90-application"></a><span data-ttu-id="a08be-102">sqlagent90 應用程式</span><span class="sxs-lookup"><span data-stu-id="a08be-102">sqlagent90 Application</span></span>
  <span data-ttu-id="a08be-103">**sqlagent90** 應用程式可從命令提示字元啟動 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent。</span><span class="sxs-lookup"><span data-stu-id="a08be-103">The **sqlagent90** application starts [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent from the command prompt.</span></span> <span data-ttu-id="a08be-104">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent 通常應該從 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 執行，或利用應用程式中的 SQL-SMO 方法來執行。</span><span class="sxs-lookup"><span data-stu-id="a08be-104">Usually, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent should be run from [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] or by using SQL-SMO methods in an application.</span></span> <span data-ttu-id="a08be-105">請只在診斷 **Agent 時，或您的主要支援提供者指示您這麼做時，才從命令提示字元執行** sqlagent90 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="a08be-105">Only run **sqlagent90** from the command prompt when you are diagnosing [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent, or when you are directed to it by your primary support provider.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a08be-106">語法</span><span class="sxs-lookup"><span data-stu-id="a08be-106">Syntax</span></span>  
  
```  
  
sqlagent90  
-c [-v] [-iinstance_name]  
```  
  
## <a name="arguments"></a><span data-ttu-id="a08be-107">引數</span><span class="sxs-lookup"><span data-stu-id="a08be-107">Arguments</span></span>  
 <span data-ttu-id="a08be-108">**-c**</span><span class="sxs-lookup"><span data-stu-id="a08be-108">**-c**</span></span>  
 <span data-ttu-id="a08be-109">指出 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent 是在命令提示字元之下執行，與 Microsoft Windows 服務控制管理員無關。</span><span class="sxs-lookup"><span data-stu-id="a08be-109">Indicates that [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent is running from the command prompt and is independent of the Microsoft Windows Services Control Manager.</span></span> <span data-ttu-id="a08be-110">當使用 **-c** 時， [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent 無法利用 [系統管理工具] 中的 [服務] 應用程式來控制，也無法利用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 組態管理員來控制。</span><span class="sxs-lookup"><span data-stu-id="a08be-110">When **-c** is used, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent cannot be controlled from either the Services application in Administrative Tools or [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Configuration Manager.</span></span> <span data-ttu-id="a08be-111">這是強制引數。</span><span class="sxs-lookup"><span data-stu-id="a08be-111">This argument is mandatory.</span></span>  
  
 <span data-ttu-id="a08be-112">**-v**</span><span class="sxs-lookup"><span data-stu-id="a08be-112">**-v**</span></span>  
 <span data-ttu-id="a08be-113">指出 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent 執行詳細模式，且將診斷資訊寫入命令提示字元視窗中。</span><span class="sxs-lookup"><span data-stu-id="a08be-113">Indicates that [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent runs in verbose mode and writes diagnostic information to the command-prompt window.</span></span> <span data-ttu-id="a08be-114">診斷資訊與寫入 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent 錯誤記錄的資訊相同。</span><span class="sxs-lookup"><span data-stu-id="a08be-114">The diagnostic information is the same as the information written to the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent error log.</span></span>  
  
 <span data-ttu-id="a08be-115">**-i** *instance_name*</span><span class="sxs-lookup"><span data-stu-id="a08be-115">**-i** *instance_name*</span></span>  
 <span data-ttu-id="a08be-116">指出 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent 連接到 <執行個體名稱> 所指定的具名 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="a08be-116">Indicates that [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent connects to the named [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instance specified by *instance_name*.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a08be-117">備註</span><span class="sxs-lookup"><span data-stu-id="a08be-117">Remarks</span></span>  
 <span data-ttu-id="a08be-118">顯示著作權訊息之後，只有在指定了 **-v** 參數的情況下， **sqlagent90** 才會在命令提示字元視窗中顯示輸出。</span><span class="sxs-lookup"><span data-stu-id="a08be-118">After displaying a copyright message, **sqlagent90** displays output in the command prompt window only when the **-v** switch is specified.</span></span> <span data-ttu-id="a08be-119">若要停止 **sqlagent90**，請在命令提示字元按 CTRL+C。</span><span class="sxs-lookup"><span data-stu-id="a08be-119">To stop **sqlagent90**, press CTRL+C at the command prompt.</span></span> <span data-ttu-id="a08be-120">在停止 **sqlagent90**之前，請勿關閉命令提示字元視窗。</span><span class="sxs-lookup"><span data-stu-id="a08be-120">Do not close the command-prompt window before stopping **sqlagent90**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a08be-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a08be-121">See Also</span></span>  
 [<span data-ttu-id="a08be-122">自動化管理工作 &#40;SQL Server Agent&#41;</span><span class="sxs-lookup"><span data-stu-id="a08be-122">Automated Administration Tasks &#40;SQL Server Agent&#41;</span></span>](../ssms/agent/automated-administration-tasks-sql-server-agent.md)  
  
  
