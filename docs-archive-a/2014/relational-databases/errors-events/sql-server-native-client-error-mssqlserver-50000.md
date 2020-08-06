---
title: MSSQLSERVER_50000 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: reference
helpviewer_keywords:
- 50000 [SQL Server Native Client setup error]
ms.assetid: 5426d87a-d5d9-4984-b211-b07d69e834a2
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3cc805042bff7259a311ca3f2acf4c26db59381b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701215"
---
# <a name="mssqlserver_50000"></a><span data-ttu-id="48be3-102">MSSQLSERVER_50000</span><span class="sxs-lookup"><span data-stu-id="48be3-102">MSSQLSERVER_50000</span></span>
    
## <a name="details"></a><span data-ttu-id="48be3-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="48be3-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="48be3-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="48be3-104">Product Name</span></span>|<span data-ttu-id="48be3-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="48be3-105">SQL Server</span></span>|  
|<span data-ttu-id="48be3-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="48be3-106">Product Version</span></span>|<span data-ttu-id="48be3-107">11.0</span><span class="sxs-lookup"><span data-stu-id="48be3-107">11.0</span></span>|  
|<span data-ttu-id="48be3-108">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="48be3-108">Event ID</span></span>|<span data-ttu-id="48be3-109">50000</span><span class="sxs-lookup"><span data-stu-id="48be3-109">50000</span></span>|  
|<span data-ttu-id="48be3-110">事件來源</span><span class="sxs-lookup"><span data-stu-id="48be3-110">Event Source</span></span>|<span data-ttu-id="48be3-111">SETUP</span><span class="sxs-lookup"><span data-stu-id="48be3-111">SETUP</span></span>|  
|<span data-ttu-id="48be3-112">元件</span><span class="sxs-lookup"><span data-stu-id="48be3-112">Component</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="48be3-113">Native Client</span><span class="sxs-lookup"><span data-stu-id="48be3-113">Native Client</span></span>|  
|<span data-ttu-id="48be3-114">符號名稱</span><span class="sxs-lookup"><span data-stu-id="48be3-114">Symbolic Name</span></span>||  
|<span data-ttu-id="48be3-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="48be3-115">Message Text</span></span>|<span data-ttu-id="48be3-116">嘗試讀取檔案 '%.\*ls' 時發生網路錯誤。</span><span class="sxs-lookup"><span data-stu-id="48be3-116">A network error occurred while attempting to read from the file '%.\*ls'.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="48be3-117">說明</span><span class="sxs-lookup"><span data-stu-id="48be3-117">Explanation</span></span>  
 <span data-ttu-id="48be3-118">嘗試在已經安裝 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 而且現有安裝來自從 sqlncli.msi 重新命名之 MSI 檔案的電腦上安裝 (或更新) [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client。</span><span class="sxs-lookup"><span data-stu-id="48be3-118">An attempt was made to install (or update) [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client on a computer where [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client is already installed, and where the existing installation was from an MSI file that was renamed from sqlncli.msi.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="48be3-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="48be3-119">User Action</span></span>  
 <span data-ttu-id="48be3-120">若要解決這個錯誤，請解除安裝現有的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 版本。</span><span class="sxs-lookup"><span data-stu-id="48be3-120">To resolve this error, uninstall the existing version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.</span></span> <span data-ttu-id="48be3-121">若要防止這個錯誤發生，請避免從不是名為 sqlncli.msi 的 MSI 檔案安裝 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client。</span><span class="sxs-lookup"><span data-stu-id="48be3-121">To prevent this error, do not install [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client from an MSI file that is not named sqlncli.msi.</span></span>  
  
## <a name="internal-only"></a><span data-ttu-id="48be3-122">僅供內部使用</span><span class="sxs-lookup"><span data-stu-id="48be3-122">Internal-Only</span></span>  
  
