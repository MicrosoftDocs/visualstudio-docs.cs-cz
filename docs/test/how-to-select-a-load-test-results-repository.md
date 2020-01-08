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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75589003"
---
# <a name="how-to-select-a-load-test-results-repository"></a>Postupy: Výběr úložiště výsledků zátěžového testu

Nejste omezeni na úložiště místních výsledků. Často jsou zátěžové testy spuštěny na vzdálené sadě počítačů agentů. Agenty mohou spolu s kontrolérem generovat více simulované zátěže než jakýkoli jeden počítač. Další informace najdete v tématu [testovací kontrolery a testovací agenty](configure-test-agents-and-controllers-for-load-tests.md).

Výsledky testu z agentů nebo místního počítače můžete uložit na každý serversql, na kterém jste vytvořili úložiště výsledků zátěžového testu. V obou případech je nutné určit, kam chcete uložit výsledky zátěžového testu pomocí **Správa testovacích Kontrolérů** okna.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="identify-a-results-store-for-load-test-data"></a>Identifikace úložiště výsledků pro data zátěžového testu

1. V **Průzkumníka řešení**, otevřete soubor zátěžového testu.

2. Z **zátěžový Test** nástrojů, zvolte **spravovat testovací Kontroléry**. **Spravovat testovací Kontrolér** se zobrazí dialogové okno. Používáte-li agent vzdáleně, je zapotřebí zvolit kontrolér.

     ![Vlastnosti připojení úložiště výsledků zátěžového testu](../test/media/loadtestconnectionproperties.png) vlastnosti připojení úložiště výsledků zátěžového testu

3. V **úložiště výsledků zátěžového testu**, klikněte na tlačítko **(...)**  zobrazíte **vlastnosti připojení** dialogové okno.

4. V **název serveru**, zadejte název serveru, na kterém jste spustili `LoadTest` skripty.

    > [!TIP]
    > Pokud používáte SQL Express na místním počítači pro úložiště zátěžového testu, zadejte \<názevpočítače > \sqlexpress (například **Můjpočítač\sqlexpress**).

5. V části **Přihlaste se k serveru**, můžete zvolit **použít ověřování Windows**. Můžete zadat uživatelské jméno a heslo, ale pokud tak učiníte, musíte vybrat možnost **uložit heslo**.

6. V části **připojit k databázi**, zvolte **vyberte nebo zadejte název databáze**. Vyberte **LoadTest** z rozevíracího seznamu.

7. Vyberte **OK**. Připojení můžete otestovat pomocí příkazu **Test připojení**.

8. Zvolte **Zavřít** v **spravovat testovací Kontrolér** dialogové okno.

## <a name="see-also"></a>Viz také:

- [Správa výsledků zátěžových testů v úložiště výsledků testu zátěže](../test/manage-load-test-results-in-the-load-test-results-repository.md)
- [Kontrolery testů a testovací agenti](configure-test-agents-and-controllers-for-load-tests.md)
