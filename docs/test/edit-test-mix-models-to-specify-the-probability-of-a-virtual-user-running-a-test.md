---
title: Úpravy modelů míchání textu
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, scenarios
- load tests, virtual users
ms.assetid: e3b7d952-9012-400a-8131-3444390a6066
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 62c817a2df6c56f70ab2217292feeb545cf66c85
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75593210"
---
# <a name="edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test"></a>Úprava modelů kombinace testů pro určení pravděpodobnosti spuštění testu virtuálním uživatelem

*Model kombinace testů* určuje pravděpodobnost, že virtuální uživatel spouštěný daný test ve scénáři zátěžového testu. To umožňuje simulovat zatížení realističtější. Místo toho, abyste měli pouze jeden pracovní postup prostřednictvím aplikací, můžete mít několik pracovních postupů, což je bližší aproximace toho, jak koncoví uživatelé interagují s vašimi aplikacemi.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="test-mix-model-options"></a>Možnosti modelu kombinace testů

Můžete zadat jednu z následujících možností modelu kombinace testů pro scénář zátěžového testu:

- **Na základě celkového počtu testů:** Určuje, který webový výkon nebo testování částí je spuštěno, když virtuální uživatel spustí iteraci testu. Na konci zátěžového testu počet spuštění konkrétního testu odpovídá přiřazené mu distribuce testu. Tento model kombinace testů použijte, pokud zakládáte kombinaci testů na procentech transakcí v protokolu iis nebo v produkčních datech.

- **Na základě počtu virtuálních uživatelů:** Určuje procento virtuálních uživatelů, kteří budou spouštět konkrétní webový výkon nebo testování částí. V libovolném bodě zátěžového testu počet uživatelů, kteří jsou spuštěny konkrétní test odpovídá přiřazené distribuce. Tento model kombinace testů použijte, pokud zakládáte kombinaci testů na procentu uživatelů, kteří spouštějí určitý test.

- **Na základě uživatelského tempa:** V průběhu zátěžového testu je každý test výkonu webu nebo test částí spuštěn zadaný počet časů na uživatele za hodinu. Tento model kombinace testů použijte, pokud chcete, aby virtuální uživatelé spouštěli test určitým tempem v průběhu zátěžového testu.

- **Na základě sekvenčního pořadí:** Každý virtuální uživatel spustí webové testy výkonu nebo jednotkových testů v pořadí, v jakém jsou testy definovány ve scénáři. Virtuální uživatel pokračuje v procházení testy v tomto pořadí, dokud není dokončen zátěžový test.

## <a name="tasks"></a>Úlohy

|Úlohy|Související témata|
|-|-----------------------|
|**Určení kombinace testů pro zátěžový test:** Při vytváření zátěžového testu zadáte nastavení zátěžového testu v **Průvodci novým zátěžového testu**. V **Průvodci novým zátěžového testu**zvolíte existující webové a jednotkové testy, které chcete přidat do počátečního scénáře. Po přidání testů do scénáře zadáte kombinaci testů pro scénář.<br /><br /> Pomocí možností modelování zatížení můžete přesněji předpovědět očekávané reálné využití webu nebo aplikace, které testujete zatížení. Je důležité to provést, protože zátěžový test, který není založen na přesném modelu zatížení, může generovat zavádějící výsledky.|-   [Emulujte očekávané reálné používání webových stránek nebo aplikací](../test/emulate-real-world-usage-of-a-web-site-in-a-load-test-using-test-mix-models.md)|
|**Upravit model kombinace testů:** Scénář zátěžového testu můžete změnit tak, aby používal jeden z modelů kombinace testů pomocí **Editoru zátěžového testu**.||
|**Nakonfigurujte zpoždění tempa pro model kombinace testů s tempem uživatele:** Pokud je váš scénář zátěžového testu nakonfigurován tak, aby používal **model Mix mixu testů tempa uživatele**, můžete určit, jak chcete nakonfigurovat zpoždění distribuce.|-   [Postup: Použití distribuce na zpoždění při použití modelu mixu testů tempa uživatele](../test/how-to-apply-distribution-to-pacing-delay-when-using-a-user-pace-test-mix-model.md)|

## <a name="change-the-test-mix-model-in-a-scenario"></a>Změna modelu kombinace testů ve scénáři

Po vytvoření zátěžového testu pomocí **Průvodce novým zátěžovými testy**můžete pomocí **Editoru zátěžového testu** změnit vlastnosti scénářů tak, aby vyhovovaly vašim potřebám a cílům testování.

> [!NOTE]
> Úplný seznam vlastností nastavení zatížení a jejich popisy naleznete v tématu [Load test scenario properties](../test/load-test-scenario-properties.md).

Pomocí **Editoru zátěžových testů**můžete změnit model kombinace testů ve scénáři zátěžového testu úpravou vlastnosti **Typ kombinace testů** v okně **Vlastnosti.**

### <a name="to-change-the-test-mix-model"></a>Změna modelu kombinace testů

1. Otevřete zátěžový test.

     Zobrazí se **Editor zátěžového testu.** Zobrazí se strom zátěžového testu.

2. Ve složce *Scénáře* stromu zátěžového testu zvolte uzel scénáře, pro který chcete zadat maximální počet iterací testu.

3. V nabídce **Zobrazení** vyberte **Okno vlastnosti**.

     Zobrazí se kategorie a vlastnosti scénáře.

4. Ve vlastnosti **Typ kombinace testů** zvolte tlačítko se třemi tečkami ( **...**).

     Zobrazí se dialogové okno **Upravit kombinaci testů.**

5. Vyberte rozevírací seznam v části **Model kombinace testů** a vyberte model kombinace testů, který chcete použít pro scénář.

6. (Nepovinné) Upravte testovací mix pomocí tlačítek **Přidat**, **Odebrat** a **Rozmístit** a distribučních posuvníků. Další informace naleznete [v tématu Úprava kombinace testů a určení, které testy mají být zahrnuty do scénáře zátěžového testu](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md).

7. (Nepovinné) Zadejte webový výkon a testování částí, které chcete inicializovat nebo ukončit, pomocí zaškrtávacích políček a výběrem požadovaných testů. Další informace naleznete [v tématu Emulate očekávané reálné využití webu nebo aplikace](../test/emulate-real-world-usage-of-a-web-site-in-a-load-test-using-test-mix-models.md).

8. Vyberte **OK**.

     Okno **Vlastnosti** zobrazí nový model kombinace testů pro vlastnost **Typ kombinace testů.**

9. Po změně vlastnosti zvolte **Uložit** v nabídce **Soubor.** Potom můžete spustit zátěžový test pomocí nové hodnoty **Test Mix Type.**

## <a name="see-also"></a>Viz také

- [Upravit scénáře zátěžového testu](../test/edit-load-test-scenarios.md)
- [Vlastnosti scénáře zátěžového testu](../test/load-test-scenario-properties.md)
