---
title: Povolit ladění pro aplikace ASP.NET | Microsoft Docs
ms.custom: ''
ms.date: 09/21/2018
ms.topic: conceptual
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
manager: jillfra
ms.workload:
- aspnet
ms.openlocfilehash: a6f20a2272214a525b00ebf07ebc6e5e803b138c
ms.sourcegitcommit: 257fc60eb01fefafa9185fca28727ded81b8bca9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2019
ms.locfileid: "72911355"
---
# <a name="debug-aspnet-or-aspnet-core-apps-in-visual-studio"></a>Ladění aplikací ASP.NET nebo ASP.NET Core v aplikaci Visual Studio

V aplikaci Visual Studio můžete ladit aplikace ASP.NET a ASP.NET Core. Proces se liší mezi ASP.NET a ASP.NET Core a bez ohledu na to, jestli ho spouštíte v IIS Express nebo na místním serveru IIS.

>[!NOTE]
>Následující kroky a nastavení se vztahují jenom na ladění aplikací na místním serveru. Ladění aplikací na vzdáleném serveru IIS používá **připojení k procesu**a ignoruje tato nastavení. Další informace a pokyny pro vzdálené ladění aplikací ASP.NET ve službě IIS najdete v tématech [vzdálené ladění ASP.NET na počítači se službou IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md) nebo [vzdálené ladění ASP.NET Core na vzdáleném počítači IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md).

Integrovaný IIS Express Server je součástí sady Visual Studio. IIS Express je výchozí ladicí Server pro projekty ASP.NET a ASP.NET Core a je předem nakonfigurovaný. Je to nejjednodušší způsob, jak ladit a ideální pro počáteční ladění a testování.

Můžete také ladit aplikaci ASP.NET nebo ASP.NET Core na místním serveru služby IIS (verze 8,0 nebo vyšší), která je nakonfigurovaná pro spuštění aplikace. Chcete-li ladit v místní službě IIS, je nutné splnit následující požadavky:

<a name="iis"></a>
- Při instalaci sady Visual Studio vyberte **čas vývoje, který podporuje služba IIS** . (V případě potřeby znovu spusťte Instalační program pro Visual Studio, vyberte **Upravit**a přidejte tuto součást.)
- Spusťte Visual Studio jako správce.
- Nainstalujte a správně nakonfigurujte IIS pomocí odpovídajících verzí ASP.NET a/nebo ASP.NET Core. Další informace a pokyny najdete v tématu [Služba iis 8,0 s použitím ASP.NET 3,5 a ASP.NET 4,5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) nebo [ASP.NET Core hostitele ve Windows se službou IIS](/aspnet/core/host-and-deploy/iis/index).
- Ujistěte se, že aplikace běží ve službě IIS bez chyb.

## <a name="debug-aspnet-apps"></a>Ladění aplikací ASP.NET

Výchozí hodnota je IIS Express a je předem nakonfigurovaná. Pokud provádíte ladění v místní službě IIS, ujistěte se, že splňujete [požadavky pro místní ladění služby IIS](#iis).

1. Vyberte projekt ASP.NET v aplikaci Visual Studio **Průzkumník řešení** a klikněte na ikonu **vlastnosti** , stiskněte klávesu **ALT**+**ENTER**nebo klikněte pravým tlačítkem a zvolte **vlastnosti**.

1. Vyberte kartu **Web** .

1. V podokně **vlastnosti** klikněte v části **servery**na
   - V případě IIS Express v rozevíracím seznamu vyberte **IIS Express** .
   - Pro místní službu IIS,
     1. Z rozevíracího seznamu vyberte **místní IIS** .
     1. V poli **Adresa URL projektu** vyberte **vytvořit virtuální adresář**, pokud jste ještě nevytvořili aplikaci ve službě IIS.

1. V části **Debuggery**vyberte **ASP.NET**.

   ![Nastavení ladicího programu ASP.NET](media/dbg-aspnet-enable-debugging2.png "Nastavení ladicího programu ASP.NET")

1. Použijte **soubor** > **Uložit vybrané položky** nebo **CTRL**+**s** pro uložení změn.

1. Chcete-li ladit aplikaci, v projektu nastavte zarážky u určitého kódu. Na panelu nástrojů sady Visual Studio se ujistěte, že je konfigurace nastavená na **ladit**, a prohlížeč, který se má zobrazit v **IIS Express (\<název prohlížeče >)** nebo **místní IIS (\<název prohlížeče >)** v poli emulátor.

1. Chcete-li spustit ladění, vyberte možnost **IIS Express (\<název prohlížeče >)** nebo **místní služba IIS (\<název prohlížeče >)** na panelu nástrojů, vyberte možnost **Spustit ladění** z nabídky **ladění** nebo stiskněte klávesu **F5**. Ladicí program se pozastaví na zarážce. Pokud ladicí program nemůže narazit na zarážky, přečtěte si téma [řešení potíží s laděním](#troubleshoot-debugging).

## <a name="debug-aspnet-core-apps"></a>Ladění aplikací ASP.NET Core

Výchozí hodnota je IIS Express a je předem nakonfigurovaná. Pokud provádíte ladění v místní službě IIS, ujistěte se, že splňujete [požadavky pro místní ladění služby IIS](#iis).

1. Vyberte projekt ASP.NET Core v aplikaci Visual Studio **Průzkumník řešení** a klikněte na ikonu **vlastnosti** , stiskněte klávesu **ALT**+**ENTER**nebo klikněte pravým tlačítkem myši a zvolte možnost **vlastnosti**.

1. Vyberte kartu **ladit** .

1. V podokně **Vlastnosti vedle možnosti** **Profile**
   - V případě IIS Express v rozevíracím seznamu vyberte **IIS Express** .
   - V poli místní IIS vyberte název aplikace z rozevíracího seznamu nebo vyberte možnost **Nový**, vytvořte nový název profilu a vyberte **OK**.

1. Vedle nabídky **Spustit**vyberte z rozevíracího seznamu buď **IIS Express** , nebo **službu IIS** .

1. Ujistěte se, že je vybraná možnost **spustit prohlížeč** .

1. V části **proměnné prostředí**se ujistěte, že je **ASPNETCORE_ENVIRONMENT** k dispozici s hodnotou **vývoj**. Pokud ne, vyberte **Přidat** a přidat.

   ![Nastavení ladicího programu ASP.NET Core](../debugger/media/dbg-aspnet-enable-debugging3.png "Nastavení ladicího programu ASP.NET Core")

1. Použijte **soubor** > **Uložit vybrané položky** nebo **CTRL**+**s** pro uložení změn.

1. Chcete-li ladit aplikaci, v projektu nastavte zarážky u určitého kódu. Na panelu nástrojů sady Visual Studio se ujistěte, že je konfigurace nastavená na **ladit**, a v poli emulátor se zobrazí buď **IIS Express**, nebo nový název profilu IIS.

1. Chcete-li spustit ladění, vyberte možnost **IIS Express** nebo **\<název profilu služby IIS >** na panelu nástrojů vyberte možnost **Spustit ladění** z nabídky **ladění** nebo stiskněte klávesu **F5**. Ladicí program se pozastaví na zarážce. Pokud ladicí program nemůže narazit na zarážky, přečtěte si téma [řešení potíží s laděním](#troubleshoot-debugging).

## <a name="troubleshoot-debugging"></a>Řešení potíží s laděním

Pokud místní ladění služby IIS nemůže postupovat na zarážku, postupujte podle těchto kroků a odstraňte potíže.

1. Spusťte webovou aplikaci ze služby IIS a ujistěte se, že funguje správně. Ponechte webovou aplikaci spuštěnou.

2. V aplikaci Visual Studio vyberte možnost **ladění > připojit k procesu** nebo stiskněte klávesovou **zkratku Ctrl**+**ALT**+**P**a připojte se k ASP.NET nebo ASP.NET Core procesu (obvykle **W3wp. exe** nebo **dotnet. exe**). Další informace najdete v tématu [připojení k procesu](attach-to-running-processes-with-the-visual-studio-debugger.md) a [hledání názvu ASP.NET procesu](how-to-find-the-name-of-the-aspnet-process.md).

Pokud se můžete připojit a použít zarážku pomocí příkazu **připojit k procesu**, ale ne pomocí **ladění** > **Spustit ladění** nebo **F5**, je nastavení pravděpodobně nesprávné ve vlastnostech projektu. Pokud použijete soubor hostitelů, ujistěte se, že je správně nakonfigurován také.

## <a name="configure-debugging-in-the-webconfig-file"></a>Konfigurace ladění v souboru Web. config

Projekty ASP.NET mají ve výchozím nastavení soubory *Web. config* , které obsahují konfiguraci aplikace i informace o spuštění, včetně nastavení ladění. Soubory *Web. config* musí být správně nakonfigurovány pro ladění. Nastavení **vlastností** v předchozích částech aktualizuje soubory *Web. config* , ale můžete je také nakonfigurovat ručně.

> [!NOTE]
> Projekty ASP.NET Core neobsahují na začátku soubory *Web. config* , ale pro konfiguraci aplikace a informace o spuštění použijte soubory *appSettings. JSON* a *launchSettings. JSON* . Nasazení aplikace vytvoří soubor *Web. config* nebo soubory v projektu, ale obvykle neobsahuje informace o ladění.

> [!TIP]
> Proces nasazení může aktualizovat nastavení *Web. config* , takže před pokusem o ladění se ujistěte, že je soubor *Web. config* nakonfigurován pro ladění.

**Postup ruční konfigurace souboru *Web. config* pro ladění:**

1. V aplikaci Visual Studio otevřete soubor *Web. config* projektu ASP.NET.

2. *Web. config* je soubor XML, takže obsahuje vnořené oddíly označené značkami. Vyhledejte část `configuration/system.web/compilation`. (Pokud `compilation` element neexistuje, vytvořte ho.)

3. Ujistěte se, že atribut `debug` v elementu `compilation` je nastaven na `true`. (Pokud `compilation` element neobsahuje atribut `debug`, přidejte jej a nastavte jej na `true`.)

   Pokud používáte místní službu IIS namísto výchozího serveru IIS Express, ujistěte se, že hodnota atributu `targetFramework` v `compilation` elementu odpovídá rozhraní serveru IIS.

   `compilation` element souboru *Web. config* by měl vypadat jako v následujícím příkladu:

   > [!NOTE]
   > Tento příklad je částečný soubor *Web. config* . V elementech `configuration` a `system.web` jsou obvykle další oddíly XML a element `compilation` může obsahovat i další atributy a elementy.

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

[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] automaticky detekuje všechny změny v souborech *Web. config* a aplikuje nové nastavení konfigurace. Změny se projeví až po restartování počítače nebo serveru služby IIS.

Web může obsahovat několik virtuálních adresářů a podadresářů, soubory *Web. config* v každém z nich. aplikace [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] dědí nastavení konfigurace ze souborů *Web. config* na vyšších úrovních v cestě URL. Nastavení hierarchického souboru *Web. config* se vztahuje na všechny [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikace pod nimi v hierarchii. Nastavení jiné konfigurace v souboru *Web. config* , který je nižší v hierarchii, přepisuje nastavení ve vyšším souboru.

Pokud například zadáte `debug="true"` v <em>www.Microsoft.com/AAA/Web.config</em>, každá aplikace ve složce *AAA* nebo v jakékoli podsložce *AAA* zdědí toto nastavení, s výjimkou případů, kdy jedna z těchto aplikací přepisuje nastavení pomocí vlastního *souboru Web. config.* souborů.

## <a name="publish-in-debug-mode-using-the-file-system"></a>Publikovat v režimu ladění pomocí systému souborů

Existují různé způsoby, jak publikovat aplikace do služby IIS. Tyto kroky ukazují, jak vytvořit a nasadit ladicí profil publikování pomocí systému souborů. Chcete-li to provést, musíte spustit aplikaci Visual Studio jako správce.

> [!IMPORTANT]
> Pokud změníte kód nebo znovu sestavíte, je nutné zopakovat tyto kroky pro opětovné publikování.

1. V aplikaci Visual Studio klikněte pravým tlačítkem myši na projekt a vyberte možnost **publikovat**.

3. Vyberte **IIS, FTP atd.** a klikněte na **publikovat**.

    ![Publikování ve službě IIS](media/dbg-aspnet-local-iis.png "Publikování ve službě IIS")

4. V dialogovém okně **CustomProfile** pro **metodu publikovat**vyberte možnost **systém souborů**.

5. Pro **cílové umístění**vyberte **Procházet** ( **...** ).

   - Pro ASP.NET vyberte **místní IIS**, vyberte web, který jste pro aplikaci vytvořili, a pak vyberte **otevřít**.

     ![Publikování do ASP.NET do služby IIS](media/dbg-aspnet-local-iis1.png "Publikování ASP.NET do služby IIS")

   - V ASP.NET Core vyberte **systém souborů**, vyberte složku, kterou jste pro aplikaci nastavili, a pak vyberte **otevřít**.

1. Vyberte **Další**.

1. V části **Konfigurace**vyberte **ladění** z rozevíracího seznamu.

1. Vyberte **Uložit**.

1. V dialogovém okně **publikovat** se ujistěte, že se zobrazí **CustomProfile** (nebo název profilu, který jste právě vytvořili) a **LastUsedBuildConfiguration** je nastavené na **ladění**.

1. Vyberte **publikovat**.

    ![Publikování ve službě IIS](media/dbg-aspnet-local-iis-select-site.png "Publikování ve službě IIS")

> [!IMPORTANT]
> Režim ladění významně snižuje výkon aplikace. Pro nejlepší výkon nastavte `debug="false"` v *souboru Web. config* a určete sestavení pro vydání při nasazení produkční aplikace nebo provedení měření výkonu.

## <a name="see-also"></a>Viz také:
- [Ladění ASP.NET: Systémové požadavky](aspnet-debugging-system-requirements.md)
- [Postupy: Spuštění pracovního procesu v rámci uživatelského účtu](how-to-run-the-worker-process-under-a-user-account.md)
- [Postupy: Hledání názvu procesu ASP.NET](how-to-find-the-name-of-the-aspnet-process.md)
- [Ladění nasazených webových aplikací](debugging-deployed-web-applications.md)
- [Návod: ladění webového formuláře](walkthrough-debugging-a-web-form.md)
- [Postupy: Ladění výjimek ASP.NET](how-to-debug-aspnet-exceptions.md)
- [Ladění webových aplikací: chyby a řešení potíží](debugging-web-applications-errors-and-troubleshooting.md)
