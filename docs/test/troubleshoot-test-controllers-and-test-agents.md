---
title: Řešení potíží s testovacími Kontroléry a testovací agenty
ms.date: 10/20/2016
ms.topic: troubleshooting
helpviewer_keywords:
- load tests, test controllers
- load tests, troubleshooting
- load tests, test agents
- troubleshooting, test controllers and agents in load tests
ms.assetid: 77329348-3a5d-43de-b6cb-90f93296a081
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 274585d864393877b225fe6231c1f775342620f6
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2018
ms.locfileid: "52894739"
---
# <a name="strategies-for-troubleshooting-test-controllers-and-test-agents-in-load-tests"></a>Strategie pro řešení potíží s testovacími kontroléry a testovacími agenty v zátěžových testech

Tento článek popisuje některé běžné problémy, které můžete narazit při práci s testovacími kontroléry a testovací agenty v sadě Visual Studio.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

##  <a name="unable-to-collect-performance-counters-on-test-agent-computer"></a>Nepovedlo se získat čítače výkonu v počítači testovacího agenta

Při spuštění zátěžového testu, může dojít k chybám při pokusu o připojení k počítači testovacího agenta a shromáždění čítačů výkonu. Služba Vzdálený registr je služba zodpovědná za poskytování dat čítače výkonu ke vzdálenému počítači. U některých operačních systémů služba Remote Registry se nespustí automaticky. Chcete-li tento problém vyřešit, ručně spusťte službu Remote Registry.

> [!NOTE]
> Můžete přístup k službě Remote Registry v **ovládacích panelech.** Zvolte **nástroje pro správu** a klikněte na tlačítko **služby**.

Další příčinou tohoto problému je, že nemáte dostatečná oprávnění ke čtení čítačů výkonu. Místní spouštění testů účet uživatele, který spouští test musí být členem skupiny Power Users nebo vyšší nebo být členem skupiny Performance Monitor Users. Pro vzdálené test běží, účet, který kontroleru je nakonfigurováno spuštění musí být členem skupiny Power Users nebo vyšší, nebo být členem skupiny Performance Monitor Users.

## <a name="set-the-logging-level-on-a-test-controller-computer"></a>Nastavení úrovně protokolování v počítači řadiče testu

Můžete řídit úroveň protokolování v počítači řadiče testu. To je užitečné, když se pokoušíte diagnostikovat problém při spouštění zátěžového testu v prostředí.

### <a name="to-set-the-logging-level-on-a-test-controller-computer"></a>Nastavení úrovně protokolování v počítači řadiče testu

1.  Zastavte službu testovacího řadiče. Na příkazovém řádku zadejte `net stop vsttcontroller`.

2.  Otevřete soubor *QTController.exe.config*. Tento soubor je umístěn v instalačním adresáři kontroleru.

3.  Upravit položku `EqtTraceLevel` přepínat v části Diagnostika systému souboru. Váš kód by měl vypadat takto:

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

4.  Uložte soubor.

5.  Spusťte službu řadiče. Na příkazovém řádku zadejte `net start vsttcontroller`.

To platí pro testovací kontrolér, službu testovacího agenta a proces testovacího agenta. Při diagnostikování potíží je vhodné povolit protokolování všech tří procesů. Postup pro nastavení úrovně protokolování je stejný pro všechny tři procesy, jak je uvedeno výše pro řadič testu. K nastavení úrovní protokolování pro testovacího agenta, služby a proces agenta, použijte následující konfigurační soubory:

-   *QTController.exe.config* Služba ovladače

-   *QTAgentService.exe.config* Služba agenta

-   *QTDCAgent (32).exe.config* proces adaptéru dat agenta pro 32bitovou architekturu.

-   *QTDCAgent (64).exe.config* proces adaptéru dat agenta pro 64bitová architektura.

-   *QTAgent (32).exe.config* proces testování agenta pro 32bitovou architekturu.

-   *QTAgent (64).exe.config* proces testování agenta pro 64bitová architektura.

## <a name="bind-a-test-controller-to-a-network-adapter"></a>Vazba testovacího kontroléru na síťový adaptér

Při pokusu o nastavení testovacího agenta, může dojít k následující chybě:

**Došlo k chybě 8110. Nelze se připojit k počítači určenému kontroleru nebo přístup k objektu řadiče.**

Tuto chybu může způsobovat instalace testovacího kontroléru na počítači, který má více než jeden síťový adaptér.

> [!NOTE]
> Je také možné úspěšně nainstalovat testové agenty a tento problém se nezobrazují až do pokusu o spuštění testu.

Chcete-li vyřešit tuto chybu, je třeba svázat testovací kontrolér na jeden ze síťových adaptérů. Je nutné nastavit `BindTo` vlastnost na testovací kontrolér a potom změnit testovacího agenta k odkazování na testovací kontrolér podle IP adresy místo podle názvu. Kroky jsou k dispozici v následujících postupech.

### <a name="to-obtain-the-ip-address-of-the-network-adapter"></a>Chcete-li získat IP adresu síťového adaptéru

1.  Zvolte **Start**a klikněte na tlačítko **spustit**.

     **Spustit** se zobrazí dialogové okno.

2.  Typ `cmd` a klikněte na tlačítko **OK**.

     Otevře se příkazový řádek.

3.  Typ `ipconfig /all`.

     Se zobrazují IP adresy pro síťové adaptéry. Zaznamenejte adresu IP síťového adaptéru, který chcete vytvořit vazbu řadiče.

### <a name="to-bind-a-test-controller-to-a-network-adapter"></a>Vazba testovacího kontroléru na síťový adaptér

1.  Zastavte službu testovacího řadiče. Na příkazovém řádku zadejte `net stop vsttcontroller`.

2.  Otevřete soubor *QTController.exe.config*. Tento soubor je umístěn v *% ProgramFiles (x86) %\Microsoft Visual Studio\2017\Enterprise\Common7\IDE*.

3.  Přidat položku pro `BindTo` vlastností do nastavení aplikace. Zadejte IP adresu, kterou chcete vytvořit vazbu řadiče do síťového adaptéru. Váš kód by měl vypadat takto:

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

4.  Uložte soubor.

5.  Spusťte službu testovacího řadiče. Na příkazovém řádku zadejte `net start vsttcontroller`.

### <a name="to-connect-a-test-agent-to-a-bound-controller"></a>Pro připojení testovacího agenta ke kontroléru vazby

-   Spusťte instalaci testovacího agenta znovu. Tentokrát, zadejte IP adresu testovacího kontroléru, nikoli název řadiče testu.

To platí pro testovací kontrolér, službu testovacího agenta a proces testovacího agenta. `BindTo` Musí být nastavena vlastnost pro každý proces, který běží na počítači, který má více než jeden síťový adaptér. Postup pro nastavení `BindTo` vlastnost je stejný pro všechny tři procesy, jak je uvedeno výše pro řadič testu. K nastavení úrovní protokolování pro službu testovacího agenta a proces testovacího agenta použijte konfigurační soubory, které jsou uvedeny v [nastavení úrovně protokolování v počítači řadiče testu](#set-the-logging-level-on-a-test-controller-computer).

## <a name="see-also"></a>Viz také:

- [Kontrolery testů a testovací agenti](../test/configure-test-agents-and-controllers-for-load-tests.md)
