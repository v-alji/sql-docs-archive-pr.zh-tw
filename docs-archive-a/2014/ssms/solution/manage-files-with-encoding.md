---
title: 利用編碼管理檔案 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- files [SQL Server Management Studio]
- encoding [SQL Server Management Studio]
- files [SQL Server Management Studio], encoding
ms.assetid: 919544c9-59f0-4cc6-bb2a-f1ad671eb74b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 9b0aaa123001fed3f6ad42ea9d642e4007e2640f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607197"
---
# <a name="manage-files-with-encoding"></a><span data-ttu-id="6f709-102">利用編碼管理檔案</span><span class="sxs-lookup"><span data-stu-id="6f709-102">Manage Files with Encoding</span></span>
  <span data-ttu-id="6f709-103">為了有助於在特定語言和特定平台中顯示您的程式碼，您可以建立檔案與特定字元編碼的關聯。</span><span class="sxs-lookup"><span data-stu-id="6f709-103">To facilitate the display of your code in a particular language and on a particular platform, you can associate a particular character encoding with a file.</span></span>  
  
## <a name="opening-files"></a><span data-ttu-id="6f709-104">開啟檔案</span><span class="sxs-lookup"><span data-stu-id="6f709-104">Opening Files</span></span>  
 <span data-ttu-id="6f709-105">您可以選擇用來編輯檔案的編輯器。</span><span class="sxs-lookup"><span data-stu-id="6f709-105">You can choose the editor you want to use to edit the file.</span></span>  
  
#### <a name="to-open-a-file-with-a-specific-editor"></a><span data-ttu-id="6f709-106">利用特定編輯器開啟檔案</span><span class="sxs-lookup"><span data-stu-id="6f709-106">To open a file with a specific editor</span></span>  
  
1.  <span data-ttu-id="6f709-107">在 [檔案]  功能表上，指向 [開啟舊檔]  ，再按一下 [檔案]  。</span><span class="sxs-lookup"><span data-stu-id="6f709-107">On the **File** menu, point to **Open**, and then click **File**.</span></span>  
  
2.  <span data-ttu-id="6f709-108">在 [開啟檔案]  對話方塊中，選取檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="6f709-108">In the **Open File** dialog box, select the file name.</span></span>  
  
3.  <span data-ttu-id="6f709-109">按一下 [開啟舊檔]  按鈕旁的箭頭，在出現的功能表上，按一下 [開啟檔案]  。</span><span class="sxs-lookup"><span data-stu-id="6f709-109">Click the arrow next to the **Open** button, and then click**Open With** from the menu that appears.</span></span>  
  
4.  <span data-ttu-id="6f709-110">在 [選取要開啟的程式]  清單中，選取一個編輯器，再按一下 [開啟]  。</span><span class="sxs-lookup"><span data-stu-id="6f709-110">In the **Select a program to open** list, select an editor, and then click **Open**.</span></span> <span data-ttu-id="6f709-111">若要開啟含有特定編碼的檔案，請選取含編碼支援的編輯器，如含編碼的 SQL 查詢編輯器，或含編碼的 XML 編輯器。</span><span class="sxs-lookup"><span data-stu-id="6f709-111">To open the file with a particular encoding, select an editor with encoding support, such as SQL Query Editor with Encoding or XML Editor with Encoding.</span></span>  
  
## <a name="saving-files"></a><span data-ttu-id="6f709-112">儲存檔案</span><span class="sxs-lookup"><span data-stu-id="6f709-112">Saving Files</span></span>  
 <span data-ttu-id="6f709-113">您也可以利用 Unicode 編碼或不同的字碼頁來儲存您的程式碼，以便支援不同的語言，如西歐或東歐。</span><span class="sxs-lookup"><span data-stu-id="6f709-113">You can also save your code with a Unicode encoding or a different code page to support various languages, such as Western European or Eastern European.</span></span> <span data-ttu-id="6f709-114">您可以建立特定字元編碼與檔案的關聯，以便用這個語言來顯示您的程式碼，也可以建立行尾結束符號類型的關聯，以便支援特定作業系統。</span><span class="sxs-lookup"><span data-stu-id="6f709-114">You can associate a particular character encoding with a file to facilitate the display of your code in that language, as well as a line-ending type to support a particular operating system.</span></span> <span data-ttu-id="6f709-115">另外，當您在檔案名稱中使用某些字元時，除非用 Unicode 編碼來儲存，否則無法儲存它們。</span><span class="sxs-lookup"><span data-stu-id="6f709-115">Also, some characters, when used in file names, cannot be saved unless they are saved with Unicode encoding.</span></span>  
  
#### <a name="to-save-a-file-with-a-different-encoding-or-line-ending-type"></a><span data-ttu-id="6f709-116">利用不同編碼或行尾結束符號類型來儲存檔案</span><span class="sxs-lookup"><span data-stu-id="6f709-116">To save a file with a different encoding or line ending type</span></span>  
  
1.  <span data-ttu-id="6f709-117">在 [檔案]  功能表上按一下 [另存新檔] **\<filename>** 。</span><span class="sxs-lookup"><span data-stu-id="6f709-117">On the **File** menu, click **Save \<filename> As**.</span></span>  
  
2.  <span data-ttu-id="6f709-118">在 [另存新檔]  對話方塊中，展開 [儲存]  按鈕，再按一下 [使用編碼方式儲存]  。</span><span class="sxs-lookup"><span data-stu-id="6f709-118">In the **Save File As** dialog, expand the **Save** button, and then click **Save with Encoding**.</span></span>  
  
3.  <span data-ttu-id="6f709-119">在 [進階儲存選項]  對話方塊中，從 [編碼]  清單中選取您需要的編碼。</span><span class="sxs-lookup"><span data-stu-id="6f709-119">In the **Advanced Save Options** dialog box, select the encoding you want from the **Encoding** list.</span></span>  
  
4.  <span data-ttu-id="6f709-120">從 [行尾結束符號]  清單中，選取您需要的行尾結束符號類型。</span><span class="sxs-lookup"><span data-stu-id="6f709-120">From the **Line Endings**list, select the type of line ending you want.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="6f709-121">如果您利用 Unicode 編碼來儲存您的檔案，檔案應該做為二進位檔簽入 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual SourceSafe 中，因為 Visual SourceSafe 不支援合併、比較和顯示儲存成 Unicode 的檔案之間的差異。</span><span class="sxs-lookup"><span data-stu-id="6f709-121">If you save your file your file with Unicode encoding, the file should be checked into [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual SourceSafe as a binary file because Visual SourceSafe does not support merging, comparing, and showing differences between files that are saved as Unicode.</span></span>  
  
 <span data-ttu-id="6f709-122">如果您利用 Visual SourceSafe，以 ANSI、UTF8 或 Unicode 來儲存檔案，請注意下列限制：</span><span class="sxs-lookup"><span data-stu-id="6f709-122">If you are using Visual SourceSafe to store files with ANSI, UTF8, or Unicode, be aware of the following limitations for each:</span></span>  
  
-   <span data-ttu-id="6f709-123">ANSI 檔案只接受限制國際使用的目前字碼頁所支援的字元。</span><span class="sxs-lookup"><span data-stu-id="6f709-123">ANSI files allow only characters that are supported in the current code page, which limits international use.</span></span>  
  
-   <span data-ttu-id="6f709-124">Unicode 檔案無法使用共用的簽出、差異檢查或合併功能，因為它們是做為二進位檔來處理。</span><span class="sxs-lookup"><span data-stu-id="6f709-124">Unicode files cannot use shared checkout, difference checking, or merging functionality because they are handled as binary files.</span></span> <span data-ttu-id="6f709-125">您可以在國際檔案中使用這個格式。</span><span class="sxs-lookup"><span data-stu-id="6f709-125">You can use this format in international files.</span></span>  
  
-   <span data-ttu-id="6f709-126">UTF8 檔案無法與 Visual SourceSafe 一起安全地運作，因為在簽入、簽出、差異檢查和合併期間會進行變更，這些變更會使 UTF8 檔案編輯器發生問題。</span><span class="sxs-lookup"><span data-stu-id="6f709-126">UTF8 files do not work safely with Visual SourceSafe because changes that cause problems for UTF8 file editors are made during check in, check out, difference checking, and merging.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f709-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6f709-127">See Also</span></span>  
 <span data-ttu-id="6f709-128">[管理方案和專案的檔案](files-that-manage-solutions-and-projects.md) </span><span class="sxs-lookup"><span data-stu-id="6f709-128">[Files That Manage Solutions and Projects](files-that-manage-solutions-and-projects.md) </span></span>  
 [<span data-ttu-id="6f709-129">使副檔名與程式碼編輯器相關聯</span><span class="sxs-lookup"><span data-stu-id="6f709-129">Associate File Extensions to a Code Editor</span></span>](../../relational-databases/scripting/associate-file-extensions-to-a-code-editor.md)  
  
  
