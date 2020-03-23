---
title: Vytvořit zástupné procedury testovací metody
ms.date: 04/01/2019
ms.topic: conceptual
helpviewer_keywords:
- unit testing, create unit tests
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3eb001d2022bb57981f21fd99c051c54aeb08301
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75844321"
---
# <a name="create-unit-test-method-stubs-with-the-create-unit-tests-command"></a>Vytvoření zástupů testovací metody jednotky pomocí příkazu Vytvořit testy jednotek

Příkaz **Vytvořit testy částí** vytvoří zástupné procedury zkušební metody jednotky. Tato funkce umožňuje snadnou konfiguraci testovacího projektu, testovací třídy a zkušební metody se zakázaným inzerováním v něm.

::: moniker range="vs-2017"
> [!NOTE]
> Příkaz **příkazu Vytvořit testy jednotek** je k dispozici pouze pro spravovaný kód, který cílí na rozhraní .NET Framework (ale ne na jádro .NET).
::: moniker-end
::: moniker range=">=vs-2019"
> [!NOTE]
> Příkaz **Nabídky Vytvořit testy jednotek** je k dispozici pouze pro spravovaný kód.
::: moniker-end

Příkaz **příkazu Vytvořit testy částí** je rozšiřitelný a lze jej použít ke generování testů pro MSTest, MSTest V2, NUnit a xUnit.

## <a name="get-started"></a>Začínáme

Chcete-li začít, vyberte metodu, typ nebo obor názvů v editoru kódu v projektu, který chcete testovat, klepněte pravým tlačítkem myši a pak zvolte **Vytvořit testy částí**. Otevře se dialogové okno **Vytvořit testy částí,** kde můžete nakonfigurovat způsob vytvoření testů.

![Použití příkazu Vytvořit testy jednotek](media/createunittestcommand.png)

## <a name="set-unit-test-traits"></a>Nastavení vlastností testování částí

Pokud plánujete spustit tyto testy jako součást procesu automatizace testu, můžete zvážit vytvoření testu v jiném testovacím projektu (druhá možnost v dialogovém okně výše) a nastavení testovacích vlastností částí pro testování částí. To umožňuje snadněji zahrnout nebo vyloučit tyto konkrétní testy jako součást průběžné integrace nebo průběžné ho nasazení kanálu. Vlastnosti jsou nastaveny přidáním metadat do testování částí přímo, jak je znázorněno níže.

![Nastavení testovacích znaků jednotky](media/createunittest.png)

## <a name="use-third-party-unit-test-frameworks"></a>Použití rozhraní testování částí jiných výrobců

Chcete-li automaticky generovat testy částí pro NUnit nebo xUnit, nainstalujte jedno z těchto rozšíření testovacího rozhraní z webu Visual Studio Marketplace:

* [NUnit rozšíření pro testovací generátory](https://marketplace.visualstudio.com/items?itemName=NUnitDevelopers.TestGeneratorNUnitextension)
* [rozšíření xUnit.net pro zkušební generátory](https://marketplace.visualstudio.com/items?itemName=BradWilson.xUnitnetTestExtensions)

## <a name="when-should-i-use-this-feature"></a>Kdy mám tuto funkci používat?

Tuto funkci použijte vždy, když potřebujete vytvořit testy částí, ale konkrétně při testování existujícího kódu, který má malé nebo žádné pokrytí testem a žádnou dokumentaci. Jinými slovy, pokud existuje omezená nebo neexistující specifikace kódu. Účinně implementuje přístup podobný [testům inteligentní jednotky,](https://devblogs.microsoft.com/devops/introducing-smart-unit-tests/) který charakterizuje pozorované chování kódu.

Tato funkce je však stejně použitelná, když vývojář spustí psaní některých kódů a pak ji použije k zaváděcím testům jednotek. V rámci toku kódování může vývojář chtít rychle vytvořit zkušební metodu jednotky se zakázaným inzerováním (s vhodnou testovací třídou a vhodným testovacím projektem) pro konkrétní část kódu.

## <a name="see-also"></a>Viz také

- [Vytváření testovacích metod jednotek se zakázanými kódy s "Vytvořit testy částí"](https://devblogs.microsoft.com/devops/creating-unit-test-method-stubs-with-create-unit-tests/)
- [Příspěvky blogu testování částí](https://devblogs.microsoft.com/devops/?s=unit+testing)
