---
title: 使副檔名與程式碼編輯器相關聯
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- file extensions [SQL Server]
- associating file extensions [SQL Server]
- Query Editor [SQL Server Management Studio], associating file extensions
ms.assetid: 193630f4-93de-4950-8f36-68702531f925
author: rothja
ms.author: jroth
ms.openlocfilehash: 0e8cfbc89892a99971e985ffd3ff10b99f89fe53
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594466"
---
# <a name="associate-file-extensions-to-a-code-editor"></a><span data-ttu-id="d5310-102">使副檔名與程式碼編輯器相關聯</span><span class="sxs-lookup"><span data-stu-id="d5310-102">Associate File Extensions to a Code Editor</span></span>
  <span data-ttu-id="d5310-103">使副檔名與特定程式碼編輯器相關聯，可讓您在 Windows 檔案總管中按兩下檔案時，能以適當的 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 程式碼編輯器開啟檔案。</span><span class="sxs-lookup"><span data-stu-id="d5310-103">Associating file extensions to a specific code editor allows you to open a file with the appropriate [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] code editor when you double-click a file in Windows Explorer.</span></span> <span data-ttu-id="d5310-104">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]一般使用的副檔名 (例如 .sql 和 .mdx) 會在安裝期間產生關聯。</span><span class="sxs-lookup"><span data-stu-id="d5310-104">The extensions commonly used by [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], such as .sql and .mdx, are associated during installation.</span></span> <span data-ttu-id="d5310-105">新的副檔名也必須在檔案系統中與 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 相關聯。</span><span class="sxs-lookup"><span data-stu-id="d5310-105">New file extensions must also be associated to [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] in the file system.</span></span> <span data-ttu-id="d5310-106">您可以使用此功能，開啟以其他編輯器建立的檔案，或開啟已重新命名的檔案，例如重新命名為 .bak 的 .sql 檔案備份。</span><span class="sxs-lookup"><span data-stu-id="d5310-106">You can use this feature to open files created with other editors, or to open files you have renamed, such as backups of .sql files that were renamed .bak.</span></span>  
  
 <span data-ttu-id="d5310-107">處理過程有兩個步驟。</span><span class="sxs-lookup"><span data-stu-id="d5310-107">There are two steps in the process.</span></span> <span data-ttu-id="d5310-108">先使副檔名與 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]相關聯，然後再使副檔名與特定程式碼編輯器相關聯。</span><span class="sxs-lookup"><span data-stu-id="d5310-108">First associate the extension with [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], and then associate the extension with a specific code editor.</span></span>  
  
### <a name="to-associate-a-new-file-extension-with-sql-server-management-studio"></a><span data-ttu-id="d5310-109">若要使新的副檔名與 SQL Server Management Studio 相關聯</span><span class="sxs-lookup"><span data-stu-id="d5310-109">To associate a new file extension with SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="d5310-110">在 **[開始]** 功能表上，指向 **[所有程式]** ，再指向 **[附屬應用程式]** ，然後按一下 **[Windows 檔案總管]** 。</span><span class="sxs-lookup"><span data-stu-id="d5310-110">On the **Start** menu, point to **All Programs**, point to **Accessories**, and then click **Windows Explorer**.</span></span>  
  
2.  <span data-ttu-id="d5310-111">在 Windows 檔案總管的 **[工具]** 功能表中，按一下 **[資料夾選項]** 。</span><span class="sxs-lookup"><span data-stu-id="d5310-111">In Windows Explorer, on the **Tools** menu, click **Folder Options**.</span></span>  
  
3.  <span data-ttu-id="d5310-112">在 **[資料夾選項]** 對話方塊的 **[檔案類型]** 索引標籤上，按一下 **[新增]** 。</span><span class="sxs-lookup"><span data-stu-id="d5310-112">In the **Folder Options** dialog box, on the **File Types** tab, click **New**.</span></span>  
  
4.  <span data-ttu-id="d5310-113">在 **[建立新副檔名]** 對話方塊的 **[副檔名]** 方塊中，輸入要與之相關聯的新副檔名，再按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="d5310-113">In the **Create New Extension** dialog box, in the **File Extension** box, type the new file extension that you want to associate, and then click **OK**.</span></span> <span data-ttu-id="d5310-114">請不要以句點為開頭輸入副檔名。</span><span class="sxs-lookup"><span data-stu-id="d5310-114">Do not start the extension with a period.</span></span>  
  
5.  <span data-ttu-id="d5310-115">在 **[註冊的檔案類型]** 方塊中，按一下新的副檔名，再按 **[變更]** 。</span><span class="sxs-lookup"><span data-stu-id="d5310-115">In the **Registered file** types box, click on your new extension, and then click **Change**.</span></span>  
  
6.  <span data-ttu-id="d5310-116">在 [開啟方式]  對話方塊中，按一下 [SSMS - SQL Server Management Studio]  ，再按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="d5310-116">In the **Open With** dialog box, click **SSMS - SQL Server Management Studio**, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="d5310-117">按一下 **[關閉]** ，以關閉 **[資料夾選項]** 對話方塊，然後再關閉 Windows 檔案總管。</span><span class="sxs-lookup"><span data-stu-id="d5310-117">Click **Close** to close the **Folder Options** dialog box, and then close Windows Explorer.</span></span>  
  
### <a name="to-associate-a-new-file-extension-with-a-code-editor-in-sql-server-management-studio"></a><span data-ttu-id="d5310-118">若要使新的副檔名與 SQL Server Management Studio 的程式碼編輯器相關聯</span><span class="sxs-lookup"><span data-stu-id="d5310-118">To associate a new file extension with a code editor in SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="d5310-119">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，於 **[工具]** 功能表按一下 **[選項]** 。</span><span class="sxs-lookup"><span data-stu-id="d5310-119">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], from the **Tools** menu, click **Options**.</span></span>  
  
2.  <span data-ttu-id="d5310-120">在 **[選項]** 對話方塊中，按一下 **[文字編輯器]** ，再按一下 **[副檔名]** 。</span><span class="sxs-lookup"><span data-stu-id="d5310-120">In the **Options** dialog box, click **Text Editor**, and then click **File Extension**.</span></span>  
  
3.  <span data-ttu-id="d5310-121">在 **[副檔名]** 方塊中，輸入新的副檔名。</span><span class="sxs-lookup"><span data-stu-id="d5310-121">In the **Extension** box, type your new file extension.</span></span>  
  
4.  <span data-ttu-id="d5310-122">在 **[編輯器]** 方塊中，依序按一下要用來開啟此檔案類型的程式碼編輯器、 **[新增]** 及 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="d5310-122">In the **Editor** box, click the code editor that you wish to use to open this file type, click **Add**, and then click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5310-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d5310-123">See Also</span></span>  
 [<span data-ttu-id="d5310-124">Ssms 公用程式</span><span class="sxs-lookup"><span data-stu-id="d5310-124">Ssms Utility</span></span>](../../ssms/ssms-utility.md)  
  
  
