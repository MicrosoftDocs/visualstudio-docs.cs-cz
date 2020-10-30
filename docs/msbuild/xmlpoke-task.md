---
title: Úloha XmlPoke – | Microsoft Docs
description: Naučte se, jak MSBuild používá úlohu XmlPoke – k nastavení hodnot, které jsou určené dotazem XPath do souboru XML.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 35e29004116807092452a08d3835ba3e5e1dabcd
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2020
ms.locfileid: "93047233"
---
# <a name="xmlpoke-task"></a>XmlPoke – úloha

Nastaví hodnoty určené dotazem XPath do souboru XML.

## <a name="parameters"></a>Parametry

 Následující tabulka popisuje parametry `XmlPoke` úkolu.

|Parametr|Popis|
|---------------|-----------------|
|`Namespaces`|Volitelný `String` parametr.<br /><br /> Určuje obory názvů pro předpony dotazů XPath. `Namespaces` je fragment kódu XML sestávající z `Namespace` elementů s atributy `Prefix` a `Uri` . Atribut `Prefix` Určuje předponu, která má být přidružena k oboru názvů určenému v `Uri` atributu. Nepoužívejte prázdné `Prefix` .|
|`Query`|Volitelný `String` parametr.<br /><br /> Určuje dotaz XPath.|
|`Value`|Požadovaný parametr <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Určuje hodnotu, která bude vložena do zadané cesty.|
|`XmlInputPath`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> parametr.<br /><br /> Určuje vstup XML jako cestu k souboru.|

## <a name="remarks"></a>Poznámky

 Kromě parametrů, které jsou uvedeny v tabulce, tato úloha dědí parametry z <xref:Microsoft.Build.Tasks.TaskExtension> třídy, která sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam těchto dalších parametrů a jejich popis naleznete v tématu [TaskExtension – Base Class](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Příklad

Tady je sample.xml ke změně:

```xml
<Package xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10"
         xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest"
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10" >
<Identity Name="Sample.Product " Publisher="CN=1234" Version="1.0.0.0" />
<mp:PhoneIdentity PhoneProductId="456" PhonePublisherId="0" />
</Package>
```

V tomto příkladu, pokud chcete upravit `/Package/mp:PhoneIdentity/PhoneProductId` , pak použít

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

`dn` slouží jako umělá předpona oboru názvů pro výchozí obor názvů.

## <a name="see-also"></a>Viz také

- [Úlohy](../msbuild/msbuild-tasks.md)
- [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)
