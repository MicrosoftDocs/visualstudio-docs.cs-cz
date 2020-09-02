---
title: Postup instalace samostatného profileru | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: 950927510d4c7acd77db22e80dff59946c0d6c20
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85330136"
---
# <a name="how-to-install-the-stand-alone-profiler"></a>Postupy: Instalace samostatného profileru
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] poskytuje samostatný Profiler založený na příkazovém řádku, který se dá spustit bez instalace [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] integrovaného vývojového prostředí (IDE). K této situaci dochází, když počítač není nebo nemůže mít nainstalované vývojové prostředí. Například byste neměli instalovat vývojové prostředí na provozním webovém serveru.

> [!NOTE]
> Při použití samostatného profileru ke shromažďování údajů o výkonu pro web ASP.NET se nástroj [VSPerfASPNETCmd](../profiling/vsperfaspnetcmd.md) line doporučuje nad nástrojem [VSPerfCmd](../profiling/vsperfcmd.md) .

### <a name="to-install-the-stand-alone-profiler"></a>Instalace samostatného profileru

1. Stáhněte si [nástroje Performance Tools for Visual Studio](https://visualstudio.microsoft.com/downloads/?q=performance+tools#performance-tools-for-visual-studio).

1. Vyhledejte instalační program samostatného profilu (*vs_standaloneprofiler.exe*), do kterého jste stáhli nástroje pro sledování výkonu, a spusťte ho.

2. Přidejte cestu pro *vsinstr.exe* k systémové cestě.

   > [!NOTE]
   > Postup získání cesty k nástrojům pro profilaci najdete v tématu [Určení cesty k nástrojům příkazového řádku](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Na 64 počítačích jsou k dispozici i 64 32 a 32bitové verze nástrojů. Chcete-li použít nástroje příkazového řádku profileru, je nutné přidat cestu k nástrojům do proměnné prostředí PATH v okně příkazového řádku nebo je přidat do samotného příkazu.

3. Do příkazového řádku zadejte **VSInstr**.

   > [!NOTE]
   > Pokud se zobrazí informace o použití vsinstr.exe, vše se nastaví správně. Pokud se zobrazí chyba, že stav vsinstr.exe nebo jedna z jejích závislostí nebyla nalezena, ujistěte se, že máte správně nastavené cesty, jak je popsáno v kroku 2.

4. Nastavení serveru symbolů nastavením proměnné **_NT_SYMBOL_PATH** na **Symsrv \*symsrv.dll\* c:\localcache \* https://msdl.microsoft.com/download/symbols **

5. Po nastavení serveru symbolů pomocí proměnných prostředí systému spusťte nástroje profileru příkazového řádku na novém příkazovém řádku. To umožňuje, aby se nové proměnné prostředí projevily. V okně příkazového řádku zadejte následující příkaz:

    **spustit% COMSPEC%**

   > [!NOTE]
   > Podrobné pokyny k nastavení balíčku serveru symbolů naleznete v tématu [How to: Reference Windows symbol Information](../profiling/how-to-reference-windows-symbol-information.md).

6. Použijte nástroj [VSPerfReport](../profiling/vsperfreport.md) k serializaci symbolů do souboru dat profilování (. vsp). Použijte **VSPerfReport/Summary: všechny přepínače/packsymbols** . Pokud nemáte vložené symboly do datového souboru, ujistěte se, že máte nastavenou proměnnou prostředí _NT_SYMBOL_PATH.

## <a name="see-also"></a>Viz také
- [Profil z příkazového řádku](../profiling/using-the-profiling-tools-from-the-command-line.md)
- [Návod: Profilace z příkazového řádku s použitím instrumentace](command-line-profiling-of-stand-alone-applications.md)
- [Postupy: Odkazování na informace o symbolech Windows](../profiling/how-to-reference-windows-symbol-information.md)
- [VSPerfReport](../profiling/vsperfreport.md)
