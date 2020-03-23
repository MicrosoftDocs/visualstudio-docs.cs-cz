---
title: 'Postupy: Výběr úložiště výsledků zátěžového testu'
ms.date: 10/19/2016
ms.topic: conceptual
f1_keywords:
- vs.test.load.dialog.connectstringmissing
- vs.test.load.dialog.databaseconnectstring
helpviewer_keywords:
- load tests, results repository
- results, load test
- load test results, repository
- Load Test Results Repository
- SQL, Load Test Results Store
ms.assetid: fa0c4dd9-612f-4a57-b8eb-458f129d9cda
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 513dd884f65e041e7ad90dda1483633fec57e100
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589003"
---
# <a name="how-to-select-a-load-test-results-repository"></a>Postup: Výběr úložiště výsledků zátěžového testu

Nejste omezeni na místní úložiště výsledků. Zátěžové testy jsou často spouštěny ve vzdálené sadě počítačů agenta. Agenty mohou spolu s kontrolérem generovat více simulované zátěže než jakýkoli jeden počítač. Další informace naleznete v [tématu Test řadiče a testovací agenti](configure-test-agents-and-controllers-for-load-tests.md).

Výsledky testů z vašich agentů nebo místního počítače lze uložit na libovolný server SQL, na kterém jste vytvořili úložiště výsledků zátěžového testu. V obou případech je nutné určit, kde chcete uložit výsledky zátěžového testu pomocí okna **Spravovat testovací řadiče.**

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="identify-a-results-store-for-load-test-data"></a>Identifikace úložiště výsledků pro data zátěžového testu

1. V **Průzkumníku řešení**otevřete soubor zátěžového testu.

2. Na panelu nástrojů **Zátěžový test** zvolte **Spravovat testovací řadiče**. Zobrazí se dialogové okno **Spravovat testovací řadič.** Používáte-li agent vzdáleně, je zapotřebí zvolit kontrolér.

     ![Výsledky zátěžových testů](../test/media/loadtestconnectionproperties.png) ukládají vlastnosti připojení Vlastnosti zátěžových testů ukládají vlastnosti připojení

3. V **úložišti výsledků zátěžového testu**zobrazte klepnutím na **tlačítko (...)** dialogové okno **Vlastnosti připojení.**

4. Do **pole Název serveru**zadejte název serveru, `LoadTest` na kterém jste skripty spouštěli.

    > [!TIP]
    > Pokud používáte SQL Express v místním počítači pro \<úložiště zátěžových testů, zadejte název_počítače>\sqlexpress (například **MyComputer\sqlexpress**).

5. V části **Přihlásit se k serveru**můžete zvolit **Použít ověřování systému Windows**. Můžete zadat uživatelské jméno a heslo, ale pokud tak učiníte, musíte vybrat možnost **Uložit heslo**.

6. V části **Připojit k databázi**zvolte **Vybrat nebo zadat název databáze**. V rozevíracím seznamu vyberte **LoadTest.**

7. Vyberte **OK**. Připojení můžete otestovat výběrem **možnosti Testovat připojení**.

8. V dialogovém okně **Spravovat testovací řadič** zvolte **Zavřít.**

## <a name="see-also"></a>Viz také

- [Správa výsledků zátěžových testů v úložišti výsledků zátěžových testů](../test/manage-load-test-results-in-the-load-test-results-repository.md)
- [Kontrolery testů a testovací agenti](configure-test-agents-and-controllers-for-load-tests.md)
