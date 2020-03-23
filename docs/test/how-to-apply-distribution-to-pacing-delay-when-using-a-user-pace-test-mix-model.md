---
title: Použít distribuci na zpoždění převaděčů pro zátěžové testování
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, test mix model
ms.assetid: ae8b35f9-d465-4d72-8d7d-7b56ae6ffd22
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 953c1ac4cb6e0f87d2a36080cc751ea26f66d63e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "76114488"
---
# <a name="how-to-apply-distribution-to-pacing-delay-for-a-user-pace-test-mix-model"></a>Postup: Použití distribuce na zpoždění tempa pro model mixu testů tempa uživatele

Po vytvoření zátěžového testu pomocí **Průvodce novým zátěžovým testem**můžete pomocí Editoru zátěžového testu změnit vlastnosti scénáře tak, aby vyhovovaly vašim potřebám a cílům testování.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Vlastnost **Použít distribuci na zpoždění pacingu** je nastavena pomocí okna **Vlastnosti.** Vlastnosti scénáře zátěžového testu jsou změněny pomocí editoru zátěžového testu.

> [!NOTE]
> Vlastnost **Použít distribuci na zpoždění pacingu** platí pouze v případě, že je *nakonfigurována kombinace zátěžového testu* na základě tempa uživatele. Další informace naleznete [v tématu Úprava modelů kombinace textu k určení pravděpodobnosti virtuálního uživatele, který spouštěl test](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md).

Hodnotu pro **zpoždění použít distribuci na přecházení** dat lze nastavit na hodnotu true nebo false:

- **Pravda:** Scénář použije normální zpoždění statistické distribuce, které jsou určeny hodnotou ve **sloupci Testy na uživatele za hodinu** v dialogovém okně **Upravit kombinaci testů.** Další informace naleznete [v tématu Úprava modelů kombinace textu k určení pravděpodobnosti virtuálního uživatele, který spouštěl test](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md).

     Předpokládejme například, že máte **testy na uživatele za hodinu** hodnotu v **dialogovém** okně Upravit test mix pro testovací sadu na dva uživatele za hodinu. Pokud je vlastnost **Použít distribuci na zpoždění pacingu** nastavena na **hodnotu True**, použije se na čekací dobu mezi testy normální statistické rozdělení. Testy budou stále spuštěny dva testy za hodinu, ale nemusí být nutně 30 minut zpoždění mezi nimi. První test by mohl běžet po čtyřech minutách a druhý test po 45 minutách.

- **False**: Testy se spouštějí tempem, které jste zadali pro hodnotu ve **sloupci Testy na uživatele za hodinu** v dialogovém okně **Upravit kombinaci testů.** Další informace naleznete [v tématu Úprava modelů kombinace textu k určení pravděpodobnosti virtuálního uživatele, který spouštěl test](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md).

     Předpokládejme například, že máte **testy na uživatele za hodinu** hodnotu v **dialogovém** okně Upravit test mix pro testovací sadu na dva uživatele za hodinu. Pokud **je** vlastnost Použít distribuci na zpoždění funkce nastavena na **hodnotu False**, nedáváte při spuštění testů žádný prostor. Test bude spuštěn každých 30 minut. Tím zajistíte, že provedete dva testy za hodinu.

## <a name="to-specify-the-apply-distribution-to-pacing-delay-property-setting-for-a-scenario"></a>Určení nastavení vlastnosti Použít distribuci na zpoždění zpoždění pro scénář

1. Otevřete zátěžový test.

   Zobrazí se **Editor zátěžového testu.** Zobrazí se strom zátěžového testu.

2. Ve složce **Scénáře** stromu zátěžového testu vyberte uzel scénáře, na který chcete použít distribuci tempo.

3. V nabídce **Zobrazení** vyberte **Okno vlastnosti**.

   Kategorie a vlastnosti scénáře jsou zobrazeny v okně **Vlastnosti.**

4. V hodnotě vlastnosti **pro možnost Použít distribuci zpoždění při přecházení**vyberte možnost **True** nebo **False**.

5. Vyberte **Soubor** > **uložit**. Nyní můžete spustit zátěžový test s novou hodnotou **Použít distribuci na zpoždění.**

## <a name="see-also"></a>Viz také

- [Upravit scénáře zátěžového testu](../test/edit-load-test-scenarios.md)
- [Návod: Vytvoření a spuštění zátěžového testu](../test/walkthrough-create-and-run-a-load-test.md)
- [Kontrolery testů a testovací agenti](configure-test-agents-and-controllers-for-load-tests.md)
- [Vlastnosti scénáře zátěžového testu](../test/load-test-scenario-properties.md)
