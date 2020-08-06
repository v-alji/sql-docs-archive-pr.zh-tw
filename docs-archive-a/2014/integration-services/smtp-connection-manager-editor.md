---
title: SMTP 連線管理員編輯器 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.smtpconnection.f1
helpviewer_keywords:
- SMTP Connection Manager Editor
ms.assetid: 2693de0d-b04d-4325-a856-ce667d2b8aa1
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e14ed49f64b9faca40f575fc6760a8d25c0d4573
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709709"
---
# <a name="smtp-connection-manager-editor"></a><span data-ttu-id="a14eb-102">SMTP 連接管理員編輯器</span><span class="sxs-lookup"><span data-stu-id="a14eb-102">SMTP Connection Manager Editor</span></span>
  <span data-ttu-id="a14eb-103">使用 [SMTP 連線管理員編輯器]  對話方塊指定簡易郵件傳輸通訊協定 (SMTP) 伺服器。</span><span class="sxs-lookup"><span data-stu-id="a14eb-103">Use the **SMTP Connection Manager Editor** dialog box to specify a Simple Mail Transfer Protocol (SMTP) server.</span></span>  
  
 <span data-ttu-id="a14eb-104">若要深入了解 SMTP 連接管理員，請參閱＜ [SMTP Connection Manager](connection-manager/smtp-connection-manager.md)＞。</span><span class="sxs-lookup"><span data-stu-id="a14eb-104">To learn more about the SMTP connection manager, see [SMTP Connection Manager](connection-manager/smtp-connection-manager.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="a14eb-105">選項。</span><span class="sxs-lookup"><span data-stu-id="a14eb-105">Options</span></span>  
 <span data-ttu-id="a14eb-106">**名稱**</span><span class="sxs-lookup"><span data-stu-id="a14eb-106">**Name**</span></span>  
 <span data-ttu-id="a14eb-107">提供唯一的名稱給連接管理員。</span><span class="sxs-lookup"><span data-stu-id="a14eb-107">Provide a unique name for the connection manager.</span></span>  
  
 <span data-ttu-id="a14eb-108">**說明**</span><span class="sxs-lookup"><span data-stu-id="a14eb-108">**Description**</span></span>  
 <span data-ttu-id="a14eb-109">描述連接管理員。</span><span class="sxs-lookup"><span data-stu-id="a14eb-109">Describe the connection manager.</span></span> <span data-ttu-id="a14eb-110">最佳作法是以其用途描述連接管理員，使封裝可以自我記錄並易於維護。</span><span class="sxs-lookup"><span data-stu-id="a14eb-110">As a best practice, describe the connection manager in terms of its purpose, to make packages self-documenting and easier to maintain.</span></span>  
  
 <span data-ttu-id="a14eb-111">**SMTP 伺服器**</span><span class="sxs-lookup"><span data-stu-id="a14eb-111">**SMTP server**</span></span>  
 <span data-ttu-id="a14eb-112">提供 SMTP 伺服器的名稱。</span><span class="sxs-lookup"><span data-stu-id="a14eb-112">Provide the name of the SMTP server.</span></span>  
  
 <span data-ttu-id="a14eb-113">**[使用 Windows 驗證]**</span><span class="sxs-lookup"><span data-stu-id="a14eb-113">**Use Windows Authentication**</span></span>  
 <span data-ttu-id="a14eb-114">選取此選項即可使用以 Windows 驗證來驗證伺服器存取權的 SMTP 伺服器，以便傳送郵件。</span><span class="sxs-lookup"><span data-stu-id="a14eb-114">Select to send mail using an SMTP server that uses Windows Authentication to authenticate access to the server.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="a14eb-115">SMTP 連接管理員僅支援匿名驗證和 Windows 驗證，</span><span class="sxs-lookup"><span data-stu-id="a14eb-115">The SMTP connection manager supports only anonymous authentication and Windows Authentication.</span></span> <span data-ttu-id="a14eb-116">而不支援基本驗證。</span><span class="sxs-lookup"><span data-stu-id="a14eb-116">It does not support basic authentication.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a14eb-117">使用 Microsoft Exchange 做為 SMTP 伺服器時，您可能需要將 [**使用 Windows 驗證**] 設定為 `True` 。</span><span class="sxs-lookup"><span data-stu-id="a14eb-117">When using Microsoft Exchange as the SMTP server, you may need to set **Use Windows Authentication** to `True`.</span></span> <span data-ttu-id="a14eb-118">Exchange 伺服器可以設定成不允許未驗證的 SMTP 連接。</span><span class="sxs-lookup"><span data-stu-id="a14eb-118">Exchange servers may be configured to disallow unauthenticated SMTP connections.</span></span>  
  
 <span data-ttu-id="a14eb-119">**啟用安全通訊端層 (SSL)**</span><span class="sxs-lookup"><span data-stu-id="a14eb-119">**Enable Secure Sockets Layer (SSL)**</span></span>  
 <span data-ttu-id="a14eb-120">選擇在傳送電子郵件訊息時以安全通訊端層 (SSL) 將通訊加密。</span><span class="sxs-lookup"><span data-stu-id="a14eb-120">Select to encrypt communication using Secure Sockets Layer (SSL) when sending e-mail messages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a14eb-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a14eb-121">See Also</span></span>  
 [<span data-ttu-id="a14eb-122">Integration Services 錯誤和訊息參考</span><span class="sxs-lookup"><span data-stu-id="a14eb-122">Integration Services Error and Message Reference</span></span>](../../2014/integration-services/integration-services-error-and-message-reference.md)  
  
  
