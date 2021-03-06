---
title: "如何：将 Web 浏览器功能添加到 Windows 窗体应用程序"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- WebBrowser control [Windows Forms], adding Web browser capabilities to your application
- WebBrowser control [Windows Forms], examples
- Web browsers [.NET Framework], adding to Windows Forms
- examples [Windows Forms], WebBrowser control
- Windows Forms, adding Web browser functionality
ms.assetid: 3871f072-b57a-435b-9976-e5da28df04a7
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b061b62c782cf511d26d165d5b8bdf0c9c9486b3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-web-browser-capabilities-to-a-windows-forms-application"></a>如何：将 Web 浏览器功能添加到 Windows 窗体应用程序
使用 <xref:System.Windows.Forms.WebBrowser> 控件，可将 Web 浏览器功能添加到应用程序中。 默认情况下，该控件的工作方式类似于 Web 浏览器。 通过设置 <xref:System.Windows.Forms.WebBrowser.Url%2A> 属性加载初始 URL 后，可以通过单击超链接或通过使用键盘快捷方式在导航历史记录中后移或前移，从而进行导航。 默认情况下，可以通过右键单击快捷菜单来访问其他浏览器功能。 还可通过将新文档置于控件上来打开它们。 <xref:System.Windows.Forms.WebBrowser> 控件还具有几个属性、方法和事件，可将它们可用于实现与 Internet Explorer 中类似的用户界面功能。  
  
 下面的代码示例实现地址栏、典型的浏览器按钮、“文件”菜单、状态栏以及显示当前页标题的标题栏。  
  
## <a name="example"></a>示例  
 [!code-cpp[System.Windows.Forms.WebBrowser#0](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser/CPP/form1.cpp#0)]
 [!code-csharp[System.Windows.Forms.WebBrowser#0](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.WebBrowser#0](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a>编译代码  
 此示例需要：  
  
-   对 `System,``System.Drawing` 和 `System.Windows.Forms` 程序集的引用。  
  
 有关从 [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] 或 [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] 的命令行生成此示例的信息，请参阅[从命令行生成](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或[在命令行上使用 csc.exe 生成](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。 还可以通过将代码粘贴到新项目，在 [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] 中生成此示例。  另请参阅 [如何：使用 Visual Studio 编译和运行完整的 Windows 窗体代码示例](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))。  
  
## <a name="see-also"></a>请参阅  
 <xref:System.Windows.Forms.WebBrowser>  
 [WebBrowser 控件](../../../../docs/framework/winforms/controls/webbrowser-control-windows-forms.md)
