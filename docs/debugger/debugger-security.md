---
title: Zabezpečení ladicího programu | Microsoft Docs
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
ms.openlocfilehash: d8d2e951bb62cb3ac8010029b76971662d07b898
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738322"
---
# <a name="debugger-security"></a>Zabezpečení ladicího programu
Možnost ladit jiný proces vám poskytne velmi široké pravomoci, které byste jinak neměli mít, zejména při vzdáleném ladění. Škodlivý ladicí program může způsobit rozšířenou škodu v laděném počítači.

 Mnoho vývojářů ale neuvědomuje, že ohrožení zabezpečení může také přesměrovat v opačném směru. Škodlivý kód v procesu laděného procesu může ohrozit zabezpečení ladicího počítače: existuje několik zneužití zabezpečení, která musí být chráněná proti.

## <a name="security-best-practices"></a>Doporučené postupy zabezpečení
 Mezi kódem, který ladíte, existuje implicitní vztah důvěryhodnosti a ladicí program. Pokud jste ochotni něco ladit, měli byste ho také ochotni spustit. Dolním řádkem je, že musíte být schopni důvěřovat, co ladíte. Pokud ji nemůžete důvěřovat, neměli byste ji ladit nebo byste ji měli ladit z počítače, který si můžete dovolit ohrozit, a v izolovaném prostředí.

 Aby se snížila potenciální plocha pro útok, mělo by být ladění na produkčních počítačích zakázané. Z tohoto důvodu by nebylo možné ladění nikdy povolit po neomezenou dobu.

### <a name="managed-debugging-security"></a>Zabezpečení spravovaného ladění
 Tady jsou některá obecná doporučení, která platí pro všechna spravovaná ladění.

- Buďte opatrní při připojování k procesu nedůvěryhodného uživatele: Pokud tak učiníte, předpokládá se, že je důvěryhodný. Když se pokusíte připojit k procesu nedůvěryhodného uživatele, zobrazí se dialogové okno upozornění zabezpečení s dotazem, zda se chcete připojit k procesu. "Důvěryhodní uživatelé" zahrnují vás a sadu standardních uživatelů, kteří jsou obvykle definováni v počítačích s nainstalovaným .NET Framework, jako jsou **ASPNET**, **LocalSystem**, **NetworkService**a **LocalService**. Další informace najdete v tématu [Upozornění zabezpečení: připojení k procesu, který vlastní nedůvěryhodný uživatel, může být nebezpečné. Pokud tyto informace vypadají podezřele nebo si nejste jistí, nepřipojujte se k tomuto procesu](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md).

- Při stahování projektu z Internetu buďte opatrní a načítat ho do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. To je velice riskantní, aby se dokonce i bez ladění. Když to uděláte, předpokládá se, že projekt a kód, který obsahuje, jsou důvěryhodné.

  Další informace naleznete v tématu [ladění spravovaného kódu](../debugger/debugging-managed-code.md).

### <a name="remote-debugging-security"></a>Zabezpečení vzdáleného ladění
 Místní ladění je obecně bezpečnější než vzdálené ladění. Vzdálené ladění zvyšuje celkovou plochu, která může být sonda.

 Visual Studio Sledování vzdáleného ladění (Msvsmon. exe) se používá při vzdáleném ladění a existuje několik doporučení pro zabezpečení při jejich konfiguraci. Upřednostňovaným způsobem, jak nakonfigurovat režim ověřování, je ověřování systému Windows, protože žádný režim ověřování není nezabezpečený.

 ![Chybový dialog](../debugger/media/dbg_err_remotepermissionschanged.png "DBG_ERR_RemotePermissionsChanged")

 Při použití režimu ověřování systému Windows mějte na paměti, že udělení oprávnění nedůvěryhodného uživatele pro připojení k msvsmon je nebezpečné, protože uživateli jsou udělena všechna vaše oprávnění v počítači.

 Neprovádějte ladění neznámého procesu ve vzdáleném počítači: existují potenciální zneužití, která by mohla ovlivnit počítač, na kterém je spuštěn ladicí program, nebo který může ohrozit msvsmon. exe, Visual Studio Sledování vzdáleného ladění. Pokud nezbytně potřebujete ladit neznámý proces, zkuste ladění provést místně a pomocí brány firewall Udržujte potenciálně lokalizovanou hrozby.

 Další informace najdete v tématu [vzdálené ladění](../debugger/remote-debugging.md).

### <a name="web-services-debugging-security"></a>Zabezpečení ladění webových služeb
 Je bezpečnější ho ladit místně, ale vzhledem k tomu, že na webovém serveru nejspíš nemáte [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nainstalované, nemusí být místní ladění praktické. Obecně se ladění webových služeb provádí vzdáleně, s výjimkou vývoje, takže doporučení pro vzdálené ladění se vztahují také na ladění webových služeb. Tady jsou některé další osvědčené postupy. Další informace najdete v tématu [ladění webových služeb XML](https://msdn.microsoft.com/library/c900b137-9fbd-4f59-91b5-9c2c6ce06f00).

- Nepovolujte ladění na webovém serveru, u kterého došlo k ohrožení zabezpečení.

- Před laděním je nutné, abyste věděli, že je webový server zabezpečený. Pokud si nejste jisti, že je zabezpečená, neprovádějte ladění.

- Buďte obzvláště opatrní při ladění webové služby, která je vystavená na internetu.

### <a name="external-components"></a>Externí komponenty
 Mějte na paměti stav důvěryhodnosti externích komponent, se kterými komunikuje váš program, zejména v případě, že jste kód nezapsali. Také je třeba znát komponenty, které [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nebo může použít ladicí program.

### <a name="symbols-and-source-code"></a>Symboly a zdrojový kód
 Následující dva [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nástroje, které vyžadují zamyšlení na zabezpečení, jsou tyto:

- Zdrojový server, který poskytuje verze zdrojového kódu z úložiště zdrojového kódu. To je užitečné v případě, že není k dispozici aktuální verze zdrojového kódu programu. [Upozornění zabezpečení: ladicí program musí spustit nedůvěryhodný příkaz](../debugger/security-warning-debugger-must-execute-untrusted-command.md).

- Symbol server, který slouží k poskytnutí symbolů potřebných k ladění selhání během volání systému.

  Viz [určení symbolu (. pdb) a zdrojových souborů](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) .

## <a name="see-also"></a>Viz také:
- [Nastavení a příprava ladicího programu](../debugger/debugger-settings-and-preparation.md)
- [První seznámení s ladicím programem](../debugger/debugger-feature-tour.md)
- [Upozornění zabezpečení: připojení k procesu, jehož vlastníkem je nedůvěryhodný uživatel, může být nebezpečné. Pokud tyto informace vypadají podezřele nebo si nejste jistí, nepřipojujte se k tomuto procesu.](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md)
- [Upozornění zabezpečení: Ladicí program musí spustit nedůvěryhodný příkaz.](../debugger/security-warning-debugger-must-execute-untrusted-command.md)