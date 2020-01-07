---
title: Konfigurace portů pro testovací Kontroléry a testovací agenty
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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595940"
---
# <a name="configure-ports-for-test-controllers-and-test-agents"></a>Konfigurace portů pro testovací kontroléry a testovací agenty

Můžete změnit výchozí příchozí porty používané testovací kontrolér, testovacího agenta a klientem. To může být nutné v případě, že se pokoušíte použít testovací kontrolér, testovacího agenta nebo klienta spolu s dalším softwarem této je v konfliktu s nastavením portu. Dalším důvodem pro změnu portů je omezení brány firewall mezi řadičem testu a klientem. V tomto případě můžete ručně nakonfigurovat port, který chcete zpřístupnit jej pro bránu firewall tak, aby řadič testu mohl odesílat výsledky klientovi.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Následující obrázek znázorňuje spojovací body mezi řadičem testu, agentem testu a klienta. Poskytuje přehled o používaných portech pro příchozí a odchozí připojení, jakož i omezení zabezpečení použité na těchto portech.

![Testovací kontrolér a porty a zabezpečení testovacího agenta](../test/media/test-controller-agent-firewall.png)

## <a name="incoming-connections"></a>Příchozí připojení

Výchozí port používaný řadičem testu je 6901 a výchozí port agenta testu je 6910. Klient používá náhodný port ve výchozím nastavení, která se používá k získání výsledků testů z testovacího kontroléru. Pro všechna příchozí připojení řadič testu ověří volajícího a ověří, zda patří do konkrétní skupiny zabezpečení.

- **Testovací Kontrolér** příchozí připojení jsou na portu TCP 6901. Pokud potřebujete, můžete nakonfigurovat příchozí port. Další informace najdete v tématu [konfigurace příchozích portů](#configure-the-incoming-ports).

    Testovací kontrolér musí být schopen provést odchozí připojení k testovacímu agentovi a do klienta.

    > [!NOTE]
    > Testovací kontrolér potřebuje **souborů a tiskáren sdílení** otevřené připojení.

- **Testovací Agent** příchozí připojení jsou na portu TCP 6910. Pokud potřebujete, můžete nakonfigurovat příchozí port. Další informace najdete v tématu [konfigurace příchozích portů](#configure-the-incoming-ports).

   Testovací agent musí být schopen provést odchozí připojení ke kontroleru testů.

- **Klient** standardně náhodný port TCP používaný pro příchozí připojení. Pokud potřebujete, můžete nakonfigurovat příchozí port. Další informace najdete v tématu [konfigurace příchozích portů](#configure-the-incoming-ports).

   Pokud testovací kontrolér pokusí o připojení klienta první čas, může se zobrazit upozornění brány firewall.

   V systému Windows Server 2008 jsou upozornění brány firewall ve výchozím nastavení zakázána a je třeba ručně přidat výjimky brány Firewall pro klientské programy (*devenv.exe*, *mstest.exe*, *mlm.exe*) tak, aby mohl přijímat příchozí připojení.

## <a name="outgoing-connections"></a>Odchozí připojení

Pro všechny odchozí připojení se používají náhodné porty TCP.

- **Testovací Kontrolér** testovací kontrolér musí být schopen provést odchozí připojení k agentům a klientovi.

- **Testovací Agent** testovací agent musí být schopen provést odchozí připojení ke Kontroleru.

- **Klient** klienta musí být schopen provést odchozí připojení ke Kontroleru.

## <a name="configure-the-incoming-ports"></a>Konfigurace příchozích portů

Postupujte podle těchto pokynů ke konfiguraci portů pro testovací kontrolér a testovací agenty.

- **Službu řadiče** upravte hodnotu portu úpravou *% ProgramFiles (x86) %\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\QTCcontroller.exe.config* souboru:

    ```xml
    <appSettings>
      <add key="ControllerServicePort" value="6901"/>
    </appSettings>
    ```

- **Služba agenta** upravte port úpravou *% ProgramFiles (x86) %\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\QTAgentService.exe.config* souboru:

    ```xml
    <appSettings>
      <add key="AgentServicePort" value="6910"/>
    </appSettings>
    ```

- **Klient** přidat následující registru pomocí Editoru registru (**DWORD**) hodnoty. Klient použije jeden z portů v určeném rozsahu pro příjem dat z kontroleru testů:

     **HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\VisualStudio\12.0\EnterpriseTools\QualityTools\ListenPortRange\PortRangeStart**

     **HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\VisualStudio\12.0\EnterpriseTools\QualityTools\ListenPortRange\PortRangeEnd**

## <a name="see-also"></a>Viz také:

- [Instalace a konfigurace testovacích agentů](../test/lab-management/install-configure-test-agents.md)
