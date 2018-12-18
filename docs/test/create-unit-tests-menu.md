---
title: Vytvoření zástupné procedury metodu testu jednotek
ms.date: 05/02/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- unit testing, create unit tests
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 55b6af26064edc3eecb942b70aa2b4f5bc5307fd
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/09/2018
ms.locfileid: "51296408"
---
# <a name="create-unit-test-method-stubs-with-the-create-unit-tests-command"></a>Metoda zástupné procedury s příkaz Vytvořit testy jednotek pro testování částí Create

Visual Studio **vytvořit testy jednotek** příkaz poskytuje možnost vytvořit jednotku zástupné procedury testovací metody. Tato funkce umožňuje snadno konfigurace testovacího projektu, testovací třídy a pahýl metody testu v rámci něj.

## <a name="availability-and-extensions"></a>Dostupnost a rozšíření

**Vytvořit testy jednotek** příkazu nabídky:

* Je k dispozici v Community, Professional a Enterprise edice sady Visual Studio 2015 a novější.

* Podporuje pouze kód jazyka C#, který cílí na .NET Framework.

* Je možné rozšířit a podporuje generování testů MSTest, nástroji MSTest V2, NUnit, xUnit formátu.

* Ještě není k dispozici v projektech .NET Core.

## <a name="get-started"></a>Začínáme

Abyste mohli začít, vyberte metodu, typ nebo obor názvů v editoru kódu v projektu, kterou chcete testovat, otevřete místní nabídku a zvolte **vytvořit testy jednotek**. **Vytvořit testy jednotek** otevře se dialogové okno, které je možné vybrat možnosti vytvoření nové jednotkové testy.

![Pomocí příkazu Vytvořit testy jednotek](media/createunittestcommand.png)

## <a name="setting-unit-test-traits"></a>Nastavení vlastností testu jednotek

Pokud budete chtít spustit tyto testy jako součást procesu automatizace testů, můžete zvážit s testů vytvořené v jiném projektu testu (druhá možnost v dialogovém okně výše) a vlastnosti pro test jednotek pro testování částí nastavení. To umožňuje snadněji zahrňte nebo vylučte tyto specifické testy jako součást průběžné integrace nebo průběžného nasazování kanálu. Rysy jsou nastavené tak, že přidáte metadat pro testování částí přímo, jak je znázorněno níže.

![Nastavení vlastností testu jednotek](media/createunittest.png)

## <a name="using-third-party-unit-test-frameworks"></a>Pomocí rozhraní pro testování jednotky třetí strany

Pomocí sady Visual Studio můžete snadno mít vytvořené pomocí libovolné rozhraní testování částí. Chcete-li nainstalovat další rozhraní pro testování:

1. Zvolte **nástroje** > **rozšíření a aktualizace**.
2. Rozbalte **Online** > **Visual Studio Marketplace** > **nástroje**a klikněte na tlačítko **testování**.

![Pomocí rozhraní pro testování třetích stran](media/createunittestfx.png)

Testovací rozhraní framework rozšíření jsou k dispozici v aplikaci Visual Studio Marketplace:

* [NUnit rozšíření pro generátory testu](https://marketplace.visualstudio.com/items?itemName=NUnitDevelopers.TestGeneratorNUnitextension)
* [rozšíření xUnit.net pro generátory testu](https://marketplace.visualstudio.com/items?itemName=BradWilson.xUnitnetTestExtensions)

## <a name="when-should-i-use-this-feature"></a>Kdy použít tuto funkci?

Tuto funkci použít vždy, když je potřeba vytvořit testy jednotek, ale specificky při testování existující kód, který má žádné nebo téměř žádné pokrytí testu a žádná dokumentace. Jinými slovy ve kterých je specifikace omezené nebo neexistující kódu. Efektivně implementuje podobný přístup [inteligentní testování částí](https://blogs.msdn.microsoft.com/devops/2014/11/19/introducing-smart-unit-tests/) , které charakterizují zjištěnou chování kódu.

Tato funkce je však vztahuje rovněž na situaci, kdy vývojář spustí napsáním nějakého kódu a, který používá ke spuštění testování disciplíny. Ve službě flow kódování může být vhodné Vývojář můžete rychle vytvořit jednotku testovací metoda zástupnou proceduru (s vhodné testovací třídy a vhodný testovacího projektu) pro konkrétní část kódu.

## <a name="see-also"></a>Viz také:

- [Vytvoření testu jednotek metoda zástupné procedury s "Vytvoření Unit Tests"](https://blogs.msdn.microsoft.com/devops/2015/03/06/creating-unit-test-method-stubs-with-create-unit-tests/)
- [Testování blogové příspěvky](https://blogs.msdn.microsoft.com/devops/?s=unit+testing)
