---
title: Podpora Ngen ve vSIX v3 | Dokumenty společnosti Microsoft
ms.date: 11/09/2016
ms.topic: conceptual
ms.assetid: 1472e884-c74e-4c23-9d4a-6d8bdcac043b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cb75b9256ca937106235fa7a7d66d9cec71c9c60
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702403"
---
# <a name="ngen-support-in-vsix-v3"></a>Podpora Ngen ve VSIX v. 3

S Visual Studio 2017 a nový Formát manifestu rozšíření VSIX v3 (verze 3) rozšíření, rozšíření vývojáři nyní "ngen" jejich sestavení v době instalace.

Níže je výňatek z MSDN, který vysvětluje, co "ngen" dělá:

>Generátor nativního obrazu (*Ngen.exe*) je nástroj, který zlepšuje výkon spravovaných aplikací. *Ngen.exe* vytvoří nativní bitové kopie, což jsou soubory obsahující zkompilovaný strojový kód specifický pro procesor, a nainstaluje je do nativní mezipaměti bitových kopií v místním počítači. Modul runtime může ke kompilaci původního sestavení použít nativní bitové kopie z mezipaměti namísto kompilátoru JIT (just-in-time).
>
>od [Ngen.exe (Nativní generátor obrázků)](/dotnet/framework/tools/ngen-exe-native-image-generator)

Aby bylo možné "ngen" sestavení, VSIX musí být nainstalován "per-instance per-machine". To lze povolit zaškrtnutím zaškrtávacího `extension.vsixmanifest` políčka "všichni uživatelé" v návrháři:

![kontrola všech uživatelů](media/check-all-users.png)

## <a name="how-to-enable-ngen"></a>Jak povolit Ngen

Chcete-li povolit ngen pro sestavení, můžete použít okno **Vlastnosti** v sadě Visual Studio.

K dispozici jsou 4 vlastnosti, které lze nastavit:

1. **Ngen** (Boolean) - Pokud true, instalační program sady Visual Studio bude "ngen" sestavení.
2. **Ngen aplikace** (řetězec) - Ngen poskytuje možnost použít soubor *app.config* aplikace k vyřešení závislosti sestavení. Tato hodnota by měla být nastavena na aplikaci, jejíž *application.config* chcete použít (vzhledem k instalačnímu adresáři sady Visual Studio).
3. **Ngen Architektura** (výčtu) - architektura nativně zkompilovat sestavení. Možnosti jsou: a. NotSpecified b. X86 c. X64 d. Všechny
4. **Priorita Ngen** (celé číslo mezi 1 a 3) - Úroveň priority Ngen je dokumentována na [úrovních priority Ngen.exe](/dotnet/framework/tools/ngen-exe-native-image-generator#priority-levels).

Zde je pohled na okno **Vlastnosti** v akci:

![ngen ve vlastnostech](media/ngen-in-properties.png)

Tím přidáte metadata do odkazu projektu uvnitř souboru *.csproj* projektu VSIX:

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
> Soubor .csproj můžete upravit přímo, pokud dáváte přednost.

## <a name="extra-information"></a>Další informace

Změny návrháře vlastností platí pro více než jen odkazy na projekt; můžete nastavit metadata Ngen pro položky uvnitř projektu také (pomocí stejných metod popsaných výše), pokud jsou položky .NET sestavení.
