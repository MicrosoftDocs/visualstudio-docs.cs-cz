---
title: Vytvořit zástupné procedury metody testování částí
description: Naučte se používat příkaz vytvořit testy jednotek, který umožňuje snadnou konfiguraci testovacího projektu, testovací třídy a zástupné procedury testovací metody v ní.
ms.custom: SEO-VS-2020
ms.date: 04/24/2020
ms.topic: how-to
helpviewer_keywords:
- unit testing, create unit tests
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: fb30135ac5c137fdc836273855e2d9f000f1c6b2
ms.sourcegitcommit: 3a855d3513407ea78336386dc3be0b75142614b0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2021
ms.locfileid: "103622631"
---
# <a name="create-unit-test-method-stubs-from-code"></a>Vytvořit z kódu zástupné procedury metody testování částí

Příkaz **vytvořit testy jednotek** vytvoří zástupné procedury metody testování částí. Tato funkce umožňuje snadnou konfiguraci testovacího projektu, testovací třídy a zástupné procedury testovací metody v rámci ní.

::: moniker range="vs-2017"
> [!NOTE]
> Příkaz nabídky **vytvořit testy jednotek** je k dispozici pouze pro kód jazyka C#, který cílí na .NET Framework (ale ne .NET Core nebo .NET Standard).
::: moniker-end
::: moniker range=">=vs-2019"
> [!NOTE]
> Příkaz nabídky **vytvořit testy jednotek** je k dispozici pouze pro kód jazyka C#.
::: moniker-end

Příkaz nabídky **vytvořit testy jednotek** je rozšiřitelný a lze ho použít ke generování testů pro MSTest, MSTest v2, nunit a xUnit.

## <a name="get-started"></a>Začínáme

Chcete-li začít, vyberte metodu, typ nebo obor názvů v editoru kódu v projektu, který chcete otestovat, klikněte pravým tlačítkem myši a zvolte možnost **vytvořit testy jednotek**. Otevře se dialogové okno **vytvořit testy jednotek** , kde můžete nakonfigurovat, jak se mají testy vytvářet.

![Použití příkazu vytvořit testy jednotek](media/createunittestcommand.png)

Pokud nevidíte možnosti testovacího rozhraní pro NUnit nebo xUnit, přečtěte si téma [použití rozhraní pro testování částí třetích stran](#use-third-party-unit-test-frameworks).

## <a name="set-unit-test-traits"></a>Nastavit vlastnosti testu jednotek

Pokud plánujete spustit tyto testy jako součást procesu automatizace testů, můžete zvážit, že je test vytvořen v jiném testovacím projektu (druhá možnost v dialogovém okně výše) a nastavení vlastností testu jednotek pro test jednotky. To vám umožní snadněji zahrnout nebo vyloučit tyto konkrétní testy jako součást kanálu průběžné integrace nebo průběžného nasazování. Vlastnosti jsou nastaveny přidáním metadat přímo do testu jednotky, jak je znázorněno níže.

![Nastavení vlastností testu jednotek](media/createunittest.png)

## <a name="use-third-party-unit-test-frameworks"></a>Použít rozhraní pro testování částí třetích stran

Chcete-li automaticky generovat testy jednotek pro NUnit nebo xUnit, nainstalujte jedno z těchto rozšíření testovacího rozhraní z Visual Studio Marketplace:

* [Rozšíření NUnit pro generátory testů](https://marketplace.visualstudio.com/items?itemName=NUnitDevelopers.TestGeneratorNUnitextension)
* [rozšíření xUnit.net pro generátory testů](https://marketplace.visualstudio.com/items?itemName=YowkoTsai.xUnitnetTestGenerator)

## <a name="when-should-i-use-this-feature"></a>Kdy mám použít tuto funkci?

Tuto funkci použijte vždy, když potřebujete vytvořit testy jednotek, ale konkrétně při testování stávajícího kódu, který má málo nebo žádné pokrytí testu, a není k dispozici žádná dokumentace. Jinými slovy, kde je omezená nebo neexistující specifikace kódu. To efektivně implementuje přístup podobně jako [inteligentní testy jednotek](https://devblogs.microsoft.com/devops/introducing-smart-unit-tests/) , které charakterizují pozorované chování kódu.

Tato funkce je však stejně platná v případě, že vývojář začne psát kód a následně používá ke spuštění testů jednotek. V rámci toku kódování může vývojář chtít rychle vytvořit zástupnou proceduru metody testování částí (s vhodnou testovací třídou a vhodným testovacím projektem) pro konkrétní část kódu.

## <a name="see-also"></a>Viz také

- [Vytváření zástupných procedur v metodě testování částí pomocí příkazu "vytvořit testy jednotek"](https://devblogs.microsoft.com/devops/creating-unit-test-method-stubs-with-create-unit-tests/)
- [Příspěvky v blogu testování částí](https://devblogs.microsoft.com/devops/?s=unit+testing)
