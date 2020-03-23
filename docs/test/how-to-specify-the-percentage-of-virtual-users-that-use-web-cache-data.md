---
title: 'Zátěžový test: Nastavení procenta virtuálního uživatele pomocí dat webové mezipaměti'
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, virtual users
ms.assetid: f66d5d43-4121-4487-b27f-d0a0baaf7601
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8cac3368d0f03c268e086cc8636f1175a15effdd
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "76113359"
---
# <a name="how-to-specify-the-percentage-of-virtual-users-that-use-web-cache-data"></a>Postup: Určení procenta virtuálních uživatelů, kteří používají data webové mezipaměti

Po vytvoření zátěžového testu pomocí **Průvodce novým zátěžovým testem**můžete pomocí **Editoru zátěžového testu**změnit vlastnosti scénářů tak, aby vyhovovaly vašim potřebám a cílům testování. Úplný seznam vlastností scénáře zátěžového testu a jejich popisy naleznete v tématu [Load test scenario properties](../test/load-test-scenario-properties.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

**Vlastnost Procento nových uživatelů** je nastavena v okně **Vlastnosti.** Vlastnosti scénáře zátěžového testu můžete upravit v **editoru zátěžového testu**.

**Vlastnost Procento nových uživatelů** ovlivňuje způsob, jakým zátěžový test simuluje ukládání do mezipaměti, které by bylo provedeno webovým prohlížečem. Ve výchozím nastavení je vlastnost **Procento nových uživatelů** nastavena na 0 %. Pokud je hodnota vlastnosti **Procento nových uživatelů** nastavena na 100 %, bude každý test výkonu webu spuštěný v zátěžovém testu považován za prvního uživatele webu, který nemá žádný obsah z webu v mezipaměti prohlížeče z předchozích návštěv. Proto jsou staženy všechny požadavky ve webovém testu, včetně všech závislých požadavků, jako jsou obrázky.

> [!NOTE]
> Pokud je stejný prostředek, který lze uložit do mezipaměti, požadován více než jednou ve webovém testu, požadavky se nestáhnou.

Pokud načítáte testování webu, který má významný počet uživatelů vrácení, u kterých je pravděpodobné, že budou mít obrázky a další obsah, který lze uložit do mezipaměti místně, pak nastavení 100 % pro **vlastnost Procento nových uživatelů** vygeneruje více požadavků na stažení, než by se stalo v reálném používání. V takovém případě byste měli odhadnout procento návštěv vašich webových stránek, které jsou od prvních uživatelů webu, a odpovídajícím způsobem nastavit **procento nových uživatelů.**

## <a name="to-specify-the-percentage-of-new-users-for-a-scenario"></a>Určení procenta nových uživatelů pro scénář

1. Otevřete zátěžový test.

     Zobrazí se **Editor zátěžového testu.** Zobrazí se strom zátěžového testu.

2. Ve **složce** Scénáře zátěžového testu zvolte uzel scénáře, pro který chcete změnit hodnotu procenta nového uživatele.

3. V nabídce **Zobrazení** vyberte **Okno vlastnosti**.

     Kategorie a vlastnosti scénáře jsou zobrazeny v okně **Vlastnosti.**

4. Nastavte hodnotu vlastnosti **Procento nových uživatelů** zadáním čísla pro procento nových uživatelů.

5. Po dokončení změny vlastnosti zvolte **Uložit** v nabídce **Soubor.** Potom můžete spustit zátěžový test pomocí nové hodnoty **Procento nových uživatelů.**

## <a name="see-also"></a>Viz také

- [Upravit scénáře zátěžového testu](../test/edit-load-test-scenarios.md)
- [Návod: Vytvoření a spuštění zátěžového testu](../test/walkthrough-create-and-run-a-load-test.md)
- [Kontrolery testů a testovací agenti](configure-test-agents-and-controllers-for-load-tests.md)
- [Vlastnosti scénáře zátěžového testu](../test/load-test-scenario-properties.md)
- [Úprava vzorů zatížení pro modelování aktivit virtuálních uživatelů](../test/edit-load-patterns-to-model-virtual-user-activities.md)
