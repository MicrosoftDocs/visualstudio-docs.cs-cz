---
title: Úloha UpdateManifestForBrowserApplication – | Microsoft Docs
description: Přečtěte si, jak MSBuild spouští úlohu UpdateManifestForBrowserApplication – pro přidání elementu hostInBrowser do manifestu aplikace.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 43e8fc7b9b09af51ea3be73409e2dcde9a718cee
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2020
ms.locfileid: "93046814"
---
# <a name="updatemanifestforbrowserapplication-task"></a>UpdateManifestForBrowserApplication – úloha

<xref:Microsoft.Build.Tasks.Windows.UpdateManifestForBrowserApplication>Úloha je spuštěna za účelem přidání **\<hostInBrowser />** elementu do manifestu aplikace ( *\<projectname> . exe. manifest* ) při sestavení projektu aplikace prohlížeče XAML (XBAP).

## <a name="task-parameters"></a>Parametry úlohy

|Parametr|Popis|
|---------------|-----------------|
|`ApplicationManifest`|Povinný parametr **ITaskItem []** .<br /><br /> Určuje cestu a název souboru manifestu aplikace, do kterého chcete přidat `<hostInBrowser />` prvek.|
|`HostInBrowser`|Požadovaný **logický** parametr.<br /><br /> Určuje, zda má být upraven manifest aplikace pro zahrnutí **\<hostInBrowser />** elementu. Je-li **nastavena hodnota true** , **\<hostInBrowser />** je do prvku zahrnut nový prvek **\<entryPoint />** . Zahrnutí elementu je kumulativní: Pokud **\<hostInBrowser />** prvek již existuje, nebude odebrán ani přepsán. Místo toho **\<hostInBrowser />** je vytvořen další prvek. Pokud má **hodnotu false** , manifest aplikace se nezmění.|

## <a name="remarks"></a>Poznámky

 Aplikace XBAP jsou spouštěny pomocí nasazení ClickOnce, takže je nutné je publikovat s podpůrnými manifesty nasazení a aplikací. Nástroj MSBuild používá úlohu [GenerateApplicationManifest –](generateapplicationmanifest-task.md) k vygenerování manifestu aplikace.

 Chcete-li nakonfigurovat aplikaci, aby byla hostována z prohlížeče, **\<hostInBrowser />** je nutné do manifestu aplikace přidat další prvek, jak je znázorněno v následujícím příkladu:

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

 <xref:Microsoft.Build.Tasks.Windows.UpdateManifestForBrowserApplication>Úloha se spustí, když je sestaven projekt XBAP, aby bylo možné přidat `<hostInBrowser />` prvek.

## <a name="example"></a>Příklad

 Následující příklad ukazuje, jak se ujistit, zda `<hostInBrowser />` je element obsažen v souboru manifestu aplikace.

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
- [Referenční dokumentace úlohy](../msbuild/wpf-msbuild-task-reference.md)
- [Referenční dokumentace nástroje MSBuild](../msbuild/msbuild-reference.md)
- [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)
- [Sestavení aplikace WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
- [Přehled aplikací prohlížeče WPF XAML](/dotnet/framework/wpf/app-development/wpf-xaml-browser-applications-overview)