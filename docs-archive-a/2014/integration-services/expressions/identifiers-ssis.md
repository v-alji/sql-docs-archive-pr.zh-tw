---
title: 識別碼 (SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- regular identifiers [Integration Services]
- variables [Integration Services], expressions
- identifiers [Integration Services]
- expressions [Integration Services], variables
- lineage identifiers
- columns [Integration Services], identifiers
- names [Integration Services]
- expressions [Integration Services], identifiers
- qualified identifiers [Integration Services]
ms.assetid: 56af984d-88b4-4db8-b6a2-6b07315a699e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 751830d30f26e9b182b3b926549760d1df517914
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701458"
---
# <a name="identifiers-ssis"></a><span data-ttu-id="efac6-102">識別碼 (SSIS)</span><span class="sxs-lookup"><span data-stu-id="efac6-102">Identifiers (SSIS)</span></span>
  <span data-ttu-id="efac6-103">在運算式中，識別碼是可供運算的資料行和變數。</span><span class="sxs-lookup"><span data-stu-id="efac6-103">In expressions, identifiers are columns and variables that are available to the operation.</span></span> <span data-ttu-id="efac6-104">運算式可使用一般和限定識別碼。</span><span class="sxs-lookup"><span data-stu-id="efac6-104">Expressions can use regular and qualified identifiers.</span></span>  
  
## <a name="regular-identifiers"></a><span data-ttu-id="efac6-105">一般識別碼</span><span class="sxs-lookup"><span data-stu-id="efac6-105">Regular Identifiers</span></span>  
 <span data-ttu-id="efac6-106">一般識別碼是不需要額外限定詞的識別碼。</span><span class="sxs-lookup"><span data-stu-id="efac6-106">A regular identifier is an identifier that needs no additional qualifiers.</span></span> <span data-ttu-id="efac6-107">例如， **AdventureWorks**資料庫的 **Contacts** 資料表中的 **MiddleName** 資料行即為一般識別碼。</span><span class="sxs-lookup"><span data-stu-id="efac6-107">For example, **MiddleName**, a column in the **Contacts** table of the **AdventureWorks** database, is a regular identifier.</span></span>  
  
 <span data-ttu-id="efac6-108">一般識別碼的命名必須按照下列規則：</span><span class="sxs-lookup"><span data-stu-id="efac6-108">The naming of regular identifiers must follow these rules:</span></span>  
  
-   <span data-ttu-id="efac6-109">名稱的第一個字元必須是 Unicode Standard 2.0 所定義的字母，或者底線 (_)。</span><span class="sxs-lookup"><span data-stu-id="efac6-109">The first character of the name must be a letter as defined by the Unicode Standard 2.0, or an underscore (_).</span></span>  
  
-   <span data-ttu-id="efac6-110">後續的字元可以是 Unicode Standard 2.0 所定義的字母或數字、底線 (_)、\@、$ 及 # 字元。</span><span class="sxs-lookup"><span data-stu-id="efac6-110">Subsequent characters can be letters or numbers as defined in the Unicode Standard 2.0, the underscore (_), \@, $, and # characters.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="efac6-111">除了列出的字元之外，內嵌的空格和特殊字元在一般識別碼中無效。</span><span class="sxs-lookup"><span data-stu-id="efac6-111">Embedded spaces and special characters, other than the ones listed, are not valid in regular identifiers.</span></span> <span data-ttu-id="efac6-112">若要使用空格和特殊字元，您必須使用限定識別碼，而非一般識別碼。</span><span class="sxs-lookup"><span data-stu-id="efac6-112">In order to use spaces and special characters, you must use a qualified identifier instead of a regular identifier.</span></span>  
  
## <a name="qualified-identifiers"></a><span data-ttu-id="efac6-113">限定識別碼</span><span class="sxs-lookup"><span data-stu-id="efac6-113">Qualified Identifiers</span></span>  
 <span data-ttu-id="efac6-114">限定識別碼是以方括號分隔的識別碼。</span><span class="sxs-lookup"><span data-stu-id="efac6-114">A qualified identifier is an identifier that is delimited by brackets.</span></span> <span data-ttu-id="efac6-115">識別碼可能需要分隔符號，因為識別碼的名稱包含空白，或是因為識別碼名稱的開頭不是字母或底線字元。</span><span class="sxs-lookup"><span data-stu-id="efac6-115">An identifier may require a delimiter because the name of the identifier includes spaces, or because the identifier name does not begin with either a letter or the underscore character.</span></span> <span data-ttu-id="efac6-116">例如， **Middle Name** 資料行名稱必須以方括號限定，並於運算式中撰寫為 [Middle Name]。</span><span class="sxs-lookup"><span data-stu-id="efac6-116">For example, the column name **Middle Name** must be qualified by brackets and written as [Middle Name] in an expression.</span></span>  
  
 <span data-ttu-id="efac6-117">如果識別碼的名稱包含空白，或如果名稱不是有效的一般識別碼名稱，則該識別碼必須加以限定。</span><span class="sxs-lookup"><span data-stu-id="efac6-117">If the name of the identifier includes spaces, or if the name is not a valid regular identifier name, the identifier must be qualified.</span></span> <span data-ttu-id="efac6-118">運算式評估工具會使用左、右方括號 ([]) 限定識別碼。</span><span class="sxs-lookup"><span data-stu-id="efac6-118">The expression evaluator uses the opening and closing ([]) brackets to qualify identifiers.</span></span> <span data-ttu-id="efac6-119">方括號會放在字串的第一個和最後一個位置。</span><span class="sxs-lookup"><span data-stu-id="efac6-119">The brackets are put in the first and the last position of the string.</span></span> <span data-ttu-id="efac6-120">例如，識別碼 5$> 會變成 [5$>]。</span><span class="sxs-lookup"><span data-stu-id="efac6-120">For example, the identifier 5$> becomes [5$>].</span></span> <span data-ttu-id="efac6-121">方括號可用於資料行名稱、變數名稱，以及函數名稱。</span><span class="sxs-lookup"><span data-stu-id="efac6-121">Brackets can be used with column names, variable names, and function names.</span></span>  
  
 <span data-ttu-id="efac6-122">如果您使用 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師對話方塊建立運算式，則一般識別碼會自動加上方括號。</span><span class="sxs-lookup"><span data-stu-id="efac6-122">If you build expressions using the [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer dialog boxes, regular identifiers are automatically enclosed in brackets.</span></span> <span data-ttu-id="efac6-123">不過，只有在名稱包含無效字元時才需要方括號。</span><span class="sxs-lookup"><span data-stu-id="efac6-123">However, brackets are required only if the name include invalid characters.</span></span> <span data-ttu-id="efac6-124">例如，名為 **MiddleName** 的資料行是有效的資料行，不需要方括號。</span><span class="sxs-lookup"><span data-stu-id="efac6-124">For example, the column named **MiddleName** is valid without brackets.</span></span>  
  
 <span data-ttu-id="efac6-125">您無法參考運算式中包含方括號的資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="efac6-125">You cannot reference column names that include brackets in expressions.</span></span> <span data-ttu-id="efac6-126">例如，資料行名稱 **Column[1]** 不可用於運算式中。</span><span class="sxs-lookup"><span data-stu-id="efac6-126">For example, the column name **Column[1]** cannot be used in an expression.</span></span> <span data-ttu-id="efac6-127">若要在運算式中使用資料行，則必須將它重新命名為不含方括號的名稱。</span><span class="sxs-lookup"><span data-stu-id="efac6-127">To use the column in an expression it must be renamed to a name without brackets.</span></span>  
  
## <a name="lineage-identifiers"></a><span data-ttu-id="efac6-128">歷程識別碼</span><span class="sxs-lookup"><span data-stu-id="efac6-128">Lineage Identifiers</span></span>  
 <span data-ttu-id="efac6-129">運算式可以使用歷程識別碼來參考資料行。</span><span class="sxs-lookup"><span data-stu-id="efac6-129">Expressions can use lineage identifiers to refer to columns.</span></span> <span data-ttu-id="efac6-130">當您初次建立封裝時，會自動指派歷程識別碼。</span><span class="sxs-lookup"><span data-stu-id="efac6-130">The lineage identifiers are assigned automatically when you first create the package.</span></span> <span data-ttu-id="efac6-131">您可以在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師中，於 [進階編輯器] 對話方塊的 [資料行屬性] 索引標籤上檢視資料行的歷程識別碼。</span><span class="sxs-lookup"><span data-stu-id="efac6-131">You can view the lineage identifier for a column on the **Column Properties** tab of the **Advanced Editor** dialog box in the [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="efac6-132">如果您使用資料行本身的歷程識別碼參考該資料行，則識別碼前面必須包含井字號 (#) 字元。</span><span class="sxs-lookup"><span data-stu-id="efac6-132">If you refer to a column using its lineage identifier, the identifier must include the pound (#) character prefix.</span></span> <span data-ttu-id="efac6-133">例如，歷程識別碼 147 的資料行必須以 #147 的形式參考。</span><span class="sxs-lookup"><span data-stu-id="efac6-133">For example, a column with the lineage identifier 147 must be referenced as #147.</span></span>  
  
 <span data-ttu-id="efac6-134">如果運算式剖析成功，則運算式評估工具會以對話方塊中的資料行名稱取代歷程識別碼。</span><span class="sxs-lookup"><span data-stu-id="efac6-134">If an expression parses successfully, the expression evaluator replaces the lineage identifiers with column names in the dialog box.</span></span>  
  
## <a name="unique-column-names"></a><span data-ttu-id="efac6-135">唯一資料行名稱</span><span class="sxs-lookup"><span data-stu-id="efac6-135">Unique Column Names</span></span>  
 <span data-ttu-id="efac6-136">封裝中使用的多個元件可公開同名的資料行。</span><span class="sxs-lookup"><span data-stu-id="efac6-136">Multiple components used in a package can expose columns with the same name.</span></span> <span data-ttu-id="efac6-137">如果這些資料行是在運算式中使用，則須使其意義明確，運算式才能成功剖析。</span><span class="sxs-lookup"><span data-stu-id="efac6-137">If these columns are used in expressions, they must be disambiguated before the expressions can be parsed successfully.</span></span> <span data-ttu-id="efac6-138">運算式評估工具支援用來識別資料行來源的虛線標記法。</span><span class="sxs-lookup"><span data-stu-id="efac6-138">The expression evaluator supports the dotted notation for identifying the source of the column.</span></span> <span data-ttu-id="efac6-139">例如，兩個名為 **Age** 的資料行會變成 **FlatFileSource.Age** 和 **OLEDBSource.Age**，這表示其來源為 FlatFileSource 或 OLEDBSource。</span><span class="sxs-lookup"><span data-stu-id="efac6-139">For example, two columns named **Age** become **FlatFileSource.Age** and **OLEDBSource.Age**, which indicates that their sources are FlatFileSource or OLEDBSource.</span></span> <span data-ttu-id="efac6-140">剖析器會將完整名稱視為單一資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="efac6-140">The parser treats the fully qualified name as a single column name.</span></span>  
  
 <span data-ttu-id="efac6-141">來源元件名稱和資料行名稱會分別加以限定。</span><span class="sxs-lookup"><span data-stu-id="efac6-141">Source component names and column names are qualified separately.</span></span> <span data-ttu-id="efac6-142">下列範例說明，在虛線標記法中方括號的有效用法：</span><span class="sxs-lookup"><span data-stu-id="efac6-142">The following examples show valid use of brackets in a dotted notation:</span></span>  
  
-   <span data-ttu-id="efac6-143">來源元件名稱包含空白。</span><span class="sxs-lookup"><span data-stu-id="efac6-143">The source component name includes spaces.</span></span>  
  
    ```  
    [MySo urce].Age  
    ```  
  
-   <span data-ttu-id="efac6-144">資料行名稱的第一個字元無效。</span><span class="sxs-lookup"><span data-stu-id="efac6-144">The first character in the column name is not valid.</span></span>  
  
    ```  
    MySource.[#Age]  
    ```  
  
-   <span data-ttu-id="efac6-145">來源元件和資料行名稱含有無效字元。</span><span class="sxs-lookup"><span data-stu-id="efac6-145">The source component and the column names contain invalid characters.</span></span>  
  
    ```  
    [MySource?].[#Age]  
    ```  
  
> [!IMPORTANT]  
>  <span data-ttu-id="efac6-146">如果虛線標記法中的兩個元素都加上一對方括號，則運算式評估工具會將這對元素解譯為單一識別碼，而非來源資料行組合。</span><span class="sxs-lookup"><span data-stu-id="efac6-146">If both elements in dotted notation are enclosed in one pair of brackets, the expression evaluator interprets the pair as a single identifier, not a source-column combination.</span></span>  
  
## <a name="variables-in-expressions"></a><span data-ttu-id="efac6-147">運算式中的變數</span><span class="sxs-lookup"><span data-stu-id="efac6-147">Variables in Expressions</span></span>  
 <span data-ttu-id="efac6-148">在運算式中參考變數時，必須包括 \@ 前置詞。</span><span class="sxs-lookup"><span data-stu-id="efac6-148">Variables, when referenced in expressions, must include the \@ prefix.</span></span> <span data-ttu-id="efac6-149">例如，**Counter** 變數是使用 \@Counter 來參考。</span><span class="sxs-lookup"><span data-stu-id="efac6-149">For example, the **Counter** variable is referenced by using \@Counter.</span></span> <span data-ttu-id="efac6-150">\@ 字元並非變數名稱的一部分；該字元僅供運算式評估工具用來識別變數。</span><span class="sxs-lookup"><span data-stu-id="efac6-150">The \@ character is not part of the variable name; it only identifies the variable to the expression evaluator.</span></span> <span data-ttu-id="efac6-151">如果您使用 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計工具提供的對話方塊建置運算式，則 \@ 字元會自動加入變數名稱中。</span><span class="sxs-lookup"><span data-stu-id="efac6-151">If you build expressions by using the dialog boxes that [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer provides, the \@ character is automatically added to the variable name.</span></span> <span data-ttu-id="efac6-152">在 \@ 字元和變數名稱之間加入空白是無效的格式。</span><span class="sxs-lookup"><span data-stu-id="efac6-152">It is not valid to include spaces between the \@ character and the variable name.</span></span>  
  
 <span data-ttu-id="efac6-153">變數名稱與其他一般識別碼的名稱遵循相同的規則：</span><span class="sxs-lookup"><span data-stu-id="efac6-153">Variable names follow the same rules as those for other regular identifiers:</span></span>  
  
-   <span data-ttu-id="efac6-154">名稱的第一個字元必須是 Unicode Standard 2.0 所定義的字母，或者底線 (_)。</span><span class="sxs-lookup"><span data-stu-id="efac6-154">The first character of the name must be a letter as defined by the Unicode Standard 2.0, or an underscore (_).</span></span>  
  
-   <span data-ttu-id="efac6-155">後續的字元可以是 Unicode Standard 2.0 所定義的字母或數字、底線 (_)、\@、$ 及 # 字元。</span><span class="sxs-lookup"><span data-stu-id="efac6-155">Subsequent characters can be letters or numbers as defined in the Unicode Standard 2.0, the underscore (_), \@, $, and # characters.</span></span>  
  
 <span data-ttu-id="efac6-156">如果變數名稱包含所列出字元以外的字元，則變數必須加上方括號。</span><span class="sxs-lookup"><span data-stu-id="efac6-156">If a variable name contains characters other than those listed, the variable must be enclosed in brackets.</span></span> <span data-ttu-id="efac6-157">例如，含空白的變數名稱必須加上方括號。</span><span class="sxs-lookup"><span data-stu-id="efac6-157">For example, variable names with spaces must be enclosed in brackets.</span></span> <span data-ttu-id="efac6-158">左方括弧會接在 \@ 字元後面。</span><span class="sxs-lookup"><span data-stu-id="efac6-158">The opening bracket follows the \@ character.</span></span> <span data-ttu-id="efac6-159">例如，**My Name** 變數會以 \@[My Name] 的形式參考。</span><span class="sxs-lookup"><span data-stu-id="efac6-159">For example, the **My Name** variable is referenced as \@[My Name].</span></span> <span data-ttu-id="efac6-160">不可在變數名稱和方括號之間加入空白。</span><span class="sxs-lookup"><span data-stu-id="efac6-160">It is not valid to include spaces between the variable name and the brackets.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="efac6-161">使用者定義變數和系統變數的名稱會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="efac6-161">The names of user-defined and system variables are case-sensitive.</span></span>  
  
## <a name="unique-variable-names"></a><span data-ttu-id="efac6-162">唯一變數名稱</span><span class="sxs-lookup"><span data-stu-id="efac6-162">Unique Variable Names</span></span>  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="efac6-163">支援自訂變數並提供一組系統變數。</span><span class="sxs-lookup"><span data-stu-id="efac6-163">supports custom variables and provides a set of system variables.</span></span> <span data-ttu-id="efac6-164">自訂變數預設屬於 **使用者** 命名空間，而系統變數則屬於 **系統** 命名空間。</span><span class="sxs-lookup"><span data-stu-id="efac6-164">By default, custom variables belong to the **User** namespace, and system variables belong to the **System** namespace.</span></span> <span data-ttu-id="efac6-165">您可以為自訂變數建立額外的命名空間，並更新命名空間的名稱，以符合應用程式的需要。</span><span class="sxs-lookup"><span data-stu-id="efac6-165">You can create additional namespaces for custom variables and update the namespace names to suit the needs of your application.</span></span> <span data-ttu-id="efac6-166">運算式產生器會列出所有命名空間中適用的變數。</span><span class="sxs-lookup"><span data-stu-id="efac6-166">The expression builder lists in-scope variables in all namespaces.</span></span>  
  
 <span data-ttu-id="efac6-167">所有變數都有範圍且屬於命名空間。</span><span class="sxs-lookup"><span data-stu-id="efac6-167">All variables have scope and belong to a namespace.</span></span> <span data-ttu-id="efac6-168">變數擁有封裝範圍，或封裝中容器或工作的範圍。</span><span class="sxs-lookup"><span data-stu-id="efac6-168">A variable has package scope or the scope of a container or task in the package.</span></span> <span data-ttu-id="efac6-169">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師中的運算式產生器只會列出範圍內的變數。</span><span class="sxs-lookup"><span data-stu-id="efac6-169">The expression builder in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer lists only the in-scope variables.</span></span> <span data-ttu-id="efac6-170">如需詳細資訊，請參閱 [Integration Services &#40;SSIS&#41; 變數](../integration-services-ssis-variables.md)和[在封裝中使用變數](../use-variables-in-packages.md)。</span><span class="sxs-lookup"><span data-stu-id="efac6-170">For more information, see [Integration Services &#40;SSIS&#41; Variables](../integration-services-ssis-variables.md) and [Use Variables in Packages](../use-variables-in-packages.md).</span></span>  
  
 <span data-ttu-id="efac6-171">運算式中使用的變數必須有唯一名稱，運算式評估工具才能正確評估運算式。</span><span class="sxs-lookup"><span data-stu-id="efac6-171">Variables used in expressions must have unique names for the expression evaluator to evaluate the expression correctly.</span></span> <span data-ttu-id="efac6-172">如果封裝使用多個同名的變數，則其命名空間必須有所區別。</span><span class="sxs-lookup"><span data-stu-id="efac6-172">If a package uses multiple variables with the same name, their namespaces must be different.</span></span> [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="efac6-173">提供由兩個冒號 (::) 組成的命名空間解析運算子，可用於指出變數所屬的命名空間。</span><span class="sxs-lookup"><span data-stu-id="efac6-173">provides a namespace resolution operator, consisting of two colons (::), for qualifying a variable with its namespace.</span></span> <span data-ttu-id="efac6-174">例如，下列運算式使用兩個名稱為 **Count**的變數；其中一個屬於 **使用者** 命名空間，另一個屬於 **MyNamespace** 命名空間。</span><span class="sxs-lookup"><span data-stu-id="efac6-174">For example, the following expression uses two variables named **Count**; one belongs to the **User** namespace and one to the **MyNamespace** namespace.</span></span>  
  
```  
@[User::Count] > @[MyNamespace::Count]  
```  
  
> [!IMPORTANT]  
>  <span data-ttu-id="efac6-175">您必須將命名空間和限定變數名稱的組合加上方括號，運算式評估工具才能辨認該變數。</span><span class="sxs-lookup"><span data-stu-id="efac6-175">You must enclose the combination of namespace and qualified variable name in brackets for the expression evaluator to recognize the variable.</span></span>  
  
 <span data-ttu-id="efac6-176">如果**使用者**命名空間中的**count**值為10，而**MyNamespace**中的**count**值為2，則運算式會評估為，因為運算式評估工具會辨識 `true` 兩個不同的變數。</span><span class="sxs-lookup"><span data-stu-id="efac6-176">If the value of **Count** in the **User** namespace is 10 and the value of **Count** in **MyNamespace** is 2, the expression evaluates to `true` because the expression evaluator recognizes two different variables.</span></span>  
  
 <span data-ttu-id="efac6-177">即使變數名稱不是唯一的，也不會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="efac6-177">If variable names are not unique, no error occurs.</span></span> <span data-ttu-id="efac6-178">但運算式評估工具只會使用一個變數執行個體評估運算式，並傳回不正確的結果。</span><span class="sxs-lookup"><span data-stu-id="efac6-178">Instead, the expression evaluator uses only one instance of the variable to evaluate the expression and returns an incorrect result.</span></span> <span data-ttu-id="efac6-179">例如，下列運算式是要用來比較兩個不同**計數**變數的值 (10 和 2) ，但運算式會評估為， `false` 因為運算式評估工具使用相同的**count**變數實例兩次。</span><span class="sxs-lookup"><span data-stu-id="efac6-179">For example, the following expression was intended to compare the values (10 and 2) for two separate **Count** variables but the expression evaluates to `false` because the expression evaluator uses the same instance of the **Count** variable two times.</span></span>  
  
```  
@Count > @Count  
```  
  
## <a name="related-content"></a><span data-ttu-id="efac6-180">相關內容</span><span class="sxs-lookup"><span data-stu-id="efac6-180">Related Content</span></span>  
 <span data-ttu-id="efac6-181">pragmaticworks.com 上的技術文件： [SSIS 運算式小抄](https://pragmaticworks.com/Resources/Cheat-Sheets/SSIS-Expression-Cheat-Sheet)</span><span class="sxs-lookup"><span data-stu-id="efac6-181">Technical article, [SSIS Expression Cheat Sheet](https://pragmaticworks.com/Resources/Cheat-Sheets/SSIS-Expression-Cheat-Sheet), on pragmaticworks.com</span></span>  
  
  
