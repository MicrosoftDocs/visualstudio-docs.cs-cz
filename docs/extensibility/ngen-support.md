---
title: Podpora Ngen ve VSIX v. 3 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/09/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 1472e884-c74e-4c23-9d4a-6d8bdcac043b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3b5f9c7b297d98836ca3e5c017d2a0d440a30470
ms.sourcegitcommit: 9765b3fcf89375ca499afd9fc42cf4645b66a8a2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/20/2018
ms.locfileid: "46495476"
---
# <a name="ngen-support-in-vsix-v3"></a>Podpora Ngen ve VSIX v. 3

Pomocí sady Visual Studio 2017 a nové VSIX v. 3 manifestu rozšíření (verze 3) formát, teď můžou vývojáři rozšíření "ngen" jejich sestavení v době instalace.

Níže je výňatkem z webu MSDN, která vysvětluje, jaké "ngen" dělá:

>Native Image Generator (*Ngen.exe*) je nástroj zvyšující výkon spravovaných aplikací. *Ngen.exe* vytváří nativní bitové kopie, které jsou soubory obsahující zkompilovaný strojový kód závislý na procesoru a nainstaluje je do mezipaměti nativních bitových kopií v místním počítači. Modul runtime může ke kompilaci původního sestavení použít nativní bitové kopie z mezipaměti namísto kompilátoru JIT (just-in-time).
>
>z [Ngen.exe (Generátor nativních obrázků)](/dotnet/framework/tools/ngen-exe-native-image-generator)

Aby "ngen" sestavení musí být rozšíření VSIX nainstalován "jednotlivé instance vázaná na počítač". Lze povolit zaškrtnutím políčka "all users" `extension.vsixmanifest` návrháře:

![Zkontrolujte všechny uživatele](media/check-all-users.png)

## <a name="how-to-enable-ngen"></a>Povolení technologie Ngen

Pokud chcete povolit ngen pro sestavení, můžete použít **vlastnosti** okna v sadě Visual Studio.

Existují 4 vlastnosti, které je možné nastavit:

1. **Ngen** (Boolean) – Pokud je hodnota true, instalační program sady Visual Studio bude "ngen" sestavení.
2. **Aplikace Ngen** (string) – Ngen nabízí možnost použití aplikace *app.config* souboru, aby bylo možné vyřešit závislosti sestavení. Tato hodnota musí být nastavena na aplikaci jehož *app.config* chcete použít (relativní k adresáři instalace sady Visual Studio).
3. **Architektura Ngen** (výčtu) – architektura pro nativní kompilaci vašeho sestavení. Možnosti jsou:. NotSpecified b. X86 c. X64 d. Všechny
4. **Priorita Ngen** (celé číslo mezi 1 a 3) – úroveň The Ngen Priority je popsána v [úrovně priority Ngen.exe](/dotnet/framework/tools/ngen-exe-native-image-generator#priority-levels).

Tady se můžete podívat na **vlastnosti** okno v akci:

![v dialogovém okně Vlastnosti Ngen](media/ngen-in-properties.png)

Metadata se přidá do projektu odkaz v projektu VSIX *.csproj* souboru:

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

 >**Poznámka:** můžete upravit soubor .csproj přímo, který preferujete.

## <a name="extra-information"></a>Další informace

Vlastnosti návrháře změny se aplikují na víc než jenom odkazy projektu; můžete nastavit metadata Ngen pro položky v rámci projektu také (pomocí stejných metod, popsané výše), dokud položky jsou sestavení .NET.