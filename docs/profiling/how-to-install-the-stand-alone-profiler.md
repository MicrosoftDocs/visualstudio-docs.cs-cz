---
title: 'Postup: Instalace samostatného profileru | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- performance tools, installing stand-alone profiler
- profiling tools, stand-alone profiler
ms.assetid: cae81c95-83cd-4ab6-8a98-84ef977a2f6d
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: ec0f211db3d9906d83d9bcf7c7a0ab79ec3e1b7f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77557828"
---
# <a name="how-to-install-the-stand-alone-profiler"></a>Postup: Instalace samostatného profileru
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]poskytuje samostatný profiler založený na příkazovém řádku, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] který lze spustit bez instalace ide. K této situaci dochází, pokud počítač nemá nebo nemůže mít nainstalované vývojové prostředí. Například byste neměli instalovat vývojové prostředí na produkční webový server.

> [!NOTE]
> Pokud používáte samostatný profiler ke shromažďování údajů o výkonu pro ASP.NET webu, nástroj [čára VSPerfASPNetCmd](../profiling/vsperfaspnetcmd.md) se doporučuje přes nástroj [VSPerfCmd.](../profiling/vsperfcmd.md)

### <a name="to-install-the-stand-alone-profiler"></a>Instalace samostatného profileru

1. Stáhněte si [nástroje pro výkon sady Visual Studio](https://visualstudio.microsoft.com/downloads/?q=performance+tools#performance-tools-for-visual-studio).

1. Vyhledejte instalátor samostatného profilu *(vs_standaloneprofiler.exe),* do kterého jste stáhli nástroje pro výkon a spusťte je.

2. Přidejte cestu pro *vsinstr.exe* do systémové cesty.

   > [!NOTE]
   > Chcete-li získat cestu k nástrojům profilování, přečtěte si informace [o určení cesty k nástrojům příkazového řádku](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). V 64bitových počítačích jsou k dispozici 64bitová i 32bitová verze nástrojů. Chcete-li použít nástroje příkazového řádku profileru, musíte přidat cestu nástroje do proměnné prostředí PATH v okně příkazového řádku nebo ji přidat do samotného příkazu.

3. Na příkazovém řádku zadejte **Příkaz VSInstr**.

   > [!NOTE]
   > Pokud jsou zobrazeny informace o použití pro vsinstr.exe, vše je nastaveno správně. Pokud se zobrazí chyba, která uvádí vsinstr.exe nebo některá z jeho závislostí nebyla nalezena, ujistěte se, že máte správně nastavené cesty, jak je popsáno v kroku 2.

4. Nastavení serveru symbolů nastavením proměnné **_NT_SYMBOL_PATH** na **symsrv\*symsrv.dll\*c:\localcache\* **

5. Po nastavení serveru symbolů pomocí proměnných systémového prostředí spusťte nástroje profileru příkazového řádku na novém příkazovém řádku. To umožňuje nové proměnné prostředí se projeví. Do okna příkazového řádku zadejte následující příkaz:

    **spustit %COMSPEC%**

   > [!NOTE]
   > Podrobné pokyny k nastavení balíčku serveru symbolů naleznete v [tématu How to: Reference Windows symbol information](../profiling/how-to-reference-windows-symbol-information.md).

6. Pomocí nástroje [VSPerfReport](../profiling/vsperfreport.md) serializujte symboly do souboru dat profilování (.vsp). Použijte **přepínače VSPerfReport /summary:all /packsymbols.** Pokud nemáte v datovém souboru vložené symboly, ujistěte se, že máte nastavena proměnná prostředí _NT_SYMBOL_PATH.

## <a name="see-also"></a>Viz také
- [Profil z příkazového řádku](../profiling/using-the-profiling-tools-from-the-command-line.md)
- [Návod: Profilace z příkazového řádku s použitím instrumentace](command-line-profiling-of-stand-alone-applications.md)
- [Postupy: Odkazování na informace o symbolech Windows](../profiling/how-to-reference-windows-symbol-information.md)
- [VSPerfReport](../profiling/vsperfreport.md)
