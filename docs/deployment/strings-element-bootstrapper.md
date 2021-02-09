---
title: '&lt;Strings – &gt; element (zaváděcí nástroj) | Microsoft Docs'
description: Element Strings definuje lokalizované řetězce pro názvy produktů, názvy balíčků a chybové zprávy instalace.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- MSBuild.GenerateBootstrapper.NoStringsForCulture
- MSBuild.GenerateBootstrapper.ProductCultureNotFound
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- <Strings> element [bootstrapper]
ms.assetid: d5ea3613-5fc9-4a11-bef3-46a01178bf60
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a2c8cac705f4e6ae8d72f3a2e9bd5ec4c8ed68bd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99877470"
---
# <a name="ltstringsgt-element-bootstrapper"></a>&lt;Strings – &gt; element (zaváděcí nástroj)
Definuje lokalizované řetězce pro názvy produktů, názvy balíčků a chybové zprávy instalace.

## <a name="syntax"></a>Syntax

```xml
<Strings>
    <String
        Name
    >
    </String>
</Strings>
```

## <a name="elements-and-attributes"></a>Elementy a atributy
 `Strings`Prvek je podřízeným prvkem `Package` elementu. Nemá žádné atributy.

## <a name="string"></a>Řetězec
 `String`Prvek je podřízeným prvkem `Strings` elementu. `Strings`Element může obsahovat jeden nebo více `String` prvků.

 `String` má následující atribut.

|Atribut|Popis|
|---------------|-----------------|
|`Name`|Povinná hodnota. Název řetězce.|

## <a name="example"></a>Příklad
 Následující příklad kódu určuje všechny anglické řetězce pro instalační službu .NET Framework.

```xml
<Strings>
    <String Name="DisplayName">.NET Framework 2.0</String>
    <String Name="Culture">en</String>
    <String Name="AdminRequired">Administrator permissions are required to install the .NET Framework 2.0. Contact your administrator.</String>
    <String Name="InvalidPlatformWin9x">Installation of the .NET Framework 2.0 is not supported on Windows 95. Contact your application vendor.</String>
    <String Name="InvalidPlatformWinNT">Installation of the .NET Framework 2.0 is not supported on Windows NT 4.0. Contact your application vendor.</String>
    <String Name="InvalidPlatformIE">Installation of the .NET Framework 2.0 requires Internet Explorer 5.01 or greater. Contact your application vendor.</String>
    <String Name="InvalidPlatformArchitecture">This version of the .NET Framework 2.0 is not supported on a 64-bit operating system. Contact your application vendor.</String>
    <String Name="WindowsInstallerImproperInstall">Due to an error with Windows Installer, the installation of the .NET Framework 2.0 cannot proceed.</String>
    <String Name="AnotherInstanceRunning">Another instance of setup is already running. The running instance must complete before this setup can proceed.</String>
    <String Name="BetaNDPFailure">A beta version of the .NET Framework was detected on the computer. Uninstall any previous beta versions of .NET Framework before continuing.</String>
    <String Name="GeneralFailure">A failure occurred attempting to install the .NET Framework 2.0.</String>
    <String Name="DotNetFXExe">http://go.microsoft.com/fwlink/?LinkId=37283</String>
    <String Name="InstMsiAExe">http://go.microsoft.com/fwlink/?LinkId=37285</String>
    <String Name="Msi30Exe">http://go.microsoft.com/fwlink/?LinkId=37287</String>
</Strings>
```

## <a name="see-also"></a>Viz také
- [\<Package> objekt](../deployment/package-element-bootstrapper.md)