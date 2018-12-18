---
title: Konfigurovat testovacího agenta
ms.date: 09/18/2018
ms.topic: conceptual
helpviewer_keywords:
- agents, configuring for interaction with desktop
ms.assetid: 3a94dd07-6d17-402c-ae8f-7947143755c9
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: f657babf33c315be2760cf59f3ec57525643f70e
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2018
ms.locfileid: "52894570"
---
# <a name="how-to-set-up-your-test-agent-to-run-tests-that-interact-with-the-desktop"></a>Postupy: nastavení testovacího agenta pro spouštění testů komunikujících s plochou

Pokud chcete spustit automatizované testy, které spolupracují s plochou, musíte nastavit vašeho agenta ke spuštění jako proces místo jako služba. Například pokud chcete spustit programový test UI vzdáleně pomocí testovacího kontroléru a testovacího agenta nebo chcete spustit test a zachytit video zaznamenané při spuštění, musíte vytvořit agenta pro spuštění jako proces. Při přiřazení agentů k rolím v nastavení testu pomocí sady Visual Studio nebo přiřazení agentů k rolím v prostředí s použitím nástroje Microsoft Test Manager, je nutné změnit nastavení pro všechny agenty přiřazené k rolím, které musí provádět interakci s plochou.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!WARNING]
> Pokud používáte Microsoft Test Manager k nastavení testovacího prostředí, instalaci testovacího agenta. Můžete určit **Průvodci vytvořením prostředí** chcete nakonfigurovat některý z role, které chcete spustit kódované testy uživatelského rozhraní.

> [!IMPORTANT]
> Počítač, na kterém běží agent, na kterém chcete spustit programové testy UI nelze uzamknout nebo je u něj aktivní spořič obrazovky.

Pokud používáte programové testy uživatelského rozhraní, které spouští prohlížeč, účet služby pro testovacího agenta slouží ke spouštění prohlížeče. Tento účet služby musí být stejný jako uživatelský účet, který je aktivním uživatelem tohoto počítače. Pokud není stejný uživatelský účet, prohlížeč se nespustí.

> [!IMPORTANT]
> Pokud používáte programový test UI, který spouští prohlížeč jako část definice sestavení, účet služby pro službu sestavení slouží ke spouštění prohlížeče. Tento účet služby musí být stejný jako uživatelský účet, který je aktivním uživatelem tohoto počítače. Pokud není stejný uživatelský účet, prohlížeč se nespustí.

Následujícím postupem nastavte všechny agenty, které jsou přiřazeny k roli, která provede úkol vyžadující interakci s plochou.

## <a name="to-set-up-an-agent-to-run-as-a-process"></a>Nastavení agenta ke spuštění jako procesu

1. Chcete-li konfigurovat testovacího agenta, který jste nainstalovali ke spuštění jako proces, přejděte na **Start** > **konfigurační nástroj testovacího agenta**.

   **Konfigurace testovacího agenta** se zobrazí dialogové okno.

   ![Konfigurovat testovacího agenta sady Visual Studio](media/configure-test-agent.png)

2. Vyberte **interaktivní proces**. Testovací agent bude spuštěn jako proces místo jako služba. Zvolte **Další**.

3. Zadejte uživatelské jméno a heslo pro uživatele, který se spustí proces testovacího agenta.

   > [!NOTE]
   > - Uživatel, který jste přidali ke spouštění procesu musí rovněž přidán jako člen skupiny TeamTestAgentService v počítači pro testovací kontrolér tohoto agenta. Pokud je tento uživatel aktuálním uživatelem, při přidání tohoto uživatele do počítače řadiče testů musíte odhlásit nebo restartovat.
   > - Hesla s hodnotou Null nejsou pro uživatelské účty podporována.
   > - Pokud chcete použít IntelliTrace nebo data emulace sítě a diagnostický adaptér, musí být uživatelský účet členem skupiny Administrators. Pokud počítač, na kterém je spuštěn testovací agent je spuštěn operační systém, který má nejméně privilegovaný uživatelský účet, musíte také spustit jako správce (se zvýšenými oprávněními). Pokud uživatelské jméno agenta není ve službě agenta, pokusí se ho přidat, což vyžaduje oprávnění testovacího kontroléru.
   > - Uživatel pokouší použít testovací kontrolér musí být účet uživatelé testovacího kontroléru nebo nebudou moci spouštět v kontroléru testy.

4. Pokud chcete mít jistotu, že počítač, který s testovacím agentem může spouštět testy po restartování, můžete nastavit počítač pro automatické přihlášení jako uživatel – testovací agent. Vyberte **automatické přihlášení**. Toto uloží uživatelské jméno a heslo v zašifrované podobě v registru.

   > [!NOTE]
   > Pokud jsou připojeny k testovacím prostředí pomocí vzdálené plochy nebo připojení jako Host, může dojít k častým, neočekávaným odpojením. Jednou z možných příčin ztráty připojení je, že je počítač nakonfigurovaný pro automatické přihlášení do sítě.

5. Chcete-li mít jistotu, že spořič obrazovky je zakázán, protože to může narušit jakékoli automatizované testy, které musí spolupracovat s plochou, vyberte **Ujistěte se, že spořič obrazovky je zakázán**.

   > [!WARNING]
   > Pokud automatické přihlášení nebo zakázání spořiče obrazovky, vznikají bezpečnostní rizika. Povolením automatického protokolování na můžete povolit ostatním uživatelům spustit tento počítač a použít účet, který se přihlásí automaticky. Pokud zakážete spořič obrazovky, počítač nemusí vyzvat uživatele k přihlášení k odemknutí počítače. Umožňuje všem uživatelům přístup k počítači, pokud mají fyzický přístup k počítači. Pokud povolíte tyto funkce v počítači, by měl Ujistěte se, že tyto počítače byly fyzicky zabezpečeny. Například tyto počítače jsou umístěny ve fyzicky zabezpečeném prostředí. Pokud zrušíte výběr **Ujistěte se, že spořič obrazovky je zakázán**, nepovolíte spořič obrazovky.

   Chcete-li agenta změnit zpět tak, aby se spouštěl jako služba, můžete použít tento nástroj a vybrat **služby**.

6. Chcete-li změny použít, zvolte **použít nastavení**.

   A **souhrnné informace o konfiguraci** se zobrazí dialogové okno, které zobrazuje stav všech kroků konfigurace testovacího agenta.

7. Zavřete **souhrnné informace o konfiguraci** dialogového okna zvolte **zavřete**. Klikněte na tlačítko **zavřete** zavřete **Test Agent Configuration Tool**.

   > [!NOTE]
   > Existuje ikona v oznamovací oblasti, která běží na počítači pro testovacího agenta, který je spuštěn jako proces. Zobrazuje stav testovacího agenta. Můžete spustit, zastavit nebo restartovat agenta, pokud je spuštěn jako proces, který používá tento nástroj. Chcete-li spustit testovacího agenta jako proces, pokud není spuštěn, zvolte **Start** > **sady Visual Studio** > **Microsoft Visual Studio Test Agent**.

   Pokud testovací kontrolér pro tento testovací agent je registrován s Team Foundation Server, se zobrazí stav testovacího agenta, který je spuštěn jako interaktivní proces **řadiče** zobrazení v **centra testovacích prostředí**nástroje Microsoft Test Manager. Je uvedený s podobě hvězdičky k označení, že je spuštěn jako interaktivní proces. Chcete-li restartovat tohoto testovacího agenta, musíte použít nástroj, který se spustí na počítači pro testovacího agenta a ne **řadiče** zobrazení.

## <a name="see-also"></a>Viz také:

- [Instalace a konfigurace testovacích agentů](../test/lab-management/install-configure-test-agents.md)