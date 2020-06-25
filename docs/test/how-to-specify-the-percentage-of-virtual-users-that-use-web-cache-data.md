---
title: 'Zátěžový test: nastavte procento virtuálních uživatelů pomocí dat webové mezipaměti'
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, virtual users
ms.assetid: f66d5d43-4121-4487-b27f-d0a0baaf7601
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0a31ea50cdedbeb825d03de38a89200b6e8e5200
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85287399"
---
# <a name="how-to-specify-the-percentage-of-virtual-users-that-use-web-cache-data"></a>Postupy: určení procenta virtuálních uživatelů, kteří používají data mezipaměti webu

Po vytvoření zátěžového testu pomocí **nového Průvodce zátěžovým testem**můžete změnit vlastnosti scénářů tak, aby splňovaly potřeby testování a cíle pomocí **Editor zátěžového testu**. Úplný seznam vlastností scénáře zátěžového testu a jejich popis naleznete v tématu [Vlastnosti scénáře zátěžového testu](../test/load-test-scenario-properties.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

V okně **vlastnosti** je nastavená **procentuální hodnota vlastnosti New Users** . Vlastnosti scénáře zátěžového testu upravíte v **Editor zátěžového testu**.

**Procentuální hodnota vlastnosti New Users** ovlivňuje způsob, jakým zátěžový test simuluje ukládání do mezipaměti, které by prováděl webový prohlížeč. Ve výchozím nastavení je **procento nových uživatelských** vlastností nastaveno na 0%. Pokud je hodnota vlastnosti **procento nových uživatelů** nastavena na 100%, každý test výkonnosti webu v rámci zátěžového testu se považuje za prvního uživatele, který nemá žádný obsah z webové stránky v mezipaměti prohlížeče z předchozích návštěv. Proto se stáhnou všechny požadavky v rámci webového testu včetně všech závislých požadavků, jako jsou obrázky.

> [!NOTE]
> Pokud se stejný prostředek v mezipaměti požaduje více než jednou v rámci webového testu, požadavky se nestáhnou.

Pokud zátěž testujete na webu, který má velký počet vrácených uživatelů, kteří budou mít obrázky, a další obsah uložený v mezipaměti v místním počítači, pak nastavení 100% pro **procento nových uživatelů** vygeneruje více požadavků na stažení, než by se mohlo stát při použití reálného světa. V takovém případě byste měli odhadnout procento návštěv na webu, které se poprvé vystavili uživatelům webu, a odpovídajícím způsobem nastavit **procento nových vlastností uživatelů** .

## <a name="to-specify-the-percentage-of-new-users-for-a-scenario"></a>Určení procenta nových uživatelů pro scénář

1. Otevřete zátěžový test.

     Zobrazí se **Editor zátěžového testu** . Zobrazí se strom zátěžového testu.

2. Ve složce **scénáře** stromů zátěžového testu vyberte uzel scénář, pro který chcete změnit procentuální hodnotu nového uživatele pro.

3. V nabídce **zobrazení** vyberte **okno Vlastnosti**.

     Kategorie a vlastnosti scénáře se zobrazí v okně **vlastnosti** .

4. Zadáním čísla pro procento nových uživatelů nastavte hodnotu vlastnosti **procento nových uživatelů** .

5. Po dokončení změny vlastnosti vyberte v nabídce **soubor** možnost **Uložit** . Pak můžete spustit zátěžový test s použitím nového **procenta hodnoty nových uživatelů** .

## <a name="see-also"></a>Viz také

- [Upravit scénáře zátěžového testu](../test/edit-load-test-scenarios.md)
- [Návod: Vytvoření a spuštění zátěžového testu](../test/walkthrough-create-and-run-a-load-test.md)
- [Kontrolery testů a testovací agenti](configure-test-agents-and-controllers-for-load-tests.md)
- [Vlastnosti scénáře zátěžového testu](../test/load-test-scenario-properties.md)
- [Úprava vzorů zatížení pro modelování aktivit virtuálních uživatelů](../test/edit-load-patterns-to-model-virtual-user-activities.md)
