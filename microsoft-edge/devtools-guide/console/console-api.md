---
description: 使用控制台 API 以编程方式调试和分析你的代码
title: DevTools-控制台 API
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 03/05/2020
ms.topic: article
ms.prod: microsoft-edge
keywords: microsoft edge、web 开发、f12 工具、devtools、控制台 api
ms.custom: seodec18
ms.openlocfilehash: d722934c3694c3c23e367141158ad45f6d03b175
ms.sourcegitcommit: 6860234c25a8be863b7f29a54838e78e120dbb62
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/09/2020
ms.locfileid: "10564328"
---
# <span data-ttu-id="c6c14-104">控制台 API</span><span class="sxs-lookup"><span data-stu-id="c6c14-104">Console API</span></span>

<span data-ttu-id="c6c14-105">*控制台 API*通过全局对象提供对 DevTools 控制台的命令行和编程访问 `console` ，使你可以：</span><span class="sxs-lookup"><span data-stu-id="c6c14-105">The *Console API* provides command-line and programmatic access to the  DevTools Console through the global `console` object, allowing you to:</span></span>

 - <span data-ttu-id="c6c14-106">记录来自你的代码的[自定义消息](#logging-custom-messages)</span><span class="sxs-lookup"><span data-stu-id="c6c14-106">[Log custom messages](#logging-custom-messages) from you code</span></span>
 - <span data-ttu-id="c6c14-107">[检查对象和元素](#inspecting-objects-and-elements)并记录其信息</span><span class="sxs-lookup"><span data-stu-id="c6c14-107">[Inspect objects and elements](#inspecting-objects-and-elements) and log their information</span></span>
 - <span data-ttu-id="c6c14-108">通过设置断言、计时器和计数器来[测试和测量代码](#testing-and-measuring)</span><span class="sxs-lookup"><span data-stu-id="c6c14-108">[Test and measure your code](#testing-and-measuring) by setting assertions, timers and counters</span></span>
 - <span data-ttu-id="c6c14-109">[获取堆的快照](#taking-heap-snapshots)以评估运行代码的内存占用并确定内存泄漏</span><span class="sxs-lookup"><span data-stu-id="c6c14-109">[Take snapshots of the heap](#taking-heap-snapshots) to assess the memory consumption of your running code and identify memory leaks</span></span>
 - <span data-ttu-id="c6c14-110">[跟踪你的 callstacks](#tracing-callstacks)以了解你的代码的调用位置</span><span class="sxs-lookup"><span data-stu-id="c6c14-110">[Trace your callstacks](#tracing-callstacks) to understand where your code is being called from</span></span> 
 - <span data-ttu-id="c6c14-111">[整理日志输出](#organizing-log-output)以简化调试</span><span class="sxs-lookup"><span data-stu-id="c6c14-111">[Organize your log output](#organizing-log-output) to streamline your debugging</span></span>

<span data-ttu-id="c6c14-112">以下是 Microsoft Edge 当前支持的命令和格式设置参数。</span><span class="sxs-lookup"><span data-stu-id="c6c14-112">The following are the commands and formatting parameters currently supported by Microsoft Edge.</span></span> <span data-ttu-id="c6c14-113">它们在主要浏览器上的工作方式类似。</span><span class="sxs-lookup"><span data-stu-id="c6c14-113">They work similarly on major browsers.</span></span>

## <span data-ttu-id="c6c14-114">记录自定义消息</span><span class="sxs-lookup"><span data-stu-id="c6c14-114">Logging custom messages</span></span>

<span data-ttu-id="c6c14-115">你的代码可以向控制台发送多种类型的自定义消息，包括：</span><span class="sxs-lookup"><span data-stu-id="c6c14-115">Your code can send several types of custom messages to the console, including:</span></span>

<span data-ttu-id="c6c14-116">消息类型</span><span class="sxs-lookup"><span data-stu-id="c6c14-116">Message type</span></span>  | &nbsp;   |
:------------------- | :------ |
<span data-ttu-id="c6c14-117">[**错误（）**](https://developer.mozilla.org/docs/Web/API/Console/error)和[**异常（）**](https://developer.mozilla.org/docs/Web/API/Console/error)</span><span class="sxs-lookup"><span data-stu-id="c6c14-117">[**error()**](https://developer.mozilla.org/docs/Web/API/Console/error) and [**exception()**](https://developer.mozilla.org/docs/Web/API/Console/error)</span></span>| <span data-ttu-id="c6c14-118">关键错误和故障</span><span class="sxs-lookup"><span data-stu-id="c6c14-118">Critical errors and failures</span></span>
[**<span data-ttu-id="c6c14-119">警告（）</span><span class="sxs-lookup"><span data-stu-id="c6c14-119">warn()</span></span>**](https://developer.mozilla.org/docs/Web/API/Console/warn) | <span data-ttu-id="c6c14-120">可能的错误或意外行为</span><span class="sxs-lookup"><span data-stu-id="c6c14-120">Possible errors or unexpected behavior</span></span> 
[**<span data-ttu-id="c6c14-121">info （）</span><span class="sxs-lookup"><span data-stu-id="c6c14-121">info()</span></span>**](https://developer.mozilla.org/docs/Web/API/Console/info) | <span data-ttu-id="c6c14-122">有用但不重要的信息</span><span class="sxs-lookup"><span data-stu-id="c6c14-122">Useful, but non-critical information</span></span>
<span data-ttu-id="c6c14-123">[**log （）**](https://developer.mozilla.org/docs/Web/API/Console/log)和[ **debug （）**](https://developer.mozilla.org/docs/Web/API/Console/log)</span><span class="sxs-lookup"><span data-stu-id="c6c14-123">[**log()**](https://developer.mozilla.org/docs/Web/API/Console/log) and [**debug()**](https://developer.mozilla.org/docs/Web/API/Console/log)</span></span> | <span data-ttu-id="c6c14-124">常规调试（不在控制台中生成系统警报图标）</span><span class="sxs-lookup"><span data-stu-id="c6c14-124">General debugging (without generating a system alert icon in the console)</span></span>

   
<span data-ttu-id="c6c14-125">您可以将这些邮件与从 "控制台" 面板中的 Microsoft Edge 生成的其他邮件组合在一起并进行筛选。</span><span class="sxs-lookup"><span data-stu-id="c6c14-125">You can group and filter these along with the other messages generated from Microsoft Edge from the  Console panel.</span></span> <span data-ttu-id="c6c14-126">所有自定义邮件方法都需要字符串（message）参数和可选的格式替换参数。</span><span class="sxs-lookup"><span data-stu-id="c6c14-126">All custom message methods require a string (message) parameter and optional format substitution parameters.</span></span> <span data-ttu-id="c6c14-127">Microsoft Edge 支持下列格式设置选项：</span><span class="sxs-lookup"><span data-stu-id="c6c14-127">Microsoft Edge supports the following formatting options:</span></span>

<span data-ttu-id="c6c14-128">格式参数</span><span class="sxs-lookup"><span data-stu-id="c6c14-128">Format parameter</span></span> | &nbsp;
:------------------- | :--- |
**<span data-ttu-id="c6c14-129">% b</span><span class="sxs-lookup"><span data-stu-id="c6c14-129">%b</span></span>** | <span data-ttu-id="c6c14-130">二进制文件</span><span class="sxs-lookup"><span data-stu-id="c6c14-130">Binary</span></span>
**<span data-ttu-id="c6c14-131">% c</span><span class="sxs-lookup"><span data-stu-id="c6c14-131">%c</span></span>** | <span data-ttu-id="c6c14-132">内联 CSS 样式（请参阅下面的示例）</span><span class="sxs-lookup"><span data-stu-id="c6c14-132">Inline CSS style (see example below)</span></span>
<span data-ttu-id="c6c14-133">**% d**， **% i**</span><span class="sxs-lookup"><span data-stu-id="c6c14-133">**%d**, **%i**</span></span> | <span data-ttu-id="c6c14-134">整型</span><span class="sxs-lookup"><span data-stu-id="c6c14-134">Integer</span></span> 
**<span data-ttu-id="c6c14-135">% f</span><span class="sxs-lookup"><span data-stu-id="c6c14-135">%f</span></span>** | <span data-ttu-id="c6c14-136">Float</span><span class="sxs-lookup"><span data-stu-id="c6c14-136">Float</span></span>  
**<span data-ttu-id="c6c14-137">% s</span><span class="sxs-lookup"><span data-stu-id="c6c14-137">%s</span></span>** | <span data-ttu-id="c6c14-138">字符串</span><span class="sxs-lookup"><span data-stu-id="c6c14-138">String</span></span> 
**<span data-ttu-id="c6c14-139">% x</span><span class="sxs-lookup"><span data-stu-id="c6c14-139">%x</span></span>** | <span data-ttu-id="c6c14-140">十六进制数</span><span class="sxs-lookup"><span data-stu-id="c6c14-140">Hexadecimal</span></span> 
**<span data-ttu-id="c6c14-141">% e</span><span class="sxs-lookup"><span data-stu-id="c6c14-141">%e</span></span>** | <span data-ttu-id="c6c14-142">加</span><span class="sxs-lookup"><span data-stu-id="c6c14-142">Exponent</span></span> 

<span data-ttu-id="c6c14-143">例如，下面介绍了如何在日志消息中包含字符串和整数变量：</span><span class="sxs-lookup"><span data-stu-id="c6c14-143">For example, here's how you would include string and integer variables in your log message:</span></span>

```javascript
var myText = 'pieces';
var myVal = 5;
console.log("The number of %s is %d.", myText, myVal);
```

>`The number of pieces is 5.`

<span data-ttu-id="c6c14-144">下面介绍了如何使用内联 CSS （）向日志消息添加绿色突出显示效果 `%c` ：</span><span class="sxs-lookup"><span data-stu-id="c6c14-144">And here's how you might add a green highlight effect to a log message with inline CSS (`%c`):</span></span>

```javascript
console.log("%cHighlight this log message in green", "background-color: #10ff00; text-transform: uppercase;");
```

![带有内联样式的控制台日志](../media/console_api_css.png)

## <span data-ttu-id="c6c14-146">检查对象和元素</span><span class="sxs-lookup"><span data-stu-id="c6c14-146">Inspecting objects and elements</span></span>

<span data-ttu-id="c6c14-147">Inspectable 对象在具有可展开节点的折叠树视图中显示在控制台中。</span><span class="sxs-lookup"><span data-stu-id="c6c14-147">Inspectable objects appear in the console in a collapsed tree view with expandable nodes.</span></span> <span data-ttu-id="c6c14-148">控制台检测你是要发送的是 DOM 节点（如 div）还是 JavaScript 对象（如事件），并自动将其显示为检测到的类型。</span><span class="sxs-lookup"><span data-stu-id="c6c14-148">The console detects whether you are sending a DOM node (like a div) or a JavaScript object (like an event) and displays them as the detected type automatically.</span></span>

<span data-ttu-id="c6c14-149">您还可以强制执行特定输出：</span><span class="sxs-lookup"><span data-stu-id="c6c14-149">You can also force a specific output:</span></span>

<span data-ttu-id="c6c14-150">命令</span><span class="sxs-lookup"><span data-stu-id="c6c14-150">Command</span></span> | &nbsp;
:------------------- | :--- |
[**<span data-ttu-id="c6c14-151">dir （）</span><span class="sxs-lookup"><span data-stu-id="c6c14-151">dir()</span></span>**](https://developer.mozilla.org/docs/Web/API/Console/dir) | <span data-ttu-id="c6c14-152">显示为 inspectable JavaScript 对象</span><span class="sxs-lookup"><span data-stu-id="c6c14-152">Displays as inspectable JavaScript object</span></span>
[**<span data-ttu-id="c6c14-153">dirxml()</span><span class="sxs-lookup"><span data-stu-id="c6c14-153">dirxml()</span></span>**](https://developer.mozilla.org/docs/Web/API/Console/dirxml) | <span data-ttu-id="c6c14-154">显示为 inspectable DOM 节点</span><span class="sxs-lookup"><span data-stu-id="c6c14-154">Displays as inspectable DOM node</span></span>

<span data-ttu-id="c6c14-155">例如，尝试打开控制台并比较 `<div id='main'>` 此页面上的元素的以下输出：</span><span class="sxs-lookup"><span data-stu-id="c6c14-155">For example, try opening the console and compare the following outputs for the `<div id='main'>` element on this page:</span></span>

```javascript
console.dir(document.querySelector('#main'));
console.dirxml(document.querySelector('#main'));
```

!["Dir" 与 "dirxml" 输出的比较](../media/console_api_dir.png)

### <span data-ttu-id="c6c14-157">在 "**元素**" 面板中选择一个元素</span><span class="sxs-lookup"><span data-stu-id="c6c14-157">Selecting an element in the **Elements** panel</span></span>

<span data-ttu-id="c6c14-158">你可以直接从控制台选择页面的 HTML 树上下文中的元素，以便立即进行布局和样式调试。</span><span class="sxs-lookup"><span data-stu-id="c6c14-158">You can select an element within the HTML tree context of the page directly from the console for immediate layout and style debugging.</span></span>

<span data-ttu-id="c6c14-159">命令</span><span class="sxs-lookup"><span data-stu-id="c6c14-159">Command</span></span> | &nbsp;
:------------------- | :--- |
**<span data-ttu-id="c6c14-160">select （）</span><span class="sxs-lookup"><span data-stu-id="c6c14-160">select()</span></span>** | <span data-ttu-id="c6c14-161">切换到 "**元素**" 面板，并将焦点设置到指定的元素。</span><span class="sxs-lookup"><span data-stu-id="c6c14-161">Switches to the **Elements** panel and sets focus to the specified element.</span></span>

<span data-ttu-id="c6c14-162">例如，如果您在此页面上打开控制台，请键入：</span><span class="sxs-lookup"><span data-stu-id="c6c14-162">For example, if you open the console on this page and type:</span></span>

```javascript
console.select(document.querySelector("body"));
```

<span data-ttu-id="c6c14-163">DevTools 将切换到 "元素" 面板（如果它尚不是当前**元素**），并将焦点放在[*HTML 树视图*](../elements.md#html-tree-view)中的指定元素。</span><span class="sxs-lookup"><span data-stu-id="c6c14-163">The DevTools will switch to the **Elements** panel (if its not already the current) and set focus in the [*HTML tree view*](../elements.md#html-tree-view) to the specified element.</span></span>

!["Select" 方法的示例](../media/console_api_select.png)

## <span data-ttu-id="c6c14-165">测试和测量</span><span class="sxs-lookup"><span data-stu-id="c6c14-165">Testing and measuring</span></span>

### <span data-ttu-id="c6c14-166">测试代码</span><span class="sxs-lookup"><span data-stu-id="c6c14-166">Testing your code</span></span>

<span data-ttu-id="c6c14-167">将控制台 API 测试声明添加到你的代码中，以便在浏览器中运行单元测试和调试代码。</span><span class="sxs-lookup"><span data-stu-id="c6c14-167">Add Console API test assertions to your code for unit testing and debugging your code as it runs in the browser.</span></span>

<span data-ttu-id="c6c14-168">命令</span><span class="sxs-lookup"><span data-stu-id="c6c14-168">Command</span></span> | &nbsp;
:------------ | :-------------
[**<span data-ttu-id="c6c14-169">assert （）</span><span class="sxs-lookup"><span data-stu-id="c6c14-169">assert()</span></span>**](https://developer.mozilla.org/docs/Web/API/Console/assert) | <span data-ttu-id="c6c14-170">如果所提供的表达式的计算结果为*false*，则记录一个控制台错误消息。</span><span class="sxs-lookup"><span data-stu-id="c6c14-170">Logs a console error message if the provided expression evaluates to *false*.</span></span>

<span data-ttu-id="c6c14-171">除了作为可测试断言提供的逻辑表达式外，你还可以添加可选消息和格式参数，就像使用其他[自定义控制台消息](#logging-custom-messages)一样。</span><span class="sxs-lookup"><span data-stu-id="c6c14-171">In addition to the logical expression you supply as the testable assertion, you can add an optional message and formatting parameters as you would use with other [custom console messages](#logging-custom-messages).</span></span> <span data-ttu-id="c6c14-172">例如：</span><span class="sxs-lookup"><span data-stu-id="c6c14-172">For example:</span></span>

```javascript
var x = 26.8;
console.assert(x < 25, 'The value of x is %f (it is NOT less than %i)', x, 25);
```

!["Assert" 方法的示例](../media/console_api_assert.png)

### <span data-ttu-id="c6c14-174">统计代码中的执行次数</span><span class="sxs-lookup"><span data-stu-id="c6c14-174">Counting executions in your code</span></span>

<span data-ttu-id="c6c14-175">你可以在你的代码中设置计数器以跟踪已执行前后代码的次数。</span><span class="sxs-lookup"><span data-stu-id="c6c14-175">You can set counters in your code to keep track of how many times the surrounding code gets executed.</span></span> <span data-ttu-id="c6c14-176">设置计数器有助于确保你的代码按预期运行，并帮助你诊断性能瓶颈。</span><span class="sxs-lookup"><span data-stu-id="c6c14-176">Setting counters can help ensure your code is running as expected and assist you in diagnosing performance bottlenecks.</span></span>

<span data-ttu-id="c6c14-177">命令</span><span class="sxs-lookup"><span data-stu-id="c6c14-177">Command</span></span> | &nbsp;
:------------ | :-------------
[**<span data-ttu-id="c6c14-178">count （）</span><span class="sxs-lookup"><span data-stu-id="c6c14-178">count()</span></span>**](https://developer.mozilla.org/docs/Web/API/Console/count) | <span data-ttu-id="c6c14-179">增量和记录已执行给定标签的次数*计数（）* 。</span><span class="sxs-lookup"><span data-stu-id="c6c14-179">Increments and logs the number of times *count()* for the given label has been executed.</span></span>
[**<span data-ttu-id="c6c14-180">countReset()</span><span class="sxs-lookup"><span data-stu-id="c6c14-180">countReset()</span></span>**](https://developer.mozilla.org/docs/Web/API/Console/countReset) | <span data-ttu-id="c6c14-181">将给定计数器标签的计数重置为零。</span><span class="sxs-lookup"><span data-stu-id="c6c14-181">Resets the count to zero for the given counter label.</span></span>

<span data-ttu-id="c6c14-182">例如，在控制台中执行以下行：</span><span class="sxs-lookup"><span data-stu-id="c6c14-182">For example, executing the following lines in console:</span></span>

```javascript
console.count('My Counter');
console.count('My Counter');
console.countReset('My Counter');
console.count('My Counter');
```

 <span data-ttu-id="c6c14-183">.</span><span class="sxs-lookup"><span data-stu-id="c6c14-183">.</span></span> <span data-ttu-id="c6c14-184">.</span><span class="sxs-lookup"><span data-stu-id="c6c14-184">.</span></span> <span data-ttu-id="c6c14-185">.</span><span class="sxs-lookup"><span data-stu-id="c6c14-185">.</span></span> <span data-ttu-id="c6c14-186">将导致：</span><span class="sxs-lookup"><span data-stu-id="c6c14-186">will result in:</span></span>
> <span data-ttu-id="c6c14-187">我的计数器：1</span><span class="sxs-lookup"><span data-stu-id="c6c14-187">My Counter: 1</span></span>

### <span data-ttu-id="c6c14-188">对代码计时</span><span class="sxs-lookup"><span data-stu-id="c6c14-188">Timing your code</span></span>

<span data-ttu-id="c6c14-189">使用带有标签的计时器检测代码，以测量完成给定操作所需的时间。</span><span class="sxs-lookup"><span data-stu-id="c6c14-189">Instrument your code with labeled timers to measure how long it takes to complete a given operation.</span></span>

<span data-ttu-id="c6c14-190">命令</span><span class="sxs-lookup"><span data-stu-id="c6c14-190">Command</span></span> | &nbsp;
:------------ | :-------------
[**<span data-ttu-id="c6c14-191">时间（）</span><span class="sxs-lookup"><span data-stu-id="c6c14-191">time()</span></span>**](https://developer.mozilla.org/docs/Web/API/Console/time) | <span data-ttu-id="c6c14-192">启动具有给定标签的计时器。</span><span class="sxs-lookup"><span data-stu-id="c6c14-192">Starts a timer with the given label.</span></span>
[**<span data-ttu-id="c6c14-193">timeEnd()</span><span class="sxs-lookup"><span data-stu-id="c6c14-193">timeEnd()</span></span>**](https://developer.mozilla.org/docs/Web/API/Console/timeEnd) | <span data-ttu-id="c6c14-194">结束带有给定标签的计时器，并报告已用时间（以毫秒为单位）。</span><span class="sxs-lookup"><span data-stu-id="c6c14-194">Ends the timer with the given label and reports the time elapsed (in milliseconds).</span></span>
[**<span data-ttu-id="c6c14-195">timeStamp （）</span><span class="sxs-lookup"><span data-stu-id="c6c14-195">timeStamp()</span></span>**](https://developer.mozilla.org/docs/Web/API/Console/timeStamp) | <span data-ttu-id="c6c14-196">报告当前系统时间（以毫秒为单位）。</span><span class="sxs-lookup"><span data-stu-id="c6c14-196">Reports the current system time (in milliseconds).</span></span>

<span data-ttu-id="c6c14-197">例如，请尝试在控制台中执行以下行：</span><span class="sxs-lookup"><span data-stu-id="c6c14-197">For example, try executing the following lines in console:</span></span>

```javascript
console.time('My Timer');
console.timeEnd('My Timer');
```

### <span data-ttu-id="c6c14-198">获取堆快照</span><span class="sxs-lookup"><span data-stu-id="c6c14-198">Taking heap snapshots</span></span>

<span data-ttu-id="c6c14-199">获取堆的快照，以评估运行代码的内存占用并确定内存泄漏。</span><span class="sxs-lookup"><span data-stu-id="c6c14-199">Take snapshots of the heap to assess the memory consumption of your running code and identify memory leaks.</span></span>

<span data-ttu-id="c6c14-200">命令</span><span class="sxs-lookup"><span data-stu-id="c6c14-200">Command</span></span> | &nbsp;
:------------ | :-------------
**<span data-ttu-id="c6c14-201">takeHeapSnapshot()</span><span class="sxs-lookup"><span data-stu-id="c6c14-201">takeHeapSnapshot()</span></span>** | <span data-ttu-id="c6c14-202">捕获有关当前 JavaScript 堆及其分配的对象的详细信息。</span><span class="sxs-lookup"><span data-stu-id="c6c14-202">Captures details about the current JavaScript heap and its allocated objects.</span></span>

<span data-ttu-id="c6c14-203">DevTools[内存探查器](../memory.md#toolbar)必须运行才能获取堆快照。</span><span class="sxs-lookup"><span data-stu-id="c6c14-203">The  DevTools [memory profiler](../memory.md#toolbar) must be running in order to take heap snapshots.</span></span> <span data-ttu-id="c6c14-204">每个快照将在 "[**内存**](../memory.md)" 面板的 "[*快照摘要*](../memory.md#snapshot-summary)" 中显示为一个磁贴，以便进一步检查。</span><span class="sxs-lookup"><span data-stu-id="c6c14-204">Each snapshot will appear as a tile in the [*Snapshot summary*](../memory.md#snapshot-summary) of the [**Memory**](../memory.md) panel for further inspection.</span></span>

## <span data-ttu-id="c6c14-205">跟踪 callstacks</span><span class="sxs-lookup"><span data-stu-id="c6c14-205">Tracing callstacks</span></span>

<span data-ttu-id="c6c14-206">了解代码的调用位置、正在运行的代码，以及执行时间在分析 slowness 或意外行为时可能会很有用。</span><span class="sxs-lookup"><span data-stu-id="c6c14-206">Understanding where your code is being called from, what code is running, and how long that execution takes can be useful in analyzing slowness or unexpected behavior.</span></span> <span data-ttu-id="c6c14-207">堆栈跟踪显示你的代码为到达它所需的执行路径，从跟踪请求向上遍历路径。</span><span class="sxs-lookup"><span data-stu-id="c6c14-207">A stack trace shows you the execution path your code took to reach it, from the trace request upward through the path.</span></span> 

<span data-ttu-id="c6c14-208">命令</span><span class="sxs-lookup"><span data-stu-id="c6c14-208">Command</span></span> | &nbsp;
:------------ | :-------------
[**<span data-ttu-id="c6c14-209">trace （）</span><span class="sxs-lookup"><span data-stu-id="c6c14-209">trace()</span></span>**](https://developer.mozilla.org/docs/Web/API/Console/trace) | <span data-ttu-id="c6c14-210">输出当前脚本执行调用堆栈的跟踪。</span><span class="sxs-lookup"><span data-stu-id="c6c14-210">Outputs a trace of the current script execution callstack.</span></span>

<span data-ttu-id="c6c14-211">例如，在控制台中运行以下代码：</span><span class="sxs-lookup"><span data-stu-id="c6c14-211">For example, running the following code in the console:</span></span>

```javascript
function a(){
  c();
}
function b(){
  c();
}
function c(){
  console.trace()
}
function d(){
  b();
}

a();
d();
```

<span data-ttu-id="c6c14-212">.</span><span class="sxs-lookup"><span data-stu-id="c6c14-212">.</span></span> <span data-ttu-id="c6c14-213">.</span><span class="sxs-lookup"><span data-stu-id="c6c14-213">.</span></span> <span data-ttu-id="c6c14-214">.</span><span class="sxs-lookup"><span data-stu-id="c6c14-214">.</span></span> <span data-ttu-id="c6c14-215">将输出以下堆栈跟踪：</span><span class="sxs-lookup"><span data-stu-id="c6c14-215">will output the following stack traces:</span></span>
> <span data-ttu-id="c6c14-216">位于 c （eval 代码：8：3）（eval 代码：2：3）（eval 代码：14：1）处的 console、trace （）</span><span class="sxs-lookup"><span data-stu-id="c6c14-216">console.trace() at c (eval code:8:3) at a (eval code:2:3) at eval code (eval code:14:1)</span></span>
> 
> <span data-ttu-id="c6c14-217">在 c （eval 代码：8：3）处的 c （eval 代码：5：3）在 eval （eval 代码：11：3）的 eval 代码（eval 代码：15：1）处的 trace （）</span><span class="sxs-lookup"><span data-stu-id="c6c14-217">console.trace() at c (eval code:8:3) at b (eval code:5:3) at d (eval code:11:3) at eval code (eval code:15:1)</span></span>

## <span data-ttu-id="c6c14-218">组织日志输出</span><span class="sxs-lookup"><span data-stu-id="c6c14-218">Organizing log output</span></span>

<span data-ttu-id="c6c14-219">若只需清除以前的所有控制台输出，请使用*console。 clear （）* （或 `CTRL + L` ）。</span><span class="sxs-lookup"><span data-stu-id="c6c14-219">To simply clear all previous console output, use *console.clear()* (or `CTRL + L`).</span></span> <span data-ttu-id="c6c14-220">这不会清除您的控制台命令历史记录的 backstack （您仍可以用向上和向下箭头键遍历它）。</span><span class="sxs-lookup"><span data-stu-id="c6c14-220">This does not clear the backstack of your console command history (you can still traverse it with the up and down arrow keys).</span></span>

<span data-ttu-id="c6c14-221">命令</span><span class="sxs-lookup"><span data-stu-id="c6c14-221">Command</span></span> | &nbsp;
:------------ | :-------------
[**<span data-ttu-id="c6c14-222">clear （）</span><span class="sxs-lookup"><span data-stu-id="c6c14-222">clear()</span></span>**](https://developer.mozilla.org/docs/Web/API/Console/clear) | <span data-ttu-id="c6c14-223">清除以前的所有控制台输出。</span><span class="sxs-lookup"><span data-stu-id="c6c14-223">Clears all previous console output.</span></span>

<span data-ttu-id="c6c14-224">如果你的代码输出了大量的控制台消息，你可以使用以下命令直观地将它们组织到嵌套块中：</span><span class="sxs-lookup"><span data-stu-id="c6c14-224">If your code outputs a lot of console messages, you can visually organize them into nested blocks with the following commands:</span></span>

 <span data-ttu-id="c6c14-225">命令</span><span class="sxs-lookup"><span data-stu-id="c6c14-225">Command</span></span> | &nbsp;
:------------ | :-------------
[**<span data-ttu-id="c6c14-226">group （）</span><span class="sxs-lookup"><span data-stu-id="c6c14-226">group()</span></span>**](https://developer.mozilla.org/docs/Web/API/Console/group) | <span data-ttu-id="c6c14-227">使用指定的（可选）标签为控制台输出启动新的嵌套级别。</span><span class="sxs-lookup"><span data-stu-id="c6c14-227">Starts a new level of nesting for console output with the specified (optional) label.</span></span>
[**<span data-ttu-id="c6c14-228">groupCollapsed()</span><span class="sxs-lookup"><span data-stu-id="c6c14-228">groupCollapsed()</span></span>**](https://developer.mozilla.org/docs/Web/API/Console/groupCollapsed) | <span data-ttu-id="c6c14-229">使用指定的（可选）标签启动控制台输出的新嵌套层嵌套，但是分组控件在默认情况下处于折叠状态，并且必须展开（通过单击箭头控件）才能显示子输出。</span><span class="sxs-lookup"><span data-stu-id="c6c14-229">Starts a new level of nesting for console output with the specified (optional) label, however the grouping control is collapsed by default and must be expanded (by clicking on the arrow control) to display the child output.</span></span>
[**<span data-ttu-id="c6c14-230">groupEnd()</span><span class="sxs-lookup"><span data-stu-id="c6c14-230">groupEnd()</span></span>**](https://developer.mozilla.org/docs/Web/API/Console/groupEnd) | <span data-ttu-id="c6c14-231">结束指定标签的嵌套组。</span><span class="sxs-lookup"><span data-stu-id="c6c14-231">Ends the nesting group for the specified label.</span></span>

<span data-ttu-id="c6c14-232">例如，尝试在控制台中输入以下命令：</span><span class="sxs-lookup"><span data-stu-id="c6c14-232">For example, try entering the following commands in the console:</span></span>

```javascript
console.groupCollapsed('Group 1');
console.log('In Group 1');
console.groupCollapsed('Group 1.1');
console.log('In Group 1.1');
console.groupEnd('Group 1.1');
console.groupEnd('Group 1');
console.log('No longer in a group');
```

<span data-ttu-id="c6c14-233">.</span><span class="sxs-lookup"><span data-stu-id="c6c14-233">.</span></span> <span data-ttu-id="c6c14-234">.</span><span class="sxs-lookup"><span data-stu-id="c6c14-234">.</span></span> <span data-ttu-id="c6c14-235">.</span><span class="sxs-lookup"><span data-stu-id="c6c14-235">.</span></span> <span data-ttu-id="c6c14-236">然后展开*组 1*和*组 1.1*控件以查看日志注释的嵌套方式：</span><span class="sxs-lookup"><span data-stu-id="c6c14-236">and then expand the *Group 1* and *Group 1.1* controls to see how the log comments are nested:</span></span>

![对控制台中的邮件进行分组](../media/console_api_group.png)

<span data-ttu-id="c6c14-238">有时，使用表格形式（而不是简单列表）可视化 JavaScript 对象或数组更容易。</span><span class="sxs-lookup"><span data-stu-id="c6c14-238">Sometimes its easier to visualize a JavaScript object or array in tabular form, rather than a flat list.</span></span> <span data-ttu-id="c6c14-239">为此，你可以使用*console for table （）* 命令：</span><span class="sxs-lookup"><span data-stu-id="c6c14-239">For that, you can use the *console.table()* command:</span></span>

<span data-ttu-id="c6c14-240">命令</span><span class="sxs-lookup"><span data-stu-id="c6c14-240">Command</span></span> | &nbsp;
:------------ | :-------------
[**<span data-ttu-id="c6c14-241">table （）</span><span class="sxs-lookup"><span data-stu-id="c6c14-241">table()</span></span>**](https://developer.mozilla.org/docs/Web/API/Console/table) | <span data-ttu-id="c6c14-242">将提供的数组或对象以表格形式输出到控制台。</span><span class="sxs-lookup"><span data-stu-id="c6c14-242">Outputs the supplied array or object to the console in tabular form.</span></span>

<span data-ttu-id="c6c14-243">例如，以下对象数组：</span><span class="sxs-lookup"><span data-stu-id="c6c14-243">For example, the following object array:</span></span>

```javascript
var orders = [{'Size':'XL', 'Quantity':1},{'Size':'M', 'Quantity':3}, {'Size':'L', 'Quantity':2}];
console.table(orders);
```

<span data-ttu-id="c6c14-244">.</span><span class="sxs-lookup"><span data-stu-id="c6c14-244">.</span></span> <span data-ttu-id="c6c14-245">.</span><span class="sxs-lookup"><span data-stu-id="c6c14-245">.</span></span> <span data-ttu-id="c6c14-246">.</span><span class="sxs-lookup"><span data-stu-id="c6c14-246">.</span></span> <span data-ttu-id="c6c14-247">将在控制台中呈现为此表：</span><span class="sxs-lookup"><span data-stu-id="c6c14-247">will render as this table in the console:</span></span>

![在控制台中将对象数组显示为表](../media/console_api_table.png)