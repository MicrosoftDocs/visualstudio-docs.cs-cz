---
title: Úloha GetWinFXPath | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- getting the directory of the current .NET Framework runtime [WPF MSBuild]
- GetWinFXPath task [WPF MSBuild], parameters
- GetWinFXPath task [WPF MSBuild]
- obtaining the path to the current .NET Framework runtime [WPF MSBuild]
ms.assetid: b1dfb467-f3d3-47f3-83ef-af7b0e33a772
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ab8e15cef722e935dde322072f6834ba00be8bc5
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633964"
---
# <a name="getwinfxpath-task"></a>Úloha GetWinFXPath

Úloha <xref:Microsoft.Build.Tasks.Windows.GetWinFXPath> vrátí adresář aktuálního běhu .NET.

## <a name="task-parameters"></a>Parametry úlohy

| Parametr | Popis |
|-------------------| - |
| `WinFXPath` | Volitelný výstupní parametr **String.**<br /><br /> Určuje skutečnou cestu k běhu .NET. |
| `WinFXNativePath` | Povinný **parametr String.**<br /><br /> Určuje cestu k nativnímu běhu .NET. |
| `WinFXWowPath` | Povinný **parametr String.**<br /><br /> Určuje cestu k sestavením .NET v 32bitovém **modulu systému Windows** v 64bitových systémech. |

## <a name="remarks"></a>Poznámky

 Pokud <xref:Microsoft.Build.Tasks.Windows.GetWinFXPath> je úloha spuštěna na 64bitovém procesoru, parametr **WinFXPath** je nastaven na cestu uloženou v parametru **WinFXWowPath;** jinak je parametr **WinFXPath** nastaven na cestu, která je uložena v parametru **WinFXNativePath.**

## <a name="example"></a>Příklad

 Následující příklad ukazuje, jak pomocí úlohy **GetWinFXPath** zjistit nativní cestu k běhu .NET.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <UsingTask
    TaskName="Microsoft.Build.Tasks.Windows.GetWinFXPath"
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />
  <Target Name="GetWinFXPathTask">
    <GetWinFXPath
      WinFXNativePath="c:\WinFXNative"
      WinFXWowPath="c:\WinFXWowNative" />
  </Target>
  <Import Project="$(MSBuildBinPath)\Microsoft.WinFX.targets" />
</Project>
```

## <a name="see-also"></a>Viz také

- [WPF MSBuild odkaz](../msbuild/wpf-msbuild-reference.md)
- [Odkaz na úkol](../msbuild/wpf-msbuild-task-reference.md)
- [Odkaz na sestavení msbuild](../msbuild/msbuild-reference.md)
- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
- [Vytvoření aplikace WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
