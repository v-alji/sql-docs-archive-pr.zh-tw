---
title: 增強式密碼 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- logins [SQL Server], passwords
- passwords [SQL Server], strong
- symbols [SQL Server]
- security [SQL Server], passwords
- passwords [SQL Server], symbols
- characters [SQL Server], password policies
- strong passwords [SQL Server]
ms.assetid: 338548f4-c4d8-47ca-b597-5c9c0f2fa205
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 5e878e0de5ee1f496dcc981182d42f5898838c64
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688706"
---
# <a name="strong-passwords"></a><span data-ttu-id="6dab0-102">增強式密碼</span><span class="sxs-lookup"><span data-stu-id="6dab0-102">Strong Passwords</span></span>
  <span data-ttu-id="6dab0-103">密碼會是伺服器安全性部署中最薄弱的連結。</span><span class="sxs-lookup"><span data-stu-id="6dab0-103">Passwords can be the weakest link in a server security deployment.</span></span> <span data-ttu-id="6dab0-104">您在選取密碼的時候，應該始終保持小心謹慎的態度。</span><span class="sxs-lookup"><span data-stu-id="6dab0-104">You should always take great care when you select a password.</span></span> <span data-ttu-id="6dab0-105">增強式密碼具有下列特性：</span><span class="sxs-lookup"><span data-stu-id="6dab0-105">A strong password has the following characteristics:</span></span>  
  
-   <span data-ttu-id="6dab0-106">長度至少為 8 個字元。</span><span class="sxs-lookup"><span data-stu-id="6dab0-106">Is at least 8 characters long.</span></span>  
  
-   <span data-ttu-id="6dab0-107">密碼中結合字母、數字和符號字元。</span><span class="sxs-lookup"><span data-stu-id="6dab0-107">Combines letters, numbers, and symbol characters within the password.</span></span>  
  
-   <span data-ttu-id="6dab0-108">在字典中找不到。</span><span class="sxs-lookup"><span data-stu-id="6dab0-108">Is not found in a dictionary.</span></span>  
  
-   <span data-ttu-id="6dab0-109">不是命令名稱。</span><span class="sxs-lookup"><span data-stu-id="6dab0-109">Is not the name of a command.</span></span>  
  
-   <span data-ttu-id="6dab0-110">不是個人名稱。</span><span class="sxs-lookup"><span data-stu-id="6dab0-110">Is not the name of a person.</span></span>  
  
-   <span data-ttu-id="6dab0-111">不是使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="6dab0-111">Is not the name of a user.</span></span>  
  
-   <span data-ttu-id="6dab0-112">不是電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="6dab0-112">Is not the name of a computer.</span></span>  
  
-   <span data-ttu-id="6dab0-113">經常變更。</span><span class="sxs-lookup"><span data-stu-id="6dab0-113">Is changed regularly.</span></span>  
  
-   <span data-ttu-id="6dab0-114">與先前的密碼完全不同。</span><span class="sxs-lookup"><span data-stu-id="6dab0-114">Is significantly different from previous passwords.</span></span>  
  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="6dab0-115">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 密碼可以包含最多 128 個字元，可由字母、符號和數字組成。</span><span class="sxs-lookup"><span data-stu-id="6dab0-115">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] passwords can contain up to 128 characters, including letters, symbols, and digits.</span></span> <span data-ttu-id="6dab0-116">因為登入、使用者名稱、角色與密碼常用於 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式中，所以某些符號必須以雙引號 (") 或方括號 ([ ]) 括住。</span><span class="sxs-lookup"><span data-stu-id="6dab0-116">Because logins, user names, roles, and passwords are frequently used in [!INCLUDE[tsql](../../includes/tsql-md.md)] statements, certain symbols must be enclosed by double quotation marks (") or square brackets ([ ]).</span></span> <span data-ttu-id="6dab0-117">當 [!INCLUDE[tsql](../../includes/tsql-md.md)] 登入、使用者、角色或密碼具有下列特性時，請在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 陳述式中使用這些分隔符號：</span><span class="sxs-lookup"><span data-stu-id="6dab0-117">Use these delimiters in [!INCLUDE[tsql](../../includes/tsql-md.md)] statements when the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login, user, role, or password has the following characteristics:</span></span>  
  
-   <span data-ttu-id="6dab0-118">包含空白字元，或以空白字元開始。</span><span class="sxs-lookup"><span data-stu-id="6dab0-118">Contains or starts with a space character.</span></span>  
  
-   <span data-ttu-id="6dab0-119">以 $ 或 \@ 字元開始。</span><span class="sxs-lookup"><span data-stu-id="6dab0-119">Starts with the $ or \@ character.</span></span>  
  
 <span data-ttu-id="6dab0-120">如果是用在 OLE DB 或 ODBC 連接字串中，則登入或密碼中不能包含下列字元：[] {}() , ; ?</span><span class="sxs-lookup"><span data-stu-id="6dab0-120">If used in an OLE DB or ODBC connection string, a login or password must not contain the following characters: [] {}() , ; ?</span></span> <span data-ttu-id="6dab0-121">\* !</span><span class="sxs-lookup"><span data-stu-id="6dab0-121">\* !</span></span> <span data-ttu-id="6dab0-122">\@.</span><span class="sxs-lookup"><span data-stu-id="6dab0-122">\@.</span></span> <span data-ttu-id="6dab0-123">這些字元是用來初始化連接或分隔連接值。</span><span class="sxs-lookup"><span data-stu-id="6dab0-123">These characters are used to either initialize a connection or separate connection values.</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="6dab0-124">相關內容</span><span class="sxs-lookup"><span data-stu-id="6dab0-124">Related Content</span></span>  
 [<span data-ttu-id="6dab0-125">密碼原則</span><span class="sxs-lookup"><span data-stu-id="6dab0-125">Password Policy</span></span>](password-policy.md)  
  
  
