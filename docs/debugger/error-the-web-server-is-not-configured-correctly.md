---
title: Webový server není správně nakonfigurován | Microsoft Docs
ms.date: 09/20/2017
ms.topic: error-reference
f1_keywords:
- vs.debug.remote.projnotconfigured
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3a5c50822b516b73206791e3d8538bd174cfc8f6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99871231"
---
# <a name="error-the-web-server-is-not-configured-correctly"></a>Chyba: Webový server není správně nakonfigurován.

Po provedení kroků popsaných tady můžete problém vyřešit a před opakovaným pokusem o ladění může být potřeba resetovat službu IIS. Můžete to udělat tak, že otevřete příkazový řádek správce a zadáte ho `iisreset` .

Tento problém vyřešíte provedením těchto kroků:

1. Pokud je webová aplikace hostovaná na serveru nakonfigurovaná jako sestavení pro vydání, publikujte je znovu jako sestavení pro ladění a ověřte, že web.config soubor obsahuje `debug=true` v elementu compilation. Obnovte IIS a zkuste to znovu.

    Například pokud používáte profil publikování pro sestavení vydaných verzí, změňte ho na ladění a opětovné publikování. V opačném případě se atribut ladění nastaví na hodnotu `false` při publikování.

2. SLUŽBU Ověřte, zda je fyzická cesta správná. Ve službě IIS najdete toto nastavení v části **základní nastavení > fyzickou cestu** (nebo **Rozšířené nastavení** ve starších verzích služby IIS).

    Pokud byla webová aplikace zkopírována do jiného počítače, ručně přejmenována nebo přesunuta, nemusí být fyzická cesta správná. Obnovte IIS a zkuste to znovu.

3. Pokud provádíte ladění lokálně v aplikaci Visual Studio, ověřte, zda je ve vlastnostech vybrán správný server. (Otevřené **vlastnosti > serverech a vlastnostech webového >** **> ladit** v závislosti na typu projektu. V případě projektu webových formulářů otevřete **stránky vlastností > možnosti Start > Server**).

    Pokud používáte externí (vlastní) Server, jako je IIS, musí být adresa URL správná. V opačném případě vyberte IIS Express a zkuste to znovu.

4. SLUŽBU Ujistěte se, že je na serveru nainstalovaná správná verze ASP.NET.

    Tyto potíže mohou způsobovat neshodné verze ASP.NET ve službě IIS a v projektu sady Visual Studio. Možná budete muset nastavit verzi Frameworku v web.config. K instalaci ASP.NET ve službě IIS použijte [instalační program webové platformy (WebPI)](https://www.microsoft.com/web/downloads/platform.aspx). Přečtěte si také téma [IIS 8,0 s použitím ASP.NET 3,5 a ASP.NET 4,5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) nebo, pro ASP.NET Core [hostitele ve Windows se službou IIS](https://docs.asp.net/en/latest/publishing/iis.html).

4. Pokud `maxConnection` je limit ve službě IIS příliš nízký a máte příliš mnoho připojení, možná bude nutné [zvýšit limit připojení](/iis/configuration/system.applicationhost/sites/sitedefaults/limits).

## <a name="see-also"></a>Viz také
- [Vzdálené ladění ASP.NET na vzdáleném počítači se službou IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)
- [Ladění webových aplikací: chyby a řešení potíží](../debugger/debugging-web-applications-errors-and-troubleshooting.md)