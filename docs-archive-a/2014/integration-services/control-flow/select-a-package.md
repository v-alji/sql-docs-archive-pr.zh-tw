---
title: 選取封裝 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.selectapackage.f1
helpviewer_keywords:
- Select a Package dialog box
ms.assetid: 92b47a2b-21b5-460a-885d-6cc4bb567249
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b35276791b004a011a1c2656057046be05ed6770
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584673"
---
# <a name="select-a-package"></a><span data-ttu-id="1a9bc-102">選取封裝</span><span class="sxs-lookup"><span data-stu-id="1a9bc-102">Select a Package</span></span>
  <span data-ttu-id="1a9bc-103">使用 **[選取封裝]** 對話方塊，即可指定訊息佇列工作可以接收訊息的來源封裝。</span><span class="sxs-lookup"><span data-stu-id="1a9bc-103">Use the **Select a Package** dialog box to specify the package from which the Message Queue task can receive messages.</span></span>  
  
## <a name="static-options"></a><span data-ttu-id="1a9bc-104">靜態選項</span><span class="sxs-lookup"><span data-stu-id="1a9bc-104">Static Options</span></span>  
 <span data-ttu-id="1a9bc-105">**位置**</span><span class="sxs-lookup"><span data-stu-id="1a9bc-105">**Location**</span></span>  
 <span data-ttu-id="1a9bc-106">指定封裝的位置。</span><span class="sxs-lookup"><span data-stu-id="1a9bc-106">Specify the location of the package.</span></span> <span data-ttu-id="1a9bc-107">這個屬性具有下表中所列的選項。</span><span class="sxs-lookup"><span data-stu-id="1a9bc-107">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="1a9bc-108">值</span><span class="sxs-lookup"><span data-stu-id="1a9bc-108">Value</span></span>|<span data-ttu-id="1a9bc-109">描述</span><span class="sxs-lookup"><span data-stu-id="1a9bc-109">Description</span></span>|  
|-----------|-----------------|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<span data-ttu-id="1a9bc-110">設定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體的位置。</span><span class="sxs-lookup"><span data-stu-id="1a9bc-110">Set the location to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="1a9bc-111">選取此值會顯示動態選項 **[伺服器]** 、 **[使用 Windows 驗證]** 、 **[使用 SQL Server 驗證]** 、 **[使用者名稱]** 和 **[密碼]** 。</span><span class="sxs-lookup"><span data-stu-id="1a9bc-111">Selecting this value displays the dynamic options, **Server**, **Use Windows Authentication**, **Use SQL Server Authentication**, **User name**, and **Password**.</span></span>|  
|<span data-ttu-id="1a9bc-112">DTSX 檔案</span><span class="sxs-lookup"><span data-stu-id="1a9bc-112">DTSX file</span></span>|<span data-ttu-id="1a9bc-113">設定 DTSX 檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="1a9bc-113">Set the location to a DTSX file.</span></span> <span data-ttu-id="1a9bc-114">選取此值會顯示動態選項 **[檔案名稱]** 。</span><span class="sxs-lookup"><span data-stu-id="1a9bc-114">Selecting this value displays the dynamic option, **File name**.</span></span>|  
  
## <a name="location-dynamic-options"></a><span data-ttu-id="1a9bc-115">位置動態選項</span><span class="sxs-lookup"><span data-stu-id="1a9bc-115">Location Dynamic Options</span></span>  
  
### <a name="location--sql-server"></a><span data-ttu-id="1a9bc-116">位置 = SQL Server</span><span class="sxs-lookup"><span data-stu-id="1a9bc-116">Location = SQL Server</span></span>  
 <span data-ttu-id="1a9bc-117">**封裝名稱**</span><span class="sxs-lookup"><span data-stu-id="1a9bc-117">**Package name**</span></span>  
 <span data-ttu-id="1a9bc-118">選取儲存在指定之伺服器上的封裝。</span><span class="sxs-lookup"><span data-stu-id="1a9bc-118">Select a package that is stored on the specified server.</span></span>  
  
 <span data-ttu-id="1a9bc-119">**Server**</span><span class="sxs-lookup"><span data-stu-id="1a9bc-119">**Server**</span></span>  
 <span data-ttu-id="1a9bc-120">提供伺服器名稱或從清單中選取伺服器。</span><span class="sxs-lookup"><span data-stu-id="1a9bc-120">Provide a server name or select a server from the list.</span></span>  
  
 <span data-ttu-id="1a9bc-121">**[使用 Windows 驗證]**</span><span class="sxs-lookup"><span data-stu-id="1a9bc-121">**Use Windows Authentication**</span></span>  
 <span data-ttu-id="1a9bc-122">按一下即可使用 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="1a9bc-122">Click to use Windows Authentication.</span></span>  
  
 <span data-ttu-id="1a9bc-123">**[使用 SQL Server 驗證]**</span><span class="sxs-lookup"><span data-stu-id="1a9bc-123">**Use SQL Server Authentication**</span></span>  
 <span data-ttu-id="1a9bc-124">按一下即可使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證。</span><span class="sxs-lookup"><span data-stu-id="1a9bc-124">Click to use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
 <span data-ttu-id="1a9bc-125">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="1a9bc-125">**User name**</span></span>  
 <span data-ttu-id="1a9bc-126">如果使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證，請提供登入伺服器時要使用的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="1a9bc-126">If using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication, provide a user name to use when logging on to the server.</span></span>  
  
 <span data-ttu-id="1a9bc-127">**密碼**</span><span class="sxs-lookup"><span data-stu-id="1a9bc-127">**Password**</span></span>  
 <span data-ttu-id="1a9bc-128">如果使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證，請提供密碼。</span><span class="sxs-lookup"><span data-stu-id="1a9bc-128">If using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication, provide a password.</span></span>  
  
### <a name="location--dtsx-file"></a><span data-ttu-id="1a9bc-129">位置 = DTSX 檔案</span><span class="sxs-lookup"><span data-stu-id="1a9bc-129">Location = DTSX file</span></span>  
 <span data-ttu-id="1a9bc-130">**檔案名稱**</span><span class="sxs-lookup"><span data-stu-id="1a9bc-130">**File name**</span></span>  
 <span data-ttu-id="1a9bc-131">提供封裝的路徑，或按一下瀏覽按鈕 ([...])  並尋找封裝。</span><span class="sxs-lookup"><span data-stu-id="1a9bc-131">Provide the path of a package or click the browse button **(...)** and locate the package.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a9bc-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1a9bc-132">See Also</span></span>  
 [<span data-ttu-id="1a9bc-133">訊息佇列工作</span><span class="sxs-lookup"><span data-stu-id="1a9bc-133">Message Queue Task</span></span>](message-queue-task.md)  
  
  
