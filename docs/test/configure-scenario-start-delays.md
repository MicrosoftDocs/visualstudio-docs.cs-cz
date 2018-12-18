---
title: Konfigurace prodlevy spustit scénář pro zátěžové testování
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, scenarios, start delays
ms.assetid: 2f634fba-8dfa-4c7a-a8b9-be867b78d16a
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: e3c090fbcbc1a322574a5b0eca06ce917594348b
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2018
ms.locfileid: "52896546"
---
# <a name="configure-scenario-start-delays-in-load-tests"></a>Konfigurace zpoždění pro spuštění scénáře v zátěžových testech

Zadejte zpoždění před zahájením scénáře v zátěžovém testu pomocí editoru zátěžových testů a **vlastnosti** okna.

Například můžete chtít použít **zpoždění spuštění** vlastnost potřebujete jeden scénář pro zahájení výroby položek, které jiný scénář spotřebovává. Můžete pozdržet náročnou situaci povolení výrobního scénáře k naplnění nějaká data.

Dalším příkladem je, že může mít jeden scénář, který se spustí jenom v určité denní doby. Ano budete chtít zpoždění spuštění scénář nasimulovali.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="specify-the-delay-start-time-of-a-scenario"></a>Zadejte zpoždění spuštění scénáře

Můžete zadat zpoždění před zahájením scénáře v zátěžovém testu pomocí editoru zátěžových testů, chcete-li změnit **zpoždění spuštění** vlastnost **vlastnosti** okna.

> [!NOTE]
> Úplný seznam vlastnosti scénáře zátěžového testu a jejich popis najdete v tématu [vlastnosti scénáře zátěžového testu](../test/load-test-scenario-properties.md).

 Příklad instance, pokud chcete použít **zpoždění spuštění** vlastnost je, když potřebujete jeden scénář pro zahájení výroby položek, které jiný scénář spotřebovává. Můžete pozdržet náročnou situaci povolení výrobního scénáře k naplnění nějaká data.

 Dalším příkladem je, že může mít jeden scénář, který se spustí jenom v určité denní dobu. Proto budete chtít zpoždění spuštění scénář nasimulovali.

> [!NOTE]
> Úplný seznam vlastností parametrů spuštění a jejich popis najdete v tématu [vlastnosti scénáře zátěžového testu](../test/load-test-scenario-properties.md).

### <a name="to-specify-the-delay-start-time-for-a-scenario"></a>K určení zpoždění spuštění pro scénář

1. Otevřete zátěžový test.

     Zobrazí se Editor zátěžového testu. Zobrazí se strom zátěžového testu.

2. V zátěžového testu stromů **scénáře** složky, vyberte uzel scénáře, pro kterou chcete zadat čas zahájení zpoždění.

3. Na **zobrazení** nabídce vyberte možnost **okno vlastností**.

     Kategorie a vlastnosti scénáře jsou zobrazeny v **vlastnosti** okna.

4. V textovém poli pro **zpoždění spuštění** zadejte hodnotu času, který označuje dobu čekání po zátěžový test spustí před spuštěním scénáře při spuštění zátěžového testu.

    > [!NOTE]
    > Pokud hodnota **zakázat při zahřívání** pro tento scénář je nastavena na **True**, pak bude **zpoždění spuštění** hodnotu vlastnosti času se použije po zahřívání období. Můžete řídit, jaké scénáře jsou součástí zahřívání pomocí **zakázat při zahřívání** vlastnost scénář.

5. Po změně vlastnosti zvolte **Uložit** na **souboru** nabídky. Potom můžete spustit zátěžový test pomocí nového **zpoždění spuštění** hodnotu.

## <a name="enable-and-disable-whether-a-scenario-runs-during-the-warm-up-period"></a>Povolit nebo zakázat, zda se scénář spustí během doby zahřívání

**Zakázat při zahřívání** je nastavena pomocí **vlastnosti** okna. Úpravy vlastnosti scénáře zátěžového testu je nastavena pomocí editoru zátěžového testu.

 **Zakázat při zahřívání** vlastnost se používá k označení, zda tento scénář by měl spustit nebo nepoběží během doby zahřívání ve stanoveném **zpoždění spuštění** vlastnost. Další informace najdete v tématu z předchozího postupu [určení zpoždění spuštění scénáře](#specify-the-delay-start-time-of-a-scenario).

> [!NOTE]
> Úplný seznam vlastností parametrů spuštění a jejich popis najdete v části [vlastnosti scénáře zátěžového testu](../test/load-test-scenario-properties.md).

### <a name="to-enable-or-disable-the-warm-up-period-for-a-scenario"></a>K povolení nebo zakázání zahřívání pro scénář

1. Otevřete zátěžový test.

     **Editoru zátěžových testů** se zobrazí. Zobrazí se strom zátěžového testu.

2. V zátěžového testu stromů **scénáře** složky, vyberte uzel scénář, který chcete změnit chování zahřívání.

3. Na **zobrazení** nabídce vyberte možnost **okno vlastností**.

     Tento scénář kategorie a vlastnosti jsou zobrazeny v **vlastnosti** okna.

     V **zakázat při zahřívání** vlastnosti, vyberte buď **True** nebo **hodnotu False.**

4. Po dokončení změn vlastnosti, zvolte **Uložit** na **souboru** nabídky. Potom můžete spustit zátěžový test pomocí nového **zakázat při zahřívání** hodnotu.

## <a name="see-also"></a>Viz také:

- [Úpravy scénářů zátěžových testů](../test/edit-load-test-scenarios.md)
- [Konfigurace testovacích agentů a testovací kontrolery pro zátěžové testy](../test/configure-test-agents-and-controllers-for-load-tests.md)
- [Vlastnosti scénáře zátěžového testu](../test/load-test-scenario-properties.md)