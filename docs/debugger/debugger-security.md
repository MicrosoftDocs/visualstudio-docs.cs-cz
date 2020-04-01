---
title: Zabezpečení ladicího programu | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], security
- debugger, security
- security [Visual Studio], debugging best practices
ms.assetid: d4fc3c43-e844-419c-8dbb-551cc2a9b09e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a89e60a47e5bab6580c78275357234bb9d3f1c56
ms.sourcegitcommit: 334024a43477290ecc610e70c80a0f772787a7d6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2020
ms.locfileid: "80527928"
---
# <a name="debugger-security"></a>Zabezpečení ladicího programu
Možnost ladit jiný proces vám dává extrémně široké pravomoci, které byste jinak neměli, zejména při vzdáleném ladění. Škodlivý ladicí program může způsobit rozsáhlé škody na ladění počítače.

 Mnoho vývojářů si však neuvědomuje, že bezpečnostní hrozba může také proudit v opačném směru. Je možné, že škodlivý kód v procesu ladění ohrozit zabezpečení ladicího stroje: existuje celá řada zneužití zabezpečení, které musí být chráněny proti.

## <a name="security-best-practices"></a>Doporučené postupy zabezpečení
 Existuje implicitní vztah důvěryhodnosti mezi kódem, který ladíte, a ladicím programem. Pokud jste ochotni něco ladit, měli byste být také ochotni jej spustit. Pointa je, že musíte být schopni důvěřovat tomu, co ladíte. Pokud nemůžete důvěřovat, pak byste neměli ladit, nebo byste měli ladit z počítače, který si můžete dovolit ohrozit, a v izolovaném prostředí.

 Aby se snížil potenciální prostor pro útok, ladění by mělo být zakázáno na výrobních počítačích. Ze stejného důvodu ladění by nikdy být povolena neomezeně dlouho.

### <a name="managed-debugging-security"></a>Spravované zabezpečení ladění
 Zde jsou některá obecná doporučení, která platí pro všechny spravované ladění.

- Při připojování k procesu nedůvěryhodného uživatele buďte opatrní: pokud tak učiníte, předpokládáte, že je důvěryhodný. Při pokusu o připojení k procesu nedůvěryhodného uživatele se zobrazí potvrzení dialogového okna upozornění zabezpečení s dotazem, zda se chcete k procesu připojit. "Důvěryhodní uživatelé" zahrnují vás a sadu standardních uživatelů běžně definovaných v počítačích, které mají nainstalovanou architekturu .NET Framework, jako je **například aspnet**, **localsystem**, **networkservice**a **localservice**. Další informace naleznete v [tématu Upozornění zabezpečení: Připojení k procesu vlastněného nedůvěryhodným uživatelem může být nebezpečné. Pokud následující informace vypadají podezřele nebo si nejste jisti, nepřipojujte se k tomuto procesu](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md).

- Buďte opatrní při stahování projektu z Internetu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]a jeho načítání do aplikace . To je velmi riskantní dělat i bez ladění. Když toto, předpokládáte, že projekt a kód, který obsahuje, jsou důvěryhodné.

  Další informace naleznete [v tématu Ladění spravovaného kódu](../debugger/debugging-managed-code.md).

### <a name="remote-debugging-security"></a>Vzdálené zabezpečení ladění
 Místní ladění je obecně bezpečnější než vzdálené ladění. Vzdálené ladění zvyšuje celkovou plochu, kterou lze sondovat.

 Visual Studio Vzdálené ladění Monitor (msvsmon.exe) se používá ve vzdálenéladění a existuje několik doporučení zabezpečení pro jeho konfiguraci. Upřednostňovaným způsobem konfigurace režimu ověřování je ověřování systému Windows, protože režim žádnéověřování není nezabezpečený.

 ![Dialogové okno Chyba](../debugger/media/dbg_err_remotepermissionschanged.png "DBG_ERR_RemotePermissionsChanged")

 Při použití režimu ověřování systému Windows mějte na paměti, že udělení oprávnění nedůvěryhodného uživatele k připojení k msvsmon uděluje nebezpečné, protože uživateli jsou udělena všechna oprávnění k počítači hostujícímu msvsmon.

 Neladí neznámý proces ve vzdáleném počítači: existují potenciální zneužití, které by mohly ovlivnit počítač se systémem ladicího programu nebo které by mohly ohrozit msvsmon. Pokud je absolutně nutné ladit neznámý proces, zkuste ladění místně a pomocí brány firewall, aby všechny potenciální hrozby lokalizovány.

 Informace o konfiguraci msvsmonu naleznete [v tématu Nastavení vzdáleného ladicího programu](../debugger/remote-debugging.md#bkmk_setup).

### <a name="web-services-debugging-security"></a>Zabezpečení ladění webových služeb
 Je bezpečnější ladit místně, ale protože pravděpodobně nemáte [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nainstalovaný na webovém serveru, místní ladění nemusí být praktické. Obecně platí, že ladění webových služeb se provádí vzdáleně, s výjimkou během vývoje, takže doporučení pro vzdálené ladění zabezpečení platí také pro ladění webových služeb. Zde jsou některé další doporučené postupy. Další informace naleznete [v tématu Ladění webových služeb XML](https://msdn.microsoft.com/library/c900b137-9fbd-4f59-91b5-9c2c6ce06f00).

- Nepovolujte ladění na webovém serveru, který byl ohrožen.

- Před laděním se ujistěte, že je webový server zabezpečený. Pokud si nejste jisti, že je zabezpečený, neladit.

- Buďte obzvláště opatrní, pokud ladíte webovou službu, která je vystavena v Síti Internet.

### <a name="external-components"></a>Externí součásti
 Uvědomte si stav důvěryhodnosti externích součástí, se kterými program spolupracuje, zejména pokud jste kód nenapsali. Také být vědomi součásti, které [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nebo ladicí program může použít.

### <a name="symbols-and-source-code"></a>Symboly a zdrojový kód
 Dva [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nástroje, které vyžadují přemýšlení o zabezpečení, jsou následující:

- Zdrojový server, který poskytuje verze zdrojového kódu z úložiště zdrojového kódu. To je užitečné, pokud nemáte aktuální verzi zdrojového kódu programu. [Upozornění zabezpečení: Ladicí program musí provést nedůvěryhodný příkaz](../debugger/security-warning-debugger-must-execute-untrusted-command.md).

- Symbol Server, který se používá k dodání symboly potřebné k ladění selhání během volání systému.

  Viz [Určení symbolu (.pdb) a zdrojových souborů](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)

## <a name="see-also"></a>Viz také
- [Nastavení a příprava ladicího programu](../debugger/debugger-settings-and-preparation.md)
- [První seznámení s ladicím programem](../debugger/debugger-feature-tour.md)
- [Upozornění zabezpečení: Připojení k procesu vlastněného nedůvěryhodným uživatelem může být nebezpečné. Pokud následující informace vypadají podezřele nebo si nejste jisti, nepřipojuji se k tomuto procesu](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md)
- [Upozornění zabezpečení: Ladicí program musí provést nedůvěryhodný příkaz](../debugger/security-warning-debugger-must-execute-untrusted-command.md)