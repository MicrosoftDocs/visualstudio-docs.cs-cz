---
title: Úloha UidManager | Microsoft Docs
description: Naučte se, jak úloha UidManager MSBuild kontroluje, aktualizuje nebo odebírá jedinečné identifikátory (UID) pro lokalizaci všech prvků XAML ve zdrojových souborech XAML.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6287abee811d406ef7aafa5ce3cc3dc62624b0d1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99902622"
---
# <a name="uidmanager-task"></a>UidManager – úloha

<xref:Microsoft.Build.Tasks.Windows.UidManager>Úkol zkontroluje, aktualizuje nebo odebere jedinečné identifikátory (UID), aby bylo možné lokalizovat všechny prvky XAML, které jsou zahrnuty ve zdrojových souborech XAML.

## <a name="task-parameters"></a>Parametry úlohy

| Parametr | Popis |
|-------------------------| - |
| `IntermediateDirectory` | Volitelný **řetězcový** parametr.<br /><br /> Určuje adresář, který se použije k zálohování zdrojových souborů XAML, které jsou určené parametrem **MarkupFiles** . |
| `MarkupFiles` | Povinný parametr **ITaskItem []** .<br /><br /> Určuje zdrojové soubory XAML, které mají být zahrnuty pro kontrolu UID, aktualizaci nebo odebrání. |
| `Task` | Povinný parametr **řetězce**<br /><br /> Určuje úlohu správy UID, kterou chcete provést. Platné možnosti jsou **check**, **Update** nebo **Remove**. |

## <a name="example"></a>Příklad

 Následující příklad používá <xref:Microsoft.Build.Tasks.Windows.UidManager> úlohu ke kontrole, zda zadané zdrojové soubory XAML obsahují prvky XAML, které mají odpovídající identifikátory UID.

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
- [Referenční dokumentace úlohy](../msbuild/wpf-msbuild-task-reference.md)
- [Referenční dokumentace nástroje MSBuild](../msbuild/msbuild-reference.md)
- [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)
- [Sestavení aplikace WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
- [Postupy: lokalizace aplikace](/dotnet/framework/wpf/advanced/how-to-localize-an-application)