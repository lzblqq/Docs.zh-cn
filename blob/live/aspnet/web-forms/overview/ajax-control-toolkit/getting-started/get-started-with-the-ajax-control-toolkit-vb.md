---
uid: web-forms/overview/ajax-control-toolkit/getting-started/get-started-with-the-ajax-control-toolkit-vb
title: "要开始使用 AJAX 控件工具包 (VB) |Microsoft 文档"
author: microsoft
description: "了解你需要知道若要开始使用 AJAX 控件工具包。"
ms.author: aspnetcontent
manager: wpickett
ms.date: 05/12/2009
ms.topic: article
ms.assetid: 9f8fa166-49a2-402c-b236-20caef0c658f
ms.technology: dotnet-webforms
ms.prod: .net-framework
msc.legacyurl: /web-forms/overview/ajax-control-toolkit/getting-started/get-started-with-the-ajax-control-toolkit-vb
msc.type: authoredcontent
ms.openlocfilehash: 0bbf6dc0be8a96ecd47b8620a6ba3220b50f10d4
ms.sourcegitcommit: 9a9483aceb34591c97451997036a9120c3fe2baf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/10/2017
---
<a name="get-started-with-the-ajax-control-toolkit-vb"></a><span data-ttu-id="cdfdb-103">要开始使用 AJAX 控件工具包 (VB)</span><span class="sxs-lookup"><span data-stu-id="cdfdb-103">Get Started with the AJAX Control Toolkit (VB)</span></span>
====================
<span data-ttu-id="cdfdb-104">通过[Microsoft](https://github.com/microsoft)</span><span class="sxs-lookup"><span data-stu-id="cdfdb-104">by [Microsoft](https://github.com/microsoft)</span></span>

> <span data-ttu-id="cdfdb-105">了解你需要知道若要开始使用 AJAX 控件工具包。</span><span class="sxs-lookup"><span data-stu-id="cdfdb-105">Learn all you need to know to get started using the AJAX Control Toolkit.</span></span>


<span data-ttu-id="cdfdb-106">AJAX 控件工具包包含 30 多个可用的控件，可以使用 ASP.NET 应用程序中。</span><span class="sxs-lookup"><span data-stu-id="cdfdb-106">The AJAX Control Toolkit contains more than 30 free controls that you can use in your ASP.NET applications.</span></span> <span data-ttu-id="cdfdb-107">在本教程中，您将学习如何下载 AJAX 控件工具包和将工具包控件添加到你 Visual Studio/Visual Web Developer Express 工具箱。</span><span class="sxs-lookup"><span data-stu-id="cdfdb-107">In this tutorial, you learn how to download the AJAX Control Toolkit and add the toolkit controls to your Visual Studio/Visual Web Developer Express toolbox.</span></span>

## <a name="downloading-the-ajax-control-toolkit"></a><span data-ttu-id="cdfdb-108">下载 AJAX 控件工具包</span><span class="sxs-lookup"><span data-stu-id="cdfdb-108">Downloading the AJAX Control Toolkit</span></span>

<span data-ttu-id="cdfdb-109">[AJAX 控件工具包](http://devexpress.com/act)开放源代码项目开发的 ASP.NET 社区和 ASP.NET 团队的成员。</span><span class="sxs-lookup"><span data-stu-id="cdfdb-109">The [AJAX Control Toolkit](http://devexpress.com/act) is an open source project developed by the members of the ASP.NET community and the ASP.NET team.</span></span>


<span data-ttu-id="cdfdb-110">[![下载 AJAX 控件工具包](get-started-with-the-ajax-control-toolkit-vb/_static/image1.jpg)](get-started-with-the-ajax-control-toolkit-vb/_static/image1.png)</span><span class="sxs-lookup"><span data-stu-id="cdfdb-110">[![Downloading the AJAX Control Toolkit](get-started-with-the-ajax-control-toolkit-vb/_static/image1.jpg)](get-started-with-the-ajax-control-toolkit-vb/_static/image1.png)</span></span>

<span data-ttu-id="cdfdb-111">**图 01**： 下载 AJAX 控件工具包 ([单击以查看实际尺寸的图像](get-started-with-the-ajax-control-toolkit-vb/_static/image2.png))</span><span class="sxs-lookup"><span data-stu-id="cdfdb-111">**Figure 01**: Downloading the AJAX Control Toolkit([Click to view full-size image](get-started-with-the-ajax-control-toolkit-vb/_static/image2.png))</span></span>


<span data-ttu-id="cdfdb-112">下载文件后，你需要取消阻止该文件。</span><span class="sxs-lookup"><span data-stu-id="cdfdb-112">After you download the file, you need to unblock the file.</span></span> <span data-ttu-id="cdfdb-113">右键单击该文件，选择属性，然后单击**解除阻止**按钮 （请参见图 2）。</span><span class="sxs-lookup"><span data-stu-id="cdfdb-113">Right-click the file, select Properties, and click the **Unblock** button (see Figure 2).</span></span>


<span data-ttu-id="cdfdb-114">[![取消阻止 AJAX 控件工具包 ZIP 文件](get-started-with-the-ajax-control-toolkit-vb/_static/image2.jpg)](get-started-with-the-ajax-control-toolkit-vb/_static/image3.png)</span><span class="sxs-lookup"><span data-stu-id="cdfdb-114">[![Unblocking the AJAX Control Toolkit ZIP file](get-started-with-the-ajax-control-toolkit-vb/_static/image2.jpg)](get-started-with-the-ajax-control-toolkit-vb/_static/image3.png)</span></span>

<span data-ttu-id="cdfdb-115">**图 02**： 取消阻止 AJAX 控件工具包 ZIP 文件 ([单击以查看实际尺寸的图像](get-started-with-the-ajax-control-toolkit-vb/_static/image4.png))</span><span class="sxs-lookup"><span data-stu-id="cdfdb-115">**Figure 02**: Unblocking the AJAX Control Toolkit ZIP file([Click to view full-size image](get-started-with-the-ajax-control-toolkit-vb/_static/image4.png))</span></span>


<span data-ttu-id="cdfdb-116">取消阻止该文件后，你可以将文件解压缩： 右键单击该文件并选择**提取所有**菜单选项。</span><span class="sxs-lookup"><span data-stu-id="cdfdb-116">After you unblock the file, you can unzip the file: Right-click the file and select the **Extract All** menu option.</span></span> <span data-ttu-id="cdfdb-117">现在，我们已准备好将该工具包添加到 Visual Studio/Visual Web Developer 工具箱。</span><span class="sxs-lookup"><span data-stu-id="cdfdb-117">Now, we are ready to add the toolkit to the Visual Studio/Visual Web Developer toolbox.</span></span>

## <a name="adding-the-ajax-control-toolkit-to-the-toolbox"></a><span data-ttu-id="cdfdb-118">添加到工具箱的 AJAX 控件工具包</span><span class="sxs-lookup"><span data-stu-id="cdfdb-118">Adding the AJAX Control Toolkit to the Toolbox</span></span>

<span data-ttu-id="cdfdb-119">使用 AJAX 控件工具包的最简单方法是将该工具包添加到 Visual Studio/Visual Web Developer 工具箱 （请参见图 3）。</span><span class="sxs-lookup"><span data-stu-id="cdfdb-119">The easiest way to use the AJAX Control Toolkit is to add the toolkit to your Visual Studio/Visual Web Developer toolbox (see Figure 3).</span></span> <span data-ttu-id="cdfdb-120">这样一来，你可以只需将工具包控件拖到页在你想要使用它。</span><span class="sxs-lookup"><span data-stu-id="cdfdb-120">That way, you can simply drag a toolkit control onto a page when you want to use it.</span></span>


<span data-ttu-id="cdfdb-121">[![AJAX 控件工具包将显示在工具箱](get-started-with-the-ajax-control-toolkit-vb/_static/image3.jpg)](get-started-with-the-ajax-control-toolkit-vb/_static/image5.png)</span><span class="sxs-lookup"><span data-stu-id="cdfdb-121">[![AJAX Control Toolkit appears in toolbox](get-started-with-the-ajax-control-toolkit-vb/_static/image3.jpg)](get-started-with-the-ajax-control-toolkit-vb/_static/image5.png)</span></span>

<span data-ttu-id="cdfdb-122">**图 03**: AJAX 控件工具包将显示在工具箱 ([单击以查看实际尺寸的图像](get-started-with-the-ajax-control-toolkit-vb/_static/image6.png))</span><span class="sxs-lookup"><span data-stu-id="cdfdb-122">**Figure 03**: AJAX Control Toolkit appears in toolbox([Click to view full-size image](get-started-with-the-ajax-control-toolkit-vb/_static/image6.png))</span></span>


<span data-ttu-id="cdfdb-123">首先，你需要向工具箱添加一个 AJAX 控件工具包选项卡。</span><span class="sxs-lookup"><span data-stu-id="cdfdb-123">First, you need to add an AJAX Control Toolkit tab to the toolbox.</span></span> <span data-ttu-id="cdfdb-124">请按照下列步骤。</span><span class="sxs-lookup"><span data-stu-id="cdfdb-124">Follow these steps.</span></span>

1. <span data-ttu-id="cdfdb-125">通过选择菜单选项文件中，新的网站中创建新的 ASP.NET 网站。</span><span class="sxs-lookup"><span data-stu-id="cdfdb-125">Create a new ASP.NET Website by selecting the menu option File, New Website.</span></span> <span data-ttu-id="cdfdb-126">双击解决方案资源管理器窗口中的 Default.aspx，以在编辑器中打开该文件。</span><span class="sxs-lookup"><span data-stu-id="cdfdb-126">Double-click the Default.aspx in the Solution Explorer window to open the file in the editor.</span></span>
2. <span data-ttu-id="cdfdb-127">右键单击常规选项卡下的工具箱，然后选择菜单选项**添加选项卡**（请参见图 4）。</span><span class="sxs-lookup"><span data-stu-id="cdfdb-127">Right-click the Toolbox beneath the General Tab and select the menu option **Add Tab** (see Figure 4).</span></span>
3. <span data-ttu-id="cdfdb-128">输入一个称为 AJAX 控件工具包的新选项卡。</span><span class="sxs-lookup"><span data-stu-id="cdfdb-128">Enter a new tab named AJAX Control Toolkit.</span></span>


<span data-ttu-id="cdfdb-129">[![添加新选项卡](get-started-with-the-ajax-control-toolkit-vb/_static/image4.jpg)](get-started-with-the-ajax-control-toolkit-vb/_static/image7.png)</span><span class="sxs-lookup"><span data-stu-id="cdfdb-129">[![Adding a new tab](get-started-with-the-ajax-control-toolkit-vb/_static/image4.jpg)](get-started-with-the-ajax-control-toolkit-vb/_static/image7.png)</span></span>

<span data-ttu-id="cdfdb-130">**图 04**： 添加新选项卡 ([单击以查看实际尺寸的图像](get-started-with-the-ajax-control-toolkit-vb/_static/image8.png))</span><span class="sxs-lookup"><span data-stu-id="cdfdb-130">**Figure 04**: Adding a new tab([Click to view full-size image](get-started-with-the-ajax-control-toolkit-vb/_static/image8.png))</span></span>


<span data-ttu-id="cdfdb-131">接下来，你需要将 AJAX 控件工具包控件添加到新选项卡。请执行这些步骤：</span><span class="sxs-lookup"><span data-stu-id="cdfdb-131">Next, you need to add the AJAX Control Toolkit controls to the new tab. Follow these steps:</span></span>

- <span data-ttu-id="cdfdb-132">AJAX 控件工具包选项卡下右键单击并选择菜单选项**选择项 （请参见图 5）**。</span><span class="sxs-lookup"><span data-stu-id="cdfdb-132">Right-click beneath the AJAX Control Toolkit tab and select the menu option **Choose Items (see Figure 5)**.</span></span>
- <span data-ttu-id="cdfdb-133">浏览到您解压缩 AJAX 控件工具包并选择 AjaxControlToolkit.dll 程序集的位置。</span><span class="sxs-lookup"><span data-stu-id="cdfdb-133">Browse to the location where you unzipped the AJAX Control Toolkit and select the AjaxControlToolkit.dll assembly.</span></span>


<span data-ttu-id="cdfdb-134">[![选择要添加到工具箱项](get-started-with-the-ajax-control-toolkit-vb/_static/image5.jpg)](get-started-with-the-ajax-control-toolkit-vb/_static/image9.png)</span><span class="sxs-lookup"><span data-stu-id="cdfdb-134">[![Choose items to add to the toolbox](get-started-with-the-ajax-control-toolkit-vb/_static/image5.jpg)](get-started-with-the-ajax-control-toolkit-vb/_static/image9.png)</span></span>

<span data-ttu-id="cdfdb-135">**图 05**： 选择要添加到工具箱项 ([单击以查看实际尺寸的图像](get-started-with-the-ajax-control-toolkit-vb/_static/image10.png))</span><span class="sxs-lookup"><span data-stu-id="cdfdb-135">**Figure 05**: Choose items to add to the toolbox([Click to view full-size image](get-started-with-the-ajax-control-toolkit-vb/_static/image10.png))</span></span>


<span data-ttu-id="cdfdb-136">完成这些步骤后，所有工具包控件都将出现在工具箱中。</span><span class="sxs-lookup"><span data-stu-id="cdfdb-136">After you complete these steps, all of the toolkit controls will appear in your toolbox.</span></span>

## <a name="upgrading-to-a-new-version-of-the-toolkit"></a><span data-ttu-id="cdfdb-137">升级到新版本的工具包</span><span class="sxs-lookup"><span data-stu-id="cdfdb-137">Upgrading to a New Version of the Toolkit</span></span>

<span data-ttu-id="cdfdb-138">如果你使用较旧版本的该工具包的并现在需要将移到更高版本是建议的步骤：</span><span class="sxs-lookup"><span data-stu-id="cdfdb-138">If you were using an older release of the Toolkit and now need to move to a later version here are the recommended steps:</span></span>

- <span data-ttu-id="cdfdb-139">二进制文件-从你的网站 Bin 文件夹中删除 AjaxControlToolkit.dll 程序集的旧版本。</span><span class="sxs-lookup"><span data-stu-id="cdfdb-139">Binaries - Delete the old version of the AjaxControlToolkit.dll assembly from your website Bin folder.</span></span>
- <span data-ttu-id="cdfdb-140">工具箱项-删除 AJAX 控件工具包选项卡，然后按照上述步骤以重新创建具有 AjaxControlToolkit.dll 程序集的新版本的选项卡。</span><span class="sxs-lookup"><span data-stu-id="cdfdb-140">Toolbox Items - Delete the AJAX Control Toolkit tab and follow the steps above to re-create the tab with the new version of the AjaxControlToolkit.dll assembly.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="cdfdb-141">[上一页](creating-a-custom-ajax-control-toolkit-control-extender-cs.md)
[下一页](using-ajax-control-toolkit-controls-and-control-extenders-vb.md)</span><span class="sxs-lookup"><span data-stu-id="cdfdb-141">[Previous](creating-a-custom-ajax-control-toolkit-control-extender-cs.md)
[Next](using-ajax-control-toolkit-controls-and-control-extenders-vb.md)</span></span>