---
title: 資料庫識別碼 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- regular identifiers [SQL Server]
- identifiers [SQL Server]
- names [SQL Server], identifiers
- identifiers [SQL Server], about identifiers
- SQL Server identifiers
- Transact-SQL identifiers
- database objects [SQL Server], names
ms.assetid: 171291bb-f57f-4ad1-8cea-0b092d5d150c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 347b20c12a0ac5edd82172741377617aa0fe12c6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595115"
---
# <a name="database-identifiers"></a><span data-ttu-id="3cf93-102">資料庫識別碼</span><span class="sxs-lookup"><span data-stu-id="3cf93-102">Database Identifiers</span></span>
  <span data-ttu-id="3cf93-103">資料庫物件名稱又稱為識別碼。</span><span class="sxs-lookup"><span data-stu-id="3cf93-103">The database object name is referred to as its identifier.</span></span> <span data-ttu-id="3cf93-104">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中的每一個物件都具有識別碼。</span><span class="sxs-lookup"><span data-stu-id="3cf93-104">Everything in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] can have an identifier.</span></span> <span data-ttu-id="3cf93-105">伺服器、資料庫與資料庫物件 (如資料表、檢視、資料行、索引、觸發程序、程序、條件約束、規則) 都可以有識別碼。</span><span class="sxs-lookup"><span data-stu-id="3cf93-105">Servers, databases, and database objects, such as tables, views, columns, indexes, triggers, procedures, constraints, and rules, can have identifiers.</span></span> <span data-ttu-id="3cf93-106">大多數物件都需要識別碼，但對部分物件如條件約束，則是選擇性的需求。</span><span class="sxs-lookup"><span data-stu-id="3cf93-106">Identifiers are required for most objects, but are optional for some objects such as constraints.</span></span>  
  
 <span data-ttu-id="3cf93-107">定義物件時會建立物件識別碼。</span><span class="sxs-lookup"><span data-stu-id="3cf93-107">An object identifier is created when the object is defined.</span></span> <span data-ttu-id="3cf93-108">之後就可以使用識別碼來參考物件。</span><span class="sxs-lookup"><span data-stu-id="3cf93-108">The identifier is then used to reference the object.</span></span> <span data-ttu-id="3cf93-109">例如，以下陳述式會建立具有識別碼 `TableX`的資料表，以及具有識別碼 `KeyCol` 與 `Description`的兩個資料行：</span><span class="sxs-lookup"><span data-stu-id="3cf93-109">For example, the following statement creates a table with the identifier `TableX`, and two columns with the identifiers `KeyCol` and `Description`:</span></span>  
  
```  
CREATE TABLE TableX  
(KeyCol INT PRIMARY KEY, Description nvarchar(80))  
```  
  
 <span data-ttu-id="3cf93-110">這個資料表也有一個未命名的條件約束。</span><span class="sxs-lookup"><span data-stu-id="3cf93-110">This table also has an unnamed constraint.</span></span> <span data-ttu-id="3cf93-111">`PRIMARY KEY` 條件約束沒有識別碼。</span><span class="sxs-lookup"><span data-stu-id="3cf93-111">The `PRIMARY KEY` constraint has no identifier.</span></span>  
  
 <span data-ttu-id="3cf93-112">識別碼的定序會隨定義的層級而不同。</span><span class="sxs-lookup"><span data-stu-id="3cf93-112">The collation of an identifier depends on the level at which it is defined.</span></span> <span data-ttu-id="3cf93-113">執行個體層級物件 (如登入和資料庫名稱) 的識別碼會被指派執行個體的預設定序。</span><span class="sxs-lookup"><span data-stu-id="3cf93-113">Identifiers of instance-level objects, such as logins and database names, are assigned the default collation of the instance.</span></span> <span data-ttu-id="3cf93-114">而資料庫中物件 (如資料表、檢視和資料行名稱) 的識別碼，則會被指派資料庫的預設定序。</span><span class="sxs-lookup"><span data-stu-id="3cf93-114">Identifiers of objects in a database, such as tables, views, and column names, are assigned the default collation of the database.</span></span> <span data-ttu-id="3cf93-115">例如，在區分大小寫定序的資料庫中，您可以建立名稱相同但大小寫不同的兩個資料表，但在不區分大小寫定序的資料庫中，就不可以建立名稱相同但大小寫不同的兩個資料表。</span><span class="sxs-lookup"><span data-stu-id="3cf93-115">For example, two tables with names that differ only in case can be created in a database that has case-sensitive collation, but cannot be created in a database that has case-insensitive collation.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3cf93-116">變數名稱或函數和預存程序的參數，必須符合 [!INCLUDE[tsql](../../includes/tsql-md.md)] 識別碼的規則。</span><span class="sxs-lookup"><span data-stu-id="3cf93-116">The names of variables, or the parameters of functions and stored procedures must comply with the rules for [!INCLUDE[tsql](../../includes/tsql-md.md)] identifiers.</span></span>  
  
## <a name="classes-of-identifiers"></a><span data-ttu-id="3cf93-117">識別碼的分類</span><span class="sxs-lookup"><span data-stu-id="3cf93-117">Classes of Identifiers</span></span>  
 <span data-ttu-id="3cf93-118">識別碼分為兩類：</span><span class="sxs-lookup"><span data-stu-id="3cf93-118">There are two classes of identifiers:</span></span>  
  
 <span data-ttu-id="3cf93-119">一般識別碼</span><span class="sxs-lookup"><span data-stu-id="3cf93-119">Regular identifiers</span></span>  
 <span data-ttu-id="3cf93-120">符合識別碼格式的規則。</span><span class="sxs-lookup"><span data-stu-id="3cf93-120">Comply with the rules for the format of identifiers.</span></span> <span data-ttu-id="3cf93-121">在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式中使用一般識別碼時不以符號分隔。</span><span class="sxs-lookup"><span data-stu-id="3cf93-121">Regular identifiers are not delimited when they are used in [!INCLUDE[tsql](../../includes/tsql-md.md)] statements.</span></span>  
  
```  
SELECT *  
FROM TableX  
WHERE KeyCol = 124  
```  
  
 <span data-ttu-id="3cf93-122">分隔識別碼</span><span class="sxs-lookup"><span data-stu-id="3cf93-122">Delimited identifiers</span></span>  
 <span data-ttu-id="3cf93-123">括在雙引號 (") 或方括號 ([ ]) 中的識別碼。</span><span class="sxs-lookup"><span data-stu-id="3cf93-123">Are enclosed in double quotation marks (") or brackets ([ ]).</span></span> <span data-ttu-id="3cf93-124">符合識別碼格式規則的識別碼不一定要以符號分隔。</span><span class="sxs-lookup"><span data-stu-id="3cf93-124">Identifiers that comply with the rules for the format of identifiers might not be delimited.</span></span> <span data-ttu-id="3cf93-125">例如：</span><span class="sxs-lookup"><span data-stu-id="3cf93-125">For example:</span></span>  
  
```  
SELECT *  
FROM [TableX]         --Delimiter is optional.  
WHERE [KeyCol] = 124  --Delimiter is optional.  
```  
  
 <span data-ttu-id="3cf93-126">不符合所有識別碼規則的識別碼在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式中一定要以符號分隔。</span><span class="sxs-lookup"><span data-stu-id="3cf93-126">Identifiers that do not comply with all the rules for identifiers must be delimited in a [!INCLUDE[tsql](../../includes/tsql-md.md)] statement.</span></span> <span data-ttu-id="3cf93-127">例如：</span><span class="sxs-lookup"><span data-stu-id="3cf93-127">For example:</span></span>  
  
```  
SELECT *  
FROM [My Table]      --Identifier contains a space and uses a reserved keyword.  
WHERE [order] = 10   --Identifier is a reserved keyword.  
```  
  
 <span data-ttu-id="3cf93-128">一般識別碼與分隔識別碼都必須包含在 1 到 128 個字元之間。</span><span class="sxs-lookup"><span data-stu-id="3cf93-128">Both regular and delimited identifiers must contain from 1 through 128 characters.</span></span> <span data-ttu-id="3cf93-129">至於本機暫存資料表，識別碼最多可有 116 個字元。</span><span class="sxs-lookup"><span data-stu-id="3cf93-129">For local temporary tables, the identifier can have a maximum of 116 characters.</span></span>  
  
## <a name="rules-for-regular-identifiers"></a><span data-ttu-id="3cf93-130">一般識別碼的規則</span><span class="sxs-lookup"><span data-stu-id="3cf93-130">Rules for Regular Identifiers</span></span>  
 <span data-ttu-id="3cf93-131">變數、函數及預存程序的名稱必須符合下列 [!INCLUDE[tsql](../../includes/tsql-md.md)] 識別碼規則。</span><span class="sxs-lookup"><span data-stu-id="3cf93-131">The names of variables, functions, and stored procedures must comply with the following rules for [!INCLUDE[tsql](../../includes/tsql-md.md)] identifiers.</span></span>  
  
1.  <span data-ttu-id="3cf93-132">第一個字元必須是以下任一項：</span><span class="sxs-lookup"><span data-stu-id="3cf93-132">The first character must be one of the following:</span></span>  
  
    -   <span data-ttu-id="3cf93-133">Unicode Standard 3.2 所定義的字母。</span><span class="sxs-lookup"><span data-stu-id="3cf93-133">A letter as defined by the Unicode Standard 3.2.</span></span> <span data-ttu-id="3cf93-134">Unicode 的字母定義包括從 a 到 z 以及從 A 到 Z 的拉丁字元，還有其他語系中的字母字元。</span><span class="sxs-lookup"><span data-stu-id="3cf93-134">The Unicode definition of letters includes Latin characters from a through z, from A through Z, and also letter characters from other languages.</span></span>  
  
    -   <span data-ttu-id="3cf93-135">底線 (_)、@ 符號或數字符號 (#)。</span><span class="sxs-lookup"><span data-stu-id="3cf93-135">The underscore (_), at sign (@), or number sign (#).</span></span>  
  
         <span data-ttu-id="3cf93-136">識別碼開頭的某些符號在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中有特殊意義。</span><span class="sxs-lookup"><span data-stu-id="3cf93-136">Certain symbols at the beginning of an identifier have special meaning in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="3cf93-137">以 @ 符號開頭的一般識別碼代表本機變數或參數，而且不能做為任何其他類型之物件的名稱。</span><span class="sxs-lookup"><span data-stu-id="3cf93-137">A regular identifier that starts with the at sign always denotes a local variable or parameter and cannot be used as the name of any other type of object.</span></span> <span data-ttu-id="3cf93-138">開頭為 # 符號的識別碼代表暫存資料表或程序。</span><span class="sxs-lookup"><span data-stu-id="3cf93-138">An identifier that starts with a number sign denotes a temporary table or procedure.</span></span> <span data-ttu-id="3cf93-139">開頭為兩個 ## 符號的識別碼代表全域暫存物件。</span><span class="sxs-lookup"><span data-stu-id="3cf93-139">An identifier that starts with double number signs (##) denotes a global temporary object.</span></span> <span data-ttu-id="3cf93-140">雖然 # 符號或兩個 ## 符號字元可做為其他類型之物件的名稱開頭，但是不建議此用法。</span><span class="sxs-lookup"><span data-stu-id="3cf93-140">Although the number sign or double number sign characters can be used to begin the names of other types of objects, we do not recommend this practice.</span></span>  
  
         <span data-ttu-id="3cf93-141">部分 [!INCLUDE[tsql](../../includes/tsql-md.md)] 功能的名稱會以兩個 @@ 符號為開頭。</span><span class="sxs-lookup"><span data-stu-id="3cf93-141">Some [!INCLUDE[tsql](../../includes/tsql-md.md)] functions have names that start with double at signs (@@).</span></span> <span data-ttu-id="3cf93-142">為了避免與這些功能產生混淆，不應該使用以 @@ 為開頭的名稱。</span><span class="sxs-lookup"><span data-stu-id="3cf93-142">To avoid confusion with these functions, you should not use names that start with @@.</span></span>  
  
2.  <span data-ttu-id="3cf93-143">可包含的後續字元如下：</span><span class="sxs-lookup"><span data-stu-id="3cf93-143">Subsequent characters can include the following:</span></span>  
  
    -   <span data-ttu-id="3cf93-144">Unicode Standard 3.2 所定義的字母。</span><span class="sxs-lookup"><span data-stu-id="3cf93-144">Letters as defined in the Unicode Standard 3.2.</span></span>  
  
    -   <span data-ttu-id="3cf93-145">其他基本拉丁文或其他國家 (地區) 字集中的十進位數字。</span><span class="sxs-lookup"><span data-stu-id="3cf93-145">Decimal numbers from either Basic Latin or other national scripts.</span></span>  
  
    -   <span data-ttu-id="3cf93-146">@ 符號、錢幣符號 ($)、數字符號或底線。</span><span class="sxs-lookup"><span data-stu-id="3cf93-146">The at sign, dollar sign ($), number sign, or underscore.</span></span>  
  
3.  <span data-ttu-id="3cf93-147">識別碼不得為 [!INCLUDE[tsql](../../includes/tsql-md.md)] 保留字。</span><span class="sxs-lookup"><span data-stu-id="3cf93-147">The identifier must not be a [!INCLUDE[tsql](../../includes/tsql-md.md)] reserved word.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="3cf93-148">會保留大小寫版本的保留字。</span><span class="sxs-lookup"><span data-stu-id="3cf93-148">reserves both the uppercase and lowercase versions of reserved words.</span></span> <span data-ttu-id="3cf93-149">在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式中使用識別碼時，如果識別碼與上述規則不符，您必須使用雙引號 ("") 或方括號 ([]) 加以分隔。</span><span class="sxs-lookup"><span data-stu-id="3cf93-149">When identifiers are used in [!INCLUDE[tsql](../../includes/tsql-md.md)] statements, the identifiers that do not comply with these rules must be delimited by double quotation marks or brackets.</span></span> <span data-ttu-id="3cf93-150">保留字取決於資料庫相容性層級。</span><span class="sxs-lookup"><span data-stu-id="3cf93-150">The words that are reserved depend on the database compatibility level.</span></span> <span data-ttu-id="3cf93-151">這個層級可以使用 [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level) 陳述式加以設定。</span><span class="sxs-lookup"><span data-stu-id="3cf93-151">This level can be set by using the [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level) statement.</span></span>  
  
4.  <span data-ttu-id="3cf93-152">不允許內嵌的空格或特殊字元。</span><span class="sxs-lookup"><span data-stu-id="3cf93-152">Embedded spaces or special characters are not allowed.</span></span>  
  
5.  <span data-ttu-id="3cf93-153">不允許補充字元。</span><span class="sxs-lookup"><span data-stu-id="3cf93-153">Supplementary characters are not allowed.</span></span>  
  
 <span data-ttu-id="3cf93-154">在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式中使用識別碼時，如果識別碼與上述規則不符，您必須使用雙引號 ("") 或方括號 ([]) 加以分隔。</span><span class="sxs-lookup"><span data-stu-id="3cf93-154">When identifiers are used in [!INCLUDE[tsql](../../includes/tsql-md.md)] statements, the identifiers that do not comply with these rules must be delimited by double quotation marks or brackets.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3cf93-155">某些有關於一般識別碼格式的規則，取決於資料庫的相容性層級。</span><span class="sxs-lookup"><span data-stu-id="3cf93-155">Some rules for the format of regular identifiers depend on the database compatibility level.</span></span> <span data-ttu-id="3cf93-156">您可以使用 [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level)來設定這個層級。</span><span class="sxs-lookup"><span data-stu-id="3cf93-156">This level can be set by using [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3cf93-157">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3cf93-157">See Also</span></span>  
 <span data-ttu-id="3cf93-158">[ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="3cf93-158">[ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql) </span></span>  
 <span data-ttu-id="3cf93-159">[CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="3cf93-159">[CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) </span></span>  
 <span data-ttu-id="3cf93-160">[CREATE DEFAULT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-default-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="3cf93-160">[CREATE DEFAULT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-default-transact-sql) </span></span>  
 <span data-ttu-id="3cf93-161">[CREATE PROCEDURE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-procedure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="3cf93-161">[CREATE PROCEDURE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-procedure-transact-sql) </span></span>  
 <span data-ttu-id="3cf93-162">[CREATE RULE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-rule-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="3cf93-162">[CREATE RULE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-rule-transact-sql) </span></span>  
 <span data-ttu-id="3cf93-163">[CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="3cf93-163">[CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql) </span></span>  
 <span data-ttu-id="3cf93-164">[CREATE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-trigger-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="3cf93-164">[CREATE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-trigger-transact-sql) </span></span>  
 <span data-ttu-id="3cf93-165">[CREATE VIEW &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-view-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="3cf93-165">[CREATE VIEW &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-view-transact-sql) </span></span>  
 <span data-ttu-id="3cf93-166">[DECLARE @local_variable &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/declare-local-variable-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="3cf93-166">[DECLARE @local_variable &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/declare-local-variable-transact-sql) </span></span>  
 <span data-ttu-id="3cf93-167">[DELETE &#40;Transact-SQL&#41;](/sql/t-sql/statements/delete-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="3cf93-167">[DELETE &#40;Transact-SQL&#41;](/sql/t-sql/statements/delete-transact-sql) </span></span>  
 <span data-ttu-id="3cf93-168">[INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/insert-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="3cf93-168">[INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/insert-transact-sql) </span></span>  
 <span data-ttu-id="3cf93-169">[保留關鍵字 &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reserved-keywords-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="3cf93-169">[Reserved Keywords &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reserved-keywords-transact-sql) </span></span>  
 <span data-ttu-id="3cf93-170">[SELECT &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="3cf93-170">[SELECT &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql) </span></span>  
 [<span data-ttu-id="3cf93-171">UPDATE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="3cf93-171">UPDATE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/queries/update-transact-sql)  
  
  
