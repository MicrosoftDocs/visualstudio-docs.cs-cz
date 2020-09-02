---
title: Úloha GetWinFXPath – | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
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
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: da32f0bfce9edf652e19df6b68bc51ed92624d80
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65699014"
---
# <a name="getwinfxpath-task"></a>GetWinFXPath – úloha
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

<xref:Microsoft.Build.Tasks.Windows.GetWinFXPath>Úloha vrátí adresář aktuálního [!INCLUDE[TLA#tla_winfx](../includes/tlasharptla-winfx-md.md)] modulu runtime.  
  
## <a name="task-parameters"></a>Parametry úlohy  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`WinFXPath`|Volitelný výstupní parametr **řetězce** .<br /><br /> Určuje skutečnou cestu k [!INCLUDE[TLA2#tla_winfx](../includes/tla2sharptla-winfx-md.md)] modulu runtime.|  
|`WinFXNativePath`|Povinný parametr **řetězce**<br /><br /> Určuje cestu k nativnímu [!INCLUDE[TLA2#tla_titlewinfx](../includes/tla2sharptla-titlewinfx-md.md)] modulu runtime.|  
|`WinFXWowPath`|Povinný parametr **řetězce**<br /><br /> Určuje cestu k [!INCLUDE[TLA#tla_winfx](../includes/tlasharptla-winfx-md.md)] sestavením v 32 **Windows** v modulu Windows na 64 bitových systémech.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud <xref:Microsoft.Build.Tasks.Windows.GetWinFXPath> úloha běží na 64 procesoru, parametr **WinFXPath** se nastaví na cestu, která je uložená v parametru **WinFXWowPath** . v opačném případě je parametr **WinFXPath** nastavený na cestu, která je uložená v parametru **WinFXNativePath** .  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak použít úlohu **GetWinFXPath –** k detekci nativní cesty k [!INCLUDE[TLA2#tla_titlewinfx](../includes/tla2sharptla-titlewinfx-md.md)] modulu runtime.  
  
```  
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
 [Referenční dokumentace WPF MSBuild](../msbuild/wpf-msbuild-reference.md)   
 [Odkaz na úkol](../msbuild/wpf-msbuild-task-reference.md)   
 [Referenční dokumentace nástroje MSBuild](../msbuild/msbuild-reference.md)   
 [Odkaz na úkol](../msbuild/msbuild-task-reference.md)   
 [Sestavení aplikace WPF (WPF)](https://msdn.microsoft.com/library/a58696fd-bdad-4b55-9759-136dfdf8b91c)
