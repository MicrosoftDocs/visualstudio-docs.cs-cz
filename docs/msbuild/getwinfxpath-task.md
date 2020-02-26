---
title: Úloha GetWinFXPath – | Microsoft Docs
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
ms.openlocfilehash: 894cfe9fd6e116e983a5290e5817211182b073c7
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/25/2020
ms.locfileid: "77578612"
---
# <a name="getwinfxpath-task"></a>GetWinFXPath – – úloha
Úloha <xref:Microsoft.Build.Tasks.Windows.GetWinFXPath> vrátí adresář aktuálního modulu runtime [!INCLUDE[TLA#tla_winfx](../msbuild/includes/tlasharptla_winfx_md.md)].

## <a name="task-parameters"></a>Parametry úlohy

| Parametr | Popis |
|-------------------| - |
| `WinFXPath` | Volitelný výstupní parametr **řetězce** .<br /><br /> Určuje skutečnou cestu k modulu runtime [!INCLUDE[TLA2#tla_winfx](../msbuild/includes/tla2sharptla_winfx_md.md)]. |
| `WinFXNativePath` | Povinný parametr **řetězce**<br /><br /> Určuje cestu k nativnímu modulu runtime [!INCLUDE[TLA2#tla_titlewinfx](../msbuild/includes/tla2sharptla_titlewinfx_md.md)]. |
| `WinFXWowPath` | Povinný parametr **řetězce**<br /><br /> Určuje cestu k [!INCLUDE[TLA#tla_winfx](../msbuild/includes/tlasharptla_winfx_md.md)] sestavení v 32 **Windows** v modulu windows na 64 bitových systémech. |

## <a name="remarks"></a>Poznámky
 Pokud je úloha <xref:Microsoft.Build.Tasks.Windows.GetWinFXPath> prováděna na 64ovém procesoru, parametr **WinFXPath** je nastaven na cestu, která je uložena v parametru **WinFXWowPath** ; v opačném případě je parametr **WinFXPath** nastaven na cestu, která je uložena v parametru **WinFXNativePath** .

## <a name="example"></a>Příklad
 Následující příklad ukazuje, jak použít úlohu **GetWinFXPath –** k detekci nativní cesty k modulu runtime [!INCLUDE[TLA2#tla_titlewinfx](../msbuild/includes/tla2sharptla_titlewinfx_md.md)].

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
- [Referenční dokumentace WPF MSBuild](../msbuild/wpf-msbuild-reference.md)
- [Odkaz na úkol](../msbuild/wpf-msbuild-task-reference.md)
- [Referenční dokumentace nástroje MSBuild](../msbuild/msbuild-reference.md)
- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
- [Sestavení aplikace WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
