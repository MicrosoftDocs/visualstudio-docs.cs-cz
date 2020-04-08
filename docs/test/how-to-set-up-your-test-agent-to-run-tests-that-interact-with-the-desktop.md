---
title: Konfigurace testovacího agenta
ms.date: 09/18/2018
ms.topic: conceptual
helpviewer_keywords:
- agents, configuring for interaction with desktop
ms.assetid: 3a94dd07-6d17-402c-ae8f-7947143755c9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: dc00598595ee3e3d958562682900bde9aad2a353
ms.sourcegitcommit: 5d1b2895d3a249c6bea30eb12b0ad7c0f0862d85
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2020
ms.locfileid: "80880179"
---
# <a name="how-to-set-up-your-test-agent-to-run-tests-that-interact-with-the-desktop"></a>Postup: Nastavení testovacího agenta pro spuštění testů, které interagují s plochou

::: moniker range="vs-2017"
Pokud chcete spustit automatizované testy, které interagují s plochou, musíte nastavit agenta spustit jako proces namísto služby. Například pokud chcete spustit kódovaný test uživatelského postupu vzdáleně pomocí testovacího řadiče a testovacího agenta, nebo chcete spustit test a zachytit záznam videa při jeho spuštění, musíte nastavit agenta spustit jako proces. Při přiřazení agentů k rolím v nastavení testu pomocí sady Visual Studio nebo přiřazujete agenty k rolím ve vašem prostředí pomocí Microsoft Test Manager, je nutné změnit nastavení pro všechny agenty přiřazené k rolím, které mají pracovat s plochou.
::: moniker-end
::: moniker range=">=vs-2019"
Pokud chcete spustit automatizované testy, které interagují s plochou, musíte nastavit agenta spustit jako proces namísto služby. Například pokud chcete spustit kódovaný test uživatelského postupu vzdáleně pomocí testovacího řadiče a testovacího agenta, nebo chcete spustit test a zachytit záznam videa při jeho spuštění, musíte nastavit agenta spustit jako proces. Při přiřazení agentů k rolím v nastavení testu pomocí sady Visual Studio je nutné změnit nastavení pro všechny agenty přiřazené k rolím, které mají pracovat s plochou.
::: moniker-end

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

::: moniker range="vs-2017"
> [!WARNING]
> Pokud k nastavení testovacího prostředí použijete Správce testů společnosti Microsoft, nainstaluje testovacího agenta. V **Průvodci vytvořením prostředí** můžete určit, že chcete nakonfigurovat jednu z rolí pro spuštění kódovaných testů ui.
:::moniker-end

> [!IMPORTANT]
> Počítač, ve kterém je spuštěn agent, ve kterém chcete spustit programové testy ui, nelze uzamknout nebo mít aktivní spořič obrazovky.

Pokud používáte programové testy ui, které spouštějí prohlížeč, účet služby pro testovacího agenta se používá ke spuštění tohoto prohlížeče. Tento účet služby musí být stejný jako uživatelský účet, který je aktivním uživatelem v tomto počítači. Pokud se nejedná o stejný uživatelský účet, prohlížeč se nespustí.

> [!IMPORTANT]
> Pokud používáte kódovaný test ui, který spustí prohlížeč jako součást definice sestavení, účet služby pro službu sestavení se používá ke spuštění tohoto prohlížeče. Tento účet služby musí být stejný jako uživatelský účet, který je aktivním uživatelem v tomto počítači. Pokud se nejedná o stejný uživatelský účet, prohlížeč se nespustí.

Pomocí následujícího postupu nastavte všechny agenty, kteří jsou přiřazeni k roli, která provádí úlohu, která potřebuje interakci s plochou.

## <a name="to-set-up-an-agent-to-run-as-a-process"></a>Nastavení agenta tak, aby byl spuštěn jako proces

1. Chcete-li nakonfigurovat testovacího agenta, který jste nainstalovali, aby byl spuštěn jako proces, přejděte na **nástroj Spustit** > **nástroj pro konfiguraci agenta testu**.

   Zobrazí se dialogové okno **Konfigurovat testovacího agenta.**

   ![Konfigurace testovacího agenta pro visual studio](media/configure-test-agent.png)

2. Vyberte **interaktivní proces**. Testovací agent bude spuštěn jako proces namísto služby. Zvolte **Další**.

3. Zadejte uživatelské jméno a heslo pro uživatele, který spustí proces testovacího agenta.

   > [!NOTE]
   > - Uživatel, kterého přidáte ke spuštění procesu, musí být také přidán jako člen skupiny TeamTestAgentService v počítači pro testovací řadič pro tohoto agenta. Pokud je tento uživatel aktuálním uživatelem, musíte se při přidání tohoto uživatele do počítače testovacího řadiče odhlásit nebo restartovat.
   > - Nulová hesla nejsou pro uživatelské účty podporována.
   > - Pokud chcete použít IntelliTrace nebo data emulace sítě a diagnostický adaptér, musí být uživatelský účet členem skupiny Administrators. Pokud počítač, ve který běží testovací agent, používá operační systém, který má nejméně privilegovaný uživatelský účet, musíte jej spustit také jako správce (se zvýšenými oprávněními). Pokud uživatelské jméno agenta není ve službě agenta, pokusí se jej přidat, což vyžaduje oprávnění na testovacím řadiči.
   > - Uživatel, který se pokouší použít testovací řadič, musí být v účtu Users testovacího řadiče, jinak nebude moci spustit testy proti kontroleru.

4. Chcete-li se ujistit, že počítač, který má testovacího agenta, může po restartování spustit testy, můžete nastavit, aby se počítač automaticky přihlašoval jako uživatel testovacího agenta. Vyberte **Možnost Přihlásit se automaticky**. Tím bude uživatelské jméno a heslo v registru ukládáno v zašifrované podobě.

   > [!NOTE]
   > Pokud jste připojeni k testovacímu prostředí pomocí vzdálené plochy nebo připojení založeného na hostu, může docházet k častým a neočekávaným odpojením. Jednou z možných příčin ztráty připojení je, že počítač je nakonfigurován tak, aby se automaticky přihlašoval k síti.

5. Chcete-li se ujistit, že je spořič obrazovky zakázán, protože by to mohlo narušit všechny automatizované testy, které musí pracovat s plochou, vyberte **možnost Zajistit zakázání spořiče obrazovky**.

   > [!WARNING]
   > Pokud se automaticky přihlásíte nebo zakážete spořič obrazovky, existují bezpečnostní rizika. Povolením automatického přihlášení povolíte ostatním uživatelům spuštění tohoto počítače a možnost používat účet, který se automaticky přihlásí. Pokud zakážete spořič obrazovky, počítač nemusí vyzvat uživatele k přihlášení k odemknutí počítače. To umožňuje komukoli přístup k počítači, pokud mají fyzický přístup k počítači. Pokud tyto funkce povolíte v počítači, měli byste se ujistit, že tyto počítače jsou fyzicky zabezpečené. Tyto počítače jsou například umístěny ve fyzicky zabezpečené laboratoři. Pokud zrušte **zaškrtnutí políčka Zajistit zakázání spořiče obrazovky**, nepovolíte spořič obrazovky.

   Chcete-li změnit agenta zpět spustit jako služba, můžete použít tento nástroj a vyberte **služba**.

6. Chcete-li změny použít, zvolte **Použít nastavení**.

   Zobrazí se dialogové okno **Souhrn konfigurace,** které zobrazuje stav jednotlivých kroků konfigurace testovacího agenta.

7. Chcete-li zavřít dialogové okno **Souhrn konfigurace,** zvolte **Zavřít**. Pak zvolte **Zavřít** znovu, chcete-li zavřít **nástroj pro konfiguraci testovacího agenta**.

   > [!NOTE]
   > V počítači je spuštěna ikona oznamovací oblasti pro testovacího agenta, který je spuštěn jako proces. Zobrazuje stav testovacího agenta. Agenta můžete spustit, zastavit nebo restartovat, pokud je spuštěn jako proces pomocí tohoto nástroje. Chcete-li spustit testovacího agenta jako proces, pokud není spuštěn, zvolte **Spustit** > **Visual Studio** > **Microsoft Visual Studio Test Agent**.

   ::: moniker range="vs-2017"
   Pokud je testovací řadič pro tohoto testovacího agenta registrován na serveru Team Foundation, zobrazí se stav testovacího agenta, který je spuštěn jako interaktivní proces, v zobrazení **Řadiče** v **Centru testovacího prostředí** pro Správce testů společnosti Microsoft. Je uveden s předchozím symbolem hvězdičky, který označuje, že je spuštěn jako interaktivní proces. Chcete-li restartovat tohoto testovacího agenta, musíte použít nástroj, který běží v počítači pro testovacího agenta a nikoli zobrazení **Řadiče.**
   ::: moniker-end

## <a name="see-also"></a>Viz také

- [Instalace a konfigurace testovacích agentů](../test/lab-management/install-configure-test-agents.md)
