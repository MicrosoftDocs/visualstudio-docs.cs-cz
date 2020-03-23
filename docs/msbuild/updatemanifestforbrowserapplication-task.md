---
title: Úloha aplikace UpdateManifestForBrowserApplication | Dokumenty společnosti Microsoft
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
ms.openlocfilehash: 079eecd6751f168a7beba32eda6d15eda712bd7f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77631325"
---
# <a name="updatemanifestforbrowserapplication-task"></a>Úloha UpdateManifestForBrowserApplication

Úloha je spuštěna <xref:Microsoft.Build.Tasks.Windows.UpdateManifestForBrowserApplication> pro přidání prvku ** \<hostInBrowser />** do manifestu aplikace*\<(název projektu>.exe.manifest)* při sestavení projektu aplikace prohlížeče XAML (XBAP).

## <a name="task-parameters"></a>Parametry úlohy

|Parametr|Popis|
|---------------|-----------------|
|`ApplicationManifest`|Povinný parametr **ITaskItem[].**<br /><br /> Určuje cestu a název souboru manifestu aplikace, `<hostInBrowser />` do kterého chcete prvek přidat.|
|`HostInBrowser`|Povinný **logický** parametr.<br /><br /> Určuje, zda má být manifest aplikace modifikován tak, aby zahrnoval prvek ** \<hostInBrowser />.** Pokud **true**, nový ** \<hostInBrowser />** element je součástí ** \<entryPoint />** element. Zahrnutí prvku je kumulativní: Pokud prvek ** \<hostInBrowser />** již existuje, není odebrán nebo přepsán. Místo toho je vytvořen další ** \<prvek hostInBrowser />.** Pokud **false**, manifest aplikace není změněn.|

## <a name="remarks"></a>Poznámky

 XBAPs jsou spouštěny pomocí clickonce nasazení, takže musí být publikovány s podporou nasazení a manifesty aplikací. MSBuild používá úlohu [GenerateApplicationManifest](generateapplicationmanifest-task.md) ke generování manifestu aplikace.

 Potom chcete-li nakonfigurovat aplikaci, která má být hostována z prohlížeče, musí být do manifestu aplikace přidán další ** \<prvek hostInBrowser />,** jak je znázorněno v následujícím příkladu:

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

 Úloha je spuštěna <xref:Microsoft.Build.Tasks.Windows.UpdateManifestForBrowserApplication> při projektu XBAP je `<hostInBrowser />` sestaven za účelem přidání prvku.

## <a name="example"></a>Příklad

 Následující příklad ukazuje, jak se `<hostInBrowser />` ujistit, že prvek je součástí souboru manifestu aplikace.

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

- [WPF MSBuild odkaz](../msbuild/wpf-msbuild-reference.md)
- [Odkaz na úkol](../msbuild/wpf-msbuild-task-reference.md)
- [Odkaz na sestavení msbuild](../msbuild/msbuild-reference.md)
- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
- [Vytvoření aplikace WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
- [Přehled aplikací prohlížeče WPF XAML](/dotnet/framework/wpf/app-development/wpf-xaml-browser-applications-overview)