---
title: Povolení ladění pro ASP.NET aplikace | Microsoft Docs
description: Zjistěte, jak povolit ladění pro ASP.NET a ASP.NET Core v Visual Studio. Tento proces můžete spustit na IIS Express serveru nebo na místním serveru služby IIS.
ms.custom: SEO-VS-2020
ms.date: 10/29/2020
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging ASP.NET Web applications
- Web.config configuration file, debug mode
- debugging [Visual Studio], ASP.NET
ms.assetid: 3beed819-cece-4864-8184-bd410000973a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- aspnet
ms.openlocfilehash: 1fd620a0c7f4860421b6f8b1a15c0b708c1ba860
ms.sourcegitcommit: a0f5e7188838c5989c9cc78d99fb29bb2813501e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/11/2021
ms.locfileid: "109729257"
---
# <a name="debug-aspnet-or-aspnet-core-apps-in-visual-studio"></a>Ladění aplikací ASP.NET nebo ASP.NET Core v sadě Visual Studio

Aplikace Core můžete ASP.NET a ASP.NET v Visual Studio. Proces se liší mezi ASP.NET a ASP.NET Core a jestli ho spustíte na IIS Express nebo na místním serveru SLUŽBY IIS.

>[!NOTE]
>Následující kroky a nastavení se vztahují pouze na ladění aplikací na místním serveru. Ladění aplikací na vzdáleném serveru služby IIS používá **funkci Připojit k procesu** a tato nastavení ignoruje. Další informace a pokyny pro vzdálené ladění ASP.NET ve službě IIS najdete v tématu Vzdálené ladění ASP.NET na počítači se službou [IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md) nebo Vzdálené ladění ASP.NET Core na vzdáleném počítači [se službou IIS.](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)

Integrovaný server IIS Express je součástí Visual Studio. IIS Express je výchozí ladicí server pro ASP.NET a ASP.NET Core a je předem nakonfigurovaný. Je to nejjednodušší způsob ladění a je ideální pro počáteční ladění a testování.

Můžete také ladit aplikaci ASP.NET nebo ASP.NET Core na místním serveru služby IIS (verze 8.0 nebo vyšší), která je nakonfigurovaná pro spuštění aplikace. Pokud chcete ladit v místní službě IIS, musíte splňovat následující požadavky:

<a name="iis"></a>
- Pokud není nainstalovaný, nainstalujte úlohu **ASP.NET a web development.** (Znovu spusťte Instalační program pro Visual Studio, vyberte **Upravit** a přidejte tuto úlohu.)

   ::: moniker range="vs-2017"
   V Visual Studio 2017 vyhledejte komponentu **Podpora služby IIS pro dobu** vývoje. Při přidávání úlohy se ujistěte, že je vybraná.
   ::: moniker-end
- Spusťte sadu Visual Studio jako správce.
- Nainstalujte a správně nakonfigurujte službu IIS s příslušnými verzemi ASP.NET nebo ASP.NET Core. Další informace o používání služby IIS s ASP.NET Core najdete v tématu [Hostování ASP.NET Core ve Windows se službou IIS.](/aspnet/core/host-and-deploy/iis/index) Další ASP.NET tématu [Instalace služby IIS a ASP.NET Modules.](/iis/application-frameworks/scenario-build-an-aspnet-website-on-iis/configuring-step-1-install-iis-and-asp-net-modules)
- Ujistěte se, že aplikace běží ve službě IIS bez chyb.

## <a name="debug-aspnet-apps"></a>Ladění aplikací ASP.NET

Výchozí hodnota je IIS Express a je předem nakonfigurovaná. Pokud provádíte ladění v místní službě IIS, ujistěte se, že splňujete [požadavky pro místní ladění služby IIS](#iis).

1. Vyberte projekt ASP.NET v aplikaci Visual Studio **Průzkumník řešení** a klikněte na ikonu **vlastnosti** , nebo stiskněte klávesu **ALT** + **ENTER** nebo klikněte pravým tlačítkem myši a zvolte možnost **vlastnosti**.

1. Vyberte kartu **Web** .

1. V podokně **vlastnosti** klikněte v části **servery** na
   - V případě IIS Express v rozevíracím seznamu vyberte **IIS Express** .
   - Pro místní službu IIS,
     1. Z rozevíracího seznamu vyberte **místní IIS** .
     1. V poli **Adresa URL projektu** vyberte **vytvořit virtuální adresář**, pokud jste ještě nevytvořili aplikaci ve službě IIS.

1. V části **Debuggery** vyberte **ASP.NET**.

   ![Nastavení ladicího programu ASP.NET](media/dbg-aspnet-enable-debugging2.png "Nastavení ladicího programu ASP.NET")

1. Zvolte **soubor**  >  **Uložit vybrané položky** (nebo stiskněte klávesovou **zkratku CTRL +** + ) a uložte všechny změny.

1. Chcete-li ladit aplikaci, v projektu nastavte zarážky u určitého kódu. Na panelu nástrojů sady Visual Studio se ujistěte, že je konfigurace nastavená na **ladit**, a prohlížeč, který chcete, se v poli emulátoru zobrazuje v **IIS Express ( \<Browser name> )** nebo v **místní službě IIS ( \<Browser name> )** .

1. Chcete-li spustit ladění, vyberte možnost **IIS Express ( \<Browser name> )** nebo **místní služba IIS ( \<Browser name> )** na panelu nástrojů, vyberte možnost **Spustit ladění** z nabídky **ladění** nebo stiskněte klávesu **F5**. Ladicí program se pozastaví na zarážce. Pokud ladicí program nemůže narazit na zarážky, přečtěte si téma [řešení potíží s laděním](#troubleshoot-debugging).

## <a name="debug-aspnet-core-apps"></a>Ladění aplikací ASP.NET Core

IIS Express je výchozí nastavení a je předem nakonfigurované. Pokud ladíte v místní službě IIS, ujistěte se, že splňujete požadavky [na místní ladění služby IIS.](#iis)

1. Vyberte projekt ASP.NET Core v Visual Studio **Průzkumník řešení** a klikněte na  ikonu Vlastnosti, nebo stiskněte **Alt** Enter nebo klikněte pravým tlačítkem a + zvolte **Vlastnosti**.

1. Vyberte **kartu** Ladit.

1. V **podokně Vlastnosti** vedle možnosti **Profil**
   - Jako IIS Express vyberte **IIS Express** z rozevíracího seznamu.
   - V případě místní služby IIS vyberte název aplikace z rozevíracího seznamu nebo vyberte **Nový,** vytvořte nový název profilu a vyberte **OK.**

1. Vedle launch **(Spustit)** vyberte **IIS Express** **nebo IIS** z rozevíracího seznamu.

1. Ujistěte **se, že je vybraná možnost** Spustit prohlížeč.

1. V **části Proměnné** prostředí se ujistěte, **ASPNETCORE_ENVIRONMENT** je k dispozici s hodnotou **Vývoj.** Pokud ne, vyberte **Přidat** a přidejte ho.

   ![ASP.NET core ladicího programu](../debugger/media/dbg-aspnet-enable-debugging3.png "Nastavení ladicího programu ASP.NET Core")

1. K **uložení** změn použijte soubor Uložit vybrané položky nebo  >   **Ctrl** + **S.**

1. Pokud chcete aplikaci ladit, nastavte v projektu zarážky na nějaký kód. Na panelu Visual Studio se ujistěte, že je konfigurace nastavená na Ladit a v poli emulátoru se zobrazí **buď IIS Express**, nebo nový název profilu služby IIS.

1. Pokud chcete spustit ladění, **IIS Express** nebo na panelu nástrojů vyberte Spustit ladění z nabídky Ladit **\<IIS profile name>** nebo stiskněte klávesu **F5**  .  Ladicí program se pozastaví na zarážkách. Pokud ladicí program nemůže získat zarážky, podívejte se na článek Řešení [potíží s laděním.](#troubleshoot-debugging)

## <a name="troubleshoot-debugging"></a>Řešení potíží s laděním

Pokud místní ladění SLUŽBY IIS nemůže posouovat k zarážce, při řešení potíží postupujte podle těchto kroků.

1. Spusťte webovou aplikaci ze služby IIS a ujistěte se, že funguje správně. Ponechte webovou aplikaci spuštěnou.

2. V aplikaci Visual Studio vyberte možnost **ladění > připojit k procesu** nebo stiskněte klávesovou **zkratku CTRL** + **+** + **P** a připojte se k ASP.NET nebo ASP.NET Coremu procesu (obvykle **w3wp.exe** nebo **dotnet.exe**). Další informace najdete v tématu [připojení k procesu](attach-to-running-processes-with-the-visual-studio-debugger.md) a [hledání názvu ASP.NET procesu](how-to-find-the-name-of-the-aspnet-process.md).

Pokud se můžete připojit a použít zarážku pomocí příkazu **připojit k procesu**, ale **ne pomocí ladění**  >  **Spustit ladění** nebo **F5**, je nastavení pravděpodobně nesprávné ve vlastnostech projektu. Pokud použijete soubor hostitelů, ujistěte se, že je správně nakonfigurován také.

## <a name="configure-debugging-in-the-webconfig-file"></a>Konfigurace ladění v souboru web.config

Projekty ASP.NET mají ve výchozím nastavení *web.config* soubory, které obsahují konfiguraci aplikace i informace o spuštění, včetně nastavení ladění. *web.config* soubory musí být správně nakonfigurovány pro ladění. Nastavení **vlastností** v předchozích částech aktualizují soubory *web.config* , ale můžete je také nakonfigurovat ručně.

> [!NOTE]
> ASP.NET Core projekty nemají na začátku *web.config* soubory, ale použijte *appsettings.jsna* a *launchSettings.js* soubory pro konfiguraci aplikace a informace o spuštění. Nasazením aplikace se vytvoří soubor *web.config* nebo soubory v projektu, které obvykle neobsahují informace o ladění.

> [!TIP]
> Proces nasazení může aktualizovat nastavení *web.config* , takže před pokusem o ladění se ujistěte, že je *web.config* nakonfigurované pro ladění.

**Postup ruční konfigurace *web.config* souboru pro ladění:**

1. V aplikaci Visual Studio otevřete soubor *web.config* projektu ASP.NET.

2. *Web.config* je soubor XML, takže obsahuje vnořené oddíly označené značkami. Vyhledejte část `configuration/system.web/compilation`. (Pokud `compilation` prvek neexistuje, vytvořte jej.)

3. Ujistěte se, že `debug` atribut v `compilation` elementu je nastaven na hodnotu `true` . (Pokud `compilation` element neobsahuje `debug` atribut, přidejte ho a nastavte na `true` .)

   Pokud místo výchozího serveru služby IIS IIS Express, ujistěte se, že hodnota atributu v elementu odpovídá rozhraní `targetFramework` `compilation` na serveru služby IIS.

   Element `compilation` souboru web.configby měl vypadat jako v následujícím příkladu:

   > [!NOTE]
   > Tento příklad je částečný *web.config* souboru. V elementech a jsou obvykle k dispozici další oddíly XML a element může také obsahovat další atributy a `configuration` `system.web` `compilation` elementy.

   ```xml
   <configuration>
      ...
      <system.web>
          <compilation  debug="true"  targetFramework="4.6.1" ... >
             ...
          </compilation>
      </system.web>
   </configuration>
   ```

[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] automaticky rozpozná všechny změnyweb.config *souborů* a použije nová nastavení konfigurace. Aby se změny projeví, nemusíte restartovat počítač ani server služby IIS.

Web může obsahovat několik virtuálních adresářů a podadresářů sweb.config *soubory* v každém z nich. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikace dědí nastavení konfigurace *web.config* souborů na vyšších úrovních v cestě URL. Hierarchická *nastaveníweb.config* se vztahují na všechny aplikace pod nimi v [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] hierarchii. Nastavení jiné konfigurace v *web.config* v hierarchii přepíše nastavení ve vyšším souboru.

Pokud například zadáte v souboru www.microsoft.com/aaa/web.config, zdědí nastavení jakákoli aplikace ve složce `debug="true"` *aaa* <em></em>nebo v libovolné podsložce  *aaa* s výjimkou případů, kdy jedna z těchto aplikací přepíše nastavení vlastnímweb.configsouboru.

## <a name="publish-in-debug-mode-using-the-file-system"></a>Publikování v režimu ladění pomocí systému souborů

Existují různé způsoby publikování aplikací do služby IIS. Tyto kroky ukazují, jak vytvořit a nasadit profil publikování ladění pomocí systému souborů. Chcete-li to provést, musíte Visual Studio jako správce.

> [!IMPORTANT]
> Pokud kód změníte nebo znovu sestavíte, musíte tento postup zopakovat a znovu publikovat.

1. V Visual Studio klikněte pravým tlačítkem na projekt a zvolte **Publikovat.**

3. Zvolte **IIS, FTP atd.** a klikněte na **Publikovat.**

    ![Snímek obrazovky s dialogem Vybrat cíl publikování v Visual Studio Je vybraná možnost IIS, FTP Nasazení webu a zvýrazněné tlačítko Publikovat.](media/dbg-aspnet-local-iis.png)

4. V dialogovém okně **CustomProfile** pro **metodu publikovat** vyberte možnost **systém souborů**.

5. Pro **cílové umístění** vyberte **Procházet** (**...**).

   - Pro ASP.NET vyberte **místní IIS**, vyberte web, který jste pro aplikaci vytvořili, a pak vyberte **otevřít**.

     ![Publikování do ASP.NET do služby IIS](media/dbg-aspnet-local-iis1.png "Publikování ASP.NET do služby IIS")

   - V ASP.NET Core vyberte **systém souborů**, vyberte složku, kterou jste pro aplikaci nastavili, a pak vyberte **otevřít**.

1. Vyberte **Další**.

1. V části **Konfigurace** vyberte **ladění** z rozevíracího seznamu.

1. Vyberte **Uložit**.

1. V dialogovém okně **publikovat** se ujistěte, že se zobrazí **CustomProfile** (nebo název profilu, který jste právě vytvořili) a **LastUsedBuildConfiguration** je nastavené na **ladění**.

1. Vyberte **Publikovat**.

    ![Snímek obrazovky dialogového okna publikovat, ve kterém je vybraná aplikace CustomProfile, bylo zvýrazněno tlačítko publikovat a LastBuildConfiguration nastavené na ladění.](media/dbg-aspnet-local-iis-select-site.png)

> [!IMPORTANT]
> Režim ladění významně snižuje výkon aplikace. Nejlepšího výkonu nastavíte `debug="false"` v *web.config* a určíte sestavení pro vydání při nasazení produkční aplikace nebo provedení měření výkonu.

## <a name="see-also"></a>Viz také
- [Ladění ASP.NET: Požadavky na systém](aspnet-debugging-system-requirements.md)
- [Postupy: Spuštění pracovního procesu v rámci uživatelského účtu](how-to-run-the-worker-process-under-a-user-account.md)
- [Postupy: Hledání názvu procesu ASP.NET](how-to-find-the-name-of-the-aspnet-process.md)
- [Ladění nasazených webových aplikací](debugging-deployed-web-applications.md)
- [Návod: ladění webového formuláře](walkthrough-debugging-a-web-form.md)
- [Postupy: ladění výjimek ASP.NET](how-to-debug-aspnet-exceptions.md)
- [Ladění webových aplikací: chyby a řešení potíží](debugging-web-applications-errors-and-troubleshooting.md)
