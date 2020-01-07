---
title: Vytvořit zástupné procedury metody testování částí
ms.date: 04/01/2019
ms.topic: conceptual
helpviewer_keywords:
- unit testing, create unit tests
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3c562d6f750db7096e37b863c46d6330eb484912
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75588821"
---
# <a name="create-unit-test-method-stubs-with-the-create-unit-tests-command"></a>Vytvořte zástupné procedury metody testování částí pomocí příkazu vytvořit testy jednotek.

Příkaz **vytvořit testy jednotek** vytvoří zástupné procedury metody testování částí. Tato funkce umožňuje snadnou konfiguraci testovacího projektu, testovací třídy a zástupné procedury testovací metody v rámci ní.

> [!NOTE]
> Příkaz nabídky **vytvořit testy jednotek** je k dispozici pouze pro spravovaný kód, který cílí na .NET Framework (ale ne .NET Core).

Příkaz nabídky **vytvořit testy jednotek** je rozšiřitelný a lze ho použít ke generování testů pro MSTest, MSTest v2, nunit a xUnit.

## <a name="get-started"></a>Začínáme

Chcete-li začít, vyberte metodu, typ nebo obor názvů v editoru kódu v projektu, který chcete otestovat, klikněte pravým tlačítkem myši a zvolte možnost **vytvořit testy jednotek**. Otevře se dialogové okno **vytvořit testy jednotek** , kde můžete nakonfigurovat, jak se mají testy vytvářet.

![Použití příkazu vytvořit testy jednotek](media/createunittestcommand.png)

## <a name="set-unit-test-traits"></a>Nastavit vlastnosti testu jednotek

Pokud plánujete spustit tyto testy jako součást procesu automatizace testů, můžete zvážit, že je test vytvořen v jiném testovacím projektu (druhá možnost v dialogovém okně výše) a nastavení vlastností testu jednotek pro test jednotky. To vám umožní snadněji zahrnout nebo vyloučit tyto konkrétní testy jako součást kanálu průběžné integrace nebo průběžného nasazování. Vlastnosti jsou nastaveny přidáním metadat přímo do testu jednotky, jak je znázorněno níže.

![Nastavení vlastností testu jednotek](media/createunittest.png)

## <a name="use-third-party-unit-test-frameworks"></a>Použít rozhraní pro testování částí třetích stran

Chcete-li automaticky generovat testy jednotek pro NUnit nebo xUnit, nainstalujte jedno z těchto rozšíření testovacího rozhraní z Visual Studio Marketplace:

* [Rozšíření NUnit pro generátory testů](https://marketplace.visualstudio.com/items?itemName=NUnitDevelopers.TestGeneratorNUnitextension)
* [rozšíření xUnit.net pro generátory testů](https://marketplace.visualstudio.com/items?itemName=BradWilson.xUnitnetTestExtensions)

## <a name="when-should-i-use-this-feature"></a>Kdy mám použít tuto funkci?

Tuto funkci použijte vždy, když potřebujete vytvořit testy jednotek, ale konkrétně při testování stávajícího kódu, který má málo nebo žádné pokrytí testu, a není k dispozici žádná dokumentace. Jinými slovy, kde je omezená nebo neexistující specifikace kódu. To efektivně implementuje přístup podobně jako [inteligentní testy jednotek](https://devblogs.microsoft.com/devops/introducing-smart-unit-tests/) , které charakterizují pozorované chování kódu.

Tato funkce je však stejně platná v případě, že vývojář začne psát kód a následně používá ke spuštění testů jednotek. V rámci toku kódování může vývojář chtít rychle vytvořit zástupnou proceduru metody testování částí (s vhodnou testovací třídou a vhodným testovacím projektem) pro konkrétní část kódu.

## <a name="see-also"></a>Viz také:

- [Vytváření zástupných procedur v metodě testování částí pomocí příkazu "vytvořit testy jednotek"](https://devblogs.microsoft.com/devops/creating-unit-test-method-stubs-with-create-unit-tests/)
- [Příspěvky v blogu testování částí](https://devblogs.microsoft.com/devops/?s=unit+testing)
