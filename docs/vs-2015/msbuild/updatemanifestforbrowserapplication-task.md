---
title: Úloha UpdateManifestForBrowserApplication – | Microsoft Docs
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
- UpdateManifestForBrowserApplication task [WPF MSBuild]
- adding the <hostInBrowser /> element to the application manifest [WPF MSBuild]
- building XBAP projects [WPF MSBuild]
- UpdateManifestForBrowserApplication task [WPF MSBuild], parameters
ms.assetid: 653339f7-654b-4d64-a26a-5c9f27036895
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6dffa98a8abbf74bd6eee8761d91f09a7c022666
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68740223"
---
# <a name="updatemanifestforbrowserapplication-task"></a>UpdateManifestForBrowserApplication – úloha
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

<xref:Microsoft.Build.Tasks.Windows.UpdateManifestForBrowserApplication>Úloha je spuštěna za účelem přidání **\<hostInBrowser />** elementu do manifestu aplikace (*ProjectName*. exe. manifest) při [!INCLUDE[TLA#tla_xbap](../includes/tlasharptla-xbap-md.md)] sestavení projektu.  
  
## <a name="task-parameters"></a>Parametry úlohy  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`ApplicationManifest`|Povinný parametr **ITaskItem []** .<br /><br /> Určuje cestu a název souboru manifestu aplikace, do kterého chcete přidat `<hostInBrowser />` prvek.|  
|`HostInBrowser`|Požadovaný **logický** parametr.<br /><br /> Určuje, zda má být upraven manifest aplikace pro zahrnutí **\<hostInBrowser />** elementu. Je-li **nastavena hodnota true**, `<` je v elementu obsažen nový prvek **HostInBrowser/>** **\<entryPoint />** . Zahrnutí elementu je kumulativní: Pokud **\<hostInBrowser />** prvek již existuje, není odebrán ani přepsán. Místo toho **\<hostInBrowser />** je vytvořen další prvek. Pokud má **hodnotu false**, manifest aplikace se nezmění.|  
  
## <a name="remarks"></a>Poznámky  
 [!INCLUDE[TLA2#tla_xbap#plural](../includes/tla2sharptla-xbapsharpplural-md.md)] jsou spouštěny pomocí [!INCLUDE[TLA#tla_clickonce](../includes/tlasharptla-clickonce-md.md)] nasazení, a proto musí být publikovány s podpůrnými manifesty nasazení a aplikací. [!INCLUDE[TLA#tla_msbuild](../includes/tlasharptla-msbuild-md.md)] vygeneruje manifest aplikace pomocí úlohy [GenerateApplicationManifest –](/dotnet/api/microsoft.build.tasks.generateapplicationmanifest) .  
  
 Chcete-li nakonfigurovat aplikaci, aby byla hostována z prohlížeče, je **\<hostInBrowser />** nutné do manifestu aplikace přidat další prvek, jak je znázorněno v následujícím příkladu:  
  
```  
<!--MyXBAPApplication.exe.manifest-->  
<?xml version="1.0" encoding="utf-8"?>  
<asmv1:assembly ... >  
    <asmv1:assemblyIdentity ... />  
    <application />  
    <entryPoint>  
      ...  
      <hostInBrowser xmlns="urn:schemas-microsoft-com:asm.v3" />  
    </entryPoint>  
  ...  
/>  
```  
  
 <xref:Microsoft.Build.Tasks.Windows.UpdateManifestForBrowserApplication>Úloha se spustí, když [!INCLUDE[TLA2#tla_xbap](../includes/tla2sharptla-xbap-md.md)] je projekt sestaven, aby bylo možné přidat `<hostInBrowser />` prvek.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak zajistit, aby byl `<hostInBrowser />` prvek součástí souboru manifestu aplikace.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <UsingTask   
    TaskName="Microsoft.Build.Tasks.Windows.UpdateManifestForBrowserApplication"  
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />  
  <Target Name="UpdateManifestForBrowserApplicationTask">  
    <UpdateManifestForBrowserApplication  
      ApplicationManifest="MyXBAPApplication.exe.manifest"  
      HostInBrowser="true" />  
  </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace WPF MSBuild](../msbuild/wpf-msbuild-reference.md)   
 [Odkaz na úkol](../msbuild/wpf-msbuild-task-reference.md)   
 [Referenční dokumentace nástroje MSBuild](../msbuild/msbuild-reference.md)   
 [Odkaz na úkol](../msbuild/msbuild-task-reference.md)   
 [Sestavení aplikace WPF (WPF)](https://msdn.microsoft.com/library/a58696fd-bdad-4b55-9759-136dfdf8b91c)   
 [Přehled aplikací Prohlížeče WPF XAML](https://msdn.microsoft.com/library/3a7a86a8-75d5-4898-96b9-73da151e5e16)
