---
uid: web-api/overview/web-api-routing-and-actions/routing-in-aspnet-web-api
title: "ASP.NET Web API 中的路由 |Microsoft 文档"
author: MikeWasson
description: 
ms.author: aspnetcontent
manager: wpickett
ms.date: 02/11/2012
ms.topic: article
ms.assetid: 0675bdc7-282f-4f47-b7f3-7e02133940ca
ms.technology: dotnet-webapi
ms.prod: .net-framework
msc.legacyurl: /web-api/overview/web-api-routing-and-actions/routing-in-aspnet-web-api
msc.type: authoredcontent
ms.openlocfilehash: aa0ecc96029051fef6a81ac08f7fcf52a24de59c
ms.sourcegitcommit: 9a9483aceb34591c97451997036a9120c3fe2baf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/10/2017
---
<a name="routing-in-aspnet-web-api"></a><span data-ttu-id="f6fe1-102">ASP.NET Web API 中的路由</span><span class="sxs-lookup"><span data-stu-id="f6fe1-102">Routing in ASP.NET Web API</span></span>
====================
<span data-ttu-id="f6fe1-103">通过[Mike Wasson](https://github.com/MikeWasson)</span><span class="sxs-lookup"><span data-stu-id="f6fe1-103">by [Mike Wasson](https://github.com/MikeWasson)</span></span>

<span data-ttu-id="f6fe1-104">本指南介绍了 ASP.NET Web API 将 HTTP 请求路由到控制器的方式。</span><span class="sxs-lookup"><span data-stu-id="f6fe1-104">This article describes how ASP.NET Web API routes HTTP requests to controllers.</span></span>

> [!NOTE]
> <span data-ttu-id="f6fe1-105">如果你熟悉使用 ASP.NET MVC，Web API 路由是非常类似于 MVC 路由。</span><span class="sxs-lookup"><span data-stu-id="f6fe1-105">If you are familiar with ASP.NET MVC, Web API routing is very similar to MVC routing.</span></span> <span data-ttu-id="f6fe1-106">主要区别是 Web API 使用的 HTTP 方法，而不是 URI 路径，选择的操作。</span><span class="sxs-lookup"><span data-stu-id="f6fe1-106">The main difference is that Web API uses the HTTP method, not the URI path, to select the action.</span></span> <span data-ttu-id="f6fe1-107">你还可以使用 MVC 样式中 Web API 的路由。</span><span class="sxs-lookup"><span data-stu-id="f6fe1-107">You can also use MVC-style routing in Web API.</span></span> <span data-ttu-id="f6fe1-108">本文不会采用 ASP.NET MVC 任何知识。</span><span class="sxs-lookup"><span data-stu-id="f6fe1-108">This article does not assume any knowledge of ASP.NET MVC.</span></span>


## <a name="routing-tables"></a><span data-ttu-id="f6fe1-109">路由表</span><span class="sxs-lookup"><span data-stu-id="f6fe1-109">Routing Tables</span></span>

<span data-ttu-id="f6fe1-110">在 ASP.NET Web API 中，*控制器*是处理 HTTP 请求的类。</span><span class="sxs-lookup"><span data-stu-id="f6fe1-110">In ASP.NET Web API, a *controller* is a class that handles HTTP requests.</span></span> <span data-ttu-id="f6fe1-111">控制器的公共方法在调用*操作方法*或只需*操作*。</span><span class="sxs-lookup"><span data-stu-id="f6fe1-111">The public methods of the controller are called *action methods* or simply *actions*.</span></span> <span data-ttu-id="f6fe1-112">当 Web API 框架收到请求时，它将请求路由到的操作。</span><span class="sxs-lookup"><span data-stu-id="f6fe1-112">When the Web API framework receives a request, it routes the request to an action.</span></span>

<span data-ttu-id="f6fe1-113">若要确定要调用的操作，框架将使用*路由表*。</span><span class="sxs-lookup"><span data-stu-id="f6fe1-113">To determine which action to invoke, the framework uses a *routing table*.</span></span> <span data-ttu-id="f6fe1-114">Web API 的 Visual Studio 项目模板创建的默认路由：</span><span class="sxs-lookup"><span data-stu-id="f6fe1-114">The Visual Studio project template for Web API creates a default route:</span></span>

[!code-csharp[Main](routing-in-aspnet-web-api/samples/sample1.cs)]

<span data-ttu-id="f6fe1-115">此路由定义在 WebApiConfig.cs 文件中，放置在应用程序\_启动目录：</span><span class="sxs-lookup"><span data-stu-id="f6fe1-115">This route is defined in the WebApiConfig.cs file, which is placed in the App\_Start directory:</span></span>

![](routing-in-aspnet-web-api/_static/image1.png)

<span data-ttu-id="f6fe1-116">有关详细信息**WebApiConfig**类，请参阅[配置 ASP.NET Web API](../advanced/configuring-aspnet-web-api.md)。</span><span class="sxs-lookup"><span data-stu-id="f6fe1-116">For more information about the **WebApiConfig** class, see [Configuring ASP.NET Web API](../advanced/configuring-aspnet-web-api.md).</span></span>

<span data-ttu-id="f6fe1-117">如果你自承载 Web API，则必须直接在上设置路由表**HttpSelfHostConfiguration**对象。</span><span class="sxs-lookup"><span data-stu-id="f6fe1-117">If you self-host Web API, you must set the routing table directly on the **HttpSelfHostConfiguration** object.</span></span> <span data-ttu-id="f6fe1-118">有关详细信息，请参阅[自承载 Web API](../older-versions/self-host-a-web-api.md)。</span><span class="sxs-lookup"><span data-stu-id="f6fe1-118">For more information, see [Self-Host a Web API](../older-versions/self-host-a-web-api.md).</span></span>

<span data-ttu-id="f6fe1-119">路由表中的每个条目包含*路由模板*。</span><span class="sxs-lookup"><span data-stu-id="f6fe1-119">Each entry in the routing table contains a *route template*.</span></span> <span data-ttu-id="f6fe1-120">Web API 的默认路由模板&quot;api / {controller} / {id}&quot;。</span><span class="sxs-lookup"><span data-stu-id="f6fe1-120">The default route template for Web API is &quot;api/{controller}/{id}&quot;.</span></span> <span data-ttu-id="f6fe1-121">在此模板中， &quot;api&quot;是文本路径段和 {controller} 和 {id} 占位符的变量。</span><span class="sxs-lookup"><span data-stu-id="f6fe1-121">In this template, &quot;api&quot; is a literal path segment, and {controller} and {id} are placeholder variables.</span></span>

<span data-ttu-id="f6fe1-122">当 Web API 框架收到 HTTP 请求时，它会尝试匹配对路由表中的路由模板之一的 URI。</span><span class="sxs-lookup"><span data-stu-id="f6fe1-122">When the Web API framework receives an HTTP request, it tries to match the URI against one of the route templates in the routing table.</span></span> <span data-ttu-id="f6fe1-123">如果没有路由与匹配，则客户端收到 404 错误。</span><span class="sxs-lookup"><span data-stu-id="f6fe1-123">If no route matches, the client receives a 404 error.</span></span> <span data-ttu-id="f6fe1-124">例如，下面的 Uri 匹配默认路由：</span><span class="sxs-lookup"><span data-stu-id="f6fe1-124">For example, the following URIs match the default route:</span></span>

- <span data-ttu-id="f6fe1-125">/ api/联系人</span><span class="sxs-lookup"><span data-stu-id="f6fe1-125">/api/contacts</span></span>
- <span data-ttu-id="f6fe1-126">/api/contacts/1</span><span class="sxs-lookup"><span data-stu-id="f6fe1-126">/api/contacts/1</span></span>
- <span data-ttu-id="f6fe1-127">/api/products/gizmo1</span><span class="sxs-lookup"><span data-stu-id="f6fe1-127">/api/products/gizmo1</span></span>

<span data-ttu-id="f6fe1-128">但是，下面的 URI 不匹配，因为它缺少&quot;api&quot;段：</span><span class="sxs-lookup"><span data-stu-id="f6fe1-128">However, the following URI does not match, because it lacks the &quot;api&quot; segment:</span></span>

- <span data-ttu-id="f6fe1-129">/ 联系人/1</span><span class="sxs-lookup"><span data-stu-id="f6fe1-129">/contacts/1</span></span>

> [!NOTE]
> <span data-ttu-id="f6fe1-130">在路由中使用"api"的原因是使用 ASP.NET MVC 路由避免冲突。</span><span class="sxs-lookup"><span data-stu-id="f6fe1-130">The reason for using "api" in the route is to avoid collisions with ASP.NET MVC routing.</span></span> <span data-ttu-id="f6fe1-131">这种方式，可以进行&quot;/联系&quot;转到一个 MVC 控制器，和&quot;/api/联系人&quot;转到 Web API 控制器。</span><span class="sxs-lookup"><span data-stu-id="f6fe1-131">That way, you can have &quot;/contacts&quot; go to an MVC controller, and &quot;/api/contacts&quot; go to a Web API controller.</span></span> <span data-ttu-id="f6fe1-132">当然，如果你不喜欢此约定，你可以更改默认的路由表。</span><span class="sxs-lookup"><span data-stu-id="f6fe1-132">Of course, if you don't like this convention, you can change the default route table.</span></span>

<span data-ttu-id="f6fe1-133">一旦找到匹配的路由，Web API 选择控制器和操作：</span><span class="sxs-lookup"><span data-stu-id="f6fe1-133">Once a matching route is found, Web API selects the controller and the action:</span></span>

- <span data-ttu-id="f6fe1-134">若要查找控制器，Web API 添加&quot;控制器&quot;为的值*{controller}*变量。</span><span class="sxs-lookup"><span data-stu-id="f6fe1-134">To find the controller, Web API adds &quot;Controller&quot; to the value of the *{controller}* variable.</span></span>
- <span data-ttu-id="f6fe1-135">若要查找操作，Web API 的 HTTP 方法，查找并随后查找名称开头的 HTTP 方法名称的操作。</span><span class="sxs-lookup"><span data-stu-id="f6fe1-135">To find the action, Web API looks at the HTTP method, and then looks for an action whose name begins with that HTTP method name.</span></span> <span data-ttu-id="f6fe1-136">例如，使用 GET 请求，Web API 中寻找开头的操作&quot;获取...&quot;，如&quot;GetContact&quot;或&quot;GetAllContacts&quot;。</span><span class="sxs-lookup"><span data-stu-id="f6fe1-136">For example, with a GET request, Web API looks for an action that starts with &quot;Get...&quot;, such as &quot;GetContact&quot; or &quot;GetAllContacts&quot;.</span></span> <span data-ttu-id="f6fe1-137">此约定仅适用于获取、 POST、 PUT 和删除方法。</span><span class="sxs-lookup"><span data-stu-id="f6fe1-137">This convention applies only to GET, POST, PUT, and DELETE methods.</span></span> <span data-ttu-id="f6fe1-138">可以通过在你的控制器上使用属性来启用其他 HTTP 方法。</span><span class="sxs-lookup"><span data-stu-id="f6fe1-138">You can enable other HTTP methods by using attributes on your controller.</span></span> <span data-ttu-id="f6fe1-139">我们将更高版本看到举例说明的。</span><span class="sxs-lookup"><span data-stu-id="f6fe1-139">We'll see an example of that later.</span></span>
- <span data-ttu-id="f6fe1-140">在路由模板中，其他占位符变量如*{id}、*映射到操作参数。</span><span class="sxs-lookup"><span data-stu-id="f6fe1-140">Other placeholder variables in the route template, such as *{id},* are mapped to action parameters.</span></span>

<span data-ttu-id="f6fe1-141">让我们看一个示例。</span><span class="sxs-lookup"><span data-stu-id="f6fe1-141">Let's look at an example.</span></span> <span data-ttu-id="f6fe1-142">假设定义以下控制器：</span><span class="sxs-lookup"><span data-stu-id="f6fe1-142">Suppose that you define the following controller:</span></span>

[!code-csharp[Main](routing-in-aspnet-web-api/samples/sample2.cs)]

<span data-ttu-id="f6fe1-143">下面是一些可能的 HTTP 请求，以及每个调用的操作：</span><span class="sxs-lookup"><span data-stu-id="f6fe1-143">Here are some possible HTTP requests, along with the action that gets invoked for each:</span></span>

| <span data-ttu-id="f6fe1-144">HTTP 方法</span><span class="sxs-lookup"><span data-stu-id="f6fe1-144">HTTP Method</span></span> | <span data-ttu-id="f6fe1-145">URI 路径</span><span class="sxs-lookup"><span data-stu-id="f6fe1-145">URI Path</span></span> | <span data-ttu-id="f6fe1-146">操作</span><span class="sxs-lookup"><span data-stu-id="f6fe1-146">Action</span></span> | <span data-ttu-id="f6fe1-147">参数</span><span class="sxs-lookup"><span data-stu-id="f6fe1-147">Parameter</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="f6fe1-148">GET</span><span class="sxs-lookup"><span data-stu-id="f6fe1-148">GET</span></span> | <span data-ttu-id="f6fe1-149">api/产品</span><span class="sxs-lookup"><span data-stu-id="f6fe1-149">api/products</span></span> | <span data-ttu-id="f6fe1-150">GetAllProducts</span><span class="sxs-lookup"><span data-stu-id="f6fe1-150">GetAllProducts</span></span> | <span data-ttu-id="f6fe1-151">*（无）*</span><span class="sxs-lookup"><span data-stu-id="f6fe1-151">*(none)*</span></span> |
| <span data-ttu-id="f6fe1-152">GET</span><span class="sxs-lookup"><span data-stu-id="f6fe1-152">GET</span></span> | <span data-ttu-id="f6fe1-153">api/产品/4</span><span class="sxs-lookup"><span data-stu-id="f6fe1-153">api/products/4</span></span> | <span data-ttu-id="f6fe1-154">GetProductById</span><span class="sxs-lookup"><span data-stu-id="f6fe1-154">GetProductById</span></span> | <span data-ttu-id="f6fe1-155">4</span><span class="sxs-lookup"><span data-stu-id="f6fe1-155">4</span></span> |
| <span data-ttu-id="f6fe1-156">DELETE</span><span class="sxs-lookup"><span data-stu-id="f6fe1-156">DELETE</span></span> | <span data-ttu-id="f6fe1-157">api/产品/4</span><span class="sxs-lookup"><span data-stu-id="f6fe1-157">api/products/4</span></span> | <span data-ttu-id="f6fe1-158">DeleteProduct</span><span class="sxs-lookup"><span data-stu-id="f6fe1-158">DeleteProduct</span></span> | <span data-ttu-id="f6fe1-159">4</span><span class="sxs-lookup"><span data-stu-id="f6fe1-159">4</span></span> |
| <span data-ttu-id="f6fe1-160">发布</span><span class="sxs-lookup"><span data-stu-id="f6fe1-160">POST</span></span> | <span data-ttu-id="f6fe1-161">api/产品</span><span class="sxs-lookup"><span data-stu-id="f6fe1-161">api/products</span></span> | <span data-ttu-id="f6fe1-162">*（没有匹配项）*</span><span class="sxs-lookup"><span data-stu-id="f6fe1-162">*(no match)*</span></span> |  |

<span data-ttu-id="f6fe1-163">请注意， *{id}*段的 URI，如果存在，将映射到*id*操作的参数。</span><span class="sxs-lookup"><span data-stu-id="f6fe1-163">Notice that the *{id}* segment of the URI, if present, is mapped to the *id* parameter of the action.</span></span> <span data-ttu-id="f6fe1-164">在此示例中，控制器定义两个 GET 方法，其中一个有*id*参数，另一个不带任何参数。</span><span class="sxs-lookup"><span data-stu-id="f6fe1-164">In this example, the controller defines two GET methods, one with an *id* parameter and one with no parameters.</span></span>

<span data-ttu-id="f6fe1-165">此外，请注意，POST 请求将失败，因为控制器不会定义&quot;Post...&quot;方法。</span><span class="sxs-lookup"><span data-stu-id="f6fe1-165">Also, note that the POST request will fail, because the controller does not define a &quot;Post...&quot; method.</span></span>

## <a name="routing-variations"></a><span data-ttu-id="f6fe1-166">路由的变体</span><span class="sxs-lookup"><span data-stu-id="f6fe1-166">Routing Variations</span></span>

<span data-ttu-id="f6fe1-167">上一节所述 ASP.NET Web API 的基本路由机制。</span><span class="sxs-lookup"><span data-stu-id="f6fe1-167">The previous section described the basic routing mechanism for ASP.NET Web API.</span></span> <span data-ttu-id="f6fe1-168">本部分介绍一些变体。</span><span class="sxs-lookup"><span data-stu-id="f6fe1-168">This section describes some variations.</span></span>

### <a name="http-methods"></a><span data-ttu-id="f6fe1-169">HTTP 方法</span><span class="sxs-lookup"><span data-stu-id="f6fe1-169">HTTP Methods</span></span>

<span data-ttu-id="f6fe1-170">而不是使用 HTTP 方法的命名约定，你可以显式指定操作的 HTTP 方法的修饰具有的操作方法**HttpGet**， **HttpPut**， **HttpPost**，或**HttpDelete**属性。</span><span class="sxs-lookup"><span data-stu-id="f6fe1-170">Instead of using the naming convention for HTTP methods, you can explicitly specify the HTTP method for an action by decorating the action method with the **HttpGet**, **HttpPut**, **HttpPost**, or **HttpDelete** attribute.</span></span>

<span data-ttu-id="f6fe1-171">在下面的示例中，FindProduct 方法映射到 GET 请求：</span><span class="sxs-lookup"><span data-stu-id="f6fe1-171">In the following example, the FindProduct method is mapped to GET requests:</span></span>

[!code-csharp[Main](routing-in-aspnet-web-api/samples/sample3.cs)]

<span data-ttu-id="f6fe1-172">若要允许多个 HTTP 方法对于一个操作，或允许 GET、 PUT、 POST 和 DELETE 以外的 HTTP 方法，使用**AcceptVerbs**属性，它采用 HTTP 方法的列表。</span><span class="sxs-lookup"><span data-stu-id="f6fe1-172">To allow multiple HTTP methods for an action, or to allow HTTP methods other than GET, PUT, POST, and DELETE, use the **AcceptVerbs** attribute, which takes a list of HTTP methods.</span></span>

[!code-csharp[Main](routing-in-aspnet-web-api/samples/sample4.cs)]

<a id="routing_by_action_name"></a>
### <a name="routing-by-action-name"></a><span data-ttu-id="f6fe1-173">路由由操作名称</span><span class="sxs-lookup"><span data-stu-id="f6fe1-173">Routing by Action Name</span></span>

<span data-ttu-id="f6fe1-174">与默认路由模板中，Web API 使用的 HTTP 方法来选择操作。</span><span class="sxs-lookup"><span data-stu-id="f6fe1-174">With the default routing template, Web API uses the HTTP method to select the action.</span></span> <span data-ttu-id="f6fe1-175">但是，你还可以创建一个路由，其中 URI 中包含的操作名称：</span><span class="sxs-lookup"><span data-stu-id="f6fe1-175">However, you can also create a route where the action name is included in the URI:</span></span>

[!code-csharp[Main](routing-in-aspnet-web-api/samples/sample5.cs)]

<span data-ttu-id="f6fe1-176">在此路由模板中， *{action}*参数名称在控制器上的操作方法。</span><span class="sxs-lookup"><span data-stu-id="f6fe1-176">In this route template, the *{action}* parameter names the action method on the controller.</span></span> <span data-ttu-id="f6fe1-177">这种样式的路由，与使用属性来指定允许的 HTTP 方法。</span><span class="sxs-lookup"><span data-stu-id="f6fe1-177">With this style of routing, use attributes to specify the allowed HTTP methods.</span></span> <span data-ttu-id="f6fe1-178">例如，假设你的控制器具有以下方法：</span><span class="sxs-lookup"><span data-stu-id="f6fe1-178">For example, suppose your controller has the following method:</span></span>

[!code-csharp[Main](routing-in-aspnet-web-api/samples/sample6.cs)]

<span data-ttu-id="f6fe1-179">在这种情况下，"api/产品/详细信息/1"的 GET 请求将映射为详细信息方法。</span><span class="sxs-lookup"><span data-stu-id="f6fe1-179">In this case, a GET request for "api/products/details/1" would map to the Details method.</span></span> <span data-ttu-id="f6fe1-180">这种样式的路由类似于 ASP.NET MVC，并且可能适合 RPC 样式 API。</span><span class="sxs-lookup"><span data-stu-id="f6fe1-180">This style of routing is similar to ASP.NET MVC, and may be appropriate for an RPC-style API.</span></span>

<span data-ttu-id="f6fe1-181">你可以使用重写的操作名称**ActionName**属性。</span><span class="sxs-lookup"><span data-stu-id="f6fe1-181">You can override the action name by using the **ActionName** attribute.</span></span> <span data-ttu-id="f6fe1-182">在以下示例中，有两个操作映射到&quot;缩略图产品/api / /*id*。必须有一个支持 GET 和其他支持文章：</span><span class="sxs-lookup"><span data-stu-id="f6fe1-182">In the following example, there are two actions that map to &quot;api/products/thumbnail/*id*. One supports GET and the other supports POST:</span></span>

[!code-csharp[Main](routing-in-aspnet-web-api/samples/sample7.cs)]

### <a name="non-actions"></a><span data-ttu-id="f6fe1-183">非操作</span><span class="sxs-lookup"><span data-stu-id="f6fe1-183">Non-Actions</span></span>

<span data-ttu-id="f6fe1-184">若要阻止用作一项操作正在调用的方法，使用**NonAction**属性。</span><span class="sxs-lookup"><span data-stu-id="f6fe1-184">To prevent a method from getting invoked as an action, use the **NonAction** attribute.</span></span> <span data-ttu-id="f6fe1-185">这指示 framework 此方法不是操作，即使它否则将匹配的路由规则。</span><span class="sxs-lookup"><span data-stu-id="f6fe1-185">This signals to the framework that the method is not an action, even if it would otherwise match the routing rules.</span></span>

[!code-csharp[Main](routing-in-aspnet-web-api/samples/sample8.cs)]

## <a name="further-reading"></a><span data-ttu-id="f6fe1-186">其他阅读材料</span><span class="sxs-lookup"><span data-stu-id="f6fe1-186">Further Reading</span></span>

<span data-ttu-id="f6fe1-187">本主题提供路由的高级的视图。</span><span class="sxs-lookup"><span data-stu-id="f6fe1-187">This topic provided a high-level view of routing.</span></span> <span data-ttu-id="f6fe1-188">有关详细信息，请参阅[路由和操作选择](routing-and-action-selection.md)，用于描述完全如何框架路由到的 URI 匹配、 选择一个控制器，然后选择要调用的操作。</span><span class="sxs-lookup"><span data-stu-id="f6fe1-188">For more detail, see [Routing and Action Selection](routing-and-action-selection.md), which describes exactly how the framework matches a URI to a route, selects a controller, and then selects the action to invoke.</span></span>