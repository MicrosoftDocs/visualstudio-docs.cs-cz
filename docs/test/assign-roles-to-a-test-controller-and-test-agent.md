---
title: Role testovacího řadiče a testovacího agenta pro automatizované testy
ms.date: 10/20/2016
ms.topic: conceptual
helpviewer_keywords:
- testing, walkthroughs, test controller and test agents
- test agent, walkthrough
- walkthroughs [Visual Studio ALM] testing
- test controller, walkthrough
- walkthroughs, test controller and test agents
ms.assetid: 57ed43ae-4e67-4139-8aec-3e9fceb0a745
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f0ea644294ea79f1e4c044c0cebf3f427f5b672a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591187"
---
# <a name="assign-roles-to-a-test-controller-and-test-agent"></a>Přiřazení rolí testovacímu řadiči a testovacímu agentovi

Tento článek ukazuje, jak vytvořit a nakonfigurovat testovací nastavení, které používá testovací řadič a testovací agent k distribuci testování mezi několik počítačů pomocí sady Visual Studio. Také ukazuje, jak přidat diagnostické a datové adaptéry do nastavení testu.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="prerequisites"></a>Požadavky

- Vytvořte testy částí nebo kódované testy ui pro spuštění s nastavením testu.

- Nainstalujte testovací řadič a testovací agenty. Informace o instalaci testovacího řadiče a testovacích agentů naleznete v [tématu Instalace a konfigurace testovacích agentů](../test/lab-management/install-configure-test-agents.md).

## <a name="to-create-and-configure-a-test-setting"></a>Vytvoření a konfigurace nastavení testu

1. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na **položku Položky řešení ,** přejděte na **Přidat**a pak zvolte Nová **položka**.

     Zobrazí se dialogové okno **Přidat novou položku**.

2. V podokně **Nainstalované šablony** zvolte **Testovat nastavení**.

3. Do pole **Název** zadejte **testSettingDistributedTestWalkthrough**.

4. Zvolte **Přidat**.

     Nový test *TestSettingDistributedTestWalkthrough.testsettings* soubor se zobrazí v **Průzkumníku řešení**, ve složce **Položky řešení.**

     Zobrazí se dialogové okno **Nastavení testu.** Je vybrána stránka **Obecné.**

     Nyní můžete upravovat a ukládat hodnoty nastavení testu.

5. V **části Název**zadejte název nastavení testu.

6. V části **Popis**zadejte **Nastavení distribuovaného testu**.

7. Ponechat **vybrané výchozí schéma pojmenování.**

## <a name="to-assign-roles-to-a-test-controller-and-test-agents"></a>Přiřazení rolí testovacímu řadiči a testovacím agentům

1. Zvolte **Role**.

     Zobrazí se stránka **Role.**

2. Chcete-li spustit test vzdáleně, použijte rozevírací seznam **Metody spuštění testu** a vyberte možnost Vzdálené **spuštění**.

3. V rozevíracím seznamu **Řadič** zadejte název počítače [testovacího řadiče](../test/lab-management/install-configure-test-agents.md).

    > [!NOTE]
    > Pokud je to poprvé, co přidáváte řadič, nejsou v rozevíracím seznamu uvedeny žádné řadiče. Seznam je naplněn předchozími řadiči, které jste zadali v jiných nastaveních testu.

4. V části **Role**zvolte **Přidat**.

5. Ve zvýrazněném řádku ve sloupci **Název** zadejte **Distributed test**.

## <a name="to-assign-a-diagnostic-and-data-adapter-to-your-test-setting"></a>Přiřazení diagnostického a datového adaptéru k nastavení testu

1. Zvolte **Data a diagnostika**.

     Zobrazí se stránka **Data a diagnostika.**

2. V **části Role**ověřte, zda je vybrána role **distribuovaného testu.**

3. V části **Data and Diagnostic for select role**vyberte adaptéry **IntelliTrace** a **System Information** .

     Informace o těchto adaptérech a dalších adaptérech, které lze použít v testovacím nastavení, naleznete v [tématu Konfigurace testů částí](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md).

4. Zvolte **Hostitelé**.

5. (Nepovinné) Pokud je váš počítač spuštěn v 64bitové verzi systému Microsoft Windows a test jste zkompilovali pomocí konfigurace **Libovolný procesor,** použijte **spustit test v 32bitovém nebo 64bitovém** seznamu procesů a vyberte Spustit testy v **64bitovém procesu v 64bitovém počítači**.

    > [!TIP]
    > Pro maximální flexibilitu byste měli zkompilovat testovací projekty s konfigurací **libovolný procesor.** Pak můžete spustit na 32bitové i 64bitové agenty. Kompilace testovacích projektů s **64bitovou** konfigurací nemá žádnou výhodu.

6. Chcete-li uložit nové nastavení testu, zvolte **Použít**.

7. Zvolte **Zavřít**.

::: moniker range="vs-2017"

8. V nabídce **Test** vyberte **Možnost Nastavení** > **testu Vybrat soubor nastavení testu** a pak zvolte soubor *TestSettingDistributedTestWalkthrough.testsettings.*

::: moniker-end

::: moniker range=">=vs-2019"

8. V nabídce **Test** zvolte **Vybrat soubor nastavení**. Vyhledejte a vyberte soubor *TestSettingDistributedTestWalkthrough.testsettings.*

::: moniker-end

9. Spusťte test jako obvykle.

     Když testovací regulátor zpracovává testy částí a kódované testy ui, testovací řadič rozdělí testy do skupin po 100 a odešle je do počítače testovacího agenta. Například pokud máte 250 testů částí a tři testovací agenti, prvních 100 testů částí budou odeslány agent1, dalších 100 testů částí budou odeslány agent2 a zbývajících 50 testů částí bude odeslána agent3.

## <a name="see-also"></a>Viz také

- [Instalace a konfigurace testovacích agentů](../test/lab-management/install-configure-test-agents.md)
