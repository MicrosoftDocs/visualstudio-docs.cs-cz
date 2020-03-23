---
title: Konfigurace portů pro testovací řadiče a testovací agenty
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- firewalls, configuring for test agents
- firewalls, configuring for test controllers
- test agents, firewalls
- test controllers, firewalls
- agents, firewalls
- controllers, firewalls
ms.assetid: 211edbd7-9fe4-4251-ba85-8bec4363261b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2228f5ac4dce4743fa6dafbb321f0106b5d6cc11
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595940"
---
# <a name="configure-ports-for-test-controllers-and-test-agents"></a>Konfigurace portů pro testovací řadiče a testovací agenty

Můžete změnit výchozí příchozí porty používané testovacím řadičem, testovacím agentem a klientem. To může být nezbytné, pokud se pokoušíte použít testovací řadič, testovacího agenta nebo klienta společně s jiným softwarem, který je v konfliktu s nastavením portu. Dalším důvodem pro změnu portů je z důvodu omezení brány firewall mezi testovacím řadičem a klientem. V takovém případě můžete chtít ručně nakonfigurovat port tak, aby vyhovoval povolení pro bránu firewall tak, aby testovací řadič mohl odeslat výsledky klientovi.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Následující obrázek znázorňuje spojovací body mezi testovacím řadičem, testovacím agentem a klientem. Popisuje, které porty se používají pro příchozí a odchozí připojení, stejně jako omezení zabezpečení používané na těchto portech.

![Testovací řadič a porty testovacího agenta a zabezpečení](../test/media/test-controller-agent-firewall.png)

## <a name="incoming-connections"></a>Příchozí připojení

Výchozí port používaný testovacím řadičem je 6901 a výchozí port testovacího agenta je 6910. Klient používá náhodný port ve výchozím nastavení, který se používá k příjmu výsledků testu z testovacího řadiče. Pro všechna příchozí připojení testovací řadič ověří volající ho a ověří, zda patří do určité skupiny zabezpečení.

- **Testovací řadič** Příchozí připojení jsou na portu TCP 6901. V případě potřeby můžete nakonfigurovat příchozí port. Další informace naleznete [v tématu Konfigurace příchozích portů](#configure-the-incoming-ports).

    Testovací řadič musí být schopen provést odchozí připojení k testovacím agentům a klientovi.

    > [!NOTE]
    > Testovací řadič potřebuje otevřené příchozí připojení **pro sdílení souborů a tiskáren.**

- **Testovací agent** Příchozí připojení jsou na portu TCP 6910. V případě potřeby můžete nakonfigurovat příchozí port. Další informace naleznete [v tématu Konfigurace příchozích portů](#configure-the-incoming-ports).

   Testovací agent musí být schopen provést odchozí připojení k testovacímu řadiči.

- **Klient** Ve výchozím nastavení se pro příchozí připojení používá náhodný port TCP. V případě potřeby můžete nakonfigurovat příchozí port. Další informace naleznete [v tématu Konfigurace příchozích portů](#configure-the-incoming-ports).

   Při prvním pokusu o připojení ke klientovi může být upozornění brány firewall.

   V systému Windows Server 2008 jsou oznámení brány firewall ve výchozím nastavení zakázána a je nutné ručně přidat výjimky brány firewall pro klientské programy (*devenv.exe*, *mstest.exe*, *mlm.exe*), aby mohla přijímat příchozí připojení.

## <a name="outgoing-connections"></a>Odchozí připojení

Náhodné porty TCP se používají pro všechna odchozí připojení.

- **Testovací řadič** Testovací řadič musí být schopen provést odchozí připojení k agentům a klientovi.

- **Testovací agent** Testovací agent musí být schopen provést odchozí připojení k řadiči.

- **Klient** Klient musí být schopen provést odchozí připojení k řadiči.

## <a name="configure-the-incoming-ports"></a>Konfigurace příchozích portů

Postupujte podle těchto pokynů a nakonfigurujte porty pro testovací řadič a testovací agenty.

- **Služba řadiče** Upravte hodnotu portu úpravou souboru *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\QTCcontroller.exe.config:*

    ```xml
    <appSettings>
      <add key="ControllerServicePort" value="6901"/>
    </appSettings>
    ```

- **Služba agenta** Upravte port úpravou souboru *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\QTAgentService.exe.config:*

    ```xml
    <appSettings>
      <add key="AgentServicePort" value="6910"/>
    </appSettings>
    ```

- **Klient** Pomocí editoru registru přidejte následující hodnoty registru (**DWORD).** Klient použije jeden z portů ze zadaného rozsahu pro příjem dat z testovacího řadiče:

     **HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\VisualStudio\12.0\EnterpriseTools\QualityTools\ListenPortRange\PortRangeStart**

     **HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\VisualStudio\12.0\EnterpriseTools\QualityTools\ListenPortRange\PortRangeEnd**

## <a name="see-also"></a>Viz také

- [Instalace a konfigurace testovacích agentů](../test/lab-management/install-configure-test-agents.md)
