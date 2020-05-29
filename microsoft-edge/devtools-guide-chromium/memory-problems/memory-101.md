---
title: 内存术语
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 04/03/2020
ms.topic: article
ms.prod: microsoft-edge
keywords: microsoft edge、web 开发、f12 工具、devtools
ms.openlocfilehash: e3373cf1475ec0eeaabcebf1a7f49505c7a3c1bb
ms.sourcegitcommit: 50991a04c18283a8890ae33fcc3491c0476c7684
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/30/2020
ms.locfileid: "10611725"
---
<!-- Copyright Meggin Kearney 

   Licensed under the Apache License, Version 2.0 (the "License");
   you may not use this file except in compliance with the License.
   You may obtain a copy of the License at

       https://www.apache.org/licenses/LICENSE-2.0

   Unless required by applicable law or agreed to in writing, software
   distributed under the License is distributed on an "AS IS" BASIS,
   WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
   See the License for the specific language governing permissions and
   limitations under the License. -->





# <span data-ttu-id="91a5d-103">内存术语</span><span class="sxs-lookup"><span data-stu-id="91a5d-103">Memory Terminology</span></span>   



<span data-ttu-id="91a5d-104">本部分介绍内存分析中使用的常见术语，并适用于不同语言的各种内存分析工具。</span><span class="sxs-lookup"><span data-stu-id="91a5d-104">This section describes common terms used in memory analysis, and is applicable to a variety of memory profiling tools for different languages.</span></span>  

<span data-ttu-id="91a5d-105">此处所述的条款和概念指的是[内存面板][DevtoolsMemoryProblemsHeapSnapshots]。</span><span class="sxs-lookup"><span data-stu-id="91a5d-105">The terms and notions described here refer to the [Memory panel][DevtoolsMemoryProblemsHeapSnapshots].</span></span>  <span data-ttu-id="91a5d-106">如果您曾经使用过 Java、.NET 或其他一些内存探查器，则这可能是复习。</span><span class="sxs-lookup"><span data-stu-id="91a5d-106">If you have ever worked with either the Java, .NET, or some other memory profiler, then this may be a refresher.</span></span>  

## <span data-ttu-id="91a5d-107">对象大小</span><span class="sxs-lookup"><span data-stu-id="91a5d-107">Object sizes</span></span>  

<span data-ttu-id="91a5d-108">将内存视为具有基元类型的图形 \ （如数字和字符串 \）和对象 \ （关联数组 \）。</span><span class="sxs-lookup"><span data-stu-id="91a5d-108">Think of memory as a graph with primitive types \(like numbers and strings\) and objects \(associative arrays\).</span></span>  <span data-ttu-id="91a5d-109">它可能以图形形式表示为具有许多互连点的图形，如下所示：</span><span class="sxs-lookup"><span data-stu-id="91a5d-109">It might visually be represented as a graph with a number of interconnected points as follows:</span></span>  

> ##### <span data-ttu-id="91a5d-110">图 1</span><span class="sxs-lookup"><span data-stu-id="91a5d-110">Figure 1</span></span>  
> <span data-ttu-id="91a5d-111">内存的可视化表示形式</span><span class="sxs-lookup"><span data-stu-id="91a5d-111">Visual representation of memory</span></span>  
>![内存的可视化表示形式][ImageThinkGraph]  

<span data-ttu-id="91a5d-113">对象可以通过两种方式保留内存：</span><span class="sxs-lookup"><span data-stu-id="91a5d-113">An object may hold memory in two ways:</span></span>  

*   <span data-ttu-id="91a5d-114">直接由对象。</span><span class="sxs-lookup"><span data-stu-id="91a5d-114">Directly by the object.</span></span>  
*   <span data-ttu-id="91a5d-115">通过保留对其他对象的引用来进行隐式处理，从而阻止垃圾回收器自动释放这些对象 \ （**GC**的短 \）。</span><span class="sxs-lookup"><span data-stu-id="91a5d-115">Implicitly by holding references to other objects, and therefore preventing those objects from being automatically disposed by a garbage collector \(**GC** for short\).</span></span>  

<span data-ttu-id="91a5d-116">在 DevTools 中使用[内存面板][DevtoolsMemoryProblemsHeapSnapshots]\ （用于调查在 "内存" 下找到的内存问题的工具）时，您可能会发现自己查看的信息有几个不同列。</span><span class="sxs-lookup"><span data-stu-id="91a5d-116">When working with the [Memory panel][DevtoolsMemoryProblemsHeapSnapshots] in DevTools \(a tool for investigating memory issues found under "Memory"\), you may find yourself looking at a few different columns of information.</span></span>  <span data-ttu-id="91a5d-117">有两个是**浅大小**和**保留大小**，但它们代表什么？</span><span class="sxs-lookup"><span data-stu-id="91a5d-117">Two that stand out are **Shallow Size** and **Retained Size**, but what do these represent?</span></span>  

> ##### <span data-ttu-id="91a5d-118">图 2</span><span class="sxs-lookup"><span data-stu-id="91a5d-118">Figure 2</span></span>  
> <span data-ttu-id="91a5d-119">浅和保留大小</span><span class="sxs-lookup"><span data-stu-id="91a5d-119">Shallow and Retained Size</span></span>  
>![浅和保留大小][ImageShallowRetained]  

### <span data-ttu-id="91a5d-121">浅大小</span><span class="sxs-lookup"><span data-stu-id="91a5d-121">Shallow size</span></span>  

<span data-ttu-id="91a5d-122">这是对象占用的内存大小。</span><span class="sxs-lookup"><span data-stu-id="91a5d-122">This is the size of memory that is held by the object.</span></span>  

<span data-ttu-id="91a5d-123">典型的 JavaScript 对象为其描述保留了一些内存，并用于存储即时值。</span><span class="sxs-lookup"><span data-stu-id="91a5d-123">Typical JavaScript objects have some memory reserved for their description and for storing immediate values.</span></span>  <span data-ttu-id="91a5d-124">通常，只有数组和字符串能够具有显著的浅规格。</span><span class="sxs-lookup"><span data-stu-id="91a5d-124">Usually, only arrays and strings are able to have a significant shallow size.</span></span>  <span data-ttu-id="91a5d-125">但是，字符串和外部数组在呈现器内存中通常具有主存储，仅在 JavaScript 堆上公开一个小型包装对象。</span><span class="sxs-lookup"><span data-stu-id="91a5d-125">However, strings and external arrays often have their main storage in renderer memory, exposing only a small wrapper object on the JavaScript heap.</span></span>  

<span data-ttu-id="91a5d-126">呈现器内存是已检查页面呈现的进程的所有内存：页面上启动的页面 + JS 堆内存的本机内存 + JS 堆内存。</span><span class="sxs-lookup"><span data-stu-id="91a5d-126">Renderer memory is all memory of the process where an inspected page is rendered: native memory + JS heap memory of the page + JS heap memory of all dedicated workers started by the page.</span></span>  <span data-ttu-id="91a5d-127">尽管如此，即使是小对象也可以通过自动垃圾回收进程来处理其他对象，从而间接容纳大量内存。</span><span class="sxs-lookup"><span data-stu-id="91a5d-127">Nevertheless, even a small object is able to hold a large amount of memory indirectly, by preventing other objects from being disposed of by the automatic garbage collection process.</span></span>  

### <span data-ttu-id="91a5d-128">保留大小</span><span class="sxs-lookup"><span data-stu-id="91a5d-128">Retained size</span></span>  

<span data-ttu-id="91a5d-129">这是在删除对象后释放的内存大小，以及从**垃圾回收器根**\ （GC 根 \）中无法访问的依赖对象。</span><span class="sxs-lookup"><span data-stu-id="91a5d-129">This is the size of memory that is freed once the object is deleted along with the dependent objects that were made unreachable from **Garbage Collector roots** \(GC roots\) .</span></span>  

<span data-ttu-id="91a5d-130">**垃圾回收器根**\ （GC 根 \）是指在从本机代码到 V8 之外的 JavaScript 对象进行引用时创建的**句柄**\ （本地或全局 \）。</span><span class="sxs-lookup"><span data-stu-id="91a5d-130">**Garbage Collector roots** \(GC roots\) are made up of **handles** that are created \(either local or global\) when making a reference from native code to a JavaScript object outside of V8.</span></span>  <span data-ttu-id="91a5d-131">所有此类句柄都可以在 " **gc 根**" 下的堆快照中找到  >  ，它**处理作用域**和**GC 根**  >  **全局句柄**。</span><span class="sxs-lookup"><span data-stu-id="91a5d-131">All such handles may be found within a heap snapshot under **GC roots** > **Handle scope** and **GC roots** > **Global handles**.</span></span>  <span data-ttu-id="91a5d-132">在此文档中描述句柄，而无需深入了解浏览器实现的详细信息可能会令人困惑。</span><span class="sxs-lookup"><span data-stu-id="91a5d-132">Describing the handles in this documentation without diving into details of the browser implementation may be confusing.</span></span>  <span data-ttu-id="91a5d-133">垃圾回收器（GC）根目录和句柄都不是您需要担心的问题。</span><span class="sxs-lookup"><span data-stu-id="91a5d-133">Both Garbage Collector (GC) roots and the handles are not something you need to worry about.</span></span>  

<span data-ttu-id="91a5d-134">有许多内部 GC 根，其中大多数不会对用户感兴趣。</span><span class="sxs-lookup"><span data-stu-id="91a5d-134">There are lots of internal GC roots, most of which are not interesting for the users.</span></span>  <span data-ttu-id="91a5d-135">从应用程序角度看，有以下类型的根。</span><span class="sxs-lookup"><span data-stu-id="91a5d-135">From the applications standpoint there are following kinds of roots.</span></span>  

*   <span data-ttu-id="91a5d-136">Window 全局对象 \ （在每个 iframe 中 \）。</span><span class="sxs-lookup"><span data-stu-id="91a5d-136">Window global object \(in each iframe\).</span></span>  <span data-ttu-id="91a5d-137">堆快照中有一个距离字段，这是窗口的最短保留路径上的属性引用数。</span><span class="sxs-lookup"><span data-stu-id="91a5d-137">There is a distance field in the heap snapshots which is the number of property references on the shortest retaining path from the window.</span></span>  
*   <span data-ttu-id="91a5d-138">文档 DOM 树，其中包含通过遍历文档可访问的所有本地 DOM 节点。</span><span class="sxs-lookup"><span data-stu-id="91a5d-138">Document DOM tree consisting of all native DOM nodes reachable by traversing the document.</span></span>  <span data-ttu-id="91a5d-139">并非所有节点都可以具有 JS 包装，但如果节点具有包装器，则在文档处于活动状态时，它处于活动状态。</span><span class="sxs-lookup"><span data-stu-id="91a5d-139">Not all of the nodes may have JS wrappers but if a node has a wrapper, it is alive while the document is alive.</span></span>  
*   <span data-ttu-id="91a5d-140">有时，**源**面板和**控制台**中的调试器上下文可能会保留对象，例如，在控制台评估后 \）。</span><span class="sxs-lookup"><span data-stu-id="91a5d-140">Sometimes objects may be retained by the debugger context in the **Sources** panel and the **Console** \(for example after Console evaluation\).</span></span>  <span data-ttu-id="91a5d-141">在 "**源**" 面板中，使用已清除的**控制台**面板和调试器中没有活动断点创建堆快照。</span><span class="sxs-lookup"><span data-stu-id="91a5d-141">Create heap snapshots with a cleared **Console** panel and no active breakpoints in the debugger in the **Sources** panel.</span></span>

>[!TIP]
> <span data-ttu-id="91a5d-142">在 " **Console** `clear()` [内存" 面板][DevtoolsMemoryProblemsHeapSnapshots]中获取堆快照之前，通过运行和停用 "**源**" 面板中的断点来清除控制台面板。</span><span class="sxs-lookup"><span data-stu-id="91a5d-142">Clear the **Console** panel by running `clear()` and deactivate breakpoints in the **Sources** panel before taking a heap snapshot in the [Memory panel][DevtoolsMemoryProblemsHeapSnapshots].</span></span>

<span data-ttu-id="91a5d-143">内存图从根开始，它可能是 `window` 浏览器的对象或 `Global` 节点 .js 模块的对象。</span><span class="sxs-lookup"><span data-stu-id="91a5d-143">The memory graph starts with a root, which may be the `window` object of the browser or the `Global` object of a Node.js module.</span></span>  <span data-ttu-id="91a5d-144">你不控制此根对象的垃圾回收方式（GCd）。</span><span class="sxs-lookup"><span data-stu-id="91a5d-144">You do not control how this root object is garbage collected (GCd).</span></span>  

> ##### <span data-ttu-id="91a5d-145">图 3</span><span class="sxs-lookup"><span data-stu-id="91a5d-145">Figure 3</span></span>  
> <span data-ttu-id="91a5d-146">您无法控制如何对根对象进行垃圾回收 \ （GCd \）。</span><span class="sxs-lookup"><span data-stu-id="91a5d-146">You are not able to control how the root object is garbage collected \(GCd\).</span></span>  
>![你无法控制如何对根对象进行垃圾回收（GCd）。][ImageDontControl]  

<span data-ttu-id="91a5d-148">从根中无法访问的任何内容都会获取垃圾回收 \ （GCd \）。</span><span class="sxs-lookup"><span data-stu-id="91a5d-148">Whatever is not reachable from the root gets garbage collected \(GCd\).</span></span>  

> [!NOTE]
> <span data-ttu-id="91a5d-149">"[浅层大小](#shallow-size)" 和 "[保留大小](#retained-size)" 列均表示数据，以字节为单位。</span><span class="sxs-lookup"><span data-stu-id="91a5d-149">Both the [Shallow size](#shallow-size) and [Retained size](#retained-size) columns represent data in bytes.</span></span>  

## <span data-ttu-id="91a5d-150">对象保留树</span><span class="sxs-lookup"><span data-stu-id="91a5d-150">Objects retaining tree</span></span>  

<span data-ttu-id="91a5d-151">堆是互连对象的网络。</span><span class="sxs-lookup"><span data-stu-id="91a5d-151">The heap is a network of interconnected objects.</span></span>  <span data-ttu-id="91a5d-152">在数学世界中，此结构称为**图形**或内存图。</span><span class="sxs-lookup"><span data-stu-id="91a5d-152">In the mathematical world, this structure is called a **graph** or memory graph.</span></span>  <span data-ttu-id="91a5d-153">图形由通过**边缘**连接的节点构造，这两个**节点**都具有标签。</span><span class="sxs-lookup"><span data-stu-id="91a5d-153">A graph is constructed from **nodes** connected by means of **edges**, both of which are given labels.</span></span>  

*   <span data-ttu-id="91a5d-154">**节点**\ （或**对象**\）使用用于生成它们的**构造**函数的名称进行标记。</span><span class="sxs-lookup"><span data-stu-id="91a5d-154">**Nodes**  \(or **objects**\) are labelled using the name of the **constructor** function that was used to build them.</span></span>  
*   <span data-ttu-id="91a5d-155">使用**属性**名称对**边缘**进行标记。</span><span class="sxs-lookup"><span data-stu-id="91a5d-155">**Edges**  are labelled using the names of **properties**.</span></span>  

<span data-ttu-id="91a5d-156">了解[如何使用堆探查器录制配置文件][DevtoolsMemoryProblemsHeapSnapshots]。</span><span class="sxs-lookup"><span data-stu-id="91a5d-156">Learn [how to record a profile using the Heap Profiler][DevtoolsMemoryProblemsHeapSnapshots].</span></span>  <span data-ttu-id="91a5d-157">[图 4](#figure-4)中 "[内存" 面板][DevtoolsMemoryProblemsHeapSnapshots]的堆快照记录中可能会显示的一些引人注目的内容包括距离：垃圾回收器 \ （GC \）根的距离。</span><span class="sxs-lookup"><span data-stu-id="91a5d-157">Some of the eye-catching things that you may see in the Heap Snapshot recording in the [Memory panel][DevtoolsMemoryProblemsHeapSnapshots] in [Figure 4](#figure-4) include distance: the distance from the Garbage Collector \(GC\) root.</span></span>  <span data-ttu-id="91a5d-158">如果几乎所有相同类型的对象都在同一距离上，并且有几个更远的距离，这就是值得研究的事情。</span><span class="sxs-lookup"><span data-stu-id="91a5d-158">If almost all the objects of the same type are at the same distance, and a few are at a bigger distance, that is something worth investigating.</span></span>  

> ##### <span data-ttu-id="91a5d-159">图 4</span><span class="sxs-lookup"><span data-stu-id="91a5d-159">Figure 4</span></span>  
> <span data-ttu-id="91a5d-160">与根的距离</span><span class="sxs-lookup"><span data-stu-id="91a5d-160">Distance from root</span></span>  
>![与根的距离][ImageRoot]  

## <span data-ttu-id="91a5d-162">Dominators</span><span class="sxs-lookup"><span data-stu-id="91a5d-162">Dominators</span></span>  

<span data-ttu-id="91a5d-163">Dominator 对象由树形结构组成，因为每个对象都有一个 Dominator。</span><span class="sxs-lookup"><span data-stu-id="91a5d-163">Dominator objects are comprised of a tree structure because each object has exactly one dominator.</span></span>  <span data-ttu-id="91a5d-164">对象的 dominator 可能缺少直接引用它 dominates 的对象;也就是说，dominator 的树不是图形的生成树。</span><span class="sxs-lookup"><span data-stu-id="91a5d-164">A dominator of an object may lack direct references to an object it dominates; that is, the tree of the dominator is not a spanning tree of the graph.</span></span>  

<span data-ttu-id="91a5d-165">[图 5](#figure-5)：</span><span class="sxs-lookup"><span data-stu-id="91a5d-165">In [Figure 5](#figure-5):</span></span>  

*   <span data-ttu-id="91a5d-166">节点 1 dominates 节点2</span><span class="sxs-lookup"><span data-stu-id="91a5d-166">Node 1 dominates node 2</span></span>  
*   <span data-ttu-id="91a5d-167">节点 2 dominates 节点3、4和6</span><span class="sxs-lookup"><span data-stu-id="91a5d-167">Node 2 dominates nodes 3, 4 and 6</span></span>  
*   <span data-ttu-id="91a5d-168">节点 3 dominates 节点5</span><span class="sxs-lookup"><span data-stu-id="91a5d-168">Node 3 dominates node 5</span></span>  
*   <span data-ttu-id="91a5d-169">节点 5 dominates 节点8</span><span class="sxs-lookup"><span data-stu-id="91a5d-169">Node 5 dominates node 8</span></span>  
*   <span data-ttu-id="91a5d-170">节点 6 dominates 节点7</span><span class="sxs-lookup"><span data-stu-id="91a5d-170">Node 6 dominates node 7</span></span>  

> ##### <span data-ttu-id="91a5d-171">图 5</span><span class="sxs-lookup"><span data-stu-id="91a5d-171">Figure 5</span></span>  
> <span data-ttu-id="91a5d-172">Dominator 树结构</span><span class="sxs-lookup"><span data-stu-id="91a5d-172">Dominator tree structure</span></span>  
>![Dominator 树结构][ImageDominatorsSpanning]  

<span data-ttu-id="91a5d-174">在[图 6](#figure-6)中，node `#3` 是 dominator `#10` ，但 `#7` 也存在于从垃圾回收器 \ （GC \）到的每个简单路径中 `#10` 。</span><span class="sxs-lookup"><span data-stu-id="91a5d-174">In [Figure 6](#figure-6), node `#3` is the dominator of `#10`, but `#7` also exists in every simple path from Garbage Collector \(GC\) to `#10`.</span></span>  <span data-ttu-id="91a5d-175">因此，对象 B 是对象 A 的 dominator，即 B 存在于从根到对象 A 的每个简单路径中的 a。</span><span class="sxs-lookup"><span data-stu-id="91a5d-175">Therefore, an object B is a dominator of an object A if B exists in every simple path from the root to the object A.</span></span>  

> ##### <span data-ttu-id="91a5d-176">图 6</span><span class="sxs-lookup"><span data-stu-id="91a5d-176">Figure 6</span></span>  
> <span data-ttu-id="91a5d-177">动画 dominator 图</span><span class="sxs-lookup"><span data-stu-id="91a5d-177">Animated dominator illustration</span></span>  
>![动画 dominator 图][ImageDominators]  

## <span data-ttu-id="91a5d-179">V8 详细信息</span><span class="sxs-lookup"><span data-stu-id="91a5d-179">V8 specifics</span></span>  

<span data-ttu-id="91a5d-180">分析内存时，了解堆快照的外观很有帮助。</span><span class="sxs-lookup"><span data-stu-id="91a5d-180">When profiling memory, it is helpful to understand why heap snapshots look a certain way.</span></span>  <span data-ttu-id="91a5d-181">本部分介绍了一些与**V8 JavaScript 虚拟机**\ （V8 VM 或 vm \）特别对应的内存相关主题。</span><span class="sxs-lookup"><span data-stu-id="91a5d-181">This section describes some memory-related topics specifically corresponding to the **V8 JavaScript virtual machine** \(V8 VM or VM\).</span></span>  

### <span data-ttu-id="91a5d-182">JavaScript 对象表示形式</span><span class="sxs-lookup"><span data-stu-id="91a5d-182">JavaScript object representation</span></span>  

<span data-ttu-id="91a5d-183">有三种基元类型：</span><span class="sxs-lookup"><span data-stu-id="91a5d-183">There are three primitive types:</span></span>  

*   <span data-ttu-id="91a5d-184">数字 \ （例如 `3.14159...` \）</span><span class="sxs-lookup"><span data-stu-id="91a5d-184">Numbers \(for example `3.14159...`\)</span></span>  
*   <span data-ttu-id="91a5d-185">布尔值 \ （ `true` 或 `false` \）</span><span class="sxs-lookup"><span data-stu-id="91a5d-185">Booleans \(`true` or `false`\)</span></span>  
*   <span data-ttu-id="91a5d-186">字符串 \ （例如 `"Werner Heisenberg"` \）</span><span class="sxs-lookup"><span data-stu-id="91a5d-186">Strings \(for example `"Werner Heisenberg"`\)</span></span>  

<span data-ttu-id="91a5d-187">基元不能引用其他值，并且始终 leafs 或终止节点。</span><span class="sxs-lookup"><span data-stu-id="91a5d-187">Primitives are not able to reference other values and are always leafs or terminating nodes.</span></span>  

<span data-ttu-id="91a5d-188">**数字**可以存储为：</span><span class="sxs-lookup"><span data-stu-id="91a5d-188">**Numbers** are able to be stored as either:</span></span>  

*   <span data-ttu-id="91a5d-189">名为**小整数**\ （**SMI**s）的直接31位整数值</span><span class="sxs-lookup"><span data-stu-id="91a5d-189">an immediate 31-bit integer values called **small integers** \(**SMI**s\), or</span></span>  
*   <span data-ttu-id="91a5d-190">堆对象，称为**堆编号**。</span><span class="sxs-lookup"><span data-stu-id="91a5d-190">heap objects, referred to as **heap numbers**.</span></span> <span data-ttu-id="91a5d-191">堆编号用于存储不适合 SMI 形式的值（如**双精度或双精度**型），或者需要对值进行**装箱**时（如在其上设置属性）。</span><span class="sxs-lookup"><span data-stu-id="91a5d-191">Heap numbers are used for storing values that do not fit into the SMI form, such as **doubles**, or when a value needs to be **boxed**, such as setting properties on it.</span></span>  

<span data-ttu-id="91a5d-192">**字符串**能够存储在以下其中一种：</span><span class="sxs-lookup"><span data-stu-id="91a5d-192">**Strings** are able to be stored in either:</span></span>  

*   <span data-ttu-id="91a5d-193">**VM 堆**或</span><span class="sxs-lookup"><span data-stu-id="91a5d-193">the **VM heap**, or</span></span>
*   <span data-ttu-id="91a5d-194">在呈现器的**内存**中外部。</span><span class="sxs-lookup"><span data-stu-id="91a5d-194">externally in the **memory of the renderer**.</span></span>  <span data-ttu-id="91a5d-195">创建一个**包装对象**，并使用它来访问外部存储，例如，存储从 Web 接收的脚本源和其他内容，而不是将其复制到 VM 堆。</span><span class="sxs-lookup"><span data-stu-id="91a5d-195">A **wrapper object** is created and used for accessing external storage where, for example, script sources and other content that is received from the Web is stored, rather than copied onto the VM heap.</span></span>

<span data-ttu-id="91a5d-196">新 JavaScript 对象的内存是从专用的 JavaScript 堆 \ （或**VM 堆**\）分配的。</span><span class="sxs-lookup"><span data-stu-id="91a5d-196">Memory for new JavaScript objects is allocated from a dedicated JavaScript heap \(or **VM heap**\).</span></span>  <span data-ttu-id="91a5d-197">这些对象由 V8 中的垃圾回收器管理，因此只要存在至少一个强引用，就保持活动。</span><span class="sxs-lookup"><span data-stu-id="91a5d-197">These objects are managed by the garbage collector in V8 and therefore, stay alive as long as there is at least one strong reference to them.</span></span>  

<span data-ttu-id="91a5d-198">任何不在 JavaScript 堆中的内容称为**本机对象**。</span><span class="sxs-lookup"><span data-stu-id="91a5d-198">Anything not in the JavaScript heap is called a **native object**.</span></span>  <span data-ttu-id="91a5d-199">与堆对象相比，本机对象不会在其整个生存期内由 V8 垃圾回收器管理，并且只能通过 javascript 包装对象从 JavaScript 中访问。</span><span class="sxs-lookup"><span data-stu-id="91a5d-199">Native objects, in contrast to heap objects, are not managed by the V8 garbage collector throughout their lifetime, and may only be accessed from JavaScript using the JavaScript wrapper object.</span></span>  

<span data-ttu-id="91a5d-200">**缺点字符串**是包含存储和联接的字符串对，并且是连接的结果的对象。</span><span class="sxs-lookup"><span data-stu-id="91a5d-200">**Cons string** is an object that consists of pairs of strings stored and then joined, and is a result of concatenation.</span></span>  <span data-ttu-id="91a5d-201">仅在需要时，才会出现操作**字符串**内容的联接。</span><span class="sxs-lookup"><span data-stu-id="91a5d-201">The joining of the **cons string** contents occurs only as needed.</span></span> <span data-ttu-id="91a5d-202">当需要构造联接的字符串的子字符串时，就会出现一个示例。</span><span class="sxs-lookup"><span data-stu-id="91a5d-202">An example would be when a substring of a joined string needs to be constructed.</span></span>

<span data-ttu-id="91a5d-203">例如，如果你连接， `a` `b` 则会收到一个 `(a, b)` 表示连接结果的字符串。</span><span class="sxs-lookup"><span data-stu-id="91a5d-203">For example, if you concatenate `a` and `b`, you get a string `(a, b)` which represents the result of concatenation.</span></span>  <span data-ttu-id="91a5d-204">如果稍后 `d` 与该结果连接，将获得另一个**缺点字符串**： `((a, b, d)` 。</span><span class="sxs-lookup"><span data-stu-id="91a5d-204">If you later concatenated `d` with that result, you get another **cons string**: `((a, b, d)`.</span></span>  

<span data-ttu-id="91a5d-205">**Array**是带有数字键的对象。</span><span class="sxs-lookup"><span data-stu-id="91a5d-205">**Array** is an object with numeric keys.</span></span> <span data-ttu-id="91a5d-206">**数组**在 V8 VM 中广泛用于存储大量数据。</span><span class="sxs-lookup"><span data-stu-id="91a5d-206">**Arrays** are used extensively in the V8 VM for storing large amounts of data.</span></span> <span data-ttu-id="91a5d-207">键/值对的集（如字典）由**数组**进行备份。</span><span class="sxs-lookup"><span data-stu-id="91a5d-207">Sets of key-value pairs, like dictionaries, are backed up by **arrays**.</span></span>  

<span data-ttu-id="91a5d-208">典型的 JavaScript 对象被存储为两种**数组**类型中的一种：</span><span class="sxs-lookup"><span data-stu-id="91a5d-208">A typical JavaScript object is stored as only one of two **array** types:</span></span>  

*   <span data-ttu-id="91a5d-209">命名属性和</span><span class="sxs-lookup"><span data-stu-id="91a5d-209">named properties, and</span></span>  
*   <span data-ttu-id="91a5d-210">数字元素</span><span class="sxs-lookup"><span data-stu-id="91a5d-210">numeric elements</span></span>  

<span data-ttu-id="91a5d-211">当存在少量属性时，属性在内部存储在 JavaScript 对象中。</span><span class="sxs-lookup"><span data-stu-id="91a5d-211">When there are a small number of properties, the properties are stored internally in the JavaScript object.</span></span>  

<span data-ttu-id="91a5d-212">**Map**是描述对象类型和布局的对象。</span><span class="sxs-lookup"><span data-stu-id="91a5d-212">**Map** is an object that describes both the kind of object it is and the layout.</span></span> <span data-ttu-id="91a5d-213">例如，映射用于描述用于[快速属性访问][V8FastProperties]的隐式对象层次结构。</span><span class="sxs-lookup"><span data-stu-id="91a5d-213">For example, maps are used to describe implicit object hierarchies for [fast property access][V8FastProperties].</span></span>  


### <span data-ttu-id="91a5d-214">对象组</span><span class="sxs-lookup"><span data-stu-id="91a5d-214">Object groups</span></span>  

<span data-ttu-id="91a5d-215">每个**本机对象**组都由相互保持相互引用的对象组成。</span><span class="sxs-lookup"><span data-stu-id="91a5d-215">Each **native objects** group is made up of objects that hold mutual references to each other.</span></span>  <span data-ttu-id="91a5d-216">例如，请考虑一个 DOM 子树，其中每个节点都有指向相对父级的链接和指向下一个子元素和下一个同级元素的链接，从而形成连接的图表。</span><span class="sxs-lookup"><span data-stu-id="91a5d-216">Consider, for example, a DOM subtree where every node has a link to the relative parent and links to the next child and next sibling, thus forming a connected graph.</span></span>  <span data-ttu-id="91a5d-217">请注意，在 JavaScript 堆中不表示本机对象，这就是本机对象大小为零的原因。</span><span class="sxs-lookup"><span data-stu-id="91a5d-217">Note that native objects are not represented in the JavaScript heap  —  that is why native objects have zero size.</span></span> <span data-ttu-id="91a5d-218">而是创建包装对象。</span><span class="sxs-lookup"><span data-stu-id="91a5d-218">Instead, wrapper objects are created.</span></span>  

<span data-ttu-id="91a5d-219">每个包装对象都包含对相应本机对象的引用，用于将命令重定向到该对象。</span><span class="sxs-lookup"><span data-stu-id="91a5d-219">Each wrapper object holds a reference to the corresponding native object, for redirecting commands to it.</span></span>  <span data-ttu-id="91a5d-220">反过来，对象组保留包装对象。</span><span class="sxs-lookup"><span data-stu-id="91a5d-220">In turn, an object group holds wrapper objects.</span></span>  <span data-ttu-id="91a5d-221">但是，这不会创建 uncollectable 循环，因为垃圾回收器 \ （GC \）非常智能，足以释放不再引用包装的对象组。</span><span class="sxs-lookup"><span data-stu-id="91a5d-221">However, this does not create an uncollectable cycle, as Garbage Collector \(GC\) is smart enough to release object groups whose wrappers are no longer referenced.</span></span> <span data-ttu-id="91a5d-222">但忘记发布单个包装器会保留整个组和关联的包装。</span><span class="sxs-lookup"><span data-stu-id="91a5d-222">But forgetting to release a single wrapper holds the whole group and associated wrappers.</span></span>  

<!--## Feedback   -->  



<!-- image links -->  

[ImageThinkGraph]: /microsoft-edge/devtools-guide-chromium/media/memory-problems-thinkgraph.msft.png "图1：内存的可视化表示形式"  
[ImageShallowRetained]: /microsoft-edge/devtools-guide-chromium/media/memory-problems-shallow-retained.msft.png "图2：浅表和保留大小"  
[ImageDontControl]: /microsoft-edge/devtools-guide-chromium/media/memory-problems-dontcontrol.msft.png "图3：无法控制根对象的垃圾回收方式（GCd）。"  
[ImageRoot]: /microsoft-edge/devtools-guide-chromium/media/memory-problems-root.msft.png "图4：从根开始的距离"  
[ImageDominatorsSpanning]: /microsoft-edge/devtools-guide-chromium/media/memory-problems-dominatorsspanning.msft.png "图5： Dominator 树形结构"  
[ImageDominators]: /microsoft-edge/devtools-guide-chromium/media/memory-problems-dominators.msft.gif "图6：动画 dominator 插图"  

<!-- links -->  

[DevtoolsMemoryProblemsHeapSnapshots]: /microsoft-edge/devtools-guide-chromium/media/memory-problems/heap-snapshots "/microsoft-edge/devtools-guide-chromium/media/memory-problems"  

[V8FastProperties]: https://v8.dev/blog/fast-properties "V8 | 中的快速属性V8"  

> [!NOTE]
> <span data-ttu-id="91a5d-231">此页面的某些部分是基于[由 Google][GoogleSitePolicies]创建和共享的工作的修改，并根据 "[创造性 Commons 归属4.0 国际许可证][CCA4IL]" 中所述的条款使用。</span><span class="sxs-lookup"><span data-stu-id="91a5d-231">Portions of this page are modifications based on work created and [shared by Google][GoogleSitePolicies] and used according to terms described in the [Creative Commons Attribution 4.0 International License][CCA4IL].</span></span>  
> <span data-ttu-id="91a5d-232">原始页面位于[此处](https://developers.google.com/web/tools/chrome-devtools/memory-problems/memory-101)，由[Meggin Kearney][MegginKearney] \ （技术作者 \）创作。</span><span class="sxs-lookup"><span data-stu-id="91a5d-232">The original page is found [here](https://developers.google.com/web/tools/chrome-devtools/memory-problems/memory-101) and is authored by [Meggin Kearney][MegginKearney] \(Technical Writer\).</span></span>  

[![创造性 Commons 许可证][CCby4Image]][CCA4IL]  
<span data-ttu-id="91a5d-234">此作品通过 [Creative Commons Attribution 4.0 国际许可证][CCA4IL]获得许可。</span><span class="sxs-lookup"><span data-stu-id="91a5d-234">This work is licensed under a [Creative Commons Attribution 4.0 International License][CCA4IL].</span></span>  

[CCA4IL]: https://creativecommons.org/licenses/by/4.0  
[CCby4Image]: https://i.creativecommons.org/l/by/4.0/88x31.png  
[GoogleSitePolicies]: https://developers.google.com/terms/site-policies  
[KayceBasques]: https://developers.google.com/web/resources/contributors/kaycebasques  
[MegginKearney]: https://developers.google.com/web/resources/contributors/megginkearney