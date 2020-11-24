---
title: 'Postupy: Výběr úložiště výsledků zátěžového testu'
description: Přečtěte si, jak identifikovat místní nebo vzdálený SQL Server pro ukládání výsledků testů. Server musí mít úložiště výsledků zátěžového testu.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
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
ms.openlocfilehash: ada73cc1f907a298a2cc1efcf3281fb8a219ef32
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2020
ms.locfileid: "95439937"
---
# <a name="how-to-select-a-load-test-results-repository"></a>Postupy: výběr úložiště výsledků zátěžového testu

Nejste omezeni na místní úložiště výsledků. Zátěžové testy jsou často spouštěny ve vzdálené sadě počítačů agenta. Agenty mohou spolu s kontrolérem generovat více simulované zátěže než jakýkoli jeden počítač. Další informace naleznete v tématu [řadiče testů a testovací agenti](configure-test-agents-and-controllers-for-load-tests.md).

Výsledky testů z agentů nebo místního počítače lze uložit na jakýkoli SQL Server, na kterém jste vytvořili úložiště výsledků zátěžového testu. V obou případech je nutné určit, kam chcete uložit výsledky zátěžového testu pomocí okna **Spravovat testovací kontroléry** .

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="identify-a-results-store-for-load-test-data"></a>Identifikace úložiště výsledků pro data zátěžového testu

1. V **Průzkumník řešení** otevřete soubor zátěžového testu.

2. Z panelu nástrojů **zátěžového testu** vyberte možnost **Spravovat testovací kontroléry**. Zobrazí se dialogové okno **spravovat Test Controller** . Používáte-li agent vzdáleně, je zapotřebí zvolit kontrolér.

     ![Výsledky zátěžového testu vlastnosti připojení ](../test/media/loadtestconnectionproperties.png) úložiště výsledků zátěžového testu vlastnosti připojení úložiště

3. V **úložišti výsledků zátěžového testu** klikněte na **(...)** a zobrazte dialogové okno **Vlastnosti připojení** .

4. Do pole **název serveru** zadejte název serveru, na kterém jste spustili `LoadTest` skripty.

    > [!TIP]
    > Pokud používáte SQL Express na místním počítači pro úložiště zátěžového testu, zadejte \<computername> \SQLExpress (například **MyComputer\sqlexpress**).

5. V části **Přihlásit se k serveru** můžete zvolit možnost **použít ověřování systému Windows**. Můžete zadat uživatelské jméno a heslo, ale pokud to uděláte, musíte vybrat možnost **Uložit heslo**.

6. V části **připojit k databázi** zvolte **možnost vybrat nebo zadejte název databáze**. V rozevíracím seznamu vyberte **LoadTest** .

7. Vyberte **OK**. Připojení můžete otestovat kliknutím na **Test připojení**.

8. V dialogovém okně **spravovat Test Controller** vyberte **Zavřít** .

## <a name="see-also"></a>Viz také

- [Správa výsledků zátěžového testu v úložišti Výsledky testů zatížení](../test/manage-load-test-results-in-the-load-test-results-repository.md)
- [Kontrolery testů a testovací agenti](configure-test-agents-and-controllers-for-load-tests.md)
