---
title: Úpravy modelů kombinace textu
description: Přečtěte si, jak model kombinace testů umožňuje mít několik pracovních postupů, které přesněji blíží způsob, jakým uživatelé pracují s vašimi aplikacemi.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, scenarios
- load tests, virtual users
ms.assetid: e3b7d952-9012-400a-8131-3444390a6066
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0d95eee8dd4e49e74b9bafd048e3f672fe560c68
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2020
ms.locfileid: "95441362"
---
# <a name="edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test"></a>Úprava modelů kombinace testů pro určení pravděpodobnosti, že virtuální uživatel spustí test

*Model kombinace testů* určuje pravděpodobnost, že virtuální uživatel spustí daný test ve scénáři zátěžového testu. To vám umožní simulovat zatížení realističtějším způsobem. Místo toho, abyste měli v rámci svých aplikací pouze jeden pracovní postup, můžete mít několik pracovních postupů, což je bližší odhad toho, jak koncoví uživatelé pracují s vašimi aplikacemi.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="test-mix-model-options"></a>Možnosti modelu kombinace testů

Pro scénář zátěžového testu můžete zadat jednu z následujících možností modelu kombinace testů:

- **Na základě celkového počtu testů:** Určuje, který webový výkon nebo test jednotek se spustí, když virtuální uživatel spustí iteraci testu. Na konci zátěžového testu odpovídá počet, kolikrát byl konkrétní test spuštěn, shodný s přiřazenou distribucí testu. Tento model kombinace testů použijte, když vytváříte kombinaci testů v procentech transakcí v protokolu služby IIS nebo v provozních datech.

- **Na základě počtu virtuálních uživatelů:** Určuje procentuální podíl virtuálních uživatelů, kteří spustí určitý webový výkon nebo test jednotky. V jakémkoli bodě zátěžového testu odpovídá počet uživatelů, kteří spouštějí určitý test, přiřazenému rozdělení. Tento model kombinace testů použijte, když vytváříte kombinaci testů na procentu uživatelů, kteří spouštějí určitý test.

- **Podle tempa uživatele:** V průběhu zátěžového testu každý test výkonnosti webu nebo test jednotky spustí určitý počet opakování na uživatele za hodinu. Tento model kombinace testů použijte, pokud chcete, aby virtuální uživatelé spouštěli test s použitím určitého tempa v průběhu zátěžového testu.

- **Na základě sekvenčního pořadí:** Každý virtuální uživatel spouští testy webového výkonu nebo jednotek v pořadí, ve kterém jsou testy definovány ve scénáři. Virtuální uživatel pokračuje v provádění testů v tomto pořadí, dokud není dokončen zátěžový test.

## <a name="tasks"></a>Úlohy

|Úlohy|Související témata|
|-|-----------------------|
|**Zadání kombinace testů pro zátěžový test:** Když vytvoříte zátěžový test, zadáte nastavení pro zátěžový test v **novém Průvodce zátěžovým testem**. V **novém Průvodce zátěžovým testem** zvolíte existující testy webu a jednotky, které chcete přidat do prvotního scénáře. Po přidání testů do scénáře zadáte kombinaci testů pro daný scénář.<br /><br /> K přesnější předpovědi očekávaného reálného využití webu nebo aplikace, které provádíte testování, použijete možnosti modelu zatížení. Je důležité to udělat, protože zátěžový test, který není založen na přesný model zatížení, může generovat zavádějící výsledky.|-   [Emulace očekávaného reálného využití webu nebo aplikace](../test/emulate-real-world-usage-of-a-web-site-in-a-load-test-using-test-mix-models.md)|
|**Upravit model kombinace testů:** Scénář zátěžového testu můžete změnit tak, aby používal jeden z modelů kombinace testů pomocí **Editor zátěžového testu**.||
|**Konfigurace zpoždění stimulace pro model kombinace testů pro uživatele tempa:** Pokud je váš scénář zátěžového testu nakonfigurován tak, aby používal **model kombinace testů tempa uživatele**, můžete určit, jak chcete nakonfigurovat zpoždění distribuce stimulace.|-   [Postupy: použití distribuce na zpoždění stimulace při použití modelu kombinace testů tempa uživatele](../test/how-to-apply-distribution-to-pacing-delay-when-using-a-user-pace-test-mix-model.md)|

## <a name="change-the-test-mix-model-in-a-scenario"></a>Změna modelu kombinace testů ve scénáři

Po vytvoření zátěžového testu pomocí **nového Průvodce zátěžovým testem** můžete pomocí **Editor zátěžového testu** změnit vlastnosti scénářů tak, aby vyhovovaly vašim požadavkům na testování a cílům.

> [!NOTE]
> Úplný seznam vlastností nastavení zatížení a jejich popis naleznete v tématu [Vlastnosti scénáře zátěžového testu](../test/load-test-scenario-properties.md).

Pomocí **Editor zátěžového testu** můžete změnit model kombinace testů ve scénáři zátěžového testu úpravou vlastnosti **typ kombinace testů** v okně **vlastnosti** .

### <a name="to-change-the-test-mix-model"></a>Změna modelu kombinace testů

1. Otevřete zátěžový test.

     Zobrazí se **Editor zátěžového testu** . Zobrazí se strom zátěžového testu.

2. Ve složce *scénáře* ve stromu zátěžového testu zvolte uzel scénáře, pro který chcete zadat maximální počet iterací testu.

3. V nabídce **zobrazení** vyberte **okno Vlastnosti**.

     Zobrazí se kategorie a vlastnosti scénáře.

4. V vlastnosti **typ kombinace testů** klikněte na tlačítko se třemi tečkami ( **...**).

     Zobrazí se dialogové okno **Upravit kombinaci testů** .

5. Zvolte rozevírací seznam v části **model kombinace testů** a vyberte model kombinace testů, který chcete použít pro scénář.

6. Volitelné Upravte kombinaci testů pomocí tlačítek **Přidat**, **Odebrat** a **distribuovat** a posuvníky distribuce. Další informace naleznete v tématu [Úprava kombinace testů a určení, které testy mají být zahrnuty do scénáře zátěžového testu](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md).

7. Volitelné Určete webový výkon a test jednotky pro inicializaci nebo ukončení pomocí zaškrtávacích políček a výběr požadovaných testů. Další informace najdete v tématu [emulace očekávaného reálného využití webu nebo aplikace](../test/emulate-real-world-usage-of-a-web-site-in-a-load-test-using-test-mix-models.md).

8. Vyberte **OK**.

     V okně **vlastnosti** se zobrazí nový model kombinace testů pro vlastnost **typ** poměru testů.

9. Po změně vlastnosti klikněte na možnost **Uložit** v nabídce **soubor** . Pak můžete spustit zátěžový test pomocí nové hodnoty **typu kombinace testů** .

## <a name="see-also"></a>Viz také

- [Upravit scénáře zátěžového testu](../test/edit-load-test-scenarios.md)
- [Vlastnosti scénáře zátěžového testu](../test/load-test-scenario-properties.md)
