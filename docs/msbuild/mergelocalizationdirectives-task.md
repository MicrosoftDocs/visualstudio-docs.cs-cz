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
ms.openlocfilehash: 86c689122ac0ddfd9441122fdead64ecd8049e72
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/25/2020
ms.locfileid: "77579636"
---
# <a name="mergelocalizationdirectives-task"></a>MergeLocalizationDirectives – – úloha
Úloha <xref:Microsoft.Build.Tasks.Windows.MergeLocalizationDirectives> sloučí atributy lokalizace a komentáře jednoho nebo více [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] binárních formátů souborů do jednoho souboru pro celé sestavení.

## <a name="task-parameters"></a>Parametry úlohy

| Parametr | Popis |
|------------------------------| - |
| `GeneratedLocalizationFiles` | Povinný parametr **ITaskItem []** .<br /><br /> Určuje seznam souborů pokynů pro lokalizaci pro jednotlivé soubory v binárním formátu [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)]. |
| `OutputFile` | Povinný výstupní parametr **řetězce** .<br /><br /> Určuje výstupní cestu sestavení kompilovaných direktiv lokalizace. |

## <a name="remarks"></a>Poznámky
K [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] obsahu lze přidat atributy lokalizace a komentáře. Díky podpoře lokalizace [!INCLUDE[TLA#tla_wpf](../msbuild/includes/tlasharptla_wpf_md.md)] můžete oddělit atributy lokalizace a komentáře a vkládat je do souboru *. Loc* , který je oddělen od generovaného sestavení. Můžete to provést pomocí atributu **LocalizationPropertyStorage** . Další informace o atributech lokalizace a komentářích a **LocalizationPropertyStorage**naleznete v tématu [lokalizace atributů a komentářů](/dotnet/framework/wpf/advanced/localization-attributes-and-comments).

## <a name="example"></a>Příklad
Následující příklad sloučí komentáře lokalizace několika souborů binárního formátu [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] do jediného souboru *. Loc* .

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
