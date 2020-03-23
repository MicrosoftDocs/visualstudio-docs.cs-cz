---
title: Úloha MergeLocalizationDirectives | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633496"
---
# <a name="mergelocalizationdirectives-task"></a>Úloha MergeLocalizationDirectives

Úloha <xref:Microsoft.Build.Tasks.Windows.MergeLocalizationDirectives> sloučí lokalizační atributy a komentáře jednoho nebo více souborů binárního formátu XAML do jednoho souboru pro celé sestavení.

## <a name="task-parameters"></a>Parametry úlohy

| Parametr | Popis |
|------------------------------| - |
| `GeneratedLocalizationFiles` | Povinný parametr **ITaskItem[].**<br /><br /> Určuje seznam souborů lokalizačních směrnic pro jednotlivé soubory v binárním formátu XAML. |
| `OutputFile` | Požadovaný výstupní parametr **řetězce.**<br /><br /> Určuje výstupní cestu sestavení kompilované lokalizační direktivy. |

## <a name="remarks"></a>Poznámky

Do obsahu XAML můžete přidat atributy lokalizace a komentáře. S podporou lokalizace Windows Presentation Foundation (WPF) můžete odstranit atributy lokalizace a komentáře a umístit je do souboru *LOC,* který je oddělený od generovaného sestavení. Můžete to provést pomocí **LocalizationPropertyStorage** atribut. Další informace o lokalizačních atributech a komentářích a **LocalizationPropertyStorage**naleznete v [tématu Atributy lokalizace a komentáře](/dotnet/framework/wpf/advanced/localization-attributes-and-comments).

## <a name="example"></a>Příklad

Následující příklad sloučí lokalizační komentáře několika souborů binárního formátu XAML do jednoho souboru *LOC.*

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

- [WPF MSBuild odkaz](../msbuild/wpf-msbuild-reference.md)
- [WPF MSBuild odkaz na úkol](../msbuild/wpf-msbuild-task-reference.md)
- [Odkaz na sestavení msbuild](../msbuild/msbuild-reference.md)
- [Odkaz na úkol MSBuild](../msbuild/msbuild-task-reference.md)
- [Vytvoření aplikace WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
