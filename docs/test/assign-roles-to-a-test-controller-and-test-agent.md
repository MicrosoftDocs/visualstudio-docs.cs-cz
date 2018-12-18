---
title: Přiřazení rolí na testovací Kontrolér a testovací Agent pro automatizované testování
ms.date: 10/20/2016
ms.topic: conceptual
helpviewer_keywords:
- testing, walkthroughs, test controller and test agents
- test agent, walkthrough
- walkthroughs [Visual Studio ALM] testing
- test controller, walkthrough
- walkthroughs, test controller and test agents
ms.assetid: 57ed43ae-4e67-4139-8aec-3e9fceb0a745
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 021693266278bd705678c22d2c3f07e534901e5a
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2018
ms.locfileid: "52895337"
---
# <a name="assign-roles-to-a-test-controller-and-test-agent"></a>Přiřazení rolí na testovací kontrolér a testovací agent

Tento návod ukazuje, jak vytvořit a nakonfigurovat nastavení testu používající testovací kontrolér a testovací agent pro distribuci testování v několika počítačích pomocí sady Visual Studio. Kromě toho tento návod ukazuje, jak přidat adaptéry diagnostických do nastavení testu.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="prerequisites"></a>Požadavky

-   Vytvořte testy jednotek nebo programové testy UI pomocí nastavení testu.

-   Nainstalujte testovací kontrolér a testovací agenty. Informace o tom, jak instalace testovacího kontroléru a testovacích agentů najdete v tématu [instalace a konfigurace testovacích agentů](../test/lab-management/install-configure-test-agents.md).

## <a name="to-create-and-configure-a-test-setting"></a>Vytvoření a konfigurace nastavení testu

1.  V **Průzkumníka řešení**, klikněte pravým tlačítkem na **položky řešení** přejděte **přidat**a klikněte na tlačítko **nová položka**.

     **Přidat novou položku** zobrazí se dialogové okno.

2.  V **nainstalované šablony** podokně zvolte **nastavení testu**.

3.  V **název** zadejte **TestSettingDistributedTestWalkthrough**.

4.  Zvolte **přidat**.

     Nový test *TestSettingDistributedTestWalkthrough.testsettings* souboru se zobrazí v **Průzkumníka řešení**v části **položky řešení** složky.

     **Nastavení testu** se zobrazí dialogové okno. **Obecné** je vybrána stránka.

     Teď můžete upravit a uložit hodnoty nastavení testu.

    > [!NOTE]
    > Každé nastavení testu, které vytvoříte, je uvedeno jako volba pro **vybrat aktivní nastavení testu** a **upravit nastavení testu** možnosti **testování** nabídky.

5.  V části **název**, zadejte název pro nastavení testu.

6.  V části **popis**, typ **nastavení distribuovaného testu**.

7.  Ponechte **výchozí schéma pojmenování** vybrané.

## <a name="to-assign-roles-to-a-test-controller-and-test-agents"></a>K přiřazení rolí na testovací kontrolér a testovací agenty

1.  Zvolte **role**.

     **Role** zobrazí se stránka.

2.  Chcete-li spustit test vzdáleně, použijte **metoda spuštění testu** rozevíracího seznamu a vyberte **vzdálené spuštění**.

3.  V **řadič** rozevíracího seznamu, zadejte název počítače [testovací kontrolér](../test/lab-management/install-configure-test-agents.md).

    > [!NOTE]
    > Pokud je to poprvé, co přidáváte řadič, nejsou žádné řadiče uvedeny v rozevíracím seznamu. Seznam je vyplněn předchozími řadiči, které jste zadali v rámci jiných nastaveních testu.

4.  V části **role**, zvolte **přidat**.

5.  Na zvýrazněný řádek ve **název** sloupců, typ **distribuovaný test**.

## <a name="to-assign-a-diagnostic-and-data-adapter-to-your-test-setting"></a>Přiřazení diagnostiky a datového adaptéru k nastavení testu

1.  Zvolte **dat a diagnostiky**.

     **Dat a diagnostiky** zobrazí se stránka.

2.  V části **Role**, ověřte, že **distribuovaný test** je vybrána role.

3.  V části **dat a diagnostiky pro roli vyberte**, vyberte **IntelliTrace** a **systémové informace** adaptéry.

     Informace o těchto adaptérech a jiných adaptérech, které můžete v nastavení testu, naleznete v tématu [konfigurace testů jednotek](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md).

4.  Zvolte **hostitele**.

5.  (Volitelné) Pokud váš počítač běží v 64bitové verzi systému Microsoft Windows a zkompilujete test pomocí **jakýkoli procesor** konfigurace, použijte **spustit test v 32bitovém nebo 64bitovém procesu** rozevíracího seznamu a vyberte **Spustit testy v 64bitový proces na 64bitovém počítači**.

    > [!TIP]
    > Pro maximální flexibilitu byste měli kompilovat testovací projekty s **jakýkoli procesor** konfigurace. Poté můžete spouštět na 32bitových a 64bitových agentech. Neexistuje žádná výhoda pro kompilaci testovacích projektů s **64-bit** konfigurace.

6.  Chcete-li uložit nové nastavení testu, zvolte **použít**.

7.  Zvolte **Zavřít**.

8.  V nabídce Test vyberte **vybrat aktivní nastavení testu** a klikněte na tlačítko **TestSettingDistributedTestWalkthrough.testsettings**.

9. Spusťte test obvyklým způsobem.

     Když procesy řadiče testu zpracovávají, testy částí a programové testy UI, řadič testu rozdělí testy do skupin po 100 a odešle je do počítače testovacího agenta. Například pokud máte 250 testů jednotky a tři testovací agenti, se pošle prvních 100 jednotkové testy agent1, další 100 jednotkové testy se odešlou do agent2 a zbývajících 50 jednotkové testy se odešlou do agent3.

## <a name="see-also"></a>Viz také:

- [Instalace a konfigurace testovacích agentů](../test/lab-management/install-configure-test-agents.md)