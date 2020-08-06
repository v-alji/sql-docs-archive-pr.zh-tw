---
title: c2 audit mode 伺服器組態選項 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- auditing [SQL Server]
- audits [SQL Server], C2 Audit Mode option
- C2 auditing
- C2 Audit Mode option
- recording attempts
ms.assetid: 5a8d73a6-c4f6-4967-ba11-ecbcfc90b9cc
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 3407a2a94a43adb2d3d3b52994093d6ed0c2e684
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707866"
---
# <a name="c2-audit-mode-server-configuration-option"></a><span data-ttu-id="d0b91-102">C2 稽核模式伺服器組態選項</span><span class="sxs-lookup"><span data-stu-id="d0b91-102">c2 audit mode Server Configuration Option</span></span>
  <span data-ttu-id="d0b91-103">C2 稽核模式可以透過 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 或 **sp_configure** 中的 [C2 稽核模式] 選項來設定。</span><span class="sxs-lookup"><span data-stu-id="d0b91-103">C2 audit mode can be configured through [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or with the **c2 audit mode** option in **sp_configure**.</span></span> <span data-ttu-id="d0b91-104">選取這個選項，會將伺服器設定為將存取陳述式和物件的失敗嘗試和成功嘗試都記錄下來。</span><span class="sxs-lookup"><span data-stu-id="d0b91-104">Selecting this option will configure the server to record both failed and successful attempts to access statements and objects.</span></span> <span data-ttu-id="d0b91-105">這項資訊可協助您分析系統活動並追蹤可能的安全性原則違規。</span><span class="sxs-lookup"><span data-stu-id="d0b91-105">This information can help you profile system activity and track possible security policy violations.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]<span data-ttu-id="d0b91-106">通用條件憑證已取代 C2 安全性標準。</span><span class="sxs-lookup"><span data-stu-id="d0b91-106">The C2 security standard has been superseded by Common Criteria Certification.</span></span> <span data-ttu-id="d0b91-107">請參閱 [通用條件符合已啟用伺服器組態選項](common-criteria-compliance-enabled-server-configuration-option.md)。</span><span class="sxs-lookup"><span data-stu-id="d0b91-107">See the [common criteria compliance enabled Server Configuration Option](common-criteria-compliance-enabled-server-configuration-option.md).</span></span>  
  
## <a name="audit-log-file"></a><span data-ttu-id="d0b91-108">稽核記錄檔</span><span class="sxs-lookup"><span data-stu-id="d0b91-108">Audit Log File</span></span>  
 <span data-ttu-id="d0b91-109">C2 稽核模式資料會儲存在執行個體之預設資料目錄的檔案中。</span><span class="sxs-lookup"><span data-stu-id="d0b91-109">C2 audit mode data is saved in a file in the default data directory of the instance.</span></span> <span data-ttu-id="d0b91-110">如果稽核記錄檔已達到 200 MB 的大小限制， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 將建立新檔案、關閉舊檔案，並將所有新稽核記錄寫入新檔案。</span><span class="sxs-lookup"><span data-stu-id="d0b91-110">If the audit log file reaches its size limit of 200 megabytes (MB), [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will create a new file, close the old file, and write all new audit records to the new file.</span></span> <span data-ttu-id="d0b91-111">在填滿稽核資料目錄或關閉稽核之前，會繼續進行這個程序。</span><span class="sxs-lookup"><span data-stu-id="d0b91-111">This process will continue until the audit data directory fills up or auditing is turned off.</span></span> <span data-ttu-id="d0b91-112">若要判斷 C2 追蹤的狀態，請查詢 sys.traces 目錄檢視。</span><span class="sxs-lookup"><span data-stu-id="d0b91-112">To determine the status of a C2 trace, query the sys.traces catalog view.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="d0b91-113">C2 稽核模式會將大量的事件資訊儲存到記錄檔，因此該記錄檔會快速成長。</span><span class="sxs-lookup"><span data-stu-id="d0b91-113">C2 audit mode saves a large amount of event information to the log file, which can grow quickly.</span></span> <span data-ttu-id="d0b91-114">如果儲存記錄檔的資料目錄已用盡空間， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 將自行關閉。</span><span class="sxs-lookup"><span data-stu-id="d0b91-114">If the data directory in which logs are being saved runs out of space, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will shut itself down.</span></span> <span data-ttu-id="d0b91-115">如果將稽核設為自動啟動，您必須以 **-f** 旗標 (略過稽核) 重新啟動執行個體，或為稽核記錄釋放額外的磁碟空間。</span><span class="sxs-lookup"><span data-stu-id="d0b91-115">If auditing is set to start automatically, you must either restart the instance with the **-f** flag (which bypasses auditing), or free up additional disk space for the audit log.</span></span>  
  
## <a name="permissions"></a><span data-ttu-id="d0b91-116">權限</span><span class="sxs-lookup"><span data-stu-id="d0b91-116">Permissions</span></span>  
 <span data-ttu-id="d0b91-117">需要 **系統管理員 (sysadmin)** 固定伺服器角色中的成員資格。</span><span class="sxs-lookup"><span data-stu-id="d0b91-117">Requires membership in the **sysadmin** fixed server role.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d0b91-118">範例</span><span class="sxs-lookup"><span data-stu-id="d0b91-118">Example</span></span>  
 <span data-ttu-id="d0b91-119">下列範例會開啟 C2 稽核模式。</span><span class="sxs-lookup"><span data-stu-id="d0b91-119">The following example turns on C2 audit mode.</span></span>  
  
```  
sp_configure 'show advanced options', 1 ;  
GO  
RECONFIGURE ;  
GO  
  
sp_configure 'c2 audit mode', 1 ;  
GO  
RECONFIGURE ;  
GO  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="d0b91-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d0b91-120">See Also</span></span>  
 <span data-ttu-id="d0b91-121">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="d0b91-121">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="d0b91-122">[伺服器組態選項 &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="d0b91-122">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 [<span data-ttu-id="d0b91-123">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d0b91-123">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
