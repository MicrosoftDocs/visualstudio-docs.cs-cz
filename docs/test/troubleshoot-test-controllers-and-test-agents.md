---
title: Řešení potíží s testovacími kontroléry a testovacími agenty
description: Přečtěte si o některých běžných problémech, se kterými se můžete setkat při práci s testovacími kontroléry a testovacími agenty ve Visual Studiu.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.openlocfilehash: 8d9cae19736c9578f812e5e5fcd60dd9c6092e96
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99838279"
---
# <a name="strategies-for-troubleshooting-test-controllers-and-test-agents-in-load-tests"></a>Strategie pro řešení potíží s testovacími kontroléry a testovacími agenty v zátěžových testech

Tento článek popisuje některé běžné problémy, se kterými se můžete setkat při práci s testovacími kontroléry a testovacími agenty v aplikaci Visual Studio.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="unable-to-collect-performance-counters-on-test-agent-computer"></a>Nelze shromáždit čítače výkonu na počítači testovacího agenta.

Když spustíte zátěžový test, může docházet k chybám při pokusu o připojení k počítači testovacího agenta a ke shromažďování čítačů výkonu. Služba Remote Registry je služba zodpovědná za poskytování dat čítače výkonu ve vzdáleném počítači. V některých operačních systémech se služba Remote Registry nespustí automaticky. Pokud chcete tento problém vyřešit, ručně spusťte službu Remote Registry.

> [!NOTE]
> Ke službě Remote Registry můžete přistupovat v **Ovládacích panelech.** Zvolte **Nástroje pro správu** a pak zvolte **služby**.

Další příčinou tohoto problému je, že nemáte dostatečná oprávnění ke čtení čítačů výkonu. Pro místní testovací běhy musí být účet uživatele, který spouští test, členem skupiny Power Users nebo vyšší, nebo členem skupiny Performance Monitor Users. Pro vzdálené spuštění testů musí být účet, ke kterému je nastavené spuštění kontroleru, členem skupiny Power Users nebo vyšší, nebo členem skupiny Performance Monitor Users.

## <a name="set-the-logging-level-on-a-test-controller-computer"></a>Nastavení úrovně protokolování v počítači řadiče testu

Můžete řídit úroveň protokolování v počítači testovacího kontroléru. To je užitečné v případě, že se snažíte diagnostikovat problém při spuštění zátěžového testu v prostředí.

### <a name="to-set-the-logging-level-on-a-test-controller-computer"></a>Nastavení úrovně protokolování v počítači řadiče testu

1. Zastavte službu testovacího kontroléru. Do příkazového řádku zadejte `net stop vsttcontroller` .

2. Otevřete soubor *QTController.exe.config*. Tento soubor se nachází v instalačním adresáři kontroleru.

3. Upravte záznam pro `EqtTraceLevel` přepínač v souboru v části Diagnostika systému v souboru. Váš kód by měl vypadat takto:

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

4. Soubor uložte.

5. Spusťte službu kontroleru. Do příkazového řádku zadejte `net start vsttcontroller` .

To platí pro testovací kontrolér, službu testovacího agenta a proces testovacího agenta. Při diagnostikování problémů je vhodné povolit protokolování pro všechny tři procesy. Postup pro nastavení úrovně protokolování je stejný pro všechny tři procesy, jak je uvedeno výše pro řadič testu. Chcete-li nastavit úrovně protokolování pro službu testovacího agenta a proces agenta, použijte následující konfigurační soubory:

- *QTController.exe.config* Služba Conttoller

- *QTAgentService.exe.config* Služba agenta

- *QTDCAgent (32) .exe.config* Proces adaptéru dat agenta pro 32 bitovou architekturu.

- *QTDCAgent (64) .exe.config* Proces adaptéru dat agenta pro 64 bitovou architekturu.

- *QTAgent (32) .exe.config* Proces testování agenta pro 32 bitovou architekturu.

- *QTAgent (64) .exe.config* Proces testování agenta pro 64 bitovou architekturu.

## <a name="bind-a-test-controller-to-a-network-adapter"></a>Vazba testovacího kontroléru na síťový adaptér

Při pokusu o nastavení testovacího agenta se může zobrazit následující chyba:

**Chyba 8110. Nelze se připojit k zadanému počítači kontroléru nebo získat přístup k objektu kontroleru.**

Tato chyba může být způsobena instalací kontroleru testů na počítači, který má více než jeden síťový adaptér.

> [!NOTE]
> Je také možné úspěšně nainstalovat testovací agenty a tento problém se neprojeví, dokud se nepokusíte spustit test.

Chcete-li tuto chybu opravit, je nutné vytvořit vazby kontroleru testů k jednomu ze síťových adaptérů. Je nutné nastavit `BindTo` vlastnost testovacího kontroléru a poté změnit testovacího agenta tak, aby odkazoval na testovací kontrolér podle IP adresy místo podle názvu. Postup je k dispozici v následujících postupech.

### <a name="to-obtain-the-ip-address-of-the-network-adapter"></a>Získání IP adresy síťového adaptéru

1. Zvolte možnost **Start** a pak zvolte možnost **Spustit**.

     Zobrazí se dialogové okno **Spustit** .

2. Zadejte `cmd` a pak zvolte **OK**.

     Otevře se příkazový řádek.

3. Zadejte `ipconfig /all`.

     Zobrazí se IP adresy pro vaše síťové adaptéry. Poznamenejte si IP adresu síťového adaptéru, ke kterému chcete vytvořit vazby řadiče.

### <a name="to-bind-a-test-controller-to-a-network-adapter"></a>Navázání testovacího kontroléru na síťový adaptér

1. Zastavte službu testovacího kontroléru. Do příkazového řádku zadejte `net stop vsttcontroller` .

2. Otevřete soubor *QTController.exe.config*. Tento soubor je umístěný v umístění *% ProgramFiles (x86)% \ Microsoft Visual Studio\2017\Enterprise\Common7\IDE*.

3. Přidejte položku pro `BindTo` vlastnost do nastavení aplikace. Zadejte IP adresu síťového adaptéru, ke kterému chcete vytvořit vazby řadiče. Váš kód by měl vypadat takto:

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

4. Soubor uložte.

5. Spusťte službu testovacího kontroléru. Do příkazového řádku zadejte `net start vsttcontroller` .

### <a name="to-connect-a-test-agent-to-a-bound-controller"></a>Připojení testovacího agenta k vázanému kontroleru

- Spusťte instalaci testovacího agenta znovu. Tentokrát zadejte IP adresu testovacího kontroleru místo názvu kontroleru testů.

To platí pro testovací kontrolér, službu testovacího agenta a proces testovacího agenta. `BindTo`Vlastnost musí být nastavena pro každý proces, který je spuštěn v počítači, který má více než jeden síťový adaptér. Postup pro nastavení `BindTo` vlastnosti je stejný pro všechny tři procesy, jak je uvedeno výše pro kontroler testů. Chcete-li nastavit úrovně protokolování pro službu testovacího agenta a proces testovacího agenta, použijte konfigurační soubory, které jsou uvedeny v [části nastavení úrovně protokolování v počítači testovacího kontroléru](#set-the-logging-level-on-a-test-controller-computer).

## <a name="see-also"></a>Viz také

- [Kontrolery testů a testovací agenti](../test/configure-test-agents-and-controllers-for-load-tests.md)
