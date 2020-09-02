---
title: Úloha UidManager | Microsoft Docs
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
- UidManager task [WPF MSBuild]
- UidManager task [WPF MSBuild], parameters
- managing UIDs when localizing XAML elements [WPF MSBuild]
- localizing XAML elements [WPF MSBuild], managing UIDs
- checking UIDs when localizing XAML elements [WPF MSBuild]
ms.assetid: 4fc7b5a5-11b0-46ca-9656-8c2a0b08d1fe
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5fd8175911def7fb1b63dc63d967c404d649e9e4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65703698"
---
# <a name="uidmanager-task"></a>UidManager – úloha
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

<xref:Microsoft.Build.Tasks.Windows.UidManager>Úkol zkontroluje, aktualizuje nebo odebere jedinečné identifikátory (UID), aby bylo možné lokalizovat všechny [!INCLUDE[TLA#tla_xaml](../includes/tlasharptla-xaml-md.md)] prvky, které jsou součástí zdrojových [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] souborů.  
  
## <a name="task-parameters"></a>Parametry úlohy  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`IntermediateDirectory`|Volitelný **řetězcový** parametr.<br /><br /> Určuje adresář, který se použije k zálohování zdrojových [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] souborů, které jsou určené parametrem **MarkupFiles** .|  
|`MarkupFiles`|Povinný parametr **ITaskItem []** .<br /><br /> Určuje zdrojové [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] soubory, které se mají zahrnout pro kontrolu UID, aktualizaci nebo odebrání.|  
|`Task`|Povinný parametr **řetězce**<br /><br /> Určuje úlohu správy UID, kterou chcete provést. Platné možnosti jsou **check**, **Update**nebo **Remove**.|  
  
## <a name="example"></a>Příklad  
 Následující příklad používá <xref:Microsoft.Build.Tasks.Windows.UidManager> úlohu ke kontrole, zda zadané zdrojové [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] soubory obsahují [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] prvky, které mají příslušné identifikátory UID.  
  
```  
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
 [Referenční dokumentace WPF MSBuild](../msbuild/wpf-msbuild-reference.md)   
 [Odkaz na úkol](../msbuild/wpf-msbuild-task-reference.md)   
 [Referenční dokumentace nástroje MSBuild](../msbuild/msbuild-reference.md)   
 [Odkaz na úkol](../msbuild/msbuild-task-reference.md)   
 [Sestavení aplikace WPF (WPF)](https://msdn.microsoft.com/library/a58696fd-bdad-4b55-9759-136dfdf8b91c)   
 [Postupy: Lokalizace aplikace](https://msdn.microsoft.com/library/5001227e-9326-48a4-9dcd-ba1b89ee6653)
