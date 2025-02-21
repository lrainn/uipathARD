﻿> 前言：【【非原创】】UiPath Advanced RPA Developer Certification Training的课程资料机翻版。
课程链接：[Link](https://academy.uipath.com/learningpath/debugging-in-studio)

@[toc]

# 1 关于本课程
欢迎！

在本课程中，我们将介绍让自动​​化生产做好准备的最重要方面之一：**如何使用调试功能解决工作流程中的错误。**

**您将在本课程中学到什么**
在本课程结束时，您应该能够：
- 解释所有调试操作的作用。
- 解释所有调试面板指示的内容。
- 使用所有 UiPath Studio 调试功能让您的项目按预期运行。

# 2 调试功能概述 Debugging Features Overview
## 2.1 什么是调试

调试是检测和解决项目中可能导致项目异常行为或崩溃的错误的过程。通常建议在自动化项目的**设计阶段**、**活动**、**文件**和**项目**级别执行调试。让我们在下一节中学习调试操作和面板。

**调试操作和面板**
让我们详细了解调试操作和面板。

### 2.1.1 调试操作
花一些时间熟悉功能区中可用的所有调试操作。

![在这里插入图片描述](https://img-blog.csdnimg.cn/96fe8da037ae4a6ca296d3f9fd3c4ecd.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAcXFfMzgzMTYxNDg=,size_20,color_FFFFFF,t_70,g_se,x_16)
- **调试文件 Debug File**
调试文件允许我们调试当前的工作流文件。 Play 按钮下的下拉菜单有 RunFile 运行当前文件、Debug 在调试模式下运行整个项目和 Run 在运行模式下执行整个项目等选项。单击调试文件按钮将启动项目的调试。在调试过程中，单击 Break 按钮暂停。按继续将继续在调试模式下运行工作流。
- **Stop (F12)**
按停止按钮将退出调试模式并返回设计模式。
- **Step Into (F11)**
 使用 Step Into 一次调试一个活动。触发此操作时，调试器会打开并突出显示活动，然后再执行。当 Step Into 与 Invoke Workflow File 活动一起使用时，工作流将在只读模式下的新选项卡中打开，并且每个活动都被一个一个地执行。
 - **Step Over (F10)**
 与 Step Into 操作不同，Step Over 不会打开当前容器。使用时，该操作会调试下一个活动，突出显示容器（例如流程图、序列或调用工作流文件活动）而无需打开它们。此操作可用于跳过不太可能在执行期间触发任何问题的大型容器的分析。它执行容器内的所有内容，然后暂停。==使用 Step Over 将执行容器内的所有内容，并且仅在退出容器后才会暂停，停止在容器层==。
 	
 - **Step Out (Shift + F11)** 
顾名思义，这个动作是用于在当前**容器层级**跳出和暂停执行。 Step Out 在暂停调试之前完成当前容器中活动的执行。此选项适用于嵌套序列。==完成当前容器，停止在容器上一级容器==。
- **Retry**
 重新执行之前的活动，如果再次遇到则抛出异常。引发异常的活动突出显示，错误详细信息显示在本地和调用堆栈面板中。
 - **Ignore** 
Ignore 操作可用于忽略遇到的异常并从下一个活动继续执行以调试工作流的其余部分。
 - **Restart**
 抛出异常并暂停调试过程后可以重新启动。该操作用于从项目的第一个活动重新启动调试过程。使用“从此活动中运行”操作后单击“重新启动”选项时，将从先前指示的活动重新启动调试。
- **Focus** 
Focus Execution Point 可帮助您返回当前断点或在调试期间导致错误的活动。在浏览过程后使用“焦点”按钮，作为**返回导致错误的活动并恢复调试过程**的简单方法。
- **Breakpoints**
此按钮启动 Breakpoints 菜单。此菜单可让您在所选活动上切换断点或显示“断点”面板。断点不会在运行时持续存在，它们仅在调试模式下可用。
- **Slow Step** 
Slow Step使您可以在调试期间仔细查看任何活动。启用此操作后，活动会在调试过程中突出显示。可以在调试过程之前或期间激活慢步。激活操作不会暂停调试。慢步有 4 种不同的速度，范围从 1X 到 4X，其中 1X 是最慢的。
- **Execution Trail 执行轨迹**
默认情况下禁用此按钮。启用后，它会在调试时显示确切的执行路径。在流程执行期间，每个活动都在设计器面板中突出显示并标记，显示执行发生时：已执行的活动以绿色标记和突出显示；未执行的活动未以任何方式标记；引发异常的活动以红色标记和突出显示。
- **突出显示元素** 
如果启用，则在调试期间突出显示 UI 元素。该选项可用于常规调试和逐步调试。
- **日志活动  Log Activities**
如果启用，已调试的活动将在“输出”面板中显示为跟踪日志。如果已连接，日志会自动发送到 Orchestrator，但您可以通过从添加或编辑机器人窗口的设置选项卡中禁用允许开发日志记录选项，将它们存储在本地。禁用日志活动是一种将较小的日志文件发送到 Orchestrator 的方法。
- **出现异常时继续**
 默认情况下禁用此调试功能。在功能区中禁用时，它会引发执行错误并停止调试，突出显示异常活动并在“输出”面板中记录异常。如果之前在项目中设置了全局异常处理程序，则异常将传递给处理程序。启用后，异常会记录在“输出”面板中，然后继续执行。
- **画中画  Picture in Picture**
调试选项卡中的画中画 (PiP) 功能区选项可用于在您计算机上的单独会话中执行和调试进程或库。
如果启用，则只要您选择运行或运行文件、调试或调试文件，该过程就会在单独的会话中启动。如果禁用，则在当前会话中执行调试和执行。可以选择在 PiP 中运行流程在有人值守的自动化中非常有用。
- **打开日志 Open Logs**
 单击打开日志会打开 %localappdata%\UiPath\Logs 文件夹，日志存储在本地。日志文件的命名格式为 YYYY-DD-MM_Component.log。

在设计时，每个活动的上下文菜单中提供了三个选项：运行到此活动、从此活动运行和测试活动。在下图中，您可以看到 Type Company Name 活动的上下文菜单。
![在这里插入图片描述](https://img-blog.csdnimg.cn/759e6df32db2404893ea9a5129e86597.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAcXFfMzgzMTYxNDg=,size_20,color_FFFFFF,t_70,g_se,x_16)
- **运行到此活动 Run to this Activity**
右键单击​​“设计器”面板中的活动时，可以使用“运行到此活动”选项。此选项启动调试过程并在所选活动执行之前暂停，同时在面板中突出显示它。如果在调试已暂停时触发 Run to this Activity，则执行将继续，直到到达该 Activity。
- **从该活动运行 Run from this Activity**
 “从该活动运行”上下文菜单选项在暂停状态下进入调试，**允许您从“本地”面板更改变量和参数的值**。按 Continue 开始调试或使用 Step Into、Step Over 和 Step Out 等操作。
- **测试活动 Test Activity**
设计器面板的测试活动上下文菜单选项部分用于对当前选定的活动运行测试。可以通过两种方式使用测试活动：**向属性添加默认值**和**测试向活动属性添加参数和/或属性**，并在单击“测试活动”选项后使用“本地”面板添加值。


### 2.1.2 调试面板 
既然我们已经了解了有关调试操作的更多信息，让我们看看在调试模式下可用的面板。![在这里插入图片描述](https://img-blog.csdnimg.cn/229035d3ba9148c59bd95457b066cb36.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAcXFfMzgzMTYxNDg=,size_20,color_FFFFFF,t_70,g_se,x_16)
- **Locals**
	 Locals 面板仅在调试时可见。面板显示：
	- 异常 - 异常的描述和类型。
	- 参数
	- 变量
	- 先前执行的活动的属性 - 仅显示输入和输出属性。
	- 当前活动的属性 
	当调试暂停时，可以修改变量和参数的值。右键单击当前正在执行的活动的参数、变量或属性，将其添加到 Watch 面板并在整个调试过程中监视其执行情况。
- **Immediate**
 Immediate 面板仅在调试期间可见，可用于评估变量、参数或语句，并检查调试期间某个点可用的数据。为此，只需在“立即”窗口中键入变量或参数名称，然后按 Enter。 “立即”面板会保留之前评估过的语句的历史记录，并且可以使用“全部清除”上下文菜单选项将其删除。
 - **Breakpoints**
 Breakpoints 面板显示当前项目中的所有断点，以及它们所在的文件。活动名称列显示带有切换断点的活动，而文件路径列显示文件及其位置。条件列显示设置为断点的条件。如果条件满足，日志消息列会显示要记录的消息。将鼠标悬停在活动的断点标记上以查看其条件和日志消息。

- **Designer**
在调试模式下，Designer面板显示工作流、活动断点，并以黄色突出显示当前执行的活动，以红色突出显示引发异常的活动。

- **Highlight current action**
 在调试模式下，当前运行的活动在设计器面板中突出显示。这也适用于暂停执行的操作。
- **Watch**
 与 Call Stack 面板类似，Watch 面板仅在调试期间可见。它可以设置为显示变量或参数的值，以及在范围内的用户定义表达式的值。这些值在调试时每次活动执行后更新。

- **调用堆栈 Call Stack** 
当项目在调试中暂停时，调用堆栈面板显示下一个要执行的活动及其父容器。该面板在调试模式下执行期间显示，并在使用 Step Into、Break、Slow Step 或由于错误或断点暂停执行后填充。如果在调试过程中，活动抛出异常，则会在“调用堆栈”面板中进行标记，并以红色突出显示该活动。

- **输出 Output**
输出面板使您能够显示日志消息或写入行活动的输出等。此面板中还会显示包的例外情况。在“输出”面板中，您可以通过单击面板标题中的按钮来显示或隐藏具有不同日志级别（错误、警告）的消息。双击消息会显示有关它的更多详细信息，以及复制信息的选项。


现在我们对调试操作和面板有了一个概述，让我们进入下一课，看看我们如何使用一些基本的调试功能来解决我们项目中的错误。
# 3 基本调试功能 Basic Debugging Features
## 3.1 调试界面 The debugging interface
让我们花点时间熟悉 UiPath Studio 调试器的基本功能。
开始调试时，请记住以下功能：
- 调试文件、运行文件、调试和运行；Debug File, Run File, Debug and Run;  
- 功能区选项；The Ribbon Options;  
- 断点；Breakpoints;  
- 重试、忽略和重启；Retry, Ignore and Restart;  
- 踏入、跨出和跨出；Step Into, Step Over and Step Out;  
- 中断、继续和停止；Break, Continue and Stop;  
- 以及本地和输出面板。And the Locals and Output panels.  

# 3.2 断点 Breakpoints

让我们深入了解在 UiPath Studio 中使用断点breakpoints、条件断点conditional breakpoints、跟踪点tracepoints和条件跟踪点conditional tracepoints。

**我们的断点演示到此结束。快速回顾一下：**
断点用于暂停可能导致执行问题的活动的调试过程。断点将在运行活动或持有它的容器之前暂停执行。它们不影响运行模式下的执行。
条件断点是带有条件或命中计数的简单断点。
一个简单的跟踪点是一个带有日志记录的简单断点。
条件跟踪点是带有日志记录的条件断点。
对于跟踪点，我们可以禁用暂停执行并仅在调试模式下将它们用于日志记录目的。

[About the Breakpoints Panel - UiPath Studio Guide](https://docs.uipath.com/studio/v2020.10/docs/the-breakpoints-panel)

## 3.3 从此活动运行和运行到此活动 Run from this Activity and Run to this Activity

让我们看看两个调试操作：从这个活动运行和运行到这个活动。
**快速回顾一下：**

- 运行到此活动将调试项目并在执行所选活动之前停止。此操作可帮助您分解工作流程并检查第一部分。
- 从此活动运行将从所选活动开始调试。此操作可帮助您跳过工作流的第一部分并设置变量值以调试第二部分。
## 3.4 测试活动和创建测试台 Test Activity and Create Test Bench
在本视频中，我们将了解如何在工作流程中测试活动，以及如何创建测试平台来尝试想法。

**回顾一下：**

测试活动操作可从设计器面板中活动的上下文菜单访问，可用于测试单个活动或包含工作流中多个活动的容器。
CreateTest Bench 操作可从“活动”面板访问，可用于测试工作流想法。

我们关于基本调试功能的课程到此结束。在下一课中，我们将了解如何使用 Immediate、Watch 和 Call Stack 面板获得更高级的调试选项。
# 4 高级调试功能 Advanced Debugging Features
# 4.1 The Watch panel
让我们看看如何使用 Watch Panel 来监视变量或参数的值，以及在范围内的用户定义表达式的值。
快速回顾一下：
- 您可以使用 Watch 面板来**监视变量、参数和表达式值**。
- 这些值在调试时执行每个活动后更新。
- Watch 面板仅在**调试模式**下可见。


# 4.2 The Immediate panel 即时面板
观看下面的视频，了解我们如何在调试过程中使用即时面板检查**特定时间点**的可用数据。
**Video Transcript：**
在本视频中，我们将学习如何使用“立即”面板检查变量、参数和表达式的值，以及在调试过程中的某个时刻为变量赋值。

您可以在左侧看到“立即”面板。它可用于在调试期间检查某个点可用的数据。它可以计算变量、参数或语句，甚至赋值。为此，您只需在“立即”面板中键入变量、参数或表达式，然后按 Enter。
让我们添加一个变量来检查它的当前值。我们将使用名字。

请注意，按下“f”键会弹出 Intelliprompt 窗口，其中包含一些非常有用的建议，包括我们想要输入的变量。如果我们点击离开并点击返回，我们可以看到它不再可用。这是一个有用的提示：我们可以通过按 Control + Space 将其恢复。
对于您可以在“立即”面板中执行的更多操作：
您可以从面板中选择数据，右键单击并复制它。如您所见，您可以通过选择条目并按 Space 来删除条目。您可以右键单击面板窗口中的任意位置，然后选择全部清除以删除所有条目。

我们关于使用“立即”面板的演示到此结束。

**回顾一下：**
“立即”面板可用于在调试期间检查特定时间点可用的数据。它可以计算变量、参数或语句，甚至赋值。它仅在调试模式下可见。
# 4.3 调用堆栈面板 The Call Stack panel
让我们看看当项目在调试中暂停时，调用堆栈面板如何帮助我们**看到下一个要执行的活动及其父容器**。

**Video Transcript：**
——
在本视频中，我们将了解如何使用“调用堆栈”面板查看要执行的下一个活动的父容器。

您可以在右侧看到 Call Stack 面板。当在调试模式下暂停执行时，它会显示**要执行的下一个活动及其父容器**。在使用 Step Into、Break、Slow Step 或由于遇到错误或断点而暂停执行之后，它会被填充。

双击“调用堆栈”面板中的容器将聚焦于它。
让我们双击 Sequence 进行调试。请注意，它侧重于容器。

接下来，让我们看看“调用堆栈”面板中的异常是什么样的。我们将单击继续……我们已经到了抛出异常的地步。
正如之前的视频中提到的，我们可以在 Locals 和 Output 面板中看到异常消息。我们也可以在 Call Stack 面板中看到它。它通知我们异常是由 Assign 活动抛出的。

我们关于使用“调用堆栈”面板的演示到此结束。
在调试模式下暂停执行时，“调用堆栈”面板会显示要执行的下一个活动及其父容器。

# 5  Practice - Fix My Workflow
调试同事的工作流程

您的同事的任务是创建一个概念证明，以证明 UiPath 对不断变化的界面的适应性。机器人需要从 www.fakenamegenerator.com 中提取名字、姓氏、电话号码和公司名称，并将它们插入到 rpahallenge.com 上的正确字段中。

机器人运行不正常，您的同事需要您的帮助才能使其正常工作。您可以使用第一章中讨论的方法下载项目并调试此工作流吗？
