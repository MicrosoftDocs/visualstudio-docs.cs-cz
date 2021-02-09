---
title: Hledání aplikace Visual Studio | Microsoft Docs
description: Můžete nainstalovat více instancí stejné verze sady Visual Studio. Naučte se používat rozhraní API pro dotazování objektů COM k nalezení požadované instance.
ms.custom: SEO-VS-2020
ms.date: 08/21/2017
ms.topic: conceptual
helpviewer_keywords:
- deployment, VSIX
ms.assetid: 680c3b25-7901-4768-8363-6d1fcd1ea636
ms.author: heaths
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 175623723b8f7b59a644a439afd10246eab01c95
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99893591"
---
# <a name="locate-visual-studio"></a>Vyhledání sady Visual Studio

Počínaje sadou Visual Studio 2017 můžete nainstalovat více instancí stejné verze nebo dokonce edice. To je užitečné, když chcete zobrazit náhled nových funkcí na primárním vývojovém počítači a přitom zachovat předchozí instalaci. Z důvodu těchto změn neexistuje žádná proměnná prostředí nebo hodnota registru, kterou můžete použít k vyhledání instance. Místo toho můžete použít [rozhraní API pro dotazování objektů COM](/dotnet/api/microsoft.visualstudio.setup.configuration) k nalezení instancí na základě kritérií relevantních pro vaše rozšíření.

Toto je rychlé rozhraní API jen pro čtení s balíčky NuGet dostupnými pro nativní a spravovaný kód.

| Kód | Balíček |
| ---- | --- |
| Nativní | https://nuget.org/packages/Microsoft.VisualStudio.Setup.Configuration.Native |
| Spravované | https://nuget.org/packages/Microsoft.VisualStudio.Setup.Configuration.Interop |

Můžete vyhledat jednu instanci, která má danou cestu nebo aktuální proces, nebo zobrazit výčet všech instancí. Kompletní příklady, jak najít sadu Visual Studio, najdete v [našich ukázkách](https://github.com/Microsoft/vs-setup-samples) .

## <a name="tools"></a>nástroje

Pokud chcete najít sadu Visual Studio a další nástroje v prostředích pro vytváření sestavení, skripty PowerShellu, instalační programy a další scénáře, můžete použít přímo nebo distribuovatelné nástroje společně s vlastními skripty.

| Projekt | Popis |
| ------- | ----------- |
| [vswhere](https://github.com/Microsoft/vswhere) | Nativní spustitelný soubor s jedním souborem pro vyhledání instancí, jako je vydání nebo předběžná verze, jaký produkt je nainstalovaný a které úlohy se nainstalují. Také podporuje hledání v aplikaci Visual Studio 2010 a novější, i když je vráceno méně informací, které jsou k dispozici pro Visual Studio 2017 a novější. Příklady najdete na [wikiwebu](https://github.com/Microsoft/vswhere/wiki) . |
| [Rutiny VSSetup](https://github.com/Microsoft/vssetup.powershell) | Rutiny prostředí PowerShell podporované 2,0 a novějším, které vracejí formátované informace jako objekty, které můžete použít k vyhledání instancí na základě stejných kritérií jako _vswhere_ a zjišťování ještě více vlastností instancí. Příklady najdete na [wikiwebu](https://github.com/Microsoft/vssetup.powershell/wiki) . |
| [VSIXBootstrapper](https://github.com/Microsoft/vsixbootstrapper) | Automaticky vyhledá _VSIXInstaller_ a předá příkazový řádek a nainstaluje soubor **. vsix* . Tato funkce může být užitečná v instalačních nástrojích, které nemají přímou podporu pro rozhraní API pro dotazy. Příklady najdete na [wikiwebu](https://github.com/Microsoft/vsixbootstrapper/wiki) . |

## <a name="see-also"></a>Viz také

* [Změny v instalačním programu sady Visual Studio 2017](https://devblogs.microsoft.com/setup/changes-to-visual-studio-15-setup/)
* [Spuštění sady Visual Studio pomocí DTE](launch-visual-studio-dte.md)