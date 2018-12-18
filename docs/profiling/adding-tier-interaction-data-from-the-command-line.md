---
title: Přidání dat interakce vrstev z příkazového řádku | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- tier interaction profiling method
- profiling tools,tier interaction method
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bbb950947b3f97a4f6d6e9c1461dd2023595058c
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43775030"
---
# <a name="add-tier-interaction-data-from-the-command-line"></a>Přidání dat interakce vrstev z příkazového řádku

Profilování interakce vrstev poskytuje další informace o spuštění s úspěšností synchronní [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)] volání funkce víceúrovňových aplikací, které komunikují po jedné nebo víc databází.

**Windows 8 a Windows Server 2012**

Ke shromažďování dat interakce vrstev pro aplikace klasické pracovní plochy systému Windows 8 a Windows Server 2012 aplikací musí použít metody instrumentace. Shromažďování dat interakce vrstev v aplikacích pro UWP se nepodporuje.

**Edice sady Visual Studio**

Profilování interakce vrstev lze shromažďovat pomocí libovolné edice sady Visual Studio. Nicméně data profilace interakce vrstev lze zobrazit pouze v sadě Visual Studio Enterprise.

**Shromažďování dat TIP na vzdáleném počítači**

Ke shromažďování dat interakce vrstev ve vzdáleném počítači, je nutné zkopírovat **vs_profiler\_**_\<platformy >_ **\_**  _\<Jazyk >_**.exe** soubor _VSInstallDir %_**\Team Tools\Performance Tools\Setups** složky Visual Studio počítače ke vzdálenému počítači a nainstalujte ho. Nelze použít v nástrojů pro profilaci [vzdálené ladění](../debugger/remote-debugging.md) stažení balíčku.

**TIP sestavy**

Dat interakce vrstev lze zobrazit pouze v sadě Visual Studio Enterprise. Interakce vrstev souborovému sestavy prostřednictvím [VSPerfReport](../profiling/vsperfreport.md) nejsou k dispozici.

## <a name="add-tier-interaction-data-with-vsperfcmd"></a>Přidání dat interakce vrstev s VSPerfCmd

Nástroj příkazového řádku příkaz VSPerfASPNETCmd vám umožní přístup k dokončení funkce dostupná v nástrojích pro profilaci. Chcete-li přidat data shromážděná pomocí, VSPerfCmd profilace interakce vrstev, musíte použít **VSPerfCLREnv** nástroj pro nastavení a odebrání proměnné prostředí, která umožňuje dat interakce vrstev. Možnosti, které zadáte a postupy potřebné ke shromažďování dat závisí na typu aplikace, který profilujete.

## <a name="profile-stand-alone-applications"></a>Samostatné aplikace profilu

Přidání dat interakce vrstev do aplikace, která se spustí jiný proces, jako jsou aplikace klasické pracovní plochy Windows, která umožňuje synchronní [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)] volání do databáze systému SQL Server, je použít **VSPerfClrEnv /InteractionOn** možnost nastavit proměnné prostředí a **VSPerfClrEnv /InteractionOff** možností jejich odebrání.

V následujícím příkladu je pomocí metody instrumentace profilované aplikace klasické pracovní plochy Windows a shromažďovaných dat interakce vrstev.

### <a name="profile-a-windows-desktop-application-example"></a>Příklad aplikace klasické pracovní plochy Windows profilu

1. Otevřete okno příkazového řádku s oprávněními správce. Klikněte na tlačítko **Start**, přejděte na **všechny programy**a pak na **Příslušenství**. Klikněte pravým tlačítkem na **příkazového řádku**a potom klikněte na tlačítko **spustit jako správce**.

2. Inicializace proměnných prostředí TIP a profilování rozhraní .NET. Zadejte následující příkazy:

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

5. Výkon aplikace ke shromažďování dat profilování a poté ukončete aplikaci běžným způsobem.

6. Vyčistěte proměnné prostředí pro popis TLAČÍTKA. Zadejte následující příkaz:

    ```cmd
    vsperfclrenv /off
    ```

Další informace najdete v tématu [Profilovat samostatné aplikace](../profiling/command-line-profiling-of-stand-alone-applications.md).

## <a name="profile-services"></a>Profil služby

Do profilu služby, včetně [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikací, použijte **VSPerfClrEnv /GlobalInteractionOn** možnost nastavit proměnné prostředí a **VSPerfClrEnv /GlobalInteractionOff** možností jejich odebrání.

Pokud provádíte profilaci služeb, včetně [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] webových aplikací, je často potřeba počítač restartovat, aby povolit profilaci.

V následujícím příkladu je pomocí metody instrumentace profilované služby Windows a shromažďovaných dat interakce vrstev.

### <a name="profile-a-windows-service-example"></a>Profil příklad služby Windows

1. V případě potřeby nainstalujte službu.

2. Otevřete okno příkazového řádku s oprávněními správce. Klikněte na tlačítko **Start**, přejděte na **všechny programy**a pak na **Příslušenství**. Klikněte pravým tlačítkem na **příkazového řádku**a potom klikněte na tlačítko **spustit jako správce**.

3. Inicializujte proměnné prostředí profilování rozhraní .NET. Zadejte následující příkaz:

    ```cmd
    vsperfclrenv /globaltraceon
    ```

4. Inicializujte proměnné prostředí TIP. Zadejte následující příkaz:

    ```cmd
    vsperfclrenv /globalinteractionon
    ```

5. Restartujte počítač a zaregistrovat proměnné prostředí.

6. Otevřete okno příkazového řádku s oprávněními správce.

7. Spusťte profiler. Zadejte následující příkaz:

    ```cmd
    vsperfcmd /start:trace /output:MiddleTier_tip.vsp /user:SYSTEM /crosssession 
    ```

8. V případě potřeby spusťte službu.

9. Připojení profileru ke službě. Zadejte následující příkaz:

    ```cmd
    vsperfcmd /attach:MiddleTier.exe /output:MyService_tip.vsp /user:SYSTEM /crosssession 
    ```

10. Výkon služby a shromažďování dat profilace.

11. Ukončete profiler. Zadejte následující příkaz:

     `vsperfcmd /detach`

12. Vymažte .NET a TIP proměnných prostředí profilování. Zadejte následující příkaz:

    ```cmd
    vsperfclrenv /globaloff
    ```

13. Restartujte počítač a zaregistrovat proměnné prostředí nezaškrtnuté.

Další informace naleznete v jednom z následujících témat:

[Webové aplikace ASP.NET profilu](../profiling/command-line-profiling-of-aspnet-web-applications.md)

[Profil služby](../profiling/command-line-profiling-of-services.md)

## <a name="add-tier-interaction-data-with-vsperfaspnetcmd"></a>Přidání dat interakce vrstev stránek pomocí VSPerfASPNETCmd

Nástroj příkazového řádku příkaz VSPerfASPNETCmd vám umožní snadno profilu [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] webové aplikace. Ve srovnání s **VSPerfCmd** nástroj příkazového řádku, možnosti jsou zmenšeny, musí být nastaveny žádné proměnné prostředí a restartování počítače se nevyžaduje. Tyto funkce VSPerfASPNETCmd shromažďování dat interakce vrstev výjimečně usnadňují.

Chcete-li přidat data shromážděná pomocí VSPerfASPNETCmd profilace interakce vrstev, přidejte **/TIP** možnost příkazového řádku. Například použijte následující příkazový řádek ke shromažďování dat interakce vrstev pro [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] webovou aplikaci pomocí metody instrumentace:

```cmd
vsperfaspnetcmd /tip /trace http://localhost/MyWebApp
```

Další informace o VSPerfASPNETCmd najdete v tématu [profilace pohotová webových stránek pomocí VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md).