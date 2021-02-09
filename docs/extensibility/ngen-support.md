---
title: Podpora Ngen v VSIX V3 | Microsoft Docs
description: Naučte se, jak povolit generátor nativních bitových kopií, což je nástroj, který mohou vývojáři rozšíření využít ke zvýšení výkonu spravovaných aplikací.
ms.custom: SEO-VS-2020
ms.date: 11/09/2016
ms.topic: conceptual
ms.assetid: 1472e884-c74e-4c23-9d4a-6d8bdcac043b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: cc674fbc8930415584eb5bed64f8c9cc67e0a8a2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99886649"
---
# <a name="ngen-support-in-vsix-v3"></a>Podpora Ngen ve VSIX v. 3

V rámci sady Visual Studio 2017 a nového formátu manifestu rozšíření VSIX V3 (verze 3) můžou vývojáři rozšíření nyní v době instalace "Ngen" svá sestavení.

Níže je uveden výňatek z webu MSDN, který vysvětluje, co dělá "Ngen":

>Generátor nativních bitových kopií (*Ngen.exe*) je nástroj, který vylepšuje výkon spravovaných aplikací. *Ngen.exe* vytvoří nativní bitové kopie, které jsou soubory obsahující zkompilovaný kód počítače specifický pro procesor, a nainstaluje je do mezipaměti nativních imagí v místním počítači. Modul runtime může ke kompilaci původního sestavení použít nativní bitové kopie z mezipaměti namísto kompilátoru JIT (just-in-time).
>
>z [Ngen.exe (generátor nativních imagí)](/dotnet/framework/tools/ngen-exe-native-image-generator)

Aby bylo možné sestavení "Ngen", musí být VSIX nainstalováno "na jednotlivé instance pro každý počítač". To lze povolit zaškrtnutím políčka Všichni uživatelé v `extension.vsixmanifest` Návrháři:

![kontrolovat všechny uživatele](media/check-all-users.png)

## <a name="how-to-enable-ngen"></a>Jak povolit Ngen

Chcete-li povolit Ngen pro sestavení, můžete použít okno **vlastnosti** v aplikaci Visual Studio.

Je možné nastavit 4 vlastnosti:

1. **Ngen** (Boolean) – při hodnotě true bude instalační program sady Visual Studio sestavení Ngen.
2. **Aplikace Ngen** (String) – Ngen poskytuje možnost použít soubor *app.config* aplikace, aby se vyřešily závislosti sestavení. Tato hodnota by měla být nastavena na aplikaci, jejíž *app.config* chcete použít (vzhledem k instalačnímu adresáři sady Visual Studio).
3. **Architektura Ngen** (Enum) – architektura pro nativně zkompilování sestavení. Možnosti jsou: a. NotSpecified b. X86 c. X64 d. Vše
4. **Priorita Ngen** (celé číslo od 1 do 3) – úroveň priority Ngen je dokumentována na [Ngen.exe úrovní priority](/dotnet/framework/tools/ngen-exe-native-image-generator#priority-levels).

Tady je pohled na okno **vlastnosti** v akci:

![Ngen ve vlastnostech](media/ngen-in-properties.png)

Tím se do odkazu projektu přidá metadata v souboru *. csproj* projektu VSIX:

```xml
 <ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
    <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
    <Name>ClassLibrary1</Name>
    <Ngen>True</Ngen>
    <NgenApplication>vsn.exe</NgenApplication>
    <NgenArchitecture>X86</NgenArchitecture>
    <NgenPriority>2</NgenPriority>
</ProjectReference>
```

> [!NOTE]
> Pokud dáváte přednost, můžete soubor. csproj upravit přímo.

## <a name="extra-information"></a>Další informace

Změny návrháře vlastností se použijí na více než jenom odkazy na projekt. Můžete také nastavit metadata Ngen pro položky uvnitř projektu (pomocí stejných metod popsaných výše), pokud jsou položky sestavení .NET.
