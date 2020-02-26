---
title: Úloha UpdateManifestForBrowserApplication – | Microsoft Docs
ms.date: 11/04/2016
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a78add284a5cea966d1176645649eed19017addd
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/25/2020
ms.locfileid: "77579543"
---
# <a name="updatemanifestforbrowserapplication-task"></a>UpdateManifestForBrowserApplication task
Úloha <xref:Microsoft.Build.Tasks.Windows.UpdateManifestForBrowserApplication> je spuštěna za účelem přidání prvku **\<HostInBrowser/>** do manifestu aplikace ( *\<ProjectName >. exe. manifest*) při sestavení projektu [!INCLUDE[TLA#tla_xbap](../msbuild/includes/tlasharptla_xbap_md.md)].

## <a name="task-parameters"></a>Parametry úlohy

|Parametr|Popis|
|---------------|-----------------|
|`ApplicationManifest`|Povinný parametr **ITaskItem []** .<br /><br /> Určuje cestu a název souboru manifestu aplikace, do kterého chcete přidat prvek `<hostInBrowser />`.|
|`HostInBrowser`|Požadovaný **logický** parametr.<br /><br /> Určuje, zda se má změnit manifest aplikace tak, aby zahrnoval prvek **\<HostInBrowser/>** . Je-li **nastavena hodnota true**, je v prvku **\<EntryPoint/>** obsažen nový prvek **\<HostInBrowser/>** . Zahrnutí elementu je kumulativní: Pokud **\<prvek HostInBrowser/>** již existuje, není odebrán ani přepsán. Místo toho je vytvořen další **\<prvek HostInBrowser/>** . Pokud má **hodnotu false**, manifest aplikace se nezmění.|

## <a name="remarks"></a>Poznámky
 [!INCLUDE[TLA2#tla_xbap#plural](../msbuild/includes/tla2sharptla_xbapsharpplural_md.md)] se spouští pomocí nasazení [!INCLUDE[TLA#tla_clickonce](../msbuild/includes/tlasharptla_clickonce_md.md)], takže je nutné je publikovat s podpůrnými manifesty nasazení a aplikací. [!INCLUDE[TLA#tla_msbuild](../msbuild/includes/tlasharptla_msbuild_md.md)] používá úlohu [GenerateApplicationManifest –](generateapplicationmanifest-task.md) k vygenerování manifestu aplikace.

 Chcete-li nakonfigurovat aplikaci, aby byla hostována z prohlížeče, je nutné do manifestu aplikace přidat další **\<prvek HostInBrowser/>** , jak je znázorněno v následujícím příkladu:

```xml
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

 Úkol <xref:Microsoft.Build.Tasks.Windows.UpdateManifestForBrowserApplication> je spuštěn při sestavení [!INCLUDE[TLA2#tla_xbap](../msbuild/includes/tla2sharptla_xbap_md.md)] projektu, aby bylo možné přidat prvek `<hostInBrowser />`.

## <a name="example"></a>Příklad
 Následující příklad ukazuje, jak zajistit, aby byl prvek `<hostInBrowser />` zahrnutý v souboru manifestu aplikace.

```xml
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
- [Referenční dokumentace WPF MSBuild](../msbuild/wpf-msbuild-reference.md)
- [Odkaz na úkol](../msbuild/wpf-msbuild-task-reference.md)
- [Referenční dokumentace nástroje MSBuild](../msbuild/msbuild-reference.md)
- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
- [Sestavení aplikace WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
- [Přehled aplikací prohlížeče WPF XAML](/dotnet/framework/wpf/app-development/wpf-xaml-browser-applications-overview)