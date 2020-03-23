---
title: Úloha XmlPeek | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- XmlPeek task [MSBuild]
- MSBuild, XmlPeek task
ms.assetid: 19196031-a3bc-41b5-9c4a-f2572630e179
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c5a76bf033fa3eb85f0626478b965285f32e5fb6
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094668"
---
# <a name="xmlpeek-task"></a>XmlPeek – úloha

Vrátí hodnoty určené dotazem XPath ze souboru XML.

## <a name="parameters"></a>Parametry

 Následující tabulka popisuje parametry `XmlPeek` úkolu.

|Parametr|Popis|
|---------------|-----------------|
|`Namespaces`|Volitelný `String` parametr.<br /><br /> Určuje obory názvů předpon dotazu XPath.|
|`Query`|Volitelný `String` parametr.<br /><br /> Určuje dotaz XPath.|
|`Result`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` výstupní parametr.<br /><br /> Obsahuje výsledky, které jsou vráceny tímto úkolem.|
|`XmlContent`|Volitelný `String` parametr.<br /><br /> Určuje vstup XML jako řetězec.|
|`XmlInputPath`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> parametr.<br /><br /> Určuje vstup XML jako cestu k souboru.|

## <a name="remarks"></a>Poznámky

 Kromě parametrů, které jsou uvedeny v tabulce, tato úloha <xref:Microsoft.Build.Tasks.TaskExtension> dědí parametry z <xref:Microsoft.Build.Utilities.Task> třídy, která sama dědí z třídy. Seznam těchto dalších parametrů a jejich popisy naleznete v tématu [TaskExtension base class](../msbuild/taskextension-base-class.md).



## <a name="example"></a>Příklad

Zde je ukázkový `settings.config` soubor XML ke čtení:

```xml
<appSettings>
  <add key="ProjectFolder" value="S1" />
</appSettings>
```

V tomto příkladu, pokud `value`chcete číst , použijte kód jako následující:

```xml
<Target Name="BeforeBuild">
    <XmlPeek XmlInputPath="settings.config" Query="appSettings/add[@key='ProjectFolder']/@value">
        <Output TaskParameter="Result" ItemName="value" />
    </XmlPeek>
    <Message Text="Using project folder @(value)." Importance="high" />
    <PropertyGroup>
        <ProjectFolder>@(value)</ProjectFolder>
    </PropertyGroup>
    <ItemGroup>
        <Compile Include="Projects\$(ProjectFolder)\Controls\Control1.ascx.cs">
            <SubType>ASPXCodeBehind</SubType>
        </Compile>
    </ItemGroup>
</Target>
```

## <a name="see-also"></a>Viz také

- [Úlohy](../msbuild/msbuild-tasks.md)
- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
