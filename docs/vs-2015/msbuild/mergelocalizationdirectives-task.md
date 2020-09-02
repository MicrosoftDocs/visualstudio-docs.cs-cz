---
title: Úloha MergeLocalizationDirectives – | Microsoft Docs
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
- localizing XAML [WPF MSBuild], moving comments and attributes to a separate file
- MergeLocalizationDirectives task [WPF MSBuild], parameters
- MergeLocalizationDirectives task [WPF MSBuild]
- moving localization comments and attributes to a separate file [WPF MSBuild]
ms.assetid: 9095b4f1-88da-4194-914b-ee1456826830
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2d6c2aa6cea687119e69b565da5468e8fa723641
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65703423"
---
# <a name="mergelocalizationdirectives-task"></a>MergeLocalizationDirectives – úloha
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

<xref:Microsoft.Build.Tasks.Windows.MergeLocalizationDirectives>Úkol sloučí atributy lokalizace a komentáře jednoho nebo více [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] souborů binárního formátu do jediného souboru pro celé sestavení.  
  
## <a name="task-parameters"></a>Parametry úlohy  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`GeneratedLocalizationFiles`|Povinný parametr **ITaskItem []** .<br /><br /> Určuje seznam souborů pokynů pro lokalizaci pro jednotlivé soubory v [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] binárním formátu.|  
|`OutputFile`|Povinný výstupní parametr **řetězce** .<br /><br /> Určuje výstupní cestu sestavení kompilovaných direktiv lokalizace.|  
  
## <a name="remarks"></a>Poznámky  
 K obsahu můžete přidat atributy lokalizace a komentáře [!INCLUDE[TLA#tla_xaml](../includes/tlasharptla-xaml-md.md)] . S [!INCLUDE[TLA#tla_wpf](../includes/tlasharptla-wpf-md.md)] podporou lokalizace můžete oddělit atributy lokalizace a komentáře a vkládat je do souboru. Loc, který je oddělen od generovaného sestavení. Můžete to provést pomocí atributu **LocalizationPropertyStorage** . Další informace o atributech lokalizace a komentářích a **LocalizationPropertyStorage**naleznete v tématu [lokalizace atributů a komentářů](https://msdn.microsoft.com/library/ead2d9ac-b709-4ec1-a924-39927a29d02f).  
  
## <a name="example"></a>Příklad  
 Následující příklad sloučí komentáře lokalizace několika [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] souborů binárního formátu do jediného souboru. Loc.  
  
```  
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
 [Referenční dokumentace WPF MSBuild](../msbuild/wpf-msbuild-reference.md)   
 [Odkaz na úkol](../msbuild/wpf-msbuild-task-reference.md)   
 [Referenční dokumentace nástroje MSBuild](../msbuild/msbuild-reference.md)   
 [Odkaz na úkol](../msbuild/msbuild-task-reference.md)   
 [Sestavení aplikace WPF (WPF)](https://msdn.microsoft.com/library/a58696fd-bdad-4b55-9759-136dfdf8b91c)
