---
title: 例外狀況訊息方塊程式設計 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
helpviewer_keywords:
- ExceptionMessageBox class, about ExceptionMessageBox class
- exception message box [SQL Server], about exception message box
- exception message box [SQL Server]
- interfaces [SQL Server]
- exceptions [SQL Server]
- messages [SQL Server], exception message box
ms.assetid: 0b1ba514-6959-4e69-bfd2-3cf3c1ac4b9c
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: b2425169f838199ce24b4331dd57c74b480adf62
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709897"
---
# <a name="exception-message-box-programming"></a><span data-ttu-id="ead79-102">例外狀況訊息方塊程式設計</span><span class="sxs-lookup"><span data-stu-id="ead79-102">Exception Message Box Programming</span></span>
  <span data-ttu-id="ead79-103">例外狀況訊息方塊是以安裝的程式設計介面，並由 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 圖形元件所使用。</span><span class="sxs-lookup"><span data-stu-id="ead79-103">The exception message box is a programmatic interface that is installed with and used by [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] graphical components.</span></span> <span data-ttu-id="ead79-104">例外狀況訊息方塊是支援的 Managed 組件，可讓您用於應用程式中，以便更有效地控制訊息經驗，以及讓使用者選擇要儲存錯誤訊息內容以供日後參考，或是取得訊息的相關說明。</span><span class="sxs-lookup"><span data-stu-id="ead79-104">The exception message box is a supported managed assembly that you can use in your applications to provide significantly more control over the messaging experience and to give your users the options to save error message content for later reference and to get help on messages.</span></span> <span data-ttu-id="ead79-105">由於所有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 版本都會安裝例外狀況訊息方塊 ([!INCLUDE[ssEW](../../includes/ssew-md.md)] 除外)，因此您可以在已安裝 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 用戶端元件的任何電腦上使用此功能，不需要進行其他組態設定。</span><span class="sxs-lookup"><span data-stu-id="ead79-105">Because the exception message box is installed by all editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] except [!INCLUDE[ssEW](../../includes/ssew-md.md)], you can use it with no additional configuration on any computer on which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] client components have been installed.</span></span>  
  
 <span data-ttu-id="ead79-106"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox> 命名空間中的 <xref:Microsoft.SqlServer.MessageBox> 類別具有 <xref:System.Windows.Forms.MessageBox> 類別的所有功能和其他功能。</span><span class="sxs-lookup"><span data-stu-id="ead79-106">The <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox> class in the <xref:Microsoft.SqlServer.MessageBox> namespace has all the functionality of the <xref:System.Windows.Forms.MessageBox> class and more.</span></span> <span data-ttu-id="ead79-107"><xref:System.Windows.Forms.MessageBox> 是為了適當地處理 Managed 程式碼例外狀況所設計的，所以適合使用 <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox> 的任何工作採用。</span><span class="sxs-lookup"><span data-stu-id="ead79-107">Ideal for any tasks for which <xref:System.Windows.Forms.MessageBox> may be used, <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox> is designed to elegantly handle managed code exceptions.</span></span> <span data-ttu-id="ead79-108">例外狀況訊息方塊可讓您執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="ead79-108">The exception message box allows you to do the following:</span></span>  
  
-   <span data-ttu-id="ead79-109">提供自訂的按鈕文字，最多五個按鈕。</span><span class="sxs-lookup"><span data-stu-id="ead79-109">Provide customized button text for up to five buttons.</span></span> <span data-ttu-id="ead79-110">按鈕和對話方塊的大小會自動根據不同的文字長度而自動調整。</span><span class="sxs-lookup"><span data-stu-id="ead79-110">Buttons and the dialog box resize automatically for different text lengths.</span></span>  
  
-   <span data-ttu-id="ead79-111">讓使用者輕鬆地將訊息標題、文字、按鈕文字和說明連結 (如果有的話) 複製到 [剪貼簿] 或是透過電子郵件訊息傳送這項資訊。</span><span class="sxs-lookup"><span data-stu-id="ead79-111">Allow users to easily copy the message title, text, button text, and help links (if any) to the Clipboard or send this information in an e-mail message.</span></span>  
  
-   <span data-ttu-id="ead79-112">當使用者按一下 [**其他資訊**] 時，顯示階層式關聯性樹狀結構中的所有基礎例外狀況和錯誤。</span><span class="sxs-lookup"><span data-stu-id="ead79-112">Display all underlying exceptions and errors in a hierarchical relationship tree when users click **Additional Information**.</span></span>  
  
-   <span data-ttu-id="ead79-113">讓使用者決定再次發生相同的例外狀況時，是否要顯示訊息。</span><span class="sxs-lookup"><span data-stu-id="ead79-113">Allow users to decide whether to display the message when the same exception occurs again.</span></span>  
  
-   <span data-ttu-id="ead79-114">使用與例外狀況相關聯的說明連結來存取線上說明系統。</span><span class="sxs-lookup"><span data-stu-id="ead79-114">Access an online help system by using a help link associated with the exception.</span></span>  
  
 <span data-ttu-id="ead79-115">如需詳細資訊，請參閱[程式例外狀況訊息方塊](../../../2014/database-engine/dev-guide/program-exception-message-box.md)。</span><span class="sxs-lookup"><span data-stu-id="ead79-115">For more information, see [Program Exception Message Box](../../../2014/database-engine/dev-guide/program-exception-message-box.md).</span></span>  
  
  
