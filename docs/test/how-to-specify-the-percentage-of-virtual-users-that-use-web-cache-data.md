---
title: 'Zátěžový test: nastavte procento virtuálních uživatelů pomocí dat webové mezipaměti'
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, virtual users
ms.assetid: f66d5d43-4121-4487-b27f-d0a0baaf7601
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8cac3368d0f03c268e086cc8636f1175a15effdd
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2020
ms.locfileid: "76113359"
---
# <a name="how-to-specify-the-percentage-of-virtual-users-that-use-web-cache-data"></a>Postupy: určení procentuální podíl virtuálních uživatelů, které používají data ve webové mezipaměti

Po vytvoření zátěžového testu pomocí **nového Průvodce zátěžovým testem**, můžete změnit vlastnosti scénářů pro splnění potřebám a cílům testování s použitím **editoru zátěžového testu**. Úplný seznam vlastnosti scénáře zátěžového testu a jejich popis najdete v tématu [vlastnosti scénáře zátěžového testu](../test/load-test-scenario-properties.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

**Procentuální podíl nových uživatelů** je nastavena **vlastnosti** okna. Upravit vlastnosti scénáře zátěžového testu v **editoru zátěžového testu**.

**Procentuální podíl nových uživatelů** vlastnost ovlivňuje způsob, ve kterém zátěžový test simuluje ukládání do mezipaměti, která by se provedla ve webovém prohlížeči. Ve výchozím nastavení **procentuální podíl nových uživatelů** je nastavena na 0 %. Pokud hodnota **procentuální podíl nových uživatelů** je nastavena na 100 %, každý test výkonnosti webu spuštění v rámci zátěžového testu se zachází stejně jako jste nový uživatel na web který nemá žádný obsah z webu do mezipaměti prohlížeče z předchozí návštěvě. Proto se stáhnou všechny požadavky do webového testu, všechny závislé požadavky, jako jsou obrázky, včetně.

> [!NOTE]
> Pokud stejný prostředek možné ukládat do mezipaměti se požaduje více než jednou v testu webu, se nestáhnou požadavky.

Pokud jsou zátěžové testy webu, který má velký počet návratový uživatelů, kteří mohou mít obrázky a další možné ukládat do mezipaměti obsah v místní mezipaměti, potom nastavení 100 % **procentuální podíl nových uživatelů** vlastnost bude generovat informace požadavků na stažení než by tomu bylo v využití z reálného světa. V takovém případě by měl odhadnou procento návštěvy vašeho webu, které jsou z první čas uživatelé tohoto webu a nastavte **procentuální podíl nových uživatelů** vlastnost odpovídajícím způsobem.

## <a name="to-specify-the-percentage-of-new-users-for-a-scenario"></a>K určení procentuální podíl nových uživatelů pro scénář

1. Otevřete zátěžový test.

     **Editoru zátěžových testů** se zobrazí. Zobrazí se strom zátěžového testu.

2. V zátěžového testu stromů **scénáře** složky, zvolte scénář uzel, který chcete změnit nové uživatele procentuální hodnotu.

3. Na **zobrazení** nabídce vyberte možnost **okno vlastností**.

     Tento scénář kategorie a vlastnosti jsou zobrazeny v **vlastnosti** okna.

4. Nastavte hodnotu **procento noví uživatelé** vlastnost tak, že zadáte číslo pro procentuální podíl nových uživatelů.

5. Po dokončení změn vlastnosti, zvolte **Uložit** na **souboru** nabídky. Potom můžete spustit zátěžový test pomocí nového **procento noví uživatelé** hodnotu.

## <a name="see-also"></a>Viz také:

- [Úpravy scénářů zátěžových testů](../test/edit-load-test-scenarios.md)
- [Návod: Vytvoření a spuštění zátěžového testu](../test/walkthrough-create-and-run-a-load-test.md)
- [Kontrolery testů a testovací agenti](configure-test-agents-and-controllers-for-load-tests.md)
- [Vlastnosti scénáře zátěžového testu](../test/load-test-scenario-properties.md)
- [Úpravy vzorů zatížení pro model aktivity virtuálního uživatele](../test/edit-load-patterns-to-model-virtual-user-activities.md)
