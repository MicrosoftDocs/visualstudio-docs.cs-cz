---
title: Úloha MergeLocalizationDirectives – | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- localizing XAML [WPF MSBuild], moving comments and attributes to a separate file
- MergeLocalizationDirectives task [WPF MSBuild], parameters
- MergeLocalizationDirectives task [WPF MSBuild]
- moving localization comments and attributes to a separate file [WPF MSBuild]
ms.assetid: 9095b4f1-88da-4194-914b-ee1456826830
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9c7699afeb09604a437aad091f9aaf9ce624d33e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "77633496"
---
# <a name="mergelocalizationdirectives-task"></a>MergeLocalizationDirectives – úloha

<xref:Microsoft.Build.Tasks.Windows.MergeLocalizationDirectives>Úkol sloučí atributy lokalizace a komentáře jednoho nebo více souborů binárního formátu XAML do jednoho souboru pro celé sestavení.

## <a name="task-parameters"></a>Parametry úlohy

| Parametr | Popis |
|------------------------------| - |
| `GeneratedLocalizationFiles` | Povinný parametr **ITaskItem []** .<br /><br /> Určuje seznam souborů pokynů pro lokalizaci pro jednotlivé soubory v binárním formátu XAML. |
| `OutputFile` | Povinný výstupní parametr **řetězce** .<br /><br /> Určuje výstupní cestu sestavení kompilovaných direktiv lokalizace. |

## <a name="remarks"></a>Poznámky

Do obsahu XAML lze přidat atributy lokalizace a komentáře. S podporou lokalizace Windows Presentation Foundation (WPF) můžete oddělit atributy lokalizace a komentáře a umístit je do souboru *. Loc* , který je oddělen od generovaného sestavení. Můžete to provést pomocí atributu **LocalizationPropertyStorage** . Další informace o atributech lokalizace a komentářích a **LocalizationPropertyStorage**naleznete v tématu [lokalizace atributů a komentářů](/dotnet/framework/wpf/advanced/localization-attributes-and-comments).

## <a name="example"></a>Příklad

Následující příklad sloučí lokalizační komentáře několika souborů binárního formátu XAML do jediného souboru *. Loc* .

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <UsingTask
    TaskName="Microsoft.Build.Tasks.Windows.MergeLocalizationDirectives"
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />
  <Target Name="MergeLocalizationDirectivesTask">
    <MergeLocalizationDirectives
      GeneratedLocalizationFiles="obj\debug\page1.loc;obj\debug\page2.loc;obj\debug\page3.loc"
      OutputFile="obj\debug\WPFMSBuildSample.loc" />
  </Target>
</Project>
```

## <a name="see-also"></a>Viz také

- [Referenční dokumentace WPF MSBuild](../msbuild/wpf-msbuild-reference.md)
- [WPF MSBuild – referenční dokumentace úlohy](../msbuild/wpf-msbuild-task-reference.md)
- [Referenční dokumentace nástroje MSBuild](../msbuild/msbuild-reference.md)
- [Referenční dokumentace úlohy nástroje MSBuild](../msbuild/msbuild-task-reference.md)
- [Sestavení aplikace WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
