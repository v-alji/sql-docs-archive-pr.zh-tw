---
title: 範本總管 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.wb.templates.f1
- sql12.swb.templates.explorer.f1
helpviewer_keywords:
- templates [SQL Server]
- SQL Server Management Studio [SQL Server], Template Explorer
- Template Explorer
- templates [Transact-SQL]
- templates [SQL Server], Template Explorer
ms.assetid: b9ee55c5-bb44-4f76-90ac-792d8d83b4c8
author: stevestein
ms.author: sstein
ms.openlocfilehash: 35e7ee1e6261c759580df3a836f9cc4b500a77ce
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597511"
---
# <a name="template-explorer"></a><span data-ttu-id="6263c-102">範本總管</span><span class="sxs-lookup"><span data-stu-id="6263c-102">Template Explorer</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="6263c-103">提供各種範本。</span><span class="sxs-lookup"><span data-stu-id="6263c-103">provides a variety of templates.</span></span> <span data-ttu-id="6263c-104">範本為包含 SQL 指令碼的模板檔案，可協助您在資料庫中建立物件。</span><span class="sxs-lookup"><span data-stu-id="6263c-104">Templates are boilerplate files containing SQL scripts that help you create objects in a database.</span></span> <span data-ttu-id="6263c-105">第一次開啟 [範本瀏覽器] 時，範本的複本會放在使用者資料夾的 C:\Users 中，位於 [AppData\Roaming\Microsoft\SQL Server Management Studio\120\Templates.] 底下。</span><span class="sxs-lookup"><span data-stu-id="6263c-105">The first time the template explorer is opened, a copy of the templates are placed in the user's folder in C:\Users, under AppData\Roaming\Microsoft\SQL Server Management Studio\120\Templates.</span></span>  
  
 <span data-ttu-id="6263c-106">您可以在 [範本總管] 中瀏覽可用的範本，然後開啟範本以將程式碼併入程式碼編輯器視窗。</span><span class="sxs-lookup"><span data-stu-id="6263c-106">You can browse the available templates in Template Explorer, then open a template to incorporate the code into a code editor window.</span></span> <span data-ttu-id="6263c-107">您還可以建立自訂範本。</span><span class="sxs-lookup"><span data-stu-id="6263c-107">You can also create custom templates.</span></span>  
  
## <a name="benefits-of-templates"></a><span data-ttu-id="6263c-108">範本的優點</span><span class="sxs-lookup"><span data-stu-id="6263c-108">Benefits of Templates</span></span>  
 <span data-ttu-id="6263c-109">方案、專案和各類型的程式碼編輯器都可以使用範本。</span><span class="sxs-lookup"><span data-stu-id="6263c-109">Templates are available for solutions, projects, and various types of code editors.</span></span> <span data-ttu-id="6263c-110">您可以利用範本來建立資料庫、資料表、檢視、索引、預存程序、觸發程序、統計資料和函數這類物件。</span><span class="sxs-lookup"><span data-stu-id="6263c-110">Templates are available to create objects like databases, tables, views, indexes, stored procedures, triggers, statistics, and functions.</span></span> <span data-ttu-id="6263c-111">此外，還有一些範本可協助您建立 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]的擴充屬性、連結伺服器、登入、角色、使用者和範本來管理伺服器。</span><span class="sxs-lookup"><span data-stu-id="6263c-111">In addition, there are templates that help you to manage your server by creating extended properties, linked servers, logins, roles, users, and templates for [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="6263c-112">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 所提供的範本指令碼包含協助您自訂程式碼的參數。</span><span class="sxs-lookup"><span data-stu-id="6263c-112">The template scripts provided with [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] contain parameters to help you customize the code.</span></span> <span data-ttu-id="6263c-113">開啟範本時，請使用 [取代範本參數]  對話方塊，在指令碼中插入值。</span><span class="sxs-lookup"><span data-stu-id="6263c-113">When you open a template, Use the **Replace Template Parameters** dialog box to insert values into the script.</span></span>  
  
 <span data-ttu-id="6263c-114">請建立您經常執行之工作的自訂範本。</span><span class="sxs-lookup"><span data-stu-id="6263c-114">Create custom templates for tasks you perform frequently.</span></span> <span data-ttu-id="6263c-115">請將您的自訂指令碼組織成現有的資料夾，或建立新的資料夾結構。</span><span class="sxs-lookup"><span data-stu-id="6263c-115">Organize your custom scripts into the existing folders or create a new folder structure.</span></span>  
  
 <span data-ttu-id="6263c-116">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 查詢編輯器也支援程式碼片段，可透過以滑鼠右鍵按一下指令碼中的特定位置，在該位置插入程式碼片段。</span><span class="sxs-lookup"><span data-stu-id="6263c-116">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query editor also supports code snippets, which can be inserted at specific locations in a script by right-clicking at that location.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="6263c-117">相關工作</span><span class="sxs-lookup"><span data-stu-id="6263c-117">Related Tasks</span></span>  
 <span data-ttu-id="6263c-118">若要開始使用範本，請使用下列主題。</span><span class="sxs-lookup"><span data-stu-id="6263c-118">Use the following topics to get started with templates</span></span>  
  
|<span data-ttu-id="6263c-119">**說明**</span><span class="sxs-lookup"><span data-stu-id="6263c-119">**Description**</span></span>|<span data-ttu-id="6263c-120">**主題**</span><span class="sxs-lookup"><span data-stu-id="6263c-120">**Topic**</span></span>|  
|---------------------|---------------|  
|<span data-ttu-id="6263c-121">描述如何將範本中的程式碼併入至程式碼編輯器視窗。</span><span class="sxs-lookup"><span data-stu-id="6263c-121">Describes how to incorporate the code from a template into a code editor window.</span></span>|[<span data-ttu-id="6263c-122">開啟範本</span><span class="sxs-lookup"><span data-stu-id="6263c-122">Open a Template</span></span>](open-a-template.md)|  
|<span data-ttu-id="6263c-123">描述在程式碼編輯器中開啟範本後如何取代範本參數值。</span><span class="sxs-lookup"><span data-stu-id="6263c-123">Describes how to replace template parameter values after opening a template in a code editor.</span></span>|[<span data-ttu-id="6263c-124">取代範本參數</span><span class="sxs-lookup"><span data-stu-id="6263c-124">Replace Template Parameters</span></span>](replace-template-parameters.md)|  
  
  
