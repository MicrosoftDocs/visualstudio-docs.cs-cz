---
title: Testovací kontrolér a role testovacího agenta
description: Naučte se, jak vytvořit a nakonfigurovat nastavení testu, které používá testovací kontrolér a testovací agenty k distribuci testování napříč několika počítači pomocí sady Visual Studio.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: c059510dc39472d5c981f93e4d7259545b809d38
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2020
ms.locfileid: "95442440"
---
# <a name="assign-roles-to-a-test-controller-and-test-agent"></a>Přiřazení rolí k testovacímu kontroleru a testovacímu agentovi

Tento článek ukazuje, jak vytvořit a nakonfigurovat nastavení testu, které používá testovací kontrolér a testovací agenty k distribuci testování napříč několika počítači pomocí sady Visual Studio. Také ukazuje, jak přidat diagnostické a datové adaptéry do nastavení testu.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="prerequisites"></a>Předpoklady

- Vytvořte testy jednotek nebo kódované testy uživatelského rozhraní, které chcete spustit s nastavením testu.

- Nainstalujte testovací kontrolér a testovací agenty. Informace o tom, jak nainstalovat testovací kontrolér a testovací agenty, najdete v tématu [instalace a konfigurace testovacích agentů](../test/lab-management/install-configure-test-agents.md).

## <a name="to-create-and-configure-a-test-setting"></a>Vytvoření a konfigurace nastavení testu

1. V **Průzkumník řešení** klikněte pravým tlačítkem myši na **položky řešení,** přejděte na **Přidat** a pak zvolte **Nová položka**.

     Zobrazí se dialogové okno **Přidat novou položku**.

2. V podokně **Nainstalované šablony** vyberte možnost **nastavení testu**.

3. Do pole **název** zadejte **TestSettingDistributedTestWalkthrough**.

4. Klikněte na tlačítko **Přidat**.

     Nový soubor test *TestSettingDistributedTestWalkthrough. testsettings* se zobrazí v **Průzkumník řešení** ve složce **položky řešení** .

     Zobrazí se dialogové okno **nastavení testu** . Je vybrána stránka **Obecné** .

     Nyní můžete upravit a uložit hodnoty nastavení testu.

5. Do pole **název** zadejte název nastavení testu.

6. V části **Popis** zadejte **Nastavení distribuovaného testu**.

7. Ponechte vybrané **výchozí schéma pojmenování** .

## <a name="to-assign-roles-to-a-test-controller-and-test-agents"></a>Přiřazení rolí k testovacímu kontroleru a testovacím agentům

1. Vyberte **role**.

     Zobrazí se stránka **role** .

2. Chcete-li spustit test vzdáleně, použijte rozevírací seznam **Metoda provedení testu** a vyberte **vzdálené spuštění**.

3. V rozevíracím seznamu **kontrolér** zadejte název počítače [testovacího kontroléru](../test/lab-management/install-configure-test-agents.md).

    > [!NOTE]
    > Pokud přidáváte řadič poprvé, v rozevíracím seznamu nejsou uvedené žádné řadiče. Seznam je vyplněn předchozími řadiči, které jste zadali v jiných nastaveních testu.

4. V části **role** klikněte na možnost **Přidat**.

5. Do zvýrazněného řádku ve sloupci **název** zadejte **Distribuovaný test**.

## <a name="to-assign-a-diagnostic-and-data-adapter-to-your-test-setting"></a>Přiřazení diagnostického a datového adaptéru k nastavení testu

1. Vyberte **data a diagnostiku**.

     Zobrazí se stránka **data a diagnostika** .

2. V části **role** ověřte, že je vybraná role **distribuovaného testu** .

3. V části **data a Diagnostika pro vybranou roli** vyberte adaptéry **IntelliTrace** a **Systémové informace** .

     Informace o těchto adaptérech a jiných adaptérech, které lze použít v nastavení testu, naleznete v tématu [Configure Unit Tests](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md).

4. Vyberte možnost **hostitelé**.

5. Volitelné Pokud je v počítači spuštěná 64 verze Microsoft Windows a váš test jste zkompilováni pomocí **jakékoli konfigurace CPU** , použijte rozevírací seznam **Spustit test v systému 32 nebo 64 bitových procesů** a vyberte možnost **spouštět testy 64 v 64 procesu 16Bitového počítače v počítači s operačním** systémem.

    > [!TIP]
    > Pro maximální flexibilitu byste měli kompilovat testovací projekty s libovolnou konfigurací **procesoru** . Pak můžete spustit na 32 i 64 bitových agentů. Není k dispozici žádná výhoda pro kompilování testovacích projektů s **64** konfigurací.

6. Chcete-li uložit nové nastavení testu, klikněte na tlačítko **použít**.

7. Klikněte na tlačítko **Zavřít**.

::: moniker range="vs-2017"

8. V nabídce **test** vyberte možnost **nastavení testu** > **Vybrat soubor nastavení testu** a pak zvolte soubor *TestSettingDistributedTestWalkthrough. testsettings* .

::: moniker-end

::: moniker range=">=vs-2019"

8. V nabídce **test** zvolte **možnost vybrat soubor nastavení**. Vyhledejte a vyberte soubor *TestSettingDistributedTestWalkthrough. testsettings* .

::: moniker-end

9. Spusťte test obvyklým způsobem.

     Když kontroler testů zpracuje testy jednotek a kódované testy UI, kontroler testů rozdělí testy do skupin 100 a odešle je do počítače testovacího agenta. Například pokud máte 250 jednotkových testů a tři testovací agenty, do obdrží agent1 se pošle prvních 100 jednotek testů, do obdrží agent2 se pošle 100 další testy jednotek a zbývající testy 50 jednotek se odešlou do obdrží Agent3.

## <a name="see-also"></a>Viz také

- [Instalace a konfigurace testovacích agentů](../test/lab-management/install-configure-test-agents.md)
