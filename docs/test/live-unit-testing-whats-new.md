---
title: Co je nového v testování živých částí v Sadě Visual Studio 2017
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "76114270"
---
# <a name="whats-new-in-live-unit-testing-for-visual-studio-2017"></a>Co je nového v živém testování částí pro Visual Studio 2017

Toto téma obsahuje seznam nových funkcí přidaných do živého testování částí v každé verzi sady Visual Studio počínaje Visual Studio 2017 verze 15.3. Přehled použití živého testování částí naleznete v tématu [Živé testování částí s visual studio](live-unit-testing.md).

## <a name="version-154"></a>Verze 15.4

Počínaje Visual Studio 2017 verze 15.4, live testování částí zahrnuje vylepšení a vylepšení v řadě oblastí:

- **Vylepšená zjistitelnost**. Pro uživatele, kteří nevědí, že funkce testování živých částí existuje, ide sady Visual Studio zobrazí zlatý pruh, který zmiňuje živé testování částí vždy, když uživatel otevře řešení, které zahrnuje testování částí, ale testování živých částí není povoleno. Informace uvedené ve zlaté liště umožňují uživateli dozvědět se více o testování živých částí a povolit je. Zlatý pruh také zobrazuje informace, když nejsou splněny požadavky testování živých částí. Mezi ně patří:

  - Testovací adaptéry chybí.
  - Starší verze testovacích adaptérů jsou k dispozici.
  - Obnovení Balíčky NuGet odkazuje řešení je potřeba.

- **Integrace s oznámeními Centra úloh**. Prostředí IDE sady Visual Studio nyní zobrazuje oznámení o zpracování živého testování částí na pozadí v Centru úloh, aby uživatelé mohli snadno zjistit, co se děje, když je povoleno testování živých částí. To řeší klíčový problém spuštění živého testování částí na velkém řešení. Dříve, po dobu několika minut, dokud se neobjevily ikony pokrytí, uživatelé nemohli určit, zda bylo testování živých částí skutečně povoleno a zda fungovalo. Teď už ne!

- **Podpora architektury MSTest verze 1**: Testování živých částí již funguje se třemi oblíbenými architekturami testování částí: xUnit, NUnit a MSTest. Dříve živé testování částí fungovalo pouze v případě, že projekty testování částí MSTest používaly test MS verze 2. Počínaje Visual Studio 2017 verze 15.4, nyní také podporuje MSTest verze 1 také.

- **Spolehlivost & výkon:** Testování živých částí nyní zajišťuje, že systém může lépe zjistit, kdy projekty plně nedokončily načítání a zabrání zhroucení testování živých částí. Sestavení vylepšení výkonu také vyhnout přehodnocení MSBuild projekty, když systém ví, že nic v souboru projektu se změnilo.

- **Různé upřesnění uživatelského rozhraní**: Matoucí **live test set - Zahrnout/ Vyloučit** možnost z gesta pravým tlačítkem myši byla přejmenována na **Živé testování částí Zahrnout/vyloučit**. Možnost **Obnovit čisté** v nabídce **Testování** > **živých částí** byla odebrána. Nyní je přístupný výběrem**možnosti** >  **nástroje** > **live testování částí** a výběrem odstranit **trvalá data**.

## <a name="version-153"></a>Verze 15.3

Počínaje Visual Studio 2017 verze 15.3, live testování částí funkce vylepšení a vylepšení ve dvou hlavních oblastech:

- Podpora pro .NET Core a .NET Standard. Živé testování částí můžete použít na .NET Core a .NET Standard řešení napsaná v jazyce C# nebo Visual Basic.

- Byl vylepšen výkon. Všimněte si, že výkon je výrazně rychlejší po prvním úplném sestavení a spuštění testů v rámci testování živých částí. Také si všimnete významné zlepšení výkonu v následných spuštěních testování živých částí na stejném řešení. Nyní uchováváme data generovaná živým testováním částí a co nejvíce je znovu používáme s aktuálními kontrolami.

Kromě těchto hlavních dodatků zahrnuje testování živých částí následující vylepšení:

- Nová ikona kádinky se nyní používá k odlišení zkušební metody od běžných metod. Prázdná ikona kádinky označuje, že konkrétní test není součástí testování živých částí.

- Při kliknutí na testovací metodu z okna automaticky otevíraného rozhraní ikony pokrytí živého testování částí máte nyní možnost ladit test přímo z tohoto kontextu v okně uhlavního rozhraní a bez nutnosti opustit editor kódu. To je užitečné zejména při pohledu na neúspěšný test.

- Do nástroje/možnosti/testování živých částí/obecné bylo přidáno několik dalších konfigurovatelných možností. Můžete završit paměť použitou pro živé testování částí. Můžete také určit cestu k souboru pro trvalá data živého testování částí pro otevřené řešení.

- Několik dalších položek nabídky byly přidány do řádku nabídek Test / Live Testování částí. **Obnovit čisté** odstraní trvalá data a znovu je vygeneruje. **Možnost** přeskočí na Nástroje/Možnosti/Testování živých částí/Obecné.

- Nyní můžete použít následující atributy k určení ve zdrojovém kódu, který chcete vyloučit cílené testovací metody z testování živých částí:

  - Pro xUnit:`[Trait("Category", "SkipWhenLiveUnitTesting")]`
  - Pro NUnit:`[Category("SkipWhenLiveUnitTesting")]`
  - Pro MSTest:`[TestCategory("SkipWhenLiveUnitTesting")]`

## <a name="see-also"></a>Viz také

- [Představení funkce Live Unit Testing](live-unit-testing-intro.md)
- [Živé testování částí pomocí sady Visual Studio](live-unit-testing.md)
