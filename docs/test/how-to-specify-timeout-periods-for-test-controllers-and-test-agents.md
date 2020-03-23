---
title: Období časového ochacovaní pro testovací řadiče a testovací agenty
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- agents, configuring
- agetns, timeouts
- controllers, configuring
- controllers, timeouts
ms.assetid: 777d0db5-0073-458a-a2a3-58b1c1f24c60
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 64ce566369f2c60a52e9026e8f92fc30836d523c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75594757"
---
# <a name="how-to-specify-timeout-periods-for-test-controllers-and-test-agents"></a>Postup: Zadejte časové období pro testovací řadiče a testovací agenty

Řadič testu i testovací agent mají několik nastavení časového plánu, které určují, jak dlouho by měly čekat na odpovědi od sebe navzájem nebo ze zdroje dat před selháním s chybou. Za určitých okolností může být nutné upravit hodnoty časového času tak, aby vyhovovaly potřebám topologie nebo jiných problémů prostředí. Chcete-li upravit hodnoty časového času, upravte konfigurační soubor XML, který je přidružen k testovacímu řadiči nebo testovacímu agentovi, jak je uvedeno v následujících postupech.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Chcete-li upravit testovací řadič nebo různá nastavení časového času testovacího agenta, upravte následující konfigurační soubory pomocí názvů klíčů a hodnot v tabulkách:

- Řadič testu: *QTController.exe.config*

    |Název klíče|Popis|Hodnota|
    |-|-----------------|-|
    |AgentConnectionTimeoutInSeconds|Počet sekund čekání na požadavek ping agenta před připojení mj.|"n" sekund.|
    |V několikasekundách agenta SyncTimeout|Při spuštění spuštění testu synchronizace, počet sekund čekat na všechny agenty synchronizovat před přerušením spuštění.|"n" sekund.|
    |Inicialize agentaTimeout|Počet sekund čekat na všechny agenty a jejich sběrače dat inicializovat na začátku testovacího běhu, před přerušením spuštění testu. Tato hodnota by měla být přiměřeně velká, pokud používáte sběrače dat.|"n" sekund. Výchozí hodnota: "120" (dvě minuty).|
    |AgentCleanupTimeout|Počet sekund čekat na všechny agenty a jejich sběrače dat vyčistit, před dokončením testovacího běhu. Tato hodnota by měla být přiměřeně velká, pokud používáte sběrače dat.|"n" sekund. Výchozí hodnota: "120" (dvě minuty).|

- Testovací agent: *QTAgentService.exe.config*

    |Název klíče|Popis|Hodnota|
    |-|-----------------|-|
    |ControllerConnectionPeriodInSeconds|Počet sekund mezi pokusy o připojení k řadiči.|"n" sekund. Výchozí hodnota: "30" (třicet sekund).|
    |Vzdálené časovky|Maximální doba vzdáleného volání může trvat v sekundách.|"n" sekund. Výchozí hodnota: "600" (deset minut).|
    |StopTestRunCallTimeoutVsekundách|Počet sekund čekání na volání zastavit spuštění testu.|"n" sekund. Výchozí hodnota: "120" (dvě minuty).|
    |GetCollectorDataTimeout|Počet sekund čekání na kolekcí dat.|"n" sekund. Výchozí hodnota: "300" (pět minut).|

## <a name="to-specify-agent-timeout-options-for-a-test-controller"></a>Určení možností časového časového času agenta pro testovací řadič

1. Otevřete konfigurační soubor XML *QTCcontroller.exe.config* umístěný v *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE*.

2. Vyhledejte `<appSettings>` značku.

    ```xml
    <appSettings>
      <add key="LogSizeLimitInMegs" value="20"/>
      <add key="AgentConnectionTimeoutInSeconds" value="120"/>
      <add key="AgentSyncTimeoutInSeconds" value="300"/>
      <add key="ControllerServicePort" value="6901"/>
      <add key="ControllerUsersGroup" value="TeamTestControllerUsers"/>
      <add key="ControllerAdminsGroup" value="TeamTestControllerAdmins"/>
      <add key="CreateTraceListener" value="no"/>
    </appSettings>
    ```

3. Upravte existující hodnotu pro jeden z klíčů časového času testovacího řadiče. Můžete například změnit výchozí hodnotu `AgentConnectionTimeoutInSeconds` klíče ze dvou minut na tři minuty:

    ```xml
    <add key="AgentConnectionTimeoutInSeconds" value="180"/>
    ```

    -nebo-

    Přidejte další klíč a zadejte hodnotu časového času. Můžete například přidat `AgentInitializeTimeout` klíč do `<appSettings>` oddílu a zadat hodnotu pěti minut:

    ```xml
    <appSettings>
            <add key="AgentInitializeTimeout" value="300"/>
    </appSettings>
    ```

## <a name="to-specify-agent-timeout-options-for-a-test-agent"></a>Určení možností časového času agenta pro testovacího agenta

1. Otevřete konfigurační soubor XML *QTAgentService.exe.config* umístěný v *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE*.

2. Vyhledejte `<appSettings>` značku.

    ```xml
    <appSettings>
      <appSettings>
      <add key="LogSizeLimitInMegs" value="20"/>
      <add key="AgentServicePort" value="6910"/>
      <add key="ControllerConnectionPeriodInSeconds" value="30"/>
      <add key="StopTestRunCallTimeoutInSeconds" value="120"/>
      <add key="CreateTraceListener" value="no"/>
      <add key="GetCollectorDataTimeout" value="300"/>
    </appSettings>  </appSettings>
    ```

3. Upravte existující hodnotu pro jeden z klíčů časového času testovacího agenta. Můžete například změnit výchozí hodnotu `ControllerConnectionPeriodInSeconds` klíče z třiceti sekund na jednu minutu:

    ```xml
    <add key="ControllerConnectionPeriodInSeconds" value="60"/>
    ```

    -nebo-

    Přidejte další klíč a zadejte hodnotu časového času. Můžete například přidat `RemotingTimeoutSeconds` klíč do `<appSettings>` oddílu a zadat hodnotu patnácti minut:

    ```xml
    <appSettings>
            <add key=" RemotingTimeoutSeconds " value="900"/>
    </appSettings>
    ```

## <a name="see-also"></a>Viz také

- [Instalace a konfigurace testovacích agentů](../test/lab-management/install-configure-test-agents.md)
- [Změna nastavení protokolování zátěžového testu](../test/modify-load-test-logging-settings.md)
- [Konfigurace portů pro testovací řadiče a testovací agenty](../test/configure-ports-for-test-controllers-and-test-agents.md)
- [Postup: Svázání testovacího řadiče nebo testovacího agenta se síťovým adaptérem](../test/how-to-bind-a-test-controller-or-test-agent-to-a-network-adapter.md)
