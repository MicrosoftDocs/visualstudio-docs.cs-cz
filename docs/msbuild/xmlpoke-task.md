---
title: XmlPoke Úkol | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- XmlPoke task [MSBuild]
- MSBuild, XmlPoke task
ms.assetid: 6ba1953c-be3b-4df8-8561-e133408f8270
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f44ce4736900fde35716ca3ec9dabb2d55c6df51
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75588379"
---
# <a name="xmlpoke-task"></a>XmlPoke – úloha

Nastaví hodnoty určené dotazem XPath do souboru XML.

## <a name="parameters"></a>Parametry

 Následující tabulka popisuje parametry `XmlPoke` úkolu.

|Parametr|Popis|
|---------------|-----------------|
|`Namespaces`|Volitelný `String` parametr.<br /><br /> Určuje obory názvů pro předpony dotazu XPath. `Namespaces`je výstřižek XML `Namespace` skládající se `Prefix` z `Uri`prvků s atributy a . Atribut `Prefix` určuje předponu, kterou chcete přidružit k oboru názvů zadanému v atributu. `Uri` Nepoužívejte prázdný `Prefix`.|
|`Query`|Volitelný `String` parametr.<br /><br /> Určuje dotaz XPath.|
|`Value`|Požadovaný parametr <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Určuje hodnotu, která má být vložena do zadané cesty.|
|`XmlInputPath`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> parametr.<br /><br /> Určuje vstup XML jako cestu k souboru.|

## <a name="remarks"></a>Poznámky

 Kromě parametrů, které jsou uvedeny v tabulce, tato úloha <xref:Microsoft.Build.Tasks.TaskExtension> dědí parametry z <xref:Microsoft.Build.Utilities.Task> třídy, která sama dědí z třídy. Seznam těchto dalších parametrů a jejich popisy naleznete v tématu [TaskExtension base class](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Příklad

Zde je sample.xml upravit:

```xml
<Package xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10"
         xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest"
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10" >
<Identity Name="Sample.Product " Publisher="CN=1234" Version="1.0.0.0" />
<mp:PhoneIdentity PhoneProductId="456" PhonePublisherId="0" />
</Package>
```

V tomto příkladu, pokud `/Package/mp:PhoneIdentity/PhonePublisherId`chcete upravit , použijte

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <PropertyGroup>
    <Namespace>
        <Namespace Prefix="dn" Uri="http://schemas.microsoft.com/appx/manifest/foundation/windows10" />
        <Namespace Prefix="mp" Uri="http://schemas.microsoft.com/appx/2014/phone/manifest" />
        <Namespace Prefix="uap" Uri="http://schemas.microsoft.com/appx/manifest/uap/windows10" />
    </Namespace>
</PropertyGroup>

<Target Name="Poke">
  <XmlPoke
    XmlInputPath="Sample.xml"
    Value="MyId"
    Query="/dn:Package/mp:PhoneIdentity/@PhoneProductId"
    Namespaces="$(Namespace)"/>
</Target>
</Project>
```

`dn`slouží jako předpona umělého oboru názvů pro výchozí obor názvů.

## <a name="see-also"></a>Viz také

- [Úlohy](../msbuild/msbuild-tasks.md)
- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
