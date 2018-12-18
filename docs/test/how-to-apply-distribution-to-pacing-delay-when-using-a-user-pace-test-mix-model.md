---
title: Použít rozdělení na zpoždění stimulace pro zátěžové testování
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, test mix model
ms.assetid: ae8b35f9-d465-4d72-8d7d-7b56ae6ffd22
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 19634186e13574c322c2e9bcc636dda3a823b158
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2018
ms.locfileid: "52896186"
---
# <a name="how-to-apply-distribution-to-pacing-delay-for-a-user-pace-test-mix-model"></a>Postupy: použít rozdělení na zpoždění pro kroku model kombinace testů uživatele stimulace

Po vytvoření zátěžového testu s použitím **nového Průvodce zátěžovým testem**, chcete-li změnit vlastnosti ve scénáři podle potřebám a cílům testování můžete použít Editor zátěžového testu.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

**Použít rozdělení na zpoždění stimulace** je nastavena pomocí **vlastnosti** okna. Vlastnosti scénáře zátěžového testu se upravit pomocí editoru zátěžových testů.

> [!NOTE]
> **Použít rozdělení na zpoždění stimulace** vlastnost se projeví pouze v případě *načíst poměru testů* je nakonfigurovaný založený na kroku uživatele. Další informace najdete v tématu [úpravy modelů kombinací testů a určení pravděpodobnosti, že virtuální uživatel spustí test](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md).

Hodnota **použít rozdělení na zpoždění stimulace** lze nastavit na hodnotu true nebo false:

- **True**: Tento scénář platí normální statistické rozložení zpoždění, která jsou určena podle hodnoty v **testů na uživatele za hodinu** sloupec **upravit kombinaci testů** dialogové okno. Další informace najdete v tématu [úpravy modelů kombinací testů a určení pravděpodobnosti, že virtuální uživatel spustí test](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md).

     Předpokládejme například, že máte **testů na uživatele za hodinu** hodnotu **upravit kombinaci testů** dialogové okno pro test nastavena na dva uživatele za hodinu. Pokud **použít rozdělení na zpoždění stimulace** je nastavena na **True**, normální statistické rozdělení se použije na čekací dobu mezi testy. Testy budou stále spuštěny dva testy za hodinu, ale nemusí být nutně 30 minut, než mezi nimi. První test spustit až čtyři minuty a druhý test za 45 minut.

- **False**: testy spuštěny tempem, které jste zadali pro hodnotu v **testů na uživatele za hodinu** sloupec **upravit kombinaci testů** dialogové okno. Další informace najdete v tématu [úpravy modelů kombinací testů a určení pravděpodobnosti, že virtuální uživatel spustí test](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md).

     Předpokládejme například, že máte **testů na uživatele za hodinu** hodnotu **upravit kombinaci testů** dialogové okno pro test nastavena na dva uživatele za hodinu. Pokud **použít rozdělení na zpoždění stimulace** je nastavena na **False**, udělujete žádné volnost při spuštění testů. Test se spouští každých 30 minut. Tím zajistíte, že provést dva testy za hodinu.

## <a name="to-specify-the-apply-distribution-to-pacing-delay-property-setting-for-a-scenario"></a>Chcete-li určit použít rozdělení na zpoždění stimulace vlastnosti pro scénář

1. Otevřete zátěžový test.

   **Editoru zátěžových testů** se zobrazí. Zobrazí se strom zátěžového testu.

2. V **scénáře** složky strom zátěžového testu, vyberte uzel scénář, který chcete použít nemusely rozdělení na.

3. Na **zobrazení** nabídce vyberte možnost **okno vlastností**.

   Kategorie a vlastnosti scénáře jsou zobrazeny v **vlastnosti** okna.

4. V hodnotě vlastnosti pro **použít rozdělení na zpoždění stimulace**, vyberte buď **True** nebo **False**.

5. Vyberte **souboru** > **Uložit**. Teď můžete spustit zátěžový test pomocí nového **použít rozdělení na zpoždění stimulace** hodnotu.

## <a name="see-also"></a>Viz také:

- [Úpravy scénářů zátěžových testů](../test/edit-load-test-scenarios.md)
- [Návod: Vytvoření a spuštění zátěžového testu](../test/walkthrough-create-and-run-a-load-test.md)
- [Kontrolery testů a testovací agenti](configure-test-agents-and-controllers-for-load-tests.md)
- [Vlastnosti scénáře zátěžového testu](../test/load-test-scenario-properties.md)