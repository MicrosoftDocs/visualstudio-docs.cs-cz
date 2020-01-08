---
title: Úloha XmlPoke – | Microsoft Docs
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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75588379"
---
# <a name="xmlpoke-task"></a>XmlPoke – úloha

Nastaví hodnoty určené dotazem XPath do souboru XML.

## <a name="parameters"></a>Parametry

 Následující tabulka popisuje parametry úlohy `XmlPoke`.

|Parametr|Popis|
|---------------|-----------------|
|`Namespaces`|Volitelný parametr `String`.<br /><br /> Určuje obory názvů pro předpony dotazů XPath. `Namespaces` je fragment kódu XML sestávající z `Namespace` prvků s atributy `Prefix` a `Uri`. Atribut `Prefix` Určuje předponu, která má být přidružena k oboru názvů určenému v atributu `Uri`. Nepoužívejte prázdné `Prefix`.|
|`Query`|Volitelný parametr `String`.<br /><br /> Určuje dotaz XPath.|
|`Value`|Vyžaduje se <xref:Microsoft.Build.Framework.ITaskItem> parametr.<br /><br /> Určuje hodnotu, která bude vložena do zadané cesty.|
|`XmlInputPath`|Volitelný parametr <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Určuje vstup XML jako cestu k souboru.|

## <a name="remarks"></a>Poznámky

 Kromě toho, že mají parametry, které jsou uvedeny v tabulce, tato úloha dědí parametry z třídy <xref:Microsoft.Build.Tasks.TaskExtension>, kterou sám dědí z třídy <xref:Microsoft.Build.Utilities.Task>. Seznam těchto dalších parametrů a jejich popis naleznete v tématu [TaskExtension – Base Class](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Příklad

Tady je ukázkový soubor. XML, který se má změnit:

```xml
<Package xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10"
         xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest"
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10" >
<Identity Name="Sample.Product " Publisher="CN=1234" Version="1.0.0.0" />
<mp:PhoneIdentity PhoneProductId="456" PhonePublisherId="0" />
</Package>
```

V tomto příkladu, pokud chcete upravit `/Package/mp:PhoneIdentity/PhonePublisherId`, použijte

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

`dn` se používá jako umělá předpona oboru názvů pro výchozí obor názvů.

## <a name="see-also"></a>Viz také:

- [Úlohy](../msbuild/msbuild-tasks.md)
- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
