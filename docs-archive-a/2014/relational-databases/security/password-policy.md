---
title: 密碼原則 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- ALTER LOGIN statement
- passwords [SQL Server], policy enforcement
- logins [SQL Server], passwords
- CHECK_EXPIRATION option
- complex passwords [SQL Server]
- passwords [SQL Server], expiration
- manual bad password count resets
- MUST_CHANGE option
- expiration [SQL Server]
- expired password [SQL Server]
- symbols [SQL Server]
- NetValidatePasswordPolicy() API
- passwords [SQL Server]
- password policy [SQL Server]
- resetting bad password counts
- security [SQL Server], passwords
- CHECK_POLICY option
- passwords [SQL Server], symbols
- bad password counts
- passwords [SQL Server], complexity
- characters [SQL Server], password policies
ms.assetid: c0040c0a-a18f-45b9-9c40-0625685649b1
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 902c46b4609a32139450843414a3c4d97b52fcf7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592560"
---
# <a name="password-policy"></a><span data-ttu-id="29cc8-102">密碼原則</span><span class="sxs-lookup"><span data-stu-id="29cc8-102">Password Policy</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="29cc8-103">可以使用 Windows 密碼原則機制。</span><span class="sxs-lookup"><span data-stu-id="29cc8-103">can use Windows password policy mechanisms.</span></span> <span data-ttu-id="29cc8-104">密碼原則適用於使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證的登入，以及適用於具有密碼的自主資料庫使用者。</span><span class="sxs-lookup"><span data-stu-id="29cc8-104">The password policy applies to a login that uses [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] authentication, and to a contained database user with password.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="29cc8-105">可將 Windows 所使用的相同複雜性和到期原則套用於 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]內部使用的密碼。</span><span class="sxs-lookup"><span data-stu-id="29cc8-105">can apply the same complexity and expiration policies used in Windows to passwords used inside [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="29cc8-106">這項功能取決於 `NetValidatePasswordPolicy` API。</span><span class="sxs-lookup"><span data-stu-id="29cc8-106">This functionality depends on the `NetValidatePasswordPolicy` API.</span></span>  
  
## <a name="password-complexity"></a><span data-ttu-id="29cc8-107">密碼複雜性</span><span class="sxs-lookup"><span data-stu-id="29cc8-107">Password Complexity</span></span>  
 <span data-ttu-id="29cc8-108">密碼複雜性原則是為了阻止暴力攻擊而設計，方法是盡可能地增加密碼數目。</span><span class="sxs-lookup"><span data-stu-id="29cc8-108">Password complexity policies are designed to deter brute force attacks by increasing the number of possible passwords.</span></span> <span data-ttu-id="29cc8-109">當強制執行密碼複雜性原則時，新的密碼必須符合下列指導方針：</span><span class="sxs-lookup"><span data-stu-id="29cc8-109">When password complexity policy is enforced, new passwords must meet the following guidelines:</span></span>  
  
-   <span data-ttu-id="29cc8-110">密碼不包含使用者的帳戶名稱。</span><span class="sxs-lookup"><span data-stu-id="29cc8-110">The password does not contain the account name of the user.</span></span>  
  
-   <span data-ttu-id="29cc8-111">密碼長度至少為八個字元。</span><span class="sxs-lookup"><span data-stu-id="29cc8-111">The password is at least eight characters long.</span></span>  
  
-   <span data-ttu-id="29cc8-112">密碼包含下列四種類別的其中三種：</span><span class="sxs-lookup"><span data-stu-id="29cc8-112">The password contains characters from three of the following four categories:</span></span>  
  
    -   <span data-ttu-id="29cc8-113">拉丁文大寫字母 (A 到 Z)。</span><span class="sxs-lookup"><span data-stu-id="29cc8-113">Latin uppercase letters (A through Z)</span></span>  
  
    -   <span data-ttu-id="29cc8-114">拉丁文小寫字母 (a 到 z)。</span><span class="sxs-lookup"><span data-stu-id="29cc8-114">Latin lowercase letters (a through z)</span></span>  
  
    -   <span data-ttu-id="29cc8-115">以 10 為基底的數字 (0 到 9)。</span><span class="sxs-lookup"><span data-stu-id="29cc8-115">Base 10 digits (0 through 9)</span></span>  
  
    -   <span data-ttu-id="29cc8-116">非英數字元，例如：驚嘆號 (!)、錢幣符號 ($)、數字符號 (#) 或百分比符號 (%)。</span><span class="sxs-lookup"><span data-stu-id="29cc8-116">Non-alphanumeric characters such as: exclamation point (!), dollar sign ($), number sign (#), or percent (%).</span></span>  
  
 <span data-ttu-id="29cc8-117">密碼長度最多可達 128 個字元。</span><span class="sxs-lookup"><span data-stu-id="29cc8-117">Passwords can be up to 128 characters long.</span></span> <span data-ttu-id="29cc8-118">您應該盡可能使用長且複雜的密碼。</span><span class="sxs-lookup"><span data-stu-id="29cc8-118">You should use passwords that are as long and complex as possible.</span></span>  
  
## <a name="password-expiration"></a><span data-ttu-id="29cc8-119">密碼過期</span><span class="sxs-lookup"><span data-stu-id="29cc8-119">Password Expiration</span></span>  
 <span data-ttu-id="29cc8-120">密碼過期原則用於管理密碼的壽命。</span><span class="sxs-lookup"><span data-stu-id="29cc8-120">Password expiration policies are used to manage the lifespan of a password.</span></span> <span data-ttu-id="29cc8-121">當 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 強制執行密碼到期原則時，系統會提醒使用者變更舊密碼和停用有過期密碼的帳戶。</span><span class="sxs-lookup"><span data-stu-id="29cc8-121">When [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] enforces password expiration policy, users are reminded to change old passwords, and accounts that have expired passwords are disabled.</span></span>  
  
## <a name="policy-enforcement"></a><span data-ttu-id="29cc8-122">原則強制執行</span><span class="sxs-lookup"><span data-stu-id="29cc8-122">Policy Enforcement</span></span>  
 <span data-ttu-id="29cc8-123">可個別對每一個 SQL Server 登入設定密碼原則的強制執行。</span><span class="sxs-lookup"><span data-stu-id="29cc8-123">The enforcement of password policy can be configured separately for each SQL Server login.</span></span> <span data-ttu-id="29cc8-124">使用 [ALTER LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-login-transact-sql) 來設定 SQL Server 登入的密碼原則選項。</span><span class="sxs-lookup"><span data-stu-id="29cc8-124">Use [ALTER LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-login-transact-sql) to configure the password policy options of a SQL Server login.</span></span> <span data-ttu-id="29cc8-125">下列規則會套用至密碼原則強制執行的組態：</span><span class="sxs-lookup"><span data-stu-id="29cc8-125">The following rules apply to the configuration of password policy enforcement:</span></span>  
  
-   <span data-ttu-id="29cc8-126">當 CHECK_POLICY 改為 ON 時，會發生下列行為：</span><span class="sxs-lookup"><span data-stu-id="29cc8-126">When CHECK_POLICY is changed to ON, the following behaviors occur:</span></span>  
  
    -   <span data-ttu-id="29cc8-127">CHECK_EXPIRATION 也會設為 ON，除非它已明確設為 OFF。</span><span class="sxs-lookup"><span data-stu-id="29cc8-127">CHECK_EXPIRATION is also set to ON unless it is explicitly set to OFF.</span></span>  
  
    -   <span data-ttu-id="29cc8-128">密碼記錄會使用目前密碼雜湊的值來初始化。</span><span class="sxs-lookup"><span data-stu-id="29cc8-128">The password history is initialized with the value of the current password hash.</span></span>  
  
    -   <span data-ttu-id="29cc8-129">[帳戶鎖定期間]、[帳戶鎖定閾值] 和 [重設帳戶鎖定計數器的時間] 也會啟用。</span><span class="sxs-lookup"><span data-stu-id="29cc8-129">**Account lockout duration**, **account lockout threshold**, and **reset account lockout counter after** are also enabled.</span></span>  
  
-   <span data-ttu-id="29cc8-130">當 CHECK_POLICY 改為 OFF 時，會發生下列行為：</span><span class="sxs-lookup"><span data-stu-id="29cc8-130">When CHECK_POLICY is changed to OFF, the following behaviors occur:</span></span>  
  
    -   <span data-ttu-id="29cc8-131">CHECK_EXPIRATION 也會設為 OFF。</span><span class="sxs-lookup"><span data-stu-id="29cc8-131">CHECK_EXPIRATION is also set to OFF.</span></span>  
  
    -   <span data-ttu-id="29cc8-132">會清除密碼記錄。</span><span class="sxs-lookup"><span data-stu-id="29cc8-132">The password history is cleared.</span></span>  
  
    -   <span data-ttu-id="29cc8-133">會重設 `lockout_time` 的值。</span><span class="sxs-lookup"><span data-stu-id="29cc8-133">The value of `lockout_time` is reset.</span></span>  
  
 <span data-ttu-id="29cc8-134">有些原則選項組合不受支援。</span><span class="sxs-lookup"><span data-stu-id="29cc8-134">Some combinations of policy options are not supported.</span></span>  
  
-   <span data-ttu-id="29cc8-135">如果指定 MUST_CHANGE，則 CHECK_EXPIRATION 和 CHECK_POLICY 必須設為 ON。</span><span class="sxs-lookup"><span data-stu-id="29cc8-135">If MUST_CHANGE is specified, CHECK_EXPIRATION and CHECK_POLICY must be set to ON.</span></span> <span data-ttu-id="29cc8-136">否則，陳述式便會失敗。</span><span class="sxs-lookup"><span data-stu-id="29cc8-136">Otherwise, the statement will fail.</span></span>  
  
-   <span data-ttu-id="29cc8-137">如果 CHECK_POLICY 設為 OFF，CHECK_EXPIRATION 就不可設為 ON。</span><span class="sxs-lookup"><span data-stu-id="29cc8-137">If CHECK_POLICY is set to OFF, CHECK_EXPIRATION cannot be set to ON.</span></span> <span data-ttu-id="29cc8-138">具有這些選項組合的 ALTER LOGIN 陳述式會失敗。</span><span class="sxs-lookup"><span data-stu-id="29cc8-138">An ALTER LOGIN statement that has this combination of options will fail.</span></span>  
  
 <span data-ttu-id="29cc8-139">設定 CHECK_POLICY = ON 將阻止建立密碼：</span><span class="sxs-lookup"><span data-stu-id="29cc8-139">Setting CHECK_POLICY = ON will prevent the creation of passwords that are:</span></span>  
  
-   <span data-ttu-id="29cc8-140">Null 或空白</span><span class="sxs-lookup"><span data-stu-id="29cc8-140">Null or empty</span></span>  
  
-   <span data-ttu-id="29cc8-141">與電腦或登入名稱相同</span><span class="sxs-lookup"><span data-stu-id="29cc8-141">Same as name of computer or login</span></span>  
  
-   <span data-ttu-id="29cc8-142">下列其中之一："password"、"admin"、"administrator"、"sa"、"sysadmin"</span><span class="sxs-lookup"><span data-stu-id="29cc8-142">Any of the following: "password", "admin", "administrator", "sa", "sysadmin"</span></span>  
  
 <span data-ttu-id="29cc8-143">安全性原則可能是在 Windows 中設定的，也可能是從網域收到的。</span><span class="sxs-lookup"><span data-stu-id="29cc8-143">The security policy might be set in Windows, or might be received from the domain.</span></span> <span data-ttu-id="29cc8-144">若要檢視電腦上的密碼原則，請使用 [本機安全性原則] MMC 嵌入式管理單元 (**secpol.msc**)。</span><span class="sxs-lookup"><span data-stu-id="29cc8-144">To view the password policy on the computer, use the Local Security Policy MMC snap-in (**secpol.msc**).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="29cc8-145">相關工作</span><span class="sxs-lookup"><span data-stu-id="29cc8-145">Related Tasks</span></span>  
 [<span data-ttu-id="29cc8-146">CREATE LOGIN &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="29cc8-146">CREATE LOGIN &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-login-transact-sql)  
  
 [<span data-ttu-id="29cc8-147">ALTER LOGIN &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="29cc8-147">ALTER LOGIN &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-login-transact-sql)  
  
 [<span data-ttu-id="29cc8-148">CREATE USER &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="29cc8-148">CREATE USER &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-user-transact-sql)  
  
 [<span data-ttu-id="29cc8-149">ALTER USER &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="29cc8-149">ALTER USER &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-user-transact-sql)  
  
 [<span data-ttu-id="29cc8-150">建立登入</span><span class="sxs-lookup"><span data-stu-id="29cc8-150">Create a Login</span></span>](authentication-access/create-a-login.md)  
  
 [<span data-ttu-id="29cc8-151">建立資料庫使用者</span><span class="sxs-lookup"><span data-stu-id="29cc8-151">Create a Database User</span></span>](authentication-access/create-a-database-user.md)  
  
## <a name="related-content"></a><span data-ttu-id="29cc8-152">相關內容</span><span class="sxs-lookup"><span data-stu-id="29cc8-152">Related Content</span></span>  
 [<span data-ttu-id="29cc8-153">增強式密碼</span><span class="sxs-lookup"><span data-stu-id="29cc8-153">Strong Passwords</span></span>](strong-passwords.md)  
  
  
