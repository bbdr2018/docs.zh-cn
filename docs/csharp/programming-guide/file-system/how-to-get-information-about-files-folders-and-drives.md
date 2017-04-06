---
title: "如何：获取有关文件、文件夹和驱动器的信息（C# 编程指南）| Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- files [C#], getting information about
ms.assetid: 22fc2da6-5494-405b-995e-c0b99142a93e
caps.latest.revision: 30
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 16950f835938846804ade1a8ad23d907aa69b9c3
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-get-information-about-files-folders-and-drives--c-programming-guide"></a>如何：获取有关文件、文件夹和驱动器的信息（C# 编程指南）
在 .NET Framework 中，可以使用以下类访问文件系统信息：  
  
-   <xref:System.IO.FileInfo?displayProperty=fullName>  
  
-   <xref:System.IO.DirectoryInfo?displayProperty=fullName>  
  
-   <xref:System.IO.DriveInfo?displayProperty=fullName>  
  
-   <xref:System.IO.Directory?displayProperty=fullName>  
  
-   <xref:System.IO.File?displayProperty=fullName>  
  
 <xref:System.IO.FileInfo> 和 <xref:System.IO.DirectoryInfo> 类表示文件或目录，并包含用于公开 NTFS 文件系统所支持的许多文件特性的属性。 它们还包含用于打开、关闭、移动和删除文件和文件夹的方法。 可以通过将表示文件、文件夹或驱动器名称的字符串传入构造函数来创建这些类的实例：  
  
```csharp  
System.IO.DriveInfo di = new System.IO.DriveInfo(@"C:\");  
```  
  
 还可以使用对 <xref:System.IO.DirectoryInfo.GetDirectories%2A?displayProperty=fullName>、<xref:System.IO.DirectoryInfo.GetFiles%2A?displayProperty=fullName> 和 <xref:System.IO.DriveInfo.RootDirectory%2A?displayProperty=fullName> 的调用来获取文件、文件夹或驱动器的名称。  
  
 <xref:System.IO.Directory?displayProperty=fullName> 和 <xref:System.IO.File?displayProperty=fullName> 类提供用于检索有关目录和文件的信息的静态方法。  
  
## <a name="example"></a>示例  
 下面的示例演示用于访问有关文件和文件夹的信息的各种方法。  
  
 [!code-cs[csFilesandFolders#6](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-get-information-about-files-folders-and-drives_1.cs)]  
  
## <a name="robust-programming"></a>可靠编程  
 处理用户指定的路径字符串时，还应针对以下情况处理异常：  
  
-   文件名格式不正确。 例如，它包含无效字符或只包含空格。  
  
-   文件名为 null。  
  
-   文件名超过系统定义的最大长度。  
  
-   文件名包含冒号 (:)。  
  
 如果应用程序没有足够权限来读取指定文件，`Exists` 方法会返回 `false`（无论路径是否存在）；该方法不会引发异常。  
  
## <a name="see-also"></a>请参阅  
 <xref:System.IO?displayProperty=fullName>   
 [C# 编程指南](../../../csharp/programming-guide/index.md)   
 [文件系统和注册表（C# 编程指南）](../../../csharp/programming-guide/file-system/index.md)