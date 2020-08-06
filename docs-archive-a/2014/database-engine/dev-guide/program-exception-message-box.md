---
title: 程式例外狀況訊息方塊 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
helpviewer_keywords:
- exception message box [SQL Server]
- displaying exception message box
ms.assetid: c771985b-149c-459a-b3cb-7b15fde01150
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 9d49bdf8c73f86b2c334018d40510b4ae67c85ca
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708590"
---
# <a name="program-exception-message-box"></a><span data-ttu-id="93fa4-102">程式例外狀況訊息方塊</span><span class="sxs-lookup"><span data-stu-id="93fa4-102">Program Exception Message Box</span></span>
  <span data-ttu-id="93fa4-103">您可以在應用程式中使用例外狀況訊息方塊，此訊息方塊對訊息經驗所提供的控制要比 <xref:System.Windows.Forms.MessageBox> 類別所提供的高出許多。</span><span class="sxs-lookup"><span data-stu-id="93fa4-103">You can use the exception message box in your applications to provide significantly more control over the messaging experience than is provided by the <xref:System.Windows.Forms.MessageBox> class.</span></span> <span data-ttu-id="93fa4-104">如需詳細資訊，請參閱[例外狀況訊息方塊程式設計](../../../2014/database-engine/dev-guide/exception-message-box-programming.md)。</span><span class="sxs-lookup"><span data-stu-id="93fa4-104">For more information, see [Exception Message Box Programming](../../../2014/database-engine/dev-guide/exception-message-box-programming.md).</span></span> <span data-ttu-id="93fa4-105">如需有關如何取得及部署例外狀況訊息方塊 .dll 的詳細資訊，請參閱＜ [Deploying an Exception Message Box Application](../../../2014/database-engine/dev-guide/deploying-an-exception-message-box-application.md)＞。</span><span class="sxs-lookup"><span data-stu-id="93fa4-105">For information about how to obtain and deploy the exception message box .dll, see [Deploying an Exception Message Box Application](../../../2014/database-engine/dev-guide/deploying-an-exception-message-box-application.md).</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="93fa4-106">程序</span><span class="sxs-lookup"><span data-stu-id="93fa4-106">Procedure</span></span>  
  
#### <a name="to-handle-an-exception-by-using-the-exception-message-box"></a><span data-ttu-id="93fa4-107">使用例外狀況訊息方塊處理例外狀況</span><span class="sxs-lookup"><span data-stu-id="93fa4-107">To handle an exception by using the exception message box</span></span>  
  
1.  <span data-ttu-id="93fa4-108">在 Managed 程式碼專案中加入 Microsoft.ExceptionMessageBox.dll 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="93fa4-108">Add a reference in your managed code project to the Microsoft.ExceptionMessageBox.dll assembly.</span></span>  
  
2.  <span data-ttu-id="93fa4-109"> (選擇性) 新增 `using` (c # ) 或 `Imports` ([!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic .net) 指示詞，以使用 <xref:Microsoft.SqlServer.MessageBox> 命名空間。</span><span class="sxs-lookup"><span data-stu-id="93fa4-109">(Optional) Add a `using` (C#) or `Imports` ([!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic .NET) directive to use the <xref:Microsoft.SqlServer.MessageBox> namespace.</span></span>  
  
3.  <span data-ttu-id="93fa4-110">建立 try-catch 區塊來處理預期的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="93fa4-110">Create a try-catch block to handle the anticipated exception.</span></span>  
  
4.  <span data-ttu-id="93fa4-111">在 `catch` 區塊內建立 <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox> 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="93fa4-111">Within the `catch` block, create an instance of the <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox> class.</span></span> <span data-ttu-id="93fa4-112">傳遞 <xref:System.Exception> 由區塊處理的物件 `try` - `catch` 。</span><span class="sxs-lookup"><span data-stu-id="93fa4-112">Pass the <xref:System.Exception> object handled by the `try`-`catch` block.</span></span>  
  
5.  <span data-ttu-id="93fa4-113">(選擇性) 在 <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox> 上設定下列其中一個或多個屬性：</span><span class="sxs-lookup"><span data-stu-id="93fa4-113">(Optional) Set one or more of the following properties on <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox>:</span></span>  
  
    -   <span data-ttu-id="93fa4-114"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Buttons%2A> - <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxButtons>列舉，指定要在例外狀況訊息方塊中顯示的按鈕。</span><span class="sxs-lookup"><span data-stu-id="93fa4-114"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Buttons%2A> - <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxButtons> enumeration that specifies the buttons to display in the exception message box.</span></span>  
  
    -   <span data-ttu-id="93fa4-115"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.DefaultButton%2A> - <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxDefaultButton>列舉，指定例外狀況訊息方塊的預設按鈕。</span><span class="sxs-lookup"><span data-stu-id="93fa4-115"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.DefaultButton%2A> - <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxDefaultButton> enumeration that specifies the default button for the exception message box.</span></span>  
  
    -   <span data-ttu-id="93fa4-116"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Options%2A> - <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxOptions>列舉，用來控制例外狀況訊息方塊的其他行為。</span><span class="sxs-lookup"><span data-stu-id="93fa4-116"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Options%2A> - <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxOptions> enumeration that you use to control other behaviors of the exception message box.</span></span>  
  
    -   <span data-ttu-id="93fa4-117"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Symbol%2A> - <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxSymbol>列舉，指定要在例外狀況訊息方塊中顯示的符號。</span><span class="sxs-lookup"><span data-stu-id="93fa4-117"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Symbol%2A> - <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxSymbol> enumeration that specifies the symbol to display in the exception message box.</span></span>  
  
6.  <span data-ttu-id="93fa4-118">呼叫 <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Show%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="93fa4-118">Call the <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Show%2A> method.</span></span> <span data-ttu-id="93fa4-119">傳遞例外狀況訊息方塊所屬的父視窗。</span><span class="sxs-lookup"><span data-stu-id="93fa4-119">Pass the parent window to which the exception message box belongs.</span></span>  
  
7.  <span data-ttu-id="93fa4-120">(選擇性) 如需判斷使用者所按的按鈕，請注意傳回的 <xref:System.Windows.Forms.DialogResult> 列舉值。</span><span class="sxs-lookup"><span data-stu-id="93fa4-120">(Optional) Note the value of returned <xref:System.Windows.Forms.DialogResult> enumeration if you need to determine which button the user clicked.</span></span>  
  
#### <a name="to-display-the-exception-message-box-without-an-exception"></a><span data-ttu-id="93fa4-121">顯示沒有例外狀況的例外狀況訊息方塊</span><span class="sxs-lookup"><span data-stu-id="93fa4-121">To display the exception message box without an exception</span></span>  
  
1.  <span data-ttu-id="93fa4-122">在 Managed 程式碼專案中加入 Microsoft.ExceptionMessageBox.dll 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="93fa4-122">Add a reference in your managed code project to the Microsoft.ExceptionMessageBox.dll assembly.</span></span>  
  
2.  <span data-ttu-id="93fa4-123"> (選擇性) 新增 `using` (c # ) 或 `Imports` (Visual Basic .net) 指示詞，以使用 <xref:Microsoft.SqlServer.MessageBox> 命名空間。</span><span class="sxs-lookup"><span data-stu-id="93fa4-123">(Optional) Add a `using` (C#) or `Imports` (Visual Basic .NET) directive to use the <xref:Microsoft.SqlServer.MessageBox> namespace.</span></span>  
  
3.  <span data-ttu-id="93fa4-124">建立 <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox> 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="93fa4-124">Create an instance of the <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox> class.</span></span> <span data-ttu-id="93fa4-125">將訊息文字當做 <xref:System.String> 值傳遞。</span><span class="sxs-lookup"><span data-stu-id="93fa4-125">Pass the message text as a <xref:System.String> value.</span></span>  
  
4.  <span data-ttu-id="93fa4-126">(選擇性) 在 <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox> 上設定下列其中一個或多個屬性：</span><span class="sxs-lookup"><span data-stu-id="93fa4-126">(Optional) Set one or more of the following properties on <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox>:</span></span>  
  
    -   <span data-ttu-id="93fa4-127"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Buttons%2A> - <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxButtons>列舉，指定要在例外狀況訊息方塊中顯示的按鈕。</span><span class="sxs-lookup"><span data-stu-id="93fa4-127"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Buttons%2A> - <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxButtons> enumeration that specifies the buttons to display in the exception message box.</span></span>  
  
    -   <span data-ttu-id="93fa4-128"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Caption%2A> - 例外狀況訊息方塊的對話方塊標題。</span><span class="sxs-lookup"><span data-stu-id="93fa4-128"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Caption%2A> - Dialog box caption of the exception message box.</span></span>  
  
    -   <span data-ttu-id="93fa4-129"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.DefaultButton%2A> - <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxDefaultButton>列舉，為例外狀況訊息方塊的對話方塊指定預設按鈕。</span><span class="sxs-lookup"><span data-stu-id="93fa4-129"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.DefaultButton%2A> - <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxDefaultButton> enumeration that specifies the default button for the dialog box of the exception message box.</span></span>  
  
    -   <span data-ttu-id="93fa4-130"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Options%2A> - <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxOptions>列舉，用來控制例外狀況訊息方塊的其他行為。</span><span class="sxs-lookup"><span data-stu-id="93fa4-130"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Options%2A> - <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxOptions> enumeration that you use to control other behaviors of the exception message box.</span></span>  
  
    -   <span data-ttu-id="93fa4-131"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Symbol%2A> - <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxSymbol>列舉，指定要在例外狀況訊息方塊中顯示的符號。</span><span class="sxs-lookup"><span data-stu-id="93fa4-131"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Symbol%2A> - <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxSymbol> enumeration that specifies the symbol to display in the exception message box.</span></span>  
  
5.  <span data-ttu-id="93fa4-132">呼叫 <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Show%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="93fa4-132">Call the <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Show%2A> method.</span></span> <span data-ttu-id="93fa4-133">傳遞例外狀況訊息方塊所屬的父視窗。</span><span class="sxs-lookup"><span data-stu-id="93fa4-133">Pass the parent window to which the exception message box belongs.</span></span>  
  
6.  <span data-ttu-id="93fa4-134">(選擇性) 如需判斷使用者所按的按鈕，請注意傳回的 <xref:System.Windows.Forms.DialogResult> 列舉值。</span><span class="sxs-lookup"><span data-stu-id="93fa4-134">(Optional) Note the value of the returned <xref:System.Windows.Forms.DialogResult> enumeration if you need to determine which button the user clicked.</span></span>  
  
#### <a name="to-display-the-exception-message-box-with-customized-buttons"></a><span data-ttu-id="93fa4-135">顯示具有自訂按鈕的例外狀況訊息方塊</span><span class="sxs-lookup"><span data-stu-id="93fa4-135">To display the exception message box with customized buttons</span></span>  
  
1.  <span data-ttu-id="93fa4-136">在 Managed 程式碼專案中加入 Microsoft.ExceptionMessageBox.dll 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="93fa4-136">Add a reference in your managed code project to the Microsoft.ExceptionMessageBox.dll assembly.</span></span>  
  
2.  <span data-ttu-id="93fa4-137"> (選擇性) 新增 `using` (c # ) 或 `Imports` (Visual Basic .net) 指示詞，以使用 <xref:Microsoft.SqlServer.MessageBox> 命名空間。</span><span class="sxs-lookup"><span data-stu-id="93fa4-137">(Optional) Add a `using` (C#) or `Imports` (Visual Basic .NET) directive to use the <xref:Microsoft.SqlServer.MessageBox> namespace.</span></span>  
  
3.  <span data-ttu-id="93fa4-138">以下列兩種方式中的一種來建立 <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox> 類別的執行個體：</span><span class="sxs-lookup"><span data-stu-id="93fa4-138">Create an instance of the <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox> class in one of two ways:</span></span>  
  
    -   <span data-ttu-id="93fa4-139">傳遞 <xref:System.Exception> 由區塊處理的物件 `try` - `catch` 。</span><span class="sxs-lookup"><span data-stu-id="93fa4-139">Pass the <xref:System.Exception> object handled by a `try`-`catch` block.</span></span>  
  
    -   <span data-ttu-id="93fa4-140">將訊息文字當做 <xref:System.String> 值傳遞。</span><span class="sxs-lookup"><span data-stu-id="93fa4-140">Pass the message text as a <xref:System.String> value.</span></span>  
  
4.  <span data-ttu-id="93fa4-141">針對 <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Buttons%2A> 設定下列其中一個值：</span><span class="sxs-lookup"><span data-stu-id="93fa4-141">Set one of the following values for <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Buttons%2A>:</span></span>  
  
    -   <span data-ttu-id="93fa4-142"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxButtons.AbortRetryIgnore>-顯示 [**中止**]、[**重試**] 和 [**忽略**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="93fa4-142"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxButtons.AbortRetryIgnore> - displays the **Abort**, **Retry**, and **Ignore** buttons.</span></span>  
  
    -   <span data-ttu-id="93fa4-143"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxButtons.Custom> - 顯示自訂按鈕。</span><span class="sxs-lookup"><span data-stu-id="93fa4-143"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxButtons.Custom> - displays custom buttons.</span></span>  
  
    -   <span data-ttu-id="93fa4-144"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxButtons.OK>-顯示 [**確定]** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="93fa4-144"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxButtons.OK> - displays the **OK** button.</span></span>  
  
    -   <span data-ttu-id="93fa4-145"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxButtons.OKCancel>-顯示 [**確定] 和 [** **取消**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="93fa4-145"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxButtons.OKCancel> - displays the **OK** and **Cancel** buttons.</span></span>  
  
    -   <span data-ttu-id="93fa4-146"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxButtons.RetryCancel>-顯示 [**重試**] 和 [**取消**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="93fa4-146"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxButtons.RetryCancel> - displays the **Retry** and **Cancel** buttons.</span></span>  
  
    -   <span data-ttu-id="93fa4-147"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxButtons.YesNo>-顯示 **[是] 和 [** **否**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="93fa4-147"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxButtons.YesNo> - displays **Yes** and **No** buttons.</span></span>  
  
    -   <span data-ttu-id="93fa4-148"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxButtons.YesNoCancel>-顯示 **[是]、[\*\*\*\*否**] 和 [**取消**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="93fa4-148"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxButtons.YesNoCancel> - displays **Yes**, **No**, and **Cancel** buttons.</span></span>  
  
5.  <span data-ttu-id="93fa4-149">(選擇性) 如果您使用自訂按鈕，請呼叫 <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.SetButtonText%2A> 方法的其中一個多載來指定最多五個自訂按鈕的文字。</span><span class="sxs-lookup"><span data-stu-id="93fa4-149">(Optional) If you use custom buttons, call one of the overloads of the <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.SetButtonText%2A> method to specify text for up to five custom buttons.</span></span>  
  
6.  <span data-ttu-id="93fa4-150">呼叫 <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Show%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="93fa4-150">Call the <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Show%2A> method.</span></span> <span data-ttu-id="93fa4-151">傳遞例外狀況訊息方塊所屬的父視窗。</span><span class="sxs-lookup"><span data-stu-id="93fa4-151">Pass the parent window to which the exception message box belongs.</span></span>  
  
7.  <span data-ttu-id="93fa4-152">(選擇性) 如需判斷使用者所按的按鈕，請注意傳回的 <xref:System.Windows.Forms.DialogResult> 列舉值。</span><span class="sxs-lookup"><span data-stu-id="93fa4-152">(Optional) Note the value of the returned <xref:System.Windows.Forms.DialogResult> enumeration if you need to determine which button the user clicked.</span></span> <span data-ttu-id="93fa4-153">如果使用自訂按鈕，請注意 <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxDialogResult> 屬性的 <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.CustomDialogResult%2A>，以判斷使用者所按的自訂按鈕。</span><span class="sxs-lookup"><span data-stu-id="93fa4-153">If you use custom buttons, note the value of <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxDialogResult> for the <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.CustomDialogResult%2A> property to determine which of the custom buttons the user clicked.</span></span>  
  
#### <a name="to-allow-users-to-decide-whether-to-show-the-exception-message-box"></a><span data-ttu-id="93fa4-154">讓使用者決定是否顯示例外狀況訊息方塊</span><span class="sxs-lookup"><span data-stu-id="93fa4-154">To allow users to decide whether to show the exception message box</span></span>  
  
1.  <span data-ttu-id="93fa4-155">在 Managed 程式碼專案中加入 Microsoft.ExceptionMessageBox.dll 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="93fa4-155">Add a reference in your managed code project to the Microsoft.ExceptionMessageBox.dll assembly.</span></span>  
  
2.  <span data-ttu-id="93fa4-156"> (選擇性) 新增 `using` (c # ) 或 `Imports` (Visual Basic .net) 指示詞，以使用 <xref:Microsoft.SqlServer.MessageBox> 命名空間。</span><span class="sxs-lookup"><span data-stu-id="93fa4-156">(Optional) Add a `using` (C#) or `Imports` (Visual Basic .NET) directive to use the <xref:Microsoft.SqlServer.MessageBox> namespace.</span></span>  
  
3.  <span data-ttu-id="93fa4-157">以下列兩種方式中的一種來建立 <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox> 類別的執行個體：</span><span class="sxs-lookup"><span data-stu-id="93fa4-157">Create an instance of the <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox> class in one of two ways:</span></span>  
  
    -   <span data-ttu-id="93fa4-158">傳遞 <xref:System.Exception> 由區塊處理的物件 `try` - `catch` 。</span><span class="sxs-lookup"><span data-stu-id="93fa4-158">Pass the <xref:System.Exception> object handled by a `try`-`catch` block.</span></span>  
  
    -   <span data-ttu-id="93fa4-159">將訊息文字當做 <xref:System.String> 值傳遞。</span><span class="sxs-lookup"><span data-stu-id="93fa4-159">Pass the message text as a <xref:System.String> value.</span></span>  
  
4.  <span data-ttu-id="93fa4-160">將 <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.ShowCheckbox%2A> 屬性設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="93fa4-160">Set the <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.ShowCheckbox%2A> property to `true`.</span></span>  
  
5.  <span data-ttu-id="93fa4-161">(選擇性) 指定文字以要求使用者決定是否針對 <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.CheckboxText%2A> 再次顯示例外狀況訊息方塊。</span><span class="sxs-lookup"><span data-stu-id="93fa4-161">(Optional) Specify the text that asks the user to decide whether to show the exception message box again for <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.CheckboxText%2A>.</span></span> <span data-ttu-id="93fa4-162">預設的文字為「不要再顯示此訊息」。</span><span class="sxs-lookup"><span data-stu-id="93fa4-162">The default text is "Do not show this message again."</span></span>  
  
6.  <span data-ttu-id="93fa4-163">如果只需在應用程式的執行期間保留使用者的決定，請將 <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.IsCheckboxChecked%2A> 的值設定為全域的 <xref:System.Boolean> 變數。</span><span class="sxs-lookup"><span data-stu-id="93fa4-163">If you need to keep the user's decision only for the duration of the application's execution, set the value of <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.IsCheckboxChecked%2A> to a global <xref:System.Boolean> variable.</span></span> <span data-ttu-id="93fa4-164">在建立例外狀況訊息方塊的執行個體之前，請先評估此值。</span><span class="sxs-lookup"><span data-stu-id="93fa4-164">Evaluate this value before creating an instance of the exception message box.</span></span>  
  
7.  <span data-ttu-id="93fa4-165">如果需要永久儲存使用者的決定，請進行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="93fa4-165">If you need to store a user's decision permanently, do the following:</span></span>  
  
    1.  <span data-ttu-id="93fa4-166">呼叫 CreateSubKey 方法來開啟應用程式所使用的自訂登錄機碼，然後將 <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.CheckboxRegistryKey%2A> 設定為傳回的 RegistryKey 物件。</span><span class="sxs-lookup"><span data-stu-id="93fa4-166">Call the CreateSubKey method to open a custom registry key that your application uses, and set <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.CheckboxRegistryKey%2A> to the returned RegistryKey object.</span></span>  
  
    2.  <span data-ttu-id="93fa4-167">將 <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.CheckboxRegistryValue%2A> 設定為所使用之登錄值的名稱。</span><span class="sxs-lookup"><span data-stu-id="93fa4-167">Set <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.CheckboxRegistryValue%2A> to the name of the registry value that is used.</span></span>  
  
    3.  <span data-ttu-id="93fa4-168">將 <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.CheckboxRegistryMeansDoNotShowDialog%2A> 設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="93fa4-168">Set <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.CheckboxRegistryMeansDoNotShowDialog%2A> to `true`.</span></span>  
  
    4.  <span data-ttu-id="93fa4-169">呼叫 <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Show%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="93fa4-169">Call the <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Show%2A> method.</span></span> <span data-ttu-id="93fa4-170">系統會評估指定的登錄機碼，只有當登錄機碼所儲存的資料為 0 時，才會顯示例外狀況訊息方塊。</span><span class="sxs-lookup"><span data-stu-id="93fa4-170">The specified registry key is evaluated, and the exception message box is displayed only if the data stored in the registry key is 0.</span></span> <span data-ttu-id="93fa4-171">如果對話方塊顯示，而且使用者在按按鈕之前先選取了這個核取方塊，則登錄機碼中的資料會設為 1。</span><span class="sxs-lookup"><span data-stu-id="93fa4-171">If the dialog box is displayed and the user selects the check box before clicking a button, the data in the registry key is set to 1.</span></span>  
  
## <a name="example"></a><span data-ttu-id="93fa4-172">範例</span><span class="sxs-lookup"><span data-stu-id="93fa4-172">Example</span></span>  
 <span data-ttu-id="93fa4-173">此範例所使用的例外狀況訊息方塊只具有 **[確定]** 按鈕，可顯示應用程式例外狀況的資訊，這些資訊包含處理的例外狀況以及其他的應用程式特定資訊。</span><span class="sxs-lookup"><span data-stu-id="93fa4-173">This example uses the exception message box with only the **OK** button to display information from an application exception that includes the handled exception along with additional application-specific information.</span></span>  
  
 [!code-csharp[HowTo#emb_showOKbutton](../../snippets/csharp/SQL15/replication/howto/cs/embform.cs#emb_showokbutton)]  
  
 [!code-vb[HowTo#emb_vb_showOKbutton](../../snippets/visualbasic/SQL15/replication/howto/vb/embform.vb#emb_vb_showokbutton)]  
  
## <a name="example"></a><span data-ttu-id="93fa4-174">範例</span><span class="sxs-lookup"><span data-stu-id="93fa4-174">Example</span></span>  
 <span data-ttu-id="93fa4-175">此範例所使用的例外狀況訊息方塊具有 **[是]** 和 **[否]** 按鈕，使用者可從中進行選擇。</span><span class="sxs-lookup"><span data-stu-id="93fa4-175">This example uses the exception message box with **Yes** and **No** buttons from which the user chooses.</span></span>  
  
 [!code-csharp[HowTo#emb_showYesNobutton](../../snippets/csharp/SQL15/replication/howto/cs/embform.cs#emb_showyesnobutton)]  
  
 [!code-vb[HowTo#emb_vb_showYesNobutton](../../snippets/visualbasic/SQL15/replication/howto/vb/embform.vb#emb_vb_showyesnobutton)]  
  
## <a name="example"></a><span data-ttu-id="93fa4-176">範例</span><span class="sxs-lookup"><span data-stu-id="93fa4-176">Example</span></span>  
 <span data-ttu-id="93fa4-177">此範例所使用的例外狀況訊息方塊具有自訂按鈕。</span><span class="sxs-lookup"><span data-stu-id="93fa4-177">This example uses the exception message box with custom buttons.</span></span>  
  
 [!code-csharp[HowTo#emb_showcustombutton](../../snippets/csharp/SQL15/replication/howto/cs/embform.cs#emb_showcustombutton)]  
  
 [!code-vb[HowTo#emb_vb_showcustombutton](../../snippets/visualbasic/SQL15/replication/howto/vb/embform.vb#emb_vb_showcustombutton)]  
  
## <a name="example"></a><span data-ttu-id="93fa4-178">範例</span><span class="sxs-lookup"><span data-stu-id="93fa4-178">Example</span></span>  
 <span data-ttu-id="93fa4-179">此範例使用核取方塊來決定是否顯示例外狀況訊息方塊。</span><span class="sxs-lookup"><span data-stu-id="93fa4-179">This example uses the check box to determine whether to show the exception message box.</span></span>  
  
 [!code-csharp[HowTo#emb_usecheckbox](../../snippets/csharp/SQL15/replication/howto/cs/embform.cs#emb_usecheckbox)]  
  
 [!code-vb[HowTo#emb_vb_usecheckbox](../../snippets/visualbasic/SQL15/replication/howto/vb/embform.vb#emb_vb_usecheckbox)]  
  
## <a name="example"></a><span data-ttu-id="93fa4-180">範例</span><span class="sxs-lookup"><span data-stu-id="93fa4-180">Example</span></span>  
 <span data-ttu-id="93fa4-181">此範例使用核取方塊和登錄機碼來決定是否顯示例外狀況訊息方塊。</span><span class="sxs-lookup"><span data-stu-id="93fa4-181">This example uses the check box and a registry key to determine whether to show the exception message box.</span></span>  
  
 [!code-csharp[HowTo#emb_useregkey](../../snippets/csharp/SQL15/replication/howto/cs/embform.cs#emb_useregkey)]  
  
 [!code-vb[HowTo#emb_vb_useregkey](../../snippets/visualbasic/SQL15/replication/howto/vb/embform.vb#emb_vb_useregkey)]  
  
## <a name="example"></a><span data-ttu-id="93fa4-182">範例</span><span class="sxs-lookup"><span data-stu-id="93fa4-182">Example</span></span>  
 <span data-ttu-id="93fa4-183">此範例使用例外狀況訊息方塊來顯示額外的資訊，這些資訊在進行疑難排解或偵錯時很有用。</span><span class="sxs-lookup"><span data-stu-id="93fa4-183">This example uses the exception message box to show additional information that is helpful when troubleshooting or debugging.</span></span>  
  
 [!code-csharp[HowTo#emb_moreinfo](../../snippets/csharp/SQL15/replication/howto/cs/embform.cs#emb_moreinfo)]  
  
 [!code-vb[HowTo#emb_vb_moreinfo](../../snippets/visualbasic/SQL15/replication/howto/vb/embform.vb#emb_vb_moreinfo)]  
  
  
