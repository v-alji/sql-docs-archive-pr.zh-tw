---
title: MSSQLSERVER 屬性的通訊協定 ([憑證] 索引標籤) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- sql12.swb.computermgr.cert.general.f1
helpviewer_keywords:
- MSSQLSERVER property protocols
ms.assetid: 776addd6-25f3-4875-9a71-064035787090
author: stevestein
ms.author: sstein
ms.openlocfilehash: 020d33eba7621f877f8622ca89dbd26a071f16a8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705774"
---
# <a name="protocols-for-mssqlserver-properties-certificate-tab"></a><span data-ttu-id="d1083-102">MSSQLSERVER 的通訊協定內容 (憑證索引標籤)</span><span class="sxs-lookup"><span data-stu-id="d1083-102">Protocols for MSSQLSERVER Properties (Certificate Tab)</span></span>
  <span data-ttu-id="d1083-103">您可以使用 [MSSQLSERVER 屬性的通訊協定]  對話方塊的 [憑證]  索引標籤，以選取 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的憑證或檢視憑證內容。</span><span class="sxs-lookup"><span data-stu-id="d1083-103">Use the **Certificate** tab on the **Protocols for MSSQLSERVER Properties** dialog box to select a certificate for [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], or to view the properties of a certificate.</span></span> <span data-ttu-id="d1083-104">選取憑證之前所有欄位都會是空白。</span><span class="sxs-lookup"><span data-stu-id="d1083-104">All fields are blank until a certificate is selected.</span></span>  
  
 <span data-ttu-id="d1083-105">電腦上之使用者的憑證會儲存在本機中。</span><span class="sxs-lookup"><span data-stu-id="d1083-105">Certificates are stored locally for the users on the computer.</span></span> <span data-ttu-id="d1083-106">若要載入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]所使用的憑證，您必須使用和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務相同的使用者帳戶來執行「 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 組態管理員」。</span><span class="sxs-lookup"><span data-stu-id="d1083-106">To load a certificate for use by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you must be running [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager under the same user account as the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service.</span></span>  
  
## <a name="page-header"></a><span data-ttu-id="d1083-107">頁首</span><span class="sxs-lookup"><span data-stu-id="d1083-107">Page Header</span></span>  
 <span data-ttu-id="d1083-108">**檢視**</span><span class="sxs-lookup"><span data-stu-id="d1083-108">**View**</span></span>  
 <span data-ttu-id="d1083-109">可存取憑證上其他的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="d1083-109">Provides access to additional details on the certificate.</span></span> <span data-ttu-id="d1083-110">在 **[憑證]** 方塊中選取憑證之前，此按鈕無法使用。</span><span class="sxs-lookup"><span data-stu-id="d1083-110">Not available until a certificate is selected in the **Certificate** box.</span></span> <span data-ttu-id="d1083-111">如需憑證詳細資料的詳細資訊，請參閱 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 文件集。</span><span class="sxs-lookup"><span data-stu-id="d1083-111">For additional information on certificate details, see your [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows documentation.</span></span>  
  
 <span data-ttu-id="d1083-112">**Clear**</span><span class="sxs-lookup"><span data-stu-id="d1083-112">**Clear**</span></span>  
 <span data-ttu-id="d1083-113">從 [憑證]  方塊中移除選取的項目。</span><span class="sxs-lookup"><span data-stu-id="d1083-113">Removes the selection from the **Certificate** box.</span></span>  
  
 <span data-ttu-id="d1083-114">**[MSSQLSERVER 的通訊協定內容]**</span><span class="sxs-lookup"><span data-stu-id="d1083-114">**Certificate**</span></span>  
 <span data-ttu-id="d1083-115">憑證名稱，此名稱是由安全性提供者所決定。</span><span class="sxs-lookup"><span data-stu-id="d1083-115">Name of certificate as determined by security provider.</span></span> <span data-ttu-id="d1083-116">選取憑證，以便在內容方格中檢視其詳細資料。</span><span class="sxs-lookup"><span data-stu-id="d1083-116">Select a certificate to see the details in the properties grid.</span></span>  
  
## <a name="options"></a><span data-ttu-id="d1083-117">選項。</span><span class="sxs-lookup"><span data-stu-id="d1083-117">Options</span></span>  
 <span data-ttu-id="d1083-118">到期日</span><span class="sxs-lookup"><span data-stu-id="d1083-118">Expiration Date</span></span>  
 <span data-ttu-id="d1083-119">憑證有效的期限日。</span><span class="sxs-lookup"><span data-stu-id="d1083-119">The final date for the period in which the certificate is valid.</span></span>  
  
 <span data-ttu-id="d1083-120">易記名稱</span><span class="sxs-lookup"><span data-stu-id="d1083-120">Friendly Name</span></span>  
 <span data-ttu-id="d1083-121">由個人或憑證授權單位發給憑證對象的易記或常見名稱。</span><span class="sxs-lookup"><span data-stu-id="d1083-121">A friendly or common name for the individual or certification authority to whom the certificate is issued.</span></span>  
  
 <span data-ttu-id="d1083-122">發行者</span><span class="sxs-lookup"><span data-stu-id="d1083-122">Issued By</span></span>  
 <span data-ttu-id="d1083-123">憑證發行單位的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="d1083-123">Information regarding the certification authority that issued the certificate.</span></span>  
  
 <span data-ttu-id="d1083-124">發給</span><span class="sxs-lookup"><span data-stu-id="d1083-124">Issued To</span></span>  
 <span data-ttu-id="d1083-125">憑證接受者的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="d1083-125">Information regarding the recipient of the certificate.</span></span>  
  
  
