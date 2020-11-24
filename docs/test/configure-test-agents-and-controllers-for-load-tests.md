---
title: Konfigurace testovacích agentů/řadičů testů pro zátěžové testy
description: Přečtěte si, jak může Visual Studio vytvořit simulované zatížení pomocí fyzických nebo virtuálních počítačů, aby se vygenerovalo více zátěže, než může jeden počítač vygenerovat samostatně.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, test agents and controllers
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e70c1f3783945fbea00816d961f8ae6518ff726b
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2020
ms.locfileid: "95442609"
---
# <a name="overview-of-test-agents-and-test-controllers-for-running-load-tests"></a>Přehled testovacích agentů a testovacích kontrolérů pro spouštění zátěžových testů

Visual Studio může generovat simulované zatížení vaší aplikace pomocí fyzických nebo virtuálních počítačů. Tyto počítače musí být nastavené jako jeden testovací kontrolér a jeden nebo více testovacích agentů. Testovací kontrolér a testovací agenty lze použít ke generování větší zátěže, než je jeden počítač, může generovat samostatně.

> [!NOTE]
> Můžete také použít cloudové zátěžové testování k poskytnutí virtuálních počítačů, které generují zatížení mnoha uživatelů, kteří přistupují k webu. Použití testovacího kontroléru nebo instalace testovacího agenta u virtuálních počítačů hostovaných v cloudu se ale nepodporuje. Přečtěte si další informace o cloudovém zátěžovém testování při [spuštění zátěžových testů pomocí Azure test Plans](/azure/devops/test/load-test/get-started-simple-cloud-load-test?view=vsts&preserve-view=true).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="load-simulation-architecture"></a>Architektura simulace zátěže

Architektura simulace zátěže se skládá z klientské aplikace Visual Studio, testovacího kontroléru a testovacích agentů.

- Klient se používá pro vývoj a spouštění testů a zobrazování jejich výsledků.

- Testovací kontrolér slouží ke správě testovacích agentů a shromažďování výsledků testu.

- Testovací agenty se používají ke spouštění testů a shromažďování dat včetně systémových informací a dat profilování ASP.NET definovaných v nastavení testu.

Tato architektura přináší následující výhody:

- Možnost škálovat generování zátěže přidáváním dalších testovacích agentů k testovacímu kontroléru.

- Pružnost při instalaci softwaru klientu, testovacího kontroléru a testovacího agentu na stejném počítači i různých počítačích. Například:

   **Místní konfigurace:**

  - Počítač 1: Visual Studio, kontrolér, agent.

    ![Místní počítač s použitím řadiče a agenta](./media/load-test-configa.png)

    **Typická Vzdálená konfigurace:**

  - Počítač 1 a 2: Visual Studio (více testerů může používat stejný kontrolér).

  - Počítač 3: Kontrolér (může mít nainstalovány také agenty).

  - Machine4-n: agenti nebo agenti přidružení k řadiči v Machine3.

    ![Vzdálené počítače s použitím řadiče a agentů](./media/load-test-configb.png)

Přestože testovací kontrolér obvykle spravuje několik testovacích agentů, jeden agent může být přidružen pouze k jednomu kontroléru. Každý testovací agent může být sdílen týmem vývojářů. Tato architektura umožňuje snadno zvýšit počet testovacích agentů a generovat tak větší zátěž.

## <a name="test-agent-and-test-controller-interaction"></a>Interakce testovacího agenta a testovacího kontroleru

Testovací kontrolér spravuje sadu testovacích agentů pro spouštění testů. Testovací kontrolér komunikuje s testovacími agenty, aby zahájil testy, zastavila testy, sledoval stav testovacího agenta a shromáždil výsledky testů.

### <a name="test-controller"></a>Kontroler testů

Testovací kontrolér poskytuje obecnou architekturu pro spouštění testů a zahrnuje speciální funkce pro spouštění zátěžových testů. Testovací kontrolér odesílá zátěžový test všem testovacím agentům a čeká, dokud není test inicializován všemi agenty. Jsou-li všichni testovací agenti připraveni, řadič testů jim odešle zprávu, aby zahájili test.

### <a name="test-agent"></a>Testovací agent

Testovací agent je spouštěn jako služba, která naslouchá požadavkům testovacího kontroléru na spuštění nového testu. Když testovací agent obdrží žádost, služba testovacího agenta spustí proces, ve kterém budou testy spuštěny. Každý testovací agent spouští stejný zátěžový test.

Testovacím agentům je správcem přiřazována váha a zátěž je přerozdělena dle váhy jednotlivých agentů. Pokud má například testovací agent 1 váhu 30 a testovací agent 2 váhu 70, přičemž je zátěž nastavena na 1000 uživatelů, testovací agent 1 simuluje 300 virtuálních uživatelů, zatímco testovací agent 2 jich simuluje 700. Viz [Správa testovacích kontrolérů a testovacích agentů se sadou Visual Studio](../test/manage-test-controllers-and-test-agents.md).

Testovací agent přijímá sadu testů a sadu parametrů simulace jako vstup. Klíčovým konceptem je, že testy jsou nezávislé na počítači, na kterém jsou spuštěny.

## <a name="test-controller-and-test-agent-connection-points"></a>Testovací kontrolér a body připojení testovacího agenta

Následující obrázek znázorňuje spojovací body mezi testovacím kontrolérem, testovacím agentem a klientem. Popisuje, které porty se používají pro příchozí a odchozí připojení a také omezení zabezpečení používaná na těchto portech.

![Testovací kontrolér a porty a zabezpečení testovacího agenta](./media/test-controller-agent-firewall.png)

Další informace najdete v tématu [Konfigurace portů pro řadiče testů a testovací agenty](../test/configure-ports-for-test-controllers-and-test-agents.md).

## <a name="test-controller-and-agent-installation-information"></a>Informace o kontroleru testů a instalaci agenta

Důležité informace o požadavcích na hardware a software pro testovací kontroléry a testovací agenty, postupy pro jejich instalaci a konfiguraci prostředí pro zajištění optimálního výkonu najdete v tématu [instalace a konfigurace testovacích agentů](../test/lab-management/install-configure-test-agents.md).

## <a name="use-the-test-controller-and-test-agent-with-unit-tests"></a>Použití testovacího kontroléru a testovacího agenta s testováním částí

Po instalaci testovacího kontroléru a jednoho nebo více agentů lze v nastavení zátěžových testů určit, zda má být u kontroléru používáno vzdálené spuštění. Dále lze v nastavení testu určit datové a diagnostické adaptéry, které mají být použity spolu s rolí přidruženou k agentům.

## <a name="see-also"></a>Viz také

- [Instalace a konfigurace testovacích agentů](../test/lab-management/install-configure-test-agents.md)
