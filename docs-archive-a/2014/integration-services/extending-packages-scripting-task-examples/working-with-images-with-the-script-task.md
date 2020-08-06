---
title: 以指令碼工作處理映像 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- graphics [Integration Services]
- Script task [Integration Services], images
- Drawing namespace
- images [Integration Services]
- SSIS Script task, images
- Script task [Integration Services], examples
- thumbnails [Integration Services]
- System.Drawing namespace
- JPEG format [Integration Services]
- .jpeg files
ms.assetid: 74aeb7ab-51b2-4b9f-84ee-0b46a7908ab9
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 75a5b72f87a4463d7270dc9f28529a81525860cf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596207"
---
# <a name="working-with-images-with-the-script-task"></a><span data-ttu-id="b5dbd-102">以指令碼工作處理影像</span><span class="sxs-lookup"><span data-stu-id="b5dbd-102">Working with Images with the Script Task</span></span>
  <span data-ttu-id="b5dbd-103">產品或是使用者的資料庫除了文字與數值資料之外經常包括影像。</span><span class="sxs-lookup"><span data-stu-id="b5dbd-103">A database of products or users frequently includes images in addition to text and numeric data.</span></span> <span data-ttu-id="b5dbd-104">Microsoft .NET Framework 中的 `System.Drawing` 命名空間提供操作影像的類別。</span><span class="sxs-lookup"><span data-stu-id="b5dbd-104">The `System.Drawing` namespace in the Microsoft .NET Framework provides classes for manipulating images.</span></span>  
  
 [<span data-ttu-id="b5dbd-105">範例 1：將影像轉換為 JPEG 格式</span><span class="sxs-lookup"><span data-stu-id="b5dbd-105">Example 1: Convert Images to JPEG Format</span></span>](#example1)  
  
 [<span data-ttu-id="b5dbd-106">範例 2：建立和儲存縮圖影像</span><span class="sxs-lookup"><span data-stu-id="b5dbd-106">Example 2: Create and Save Thumbnail Images</span></span>](#example2)  
  
> [!NOTE]  
>  <span data-ttu-id="b5dbd-107">如果您想要建立可更輕鬆地在多個封裝之間重複使用的工作，請考慮使用此指令碼工作範例中的程式碼做為自訂工作的起點。</span><span class="sxs-lookup"><span data-stu-id="b5dbd-107">If you want to create a task that you can more easily reuse across multiple packages, consider using the code in this Script task sample as the starting point for a custom task.</span></span> <span data-ttu-id="b5dbd-108">如需詳細資訊，請參閱 [開發自訂工作](../extending-packages-custom-objects/task/developing-a-custom-task.md)。</span><span class="sxs-lookup"><span data-stu-id="b5dbd-108">For more information, see [Developing a Custom Task](../extending-packages-custom-objects/task/developing-a-custom-task.md).</span></span>  
  
##  <a name="example-1-description-convert-images-to-jpeg-format"></a><a name="example1"></a> <span data-ttu-id="b5dbd-109">範例 1 描述：將影像轉換為 JPEG 格式</span><span class="sxs-lookup"><span data-stu-id="b5dbd-109">Example 1 Description: Convert Images to JPEG Format</span></span>  
 <span data-ttu-id="b5dbd-110">下列範例會開啟變數指定的影像檔，並使用編碼器將它儲存為壓縮的 JPEG 檔案。</span><span class="sxs-lookup"><span data-stu-id="b5dbd-110">The following example opens an image file specified by a variable and saves it as a compressed JPEG file by using an encoder.</span></span> <span data-ttu-id="b5dbd-111">擷取編碼器資訊的程式碼是封裝在私用函數中。</span><span class="sxs-lookup"><span data-stu-id="b5dbd-111">The code to retrieve encoder information is encapsulated in a private function.</span></span>  
  
#### <a name="to-configure-this-script-task-example-for-use-with-a-single-image-file"></a><span data-ttu-id="b5dbd-112">若要將指令碼工作範例設定成與單一影像檔搭配使用</span><span class="sxs-lookup"><span data-stu-id="b5dbd-112">To configure this Script Task example for use with a single image file</span></span>  
  
1.  <span data-ttu-id="b5dbd-113">建立名為 `CurrentImageFile` 的字串變數，並將其值設定為現有影像檔的路徑與檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="b5dbd-113">Create a string variable named `CurrentImageFile` and set its value to the path and file name of an existing image file.</span></span>  
  
2.  <span data-ttu-id="b5dbd-114">在 [**腳本工作編輯器**] 的 [**腳本**] 頁面上，將 `CurrentImageFile` 變數加入至 `ReadOnlyVariables` 屬性。</span><span class="sxs-lookup"><span data-stu-id="b5dbd-114">On the **Script** page of the **Script Task Editor**, add the `CurrentImageFile` variable to the `ReadOnlyVariables` property.</span></span>  
  
3.  <span data-ttu-id="b5dbd-115">在指令碼專案中，設定 `System.Drawing` 命名空間的參考。</span><span class="sxs-lookup"><span data-stu-id="b5dbd-115">In the script project, set a reference to the `System.Drawing` namespace.</span></span>  
  
4.  <span data-ttu-id="b5dbd-116">在您的程式碼中，使用 `Imports` 陳述式匯入 `System.Drawing` 與 `System.IO` 命名空間。</span><span class="sxs-lookup"><span data-stu-id="b5dbd-116">In your code, use `Imports` statements to import the `System.Drawing` and `System.IO` namespaces.</span></span>  
  
#### <a name="to-configure-this-script-task-example-for-use-with-multiple-image-files"></a><span data-ttu-id="b5dbd-117">若要將指令碼工作範例設定成與多個影像檔搭配使用</span><span class="sxs-lookup"><span data-stu-id="b5dbd-117">To configure this Script Task example for use with multiple image files</span></span>  
  
1.  <span data-ttu-id="b5dbd-118">在 Foreach 迴圈容器中置放指令碼工作。</span><span class="sxs-lookup"><span data-stu-id="b5dbd-118">Place the Script task within a Foreach Loop container.</span></span>  
  
2.  <span data-ttu-id="b5dbd-119">在 **Foreach 迴圈編輯器** 的 [集合] 頁面上，將 [Foreach 檔案列舉值] 選取為列舉值，以及指定來源檔案的路徑與檔案遮罩，例如 "\*.bmp"。</span><span class="sxs-lookup"><span data-stu-id="b5dbd-119">On the **Collection** page of the **Foreach Loop Editor**, select the **Foreach File Enumerator** as the enumerator, and specify the path and file mask of the source files, such as "\*.bmp."</span></span>  
  
3.  <span data-ttu-id="b5dbd-120">在 [變數對應]  頁面上，將 `CurrentImageFile` 變數對應至索引 0。</span><span class="sxs-lookup"><span data-stu-id="b5dbd-120">On the **Variable Mappings** page, map the `CurrentImageFile` variable to Index 0.</span></span> <span data-ttu-id="b5dbd-121">這個變數會在每次反覆運算列舉值時，將目前的檔案名稱傳遞給指令碼工作。</span><span class="sxs-lookup"><span data-stu-id="b5dbd-121">This variable passes the current file name to the Script task on each iteration of the enumerator.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="b5dbd-122">除了列在用於單一影像檔之程序的步驟之外，這是額外的步驟。</span><span class="sxs-lookup"><span data-stu-id="b5dbd-122">These steps are in addition to the steps listed in the procedure for use with a single image file.</span></span>  
  
### <a name="example-1-code"></a><span data-ttu-id="b5dbd-123">範例 1 程式碼</span><span class="sxs-lookup"><span data-stu-id="b5dbd-123">Example 1 Code</span></span>  
  
```vb  
Public Sub Main()  
  
    'Create and initialize variables.  
    Dim currentFile As String  
    Dim newFile As String  
    Dim bmp As Bitmap  
    Dim eps As New Imaging.EncoderParameters(1)  
    Dim ici As Imaging.ImageCodecInfo  
    Dim supportedExtensions() As String = _  
        {".BMP", ".GIF", ".JPG", ".JPEG", ".EXIF", ".PNG", _  
        ".TIFF", ".TIF", ".ICO", ".ICON"}  
  
    Try  
        'Store the variable in a string for local manipulation.  
        currentFile = Dts.Variables("CurrentImageFile").Value.ToString  
        'Check the extension of the file against a list of  
        'files that the Bitmap class supports.  
        If Array.IndexOf(supportedExtensions, _  
            Path.GetExtension(currentFile).ToUpper) > -1 Then  
  
            'Load the file.  
            bmp = New Bitmap(currentFile)  
  
            'Calculate the new name for the compressed image.  
            'Note: This will overwrite existing JPEGs.  
            newFile = Path.Combine( _  
                Path.GetDirectoryName(currentFile), _  
                String.Concat(Path.GetFileNameWithoutExtension(currentFile), _  
                ".jpg"))  
  
            'Specify the compression ratio (0=worst quality, 100=best quality).  
            eps.Param(0) = New Imaging.EncoderParameter( _  
                Imaging.Encoder.Quality, 75)  
  
            'Retrieve the ImageCodecInfo associated with the jpeg format.  
            ici = GetEncoderInfo("image/jpeg")  
  
            'Save the file, compressing it into the jpeg encoding.  
            bmp.Save(newFile, ici, eps)  
        Else  
            'The file is not supported by the Bitmap class.  
            Dts.Events.FireWarning(0, "Image Resampling Sample", _  
                "File " & currentFile & " is not a supported format.", _  
                "", 0)  
         End If  
        Dts.TaskResult = ScriptResults.Success  
    Catch ex As Exception  
        'An error occurred.  
        Dts.Events.FireError(0, "Image Resampling Sample", _  
            ex.Message & ControlChars.CrLf & ex.StackTrace, _  
            String.Empty, 0)  
        Dts.TaskResult = ScriptResults.Failure  
    End Try  
  
End Sub  
  
Private Function GetEncoderInfo(ByVal mimeType As String) As Imaging.ImageCodecInfo  
  
    'The available image codecs are returned as an array,  
    'which requires code to iterate until the specified codec is found.  
  
    Dim count As Integer  
    Dim encoders() As Imaging.ImageCodecInfo  
  
    encoders = Imaging.ImageCodecInfo.GetImageEncoders()  
  
    For count = 0 To encoders.Length  
        If encoders(count).MimeType = mimeType Then  
            Return encoders(count)  
        End If  
    Next  
  
    'This point is only reached if a codec is not found.  
    Err.Raise(513, "Image Resampling Sample", String.Format( _  
        "The {0} codec is not available. Unable to compress file.", _  
            mimeType))  
    Return Nothing  
  
End Function  
  
```  
  
##  <a name="example-2-description-create-and-save-thumbnail-images"></a><a name="example2"></a> <span data-ttu-id="b5dbd-124">範例 2 描述：建立和儲存縮圖影像</span><span class="sxs-lookup"><span data-stu-id="b5dbd-124">Example 2 Description: Create and Save Thumbnail Images</span></span>  
 <span data-ttu-id="b5dbd-125">下列範例會開啟變數所指定的影像檔、建立影像的縮圖，同時維護固定的外觀比例，並以修改的檔案名稱儲存縮圖。</span><span class="sxs-lookup"><span data-stu-id="b5dbd-125">The following example opens an image file specified by a variable, creates a thumbnail of the image while maintaining a constant aspect ratio, and saves the thumbnail with a modified file name.</span></span> <span data-ttu-id="b5dbd-126">計算縮圖的高度與寬度並維持其固定外觀比例的程式碼，是封裝在私用副程式中。</span><span class="sxs-lookup"><span data-stu-id="b5dbd-126">The code that calculates the height and width of the thumbnail while maintaining a constant aspect ratio is encapsulated in a private subroutine.</span></span>  
  
#### <a name="to-configure-this-script-task-example-for-use-with-a-single-image-file"></a><span data-ttu-id="b5dbd-127">若要將指令碼工作範例設定成與單一影像檔搭配使用</span><span class="sxs-lookup"><span data-stu-id="b5dbd-127">To configure this Script Task example for use with a single image file</span></span>  
  
1.  <span data-ttu-id="b5dbd-128">建立名為 `CurrentImageFile` 的字串變數，並將其值設定為現有影像檔的路徑與檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="b5dbd-128">Create a string variable named `CurrentImageFile` and set its value to the path and file name of an existing image file.</span></span>  
  
2.  <span data-ttu-id="b5dbd-129">另外建立 `MaxThumbSize` 整數變數並指派以像素為單位的值，例如 100。</span><span class="sxs-lookup"><span data-stu-id="b5dbd-129">Also create the `MaxThumbSize` integer variable and assign a value in pixels, such as 100.</span></span>  
  
3.  <span data-ttu-id="b5dbd-130">在 [**腳本工作編輯器**] 的 [**腳本**] 頁面上，將這兩個變數加入至 `ReadOnlyVariables` 屬性。</span><span class="sxs-lookup"><span data-stu-id="b5dbd-130">On the **Script** page of the **Script Task Editor**, add both variables to the `ReadOnlyVariables` property.</span></span>  
  
4.  <span data-ttu-id="b5dbd-131">在指令碼專案中，設定 `System.Drawing` 命名空間的參考。</span><span class="sxs-lookup"><span data-stu-id="b5dbd-131">In the script project, set a reference to the `System.Drawing` namespace.</span></span>  
  
5.  <span data-ttu-id="b5dbd-132">在您的程式碼中，使用 `Imports` 陳述式匯入 `System.Drawing` 與 `System.IO` 命名空間。</span><span class="sxs-lookup"><span data-stu-id="b5dbd-132">In your code, use `Imports` statements to import the `System.Drawing` and `System.IO` namespaces.</span></span>  
  
#### <a name="to-configure-this-script-task-example-for-use-with-multiple-image-files"></a><span data-ttu-id="b5dbd-133">若要將指令碼工作範例設定成與多個影像檔搭配使用</span><span class="sxs-lookup"><span data-stu-id="b5dbd-133">To configure this Script Task example for use with multiple image files</span></span>  
  
1.  <span data-ttu-id="b5dbd-134">在 Foreach 迴圈容器中置放指令碼工作。</span><span class="sxs-lookup"><span data-stu-id="b5dbd-134">Place the Script task within a Foreach Loop container.</span></span>  
  
2.  <span data-ttu-id="b5dbd-135">在 **Foreach 迴圈編輯器**的 [集合] 頁面上，將 [Foreach 檔案列舉值] 選取為 [列舉值]，以及指定來源檔案的路徑與檔案遮罩，例如 "\*.jpg"。</span><span class="sxs-lookup"><span data-stu-id="b5dbd-135">On the **Collection** page of the **Foreach Loop Editor**, select the **Foreach File Enumerator** as the **Enumerator**, and specify the path and file mask of the source files, such as "\*.jpg."</span></span>  
  
3.  <span data-ttu-id="b5dbd-136">在 [變數對應]  頁面上，將 `CurrentImageFile` 變數對應至索引 0。</span><span class="sxs-lookup"><span data-stu-id="b5dbd-136">On the **Variable Mappings** page, map the `CurrentImageFile` variable to Index 0.</span></span> <span data-ttu-id="b5dbd-137">這個變數會在每次反覆運算列舉值時，將目前的檔案名稱傳遞給指令碼工作。</span><span class="sxs-lookup"><span data-stu-id="b5dbd-137">This variable passes the current file name to the Script task on each iteration of the enumerator.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="b5dbd-138">除了列在用於單一影像檔之程序的步驟之外，這是額外的步驟。</span><span class="sxs-lookup"><span data-stu-id="b5dbd-138">These steps are in addition to the steps listed in the procedure for use with a single image file.</span></span>  
  
### <a name="example-2-code"></a><span data-ttu-id="b5dbd-139">範例 2 程式碼</span><span class="sxs-lookup"><span data-stu-id="b5dbd-139">Example 2 Code</span></span>  
  
```vb  
Public Sub Main()  
  
    Dim currentImageFile As String  
    Dim currentImage As Image  
    Dim maxThumbSize As Integer  
    Dim thumbnailImage As Image  
    Dim thumbnailFile As String  
    Dim thumbnailHeight As Integer  
    Dim thumbnailWidth As Integer  
  
    currentImageFile = Dts.Variables("CurrentImageFile").Value.ToString  
    thumbnailFile = Path.Combine( _  
        Path.GetDirectoryName(currentImageFile), _  
        String.Concat(Path.GetFileNameWithoutExtension(currentImageFile), _  
        "_thumbnail.jpg"))  
  
    Try  
        currentImage = Image.FromFile(currentImageFile)  
  
        maxThumbSize = CType(Dts.Variables("MaxThumbSize").Value, Integer)  
        CalculateThumbnailSize( _  
            maxThumbSize, currentImage, thumbnailWidth, thumbnailHeight)  
  
        thumbnailImage = currentImage.GetThumbnailImage( _  
           thumbnailWidth, thumbnailHeight, Nothing, Nothing)  
        thumbnailImage.Save(thumbnailFile)  
        Dts.TaskResult = ScriptResults.Success  
    Catch ex As Exception  
        Dts.Events.FireError(0, "Script Task Example", _  
        ex.Message & ControlChars.CrLf & ex.StackTrace, _  
        String.Empty, 0)  
        Dts.TaskResult = ScriptResults.Failure  
    End Try  
  
End Sub  
  
Private Sub CalculateThumbnailSize( _  
    ByVal maxSize As Integer, ByVal sourceImage As Image, _  
    ByRef thumbWidth As Integer, ByRef thumbHeight As Integer)  
  
    If sourceImage.Width > sourceImage.Height Then  
        thumbWidth = maxSize  
        thumbHeight = CInt((maxSize / sourceImage.Width) * sourceImage.Height)  
    Else  
        thumbHeight = maxSize  
        thumbWidth = CInt((maxSize / sourceImage.Height) * sourceImage.Width)  
    End If  
  
End Sub  
```  
  
```csharp  
bool ThumbnailCallback()  
        {  
            return false;  
        }  
        public void Main()  
        {  
  
            string currentImageFile;  
            Image currentImage;  
            int maxThumbSize;  
            Image thumbnailImage;  
            string thumbnailFile;  
            int thumbnailHeight = 0;  
            int thumbnailWidth = 0;  
  
            currentImageFile = Dts.Variables["CurrentImageFile"].Value.ToString();  
            thumbnailFile = Path.Combine(Path.GetDirectoryName(currentImageFile), String.Concat(Path.GetFileNameWithoutExtension(currentImageFile), "_thumbnail.jpg"));  
  
            try  
            {  
  
                currentImage = Image.FromFile(currentImageFile);  
  
                maxThumbSize = (int)Dts.Variables["MaxThumbSize"].Value;  
                CalculateThumbnailSize(maxThumbSize, currentImage, ref thumbnailWidth, ref thumbnailHeight);  
  
                Image.GetThumbnailImageAbort myCallback = new Image.GetThumbnailImageAbort(ThumbnailCallback);  
  
                thumbnailImage = currentImage.GetThumbnailImage(thumbnailWidth, thumbnailHeight, ThumbnailCallback, IntPtr.Zero);  
                thumbnailImage.Save(thumbnailFile);  
                Dts.TaskResult = (int)ScriptResults.Success;  
            }  
            catch (Exception ex)  
            {  
                Dts.Events.FireError(0, "Script Task Example", ex.Message + "\r" + ex.StackTrace, String.Empty, 0);  
                Dts.TaskResult = (int)ScriptResults.Failure;  
            }  
  
        }  
  
        private void CalculateThumbnailSize(int maxSize, Image sourceImage, ref int thumbWidth, ref int thumbHeight)  
        {  
  
            if (sourceImage.Width > sourceImage.Height)  
            {  
                thumbWidth = maxSize;  
                thumbHeight = (int)(sourceImage.Height * maxSize / sourceImage.Width);  
            }  
            else  
            {  
                thumbHeight = maxSize;  
                thumbWidth = (int)(sourceImage.Width * maxSize / sourceImage.Height);  
  
            }  
  
        }  
  
```  
  
<span data-ttu-id="b5dbd-140">![Integration Services 圖示 (小型) ](../media/dts-16.gif "Integration Services 圖示 (小)")會**保持最**新狀態 Integration Services  </span><span class="sxs-lookup"><span data-stu-id="b5dbd-140">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="b5dbd-141">若要取得 Microsoft 的最新下載、文件、範例和影片以及社群中的精選解決方案，請瀏覽 MSDN 上的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 頁面：</span><span class="sxs-lookup"><span data-stu-id="b5dbd-141">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="b5dbd-142">瀏覽 MSDN 上的 Integration Services 頁面</span><span class="sxs-lookup"><span data-stu-id="b5dbd-142">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="b5dbd-143">若要得到這些更新的自動通知，請訂閱該頁面上所提供的 RSS 摘要。</span><span class="sxs-lookup"><span data-stu-id="b5dbd-143">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
  
