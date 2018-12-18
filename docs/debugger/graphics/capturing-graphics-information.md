---
title: Zaznamenání grafických informací | Dokumentace Microsoftu
ms.custom: ''
ms.date: 02/09/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.graphics.frame
- vs.graphics.capturewindow
- VS.ToolsOptionsPages.Graphics_Diagnostics.Capture
ms.assetid: 187ce86e-e340-4f6c-8937-8e8f1027a17f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 09571f593c77ffed1daaeaa2ac7639e2a97a32ea
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49820522"
---
# <a name="capturing-graphics-information"></a>Zaznamenání grafických informací
Zachytit informace grafiky z aplikace Direct3D analyzátoru grafiky sady Visual Studio můžete použít k diagnostice problémů s vykreslováním a problémy s výkonem.  
  
## <a name="capturing-graphics-information"></a>Zachycení informací grafiky  
 Zachycení informací grafiky je dvoustupňový proces. Nejprve spusťte aplikaci v rámci Diagnostiky grafiky a následně určete jeden nebo více snímků, ze kterých budou zachyceny podrobné informace.  
  
### <a name="to-run-your-app-under-graphics-diagnostics"></a>Spuštění aplikace v rámci Diagnostiky grafiky  
  
- V panelu nabídky zvolte **ladění**, **grafiky**, **spustit ladění grafiky**. (Klávesnice: stiskněte klávesy Alt + F5)  
  
- Na **grafiky** nástrojů, zvolte **spustit ladění grafiky** tlačítko.  
  
  Když je aplikace spuštěna v rámci Diagnostiky grafiky, některé druhy informací grafiky jsou zachycovány neustále. Patří mezi ně nastavení zařízení, vytváření řetězce přepnutí, vytváření grafických objektů a zdrojů a další důležité události, které ovlivňují více než jeden snímek. Zároveň můžete zachytit podrobné informace o konkrétních snímcích. Jedná se například o volání draw a rozesílání počítačového shaderu a objekty Direct3D a zdroje, které je podporují.  
  
### <a name="to-capture-a-frame"></a>Zachycení snímku  
  
- V sadě Visual Studio na **grafiky** nástrojů, klikněte na tlačítko **zachytit snímek** tlačítko ![zachytávání grafiky ikonu tlačítka](media/debuggingdirectxgraphics.png "DebuggingDirectXGraphics").  
  
- Na klávesnici stiskněte klávesu Print Screen.
  
  > [!NOTE]
  >  Když je aplikace spuštěna v rámci **diagnostiky grafiky**, klávesu Print Screen lze použít pouze k zachycení snímku informací grafiky; neprovádí její běžné funkci. To platí, dokud neukončíte zachycování informací grafiky – obvykle zastavením ladění nebo standardním ukončením aplikace, a to i když je aktivní jiná aplikace.  
  
- Zachycení rozhraní sady Visual Studio, zvolte **zachytit snímek** tlačítko nacházel pod **diagnostické relace** časovou osu, nebo zvolte velké **zachytit snímek** tlačítko nacházel pod **snímků za sekundu** plavecké dráhy a napravo od všechny dříve zachycené snímky. Na následujícím obrázku jsou zvýrazněné obě tlačítka.  
  
   ![Zachytit snímky pomocí nástroje využití GPU.](media/pix_gpu_usage_tool_capture_frame.png)  
  
   Jakmile budete připraveni k prozkoumání snímky jste zaznamenali, spusťte **analyzátoru grafiky sady Visual Studio** podle **snímků...**  odkaz nad miniatury obrázků nebo na něj poklikejte na miniaturu.  
  
  Pouze celé snímky se dají zachytit, takže když zahájíte zachycování, je ve skutečnosti informace grafiky z následujícího snímku, která je zaznamenána. Záznam začne okamžitě po zobrazení snímku, ve kterém jste zachycování inicializovali, a ukončí se po zobrazení zachyceného snímku. Když je aplikace spuštěna v rámci Diagnostiky grafiky, můžete zachytit libovolný počet snímků. Pokud nezachytíte žádné snímky, protokol grafiky bude zrušen.  
  
  Při zachytávání snímků, Visual Studio zobrazí okno diagnostiky relace (.diagsession). Pokud toto okno zavřít, zastavení ladění nebo zavřete aplikaci, nemůže zachytit žádné další rámce do protokolu. Chcete-li zachytit více informací grafiky, budete muset spuštění aplikace v rámci diagnostiky grafiky znovu a spusťte novou relaci diagnostiky.  
  
### <a name="graphics-diagnostics-capture-options"></a>Možnosti zachytávání diagnostiky grafiky  
 Můžete nakonfigurovat zachytávání shromažďovat zásobníky volání pro všechny události grafiky nebo omezené dílčí, zakázat zachycování HUD a povolit nebo zakázat režim kompatibility zachycení.  
  
#### <a name="to-configure-graphics-diagnostics-capture-options"></a>Konfigurace možností zachycení diagnostiky grafiky  
  
1.  V panelu nabídky zvolte Nástroje, možnosti. Zobrazí se dialogové okno Možnosti.  
  
2.  V seznamu kategorií možností na levé straně zvolte diagnostiky grafiky a pak nakonfigurujte možnosti diagnostiky grafiky, které chcete.  
  
     **Během zachytávání shromažďovat zásobníky volání (zpomaluje zachytávání)**  
     Zaškrtnutím tohoto políčka shromažďovat zásobníky volání. Ve výchozím nastavení se neshromažďují zásobníky volání. K zachycení zásobníky volání, ujistěte se, že **shromažďování volání zásobníků při zachytávání (zpomaluje zachytávání** zaškrtávací políčko je nastavena na Povolit kolekci a pak nastavte buď **pro značky kreslení, odesílání, k dispozici a výkonu**možnost (výchozí) Chcete-li shromažďovat pouze ty nejdůležitější zásobníky volání, nebo **pro všechno, co** možnost shromažďovat všechny zásobníky volání. Chcete-li zastavit shromažďování zásobníků volání později, zrušte **shromažďování volání zásobníků při zachytávání (zpomaluje zachytávání** zaškrtávací políčko.  
  
     **Během zachytávání zakázat HUD ve hře**  
     Zkontrolujte, že toto políčko Zakázat HUD překrytí, který aplikaci spuštěnou v rámci grafiky diagnostiky obvykle zobrazí. Zrušte zaškrtnutí políčka Zobrazit HUD překrytí.  
  
     **Zaznamenat v režimu kompatibility**  
     Zaškrtněte toto políčko, chcete-li zachytit informace grafiky v režimu kompatibility. Zachycení v režimu kompatibility je výchozí nastavení. V režimu kompatibility nebudou podávat Direct3D, GPU podporuje všechny další funkce nad rámec těch, definované na úrovni základní funkce. To zabrání aplikaci zachytí pomocí rozšíření specifické pro hardware jeho zachycené GPU na a zajistí, že protokol grafiky lze přehrát zpět pomocí jakékoli GPU, která podporuje úroveň funkcí stejná nebo vyšší. Zrušte zaškrtnutí tohoto políčka Zakázat režim kompatibility; protokoly zachytit pomocí režimu kompatibility zakázané se nepodaří přehrát na jakékoli GPU, který nepodporuje stejné další funkce, které byly použity aplikace při zachytávání.  
  
     **Zastavit zachytávání při nalezení chyb vrstev všechny sady SDK**  
     Zaškrtnutím tohoto políčka okamžitě zastaví sběr dat, pokud nedojde k chybám.  
  
## <a name="capturing-graphics-information-remotely"></a>Vzdálené zachycení informací grafiky  
 Informace grafiky lze zaznamenat z aplikace, která je spuštěna v místním počítači nebo ve vzdáleném počítači či zařízení. Vzdálené zachycování je podporováno pro [!INCLUDE[winblue_client_2](../includes/winblue_client_2_md.md)] počítače a [!INCLUDE[winblue_winrt_2](../includes/winblue_winrt_2_md.md)] zařízení. Chcete-li zachytit informace grafiky z aplikace, která je spuštěna vzdáleně, nakonfigurujte svůj projekt na vzdálené ladění a spusťte aplikaci v rámci Diagnostiky grafiky, jak bylo popsáno dříve. Aplikace se spustí ve vzdáleném počítači a zachycené informace grafiky se zaznamenají do vývojového počítače.  
  
 Konfigurace projektu pro vzdálené ladění závisí na typu aplikace, kterou vyvíjíte, a používaném programovacím jazyku. Informace o tom, jak konfigurovat vzdálené ladění pro aplikace pro UPW, naleznete v tématu [aplikací pro UWP spuštění na vzdáleném počítači](../run-windows-store-apps-on-a-remote-machine.md). Informace o tom, jak konfigurovat vzdálené ladění pro aplikace klasické pracovní plochy Windows najdete v tématu [vzdálené ladění](../remote-debugging.md).  
  
 Později lze vzdálený počítač nebo zařízení použít k přehrání informací grafiky bez ohledu na to, odkud byly informace zachyceny. Další informace najdete v tématu [postupy: Změna počítače pro přehrávání diagnostiky grafiky](how-to-change-the-graphics-diagnostics-playback-machine.md).  
  
## <a name="capturing-graphics-information-from-the-command-line"></a>Zaznamenání grafických informací z příkazového řádku  
 Informace grafiky lze zaznamenat z aplikace pomocí nástroje příkazového řádku. Tento nástroj DXCap.exe, můžete rychle zachytávání a přehrávání grafické informace bez použití sady Visual Studio nebo zachytávání prostřednictvím kódu programu. DXCap.exe zejména, můžete pro službu automation, nebo v testovacím prostředí. Další informace o DXCap.exe najdete v tématu [zachycení nástroj příkazového řádku](command-line-capture-tool.md)  
  
## <a name="see-also"></a>Viz také  
 [Návod: Zaznamenání grafických informací](walkthrough-capturing-graphics-information.md)