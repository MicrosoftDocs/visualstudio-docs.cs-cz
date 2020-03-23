---
title: Poradce při potížích s testovacími řadiči a testovacími agenty
ms.date: 10/20/2016
ms.topic: troubleshooting
helpviewer_keywords:
- load tests, test controllers
- load tests, troubleshooting
- load tests, test agents
- troubleshooting, test controllers and agents in load tests
ms.assetid: 77329348-3a5d-43de-b6cb-90f93296a081
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 51d7e15ec71eec7134dfc49b3515385970e593a0
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75565952"
---
# <a name="strategies-for-troubleshooting-test-controllers-and-test-agents-in-load-tests"></a>Strategie pro řešení potíží s testovacími řadiči a testovacími agenty v zátěžových testech

Tento článek popisuje některé běžné problémy, se kterými se může setkat při práci s testovacími řadiči a testovacími agenty v sadě Visual Studio.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="unable-to-collect-performance-counters-on-test-agent-computer"></a>Nelze shromáždit čítače výkonu v počítači testovacího agenta.

Při spuštění zátěžového testu se mohou zobrazit chyby při pokusu o připojení k počítači testovacího agenta a shromažďování čítačů výkonu. Služba Vzdálený registr je služba odpovědná za poskytování dat čítače výkonu do vzdáleného počítače. V některých operačních systémech se služba Vzdálený registr nespustí automaticky. Chcete-li tento problém vyřešit, ručně spusťte službu Vzdálený registr.

> [!NOTE]
> V **Ovládacích panelech** můžete přistupovat ke službě Vzdálený registr. Zvolte **Nástroje pro správu** a pak zvolte **Služby**.

Další příčinou tohoto problému je, že nemáte dostatečná oprávnění ke čtení čítačů výkonu. Pro místní testovací běhy musí být účet uživatele, který test spouští, členem skupiny Power Users nebo vyšším nebo členem skupiny Performance Monitor Users. Při spuštění vzdáleného testu musí být účet, který je řadič nakonfigurován tak, aby byl spuštěn jako člen skupiny Power Users nebo vyšší nebo členem skupiny Performance Monitor Users.

## <a name="set-the-logging-level-on-a-test-controller-computer"></a>Nastavení úrovně protokolování v počítači testovacího řadiče

Můžete řídit úroveň protokolování v počítači testovacího řadiče. To je užitečné, když se pokoušíte diagnostikovat problém při spuštění zátěžového testu v prostředí.

### <a name="to-set-the-logging-level-on-a-test-controller-computer"></a>Nastavení úrovně protokolování v počítači testovacího řadiče

1. Zastavte službu testovacího řadiče. Na příkazovém `net stop vsttcontroller`řádku zadejte příkaz .

2. Otevřete soubor *QTController.exe.config*. Tento soubor je umístěn v instalačním adresáři řadiče.

3. Upravte položku `EqtTraceLevel` přepínače v části diagnostiky systému souboru. Váš kód by měl vypadat takto:

    ```xml
    <system.diagnostics>
        <trace autoflush="true" indentsize="4">
            <listeners>
                <add name="myListener" type="System.Diagnostics.TextWriterTraceListener" initializeData="d:\VSTestHost.log" />
            </listeners>
        </trace>
        <switches>
            <!-- You must use integral values for "value":
                    0 = off,
                    1 = error,
                    2 = warn,
                    3 = info,
                    4 = verbose. -->
            <add name="EqtTraceLevel" value="4" />
        </switches>
    </system.diagnostics>
    ```

4. Uložte soubor.

5. Spusťte službu řadiče. Na příkazovém `net start vsttcontroller`řádku zadejte příkaz .

To platí pro řadič testu, službu testovacího agenta a proces testovacího agenta. Při diagnostice problémů je užitečné povolit protokolování všech tří procesů. Postup pro nastavení úrovně protokolování je stejný pro všechny tři procesy, jak bylo uvedeno dříve pro testovací řadič. Chcete-li nastavit úrovně protokolování pro službu testovacího agenta a proces agenta, použijte následující konfigurační soubory:

- Služba Conttoller *qtController.exe.config*

- Služba *Agent QTAgentService.exe.config*

- *QTDCAgent(32).exe.config* Proces adaptéru dat agenta pro 32bitovou architekturu.

- *QTDCAgent(64).exe.config* Proces adaptéru dat agenta pro 64bitovou architekturu.

- *QTAgent(32).exe.config* Proces testování agenta pro 32bitovou architekturu.

- *QTAgent(64).exe.config* Proces testování agenta pro 64bitovou architekturu.

## <a name="bind-a-test-controller-to-a-network-adapter"></a>Vazba testovacího řadiče na síťový adaptér

Při pokusu o nastavení testovacího agenta se může zobrazit následující chyba:

**Chyba 8110. Nelze se připojit k zadanému počítači řadiče nebo získat přístup k objektu řadiče.**

Tato chyba může být způsobena instalací testovacího řadiče do počítače, který má více než jeden síťový adaptér.

> [!NOTE]
> Je také možné úspěšně nainstalovat testovací agenty a tento problém se nezobrazí, dokud se nepokusíte spustit test.

Chcete-li tuto chybu opravit, je nutné svázat testovací řadič s jedním ze síťových adaptérů. Je třeba nastavit `BindTo` vlastnost na testovací řadič a potom změnit testovacíagent odkazovat na testovací řadič podle IP adresy namísto podle názvu. Kroky jsou uvedeny v následujících postupech.

### <a name="to-obtain-the-ip-address-of-the-network-adapter"></a>Získání adresy IP síťového adaptéru

1. Zvolte **Start**a pak zvolte **Spustit**.

     Zobrazí se dialogové okno **Spustit.**

2. Zadejte `cmd` a pak zvolte **OK**.

     Otevře se příkazový řádek.

3. Zadejte `ipconfig /all`.

     Zobrazí se adresy IP síťových adaptérů. Zaznamenejte adresu IP síťového adaptéru, se kterou chcete řadič svázat.

### <a name="to-bind-a-test-controller-to-a-network-adapter"></a>Vytvoření svázání testovacího řadiče se síťovým adaptérem

1. Zastavte službu testovacího řadiče. Na příkazovém `net stop vsttcontroller`řádku zadejte příkaz .

2. Otevřete soubor *QTController.exe.config*. Tento soubor je umístěn v *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE*.

3. Přidejte položku `BindTo` vlastnosti do nastavení aplikace. Zadejte adresu IP síťového adaptéru, se kterým chcete řadič svázat. Váš kód by měl vypadat takto:

    ```xml
    <appSettings>
        <add key="LogSizeLimitInMegs" value="20" />
        <add key="AgentSyncTimeoutInSeconds" value="120" />
        <add key="ControllerServicePort" value="6901" />
        <add key="ControllerUsersGroup" value="TeamTestControllerUsers" />
        <add key="ControllerAdminsGroup" value="TeamTestControllerAdmins" />
        <add key="CreateTraceListener" value="no" />
        <add key="BindTo" value="<YOUR IP ADDRESS>" />
    </appSettings>
    ```

4. Uložte soubor.

5. Spusťte službu testovacího řadiče. Na příkazovém `net start vsttcontroller`řádku zadejte příkaz .

### <a name="to-connect-a-test-agent-to-a-bound-controller"></a>Připojení testovacího agenta k vázanému řadiči

- Spusťte instalaci testovacího agenta znovu. Tentokrát zadejte IP adresu testovacího řadiče namísto názvu testovacího řadiče.

To platí pro řadič testu, službu testovacího agenta a proces testovacího agenta. Vlastnost `BindTo` musí být nastavena pro každý proces, který je spuštěn v počítači, který má více než jeden síťový adaptér. Postup nastavení vlastnosti `BindTo` je stejný pro všechny tři procesy, jak bylo uvedeno dříve pro testovací řadič. Chcete-li nastavit úrovně protokolování pro službu testovacího agenta a proces testovacího agenta, použijte konfigurační soubory uvedené v části [Nastavit úroveň protokolování v počítači testovacího řadiče](#set-the-logging-level-on-a-test-controller-computer).

## <a name="see-also"></a>Viz také

- [Kontrolery testů a testovací agenti](../test/configure-test-agents-and-controllers-for-load-tests.md)
