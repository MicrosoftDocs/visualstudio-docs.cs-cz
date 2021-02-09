---
title: Zachytávání informací grafiky | Microsoft Docs
description: Zachyťte informace grafiky z aplikace Direct3D, abyste mohli pomocí Analyzátor grafiky sady Visual Studio diagnostikovat problémy s vykreslováním a problémy s výkonem.
ms.custom: SEO-VS-2020
ms.date: 02/09/2017
ms.topic: conceptual
f1_keywords:
- vs.graphics.frame
- vs.graphics.capturewindow
- VS.ToolsOptionsPages.Graphics_Diagnostics.Capture
ms.assetid: 187ce86e-e340-4f6c-8937-8e8f1027a17f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 29a6371d8c49aabf27227d283ec0887f07f0c89f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99876443"
---
# <a name="capturing-graphics-information"></a>Zaznamenání grafických informací
Zachyťte informace grafiky z aplikace Direct3D, abyste mohli pomocí Analyzátor grafiky sady Visual Studio diagnostikovat problémy s vykreslováním a problémy s výkonem.

## <a name="capturing-graphics-information"></a>Zachycení informací grafiky
 Zachycení informací grafiky je dvoustupňový proces. Nejprve spusťte aplikaci v rámci Diagnostiky grafiky a následně určete jeden nebo více snímků, ze kterých budou zachyceny podrobné informace.

### <a name="to-run-your-app-under-graphics-diagnostics"></a>Spuštění aplikace v rámci Diagnostiky grafiky

- Na panelu nabídek vyberte možnost **ladění**, **Grafika** a **Spustit ladění grafiky**. (Klávesnice: stiskněte klávesy Alt + F5)

- Na panelu nástrojů **Grafika** klikněte na tlačítko **Spustit ladění grafiky** .

  Když je aplikace spuštěna v rámci Diagnostiky grafiky, některé druhy informací grafiky jsou zachycovány neustále. Patří mezi ně nastavení zařízení, vytváření řetězce přepnutí, vytváření grafických objektů a zdrojů a další důležité události, které ovlivňují více než jeden snímek. Zároveň můžete zachytit podrobné informace o konkrétních snímcích. Jedná se například o volání draw a rozesílání počítačového shaderu a objekty Direct3D a zdroje, které je podporují.

### <a name="to-capture-a-frame"></a>Zachycení snímku

- V sadě Visual Studio na panelu nástrojů **Grafika** klikněte na ikonu **zachytit rámeček** tlačítko zachytit ![obrázek ikona](media/debuggingdirectxgraphics.png "DebuggingDirectXGraphics").

- Na klávesnici stiskněte klávesu PRINT SCREEN.

  > [!NOTE]
  > Když je aplikace spuštěná pod **Diagnostika grafiky**, Klávesa Print Screen se dá použít jenom k zachycení snímku informací o grafice. neprovádí svou běžnou funkci. To platí, dokud neukončíte zachycování informací grafiky – obvykle zastavením ladění nebo standardním ukončením aplikace, a to i když je aktivní jiná aplikace.

- V rozhraní pro zachycení sady Visual Studio zvolte tlačítko **zachytit rámec** , které se nachází pod časovou osou **diagnostické relace** , nebo zvolte tlačítko velký **snímek zachycení** ležící pod **snímky za sekundu** plavecké-Lane a napravo od dříve zachycených snímků. Na následujícím obrázku jsou zvýrazněna obě tlačítka.

   ![Zachyťte snímky pomocí nástroje využití GPU.](media/pix_gpu_usage_tool_capture_frame.png)

   Až budete připraveni k prohlédnutí rámců, které jste si zachytili, spusťte **analyzátor grafiky sady Visual Studio** pomocí **rámečku...** odkaz nad miniaturami obrázku nebo Poklikáním na miniaturu.

  Zachytit lze pouze celé snímky, takže když zahájíte zachytávání, jsou ve skutečnosti informace o grafech z dalšího zaznamenaného snímku. Záznam začne okamžitě po zobrazení snímku, ve kterém jste zachycování inicializovali, a ukončí se po zobrazení zachyceného snímku. Když je aplikace spuštěna v rámci Diagnostiky grafiky, můžete zachytit libovolný počet snímků. Pokud nezachytíte žádné snímky, protokol grafiky bude zrušen.

  Při zachytávání snímků Visual Studio zobrazí okno diagnostické relace (. diagsession). Pokud toto okno zavřete, zastavíte ladění nebo zavřete aplikaci, nebudete moct zachytit žádné další snímky do tohoto protokolu. Pokud chcete zachytit více grafických informací, musíte aplikaci spustit v části Diagnostika grafiky znovu a spustit novou relaci diagnostiky.

### <a name="graphics-diagnostics-capture-options"></a>Možnosti zachycení Diagnostika grafiky
 Můžete nakonfigurovat funkci Capture pro shromažďování zásobníků volání pro všechny události grafiky nebo omezené podmnožiny, Zakázat HUD zachycení a povolit nebo zakázat režim kompatibility zachycení.

#### <a name="to-configure-graphics-diagnostics-capture-options"></a>Konfigurace možností zachycení Diagnostika grafiky

1. Na řádku nabídek klikněte na nástroje, možnosti. Zobrazí se dialogové okno Možnosti.

2. V seznamu kategorie možností na levé straně vyberte možnost Diagnostika grafiky a pak nakonfigurujte požadované možnosti Diagnostika grafiky.

     **Během zachytávání shromažďovat zásobníky volání (pomaleji je zachytávání)** Zaškrtněte toto políčko, pokud chcete shromažďovat zásobníky volání. Ve výchozím nastavení nejsou shromažďovány zásobníky volání. Chcete-li zachytit zásobníky volání, ujistěte se, že je zaškrtávací políčko **zachytit zásobníky během zachytávání** nastaveno na hodnotu Povolit shromažďování a pak nastavte buď možnost **pro vykreslení, odeslání, zobrazení a značky výkonu** (výchozí) pro shromažďování pouze těch nejdůležitějších zásobníků volání, nebo možnost **pro vše** pro shromáždění všech zásobníků volání. Chcete-li zastavit shromažďování zásobníků volání později, zrušte zaškrtnutí políčka **shromáždit zásobníky volání během zachytávání (má podobu zachytit pomaleji** ).

     **Během zachytávání Zakázat HUD ve hře** Zaškrtněte toto políčko, pokud chcete zakázat překrytí HUD, že se obvykle zobrazuje aplikace běžící v rámci diagnostiky grafiky. Zrušte jeho vrácení, aby se zobrazilo překrytí HUD.

     **Zachytit v režimu kompatibility** Zaškrtněte toto políčko, pokud chcete zachytit informace grafiky v režimu kompatibility. Výchozím nastavením je zachycení v režimu kompatibility. V režimu kompatibility nebude rozhraní Direct3D hlásit, že grafický procesor podporuje všechny další funkce nad rámec těch, které jsou definovány na úrovni základní funkce. Tím se zabrání aplikaci zachycená v používání rozšíření GPU pro konkrétní hardware, které se zachycuje na, a zajišťuje, aby se protokol grafiky mohl přehrávat zpátky pomocí libovolného GPU, který podporuje stejnou nebo vyšší úroveň funkcí. Zrušením tohoto políčka zakážete režim kompatibility. protokoly zachycené pomocí zakázaného režimu kompatibility se nepodaří přehrát na jakémkoli GPU, který nepodporuje stejné další funkce, které aplikace použila při zachytávání.

     **Zastavit zachytávání při nalezení chyb vrstev sady SDK** Zaškrtněte toto políčko, pokud chcete zastavit zachytávání okamžitě, pokud dojde k chybám.

## <a name="capturing-graphics-information-remotely"></a>Vzdálené zachycení informací grafiky
 Informace grafiky lze zaznamenat z aplikace, která je spuštěna v místním počítači nebo ve vzdáleném počítači či zařízení. Pro počítače a zařízení se podporuje vzdálené zachytávání [!INCLUDE[winblue_client_2](../includes/winblue_client_2_md.md)] [!INCLUDE[winblue_winrt_2](../includes/winblue_winrt_2_md.md)] . Chcete-li zachytit informace grafiky z aplikace, která je spuštěna vzdáleně, nakonfigurujte svůj projekt na vzdálené ladění a spusťte aplikaci v rámci Diagnostiky grafiky, jak bylo popsáno dříve. Aplikace se spustí ve vzdáleném počítači a zachycené informace grafiky se zaznamenají do vývojového počítače.

 Konfigurace projektu pro vzdálené ladění závisí na typu aplikace, kterou vyvíjíte, a používaném programovacím jazyku. Informace o tom, jak nakonfigurovat vzdálené ladění pro aplikaci UWP, najdete v tématu [spouštění aplikací pro UWP na vzdáleném počítači](../run-windows-store-apps-on-a-remote-machine.md). Informace o tom, jak nakonfigurovat vzdálené ladění pro desktopovou aplikaci pro Windows, najdete v tématu [vzdálené ladění](../remote-debugging.md).

 Později lze vzdálený počítač nebo zařízení použít k přehrání informací grafiky bez ohledu na to, odkud byly informace zachyceny. Další informace najdete v tématu [Postup: změna Diagnostika grafiky počítač pro přehrávání](how-to-change-the-graphics-diagnostics-playback-machine.md).

## <a name="capturing-graphics-information-from-the-command-line"></a>Zachycení informací grafiky z příkazového řádku
 Informace o grafech se dají zachytit z aplikace pomocí nástroje příkazového řádku. Tento nástroj, DXCap.exe, může rychle zachytit a přehrát grafické informace bez použití sady Visual Studio nebo programového zachycení. Konkrétně můžete použít DXCap.exe pro automatizaci nebo v testovacím prostředí. Další informace o DXCap.exe najdete v tématu [Nástroj pro zachycení z příkazového řádku](command-line-capture-tool.md) .

## <a name="see-also"></a>Viz také
- [Návod: Zaznamenání grafických informací](walkthrough-capturing-graphics-information.md)