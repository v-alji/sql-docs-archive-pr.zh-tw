---
title: Database Mail XPs 伺服器組態選項 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- Database Mail XPs option
- Database Mail [SQL Server], enabling
ms.assetid: e22c4e63-1792-473b-af11-14a7931ca9ed
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 33ee15e862e0992f39373ec30275040c4fcacc0b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597321"
---
# <a name="database-mail-xps-server-configuration-option"></a><span data-ttu-id="eaf85-102">Database Mail XP 伺服器組態選項</span><span class="sxs-lookup"><span data-stu-id="eaf85-102">Database Mail XPs Server Configuration Option</span></span>
  <span data-ttu-id="eaf85-103">使用 [DatabaseMail XP] 選項，可在此伺服器上啟用 Database Mail。</span><span class="sxs-lookup"><span data-stu-id="eaf85-103">Use the **DatabaseMail XPs** option to enable Database Mail on this server.</span></span> <span data-ttu-id="eaf85-104">可能的值包括：</span><span class="sxs-lookup"><span data-stu-id="eaf85-104">The possible values are:</span></span>  
  
-   <span data-ttu-id="eaf85-105">**0** 表示無法使用 Database Mail (預設值)。</span><span class="sxs-lookup"><span data-stu-id="eaf85-105">**0** indicating Database Mail is not available (default).</span></span>  
  
-   <span data-ttu-id="eaf85-106">**1** 表示可使用 Database Mail。</span><span class="sxs-lookup"><span data-stu-id="eaf85-106">**1** indicating Database Mail is available.</span></span>  
  
 <span data-ttu-id="eaf85-107">設定立即生效，伺服器不必停止再重新啟動。</span><span class="sxs-lookup"><span data-stu-id="eaf85-107">The setting takes effect immediately without a server stop and restart.</span></span>  
  
 <span data-ttu-id="eaf85-108">啟用 Database Mail 後，您必須設定 Database Mail 主機資料庫來使用 Database Mail。</span><span class="sxs-lookup"><span data-stu-id="eaf85-108">After enabling Database Mail, you must configure a Database Mail host database to use Database Mail.</span></span>  
  
 <span data-ttu-id="eaf85-109">使用 [Database Mail 組態精靈]\*\*\*\* 設定 Database Mail，可啟用 **msdb** 資料庫中的 Database Mail 擴充預存程序。</span><span class="sxs-lookup"><span data-stu-id="eaf85-109">Configuring Database Mail using the **Database Mail Configuration Wizard** enables the Database Mail extended stored procedures in the **msdb** database.</span></span> <span data-ttu-id="eaf85-110">如果您使用 [Database Mail 組態精靈]\*\*\*\*，就不需使用以下的 **sp_configure** 範例。</span><span class="sxs-lookup"><span data-stu-id="eaf85-110">If you use the **Database Mail Configuration Wizard**, you do not have to use the **sp_configure** example below.</span></span>  
  
 <span data-ttu-id="eaf85-111">將 [Database Mail XP]\*\*\*\* 選項設為 0，會使 Database Mail 無法啟動。</span><span class="sxs-lookup"><span data-stu-id="eaf85-111">Setting the **Database Mail XPs** option to 0 prevents Database Mail from starting.</span></span> <span data-ttu-id="eaf85-112">如果 Database Mail 在該選項設為 0 時仍在執行中，則會繼續執行並傳送郵件，直到 **DatabaseMailExeMinimumLifeTime** 選項所設定的時間才會閒置。</span><span class="sxs-lookup"><span data-stu-id="eaf85-112">If it is running when the option is set to 0, it continues to run and send mail until it is idle for the time configured in the **DatabaseMailExeMinimumLifeTime** option.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="eaf85-113">範例</span><span class="sxs-lookup"><span data-stu-id="eaf85-113">Examples</span></span>  
 <span data-ttu-id="eaf85-114">下列範例會啟用 Database Mail 擴充預存程序。</span><span class="sxs-lookup"><span data-stu-id="eaf85-114">The following example enables the Database Mail extended stored procedures.</span></span>  
  
```  
sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
sp_configure 'Database Mail XPs', 1;  
GO  
RECONFIGURE  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="eaf85-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eaf85-115">See Also</span></span>  
 [<span data-ttu-id="eaf85-116">Database Mail</span><span class="sxs-lookup"><span data-stu-id="eaf85-116">Database Mail</span></span>](../../relational-databases/database-mail/database-mail.md)  
  
  
