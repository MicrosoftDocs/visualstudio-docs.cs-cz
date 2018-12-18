---
title: Povolit ladění pro aplikace ASP.NET | Dokumentace Microsoftu
ms.custom: H1HackMay2017
ms.date: 09/21/18
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: 41da2eb360bac4c50f85bd908f980f5ee3c1d141
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49813417"
---
# <a name="debug-aspnet-or-aspnet-core-apps-in-visual-studio"></a>Ladění aplikací ASP.NET nebo ASP.NET Core v sadě Visual Studio

Můžete ladit aplikace ASP.NET a ASP.NET Core v sadě Visual Studio. Proces se liší mezi ASP.NET a ASP.NET Core, a určuje, zda jeho spuštění na službu IIS Express nebo místního serveru služby IIS. 

>[!NOTE]
>Následující kroky a nastavení platí pouze pro ladění aplikací na místním serveru. Ladění aplikací na vzdálené služby IIS používá server **připojit k procesu**a tato nastavení ignoruje. Další informace a pokyny pro vzdálené ladění aplikace v ASP.NET ve službě IIS najdete v tématu [vzdálené ladění ASP.NET na počítači se službou IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md) nebo [vzdálené ladění ASP.NET Core ve vzdáleném počítači IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md).

Integrovaný server služby IIS Express je součástí sady Visual Studio. Služba IIS Express je výchozí server pro ladění pro projekty ASP.NET a ASP.NET Core a byl předem nakonfigurován. Je nejjednodušší způsob, jak ladit a je ideální pro počáteční ladění a testování. 

Můžete také ladit ASP.NET nebo ASP.NET Core aplikaci na místním serveru služby IIS (verze 8.0 nebo novější), který je nakonfigurován ke spuštění aplikace. Chcete-li ladit na místním serveru IIS, musí splňovat následující požadavky: 

<a name="iis"></a>
- Vyberte **dobu vývoje podpora služby IIS** při instalaci sady Visual Studio. (V případě potřeby znovu spusťte instalační program sady Visual Studio, vyberte **změnit**a přidejte tuto součást.)
- Spustíte aplikaci Visual Studio jako správce. 
- Instalace a správnou konfiguraci služby IIS s odpovídající verzí technologie ASP.NET nebo ASP.NET Core. Další informace a pokyny najdete v tématu [IIS 8.0 pomocí technologie ASP.NET 3.5 a technologii ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) nebo [hostitele ASP.NET Core ve Windows se službou IIS](https://docs.microsoft.com/aspnet/core/host-and-deploy/iis/index).
- Ujistěte se, že aplikace běží ve službě IIS bez chyb.

## <a name="debug-aspnet-apps"></a>Ladění aplikací ASP.NET 

Služba IIS Express je výchozí a je předem nakonfigurován. Pokud ladíte na místním serveru IIS, ujistěte se, že splňujete [požadavky pro místní ladění služby IIS](#iis). 

1. Vyberte projekt ASP.NET v sadě Visual Studio **Průzkumníka řešení** a klikněte na tlačítko **vlastnosti** ikonu, stiskněte klávesu **Alt**+**Enter**, nebo klikněte pravým tlačítkem a zvolte **vlastnosti**.
   
1. Vyberte **webové** kartu.
   
1. V **vlastnosti** podokně v části **servery**, 
   - Pro službu IIS Express, vyberte **služby IIS Express** z rozevíracího seznamu.
   - Pro místní služby IIS
     1. Vyberte **místní služby IIS** z rozevíracího seznamu.
     1. Vedle položky **adresa URL projektu** pole, vyberte **vytvořit virtuální adresář**, pokud jste ještě nenastavili aplikace ve službě IIS.
   
1. V části **ladicí programy**vyberte **ASP.NET**.
   
   ![Nastavení ladicího programu ASP.NET](media/dbg-aspnet-enable-debugging2.png "ASP.NET nastavení ladicího programu")
   
1. Použití **souboru** > **uložit vybrané položky** nebo **Ctrl**+**S** ukládat změny. 
   
1. Ladění aplikací ve vašem projektu, nastavte zarážky v kódu. Na panelu nástrojů sady Visual Studio, ujistěte se, že v konfiguraci nastavená na **ladění**, a zobrazí se v prohlížeči chcete **služby IIS Express (\<názvu prohlížeče >)** nebo **místní služby IIS (\< Název prohlížeče >)** v poli emulátoru. 
   
1. Chcete-li spustit ladění, vyberte **služby IIS Express (\<názvu prohlížeče >)** nebo **místní služby IIS (\<názvu prohlížeče >)** na panelu nástrojů vyberte **spustit ladění**z **ladění** nabídky nebo stisknutím klávesy **F5**. Ladicí program pozastavení na zarážce. Pokud ladicí program nemůže dosažení zarážky, přečtěte si téma [ladění Poradce při potížích](#troubleshoot-debugging).

## <a name="debug-aspnet-core-apps"></a>Ladění aplikací ASP.NET Core 

Služba IIS Express je výchozí a je předem nakonfigurován. Pokud ladíte na místním serveru IIS, ujistěte se, že splňujete [požadavky pro místní ladění služby IIS](#iis). 

1. Vyberte projekt ASP.NET Core v sadě Visual Studio **Průzkumníka řešení** a klikněte na tlačítko **vlastnosti** ikonu, stiskněte klávesu **Alt**+**Enter**, nebo klikněte pravým tlačítkem a zvolte **vlastnosti**.

1. Vyberte **ladění** kartu.
   
1. V **vlastnosti** podokno, další **profilu**, 
   - Pro službu IIS Express, vyberte **služby IIS Express** z rozevíracího seznamu.
   - Pro místní služby IIS, vyberte název aplikace z rozevíracího seznamu nebo **nový**, vytvořte nový název profilu a vyberte **OK**.
   
1. Vedle položky **spuštění**, vyberte buď **služby IIS Express** nebo **IIS** z rozevíracího seznamu. 
   
1. Ujistěte se, že **spuštění prohlížeče** zaškrtnuto.
   
1. V části **proměnné prostředí**, ujistěte se, že **ASPNETCORE_ENVIRONMENT** je k dispozici s hodnotou **vývoj**. Pokud ne, vyberte **přidat** a přidejte ji.
   
   ![Nastavení ladění ASP.NET Core](../debugger/media/dbg-aspnet-enable-debugging3.png "nastavení ladicího programu ASP.NET Core")
   
1. Použití **souboru** > **uložit vybrané položky** nebo **Ctrl**+**S** ukládat změny. 
   
1. Ladění aplikací ve vašem projektu, nastavte zarážky v kódu. Na panelu nástrojů sady Visual Studio, ujistěte se, že v konfiguraci nastavená na **ladění**a buď **služby IIS Express**, nebo název nového profilu služby IIS, se zobrazí v poli emulátoru. 
   
1. Chcete-li spustit ladění, vyberte **služby IIS Express** nebo  **\<název profilu služby IIS >** na panelu nástrojů vyberte **spustit ladění** z **ladění** nabídky nebo stisknutím klávesy **F5**. Ladicí program pozastavení na zarážce. Pokud ladicí program nemůže dosažení zarážky, přečtěte si téma [ladění Poradce při potížích](#troubleshoot-debugging).

## <a name="troubleshoot-debugging"></a>Řešení potíží s ladění

Pokud místní ladění služby IIS nelze průběh až k zarážce, použijte následující postup řešení potíží. 

1. Spusťte webovou aplikaci služby IIS a ujistěte se, že běží správně. Ponechte webová aplikace spuštěná.
   
2. Ze sady Visual Studio, vyberte **ladit > připojit k procesu** nebo stiskněte klávesu **Ctrl**+**Alt**+**P**, a připojit k procesu ASP.NET nebo ASP.NET Core (obvykle **w3wp.exe** nebo **dotnet.exe**). Další informace najdete v tématu [připojit k procesu](attach-to-running-processes-with-the-visual-studio-debugger.md) a [postupy hledání názvu procesu ASP.NET](how-to-find-the-name-of-the-aspnet-process.md).

Pokud se můžete připojit a zarážce pomocí **připojit k procesu**, ale ne prostřednictvím **ladění** > **spustit ladění** nebo **F5**, nastavení je pravděpodobně nesprávná ve vlastnostech projektu. Pokud používáte soubor HOSTITELŮ, ujistěte se, že je také nakonfigurováno správně.

## <a name="configure-debugging-in-the-webconfig-file"></a>Konfigurovat ladění v souboru web.config  

Projekty ASP.NET mají *web.config* soubory ve výchozím nastavení, které obsahují obě konfigurace a spuštění informace o aplikaci, včetně nastavení pro ladění. *Web.config* soubory musí být správně nakonfigurované pro ladění. **Vlastnosti** nastavení v předchozí části aktualizace *web.config* soubory, ale můžete také nakonfigurovat jejich ručně. 

> [!NOTE]
> Projekty ASP.NET Core nemají zpočátku *web.config* soubory, ale použijte *appsettings.json* a *launchSettings.json* souborů pro konfiguraci aplikací a spuštění informace. Nasazení aplikace vytvoří *web.config* soubor či soubory v projektu, ale obvykle neobsahují informace o ladění.

> [!TIP]
> Proces nasazení může aktualizovat *web.config* nastavení, takže před pokusem o ladění, ujistěte se, že *web.config* je nakonfigurovaná pro ladění.
  
**Jak ručně nakonfigurovat *web.config* soubor pro ladění:**

1. V sadě Visual Studio, otevřete projekt ASP.NET *web.config* souboru.  
  
2. *Soubor Web.config* je soubor XML, obsahuje proto vnořené oddíly označené značkami. Vyhledejte `configuration/system.web/compilation` oddílu. (Pokud `compilation` element neexistuje, vytvořte ji.)
  
3. Ujistěte se, že `debug` atribut `compilation` prvek je nastaven na `true`. (Pokud `compilation` neobsahuje element `debug` atribut, přidejte ho a nastavte ho na `true`.) 
  
   Pokud používáte místní služby IIS místo výchozí server služby IIS Express, ujistěte se, že `targetFramework` hodnotu v atributu `compilation` neshodují elementy rozhraní na serveru služby IIS.
  
   `compilation` Elementu *web.config* soubor by měl vypadat jako v následujícím příkladu:

   > [!NOTE]
   > V tomto příkladu je částečné *web.config* souboru. Jsou obvykle další části XML `configuration` a `system.web` elementy a `compilation` element může také obsahovat jiné atributy a elementy.
  
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

[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] automaticky detekuje jakékoli změny *web.config* soubory a aplikuje nové nastavení konfigurace. Není nutné restartovat počítač nebo server služby IIS se změny projevily.  
  
Web může obsahovat několik virtuálních adresářů a podadresářů, *web.config* soubory v každém z nich. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikace dědit nastavení z *web.config* soubory na vyšších úrovních v cestě adresy URL. Hierarchických *web.config* soubor nastavení platí pro všechny [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikace pod nimi v hierarchii. Nastavení jiné konfiguraci *web.config* souboru níže v hierarchii, přepíše nastavení v souboru vyšší.  
  
Pokud zadáte například `debug="true"` v <em>www.microsoft.com/aaa/web.config</em>, libovolnou aplikaci v *aaa* složce nebo v libovolné podsložce *aaa* zdědí toto nastavení s výjimkou Pokud některou z těchto aplikací přepíše nastavení vlastní *web.config* souboru.  
  
## <a name="publish-in-debug-mode-using-the-file-system"></a>Publikování v režimu ladění pomocí systému souborů

Existují různé způsoby, jak publikovat aplikace do služby IIS. Tyto kroky ukazují, jak vytvořit a nasadit ladicí profil publikování pomocí systému souborů. Chcete-li to provést, musíte používat Visual Studio jako správce. 

> [!IMPORTANT]
> Pokud změníte kód nebo znovu sestavit, musíte opakováním těchto kroků znovu publikovat. 

1. V sadě Visual Studio, klikněte pravým tlačítkem na projekt a zvolte **publikovat**.

3. Zvolte **služby IIS, FTP atd** a klikněte na tlačítko **publikovat**.

    ![Publikování do služby IIS](media/dbg-aspnet-local-iis.png "publikovat do služby IIS")

4. V **CustomProfile** dialogovém okně pro **metodu publikování**, zvolte **systém souborů**.

5. Pro **cílové umístění**vyberte **Procházet** (**...** ).
   
   - Pro technologii ASP.NET, vyberte **místní služby IIS**, vyberte web, který jste vytvořili pro aplikaci a pak vyberte **otevřít**.
     
     ![Publikovat do technologie ASP.NET na IIS](media/dbg-aspnet-local-iis1.png "publikovat ASP.NET do služby IIS")
     
   - ASP.NET Core, vyberte **systému souborů**, vyberte složku, nastavení pro aplikaci a pak vyberte **otevřít**.

1. Vyberte **Další**. 

1. V části **konfigurace**vyberte **ladění** z rozevíracího seznamu.

1. Vyberte **Uložit**.

1. V **publikovat** dialogového okna, ujistěte se, že **CustomProfile** (nebo název profilu, který jste právě vytvořili) se zobrazí, a **LastUsedBuildConfiguration** je nastavena na  **Ladění**. 

1. Vyberte **publikovat**.

    ![Publikování do služby IIS](media/dbg-aspnet-local-iis-select-site.png "publikovat do služby IIS")

> [!IMPORTANT]
> Režim ladění výrazně snižuje výkon vaší aplikace. Pro zajištění nejlepšího výkonu nastavte `debug="false"` v *web.config* a určení verze sestavení při nasazení aplikace v produkčním prostředí nebo měřením výkonu.  

## <a name="see-also"></a>Viz také:  
[Ladění ASP.NET: systémové požadavky](aspnet-debugging-system-requirements.md)   
[Postupy: spuštění pracovního procesu v rámci uživatelského účtu](how-to-run-the-worker-process-under-a-user-account.md)   
[Postupy: hledání názvu procesu ASP.NET](how-to-find-the-name-of-the-aspnet-process.md)   
[Ladění nasazených webových aplikací](debugging-deployed-web-applications.md)   
[Návod: Ladění webového formuláře](walkthrough-debugging-a-web-form.md)   
[Postupy: ladění výjimek ASP.NET](how-to-debug-aspnet-exceptions.md)   
[Ladění webových aplikací: chyby a řešení potíží](debugging-web-applications-errors-and-troubleshooting.md)
  
