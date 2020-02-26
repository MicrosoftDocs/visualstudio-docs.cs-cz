---
title: Úloha UidManager | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- UidManager task [WPF MSBuild]
- UidManager task [WPF MSBuild], parameters
- managing UIDs when localizing XAML elements [WPF MSBuild]
- localizing XAML elements [WPF MSBuild], managing UIDs
- checking UIDs when localizing XAML elements [WPF MSBuild]
ms.assetid: 4fc7b5a5-11b0-46ca-9656-8c2a0b08d1fe
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 312e174b1bbe0a21d155e4e6b5050e6f41dd8352
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/25/2020
ms.locfileid: "77579558"
---
# <a name="uidmanager-task"></a>UidManager – úloha
Úloha <xref:Microsoft.Build.Tasks.Windows.UidManager> kontroluje, aktualizuje nebo odebírá jedinečné identifikátory (UID), aby bylo možné lokalizovat všechny [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] prvky, které jsou součástí zdrojových [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] souborů.

## <a name="task-parameters"></a>Parametry úlohy

| Parametr | Popis |
|-------------------------| - |
| `IntermediateDirectory` | Volitelný **řetězcový** parametr.<br /><br /> Určuje adresář, který se použije k zálohování zdrojových [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] souborů, které jsou určené parametrem **MarkupFiles** . |
| `MarkupFiles` | Povinný parametr **ITaskItem []** .<br /><br /> Určuje zdrojové [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] soubory, které se mají zahrnout pro kontrolu UID, aktualizaci nebo odebrání. |
| `Task` | Povinný parametr **řetězce**<br /><br /> Určuje úlohu správy UID, kterou chcete provést. Platné možnosti jsou **check**, **Update**nebo **Remove**. |

## <a name="example"></a>Příklad
 Následující příklad používá úlohu <xref:Microsoft.Build.Tasks.Windows.UidManager> ke kontrole, zda zadané zdrojové [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] soubory obsahují [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] prvky, které mají příslušné identifikátory UID.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <UsingTask
    TaskName="Microsoft.Build.Tasks.Windows.UidManager"
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />
  <Target Name="UidManagerTask">
    <UidManager
      Task="Check"
      MarkupFiles="Page1.xaml;Page2.xaml"
      IntermediateDirectory="c:\UidManagerIntermediateDirectory" />
  </Target>
</Project>
```

## <a name="see-also"></a>Viz také
- [Referenční dokumentace WPF MSBuild](../msbuild/wpf-msbuild-reference.md)
- [Odkaz na úkol](../msbuild/wpf-msbuild-task-reference.md)
- [Referenční dokumentace nástroje MSBuild](../msbuild/msbuild-reference.md)
- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
- [Sestavení aplikace WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
- [Postupy: lokalizace aplikace](/dotnet/framework/wpf/advanced/how-to-localize-an-application)