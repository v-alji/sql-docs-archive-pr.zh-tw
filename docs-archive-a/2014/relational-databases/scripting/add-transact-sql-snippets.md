---
title: 新增 Transact-SQL 程式碼片段
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 901c7995-8eb5-4d12-8bb0-de0a922b48f8
author: rothja
ms.author: jroth
ms.openlocfilehash: 5b5886f8f36ae3753fcb7c89dd3aeff9c69eeba5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594469"
---
# <a name="add-transact-sql-snippets"></a><span data-ttu-id="5d59f-102">新增 Transact-SQL 程式碼片段</span><span class="sxs-lookup"><span data-stu-id="5d59f-102">Add Transact-SQL Snippets</span></span>
  <span data-ttu-id="5d59f-103">將您自己的 Transact-SQL 程式碼片段加入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中包含的預先定義程式碼片段集合。</span><span class="sxs-lookup"><span data-stu-id="5d59f-103">You can add your own Transact-SQL code snippets to the set of pre-defined snippets included in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="creating-a-transact-sql-snippet-file"></a><span data-ttu-id="5d59f-104">建立 Transact-SQL 程式碼片段檔案</span><span class="sxs-lookup"><span data-stu-id="5d59f-104">Creating a Transact-SQL Snippet File</span></span>  
 <span data-ttu-id="5d59f-105">建立 [!INCLUDE[tsql](../../includes/tsql-md.md)] 程式碼片段的第一部分是使用您自己的程式碼片段文字建立 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="5d59f-105">The first part of creating a [!INCLUDE[tsql](../../includes/tsql-md.md)] code snippet is to create an XML file with the text of your code snippet.</span></span> <span data-ttu-id="5d59f-106">此檔案必須有 .snippet 副檔名，且必須符合 [程式碼片段結構描述參考](https://go.microsoft.com/fwlink/?LinkId=207504)的需求。</span><span class="sxs-lookup"><span data-stu-id="5d59f-106">The file must have a .snippet file extension, and meet the requirements of the [Code Snippets Schema](https://go.microsoft.com/fwlink/?LinkId=207504).</span></span> <span data-ttu-id="5d59f-107">將程式碼片段語言設定為 SQL。</span><span class="sxs-lookup"><span data-stu-id="5d59f-107">Set the snippet language to SQL.</span></span>  
  
 <span data-ttu-id="5d59f-108">您可以使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 所隨附的預先定義程式碼片段當做範例。</span><span class="sxs-lookup"><span data-stu-id="5d59f-108">You can use the pre-defined snippets that ship with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] as examples.</span></span> <span data-ttu-id="5d59f-109">若要尋找預先定義的程式碼片段，請開啟 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]，選取 [工具]  功能表，然後按一下 [程式碼片段管理員]  。</span><span class="sxs-lookup"><span data-stu-id="5d59f-109">To find the pre-defined snippets, open [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], select the **Tools** menu, and click **Code Snippet Manager**.</span></span> <span data-ttu-id="5d59f-110">在 **[語言]** 清單方塊中選取 **[SQL]** ， [!INCLUDE[tsql](../../includes/tsql-md.md)] 程式碼片段的路徑就會顯示在 **[位置]** 方塊中。</span><span class="sxs-lookup"><span data-stu-id="5d59f-110">Select **SQL** in the **Language** list box, the path to the [!INCLUDE[tsql](../../includes/tsql-md.md)] snippets is displayed in the **Location** box.</span></span>  
  
## <a name="registering-the-code-snippet"></a><span data-ttu-id="5d59f-111">註冊程式碼片段</span><span class="sxs-lookup"><span data-stu-id="5d59f-111">Registering the Code Snippet</span></span>  
 <span data-ttu-id="5d59f-112">在建立程式碼片段檔案之後，請使用程式碼片段管理員，向 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]註冊程式碼片段。</span><span class="sxs-lookup"><span data-stu-id="5d59f-112">After creating the snippet file, use the Code Snippets Manager to register the snippet with [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="5d59f-113">您可以加入包含多個程式碼片段的資料夾，或是將個別程式碼片段匯入到 **[My Code 程式碼片段]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="5d59f-113">You can either add a folder containing multiple snippets, or import individual snippets to the **My Code Snippets** folder.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="5d59f-114">程序</span><span class="sxs-lookup"><span data-stu-id="5d59f-114">Procedures</span></span>  
  
#### <a name="adding-a-snippet-folder"></a><span data-ttu-id="5d59f-115">加入程式碼片段資料夾</span><span class="sxs-lookup"><span data-stu-id="5d59f-115">Adding a Snippet Folder</span></span>  
  
1.  <span data-ttu-id="5d59f-116">開啟 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="5d59f-116">Open [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
2.  <span data-ttu-id="5d59f-117">選取 **[工具]** 功能表，然後按一下 **[程式碼片段管理員]** 。</span><span class="sxs-lookup"><span data-stu-id="5d59f-117">Select the **Tools** menu, and click **Code Snippets Manager**.</span></span>  
  
3.  <span data-ttu-id="5d59f-118">按一下 [新增]  按鈕。</span><span class="sxs-lookup"><span data-stu-id="5d59f-118">Click the **Add** button.</span></span>  
  
4.  <span data-ttu-id="5d59f-119">導覽至包含程式碼片段的資料夾，然後按一下 **[選取資料夾]** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="5d59f-119">Navigate to the folder containing your code snippets, and click the **Select Folder** button.</span></span>  
  
#### <a name="importing-a-snippet"></a><span data-ttu-id="5d59f-120">匯入程式碼片段</span><span class="sxs-lookup"><span data-stu-id="5d59f-120">Importing a Snippet</span></span>  
  
1.  <span data-ttu-id="5d59f-121">開啟 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="5d59f-121">Open [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
2.  <span data-ttu-id="5d59f-122">選取 **[工具]** 功能表，然後按一下 **[程式碼片段管理員]** 。</span><span class="sxs-lookup"><span data-stu-id="5d59f-122">Select the **Tools** menu, and click **Code Snippets Manager**.</span></span>  
  
3.  <span data-ttu-id="5d59f-123">按一下 [匯入]  按鈕。</span><span class="sxs-lookup"><span data-stu-id="5d59f-123">Click the **Import** button.</span></span>  
  
4.  <span data-ttu-id="5d59f-124">導覽至包含程式碼片段的資料夾，然後按一下 .snippet 檔案，再按一下 **[開啟]** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="5d59f-124">Navigate to the folder containing your snippet, click on the .snippet file, and click the **Open** button.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="5d59f-125">範例</span><span class="sxs-lookup"><span data-stu-id="5d59f-125">Examples</span></span>  
 <span data-ttu-id="5d59f-126">下列範例會建立 `TRY-CATCH` 範圍陳述式程式碼片段，並將其匯入至 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="5d59f-126">The following example creates a `TRY-CATCH` surround-with snippet and imports it to [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
1.  <span data-ttu-id="5d59f-127">將下列程式碼貼到 [記事本]，然後將檔案儲存為 TryCatch.snippet 名稱。</span><span class="sxs-lookup"><span data-stu-id="5d59f-127">Paste the following code into notepad, then save as a file named TryCatch.snippet.</span></span>  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>  
    <CodeSnippets  xmlns="https://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">  
    <_locDefinition xmlns="urn:locstudio">  
        <_locDefault _loc="locNone" />  
        <_locTag _loc="locData">Title</_locTag>  
        <_locTag _loc="locData">Description</_locTag>  
        <_locTag _loc="locData">Author</_locTag>  
        <_locTag _loc="locData">ToolTip</_locTag>  
       <_locTag _loc="locData">Default</_locTag>  
    </_locDefinition>  
    <CodeSnippet Format="1.0.0">  
    <Header>  
    <Title>TryCatch</Title>  
                            <Shortcut></Shortcut>  
    <Description>Example Snippet for Try-Catch.</Description>  
    <Author>SQL Server Books Online Example</Author>  
    <SnippetTypes>  
                                    <SnippetType>SurroundsWith</SnippetType>  
    </SnippetTypes>  
    </Header>  
    <Snippet>  
    <Declarations>  
                                    <Literal>  
                                    <ID>CatchCode</ID>  
                                    <ToolTip>Code to handle the caught error</ToolTip>  
                                    <Default>CatchCode</Default>  
                                    </Literal>  
    </Declarations>  
    <Code Language="SQL"><![CDATA[  
    BEGIN TRY  
  
    $selected$ $end$  
  
    END TRY  
    BEGIN CATCH  
  
    $CatchCode$  
  
    END CATCH;  
    ]]>  
    </Code>  
    </Snippet>  
    </CodeSnippet>  
    </CodeSnippets>  
    ```  
  
2.  <span data-ttu-id="5d59f-128">開啟 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="5d59f-128">Open [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
3.  <span data-ttu-id="5d59f-129">選取 **[工具]** 功能表，然後按一下 **[程式碼片段管理員]** 。</span><span class="sxs-lookup"><span data-stu-id="5d59f-129">Select the **Tools** menu, and click **Code Snippets Manager**.</span></span>  
  
4.  <span data-ttu-id="5d59f-130">按一下 [匯入]  按鈕。</span><span class="sxs-lookup"><span data-stu-id="5d59f-130">Click the **Import** button.</span></span>  
  
5.  <span data-ttu-id="5d59f-131">導覽至包含 TryCatch.snippet 的資料夾，然後按一下 TryCatch.snippet 檔案，再按一下 **[開啟]** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="5d59f-131">Navigate to the folder containing TryCatch.snippet, click on the TryCatch.snippet file, and click the **Open** button.</span></span> <span data-ttu-id="5d59f-132">**[My Code 程式碼片段]** 資料夾中應該不會有 TryCatch 程式碼片段。</span><span class="sxs-lookup"><span data-stu-id="5d59f-132">You should not have a TryCatch snippet in your **My Code Snippets** folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d59f-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5d59f-133">See Also</span></span>  
 [<span data-ttu-id="5d59f-134">插入範圍陳述式 Transact-SQL 程式碼片段</span><span class="sxs-lookup"><span data-stu-id="5d59f-134">Insert Surround-with Transact-SQL snippets</span></span>](insert-surround-with-transact-sql-snippets.md)  
  
  
