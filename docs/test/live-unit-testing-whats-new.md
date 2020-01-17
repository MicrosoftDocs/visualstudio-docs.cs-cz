---
title: Co je nového v Live Unit Testing v aplikaci Visual Studio 2017
titleSuffix: ''
ms.date: 10/11/2017
ms.topic: conceptual
helpviewer_keywords:
- Live Unit Testing
- Live Unit Testing What's New
author: mikejo5000
ms.author: mikejo
ms.workload:
- dotnet
monikerRange: vs-2017
ms.openlocfilehash: 7f7ab0c257bfed4521e95d9da12eaa0b9e25a71e
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2020
ms.locfileid: "76114270"
---
# <a name="whats-new-in-live-unit-testing-for-visual-studio-2017"></a>Co je nového v Live Unit Testing pro Visual Studio 2017

Toto téma obsahuje seznam nových funkcí přidaných do Live Unit Testing v každé verzi sady Visual Studio počínaje verzí Visual Studio 2017 verze 15,3. Přehled použití Live Unit Testing naleznete v tématu [Live Unit Testing se sadou Visual Studio](live-unit-testing.md).

## <a name="version-154"></a>Verze 15,4

Počínaje verzí Visual Studio 2017 verze 15,4 Live Unit Testing obsahuje vylepšení a vylepšení v různých oblastech:

- **Vylepšení zjistitelnosti**. Pro uživatele, kteří neví, že existuje funkce Live Unit Testing, se v integrovaném vývojovém prostředí sady Visual Studio zobrazí zlatý pruh, který označuje Live Unit Testing pokaždé, když uživatel otevře řešení, které zahrnuje testy jednotek, ale Live Unit Testing není povolené. Informace zobrazené na zlatým panelu umožňují uživateli získat další informace o Live Unit Testing a jeho povolení. Zlatý pruh také zobrazuje informace, když Live Unit Testing požadavky nejsou splněny. Zde jsou některé z nich:

  - Testovací adaptéry chybí.
  - K dispozici jsou starší verze testovacích adaptérů.
  - Je potřeba obnovit balíčky NuGet, na které se odkazuje řešení.

- **Integrace s oznámeními centra úloh**. Integrované vývojové prostředí (IDE) sady Visual Studio teď zobrazuje Live Unit Testing oznámení o zpracování na pozadí v centru úloh, aby uživatelé mohli snadno zjistit, co se děje, když je Live Unit Testing povolený. To řeší klíčovou potíž spuštění Live Unit Testing ve velkém řešení. Předtím, než se na ikonu pokrytí objevily ikony pokrytí, nemohli uživatelé určit, jestli je Live Unit Testing skutečně povolená a jestli fungovala. Již není!

- **Podpora rozhraní MSTest Framework verze 1**: Live Unit Testing již pracuje se třemi oblíbenými architekturami testování částí: XUnit, nunit a MSTest. Dříve Live Unit Testing pracovali pouze v případě, že projekty testů jednotek MSTest používají MS test verze 2. Počínaje verzí Visual Studio 2017 verze 15,4 teď podporuje i MSTest verze 1.

- **Spolehlivost & výkon**: Live Unit Testing nyní zajišťuje, že systém může lépe rozpoznat, kdy se projekty nedokončily úplně, a vyhnout se selhání Live Unit Testing. Vylepšení výkonu sestavení také vyhněte opětovnému vyhodnocování projektů MSBuild v případě, že systém ví, že se nic v souboru projektu nezměnilo.

- **Různá vylepšení uživatelského rozhraní**: možnost matoucí **živý test – zahrnout/vyloučit** z gesta pravého kliknutí byla přejmenována na **Live Unit Testing zahrnout/vyloučit**. Byla odstraněna možnost **obnovit vyčištění** v nabídce **test** > **Live Unit Testing** . Je teď dostupná výběrem **nástrojů** > možností > **Live Unit Testing** a výběrem **Možnosti** **Odstranit trvalá data**.

## <a name="version-153"></a>Verze 15,3

Počínaje sadou Visual Studio 2017 verze 15,3 Live Unit Testing vylepšení funkcí a vylepšení ve dvou hlavních oblastech:

- Podpora pro .NET Core a .NET Standard. Můžete použít Live Unit Testing pro .NET Core a .NET Standard řešení napsaná v C# nebo Visual Basic.

- Byl vylepšen výkon. Všimněte si, že výkon je výrazně rychlejší po prvním úplném sestavení a spuštění testů v rámci Live Unit Testing. Také si všimnete významného zlepšení výkonu při dalších spuštěních Live Unit Testing ve stejném řešení. Nyní zachováváme data vygenerovaná Live Unit Testing a co nejvíc znovu použijeme s aktuálními kontrolami.

Kromě těchto hlavních doplňků Live Unit Testing zahrnuje následující vylepšení:

- Nová ikona kádinky se teď používá k rozlišení testovací metody od běžných metod. Prázdná ikona kádinky indikuje, že konkrétní test není zahrnutý v Live Unit Testing.

- Když kliknete na testovací metodu z překryvného okna uživatelského rozhraní ikony Live Unit Testing, teď máte možnost ladit test přímo z tohoto kontextu v okně uživatelského rozhraní a bez nutnosti opustit Editor kódu. To je užitečné hlavně v případě, že se díváte na neúspěšný test.

- Do nástroje/Možnosti/Live Unit Testing/obecné bylo přidáno několik dalších konfigurovatelných možností. Můžete nastavit paměť, která se používá pro Live Unit Testing. Můžete také zadat cestu k souboru pro trvalá Live Unit Testing data pro otevřené řešení.

- V řádku nabídek test/Live Unit Testing bylo přidáno několik dalších položek nabídky. **Resetovat vyčistit** odstraní trvalá data a znovu ji vygeneruje. **Možnost** přejde na Nástroje/možnosti/Live Unit Testing/Obecné.

- Nyní můžete použít následující atributy k určení ve zdrojovém kódu, který chcete vyloučit cílené testovací metody z Live Unit Testing:

  - Pro xUnit: `[Trait("Category", "SkipWhenLiveUnitTesting")]`
  - Pro NUnit: `[Category("SkipWhenLiveUnitTesting")]`
  - Pro MSTest: `[TestCategory("SkipWhenLiveUnitTesting")]`

## <a name="see-also"></a>Viz také:

- [Představení funkce Live Unit Testing](live-unit-testing-intro.md)
- [Live Unit Testing se sadou Visual Studio](live-unit-testing.md)
