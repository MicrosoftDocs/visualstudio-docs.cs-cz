---
title: Přidání dat interakce vrstev z příkazového řádku | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tier interaction profiling method
- profiling tools,tier interaction method
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 20b8438243382b28cccb510894d1674aa5872946
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74779867"
---
# <a name="add-tier-interaction-data-from-the-command-line"></a>Přidání dat interakce vrstev z příkazového řádku

Profilace interakce vrstev poskytuje další informace o době spuštění synchronních [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)] volání ve funkcích vícevrstvých aplikací, které komunikují s jednou nebo více databázemi.

**Windows 8 a Windows Server 2012**

Pro shromažďování dat interakce vrstev v aplikacích pro stolní počítače se systémem Windows 8 a Windows Server 2012 je nutné použít metodu instrumentace. Shromažďování dat interakce vrstev v aplikacích pro UWP se nepodporuje.

**Edice sady Visual Studio**

Profilace interakce vrstev se dá shromáždit pomocí libovolné edice sady Visual Studio. Data profilování interakce vrstev ale můžete zobrazit jenom v Visual Studio Enterprise.

**Shromažďovat data tipu na vzdáleném počítači**

Chcete-li shromáždit data interakce vrstev na vzdáleném počítači, je nutné zkopírovat **vs_profiler\_** _\<Platform >_ **\_** _\<souboru jazyka >_ **. exe** ze složky _% VSINSTALLDIR%_ **\Team Tools\Performance** počítače sady Visual Studio do vzdáleného počítače a nainstalovat ji. Nástroje pro profilaci nelze použít v balíčku pro stažení [vzdáleného ladění](../debugger/remote-debugging.md) .

**Sestavy tipů**

Data interakce vrstev se dají zobrazit jenom v Visual Studio Enterprise. Sestavy interakce na úrovni souborů prostřednictvím [VSPerfReport](../profiling/vsperfreport.md) nejsou k dispozici.

## <a name="add-tier-interaction-data-with-vsperfcmd"></a>Přidání dat interakce vrstev pomocí VSPerfCmd

Nástroj příkazového řádku VSPerfASPNETCmd umožňuje přístup k kompletním funkcím, které jsou k dispozici v Nástroje pro profilaci. Chcete-li přidat interakci vrstev do dat profilace shromážděných pomocí VSPerfCmd, je nutné použít nástroj **VSPerfCLREnv** k nastavení a odebrání proměnných prostředí, které povolují data interakce vrstev. Možnosti, které zadáte, a postupy vyžadované ke shromažďování dat závisí na typu aplikace, kterou vytváříte profilování.

## <a name="profile-stand-alone-applications"></a>Profilovat samostatné aplikace

Chcete-li přidat data interakce vrstev do aplikace, kterou nespouští jiný proces, jako je například aplikace klasické pracovní plochy systému Windows, která provádí synchronní [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)] volání databáze SQLServer, použijte možnost **VSPerfCLREnv/InteractionOn** pro nastavení proměnných prostředí a možnost **VSPerfCLREnv/InteractionOff** pro jejich odebrání.

V následujícím příkladu je aplikace klasické pracovní plochy systému Windows profilovaná pomocí metody instrumentace a dat interakce vrstev.

### <a name="profile-a-windows-desktop-application-example"></a>Příklad profilování desktopové aplikace pro Windows

1. Otevřete okno příkazového řádku s oprávněními správce. Klikněte na tlačítko **Start**, přejděte na příkaz **všechny programy**a pak na položku **příslušenství**. Klikněte pravým tlačítkem myši na **příkazový řádek**a pak klikněte na **Spustit jako správce**.

2. Inicializujte profilaci .NET a proměnné prostředí TIP. Zadejte následující příkazy:

    ```cmd
    vsperfclrenv /traceon
    vsperfclrenv /interactionon
    ```

3. Spusťte profiler. Zadejte následující příkaz:

    ```cmd
    vsperfcmd /start:trace /output:Desktop_tip.vsp
    ```

4. Spusťte aplikaci pomocí VSPerfCmd. Zadejte následující příkaz:

    ```cmd
    vsperfcmd /launch:DesktopApp.exe
    ```

5. Pocvičením aplikace Shromážděte data profilace a pak aplikaci zavřete běžným způsobem.

6. Vymažte proměnné prostředí s tipem. Zadejte následující příkaz:

    ```cmd
    vsperfclrenv /off
    ```

Další informace najdete v tématu [profilace samostatných aplikací](../profiling/command-line-profiling-of-stand-alone-applications.md).

## <a name="profile-services"></a>Profilovací služby

Chcete-li profilovat služby, včetně aplikací [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], nastavte proměnné prostředí pomocí možnosti **/GlobalInteractionOn VSPerfCLREnv** a možnost **VSPerfCLREnv/GlobalInteractionOff** je odeberte.

Pokud používáte služby profilování, včetně [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] webových aplikací, budete často muset restartovat počítač, aby bylo možné profilování povolit.

V následujícím příkladu je služba systému Windows profilovaná pomocí metody instrumentace a dat interakce vrstev, která jsou shromažďována.

### <a name="profile-a-windows-service-example"></a>Příklad profilu služby systému Windows

1. V případě potřeby nainstalujte službu.

2. Otevřete okno příkazového řádku s oprávněními správce. Klikněte na tlačítko **Start**, přejděte na příkaz **všechny programy**a pak na položku **příslušenství**. Klikněte pravým tlačítkem myši na **příkazový řádek**a pak klikněte na **Spustit jako správce**.

3. Inicializujte proměnné prostředí pro profilování .NET. Zadejte následující příkaz:

    ```cmd
    vsperfclrenv /globaltraceon
    ```

4. Inicializujte proměnné prostředí s tipem. Zadejte následující příkaz:

    ```cmd
    vsperfclrenv /globalinteractionon
    ```

5. Chcete-li zaregistrovat proměnné prostředí, restartujte počítač.

6. Otevřete okno příkazového řádku s oprávněními správce.

7. Spusťte profiler. Zadejte následující příkaz:

    ```cmd
    vsperfcmd /start:trace /output:MiddleTier_tip.vsp /user:SYSTEM /crosssession
    ```

8. V případě potřeby službu spusťte.

9. Připojte profiler ke službě. Zadejte následující příkaz:

    ```cmd
    vsperfcmd /attach:MiddleTier.exe /output:MyService_tip.vsp /user:SYSTEM /crosssession
    ```

10. Cvičení služby a shromažďování dat profilace.

11. Zastavte Profiler. Zadejte následující příkaz:

     `vsperfcmd /detach`

12. Vymažte proměnné prostředí pro profilování rozhraní .NET a TIP. Zadejte následující příkaz:

    ```cmd
    vsperfclrenv /globaloff
    ```

13. Restartujte počítač pro registraci vymazaných proměnných prostředí.

Další informace naleznete v jednom z následujících témat:

[ASP.NET webové aplikace Profile](../profiling/command-line-profiling-of-aspnet-web-applications.md)

[Profilovací služby](../profiling/command-line-profiling-of-services.md)

## <a name="add-tier-interaction-data-with-vsperfaspnetcmd"></a>Přidání dat interakce vrstev pomocí VSPerfASPNETCmd

Nástroj příkazového řádku VSPerfASPNETCmd umožňuje snadno profilovat [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] webové aplikace. V porovnání s nástrojem příkazového řádku **VSPerfCmd** se možnosti sníží, žádné proměnné prostředí není potřeba nastavit a restartování počítače se nevyžaduje. Díky těmto funkcím VSPerfASPNETCmd je shromažďování dat interakce vrstev výjimečně snadné.

Chcete-li přidat interakci vrstvy k datům profilování shromážděným pomocí VSPerfASPNETCmd, přidejte do příkazového řádku možnost **/Tip** . Pomocí následujícího příkazového řádku můžete například shromažďovat data interakce vrstev pro [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] webové aplikace pomocí metody instrumentace:

```cmd
vsperfaspnetcmd /tip /trace http://localhost/MyWebApp
```

Další informace o VSPerfASPNETCmd najdete v tématu [rychlé profilování webu pomocí VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md).
