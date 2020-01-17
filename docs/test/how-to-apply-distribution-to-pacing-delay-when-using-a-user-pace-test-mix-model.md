---
title: Použít distribuci na zpoždění stimulace pro zátěžové testování
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, test mix model
ms.assetid: ae8b35f9-d465-4d72-8d7d-7b56ae6ffd22
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 953c1ac4cb6e0f87d2a36080cc751ea26f66d63e
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2020
ms.locfileid: "76114488"
---
# <a name="how-to-apply-distribution-to-pacing-delay-for-a-user-pace-test-mix-model"></a>Postupy: použití distribuce na zpoždění stimulace pro model kombinace testů tempa uživatele

Po vytvoření zátěžového testu pomocí **nového Průvodce zátěžovým testem**můžete pomocí Editor zátěžového testu změnit vlastnosti scénáře tak, aby splňovaly potřeby testování a cíle.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Vlastnost **použít rozdělení do stimulace Delay** je nastavena pomocí okna **vlastnosti** . Vlastnosti scénáře zátěžového testu se upravují pomocí Editor zátěžového testu.

> [!NOTE]
> Vlastnost **použít distribuci do stimulace Delay** se vztahuje pouze v případě, že je *kombinace zátěžového testu* konfigurována na základě tempa uživatele. Další informace najdete v tématu [Úpravy modelů kombinace textu a určení pravděpodobnosti, že virtuální uživatel spustí test](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md).

Hodnotu pro **zpoždění použití rozdělení na stimulace** lze nastavit buď na hodnotu true, nebo na hodnotu false:

- **True**: scénář aplikuje normální statistické prodlevy, které jsou určené hodnotou ve sloupci **testy na uživatele za hodinu** v dialogovém okně **Upravit kombinaci testů** . Další informace najdete v tématu [Úpravy modelů kombinace textu a určení pravděpodobnosti, že virtuální uživatel spustí test](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md).

     Předpokládejme například, že máte **testy na hodnotu uživatel za hodinu** v dialogovém okně **Upravit kombinaci testů** pro sadu testů na dva uživatele za hodinu. Pokud je vlastnost **použít distribuci na stimulace Delay** nastavená na **hodnotu true**, použije se pro čekací dobu mezi testy normální statistická distribuce. Testy budou i nadále běžet dvakrát za hodinu, ale nemusí to nutně trvat 30 minut zpoždění. První test může běžet po čtyřech minutách a druhý test po 45 minutách.

- **False**: testy se spouští podle tempa, který jste zadali pro hodnotu ve sloupci **testy na uživatele za hodinu** v dialogovém okně **Upravit kombinaci testů** . Další informace najdete v tématu [Úpravy modelů kombinace textu a určení pravděpodobnosti, že virtuální uživatel spustí test](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md).

     Předpokládejme například, že máte **testy na hodnotu uživatel za hodinu** v dialogovém okně **Upravit kombinaci testů** pro sadu testů na dva uživatele za hodinu. Pokud je vlastnost **použít rozdělení na zpoždění stimulace** nastavena na **hodnotu false**, neposkytnete žádné Leeway při spuštění testů. Test se spustí každých 30 minut. Tím zajistíte, že spustíte dvě testy za hodinu.

## <a name="to-specify-the-apply-distribution-to-pacing-delay-property-setting-for-a-scenario"></a>Určení nastavení vlastnosti použít distribuci na zpoždění stimulace pro scénář

1. Otevřete zátěžový test.

   **Editoru zátěžových testů** se zobrazí. Zobrazí se strom zátěžového testu.

2. Ve složce **scénáře** ve stromové struktuře zátěžového testu vyberte uzel scénáře, pro který chcete stimulace distribuci použít.

3. Na **zobrazení** nabídce vyberte možnost **okno vlastností**.

   Kategorie a vlastnosti scénáře jsou zobrazeny v **vlastnosti** okna.

4. V hodnotě vlastnosti pro **zpoždění použít rozdělení na stimulace**vyberte **true** nebo **false**.

5. Vyberte **soubor** > **Uložit**. Nyní můžete spustit zátěžový test s novou hodnotou **zpoždění použít rozdělení na stimulace** .

## <a name="see-also"></a>Viz také:

- [Úpravy scénářů zátěžových testů](../test/edit-load-test-scenarios.md)
- [Návod: Vytvoření a spuštění zátěžového testu](../test/walkthrough-create-and-run-a-load-test.md)
- [Kontrolery testů a testovací agenti](configure-test-agents-and-controllers-for-load-tests.md)
- [Vlastnosti scénáře zátěžového testu](../test/load-test-scenario-properties.md)
