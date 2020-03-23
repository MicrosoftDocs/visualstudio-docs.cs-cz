---
title: Přidání dat interakce vrstvy z příkazového řádku | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779867"
---
# <a name="add-tier-interaction-data-from-the-command-line"></a>Přidání dat interakce vrstev z příkazového řádku

Profilování interakce vrstvy poskytuje další informace o [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)] době provádění synchronních volání ve funkcích vícevrstvých aplikací, které komunikují s jednou nebo více databázemi.

**Windows 8 a Windows Server 2012**

Pokud chcete shromažďovat data interakce na windows 8 desktopových aplikacích a v aplikacích pro Windows Server 2012, musíte použít metodu instrumentace. Shromažďování dat interakce vrstvy v aplikacích UPW není podporováno.

**Edice Visual Studia**

Profilování interakce úrovně lze shromažďovat pomocí libovolné edice sady Visual Studio. Data profilování interakce vrstvy však lze zobrazit pouze v sadě Visual Studio Enterprise.

**Shromažďování dat TIP na vzdáleném počítači**

Chcete-li shromažďovat data interakce vrstvy ve vzdáleném počítači, musíte do vzdáleného počítače zkopírovat soubor **vs_profiler\_** **\_**_\<platformy>_ _ \<jazyk>.exe _ze složky _%VSInstallDir%_**\Team Tools\Performance Tools\Setups** počítače Visual Studio a nainstalovat jej. **.exe** Nástroje pro profilování nelze použít v balíčku pro stažení [vzdáleného ladění.](../debugger/remote-debugging.md)

**Zprávy TIP**

Data interakce úrovně lze zobrazit pouze v sadě Visual Studio Enterprise. Sestavy interakce na základě vrstvy založené na souborech prostřednictvím [vsperfreportu](../profiling/vsperfreport.md) nejsou k dispozici.

## <a name="add-tier-interaction-data-with-vsperfcmd"></a>Přidání dat interakce vrstvy s VSPerfCmd

Nástroj příkazového řádku VSPerfASPNETCmd umožňuje přístup k úplným funkcím dostupným v nástrojích profilování. Chcete-li přidat interakci vrstvy k profilování dat shromážděných pomocí VSPerfCmd, musíte použít nástroj **VSPerfCLREnv** k nastavení a odebrání proměnných prostředí, které umožňují data interakce vrstvy. Zadané možnosti a postupy potřebné ke shromažďování dat závisí na typu aplikace, kterou profilujete.

## <a name="profile-stand-alone-applications"></a>Profilovat samostatné aplikace

Chcete-li přidat data interakce vrstvy do aplikace, která není spuštěna jiným [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)] procesem, jako je například desktopová aplikace systému Windows, která provádí synchronní volání databáze SQLServer, použijte možnost **VSPerfClrEnv /InteractionOn** k nastavení proměnných prostředí a možnost **VSPerfClrEnv /InteractionOff** k jejich odebrání.

V následujícím příkladu je desktopová aplikace systému Windows profilována pomocí metody instrumentace a jsou shromažďována data interakce vrstvy.

### <a name="profile-a-windows-desktop-application-example"></a>Profilování desktopové aplikace systému Windows

1. Otevřete okno příkazového řádku s oprávněními správce. Klepněte na tlačítko **Start**, přejděte na **položku Všechny programy**a potom přejděte na **položku Příslušenství**. Klepněte pravým tlačítkem myši na **příkazový řádek**a potom klepněte na příkaz **Spustit jako správce**.

2. Inicializovat profilování .NET a proměnné prostředí TIP. Zadejte následující příkazy:

    ```cmd
    vsperfclrenv /traceon
    vsperfclrenv /interactionon
    ```

3. Spusťte profiler. Zadejte následující příkaz:

    ```cmd
    vsperfcmd /start:trace /output:Desktop_tip.vsp
    ```

4. Spusťte aplikaci s VSPerfCmd. Zadejte následující příkaz:

    ```cmd
    vsperfcmd /launch:DesktopApp.exe
    ```

5. Pomocí aplikace shromažďovat data profilování a potom zavřít aplikaci v pravidelných způsobem.

6. Vymažte proměnné prostředí TIP. Zadejte následující příkaz:

    ```cmd
    vsperfclrenv /off
    ```

Další informace naleznete v [tématu Profil ových samostatných aplikací](../profiling/command-line-profiling-of-stand-alone-applications.md).

## <a name="profile-services"></a>Profilové služby

Chcete-li profil [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] služby, včetně aplikací, použijte **VSPerfClrEnv /GlobalInteractionOn** možnost nastavit proměnné prostředí a **VSPerfClrEnv /GlobalInteractionOff** možnost odebrat.

Při profilování služeb, [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] včetně webových aplikací, budete často muset restartovat počítač povolit profilování.

V následujícím příkladu je služba systému Windows profilována pomocí metody instrumentace a jsou shromažďována data interakce vrstvy.

### <a name="profile-a-windows-service-example"></a>Profilovat příklad služby systému Windows

1. V případě potřeby nainstalujte službu.

2. Otevřete okno příkazového řádku s oprávněními správce. Klepněte na tlačítko **Start**, přejděte na **položku Všechny programy**a potom přejděte na **položku Příslušenství**. Klepněte pravým tlačítkem myši na **příkazový řádek**a potom klepněte na příkaz **Spustit jako správce**.

3. Inicializovat proměnné prostředí profilování .NET. Zadejte následující příkaz:

    ```cmd
    vsperfclrenv /globaltraceon
    ```

4. Inicializovat proměnné prostředí TIP. Zadejte následující příkaz:

    ```cmd
    vsperfclrenv /globalinteractionon
    ```

5. Chcete-li zaregistrovat proměnné prostředí, restartujte počítač.

6. Otevřete okno příkazového řádku s oprávněními správce.

7. Spusťte profiler. Zadejte následující příkaz:

    ```cmd
    vsperfcmd /start:trace /output:MiddleTier_tip.vsp /user:SYSTEM /crosssession
    ```

8. V případě potřeby spusťte službu.

9. Připojte profiler ke službě. Zadejte následující příkaz:

    ```cmd
    vsperfcmd /attach:MiddleTier.exe /output:MyService_tip.vsp /user:SYSTEM /crosssession
    ```

10. Využijte službu a shromážděte data profilování.

11. Zastavte profileru. Zadejte následující příkaz:

     `vsperfcmd /detach`

12. Zrušte zaškrtnutí proměnných prostředí profilování .NET a TIP. Zadejte následující příkaz:

    ```cmd
    vsperfclrenv /globaloff
    ```

13. Restartujte počítač a zaregistrujte nezaškrtnuté proměnné prostředí.

Další informace naleznete v jednom z následujících témat:

[Profil ASP.NET webových aplikací](../profiling/command-line-profiling-of-aspnet-web-applications.md)

[Profilové služby](../profiling/command-line-profiling-of-services.md)

## <a name="add-tier-interaction-data-with-vsperfaspnetcmd"></a>Přidání dat interakce vrstvy s VSPerfASPNETCmd

Nástroj příkazového řádku VSPerfASPNETCmd umožňuje [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] snadno profilovat webové aplikace. Ve srovnání s nástrojem příkazového řádku **VSPerfCmd** jsou možnosti sníženy, není nutné nastavit žádné proměnné prostředí a restartování počítače není vyžadováno. Tyto funkce VSPerfASPNETCmd usnadňují shromažďování dat interakce vrstvy.

Chcete-li přidat interakci vrstvy do profilování dat shromážděných pomocí VSPerfASPNETCmd, přidejte možnost **/TIP** do příkazového řádku. Pomocí následujícího příkazového řádku můžete například [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] shromažďovat data interakce vrstvy pro webovou aplikaci pomocí metody instrumentace:

```cmd
vsperfaspnetcmd /tip /trace http://localhost/MyWebApp
```

Další informace o VSPerfASPNETCmd naleznete [v tématu Rychlé profilování webových stránek pomocí nástroje VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md).
