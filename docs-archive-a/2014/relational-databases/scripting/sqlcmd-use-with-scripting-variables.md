---
title: 以指令碼變數使用 sqlcmd
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- scripts [SQL Server], sqlcmd utility
- variables [SQL Server], scripts
- scripting variables [SQL Server]
- sqlcmd utility, scripts
- setvar command
ms.assetid: 793495ca-cfc9-498d-8276-c44a5d09a92c
author: rothja
ms.author: jroth
ms.openlocfilehash: 8443cb400dc099726ba75bfcec2d38cee4ee2dff
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598810"
---
# <a name="use-sqlcmd-with-scripting-variables"></a><span data-ttu-id="085f7-102">以指令碼變數使用 sqlcmd</span><span class="sxs-lookup"><span data-stu-id="085f7-102">Use sqlcmd with Scripting Variables</span></span>
  <span data-ttu-id="085f7-103">用於指令碼中的變數稱為指令碼變數。</span><span class="sxs-lookup"><span data-stu-id="085f7-103">Variables that are used in scripts are called scripting variables.</span></span> <span data-ttu-id="085f7-104">指令碼變數可讓一個指令碼使用於多個狀況中。</span><span class="sxs-lookup"><span data-stu-id="085f7-104">Scripting variables enable one script to be used in multiple scenarios.</span></span> <span data-ttu-id="085f7-105">例如，如果您想要針對多個伺服器執行一個指令碼，而不針對每個伺服器修改指令碼，您可以使用指令碼變數來代表伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="085f7-105">For example, if you want to run one script against multiple servers, instead of modifying the script for each server, you can use a scripting variable for the server name.</span></span> <span data-ttu-id="085f7-106">只要變更提供給指令碼變數的伺服器名稱，相同的指令碼就可以在不同的伺服器上執行。</span><span class="sxs-lookup"><span data-stu-id="085f7-106">By changing the server name supplied to the scripting variable, the same script can be executed on different servers.</span></span>  
  
 <span data-ttu-id="085f7-107">指令碼變數可以使用 **setvar** 命令來明確定義，或使用 **sqlcmd-v** 選項來隱含定義。</span><span class="sxs-lookup"><span data-stu-id="085f7-107">Scripting variables can be defined explicitly by using the **setvar** command, or implicitly by using the **sqlcmd-v** option.</span></span>  
  
 <span data-ttu-id="085f7-108">本主題也包含在 Cmd.exe 命令提示字元中使用 **SET**來定義環境變數的範例。</span><span class="sxs-lookup"><span data-stu-id="085f7-108">This topic also includes examples defining environmental variables at the Cmd.exe command prompt by using **SET**.</span></span>  
  
## <a name="setting-scripting-variables-by-using-the-setvar-command"></a><span data-ttu-id="085f7-109">使用 setvar 命令設定指令碼變數</span><span class="sxs-lookup"><span data-stu-id="085f7-109">Setting Scripting Variables by Using the setvar Command</span></span>  
 <span data-ttu-id="085f7-110">**setvar** 命令可用來定義指令碼變數。</span><span class="sxs-lookup"><span data-stu-id="085f7-110">The **setvar** command is used to define scripting variables.</span></span> <span data-ttu-id="085f7-111">使用 **setvar** 命令定義的變數會儲存在內部。</span><span class="sxs-lookup"><span data-stu-id="085f7-111">Variables that are defined by using the **setvar** command are stored internally.</span></span> <span data-ttu-id="085f7-112">指令碼變數不應與在命令提示字元中使用 **SET**所定義的環境變數產生混淆。</span><span class="sxs-lookup"><span data-stu-id="085f7-112">Scripting variables should not be confused with environment variables that are defined at the command prompt by using **SET**.</span></span> <span data-ttu-id="085f7-113">如果指令碼參考非環境變數的變數，或不是使用 **setvar**所定義的變數，則會傳回錯誤訊息並停止執行指令碼。</span><span class="sxs-lookup"><span data-stu-id="085f7-113">If a script references a variable that is not an environment variable or is not defined by using **setvar**, an error message is returned and the execution of the script will stop.</span></span> <span data-ttu-id="085f7-114">如需詳細資訊，請參閱 **sqlcmd 公用程式** 中的 [-b](../../tools/sqlcmd-utility.md)選項。</span><span class="sxs-lookup"><span data-stu-id="085f7-114">For more information, see the **-b** option in [sqlcmd Utility](../../tools/sqlcmd-utility.md).</span></span>  
  
## <a name="variable-precedence-low-to-high"></a><span data-ttu-id="085f7-115">變數優先順序 (由低至高)</span><span class="sxs-lookup"><span data-stu-id="085f7-115">Variable Precedence (Low to High)</span></span>  
 <span data-ttu-id="085f7-116">如果有多個類型的變數具有相同的名稱，會使用具有最高優先順序的變數。</span><span class="sxs-lookup"><span data-stu-id="085f7-116">If more than one type of variable has the same name, the variable with the highest precedence is used.</span></span>  
  
1.  <span data-ttu-id="085f7-117">系統層級環境變數</span><span class="sxs-lookup"><span data-stu-id="085f7-117">System level environmental variables</span></span>  
  
2.  <span data-ttu-id="085f7-118">使用者層級環境變數</span><span class="sxs-lookup"><span data-stu-id="085f7-118">User level environmental variables</span></span>  
  
3.  <span data-ttu-id="085f7-119">在啟動**SET X=Y**之前，於命令提示字元設定命令殼層 ( **SET X=Y**)</span><span class="sxs-lookup"><span data-stu-id="085f7-119">Command shell (**SET X=Y**) set at command prompt before starting **sqlcmd**</span></span>  
  
4.  <span data-ttu-id="085f7-120">**sqlcmd-v** X=Y</span><span class="sxs-lookup"><span data-stu-id="085f7-120">**sqlcmd-v** X=Y</span></span>  
  
5.  <span data-ttu-id="085f7-121">**:Setvar** X Y</span><span class="sxs-lookup"><span data-stu-id="085f7-121">**:Setvar** X Y</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="085f7-122">若要檢視環境變數，請在 [控制台]  中開啟 [系統]  ，然後按一下 [進階]  索引標籤。</span><span class="sxs-lookup"><span data-stu-id="085f7-122">To view the environmental variables, in **Control Panel**, open **System**, and then click the **Advanced** tab.</span></span>  
  
## <a name="implicitly-setting-scripting-variables"></a><span data-ttu-id="085f7-123">隱含設定指令碼變數</span><span class="sxs-lookup"><span data-stu-id="085f7-123">Implicitly Setting Scripting Variables</span></span>  
 <span data-ttu-id="085f7-124">當您透過含有 **sqlcmd** 相關變數的選項啟動 **sqlcmd** 時，會將 **sqlcmd** 變數隱含設定為使用該選項所指定的值。</span><span class="sxs-lookup"><span data-stu-id="085f7-124">When you start **sqlcmd** with an option that has a related **sqlcmd** variable, the **sqlcmd** variable is set implicitly to the value that is specified by using the option.</span></span> <span data-ttu-id="085f7-125">在下列範例中， `sqlcmd` 透過 `-l` 選項啟動。</span><span class="sxs-lookup"><span data-stu-id="085f7-125">In the following example, `sqlcmd` is started with the `-l` option.</span></span> <span data-ttu-id="085f7-126">這將會隱含地設定 SQLLOGINTIMEOUT 變數。</span><span class="sxs-lookup"><span data-stu-id="085f7-126">This implicitly sets the SQLLOGINTIMEOUT variable.</span></span>  
  
 `c:\> sqlcmd -l 60`  
  
 <span data-ttu-id="085f7-127">您也可以使用 **-v** 選項來設定存在於指令碼中的指令碼變數。</span><span class="sxs-lookup"><span data-stu-id="085f7-127">You can also use the **-v** option to set a scripting variable that exists in a script.</span></span> <span data-ttu-id="085f7-128">在下列指令碼 (檔名為 `testscript.sql`) 中， `ColumnName` 為指令碼變數。</span><span class="sxs-lookup"><span data-stu-id="085f7-128">In the following script (the file name is `testscript.sql`), `ColumnName` is a scripting variable.</span></span>  
  
 `USE AdventureWorks2012;`  
  
 `SELECT x.$(ColumnName)`  
  
 `FROM Person.Person x`  
  
 <span data-ttu-id="085f7-129">`WHERE c.`BusinessEntityID `< 5;`</span><span class="sxs-lookup"><span data-stu-id="085f7-129">`WHERE c.`BusinessEntityID `< 5;`</span></span>  
  
 <span data-ttu-id="085f7-130">您可以接著指定要使用 `-v` 選項傳回的資料行名稱：</span><span class="sxs-lookup"><span data-stu-id="085f7-130">You can then specify the name of the column that you want returned by using the `-v` option:</span></span>  
  
 `sqlcmd -v ColumnName ="FirstName" -i c:\testscript.sql`  
  
 <span data-ttu-id="085f7-131">若要使用相同的指令碼傳回不同的資料行，請變更 `ColumnName` 指令碼變數的值。</span><span class="sxs-lookup"><span data-stu-id="085f7-131">To return a different column by using the same script, change the value of the `ColumnName` scripting variable.</span></span>  
  
 `sqlcmd -v ColumnName ="LastName" -i c:\testscript.sql`  
  
## <a name="guidelines-for-scripting-variable-names-and-values"></a><span data-ttu-id="085f7-132">指令碼變數名稱和值的指導方針</span><span class="sxs-lookup"><span data-stu-id="085f7-132">Guidelines for Scripting Variable Names and Values</span></span>  
 <span data-ttu-id="085f7-133">當您為指令碼變數命名時，請考慮下列指導方針：</span><span class="sxs-lookup"><span data-stu-id="085f7-133">Consider the following guidelines when you name scripting variables:</span></span>  
  
-   <span data-ttu-id="085f7-134">變數名稱不能包含空白字元或引號。</span><span class="sxs-lookup"><span data-stu-id="085f7-134">Variable names must not contain white space characters or quotation marks.</span></span>  
  
-   <span data-ttu-id="085f7-135">變數名稱的格式不能和變數運算式的格式相同，例如 *$(var)*。</span><span class="sxs-lookup"><span data-stu-id="085f7-135">Variable names must not have the same form as a variable expression, such as *$(var)*.</span></span>  
  
-   <span data-ttu-id="085f7-136">指令碼變數不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="085f7-136">Scripting variables are case-insensitive</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="085f7-137">如果未指定任何值給 **sqlcmd** 環境變數，則會移除該變數。</span><span class="sxs-lookup"><span data-stu-id="085f7-137">If no value is assigned to a **sqlcmd** environment variable, the variable is removed.</span></span> <span data-ttu-id="085f7-138">使用未含值的 **:setvar VarName** ，會清除變數。</span><span class="sxs-lookup"><span data-stu-id="085f7-138">Using **:setvar VarName** without a value clears the variable.</span></span>  
  
 <span data-ttu-id="085f7-139">當您指定指令碼變數的值時，請考慮下列指導方針：</span><span class="sxs-lookup"><span data-stu-id="085f7-139">Consider the following guidelines when you specify values for scripting variables:</span></span>  
  
-   <span data-ttu-id="085f7-140">如果字串值包含空格，則使用 **setvar** 或 **-v** 選項所定義的變數值必須用引號括住。</span><span class="sxs-lookup"><span data-stu-id="085f7-140">Variable values that are defined by using **setvar** or the **-v** option must be enclosed by quotation marks if the string value contains spaces.</span></span>  
  
-   <span data-ttu-id="085f7-141">如果引號是變數值的一部分，則必須逸出。</span><span class="sxs-lookup"><span data-stu-id="085f7-141">If quotation marks are part of the variable value, they must be escaped.</span></span> <span data-ttu-id="085f7-142">例如：`setvar MyVar "spac""e"`。</span><span class="sxs-lookup"><span data-stu-id="085f7-142">For example: :`setvar MyVar "spac""e"`.</span></span>  
  
## <a name="guidelines-for-cmdexe-set-variable-values-and-names"></a><span data-ttu-id="085f7-143">Cmd.exe SET 變數值和名稱的指導方針</span><span class="sxs-lookup"><span data-stu-id="085f7-143">Guidelines for Cmd.exe SET Variable Values and Names</span></span>  
 <span data-ttu-id="085f7-144">使用 SET 所定義的變數是 Cmd.exe 環境的一部分，並且可供 **sqlcmd**參考。</span><span class="sxs-lookup"><span data-stu-id="085f7-144">Variables that are defined by using SET are part of the Cmd.exe environment and can be referenced by **sqlcmd**.</span></span> <span data-ttu-id="085f7-145">請參考下列指引：</span><span class="sxs-lookup"><span data-stu-id="085f7-145">Consider the following guidelines:</span></span>  
  
-   <span data-ttu-id="085f7-146">變數名稱不能包含空白字元或引號。</span><span class="sxs-lookup"><span data-stu-id="085f7-146">Variable names must not contain white space characters or quotation marks.</span></span>  
  
-   <span data-ttu-id="085f7-147">變數值可以包含空格或引號。</span><span class="sxs-lookup"><span data-stu-id="085f7-147">Variable values may contain spaces or quotation marks.</span></span>  
  
## <a name="sqlcmd-scripting-variables"></a><span data-ttu-id="085f7-148">sqlcmd 指令碼變數</span><span class="sxs-lookup"><span data-stu-id="085f7-148">sqlcmd Scripting Variables</span></span>  
 <span data-ttu-id="085f7-149">由 **sqlcmd** 定義的變數稱為指令碼變數。</span><span class="sxs-lookup"><span data-stu-id="085f7-149">Variables that are defined by **sqlcmd** are known as scripting variables.</span></span> <span data-ttu-id="085f7-150">下表列出 **sqlcmd** 指令碼變數。</span><span class="sxs-lookup"><span data-stu-id="085f7-150">The following table lists **sqlcmd** scripting variables.</span></span>  
  
|<span data-ttu-id="085f7-151">變數</span><span class="sxs-lookup"><span data-stu-id="085f7-151">Variable</span></span>|<span data-ttu-id="085f7-152">相關的選項</span><span class="sxs-lookup"><span data-stu-id="085f7-152">Related option</span></span>|<span data-ttu-id="085f7-153">R/W</span><span class="sxs-lookup"><span data-stu-id="085f7-153">R/W</span></span>|<span data-ttu-id="085f7-154">預設</span><span class="sxs-lookup"><span data-stu-id="085f7-154">Default</span></span>|  
|--------------|--------------------|----------|-------------|  
|<span data-ttu-id="085f7-155">SQLCMDUSER\*</span><span class="sxs-lookup"><span data-stu-id="085f7-155">SQLCMDUSER\*</span></span>|<span data-ttu-id="085f7-156">-U</span><span class="sxs-lookup"><span data-stu-id="085f7-156">-U</span></span>|<span data-ttu-id="085f7-157">R</span><span class="sxs-lookup"><span data-stu-id="085f7-157">R</span></span>|<span data-ttu-id="085f7-158">""</span><span class="sxs-lookup"><span data-stu-id="085f7-158">""</span></span>|  
|<span data-ttu-id="085f7-159">SQLCMDPASSWORD\*</span><span class="sxs-lookup"><span data-stu-id="085f7-159">SQLCMDPASSWORD\*</span></span>|<span data-ttu-id="085f7-160">-P</span><span class="sxs-lookup"><span data-stu-id="085f7-160">-P</span></span>|--|<span data-ttu-id="085f7-161">""</span><span class="sxs-lookup"><span data-stu-id="085f7-161">""</span></span>|  
|<span data-ttu-id="085f7-162">SQLCMDSERVER\*</span><span class="sxs-lookup"><span data-stu-id="085f7-162">SQLCMDSERVER\*</span></span>|<span data-ttu-id="085f7-163">-S</span><span class="sxs-lookup"><span data-stu-id="085f7-163">-S</span></span>|<span data-ttu-id="085f7-164">R</span><span class="sxs-lookup"><span data-stu-id="085f7-164">R</span></span>|<span data-ttu-id="085f7-165">"DefaultLocalInstance"</span><span class="sxs-lookup"><span data-stu-id="085f7-165">"DefaultLocalInstance"</span></span>|  
|<span data-ttu-id="085f7-166">SQLCMDWORKSTATION</span><span class="sxs-lookup"><span data-stu-id="085f7-166">SQLCMDWORKSTATION</span></span>|<span data-ttu-id="085f7-167">-H</span><span class="sxs-lookup"><span data-stu-id="085f7-167">-H</span></span>|<span data-ttu-id="085f7-168">R</span><span class="sxs-lookup"><span data-stu-id="085f7-168">R</span></span>|<span data-ttu-id="085f7-169">"ComputerName"</span><span class="sxs-lookup"><span data-stu-id="085f7-169">"ComputerName"</span></span>|  
|<span data-ttu-id="085f7-170">SQLCMDDBNAME</span><span class="sxs-lookup"><span data-stu-id="085f7-170">SQLCMDDBNAME</span></span>|<span data-ttu-id="085f7-171">-d</span><span class="sxs-lookup"><span data-stu-id="085f7-171">-d</span></span>|<span data-ttu-id="085f7-172">R</span><span class="sxs-lookup"><span data-stu-id="085f7-172">R</span></span>|<span data-ttu-id="085f7-173">""</span><span class="sxs-lookup"><span data-stu-id="085f7-173">""</span></span>|  
|<span data-ttu-id="085f7-174">SQLCMDLOGINTIMEOUT</span><span class="sxs-lookup"><span data-stu-id="085f7-174">SQLCMDLOGINTIMEOUT</span></span>|<span data-ttu-id="085f7-175">-l</span><span class="sxs-lookup"><span data-stu-id="085f7-175">-l</span></span>|<span data-ttu-id="085f7-176">R/W</span><span class="sxs-lookup"><span data-stu-id="085f7-176">R/W</span></span>|<span data-ttu-id="085f7-177">"8" (秒)</span><span class="sxs-lookup"><span data-stu-id="085f7-177">"8" (seconds)</span></span>|  
|<span data-ttu-id="085f7-178">SQLCMDSTATTIMEOUT</span><span class="sxs-lookup"><span data-stu-id="085f7-178">SQLCMDSTATTIMEOUT</span></span>|<span data-ttu-id="085f7-179">-t</span><span class="sxs-lookup"><span data-stu-id="085f7-179">-t</span></span>|<span data-ttu-id="085f7-180">R/W</span><span class="sxs-lookup"><span data-stu-id="085f7-180">R/W</span></span>|<span data-ttu-id="085f7-181">"0" = 永遠等候</span><span class="sxs-lookup"><span data-stu-id="085f7-181">"0" = wait indefinitely</span></span>|  
|<span data-ttu-id="085f7-182">SQLCMDHEADERS</span><span class="sxs-lookup"><span data-stu-id="085f7-182">SQLCMDHEADERS</span></span>|<span data-ttu-id="085f7-183">-H</span><span class="sxs-lookup"><span data-stu-id="085f7-183">-h</span></span>|<span data-ttu-id="085f7-184">R/W</span><span class="sxs-lookup"><span data-stu-id="085f7-184">R/W</span></span>|<span data-ttu-id="085f7-185">"0"</span><span class="sxs-lookup"><span data-stu-id="085f7-185">"0"</span></span>|  
|<span data-ttu-id="085f7-186">SQLCMDCOLSEP</span><span class="sxs-lookup"><span data-stu-id="085f7-186">SQLCMDCOLSEP</span></span>|<span data-ttu-id="085f7-187">-S</span><span class="sxs-lookup"><span data-stu-id="085f7-187">-s</span></span>|<span data-ttu-id="085f7-188">R/W</span><span class="sxs-lookup"><span data-stu-id="085f7-188">R/W</span></span>|<span data-ttu-id="085f7-189">" "</span><span class="sxs-lookup"><span data-stu-id="085f7-189">" "</span></span>|  
|<span data-ttu-id="085f7-190">SQLCMDCOLWIDTH</span><span class="sxs-lookup"><span data-stu-id="085f7-190">SQLCMDCOLWIDTH</span></span>|<span data-ttu-id="085f7-191">-w</span><span class="sxs-lookup"><span data-stu-id="085f7-191">-w</span></span>|<span data-ttu-id="085f7-192">R/W</span><span class="sxs-lookup"><span data-stu-id="085f7-192">R/W</span></span>|<span data-ttu-id="085f7-193">"0"</span><span class="sxs-lookup"><span data-stu-id="085f7-193">"0"</span></span>|  
|<span data-ttu-id="085f7-194">SQLCMDPACKETSIZE</span><span class="sxs-lookup"><span data-stu-id="085f7-194">SQLCMDPACKETSIZE</span></span>|<span data-ttu-id="085f7-195">-a</span><span class="sxs-lookup"><span data-stu-id="085f7-195">-a</span></span>|<span data-ttu-id="085f7-196">R</span><span class="sxs-lookup"><span data-stu-id="085f7-196">R</span></span>|<span data-ttu-id="085f7-197">"4096"</span><span class="sxs-lookup"><span data-stu-id="085f7-197">"4096"</span></span>|  
|<span data-ttu-id="085f7-198">SQLCMDERRORLEVEL</span><span class="sxs-lookup"><span data-stu-id="085f7-198">SQLCMDERRORLEVEL</span></span>|<span data-ttu-id="085f7-199">-M</span><span class="sxs-lookup"><span data-stu-id="085f7-199">-m</span></span>|<span data-ttu-id="085f7-200">R/W</span><span class="sxs-lookup"><span data-stu-id="085f7-200">R/W</span></span>|<span data-ttu-id="085f7-201">"0"</span><span class="sxs-lookup"><span data-stu-id="085f7-201">"0"</span></span>|  
|<span data-ttu-id="085f7-202">SQLCMDMAXVARTYPEWIDTH</span><span class="sxs-lookup"><span data-stu-id="085f7-202">SQLCMDMAXVARTYPEWIDTH</span></span>|<span data-ttu-id="085f7-203">-y</span><span class="sxs-lookup"><span data-stu-id="085f7-203">-y</span></span>|<span data-ttu-id="085f7-204">R/W</span><span class="sxs-lookup"><span data-stu-id="085f7-204">R/W</span></span>|<span data-ttu-id="085f7-205">"256"</span><span class="sxs-lookup"><span data-stu-id="085f7-205">"256"</span></span>|  
|<span data-ttu-id="085f7-206">SQLCMDMAXFIXEDTYPEWIDTH</span><span class="sxs-lookup"><span data-stu-id="085f7-206">SQLCMDMAXFIXEDTYPEWIDTH</span></span>|<span data-ttu-id="085f7-207">-y</span><span class="sxs-lookup"><span data-stu-id="085f7-207">-Y</span></span>|<span data-ttu-id="085f7-208">R/W</span><span class="sxs-lookup"><span data-stu-id="085f7-208">R/W</span></span>|<span data-ttu-id="085f7-209">"0" = 無限制</span><span class="sxs-lookup"><span data-stu-id="085f7-209">"0" = unlimited</span></span>|  
|<span data-ttu-id="085f7-210">SQLCMDEDITOR</span><span class="sxs-lookup"><span data-stu-id="085f7-210">SQLCMDEDITOR</span></span>||<span data-ttu-id="085f7-211">R/W</span><span class="sxs-lookup"><span data-stu-id="085f7-211">R/W</span></span>|<span data-ttu-id="085f7-212">"edit.com"</span><span class="sxs-lookup"><span data-stu-id="085f7-212">"edit.com"</span></span>|  
|<span data-ttu-id="085f7-213">SQLCMDINI</span><span class="sxs-lookup"><span data-stu-id="085f7-213">SQLCMDINI</span></span>||<span data-ttu-id="085f7-214">R</span><span class="sxs-lookup"><span data-stu-id="085f7-214">R</span></span>|<span data-ttu-id="085f7-215">""</span><span class="sxs-lookup"><span data-stu-id="085f7-215">""</span></span>|  
  
 <span data-ttu-id="085f7-216">\*SQLCMDUSER、SQLCMDPASSWORD 和 SQLCMDSERVER 是在使用 **： Connect**時設定。</span><span class="sxs-lookup"><span data-stu-id="085f7-216">\* SQLCMDUSER, SQLCMDPASSWORD and SQLCMDSERVER are set when **:Connect** is used.</span></span>  
  
 <span data-ttu-id="085f7-217">R 表示在程式初始化期間只能設定該值一次。</span><span class="sxs-lookup"><span data-stu-id="085f7-217">R indicates the value can only be set one time during program initialization.</span></span>  
  
 <span data-ttu-id="085f7-218">R/W 表示可以使用 **setvar** 命令來重設該值，且後續的命令將會使用新值。</span><span class="sxs-lookup"><span data-stu-id="085f7-218">R/W indicates that the value can be reset by using the **setvar** command and subsequent commands will use the new value.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="085f7-219">範例</span><span class="sxs-lookup"><span data-stu-id="085f7-219">Examples</span></span>  
  
### <a name="a-using-the-setvar-command-in-a-script"></a><span data-ttu-id="085f7-220">A.</span><span class="sxs-lookup"><span data-stu-id="085f7-220">A.</span></span> <span data-ttu-id="085f7-221">在指令碼中使用 setvar 命令</span><span class="sxs-lookup"><span data-stu-id="085f7-221">Using the setvar command in a script</span></span>  
 <span data-ttu-id="085f7-222">許多 **sqlcmd** 選項可以在指令碼中使用 **setvar** 命令來控制。</span><span class="sxs-lookup"><span data-stu-id="085f7-222">Many **sqlcmd** options can be controlled in a script by using the **setvar** command.</span></span> <span data-ttu-id="085f7-223">下列範例會建立指令碼 `test.sql` ，其中的 `SQLCMDLOGINTIMEOUT` 變數設為 `60` 秒，而另一個指令碼變數 `server`則設為 `testserver`。</span><span class="sxs-lookup"><span data-stu-id="085f7-223">In the following example, the script `test.sql` is created in which the `SQLCMDLOGINTIMEOUT` variable is set to `60` seconds and another scripting variable, `server`, is set to `testserver`.</span></span> <span data-ttu-id="085f7-224">下列程式碼是在 `test.sql`中。</span><span class="sxs-lookup"><span data-stu-id="085f7-224">The following code is in `test.sql`.</span></span>  
  
 `:setvar SQLCMDLOGINTIMEOUT 60`  
  
 `:setvar server "testserver"`  
  
 `:connect $(server) -l $(SQLCMDLOGINTIMEOUT)`  
  
 `USE AdventureWorks2012;`  
  
 `SELECT FirstName, LastName`  
  
 `FROM Person.Person;`  
  
 `The script is then called by using sqlcmd:`  
  
 `sqlcmd -i c:\test.sql`  
  
### <a name="b-using-the-setvar-command-interactively"></a><span data-ttu-id="085f7-225">B.</span><span class="sxs-lookup"><span data-stu-id="085f7-225">B.</span></span> <span data-ttu-id="085f7-226">以互動方式使用 setvar 命令</span><span class="sxs-lookup"><span data-stu-id="085f7-226">Using the setvar command interactively</span></span>  
 <span data-ttu-id="085f7-227">下列範例顯示如何使用 `setvar` 命令，以互動方式設定指令碼變數。</span><span class="sxs-lookup"><span data-stu-id="085f7-227">The following example shows how to set a scripting variable interactively by using the `setvar` command.</span></span>  
  
 `sqlcmd`  
  
 `:setvar  MYDATABASE AdventureWorks2012`  
  
 `USE $(MYDATABASE);`  
  
 `GO`  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `Changed database context to 'AdventureWorks2012'`  
  
 `1>`  
  
### <a name="c-using-command-prompt-environment-variables-within-sqlcmd"></a><span data-ttu-id="085f7-228">C.</span><span class="sxs-lookup"><span data-stu-id="085f7-228">C.</span></span> <span data-ttu-id="085f7-229">在 sqlcmd 內使用命令提示字元環境變數</span><span class="sxs-lookup"><span data-stu-id="085f7-229">Using command prompt environment variables within sqlcmd</span></span>  
 <span data-ttu-id="085f7-230">在下列範例中，設定了四個環境變數 `are` ，然後從 `sqlcmd`進行呼叫。</span><span class="sxs-lookup"><span data-stu-id="085f7-230">In the following example, four environment variables `are` set and then called from `sqlcmd`.</span></span>  
  
 `C:\>SET tablename=Person.Person`  
  
 `C:\>SET col1=FirstName`  
  
 `C:\>SET col2=LastName`  
  
 `C:\>SET title=Ms.`  
  
 `C:\>sqlcmd -d AdventureWorks2012`  
  
 `1> SELECT TOP 5 $(col1) + ' ' + $(col2) AS Name`  
  
 `2> FROM $(tablename)`  
  
 `3> WHERE Title ='$(title)'`  
  
 `4> GO`  
  
### <a name="d-using-user-level-environment-variables-within-sqlcmd"></a><span data-ttu-id="085f7-231">D.</span><span class="sxs-lookup"><span data-stu-id="085f7-231">D.</span></span> <span data-ttu-id="085f7-232">在 sqlcmd 內使用使用者層級環境變數</span><span class="sxs-lookup"><span data-stu-id="085f7-232">Using user-level environment variables within sqlcmd</span></span>  
 <span data-ttu-id="085f7-233">下列範例在命令提示字元中設定了使用者層級環境變數 `%Temp%` ，並將其傳遞至 `sqlcmd` 輸入檔。</span><span class="sxs-lookup"><span data-stu-id="085f7-233">In the following example the user-level environmental variable `%Temp%` is set at the command prompt and passed to the `sqlcmd` input file.</span></span> <span data-ttu-id="085f7-234">若要取得使用者層級環境變數，請在 [控制台]  中按兩下 [系統]  。</span><span class="sxs-lookup"><span data-stu-id="085f7-234">To obtain the user-level environment variable, in **Control Panel**, double-click **System**.</span></span> <span data-ttu-id="085f7-235">按一下 [進階]  索引標籤，然後按一下 [環境變數]  。</span><span class="sxs-lookup"><span data-stu-id="085f7-235">Click the **Advance** tab, and then click **Environment Variables**.</span></span>  
  
 <span data-ttu-id="085f7-236">下列程式碼是在輸入檔 `c:\testscript.txt`中：</span><span class="sxs-lookup"><span data-stu-id="085f7-236">The following code is in the input file `c:\testscript.txt`:</span></span>  
  
 `:OUT $(MyTempDirectory)`  
  
 `USE AdventureWorks2012;`  
  
 `SELECT FirstName`  
  
 `FROM AdventureWorks2012.Person.Person`  
  
 <span data-ttu-id="085f7-237">`WHERE BusinessEntityID` `< 5;`</span><span class="sxs-lookup"><span data-stu-id="085f7-237">`WHERE BusinessEntityID` `< 5;`</span></span>  
  
 <span data-ttu-id="085f7-238">下列程式碼是在命令提示字元中輸入的：</span><span class="sxs-lookup"><span data-stu-id="085f7-238">This following code is entered at the command prompt:</span></span>  
  
 `C:\ >SET MyTempDirectory=%Temp%\output.txt`  
  
 `C:\ >sqlcmd -i C:\testscript.txt`  
  
 <span data-ttu-id="085f7-239">下列結果會傳送到輸出檔 C:\Documents and Settings\\<使用者\>\Local Settings\Temp\output.txt。</span><span class="sxs-lookup"><span data-stu-id="085f7-239">The following result is sent to the output file C:\Documents and Settings\\<user\>\Local Settings\Temp\output.txt.</span></span>  
  
 `Changed database context to 'AdventureWorks2012'.`  
  
 `FirstName`  
  
 `--------------------------------------------------`  
  
 `Gustavo`  
  
 `Catherine`  
  
 `Kim`  
  
 `Humberto`  
  
 `(4 rows affected)`  
  
### <a name="e-using-a-startup-script"></a><span data-ttu-id="085f7-240">E.</span><span class="sxs-lookup"><span data-stu-id="085f7-240">E.</span></span> <span data-ttu-id="085f7-241">使用啟動指令碼</span><span class="sxs-lookup"><span data-stu-id="085f7-241">Using a startup script</span></span>  
 <span data-ttu-id="085f7-242">啟動 **sqlcmd** 時，會執行 **sqlcmd** 啟動指令碼。</span><span class="sxs-lookup"><span data-stu-id="085f7-242">A **sqlcmd** startup script is executed when **sqlcmd** is started.</span></span> <span data-ttu-id="085f7-243">下列範例會設定環境變數 `SQLCMDINI`。</span><span class="sxs-lookup"><span data-stu-id="085f7-243">The following example sets the environment variable `SQLCMDINI`.</span></span> <span data-ttu-id="085f7-244">這是下者的內容： `init.sql.`</span><span class="sxs-lookup"><span data-stu-id="085f7-244">This is the contents of `init.sql.`</span></span>  
  
 `SET NOCOUNT ON`  
  
 `GO`  
  
 `DECLARE @nt_username nvarchar(128)`  
  
 `SET @nt_username = (SELECT rtrim(convert(nvarchar(128), nt_username))`  
  
 `FROM sys.dm_exec_sessions WHERE spid = @@SPID)`  
  
 `SELECT  @nt_username + ' is connected to ' +`  
  
 `rtrim(CONVERT(nvarchar(20), SERVERPROPERTY('servername'))) +`  
  
 `' (' +`  
  
 `rtrim(CONVERT(nvarchar(20), SERVERPROPERTY('productversion'))) +`  
  
 `')'`  
  
 `:setvar SQLCMDMAXFIXEDTYPEWIDTH 100`  
  
 `SET NOCOUNT OFF`  
  
 `GO`  
  
 `:setvar SQLCMDMAXFIXEDTYPEWIDTH`  
  
 <span data-ttu-id="085f7-245">這會在 `init.sql` 啟動時呼叫 `sqlcmd` 檔案。</span><span class="sxs-lookup"><span data-stu-id="085f7-245">This calls the `init.sql` file when `sqlcmd` is started.</span></span>  
  
 `C:\> SET sqlcmdini=c:\init.sql`  
  
 `>1 Sqlcmd`  
  
 <span data-ttu-id="085f7-246">以下是輸出。</span><span class="sxs-lookup"><span data-stu-id="085f7-246">This is the output.</span></span>  
  
 `>1 < user > is connected to < server > (9.00.2047.00)`  
  
> [!NOTE]  
>  <span data-ttu-id="085f7-247">**-X** 選項會停用啟動指令碼功能。</span><span class="sxs-lookup"><span data-stu-id="085f7-247">The **-X** option disables the startup script feature.</span></span>  
  
### <a name="f-variable-expansion"></a><span data-ttu-id="085f7-248">F.</span><span class="sxs-lookup"><span data-stu-id="085f7-248">F.</span></span> <span data-ttu-id="085f7-249">變數展開</span><span class="sxs-lookup"><span data-stu-id="085f7-249">Variable expansion</span></span>  
 <span data-ttu-id="085f7-250">下列範例顯示如何以 **sqlcmd** 變數的形式來使用資料。</span><span class="sxs-lookup"><span data-stu-id="085f7-250">The following example shows working with data in the form of a **sqlcmd** variable.</span></span>  
  
 `USE AdventureWorks2012;`  
  
 `CREATE TABLE AdventureWorks2012.dbo.VariableTest`  
  
 `(`  
  
 `Col1 nvarchar(50)`  
  
 `);`  
  
 `GO`  
  
 <span data-ttu-id="085f7-251">在 `Col1` 的 `dbo.VariableTest` 中插入一個資料列，內含值 `$(tablename)`。</span><span class="sxs-lookup"><span data-stu-id="085f7-251">Insert one row into `Col1` of `dbo.VariableTest` that contains the value `$(tablename)`.</span></span>  
  
 `INSERT INTO AdventureWorks2012.dbo.VariableTest(Col1)`  
  
 `VALUES('$(tablename)');`  
  
 `GO`  
  
 <span data-ttu-id="085f7-252">在 `sqlcmd` 提示字元中，當沒有任何變數設定為等於 `$(tablename)`時，下列陳述式會傳回資料列。</span><span class="sxs-lookup"><span data-stu-id="085f7-252">At the `sqlcmd` prompt, when no variable is set equal to `$(tablename)`, the following statements return the row.</span></span>  
  
 `C:\> sqlcmd`  
  
 `>1 SELECT Col1 FROM dbo.VariableTest WHERE Col1 = '$(tablename)';`  
  
 `>2 GO`  
  
 `>3 SELECT Col1 FROM dbo.VariableTest WHERE Col1 = N'$(tablename)';`  
  
 `>4 GO`  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `>1 Col1`  
  
 `>2 ------------------`  
  
 `>3 $(tablename)`  
  
 `>4`  
  
 `>5 (1 rows affected)`  
  
 <span data-ttu-id="085f7-253">假使變數 `MyVar` 設定為 `$(tablename)`。</span><span class="sxs-lookup"><span data-stu-id="085f7-253">Given the variable `MyVar` is set to `$(tablename)`.</span></span>  
  
 `>6 :setvar MyVar $(tablename)`  
  
 <span data-ttu-id="085f7-254">下列陳述式會傳回該資料列，而且還會傳回訊息「'tablename' 指令碼變數未定義」。</span><span class="sxs-lookup"><span data-stu-id="085f7-254">These statements return the row and also return the message "'tablename' scripting variable not defined."</span></span>  
  
 `>6 SELECT Col1 FROM dbo.VariableTest WHERE Col1 = '$(tablename)';`  
  
 `>7 GO`  
  
 `>1 SELECT Col1 FROM dbo.VariableTest WHERE Col1 = N'$(tablename)';`  
  
 `>2 GO`  
  
 <span data-ttu-id="085f7-255">下列陳述式會傳回資料列。</span><span class="sxs-lookup"><span data-stu-id="085f7-255">These statements return the row.</span></span>  
  
 `>1 SELECT Col1 FROM dbo.VariableTest WHERE Col1 = '$(MyVar)';`  
  
 `>2 GO`  
  
 `>1 SELECT Col1 FROM dbo.VariableTest WHERE Col1 = N'$(MyVar)';`  
  
 `>2 GO`  
  
## <a name="see-also"></a><span data-ttu-id="085f7-256">另請參閱</span><span class="sxs-lookup"><span data-stu-id="085f7-256">See Also</span></span>  
 <span data-ttu-id="085f7-257">[使用 sqlcmd 公用程式](sqlcmd-use-the-utility.md) </span><span class="sxs-lookup"><span data-stu-id="085f7-257">[Use the sqlcmd Utility](sqlcmd-use-the-utility.md) </span></span>  
 <span data-ttu-id="085f7-258">[sqlcmd 公用程式](../../tools/sqlcmd-utility.md) </span><span class="sxs-lookup"><span data-stu-id="085f7-258">[sqlcmd Utility](../../tools/sqlcmd-utility.md) </span></span>  
 [<span data-ttu-id="085f7-259">命令提示字元公用程式參考 &#40;Database Engine&#41;</span><span class="sxs-lookup"><span data-stu-id="085f7-259">Command Prompt Utility Reference &#40;Database Engine&#41;</span></span>](../../tools/command-prompt-utility-reference-database-engine.md)  
  
  
